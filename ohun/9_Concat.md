```ts
/* _____________ Your Code Here _____________ */
type Concat<T extends unknown[], U extends unknown[]> = [...T, ...U]

/* _____________ Test Cases _____________ */
type Result = Concat<[1], [2]> // expected to be [1, 2]

```

# 설명

Spread Operator

Result

    [...T, ...U]
