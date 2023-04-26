
2 - Get Return Type
  -------
by Anthony Fu (@antfu) #보통 #infer #built-in

### 질문

내장 제네릭 `ReturnType<T>`을 이를 사용하지 않고 구현하세요.

예시:

  ```ts
  const fn = (v: boolean) => {
    if (v)
      return 1
    else
      return 2
  }

  type a = MyReturnType<typeof fn> // should be "1 | 2"
  ```

> GitHub에서 보기: https://tsch.js.org/2/ko


/* _____________ 여기에 코드 입력 _____________ */
```ts
// type MyReturnType<T> = T extends () => infer K ? K : never;
type MyReturnType<T> = T extends (...arg : any[]) => infer K ? K : never;
type MyReturnType<T> = T extends (...arg : any[]) => infer K ? K : T;

```

### 정리
* () => infer K 는 함수의 인자가 없는 함수
  * 인자가 있는 fn, fn1을 통과를 못함, 그래서 arg를 추가
* T가 K를 리턴하는 함수를 상속한다면, K를 리턴하고 아니면 never를 리턴한다.
* 일반 타입 매개변수에 대한 제약조건 절에서 infer 선언을 사용할 수 없습니다.
```ts
type ReturnType<T extends (...args: any[]) => infer R> = R;  // 오류, 지원되지 않습니다.
```
