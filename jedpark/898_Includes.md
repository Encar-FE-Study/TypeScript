898 - Includes
-------
by null (@kynefuk) #���� #array

### ����

JavaScript�� `Array.includes` �Լ��� Ÿ�� �ý��ۿ��� �����ϼ���. Ÿ���� �� �μ��� �ް�, `true` �Ǵ� `false`�� ��ȯ�ؾ� �մϴ�.

����:

  ```ts
  type isPillarMen = Includes<['Kars', 'Esidisi', 'Wamuu', 'Santana'], 'Dio'> // expected to be `false`
  ```

> GitHub���� ����: https://tsch.js.org/898/ko
*/

/* _____________ ���⿡ �ڵ� �Է� _____________ */
```ts
type MyEqual<X, Y> = (<T>() => T extends X ? 1 : 2) extends (<T>() => T extends Y ? 1 : 2) ? true : false;

// type Includes<T extends readonly any[], U> = T extends [...infer O]
// 	? Equal<O, U> extends true
// 		? true
// 		: Includes<O, U>
// 	: false;
type Includes<T extends readonly any[], U> = T extends [infer F, ...infer O]
    ? MyEqual<F, U> extends true
        ? true
        : Includes<O, U>
    : false;

```

### ����
* ���� �迭���� ù��? F�� ������ O�� �����ٸ�
* ù��° F�� ���� U�� ������ MyEqual�� ���ϰ�, false�̸� ����Լ��� ���� ������ O�� ���Ѵ�. 
* (�� infer�� �ι��Ἥ ������ �ұ�)
