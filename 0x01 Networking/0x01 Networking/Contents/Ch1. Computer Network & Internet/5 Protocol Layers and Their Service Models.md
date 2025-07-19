[[Computer Networks and the Internet]]

#### **요약 (Summary)**
인터넷은 **protocol stack(프로토콜 스택)**을 기반으로 동작하며, 각 계층(layer)은 특정한 **service model(서비스 모델)**을 제공한다.  
이 계층 구조를 통해 네트워크 통신을 단순화하고, 다양한 기술과 시스템이 서로 호환될 수 있도록 한다.  
인터넷에서는 **5-layer Internet protocol stack**이 사용되며, 이는 **Application, Transport, Network, Link, Physical Layer**로 구성된다.

---

## **1.5.1 Layered Architecture (계층적 아키텍처)**

### **설명 (Explanation)**

**Protocol layering(프로토콜 계층화)**는 네트워크의 복잡성을 줄이고, 각 기능을 모듈화하여 효율적으로 관리할 수 있도록 한다.  
각 계층은 **위층(layer above)**에 서비스를 제공하며, **아래층(layer below)**에서 서비스를 받는다.

### **Protocol Layering의 장점**

1. **Modularity (모듈화)**
    - 특정 계층을 변경해도 다른 계층에 영향을 주지 않음.
2. **Interoperability (상호 운용성)**
    - 서로 다른 장치와 네트워크가 동일한 계층 구조를 사용하면 원활한 통신 가능.
3. **Simplification (복잡성 감소)**
    - 각 계층이 특정 기능만 수행하여 설계와 디버깅이 쉬워짐.

##### **💡 Real-Life Example (실생활 예시)**

> **비행기 여행**을 생각해보자.
> 
> - 공항에서 **티켓을 구입**하고(예약 시스템, Application Layer)
> - **짐을 맡기고**(Baggage Handling, Transport Layer)
> - **탑승 게이트에서 비행기에 탑승하고**(Gate, Network Layer)
> - **비행기를 타고 이동하고**(항공사 운영, Link Layer)
> - **비행기가 활주로를 따라 이동한다**(Physical Layer)
> 
> 각 단계는 독립적으로 운영되며, 전체 시스템의 일부분으로 작동한다.

---

## **1.5.2 Internet Protocol Stack (인터넷 프로토콜 스택)**

### **설명 (Explanation)**

인터넷에서 사용되는 **5-layer Internet protocol stack**은 다음과 같이 구성된다.

|Layer|역할 및 기능|
|---|---|
|**Application Layer**|사용자와 직접 상호 작용하는 계층 (HTTP, SMTP, FTP 등)|
|**Transport Layer**|**end-to-end data transfer** (TCP, UDP)|
|**Network Layer**|패킷을 **source to destination**으로 라우팅 (IP, ICMP)|
|**Link Layer**|**host-to-host** 간 데이터 전송 (Ethernet, Wi-Fi)|
|**Physical Layer**|**bit transmission(비트 전송)**을 담당 (광섬유, 구리선, 무선)|

---

### **1️⃣ Application Layer (애플리케이션 계층)**

- **사용자와 가장 가까운 계층**
- **Network applications(네트워크 애플리케이션)**이 실행되는 곳
- 예시: **HTTP(웹), SMTP(이메일), FTP(파일 전송), DNS(도메인 네임 시스템)**

##### **💡 Real-Life Example (실생활 예시)**

> Application Layer는 **음식 배달 앱**과 같다.  
> 사용자는 앱을 통해 피자를 주문(HTTP 요청)하고, 앱은 이를 처리하여 배달원에게 전달한다.

---

### **2️⃣ Transport Layer (전송 계층)**

- **end-to-end communication(종단 간 데이터 전송)**을 담당
- 두 가지 주요 프로토콜 제공:
    - **TCP (Transmission Control Protocol)**
        - **신뢰성 있는 데이터 전송(reliable data transfer)** 보장
        - **데이터 흐름 제어(flow control), 혼잡 제어(congestion control)** 제공
    - **UDP (User Datagram Protocol)**
        - **빠른 전송(fast transfer)** 가능하지만 신뢰성이 없음
        - 스트리밍 서비스, 온라인 게임 등에 사용됨

##### **💡 Real-Life Example (실생활 예시)**

> TCP는 **우체국 등기 서비스**와 같다.
> 
> - 패킷이 목적지에 도착했는지 확인하며, 손실되면 재전송한다.  
>     UDP는 **엽서 보내기**와 같다.
> - 빠르게 전송되지만, 중간에 잃어버려도 알 수 없다.

---

### **3️⃣ Network Layer (네트워크 계층)**

- 패킷을 **source에서 destination으로 라우팅**
- 주요 프로토콜:
    - **IP (Internet Protocol)**: 네트워크 주소 지정 및 패킷 전달
    - **ICMP (Internet Control Message Protocol)**: 오류 메시지 전송 (ex: ping 명령어)

##### **💡 Real-Life Example (실생활 예시)**

> 네트워크 계층은 **택배 회사의 배송 시스템**과 같다.
> 
> - IP 주소는 집 주소와 같으며, 패킷은 택배 상자와 같다.
> - 라우터는 택배 분류 센터처럼 패킷을 최적 경로로 보내는 역할을 한다.

---

### **4️⃣ Link Layer (링크 계층)**

- 같은 네트워크 내에서 **host-to-host** 간 데이터 전송
- 예시: **Ethernet(이더넷), Wi-Fi(무선), PPP(점대점 프로토콜)**
- 패킷을 **frame(프레임)** 단위로 캡슐화(encapsulation)

##### **💡 Real-Life Example (실생활 예시)**

> Link Layer는 **버스 환승 시스템**과 비슷하다.
> 
> - 사람이 목적지까지 가려면 여러 번 환승해야 할 수도 있다.
> - 마찬가지로, 패킷은 네트워크 경로를 따라 여러 링크를 거쳐 이동한다.

---

### **5️⃣ Physical Layer (물리 계층)**

- **비트(bit)를 전기적 신호 또는 무선 신호로 변환하여 전송**
- 네트워크의 가장 하위 계층이며, 하드웨어 수준에서 동작
- 예시: **광섬유, 구리선, 무선(Wi-Fi, LTE, 5G)**

##### **💡 Real-Life Example (실생활 예시)**

> 물리 계층은 **전화선이나 Wi-Fi 신호**처럼 실제 데이터가 전달되는 매체와 같다.

---

## **1.5.3 Encapsulation (캡슐화)**

### **설명 (Explanation)**

각 계층은 데이터를 **하위 계층으로 전달하면서 헤더(header)를 추가**하는 방식으로 동작한다.  
이 과정을 **Encapsulation(캡슐화)**이라고 하며, 데이터는 각 계층에서 아래로 내려가면서 패킷이 점점 커진다.

- **Application Layer:** 원본 메시지
- **Transport Layer:** **Segment** (TCP/UDP 헤더 추가)
- **Network Layer:** **Datagram** (IP 헤더 추가)
- **Link Layer:** **Frame** (Ethernet/Wi-Fi 헤더 추가)

##### **💡 Real-Life Example (실생활 예시)**

> 캡슐화는 **우체국 소포 포장 과정**과 같다.
> 
> - 상품(Application Layer)을 포장하고(Transport Layer)
> - 주소를 쓰고(Network Layer)
> - 택배 박스에 담아 운송한다(Link Layer).
> - 마지막으로, 택배 트럭이 실제로 운송(Physical Layer)한다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. 인터넷은 **5-layer Internet protocol stack**을 사용하며, 각 계층은 특정 서비스를 제공한다.
2. **Protocol Layering(프로토콜 계층화)**은 네트워크 통신을 단순화하고 효율적으로 관리할 수 있도록 한다.
3. **Encapsulation(캡슐화)**을 통해 데이터는 각 계층을 거치며 헤더를 추가하여 전송된다.

🚀 **한 문장 요약:**  
인터넷은 **5-layer protocol stack**을 사용하여 데이터를 계층적으로 전송하며, **encapsulation**을 통해 패킷을 캡슐화하여 통신을 수행한다.