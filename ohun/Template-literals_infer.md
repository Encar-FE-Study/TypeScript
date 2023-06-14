# Replace
```ts
type replaced = Replace<'types are fun!', 'fun', 'awesome'>
// expected to be 'types are awesome!'
```
<details><summary>js</summary>

```js
function Replace(S, From, To){
    console.log(S.replace(From, To))
}

Replace('types are fun!', 'fun', 'awesome')
// types are awesome!
```
</details>

<details><summary>ts</summary>

```ts
type Replace<S extends string, From extends string, To extends string> =
  From extends ''
    ? S
    : S extends `${infer U}${From}${infer V}`
        ? `${U}${To}${V}`
        : S;
```
</details>
<br/><br/>










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
type SnakeCase<T extends string,Result extends string = ""> =
  T  extends `${infer A}${infer B}`?
  A extends Uppercase<A> ?
    SnakeCase<B,`${Result}_${Lowercase<A>}`>:
    SnakeCase<B,`${Result}${A}`>:
    Result
```
</details>
<br/><br/>