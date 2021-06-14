### git 설치 여부 확인

```git --version```


### 버전 관리가 불필요한 파일

- 개발 툴에 의해서 생기는 설정 파일
- 컴파일 시 자동으로 생기는 파일
- 문서의 자동 저장 버전
- 빌드한 프로그램이 자동으로 만드는 파일

### .gitignore
- 버전 관리에서 제외되도록 설정


### stage

![image](https://user-images.githubusercontent.com/73538957/121835462-525c1480-cd0c-11eb-92d2-4f6019fdaf67.png)


### commit 
![image](https://user-images.githubusercontent.com/73538957/121835604-acf57080-cd0c-11eb-8a03-8754a0de0617.png)
- 메시지 = 변경의 이유


### push
![image](https://user-images.githubusercontent.com/73538957/121835705-dc0be200-cd0c-11eb-9cd5-28492e02f990.png)


### 변경후 다시 stage, commit, push

![image](https://user-images.githubusercontent.com/73538957/121835769-03fb4580-cd0d-11eb-86d0-b89bf8150546.png)


### 변경 이유가 다르면, 커밋은 분리되어야 함
```
git add graph.py
git commit -m"커밋메시지"
git add .gitignore
git commit -m"커밋메시지"
git push
```

### 이슈

- 커밋 메시지에 ```#issue_id```를 포함하면 해당 이슈에 등록됨

### git으로 파일명을 변경하여도 과거 파일 기억하도록 하기

- 이력 조회 : ```git log --oneline 파일명```
- 파일명 변경 : ```git mv 파일명 변경할파일명```
- 상태 조회 : ```git status```




### 직전 커밋과 합치기 ( 마지막 커밋에 파일이 누락된 경우 )
```git commit --amend```



