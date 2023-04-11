- model에 article = models.ForeignKey(Article, on_delete=models.CASCADE) 를 만들게 되면 

- db 테이블에 article_id(외래키 필드의 이름)가 만들어지게 됨.

- %주의% 그렇다고 model 만들 때 
article_id = models.ForeignKey(Article, on_delete=models.CASCADE)로 만들면 안됨

- 이러면 외래키 필드가 article_id_id로 만들어지게 됨

<br>

- commit=False -> 인스터스는 생성, DB에 record는 멈춤

- 원래는 기본값으로 commit=True가 계속 들어가고 있던 것.

<br>
<hr>
<br>

- 오늘의 오류

    - `TemplateDoesNotExist at ~/~/`
    
    - 회원가입 버튼을 누르니 위와 같은 오류가 떠서 살펴봄. 

    - 경로를 다 올바르게 설정했는데도 장고에서 signup.html파일을 accounts/templates/accounts/signup.html 이 아닌

    - reviews/templates/accounts/signup.html 에서 찾음

    - 왜 그런지 찾아보니 처음에 settings.py -> app 등록에서 accounts를 등록 안하고 시작한 것;;
    - 얼탱x 그래서 등록하고 앱 지우고 다시 시작하려니 다른 오류가 발생해서 그냥 새로 시작.

