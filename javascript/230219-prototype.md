## Prototype

JavaScript는 프로토타입 기반 언어라고 불린다.

즉, <u>모든 객체들이</u> 메소드와 속성을 상속 받기 위한 템플릿으로써 <u>프로토타입 객체를 갖는다</u>는 의미이다.

프로토타입 객체는 또 다시 상위 프로토타입 객체로부터 메소드, 속성을 상속 받을 수 있다. 이를 **프로토타입 체인** 이라고 한다.

정확히 말하면 상속되는 속성, 메소드들은 각 객체가 아니라 객체의 생성자의 `prototype` 속성에 정의되어 있다.

JavaScript에서는 객체 인스턴스와 프로토타입 간에 연결이 구성되며, 이 연결을 따라 프로토타입 체인을 타고 올라가며 속성과 메소드를 탐색한다. (메소드와 속성들이 다른 객체로 복사되는 것 x)

+)

객체의 prototype(`Object.getPrototypeOf(obj)` / `obj.__proto__` )과 생성자의 `prototype` 속성은 차이가 있다.

전자는 개별 객체의 속성이고 후자는 생성자의 속성이다.

(전자는 특정 객체(obj)의 프로토타입 속성(프로토타입 객체)에 접근하는 것이고, 후자는 생성자의 프로토타입 속성이다.)

즉, `Object.getPrototypeOf(new Foobar())` 의 반환값이 `Foobar.prototype` 과 동일한 객체라는 의미이다.

상속 받은 속성과 메소드들은 프로토타입 속성에 정의되어 있다.

즉, 프로토타입 속성은 상속시키려는 멤버들이 정의된 객체이다.

예를 들어, 상속 받는 멤버들은 `Object.` 이 아니라 `Object.prototype.` 을 통해 접근할 수 있다.

`Object.is()` , `Object.keys()` 등 프로토타입에 정의되지 않은 멤버들은 상속되지 않는다.

### `this`

this 키워드는 지금 동작하고 있는 코드를 가지고 있는 객체를 가리킨다.

- 전역 context: 전역 객체 참조 (strict 모드 상관 없이)
- 함수 context
  - strict 모드가 아니고, 호출에 의해 값이 설정되지 않는 경우 기본적으로 전역 객체(`window` ) 참조
  - strict 모드에서는 `undefined`
- 화살표 함수
  - 자신을 감싼 context에서의 this를 가리킴
- 객체의 메서드
  - 해당 객체를 가리킴

------

- 참고
  - [MDN Object prototypes](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/Object_prototypes)
  - [MDN this](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)