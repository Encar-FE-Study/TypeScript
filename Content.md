# 스터디 내용정리

## 주차별 키워드 정리

1. 1주차
   1. extends
   2. union type
   3. blurblur~~


2. 2주차
   1. number : 배열에서 사용가능한 index같이 ~~
   2. infer~~ : 
   3. blurblur~~ : 


3. 3주차
   1. length : 튜플, 배열의 길이를 구하는 타입 키워드.
   2. exclude : pick, omit 과 유사한 메소드로 해당 타입을 제외한 타입설정.


4. 4주차
    1. extends
        - 클래스나 인터페이스의 상속할 때 사용
            ```TS
            interface IExample1 {
              x: number;
              y: number;
            }
            
            interface IExample2 extends IExample1 {
              z: number;
            }
            ```
        - 제네릭 타입 매개변수에 대한 제약 조건을 지정할 때 사용
            ```TS
            function IExample1<T extends string>(arg:T): T {
            	return arg;
            }
            
            IExample1(10); // Argument of type 'number' is not assignable to parameter of type 'string'
            ```
        - 제네릭 타입의 조건을 만족할 때 적용되는 타입을 지정하는데 사용  
            ```TS
            type IExample1<T> = T extends string ? string : never;

            const ex1:IExample1<string> = 'example';
            const ex2:IExample1<number> = 10; // Type 'number' is not assignable to type 'never'.
            ```
    2. [infer](https://dev-boku.tistory.com/entry/%EB%B2%88%EC%97%AD-%EC%A0%84%EB%AC%B8%EA%B0%80%EC%B2%98%EB%9F%BC-%ED%83%80%EC%9E%85%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-infer-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)
        - 제네릭 타입에서 타입 매개변수를 추론하는 기능을 제공하는 키워드
        - **오직 extends 제네릭 조건부 타입에서 사용**
        - 입력 타입에 따라 타입 매개변수를 추론하여 출력 타입을 결정할 수 있음
            ```TS
            type IExample1<T> = T extends (infer U)[] ? U : never;
            const ex1:IExample1<string[]> = 'example';
            const ex2:IExample1<10> = 'example'; // Type 'string' is not assignable to type 'never'
            ```
    
    3. [promise vs promiseLike](https://yceffort.kr/2021/11/array-arraylike-promise-promiselike)
        - promise
          - 프로미스 체이닝을 비롯한 모든 Promise 메소드를 가지고 있으며, 항상 프로미스 객체를 반환
          - 프로미스 객체를 생성하거나 반환할 때는 일반적으로 Promise를 사용
        - promiseLike
          - Promise와 매우 유사한 인터페이스를 가진 객체를 나타내며, then 메소드를 포함한 프로미스 체이닝을 지원
          - 프로미스, PromiseLike 객체는 항상 Promise 객체와 같은 방식으로 동작하는 것은 아니며, then 메소드를 포함하지 않을 수도 있음

    4. [type vs Interface](https://yceffort.kr/2021/03/typescript-interface-vs-type)
        - type
          - 타입 앨리어스(Type alias)를 정의하는데 사용
          - Union 타입, Intersection 타입 등을 포함한 다양한 타입을 정의할 수 있음
        - interface
          - Interface는 객체의 구조를 정의하는 데 사용
          - 객체의 프로퍼티 이름, 타입 및 메소드를 정의하여 해당 객체가 가져야 할 모양을 정의

    5. tuple 타입
        - 고정된 요소의 수와 각 요소의 타입이 정의된 배열
        - 배열과 비슷하지만, 배열 요소의 개수와 타입이 미리 정의된다는 차이점이 있음
             ```TS
            let IExample1: [string, number, boolean] = ["hi", 100, true];
            ```       
   
## 참고 링크 정리

1주차

- https://ghaiklor.github.io/type-challenges-solutions/ko/easy-tuple-to-object.html

2주차

- https://ghaiklor.github.io/type-challenges-solutions/ko/easy-tuple-to-object.html

4주차

- https://yceffort.kr/2021/03/typescript-interface-vs-type
