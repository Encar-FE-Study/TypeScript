# 16-Pop

### 질문
	배열 T를 사용하고 마지막 요소를 반환하는 제네릭 Last<T>를 구현합니다.

### 풀이
	1. T를 배열의 마지막, 나머지로 분리한다.
	2. 맨 마지막을 제외한 L을 리턴한다.
	3. 빈 배열인 경우를 고려해 []를 리턴한다.
### 해답
```javascript
	type Pop<T extends any[]> = T extends [...infer L, infer _] ? L : [];

	/* _____________ 예시 _____________ */
	type arr1 = ['a', 'b', 'c', 'd']
	type arr2 = [3, 2, 1]

	type re1 = Pop<arr1> // expected to be ['a', 'b', 'c']
	type re2 = Pop<arr2> // expected to be [3, 2]
```