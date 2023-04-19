/*
3060 - Unshift
  -------
by jiangshan (@jiangshanmeta) #쉬움 #array

### 질문

`Array.unshift`의 타입 버전을 구현하세요.

예시:

  ```typescript
  type Result = Unshift<[1, 2], 0> // [0, 1, 2,]
  ```

> GitHub에서 보기: https://tsch.js.org/3060/ko
*/

/* _____________ 여기에 코드 입력 _____________ */
```ts
type Unshift<T extends any[], U> = [U, ...T];

```

### 정리
* 
