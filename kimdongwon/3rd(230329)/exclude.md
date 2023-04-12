# Exclude

/*
  43 - Exclude
  -------
  by Zheeeng (@zheeeng) #쉬움 #built-in #union

  ### 질문

  `T`에서 `U`에 할당할 수 있는 타입을 제외하는 내장 제네릭 `Exclude<T, U>`를 이를 사용하지 않고 구현하세요.

  예시:

  ```ts
  type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'
  ```

  > GitHub에서 보기: https://tsch.js.org/43/ko
*/

/* _____________ 여기에 코드 입력 _____________ */

// type MyExclude<T, U> = T extends U ? never : T;
// type MyExclude<T, U> = Exclude<T, U>
type MyExclude<T, U> = Omit<T, U extends keyof any>;

/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<MyExclude<'a' | 'b' | 'c', 'a'>, 'b' | 'c'>>,
  Expect<Equal<MyExclude<'a' | 'b' | 'c', 'a' | 'b'>, 'c'>>,
  Expect<Equal<MyExclude<string | number | (() => void), Function>, string | number>>,
]

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/43/answer/ko
  > 정답 보기: https://tsch.js.org/43/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/

## 알게된 점

- exclude를 바로 사용하면 되는데 왜 이렇게 사용하는지 잘 모르겠다. 
- 이 문제에서는 omit과 excludes의 차이점을 구별할 수 있었다. 
- omit으로도 처리해보고 싶어 시도를 해보았지만 실패..