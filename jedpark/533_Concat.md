533 - Concat
-------
by Andrey Krasovsky (@bre30kra69cs) #���� #array

### ����

JavaScript�� `Array.concat` �Լ��� Ÿ�� �ý��ۿ��� �����ϼ���. Ÿ���� �� �μ��� �ް�, �μ��� ���ʺ��� concat�� ���ο� �迭�� ��ȯ�ؾ� �մϴ�.

����:

  ```ts
  type Result = Concat<[1], [2]> // expected to be [1, 2]
  ```

> GitHub���� ����: https://tsch.js.org/533/ko


/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
type Concat<T extends any[], U extends any[]> = [...T, ...U];
```

### ����
* T,U�� extends �� �迭�� �����ϰ�, ���������ڷ� �Ҵ�
