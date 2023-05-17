```ts
/* _____________ Your Code Here _____________ */
type Pop<T extends any[]> = T extends [...infer O, infer L] ? O : never;


/* _____________ Test Cases _____________ */
type arr1 = ['a', 'b', 'c', 'd']
type arr2 = [3, 2, 1]

type re1 = Pop<arr1> // expected to be ['a', 'b', 'c']
type re2 = Pop<arr2> // expected to be [3, 2]


```

# 설명
    [infer O, ...infer L] 첫번째요소가 O
    [...infer O, infer L] 마지막요소가 L
