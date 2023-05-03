# Omit

### 질문

T에서 K 프로퍼티만 제거해 새로운 오브젝트 타입을 만드는 내장 제네릭 Omit<T, K>를 이를 사용하지 않고 구현하세요.

예시:

```ts
interface Todo {
	title: string;
	description: string;
	completed: boolean;
}

type TodoPreview = MyOmit<Todo, "description" | "title">;

const todo: TodoPreview = {
	completed: false,
};
```

답:

```ts
type MyOmit<T, K extends keyof T> = {
	[P in keyof T as P extends K ? never : P]: T[P];
};
```

풀이:

1. keyof T는 T 타입의 속성 이름들을 유니온 타입으로 가져옵니다.
2. K extends keyof T는 K가 T의 속성 이름들의 유니온 타입(keyof T)에 포함되는지를 체크합니다. K는 T의 일부 속성 이름을 포함하고 있어야 합니다.
3. P in keyof T는 T의 모든 속성 이름들을 반복(iterate)하면서 새로운 객체의 속성 이름으로 사용합니다.
4. P extends K ? never : P는 P가 K의 일부분이면 never(존재하지 않는 타입)으로 설정하고, 그렇지 않으면 P 자체를 속성 이름으로 설정합니다.
5. T[P]는 T 타입의 속성 값 타입을 가져와서 새로운 객체의 속성 값 타입으로 사용합니다.

키워드:

- keyof 연산자

  keyof T → T의 모든 프로퍼티의 키값을 union 형태로 반환

- Type Assertion (타입 단언 / as)
  타입스크립트가 추론하지 못하는 타입을 as키워드를 통해 명시해주는 것
  https://lakelouise.tistory.com/195

- Omit
