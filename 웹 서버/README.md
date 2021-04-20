# 데몬 프로세스
1. 사용자가 직접적으로 제어 하지않고, 백그라운드에서 여러 작업을 한다.
2. 데몬을 뜻하는 'd'를 이름끝에 달고 있다.
3. 일반적으로 프로세스로 실행된다.
4. 부모 프로세스를 가지지않으며, init 바로 아래에 위치한다.


### :dart: 웹서버 서비스 시작
```
$ service apache2 start
```

### :dart: 웹서버 서비스 중단
```
$ service apache2 stop
```

### :dart: 웹서버 서비스 재시작
```
$ service apache2 restart
```

### :dart: 웹서버 실행 확인
```
$ service apache2 status
```

### :dart: 웹 서버의 설정 파일 위치
/ect/apache2/apache2.conf

### :dart: 테스트 페이지 위치
/var/www/html


### :dart: html페이지 지정
설정파일의 DocumentRoot

### :dart: CGI 실행
1. /etc/apache2/conf-enabled/serve-cgi-bin.conf 에서 GCI 스크립트 위치 확인

2. 그 위치에서 스크립트 작성(.sh)

3. 권한 부여(스크립트에 r,x권한 있어야함)
```
$ sudo chmod 755 /usr/lib/cgi-bin/example.sh
```

4. CGI모듈 활성화

```
$ sudo a2enmod cgi
```

5. 서버 재시작

6. http://localhost/cgi-bin/example.sh로 접속
