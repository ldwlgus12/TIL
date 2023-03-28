- migration 필수 단계
1. models.py에 변경사항이 생겼을 때
2. 청사진(찐설계도), makemigrations
3. migrate

---------------------

- Article.objects.all() 에서 all
이 문구는 SQL에서 SELECT * FROM table 과 같다.

- objects는 Queryset API를 제공해주는 중간 매개체 (신경 쓸 필요가 별로 없다)
- `여기서 핵심은 Queryset API(all())
(QuerySet은 타입 이름)`

- 파이썬 셸에서 외부 라이브러리 설치
- `pip install ipython django-extensions` 이렇게 한 줄로 여러개 설치가능
- 설치하고 settings.py에 django_extensions를 등록 해줘야 python manage.py shell_plus 사용가능
- 그 후 pip freeze > requirements.txt 를 입력해 업데이트 해준다.

- python manage.py shell을 입력하면 ipython을 입력했을 때와 같은 셸 형태가 생기지만
장고 프로젝트에 영향을 주고, import 또한 할 수 있다.
- 나갈 땐 exit 입력

- class도 일종의 청사진
- a = math() 에서 a는 math 클래스의 인스턴스

- 17페이지)
- article.save() 라는 인스턴스 메서드 호출
- Article.objects.all()하면 목록으로 기본적으로 온다. -> 즉, 순회가 가능하다
- 테이블을 객체로 변환해 각각 출력

```py
articles = Article.objects.all() 넣고

for article in articles:
   print(article) 하면

Article object (1)
Article object (2) 출력
```
```py
for article in articles:
    ...:     print(article.id)
    ...:     print(article.title)
    ...:     print(article.content)
    ...:     print(article.created_at) 하면

1
title
django!
2023-03-28 01:38:58.549553+00:00
2
second
django!
2023-03-28 01:46:49.677412+00:00  

- 이렇게 테이블 값을 불러올 수 있음
```
- article.id 대신 `article.pk`로 입력하는 것을 권장

- `save를 하지 않으면` 데이터가 저장된 상태가 아니기 때문에 article.pk를 해도 데이터 조회가 안된다.

----------------------------------------------------------
- 단일 데이터 조회
```py
article = Article.objects.get(pk=1)
```

- Article.objects.get(pk=100) 이렇게 없는 값을 조회하면
- DoesNotExist: Article matching query does not exist. 라는 에러가 뜸.

- `get은 무조건 존재하는 '하나'의 데이터를 조회`해야함. 유일한 값(즉, pk를 사용해야함)

- 그래서 일치하는 여러개의 데이터를 조회할 땐 `Article.objects.filter(content='django!') 처럼
filter를 사용`해야함 (만약 그 데이터가 없다면 빈 쿼리문을 조회한다. 에러 발생x)

```py
# 만약 dj로 시작하는 데이터를 조회하고 싶다면?
Article.objects.filter(content__startswith='dj')와 같이 __startswith 을 사용


# 문자열에 !가 들어가는 데이터를 조회하고 싶다면?
Article.objects.filter(content__contains='!')


# ~보다 큰 (gt - greater than / gte - greater than or equal)
pk 3 이후의 값 -> Article.objects.filter(pk__gte='3')



# pk를 오름차순으로 정렬(order_by)
Article.objects.order_by('pk')

# 뒤집어서 내림차순으로 정렬
Article.objects.order_by('-pk')

# 임의로 정렬(랜덤)
Article.objects.order_by('?')
```
- 아직은 get과 filter에 집중

------------------
- print(~.query) 를 입력하면 SQL문으로 출력
```py
# print(Article.objects.all().query) 하면

SELECT "articles_article"."id", "articles_article"."title", "articles_article"."content", "articles_article"."created_at", "articles_article"."updated_at" FROM "articles_article"

# print(Article.objects.filter(content='django!').query) 하면

SELECT "articles_article"."id", "articles_article"."title", "articles_article"."content", "articles_article"."created_at", "articles_article"."updated_at" FROM "articles_article" WHERE "articles_article"."content" = django!
```



