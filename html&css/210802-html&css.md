### 목차

- [HTML & CSS](#html--css)
- [HTML](#html)
  * [HTML(Hyper Text Markup Language)](#htmlhyper-text-markup-language)
  * [HTML 기본 구조](#html-기본-구조)
  * [HTML 문서 구조화](#html-문서-구조화)
- [CSS: Cascading Style Sheets](#css-cascading-style-sheets)
  * [CSS 정의 방법](#css-정의-방법)
  * [CSS 선택자](#css-선택자)
  * [CSS 단위](#css-단위)
  * [CSS Box model](#css-box-model)
  * [CSS Display](#css-display)
  * [CSS Position](#css-position)
  * [+) Emmet](#-emmet)

<br>

## HTML & CSS

- 웹 표준을 만드는 곳: W3C, WHATWG

<br>

## HTML

<br>

### HTML(Hyper Text Markup Language)

- Hyper Text

  : 웹에서 하이퍼 링크(참조)를 통해서 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트 (과거에는 동일 선상에 있는 이전 페이지, 다음 페이지로만 이동했음)

  (Hyper Text가 쓰인 기술들 중 가장 중요한 2가지: http, html)

- Markup

  : 텍스트 하나하나에 역할을 부여하는 것(텍스트를 구조화)

  이건 제목이다~라고 <h1></h1> 달아주고 본문은 <p></p> 마킹해주는 것

- Markup Language (ex. HTML, Markdown)

  : 태그 등을 이용해서 문서/데이터의 **구조**를 명시하는 언어 (*프로그래밍 언어 X*)



### HTML 기본 구조

```html
<!-- 이 문서가 HTML5라는 걸 알려줌-->
<!DOCTYPE html>
<!--문서의 디폴트 언어 설정-->
<!--html 요소: HTML 문서의 최상위 요소-->
<html lang="ko">
    <head>
        <!--해당 문서 정보를 담음. 브라우저에 나타나지 않음-->
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        <!--브라우저 화면에 나타나는 정보-->
    </body>
</html>
```

- OG: Open Graph

  - 메타 데이터를 표현하는 새로운 규약: Open Graph Protocol

  - 페이스북이 개발
  - url을 공유했을 때 네모칸으로 나타나는 간단한 정보
  - html문서의 meta 태그를 이용해 head에 작성



- DOM(Document Object Model) 트리

  - 문서의 구조화된 표현을 제공: 프로그래밍 언어가 구조에 객체로서 접근할 수 있도록 하여 문서 구조, 스타일 내용 등을 변경할 수 있게 도움

  - 각 태그를 객체로서 접근할 수 있도록 트리화 한 것

    -> 웹 페이지의 객체 지향 표현 (`<html>` 아래에 `<head>`, `<body>` 등이 있는 것처럼 트리화)

  - 2spaces로 들여쓰기



- 요소(element) = 태그 + 내용
  - 오류를 반환하지 않고 레이아웃이 깨진 상태로 출력
- 속성(attribute)
  - 속성 이름과 값이 key-value 형태로 되어 있음
  - 공백 없이, **쌍 따옴표** 사용! (안 지켜도 에러나진 않지만 지키자)
  - 태그와 상관없이 사용 가능한 global attribute도 있음

+) 웹에 대해 구글링 할 때 MDN 키워드 넣어서 하기



- **시맨틱 태그**
- HTML5에서 의미론적 요소를 담은 태그
  - 개발자, 사용자 뿐만 아니라 검색엔진 등에 의미 있는 정보 그룹을 태그로 표현
- 단순히 구역 나누는 게 아니라 의미를 갖는!
  - 시맨틱 태그 종류 hws에서 찾아서 적기!!!
  - `header`, `nav`, `aside`, `section`, `article`, `footer`

- 시맨틱 웹
  - 기존에 단순한 데이터의 집합이었던 웹페이지를 의미와 관련성을 갖는 거대한 데이터베이스로 구축하고자 하는 발상



### HTML 문서 구조화

- form
  - 사용자로부터 입력을 받고 보내기 위함
  - 보통 input 태그와 함께 사용됨
  
  ```html
  <body>
    <!--id에 대한 게 for-->
    <label for="username">아이디</label>
    <input type="text" id="username">
    <label for="password">비밀번호</label>
    <input type="password" id="password">
  </body>
  </html>
  ```
  
  

<br>

## CSS: Cascading Style Sheets

<br>

### CSS 정의 방법

1. 인라인

   ```css
   <h1 style="color: blue; font-size: 100px;">Hello<h1>
   ```

2. 내부 참조 - `<style>`

   ```css
   <head>
     <style>
       h1 {
   	  color: blue;
         font-size: 100px;
       }
     </style>
   </head>
   ```

3. 외부 참조 - 분리된 css 파일

```css
<head>
  <title>Document</title>
  /* head 내 link를 통해 외부 css파일 불러오기 */
  <link rel="stylesheet" href="mystyle.css">
</head>
```



### CSS 선택자

- 기본 선택자
  - `* {}` : 전체 선택자
  - `h2 {}`, `h2, h3 {}` : 요소 선택자 - 태그를 직접 선택
  - `.py3 {}` : 클래스 선택자
  - `#purple {}` : id 선택자 - unique하게 사용
- 결합자
  - `.box > p {}` : 자식 결합자(바로 아래 p 요소)
  - `.box p {}` : 자손 결합자(하위의 모든 p 요소)
  - `p ~ span {}` : 일반 형제 결합자(형제 요소 중 뒤에 있는 모든 span)
  - `p + span {}` : 인접 형제 결합자(형제 요소 중 바로 뒤 span요소)



- css 적용 우선순위

  ```css
  /* !important > 인라인 > id > class > 요소 > 소스 순서 */
  ```

  - 소스 순서 주의!! `class="blue green"`  클래스 순서가 아니라 style에 작성된 코드 순서 의미하는 것



- **css 상속**

  - 상속 되는 것

    : text 관련 요소(font, color, text-align), opacity, visibility 등

  - 상속 안 되는 것

    : box model 관련 요소(width, height, margin, padding, border, box-sizing, display), position 관련 요소(position, top/right/bottom/left) 등



### CSS 단위

- 크기 단위
  - px: 고정적인 단위
  - %: 백분율 단위. 가변적인 레이아웃에서 자주 사용
  
  - em: 상속 영향받음. 배수 단위/요소 지정 사이즈에 상대적
  - rem: 상속 영향 X. **최상위 요소(html) 사이즈 기준으로 배수 단위 가짐**
  - viewport: 디바이스의 viewport를 기준으로 상대적 사이즈 결정

- 색상 단위

  - 색상 키워드(대소문자 구분 X), RGB 색상, HSL 색상

    +) rgba, hsla에서 a는 alpha(투명도)



### CSS Box model

- Box model

  - 모든 html 요소는 box 형태로 되어 있음 -> display 속성을 가짐

  - 하나의 박스는 네 부분으로 구성

    : content, padding, border, margin
  
  - Content
    - 가로는 width, 세로는 height
  - Padding
    - 안쪽 여백. content와 border 사이의 공간을 나타냄
  - Border
    - 테두리
  - Margin
    - 바깥쪽 여백



- margin/padding/border shorthand

  - shorthand : 상 우 좌 하 시계방향
  
  ```css
  /* margin shorthand */
  .margin-2 {
      /* 상하 좌우 */
      margin: 10px 20px;
  }
  .margin-3 {
      /* 상 좌우 하 */
      margin: 10px 20px 30px;
  }
  
  .border {
      border-width: 2px;
      border-style: dashed;
      border-color: black;
  }
  
  /* border shorthand */
  .border {
      border-top-left-radius: 10px;
      border-bottom-right-radius: 10px;
  }
  
  .border {
      /* 굵기 스타일 색상 */
      border: 2px solid black;
  }
  
  /* margin 상하 0 좌우 auto로 주면 좌우 가운데정렬 */
  .box2 {
      width: 500px;
      border: 2px solid black;
      padding: 20px 30px;
      margin: 0 auto;
  }
  ```



- Box sizing

  ```css
  .box {
        /* 컨텐트 너비 100 + 마진 20 * 2 + 보더 2 = 총 너비 142px*/
        /* width를 100으로 설정했더라도! */
        /* 기본 box-sizing이 content-box이기 때문 */
        width: 100px;
        margin: 10px auto;
        padding: 20px;
        border: 1px solid black;
        color: white;
        text-align: center;
        background-color: blueviolet;
      }
  
  .box-sizing {
        /* 이렇게 box-sizing을 border-box로 변경 */
        /* => border까지 합해서 width 설정 */
        box-sizing: border-box;
        margin-top: 50px;
      }
  
  /* 그래서 그냥 모든 요소에 border-box 기준으로 사이즈 잡게 설정하기도 함 */
  * {
      box-sizing: border-box;
  }
  ```



- 마진 상쇄

  : 블록 A의 top, 블록 B의 bottom 마진 중 큰 마진으로 겹쳐짐



### CSS Display

- display

  - `display: block` 
    - 화면 크기 전체의 가로폭 차지(줄 바꿈 O). 안에 인라인 레벨 요소 들어갈 수 있음
    - 따로 width를 준 경우 남은 공간은 알아서 margin으로 채움
    - 따로 height을 주지 않은 경우 자식 요소들의 height의 합이 height가 됨
    - width, height, padding, border, margin 모두 가능
    - 정렬방법: `text-align: left;`, `text-align: right;`, `text-align: center;`
  - `display: inline`
    - content 너비만큼만 가로폭 차지(줄 바꿈 X)
    - 공간이 모자르면 알아서 줄바꿈
    - **width, height, padding/border/margin -top/-bottom 설정 불가** -> 인라인의 흐름을 박살내기 때문! left right은 인라인에서 좌우 간격만 띄워주므로 흐름에 방해가 되지 않음.
    - 정렬방법: `margin-right: auto;`, `margin-left: auto;`, `margin-right: auto; margin-left: auto;`
  - `display: inline-block`
    - inline처럼 한 줄에 표시 가능 & block처럼 width, height, margin 지정 가능
  - `display: none`: 화면에 표시 X(공간 차지도 안 함)
  
    - +) `visibility: hidden`: 공간 차지 하지만 화면에만 안 보임



### CSS Position

- `static`: 기본값 - 좌측 상단 배치(부모 요소 내에서 배치 시 부모요소 위치 기준으로 배치)

  <아래는 top, bottom, left, right을 사용해 이동 가능>

- `relative` : 상대 위치

  자신의 static 위치를 기준으로, **static 위치 공간 차지하며** 이동

  (본인은 겹쳐질 수 있지만 다른 요소는 원래 static 공간 이후에 배치)

   (blue position이 relative여도 top, left 지정해서 여기에 놓겠다!하면 pink가 absolute니까 덮어쓰기 가능)

- `absolute` : 절대 위치

  레이아웃에 공간 차지 X. 가장 가까이 있는 부모/조상 요소를 기준으로 이동(없는 경우 body에 붙음)

- `fixed` : 고정 위치

  레이아웃에 공간 차지 X. 부모요소 관계 없이 viewport 기준으로 위치 고정

- +) `sticky` : 스크롤을 따라 화면에 고정



### +) Emmet

- HTML&CSS 작성 시 보다 빠른 마크업을 위해 사용되는 오픈 소스
- 단축키, 약어 등을 사용

