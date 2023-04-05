43 - Exclude
-------
by Zheeeng (@zheeeng) #쉬움 #built-in #union

### 질문

`T`에서 `U`에 할당할 수 있는 타입을 제외하는 내장 제네릭 `Exclude<T, U>`를 이를 사용하지 않고 구현하세요.

예시:

  ```ts
  type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'
  ```

/* _____________ 여기에 코드 입력 _____________ */

```ts
type MyExclude<T, U> = T extends U ? never : T
```

### 정리
* extends 에서 왼쪽에서 오른쪽 타입으로 할당 가능하면 트루
