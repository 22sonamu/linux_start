# shell


**사용자가 입력하는 명령을 해석, 실행하는 프로그램**
> > 응용프로그램>쉘>커널>CPU,RAM

### :dart: 나의 로그인 shell

**/ect/passwd**


### :dart: shell 환경변수
**프로그램 사이에 미리 설정된 값들을 전달해주는 역할을 하는 변수**

- 설정
  ```
  $ export variable_name=value
  ```
  
- 확인
  ```
  $ pritenv [variable_name]
  $ env
  ```
- 대표적인 환경변수
  - PATH
    - 디렉토리 값을 넣는다
- 환경 변수 파일
  - bin 디렉토리
  - ~/,bashrc 에 경로를 지정한다
### :dart: Shell Scripts

**명령들을 프로그래밍 형태로 파일에 저장하여 실행 가능**
