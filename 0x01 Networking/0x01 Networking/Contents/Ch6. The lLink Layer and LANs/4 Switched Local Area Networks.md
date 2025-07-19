[[The Link Layer and LANs]]


#### **요약 (Summary)**

**Switched LAN(스위치 기반 로컬 네트워크)**는 **스위치(Switch)를 사용하여 여러 장치를 연결하고, 데이터를 효율적으로 전달하는 LAN(Local Area Network) 구조**이다.  
전통적인 **Shared LAN(공유형 LAN)**에서는 네트워크 자원을 여러 장치가 공유하여 **충돌(Collision)**이 발생했지만,  
Switched LAN에서는 **각 장치가 독립적인 연결을 가지므로 충돌이 제거되고 네트워크 성능이 향상됨**.  
대표적인 Switched LAN 기술로는 **Ethernet(이더넷, IEEE 802.3)**과 **VLAN(Virtual LAN)**이 있다.

---

## **6.4.1 Shared LAN vs. Switched LAN (공유형 LAN vs. 스위치 기반 LAN 비교)**

### **설명 (Explanation)**

LAN(Local Area Network)은 **여러 개의 장치(컴퓨터, 프린터 등)를 하나의 네트워크로 연결하는 방식**을 의미하며,  
구현 방식에 따라 **Shared LAN(공유형 LAN)과 Switched LAN(스위치 기반 LAN)으로 구분**된다.

### **1️⃣ Shared LAN (허브 기반 LAN – 전통적인 LAN 구조)**

- **네트워크의 모든 장치가 하나의 공유된 매체를 사용하여 데이터를 전송**.
- **CSMA/CD (Collision Detection) 방식으로 충돌을 감지하고 재전송**.
- **네트워크 트래픽이 증가하면 성능이 급격히 저하됨**.
- **예:** **허브(Hub) 기반의 이더넷 네트워크**.

### **2️⃣ Switched LAN (스위치 기반 LAN – 현대적인 LAN 구조)**

- **스위치(Switch)가 각 장치를 개별적으로 연결하여 충돌을 방지**.
- **전이중 통신(Full-Duplex)을 지원하여 네트워크 성능 향상**.
- **각 포트가 독립적인 링크를 가지므로 대역폭을 최적화할 수 있음**.
- **예:** **Ethernet Switch 기반 네트워크**.

#### **📌 Shared LAN vs. Switched LAN 비교**

|구분|Shared LAN (허브 기반)|Switched LAN (스위치 기반)|
|---|---|---|
|**통신 방식**|브로드캐스트 (모든 장치에 전송)|개별 장치 간 전용 연결|
|**충돌 가능성**|있음 (CSMA/CD 필요)|없음 (Full-Duplex 지원)|
|**성능**|트래픽 증가 시 성능 저하|트래픽 증가에도 안정적|
|**사용 장비**|허브 (Hub)|스위치 (Switch)|

##### **💡 Real-Life Example (실생활 예시)**

> - **Shared LAN = 한 방에서 여러 사람이 동시에 대화하여 서로 방해하는 상황**
> - **Switched LAN = 개별 방에서 1:1로 대화하는 방식 (충돌 없이 독립적 통신 가능)**

---

## **6.4.2 Ethernet Switches (이더넷 스위치의 동작 방식)**

### **설명 (Explanation)**

**Ethernet Switch(이더넷 스위치)**는 **각 장치가 네트워크에 개별적으로 연결될 수 있도록 도와주는 네트워크 장비**이다.  
스위치는 **MAC Address(물리적 주소)를 기반으로 프레임을 전달**하며, 효율적인 네트워크 트래픽을 관리할 수 있다.

### **1️⃣ Switch Forwarding Table (스위치 포워딩 테이블)**

스위치는 **MAC 주소 테이블(MAC Address Table, CAM Table)을 사용하여 프레임을 적절한 포트로 전달**한다.

📌 **Switch의 동작 방식**

1. 장치가 데이터를 전송하면, **스위치는 송신자의 MAC 주소를 테이블에 저장**.
2. 목적지 MAC 주소가 테이블에 있으면, 해당 포트로 데이터를 전송 (Unicast).
3. 목적지 MAC 주소가 없으면, 네트워크 전체에 브로드캐스트 후 응답을 기다림.
4. 테이블을 지속적으로 업데이트하여 네트워크 성능을 최적화.

#### **📌 Switch Forwarding 방식**

|Forwarding 방식|설명|
|---|---|
|**Unicast (유니캐스트)**|특정 목적지 MAC 주소로 프레임 전송|
|**Broadcast (브로드캐스트)**|네트워크 전체로 프레임 전송 (목적지 MAC 주소 미확인 시)|
|**Multicast (멀티캐스트)**|특정 그룹의 장치에만 프레임 전송|

##### **💡 Real-Life Example (실생활 예시)**

> **이더넷 스위치는 스마트 우체국과 유사하다.**
> 
> - 모든 편지를 무작위로 배달하는 것이 아니라(Shared LAN),
> - **우편번호(MAC 주소)를 기반으로 정확한 목적지로 배달 (Switched LAN).**

---

## **6.4.3 VLAN (Virtual LAN, 가상 LAN)**

### **설명 (Explanation)**

**VLAN(Virtual LAN)**은 **하나의 물리적 네트워크에서 논리적으로 다른 네트워크를 생성할 수 있도록 하는 기술**이다.  
즉, **같은 스위치에 연결된 장치라도 VLAN을 설정하면 서로 다른 네트워크로 동작할 수 있음**.

### **1️⃣ VLAN의 주요 기능 (Key Features of VLAN)**

|기능|설명|
|---|---|
|**논리적 네트워크 분리**|같은 스위치 내에서도 서로 다른 VLAN을 구성하여 트래픽을 분리|
|**보안 강화**|특정 VLAN 간 통신을 제한하여 보안성을 높일 수 있음|
|**트래픽 감소**|불필요한 브로드캐스트 트래픽을 줄여 네트워크 성능 향상|
|**유연한 네트워크 구성**|물리적 위치에 상관없이 VLAN을 통해 논리적으로 네트워크 구성 가능|

📌 **VLAN 예제**

yaml

CopyEdit

`VLAN 10: IT 부서 (192.168.1.x) VLAN 20: HR 부서 (192.168.2.x) VLAN 30: 회계 부서 (192.168.3.x)`

→ **각 부서는 서로 다른 VLAN을 사용하여 분리된 네트워크 환경을 유지**.

##### **💡 Real-Life Example (실생활 예시)**

> **VLAN은 회사에서 부서별로 내부 네트워크를 분리하는 것과 유사하다.**
> 
> - IT 부서, 회계 부서, 인사 부서가 동일한 건물에 있어도 **네트워크 트래픽을 논리적으로 분리하여 보안성과 성능을 유지**.

---

## **6.4.4 Link Layer Addressing: ARP (Address Resolution Protocol)**

### **설명 (Explanation)**

**ARP(Address Resolution Protocol)**는 **IP 주소를 MAC 주소로 변환하는 프로토콜**이다.  
네트워크에서 **IP 주소만으로는 데이터를 전송할 수 없기 때문에, 목적지 장치의 MAC 주소를 알아내야 함**.

### **1️⃣ ARP 동작 방식 (How ARP Works)**

1. 송신 장치가 ARP Request(브로드캐스트)를 전송: "이 IP 주소를 가진 장치의 MAC 주소를 알려주세요!"
2. 목적지 장치가 ARP Reply(유니캐스트)로 MAC 주소를 응답.
3. 송신 장치는 응답받은 MAC 주소를 **ARP Cache(캐시)에 저장**하여 향후 동일한 요청을 반복하지 않음.

📌 **ARP Request & Reply 예제**

arduino

CopyEdit

`송신자: "192.168.1.10의 MAC 주소를 알고 싶어요!" 응답자: "192.168.1.10의 MAC 주소는 00:1A:2B:3C:4D:5E 입니다."`

##### **💡 Real-Life Example (실생활 예시)**

> **ARP는 전화번호부와 유사하다.**
> 
> - 친구의 전화번호(IP 주소)는 알지만, 휴대폰(MAC 주소) 번호는 모르므로 전화번호부(ARP)를 이용해 조회하는 것과 같다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Switched LAN(스위치 기반 LAN)은 허브 기반의 Shared LAN보다 충돌이 없고, 더 높은 성능을 제공한다.**
2. **Ethernet Switch는 MAC 주소 기반으로 포워딩을 수행하며, VLAN을 통해 네트워크를 논리적으로 분리할 수 있다.**
3. **ARP(Address Resolution Protocol)는 IP 주소를 MAC 주소로 변환하는 프로토콜이다.**

🚀 **한 문장 요약:**  
**Switched LAN은 네트워크 트래픽을 효율적으로 관리하는 Ethernet Switch 기반의 네트워크 구조이며, VLAN과 ARP를 활용하여 논리적 네트워크 분리 및 주소 변환을 수행한다.**