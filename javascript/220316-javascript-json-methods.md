[toc]

## Response.json()

```javascript
response.json().then(data => {
  // do something with your data
});
```

- 응답 JSON 데이터를 JavaScript Object 형식으로 변환하는 메서드
- 아래에 있는 `JSON.parse()` 메서드와 거의 같은 역할이지만 `Response.json()` 메서드에서는 응답 헤더, 바디를 포함한 응답 객체 자체를 받아서 바디만 읽음
-  JSON 데이터를 변환해서 Promise 객체를 반환하기 때문에 API 호출에서 사용하기 용이하다.



## JSON.parse()

```javascript
JSON.parse(text[, reviver])
```

- 주어진 JSON 문자열을 JavaScript Object 형식으로 반환

- JSON 데이터는 문자열 형식으로 이루어져 있으므로 key에 대해 value를 뽑아내는 등 해당 데이터를 사용하려면 변환이 필요. 이 과정을 도와주는 것이 `JSON.parse()` 메서드

- 응답 바디만 받을 수 있음

  ```javascript
  const jsonData = '{"name": "YJ", "count": 33}';
  const myObj = jsonData.parse();
  console.log(myObj.name);
  // "YJ"
  console.log(myObj.count);
  // 33
  ```

  

## JSON.stringify()

```javascript
JSON.stringify(value[, replacer[, space]])
```

- JavaScript 값/객체를 JSON 문자열로 변환해주는 메서드
- stringify: string(문자열) + ify(~화 하다) = 문자열화 하다, 문자열로 만들다