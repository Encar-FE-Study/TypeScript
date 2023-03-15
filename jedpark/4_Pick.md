# 4 - Pick
-------
by Anthony Fu (@antfu) #���� #union #built-in

### ����

`T`���� `K` ������Ƽ�� ������ ���ο� ������Ʈ Ÿ���� ����� ���� ���׸� `Pick<T, K>`�� �̸� ������� �ʰ� �����ϼ���.

����:

  ```ts
  interface Todo {
    title: string
    description: string
    completed: boolean
  }

  type TodoPreview = MyPick<Todo, 'title' | 'completed'>

  const todo: TodoPreview = {
      title: 'Clean room',
      completed: false,
  }
  ```

> GitHub���� ����: https://tsch.js.org/4/ko


/* _____________ Your Code Here _____________ */
```ts
type MyPick<T, Props extends keyof T> = {
    [K in Props] : T[K]
}
```
### ����
* ���׸� �������ǿ��� Ÿ�� �Ű����� ��� (Using Type Parameters in Generic Constraints)
* ���� type�� Pick�� ������� �ʰ� Mapped type�� �̿��Ͽ� ���� ����� ����
* in ���� �ݺ��Ͽ� T�� �� key�� �ش��ϴ� Ÿ���� Ÿ������ ����  
