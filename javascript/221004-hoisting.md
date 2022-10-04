## 호이스팅

- 인터프리터가 변수/함수의 메모리 공간을 선언 전에 미리 할당하는 것
- 선언문이 코드의 상단으로 끌어 올려진 것처럼 동작하는 것 (초기화 제외)

## 함수 호이스팅

- 함수 선언은 호이스팅 된다.

  ```jsx
  hoisted(); // logs "foo"
  
  function hoisted() {
    console.log("foo");
  }
  ```

- 함수 표현식은 호이스팅 되지 않는다.

  ```jsx
  console.log(notHoisted); // undefined
  notHoisted(); // TypeError: notHoisted is not a function
  
  var notHoisted = function() {
     console.log("bar");
  };
  ```

## 변수 호이스팅

- `let` , `const` , `var` 로 선언한 모든 변수는 호이스팅 된다.
- `let` , `const` 로 선언한 변수의 초기화는 변수 선언문에 도달했을 때 실행된다. 따라서 호이스팅이 발생하지 않는 것처럼 동작할 뿐이다.
- `var` 로 선언한 변수는 선언 즉시 undefined로 초기화된다.

### 시간상 사각지대(TDZ: Temporal Dead Zone)

- 변수 스코프의 맨 위에서 변수가 초기화가 완료되는 시점까지 변수는 시간상 사각지대에 들어갔다고 표현한다.

- “시간상” 사각지대인 이유는, 코드의 작성 순서(위치)가 아니라 실행 순서(시간)에 의해 사각지대가 형성되기 때문이다.

  ```jsx
  function do_something() {
  	// TDZ가 스코프 맨 위에서 시작됨
    console.log(bar); // undefined
    console.log(foo); // ReferenceError
    var bar = 1;  // bar의 TDZ 종료
    let foo = 2;  // foo의 TDZ 종료
  }
  ```

------

- 참고
  - MDN [호이스팅](https://developer.mozilla.org/ko/docs/Glossary/Hoisting)