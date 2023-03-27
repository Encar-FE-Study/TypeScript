# 14-First Of Array

### 느낀점
	타입스크립트의 인덱스 타입 쿼리 length를 몰라서 헤맸다.
	배열타입이 가진 length 속성을 가지고 오기위해 T['length']와 같이 인덱스타입 쿼리를 사용해 배열 타입의 length 속성을 가져올 수 있다.

### 질문
	배열(튜플)을 받아 길이를 반환하는 제네릭 Length<T>를 구현하세요.

### 해답
```javascript
	type Length<T extends readonly any[]> = T["length"];

	/* _____________ 예시 _____________ */
	type tesla = ['tesla', 'model 3', 'model X', 'model Y']
	type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

	type teslaLength = Length<tesla>  // expected 4
	type spaceXLength = Length<spaceX> // expected 5
```