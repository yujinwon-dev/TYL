### 목차

- [Vue](#vue)
  * [Why Vue.js?](#why-vuejs)
  * [Concepts of Vue.js](#concepts-of-vuejs)
    + [MVVM Pattern](#mvvm-pattern)
  * [Basic syntax of Vue.js](#basic-syntax-of-vuejs)
    + [Vue instance 생성](#vue-instance-생성)
    + [Options/DOM: 'el'](#optionsdom-el)
    + [Options/DOM: 'data'](#optionsdom-data)
    + [Options/DOM: 'methods'](#optionsdom-methods)
    + [`this` keyword](#this-keyword)
  * [Template Syntax](#template-syntax)
    + [Interpolation (보간법)](#interpolation-보간법)
    + [Directive](#directive)
  * [Lifecycle Hooks](#lifecycle-hooks)
  * [Lodash library](#lodash-library)

# Vue

- React와 Vue.js의 공통점

  - 가상 DOM을 활용! -> FE Framework의 큰 특징

  - FE 개발자 되려면 가상 DOM 더 잘 알아야

    => 실제 DOM과는 별개로 js가 이걸 js code 형태로, 가상으로 DOM을 갖고 있는 것

    => 가상 DOM이 관리하는 data가 있고, 내용이 변경될 경우 가상 DOM과 실제 DOM의 차이점 발생 => 가상 DOM이 실제 DOM을 대체

    => FE framework가 가상 DOM을 이용해 데이터 관리 해주는 ~



- SPA (Single Page Application)

  - 하나의 페이지(ex)`index.html`)에 js를 활용해서 필요한 부분만 부분적으로 변경

    => 현재 페이지를 동적으로 렌더링

  - 서버로부터 최초에만 웹 애플리케이션에 필요한 모든 정적 리소스를 받고, 이후에는 동적으로 DOM 구성 (필요한 데이터만 전달받음)
  
    => 사용자 경험 향상!
  
  - 동작 원리의 일부가 CSR의 구조를 따름
  



- CSR(Client Side Rendering)

  - SSR(Server Side Rendering)과 달리 클라이언트에서 화면 구성

  - 최초 요청 시 데이터를 제외한 HTML, CSS, JS 등의 리소스를 응답받고, 이후에는 클라이언트에서 필요한 데이터만 요청해서 JS로 DOM 렌더링

  - SPA가 사용하는 렌더링 방식

  - 장점

    1. 서버와 클라이언트 간 트래픽 감소

       : 매번 모든 리소스를 주고 받지 않아도 됨

    2. 사용자 경험 향상

       : 변경되는 부분만 갱신하므로

  - 단점

    1. SSR에 비해 전체 페이지 렌더링 느림

       : 필요한 모든 정적 리소스를 처음에 전부 받아와야 하므로

    2. SEO(검색 엔진 최적화)에 어려움이 있음

       : 최초 문서에 데이터가 없음



- SSR(Server Side Rendering)

  - 장점

    1. 초기 구동 속도 빠름

    2. SEO에 적합

       : DOM에 이미 모든 데이터가 작성되어 있으므로

  - 단점

    - 모든 요청마다 새로운 페이지를 구성하여 전달

      : 사용자 경험 떨어짐 -> 뭐 할 때마다 전체 새로고침

      상대적으로 트래픽이 많아 서버 부담 클 수 있음



> SSR과 CSR 중 단순히 어느 것이 더 좋다! 라고 할 수 없음
>
> 두 방식 중 서비스에 더 맞는 것을 선택하거나, 섞어서 구성



- SEO(Search Engine Optimization)

  - 웹 페이지 검색엔진이 자료 수집&순위 매기는 방식에 맞게 웹 페이지 구성 -> 검색 결과의 상위에 노출될 수 있도록 하는 작업

  - SPA 프레임워크는 SSR을 지원하는 SEO 대응기술 이미 존재!

    -> Nuxt.js, Next.js 등

<br>

## Why Vue.js?

- 원래 vanilla js로 하려면 innerText ..해서 모든 요소를 하나하나 바꿔줘야 했음

  이걸 지켜봐서 바꿔주는 걸 Vue.js가 proxy 형태로 해줌!

<br>

## Concepts of Vue.js

### MVVM Pattern

- Model
  - JavaScript object 자료구조. Vue 인스턴스 내부에서 데이터로 사용됨
- View
  - 실제 사용자가 보게 될 화면
- ViewModel
  - 모든 Vue 인스턴스. View와 Model 사이에서 Model의 변화를 지켜보고 데이터를 처리

- model(->data)의 변경사항이 발생했을 때 바로 view에 적용하는 건 vanilla js를 사용하는 거나 다름 없고, HTML 문서를 data를 이용해서 Vue 객체 형태로 조작하고 싶어서 Vue.js 사용하는 것

- 가상DOM을 쓰는 건 View를 직접 관리하지 않기 위함! Vue 객체 생성할 때만 querySelector 처럼 잡아오고, (-> `el: '#app'`) 그 이후에는 거의 직접 하지 않음
- 데이터를 얼마만큼 잘 처리해서 보여줄지.. 가 포인트

<br>

## Basic syntax of Vue.js

### Vue instance 생성

```html
<script>
    const app = new Vue({
		// 여기에 여러 options를 작성
	})
</script>
```

### Options/DOM: 'el'

```html
<script>
	const app = new Vue({
        // Vue 인스턴스에 연결(마운트)할 DOM 엘리먼트
        el: '#app'
    })
</script>
```

### Options/DOM: 'data'

```html
<script>
	const app = new Vue({
        el: '#app',
        data: {
            // Vue 인스턴스의 데이터 객체
            // Vue template에서 {{ interpolation }}을 통해 접근 가능
            // ** data에서 화살표 함수 사용 X ** => Vue 인스턴스가 아니라 Window 가리키게 됨
            message: 'Hello Vue!'
        }
    })
</script>
```

### Options/DOM: 'methods'

```html
<script>
	const app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue!'
        },
        methods: {
            // Vue 인스턴스에 추가할 메서드
            // Vue template에서 {{ interpolation }}을 통해 접근 가능
            // ** 메서드 정의할 때 화살표 함수 사용 X **
            reverseMessage: function() {
                this.message = this.message.split('').reverse().join('')
            }
        }
    })
</script>
```

### `this` keyword

- Vue 함수 객체 내에서 vue 인스턴스 가리킴

- 화살표 함수를 쓰는 것과 function을 쓸 때 this에 바인딩 되는 객체가 달라짐

  => addEventListener 할 때도!

  => *function 키워드 사용 시 상위에 있는 인스턴스. 화살표 함수 사용 시 window가 바인딩 됨.*

<br>

## Template Syntax

### Interpolation (보간법)

```html
<!-- Text -->
<span>{{ message }}</span>

<!-- Attributes -->
<ul>
    <li v-for="todo in todos" v-bind:key="todo.id">
    	{{ todo.content }}
    </li>
</ul>

<!-- JS 표현식 -->
{{ number + 1}}
```

### Directive

- `v-` 접두사가 있는 특수 속성

- *표현식의 값이 변경될 때 반응적으로 DOM에 적용하는 역할*

- `:`을 통해 전달인자 받을 수 있음

  ex) `<button v-on:click="addTodo">add</button>`

- `.`을 통해 수식어 사용 가능

  디렉티브를 특별한 방법으로 바인딩해야 함을 나타냄

  ex) `<form v-on:submit.prevent="onSubmit"></form>`

  ​		=> `.prevent` 수식어는 트리거된 이벤트에서 `event.preventDefault()`를 호출하도록 `v-on` 디렉티브에게 알려줌

---

- v-text

  ```html
  <p v-text="message"></p>
  <!-- 같음 -->
  <p>{{ message }}</p>
  ```

  - 엘리먼트의 textContent 업데이트
  - 내부적으로 interpolation 문법이 v-text로 컴파일 됨

- v-show

  ```html
  <p v-show="seen">
      seen의 값이 True이면 보임!
  </p>
  ```

  - 단순히 `display: none;` 속성을 토글하는 것
  - 엘리먼트는 항상 렌더링 됨 (렌더링 비용 높음)
    - 자주 변경되는 요소일 경우 한 번 렌더링 된 이후에는 보여줄 지 말 지만 토글해주면 되므로 토글 비용 적음

- v-if, v-else-if, v-else

  ```html
  <div v-if="seen === true">
      can see!
  </div>
  ```
  
  - 조건에 따라 블록 렌더링 (true일 때만 렌더링 됨)

- v-for

  ```html
  <div v-for="(todo, index) in todos" :key="`todo-${index}`">
      {{ todo.content }}
  </div>
  ```

  - **unique한 key를 반드시 부여**해야 함
  - *가능하면 v-if와 함께 사용하지 않기*



- v-on

  ```html
  <button v-on:click="addTodo">
      add
  </button>
  <!-- 또는 -->
  <button @click="addTodo">
      shorthand는 이렇게
  </button>
  ```

  - 엘리먼트에 이벤트 리스너 연결
  - 특정 이벤트 발생 시 주어진 코드 실행됨

- v-bind

  ```html
  <p v-bind:class="{ toRed: isActivated }">
      true면 toRed 클래스 들어감! 문자열로 한 번 묶어준 뒤 {}에 작성
  </p>
  <!-- 또는 -->
  <p :class="[toRed, myBackground]">
      shorthand는 이렇게
  </p>
  ```

- v-model

  ```html
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">{{ todo.content }}</label>
  ```

  - value가 있는 태그에서 사용

  - 양방향 바인딩이 일어남

    v-bind는 단방향 바인딩=> Vue에서 DOM으로만 조작 가능

    양방향 => input이 작성되면 js의 데이터와 연결되어 데이터가 바로바로 변경되는



- `computed`
  - 데이터가 변경될 때만 함수 실행 => **해당 데이터를 토대로 계산**한 뒤 결과를 보여줌
  - 함수 형태로 정의하여 **리턴값 사용** => 반환값 필수
  - 선언형 프로그래밍 방식
- `watch`

  - 데이터를 지켜보다가 변경되면 **함수 실행** => 특정 작업을 함 (트리거)
  - 데이터 이름과 맞춰줘야 함
  - 명령형 프로그래밍 방식
- `filter`
  - django에서 쓰던 것과 사용방식 동일
  - interpolation 또는 v-bind 이용할 때 사용 가능

<br>

## Lifecycle Hooks

- 라이프 사이클마다 호출되는 함수들

- created, mounted, updated 많이 사용

  ```javascript
  // 예시
  const app = new Vue({
      // ...
      created: function () {
          // created hook은 vue 인스턴스가 생성된 후 호출됨
          this.getImg()
      }
  })
  ```

- destroyed
  - vue 말고 다른 라이브러리에서 생성된 메모리 값들.. 무슨 문제가 발생했을 때 강제로 메모리 해제해줄 때..? 사용

<br>

## Lodash library

- array, object 등의 자료구조를 다룰 때 사용하는 다양한 함수들을 제공하는 라이브러리
