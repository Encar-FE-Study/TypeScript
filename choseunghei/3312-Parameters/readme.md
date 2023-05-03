# 3312-Parameters

### 질문
	내장 제네릭 Parameters<T>를 이를 사용하지 않고 구현하세요.

### 풀이
	1. T extends (...args: any[]) => any
	: 매개변수 T가 (args: any[]) => any와 호환 가능한지를 검사
	2. 타입 추론(infer)을 사용하여 T의 매개변수 타입들을 추론해 S라는 타입 변수에 할당합니다.
	3. 삼항 연산자를 사용해 any(모든 매개변수 타입)이 아닌 경우 never 반환

### 해답
```javascript
	type MyParameters<T extends (...args: any[]) => any> = T extends (...any: infer S) => any ? S : never

	/* _____________ 예시 _____________ */
	const foo = (arg1: string, arg2: number): void => {}

	type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]

```