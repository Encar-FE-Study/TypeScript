# 3-Omit

### 질문
	T에서 K 프로퍼티만 제거해 새로운 오브젝트 타입을 만드는 내장 제네릭 Omit<T, K>를 이를 사용하지 않고 구현하세요.

### 풀이
	1. MyOmit이 가지는 T, K 유니온 타입에서 제거하려는 K를 T의 key 값으로 한정한다.
	2. P in keyof T로 T의 모든 속성 P에 대한 맵드 타입을 선언한다.
	3. P가 K인 경우. 즉 제거하려는 속성일때 never를 반환한다. 아닌경우 그대로 P를 내보낸다.
	4. 마지막으로 해당 속성의 타입을 T[P]로 반환해 MyOmit 제네릭을 완성한다.

### 해답
```javascript
	type MyOmit<T, K extends keyof T> = {[P in keyof T as P extends K ? never : P]:T[P]}

	/* _____________ 예시 _____________ */
	interface Todo {
		title: string
		description: string
		completed: boolean
	}

	type TodoPreview = MyOmit<Todo, 'description' | 'title'>

	const todo: TodoPreview = {
		completed: false,
	}

```