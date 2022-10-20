## DOM 조작하기

### 요소 선택

- `document.querySelector()`, `document.querySelectorAll()`

  - HTML의 DOM 엘리먼트를 가져올 때 $ 표시를 관용적으로 많이 사용함

    ```javascript
    const $ = (selector) => document.querySelector(selector);
    ```



### HTML 콘텐츠 조작

- `Node.textContent()`

  ```javascript
  let text = someNode.textContent;
  someOtherNode.textContent = 'hello';
  ```

- `Element.innerHTML()`

  ```javascript
  $("#espresso-menu-name").addEventListener("keypress", (e) => {
      if (e.key === "Enter") {
        const espressoMenuName = $("#espresso-menu-name").value;
        const menuItemTemplate = (name) =>
          `<li class="menu-list-item d-flex items-center py-2">
            <span class="w-100 pl-2 menu-name">${name}</span>
            <button
              type="button"
              class="bg-gray-50 text-gray-500 text-sm mr-1 menu-edit-button"
            >
              수정
            </button>
            <button
              type="button"
              class="bg-gray-50 text-gray-500 text-sm menu-remove-button"
            >
              삭제
            </button>
          </li>`;
        const menuItem = menuItemTemplate(espressoMenuName);
        $("#espresso-menu-list").innerHTML = menuItem;
  ```


### 요소 삽입

- `Element.insertAdjacentHTML()` ([참고](https://developer.mozilla.org/ko/docs/Web/API/Element/insertAdjacentHTML))

  ```javascript
  $("#espresso-menu-list").insertAdjacentHTML('beforeend', menuItem);
  ```

  - position

    - `'beforebegin'` : 엘리먼트 앞
    - `'afterbegin'` : 엘리먼트의 가장 첫 번째 child
    - `'beforeend'` : 엘리먼트의 가장 마지막 child
    - `'afterend'` : 엘리먼트 뒤

    ```javascript
    <!-- beforebegin -->
    <p>
    <!-- afterbegin -->
    foo
    <!-- beforeend -->
    </p>
    <!-- afterend -->
    ```


- `Node.insertBefore()`

  ```javascript
  var insertedNode = parentNode.insertBefore(newNode, referenceNode);
  ```

  