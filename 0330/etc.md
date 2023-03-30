- articles -> views.py -> redirect 반환

- render로 하려면 데이터를 다시 불러와야 함. 아니면 페이지가 이상하게 뜸.
- 그러나 데이터를 불러오더라도 주소가 이상하게 뜨기에 redirect 하는 것(url을 반환)

- context - 템플릿에 데이터와 함께 렌더링
```
# 결과 페이지 (전체 조회 템플릿) 반환 - 사용 X
return render(request, 'articles/index.html')

위의 방법 대신

# 이동할 주소(url)를 사용자에게 반환
return redirect('articles:index') - 얘를 사용
```

- `요청과 응답`

- 삭제 시 조회가 아닌 데이터베이스 수정, 삭제라 post
- `조회를 제외한 모든 것`에는 post라 생각하면 됨


- 실습 시 오류 참고한 사이트
    - https://dev-mht.tistory.com/77

    - https://docs.djangoproject.com/en/3.2/ref/templates/builtins/#date

