# Push

### 질문

Array.push의 제네릭 버전을 구현하세요.

예시:

```ts
type Result = Push<[1, 2], "3">; // [1, 2, '3']
```

답:

```ts
type Push<T extends any[], U> = [...T, U];
```
