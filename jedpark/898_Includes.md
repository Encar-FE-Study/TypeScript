898 - Includes
-------
by null (@kynefuk) #쉬움 #array

### 질문

JavaScript의 `Array.includes` 함수를 타입 시스템에서 구현하세요. 타입은 두 인수를 받고, `true` 또는 `false`를 반환해야 합니다.

예시:

  ```ts
  type isPillarMen = Includes<['Kars', 'Esidisi', 'Wamuu', 'Santana'], 'Dio'> // expected to be `false`
  ```

> GitHub에서 보기: https://tsch.js.org/898/ko
*/

/* _____________ 여기에 코드 입력 _____________ */
```ts
type MyEqual<X, Y> = (<T>() => T extends X ? 1 : 2) extends (<T>() => T extends Y ? 1 : 2) ? true : false;

// type Includes<T extends readonly any[], U> = T extends [...infer O]
// 	? Equal<O, U> extends true
// 		? true
// 		: Includes<O, U>
// 	: false;
type Includes<T extends readonly any[], U> = T extends [infer F, ...infer O]
    ? MyEqual<F, U> extends true
        ? true
        : Includes<O, U>
    : false;

```

### 정리
* 만약 배열에서 첫번? F와 나머지 O로 나뉜다면
* 첫번째 F와 비교할 U가 같은지 MyEqual로 비교하고, false이면 재귀함수로 다음 나머지 O를 비교한다. 
* (왜 infer를 두번써서 나눠야 할까)
