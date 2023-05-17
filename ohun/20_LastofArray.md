```ts
/* _____________ Your Code Here _____________ */
type Last<T extends any[]> = [any, ...T][T['length']];
type Last<T extends any[]> = T extends [...infer O, infer L] ? L : never;

/* _____________ Test Cases _____________ */
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type tail1 = Last<arr1> // expected to be 'c'
type tail2 = Last<arr2> // expected to be 1


```

# 설명
    T['length'] T[0]
    [infer O, ...infer L] 첫번째요소가 O
    [...infer O, infer L] 마지막요소가 L
