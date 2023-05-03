```
type MyOmit<T, K extends keyof T> = {
  [P in keyof T as P extends K ? never : P]: T[P]
}

type MyReadonly2<T, K extends keyof T> = MyOmit<T, K> & {
  readonly [P in K]: T[P]
}
```