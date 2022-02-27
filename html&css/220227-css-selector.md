[toc]

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

