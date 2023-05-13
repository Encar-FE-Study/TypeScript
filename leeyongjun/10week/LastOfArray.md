# Last of Array

### 질문

배열 T를 사용하고 마지막 요소를 반환하는 제네릭 Last<T>를 구현합니다.

예시:

```ts
type arr1 = ["a", "b", "c"];
type arr2 = [3, 2, 1];

type tail1 = Last<arr1>; // expected to be 'c'
type tail2 = Last<arr2>; // expected to be 1
```

답:

```ts
type Last<T extends any[]> = [any, ...T][T["length"]];
```
