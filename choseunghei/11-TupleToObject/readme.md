# 11-Tuple To Object

### 느낀점
	저번 Readonly를 응용하니 쉬웠다

### 질문
	배열(튜플)을 받아, 각 원소의 값을 key/value로 갖는 오브젝트 타입을 반환하는 타입을 구현하세요.

### 해답
```javascript
	type PropertyKey = string | number
	type TupleToObject<T extends readonly PropertyKey[]> = {[key in T[number]]: key}

	/* _____________ 예시 _____________ */
	const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const

	type result = TupleToObject<typeof tuple> // expected { 'tesla': 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
```

### 참고
https://medium.com/harrythegreat/typescript-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0-%ED%81%B4%EB%9E%98%EC%8A%A4-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-7ae8a786fb20