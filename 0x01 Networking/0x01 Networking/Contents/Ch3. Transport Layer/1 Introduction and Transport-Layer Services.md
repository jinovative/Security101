[[Transport Layer]]

#### **요약 (Summary)**

**Transport Layer(전송 계층)** 은 **end-to-end communication(종단 간 통신)** 을 담당하며, 애플리케이션 계층(Application Layer)과 네트워크 계층(Network Layer) 사이에서 데이터를 전송한다.  
주요 프로토콜로 **TCP(Transmission Control Protocol)와 UDP(User Datagram Protocol)** 가 있으며, 각각 **신뢰성(reliable) vs. 속도(speed)** 중심의 특징을 가진다.  
전송 계층은 **Multiplexing(다중화) 및 Demultiplexing(역다중화)**, **Reliable Data Transfer(신뢰성 있는 데이터 전송)**, **Flow Control(흐름 제어)**, **Congestion Control(혼잡 제어)** 등의 서비스를 제공한다.

---

## **3.1.1 The Transport Layer in the Internet (인터넷에서의 전송 계층 역할)**

### **설명 (Explanation)**

전송 계층은 **end systems(종단 시스템)** 간의 데이터 교환을 관리하며, 애플리케이션이 네트워크 계층의 복잡성을 신경 쓰지 않고 데이터를 주고받을 수 있도록 한다.

### **1️⃣ Transport vs. Network Layer (전송 계층 vs. 네트워크 계층 차이점)**

|계층|역할|
|---|---|
|**Network Layer (네트워크 계층)**|**Host-to-Host** 데이터 전송 (IP 주소 기반)|
|**Transport Layer (전송 계층)**|**Process-to-Process** 데이터 전송 (Port 번호 기반)|

- 네트워크 계층이 **IP 주소 기반**으로 패킷을 전달한다면,
- 전송 계층은 **포트 번호(Port Number)** 를 이용하여 **특정 애플리케이션 프로세스로 데이터 전달** 을 보장한다.

##### **💡 Real-Life Example (실생활 예시)**

> **네트워크 계층은 택배 회사 전체 시스템**과 같고,  
> **전송 계층은 특정 집의 특정 사람(애플리케이션)에게 택배를 전달하는 과정**과 같다.

---

## **3.1.2 Transport-Layer Services (전송 계층 서비스)**

### **설명 (Explanation)**

전송 계층은 **애플리케이션이 데이터를 쉽게 주고받을 수 있도록 다양한 기능을 제공**한다.

### **1️⃣ Multiplexing & Demultiplexing (다중화 및 역다중화)**

- **Multiplexing (다중화)**: 여러 애플리케이션의 데이터를 하나의 네트워크 연결로 결합하여 전송
- **Demultiplexing (역다중화)**: 수신된 데이터를 올바른 애플리케이션에 전달

##### **💡 Real-Life Example (실생활 예시)**

> Multiplexing은 **여러 사람이 한 버스를 타는 것**과 같고,  
> Demultiplexing은 **각 사람이 목적지에서 내리는 과정**과 같다.

---

### **2️⃣ Reliable Data Transfer (신뢰성 있는 데이터 전송, RDT)**

- **TCP는 신뢰성 있는 데이터 전송 제공** (데이터 손실 시 재전송)
- **UDP는 신뢰성을 보장하지 않음**

##### **💡 Real-Life Example (실생활 예시)**

> - TCP는 **등기 우편(Registered Mail)**처럼 도착을 보장.
> - UDP는 **엽서(Postcard)**처럼 도착 여부를 알 수 없음.

---

### **3️⃣ Flow Control (흐름 제어)**

- 송신자가 **수신자의 처리 속도를 초과하지 않도록 조절**
- **TCP에서 지원**, UDP는 지원하지 않음

##### **💡 Real-Life Example (실생활 예시)**

> 흐름 제어는 **식당에서 요리를 천천히 제공하여 손님이 음식을 다 먹을 시간을 주는 것**과 같다.

---

### **4️⃣ Congestion Control (혼잡 제어)**

- 네트워크가 **과부하 상태가 되지 않도록 조절**
- **TCP에서 제공**하지만, **UDP는 제공하지 않음**

##### **💡 Real-Life Example (실생활 예시)**

> 혼잡 제어는 **고속도로에서 차량이 너무 많아지면 속도를 제한하는 것**과 같다.

---

## **3.1.3 Transport-Layer Protocols (전송 계층 프로토콜)**

### **설명 (Explanation)**

인터넷에서 가장 중요한 두 가지 전송 계층 프로토콜은 **TCP(Transmission Control Protocol)**와 **UDP(User Datagram Protocol)**이다.

### **1️⃣ TCP (Transmission Control Protocol)**

- **Connection-oriented (연결 지향)**
    - 데이터를 전송하기 전에 **3-way handshake(3방향 핸드셰이크)**를 통해 연결을 설정.
- **Reliable data transfer (신뢰성 있는 데이터 전송)**
    - 손실된 패킷을 **재전송(retransmission)**하여 보장.
- **Flow control & Congestion control (흐름 제어 및 혼잡 제어)**
- **예시:** 웹 브라우징(HTTP), 이메일(SMTP), 파일 전송(FTP)

##### **💡 Real-Life Example (실생활 예시)**

> TCP는 **전화 통화**와 같다.
> 
> - 먼저 상대방과 연결을 맺고(3-way handshake),
> - 통화 중 음성이 깨지면 다시 말해주듯 데이터가 재전송됨.

---

### **2️⃣ UDP (User Datagram Protocol)**

- **Connectionless (비연결형)**
    - 연결 설정 없이 데이터를 바로 전송.
- **No reliability (신뢰성 없음)**
    - 손실된 패킷을 재전송하지 않음.
- **No flow control & No congestion control**
- **예시:** 실시간 스트리밍(Netflix, YouTube), 온라인 게임, VoIP(Skype, Zoom)

##### **💡 Real-Life Example (실생활 예시)**

> UDP는 **라디오 방송**과 같다.
> 
> - 방송이 끊기면 다시 되돌릴 수 없지만, 실시간으로 빠르게 전달됨.

---

## **3.1.4 TCP vs. UDP Comparison (TCP vs. UDP 비교)**

|특징|**TCP**|**UDP**|
|---|---|---|
|**연결 방식**|Connection-oriented (연결형)|Connectionless (비연결형)|
|**데이터 전송 보장**|Reliable (신뢰성 보장)|No reliability (신뢰성 없음)|
|**패킷 손실 처리**|재전송 지원|재전송 없음|
|**흐름 제어**|지원 (Flow Control)|지원 안 함|
|**혼잡 제어**|지원 (Congestion Control)|지원 안 함|
|**속도**|느림|빠름|
|**사용 예시**|HTTP(웹), SMTP(이메일), FTP(파일 전송)|VoIP(음성 통화), 게임, 스트리밍|

##### **💡 Real-Life Example (실생활 예시)**

> - **TCP**는 **등기우편(Registered Mail)**
> - **UDP**는 **엽서(Postcard)**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Transport Layer(전송 계층)**은 **end-to-end communication(종단 간 통신)을 담당**하며, 애플리케이션 간 데이터를 주고받는 역할을 한다.
2. **Multiplexing & Demultiplexing (다중화 및 역다중화)**을 통해 여러 애플리케이션이 동일한 네트워크를 사용할 수 있도록 한다.
3. **TCP vs. UDP 비교**
    - **TCP:** 신뢰성 보장, 연결 지향, 흐름 제어 & 혼잡 제어 지원 (예: HTTP, 이메일).
    - **UDP:** 빠른 데이터 전송, 비연결형, 신뢰성 없음 (예: VoIP, 스트리밍, 게임).

🚀 **한 문장 요약:**  
전송 계층은 **애플리케이션 간 데이터 교환을 담당하며**, **TCP(신뢰성 보장) & UDP(빠른 전송)**을 통해 네트워크 통신을 최적화한다.