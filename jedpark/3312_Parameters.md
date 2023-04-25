
3312 - Parameters
-------
by midorizemi (@midorizemi) #쉬움 #infer #tuple #built-in

### 질문

내장 제네릭 `Parameters<T>`를 이를 사용하지 않고 구현하세요.

예시:

  ```ts
  const foo = (arg1: string, arg2: number): void => {}

  type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]
  ```

> GitHub에서 보기: https://tsch.js.org/3312/ko


/* _____________ 여기에 코드 입력 _____________ */
```ts
// type MyParameters<T extends (...args: any[]) => any> = []
// type MyParameters<T extends (...args: any[]) => any> = T extends () => any ? [] : never;
type MyParameters<T extends (...args: any[]) => any> = T extends (...args : infer Param) => any ? [...Param] : never;
type MyParameters<T extends (...args: any[]) => any> = T extends (...args : infer Param) => any ? Param : never;
type MyParameters<T extends (...args: any[]) => any> = T extends (...args : infer Param) => any 
    ? {[p in keyof Param]: Param[p]} 
    : never;

```

### 정리
* 내장유틸 Parameters 는 함수타입 T의 매개변수를 튜플타입으로 구성
```ts
declare function f1(arg: { a: number, b: string }): void
type T0 = Parameters<() => string>;  // []
type T1 = Parameters<(s: string) => void>;  // [string]
type T2 = Parameters<(<T>(arg: T) => T)>;  // [unknown]
type T4 = Parameters<typeof f1>;  // [{ a: number, b: string }]
type T5 = Parameters<any>;  // unknown[]
type T6 = Parameters<never>;  // never
type T7 = Parameters<string>;  // 오류
type T8 = Parameters<Function>;  // 오류
```
* 함수의 인자들을 튜플로 전달할때
```ts
const myFunction = (a: string, b: string) => {
    return a + b;
}

let passArray:[string, string] = [ 'hello ', 'world' ]

// Returns 'hello world'
myFunction(...passArray);
```
* myFunction이 인자 조건이 바뀌거나 타사 함수들을 사용할때 싱크해줘야하는 문제를 해결할 수 있음
* 인자들의 튜플 유형이 생성됨
```ts
const myFunction = (a: string, b: string) => {
    return a + b;
}

type myType = Parameters<typeof myFunction>

let myArray:myType = [ 'hello ', 'world' ];

myFunction(...myArray)
```
