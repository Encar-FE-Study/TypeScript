type MyPick<T, Keys extends keyof T> = { [newKey in Keys] : T[newKey] }



keyof T = A | B |C 
Keys extends A | B |C   => A | B |C 
in => for in과 유사, 순서대로 순회


알게 된 것

조건부 연산자 
- 3항 연산자 같이 사용
- 유틸리티 타입 구현시 종종 쓴다.

헷갈리는 것 
extends의 사용
- interface / class 상속
- 조건부 연산

A extends B일때
A 가 B의 부분집합이어야 하는지

ex1)

interface StringContainer {
    value : string;
    split() : string []
    ...
}

interface NumberContainer {
    value: number;
    round() :number;
    ...
}

ex2)
type Item3<T> = {
 id : T extends string | number ? T : never
 container : T extends string
    ? StringContainer
    : T extends number 
    ? NumberContainer
    : never
}
const item3 : Item<boolean> = { 
  id: true // Type 'boolean' is not assignable to type 'never'
  container : null, // Type 'null' is not assignable to type 'never'
}



type ArrayFilter<T> = T extends any [] ? T : never;
type StringOrNumber = ArrayFilter<string | number | string [] | number [] >

결과
1. string | number | string [] | number []
2. never | never | string [] | number []
3. string [] | number []

ex3)

type Exclude<T,U> = T extends U ? never : T

type Fruit = "cherry" | "banana" | "strawberry" | "lemon";

type RedFruit = Exclude<Fruit, "banana" | "lemon">;  => "cherry" | "strawberry"


참조
https://www.typescriptlang.org/ko/docs/handbook/2/conditional-types.html
https://chanhuiseok.github.io/posts/ts-3/