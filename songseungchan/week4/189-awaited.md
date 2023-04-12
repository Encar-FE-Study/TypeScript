### 질문

  Promise와 같은 타입에 감싸인 타입이 있을 때, 안에 감싸인 타입이 무엇인지 어떻게 알 수 있을까요?

  예시: 들어 `Promise<ExampleType>`이 있을 때, `ExampleType`을 어떻게 얻을 수 있을까요?

  ```ts
  type ExampleType = Promise<string>

  type Result = MyAwaited<ExampleType> // string
  ```



/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type X = Promise<string>
type Y = Promise<{ field: number }>
type Z = Promise<Promise<string | number>>
type Z1 = Promise<Promise<Promise<string | boolean>>>
type T = { then: (onfulfilled: (arg: number) => any) => any }

type cases = [
  Expect<Equal<MyAwaited<X>, string>>,
  Expect<Equal<MyAwaited<Y>, { field: number }>>,
  Expect<Equal<MyAwaited<Z>, string | number>>,
  Expect<Equal<MyAwaited<Z1>, string | boolean>>,
  Expect<Equal<MyAwaited<T>, number>>,
]

// @ts-expect-error
type error = MyAwaited<number>


=======================

## 실패한 시도:

- 1번쨰
 실패사유 :  `Unused '@ts-expect-error' directive (2578) 발생 (type error = MyAwaited<number> 에서 발생)
type MyAwaited<T> = T extends PromiseLike<infer R> ? MyAwaited<R> : T;`

- 2번째 => T가 PromiseLike여야 하니 제네릭에 타입 제한하자
실패사유 : `Type 'P' does not satisfy the constraint 'PromiseLike<any>'.(2344) => T = Promise<string>`이면 P은 PromiseLike가 아니므로 타입제한 만족X
`type MyAwaited<T extends PromiseLike<any>> = T extends PromiseLike<infer P> ? MyAwaited<P> : T;`



## 해답 
```type MyAwaited<T extends PromiseLike<any>> = T extends PromiseLike<infer P> ? ( P extends PromiseLike<any> ? MyAwaited<P> : P ) : T;```

## 살펴보자
```T extends PromiseLike<infer P> ? ( P extends PromiseLike<any> ? MyAwaited<P> : P ) : T ```을 보자

`T extends PromiseLike<infer P>`을 [1] ?` ( P extends PromiseLike<any> ? MyAwaited<P> : P )`를 [2] : `T`를 [3]이라 본다면,

- `[1]  T extends PromiseLike<infer P> :  Promise<T>`의 값을 받을때, 
T가 then메서드를 가지는 객체라면 2로 아니면 3으로 조건이 결정됨

- `[2]  ( P extends PromiseLike<any> ? MyAwaited<P> : P )` : [1]에서 추론한 P의 타입을 체크하여 then메서드를 가진 객체라면 재귀 실행, 그게 아니라면 그 값을 반환하고 종료
이를 계속 반복하는 구조이다.


### ex1) `Promise<string>`인 경우 
- [1]에서 `T는 Promise<string>, P는 string이 됨(인자의 위치를 가지고 이를 추론)`
- [2] `P는 string이므로 P를 반환`하고 끝이난다.
- 따라서 `Promise<string> = string`


### ex2) `Promise<Promise<Promise<string | boolean>>>`
 - `Expect<Equal<MyAwaited<Z1>, string | boolean>> : true`

- `[1]에서 T = Promise<Promise<string | boolean>>`이고, 이는 조건부타입을 만족
- `[2]에서 P = Promise<string | boolean>, 이는 [2]의 조건부타입을 만족 => MyAwaited<P>= MyAwaited<Promise<string | boolean>>`를 실행
-  이후는 ex1처럼 과정을 반복하므로 결과는 string | boolean;

