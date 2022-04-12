

# Transition

- transition?

  - 애니메이션을 주어서 스르르 변하게 도와주는 것

- 알아야 하는 것들 (선언해야 하는 것들)

  - property

    - css 속성을 의미

    - 변화가 일어날 속성 명시

      ex) `transition: all 2000ms;`, `transition: background-color 2000ms;`

  - duration

    - transition의 지속 시간
    - ms, s 단위 사용 가능 (1000ms = 1s)

  - [timing-function] - 생략 가능

    - 자주 쓰이는 것들

      - ease-in

        - 처음엔 천천히 바뀌다가 나중에는 휙

          ex) `transition: all 2500ms ease-in;`

      - ease-out

        - 처음엔 휙 바뀌고 나중에는 천천히 바뀜

      - ease-in-out

      - cubic-bezier()

        - 내가 변화의 가속도를 제어하고 싶을 때 사용
        - 곡선을 만드는 function.. 홈페이지 참고
          - https://cubic-bezier.com/#0,0,1,1

  - [delay] - 생략 가능

    - transition을 지연시킬 때

      ex) `transition: all 2500ms ease-out 1000ms;`

- 좀 더 섬세하게 컨트롤하려면?

  ```css
  .box {
      font-size: 20px;
      background-color: #0066ff;
      transition: font-size 1000ms ease-out, background-color 2000ms cubic-bezier(.07,.46,.73,.47) 1000ms;
  }
  
  .box.active {
      font-size: 30px;
      background-color: #ff4949;
  }
  ```

  