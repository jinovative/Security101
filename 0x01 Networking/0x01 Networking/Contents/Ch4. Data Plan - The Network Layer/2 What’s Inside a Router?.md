[[The Network Layer – Data Plane]]

#### **요약 (Summary)**

**Router(라우터)**는 **Network Layer(네트워크 계층)**에서 **packets(패킷)**을 **input port(입력 포트)**에서 받아 **output port(출력 포트)**로 전달하는 역할을 한다.  
라우터 내부에는 **Forwarding Plane(포워딩 평면, Data Plane)과 Control Plane(제어 평면)**이 있으며, **포워딩 테이블(Forwarding Table)**을 이용해 최적의 경로로 패킷을 전달한다.

---

## **4.2.1 Router Architecture (라우터 아키텍처)**

### **설명 (Explanation)**

라우터는 네트워크에서 **패킷을 중계하고 적절한 경로로 전달하는 역할**을 한다.  
라우터 내부는 **Forwarding Plane(데이터 플레인)과 Control Plane(제어 플레인)**으로 구성된다.

### **1️⃣ Forwarding Plane (데이터 플레인) – 패킷 전달 담당**

- **Packet Forwarding(패킷 포워딩)**을 수행.
- 패킷을 **Forwarding Table(포워딩 테이블)**을 참조하여 올바른 출력 포트로 전달.
- **High-speed Hardware (고속 하드웨어, ASIC, TCAM)**을 사용하여 빠른 처리 가능.

### **2️⃣ Control Plane (제어 플레인) – 라우팅 정보 관리**

- **Routing Protocols(라우팅 프로토콜, OSPF, BGP, RIP 등)**을 사용하여 **라우팅 테이블(Routing Table)**을 생성.
- **Centralized Control (SDN, 소프트웨어 정의 네트워크)**도 가능.

#### **📌 Forwarding Plane vs. Control Plane 차이점**

|개념|역할|속도|구현 방식|
|---|---|---|---|
|**Forwarding Plane**|패킷 전달 (Fast Path)|빠름 (하드웨어 처리)|ASIC, TCAM, 라우터 내부 회로|
|**Control Plane**|경로 결정 (Slow Path)|상대적으로 느림 (소프트웨어)|CPU, 소프트웨어 기반|

##### **💡 Real-Life Example (실생활 예시)**

> **Forwarding Plane은 택배 분류 기계, Control Plane은 택배 배송 경로를 결정하는 관리자**와 같다.

---

## **4.2.2 Key Components of a Router (라우터의 주요 구성 요소)**

### **설명 (Explanation)**

라우터 내부에는 **패킷을 처리하고, 저장하고, 경로를 결정하는 다양한 하드웨어 및 소프트웨어**가 존재한다.

### **1️⃣ Input Ports (입력 포트)**

- **패킷을 수신**하고 적절한 큐(Queue)에 저장.
- **Lookup 기능**: Forwarding Table을 확인하여 적절한 출력 포트를 결정.

### **2️⃣ Switching Fabric (스위칭 패브릭)**

- **입력 포트에서 출력 포트로 패킷을 전달하는 내부 네트워크.**
- 주요 방식: **Crossbar, Bus, Interconnection Network**.

### **3️⃣ Output Ports (출력 포트)**

- **적절한 네트워크 인터페이스를 통해 패킷을 송출**.
- 혼잡(Congestion) 발생 시 **Queueing(대기열 관리)** 수행.

### **4️⃣ Routing Processor (라우팅 프로세서)**

- **라우팅 프로토콜 실행 (OSPF, BGP, RIP 등)**
- **Forwarding Table 업데이트** 및 네트워크 관리 수행.

##### **💡 Real-Life Example (실생활 예시)**

> - **Input Port = 택배 물류센터에서 물건을 받는 창구**
> - **Switching Fabric = 물류센터 내부에서 택배를 분류하는 시스템**
> - **Output Port = 택배를 목적지로 보내는 출구**
> - **Routing Processor = 물류센터에서 배송 경로를 결정하는 관리자**

---

## **4.2.3 Packet Forwarding Mechanisms (패킷 포워딩 방식)**

### **설명 (Explanation)**

라우터는 **패킷을 수신한 후, Forwarding Table을 기반으로 적절한 출력 포트로 전달**한다.

### **1️⃣ Destination-Based Forwarding (목적지 기반 포워딩)**

- **패킷의 목적지 IP 주소(Destination IP)를 기반으로 출력 포트 결정**.
- 일반적인 **IP 라우팅 방식**.

### **2️⃣ Generalized Forwarding (일반화된 포워딩, SDN 기반)**

- **패킷의 다양한 속성(출발지 주소, 프로토콜 등)을 기준으로 포워딩 결정**.
- **소프트웨어 정의 네트워크(SDN)**에서 사용됨.

##### **💡 Real-Life Example (실생활 예시)**

> - **Destination-Based Forwarding** = 일반 택배 배송 (목적지 주소만 확인).
> - **Generalized Forwarding** = 특수 배송(고객 요청에 따라 빠른 배송, 냉장 배송 등 추가 고려).

---

## **4.2.4 Switching Fabric (스위칭 패브릭, 내부 데이터 이동 방식)**

### **설명 (Explanation)**

라우터 내부에서 **입력 포트에서 출력 포트로 패킷을 이동시키는 구조**를 **Switching Fabric**이라고 한다.

### **Switching Fabric의 종류**

|방식|설명|장점|단점|
|---|---|---|---|
|**Memory Switching**|CPU가 패킷을 직접 복사하여 이동|구현이 간단|속도가 느림 (소프트웨어 기반)|
|**Bus Switching**|공유 버스를 통해 패킷을 전달|비용이 저렴|버스 대역폭이 제한됨|
|**Crossbar Switching**|입력과 출력을 직접 연결하는 방식|매우 빠름|비용이 비쌈 (하드웨어 복잡)|

##### **💡 Real-Life Example (실생활 예시)**

> - **Memory Switching = 사람이 직접 택배를 옮기는 방식 (느림)**
> - **Bus Switching = 컨베이어 벨트를 사용하지만 하나만 존재 (병목 발생 가능)**
> - **Crossbar Switching = 여러 개의 컨베이어 벨트(고속 패킷 처리)**

---

## **4.2.5 Queueing and Packet Scheduling (큐잉 및 패킷 스케줄링)**

### **설명 (Explanation)**

라우터에서 출력 포트가 혼잡하면 **Queueing(대기열 관리)**가 필요하다.  
이때 **패킷을 어떤 순서로 처리할지 결정하는 것이 Packet Scheduling(패킷 스케줄링)**이다.

### **1️⃣ FIFO (First-In, First-Out)**

- **도착한 순서대로 패킷을 처리**하는 방식.
- 공정하지만, 긴급한 패킷도 대기해야 함.

### **2️⃣ Priority Queueing (우선순위 대기열)**

- **패킷마다 우선순위를 부여하여 높은 우선순위 패킷을 먼저 처리**.
- 실시간 스트리밍, VoIP 등에 사용됨.

### **3️⃣ Weighted Fair Queueing (WFQ, 가중치 기반 공정 대기열)**

- **각 트래픽 유형에 따라 대역폭을 가중치로 나누어 처리**.
- 다양한 애플리케이션이 공정하게 네트워크를 사용하도록 보장.

##### **💡 Real-Life Example (실생활 예시)**

> - **FIFO = 줄 서서 기다리는 일반 계산대 (먼저 온 사람이 먼저 처리됨).**
> - **Priority Queueing = 공항의 VIP 우선 탑승 (긴급한 패킷 먼저 처리).**
> - **WFQ = 도로에서 버스 전용 차선을 제공하는 것과 유사 (특정 트래픽에 우선권 부여).**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **라우터(Router)는 패킷을 수신하여 적절한 출력 포트로 전달하는 네트워크 장비이다.**
2. **Forwarding Plane(데이터 평면)은 패킷을 빠르게 전달하고, Control Plane(제어 평면)은 라우팅 경로를 결정한다.**
3. **라우터 내부는 Input Ports, Switching Fabric, Output Ports, Routing Processor로 구성된다.**
4. **Queueing(대기열)과 Packet Scheduling(패킷 스케줄링)은 패킷이 효율적으로 전달되도록 관리하는 역할을 한다.**

🚀 **한 문장 요약:**  
라우터는 **패킷을 입력 포트에서 출력 포트로 전달하는 역할을 수행하며, Forwarding & Routing 기능을 통해 네트워크에서 최적의 경로를 선택하여 패킷을 전달한다.**