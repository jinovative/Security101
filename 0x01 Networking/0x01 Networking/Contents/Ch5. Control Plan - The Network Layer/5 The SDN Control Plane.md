[[The Network Layer – Control Plane]]


#### **요약 (Summary)**

**Software-Defined Networking (SDN)**은 **네트워크의 Control Plane(제어 평면)과 Data Plane(데이터 평면)을 분리**하여  
중앙에서 네트워크를 동적으로 제어할 수 있도록 하는 구조이다.  
전통적인 네트워크 장비(라우터, 스위치)는 **분산형 제어 방식(Distributed Control Plane)**을 사용하지만,  
SDN에서는 **Centralized Control Plane(중앙 집중형 제어 평면)**을 통해 **네트워크를 프로그래밍 방식으로 제어**할 수 있다.  
SDN의 핵심 기술로는 **OpenFlow Protocol(오픈플로우 프로토콜)**이 있으며, **SDN Controller(컨트롤러)가 네트워크 장비를 중앙에서 제어**한다.

---

## **5.5.1 Traditional vs. SDN Control Plane (전통 네트워크 vs. SDN 제어 평면 비교)**

### **설명 (Explanation)**

SDN은 기존 네트워크의 제어 방식과 비교했을 때 **더 높은 유연성과 자동화 기능을 제공**한다.

### **1️⃣ Traditional Control Plane (전통적인 제어 평면 – 분산형 제어)**

- **각 네트워크 장비(라우터, 스위치)가 개별적으로 경로를 결정**.
- **라우팅 프로토콜(OSPF, BGP 등)이 라우터 간 정보를 공유하여 경로를 설정**.
- **경로 변경이 있을 경우 모든 장비가 독립적으로 업데이트를 수행해야 함**.

### **2️⃣ SDN Control Plane (SDN 제어 평면 – 중앙 집중형 제어)**

- **Control Plane을 중앙 집중화하여 SDN Controller(컨트롤러)가 네트워크 전체를 제어**.
- **네트워크 장비(스위치, 라우터)는 Data Plane만 담당하며, Control Plane의 결정을 따름**.
- **OpenFlow와 같은 프로토콜을 사용하여 SDN 컨트롤러가 네트워크 장비를 프로그래밍 방식으로 제어 가능**.

#### **📌 Traditional vs. SDN Control Plane 비교**

|구분|Traditional Control Plane|SDN Control Plane|
|---|---|---|
|**제어 방식**|분산형 (Distributed)|중앙 집중형 (Centralized)|
|**라우팅 방식**|개별 장비가 라우팅 결정|SDN 컨트롤러가 전체 네트워크 관리|
|**유연성**|낮음|높음 (소프트웨어 기반 제어 가능)|
|**프로토콜**|OSPF, BGP|OpenFlow, REST API|

##### **💡 Real-Life Example (실생활 예시)**

> - **전통 네트워크 = 도시 내 개별 신호등이 자체적으로 운영되는 방식**
> - **SDN 네트워크 = 스마트 교통 시스템이 중앙에서 모든 신호등을 제어하는 방식**

---

## **5.5.2 SDN Architecture (SDN 아키텍처 – 3계층 구조)**

### **설명 (Explanation)**

SDN은 **3계층 구조**로 설계되며, **Application Layer, Control Layer, Infrastructure Layer**로 구성된다.

### **1️⃣ SDN의 3-Tier Architecture (SDN 3계층 구조)**

|계층|역할|주요 구성 요소|
|---|---|---|
|**Application Layer (애플리케이션 계층)**|네트워크 운영을 위한 애플리케이션|방화벽, 로드 밸런싱, QoS|
|**Control Layer (제어 계층)**|네트워크 정책 및 경로 결정|SDN Controller (OpenDaylight, ONOS)|
|**Infrastructure Layer (데이터 계층)**|실제 패킷 전달|OpenFlow Switches, SDN Router|

### **2️⃣ SDN Controller (SDN 컨트롤러의 역할)**

- **네트워크의 "뇌(Brain)" 역할**을 수행.
- **애플리케이션 계층과 네트워크 장비 간 인터페이스 제공**.
- **OpenFlow, REST API를 통해 네트워크를 프로그래밍 방식으로 제어**.

##### **💡 Real-Life Example (실생활 예시)**

> **SDN의 3계층 구조는 회사 조직과 유사하다.**
> 
> - **Application Layer = 경영진 (네트워크 정책 결정)**
> - **Control Layer = 관리자 (정책을 실행)**
> - **Infrastructure Layer = 직원 (실제 업무 수행, 패킷 전달)**

---

## **5.5.3 OpenFlow Protocol (OpenFlow 프로토콜 – SDN의 핵심 기술)**

### **설명 (Explanation)**

OpenFlow는 **SDN 컨트롤러가 네트워크 장비(스위치, 라우터)의 동작을 원격으로 제어할 수 있도록 하는 프로토콜**이다.

### **1️⃣ OpenFlow의 동작 방식**

1. **패킷이 OpenFlow Switch에 도착**.
2. **스위치는 Flow Table(플로우 테이블)을 확인하여 패킷을 처리**.
3. **일치하는 규칙이 없으면 SDN Controller에 Query(질의) 요청**.
4. **컨트롤러가 새로운 경로를 설정하고, 스위치에 업데이트**.

### **2️⃣ OpenFlow Flow Table (플로우 테이블 구조)**

|필드|설명|
|---|---|
|**Match Fields**|패킷의 속성 (출발지 IP, 목적지 IP, 포트 등)|
|**Actions**|수행할 작업 (포워딩, 드롭, 변경 등)|
|**Priority**|규칙의 우선순위|
|**Counters**|패킷 수를 기록하여 네트워크 모니터링 가능|

##### **💡 Real-Life Example (실생활 예시)**

> **OpenFlow는 스마트 물류 시스템과 유사하다.**
> 
> - 창고(스위치)는 **자동으로 패키지를 스캔하고**,
> - 중앙 물류 센터(SDN 컨트롤러)에서 **최적의 배송 경로를 결정**하여 창고에 전달.

---

## **5.5.4 Advantages and Challenges of SDN (SDN의 장점과 한계점)**

### **설명 (Explanation)**

SDN은 기존 네트워크의 한계를 극복하지만, 몇 가지 기술적 도전 과제도 존재한다.

### **1️⃣ SDN의 장점 (Advantages of SDN)**

✅ **Centralized Control (중앙 집중 제어)** – 네트워크 정책을 일괄적으로 관리 가능  
✅ **Dynamic Traffic Management (동적 트래픽 관리)** – 실시간으로 네트워크 흐름 조절 가능  
✅ **Programmability (프로그래밍 가능성)** – API를 이용하여 네트워크 자동화 가능  
✅ **Reduced Cost (비용 절감)** – 범용 하드웨어(OpenFlow Switch) 사용 가능

### **2️⃣ SDN의 한계점 (Challenges of SDN)**

🚨 **Scalability Issues (확장성 문제)** – 대규모 네트워크에서 컨트롤러 부하 증가 가능  
🚨 **Security Risks (보안 문제)** – SDN 컨트롤러가 공격당하면 전체 네트워크 마비 가능  
🚨 **Legacy Network Compatibility (기존 네트워크와의 호환성 문제)** – 기존 장비와 통합이 어려움

##### **💡 Real-Life Example (실생활 예시)**

> - **SDN의 장점 = 스마트 도시에서 중앙에서 모든 신호등을 관리하는 것 (효율적, 동적 제어 가능)**
> - **SDN의 단점 = 중앙 시스템이 다운되면 모든 신호등이 정지될 위험**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **SDN(Software-Defined Networking)은 Control Plane(제어 평면)과 Data Plane(데이터 평면)을 분리하여 중앙에서 네트워크를 제어하는 기술이다.**
2. **SDN Controller는 네트워크 정책을 결정하고, OpenFlow를 통해 스위치와 라우터를 제어한다.**
3. **SDN의 장점으로는 중앙 집중 제어, 동적 트래픽 관리, 자동화가 있으며, 보안 및 확장성 문제가 해결해야 할 과제이다.**

🚀 **한 문장 요약:**  
**SDN은 네트워크의 Control Plane과 Data Plane을 분리하여 중앙에서 네트워크를 프로그래밍 방식으로 동적으로 제어할 수 있도록 하는 혁신적인 기술이다.**