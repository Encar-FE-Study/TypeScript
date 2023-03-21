# Tuple to Object

배열(튜플)을 받아, 각 원소의 값을 key/value로 갖는 오브젝트 타입을 반환하는 타입을 구현하세요.

예시:

```ts
const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const

type result = TupleToObject<typeof tuple> // expected { tesla: 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
```

해답:

```ts
type TupleToObject<T extends readonly string | number | symbol[]> = {
   [key in T[number]] : key
}
```

정리:

- symbol:

활용 사례:

- React에서 불변성을 유지해야하는 Props와 State의 타입 지정
- 변하지 않는 배열의 타입 ex)ReadonlyArray

참고자료:

- https://medium.com/sjk5766/es-6-symbol-%EC%9D%B4%EB%9E%80-48c2ad5b054c

