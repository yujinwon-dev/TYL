# Passing setState as props

```react
import React, { useState } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <!-- (1) Bad -->
      <Child setCount={setCount}>
        Click me
      </Child>
      <!-- (2) Good -->
      <Child onClick={() => setCount(count + 1)}>
        Click me
      </Child>
    </div>
  );
}
```

`setState` 함수를 그대로 전달하는 것을 1번 방식, `setState`를 수행하는 함수를 전달하는 것을 2번 방식이라고 하자.



1번 방식이 불가능한 것은 아니지만, 2번 방식처럼 작성하는 것을 추천한다.

`setState` 함수를 전달하는 것은 부모 컴포넌트의 내부를 노출시키고 자식 컴포넌트가 부모의 상태에 영향을 미치게 하는 일이다. 

그리고 React는 상태 변경이 즉시 적용되는 것을 보장하지 않기 때문에, 부모 컴포넌트의 상태를 변경하는 작업 간에 경쟁이 일어날 수 있으므로 `setState` 함수를 호출하는 코드를 한 곳에서 관리하는 게 좋다.

또한 이 경우에는 이벤트가 발생했을 때 부모 컴포넌트가 취할 수 있는 조치의 유연성이 줄어든다. 만약 `setState` 뿐만 아니라 `alert` 표시 등의 작업을 해야 한다면, `setState`만 props로 전달할 때보다 부모 컴포넌트에서 작성한 함수를 전달할 때 다양한 작업을 수행할 수 있다.



---

- 참고한 글
  - https://stackoverflow.com/questions/59850845/passing-setstate-to-child-component-using-react-hooks
  - https://stackoverflow.com/questions/50215364/can-we-pass-setstate-as-props-from-one-component-to-other-and-change-parent-stat