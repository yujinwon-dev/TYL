### 목차

- [Django](#django)
  * [Web framework](#web-framework)
  * [장고 설치](#장고-설치)
    + [1](#1)
    + [2](#2)
  * [Django Template](#django-template)
  * [템플릿 상속](#템플릿-상속)
  * [HTML Form](#html-form)
  * [URL](#url)
  * [Namespace](#namespace)

<br>

# Django

> Django is a Python Web framework.
>
> MTV 디자인 패턴으로 이루어진 파이썬 웹 프레임워크

<br>

## Web framework

- Static web page(정적 웹 페이지)

  - DB/추가적인 처리 과정 없이 모든 사용자에게 같은 응답을 돌려줌
  - 보통 HTML, CSS, Javascript로 작성



- React, View => 장고의 template 기능을 가져간 것과 비슷

  Django는 모든 기능을 가져온 풀스택 형태



- Dynamic web page(동적 웹 페이지)

  - 서버에서 추가 처리과정(django가 함)이 생겨 사용자가 보게되는 화면이 변경되면 Dynamic web page
  - 방문자와 상호작용 -> 페이지 내용은 그때그때 다름
  - 서버 사이드 프로그래밍 언어(python, java, c++, js 등)가 사용되며 파일을 처리하고 **DB와의 상호작용**이 이루어짐

  

- Framework

  - frame: 틀 -> framework: 뼈대, 이미 잡혀있는 규격사항
  - 프로그래밍에서 특정 OS를 위한 응용 프로그램 표준 구조를 구현하는 클래스, 라이브러리의 모임 -> 커다란 코드뭉치 형태
  - 재사용 가능한 수많은 코드를 프레임워크로 통합 -> 개발자가 코드를 다시 작성하지 않아도 사용할 수 있도록 도움
  - (Web) Application Framework라고도 함

  

- Web framework

  - 왜 사용할까? 

    : **웹 페이지를 개발하는 과정(웹 페이지를 제공하기까지)에서 겪는 어려움을 줄이는 것이 주 목적** -> DB 연동, 템플릿 형태의 표준, 세션 관리, 코드 재사용 등의 기능을 포함

  

- Django를 사용해야 하는 이유

  - 등장한 지 꽤 오래되었으며, 대규모 서비스에서도 안정적 형태로 오랫동안 사용 중

  

- Framework Architecture

  - MVC Design Pattern (Model-view-controller)
    - 소프트웨어 공학에서 사용되는 디자인 패턴 중 하나
    - 사용자 인터페이스로부터 프로그램 로직을 분리 -> 애플리케이션의 시각적 요소나 이면에서 실행되는 부분을 서로 영향없이 쉽게 고칠 수 있는 애플리케이션을 만들 수 있음. *모델, 뷰, 컨트롤러를 분리한 게 핵심!*
    - Controller가 데이터를 저장하는 Model(DB)에게서 데이터를 가져와서 조작. 조작된 정보를 템플릿에 반영하는 게 View
    
  - Django에서는 **MTV Pattern**이라고 함

    | MTV         | MVC           |
    | ----------- | ------------- |
    | M: Model    | M: Model      |
    | T: Template | V: View       |
    | V: View     | C: Controller |



- MTV Pattern (**시험이나 면접에서 나오기 좋은 부분!**)

  - Model: 응용프로그램의 데이터 구조 정의 및 DB의 기록 관리(추가, 수정, 삭제)
  - Template: 실제 사용자가 보게되는 화면, 파일의 구조나 레이아웃 정의
  - View: HTTP 요청을 수신하고 응답 반환. Model을 통해 데이터에 접근. 조작된 정보를 template에게 다시 넘겨줌.

- HTTP 요청이 오면 우선 문지기(urls.py - `urlpatterns`)가 검사.

  올바른 길인지 확인 후 맞으면 안내.

  그 길 끝에는 View(views.py에 정의된 함수)가 있음.

  model을 통해 데이터 가져옴.

  response 되돌려주는 건 HTML 형태. Template(templates 폴더) 안에 html 파일 여러 개 있고 빈 공간들에 내용 채워서 되돌려주는 게 View.

  => View를 도와서 주위에서 여러 친구들이 일을 한다 보면 될 듯!

<br>

## 장고 설치

### 1

```shell
pip install django
# python -m pip install Django

# django-admin startproject 프로젝트명
# => 경로 없이 하면 폴더를 프로젝트 이름으로 새로 하나 만들고 그 안에 프로젝트를 구성해줌!
django-admin startproject firstpjt .

cd firstpjt

python manage.py runserver

# 서버 종료: ctrl + c
```



### 2

```shell
mkdir firstpjt
cd firstpjt
# 1. 파이썬 가상환경 생성
python -m venv venv
# 가상환경 활성화
source venv/Scripts/activate

pip list
# Package    Version
# ---------- -------
# pip        21.2.4
# setuptools 56.0.0
# (venv) 

# 2. 장고 설치
pip install django
pip list
# Package    Version
# ---------- -------
# asgiref    3.4.1
# Django     3.2.6
# pip        21.2.4
# pytz       2021.1
# setuptools 56.0.0
# sqlparse   0.4.1
# (venv)

# django-admin  startproject  프로젝트이름  경로(. 현재경로)
django-admin startproject firstpjt .
ls
# firstpjt/  manage.py*  venv/

# 앱을 생성! articles는 앱 이름(일반적으로 복수형을 권장)
python manage.py startapp articles
# 생성하고 나서 직접 등록해주어야 함
# 등록방법: INSTALLED_APPS에 추가
# 순서 안 지키면 ModuleNotFoundError
```



- firstpjt: 프로젝트 폴더

  - `settings.py`: 애플리케이션의 모든 설정

  - `urls.py`: 요청이 오면 `app이름.views.함수`에 연결이 됨 (view가 `models.py`와 왔다갔다)
  - `asgi.py`: Asynk(비동기적인) Gateway Interface
  - `wsgi.py`: 웹서버 관련 게이트웨이 설정
  - `manage.py`: Django 프로젝트와 다양한 방법으로 상호작용하는 커맨드라인 유틸리티

- articles: 앱 폴더
  - migrations: 모델에 관한 설정
  - `admin.py`: 관리자용 페이지 설정 (장고에서는 admin page가 자동 생성됨)
  - `models.py`: DB와 model을 조작하기 위한 설정들
  - `tests.py`: 테스트 자동화를 위한 파일
  - `views.py`: MTV의 view를 담당



- Project: 앱의 집합

  Application: 하나의 역할 및 기능단위로 작성. 실제 요청 처리 및 페이지 보여주기 담당



- 앱 생성은 언제 해야 하나요?

  -> 기능 단위로! 게시판 기능, 유저 관리 기능 등등

  -> 앱 - views - crud 구현

---

- Chrome 창에 **url**을 입력하는 행동이 trigger! (trigger URL)

  -> 그 요청이 urls로 가서 url path checking -> views의 특정 **함수**로 전달

- View

  - HTTP 요청을 수신하고 HTTP 응답을 반환하는 함수 작성 (이 과정에서 `render()` 함수 사용)
  - 요청과 응답 사이에 Model을 통해 요청에 맞는 필요 데이터에 접근
  - Template에게 HTTP 응답 서식을 맡김

- Templates

  - 보통 `articles/templates/index.html` 이런 식으로 앱 폴더 내에 템플릿 폴더 내에 작성
  - templates 파일 경로의 기본값은 **app  폴더 안의 templates 폴더** -> 렌더 함수에서 `index.html` 이렇게만 써도 articles/templates에서 찾음
  - 실제 내용을 보여주는 데 사용되는 파일. 파일의 구조나 레이아웃을 정의

+) **`urls -> views -> html 파일` 3단 구조!**

<br>

## Django Template

> "데이터 표현을 제어하는 도구이자 표현에 관련된 로직"

- 사용하는 built-in system: Django template language(=DTL)

  -> 장고 템플릿을 문법화한 특별한 언어. 장고 템플릿만의 문법 사항

  - 단순히 파이썬이 HTML에 포함된 것이 아님. 프레젠테이션을 표현하기 위한 것.
  - 일부 프로그래밍 구조(if, for 등)를 사용할 수 있지만 해당 python 코드로 실행되는 것은 아님. 근데 유사!




- DTL Syntax

  1. Variable

     ```django
     {{ key }}
     ```

     - `render()`를 사용할 때 리퀘스트, 템플릿 + 데이터를 인자로 넘겨줌
     - 변수명은 영어, 숫자, 밑줄의 조합으로 구성. 밑줄로 시작은 X
     - dot(.)을 사용하여 변수 속성에 접근 ex)`number.value`
     - `render()`의 세 번째 인자로 `{'key': value}`와 같이 딕셔너리 형태(`context`처럼)로 넘겨줌. 여기서 key가 template에서 사용 가능한 변수명!

  2. Filters

     ```django
     {{ variable|filter}}
     ```

     - value의 필터링 된 결과를 사용하는 것
     - `django template built-in filters` 검색해서 보세요
     - 인자를 받는 필터도 있음

  3. Tags

     ```django
     {% tag %}
     ```

     - 출력 텍스트를 만들거나, 반복/논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행 ex. for, if 등
     - 시작/종료 태그가 있는 태그도 있고 없는 태그도 있음
     - 약 24개의 built-in template tags 제공

  4. Comments

     ```django
     {# #}
     
     {% comment %}
     이렇게도 가능
     {% endcomment %}
     ```
     
     - django template에서 주석을 표현하기 위해 사용



- 코드 작성 순서
  - 데이터의 흐름에 맞추어 작성!
    1. urls.py
    2. view.py
    3. templates
  - 요청 상황에 대한 가정 -> url -> `urls.py`에서 url을 갖고 연결할 함수 구성&연결 -> `views.py`가 템플릿을 렌더 -> 템플릿 구성

<br>

## 템플릿 상속

- 재사용 되는 요소 중 가장 대표적인 게 navbar

  어느 페이지를 가든 항상 보여야 해서 매 html 코드마다 상단에 같은 navbar 코드가 작성되어 있어야 함

  => 코드 라인이 반복적으로 작성됨. 이 부분을 따로 모듈 처리해서 재사용할 수 있음

- 템플릿 상속: 기준이 되는 큰 템플릿이 하나 있고 navbar가 작성되어 있고 중간에 구멍을 냄. **이 구멍 부분에 content만 채우는 형식으로 상속!**

```python
# settings.py 작성

TEMPLATES = [
    {
        # 기본이 되는 템플릿 경로 설정
        # 환경마다 os가 다르므로 os에 맞춰 파일 경로를 자동으로 바꿔주는 역할!
        'DIRS': [BASE_DIR / 'templates'],
        # BASE_DIR: 현재 프로젝트 폴더와 같은 위치에서
        # 'templates': 해당 폴더 내에서 찾겠다
    }
]
```

```django
{# 애플리케이션 폴더들과 같은 위치에서? 부모 템플릿 작성 #}
{# html~~ 작성하고 body에 block 뚫음 #}

{# 자식 템플릿(각 html 파일)에서 #}
{% extends 'base.html' %}

{% block content %}
  {# 여기에 내용 작성 #}
{% endblock content %}
```



- Django template system
  - "표현과 로직(view)을 분리"
    - 필터 작성 시 템플릿보다는 view에서 데이터 조작!
    - 템플릿은 표현 관련 로직만 있도록
  - "중복 배제"

<br>

## HTML Form

- HTML "form" element
  - 핵심 속성
    - `action`: 입력 데이터가 전송될 URL 지정
    - `method`: 입력 데이터 전달 방식(GET, POST 등) 지정



- HTML "input" element
  - `id`는 label의 for와 연결
  - `name`은 장고에서 사용. name에 설정된 값을 넘겨서 값을 가져올 수 있음
    - `?key=value&key=value` 형태로 전달됨



- HTTP
  - HyperText Transfer Protocol: 하이퍼텍스트 교환 방식
  - 웹에서 이뤄지는 모든 데이터 교환의 기초
  - HTTP 요청마다 method 존재
    - 종류: GET, POST, (PUT, DELETE) => 지금은 get/post만 사용할 것임



- HTTP request method - "GET"
  - 서버로부터 **정보를 조회**하는 데 사용
  - 데이터를 가져올 때만 사용해야 함
  - `query=글자&` 형태로, Query String Parameters를 통해 데이터를 서버로 전송

<br>

## URL

- Variable Routing

  - URL 주소를 변수로 사용하는 것

  - str, int, slug 가능

    ```python
    # urls.py
    urlpatterns = [
        # url을 변수처럼 활용해서 < > 이 부분에 내가 작성
        path('hello/<str:name>/', views.hello),
        # str은 `str:` 작성 안 해도 가능
        # path('hello/<name>/', views.hello),
    ]
    ```

- 그런데 app도 많아지고, 각 app의 view함수가 많아지면 사용하는 path 또한 많아짐

  -> 프로젝트의 urls.py에서 모두 관리하는 것은 Not Good

  -> **각 app에 urls.py 작성!**

  

  ```python
  # 프로젝트 폴더 urls.py 파일
  
  # 가장 먼저 요청을 받는 문지기가 urls!
  from django.contrib import admin
  from django.urls import path, include
  
  urlpatterns = [
     # articles라는 경로 시작이 있다면 articles.urls 여기로 가세요
     # 대장 문지기가 부하 문지기한테 이동시킬 때 include() 사용
     # URL에서 include에 작성된 부분을 잘라내고, 남은 문자열을 전달
     path('articles/', include('articles.urls')),
     path('pages/', include('pages.urls')),
      # 장고는 명시적 상대경로를 권장(ex. from .module import ..)
  ]
  ```
  
  ```python
  # app 폴더 urls.py 파일
  
  from django.urls import path
  from . import views  # articles의 views로 보내겠다
  
  # URL namespace: app_name 작성해두면 서로 다른 앱에서 같은 url 이름 사용하는 경우에도 이름이 지정된 url을 고유하게 사용 가능!
  app_name = 'articles
  urlpatterns = [
      # name은 templates에서, url tag에서 사용됐음
      path('index/', views.index, name='index'),
      path('greeting/', views.greeting, name='greeting'),
      path('dinner/', views.dinner, name='dinner'),
      path('throw/', views.throw, name='throw'),
      path('catch/', views.catch, name='catch'),
  ]
  ```
  
  +) name이 사용된 곳
  
  ```django
  {# index.html #}
  {% block content %}
    <h1>인덱스 페이지 입니다.</h1>
    <a href="{% url 'articles:greeting' %}">인사</a>
    <a href="{% url 'articles:dinner' %}">저녁메뉴 추천</a>
    <a href="{% url 'articles:throw' %}">던지기</a>
  {% endblock content %}
  ```
  
  - URL template tag
  
    ```django
    {% url '' %}
    ```
  
    주어진 URL 패턴 이름 및 선택적 매개 변수와 일치하는 절대 경로 주소 반환

<br>

## Namespace

- templates, static 등 django는 정해진 경로를 하나로 모아서 보기 때문에 중간에 폴더를 임의로 만들어 줌으로써 이름공간 설정

  -> 모든 앱에서 templates라고 불리는 모든 폴더를 탐색해서 index.html을 찾음

  -> 인덱스 이름이 겹치는 경우 문제가 될 수 있음( ex. articles 앱의 index 페이지로 가고 싶은데 pages 앱의 index 페이지로 감)

- URL namespace

  : urls.py에서 `app_name` attribute를 작성하고 url 태그에서 `app_name:name` 이렇게 사용

- Template namespace

  : templates 아래에 app_name 폴더를 만들어서 views에서 `app이름/index.html`을 찾을 수 있게 함!

  매우 중요! templates 폴더 아래에 앱 이름 폴더 만들고, views.py 파일에 return render()에서 `앱 이름/index.html` 이런 식으로 작성!