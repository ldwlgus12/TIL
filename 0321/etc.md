- 프로젝트 시작 관련 명령어는 django-admin ...임
- 그 외 나머지는 python managr.py ... 임

- vscode 에서 프젝 생성 4가지 단계 하고 django-admin startproject firstpjt . 하고
python manage.py runserver로 확인하고 ctrl + c

--------------------------------------------------

- `생성과 등록은 항상 같이 움직임`
- `생성 -> 등록`

- python manage.py startapp articles - 하면 폴더가 하나 생기는데 그게 앱 생성한거.
생성 후
firstpjt 폴더 -> setting.py -> INSTALLED_APPS = [ ... ] 맨 위에 'articles', 를 넣어주며
앱을 등록해준다.
- `반드시 앱을 생성한 후에 등록`해야 함
- 반대로 등록 후 생성은 불가능 (앱이 안만들어짐)

-----------------------------------
- mvc와 mtv에서 view는 완전 다름

- 나중에 배포할 때 빼고 지금은 firstpjt파일에서 settings.py와 urls.py 파일만 알면 됨
그 외 4개 파일은 몰라도됨 (__init__.py파일은 패키지로서 인식하게 한다.)

- http://127.0.0.1:8000 에 /admin을 붙이면 - 관리자 페이지로 접속

- 요청은url로 간다.
- 우리가 보낸 요청은 `서버`로 가서 서버는 그 요청에 대한 페이지로 응답(관리자 페이지로 응답)

- 프로젝트(firstpjt)는 mtv 패턴이 아님
app이 mtv 패턴

- mtv의 t는 기본적으로 자동으로 등장하진 않음. 우리가 만들어줘야 함

- articles의 init.py / apps.py / tests.py는 안봐도 됨
- `봐야할 것들에만 집중`

- `views.py (view)가 가장 중요한 파일이 될 것이다.` (controller니까)

---------------------------------------------------
3. 

- 데이터 흐름이 코딩 순서
- `*** URLs -> View -> Template ***
`
- http://127.0.0.1:8000/articles/ - 메인페이지 주소

- url은 메인페이지 역할을 할 view를 찾는 역할

- urls.py에 path가 무엇인지 까보려 하지 말고 이런 형태로 작성된다는 것을 알면 됨

- 우리는 파이썬을 쓰고 있기에 위치 인자의 이름은 우리가 정하는 것.  
- 그래서 views.py -> def index(request): 에서 request 객체는 바꿀 수 있음. (문법상 아무런 문제가 되지 않음)
하지만 바꾸지 않는다. django 규칙이다.
반드시 request로 써줘야 함.
(메인페이지를 보통 index라 함)

- urls.py에서 views.py 호출
```py
# urls.py 입장에서는 articles라는 패키지에서
# views라는 모듈을 가져와야 함

from articles import views

* from articles.views import index 로 쓸수도 있지만 위 형태로 쓴다.
```
- `views.index 함수안에 인자로 들어가는 함수 -> 콜백 함수`

```py
path('articles/',views.index)

path('articles/',views.index()) => 2번째 인자로 index함수의 반환 값 - 이렇게 쓰면 안됨. 값이 완전 달라짐
```

- views.py -> 페이지를 만들어내는 함수 `render`


- 다 만들고 http://127.0.0.1:8000/ 입력 시 로켓화면은 더 이상 안나옴
- http://127.0.0.1:8000/articles/ 입력 후 정상적으로 나오면 성공!
- 새로고침 하면 요청을 또 보낸 것이므로 로그에 남는 것

<br>

- 실습하며 발생한 문제점 : 
1. view에서 html파일을 지정해줄 때 return render(request, 'berners_lee.html') 인데
교재를 보고 따라하다 return render(request, 'berners_lee/berners_lee.html')로 지정해버림
기본 경로에서 하위 폴더가 없는 상태인데 하위폴더를 지정해주다 보니 페이지를 찾지 못한다고 에러가 뜬 것
django에서 template을 인식하는 경로 규칙을 주의할 것!!

2. templates 파일 내부에 이미지를 넣어도 페이지에선 이미지가 깨지는 것을 확인.
그래서 이미지를 넣을 때 링크로 넣어야 한다는 것을 알게 됨.

