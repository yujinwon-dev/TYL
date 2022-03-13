

# Media Query

- 반응형 웹

  - 반응형 웹을 만들기 위해 반드시 알아야 하는 것 중 하나가 미디어 쿼리

  - 필요한 2가지 조건

    - HTML: viewport meta tag

      ```html
      <!-- meta 데이터를 줄게. viewport에 관한 거야. 웹 페이지 가로 사이즈 잡을 때는 디바이스 width에 맞춰줘. -->
      <meta name="viewport" content="width=device-width" />
      ```

    - CSS: media query문 선언

      ```css
      /* media query 선언할게. screen에 관한 거야. 최소 가로 사이즈가 768px이면(가로 사이즈가 768px 이상이면) 이런 스타일을 먹여줘. */
      @media screen and (min-width: 768px) {
          /* CSS 선언 */
      }
      
      /* width가 겹치지 않도록 해줌 -> 그 다음 미디어쿼리 선언에서는 min-width: 992px 이런 식으로 */
      @media screen and (min-width: 768px) and (max-width: 991px) {
          .box {
              background-color: #ffc82c;
          }
      }
      ```

  - 모바일부터 시작하는 게 정설. 이후에 큰 화면 공사

    - 개발자 도구에서 iPhone 5 (width 320)으로 놓고 하면 웬만해선 안 깨짐