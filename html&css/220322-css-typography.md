[toc]

# Typography

## font-size

- 글씨의 크기

- 단위
  - px: 절대 단위 (absolute unit)
  - em: 상대 단위 (relative unit)
    - `e`qual to capital `M` -> 실제로 적용된 폰트 사이즈가 1em
    - 만약 p 태그의 font-size가 20px이라면 `1em = 20px`
    - 각 요소에 주어진 font-size마다 달라져서 불안정하기 때문에 font-size 지정할 때 em을 선호하지는 않음
  - rem: 상대 단위 (relative unit)
    - `r`oot `em` -> 최상단(html)에 적용된 폰트 사이즈가 1rem

## line-height

- 줄의 높이 -> 줄 간격

- line-height 값이 얼마든 간에 **글자는 가장 가운데**에 배치됨

- 단위

  - px

  - em

    - line-height 적용 시 많이 사용

    - 현재 폰트 사이즈에 대해 적용하는 게 편하기 때문

    - 예시

      ```css
      .text {
        /* font-size에 비례해서 em 단위로 설정할 경우 단위는 안 적는 게 관례 */
        font-size: 16px;
        line-height: 1.5;
      }
      ```

  - rem

## letter-spacing

- 글자 사이의 간격 (자간)
- 단위
  - px
  - em
    - 원래 적용된 font-size에 비례해서 늘리고 줄이므로 em 많이 사용
  - rem은 잘 사용하지 않음

## font-family

- 사용하고자 하는 서체

- 예시

  ```css
  .text {
    font-family: "Poppins",
    /* Poppins 서체 사용해줘 -> 없으면 sans-serif 글씨체 아무거나 사용해줘 */
    font-family: "Poppins", sans-serif;
  }
  ```

## font-weight

- 폰트 굵기

- 예시

  ```css
  .text {
    font-weight: 400;
    /* 100 | 200 | 300 | 400 | 500 | 600 | 700 | 800 | 900 (100 단위로) */
    /* regular: 400 */
    /* bold: 700 */
  }
  ```

## color

- 글씨 색
- 방식
  - hex
    - ex) #0066ff
  - rgb
    - ex) rgb(0, 102, 255)
  - rgba
    - ex) rgba(0, 102, 255, 1)

---

## text-align

- 텍스트 정렬
- 값
  - left
  - right
  - center

## text-indent

- 들여쓰기

- 예시

  ```css
  .text {
    text-indent: 100px;
    /* 음수값도 가능 */
    text-indent: -10px;
  }
  ```

## text-transform

- 글자 변경
- 값
  - none: 기본 상태
  - capitalize
    - ex) This Is Capitalize
  - uppercase
    - ex) THIS IS UPPERCASE
  - lowercase
    - ex) this is lowercase

## text-decoration

- 줄 끊기 관련 속성
- 값
  - none: 기본 값
    - ex) a tag에 적용되는 밑줄 없앨 때 자주 사용
  - underline: 밑줄
  - line-through: 가운데 줄
  - overline: 위에 줄

## font-style

- 글자 기울이기
- 값
  - normal: 기본값
    - em 태그의 기본값인 italic을 없앨 때 주로 사용
  - italic: 이탈릭체
  - oblique
    - 잘 사용하진 않음