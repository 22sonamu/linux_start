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


