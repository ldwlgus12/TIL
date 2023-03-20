### # `클라이언트 - 서버 구조` (***왕중요***)
- 요청을 보내야 응답이 온다

----------------------------------------


장고 git bash 에서 2번 가상환경 활성화를 하고 난 후 콘솔창 밑에 venv가 뜨는데 이것은
`지금 당신은 venv라는 가상환경이 켜져 있다. 라는 뜻 (가상)`

한 깃 베쉬에서 2개의 가상환경 쓸 수 x, 하나 더 쓸려면 깃 베쉬 하나 더 켜야함

deactivate 치면 가상환경 끌 수 있음 (잘 안씀)

환경을 공유하기 위해선 상대에게 종이 한 장(기록지)을 준다.
= 가상환경 자체를 공유하지 않는다.
= pip freeze > requirement.text (의존성 목록 생성)
venv와 requirement 라는 이름은 바꾸면 안됨 (암묵적 룰)

django-admin startproject firstpjt . 후에 vscode로 넘어가기

--------------------------------------- 
vscode

vscode에서 interpreter로 가상환경을 켜 줌
interpreter할 때 터미널 창 켜져있으면 창 끄고 interpreter 하고 터미널 창 새로키기
그 후 터미널을 새로 열면 source ~... 명령어가 돌면서 가상환경이 켜짐

vscode에서 python manage.py runserver를 하면 링크를 클릭해 장고 화면을 볼 수 있음(아무것도 하지 않았을 때 보이는 화면)
프젝 시작하고 이 화면 안보이면 문제가 있는거임

ctrl + c 하면 서버꺼짐

---------------------------------

manage.py가 있는 곳에서 서버를 켜야 활성화 할 수 있음

git add . 하기 전에 .gitignore로 venv파일 숨겨야함 (얜 공유하면 안되니까)
db 파일은 알아서 공유안됨

페어는 파일을 받으면 가상환경을 만들어야함
그리고
pip install -r requirement.text 로 의존성 파일 불러오기