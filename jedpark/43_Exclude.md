43 - Exclude
-------
by Zheeeng (@zheeeng) #���� #built-in #union

### ����

`T`���� `U`�� �Ҵ��� �� �ִ� Ÿ���� �����ϴ� ���� ���׸� `Exclude<T, U>`�� �̸� ������� �ʰ� �����ϼ���.

����:

  ```ts
  type Result = MyExclude<'a' | 'b' | 'c', 'a'> // 'b' | 'c'
  ```

/* _____________ ���⿡ �ڵ� �Է� _____________ */

```ts
type MyExclude<T, U> = T extends U ? never : T
```

### ����
* extends ���� ���ʿ��� ������ Ÿ������ �Ҵ� �����ϸ� Ʈ��
