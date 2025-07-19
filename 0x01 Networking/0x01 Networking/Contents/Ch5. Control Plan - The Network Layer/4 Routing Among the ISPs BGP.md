[[The Network Layer – Control Plane]]


#### **요약 (Summary)**

**BGP(Border Gateway Protocol)**는 **인터넷에서 Autonomous System(AS) 간 라우팅을 담당하는 프로토콜**이다.  
각 AS(자율 시스템)는 서로 **BGP를 통해 네트워크 경로 정보를 교환**하며, 이를 통해 **인터넷 전반의 라우팅이 가능**해진다.  
BGP는 **Path Vector Routing Algorithm(경로 벡터 라우팅 알고리즘)**을 기반으로 동작하며,  
**정책 기반 라우팅(Policy-Based Routing)**을 통해 단순한 최단 거리보다 다양한 경로 선택 기준을 적용할 수 있다.

---

## **5.4.1 The Role of BGP in the Internet (BGP의 역할)**

### **설명 (Explanation)**

BGP는 **인터넷의 "Glue" 역할을 하며, 여러 ISP와 네트워크를 연결하는 핵심 프로토콜**이다.

- **Intra-AS Routing (AS 내부 라우팅, IGP)** → OSPF, RIP, IS-IS 사용
- **Inter-AS Routing (AS 간 라우팅, EGP)** → **BGP 사용**

### **1️⃣ BGP의 주요 역할**

|역할|설명|
|---|---|
|**Inter-AS Routing (AS 간 라우팅)**|인터넷에서 서로 다른 AS 간 경로를 설정|
|**Scalability (확장성 지원)**|수십만 개의 네트워크를 연결할 수 있도록 설계|
|**Policy-Based Routing (정책 기반 라우팅)**|단순한 최단 경로가 아닌, 정책(비용, 신뢰도, 계약 등)에 따라 경로 선택 가능|

##### **💡 Real-Life Example (실생활 예시)**

> **BGP는 국제 항공 노선과 유사하다.**
> 
> - 각 항공사는 서로 계약(AS 간 정책)하여 최적의 노선을 결정하며,
> - 단순히 최단 거리보다는 비용, 연료 효율성, 수익성 등을 고려하여 경로를 선택.

---

## **5.4.2 BGP Peering and AS Relationships (BGP 피어링 및 AS 관계)**

### **설명 (Explanation)**

BGP를 통해 **각 AS는 BGP 피어링(Peering)을 형성하여 네트워크 정보를 교환**한다.  
AS 간 관계는 **Tier 구조**를 가지며, **Transit, Peering, Customer 관계**로 나뉜다.

### **1️⃣ AS 구조 (Autonomous System 구조)**

|Tier|설명|
|---|---|
|**Tier 1 ISP**|글로벌 ISP (예: AT&T, NTT, Level 3) – 돈을 지불하지 않고 연결 가능|
|**Tier 2 ISP**|지역 ISP – Tier 1에 비용을 지불하고 연결됨|
|**Tier 3 ISP**|소규모 ISP – 주로 최종 사용자에게 인터넷 서비스 제공|

### **2️⃣ AS 간 관계 (AS Relationships in BGP)**

|관계|설명|
|---|---|
|**Provider-Customer (공급자-고객)**|고객(소규모 ISP)이 상위 ISP(Provider)에게 비용을 지불하고 인터넷 연결 제공받음|
|**Peer-to-Peer (동등 피어링)**|두 개의 AS가 **상호 비용 없이** 트래픽을 교환 (예: 두 대형 ISP 간)|
|**Sibling Relationship (형제 관계)**|동일한 회사 또는 조직 내 AS 간 트래픽 교환|

##### **💡 Real-Life Example (실생활 예시)**

> - **Provider-Customer 관계** = 지역 상점(고객)이 도매 공급업체(Provider)에서 제품을 구매하는 것
> - **Peer-to-Peer 관계** = 두 개의 경쟁 상점이 특정 제품을 서로 교환하는 것

---

## **5.4.3 BGP Route Selection Process (BGP 경로 선택 과정)**

### **설명 (Explanation)**

BGP는 **Path Vector Routing Algorithm(경로 벡터 라우팅 알고리즘)**을 기반으로 동작하며,  
각 경로는 **AS-PATH(AS 경로), NEXT-HOP(다음 홉), LOCAL PREFERENCE(지역 우선순위)** 등의 속성을 통해 결정된다.

### **1️⃣ BGP Route Attributes (BGP 경로 속성)**

|속성|설명|
|---|---|
|**AS-PATH**|목적지까지 거치는 AS 리스트 (길이가 짧을수록 선호됨)|
|**NEXT-HOP**|다음 목적지 IP 주소 (패킷이 전달될 라우터)|
|**LOCAL PREFERENCE**|AS 내부에서 우선적으로 사용해야 하는 경로|
|**MED (Multi-Exit Discriminator)**|동일한 목적지가 여러 경로를 가질 경우 우선순위 결정|
|**COMMUNITY**|특정 경로를 그룹화하여 정책 적용 가능|

### **2️⃣ BGP Route Selection 순서**

1. **LOCAL PREFERENCE (가장 높은 값 우선)**
2. **AS-PATH (가장 짧은 경로 우선)**
3. **ORIGIN TYPE (IGP > EGP > Unknown 순)**
4. **MED (값이 낮을수록 우선)**
5. **NEXT-HOP Reachability 확인**

##### **💡 Real-Life Example (실생활 예시)**

> **BGP 경로 선택은 여행자가 항공편을 예약하는 과정과 비슷하다.**
> 
> - 최단 경로(AS-PATH)를 고려하지만,
> - 티켓 가격(LOCAL PREFERENCE), 경유지(AS-PATH), 항공사 신뢰도(ORIGIN TYPE) 등을 종합적으로 판단하여 결정.

---

## **5.4.4 BGP Messages (BGP 메시지 타입)**

### **설명 (Explanation)**

BGP 피어링(Peering)을 형성하고 네트워크 정보를 교환하기 위해 **4가지 BGP 메시지**가 사용된다.

|메시지 타입|설명|
|---|---|
|**OPEN**|BGP 피어링을 설정하는 초기 메시지|
|**UPDATE**|새로운 경로나 변경된 경로를 알림|
|**KEEPALIVE**|BGP 연결이 유지되고 있음을 확인|
|**NOTIFICATION**|오류 발생 시 연결 종료|

##### **💡 Real-Life Example (실생활 예시)**

> - **OPEN = 새로운 비즈니스 파트너십 제안**
> - **UPDATE = 계약 내용 변경**
> - **KEEPALIVE = 계약 유지 확인**
> - **NOTIFICATION = 계약 위반 시 종료**

---

## **5.4.5 BGP Convergence and Challenges (BGP 수렴 및 문제점)**

### **설명 (Explanation)**

BGP는 네트워크 경로를 동적으로 변경할 수 있지만,  
**수렴 속도(Convergence Time) 문제와 보안(Security) 취약점이 존재**한다.

### **1️⃣ BGP Convergence (BGP 수렴 문제)**

- **BGP는 변화가 발생하면 새로운 경로를 찾기까지 시간이 오래 걸림**
- **대규모 네트워크에서 라우팅 테이블이 크기 때문에, 업데이트 속도가 느려질 수 있음**

### **2️⃣ BGP Security Risks (BGP 보안 문제)**

|보안 위협|설명|
|---|---|
|**BGP Hijacking (BGP 하이재킹)**|악의적인 AS가 잘못된 경로 정보를 광고하여 트래픽을 가로챔|
|**Route Leaks (경로 유출)**|내부 네트워크 경로가 외부 AS로 유출되어 트래픽이 잘못 전달됨|
|**Prefix Hijacking (프리픽스 하이재킹)**|공격자가 자신을 다른 네트워크의 소유자로 위장하여 트래픽을 조작|

##### **💡 Real-Life Example (실생활 예시)**

> **BGP 하이재킹은 교통 표지판이 잘못된 방향을 가리켜 운전자들이 엉뚱한 길로 가게 만드는 것과 같다.**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **BGP(Border Gateway Protocol)는 ISP 간 경로를 설정하는 인터넷의 핵심 프로토콜이다.**
2. **BGP는 Path Vector Routing Algorithm을 사용하며, 정책 기반 라우팅을 지원한다.**
3. **BGP의 주요 속성(AS-PATH, NEXT-HOP, LOCAL PREFERENCE 등)을 기반으로 최적 경로를 선택한다.**
4. **BGP 보안 문제(BGP Hijacking, Route Leaks 등)는 심각한 인터넷 위협이 될 수 있다.**

🚀 **한 문장 요약:**  
**BGP는 인터넷에서 AS 간 경로를 설정하는 핵심 프로토콜로, 정책 기반 라우팅을 통해 최적 경로를 결정하며, 보안 문제를 고려해야 한다.**