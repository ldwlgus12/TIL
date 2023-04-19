- axios는 파이썬의 request

- requests를 사용하기 위해 설치해줘야함
    - pip install requests

- 자바 스크립트는 성격이 급하다
    - 응답을 기다리며 다른 것을 실행

<br>

- 밑에 두 코드는 구조만 다른 같은 개념
```py
# py
cat_image_search_url = 'https://api.thecatapi.com/v1/images/search'
response = requests.get(cat_image_search_url)


# html
axios({
      method: 'get',
      url: catImageSearchURL,
    })
      .then((response) => {
        console.log(response.data)
      })
```

<br>

- html은 대소문자 구분 못함
    - -(하이픈) 구분
- data-... 이렇게 쓰면 dataset이라는 곳에 들어가게 됨
    - 무조건 data- 로 써줘야함


<br>

- Ajax 순서 정리

1. JS의 Axios 라이브러리로 장고 서버로 요청을 보냄

2. 장고는 필요한 데이터를 정리하여 JSON으로 응답 (문서x)

3. JS는 Axios 라이브러리로 응답 데이터를 받아서 필요한 데이터를 저장

4. DOM 조작이 필요한 HTML 요소들을 선택해서 저장한 데이터를 사용해 DOM을 조작


<br>
<hr>
<br>

```py
print(os.getenv('환경변수 키')) - 환경변수 키: os

print(os.getenv('os'))
>> Windows_NT
```

- 시스템 환경변수 - os 내부에 존재

- 프로그램 환경변수 - 특정 프로그램 내부에서만 사용 가능 (다른 프로그램에서 접근 불가)

- `pip install -r requirements.txt` 잊지말기 ! !

```
Iaas - 빈 깡통 (EC2)
Paas - 환경이 구축된 상태
Saas - 완전한 상태
```

