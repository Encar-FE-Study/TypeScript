# 189-Awaited

### 질문
	Promise와 같은 타입에 감싸인 타입이 있을 때, 안에 감싸인 타입이 무엇인지 어떻게 알 수 있을까요?
	예시: 들어 Promise<ExampleType>이 있을 때, ExampleType을 어떻게 얻을 수 있을까요?

### 풀이
	1. Promise 객체가 아니면 오류를 뱉어야함. 따라서 T extends PromiseLike<any>
	2. Promise의 제네릭 타입 P를 추론한다. T가 Promise 타입인지 판단후 P를 추론하는데, T가 Promise라면 내부의 P가 또 Promise로 감싸져있는지 확인한다. 
	3. 내부가 또 Promise라면 재귀적으로 Type 을 또 호출해서 1,2를 반복한다.
	4. Promise가 아니라면 T를 뱉어준다.

	cf) TC 중에 Promise객체가 아닌게 있어서 PromiseLike로 풀이함.

### 해답
```javascript
	type MyAwaited<T extends PromiseLike<any>> = T extends PromiseLike<infer P>
	? P extends PromiseLike<any>
		? MyAwaited<P>
		: P
	: T;

	/* _____________ 예시 _____________ */
	type ExampleType = Promise<string>
	type Result = MyAwaited<ExampleType> // string
```

### 참고
https://egg-programmer.tistory.com/307