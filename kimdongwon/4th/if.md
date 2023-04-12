# if

/*
  268 - If
  -------
  by Pavel Glushkov (@pashutk) #쉬움 #utils

  ### 질문

  조건 `C`, 참일 때 반환하는 타입 `T`, 거짓일 때 반환하는 타입 `F`를 받는 타입 `If`를 구현하세요. `C`는 `true` 또는 `false`이고, `T`와 `F`는 아무 타입입니다.

  예시:

  ```ts
  type A = If<true, 'a', 'b'>  // expected to be 'a'
  type B = If<false, 'a', 'b'> // expected to be 'b'
  ```

  > GitHub에서 보기: https://tsch.js.org/268/ko
*/

/* _____________ 여기에 코드 입력 _____________ */

type If<C extends boolean, T, F> = C extends true ? T : F;

/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<If<true, 'a', 'b'>, 'a'>>,
  Expect<Equal<If<false, 'a', 2>, 2>>,
]

// @ts-expect-error
type error = If<null, 'a', 'b'>

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/268/answer/ko
  > 정답 보기: https://tsch.js.org/268/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/

## 알게된 점

- extends로 범위를 좁혀서 타입을 strict하게 지정을 해줌.
- extends 키워드는 조건부 타입에서 입력된 타입 파라미터의 범위를 제한하는 데 사용됨.


## 참고

- https://egg-programmer.tistory.com/307