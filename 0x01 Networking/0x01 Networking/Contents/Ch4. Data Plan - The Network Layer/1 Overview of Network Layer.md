[[The Network Layer – Data Plane]]


#### **요약 (Summary)**

**Network Layer(네트워크 계층)**는 **source host(발신 호스트)에서 destination host(목적지 호스트)까지 패킷을 전달**하는 역할을 한다.  
이 계층은 **Routing(라우팅)과 Forwarding(포워딩)**을 수행하며, **IP 주소 기반의 논리적 주소 지정(logical addressing)을 사용**한다.  
네트워크 계층의 주요 프로토콜은 **IP(Internet Protocol)**이며, ICMP, ARP 같은 보조 프로토콜도 포함된다.

---

## **4.1.1 The Role of the Network Layer (네트워크 계층의 역할)**

### **설명 (Explanation)**

네트워크 계층은 **end-to-end packet delivery(종단 간 패킷 전달)**을 담당하며, **라우터(router)를 통해 패킷을 올바른 경로로 이동시킨다**.

### **1️⃣ 주요 기능 (Key Functions of Network Layer)**

|기능|설명|
|---|---|
|**Forwarding (포워딩)**|패킷을 입력 포트에서 올바른 출력 포트로 전달|
|**Routing (라우팅)**|최적의 경로를 계산하여 패킷이 목적지까지 도달하도록 함|
|**Addressing (주소 지정)**|각 장치에 **IP 주소**를 할당하여 식별|
|**Fragmentation (단편화)**|패킷이 MTU(Maximum Transmission Unit)보다 클 경우 분할|
|**Error Reporting (오류 보고)**|ICMP 프로토콜을 이용해 패킷 전송 오류를 알림|

##### **💡 Real-Life Example (실생활 예시)**

> **네트워크 계층은 택배 시스템과 같다.**
> 
> - 택배가 여러 도시를 거쳐(라우팅) 올바른 배송 경로를 따라가며,
> - 각 물류센터(라우터)가 택배를 분류하고 전달(포워딩).

---

## **4.1.2 Forwarding vs. Routing (포워딩 vs. 라우팅)**

### **설명 (Explanation)**

네트워크 계층의 가장 중요한 기능은 **Forwarding(포워딩)**과 **Routing(라우팅)**이다.  
이 두 개념은 종종 혼동되지만, **서로 다른 역할을 수행**한다.

### **1️⃣ Forwarding (포워딩) – 패킷 전송**

- **Router가 수신한 패킷을 적절한 출력 포트로 전달**하는 과정.
- **패킷 스위칭(Packet Switching)**을 사용하여 빠르게 전송.
- Forwarding Table(포워딩 테이블)을 기반으로 결정됨.

### **2️⃣ Routing (라우팅) – 경로 결정**

- **출발지에서 목적지까지 최적의 경로(Path)를 찾는 과정.**
- **라우팅 알고리즘(Routing Algorithm)**을 사용하여 최적의 경로를 계산.
- Routing Table(라우팅 테이블)에 경로 정보 저장.

#### **📌 Forwarding vs. Routing 차이점**

|개념|역할|주요 구성 요소|
|---|---|---|
|**Forwarding**|개별 패킷을 올바른 출력 포트로 이동|Forwarding Table|
|**Routing**|최적의 경로를 결정|Routing Algorithm, Routing Table|

##### **💡 Real-Life Example (실생활 예시)**

> **Routing은 고속도로 네비게이션 경로 계산과 같고, Forwarding은 실제로 그 경로를 따라 운전하는 것과 같다.**

---

## **4.1.3 Network Service Models (네트워크 서비스 모델)**

### **설명 (Explanation)**

네트워크 계층은 데이터를 전송하는 **Service Model(서비스 모델)**을 정의한다.  
서비스 모델은 **패킷 전달 방식과 품질(QoS, Quality of Service)**을 결정한다.

### **1️⃣ Best-Effort Service (최선형 서비스)**

- **인터넷에서 기본적으로 사용되는 모델**.
- **전송 보장 없음** (패킷 손실 가능, 순서 변경 가능, 지연 발생 가능).
- TCP가 전송 계층에서 신뢰성을 보장해야 함.

### **2️⃣ Guaranteed Service (보장형 서비스)**

- **QoS(Quality of Service) 지원**하여 일정한 속도와 지연을 보장.
- VoIP(인터넷 전화)나 실시간 스트리밍 서비스에서 필요.

#### **📌 Best-Effort vs. Guaranteed Service 차이점**

|서비스 모델|신뢰성|패킷 손실|QoS 보장|
|---|---|---|---|
|**Best-Effort**|없음|가능|없음|
|**Guaranteed**|있음|없음|보장|

##### **💡 Real-Life Example (실생활 예시)**

> - **Best-Effort Service** = 일반 우편 (빠르지만 손실 가능).
> - **Guaranteed Service** = 택배 특송 (추적 가능, 시간 보장).

---

## **4.1.4 Network Layer Protocols (네트워크 계층 프로토콜)**

### **설명 (Explanation)**

네트워크 계층에는 다양한 프로토콜이 존재하며, 가장 중요한 프로토콜은 **IP(Internet Protocol)**이다.

### **1️⃣ Internet Protocol (IP) – 인터넷 프로토콜**

- **패킷 전달의 기본 프로토콜**
- IP 주소를 기반으로 패킷을 전송
- **IPv4 (32-bit 주소) vs. IPv6 (128-bit 주소)**

### **2️⃣ ICMP (Internet Control Message Protocol) – 오류 보고 및 진단**

- 네트워크 문제 발생 시 오류 메시지를 전송.
- **예:** `ping` 명령어는 ICMP Echo Request/Reply를 사용.

### **3️⃣ ARP (Address Resolution Protocol) – IP ↔ MAC 변환**

- 네트워크에서 **IP 주소를 MAC 주소로 변환**하는 프로토콜.
- 로컬 네트워크에서 통신할 때 사용됨.

##### **💡 Real-Life Example (실생활 예시)**

> - **IP = 지도에 표시된 목적지 주소**
> - **ICMP = 네비게이션 경로 오류 메시지(길 막힘 경고)**
> - **ARP = 목적지 주소(IP)에서 정확한 집 번호(MAC)를 찾는 과정**

---

## **4.1.5 IPv4 vs. IPv6 (IPv4와 IPv6 비교)**

### **설명 (Explanation)**

현재 인터넷에서 가장 많이 사용되는 **IPv4**는 **32-bit 주소 체계**를 사용하지만,  
IP 주소 부족 문제를 해결하기 위해 **IPv6(128-bit 주소 체계)**가 도입되었다.

#### **📌 IPv4 vs. IPv6 차이점**

|특징|IPv4|IPv6|
|---|---|---|
|**주소 크기**|32-bit (약 43억 개 주소)|128-bit (거의 무제한)|
|**표기법**|192.168.0.1 (점 구분)|2001:db8::ff00:42:8329 (콜론 구분)|
|**보안**|보안 기능 없음 (외부 IPSec 필요)|IPSec 기본 내장|
|**라우팅 효율성**|복잡한 NAT 필요|NAT 없이 직접 라우팅 가능|

##### **💡 Real-Life Example (실생활 예시)**

> **IPv4는 오래된 전화번호 체계(번호 부족), IPv6는 새로운 국제 전화번호 체계(무제한 번호)와 같다.**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **네트워크 계층(Network Layer)은 패킷을 출발지에서 목적지까지 전달하는 역할을 수행한다.**
2. **Forwarding(포워딩)**은 패킷을 적절한 출력 포트로 전달하는 과정이며, **Routing(라우팅)**은 최적의 경로를 결정하는 과정이다.
3. **네트워크 계층 서비스 모델**에는 **Best-Effort Service(최선형 서비스)**와 **Guaranteed Service(보장형 서비스)**가 있다.
4. **IPv4는 32-bit 주소를 사용하며, IPv6는 128-bit 주소를 사용하여 더 많은 IP 주소를 제공한다.**
5. **ICMP는 네트워크 오류 메시지를 처리하고, ARP는 IP 주소를 MAC 주소로 변환한다.**

🚀 **한 문장 요약:**  
**네트워크 계층은 패킷을 올바른 목적지로 전달하는 역할을 하며, Forwarding과 Routing을 수행하고 IP, ICMP, ARP 같은 프로토콜을 사용한다.**