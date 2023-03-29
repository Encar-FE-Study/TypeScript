
18 - Length of Tuple
  -------
by sinoon (@sinoon) #쉬움 #tuple

### 질문

배열(튜플)을 받아 길이를 반환하는 제네릭 `Length<T>`를 구현하세요.

예시:

  ```ts
  type tesla = ['tesla', 'model 3', 'model X', 'model Y']
  type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']

  type teslaLength = Length<tesla>  // expected 4
  type spaceXLength = Length<spaceX> // expected 5
  ```

> GitHub에서 보기: https://tsch.js.org/18/ko
*/

```ts

type Length<T extends readonly string[]> = T["length"]
```

### 정리
* 타입은 extends를 이용하여 string[] 배열로 제한한다.
* tuple 타입을 선언할 때 각 요소 자리에 다른 타입이 들어갈 수 없으므로 readonly를 수식해준다.
* T['length'] 로 타입의 길이를 가져올 수 있다.

