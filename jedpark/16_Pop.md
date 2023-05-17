
16 - Pop
-------
by Anthony Fu (@antfu) #���� #array

### ����

> �� ç�������� TypeScript 4.0 ����� ����˴ϴ�.

�迭 `T`�� ����� ������ ��Ҹ� ������ �迭�� ��ȯ�ϴ� ���׸� `Pop<T>`�� �����մϴ�.

����

  ```ts
  type arr1 = ['a', 'b', 'c', 'd']
  type arr2 = [3, 2, 1]

  type re1 = Pop<arr1> // expected to be ['a', 'b', 'c']
  type re2 = Pop<arr2> // expected to be [3, 2]
  ```

**������**: ����ϰ� `Shift`, `Push` �׸��� `Unshift`�� ������ �� �������?

> GitHub���� ����: https://tsch.js.org/16/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
type Pop<T extends any[]> = T extends [...infer X, infer L] ? X : never;

```

### ����
* last of array �ݴ�
