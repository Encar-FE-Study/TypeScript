
15 - Last of Array
-------
by Anthony Fu (@antfu) #���� #array

### ����

> �� ç�������� TypeScript 4.0 ����� ����˴ϴ�.

�迭 `T`�� ����ϰ� ������ ��Ҹ� ��ȯ�ϴ� ���׸� `Last<T>`�� �����մϴ�.

����

  ```ts
  type arr1 = ['a', 'b', 'c']
  type arr2 = [3, 2, 1]

  type tail1 = Last<arr1> // expected to be 'c'
  type tail2 = Last<arr2> // expected to be 1
  ```

> GitHub���� ����: https://tsch.js.org/15/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
type Last<T extends any[]> = T extends [...infer X, infer L] ? L : never;
```

### ����
* �������� Ʃ��Ÿ��
* ���Ǻ� Ÿ�� �߷�
