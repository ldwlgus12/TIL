- <str:pk>에서 str은 생략 가능하기 때문에 아래와 같이 적음
```py
path('<username>/', views.profile, name='profile'),
```

- 위의 주소에서 <username>은 변수명일 뿐이고 사실은 문자열, 이 밑에 쓰여지는 나머지 주소는 죽어버림


- 해결 방법 1
    - 해당 주소를 계속 맨 아래쪽에 놔둠
- 방법 2
    - path('profile/<username>/', views.profile, name='profile'), 이런식으로 앞에 추가해줌

<br>

- context로 넘겨줄 때 템플릿 파일에는 이미 내장된 user 변수가 있기 때문에 user라는 변수명을 잘 안씀. (person 같은 걸로 대체)


- followings = models.ManyToManyField('self', related_name='followers', symmetrical=False) 에서
followings의 related_name='followers' 인 이유 -> 팔로워를 조회하는 것이기 때문에 `역참조 개념`


- 내 프로필 페이지가 아니라 상대방의 프로필 페이지기 때문에 
```py
return redirect('accounts:profile', you.username) 에서
you.username 사용
```
<hr>

- fixtures : 추출 & 로드

- 생성하면서 모델명 그런거 쓸 때 다 소문자로

- `--indent 4` 는 들여쓰기 4개를 넣겠다는 뜻

```py
python manage.py loaddata articles.json users.json comments.json
```
- utf-8 뭐시기 에러 뜨는건 거의 `한글 관련` 오류

- Installed 9 object(s) from 3 fixture(s) 이런식으로 뜨면 성공

