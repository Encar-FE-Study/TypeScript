# Pick

### 질문

`T`에서 `K` 프로퍼티만 선택해 새로운 오브젝트 타입을 만드는 내장 제네릭 `Pick<T, K>`을 이를 사용하지 않고 구현하세요.

예시:

```ts
interface Todo {
	title: string;
	description: string;
	completed: boolean;
}

type TodoPreview = MyPick<Todo, "title" | "completed">;

const todo: TodoPreview = {
	title: "Clean room",
	completed: false,
};
```

답:

```ts
type MyPick<T, K extends keyof T> = {
	[P in K]: T[P];
};
```

### 정리

- keyof 연산자

  keyof A → A의 모든 프로퍼티의 키값을 union 형태로 반환

```ts
interface Todo {
	id: number;
	text: string;
}

type Keys = keyof Todo;
// === type Keys = 'id' | 'text'

let a: Keys = "id";
a = "text";
a = "ids"; // 🚨ERROR!
a = "id" | "text"; // 🚨ERROR!
```

- Mapped Type (in 연산자)

  기존 타입을 새로운 타입으로 변환

```ts
type Test = "A" | "B" | "C";
type MappedTest = {
	[key in Test]: number;
};
const data: MappedTest = { A: 1, B: 2, C: 3 };
const data1: MappedTest = { A: 1, B: 2 }; // 🚨ERROR!
```

### 참고문헌

https://velog.io/@jiseon-han/typescript-%EA%B0%84%EB%8B%A8-%EC%A0%95%EB%A6%AC-Generic
