189 - Awaited
-------
by Maciej Sikora (@maciejsikora) #쉬움 #promise #built-in

### 질문

Promise와 같은 타입에 감싸인 타입이 있을 때, 안에 감싸인 타입이 무엇인지 어떻게 알 수 있을까요?

예시: 들어 `Promise<ExampleType>`이 있을 때, `ExampleType`을 어떻게 얻을 수 있을까요?

  ```ts
  type ExampleType = Promise<string>

  type Result = MyAwaited<ExampleType> // string
  ```



/* _____________ 여기에 코드 입력 _____________ */

```ts

type MyAwaited<T extends PromiseLike<any>> =
	T extends PromiseLike<infer R> ?
		R extends PromiseLike<any> ? MyAwaited<R> : R : never;

type MyAwaited2<T extends PromiseLike<any>> =
	T extends PromiseLike<infer PromiseType>
		? Awaited<PromiseType>
		: T
```

### 정리
* T는 any 타입을 리턴하는 PromiseLike 형태이다 라는 뜻
* 조건 1. T extends PromiseLike<infer R> ? : 만약 T가 R이라는 타입을 리턴 타입으로 가지는 PromiseLike 이라면
* 조건 2. R extends PromiseLike<any> ? : 만약 R이 PromiseLike<any> 타입이라면 (재귀 형태를 띄기 때문에 R을 PromiseLike<any>로 추론하게 하려면 이런 조건이 들어가야한다)
