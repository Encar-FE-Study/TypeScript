# 10-Tuple to Union

### 질문
	튜플 값으로 유니온 타입을 생성하는 제네릭 TupleToUnion<T>를 구현하세요.

### 풀이
	1. TupleToUnion이 가지는 유니온 타입 T를 any[] 배열로 제한한다. (extends)
	2. Typescript의 내장 타입인 number를 통해 T 배열의 모든 원소의 유니온 타입을 생성한다.

### 해답
```javascript
	type TupleToUnion<T extends any[]> = T[number]

	/* _____________ 예시 _____________ */
	type Arr = ['1', '2', '3']
	type Test = TupleToUnion<Arr> // expected to be '1' | '2' | '3'
```