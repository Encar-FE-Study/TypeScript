```ts
/* _____________ Your Code Here _____________ */

type MyReadonly<T> = {
  readonly [P in keyof T] : T[P]
}

/* _____________ Test Cases _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<MyReadonly<Todo1>, Readonly<Todo1>>>,
]

interface Todo1 {
  title: string
  description: string
  completed: boolean
  meta: {
    author: string
  }
}
```

# 설명
readonly: 읽기전용
keyof: 타입지정
in: 찾기

