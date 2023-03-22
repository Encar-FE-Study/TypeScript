# 7 - Readonly
-------
by Anthony Fu (@antfu) #쉬움 #built-in #readonly #object-keys

### 질문

`T`의 모든 프로퍼티를 읽기 전용(재할당 불가)으로 바꾸는 내장 제네릭 `Readonly<T>`를 이를 사용하지 않고 구현하세요.

예시:

  ```ts
  interface Todo {
    title: string
    description: string
  }

  const todo: MyReadonly<Todo> = {
    title: "Hey",
    description: "foobar"
  }

  todo.title = "Hello" // Error: cannot reassign a readonly property
  todo.description = "barFoo" // Error: cannot reassign a readonly property
  ```

> GitHub에서 보기: https://tsch.js.org/7/ko


/* _____________ Your Code Here _____________ */
```ts
type MyReadonly<T> = {
	readonly[K in keyof T] : T[K]
}
```
### 정리
* 제네릭 제약조건에서 타입 매개변수 사용 (Using Type Parameters in Generic Constraints)
* Mapped type을 이용하여 같은 결과를 구현
* in 으로 반복하여 T의 각 key에 해당하는 타입을 타입으로 지정  
* Partial, Pick, Record
