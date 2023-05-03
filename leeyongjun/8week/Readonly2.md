# Readonly 2

### 질문

T에서 K 프로퍼티만 읽기 전용으로 설정해 새로운 오브젝트 타입을 만드는 제네릭 MyReadonly2<T, K>를 구현하세요. K가 주어지지 않으면 단순히 Readonly<T>처럼 모든 프로퍼티를 읽기 전용으로 설정해야 합니다.

예시:

```ts
interface Todo {
	title: string;
	description: string;
	completed: boolean;
}

const todo: MyReadonly2<Todo, "title" | "description"> = {
	title: "Hey",
	description: "foobar",
	completed: false,
};

todo.title = "Hello"; // Error: cannot reassign a readonly property
todo.description = "barFoo"; // Error: cannot reassign a readonly property
todo.completed = true; // OK
```

답:

```ts
type MyReadonly2<T, K extends keyof T = keyof T> = {
	readonly [P in K]: T[P];
} & Omit<T, K>;
```

풀이:

1. K가 지정되지 않으면 keyof T가 기본값으로 사용됩니다. (첫번째 test case)
2. K extends keyof T는 K가 T의 속성 이름들의 유니온 타입(keyof T)에 포함되는지를 체크합니다.
3. [P in K]: T[P];는 K에 속한 모든 속성을 읽기 전용으로 만듭니다.
4. Omit<T, K>는 T에서 K에 속한 속성 이름들을 제외한 객체 타입을 생성합니다.

- 키워드

1. readonly는 TypeScript에서 변수나 프로퍼티를 읽기 전용으로 정의할 때 사용하는 키워드입니다.
   ex)

```ts
interface Person {
	readonly name: string;
	readonly age: number;
}

const person: Person = { name: "Alice", age: 30 };
person.name = "Bob"; // 컴파일 에러!
```

2. ReadOnly는 TypeScript에서 타입 유틸리티 중 하나로, 객체의 모든 프로퍼티를 읽기 전용으로 변경하는 역할을 합니다.

```ts
type ReadonlyPerson = Readonly<Person>;

const readonlyPerson: ReadonlyPerson = { name: "Alice", age: 30 };
readonlyPerson.name = "Bob"; // 컴파일 에러!
```

3. Intersection Type (&)
   인터섹션 타입(Intersection Type)은 여러 타입을 모두 만족하는 하나의 타입을 의미합니다

```ts
interface Person {
	name: string;
	age: number;
}
interface Developer {
	name: string;
	skill: number;
}
type Capt = Person & Developer;

// Capt

{
	name: string;
	age: number;
	skill: string;
}
```
