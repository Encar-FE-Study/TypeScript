# Parameters

### 질문

내장 제네릭 Parameters<T>를 이를 사용하지 않고 구현하세요.

예시:

```ts
const foo = (arg1: string, arg2: number): void => {};

type FunctionParamsType = MyParameters<typeof foo>; // [arg1: string, arg2: number]
```

답:

```ts
type MyParameters<T extends (...args: any[]) => any> = T extends (
	...any: infer S
) => any
	? S
	: never;
```

타입추론 infer
