
9 - Deep Readonly
-------
by Anthony Fu (@antfu) #���� #readonly #object-keys #deep

### ����

��ü�� ������Ƽ�� ��� ���� ��ü�� ��������� �б� �������� �����ϴ� ���׸� `DeepReadonly<T>`�� �����ϼ���.

�� ç���������� Ÿ�� �Ķ���� `T`�� ��ü Ÿ������ �����ϰ� �ֽ��ϴ�. ��ü�Ӹ� �ƴ϶� �迭, �Լ�, Ŭ���� �� ������ �پ��� ������ Ÿ�� �Ķ���͸� ����ϵ��� ������ ������.

����:

  ```ts
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

> GitHub���� ����: https://tsch.js.org/9/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
// type DeepReadonly<T> = { readonly [P in keyof T] : T[P] };

// type DeepReadonly<T> = { 
//   readonly [P in keyof T] : T[P] extends Record<string, unknown>
//   ? DeepReadonly<T[P]>
//   : T[P];
// };

// type DeepReadonly<T> = keyof T extends never
// 	? T
// 	: { readonly [P in keyof T] : DeepReadonly<T[P]>};

type DeepReadonly<T> = {
	readonly [k in keyof T]: T[k] extends Record<any, any>
		? T[k] extends Function
			? T[k]
			: DeepReadonly<T[k]>
		: T[k]
}
```

### ����
* readonly Ÿ���� ���� ���� 
* ����Լ� ���
