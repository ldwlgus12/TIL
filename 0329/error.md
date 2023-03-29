## # 오늘의 오류

<br>

1. 
html 파일에서 form 작성 시 action에 url을 입력하고 <br>
articles : create 이런식으로 입력해야 하는데 <br>
url을 입력 안하고 그냥 articles : create 입력해버려서 작성한 내용이 보내지지 않는 현상 발생

<br>

2. 
url이 http://127.0.0.1:8000/todos/23/ 이런 방식인데 <br>
path('<int:todo_pk>/', views.detail, name='detail'), <br>
path('<int:list>/', views.list, name='list'),

만약 urls.py 파일에서 위처럼 숫자를 입력받는 방식의 url이 2가지가 된다면 <br>
`name을 지정하더라도` 맨 위의 url로 반환될 수 있다는 것을 알게 되었다. <br>
그래서 path('tds/<int:list>/', views.list, name='list'), 로 밑의 url을 수정했더니 문제가 해결됐다.
