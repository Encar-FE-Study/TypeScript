```ts
/* _____________ Your Code Here _____________ */

type First<T extends any[]> = T extends [] ? never : T[0]

/* _____________ Test Cases _____________ */
type arr1 = ['a', 'b', 'c']
type arr2 = [3, 2, 1]

type head1 = First<arr1> // expected to be 'a'
type head2 = First<arr2> // expected to be 3
```

# 설명

Javascript
```javascript
T.length === 0 ? null : T[0]
```

Indexed Types

    T[number] T[0]

Conditional Types

- 삼항연산자..와 같네

Result

    T[0]
    //빈배열체크
    T['length'] extends 0 ? never : T[0]
    T[number] extends [] ? never : T[0]
    T extends [] ? never : T[0]
