- MEDIA_ROOT = BASE_DIR / 'media' 를 설정하면 사용자들이 미디어를 업로드하면 알아서 media 폴더가 생기며 거기에 저장됨 -> `물리적 주소`

- MEDIA_URL = '/media/' - 제공

- ImageField는 그냥 사용 불가

- 테이블에는 파일에 대한 주소(경로)가 저장
- 실제 파일은 MEDIA_ROOT = BASE_DIR / 'media'로 설정해 놓은 폴더에 저장

- <img src="{{ article.image }}" alt=""> 하면 그냥 파일명을 불러온 것

- 만약 image.png 와 이름이 같은 파일이 업로드 되면 구분하기 위해 장고에서 알아서
image_uRdklsl.png 와 같이 뒤에 해시값을 붙임

```py
enctype="multipart/form-data"
```
- `input 타입이 FILE이면 무조건 써줘야 함`

<br>

```py
image = models.ImageField(blank=True, upload_to='%Y/%m/%d')
```
- 로 설정하면 media > 2023 > 04 > 10 > sample.png 이런식으로 날짜별로 세분화할 수 있음


