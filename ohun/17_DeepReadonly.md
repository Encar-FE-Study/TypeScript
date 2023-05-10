```ts
/* _____________ Your Code Here _____________ */
type DeepReadonly<T> = {
  readonly [P in keyof T] : keyof T[P] extends never ? T[P] : DeepReadonly<T[P]>
}


/* _____________ Test Cases _____________ */
type X = {
  x: {
    a: 1
    b: 'hi'
  }
  y: 'hey'
}

type Expected = {
  readonly x: {
    readonly a: 1
    readonly b: 'hi'
  }
  readonly y: 'hey'
}

type Todo = DeepReadonly<X> // should be same as `Expected`


```

# 설명

readonly: 읽기전용

keyof: 타입지정

in: 찾기

+

재귀

