- doctor1.reservation_set.all() - 1이 N을 참조하는 역참조
```py
<QuerySet [<Reservation: 1번 의사의 1번 환자>], <Reservation: 1번 의사의 2번 환자>]>
```

- doctors = models.ManyToManyField(Doctor) -> 
`중개테이블`을 위한 모델 필드

```py
patient1.doctors.add(doctor1) -참조
doctor1.patient_set.add(patient2) - 역참조

patient1.doctors.all() - <QuerySet [<Doctor: 1번 의사 alice>]>
doctor1.patient_set.all() - <QuerySet [<Patient: 1번 환자 carol>, <Patient: 2번 환자 dane>]>
```


- Foreignkey는 반드시 `N쪽`에 있어야함
- 하지만 ManyToManyField는 어느쪽에 있어도 상관x


- `오늘의 핵심 add, remove` 


- `through='Reservation'` 을 적으면 Reservation이 중개테이블이 되도록 함
-----------------------------
```py
# 충돌에러

ERRORS:
articles.Article.user: (fields.E304) Reverse accessor for 'articles.Article.user' clashes with reverse accessor for 'articles.Article.users'.
```


Article - User (N:1)
1. article.user
2. user.article_set

Article - User (N:M)
1. articles.user
2. user.article_set

- 역참조 명령어에서 충돌 발생, 다음과 같이 수정

Article - User (N:M)
1. article.like_users.all() => 게시글에 좋아요를 누른 모든 유저
2. user.like_articles_all() => 유저가 좋아요를 누른 모든 게시글

<br>
<hr>
<br>

- 오늘의 실습 오류

```py
<form action="{% url 'articles:comment_delete' article.pk comments.pk %}"> 에서

comments.pk 안써서 계속 url 오류 남ㅎㅎ 잊지말기..!
```


