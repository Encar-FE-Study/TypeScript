# Includes

### 질문

JavaScript의 Array.includes 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, true 또는 false를 반환해야 합니다.

예시:

```ts
type isPillarMen = Includes<["Kars", "Esidisi", "Wamuu", "Santana"], "Dio">; // expected to be `false`
```

답:

```ts
type Includes<T extends readonly any[], U> = T extends [
	infer First,
	...infer Rest
]
	? Equal<First, U> extends true
		? true
		: Includes<Rest, U>
	: false;
```
