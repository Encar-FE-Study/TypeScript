# 스터디 내용정리

## 주차별 키워드 정리

### 1주차
- extends
- union type

### 2주차
- Const Assertion: 타입 추론의 범위를 좁혀줄 수 있음
- Maped Types: [K in T]: K
- Indexed Types: T[number] T[0]
- Conditional Types: [] ? never : T[0]

### 3주차
- length : 튜플, 배열의 길이를 구하는 타입 키워드.
- exclude : pick, omit 과 유사한 메소드로 해당 타입을 제외한 타입설정.

### 4주차
- extends
  - 클래스나 인터페이스의 상속할 때 사용
  - 제네릭 타입 매개변수에 대한 제약 조건을 지정할 때 사용
  - 제네릭 타입의 조건을 만족할 때 적용되는 타입을 지정하는데 사용
- [infer](https://dev-boku.tistory.com/entry/%EB%B2%88%EC%97%AD-%EC%A0%84%EB%AC%B8%EA%B0%80%EC%B2%98%EB%9F%BC-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-infer-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)
  - 제네릭 타입에서 타입 매개변수를 추론하는 기능을 제공하는 키워드
  - **오직 extends 제네릭 조건부 타입에서 사용**
  - 입력 타입에 따라 타입 매개변수를 추론하여 출력 타입을 결정할 수 있음
- [promise vs promiseLike](https://yceffort.kr/2021/11/array-arraylike-promise-promiselike)
- [type vs Interface](https://yceffort.kr/2021/03/typescript-interface-vs-type)
  - tuple 타입
  - 고정된 요소의 수와 각 요소의 타입이 정의된 배열

### 6주차
- any
  - Turn off the type check.
- unknown
  - 다른 모든 타입들의 부모타입
  - 아무 값이나 될 수 있으나 사용 전에 체크 필요(ex. JSON.parse)

## 참고 링크 정리

### 1주차
- https://ghaiklor.github.io/type-challenges-solutions/ko/easy-tuple-to-object.html

### 2주차
- https://ghaiklor.github.io/type-challenges-solutions/ko/easy-tuple-to-object.html

### 4주차
- https://yceffort.kr/2021/03/typescript-interface-vs-type

### 6주차
- https://stackoverflow.com/questions/51439843/unknown-vs-any
- https://roseline.oopy.io/dev/typescript-unknown-vs-any-type
- https://dmitripavlutin.com/typescript-unknown-vs-any/
