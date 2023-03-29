/*
  11 - Tuple to Object
  -------
  by sinoon (@sinoon) #쉬움 #object-keys

  ### 질문

  배열(튜플)을 받아, 각 원소의 값을 key/value로 갖는 오브젝트 타입을 반환하는 타입을 구현하세요.

  예시:

  ```ts
  const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const

  type result = TupleToObject<typeof tuple> // expected { tesla: 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
  ```

  > GitHub에서 보기: https://tsch.js.org/11/ko
*/

/* _____________ 여기에 코드 입력 _____________ */

type TupleToObject<T extends readonly any[]> = {
  [K in T[number]]: K
}

/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const
const tupleNumber = [1, 2, 3, 4] as const
const tupleMix = [1, '2', 3, '4'] as const

type cases = [
  Expect<Equal<TupleToObject<typeof tuple>, { tesla: 'tesla'; 'model 3': 'model 3'; 'model X': 'model X'; 'model Y': 'model Y' }>>,
  Expect<Equal<TupleToObject<typeof tupleNumber>, { 1: 1; 2: 2; 3: 3; 4: 4 }>>,
  Expect<Equal<TupleToObject<typeof tupleMix>, { 1: 1; '2': '2'; 3: 3; '4': '4' }>>,
]

// @ts-expect-error
type error = TupleToObject<[[1, 2], {}]>

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/11/answer/ko
  > 정답 보기: https://tsch.js.org/11/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/

## 느낀점

```
아래 코드에서 number가 index로 사용이 되는건가?

```
type TupleToObject<T extends readonly any[]> = {
  [K in T[number]]: K
}
```

---

네, 맞습니다. 해당 코드에서 [K in T[number]] 구문은 T 배열의 모든 요소들 중에서 number 타입을 상속(확장)하는 타입으로 K를 정의합니다.

number 타입은 TypeScript에서 기본적으로 정의된 타입으로, 숫자 타입을 의미합니다. 따라서 T[number]는 T 배열의 모든 요소 중에서 숫자 타입을 상속하는 타입으로 정의됩니다. 즉, T 배열의 모든 인덱스 값들이 숫자 타입을 상속하고 있어야 합니다.

그래서 이 구문은 T 배열의 인덱스 값들이 K라는 변수에 할당될 수 있는 모든 숫자 타입들을 정의합니다. 따라서 TupleToObject 타입은 T 배열의 각 요소를 속성 키로 사용하고, 해당 요소의 값을 속성 값으로 사용하는 객체 타입으로 정의됩니다.
```


## 참고

- https://ghaiklor.github.io/type-challenges-solutions/ko/easy-tuple-to-object.html