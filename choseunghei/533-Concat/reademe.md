# 533-Concat

### 질문
	JavaScript의 Array.concat 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, 인수를 왼쪽부터 concat한 새로운 배열을 반환해야 합니다.


### 풀이
	1. T, U를 배열로 제한해야하므로 extends any[] 를 각 인수 옆에 적는다
	2. spread 연산자로 배열을 새롭게 만들어서 붙여준다.

### 해답
```javascript
	type Concat<T extends any[], U extends any[]> = [...T, ...U];

	/* _____________ 예시 _____________ */
	type Result = Concat<[1], [2]> // expected to be [1, 2]
```