[[The Network Layer – Control Plane]]


#### **요약 (Summary)**

**OSPF (Open Shortest Path First)**는 **Link-State Routing Protocol(링크 상태 라우팅 프로토콜)**로,  
**Intra-AS Routing(AS 내부 라우팅, IGP)**에서 사용된다.  
OSPF는 **각 라우터가 네트워크의 전체 맵을 유지하고, Dijkstra’s Algorithm(다익스트라 알고리즘)**을 사용하여 최단 경로를 계산한다.  
이를 통해 빠른 경로 수렴과 확장성을 제공하며, **Hierarchical OSPF(계층적 OSPF)** 구조를 사용하여 대규모 네트워크에서도 효율적인 라우팅이 가능하다.

---

## **5.3.1 Intra-AS Routing and OSPF (자율 시스템 내부 라우팅과 OSPF의 역할)**

### **설명 (Explanation)**

**Intra-AS Routing(AS 내부 라우팅)**은 **하나의 AS(Autonomous System) 내에서 최적의 경로를 찾는 과정**이다.  
기업, ISP, 기관 내의 네트워크에서 사용되며, 대표적인 프로토콜로 **OSPF(Open Shortest Path First)**와 **RIP(Routing Information Protocol)**이 있다.

### **1️⃣ Why OSPF? (왜 OSPF를 사용하는가?)**

|기존 방식|한계점|
|---|---|
|**RIP (Routing Information Protocol)**|최대 홉 수 15, 네트워크 크기가 커질수록 비효율적|
|**Static Routing (정적 라우팅)**|네트워크 변화가 있을 때 수동 업데이트 필요|

✅ **OSPF는 Distance Vector 방식의 한계를 해결하고, 대규모 네트워크에서 빠르고 안정적인 라우팅을 제공함.**

---

## **5.3.2 OSPF Key Features (OSPF의 주요 특징)**

### **설명 (Explanation)**

OSPF는 **Link-State Routing**을 기반으로 동작하며, **빠른 수렴 속도(Fast Convergence), Load Balancing(부하 분산), 보안(Security) 등의 기능을 제공한다.**

### **1️⃣ 주요 특징 (Key Features of OSPF)**

|특징|설명|
|---|---|
|**Link-State Routing (링크 상태 라우팅)**|네트워크 전체 맵을 유지하고 Dijkstra 알고리즘으로 최단 경로 계산|
|**Hierarchical Structure (계층적 구조)**|대규모 네트워크를 영역(Area)으로 나누어 관리|
|**Fast Convergence (빠른 수렴 속도)**|변화가 발생하면 즉시 업데이트하여 경로를 빠르게 수정|
|**Load Balancing (부하 분산 지원)**|여러 경로가 있을 경우 부하를 분산하여 최적의 경로를 선택|
|**Security (보안 기능 내장)**|인증(Authentication)을 통해 보안 강화 가능|

##### **💡 Real-Life Example (실생활 예시)**

> **OSPF는 네비게이션 시스템과 같다.**
> 
> - **도로 상태(링크 상태)를 실시간으로 분석**하여,
> - **가장 빠른 경로를 찾아서 안내**.

---

## **5.3.3 OSPF Routing Algorithm (OSPF 라우팅 알고리즘 – 다익스트라 알고리즘)**

### **설명 (Explanation)**

OSPF는 **Dijkstra’s Algorithm(다익스트라 알고리즘)**을 사용하여 최단 경로를 계산한다.

### **1️⃣ Dijkstra Algorithm 동작 방식**

1. **각 라우터는 Link State Database (LSDB)를 생성하여 네트워크 맵을 유지**
2. **Dijkstra’s Algorithm을 사용하여 출발지에서 모든 목적지까지의 최단 경로를 계산**
3. **최적 경로를 Forwarding Table(포워딩 테이블)에 저장하여 패킷을 전송**

### **2️⃣ OSPF 메시지 유형 (OSPF Packet Types)**

|메시지 타입|설명|
|---|---|
|**Hello Packet**|OSPF Neighbor 관계 형성 및 유지|
|**LSA (Link-State Advertisement)**|라우터 간 링크 상태 정보 공유|
|**DBD (Database Description Packet)**|LSDB 정보를 동기화|
|**LSR (Link-State Request)**|특정 링크 상태 정보를 요청|
|**LSU (Link-State Update)**|네트워크 변경 시 업데이트 정보 전송|

##### **💡 Real-Life Example (실생활 예시)**

> **OSPF의 동작 방식은 네비게이션이 실시간으로 교통 정보를 반영하여 최단 경로를 찾는 것과 유사하다.**
> 
> - 네비게이션이 **도로 상황(LSDB)**을 파악하고,
> - **최적 경로(Dijkstra 알고리즘)**를 계산하여 안내.

---

## **5.3.4 OSPF Hierarchical Design (계층적 OSPF 구조)**

### **설명 (Explanation)**

OSPF는 대규모 네트워크에서도 효율적으로 동작하기 위해 **Hierarchical Design(계층적 설계)**을 사용한다.

### **1️⃣ OSPF Areas (OSPF 영역 개념)**

OSPF 네트워크는 **Multiple Areas(여러 개의 영역)**으로 나뉘며,  
중앙 **Backbone Area (Area 0)**이 다른 영역을 연결하는 역할을 한다.

|OSPF 영역|역할|
|---|---|
|**Backbone Area (Area 0)**|모든 OSPF 영역의 중심, 다른 영역을 연결|
|**Regular Area (일반 영역, Area 1,2,3…)**|OSPF 라우터가 속하는 개별 영역|
|**Stub Area (스텁 영역)**|외부 경로를 제한하여 라우팅 효율을 높임|

### **2️⃣ OSPF 계층 구조의 장점**

✅ **라우팅 테이블 크기 감소 → 메모리 및 CPU 사용량 절감**  
✅ **라우팅 업데이트 트래픽 감소 → 네트워크 대역폭 절약**  
✅ **빠른 장애 복구 → 영역 간 격리로 인해 장애 발생 시 영향 최소화**

##### **💡 Real-Life Example (실생활 예시)**

> **OSPF의 계층적 구조는 대형 쇼핑몰의 안내 시스템과 유사하다.**
> 
> - 쇼핑몰(Backbone Area) 안에는 **여러 개의 층(Regular Areas)이 존재**하고,
> - 각 층의 정보는 중앙 안내 데스크(Area 0)를 통해 연결됨.

---

## **5.3.5 OSPF vs. RIP (OSPF와 RIP 비교)**

### **설명 (Explanation)**

RIP와 OSPF는 모두 Intra-AS Routing 프로토콜이지만, 성능과 확장성에서 큰 차이가 있다.

#### **📌 OSPF vs. RIP 비교**

|특징|OSPF|RIP|
|---|---|---|
|**라우팅 방식**|Link-State Routing|Distance Vector Routing|
|**경로 계산 방식**|Dijkstra’s Algorithm|Bellman-Ford Algorithm|
|**최대 홉 수**|제한 없음|15 홉 제한|
|**네트워크 크기**|대규모 네트워크에 적합|소규모 네트워크에 적합|
|**수렴 속도**|빠름|느림|
|**로드 밸런싱**|지원|제한적 지원|

##### **💡 Real-Life Example (실생활 예시)**

> - **OSPF = 네비게이션을 이용한 최적 경로 탐색 (최신 교통 상황 반영)**
> - **RIP = 길을 아는 친구들에게 물어보는 방식 (업데이트가 느림)**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **OSPF(Open Shortest Path First)는 Link-State Routing Protocol로, Intra-AS(자율 시스템 내부) 라우팅에 사용된다.**
2. **OSPF는 Dijkstra’s Algorithm을 사용하여 최단 경로를 계산하며, 네트워크의 전체 맵을 유지한다.**
3. **OSPF는 Hierarchical Design(계층적 구조)을 사용하여 대규모 네트워크에서 성능을 최적화한다.**
4. **OSPF는 RIP보다 빠른 수렴 속도와 높은 확장성을 제공하며, 대규모 네트워크에서 선호된다.**

🚀 **한 문장 요약:**  
**OSPF는 Link-State Routing을 기반으로 Dijkstra 알고리즘을 사용하여 최적 경로를 계산하며, 계층적 설계를 통해 대규모 네트워크에서도 효율적으로 동작하는 Intra-AS 라우팅 프로토콜이다.**