# Awaited

Promise와 같은 타입에 감싸인 타입이 있을 때, 안에 감싸인 타입이 무엇인지 어떻게 알 수 있을까요?
예시: 들어 Promise<ExampleType>이 있을 때, ExampleType을 어떻게 얻을 수 있을까요?

예시 :

```ts
type ExampleType = Promise<string>

type Result = MyAwaited<ExampleType> // string
```

해답 :

```ts
type MyAwaited<T extends PromiseLike<unknown>> = T extends PromiseLike<infer R> ? Awaited<R> : T;
type MyAwaited<T> = T extends PromiseLike<infer R> ? MyAwaited<R> : T;

type MyAwaited<T extends Promise<unknown>> = T extends Promise<infer R>
  ? R extends Promise<unknown>
    ? MyAwaited<R>
    : R
  : never;
```

활용 사례 :

정리 :

-

참고자료 :

- https://github.com/type-challenges/type-challenges/issues/25231
- https://github.com/type-challenges/type-challenges/issues/23633