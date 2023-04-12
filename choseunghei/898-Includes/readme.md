# 898-Includes

### 질문
	JavaScript의 Array.includes 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, true 또는 false를 반환해야 합니다.

### 풀이
	1. T를 첫번째 값 First 나머지 값으로 분리
	2. Equal을 사용해 First와 U(검색값)이 같은지 확인
	3. 같다면 true 반환해 루프 탈출
	4. 같지 않다면 Last에 해당하는 값을 다시 First와 나머지로 분리해 1~3 다시 수행
	5. 끝까지 다 돌았다면(분해불가) 같은 값이 없으므로 false

### 해답
```javascript
	type Includes<T extends readonly any[], U> = T extends [infer First, ...infer Last] ? 
    Equal<U, First> extends true ? 
        true :
        Includes<Last, U> :
    false

	/* _____________ 예시 _____________ */
	type isPillarMen = Includes<['Kars', 'Esidisi', 'Wamuu', 'Santana'], 'Dio'> // expected to be `false`
```