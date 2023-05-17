# 9-Last of Array

### 질문
	배열 T를 사용하고 마지막 요소를 반환하는 제네릭 Last<T>를 구현합니다.

### 풀이
	1. T 제네릭을 배열로 제한
	2. T가 [...infer _, infer L]로 배열의 마지막 값을 제외하고 버린다.
	3. 배열의 마지막 값과 T가 같다면 T를 반환 아니라면 never을 반환한다.
### 해답
```javascript
	type Last<T extends any[]> = T extends [...infer _, infer L] ? L : never

	/* _____________ 예시 _____________ */
	type arr1 = ['a', 'b', 'c']
	type arr2 = [3, 2, 1]

	type tail1 = Last<arr1> // expected to be 'c'
	type tail2 = Last<arr2> // expected to be 1
```