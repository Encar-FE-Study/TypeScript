
export type MyEquals<X, Y> =
    (<T>() => T extends X ? 1 : 2) extends
    (<T>() => T extends Y ? 1 : 2) ? true : false;

`type Includes<T extends readonly any[], U> = T extends [infer First, ...infer Rest] ? Equal<First, U> extends true ? true : Includes<Rest, U> : false`


// MyEqual 만드는 것 참고 : lhttps://github.com/microsoft/TypeScript/issues/27024
// https://kscodebase.tistory.com/643
