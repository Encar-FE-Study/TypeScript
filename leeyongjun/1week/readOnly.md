# Readonly

### 질문

`T`의 모든 프로퍼티를 읽기 전용(재할당 불가)으로 바꾸는 내장 제네릭 `Readonly<T>`를 이를 사용하지 않고 구현하세요.

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

답:

```ts
type MyReadOnly<T> = {
	readonly [P in keyof T]: T[P];
};
```
