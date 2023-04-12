```ts
/* _____________ Your Code Here _____________ */
type If<C extends boolean, T, F> = C extends true ? T : F;

/* _____________ Test Cases _____________ */
type A = If<true, 'a', 'b'>  // expected to be 'a'
type B = If<false, 'a', 'b'> // expected to be 'b'


```

# 설명
조건 C를 받아서 참일 경우에는 T를 반환하고 거짓일 경우에는 F를 반환하는 유틸리티 타입 If를 구현해보세요.
C는 true 또는 false일 것이 기대되고, T와 F는 어떤 타입이든 괜찮습니다.

Conditional Types

Result

    C extends true ? T : F;
