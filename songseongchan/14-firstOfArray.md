푼 답
type First<T extends any[]> = T["length"] extends 0 ? never :  T[0];
type First<T extends any[]>  = T extends [] ? never : T[0];

//공부가 더 필요한 것 - infer
type First<T extends any[]> = T extends [infer K, ...infer P] ? K : never


infer 참고
https://stackoverflow.com/questions/60067100/why-is-the-infer-keyword-needed-in-typescript