# 표준 입출력

**컴퓨터 프로그램과 환경 사이에 미리 연결된 입출력 통로를 가리킴**

1. 표준 입력
2. 표준 출력
3. 표준 오류


**Redirection, Pipeline을 통해 입/출력 흐름을 재정의 가능**


### :dart: 표준 출력의 Redirection
**표준 출력으로 나가는 내용들의 방향을 바꾸는 것**

- **'>'사용**
  - 어떤 명령의 결과를 파일로 보냄
  ```
  $ ls -l > dir_list
  ```
  
  
- **'>>' 사용**
  - 표준 출력 내용을 기존 파일에 append
  ```
  $ date >> dir_list
  ```
  
### :dart: 표준 입력의 Redirection
**키보드 입력을 파일로 Redirection시킴**

- **'<'사용**
  ```
  $ sort < input(filename)
  ```
  
- **표준 입력과 출력을 함께 Redirection**
  ```
  $ sort < unsorted > sorted
  ```
  > > 표준 입력은 파일 unsorted로부터, 표준 출력은 파일 sorted으로
  
### :dart: 표준 입출력의 Pipeline

**한 프로세스의 표준 출력을 다른 프로세스의 표준 입력에 연결**
**|사용**
```
$ sort input | lpr
```
> > sort프로그램의 결과를 lpr(데이터를 인쇄하는 명령어)로 보냄
```
$ ls -al | wc
```
> > ls-al 의 결과를 wc(글자수, 바이트수 알려주는 명령어) 로보냄

### :dart: 표준 출력의 Pipline


**T자 관(tee)**
  - 자신에게 들어오는 입력 데이터를 표준 출력으로 출력하고, 지정된 파일로 보내는 장치
```
$ tee [-a] <filename>
```

**보통 출력 결과를 화면으로 표시함과 동시에 파일로 저장하기 위하여 사용**
```
$ sort < input | tee sorted
```
> > 표준 입력은 파일 input으로부터, 표준 출력은 화면으로 표시함과 동시에, 파일 sorted에 저장

  
