# Readonly

T의 모든 프로퍼티를 읽기 전용(재할당 불가)으로 바꾸는 내장 제네릭 Readonly<T>를 이를 사용하지 않고 구현하세요.

예시:

```ts
interface Todo {
  title: string;
  description: string;
}

const todo: MyReadonly<Todo> = {
  title: "Hey",
  description: "foobar",
};

todo.title = "Hello"; // Error: cannot reassign a readonly property
todo.description = "barFoo"; // Error: cannot reassign a readonly property
```

해답:

```ts
type MyReadonly<T> = {
  readonly [key in T]: T[key];
};
```

활용 사례:

- React에서 불변성을 유지해야하는 Props와 State의 타입 지정
- 변하지 않는 배열의 타입 ex)ReadonlyArray

참고자료:

- https://radlohead.gitbook.io/typescript-deep-dive/type-system/readonly
