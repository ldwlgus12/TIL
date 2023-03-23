# # django - templates 연산 사용법

## # django - mathfilters

<br>

>install
- 터미널 창에 입력하여 `django-mathfilters` 설치
```py
pip install django-mathfilters
```

<br>

> Add
- settings.py 파일에 `mathfilters` 추가
```py
INSTALLED_APPS = [
    'mathfilters',
]
```

- 사용할 templates에 `{% load mathfilters %}` 추가
```py
{% load mathfilters %}
```

<br>

> 종류
- `sub`
- `mul`
- `div`
- `intdiv`
- `abs`
- `mod`
- `addition`

<br>

> 사용 예제
```django
{% load mathfilters %}

<p>8 + 3 = {{ 8|add:3 }}</p>
<p>8 - 3 = {{ 8|sub:3 }}</p>
<p>8 * 3 = {{ 8|mul:3 }}</p>
<p>8 // 3 = {{ 8|intdiv:3 }}</p>
```
<br>

- 참고) 
    - https://growing-nyang.tistory.com/40
    - https://pypi.org/project/django-mathfilters/

