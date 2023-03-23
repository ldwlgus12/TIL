- <path_converter : variable_name>
타입 : 변수 이름

--------------------------------
```
path('articles/<int:num>/', views.detail),
```

- def detail (request, num):
서로 변수명이 맞아야 한다. (num)

- `<str:name>` 에서 str은 생략가능

- 함수와 함수, 클래스와 클래스 사이는 2줄 씩 띄우는 걸 권장 (스타일 가이드)

- `<form>`과 `<a>`의 차이
    - 둘 다 매서드 get 방식으로 요청을 보낸다
    - 그러나 a는 데이터를 보낼 수 없다. 해당 주소로 요청만 보낼 수 있다.

----------------------------------
### # 두번째 앱 생성
`python manage.py startapp pages`

- url을 한 곳에서 관리 하려 했기 때문에 여러 문제 발생, 책임을 좀 위임

- 앱에는 기본적으로 url 파일이 만들어지지 않음 -> 우리가 앱에서 urls.py를 만들어야 함
만들 때 urlpatterns 이름 바뀌면 안됨
- path('admin/', admin.site.urls), 냅두고 본인 path만 옮김

- (장고 권장사항) 명시적 상대 경로 -> from . import views 입력

- url을 수정하면 form 작성시에도 action = /articles/catch/ 이런식으로 적어야 작동


- `path('index/', views.detail_name, name='index'),` 로 이름 설정해주면 이제 앞에 index/는 중요하지 않음

- name을 작성하면 form 작성시에도 `action = {% catch %}` 이런식으로 변경

- `두번째 앱 생성하고 templates 폴더 만드는거 잊지말기`

- 네임이 겹치는 걸 방지하기 위해 명찰을 달아줌 
```
urls.py -> app_name = 'articles' 추가 -> html {% url '' %} 부분 변경
```
- `app_name은 변경하면 안됨.` 변경하면 작동안할 수 있음(장고에서 정한거)

- NoReverseMatch 에러 -> `무조건 url 관련 문제`
- 명찰이 붙는 순간 단독 이름을 쓸 수 없다.
- html파일에서 {% url 'articles:catch' %} 라고 명찰을 붙여줘야 함.

-------------------------------
- 나중에 코드리뷰 같은거 할 때 왜?? 를 많이 물어봄
- 왜 이렇게 풀었냐, 왜 이런 기술을 사용했냐.. 등

- 초기 페이지가 불편하다면
path('', views.index) 이런거 추가하면 됨

```
** 직접 격은 오류 관련 **

url에 이름이나 숫자를 입력해야 하는 경우의 페이지가 있는데(그 페이지 이름을 apple이라 하고)
(ex. http://127.0.0.1:8000/articles/jihyeon/) - 입력값 jihyeon/

다른 abc라는 html에 apple 페이지의 링크를 a링크로 넣고 abc.html을 url로 불러오면
당연하게도 현재 apple 페이지 url에 입력된 값이 없기 때문에 오류가 발생한다.

<a href="{% url 'articles:detail_name' %}">이름</a> 
- 이거 때문에 오류가 나서 한참 헤맴
그렇기에 url에 입력값이 없어도 되는 페이지를 불러올 것.
```






