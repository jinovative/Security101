[[Transport Layer]]

#### **요약 (Summary)**

**UDP(User Datagram Protocol)**는 **connectionless(비연결형)** 프로토콜로, **빠른 전송 속도와 낮은 오버헤드**를 제공하지만, **신뢰성을 보장하지 않는 특징**을 가진다.  
즉, **데이터그램(datagram)** 단위로 패킷을 전송하며, **패킷 손실, 순서 변경, 중복 발생 가능성**이 있다.  
UDP는 **DNS, VoIP, 온라인 게임, 스트리밍 서비스**와 같이 빠른 데이터 전송이 필요한 애플리케이션에서 사용된다.

---

## **3.3.1 UDP Overview (UDP 개요 및 특징)**

### **설명 (Explanation)**

UDP는 **connectionless(비연결형) & lightweight(가벼운)** 프로토콜로,  
TCP와 달리 **데이터 전송 전에 연결을 설정하지 않으며**, **신뢰성(reliability)을 보장하지 않는다.**

### **UDP의 주요 특징**

| 특징                                   | 설명                                |
| ------------------------------------ | --------------------------------- |
| **Connectionless (비연결형)**            | 데이터를 전송하기 전에 **연결 설정 없이 즉시 전송**   |
| **No Reliability (신뢰성 없음)**          | 패킷 손실 시 재전송 없음 (손실, 중복, 순서 변경 가능) |
| **No Flow Control (흐름 제어 없음)**       | 송신자가 무제한으로 데이터를 보낼 수 있음           |
| **No Congestion Control (혼잡 제어 없음)** | 네트워크 혼잡과 관계없이 패킷을 전송              |
| **Low Overhead (낮은 오버헤드)**           | TCP보다 헤더 크기가 작아 **빠른 전송 가능**      |

##### **💡 Real-Life Example (실생활 예시)**

> **UDP는 "엽서(Postcard) 보내기"와 같다.**
> 
> - 빠르게 보낼 수 있지만, **도착 여부를 확인할 방법 없음**.
> - 엽서가 손실되거나 순서가 바뀌어 도착할 수도 있음.

---

## **3.3.2 UDP Segment Structure (UDP 세그먼트 구조)**

### **설명 (Explanation)**

UDP는 **데이터를 전송할 때 최소한의 헤더만 추가**하며,  
TCP보다 **헤더 크기가 작아 전송 속도가 빠르다**.

### **UDP 헤더 구조 (8 Bytes)**

|필드|크기 (Bytes)|설명|
|---|---|---|
|**Source Port (출발지 포트)**|2|송신 애플리케이션 식별|
|**Destination Port (목적지 포트)**|2|수신 애플리케이션 식별|
|**Length (길이)**|2|UDP 헤더 + 데이터 크기|
|**Checksum (체크섬)**|2|데이터 오류 검출|

##### **💡 Real-Life Example (실생활 예시)**

> **UDP 헤더는 최소한의 정보만 포함하여 빠르게 전달되는 "간단한 배송 전표"와 같다.**
> 
> - TCP는 복잡한 배송 시스템(등기), UDP는 빠른 일반 우편과 비슷함.

---

## **3.3.3 UDP Checksum (UDP 오류 검출: 체크섬)**

### **설명 (Explanation)**

UDP는 기본적으로 신뢰성을 보장하지 않지만, 데이터 손상을 방지하기 위해 **checksum(체크섬) 오류 검출 기능**을 제공한다.

### **Checksum 동작 방식**

1. **송신 측**:
    
    - UDP 세그먼트의 모든 16-bit 값을 더한 후, **1의 보수 연산(One's Complement)** 수행.
    - 결과를 **Checksum 필드**에 저장.
2. **수신 측**:
    
    - 수신한 데이터의 체크섬을 계산하여 **0이 되면 정상 수신**,
    - **0이 아니면 오류 발생 → 데이터 폐기**.

##### **💡 Real-Life Example (실생활 예시)**

> **체크섬은 "상품 배달 시 제품이 손상되지 않았는지 확인하는 과정"과 같다.**
> 
> - 배달된 제품(데이터)의 포장 상태(체크섬)를 확인하여, 손상이 있으면 반품(데이터 폐기).

---

## **3.3.4 UDP vs. TCP (UDP와 TCP 비교)**

### **설명 (Explanation)**

UDP와 TCP는 각각 **특정 애플리케이션 요구 사항**에 따라 사용된다.  
TCP는 **신뢰성이 중요한 경우** 사용되며, UDP는 **빠른 전송이 필요한 경우** 사용된다.

|**기능**|**UDP (User Datagram Protocol)**|**TCP (Transmission Control Protocol)**|
|---|---|---|
|**연결 설정 (Connection Setup)**|없음 (Connectionless)|있음 (Connection-Oriented)|
|**데이터 신뢰성 (Reliability)**|없음 (데이터 손실 가능)|있음 (손실 시 재전송)|
|**데이터 흐름 제어 (Flow Control)**|없음|있음|
|**혼잡 제어 (Congestion Control)**|없음|있음|
|**전송 속도 (Speed)**|빠름|느림|
|**사용 예시 (Use Cases)**|DNS, VoIP, 온라인 게임, 스트리밍|HTTP, 이메일, 파일 전송|

##### **💡 Real-Life Example (실생활 예시)**

> - **TCP = 등기우편(Registered Mail)** → 도착 확인 가능, 신뢰성 높음.
> - **UDP = 엽서(Postcard)** → 빠르지만 도착 여부를 보장하지 않음.

---

## **3.3.5 When to Use UDP? (UDP 사용 사례)**

### **설명 (Explanation)**

UDP는 **빠른 데이터 전송이 중요한 경우**에 사용된다.

### **1️⃣ DNS (Domain Name System) – 도메인 네임 서비스**

- 사용자가 `www.google.com`을 입력하면,
- DNS 서버가 **UDP 패킷(포트 53)을 사용하여 IP 주소를 반환**.
- **빠른 응답이 필요하므로 UDP 사용**.

### **2️⃣ VoIP (Voice over IP) – 인터넷 전화**

- 실시간 음성 통신(예: Zoom, Skype).
- 패킷 손실이 발생해도 **빠른 음성 전송이 더 중요함** → UDP 사용.

### **3️⃣ Online Gaming (온라인 게임)**

- 게임 플레이 중 데이터 손실이 발생해도,
- **속도가 중요하므로 TCP 대신 UDP 사용**.
- 예: FPS, MOBA, MMORPG 게임.

### **4️⃣ Live Streaming (라이브 스트리밍)**

- Netflix, YouTube Live, Twitch 같은 실시간 영상 전송.
- 지연(latency)이 낮아야 하므로 UDP 사용.

##### **💡 Real-Life Example (실생활 예시)**

> - **DNS 요청**은 **패스트푸드점에서 메뉴를 빨리 확인하는 것과 같다.**
> - **VoIP 통화**는 **전화 통화 중 한두 마디가 끊겨도 대화가 계속되는 것과 같다.**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **UDP(User Datagram Protocol)는 Connectionless(비연결형)이며, 빠른 전송 속도를 제공하지만 신뢰성을 보장하지 않는다.**
2. **UDP 헤더는 TCP보다 작으며, Checksum(체크섬) 필드를 이용해 데이터 오류를 검출할 수 있다.**
3. **TCP vs. UDP 비교**
    - **TCP:** 신뢰성 보장, 연결형, 데이터 재전송 가능 (예: HTTP, 이메일).
    - **UDP:** 빠른 전송, 비연결형, 신뢰성 없음 (예: DNS, VoIP, 온라인 게임).
4. **UDP는 실시간성이 중요한 애플리케이션(VoIP, 스트리밍, 게임, DNS)에서 사용된다.**

🚀 **한 문장 요약:**  
UDP는 **빠른 데이터 전송을 위해 신뢰성을 희생하는 비연결형 프로토콜**이며, **VoIP, 게임, 스트리밍 같은 실시간 애플리케이션**에서 사용된다.