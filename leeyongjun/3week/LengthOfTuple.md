# Length Of Tuple

### 질문

배열(튜플)을 받아 길이를 반환하는 제네릭 Length<T>를 구현하세요.

예시:

```ts
type tesla = ["tesla", "model 3", "model X", "model Y"];
type spaceX = [
	"FALCON 9",
	"FALCON HEAVY",
	"DRAGON",
	"STARSHIP",
	"HUMAN SPACEFLIGHT"
];

type teslaLength = Length<tesla>; // expected 4
type spaceXLength = Length<spaceX>; // expected 5
```

답:

```ts
type Length<T extends readonly any[]> = T["length"];
```
