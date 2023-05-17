
# 제목

배열 T를 사용하고 마지막 요소를 반환하는 제네릭 Last<T>를 구현합니다.


예시 :

```ts
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type tail1 = Last<arr1> // expected to be 'c'
type tail2 = Last<arr2> // expected to be 1
```

테스트케이스 :

```ts
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<Last<[2]>, 2>>,
  Expect<Equal<Last<[3, 2, 1]>, 1>>,
  Expect<Equal<Last<[() => 123, { a: string }]>, { a: string }>>,
]
```

해답 :

```ts
type Last<T extends unknown[]> = [unknown, ...T][T["length"]];
type Last<T extends any[]> = T extends [...infer _, infer L] ? L : never
```

정리 :

```ts
type Last<T extends any[]> = [any, ...T][T['length']]
type Last2<T extends any[]> = T extends [...infer _, infer L] ? L : never

type T10 = Last<string[]> // any
type T11 = Last2<string[]> // never
```

참고자료 :
