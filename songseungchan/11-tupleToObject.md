
```
type TupleToObject<T extends readonly any []> =  {
  [K in T[number]] : K
}
```



Index Signature / typeof

```
type Arrayish = { [n: number]: unknown };
type A = keyof Arrayish;
//   ^?

type Mapish = { [k: string]: boolean };
type M = keyof Mapish;
//   ^?




const myArray = ['foo', 'bar'] as const;
type MyArray = typeof myArray[number]; // foo | bar


const people = [
  { age: 20, name: 'Song' },
  { age: 21, name: 'James' },
  { age: 22, name: 'Mike' }
] as const

type Name = typeof people[number]['name']  // "Song" | "James" | "Mike"
```

참고
https://steveholgado.com/typescript-types-from-arrays/