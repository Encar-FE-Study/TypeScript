# 14-First Of Array

### 느낀점
	extends와 삼항연산자, never 3가지를 조합해서 문제를 해결했다.

### 질문
  `T`에서 `U`에 할당할 수 있는 타입을 제외하는 내장 제네릭 `Exclude<T, U>`를 이를 사용하지 않고 구현하세요.

### 해답
```javascript
	type Exclude<T, U> = T extends U ? never : T;

	/* _____________ 예시 _____________ */
	type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'
```