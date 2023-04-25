
2 - Get Return Type
  -------
by Anthony Fu (@antfu) #���� #infer #built-in

### ����

���� ���׸� `ReturnType<T>`�� �̸� ������� �ʰ� �����ϼ���.

����:

  ```ts
  const fn = (v: boolean) => {
    if (v)
      return 1
    else
      return 2
  }

  type a = MyReturnType<typeof fn> // should be "1 | 2"
  ```

> GitHub���� ����: https://tsch.js.org/2/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
// type MyReturnType<T> = T extends () => infer K ? K : never;
type MyReturnType<T> = T extends (...arg : any[]) => infer K ? K : never;
type MyReturnType<T> = T extends (...arg : any[]) => infer K ? K : T;

```

### ����
* () => infer K �� �Լ��� ���ڰ� ���� �Լ�
  * ���ڰ� �ִ� fn, fn1�� ����� ����, �׷��� arg�� �߰�
* T�� K�� �����ϴ� �Լ��� ����Ѵٸ�, K�� �����ϰ� �ƴϸ� never�� �����Ѵ�.
* �Ϲ� Ÿ�� �Ű������� ���� �������� ������ infer ������ ����� �� �����ϴ�.
```ts
type ReturnType<T extends (...args: any[]) => infer R> = R;  // ����, �������� �ʽ��ϴ�.
```
