# 12-Chainable Options

### 질문
	체인 가능 옵션은 일반적으로 Javascript에서 사용됩니다. 하지만 TypeScript로 전환하면 제대로 구현할 수 있나요?

	이 챌린지에서는 option(key, value)과 get() 두가지 함수를 제공하는 객체(또는 클래스) 타입을 구현해야 합니다. 현재 타입을 option으로 지정된 키와 값으로 확장할 수 있고 get으로 최종 결과를 가져올 수 있어야 합니다.
	문제를 해결하기 위해 js/ts 로직을 작성할 필요는 없습니다. 단지 타입 수준입니다.

	key는 string만 허용하고 value는 무엇이든 될 수 있다고 가정합니다. 같은 key는 두 번 전달되지 않습니다.

### 풀이
	1. Chainable 타입에 각각 option, get 메소드를 선언한다.
	2. option은 2개의 유니온 타입을 받는다. K는 키값으로 string만 가능하기 때문에 extends로 제한하고, V는 무엇이는 가능하니 그대로 둔다.
	3. 같은 키인지 확인하기 위한 작업을 한다. key에 해당하는 K가 T의 key집합에 속하는지 체크한다. 만약 key값이 맞다면 never로 제거해서 동일키가 없도록한다.
	4. K가 T의 Key가 아니라면 K를 그대로 넣어주고 value로 V를 가진다.
	5. 이 함수는 새로생성할 K를 제외한 T 객체(Omit), 새로 생성할 K를 키로 가지고 V를 값으로 가지는 객체(Record)를 함께 병합하여 새로운 Chainable 객체를 반환한다.
	6. 마지막으로 get 메소드는 전체 T 객체를 반환해준다.
### 해답
```javascript
	type Chainable<T = {}> = {
    option: <K extends string, V>(
        key: K extends keyof T ? never : K,
        value: V
      ) => Chainable<Omit<T, K> & Record<K, V>>;
    get: () => T;
};

	/* _____________ 예시 _____________ */
	declare const config: Chainable

	const result = config
	.option('foo', 123)
	.option('name', 'type-challenges')
	.option('bar', { value: 'Hello World' })
	.get()

	// 결과는 다음과 같습니다:
	interface Result {
		foo: number
		name: string
		bar: {
			value: string
		}
	}
```