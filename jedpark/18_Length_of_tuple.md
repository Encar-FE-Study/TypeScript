
18 - Length of Tuple
  -------
by sinoon (@sinoon) #���� #tuple

### ����

�迭(Ʃ��)�� �޾� ���̸� ��ȯ�ϴ� ���׸� `Length<T>`�� �����ϼ���.

����:

  ```ts
  type tesla = ['tesla', 'model 3', 'model X', 'model Y']
  type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

  type teslaLength = Length<tesla>  // expected 4
  type spaceXLength = Length<spaceX> // expected 5
  ```

> GitHub���� ����: https://tsch.js.org/18/ko
*/

```ts

type Length<T extends readonly string[]> = T["length"]
```

### ����
* Ÿ���� extends�� �̿��Ͽ� string[] �迭�� �����Ѵ�.
* tuple Ÿ���� ������ �� �� ��� �ڸ��� �ٸ� Ÿ���� �� �� �����Ƿ� readonly�� �������ش�.
* T['length'] �� Ÿ���� ���̸� ������ �� �ִ�.

