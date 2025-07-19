[[Wireless and Mobile Networks]]

#### **요약 (Summary)**

**Cellular Internet Access(셀룰러 인터넷 액세스)**는 **이동통신 네트워크(3G, 4G LTE, 5G)를 통해 인터넷에 연결하는 방식**이다.  
이는 **기지국(Base Station)**을 통해 무선으로 데이터를 송수신하며, 사용자가 이동 중에도 네트워크 연결을 유지할 수 있도록 지원한다.  
셀룰러 네트워크는 **광범위한 커버리지, 핸드오프(Handoff), QoS(Quality of Service) 보장** 등의 특성을 가지며,  
주요 아키텍처는 **셀 구조(Cellular Structure), 모바일 네트워크 코어(Mobile Core Network), 핸드오프 기술**로 구성된다.

---

## **7.4.1 Cellular Network Architecture (셀룰러 네트워크 아키텍처)**

### **설명 (Explanation)**

셀룰러 네트워크는 **기지국과 코어 네트워크(Core Network)를 기반으로 동작하며, 사용자가 이동하면서도 안정적인 연결을 유지할 수 있도록 설계됨**.

### **1️⃣ 주요 구성 요소 (Key Components of Cellular Network)**

|구성 요소|역할|
|---|---|
|**Mobile Device (모바일 장치)**|스마트폰, 태블릿, IoT 기기 등 네트워크에 연결하는 장치|
|**Base Station (기지국, BTS, eNodeB, gNodeB)**|모바일 장치와 무선으로 연결되는 네트워크 노드|
|**Mobile Switching Center (MSC, 이동 교환국)**|음성 및 데이터 트래픽을 관리하고 핸드오프를 수행|
|**Packet Core Network (패킷 코어 네트워크, EPC/5GC)**|인터넷과 연결되며 데이터 트래픽을 처리|
|**Home Location Register (HLR) / Subscriber Database**|가입자의 정보 및 인증 관리|

📌 **셀룰러 네트워크 예제**

scss

CopyEdit

`사용자 → 기지국(Base Station) → 코어 네트워크(EPC/5GC) → 인터넷`

→ **이 구조를 통해 사용자는 이동하면서도 인터넷 연결을 유지할 수 있음**.

##### **💡 Real-Life Example (실생활 예시)**

> - **셀룰러 네트워크는 기차에서 이동 중에도 LTE/5G를 통해 인터넷을 사용할 수 있는 것과 같다.**
> - **Wi-Fi와 달리 하나의 기지국에 연결되는 것이 아니라, 사용자의 위치에 따라 기지국이 바뀌어도 연결이 유지됨.**

---

## **7.4.2 Cellular Network Technologies (셀룰러 네트워크 기술: 3G, 4G, 5G)**

### **설명 (Explanation)**

셀룰러 네트워크는 세대별(Generation)로 발전해왔으며, **각 세대는 속도, 대역폭, 기술적인 차이를 가짐**.

### **1️⃣ 3G, 4G LTE, 5G 네트워크 비교 (3G vs. 4G vs. 5G)**

|네트워크 세대|최대 속도|주요 기술|특징|
|---|---|---|---|
|**3G (WCDMA, HSPA)**|수 Mbps|CDMA, UMTS|기본적인 모바일 데이터 지원|
|**4G LTE (Long Term Evolution)**|100 Mbps~1 Gbps|OFDMA, MIMO|고속 인터넷, VoLTE 지원|
|**5G (NR, New Radio)**|10 Gbps 이상|mmWave, Massive MIMO|초고속, 초저지연, IoT 최적화|

📌 **LTE vs. 5G 주요 차이점**  
✅ **5G는 mmWave(밀리미터파) 대역을 사용하여 초고속 데이터 전송 가능**  
✅ **5G는 초저지연(Low Latency) 기술을 적용하여 실시간 애플리케이션 지원**  
✅ **5G는 Massive MIMO, Beamforming을 통해 더 많은 기기를 동시에 연결 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **3G = 웹 서핑, 이메일 정도 가능한 느린 데이터 속도**
> - **4G LTE = 고속 동영상 스트리밍 가능 (유튜브, 넷플릭스 시청 가능)**
> - **5G = 초고속 다운로드, VR/AR, 자율주행차 같은 초저지연 서비스 지원**

---

## **7.4.3 Cellular Network Structure: Cells and Handoff (셀룰러 네트워크 구조: 셀과 핸드오프)**

### **설명 (Explanation)**

셀룰러 네트워크는 **Cell(셀) 구조**를 기반으로 동작하며, 사용자가 이동할 때 원활한 네트워크 연결을 유지하기 위해 **Handoff(핸드오프)** 기술이 필요함.

### **1️⃣ Cell Structure (셀 구조 및 네트워크 구성)**

- **셀(Cell)**: 하나의 기지국(Base Station)이 담당하는 커버리지 영역.
- **셀 크기**: 매크로셀(Macrocell), 마이크로셀(Microcell), 피코셀(Picocell), 펨토셀(Femtocell) 등으로 구분됨.

📌 **셀의 종류**

|셀 유형|크기|사용 사례|
|---|---|---|
|**Macrocell (매크로셀)**|수 km|도시 및 광역 네트워크|
|**Microcell (마이크로셀)**|수백 m~1 km|도심 지역, 건물 밀집 지역|
|**Picocell (피코셀)**|수십 m|대형 건물 내부 (공항, 쇼핑몰)|
|**Femtocell (펨토셀)**|10m 이하|가정 및 사무실 내부|

---

### **2️⃣ Handoff (핸드오프: 셀 간 이동 시 네트워크 연결 유지 기술)**

- 사용자가 **하나의 셀을 벗어나 다른 셀로 이동할 때 끊김 없이 네트워크 연결을 유지하는 기술**.
- **소프트 핸드오프(Soft Handoff)**: 기존 기지국과 연결을 유지한 상태에서 새로운 기지국과 연결
- **하드 핸드오프(Hard Handoff)**: 기존 연결을 끊고 새로운 기지국에 다시 연결

📌 **핸드오프 과정 예제**

css

CopyEdit

`사용자 → 기지국 A 연결 → 이동 → 기지국 B로 핸드오프 수행 → 연결 유지`

→ **사용자가 이동하면서도 인터넷 연결이 끊기지 않음**.

##### **💡 Real-Life Example (실생활 예시)**

> - **핸드오프는 운전 중 휴대전화 통화가 끊기지 않고 유지되는 것과 유사**
> - **기차를 타고 이동 중에도 LTE/5G 네트워크가 유지되는 이유가 핸드오프 기술 때문**

---

## **7.4.4 Mobile Network Core: EPC and 5GC (모바일 네트워크 코어: EPC 및 5G 코어 네트워크)**

### **설명 (Explanation)**

셀룰러 네트워크의 핵심 코어(Core Network)는 **모바일 장치가 인터넷에 연결되도록 지원하는 역할**을 한다.

### **1️⃣ LTE EPC (Evolved Packet Core, 4G 코어 네트워크)**

- **MME (Mobility Management Entity)**: 사용자 인증 및 핸드오프 관리
- **SGW (Serving Gateway)**: 기지국과 패킷 코어 네트워크 간 연결
- **PGW (Packet Data Network Gateway)**: 인터넷과 연결

### **2️⃣ 5G Core Network (5GC, 5G 코어 네트워크)**

- **5G Core는 클라우드 네이티브 구조를 적용하여, 네트워크 슬라이싱(Network Slicing) 지원**
- **초저지연 및 초고속 데이터 전송을 위한 최적화된 설계**

📌 **LTE EPC vs. 5GC 차이점**  
✅ **5GC는 가상화 기반(Core Virtualization)으로 더 유연한 네트워크 운영 가능**  
✅ **5GC는 네트워크 슬라이싱을 지원하여 다양한 서비스 맞춤 제공 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **LTE EPC = 기존의 고정된 네트워크 구조**
> - **5G Core = 클라우드 기반 유연한 네트워크 구조 (서비스별 최적화 가능)**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **셀룰러 네트워크는 기지국과 코어 네트워크를 통해 모바일 장치가 인터넷에 연결되도록 지원한다.**
2. **핸드오프 기술을 통해 사용자가 이동 중에도 네트워크 연결을 유지할 수 있다.**
3. **5G는 LTE보다 빠른 속도, 낮은 지연 시간, 더 많은 기기 동시 연결을 지원한다.**
4. **5G Core Network(5GC)는 클라우드 기반으로 가상화 및 네트워크 슬라이싱을 지원하여 유연한 운영이 가능하다.**

🚀 **한 문장 요약:**  
**셀룰러 네트워크는 기지국과 코어 네트워크를 통해 이동 중에도 끊김 없이 인터넷에 연결할 수 있도록 지원하며, 5G는 LTE보다 빠른 속도와 유연한 네트워크 구조를 제공한다.**

