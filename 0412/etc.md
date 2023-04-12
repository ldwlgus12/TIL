- django에서는 User 모델을 직접 참조하는 것을 권장하지 않는다 (사실상 강하게 금지)

- 간접적으로 참조할 수 있는 함수를 제공 == get_user_model()
=> 현재 프로젝트에 활성화된 'user객체'를 반환해주는 함수

- User 모델을 참조하는 방법에서 대상은 같으나 (User 모델)
```py
from django.contrib.auth import get_user_model - 객체 참조

settings.AUTH_USER_MODEL - 문자열로 참조

반환 값이 다름
```

- 관계형 필드에서 null=True는 별 의미가 없어서 사용x


- 현재 수정을 진행하려는 유저 vs 작성자 - 비교
    - 둘이 같아야만 글 수정이 가능하도록


