# Parameters

내장 제네릭 Parameters<T>를 이를 사용하지 않고 구현하세요.

예시 :

```ts
const foo = (arg1: string, arg2: number): void => {}

type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]
```

테스트케이스 :

```ts
import type { Equal, Expect } from '@type-challenges/utils'

const foo = (arg1: string, arg2: number): void => {}
const bar = (arg1: boolean, arg2: { a: 'A' }): void => {}
const baz = (): void => {}

type cases = [
  Expect<Equal<MyParameters<typeof foo>, [string, number]>>,
  Expect<Equal<MyParameters<typeof bar>, [boolean, { a: 'A' }]>>,
  Expect<Equal<MyParameters<typeof baz>, []>>,
]
```

해답 :

```ts
type MyParameters<T extends (...args: any[]) => unknown> = T extends (...args: infer R) => unknown ? R : unknown
```

정리 :

참고자료 :
- https://dev.to/aexol/typescript-tutorial-infer-keyword-2cn