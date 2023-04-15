/*
  3057 - Push
  -------
  by jiangshan (@jiangshanmeta) #쉬움 #array

  ### 질문

  `Array.push`의 제네릭 버전을 구현하세요.

  예시:

  ```typescript
  type Result = Push<[1, 2], '3'> // [1, 2, '3']
  ```

  > GitHub에서 보기: https://tsch.js.org/3057/ko
*/

/* _____________ 여기에 코드 입력 _____________ */

type Push<T extends any[], U> = [...T, U]

/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<Push<[], 1>, [1]>>,
  Expect<Equal<Push<[1, 2], '3'>, [1, 2, '3']>>,
  Expect<Equal<Push<['1', 2, '3'], boolean>, ['1', 2, '3', boolean]>>,
]

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/3057/answer/ko
  > 정답 보기: https://tsch.js.org/3057/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/


## 회고
- 제네릭 문법에 익숙하지 않아 https://www.youtube.com/watch?v=pReXmUBjU3E 해당 강의를 보며 문법을 익혔다.
- any와 unknown을 많이 쓰던데 둘 중에 어떤걸 쓰는게 더 좋을지 생각해봐야할듯
