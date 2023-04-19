```ts
/* _____________ Your Code Here _____________ */
type Unshift<T extends any[], U> = [U, ...T]


/* _____________ Test Cases _____________ */
type Result = Unshift<[1, 2], 0> // [0, 1, 2,]


```

# 설명

Spread Operator

