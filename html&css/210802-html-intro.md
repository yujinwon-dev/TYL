### 목차

- [HTML](#html)
  * [HTML(Hyper Text Markup Language)](#htmlhyper-text-markup-language)
  * [HTML 기본 구조](#html-기본-구조)
  * [HTML 문서 구조화](#html-문서-구조화)

<br>

## HTML

웹 표준을 만드는 곳: W3C, WHATWG

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
  
