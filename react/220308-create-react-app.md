[toc]

# 만들면서 배우는 리액트: 기초

## 실무 개발환경 만들기

### 실무 개발환경 만들기

1. 프로덕션 버전 리액트 라이브러리 사용

   - 개발용 경고 등이 불포함되어 용량이 작음

   - 코드

     ```react
     // 개발용 리액트 라이브러리
     <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
     <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>
     // 프로덕션용 리액트 라이브러리
     // react.production.~~ 이런 식으로 되어 있음
     ```

2. 바벨 떼기

   - 브라우저에서 매번 바벨을 이용해 JS로 통역하는 게 아니라 이미 통역된 JS를 올림

     - 어떻게? create-react-app

   - create-react-app (참고: [새로운 React 앱 만들기](https://ko.reactjs.org/docs/create-a-new-react-app.html#create-react-app))

     - 리액트 초기 개발에 필요한 모든 것을 자동으로 해줌
       - 간단한 앱 껍데기
       - 리액트 라이브러리 셋업 (개발용/프로덕션용으로 알아서 셋업)
       - 웹팩 셋업 (참고: [웹팩이란?](https://joshua1988.github.io/webpack-guide/webpack/what-is-webpack.html))
         - 대표적인 웹팩 셋업
           - 라이브 서버 (vscode extension live server처럼)
           - 저장할 때마다 JSX -> JS
       - 테스트 셋업
       - 빌드 셋업
         - JS로 변환, 코드 용량 최소화, 프로덕션 라이브러리 설정 등

   - creact-react-app

     - `vue create 프로젝트명`과 비슷함

     - 코드

       ```bash
       $ npx create-react-app my-app
       $ cd my-app
       $ npm start
       ```

### create-react-app 폴더 구조 뜯어보기

- package.json: 프로젝트가 사용 중인 라이브러리들
  - scripts: 원하는 명령어 저장

### 지금까지 만든 앱 create-react-app으로 옮기기

- 지금 cra에 있는 react 코드를 js 코드로 변환하는 빌드 과정이 필요
  - `npm i gh-pages`
  - package.json
    - `"scripts": { ..., deploy": "gh-pages -d build"}`
    - `"homepage": "https://yujinwon-dev.github.io/react-cat-jjal-maker",`
  - `npm run build`
  - `npm run deploy`: 방금 build한 build 폴더가 github pages로 올라가게 됨

### +) netlify 배포

- 빌드

  ```bash
  npm run build
  ```

- netlify-cli 설치

  ```bash
  npm install netlify-cli -g
  ```

- netlify 배포

  ```bash
  netlify deploy
  ```

  - publish directory: `build` 입력

- 참고: [cra Deployment Netlify](https://create-react-app.dev/docs/deployment#netlify)
