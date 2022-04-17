# Animation

- animation vs transition

  - animation: 애니메이션을 주는 것 (좀 더 변화가 큼)
  - transition: 스르르 변화하게 하는 것

- animation-property

  - name

    ```css
    .box {
        /* ... */
        /* 애니메이션이 끝나면 기존 선언해둔 것으로 돌아옴 */
        /* bg color 지정 안 하면 ff4949 다음에 배경 없어짐 */
        animation-name: name;
    }
    
    @keyframes name {
        /* 선언 방법 1 */
        from {
            /* rules */
            top: 0;
            background-color: #0066ff;
        }
        to {
            /* rules */
            top: 200px;
            background-color: #ff4949;
        }
    }
    ```

    ```css
    @keyframes name {
        /* 선언 방법 2 */
        0% {
            /* rules */
        }
        50% {
            /* rules */
        }
        100% {
            /* rules */
        }
    }
    ```

  - duration

    - 애니메이션 지속 시간

    - ms, s 단위 사용 가능

      ```css
      .box {
          /* ... */
          animation-duration: 2000ms;
      }
      ```

  - timing-function

    - 변화 속도

    - 종류

      - ease-in
      - ease-out
      - ease-in-out
      - cubic-bezier()

      ```css
      .box {
          /* ... */
          animation-timing-function: ease-in-out;
      }
      ```

  - delay

    - ms, s 단위 사용 가능

      ```css
      .box {
          /* ... */
          animation-delay: 1000ms;
      }
      ```

  - iteration-count

    - 반복 횟수

      ```css
      .box {
          /* ... */
          /* 숫자 지정 */
          animation-iteration-count: 3;
          /* 무한 반복 */
          animation-iteration-count: infinite;
      }
      ```

  - direction

    - 진행 방향

      ```css
      .box {
          /* ... */
          /* to에서 from으로 진행 */
          animation-direction: reverse;
          /* iter count가 2 이상일 때 이렇게 지정하면 번갈아가면서 진행됨! */
          animation-direction: alternate;
      }
      ```

      