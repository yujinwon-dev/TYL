### 목차

- [CSS selector](#css-selector)
  - [요소, 클래스, ID 선택자](#요소-클래스-id-선택자)
    - [요소 선택자 type selector](#요소-선택자-type-selector)
    - [클래스 선택자 class selector](#클래스-선택자-class-selector)
    - [ID 선택자 ID selector](#id-선택자-id-selector)
  - [속성 선택자 attribute selector](#속성-선택자-attribute-selector)
  - [자식, 자손, 형제 선택자](#자식-자손-형제-선택자)
    - [자식 선택자 child combinator](#자식-선택자-child-combinator)
    - [자손 선택자 descendant combinator](#자손-선택자-descendant-combinator)
    - [형제 선택자 sibling combinators](#형제-선택자-sibling-combinators)
  - [구조적 가상 클래스 선택자 Structural Pseudo-classes](#구조적-가상-클래스-선택자-structural-pseudo-classes)
    - [element:first-child](#elementfirst-child)
    - [element:last-child](#elementlast-child)
    - [element:nth-child(n)](#elementnth-childn)
  - [동적 가상 클래스 선택자 User Action Pseudo-classes](#동적-가상-클래스-선택자-user-action-pseudo-classes)
    - [element:hover](#elementhover)
    - [element:focus](#elementfocus)
    - [element:active](#elementactive)
  - [CSS 선택자 우선순위](#css-선택자-우선순위)

<br>

# CSS selector

## 요소, 클래스, ID 선택자

### 요소 선택자 type selector

- 예시

  ```css
  h1 {
      color: #0066ff;
  }
  strong {
      color: #ffc82c;
  }
  ```

### 클래스 선택자 class selector

- 여러 개의 요소에 같은 스타일을 적용하고 싶을 때
- 한 요소에 여러 개의 클래스를 줄 수 있음

- 예시

  ```css
  .blue {
      color: #0066ff;
  }
  /* div태그이고 box-0이자 box-1인 요소 */
  div.box-0.box-1 {
      display: flex;
  }
  ```

### ID 선택자 ID selector

- 단 한 개만 존재하는 요소에 스타일을 적용하고 싶을 때

- 예시

  ```css
  #wonyu {
      font-style: italic;
  }
  ```

<br>

## 속성 선택자 attribute selector

- 대괄호를 이용해서 선언하며, 대괄호 안에 속성 이름이 들어감

  ```css
  /* p 태그이면서 class 속성이 있다면 */
  p[class] {
  	color: silver;
  }
  
  /* p 태그이면서 class, id 속성이 있다면 */
  p[class][id] {
  	color: silver;
  }
  
  /* p 태그이면서 class 속성 값이 foo라면 */
  p[class="foo"] {
  	color: silver;
  }
  
  /* p 태그이면서 class 속성 값에 공백으로 구분한 "color" 단어가 포함된다면 */
  p[class~="color"] {
  font-style: italic;
  }
  
  /* p 태그이면서 class 속성 값이 "color"로 시작한다면 */
  p[class^="color"] {
  		font-style: italic;
  }
  
  /* p 태그이면서 class 속성 값이 "color"로 끝난다면 */
  p[class$="color"] {
  	font-style: italic;
  }
  
  /* p 태그이면서 class 속성 값에 "color"가 포함된다면 (클래스가 "colorful" 이어도 해당) */
  p[class*="color"] {
  	font-style: italic;
  }
  ```

<br>

## 자식, 자손, 형제 선택자

### 자식 선택자 child combinator

- 자식: **한 단계** 바로 내부에 있는 태그

- `parent > child`

- 예시

  ```css
  section > h1 {
      color: #ff4949;
  }
  ```

### 자손 선택자 descendant combinator

- 자손: **모든** 내부에 있는 태그

- `parent descendants`

- 예시

  ```css
  section h1 {
      color: #0066ff;
  }
  ```

### 형제 선택자 sibling combinators

- 형제: 같은 레벨에 있는 태그
- `parent + sibling` : 현제 요소의 **바로 다음에 오는 하나**의 형제
- `parent ~ sibling` : 현재 요소의 **다음에 오는** 형제들 중에 sibling에 해당하는 형제

<br>

## 구조적 가상 클래스 선택자 Structural Pseudo-classes

- 가상 클래스 선택자: 어떤 상태나 조건을 만족했을 때 사용할 수 있는 선택자

### element:first-child

- 예시

  ```css
  /* 콜론 앞뒤로 띄어쓰기 X */
  li:first-child {
      color: #0066ff;
  }
  ```

### element:last-child

- 예시

  ```css
  li:last-child {
      color: #ffc82c;
  }
  ```

### element:nth-child(n)

- 예시

  ```css
  li:nth-child(3) {
      color: #ff4949;
  }
  ```

- 짝수 표현 시

  ```css
  li:nth-child(2n) {
      color: #ffc82c;
  }
  ```

<br>

## 동적 가상 클래스 선택자 User Action Pseudo-classes

### element:hover

- 어떤 요소에 마우스를 올렸을 때

- 예시

  ```css
  a:hover {
      color: #7e5bef
  }
  ```

### element:focus

- 어떤 요소에 focus 되었을 때 (현재 입력 초점을 가진 요소에 적용)
- active 상태도 focus 상태의 일부이므로 `focus`-`active` 순서로 작성해야 두 스타일이 다 적용됨!

- 예시

  ```css
  input:focus {
      border-color: #1fb6ff;
  }
  ```

### element:active

- 어떤 요소를 누르는 찰나의 순간 ex) 버튼을 눌렀을 때처럼 순간적으로 활성화

- 예시

  ```css
  a:active {
      color: #592dea
  }
  ```

<br>

## CSS 선택자 우선순위

- 점수의 총합에 따라 점수가 높은 순으로 적용

  1. ID 선택자

  2. 클래스 및 가상 클래스 선택자

  3. 요소 선택자

- Rule Breakers

  - Inline style
  - `!important`
