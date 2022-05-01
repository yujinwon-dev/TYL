# var, let, const

## var

- ES6 이전에 자바스크립트에서 변수를 선언할 수 있는 유일한 키워드였음

- 특징

  - 중복 선언 가능

  - 문제점: 동일한 이름의 변수가 이미 선언되어 있는지 모르고 중복 선언 & 값까지 할당할 경우 먼저 선언된 변수 값이 변경되는 부작용 발생

    ```jsx
    var x = 1;
    var y = 1;
    
    // 같은 스코프 내에서 중복 선언 허용 (에러 발생 x)
    // 초기화문이 있는 변수 선언문: js 엔진에 의해 var 키워드가 없는 것처럼 동작
    var x = 100;
    // 초기화문이 없는 변수 선언문: 무시됨
    var y;
    
    console.log(x); // 100
    console.log(y); // 1
    ```

  - 함수 레벨 스코프

    - 오로지 함수의 코드 블록만을 지역 스코프로 인정
    - if문, for문 내에서 선언하면 모두 전역 변수가 됨
    - 문제점: 전역 변수를 남발할 가능성을 높임 → 의도치 않게 전역 변수가 중복 선언되는 현상 발생

    ```jsx
    var x = 1;
    
    if (true) {
    	var x = 10;
    }
    
    console.log(x); // 10
    ```

  - 변수 호이스팅

    - 변수 선언문이 스코프의 맨 앞으로 끌어 올려져서 동작

      → 선언문 이전에 참조할 수 있게 됨

    - 에러가 발생하지는 않지만, 가독성을 떨어뜨리고 오류를 발생시킬 여지를 남김

    ```jsx
    // 변수 호이스팅에 의해 foo 변수 선언 (1. 선언 단계)
    // undefined로 초기화 (2. 초기화 단계)
    console.log(foo); // undefined
    
    // 변수에 값 할당 (3. 할당 단계)
    foo = 123;
    
    console.log(foo); // 123
    
    // 변수 선언은 런타임 이전에 js 엔진에 의해 암묵적으로 실행됨 (값 할당은 소스코드가 순차적으로 실행되는 런타임에 실행됨!)
    var foo;
    ```

    - +) 호이스팅

      - 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미합니다. `var`로 선언한 변수의 경우 호이스팅 시 `undefined`로 변수를 초기화합니다. 반면 `let`과 `const`로 선언한 변수의 경우 호이스팅 시 변수를 초기화하지 않습니다.

        (참고: [호이스팅](https://developer.mozilla.org/ko/docs/Glossary/Hoisting))

## let

- 특징

  - 변수 중복 선언 금지

    ```jsx
    var bar = 123;
    var bar = 456; // SyntaxError: Identifier 'bar' has already been declared
    ```

  - 블록 레벨 스코프

    - 모든 코드 블록(if문, for문, while문 등)을 지역 스코프로 인정

    ```jsx
    	let foo = 1;  // 전역 변수
    
    if (true) {
    	let foo = 2;  // 지역 변수
    	let bar = 3;  // 지역 변수
    }
    
    console.log(foo); // 1
    console.log(bar); // ReferenceError: bar is not defined
    ```

  - 변수 호이스팅이 발생하지 않는 것처럼 동작

    - 선언 단계와 초기화 단계가 분리되어 진행됨

      - 런타임 이전에 js 엔진에 의해 암묵적으로 선언 단계 진행
      - 하지만 초기화는 변수 선언문에 도달했을 때 실행됨 (var 키워드로 선언한 변수는 선언 즉시 undefined로 초기화)

    - 자바스크립트는 let, const를 포함한 모든 선언을 호이스팅함! 호이스팅이 발생하지 않는 것처럼 동작할 뿐

      ```jsx
      console.log(foo); // ReferenceError: foo is not defined
      
      let foo;
      console.log(foo); // undefined
      
      foo = 10;
      console.log(foo); // 10
      ```

  - 전역 객체의 프로퍼티가 아님

    - `[window.foo](<http://window.foo>)` 와 같이 접근할 수 없음
    - **전역 객체 공부 후 다시 보기**

## const

- 상수(재할당이 금지된 변수)를 선언하기 위해 사용
  - 상수는 상태 유지, 가독성, 유지보수의 편의를 위해 적극적으로 사용할 것
  - 일반적으로 대문자로, 스네이크 케이스로 표현 (ex. `const TAX_RATE = 0.1;` )
- let 키워드와 대부분 동일한 특징을 가짐
  - 블록 레벨 스코프
  - 변수 호이스팅이 발생하지 않는 것처럼 동작
- let과의 차이점
  - 선언과 동시에 초기화해야 함
  - 재할당 금지
  - 하지만 const 키워드로 선언된 변수에 객체를 할당한 경우 값 변경 가능 (재할당을 금지할 뿐 불변은 아님)
    - 객체는 원시값과 달리 재할당 없이도 직접 변경이 가능하기 때문 → 참조값은 변하지 않음