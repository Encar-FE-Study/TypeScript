# awaited

/*
  189 - Awaited
  -------
  by Maciej Sikora (@maciejsikora) #쉬움 #promise #built-in

  ### 질문

  Promise와 같은 타입에 감싸인 타입이 있을 때, 안에 감싸인 타입이 무엇인지 어떻게 알 수 있을까요?

  예시: 들어 `Promise<ExampleType>`이 있을 때, `ExampleType`을 어떻게 얻을 수 있을까요?

  ```ts
  type ExampleType = Promise<string>

  type Result = MyAwaited<ExampleType> // string
  ```

  > 출처: [original article](https://dev.to/macsikora/advanced-typescript-exercises-question-1-45k4) by [@maciejsikora](https://github.com/maciejsikora)

  > GitHub에서 보기: https://tsch.js.org/189/ko
*/

/* _____________ 여기에 코드 입력 _____________ */

type MyAwaited<T> = Awaited<T>;

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

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/189/answer/ko
  > 정답 보기: https://tsch.js.org/189/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/

## 알게된 점

- promise 타입에서 반환되는 값을 추출하는 유틸리티 타입. 즉, await 키워드로 promise를 대기하고 해당 promise가 해결될 때 반환되는 값을 추출하여 타입으로 정의하는 타입.
- promiseLike랑 구분해서 사용. promise는 내부적으로 상태와 결과를 갖는다. pending, fulfiled, rejected 와 같은 3가지 상태를 갖으며 각각의 상태에 대한 결과값이 존재한다. 반면, PromiseLike 객체는 Promise와 유사한 동작을 하는 객체를 추상화하는 인터페이스일 뿐이며, 그 자체로는 내부 상태나 결과값을 갖지 않는다. 
- never 타입은 절대 발생할 수 없는 타입을 나타냄.
- void는 함수 한정.


## 종하과장님 질문

- never란? 무슨타입?
- type alias vs interface 차이. interface내에 제네릭 사용불가? 
  - interface는 재정의가 안됨
  - type alias는 인터섹션 타입을 사용하고 interface는 상속을 사용한다.
  - type alias는 union 타입이나 tuple 타입을 정의할 수 있다.
  - interface는 객체 지향적인 개념을 정의할 수 있다.
  - 디버깅 시 type alias가 좀 더 직관적으로 잘 보여줌. interface는 내부 객체를 보여줘서 파악하기가 힘듬.
- 테스트케이스를 하나하나 맞춰가면서 풀어보기.