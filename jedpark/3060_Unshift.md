/*
3060 - Unshift
  -------
by jiangshan (@jiangshanmeta) #���� #array

### ����

`Array.unshift`�� Ÿ�� ������ �����ϼ���.

����:

  ```typescript
  type Result = Unshift<[1, 2], 0> // [0, 1, 2,]
  ```

> GitHub���� ����: https://tsch.js.org/3060/ko
*/

/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
type Unshift<T extends any[], U> = [U, ...T];

```

### ����
* 
