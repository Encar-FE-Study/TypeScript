# Unshift

예시 :

```ts
type Result = Unshift<[1, 2], 0> // [0, 1, 2,]
```

테스트케이스 :

```ts
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<Unshift<[], 1>, [1]>>,
  Expect<Equal<Unshift<[1, 2], 0>, [0, 1, 2]>>,
  Expect<Equal<Unshift<['1', 2, '3'], boolean>, [boolean, '1', 2, '3']>>,
]
```

해답 :

```ts
type Unshift<T extends unknown[], U> = [U, ...T]
```

정리 :

참고자료 :
