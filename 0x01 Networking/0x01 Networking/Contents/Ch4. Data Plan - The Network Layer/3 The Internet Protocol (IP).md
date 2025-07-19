[[The Network Layer – Data Plane]]


#### **요약 (Summary)**

**IP(Internet Protocol)** 는 **네트워크 계층(Network Layer)의 핵심 프로토콜**로, **패킷(Packet)을 출발지에서 목적지까지 전송**하는 역할을 한다.  
IP는 **Best-Effort Delivery(최선형 서비스)** 를 제공하며, **패킷 손실(Packet Loss), 순서 보장 없음(No Order Guarantee), 신뢰성 없음(Unreliable)** 등의 특징을 가진다.  
현재 가장 많이 사용되는 IP 버전은 **IPv4(32-bit 주소 체계)**이며, IP 주소 부족 문제를 해결하기 위해 **IPv6(128-bit 주소 체계)** 가 도입되었다.

---

## **4.3.1 The Role of IP (IP의 역할)**

### **설명 (Explanation)**

IP는 **네트워크에서 데이터를 목적지까지 전달하는 역할**을 한다.  
IP 프로토콜은 **Connectionless(비연결형), Best-Effort Delivery(최선형 전달), Stateless(무상태)** 방식을 따른다.

### **1️⃣ 주요 기능 (Key Functions of IP)**

| 기능                          | 설명                                                           |
| --------------------------- | ------------------------------------------------------------ |
| **Addressing (주소 지정)**      | **각 장치(Host)와 라우터(Router)에 고유한 IP 주소 할당**                    |
| **Packet Routing (패킷 라우팅)** | 네트워크를 통해 **출발지에서 목적지까지 최적의 경로를 결정**                          |
| **Fragmentation (단편화)**     | 패킷 크기가 MTU(Maximum Transmission Unit)보다 클 경우 **작은 조각으로 분할**  |
| **Error Handling (오류 처리)**  | **ICMP(Internet Control Message Protocol)**을 사용하여 오류 메시지를 전달 |

##### **💡 Real-Life Example (실생활 예시)**

> **IP는 택배 시스템과 같다.**
> 
> - IP 주소 = 집 주소 (패킷의 목적지)
> - Routing = 택배가 물류센터를 거쳐 최적의 경로로 배송되는 과정
> - Fragmentation = 큰 물건을 작은 상자로 나누어 배송하는 것

---

## **4.3.2 IP Datagram Structure (IP 데이터그램 구조)**

### **설명 (Explanation)**

IP에서 데이터는 **Datagram(데이터그램)**이라는 단위로 전송된다.  
IP 데이터그램은 **Header(헤더) + Payload(데이터)**로 구성된다.

### **1️⃣ IPv4 Header (IPv4 헤더 구조, 20~60 Bytes)**

| 필드                         | 크기(Bytes) | 설명                         |
| -------------------------- | --------- | -------------------------- |
| **Version**                | 4 bits    | IP 버전 (IPv4=4, IPv6=6)     |
| **Header Length**          | 4 bits    | IP 헤더 크기                   |
| **Type of Service (ToS)**  | 1         | QoS를 위한 서비스 유형             |
| **Total Length**           | 2         | 전체 패킷 크기 (헤더 + 데이터)        |
| **Identification**         | 2         | 패킷 ID (Fragmentation 시 필요) |
| **Flags**                  | 3 bits    | 패킷 단편화 관련 플래그              |
| **Fragment Offset**        | 2         | 패킷이 단편화될 경우 조각 순서 지정       |
| **Time to Live (TTL)**     | 1         | 패킷의 생존 시간 (라우터를 거칠 때마다 감소) |
| **Protocol**               | 1         | 상위 계층 프로토콜 (TCP=6, UDP=17) |
| **Header Checksum**        | 2         | 오류 검출을 위한 체크섬              |
| **Source IP Address**      | 4         | 출발지 IP 주소                  |
| **Destination IP Address** | 4         | 목적지 IP 주소                  |

##### **💡 Real-Life Example (실생활 예시)**

> **IP 헤더는 택배 송장과 같다.**
> 
> - 발송인(출발지 IP), 수취인(목적지 IP), 배송 경로(TTL), 택배 내용물(데이터) 포함.

---

## **4.3.3 IP Addressing (IP 주소 지정 및 구조)**

### **설명 (Explanation)**

IP 주소는 **네트워크에서 장치를 식별하는 고유한 논리 주소**이다.  
현재 IPv4(32-bit)와 IPv6(128-bit) 두 가지 IP 주소 체계가 사용된다.

### **1️⃣ IPv4 Addressing (IPv4 주소 체계)**

- **32-bit 주소 체계 (4 옥텟, 예: 192.168.1.1)**
- **네트워크 부분(Network) + 호스트 부분(Host)로 구성**
- **Classful Addressing(고정 클래스 방식, A/B/C 클래스) → Subnetting(서브넷 방식)으로 발전**

### **2️⃣ IPv6 Addressing (IPv6 주소 체계)**

- **128-bit 주소 체계 (예: 2001:db8::ff00:42:8329)**
- **더 많은 IP 주소를 제공하며, NAT(Network Address Translation) 없이 글로벌 유니크 주소 할당 가능**
- **IPSec(보안) 내장, 멀티캐스트 지원 강화**

#### **📌 IPv4 vs. IPv6 차이점**

|특징|IPv4|IPv6|
|---|---|---|
|**주소 크기**|32-bit|128-bit|
|**표기법**|192.168.0.1|2001:db8::ff00:42:8329|
|**NAT 필요성**|필요 (IP 주소 부족)|불필요|
|**보안**|별도 추가|IPSec 기본 지원|

##### **💡 Real-Life Example (실생활 예시)**

> **IPv4는 오래된 우편번호 시스템(주소 부족), IPv6는 새로운 확장된 우편번호 시스템(더 많은 주소 제공)과 같다.**

---

## **4.3.4 IP Fragmentation and Reassembly (IP 단편화 및 재조합)**

### **설명 (Explanation)**

패킷 크기가 **MTU(Maximum Transmission Unit, 최대 전송 단위)**보다 크면,  
라우터는 패킷을 작은 조각으로 나누어(Fragmentation) 전송한 후,  
수신 측에서 다시 결합(Reassembly)한다.

### **1️⃣ Fragmentation (단편화 과정)**

- **라우터가 큰 패킷을 작은 단편(Fragments)으로 나눔**.
- 각 조각은 **Identification, Fragment Offset, Flags** 필드를 사용하여 추적.

### **2️⃣ Reassembly (재조합 과정)**

- **수신 측에서 동일한 Identification 값을 가진 패킷들을 조합**하여 원래 데이터그램을 복구.

##### **💡 Real-Life Example (실생활 예시)**

> **단편화는 큰 화물을 작은 상자로 나누어 배송하는 것과 같다.**
> 
> - 큰 짐(패킷)을 작은 박스(Fragments)로 나누어 각기 다른 트럭(라우터)으로 배송.
> - 도착지에서 다시 하나로 조립(Reassembly).

---

## **4.3.5 ICMP: Internet Control Message Protocol (ICMP – 인터넷 제어 메시지 프로토콜)**

### **설명 (Explanation)**

ICMP는 **네트워크 오류 메시지를 전달하고 진단하는 프로토콜**이다.

### **ICMP 주요 기능**

|기능|설명|
|---|---|
|**Echo Request/Reply**|`ping` 명령어를 통해 네트워크 연결 확인|
|**Destination Unreachable**|목적지에 도달할 수 없을 때 전송|
|**Time Exceeded (TTL Expired)**|TTL이 0이 되면 패킷을 폐기|
|**Redirect Message**|더 나은 경로가 있을 경우 알려줌|

##### **💡 Real-Life Example (실생활 예시)**

> **ICMP는 교통 경찰이 운전자에게 길 상태를 알리는 것과 같다.**
> 
> - "이 길은 막혔습니다." (Destination Unreachable)
> - "너무 오래 이동해서 목적지에 도달할 수 없습니다." (TTL Expired)

---

### **📌 핵심 정리 (Key Takeaways)**

1. **IP는 패킷을 출발지에서 목적지까지 전달하는 네트워크 계층의 핵심 프로토콜이다.**
2. **IPv4는 32-bit 주소를 사용하며, IPv6는 128-bit 주소를 사용하여 더 많은 IP를 제공한다.**
3. **MTU보다 큰 패킷은 Fragmentation(단편화) 과정을 거쳐 전송된다.**
4. **ICMP는 네트워크 오류 메시지를 전달하는 프로토콜이며, `ping` 명령어에서 사용된다.**

🚀 **한 문장 요약:**  
IP는 **패킷을 출발지에서 목적지까지 전달하는 네트워크 프로토콜이며, IPv4 & IPv6를 사용하여 주소를 관리하고, ICMP를 통해 오류 메시지를 처리한다.**