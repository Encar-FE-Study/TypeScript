```ts
/* _____________ Your Code Here _____________ */
type TupleToUnion<T extends any[]> = T[number];


/* _____________ Test Cases _____________ */
type Arr = ['1', '2', '3']

type Test = TupleToUnion<Arr> // expected to be '1' | '2' | '3'


```

# 설명
Indexed Types

    T[number] T[0]
