[[The Network Layer – Control Plane]]



### **5.1 Introduction to Control Plane (제어 평면 개요)**

#### **요약 (Summary)**

**Control Plane(제어 평면)**은 **네트워크 장치(라우터, 스위치 등)가 패킷을 목적지까지 올바르게 전달하기 위해 라우팅 정보를 관리하는 계층**이다.  
이는 **Routing Algorithms(라우팅 알고리즘)**을 사용하여 **Routing Table(라우팅 테이블)**을 생성하고, 패킷이 최적의 경로로 이동할 수 있도록 한다.  
제어 평면은 **Centralized Control (중앙 집중식, SDN)과 Distributed Control (분산형, 기존 라우팅 방식)**으로 나뉜다.

---

## **5.1.1 Data Plane vs. Control Plane (데이터 평면 vs. 제어 평면 비교)**

### **설명 (Explanation)**

네트워크 장치는 **Data Plane(데이터 평면)과 Control Plane(제어 평면)**으로 나뉜다.

- **Data Plane:** 개별 패킷을 포워딩하는 역할
- **Control Plane:** 라우팅 정보를 관리하고 최적의 경로를 설정

### **1️⃣ Data Plane (데이터 평면) – 패킷 전송 담당**

- **패킷을 Forwarding Table(포워딩 테이블)에 따라 전송**
- **라우터의 하드웨어(ASIC, TCAM 등)를 이용하여 빠르게 처리**
- **Layer 2 (Ethernet) 및 Layer 3 (IP) 수준에서 동작**

### **2️⃣ Control Plane (제어 평면) – 네트워크 경로 결정**

- **라우팅 알고리즘을 사용하여 최적의 경로를 결정**
- **Routing Protocols (OSPF, BGP, RIP 등)를 사용하여 Routing Table(라우팅 테이블) 생성**
- **소프트웨어 기반 처리 (라우터 CPU가 실행)**

#### **📌 Data Plane vs. Control Plane 차이점**

|구분|Data Plane (데이터 평면)|Control Plane (제어 평면)|
|---|---|---|
|**역할**|패킷을 전달 (포워딩)|최적의 경로 결정 (라우팅)|
|**처리 속도**|매우 빠름 (하드웨어)|상대적으로 느림 (소프트웨어)|
|**구성 요소**|포워딩 테이블, 스위칭 패브릭|라우팅 테이블, 라우팅 프로토콜|
|**사용 기술**|TCAM, ASIC|OSPF, BGP, RIP|

##### **💡 Real-Life Example (실생활 예시)**

> **Data Plane은 택배 배송 과정(패킷 전달), Control Plane은 물류 시스템의 최적 경로 설정(라우팅)과 같다.**
> 
> - 데이터 평면 = **배송 차량이 특정 경로를 따라 이동하는 과정**
> - 제어 평면 = **택배 회사가 최적의 배송 경로를 결정하는 과정**

---

## **5.1.2 Centralized vs. Distributed Control Plane (중앙 집중 vs. 분산형 제어 평면)**

### **설명 (Explanation)**

제어 평면은 **Centralized Control(중앙 집중식 제어)과 Distributed Control(분산형 제어)**로 구현될 수 있다.

### **1️⃣ Distributed Control Plane (분산형 제어 평면 – 기존 네트워크 방식)**

- **각 라우터가 독립적으로 라우팅 정보를 계산하고 공유**.
- **라우팅 프로토콜(OSPF, BGP, RIP)을 사용하여 경로 결정**.
- 네트워크가 **동적으로 변화하더라도 개별 라우터가 독립적으로 적응 가능**.

### **2️⃣ Centralized Control Plane (중앙 집중형 제어 평면 – SDN 기반 네트워크)**

- **모든 라우터의 경로 정보를 중앙 컨트롤러(SDN Controller)가 관리**.
- **라우터는 포워딩만 담당하고, 제어 평면의 모든 의사결정은 중앙에서 수행**.
- **OpenFlow와 같은 프로토콜을 사용하여 네트워크를 동적으로 제어**.

#### **📌 Centralized vs. Distributed Control 차이점**

|구분|Distributed Control (분산형)|Centralized Control (중앙 집중형)|
|---|---|---|
|**라우팅 방식**|개별 라우터가 독립적으로 경로 결정|SDN 컨트롤러가 전체 네트워크 관리|
|**장점**|자율적 동작, 장애 발생 시 복구 용이|네트워크 최적화 가능, 정책 변경 용이|
|**단점**|경로 최적화가 어려움|컨트롤러 장애 발생 시 전체 네트워크 영향|

##### **💡 Real-Life Example (실생활 예시)**

> - **Distributed Control Plane = 개별 택배 기사들이 자체적으로 최적 경로를 결정하는 방식**
> - **Centralized Control Plane = 본사에서 모든 배송 차량의 경로를 최적화하여 지정하는 방식**

---

## **5.1.3 Routing Protocols (라우팅 프로토콜의 역할)**

### **설명 (Explanation)**

제어 평면에서 라우팅을 수행하려면 **라우팅 프로토콜(Routing Protocol)**이 필요하다.  
라우팅 프로토콜은 네트워크 내에서 **최적의 경로를 동적으로 계산하고 업데이트**한다.

### **1️⃣ Intra-AS Routing (자율 시스템 내 라우팅, IGP)**

- **OSPF (Open Shortest Path First)** – Link-State 라우팅 프로토콜
- **RIP (Routing Information Protocol)** – Distance Vector 라우팅 프로토콜

### **2️⃣ Inter-AS Routing (자율 시스템 간 라우팅, EGP)**

- **BGP (Border Gateway Protocol)** – 인터넷에서 사용되는 글로벌 라우팅 프로토콜

#### **📌 Distance Vector vs. Link State 라우팅 차이점**

|구분|Distance Vector|Link State|
|---|---|---|
|**경로 계산 방식**|인접 라우터의 정보를 공유하여 거리 기반으로 경로 결정|네트워크 전체 맵을 구축하여 최적 경로 결정|
|**예제 프로토콜**|RIP|OSPF|
|**장점**|구현이 간단함|더 빠르고 정확한 경로 계산 가능|
|**단점**|경로 수렴 속도가 느림|더 많은 리소스 필요|

##### **💡 Real-Life Example (실생활 예시)**

> - **Distance Vector (RIP) = 친구에게 목적지를 물어보면서 경로를 찾아가는 방식**
> - **Link State (OSPF) = 네비게이션이 전체 지도 정보를 바탕으로 최적 경로를 계산하는 방식**

---

## **5.1.4 Challenges in Control Plane (제어 평면의 주요 과제)**

### **설명 (Explanation)**

제어 평면은 네트워크의 경로를 관리하는 중요한 역할을 하지만, 여러 도전 과제가 존재한다.

### **1️⃣ Convergence Time (수렴 시간 문제)**

- 네트워크가 변경될 때 라우팅 프로토콜이 새로운 최적 경로를 계산하는 데 시간이 필요함.

### **2️⃣ Scalability (확장성 문제)**

- 대규모 네트워크에서는 라우팅 테이블이 커지고, 제어 메시지가 많아져 성능 저하 가능.

### **3️⃣ Security (보안 문제)**

- BGP 하이재킹(BGP Hijacking)과 같은 공격으로 인해 잘못된 라우팅 정보가 네트워크에 전파될 위험이 있음.

##### **💡 Real-Life Example (실생활 예시)**

> **네트워크 수렴 문제는 지진이 발생했을 때 교통 네트워크가 새로운 우회 경로를 찾는 과정과 유사하다.**
> 
> - 도로가 차단되면(네트워크 장애),
> - 새로운 최적 경로를 찾기까지 시간이 필요(라우팅 수렴).

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Control Plane(제어 평면)은 최적의 경로를 결정하고, Data Plane(데이터 평면)은 패킷을 전달한다.**
2. **제어 평면은 Distributed 방식(전통적 라우팅)과 Centralized 방식(SDN)으로 구현될 수 있다.**
3. **라우팅 프로토콜은 Intra-AS(RIP, OSPF)와 Inter-AS(BGP)로 나뉘며, 네트워크 경로를 동적으로 관리한다.**
4. **제어 평면의 주요 과제는 Convergence Time, Scalability, Security이다.**

🚀 **한 문장 요약:**  
**제어 평면(Control Plane)은 네트워크에서 최적의 경로를 결정하는 역할을 하며, 기존 분산 방식과 SDN 기반 중앙 집중 방식으로 운영될 수 있다.**