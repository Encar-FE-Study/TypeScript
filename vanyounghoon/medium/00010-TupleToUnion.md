# TupleToUnion

튜플 값으로 유니온 타입을 생성하는 제네릭 TupleToUnion<T>를 구현하세요.

예시 :

```ts
type Arr = ['1', '2', '3']

type Test = TupleToUnion<Arr> // expected to be '1' | '2' | '3'
```

테스트케이스 :

```ts
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<TupleToUnion<[123, '456', true]>, 123 | '456' | true>>,
  Expect<Equal<TupleToUnion<[123]>, 123>>,
]
```

해답 :

```ts
type TupleToUnion<T> = T extends Array<infer U> ? U : never
type TupleToUnion<T extends unknown[]> = T[number]
```

정리 :

참고자료 :
