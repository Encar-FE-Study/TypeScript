# Exclude

T에서 U에 할당할 수 있는 타입을 제외하는 내장 제네릭 Exclude<T, U>를 이를 사용하지 않고 구현하세요.

예시 :

```ts
type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'

```

해답 :

```ts
type MyExclude<T, U> = T extends U ? never : T;
```

활용 사례 :

정리 :

-

참고자료 :
- https://nickangeli.com/posts/typescript-type-challenge-exclude-walkthrough/