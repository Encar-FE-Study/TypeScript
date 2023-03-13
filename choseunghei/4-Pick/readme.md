# 4-pick

### 느낀점
	처음 하는거라서 얼타느라 시간을 많이보냄.   
	Pick의 원형을 구현하는 문제. 그냥 무심코 썻던 내장 제네릭을 실제로 구현하니 좀 더 이해의 범위가 넓어진거 같음.

### 질문
	`T`에서 `K` 프로퍼티만 선택해 새로운 오브젝트 타입을 만드는 내장 제네릭 `Pick<T, K>`을 이를 사용하지 않고 구현하세요.

### 해답
```javascript
	type MyPick<T, K extends keyof T> = {
  		[P in K]: T[P]
	}

	/* _____________ 예시 _____________ */
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

	/* _____________ 테스트 케이스 _____________ */
	import type { Equal, Expect } from '@type-challenges/utils'

	type cases = [
		Expect<Equal<Expected1, MyPick<Todo, 'title'>>>,
		Expect<Equal<Expected2, MyPick<Todo, 'title' | 'completed'>>>,
		// @ts-expect-error
		MyPick<Todo, 'title' | 'completed' | 'invalid'>,
	]

	interface Todo {
		title: string
		description: string
		completed: boolean
	}

	interface Expected1 {
		title: string
	}

	interface Expected2 {
		title: string
		completed: boolean
	}
```

### 설명
	keyof: 타입값에 존재하는 모든 프로퍼티의 키값을 Union 형태로 리턴
	in: 해당 key를 반복하는 iterator

### 참고
https://medium.com/harrythegreat/typescript-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0-%ED%81%B4%EB%9E%98%EC%8A%A4-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0-7ae8a786fb20