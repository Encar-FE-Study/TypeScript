# Deep Readonly

### 질문

객체의 프로퍼티와 모든 하위 객체를 재귀적으로 읽기 전용으로 설정하는 제네릭 DeepReadonly<T>를 구현하세요.

이 챌린지에서는 타입 파라미터 T를 객체 타입으로 제한하고 있습니다. 객체뿐만 아니라 배열, 함수, 클래스 등 가능한 다양한 형태의 타입 파라미터를 사용하도록 도전해 보세요.

예시:

```ts
type X = {
	x: {
		a: 1;
		b: "hi";
	};
	y: "hey";
};

type Expected = {
	readonly x: {
		readonly a: 1;
		readonly b: "hi";
	};
	readonly y: "hey";
};

type Todo = DeepReadonly<X>; // should be same as `Expected`
```

답:

```ts
type DeepReadonly<T> = {
	readonly [key in keyof T]: keyof T[key] extends never
		? T[key]
		: DeepReadonly<T[key]>;
};
```
