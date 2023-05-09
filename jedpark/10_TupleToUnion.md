
10 - Tuple to Union
-------
by Anthony Fu (@antfu) #���� #infer #tuple #union

### ����

Ʃ�� ������ ���Ͽ� Ÿ���� �����ϴ� ���׸� `TupleToUnion<T>`�� �����ϼ���.

����:

  ```ts
  type Arr = ['1', '2', '3']

  type Test = TupleToUnion<Arr> // expected to be '1' | '2' | '3'
  ```

> GitHub���� ����: https://tsch.js.org/10/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
type TupleToUnion<T> = T extends Array<infer K> ? K : never;
type TupleToUnion<T extends ArrayLike<any>> = T extends [infer F, ...infer Last] ? TupleToUnion<Last> | F : never

```

### ����
* 
