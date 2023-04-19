```ts
/* _____________ Your Code Here _____________ */
type Push<T extends any[], U> = [...T, U]


/* _____________ Test Cases _____________ */
type Result = Push<[1, 2], '3'> // [1, 2, '3']


```

# 설명

Spread Operator

