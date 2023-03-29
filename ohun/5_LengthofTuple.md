```ts
/* _____________ Your Code Here _____________ */
type Length<T extends readonly any[]> = T['length']

/* _____________ Test Cases _____________ */
type tesla = ['tesla', 'model 3', 'model X', 'model Y']
type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

type teslaLength = Length<tesla>  // expected 4
type spaceXLength = Length<spaceX> // expected 5

```

# 설명

Javascript
```javascript
T.length
```

Indexed Types

    T[number] T[0] T['length']

Result

    T['length']
