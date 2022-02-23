### 목차

- [05_data structure: str, list](#05_data-structure-str-list)
  * [데이터 구조(Data structure)](#-data-structure)
  * [문자열 메서드 `.strip()` & `.split()`](#--strip--split)
  * ['seperator'.join(iterable)](#seperatorjoiniterable)
  * [문자열 검증 메소드](#--)
  * [List의 메서드](#list-)
  * [mutable vs immutable](#mutable-vs-immutable)
  * [List comprehension](#list-comprehension)
  * [`map(function, iterable)`](#mapfunction-iterable)
- [05_data structure: set, dictionary](#05_data-structure-set-dictionary)
  * [set: 추가 및 삭제](#set---)
  * [Dictionary comprehension](#dictionary-comprehension)

<br>

## 05_data structure: str, list

### 데이터 구조(Data structure)

: 파이썬에서는 데이터에 따른 메서드들이 구현되어 있음

(c언어에서는 데이터만 갖고 그에 따라 스택, 큐, 리스트 등을 직접 짜야 함)



- 순서가 없는 데이터 구조

  -> 유니크한 key를 이용해 value에 접근

  이런 걸 hash 자료형이라고 함

  중복되지 않는 key로 바로바로 접근하기 때문에 속도 빠름

  (순서 있는 데이터 구조는 중복값 존재할 수 있으나 인덱스로 구분 가능)



- List indexing

```python
s = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i']
s[2:5:-1] 
# []
# 2에서 시작해서 4에서 끝나야 되는데 거꾸로 셀 수가 없음
s[5:2:-1]
# ['f', 'e', 'd']
# 5부터 3까지. -1순서로 하면 5 4 3 이렇게 할 수 있음
```



### 문자열 메서드 `.strip()` & `.split()`

- `.strip()`
  - 공백/인자로 넣은 문자를 제거하는 메서드
  - `lstrip()`: 왼쪽 제거
  - `rstrip()`: 오른쪽 제거
- `.split()`
  - 공백/인자로 넣은 문자를 기준으로 문자열을 나누어 *list로* 반환



### 'seperator'.join(iterable)

- iterable한 컨테이너(**str!**)의 요소들을 separator로 합쳐서 반환

```python
word = '반가워'
'!'.join(word)
# 반!가!워!

words = ['안녕', 'bonjour', 'Hello']
''.join(words)
# 안녕bonjourHello
```



### 문자열 검증 메소드

- `isdecimal()` : 십진수
- `isdigit()`
- `isnumeric()` : 숫자에 가까운 (`isdecimal()`, `isdigit()`의 True값을 포함)



### List의 메서드

- `.remove(x)` 

  값이 x인 것을 **한 번** 삭제

- `.pop(i)`

  정해진 위치에 있는 값을 삭제하고 그 항목 반환

  괄호 사이에 숫자 안 넣을 때가 더 빠름

- `.index(x)`

  x값의 index를 반환

  (string에도 index() 메서드 있음!)

  - .index() 메서드로 2차원 리스트에서도 위치 가져올 수 있나?

    ```python
    my_list = [ [10, 20, 30], [40, 50, 60] ]
    my_list.index(40)
    # ValueError
    # 0부터 시작하는 인덱스를 돌려주기 때문에 2차원 리스트는 에러가 나는 듯
    ```




### mutable vs immutable

- mutable

  - list, set, dictionary

  - 크기를 고정해놓고 쓰지 않음 -> 변수가 메모리 주소를 참조하는 형식

    -> 복사한 뒤 값을 바꾸면 둘 다 바뀜

- immutable

  - 리터럴, range, tuple



### List comprehension

- 이건 왜 안 되지?

```python
my_list = [x **2 for x in range(1, 4) if x % 2 == 0]
# => [] 안 써서 그랬음
```

여러 줄 코드(indentation)가 이해하기는 대체적으로 더 편함

하지만 comprehension 으로 쓰는 법도 **알고 있기**

- 다른 예시

```python
# 이렇게 하면 [[0] * 3]이 얕은 복사 형태로 같은 공간을 세 번 참조
a = [[0] * 3] * 3
a[0][1] = 1
for row in a:
    print(row)
# [0, 1, 0]
# [0, 1, 0]
# [0, 1, 0]

# 이렇게 하면 각각 다른 공간을 가리킴
b = ([[0] * 3 for _ in range(3)])
b[0][1] = 1
for row in b:
    print(row)
# [0, 1, 0]
# [0, 0, 0]
# [0, 0, 0]
```

- 곱집합

```python
girls = ['jane', 'ashley', 'mary']
boys = ['justin', 'eric', 'david']

pair = [(girl, boy) for girl in girls for boy in boys]
# ('jane', 'justin'), ('jane', 'eric'), ('jane', 'david'), ('ashley', 'justin') ...
```



### `map(function, iterable)`

```python
# 리스트 numbers를 문자열 '102030'으로 만들기
numbers = [10, 20, 30]
print(''.join(map(str, numbers)))

# 우선 numbers의 요소들을 map() 함수를 이용해 str으로 바꿈
# str 데이터 타입이므로 join() 메서드 사용 가능
## ''.join()을 이용해서 이어붙임
```



## 05_data structure: set, dictionary

### set: 추가 및 삭제

- `.add(elem)`

  중복 값 없이 요소 추가

- `.update(*others)`

  iterable한 데이터 구조를 통해 요소 여러 개 추가

  ```python
  a = {'사과', '바나나', '수박'}
  
  a.update({'토마토', '토마토', '딸기'}, {'포도', '레몬'})
  a.update('mango', 'blueberry')
  print(a)
  # {'수박', '레몬', '사과', 'o', 'e', '딸기', '토마토', 'n', '바나나', 'b', 'm', 'y', '포도', 'u', 'a', 'r', 'g', 'l'}
  ```

- `.remove(elem)`

  elem을 세트에서 삭제, 없으면 KeyError 발생

- `.discard(elem)`

  elem을 세트에서 삭제, 없어도 에러 X



### Dictionary comprehension

```python
dusts = {'서울': 72, '인천': 82, '제주': 29, '동해': 45}

result1 = {key:value for key, value in dusts.items() if value > 80}
# {'인천': 82}
# 요소 자체를 딕셔너리에 넣을지 말지 결정하는 게 맨 뒤에 나오는 if문

result2 = {location: ('매우나쁨' if dust > 150 else '나쁨' if dust > 80 else '보통') for location, dust in dusts.items()}
# {'서울': '보통', '인천': '나쁨', '제주': '보통', '동해': '보통'}
# value위치에 나오는 () 안 조건식이 value에 해당하는 표현식!
```

