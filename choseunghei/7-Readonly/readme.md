# 7-readonly

### 느낀점
	readonly operator를 몰라서 헤맸음.

### 질문
	T`의 모든 프로퍼티를 읽기 전용(재할당 불가)으로 바꾸는 내장 제네릭 `Readonly<T>`를 이를 사용하지 않고 구현하세요.

### 해답
```javascript
	type MyReadonly<T> = { readonly [P in keyof T] : T[P]};

	/* _____________ 예시 _____________ */
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

	/* _____________ 테스트 케이스 _____________ */
	import type { Equal, Expect } from '@type-challenges/utils'

	type cases = [
		Expect<Equal<MyReadonly<Todo1>, Readonly<Todo1>>>,
	]

	interface Todo1 {
		title: string
		description: string
		completed: boolean
		meta: {
			author: string
		}
	}
```

### 참고
https://medium.com/harrythegreat/typescript-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0-%ED%81%B4%EB%9E%98%EC%8A%A4-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-7ae8a786fb20