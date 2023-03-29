```ts
/* _____________ Your Code Here _____________ */
type MyExclude<T, U> = T extends U ? never : T;

/* _____________ Test Cases _____________ */
type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'

```

# 설명

Javascript
```javascript
[1,2,3,4].filter(x => x != 2)
```

Distributive Conditional Types



Result

    U ? never : T;
