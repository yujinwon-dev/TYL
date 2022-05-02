# 동기, 비동기

## 동기 Synchronous

- 현재 실행 중인 작업이 종료할 때까지 다음에 실행될 작업이 대기하는 방식
- 장점
  - 작업을 순서대로 하나씩 처리 → 실행 순서 보장
- 단점
  - 앞선 작업이 종료될 때까지 이후의 작업들이 블로킹 됨



## 비동기 Asynchronous

- 현재 실행 중인 작업이 종료되지 않았더라도 다음 작업을 곧바로 실행하는 방식
- `setTimeout`, `setInterval`, HTTP 요청, 이벤트 핸들러는 비동기 처리 방식으로 동작
- 장점
  - 블로킹이 발생하지 않음
- 단점
  - 작업 실행 순서가 보장되지 않음



## +) 이벤트 루프 & 태스크 큐(=이벤트 큐, 콜백 큐)

![img](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/37eab3f6-baa7-4a29-8077-0c5889cb585f/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220502%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220502T142000Z&X-Amz-Expires=86400&X-Amz-Signature=7af096f415747782195fc9973acf11cad30de0a4ae0c0c121419afe5dd64a306&X-Amz-SignedHeaders=host&response-content-disposition=filename%20%3D%22Untitled.png%22&x-id=GetObject)

(참고: https://blog.sessionstack.com/how-does-javascript-actually-work-part-1-b0bacc073cf)

- JS 엔진

  - 크게 콜 스택, 힙 2개의 영역으로 구분 가능

    - 콜 스택

      - 실행 컨텍스트가 추가/제거되는 스택 자료구조인 실행 컨텍스트 스택

      - 싱글 스레드 방식으로 동작하는 것은 브라우저가 아니라 브라우저에 내장된 JS 엔진

        → 즉, JS가 싱글 스레드 방식이라는 것은 콜 스택이 하나라는 의미

    - 힙

      - 객체가 저장되는 메모리 공간

  - 단순히 태스크가 요청되면 콜 스택을 통해 작업을 순차적으로 실행

    - 비동기 처리에서 소스코드의 평가&실행을 제외한 모든 처리는 JS 엔진 구동 환경인 브라우저 또는 Node.js가 담당

      ex) 호출 스케줄링을 위한 타이머 설정, 콜백 함수 등록 등

      → 이를 위해 브라우저 환경에서 태스크 큐, 이벤트 루프를 제공

- 이벤트 루프

  - 콜 스택과 태스크 큐의 상태를 반복적으로 체크해서, 콜 스택이 빈 상태가 되면 태스크 큐의 첫번째 콜백을 콜 스택으로 이동시킴
  - HTML 요소가 애니메이션 효과를 통해 움직이면서 이벤트를 처리하거나, HTTP 요청을 통해 서버로부터 데이터를 가져오면서 렌더링 하는 등 자바스크립트의 동시성을 지원

- 태스크 큐

  - 비동기 함수의 콜백 함수 또는 이벤트 핸들러가 일시적으로 보관되는 영역



참고: https://github.com/yujinwon-dev/TYL/blob/master/javascript/211101-ajax-and-promise.md