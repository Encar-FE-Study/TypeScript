# 14-First Of Array

### 느낀점
	첫 시간에 승찬님이 설명해준 never이 떠올라 응용해서 문제를 풀었다.

### 질문
	배열(튜플) `T`를 받아 첫 원소의 타입을 반환하는 제네릭 `First<T>`를 구현하세요.

### 해답
```javascript
	type First<T extends any[]> = T extends [] ? never : T[0]

	/* _____________ 예시 _____________ */
	type arr1 = ['a', 'b', 'c']
	type arr2 = [3, 2, 1]

	type head1 = First<arr1> // expected to be 'a'
	type head2 = First<arr2> // expected to be 3
```

### 참고
https://medium.com/harrythegreat/typescript-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0-%ED%81%B4%EB%9E%98%EC%8A%A4-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-7ae8a786fb20