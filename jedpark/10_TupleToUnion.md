
10 - Tuple to Union
-------
by Anthony Fu (@antfu) #보통 #infer #tuple #union

### 질문

튜플 값으로 유니온 타입을 생성하는 제네릭 `TupleToUnion<T>`를 구현하세요.

예시:

  ```ts
  type Arr = ['1', '2', '3']

  type Test = TupleToUnion<Arr> // expected to be '1' | '2' | '3'
  ```

> GitHub에서 보기: https://tsch.js.org/10/ko


/* _____________ 여기에 코드 입력 _____________ */
```ts
type TupleToUnion<T> = T extends Array<infer K> ? K : never;
type TupleToUnion<T extends ArrayLike<any>> = T extends [infer F, ...infer Last] ? TupleToUnion<Last> | F : never

```

### 정리
* 
