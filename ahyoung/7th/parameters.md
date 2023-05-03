/*
  3312 - Parameters
  -------
  by midorizemi (@midorizemi) #쉬움 #infer #tuple #built-in

  ### 질문

  내장 제네릭 `Parameters<T>`를 이를 사용하지 않고 구현하세요.

  예시:

  ```ts
  const foo = (arg1: string, arg2: number): void => {}

  type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]
  ```

  > GitHub에서 보기: https://tsch.js.org/3312/ko
*/

/* _____________ 여기에 코드 입력 _____________ */


type MyParameters<T extends (...args: any[]) => any> = T extends (...args: infer P) => any ? P : never



/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

const foo = (arg1: string, arg2: number): void => {}
const bar = (arg1: boolean, arg2: { a: 'A' }): void => {}
const baz = (): void => {}

type cases = [
  Expect<Equal<MyParameters<typeof foo>, [string, number]>>,
  Expect<Equal<MyParameters<typeof bar>, [boolean, { a: 'A' }]>>,
  Expect<Equal<MyParameters<typeof baz>, []>>,
]

/* _____________ 다음 단계 _____________ */
/*
  > 정답 공유하기: https://tsch.js.org/3312/answer/ko
  > 정답 보기: https://tsch.js.org/3312/solutions
  > 다른 문제들: https://tsch.js.org/ko
*/


* infer
 : infer는 조건문에 쓰이는 타입 중 하나를 이름 붙여서 빼 와서, 삼항 연산자의 true절이나 false절에 사용하기 위해 사용한다. 

참고 사이트 <br />
* https://driip.me/b812974b-3974-46e3-829e-1476b9b30c94
* https://ui.toast.com/posts/ko_20220323
