/*
  533 - Concat
  -------
  by Andrey Krasovsky (@bre30kra69cs) #쉬움 #array

  ### 질문

  JavaScript의 `Array.concat` 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, 인수를 왼쪽부터 concat한 새로운 배열을 반환해야 합니다.

  예시:

  ```ts
  type Result = Concat<[1], [2]> // expected to be [1, 2]
  ```

  > GitHub에서 보기: https://tsch.js.org/533/ko
*/

/* _____________ 여기에 코드 입력 _____________ */

// 대부분 사람들이 적은 대답 type Concat<T extends any[], U extends any[]> = [...T, ...U]

// 내 생각에는 요거
type Concat<T, U> = T extends any[] ? U extends any[] ? [...T, ...U] : [...T, U] : U extends any[] ? [T, ...U] : [T, U]

/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<Concat<[], []>, []>>,
  Expect<Equal<Concat<[], [1]>, [1]>>,
  Expect<Equal<Concat<[1, 2], [3, 4]>, [1, 2, 3, 4]>>,
  Expect<Equal<Concat<['1', 2, '3'], [false, boolean, '4']>, ['1', 2, '3', false, boolean, '4']>>,
]

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/533/answer/ko
  > 정답 보기: https://tsch.js.org/533/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/


/*
Javascript Concat

concat() 메서드는 인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환합니다.

const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = ['g', ['h', 'i']];
const array4 = [{ name: '박상준' }];
const array5 = array1.concat(array4);

console.log(array4);
// Expected output: Array ["a", "b", "c", "d", "e", "f"]



*/