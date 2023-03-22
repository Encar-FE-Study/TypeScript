# First of Array

배열(튜플) T를 받아 첫 원소의 타입을 반환하는 제네릭 First<T>를 구현하세요.

예시:

```ts
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type head1 = First<arr1> // expected to be 'a'
type head2 = First<arr2> // expected to be 3
```

해답:

```ts
1. type First<T extends unknown[]> = T extends []  ? never  : T[0]

2. type First<T extends any[]> = T extends [infer K, ...infer R] ? K : never

```

정리

- infer

참고자료

- https://blog.logrocket.com/understanding-infer-typescript/