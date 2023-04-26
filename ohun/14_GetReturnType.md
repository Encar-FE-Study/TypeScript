```ts
/* _____________ Your Code Here _____________ */
type MyReturnType<T> = T extends (...args: any[])
	=> infer U ? U : T;


/* _____________ Test Cases _____________ */
const fn = (v: boolean) => {
  if (v)
    return 1
  else
    return 2
}

type a = MyReturnType<typeof fn> // should be "1 | 2"


```

# 설명
함수타입
infer로 타입추론

