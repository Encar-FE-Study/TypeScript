# Unshift

### 질문

Array.unshift의 타입 버전을 구현하세요.

예시:

```ts
type Result = Unshift<[1, 2], 0>; // [0, 1, 2,]
```

답:

```ts
type Unshift<T extends any[], U> = [U, ...T];
```
