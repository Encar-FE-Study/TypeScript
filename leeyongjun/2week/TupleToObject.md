# Tuple to Object

### 질문

배열(튜플)을 받아, 각 원소의 값을 key/value로 갖는 오브젝트 타입을 반환하는 타입을 구현하세요.

예시:

```ts
const tuple = ["tesla", "model 3", "model X", "model Y"] as const;

type result = TupleToObject<typeof tuple>; // expected { tesla: 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
```

답:

```ts
type typeofKeys = string | number;

type TupleToObject<T extends readonly typeofKeys[]> = {
	[K in T[number]]: K;
};
```

### 참고

제네릭 제약 조건
https://velog.io/@holicholicpop/Typescript-11.-Generic%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4-%EC%9E%91%EC%97%85T-extends-something-%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%A0%9C%EB%84%A4%EB%A6%AD
