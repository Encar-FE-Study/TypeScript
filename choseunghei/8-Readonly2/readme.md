# 8-Readonly2

### 질문
	T에서 K 프로퍼티만 읽기 전용으로 설정해 새로운 오브젝트 타입을 만드는 제네릭 MyReadonly2<T, K>를 구현하세요. K가 주어지지 않으면 단순히 Readonly<T>처럼 모든 프로퍼티를 읽기 전용으로 설정해야 합니다.

### 풀이
	1. MyReadonly2가 가지는 T, K 유니온 타입에서 제거하려는 K를 T의 key 값으로 한정한다. 이때 T가 없는 경우엔 모든 T 임을 명시한다.
	2. K에 지정되지 않은 속성은 Readonly가 되면 안되므로 Omit으로 분리한다
	3. Pick으로 Readonly가 되어야하는 속성들을 분리하고 이를 Readonly를 사용해서 읽기전용 속성으로 만들어준다.
	4. 2와 3에서 만들어준 속성들을 & 연산자로 교차시켜서 MyReadonly2를 완성한다.

### 해답
```javascript
	type MyReadonly2<T, K extends keyof T = keyof T> = Omit<T,K> & Readonly<Pick<T,K>>

	/* _____________ 예시 _____________ */
	interface Todo {
		title: string
		description: string
		completed: boolean
	}

	const todo: MyReadonly2<Todo, 'title' | 'description'> = {
		title: "Hey",
		description: "foobar",
		completed: false,
	}

	todo.title = "Hello" // Error: cannot reassign a readonly property
	todo.description = "barFoo" // Error: cannot reassign a readonly property
	todo.completed = true // OK

```