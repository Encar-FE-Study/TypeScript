# 268-If

### 질문
	조건 C, 참일 때 반환하는 타입 T, 거짓일 때 반환하는 타입 F를 받는 타입 If를 구현하세요. C는 true 또는 false이고, T와 F는 아무 타입입니다.

### 풀이
	1. C가 boolean 조건이 아니라면 오류 뱉어야함. 따라서 C extends boolean
	2. C가 true 조건이면 T. 따라서 extends로 제한함.
	3. 제한된 true 조건이 아니라면 F

### 해답
```javascript
	type If<C extends boolean, T, F> = C extends true ? T : F;

	/* _____________ 예시 _____________ */
	type A = If<true, 'a', 'b'>  // expected to be 'a'
	type B = If<false, 'a', 'b'> // expected to be 'b'
```

### 참고
https://egg-programmer.tistory.com/307