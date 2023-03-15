# 7 - Readonly
-------
by Anthony Fu (@antfu) #���� #built-in #readonly #object-keys

### ����

`T`�� ��� ������Ƽ�� �б� ����(���Ҵ� �Ұ�)���� �ٲٴ� ���� ���׸� `Readonly<T>`�� �̸� ������� �ʰ� �����ϼ���.

����:

  ```ts
  interface Todo {
    title: string
    description: string
  }

  const todo: MyReadonly<Todo> = {
    title: "Hey",
    description: "foobar"
  }

  todo.title = "Hello" // Error: cannot reassign a readonly property
  todo.description = "barFoo" // Error: cannot reassign a readonly property
  ```

> GitHub���� ����: https://tsch.js.org/7/ko


/* _____________ Your Code Here _____________ */
```ts
type MyReadonly<T> = {
	readonly[K in keyof T] : T[K]
}
```
### ����
* ���׸� �������ǿ��� Ÿ�� �Ű����� ��� (Using Type Parameters in Generic Constraints)
* Mapped type�� �̿��Ͽ� ���� ����� ����
* in ���� �ݺ��Ͽ� T�� �� key�� �ش��ϴ� Ÿ���� Ÿ������ ����  
* Partial, Pick, Record
