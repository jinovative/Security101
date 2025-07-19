[[The Network Layer – Control Plane]]


#### **요약 (Summary)**

**Routing Algorithm(라우팅 알고리즘)**은 **네트워크에서 최적의 경로를 찾는 방법**을 결정하는 알고리즘이다.  
라우팅 알고리즘은 **Static Routing(정적 라우팅)** 과 **Dynamic Routing(동적 라우팅)** 으로 나뉘며,  
Dynamic Routing은 다시 **Distance Vector Routing(거리 벡터 라우팅)** 과 **Link State Routing(링크 상태 라우팅)** 으로 구분된다.

---

## **5.2.1 Classification of Routing Algorithms (라우팅 알고리즘의 분류)**

### **설명 (Explanation)**

라우팅 알고리즘은 크게 **Static Routing(정적 라우팅)**과 **Dynamic Routing(동적 라우팅)**으로 나뉜다.

### **1️⃣ Static Routing (정적 라우팅)**

- **관리자가 수동으로 경로를 설정**.
- 라우팅 테이블이 **고정되어 변경되지 않음**.
- **소규모 네트워크에서 사용됨** (예: 기업 내부망).

### **2️⃣ Dynamic Routing (동적 라우팅)**

- **네트워크 상태 변화에 따라 자동으로 경로를 변경**.
- 라우팅 프로토콜을 사용하여 **최적 경로를 실시간으로 업데이트**.
- **대규모 네트워크(인터넷, ISP)에서 필수적**.
- Dynamic Routing은 **Distance Vector Routing과 Link State Routing**으로 나뉜다.

#### **📌 Static vs. Dynamic Routing 비교**

| 구분        | Static Routing | Dynamic Routing |
| --------- | -------------- | --------------- |
| **경로 변경** | 수동 설정 (고정됨)    | 자동 업데이트         |
| **확장성**   | 소규모 네트워크 적합    | 대규모 네트워크 적합     |
| **관리 부담** | 높음 (수동 관리)     | 낮음 (자동 조정)      |

##### **💡 Real-Life Example (실생활 예시)**

> - **Static Routing = 미리 정해진 출퇴근 경로 (고정된 네비게이션 경로)**
> - **Dynamic Routing = 교통 상황에 따라 자동으로 변경되는 네비게이션**

---

## **5.2.2 Distance Vector Routing (거리 벡터 라우팅)**

### **설명 (Explanation)**

**Distance Vector Routing(거리 벡터 라우팅)**은 **인접 라우터와 거리 정보를 공유하여 최적의 경로를 찾는 방식**이다.

- **각 라우터는 인접 라우터와 "도달 거리(distance)" 정보를 주고받으며 라우팅 테이블을 업데이트**.
- **Bellman-Ford Algorithm(벨만-포드 알고리즘)**을 사용하여 경로를 계산.

### **1️⃣ Distance Vector Routing 동작 방식**

1. **각 라우터는 자신이 알고 있는 목적지까지의 거리 정보를 인접 라우터와 교환**.
2. **라우터는 받은 정보를 바탕으로 최단 경로를 업데이트**.
3. **네트워크 변화가 감지되면 일정 주기마다 라우팅 정보를 갱신**.

### **2️⃣ Distance Vector Routing의 주요 특징**

- **네트워크 전체를 알지 못하고, 인접 라우터와 거리 정보만 공유**.
- **Hop Count(홉 수, 목적지까지 거쳐야 하는 라우터 개수)를 기반으로 최적 경로 선택**.
- **RIP(Routing Information Protocol)**이 대표적인 Distance Vector 라우팅 프로토콜.

#### **📌 Distance Vector Routing의 장점과 단점**

|구분|장점|단점|
|---|---|---|
|**장점**|구현이 간단하고 설정이 쉬움|경로 수렴 속도가 느림 (네트워크 변화 반영이 느림)|
|**단점**|대규모 네트워크에 비효율적|루핑(Looping) 문제 발생 가능|

##### **💡 Real-Life Example (실생활 예시)**

> **거리 벡터 라우팅은 친구들에게 목적지를 물어보면서 길을 찾는 것과 같다.**
> 
> - 친구(인접 라우터)에게 "어느 방향으로 가야 해?"라고 물어봄.
> - 각 친구는 자신이 알고 있는 최적 경로를 알려줌.
> - 여러 번 질문을 반복하면서 목적지까지 가는 최단 경로를 결정.

---

## **5.2.3 Link State Routing (링크 상태 라우팅)**

### **설명 (Explanation)**

**Link State Routing(링크 상태 라우팅)**은 **네트워크 전체 지도를 생성하여 최적의 경로를 찾는 방식**이다.

- **각 라우터는 전체 네트워크의 링크 정보를 수집하고 공유**.
- **Dijkstra’s Algorithm(다익스트라 알고리즘)**을 사용하여 최단 경로를 계산.

### **1️⃣ Link State Routing 동작 방식**

1. **각 라우터는 자신의 연결된 링크 정보를 수집하고 이를 네트워크 전체에 브로드캐스트(LSA, Link State Advertisement)로 전송**.
2. **모든 라우터는 받은 정보를 바탕으로 네트워크의 전체 맵을 구성**.
3. **Dijkstra 알고리즘을 사용하여 최적 경로를 계산**.

### **2️⃣ Link State Routing의 주요 특징**

- **네트워크의 전체 구조를 파악할 수 있음**.
- **라우터 간 변화가 빠르게 반영되므로, Distance Vector 방식보다 빠르게 수렴 가능**.
- **OSPF(Open Shortest Path First)**가 대표적인 Link State 라우팅 프로토콜.

#### **📌 Link State Routing의 장점과 단점**

|구분|장점|단점|
|---|---|---|
|**장점**|빠른 경로 수렴 속도|계산량이 많아 라우터 리소스 사용 증가|
|**단점**|대규모 네트워크에 적합|설정이 복잡하고 초기 비용이 큼|

##### **💡 Real-Life Example (실생활 예시)**

> **링크 상태 라우팅은 GPS 네비게이션이 실시간 교통 정보를 반영하여 최적 경로를 찾는 것과 같다.**
> 
> - 도로(네트워크 링크) 상태를 지속적으로 업데이트.
> - 교통 정체가 발생하면 다른 최적 경로를 즉시 탐색.

---

## **5.2.4 Comparison: Distance Vector vs. Link State Routing (거리 벡터 vs. 링크 상태 라우팅 비교)**

### **설명 (Explanation)**

Distance Vector 방식과 Link State 방식은 **각각의 장단점이 있으며, 네트워크 환경에 따라 선택된다**.

#### **📌 Distance Vector vs. Link State Routing 비교**

|구분|Distance Vector (거리 벡터)|Link State (링크 상태)|
|---|---|---|
|**경로 계산 방식**|인접 라우터와 거리 정보 공유|전체 네트워크 구조를 기반으로 계산|
|**사용 알고리즘**|Bellman-Ford Algorithm|Dijkstra’s Algorithm|
|**대표 프로토콜**|RIP|OSPF|
|**장점**|구현이 간단함|빠른 경로 수렴 및 높은 확장성|
|**단점**|경로 수렴 속도가 느림|계산량이 많고 초기 설정이 복잡|

##### **💡 Real-Life Example (실생활 예시)**

> - **Distance Vector Routing = 친구들에게 물어보며 목적지를 찾는 방식**
> - **Link State Routing = 네비게이션을 이용해 목적지를 찾는 방식**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Routing Algorithm(라우팅 알고리즘)은 네트워크에서 최적 경로를 찾는 방법을 결정한다.**
2. **Static Routing(정적 라우팅)은 고정된 경로를 사용하며, Dynamic Routing(동적 라우팅)은 자동으로 경로를 변경한다.**
3. **Distance Vector Routing은 인접 라우터와 거리 정보를 공유하여 경로를 결정하며, RIP 프로토콜이 대표적이다.**
4. **Link State Routing은 네트워크 전체 정보를 기반으로 최적 경로를 계산하며, OSPF 프로토콜이 대표적이다.**
5. **Link State 방식이 Distance Vector 방식보다 빠르고 효율적이지만, 더 많은 리소스를 사용한다.**

🚀 **한 문장 요약:**  
**라우팅 알고리즘은 네트워크에서 최적의 경로를 찾는 방법을 결정하며, Distance Vector(RIP)와 Link State(OSPF) 방식이 대표적으로 사용된다.**