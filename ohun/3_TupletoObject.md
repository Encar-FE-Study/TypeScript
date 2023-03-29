```ts
/* _____________ Your Code Here _____________ */

type TupleToObject<T extends readonly any[]> = {
  [K in T[number]]: K
}

/* _____________ Test Cases _____________ */
const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const

type result = TupleToObject<typeof tuple> // expected { 'tesla': 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
```

# 설명

Javascript
```javascript
function test(T) {
    let X = {};
    for(let K in T) {
        X[T[K]] = T[K];
    }
    return X;
}
```
Const Assertion

    ['tesla', 'model 3', 'model X', 'model Y'] as const

    // readonly ['tesla', 'model 3', 'model X', 'model Y']

- 값을 변경하지 않게 위해 사용


Maped Types

    [K in T]: K

Indexed Types

    T[number] T[0]

Result

    [K in T[number]]: K

    T extends readonly any[]