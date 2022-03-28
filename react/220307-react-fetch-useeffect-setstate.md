[toc]

# 만들면서 배우는 리액트: 기초

## 리액트 앱에 숨 불어넣기

### fetch

- 예시

  ```javascript
  fetch('http://example.com/movies.json')
    .then(function(response) {
      // response를 json 형태로 파싱
      return response.json();
    })
    .then(function(myJson) {
      // JavaScript 값이나 객체를 JSON 문자열로 변환
      console.log(JSON.stringify(myJson));
    });
  ```

- Using Fetch

  - axios와 fetch: Promise 기반의 라이브러리. 비슷한 기능을 함

    | axios                              | fetch                              |
    | ---------------------------------- | ---------------------------------- |
    | 3rd party library(설치 필요)       | 내장 라이브러리                    |
    | status가 200이면 성공              | 응답객체가 ok 속성을 포함하면 성공 |
    | 자동으로 JSON 데이터 형식으로 변환 | `.json()` 메서드를 통한 변환 필요  |
    | 요청 취소 or 타임아웃 가능         | X                                  |
    | 브라우저 호환성이 뛰어남           | fetch를 지원하지 않는 버전도 존재  |

  - 참고: [mdn Using Fetch](https://developer.mozilla.org/ko/docs/Web/API/Fetch_API/Using_Fetch)

- async&await

  - async&await의 목적: 보통 코드를 위에서부터 아래로 읽어내려가면서 해당 순서대로 실행될 것이라고 생각함. 하지만 자바스크립트의 비동기 처리에 의해 코드의 순서가 보장되지 않음 -> 이 문제를 해결할 수 있도록 도와줌

  - 사용 방법

    ```javascript
    // 1. 함수의 앞에 async라는 예약어를 붙임
    async function 함수명() {
      // 2. 함수 내붕서 HTTP 통신을 하는 비동기 처리 코드 앞에 await를 붙임
      // *해당 메서드가 Promise 객체를 반환해야 await가 의도한대로 동작함*
      await 비동기_처리_메서드_명();
    }
    ```

### useEffect

- 앱이 UI를 새로 그릴 때마다 `ReactDOM.render()`를 통해 렌더되는 컴포넌트 내의 모든 코드가 새로 불림
  - 새로고침 할 때뿐만 아니라 이미지가 새로 렌더되거나 하는 상황에도 마찬가지

- `React.useEffect()`: UI가 업데이트 될 때마다 호출되는 건 맞지만, 두번째 인자를 통해 함수가 호출될 순간을 제한할 수 있음 -> "어떤 상태가 업데이트 될 때만 불러라"

  ```react
  // 두번째 인자가 없으면 UI가 새로 그려질 때마다 호출됨 (원래의 상태)
  React.useEffect(() => {
    console.log("hello");
  })
  // 처음에 앱이 생성되었을 때만(=마운트 되었을 때 한 번만) 호출
  React.useEffect(() => {
    console.log("hello");
  }, [])
  // counter 상태가 업데이트 될 때만 호출
  React.useEffect(() => {
    console.log("hello");
  }, [counter])
  ```

### 조건부 렌더링

- if문 사용 예시

  ```react
  function Favorites({ favorites }) {
    if (favorites.length === 0) {
        return <p>사진 위 하트를 눌러 고양이 사진을 저장해봐요!</p>;
    }
  
    return (
        <ul className="favorites">
            {favorites.map((cat) => (
                <CatItem img={cat} key={cat} />
            ))}
        </ul>
    );
  }
  ```

- 삼항연산자 사용 예시

  ```react
  const MainCard = ({ img, onHandleHeartClick, alreadyFavorite }) => {
    const heartIcon = alreadyFavorite ? "💖" : "🤍";
  
    return (
        <div className="main-card">
            <img
                src={img}
                alt="고양이"
                width="400"
                />
            <button
                onClick={onHandleHeartClick}
                >{heartIcon}</button>
        </div>
    );
  }
  ```

### setState 더 알아보기 - 함수, 지연초기화

- 지연초기화

  - useState에 함수 넘기기: 앱이 처음 실행될 때만 실행됨

    ```react
    const [counter, setCounter] = React.useState(() => {
      // localStorage에 접근하는 일은 시간부하가 걸림. 하지만 카운터는 앱이 처음 실행될 때만 접근해도 됨
      return jsonLocalStorage.getItem("counter");
    });
    ```

    -  useState에 함수를 전달하면 React는 초기 값이 필요할 때만 함수를 호출 (구성 요소가 처음 렌더링 될 때)
    - 참고: [React 공식문서 지연 초기 state](https://ko.reactjs.org/docs/hooks-reference.html#lazy-initial-state)

- 함수적 갱신

  - 이전 state를 사용해서 state를 갱신할 경우 setState에 함수 전달

    ```react
    setCounter((prev) => {
      const nextCounter = prev + 1;
      jsonLocalStorage.setItem("counter", nextCounter);
      return nextCounter;
    })
    ```

    - 참고: [React 공식문서 함수적 갱신](https://ko.reactjs.org/docs/hooks-reference.html#functional-updates)