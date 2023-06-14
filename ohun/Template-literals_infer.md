# Replace
문자열 S에서 From를 찾아 한 번만 To로 교체하는 Replace<S, From, To>를 구현하세요.

예시:
```ts
type replaced = Replace<'types are fun!', 'fun', 'awesome'>
// expected to be 'types are awesome!'
```
<details><summary>js</summary>

```js
'types are fun!'.replace('fun', 'awesome')
// types are awesome!
```
</details>

<details><summary>ts</summary>

```ts
type Replace<S extends string, From extends string, To extends string> =
  From extends '' ?
    S
  :
    S extends `${infer A}${From}${infer Z}` ?
        `${A}${To}${Z}`
      :
        S
```
</details>
<br/><br/><br/><br/><br/><br/><br/><br/><br/><br/>











<!-- # Split
```ts
type result = Split<'Hi! How are you?', ' '>
// should be ['Hi!', 'How', 'are', 'you?']
```
<details><summary>js</summary>

```js
'Hi! How are you?'.split(' ')
// ['Hi!', 'How', 'are', 'you?']
```
</details>

<details><summary>ts</summary>

```ts
type Split<S extends string, SEP extends string> = string extends S
  ? string[]
  : S extends `${infer A}${SEP}${infer B}`
    ? [A, ...(B extends "" ? [] : Split<B, SEP>)]
    : SEP extends ""
      ? []
      : [S]
```
</details>
<br/><br/> -->











# SnakeCase
camelCaseSnakeCase<T> 형식의 문자열을 snake_case 형식의 문자열로 바꾸는 제네릭을 만듭니다 .

몇 가지 예:
```ts
type res1 = SnakeCase<"hello">; // => "hello"
type res2 = SnakeCase<"userName">; // => "user_name"
type res3 = SnakeCase<"getElementById">; // => "get_element_by_id"
```
<details><summary>js</summary>

```js
"getElementById".split('').map(v => v === v.toUpperCase() ? `_${v.toLowerCase()}` : v).join('')
// 'get_element_by_id'
```
</details>

<details><summary>ts</summary>

```ts
type SnakeCase<T extends string, Result extends string = ""> =
  T extends `${infer A}${infer B}` ?
    A extends Uppercase<A> ?
        SnakeCase<B, `${Result}_${Lowercase<A>}`>
      :
        SnakeCase<B, `${Result}${A}`>
  :
    Result
```
</details>
<br/><br/>