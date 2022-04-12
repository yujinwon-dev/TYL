- HTML의 DOM 엘리먼트를 가져올 때 $ 표시를 관용적으로 많이 사용함

  ```javascript
  const $ = (selector) => document.querySelector(selector);
  ```



- vanilla JS로 스타일링 입혀진 엘리먼트 반환하려면 이런 방법도 있음

  단, `innerHTML` 사용 시 내용 덧붙이는 게 아니라 바꾸는 식

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

- 이 때 사용할 수 있는 게 `Element.insertAdjacentHTML()` 메서드 ([참고](https://developer.mozilla.org/ko/docs/Web/API/Element/insertAdjacentHTML))

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

    