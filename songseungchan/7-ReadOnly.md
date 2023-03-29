답
```
type MyReadonly<T> = { 
  readonly [K in keyof T] : T[K]
}
```
삽질했던 것 -> extends를 붙여서 실행했음
extends붙이면 왜 안되지? in 오른쪽에 유니언타입이 와야 하기에

삽질
```
type MyReadonly<T> = { 
  readonly [K in extends keyof T] : T[K]
}
```