- submit이 있어야 form의 데이터를 취합해 action의 주소로 보내지게 된다.

- http://127.0.0.1:8000/search/?message=장고
- message=장고 - key=value 형태 -> 서버로 전송

<br>

- 네이버의 경우
- https://search.naver.com/search.naver?key=value & key=value & key=value & query=뉴진스 - 형태
- 즉, 데이터를 여러 개 보낼 수 있다
- 얘네는 name 속성을 query라고 설정한거임.
- `name은 input의 핵심 속성`

- https://search.naver.com/search.naver?query=뉴진스 해도 검색창에 뉴진스 친거랑 똑같이 나옴

- method="GET" - 설정안하면 자동으로 get으로 설정됨
- get은 데이터를 url로 받는다
- post도 있는데 얘는 나중에
로그인에 get형태를 써버리면 아이디, 비번이 url에 공개돼버리기 때문에 post를 사용함

------------
```
<label for="message">검색어 : </label> 
```
- 입력 후 검색어를 누르면 연결된 input이 깜빡거림 


```
<label for="message">검색어 : </label>

<input type="text" name="query" id='message'>
```
- label의 for값과 input의 id값을 매칭하는 원리


-------------------
- action에 http..로 적지 말고 /catch/ 이런식으로 적으면 현재 링크에서 catch로 바로 넘어감
- 단, 앞에 / 붙여줄 것

<br>

- 한 사이클 (결국엔 요청과 응답)
1. /throw/ 주소로 요청을 보냄
2. django는 /throw/ 주소에 맞는 throw 뷰함수를 호출(응답)
3. 유저는 django의 응답 결과(throw 페이지)를 받음
4. input에 데이터를 입력하고 제출을 누름 (action 주소로 요청을 보낸 것)
5. action 주소는 /catch/ 였고, /catch/로 django에 요청을 보내는 행위
6. django는 /catch/ 주소에 맞는 catch 뷰함수를 호출 (응답)
7. 유저는 django의 응답 결과(catch 페이지)를 받음

--------------------------
- 추가 템플릿 경로 지정
```py
settings.py ->
	TEMPLATES = [
		'DIRS': [], - 초기엔 비어있음. 여기에
		'DIRS': [BASE_DIR / 'templates', ], - 추가
```


