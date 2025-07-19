[[The Link Layer and LANs]]


#### **요약 (Summary)**

**Link Layer(링크 계층)** 는 **같은 네트워크(물리적으로 연결된 장치) 내에서 프레임(Frame) 단위로 데이터를 전송하는 역할** 을 한다.  
네트워크 계층(Network Layer)의 IP 패킷을 받아 **프레임으로 캡슐화(Encapsulation)한 후, 물리적인 링크를 통해 전달**한다.  
링크 계층에서 사용하는 주요 기술로는 **Ethernet, Wi-Fi, PPP(Point-to-Point Protocol)** 등이 있으며,  
각 장치는 **MAC Address(물리적 주소, Media Access Control Address)를 사용하여 식별**된다.

---

## **6.1.1 The Role of the Link Layer (링크 계층의 역할)**

### **설명 (Explanation)**

링크 계층은 **네트워크에서 물리적으로 연결된 장치들 간 데이터를 신뢰성 있게 전달하는 역할**을 한다.  
이는 네트워크 계층(Network Layer)의 패킷을 받아 **Frame(프레임)으로 변환하여 물리 계층(Physical Layer)로 전달**하는 과정이다.

### **1️⃣ 주요 기능 (Key Functions of the Link Layer)**

| 기능                                            | 설명                                                       |
| --------------------------------------------- | -------------------------------------------------------- |
| **Framing (프레임화)**                            | 네트워크 계층의 패킷을 프레임으로 캡슐화                                   |
| **MAC Addressing (MAC 주소 지정)**                | 장치를 식별하기 위한 **고유한 48-bit MAC 주소 사용**                     |
| **Error Detection & Correction (오류 감지 및 수정)** | **CRC(Cyclic Redundancy Check)와 같은 오류 검출 기술 사용**         |
| **Flow Control (흐름 제어)**                      | 송신자와 수신자의 속도 조절                                          |
| **Medium Access Control (매체 접근 제어)**          | CSMA/CD, CSMA/CA 같은 기술을 사용하여 여러 장치가 하나의 링크를 공유할 수 있도록 조정 |

##### **💡 Real-Life Example (실생활 예시)**

> **링크 계층은 우체국의 소포 시스템과 유사하다.**
> 
> - 주소(MAC Address)를 기반으로 정확한 목적지로 전달.
> - 소포(프레임) 내부에는 편지(IP 패킷)가 들어 있음.
> - 우체국(네트워크 장치)이 오류 검출 및 흐름 제어를 수행하여 안전한 배달을 보장.

---

## **6.1.2 Where is the Link Layer Implemented? (링크 계층은 어디에서 구현되는가?)**

### **설명 (Explanation)**

링크 계층은 네트워크 장치에서 **하드웨어 및 소프트웨어를 통해 구현**되며, 일반적으로 **Network Interface Card(NIC, 네트워크 인터페이스 카드)** 에서 동작한다. 

### **1️⃣ 링크 계층이 동작하는 위치**

|네트워크 장치|역할|
|---|---|
|**Network Interface Card (NIC, 네트워크 카드)**|MAC 주소 저장 및 링크 계층 프로토콜 처리|
|**Switch (스위치)**|MAC 주소를 기반으로 프레임을 전달 (Layer 2)|
|**Router (라우터)**|네트워크 계층에서 작동하지만, 인터페이스마다 링크 계층 사용|

##### **💡 Real-Life Example (실생활 예시)**

> **NIC는 우편 배달원의 주소록과 같다.**
> 
> - 각 장치의 MAC 주소를 기반으로 정확한 목적지로 데이터 전달.

---

## **6.1.3 Link Layer Services (링크 계층의 주요 서비스)**

### **설명 (Explanation)**

링크 계층은 데이터를 안정적으로 전달하기 위해 여러 가지 서비스를 제공한다.

### **1️⃣ 주요 서비스 (Key Services of the Link Layer)**

|서비스|설명|
|---|---|
|**Framing (프레임화)**|패킷을 프레임 단위로 나누고 헤더 및 트레일러 추가|
|**Reliable Delivery (신뢰성 있는 전송)**|일부 프로토콜(예: PPP)이 데이터 재전송 기능을 제공|
|**Error Detection (오류 검출)**|CRC(Cyclic Redundancy Check)와 같은 기법 사용|
|**Half-Duplex & Full-Duplex (반이중 & 전이중 통신)**|데이터가 한 방향 또는 양방향으로 동시에 전송 가능|

##### **💡 Real-Life Example (실생활 예시)**

> - **Framing = 문장을 시작과 끝을 표시하는 마침표와 유사함.**
> - **Error Detection = 이메일 전송 후 스팸 필터가 오류를 감지하는 과정과 유사함.**

---

## **6.1.4 Link Layer Addressing: MAC Addresses (링크 계층 주소 지정 – MAC 주소)**

### **설명 (Explanation)**

링크 계층에서는 **MAC Address(물리적 주소)**를 사용하여 장치를 식별한다.

### **1️⃣ MAC Address의 특징**

- **48-bit 주소 (6 옥텟, 예: `00:1A:2B:3C:4D:5E`)**
- **네트워크 카드(NIC)에 고유하게 할당됨 (변경 가능)**
- **ARP(Address Resolution Protocol)를 통해 IP 주소와 MAC 주소를 매핑**

📌 **예제: MAC 주소 표기법**


`00:1A:2B:3C:4D:5E`

##### **💡 Real-Life Example (실생활 예시)**

> **MAC 주소는 자동차의 번호판과 유사하다.**
> 
> - 네트워크에서 **각 장치를 식별하는 고유한 식별자** 역할 수행.

---

## **6.1.5 Error Detection and Correction (오류 검출 및 수정)**

### **설명 (Explanation)**

링크 계층은 데이터 전송 중 발생할 수 있는 오류를 검출하고, 필요할 경우 수정할 수 있는 기능을 제공한다.

### **1️⃣ 주요 오류 검출 기법**

|기법|설명|
|---|---|
|**Parity Check (패리티 체크)**|한 비트를 추가하여 데이터 오류를 감지|
|**Checksum (체크섬)**|데이터 블록의 값을 더하여 오류 검출|
|**CRC (Cyclic Redundancy Check, 순환 중복 검사)**|다항식을 이용해 높은 정확도로 오류 검출 가능|

📌 **예제: CRC 사용 방식**

1. 송신자가 데이터와 함께 CRC 값을 생성하여 전송.
2. 수신자가 수신된 데이터에서 CRC 값을 확인하여 오류가 있는지 판별.

##### **💡 Real-Life Example (실생활 예시)**

> **CRC는 신용카드 번호의 검증 방식과 유사하다.**
> 
> - 입력한 카드 번호가 올바른지 확인하기 위해 마지막 몇 자리 숫자로 오류 검출 수행.

---

## **6.1.6 Multiple Access Protocols (매체 접근 제어 프로토콜)**

### **설명 (Explanation)**

네트워크에서 여러 장치가 동시에 통신하려면 **누가 언제 데이터를 전송할지 조정하는 프로토콜(Medium Access Control, MAC Protocols)**이 필요하다.

### **1️⃣ 주요 매체 접근 제어 방식**

|방식|설명|예제|
|---|---|---|
|**Channel Partitioning (채널 분할 방식)**|대역폭을 나누어 사용|TDMA, FDMA|
|**Random Access (경쟁 방식)**|충돌 가능, 필요할 때만 전송|CSMA/CD (Ethernet), CSMA/CA (Wi-Fi)|
|**Taking Turns (순차적 접근 방식)**|정해진 순서대로 데이터 전송|Polling, Token Ring|

📌 **Ethernet과 Wi-Fi에서 사용하는 방식**

- **Ethernet → CSMA/CD (충돌 감지 후 재전송)**
- **Wi-Fi → CSMA/CA (충돌 회피 기법 사용)**

##### **💡 Real-Life Example (실생활 예시)**

> - **Channel Partitioning = 여러 개의 고속도로 차선을 나누어 차량이 달리는 것**
> - **Random Access = 출근길 교차로에서 차량이 서로 양보하며 지나가는 것**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **링크 계층(Link Layer)은 같은 네트워크 내에서 데이터 프레임을 전송하는 역할을 한다.**
2. **MAC Address를 사용하여 장치를 식별하며, 오류 검출(CRC) 및 매체 접근 제어(MAC Protocols) 기능을 제공한다.**
3. **Ethernet은 CSMA/CD, Wi-Fi는 CSMA/CA 방식을 사용하여 충돌을 방지하고 데이터를 전송한다.**

🚀 **한 문장 요약:**  
**링크 계층은 프레임을 전송하고 MAC 주소를 사용하여 장치를 식별하며, Ethernet과 Wi-Fi 같은 네트워크 기술에서 충돌을 방지하는 매체 접근 제어 프로토콜을 제공한다.**