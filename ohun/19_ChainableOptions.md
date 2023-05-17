```ts
/* _____________ Your Code Here _____________ */
type Chainable<T = {}> = {
    option: <K extends string, V>(
        key: K extends keyof T ? never : K,
        value: V
      ) => Chainable<Omit<T, K> & Record<K, V>>;
    get: () => T;
}


/* _____________ Test Cases _____________ */
declare const config: Chainable

const result = config
  .option('foo', 123)
  .option('name', 'type-challenges')
  .option('bar', { value: 'Hello World' })
  .get()

// 결과는 다음과 같습니다:
interface Result {
  foo: number
  name: string
  bar: {
    value: string
  }
}


```

# 설명
option 제네릭 설정, key value 설정
반환, 재귀로 기록
omit으로 나중 입력된 제외



