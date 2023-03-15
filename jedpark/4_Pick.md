# 4 - Pick
-------
by Anthony Fu (@antfu) #쉬움 #union #built-in

### 질문

`T`에서 `K` 프로퍼티만 선택해 새로운 오브젝트 타입을 만드는 내장 제네릭 `Pick<T, K>`을 이를 사용하지 않고 구현하세요.

예시:

  ```ts
  interface Todo {
    title: string
    description: string
    completed: boolean
  }

  type TodoPreview = MyPick<Todo, 'title' | 'completed'>

  const todo: TodoPreview = {
      title: 'Clean room',
      completed: false,
  }
  ```

> GitHub에서 보기: https://tsch.js.org/4/ko


/* _____________ Your Code Here _____________ */
```ts
type MyPick<T, Props extends keyof T> = {
    [K in Props] : T[K]
}
```
### 정리
* 제네릭 제약조건에서 타입 매개변수 사용 (Using Type Parameters in Generic Constraints)
* 내장 type인 Pick을 사용하지 않고 Mapped type을 이용하여 같은 결과를 구현
* in 으로 반복하여 T의 각 key에 해당하는 타입을 타입으로 지정  
