
3312 - Parameters
-------
by midorizemi (@midorizemi) #���� #infer #tuple #built-in

### ����

���� ���׸� `Parameters<T>`�� �̸� ������� �ʰ� �����ϼ���.

����:

  ```ts
  const foo = (arg1: string, arg2: number): void => {}

  type FunctionParamsType = MyParameters<typeof foo> // [arg1: string, arg2: number]
  ```

> GitHub���� ����: https://tsch.js.org/3312/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
// type MyParameters<T extends (...args: any[]) => any> = []
// type MyParameters<T extends (...args: any[]) => any> = T extends () => any ? [] : never;
type MyParameters<T extends (...args: any[]) => any> = T extends (...args : infer Param) => any ? [...Param] : never;
type MyParameters<T extends (...args: any[]) => any> = T extends (...args : infer Param) => any ? Param : never;
type MyParameters<T extends (...args: any[]) => any> = T extends (...args : infer Param) => any 
    ? {[p in keyof Param]: Param[p]} 
    : never;

```

### ����
* ������ƿ Parameters �� �Լ�Ÿ�� T�� �Ű������� Ʃ��Ÿ������ ����
```ts
declare function f1(arg: { a: number, b: string }): void
type T0 = Parameters<() => string>;  // []
type T1 = Parameters<(s: string) => void>;  // [string]
type T2 = Parameters<(<T>(arg: T) => T)>;  // [unknown]
type T4 = Parameters<typeof f1>;  // [{ a: number, b: string }]
type T5 = Parameters<any>;  // unknown[]
type T6 = Parameters<never>;  // never
type T7 = Parameters<string>;  // ����
type T8 = Parameters<Function>;  // ����
```
* �Լ��� ���ڵ��� Ʃ�÷� �����Ҷ�
```ts
const myFunction = (a: string, b: string) => {
    return a + b;
}

let passArray:[string, string] = [ 'hello ', 'world' ]

// Returns 'hello world'
myFunction(...passArray);
```
* myFunction�� ���� ������ �ٲ�ų� Ÿ�� �Լ����� ����Ҷ� ��ũ������ϴ� ������ �ذ��� �� ����
* ���ڵ��� Ʃ�� ������ ������
```ts
const myFunction = (a: string, b: string) => {
    return a + b;
}

type myType = Parameters<typeof myFunction>

let myArray:myType = [ 'hello ', 'world' ];

myFunction(...myArray)
```
