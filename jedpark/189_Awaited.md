189 - Awaited
-------
by Maciej Sikora (@maciejsikora) #���� #promise #built-in

### ����

Promise�� ���� Ÿ�Կ� ������ Ÿ���� ���� ��, �ȿ� ������ Ÿ���� �������� ��� �� �� �������?

����: ��� `Promise<ExampleType>`�� ���� ��, `ExampleType`�� ��� ���� �� �������?

  ```ts
  type ExampleType = Promise<string>

  type Result = MyAwaited<ExampleType> // string
  ```



/* _____________ ���⿡ �ڵ� �Է� _____________ */

```ts

type MyAwaited<T extends PromiseLike<any>> = T extends PromiseLike<infer R>
    ? R extends PromiseLike<any>
        ? MyAwaited<R>
        : R
    : never

type MyAwaited2<T extends PromiseLike<any>> = T extends PromiseLike<infer R>
    ? Awaited<R>
    : T
type MyAwaited3<T extends PromiseLike<any>> = T extends PromiseLike<infer R>
	? Awaited<R>
	: never
```

### ����
* T�� any Ÿ���� �����ϴ� PromiseLike �����̴� ��� ��
* ���� 1. T extends PromiseLike<infer R> ? : ���� T�� R�̶�� Ÿ���� ���� Ÿ������ ������ PromiseLike �̶��
* ���� 2. R extends PromiseLike<any> ? : ���� R�� PromiseLike<any> Ÿ���̶�� (��� ���¸� ��� ������ R�� PromiseLike<any>�� �߷��ϰ� �Ϸ��� �̷� ������ �����Ѵ�)
* Promise<any> �� ����ϸ� type T = { then: (onfulfilled: (arg: number) => any) => any } �� ������� ���ϹǷ� then �����ε� ����Ǵ� PromiseLike �� ���
* Promise = then, catch, finally
* PromiseLike = then
* ���� : https://jaenny-dev.tistory.com/6
* AarrayLike, PromiseLike : https://jaenny-dev.tistory.com/5#article-1-2-
