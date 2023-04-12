# Awaited

### 질문

Promise와 같은 타입에 감싸인 타입이 있을 때, 안에 감싸인 타입이 무엇인지 어떻게 알 수 있을까요?

예시: 들어 Promise<ExampleType>이 있을 때, ExampleType을 어떻게 얻을 수 있을까요?

예시:

```ts
type ExampleType = Promise<string>;

type Result = MyAwaited<ExampleType>; // string
```

답:

```ts
type MyAwaited<T extends PromiseLike<any>> = T extends PromiseLike<infer P>
	? P extends PromiseLike<any>
		? MyAwaited<P>
		: P
	: T;
```
