
```
ex) type Result = MyExclude<"a" | "b" | "c", "a">; // 'b' | 'c'

type MyExclude<T, U> = T extends U ? never : T
```

=> T가 U에 할당될 수 있다면(부분집합)이라면 제외 아니라면 해당 값 그대로 사용

```
MyExclude<"a" | "b" | "c", "d">; // 'a' | 'b' | 'c' 
```
