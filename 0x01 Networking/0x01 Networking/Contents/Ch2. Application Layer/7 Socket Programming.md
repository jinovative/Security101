[[Application Layer]]

#### **요약 (Summary)**

**Socket Programming(소켓 프로그래밍)**은 네트워크에서 서로 다른 프로세스 간에 데이터를 주고받을 수 있도록 하는 기술이다.  
네트워크 애플리케이션(예: 웹 브라우저, 이메일 클라이언트, 온라인 게임)은 **소켓(Socket)**을 사용하여 다른 컴퓨터의 애플리케이션과 통신한다.  
소켓은 **TCP와 UDP를 기반으로 동작**하며, 클라이언트와 서버 간 통신을 가능하게 한다.

---

## **2.7.1 What is a Socket? (소켓이란?)**

### **설명 (Explanation)**

**Socket(소켓)**은 네트워크에서 **프로세스 간 데이터를 송수신하기 위한 인터페이스**이다.  
운영체제(OS)는 애플리케이션이 네트워크를 통해 데이터를 주고받을 수 있도록 **소켓 API**를 제공한다.

### **소켓의 주요 특징**

- **End-to-End Communication (종단 간 통신) 지원**
- **IP 주소 + Port 번호**를 사용하여 프로세스를 식별
- **TCP와 UDP를 사용하여 신뢰성 및 속도 조절 가능**

##### **💡 Real-Life Example (실생활 예시)**

> **소켓은 우체국의 우편함(Post Box)과 같다.**
> 
> - 송신자는 편지를 **우체국(소켓)에 넣고**
> - 우체국은 주소(IP + Port 번호)에 맞게 전달

---

## **2.7.2 Socket Programming with TCP (TCP 기반 소켓 프로그래밍)**

### **설명 (Explanation)**

TCP(Transmission Control Protocol)는 **신뢰성 있는 데이터 전송을 보장**하며, **connection-oriented(연결 지향)** 방식으로 동작한다.  
TCP 소켓 프로그래밍에서는 **클라이언트와 서버가 연결을 설정한 후 데이터 전송**이 이루어진다.

### **TCP 기반 소켓 프로그래밍 과정**

### **1️⃣ TCP Server (서버) 동작 순서**

1. **Socket 생성** → `socket()`
2. **IP와 Port 바인딩** → `bind()`
3. **클라이언트 요청 대기** → `listen()`
4. **클라이언트 연결 수락** → `accept()`
5. **데이터 송수신** → `recv(), send()`
6. **연결 종료** → `close()`

### **2️⃣ TCP Client (클라이언트) 동작 순서**

1. **Socket 생성** → `socket()`
2. **서버에 연결 요청** → `connect()`
3. **데이터 송수신** → `send(), recv()`
4. **연결 종료** → `close()`

#### **📌 Python TCP Socket Example (TCP 소켓 프로그래밍 예제)**

##### **TCP Server (서버 코드)**

```python
import socket  
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
server_socket.bind(("127.0.0.1", 12345)) server_socket.listen(5)  
print("Waiting for connection...") conn, addr = server_socket.accept() 
print(f"Connected by {addr}")
data = conn.recv(1024)
print(f"Received: {data.decode()}")  
conn.sendall(b"Hello, Client!")
conn.close()
```

##### **TCP Client (클라이언트 코드)**

python

CopyEdit

```python
import socket  
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 
client_socket.connect(("127.0.0.1", 12345))  
client_socket.sendall(b"Hello, Server!") 
data = client_socket.recv(1024) 
print(f"Received: {data.decode()}")  
client_socket.close()
```
##### **💡 Real-Life Example (실생활 예시)**

> **TCP 기반 소켓 프로그래밍은 전화 통화와 유사하다.**
> 
> - 발신자(클라이언트)가 **전화를 걸고(connect)**
> - 상대방(서버)이 **전화를 받으면(accept)** 대화가 시작됨

---

## **2.7.3 Socket Programming with UDP (UDP 기반 소켓 프로그래밍)**

### **설명 (Explanation)**

UDP(User Datagram Protocol)는 **비연결형(connectionless)** 프로토콜로, TCP보다 **빠르지만 신뢰성이 낮다**.  
TCP와 달리 연결 설정 과정 없이 **데이터를 즉시 전송 가능**하지만, 패킷 손실이 발생할 수 있다.

### **UDP 기반 소켓 프로그래밍 과정**

### **1️⃣ UDP Server (서버) 동작 순서**

1. **Socket 생성** → `socket()`
2. **IP와 Port 바인딩** → `bind()`
3. **데이터 수신 대기** → `recvfrom()`
4. **데이터 응답** → `sendto()`

### **2️⃣ UDP Client (클라이언트) 동작 순서**

1. **Socket 생성** → `socket()`
2. **데이터 전송** → `sendto()`
3. **서버 응답 수신** → `recvfrom()`

#### **📌 Python UDP Socket Example (UDP 소켓 프로그래밍 예제)**

##### **UDP Server (서버 코드)**

python

CopyEdit
```python
import socket  
server_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM) 
server_socket.bind(("127.0.0.1", 12345))  
print("Waiting for message...") data, addr = server_socket.recvfrom(1024) 
print(f"Received from {addr}: {data.decode()}")  
server_socket.sendto(b"Hello, UDP Client!", addr)
```


##### **UDP Client (클라이언트 코드)**
```python 
import socket  
client_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM) 
client_socket.sendto(b"Hello, UDP Server!", ("127.0.0.1", 12345))  
data, addr = client_socket.recvfrom(1024) 
print(f"Received: {data.decode()}")  
client_socket.close()
```


##### **💡 Real-Life Example (실생활 예시)**

> **UDP 기반 소켓 프로그래밍은 엽서(Postcard) 보내기와 유사하다.**
> 
> - TCP처럼 상대방의 응답을 기다리지 않고, **빠르게 데이터 전송 가능**
> - 하지만 도착 여부를 **확인할 방법이 없음** (신뢰성 부족)

---

## **2.7.4 TCP vs. UDP (TCP와 UDP의 차이점)**

|특징|TCP (Transmission Control Protocol)|UDP (User Datagram Protocol)|
|---|---|---|
|**연결 방식**|연결 지향(Connection-Oriented)|비연결형(Connectionless)|
|**데이터 전달 보장**|신뢰성 있음 (패킷 손실 시 재전송)|신뢰성 없음 (패킷 손실 가능)|
|**전송 속도**|느림|빠름|
|**사용 예시**|웹, 이메일, 파일 전송|스트리밍, VoIP, 온라인 게임|

##### **💡 Real-Life Example (실생활 예시)**

> - **TCP**는 **등기우편(Registered Mail)**과 같다.
> - **UDP**는 **일반 엽서(Postcard)**와 같다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **소켓(Socket)이란?**
    
    - 네트워크에서 프로세스 간 데이터를 송수신하는 인터페이스.
2. **TCP 소켓 프로그래밍**
    
    - **신뢰성이 필요할 때** 사용 (웹 브라우징, 이메일, 파일 전송).
    - `socket() → bind() → listen() → accept() → recv() → send() → close()`.
3. **UDP 소켓 프로그래밍**
    
    - **빠른 데이터 전송이 필요할 때** 사용 (VoIP, 온라인 게임, 스트리밍).
    - `socket() → bind() → recvfrom() → sendto()`.

🚀 **한 문장 요약:**  
소켓 프로그래밍은 **TCP(신뢰성)와 UDP(속도)를 기반으로 네트워크 애플리케이션이 데이터를 송수신할 수 있도록 하는 기술**이다.