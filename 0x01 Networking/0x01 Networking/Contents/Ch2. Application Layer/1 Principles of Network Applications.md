[[Application Layer]]

#### **요약 (Summary)**

네트워크 애플리케이션(Network Applications)은 **end systems(종단 시스템, 클라이언트 & 서버)** 간의 통신을 통해 동작하며, 특정 **application architecture(애플리케이션 아키텍처)** 와 **protocols(프로토콜)** 을 기반으로 한다.  
네트워크 애플리케이션을 설계할 때는 **client-server model(클라이언트-서버 모델)**과 **peer-to-peer (P2P) model(피어투피어 모델)**이 주요 아키텍처로 사용된다.

---

## **2.1.1 Network Application Architectures (네트워크 애플리케이션 아키텍처)**

### **설명 (Explanation)**

네트워크 애플리케이션은 **application architecture(애플리케이션 아키텍처)**에 따라 데이터를 송수신하는 방식이 다르다.  
대표적인 아키텍처로 **Client-Server Model(클라이언트-서버 모델)**과 **Peer-to-Peer Model(P2P 모델)**이 있다.

### **1️⃣ Client-Server Model (클라이언트-서버 모델)**

- **Server(서버)**는 항상 실행되며 **클라이언트의 요청을 처리**
- **Client(클라이언트)**는 필요할 때만 서버에 요청을 보냄
- 서버는 **data center(데이터 센터)**에 위치하며, 일반적으로 **scalability(확장성) 문제**가 있음
- **예시:** 웹 서비스(HTTP), 이메일(SMTP), 온라인 게임

##### **💡 Real-Life Example (실생활 예시)**

> 클라이언트-서버 모델은 **식당에서 주문하는 시스템**과 같다.
> 
> - 고객(클라이언트)이 주문을 하면,
> - 요리사(서버)가 주문을 받아 음식을 준비한 후 제공한다.
> - 고객이 없을 때도 요리사는 계속 대기(서버는 항상 실행됨).

---

### **2️⃣ Peer-to-Peer (P2P) Model (피어투피어 모델)**

- 클라이언트와 서버 구분 없이 **모든 노드(peer)가 동등한 역할**을 수행
- **Self-scalability(자체 확장성)**: 사용자가 많아질수록 성능이 증가함
- **예시:** 토렌트(BitTorrent), Skype, 블록체인(Bitcoin)

##### **💡 Real-Life Example (실생활 예시)**

> P2P 모델은 **친구들 간의 파일 공유**와 같다.
> 
> - 모든 친구가 **서로 파일을 공유하고 다운로드할 수 있음** (서버 없이 직접 연결)
> - 사용자가 많아질수록 공유 속도도 빨라짐.

---

## **2.1.2 Processes Communicating (프로세스 간 통신)**

### **설명 (Explanation)**

네트워크에서 애플리케이션은 **process-to-process communication(프로세스 간 통신)**을 통해 데이터를 주고받는다.

- **Process(프로세스):** 실행 중인 프로그램
- **Host(호스트):** 프로세스가 실행되는 물리적 또는 가상 머신
- **Socket(소켓):** 네트워크에서 프로세스가 데이터를 송수신하는 인터페이스

#### **Client & Server의 통신 방식**

- **Client Process:** 서버에 요청을 보내는 프로세스
- **Server Process:** 클라이언트 요청을 수락하고 응답하는 프로세스
- **Socket API:** OS가 제공하는 소켓 인터페이스를 통해 통신 (예: `send()`, `recv()`)

##### **💡 Real-Life Example (실생활 예시)**

> 소켓은 **우체국의 우편함(Post Box)과 같다.**
> 
> - 사용자가(프로세스) 편지를 쓰면(데이터 생성)
> - 우체국의 우편함(소켓)에 넣고
> - 상대방이 우체국을 통해 편지를 받음.

---

## **2.1.3 Addressing Processes (프로세스 주소 지정)**

### **설명 (Explanation)**

프로세스 간 통신을 위해서는 **주소(Addressing)**가 필요하다.  
네트워크에서 프로세스를 구별하는 두 가지 요소는 다음과 같다.

1. **IP Address (IP 주소)**
    - 호스트(컴퓨터)를 구별하는 고유한 네트워크 주소
    - 예: `192.168.1.1`
2. **Port Number (포트 번호)**
    - 같은 호스트 내 여러 프로세스를 구별하는 숫자
    - 예: 웹 서버(HTTP)는 **포트 80**, 이메일(SMTP)은 **포트 25** 사용

##### **💡 Real-Life Example (실생활 예시)**

> IP 주소는 **아파트 주소**와 같고, 포트 번호는 **집 호실 번호**와 같다.
> 
> - `192.168.1.1:80` → 아파트 192.168.1.1, 80호(웹 서버)

---

## **2.1.4 Transport Services Available to Applications (애플리케이션을 위한 전송 서비스)**

### **설명 (Explanation)**

애플리케이션이 네트워크에서 데이터를 주고받을 때, **Transport Layer(전송 계층)**의 서비스를 이용한다.  
전송 계층에서 제공하는 두 가지 주요 프로토콜은 **TCP와 UDP**이다.

### **1️⃣ TCP (Transmission Control Protocol)**

- **Reliable Data Transfer (신뢰성 있는 데이터 전송)**
- **Flow Control (흐름 제어)**
- **Congestion Control (혼잡 제어)**
- **Connection-oriented (연결 지향)**
- **예시:** 웹(HTTP), 이메일(SMTP), 파일 전송(FTP)

### **2️⃣ UDP (User Datagram Protocol)**

- **No Reliability (신뢰성 없음)**
- **No Flow Control (흐름 제어 없음)**
- **No Congestion Control (혼잡 제어 없음)**
- **Connectionless (비연결형)**
- **예시:** 온라인 게임, VoIP, 스트리밍

##### **💡 Real-Life Example (실생활 예시)**

> **TCP는 등기우편(Registered Mail)**과 같고, **UDP는 엽서(Postcard)**와 같다.
> 
> - TCP: **우편물이 정확하게 도착했는지 확인 가능** (신뢰성 보장)
> - UDP: **빠르게 보내지만 도착 여부를 알 수 없음** (신뢰성 없음)

---

## **2.1.5 The Web and HTTP (웹과 HTTP 개요)**

### **설명 (Explanation)**

웹 애플리케이션의 대표적인 프로토콜은 **HTTP(HyperText Transfer Protocol)**이다.

- **Client-Server 모델 사용**
- **Stateless (상태를 저장하지 않음)**
- **TCP 기반**
- **Request-Response 방식**
- **예시:** 웹 브라우저가 서버에서 HTML, 이미지, 동영상을 요청하는 방식

##### **💡 Real-Life Example (실생활 예시)**

> HTTP는 **식당에서 음식 주문하는 방식**과 같다.
> 
> - 고객(클라이언트)이 메뉴(웹 페이지)를 요청하면,
> - 서버(주방)가 음식을 준비한 후 제공하는 방식.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **네트워크 애플리케이션 아키텍처**
    
    - **Client-Server Model:** 서버가 항상 실행되며 클라이언트 요청을 처리
    - **P2P Model:** 클라이언트와 서버 구분 없이 동등한 역할 수행
2. **프로세스 간 통신**
    
    - 네트워크 애플리케이션은 **Socket(소켓)**을 통해 통신
    - **IP 주소 + Port 번호**로 특정 프로세스를 식별
3. **전송 계층 프로토콜**
    
    - **TCP:** 신뢰성 있는 데이터 전송 (HTTP, Email, FTP)
    - **UDP:** 빠르지만 신뢰성이 없는 전송 (VoIP, Streaming, Online Games)

🚀 **한 문장 요약:**  
네트워크 애플리케이션은 **Client-Server 모델 & P2P 모델**을 기반으로 동작하며, **TCP & UDP**를 이용해 데이터를 송수신한다.

