### 목차

- [HTML tags](#html-tags)
  * [1.](#1)
    + [HTML이 왜 중요한가요?](#html--)
    + [HTML을 시맨틱하게 작성해야 하는 이유](#html----)
  * [2.](#2)
    + [제목과 문단 Headings and Paragraph](#--headings-and-paragraph)
    + [강조 Emphasis](#-emphasis)
    + [링크 Anchor](#-anchor)
    + [이미지 Image](#-image)
    + [목록 List](#-list)
    + [정의 목록 Description List](#--description-list)
    + [인용 Quotations](#-quotations)
    + [흑마법 Div & Span](#-div--span)
    + [Form(1) - Form](#form1---form)
    + [Form(2) - Input](#form2---input)
    + [Form(3) - Label](#form3---label)
    + [Form(4) - Radio & Checkbox](#form4---radio--checkbox)
    + [Form(5) - Select & Option](#form5---select--option)
    + [Form(6) - Textarea](#form6---textarea)
    + [Form(7) - Buttons](#form7---buttons)
    + [표 Table(1) - 기본 구조](#-table1----)
    + [표 Table(2) - 심화](#-table2---)
    + [미디어 파일 Media](#--media)
      - [Audio](#audio)
      - [Video](#video)
      - [iframe](#iframe)
    + [기타 Etc](#-etc)
    + [Doctype & Document Structure](#doctype--document-structure)
    + [Title, Link, Style & Script](#title-link-style--script)
    + [메타 데이터 Meta](#--meta)

<br/>

# HTML tags

## 1.

### HTML이 왜 중요한가요?

- URL을 입력하면

- -> 해당 페이지를 보기 위해 필요한 리소스를 요청하고

- -> 서버가 리소스를 보내줌(HTML, CSS, JS 등등)

  ![image-20220202233855297](C:\Users\multicampus\Desktop\wonyu\works\til\html&css\220223-html-tags.assets\image-20220202233855297.png)

- 그래서 FE에서 HTML, CSS, JS를 공부하는 것

- 웹 페이지에 보이는 모든 것들은 **기승전 HTML 태그의 결과물**. 그래서 HTML부터 탄탄히 쌓아가야 함!

- **문서의 구조**와 **정보의 위계**가 명확하게 보이는 HTML 코드를 작성하자! (Semantic Markup)

- Semantic하게 작성하면 검색 엔진 최적화(SEO)에도 도움이 됨



### HTML을 시맨틱하게 작성해야 하는 이유

- `<div>` 쳐발쳐발 하지 말자.. 다채로운 태그를 쓰면 나에게도 동료에게도 유익함

- 시맨틱하지 않다면...

  ```html
  <p>제목입니다</p>
  <p>
      <p>리스트 요소1</p>
      <p>리스트 요소2</p>
      <p>리스트 요소3</p>
  </p>
  ```

<br>

## 2.


### 제목과 문단 Headings and Paragraph

- 제목에 해당하는 부분에는 Heading Tag(`<h1>`, `<h2>` 등)
- 문단에 대해서는 `<p>` -> paragrahph



### 강조 Emphasis

- 강조하고자 하는 부분에서 사용. p 태그 내부에서도 가능. 둘 중에 끌리는 걸로 쓰면 됨.
- 글씨가 두껍다 두껍지 않다보다도 브라우저한테 이 부분이 중요하다고 알려줬다는 게 중요

- `<em></em>`: italic
- `<strong></strong>`: bold

+) `<br />`: break 태그



### 링크 Anchor

- 필수 어트리뷰트 href: hypertext reference(문서 주소값)

- href 주소값 표기 방법

  1. 웹 URL(절대/상대)

     ```html
     <a href="https://www.google.com/">Google</a>
     <a href="./index.html">Google</a>
     ```

  2. 페이지 내 이동

     - 이동하고자 하는 곳의 id값을 적어주면 됨

     ```html
     <a href="#hello">To Hello</a>
     ```

  3. 메일 쓰기

     ```html
     <a href="mailto:메일주소"></a>
     ```

     ![image-20220203231747878](C:\Users\multicampus\Desktop\wonyu\works\til\html&css\220223-html-tags.assets\image-20220203231747878.png)

  4. 전화 걸기

     ```html
     <a href="tel:전화번호"></a>
     ```

- 또다른 어트리뷰트: target

  - 새로운 탭에서 열렸으면 좋겠을 때

  ```html
  <a target="_blank">새 탭에서 열기</a>
  ```




### 이미지 Image

- 필수 어트리뷰트
  - src: 경로 or 주소
  - alt: alternate text - 이미지가 안 뜰 때 대체 텍스트가 있어야 사용자 경험 더 나아짐. 스크린리더를 사용할 때도 해당 값이 사용됨



### 목록 List

- 2가지 종류의 리스트

  - ol: ordered list(순서가 중요한 목록)
  - ul: unordered list(순서가 중요하지 않은 목록)
  - 두 태그의 자식 요소는 **무조건 li만 가능**

- 리스트 내부의 항목

  - li: list item

- 리스트 스타일 떼기

  ```html
  <ul style="list-style-type: none;">
    <li>
      웹 개발자
    </li>
    ...
  </ul>
  ```



### 정의 목록 Description List

- 용도

  1. 용어를 정의할 때
  1. key-value로 정보를 제공할 때

- 관련 태그들

  - dl: description list -> ul, ol같은 느낌
  - dt: key값
  - dd: description data -> key값에 대한 data
  - +) dfn: definition -> dt를 좀 더 구체적으로 정의하고 싶을 때

- dl 태그 내에서 하나의 정의 세트를 div로 묶어주는 것도 가능 (**div로만 가능!**)

  ![image-20220205231305704](C:\Users\multicampus\Desktop\wonyu\works\til\html&css\220223-html-tags.assets\image-20220205231305704.png)

- dd, dt를 여러개 쓸 수 있지만 dt - dd - dt 이런 식으로 번갈아 쓸 수는 없음



### 인용 Quotations

- 관련 태그

  - blockquote: 어떤 문단이나 내용 전체가 인용문일 때. q보다 자주 사용됨
  - q: 문장 내에 살짝 들어가는 인용문. 쌍따옴표가 생김

- 예시

  ```html
  <!-- 출처 url: cite 어트리뷰트에 기재 -->
  <blockquote cite="https://www.google.com/">
    우리가 겪을 수 있는 가장 아름다운 체험은 신비다. <br/>
    신비는 모든 참 예술과 과학의 근원이다.
    <!-- 출처: cite 태그 -->
    <cite>
      알버트 아인슈타인
    </cite>
  </blockquote>
  ```




### 흑마법 Div & Span

- 아무런 의미가 없음. css를 하면서 요소를 묶을 때 유용하게 쓰임.
- div: 어디에나 쓸 수 있음
- span: text level에서 어디든.. 텍스트의 일부를 그루핑할 때 많이 쓰임
- 정말 아무리 생각해도 떠오르는 의미 있는 태그가 없을 때 사용하려고 노력



### Form(1) - Form

- 사용자로부터 인풋을 받기 위한 태그
- 문법 주의! 함께 작성해야 할 어트리뷰트
  - action="API 주소"
  - method="GET|POST"



### Form(2) - Input

- 인풋 태그 사용시 type 어트리뷰트 필수

  ```html
  <input type="?" />
  ```

  - text, number, email, password, tel, file, radio..

- 타입 상관 없이 작성 가능한 어트리뷰트

  - `placeholder=""`
  - `minlength/maxlength=""`
  - `required`
  - `disabled`
  - `value=""`: 기본적으로 입력되어 있는 값

- `type="text"`

  - 한 줄 정도 분량의 인풋을 받을 수 있는 기본적인 형태

- `type="email"`

  - 인풋에 `@` 있는지 유효성 검사

- `type="password"`

- `type="url"`

  - url 간단한 유효성 검사

- `type="number"`

  - 문자 입력 안 됨.
  - 어트리뷰트
    - min
    - max

- `type="file"`

  - Choose File
  - 어트리뷰트
    - accept: 허용하고자 하는 파일 확장자 제한 ex)`accept=".png, .jpg"`



### Form(3) - Label

- 인풋에 대한 이름, 즉 라벨을 달아준다는 뜻. 폼 양식에 이름을 붙이는 태그

- for을 작성할 경우 라벨을 클릭하면 인풋에 focus됨. 사용성 up

- 문법 주의

  ```html
  <!-- 해당하는 인풋의 id를 라벨의 for에 적어줌 -->
  <!-- for을 작성하면 라벨을 클릭할 때 인풋에 focus됨. 사용성 up -->
  <label for="username"></label>
  <input type="text" id="username"/>
  ```



### Form(4) - Radio & Checkbox

- radio: 여러 개 중에 하나만 선택

  - 필수 어트리뷰트

    - name
    - value

  - `<input type="radio" />`에서 name attribute 설정해줘야 서로 연관되어 있다는 것을 파악 가능

    ```html
    <input type="radio" name="subscription" id="subscribed">
    <label for="subscribed">구독중</label>
    <input type="radio" name="subscription" id="unsubscribed">
    <label for="unsubscribed">미구독</label>
    ```

  - name, value가 key, value 형태로 서버에 전달됨 (url에서 확인 가능) -> value를 각각 다르게 지정해줘야 서버에서도 어떤 항목이 선택됐는지 확인 가능. 숫자든 문자든 가능.

    ```html
    <form action="" method="GET">
        <input type="radio" name="subscription" value="subscribed" id="subscribed">
        <label for="subscribed">구독중</label>
        <input type="radio" name="subscription" value="unsubscribed" id="unsubscribed">
        <label for="unsubscribed">미구독</label>
        <button>Submit</button>
    </form>
    ```

- checkbox: 여러 개 중에 다중 선택 가능

  ```html
  <form action="" method="GET">
      <input type="checkbox" id="html" name="skills" value="html">
      <label for="html">HTML</label>
      <input type="checkbox" id="css" name="skills" value="css">
      <label for="css">CSS</label>
      <input type="checkbox" id="js" name="skills" value="js">
      <label for="js">JavaScript</label>
      <button>Submit</button>
  </form>
  ```




### Form(5) - Select & Option

- name은 select에, value는 option에 작성

  ```html
  <form action="" method="GET">
      <!-- label은 select에 달아줌 -->
    <label for="skills">스킬</label>
    <!-- multiple 어트리뷰트: 다중 선택 가능 -->
    <select multiple name="skill" id="skills">
      <option value="HTML">HTML</option>
      <option value="CSS">CSS</option>
      <option value="JavaScript">JavaScript</option>
    </select>
    <button type="submit">submit</button>
  </form>
  ```



### Form(6) - Textarea

- 여러 줄에 걸친 인풋 가능

  ```html
  <label for="field">자기소개: </label>
  <textarea id="field" placeholder="자기소개를 입력하세요." required></textarea>
  ```

- 어트리뷰트가 있지만 css로 조절 가능하므로 꼭 기억하지는 않아도 됨

  - rows
  - cols



### Form(7) - Buttons

- 문법 주의! 필수 어트리뷰트 type
  - `type="button"`
    - 다양하게 쓸 수 있음
  - `type="submit"`
    - form 제출 용도일 경우
  - `type="reset"`
    - 인풋 작성한 것이 지워짐
    - 잘 쓰이는 어트리뷰트는 아님



### 표 Table(1) - 기본 구조

- table

  - 데이터를 담은 표를 만들 때 사용

- 구조

  ```html
  <table>
    <!-- 브라우저에게 좀 더 명확히 알려줌 -> table head -->
    <thead>
      <!-- table row -->
      <tr>
        <!-- cell -->
        <!-- 첫 row의 th에 따라 맞춰서 td를 적어줘야 함 -->
        <!-- 만약 th가 4개라면 아래에서 내용이 없더라도 td를 추가해주어야 함 -->
        <th>ID</th>
        <th>이름</th>
        <th>개발분야</th>
    	</tr>
    </thead>
    <!-- table body -->
    <tbody>
      <tr>
        <td>0001</td>
        <td>원유진</td>
        <td>FE</td>
      </tr>
      <tr>
        <td>0002</td>
        <td>김이박</td>
        <td>BE</td>
      </tr>
    </tbody>
    <!-- 테이블에 대한 총합/통계가 필요할 경우 작성 -->
    <tfoot></tfoot>
  </table>
  ```

### 표 Table(2) - 심화

```html
<table>
  <thead>
    <tr>
      <th></th>
      <th>월</th>
      <th>화</th>
      <th>수</th>
      <th>목</th>
      <th>금</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <!-- row에 대한 table header -->
      <th>1교시</th>
      <!-- &amp; -> escape code. 브라우저가 헷갈려할 수 있으므로 -->
      <!-- 여러 개의 row를 차지할 때는 rowspan -->
      <td rowspan="2">왕초보 HTML &amp; CSS</td>
      <td>모각코</td>
      <td rowspan="2">왕초보 HTML &amp; CSS</td>
      <td>모각코</td>
      <td rowspan="2">왕초보 HTML &amp; CSS</td>
    </tr>
    <!-- 두 번째 row가 가진 6개의 col에 대해 2, 4, 6번째 col은 이미 위에서 차지했음. 나머지 작성해줌 -->
    <tr>
      <th>2교시</th>
      <td rowspan="2">JavaScript 스킬업</td>
      <td rowspan="2">JavaScript 스킬업</td>
    </tr>
    <tr>
      <th>3교시</th>
      <td>JavaScript 시작반</td>
      <td>JavaScript 시작반</td>
      <td>JavaScript 시작반</td>
    </tr>
    <tr>
      <!-- 여러 col을 차지할 때는 colspan -->
      <td colspan="6">점심시간</td>
    </tr>
  </tbody>
</table>
```

- 어트리뷰트
  - `scope="row|col"`
    - `th` 가 row의 헤더인지 col의 헤더인지 알려줌



### 미디어 파일 Media

#### Audio

- 2가지 방법으로 작성 가능

  ```html
  <!-- 1 -->
  <audio src="./assets/audios/kimbug.mp3"></audio>
  
  <!-- 2: 이렇게 source 태그 따로 작성할 경우 type 작성 필수 -->
  <audio>
    <source src="./assets/audios/kimbug.wav" type="audio/wav">
  </audio>
  ```

- 사용자에게 재생이 안 될 경우를 대비

  ```html
  <audio controls>
    <source src="./assets/audios/kimbug.wav" type="audio/wav">
    <source src="./assets/audios/kimbug.mp3" type="audio/mpeg">
    <source src="./assets/audios/kimbug.ogg" type="audio/ogg">
    <p>당신의 브라우저를 버리시고 크롬을 사용하는 게 어떨까요?</p>
  </audio>
  ```

- 어트리뷰트

  - src: 필수 어트리뷰트
  - controls: 오디오 재생/음량 등의 설정
  - autoplay: 자동재생 설정
  - loop: 반복 재생

#### Video

- audio만 video로 바꾸면 됨! 거의 동일

  ```html
  <video autoplay>
    <source src="./assets/videos/kimbug.mov" type="video/mov">
    <source src="./assets/videos/kimbug.mp4" type="video/mp4">
    <a href="https://browsehappy.com/">브라우저를 업데이트 하시는 게 어떨까요?</a>
  </video>
  ```

#### iframe

- html 문서 안에 또 다른 html 문서/컨텐츠를 임베드 하고 싶을 때 사용
- 하지만 직접 작성할 일은 별로 없고 youtube/twitter 등을 share할 때 사용



### 기타 Etc

- abbreviation

  - 약자, 약어

  - hover 시 작성한 설명이 뜸

    ```html
    <p>너 혹시 <abbr title="사회인 게임 클럽">사인클</abbr> 알아?</p>
    ```

- address

  - 연락처에 관한 정보를 마크업 할 때 사용 가능
  - (물리적) 주소, URL, 이메일, 전화번호, SNS

- pre

  - preformatted text: 미리 formatted 된다

  - 코드에 작성한 대로 formatted 되어 보여짐

    ```html
    <p>
      안녕하세요
      반가워요
    </p>
    
    <pre>
    안녕하세요
    반가워요
    </pre>
    ```

    ![image-20220223155146165](C:\Users\multicampus\Desktop\wonyu\works\til\html&css\220223-html-tags.assets\image-20220223155146165.png)

- code

  - 꼭 pre 태그와 같이 쓸 필요는 없으나 여러 줄의 코드 작성 시 함께 씀

    ```html
    <code>
      console.log('hello yujin');
        var yujin = 'yujin';
      </code>
      
      <pre>
        <code>
    console.log('hello yujin');
      var yujin = 'yujin';
      </code>
    </pre>
    ```

    ![image-20220223155356494](C:\Users\multicampus\Desktop\wonyu\works\til\html&css\220223-html-tags.assets\image-20220223155356494.png)



### Doctype & Document Structure

- Doctype
  - 반드시 대문자로 작성
  - "브라우저야, 이 문서는 HTML5 버전으로 작성된 문서니까 거기에 맞춰서 렌더링 해줘"
  - `<!DOCTYPE html>` : 가장 최신 HTML5 버전을 사용하겠다는 뜻
- 이후 `<html>` 태그를 통해 html의 시작을 알려줌
- html 태그 바로 안에는 `<head>`, `<body>` 태그만 작성 가능
  - head: 사람의 뇌 같은 것. 웹 문서에 대해 눈에 보이지 않는 메타 데이터 선언할 때 사용
  - body: 웹 문서에서 보여주게 될 모든 컨텐츠

```html
<!DOCTYPE html>
<html>
    <head>
        
    </head>
    <body>
        
    </body>
</html>
```



### Title, Link, Style & Script

- title

  - html 문서의 대제목
  - **검색 최적화에 매우 중요**
  - title 잘 쓰는 방법
    1. 키워드 단순 나열은 비추. 무엇에 관한 내용인지 센스있게
    2. 페이지마다 그에 맞게 변경

- link

  - CSS 스타일시트를 첨부하는 태그
  - font 변경 시에도 사용

- style

  - HTML 문서 내에서 CSS 코드를 작성할 때 사용
  - styles.css 파일에 작성한 스타일보다 우선순위가 높음

- script

  - HTML 문서 내에 JavaScript 파일을 첨부할 때 사용

    ```html
    <script src="./app.js"></script>
    ```

  - script 태그 내에 js 코드 작성하는 것도 가능

  - 위 세 태그와 달리 **body에 작성**

    - 위 태그들은 가져오는 데에 시간이 걸리면 일단 스킵하고 다른 걸로 넘어감
    - 하지만 script 태그는 가져올 때까지 기다림. 그래서 body 안에서 모든 컨텐츠들이 로드가 된 후에 작성하는 게 좋음 



### 메타 데이터 Meta

- 필수 어트리뷰트

  - `name="메타데이터 종류"`
  - `content="메타데이터 값"`

- 코드

  ```html
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  ```

  - 화면 사이즈의 가로는 device 가로에 맞춤
  - 처음 보여줄 때의 배율은 1.0

  ```html
  <meta name="author" content="원유진">
  ```

  - 작성자를 알려줌

  ```html
  <meta name="keywords" content="김버그, 구름에듀, html강의">
  ```

  - 웹페이지의 핵심 키워드를 적음
  - 구글에서는 악용 가능성 때문에 keyword를 SEO에 사용하지 않는다고 하나, 브라우저에게 알려주기 위한 정보로서 의미는 있지 않을까?

  ```html
  <meta name="description" content="~~~">
  ```

  - 웹 페이지에 대한 설명
