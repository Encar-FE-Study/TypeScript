```ts
/* _____________ Your Code Here _____________ */
type Includes<T extends readonly unknown[], U> =
  T extends [infer First, ...infer Rest]
    ? Equal<First, U> extends true
      ? true
      : Includes<Rest, U>
    : false

/* _____________ Test Cases _____________ */
type isPillarMen = Includes<['Kars', 'Esidisi', 'Wamuu', 'Santana'], 'Dio'> // expected to be `false`


```

# 설명

Index Types, keyof

Result
ㅌ3
