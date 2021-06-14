### matplotlib

- python에서 자료를 차트나 플롯으로 시각화하는데 이용되는 패키지


```python
x = list(range(-4, 5))
y = [n ** 2 for n in x]
graph = plt.plot(x, y)
plt.grid()
plt.show()

```


##### 그래프를 이미지 파일로 저장

```
fig.savefig('graph.png')
```



##### 이미지 파일을 랩톱으로 전송

```
sftp kmucs@192.168.0.10
get graph.png
```

### WSGI

***Web Server Gateway Interface***

- python을 이용하여 웹을 유연하게 개발할 수 있게 해줌
- Django, Flask등이 wsgi 기반하여 개발됨




```python
def application(environ, start_response): # 함수 선언

  start_response('200 OK', [('Content-Type', 'text/plain')]) # 인자 : 상태 코드, 헤더
  yield 'Hello World\n' # yield -> 문자열을 응답의 몸체에 출력

```
```python

from wsgiref.simple_server import make_server

def application(environ, start_response):
 response_body = [
    '%s : %s' % (key, value) for key, value in sorted(environ.items())
  ] // environ에 들어있는 key , value 쌍을 key순서대로 정렬하여 \n으로 이어 붙힌 문자열을 만든다.
  respense_body = '/n'.join(response_body)
  status = '200 OK' # 200 OK의 상태와 헤더 정보를 담아 HTTP response를 개시한다.
  response_headers = [
    ('Content-Type', 'text/plain'),
    ('Content-Length' , str(len(response_body)))
  ]
  start_response(status, response_headers) 
  return [response_body] # 위에서 만든 문자열을 반환한다.
```
###### 첫번째 wsgi스크립트
```python
httpd = make_server( # http server 객체 생성
  '', # 서버의 주소
  8051, # 포트 지정
  application # 함수 지정

)
httpd.handle_request()
```


### environ['PATH_INFO']
  - 클라이언트로부터 요청된 url의 경로정보를 담고있음
  - documentroot로부터 경로를 "/"로 시작하여 표현
  - ex ) /graph.png
  
### environ['QUERY_STRING']
  - 클라이언트로부터 요청된 url 의 query string을 담고 있음
  - parse_qs(environ['QUERY_striNG/'])으로 key, value쌍을 dict 형태로 얻을 수 있음
  

### wsgi 구성

1. template.py
  - 입력 폼, 그래프 이미지를 포함한 html 문서 몸체를 문자열로 제공
2. graph.py
  - wsgi 핸들러 핵심이 구현되어 있음
  - Query string을 받아들여 그래프를 파일로 저장
  - 이미지가 요청되면 파일을 읽어 응답으로 출력
  ```python
  def application(environ, start_response):
    if environ['PATH_INFO'] == '/graph.png': #사진이 요청되면
      try:
        with open('graph.png', 'rb')as f:
          response_body = f.read()
      except:
        response_body = ''
       start_response('200 OK', [ ])..
       return [response_body] #응답의 형태는 image/png
    else:
  ```
   ![image](https://user-images.githubusercontent.com/73538957/121818948-6a5c7580-ccc5-11eb-8155-922fe0793390.png)

      
3. serve.py 
 - 위 두가지를 이용하여 wsgi 핸들러 몸체를 구현
 
 ```python
 httpd = make_server('', 8051, application)
 httpd.serve_forever() # 계속해서 요청 처리
 ```

### 콘솔 로그 확인
![image](https://user-images.githubusercontent.com/73538957/121819023-e5be2700-ccc5-11eb-9c22-e5552966511f.png)
