[[Transport Layer]]

#### **요약 (Summary)**

**TCP(Transmission Control Protocol)**는 **connection-oriented(연결 지향)** 프로토콜로, **신뢰성 있는(end-to-end reliable) 데이터 전송**을 보장한다.  
TCP는 **handshake(핸드셰이크) 절차**를 통해 **송신자(Sender)와 수신자(Receiver) 간 연결을 설정**하며, 데이터 전송 중 **flow control(흐름 제어), congestion control(혼잡 제어), error detection(오류 검출), retransmission(재전송) 등의 기능**을 제공한다.  
TCP는 웹(HTTP), 이메일(SMTP), 파일 전송(FTP)과 같이 **데이터의 신뢰성이 중요한 애플리케이션**에서 사용된다.

---

## **3.5.1 TCP Overview (TCP 개요 및 특징)**

### **설명 (Explanation)**

TCP는 **연결 지향(Connection-Oriented), 신뢰성 보장(Reliable), 흐름 및 혼잡 제어 제공(Flow & Congestion Control)**이라는 특징을 가진다.

### **1️⃣ TCP의 주요 특징**

|특징|설명|
|---|---|
|**Connection-Oriented (연결 지향형)**|데이터 전송 전에 **3-way handshake**를 통해 연결 설정|
|**Reliable (신뢰성 보장)**|패킷 손실 시 **Retransmission(재전송) 및 ACK 확인**|
|**In-Order Delivery (순서 보장)**|패킷이 올바른 순서로 도착하도록 **Sequencing(시퀀스 번호 사용)**|
|**Flow Control (흐름 제어)**|송신자가 **수신자의 처리 속도를 초과하지 않도록 제어**|
|**Congestion Control (혼잡 제어)**|네트워크 혼잡을 감지하여 패킷 전송 속도를 조절|

##### **💡 Real-Life Example (실생활 예시)**

> **TCP는 등기우편(Registered Mail)과 같다.**
> 
> - 보낸 사람이 우체국(송신자)에서 패키지를 보내고,
> - 수신자가 안전하게 받았는지 확인(ACK),
> - 패키지가 손실되면 다시 보내줌(재전송).

---

## **3.5.2 TCP Segment Structure (TCP 세그먼트 구조)**

### **설명 (Explanation)**

TCP는 데이터 전송을 위해 **TCP Segment(세그먼트)**를 사용하며, 헤더(Header)에는 다양한 제어 정보가 포함된다.

### **TCP Header (20~60 Bytes)**

|필드|크기(Bytes)|설명|
|---|---|---|
|**Source Port (출발지 포트)**|2|송신 애플리케이션의 포트 번호|
|**Destination Port (목적지 포트)**|2|수신 애플리케이션의 포트 번호|
|**Sequence Number (시퀀스 번호)**|4|데이터의 순서를 지정|
|**Acknowledgment Number (ACK 번호)**|4|수신자가 기대하는 다음 시퀀스 번호|
|**Header Length**|4 bits|TCP 헤더의 길이|
|**Flags (제어 플래그)**|6 bits|SYN, ACK, FIN 등 TCP 제어 비트|
|**Receive Window (수신 윈도우 크기)**|2|수신자가 처리할 수 있는 데이터 크기|
|**Checksum (체크섬)**|2|데이터 오류 검출|
|**Urgent Pointer**|2|긴급 데이터 표시|

##### **💡 Real-Life Example (실생활 예시)**

> **TCP 헤더는 "택배 운송장"과 같다.**
> 
> - 출발지와 목적지 정보(포트 번호),
> - 데이터 순서(시퀀스 번호),
> - 패킷이 손상되지 않았는지 확인하는 체크섬 포함.

---

## **3.5.3 TCP Connection Establishment (TCP 연결 설정: 3-Way Handshake)**

### **설명 (Explanation)**

TCP는 데이터 전송 전에 **3-Way Handshake(3단계 핸드셰이크)**를 수행하여 **송신자와 수신자가 통신할 준비가 되었는지 확인**한다.

### **3-Way Handshake 과정**

1. **SYN (Synchronization) – 클라이언트 → 서버**
    - 클라이언트가 **SYN 패킷**을 보내 연결 요청 (시퀀스 번호 포함)
2. **SYN-ACK – 서버 → 클라이언트**
    - 서버가 **SYN-ACK 패킷**을 보내 요청 수락 (자신의 시퀀스 번호 포함)
3. **ACK – 클라이언트 → 서버**
    - 클라이언트가 **ACK 패킷**을 보내 연결 확립 완료

##### **💡 Real-Life Example (실생활 예시)**

> **TCP 3-Way Handshake는 전화 통화 과정과 유사하다.**
> 
> - A가 전화를 걸어 "여보세요?" (SYN),
> - B가 "네, 들려요!" (SYN-ACK),
> - A가 "좋아요, 이야기합시다!" (ACK)

---

## **3.5.4 TCP Connection Termination (TCP 연결 해제: 4-Way Handshake)**

### **설명 (Explanation)**

TCP 연결을 종료할 때는 **4-Way Handshake(4단계 핸드셰이크)**를 사용한다.

### **4-Way Handshake 과정**

1. **FIN (클라이언트 → 서버)**: 클라이언트가 종료 요청(FIN)
2. **ACK (서버 → 클라이언트)**: 서버가 FIN 수락(ACK)
3. **FIN (서버 → 클라이언트)**: 서버가 종료 요청(FIN)
4. **ACK (클라이언트 → 서버)**: 클라이언트가 FIN 수락(ACK)

##### **💡 Real-Life Example (실생활 예시)**

> **TCP 4-Way Handshake는 "이별하는 대화"와 같다.**
> 
> - A가 "난 먼저 갈게" (FIN),
> - B가 "알겠어, 조심해" (ACK),
> - B가 "나도 가볼게" (FIN),
> - A가 "응, 안녕!" (ACK)

---

## **3.5.5 TCP Flow Control (TCP 흐름 제어)**

### **설명 (Explanation)**

TCP는 **송신자의 전송 속도를 수신자의 처리 속도에 맞추기 위해 Flow Control(흐름 제어)**을 제공한다.

### **TCP Flow Control 기법**

- **Receive Window (윈도우 크기 조절)**: 수신자가 **처리할 수 있는 데이터 크기를 송신자에게 전달**하여 조절.

##### **💡 Real-Life Example (실생활 예시)**

> **TCP 흐름 제어는 식당에서 음식이 한 번에 너무 많이 나오는 것을 방지하는 것과 같다.**
> 
> - 손님(수신자)이 너무 많은 음식을 주문하면,
> - 주방(송신자)은 일정한 속도로 요리를 제공.

---

## **3.5.6 TCP Congestion Control (TCP 혼잡 제어)**

### **설명 (Explanation)**

네트워크가 혼잡하면 패킷 손실이 발생할 수 있으므로, **TCP는 Congestion Control(혼잡 제어) 기법을 사용하여 네트워크 부하를 줄인다.**

### **TCP Congestion Control 기법**

- **Slow Start**: 처음에는 패킷을 천천히 보내고, 네트워크 상태를 확인하면서 점점 속도를 증가.
- **Congestion Avoidance**: 네트워크가 혼잡해지면 전송 속도를 조절하여 혼잡을 방지.

##### **💡 Real-Life Example (실생활 예시)**

> **TCP 혼잡 제어는 교통량이 많아질 때 고속도로 속도 제한이 걸리는 것과 같다.**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **TCP는 Connection-Oriented(연결 지향) 프로토콜로, 신뢰성 있는 데이터 전송을 보장한다.**
2. **TCP는 3-Way Handshake(연결 설정) 및 4-Way Handshake(연결 종료) 절차를 사용한다.**
3. **TCP는 Flow Control(흐름 제어) 및 Congestion Control(혼잡 제어)을 통해 네트워크 성능을 최적화한다.**

🚀 **한 문장 요약:**  
TCP는 **신뢰성 있는 데이터 전송을 보장하는 연결 지향 프로토콜**이며, **흐름 제어와 혼잡 제어 기능을 제공하여 안정적인 네트워크 통신을 지원한다.**