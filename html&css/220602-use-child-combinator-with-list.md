## 자식 선택자

- 마지막 요소를 제외한 리스트 요소에 스타일링 하기

  ```javascript
  import styled from 'styled-components';
  
  const Wrapper = styled.div`
    ...
    /* 이렇게! */
    & > * {
      :not(:last-child) {
        margin-bottom: 1rem;
      }
    }
  `;
  ```

  - `& > *` : Wrapper의 모든 자식 요소들 중, last child가 아닌 것에 대해 스타일링 한다.

  - `&` in styled-components

    - 컴포넌트의 모든 인스턴스를 나타낸다.

    - 현재 컴포넌트에 대해 동등한 위치에 스타일을 추가할 때만 사용하는 줄 알았는데, 해당 컴포넌트를 참조하는 것이므로 다양한 용도로, 어떤 요소를 가리키는 것처럼 사용 가능하다.

    - 예시

      ```javascript
      const Thing = styled.div`
        & ~ & {
          background: tomato; // <Thing> as a sibling of <Thing>, but maybe not directly next to it
        }
      
        & + & {
          background: lime; // <Thing> next to <Thing>
        }
      
      
        .something-else & {
          border: 1px solid; // <Thing> inside another element labeled ".something-else"
        }
      `
      ```

    - 참고: https://styled-components.com/docs/basics#pseudoelements-pseudoselectors-and-nesting