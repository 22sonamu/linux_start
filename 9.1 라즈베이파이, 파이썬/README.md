### Socket 
- ***네트워크 상에서 통신을 가능하게 해주는 통신 인터페이스***
- IP 주소와 port number로 구성됨


### 클라이언트와 서버
- 서버 : 클라이언트에서 받은 메시지를 다시 클라이언트로 전송 
  - 소켓 생성 -> ip, port 주소 할당 -> 연결 대기 -> 수락 -> 수신(클라이언트에서) -> 송신 (클라언트에) -> 소켓 소멸
- 클라이언트 : 서버로 메세지를 보내고, 서버에서 받은 메시지를 출력
  - 소켓 생성 > 연결 요청 -> 송신(서버에) -> 수신(서버에서) -> 소켓 소멸
  
### 소켓 프로그래밍(서버)
```python 
import socket, sys
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  #소켓 생성
s.bind(('', 8888))

s.listen(1)  #연결 대기
print('Socket Listen Start!')


connector, addr = s.accept() # 수락

while True:
  data = connector.recv(1024)
  if not data : break
  print('Message from Client : ' + data.decode('utf-8')) #수신
  response = data.decode('utf-8')[-1::-1]
  connector.send(response.encode('utf-8')) #송신
s.close() # 소켓 소멸
```
  
  
### 소켓 프로그래밍(클라이언트)

```python
import socket, sys
HOST = '172.30.1.54'; PORT = 8888

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) #소켓 생성

s.connect((HOST, PORT)) #연결요청

while True:
  user_input = raw_input('Message:')
  s.send(user_input.enode('utf-8') #송신
  
  echo = s.recv(1024)
  if not echo : break
  print('Echo from Server L ' + echo.decode('utf-8') #수신
s.close() #소켓 소멸
```


  
