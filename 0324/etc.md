- 모델 클래스 하나는 테이블 하나

- 모델 생성 시 startproject crud . 로 생성
- 테이블 이름이 필요하듯 클래스 이름도 필요

- 클래스의 가장 강력한 특징 : 속성
models라는 모듈안에 Model이라는 게 있음

```py
class Article(models.Model):
    # 테이블 이름을 정했으니
    # 필드 이름 / 데이터 타입 / 제약 조건을 정해야함.
```

- id, 제목, 내용 이런거 다 클래스 변수명
- 데이터 타입 : 문자열 

```py
class Article(models.Model):
    # 테이블 이름을 정했으니
    # 필드 이름(변수명) / 데이터 타입(모델 필드 클래스) / 제약 조건 (모델 필드 클래스의 키워드 인자)
    title = models.CharField(max_length=10) - (하나하나 메서드들로 구성, 클래스로 호출)
    content = models.TextField()
```

- id 필드는 자동 생성된다.
```
- CharField : 길이제한을 줘야하는 것들

- TextField : 길이 제한 x

- max_length : Required, 즉 필수 인자. 안쓰면 에러남

- max_length=10 에서 10자 이상으로 쓰려하면 장고에서 막음

- CharField에 max_length써도 상관은 없는데 써봤자 아무런 변화x. 쓸모없음
```

- 자료 13페이지 - 정확히는 model field 메서드가 아닌 클래스

--------------------------
- migration

```
python manage.py makemigrations

- 이 과정을 건너뛸 수 없음
```

- migrations폴더에서 0001_initial.py 파일은 설계도 느낌

```py
python manage.py migrate 하면 db파일에 무엇인가 쭉 생성됨

(articles_article) - 앱이름_클래스이름 ==> 테이블이름 (장고에서 알아서 만들어줌)
```
--------------------------
- 필드 추가시 models.py에
```py
# 필드 추가
created_at = models.DateTimeField(auto_now_add=True)
updated_at = models.DateTimeField(auto_now=True)

- True 안하면 기본값인 False가 됨.
```


- `변경사항 추가하고 python manage.py makemigrations 필수!!`

- 22페이지 - 문자열이면 default를직접 넣는게 (2번) 나음
- 하지만 시간 데이터는 1번이 나음
- 1번넣고 또 나오는 문구에 아무것도 입력하지 않고 엔터를 누르면 django가 제안하는 기본값으로 설정됨.

```
dependencies = [
    ('articles', '0001_initial'),
]


- 0002.~py 파일은 1번 파일을 기반으로 추가된 것이기에 의존성을 띈다.
```


- `확인하고 python manage.py migrate로 파일을 꼭!!!! 업데이트 해줘야함`

- 0001, 0002 이렇게 설계도를 쌓아감(오류가 발생하더라도 이전 시점으로 되돌리기 위해)
git commit과 똑같다.

- 페이지 26) 반드시 새로운 설계도를 생성하고 - makemigrations
- 이를 DB에 반영해야 한다. - migrate

- DateField도 있는데 얘는 날짜만 들어가는 것

- `auto_now는 updated_at에 적합`
- `auto_now_add는 created_at에 적합`

- 파이썬 설계도(0001, 0002,.. 파일)를 django가 SQL로 번역해 DB에 전달해주고 있다 생각하면 됨.

---------------------------

```py
python manage.py createsuperuser
```

- 이메일은 입력 안하고 그냥 패스가능
- 다 입력하고 y 입력 - Superuser created successfully. 뜨면 성공

- 유저 데이터 -> DB에 기록

- 테이블 안만들고 superuser만드는 건 그냥 날리는 거임

- 다 만들고 db파일에서 auth_user 확인하면 계정이 생성된 것을 확인할 수 있음
- 비밀번호는 암호화 돼서 나타남. 어떤 사이트든 비밀번호 원본을 저장하지 않음

- 이제 runserver하면 빨간색 뜨는건 migrate하라는 뜻이었는데 이제 뜨지 않음

- 그러고선 admin url들어가면 이제 로그인 할 수 있음
-------

- articles(앱 폴더)폴더에 admin.py -> 아래 내용 추가
```py
from django.contrib import admin
# 명시적 상대경로
# .models = 현재 파일 위치의 models
from .models import Article

# Register your models here.
# 우리가 만든 Article 클래스를 등록
# 암기 꿀팁 : 'admin site에 등록(register) 하겠다'
admin.site.register(Article)
```
- `admin.py에 등록하지 않으면 admin site에서 확인 할 수 없음`

- 위 내용 등록하고 admin사이트가서 articles 내용 CRUD 가능.
- 그리고 title 적을 때 아까 적어놓은 길이 제한 때문에 10자를 초과하려해도 자동으로 입력되지 않음.

- 데이터 CRUD 테스트를 하며 우리 모델에 문제가 없다는 것을 확인할 수 있다
- 그리고 db 파일에서도 실제 테이블에 저장되었다는 것을 확인할 수 있다

- settings.py 에서
- LANGUAGE_CODE = 'ko-kr'로 바꾸면 admin 사이트나 로켓화면, 에러화면 등이 한글로 바뀐 것을 확인할 수 있다.

- 40페이지 [x] 표시가 안되어 있으면 확인되지 않았다 그런 뜻

- 뭔가 잘못됐다? 0001, 0002,.. 이렇게 번호 붙은 파일이랑 db파일 삭제로 초기화 가능
- `단, migrations 폴더는 지우면 안됨!!`



