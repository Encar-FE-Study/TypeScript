# 898-Includes

### 질문
	내장 제네릭 ReturnType<T>을 이를 사용하지 않고 구현하세요.

### 풀이
	1. T extends Function으로 T의 타입을 함수로 한정
	2. T extends (...args: any) => infer R는 T(함수)가 ...args(가변갯수) 매개변수를 받는 함수이며 그 return값을 R로 추론한다는 의미
	3. 마지막으로 삼항 연산자를 통해 값이 맞다면 R(return값)을 그대로 반환. 아니라면 never로 반환하지 않음.

### 해답
```javascript
	type MyReturnType<T extends Function> = T extends (...args: any) => infer R
    	? R
    	: never

	/* _____________ 예시 _____________ */
	const fn = (v: boolean) => {
		if (v)
			return 1
		else
			return 2
	}

	type a = MyReturnType<typeof fn> // should be "1 | 2"

```