### wsgi 웹 서버 실행 순서

1. Apache 모듈 설치
  - apachectl -M 명령 --> 실행중인 서버에 적재된 모듈 나열 --> grep 에 의해 'wsgi'가 포함된 행들만을 골라서 화면에 표시
  
2. 스크립트 작성
  - /usr/local/이름 의 디렉토리 새로 생성
  - 권한 바꾸기
  - py파일 만들기
 ![image](https://user-images.githubusercontent.com/73538957/121819266-15b9fa00-ccc7-11eb-9b3b-8d251d225e0c.png)


3. 서버와 스크립트를 연결하는 ***conf파일*** 작성
 ![image](https://user-images.githubusercontent.com/73538957/121819282-266a7000-ccc7-11eb-8109-c2b1b7af3446.png)


***접속 주소는 http://IP/스크립트이름***


### 웹서버 로그 파일 확인

- /var/log/apache2/access.log
- /var/log/apache2/error.log
- 주소, 접속시각, 접근 url , 응답 코드, 길이 등


### 함수 그래프 그리기 wsgi 웹 서버 만들기
```위와 같지만 , 두가지 추가 점이 있다.```
1. 이미지를 서비스할 디렉토리
  - /evt/apache2/site-enabled/000-default.conf 의 DocumentRoot에 img 파일 경로 입력 (상위 폴더까지)
  - ![image](https://user-images.githubusercontent.com/73538957/121819474-35055700-ccc8-11eb-9d64-20f91ebc5810.png)

2. 스크립트 추가 작성
  - 파일 저장 위치 업데이트
  - conf 파일에 WSGIPythonPath ```/usr/local/이름``` 추가
