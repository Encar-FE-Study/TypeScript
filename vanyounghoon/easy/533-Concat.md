# Concat

JavaScript의 Array.concat 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, 인수를 왼쪽부터 concat한 새로운 배열을 반환해야 합니다.

예시 :

```ts
type Result = Concat<[1], [2]> // expected to be [1, 2]
```

해답 :

```ts
type Concat<T extends any[], U extends any[]> = [...T, ...U]
```

테스트 케이스
```ts
type cases = [
  Expect<Equal<Concat<[], []>, []>>,
  Expect<Equal<Concat<[], [1]>, [1]>>,
  Expect<Equal<Concat<[1, 2], [3, 4]>, [1, 2, 3, 4]>>,
  Expect<Equal<Concat<['1', 2, '3'], [false, boolean, '4']>, ['1', 2, '3', false, boolean, '4']>>,
]
```

활용 사례 :

정리 :

-

참고자료 :
