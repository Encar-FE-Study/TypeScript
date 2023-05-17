https://stackoverflow.com/questions/73135436/typescript-infer-about-arrayindex
https://dev.to/mrcmesen/infer-types-from-objects-and-arrays-with-typescript-15km


// 처음시도 :실패
type TupleToUnion<T> =  { [K in keyof T] : T[K] }



sol1)
type TupleToUnion<T extends any[]> = T[number];

sol2)
type TupleToUnion<T> = T extends Array<infer U> ? U : never



/* _____________ 테스트 케이스 _____________ */
import type { Equal, Expect } from '@type-challenges/utils'

type cases = [
  Expect<Equal<TupleToUnion<[123, '456', true]>, 123 | '456' | true>>,
  Expect<Equal<TupleToUnion<[123]>, 123>>,
]
