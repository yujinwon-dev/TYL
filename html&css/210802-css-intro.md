### 목차

- [CSS: Cascading Style Sheets](#css-cascading-style-sheets)

  * [CSS 정의 방법](#css-정의-방법)

  * [CSS 선택자](#css-선택자)

  * [CSS 단위](#css-단위)

  * [CSS Box model](#css-box-model)

  * [CSS Display](#css-display)

  * [CSS Position](#css-position)

  * [+) Emmet](#-emmet)

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

- `static`: 모든 요소의 기본값 - 좌측 상단 배치(부모 요소 내에서 배치 시 부모요소 위치 기준으로 배치)

  <아래는 top, bottom, left, right을 사용해 이동 가능>

- `relative` : 상대 위치

  자신의 static 위치를 기준으로, **static 위치 공간 차지하며** 이동

  (본인은 겹쳐질 수 있지만 다른 요소는 원래 static 공간 이후에 배치)

   (blue position이 relative여도 top, left 지정해서 여기에 놓겠다!하면 pink가 absolute니까 덮어쓰기 가능)

- `absolute` : 절대 위치

  레이아웃에 공간 차지 X. static이 아닌, 가장 가까이 있는 부모/조상 요소를 기준으로 이동(없는 경우 body에 붙음)

  float와 동일한 점

  - 붕 떠서 부모에 높이가 안 잡힘

  - `display: block`으로 신분 상승
  - 하지만 margin으로 자동 채움을 하지 않음

  float와 차이점

  - inline요소가 알아채지 못하고 그냥 붕 뜸

- `fixed` : 고정 위치

  레이아웃에 공간 차지 X. 부모요소 관계 없이 **viewport 기준**으로 위치 고정

  absolute와 동일한 점

  - 붕 떠서 부모에 높이가 안 잡힘

  - `display: block`으로 신분 상승
  - 하지만 margin으로 자동 채움을 하지 않음

  absolute와 차이점

  - viewport를 기준으로 위치함 (viewport: 내가 현재 보고있는 화면의 크기)

- +) `sticky` : 스크롤을 따라 화면에 고정

- +) z-index: position된 요소들의 수직 레벨을 알려주는 property

- +) absolute, fixed 가운데 배치 할 경우 top, left에 추가적으로 `transform: translate(-50%, -50%);`

  왼쪽 모서리 위치를 기준으로 가운데 정렬되므로 -50%씩 옮겨줌

### +) Emmet

- HTML&CSS 작성 시 보다 빠른 마크업을 위해 사용되는 오픈 소스
- 단축키, 약어 등을 사용

