```ts
/* _____________ Your Code Here _____________ */

type MyAwaited<T extends Promise<any>> = T extends Promise<infer A> ? A : never;

/* _____________ Test Cases _____________ */
type ExampleType = Promise<string>
type Result = MyAwaited<ExampleType> // string

```

# 설명
Promise<string>을 인자로 받을 경우 언래핑을 통해 string 타입을 반환하고, Promise가 아닌 경우에는 T를 반환


Conditional Types

Result

    T extends Promise<infer A> ? A : never;
