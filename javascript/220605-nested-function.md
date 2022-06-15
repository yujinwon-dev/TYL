# 중첩 함수 nested function

- 자바스크립트는 중첩 함수를 지원한다.

    ```javascript
    function solution(numbers, target) {	// outer function
      let answer = 0
      function dfs(now, idx) {	// inner function
          if (idx === numbers.length) {
              if (now === target) answer++;
              return;
          }
          dfs(now + numbers[idx], idx + 1)
          dfs(now - numbers[idx], idx + 1)
      }
      dfs(0, 0)
      return answer;
    }
    ```

- 특징

  - 내부 함수를 외부 함수 내부에 위치시키는 것은 내부 함수가 외부 함수에서 사용될 것임을 명시적으로 나타낸다.

    -> 클린 코드적 관점에서 의미가 있다.

  - `dfs` 함수는 `solution` 함수가 100번 실행될 경우 100번 생성되었다가 파괴된다. 따라서 이전에는 성능상 이슈가 있었으나, 최근에는 함수를 외부에 노출시키는 것과 성능의 차이가 없다고 한다.

  - 클로저를 구성하는 핵심성분

    -> 클로저 공부 후 다시 읽어볼 것

---

- 참고
  - [자바스크립트의 중첩 함수(Nested functions)는 언제 사용해야 할까?](https://siyoon210.tistory.com/162)