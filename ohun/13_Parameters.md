```ts
/* _____________ Your Code Here _____________ */
type MyParameters<T extends (...args: any[]) => any> =
  T extends (...args: [...infer P]) => any ? P : never;


/* _____________ Test Cases _____________ */
const foo = (arg1: string, arg2: number): void => {}

type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]


```

# 설명
함수타입
args
infer로 args의 타입을 추론

