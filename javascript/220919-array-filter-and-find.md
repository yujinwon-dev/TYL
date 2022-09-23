## Array methods: filter & find

두 메서드 모두 조건을 통과하는 요소를 반환한다는 점은 동일하다.

하지만 어떤 형태로 변환하는지에 차이가 있다.

### filter()

`filter()` 메서드는 조건을 통과하는 요소를 배열 형태로 반환한다.

```javascript
const people = [
    {name: 'YJ', age: 20},
    {name: 'MG', age: 6},
    {name: 'YS', age: 22},
];
const result = people.filter(person => person.age >= 20);
console.log(result);	// [{name: 'YJ', age: 20}, {name: 'YS', age: 22}]
```

### find()

`find()` 메서드는 조건을 통과하는 첫 번째 요소의 값을 반환한다.

조건을 만족하는 요소가 없을 경우 `undefined`를 반환한다.

```javascript
const numbers = [1, 3, 5, 7, 9, 11];
const result = numbers.find(number => number > 5);
console.log(result);	// 7
```

