### 목차

- [Vue 02](#vue-02)
  * [SFC (Single File Component)](#sfc-single-file-component)
    + [Component](#component)
    + [SFC(Single File Component)](#sfcsingle-file-component)
  * [Vue CLI](#vue-cli)
    + [Vue CLI](#vue-cli-1)
    + [Node.js](#nodejs)
    + [NPM (Node Package Manger)](#npm-node-package-manger)
  * [Babel & Webpack](#babel--webpack)
    + [Babel](#babel)
    + [Webpack](#webpack)
    + [Vue 프로젝트 구조](#vue-프로젝트-구조)
  * [:star: Pass props & emit event](#star-pass-props--emit-event)
    + [컴포넌트 작성](#컴포넌트-작성)
    + [:exclamation: 컴포넌트 등록 3단계](#exclamation-컴포넌트-등록-3단계)
    + [Props](#props)
      - [Static Props 작성](#static-props-작성)
      - [Dynamic Props 작성](#dynamic-props-작성)
      - [Props 이름 컨벤션](#props-이름-컨벤션)
      - [Props 시 주의할 점](#props-시-주의할-점)
      - [단방향 데이터 흐름](#단방향-데이터-흐름)
    + [Emit Event](#emit-event)
      - [Emit event 작성](#emit-event-작성)
      - [event 이름 컨벤션](#event-이름-컨벤션)
  * [Vue Router](#vue-router)
      - [Vue Router로 인한 변화](#vue-router로-인한-변화)
      - [History mode](#history-mode)
      - [경로 작성 방법](#경로-작성-방법)
      - [Vue Router가 필요한 이유](#vue-router가-필요한-이유)
    * [Youtube Project](#youtube-project)
      + [환경변수 설정](#환경변수-설정)

<br>

# Vue 02

## SFC (Single File Component)

### Component

- **Vue 컴포넌트 === Vue 인스턴스**

- 범용성(여러 분야나 용도로 널리 쓰일 수 있는 특성)을 위해 개발된 소프트웨어 구성요소

  -> 재사용 가능하도록 코드를 캡슐화 하는 데 도움을 줌

  -> 유지보수 및 재사용성의 측면에서 유용함

### SFC(Single File Component)

- **Vue 컴포넌트 === Vue 인스턴스 === .vue 파일**

- Vue의 컴포넌트 기반 개발의 핵심 특징

- 하나의 컴포넌트를 하나의 `.vue` 파일에 작성하여 싱글 파일 컴포넌트를 통해 개발

  -> 유지보수에 있어서 편리함

- Vue 컴포넌트는 `const app = new Vue({...})`에서 app을 의미. 즉, 하나의 .vue 파일 안에서 작성되는 코드의 결과물

  -> Vue 컴포넌트에 여러 개의 하위 컴포넌트가 있을 수 있고, 하나의 파일 안에서도 여러 개의 컴포넌트를 만들어 개발할 수 있음!

<br>

## Vue CLI

### Vue CLI

- Vue.js 개발을 위한 표준 도구

- `vue` 커맨드 제공: `vue create`, `vue add` 등

- global 하게 설치 후 버전 확인

  ```bash
  npm install -g @vue/cli
  vue --version
  ```

### Node.js

- 자바스크립트 런타임 환경(프로그램이 구동되는 환경)

  : 자바스크립트는 원래 브라우저에서만 실행될 수 있었지만, node.js를 통해 브라우저가 아닌 환경에서도 구동할 수 있음

- Chrome V8 엔진 제공 -> 여러 OS 환경에서 실행 가능하도록 환경 제공

- 로컬에서 서버를 돌릴 수 있게 됨 -> 단순히 브라우저만 조작할 수 있던 자바스크립트를 SSR(Server Side Rendering) 아키텍처에서도 사용할 수 있게 함

### NPM (Node Package Manger)

- 자바스크립트 언어를 위한 패키지 관리자(python의 pip처럼)
- Node.js의 기본 패키지 관리자

<br>

## Babel & Webpack

### Babel

- Javascript compiler

- 자바스크립트의 ECMA2015+ 코드를 이전 버전으로 번역해주는 도구

  -> 특정 브라우저에서 동작하지 않는 상황 해결할 수 있게 도와줌

### Webpack

- static module bundler
  - bundling: 모듈 의존성 문제를 해결해주는 작업
  - bundler: 모듈 의존성 문제를 해결해주는 일을 하는 도구. 여러 모듈을 하나로 묶어주고, 묶인 파일은 하나(혹은 여러 개)로 합쳐짐
- 모듈 간 의존성 문제 해결을 위해 사용
  - 의존성 문제: 특정 문제가 어떤 모듈 간에 발생한 건지 파악하기 어려운 상황

### Vue 프로젝트 구조

- node_modules
  - node.js 환경의 여러 의존성 모듈
- public/index.html
  - Vue 앱의 뼈대가 되는, 실제 제공되는 단일 html 파일
  - public/index.html의 코드를 건드는 일은 거의 없을 것!
- src/assets
  - webpack에 의해 빌드된 정적 파일
- src/components
  - 하위 컴포넌트들
- src/App.vue
  - 최상위 컴포넌트
- src/main.js
  - webpack이 빌드를 시작할 때 가장 먼저 불러오는 entry point
  - Vue 전역에서 활용할 모듈을 등록할 수 있음
- package.json
  - 프로젝트의 종속성 목록과 지원되는 브라우저에 대한 구성옵션 포함
- package-lock.json
  - node_modules에 설치되는 모듈과 관련된 모든 의존성을 설정 및 관리
  - 다른 컴퓨터에서 정확히 동일한 종속성을 설치할 수 있도록 보장(자동으로 생성&관리됨)

<br>

## :star: Pass props & emit event

### 컴포넌트 작성

- Vue app은 자연스럽게 중첩된 컴포넌트 트리로 구성됨

  -> 부모-자식 관계로 구성된 컴포넌트 간에 의사소통이 필요

  -> pass props & emit event

- 부모는 자식에게 **데이터**를 전달(Pass props)하고, 자식은 **이벤트**를 통해 부모에게 메세지를 보냄(Emit event)

- 컴포넌트 구조
  - 템플릿 (HTML)
  - 스크립트 (JavaScript)
  - 스타일 (CSS)

### :exclamation: 컴포넌트 등록 3단계

```vue
<template>
  <div>
    <!-- 3. 보여주기(카멜 케이스로 사용해도 됨) -->
    <TodoListItem
      v-for="todo in todos" 
      :key="todo.id" 
      :todo="todo"
    />
  </div>
</template>

<script>
// 1. 불러오기
import TodoListItem from './TodoListItem.vue'

export default {
  name: 'TodoList',
  components: {
      // 2. 등록하기
    TodoListItem
  }
}
</script>
```

### Props

#### Static Props 작성

- 자식 컴포넌트에 보낼 prop 데이터 선언

  ```vue
  // App.vue
  
  <template>
    	<div id="app">
          <img src="./assets/logo.png">
          <!-- 해당하는 컴포넌트의 태그 안에서 prop-data-name="data"-->
          <about my-message="This is prop data"></about>
      </div>
  </template>
  ```

- prop 데이터 수신 후 사용

  ```vue
  // About.vue
  
  <template>
  	<div>
          <!-- 수신한 prop 데이터 사용 -->
      	<h2>{{ myMessage }}</h2>
      </div>
  </template>
  
  <script>
  export default {
      name: 'About',
      // 수신할 prop 데이터 선언
      props: {
          myMessage: {
              type: String
          }
      }
  }
  </script>
  ```

#### Dynamic Props 작성

- v-bind directive를 이용해 자식 컴포넌트에 보낼 데이터를 동적으로 바인딩 (수신 및 사용 방법은 같음)

  ```vue
  <template>
    <div>
      <h2>AppParent</h2>
      <!-- 변수랑 연결할 땐 v-bind -->
      <!-- 이렇게 작성하면 parentData가 업데이트 될 때마다 자식 데이터로도 전달됨 -->
      <AppChild 
        :parent-data="parentData"
      />
    </div>
  </template>
  
  <script>
  import AppChild from './AppChild.vue'
  
  export default {
    name: 'AppParent',
    components: {
      AppChild
    },
    // **각 인스턴스가 모두 같은 data 객체를 공유하지 않도록 새로운 data 객체 리턴 -> 함수로 작성!!**
    data: function() {
        return {
            parentData: 'This is parent Data'
        }
    }
  }
  </script>
  ```

#### Props 이름 컨벤션

- 선언할 땐 camelCase, 템플릿에선 kebab-case

  ```html
  <!-- prop 데이터 이름: kebab-case -->
  <!-- 데이터 선언할 때: camelCase-->
  <AppChild :parent-data="parentData" />
  ```

#### Props 시 주의할 점

- 숫자를 전달하려면 Static 구문이 아니라 v-bind 사용할 것

  ```html
  <!-- Static 구문: 문자열 "1" 전달 -->
  <about number-data="1"></about>
  <!-- v-bind: 숫자 1 전달 -->
  <about :number-data="1"></about>
  ```

#### 단방향 데이터 흐름

- 모든 props는 상위 속성 -> 하위 속성으로의 단방향 바인딩 형성

- 부모의 속성이 변경되면 자식 속성에게 전달되지만, 반대 방향으로는 불가능

  -> 자식 요소가 부모 요소의 상태를 변경하여 데이터 흐름을 이해하기 어렵게 만드는 일 방지

<br>

### Emit Event

- `$emit('eventName'[, 추가인자])`
  - 현재 인스턴스에서 이벤트 트리거
  - 부모 컴포넌트는 v-on(`@`)을 사용해서 자식 컴포넌트에서 보낸 이벤트 청취

#### Emit event 작성

- 현재 인스턴스에서 `$emit` 인스턴스 메서드를 사용해 이벤트 트리거

  ```vue
  <template>
    <div>
      <h2>AppChild</h2>
      <input type="text" @input="inputChildData">
      <p>parentData : {{ parentData }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: 'AppChild',
    props: {
      parentData: {
        type: String,
        required: true
      }
    },
    methods: {
      inputChildData(event) {
        // input-child-data 이벤트 트리거
        this.$emit('input-child-data', event.target.value)
      }
    }
  }
  </script>
  ```

- 부모 컴포넌트는 v-on directive를 사용해서 자식 컴포넌트가 보낸 이벤트 청취

  ```vue
  <template>
    <div>
      <h2>AppParent</h2>
      <!-- 자식 컴포넌트에서 보낸 이벤트 청취 -->
      <AppChild
        :parent-data="parentData"
        @input-child-data="inputChildData"
      />
    </div>
  </template>
  
  <script>
  import AppChild from './AppChild.vue'
  
  export default {
    name: 'AppParent',
    components: {
      AppChild
    },
    methods: {
      inputChildData(newChildData) {
        console.log(`AppChild로부터 ${newChildData}를 받음`)
      }
    }
  }
  </script>
  ```

#### event 이름 컨벤션

- 컴포넌트, props와 달리 이벤트는 자동 대소문자 변환 X

- DOM 템플릿의 v-on 이벤트 리스너는 항상 자동으로 소문자 변환되므로 이벤트 이름은 **kebab-case** 사용할 것!

  ```vue
  <script>
  export default {
    name: 'VideoList',
    methods: {
      onSelectVideo: function (video) {
        // kebab-case!!!
        this.$emit('select-video', video)
      }
    }
  }
  </script>
  ```

  ```html
  <!-- @이벤트 이름(kebab-case)="실행할 메서드명(camelCase)" -->
  <video-list @select-video="onVideoSelect"></video-list>
  ```

<br>

## Vue Router

- 라우트에 컴포넌트를 매핑한 후, 어떤 주소에서 렌더링 할 지 알려줌
- SPA 상에서 라우팅을 쉽게 개발할 수 있는 기능 제공 - 마치 페이지를 이동하는 것 같은 경험을 제공
  - router: 위치에 대한 최적의 경로를 지정하여 이 경로를 따라 데이터를 다음 장치로 전향시키는 장치

- 사용 방법: Vue router plugin 설치

  ```bash
  vue add router
  ```

  - App.vue를 덮어씌우게 되므로 라우터 추가하기 전에 작성한 내용 있다면 미리 커밋해두기

#### Vue Router로 인한 변화

- App.vue

  ```vue
  <template>
    <div id="app">
      <div id="nav">
        <router-link :to="{ name: 'Home' }">Home</router-link> |
        <!-- 이렇게도 가능 -->
        <!-- <router-link to="/">Home</router-link> | -->
        <router-link :to="{ name: 'About' }">About</router-link> |
        <router-link :to="{ name: 'TheLotto', params: { lottoNum: 6} }">TheLotto</router-link>
      </div>
      <!-- router view! -->
      <router-view/>
    </div>
  </template>
  ```

  - `<router-link>`
    - 목표 경로는 `to` prop으로 전달됨
    - HTML5 히스토리 모드에서 router-link는 클릭 이벤트 차단 -> 브라우저가 페이지를 다시 로드하지 않게 함
  - `<router-view>`
    - 주어진 라우트에 대해 일치하는 컴포넌트 렌더링
    - 실제 컴포넌트가 DOM에 부착되어 보이는 자리

- router/index.js

  ```js
  import Vue from 'vue'
  import VueRouter from 'vue-router'
  // 1. import
  import Home from '../views/Home.vue'
  import About from '../views/About.vue'
  import TheLotto from '../views/TheLotto.vue'
  
  Vue.use(VueRouter)
  
  const routes = [
    // 2. 라우트 작성
    {
      path: '/',
      name: 'Home',
      component: Home
    },
    {
      // 끝나는 슬래시는 장고가 고집하는 것! router path 작성할 땐 끝나는 슬래시 X
      path: '/about',
      name: 'About',
      compoment: About,
    },
    {
     	// 동적 인자 전달은 이렇게 ':' 사용
      // 컴포넌트에서 this.$route.params로 사용 가능
      path: '/lotto/:lottonum',
      name: 'TheLotto',
      component: TheLotto
    }
  ]
  ```

- views 디렉토리 생성

  - *라우터(index.js)에 매핑되는 컴포넌트는 views 디렉토리에 작성. 해당 컴포넌트들의 하위 컴포넌트들은 components 폴더에 작성!*

#### History mode

- HTML History API를 사용해서 router를 구현한 것

- 브라우저의 히스토리는 남기지만 실제 페이지는 이동하지 않는 기능 지원

  -> 페이지를 다시 로드하지 않고 URL 탐색 가능

  -> SPA의 단점 중 하나인 "URL이 변경되지 않음"을 해결

#### 경로 작성 방법

1. Named Routes

   선언적 방식

   이름(router/index.js에서)을 갖는 라우트의 경우 이렇게 작성 가능

   ```html
   <router-link :to="{ name: 'Home' }">Home</router-link>
   ```

2. 프로그래밍 방식 네비게이션

   ```vue
   // TheLunch.vue
   
   <template>
     <div>
       <h1>점심메뉴</h1>
       <button @click="getMenu">Pick Lunch</button>
       <p>{{ selectedMenu }}</p>
       <br>
       <h2>로또를 뽑아보자</h2>
       <button @click="lottoLink">Pick Lotto</button>
     </div>
   </template>
   
   <script>
   import _ from 'lodash'
   
   export default {
     name: 'TheLunch',
     data: function () {
       return {
         selectedMenu: ''
       }
     },
     methods: {
       getMenu: function () {
         const menus = ['초밥', '칼국수', '회덮밥', '피자', '돈까스']
         this.selectedMenu = _.sample(menus)
       },
       // 이 부분! //
       lottoLink: function () {
         // Vue 인스턴스(this) 내부에서 $router로 라우터 인스턴스에 접근 가능
         // -> 다른 URL로 이동하려면 this.$router.push 호출 가능
         // router-link를 클릭할 때 내부적으로 호출되는 메서드
         this.$router.push({ name: 'TheLotto', params: { lottoNum: 6 }})
       }
     }
   }
   </script>
   ```

   ```vue
   // TheLotto.vue
   
   <template>
     <div>
       <h1>로또 번호 추첨</h1>
       <!-- 컴포넌트에서 이렇게 사용-->
       <h2>{{ $route.params.lottoNum }}개의 번호를 추첨합니다.</h2>
     </div>
   </template>
   ```

#### Vue Router가 필요한 이유

1. SPA 등장 이전

   - 서버가 모든 라우팅을 통제 -> 요청 경로에 맞는 HTML 제공
2. SPA 등장 이후

   - 서버는 index.html 하나만 제공
   - 이후 모든 처리는 HTML 위에서 JS 코드를 활용해서 진행 (요청에 대한 처리를 더 이상 서버가 하지 않음)
3. 라우팅 처리 차이

   - SSR (Server Side Rendering)

     - 라우팅 처리에 대한 결정권이 서버에 있음
   - CSR (Client Side Rendering)
   
     - 라우팅 처리에 대한 결정권을 클라이언트가 가짐
   
     - 클라이언트는 더 이상 *서버로 요청을 보내지 않음.* 응답받은 HTML 문서 안에서 주소가 변경되면 특정 주소에 맞는 컴포넌트 렌더링
   - Vue Router: 라우팅 결정권을 가진 Vue.js에서 라우팅을 편리하게 할 수 있는 툴을 제공하는 라이브러리

<br>

## Youtube Project

### 환경변수 설정

- `NODE_ENV`, `BASE_URL`, `VUE_APP_`으로 시작하는 변수만 가능
- .env.local에 작성
- 환경 변수: 컴퓨터에서 동작하는 방식에 영향을 미치는 동적인 값들의 모임