# 9-Deep Readonly

### 질문
	객체의 프로퍼티와 모든 하위 객체를 재귀적으로 읽기 전용으로 설정하는 제네릭 DeepReadonly<T>를 구현하세요.

	이 챌린지에서는 타입 파라미터 T를 객체 타입으로 제한하고 있습니다. 객체뿐만 아니라 배열, 함수, 클래스 등 가능한 다양한 형태의 타입 파라미터를 사용하도록 도전해 보세요.

### 풀이
	1. T 제네릭의 키를 keyof 키워드로 추출하고 in 키워드로 반복한다.
	2. 앞에 readonly를 붙여서 읽기 전용으로 선언
	3. T[k] extends Record<any, any> 현재 속성값이 Reacord(객체)인지 확인
	4. 객체가 아니라면 그대로 리턴
	5. 객체라면 T[k] extends Function 로 함수인지 검증
	6. 함수라면 그대로 리턴
	7. 함수가 아니라면 객체가 더 싸여있단 뜻이니 재귀로 반복
### 해답
```javascript
	type DeepReadonly<T> = {
		readonly [k in keyof T]: T[k] extends Record<any, any>
			? T[k] extends Function
				? T[k]
				: DeepReadonly<T[k]>
			: T[k]
	}

	/* _____________ 예시 _____________ */
	type X = { 
		x: { 
			a: 1
			b: 'hi'
		}
		y: 'hey'
	}

	type Expected = { 
		readonly x: { 
			readonly a: 1
			readonly b: 'hi'
		}
		readonly y: 'hey' 
	}

		type Todo = DeepReadonly<X> // should be same as `Expected`
```