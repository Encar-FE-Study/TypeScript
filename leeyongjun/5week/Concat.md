# Concat

### 질문

JavaScript의 Array.concat 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, 인수를 왼쪽부터 concat한 새로운 배열을 반환해야 합니다.

예시:

```ts
type Result = Concat<[1], [2]>; // expected to be [1, 2]
```

답:

```ts
type Concat<T extends any[], U extends any[]> = [...T, ...U];
```
