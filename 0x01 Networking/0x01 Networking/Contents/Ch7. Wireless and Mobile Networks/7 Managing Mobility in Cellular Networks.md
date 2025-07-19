[[Wireless and Mobile Networks]]


#### **요약 (Summary)**

**Managing Mobility in Cellular Networks(셀룰러 네트워크에서의 이동성 관리)**는 **사용자가 이동하면서도 네트워크 연결을 유지할 수 있도록 하는 기술과 프로세스**를 의미한다.  
핵심 요소로는 **Handoff(핸드오프), Location Management(위치 관리), Roaming(로밍)** 등이 있으며,  
이를 통해 **통화, 데이터 세션, 스트리밍 등 다양한 서비스가 이동 중에도 끊김 없이 지속될 수 있도록 보장**한다.

---

## **7.7.1 Mobility Management in Cellular Networks (셀룰러 네트워크에서의 이동성 관리 개념)**

### **설명 (Explanation)**

셀룰러 네트워크는 **Base Station(기지국), Mobile Switching Center(MSC), Packet Core Network** 등을 활용하여  
사용자가 이동하더라도 네트워크 연결을 유지할 수 있도록 관리한다.

### **1️⃣ Mobility Management의 주요 목표 (Key Goals of Mobility Management)**

|목표|설명|
|---|---|
|**Seamless Handoff (끊김 없는 핸드오프)**|사용자가 이동할 때 네트워크 연결 유지|
|**Efficient Location Management (효율적인 위치 관리)**|사용자 위치를 지속적으로 업데이트하여 트래픽 최적화|
|**Optimized Roaming (최적화된 로밍 서비스)**|네트워크 간 이동 시 서비스 연속성 제공|
|**Power Efficiency (전력 효율성 최적화)**|모바일 장치의 배터리 소모 최소화|

📌 **핵심 개념**

- **Handoff** → 기지국 간 연결 전환
- **Location Update** → 사용자의 위치 변경 시 네트워크에 알림
- **Roaming** → 사용자가 홈 네트워크를 벗어나 다른 네트워크에서 서비스 이용

##### **💡 Real-Life Example (실생활 예시)**

> - **고속열차에서 이동 중에도 LTE/5G 네트워크가 유지되는 것**
> - **해외여행 중에도 로밍을 통해 기존 번호로 통화할 수 있는 것**

---

## **7.7.2 Handoff in Cellular Networks (핸드오프: 기지국 간 전환 기술)**

### **설명 (Explanation)**

핸드오프(Handoff)는 **사용자가 한 기지국(Cell)에서 다른 기지국으로 이동할 때 네트워크 연결을 유지하는 과정**이다.  
핸드오프는 **데이터 손실 없이 네트워크를 전환하는 것이 핵심**이다.

### **1️⃣ Handoff의 유형 (Types of Handoff in Cellular Networks)**

|핸드오프 유형|설명|적용 기술|
|---|---|---|
|**Hard Handoff (하드 핸드오프)**|기존 연결을 끊고 새로운 연결을 설정|LTE, 5G NSA|
|**Soft Handoff (소프트 핸드오프)**|기존 연결을 유지하면서 새로운 연결을 설정|3G CDMA|
|**Horizontal Handoff (수평 핸드오프)**|동일한 기술 내에서 핸드오프 수행|LTE → LTE|
|**Vertical Handoff (수직 핸드오프)**|서로 다른 네트워크 기술 간 핸드오프 수행|Wi-Fi → LTE, LTE → 5G|

📌 **핸드오프 예제**

- **Hard Handoff → LTE 기지국 간 이동 시 순간적인 연결 끊김 가능**
- **Soft Handoff → 3G CDMA에서 여러 개의 기지국과 연결을 유지하면서 핸드오프 수행**
- **Vertical Handoff → Wi-Fi 신호가 약해지면 LTE로 자동 전환**

##### **💡 Real-Life Example (실생활 예시)**

> - **Wi-Fi가 약해지면 LTE로 전환되는 것 (Vertical Handoff)**
> - **고속도로에서 이동 중에도 통화가 끊기지 않는 것 (Soft Handoff)**

---

## **7.7.3 Location Management (위치 관리: 사용자 위치 추적 기술)**

### **설명 (Explanation)**

Location Management(위치 관리)는 **사용자가 이동할 때 네트워크가 현재 위치를 추적하고, 서비스 제공을 최적화하는 과정**이다.

### **1️⃣ 위치 관리 프로세스 (Location Management Process)**

|과정|설명|
|---|---|
|**Location Registration (위치 등록)**|사용자가 새로운 지역(셀)에 들어가면 네트워크에 등록|
|**Location Update (위치 갱신)**|사용자가 이동할 때 네트워크가 위치 정보를 지속적으로 업데이트|
|**Paging (페이징)**|네트워크가 사용자의 현재 위치를 찾기 위해 신호 전송|

📌 **위치 관리 예제**

- **휴대전화가 새로운 기지국에 연결되면 네트워크가 자동으로 위치 등록 수행**
- **전화 수신 시 네트워크가 사용자의 현재 위치를 검색(Paging)하여 연결**

##### **💡 Real-Life Example (실생활 예시)**

> - **비행기에서 착륙 후 전원을 켜면 네트워크가 자동으로 위치를 업데이트하는 것 (Location Update).**
> - **새로운 도시에 도착했을 때 모바일 데이터가 자동으로 연결되는 것 (Location Registration).**

---

## **7.7.4 Roaming in Cellular Networks (셀룰러 네트워크에서의 로밍)**

### **설명 (Explanation)**

**Roaming(로밍)**은 **사용자가 홈 네트워크를 벗어나 다른 네트워크에서 모바일 서비스를 이용할 수 있도록 지원하는 기능**이다.

### **1️⃣ 로밍의 종류 (Types of Roaming in Cellular Networks)**

|로밍 유형|설명|
|---|---|
|**National Roaming (국내 로밍)**|같은 국가 내에서 다른 이동통신사의 네트워크를 이용|
|**International Roaming (국제 로밍)**|해외에서 다른 이동통신사의 네트워크를 이용|
|**Inter-Standard Roaming (이종 네트워크 간 로밍)**|LTE → 5G 같은 서로 다른 네트워크 기술 간 전환|

📌 **로밍 과정 예제**

- **사용자가 해외로 이동하면 자동으로 현지 이동통신사의 네트워크와 연결**
- **국내에서도 특정 지역에서 다른 통신사의 네트워크를 사용할 수 있음**

##### **💡 Real-Life Example (실생활 예시)**

> - **해외 여행 중에도 기존 번호로 전화와 데이터를 사용할 수 있는 것 (International Roaming).**
> - **국내에서 특정 지역(산간, 도서지역)에서 다른 통신사의 네트워크를 사용하는 것 (National Roaming).**

---

## **7.7.5 Mobility Management in 5G (5G에서의 이동성 관리)**

### **설명 (Explanation)**

5G 네트워크에서는 **기존 LTE보다 더 향상된 이동성 관리 기능을 제공**하며, 특히 **초고속, 초저지연 연결을 위한 새로운 기술이 도입됨**.

### **1️⃣ 5G Mobility Management의 주요 기술**

|5G 기술|설명|
|---|---|
|**Make-Before-Break (MBB) Handoff**|새로운 네트워크에 먼저 연결한 후 기존 연결을 해제 (연결 끊김 최소화)|
|**Multi-Connectivity (다중 연결 지원)**|5G와 LTE, Wi-Fi를 동시에 사용할 수 있음|
|**Network Slicing (네트워크 슬라이싱)**|애플리케이션별 맞춤형 네트워크 제공|

📌 **5G 네트워크에서의 이동성 예제**

- **5G 기지국 간 이동 시 Make-Before-Break 방식으로 핸드오프 수행**
- **스트리밍 서비스가 5G, LTE, Wi-Fi를 동시에 사용하여 끊김 없이 재생**

##### **💡 Real-Life Example (실생활 예시)**

> - **5G가 지원되는 스마트폰에서 LTE, Wi-Fi를 동시에 연결하여 최적의 속도를 유지하는 것 (Multi-Connectivity).**
> - **자율주행차가 네트워크 연결을 유지하면서 초저지연 통신을 수행하는 것 (5G Network Slicing).**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Mobility Management(이동성 관리)는 셀룰러 네트워크에서 핸드오프, 위치 관리, 로밍을 통해 사용자의 원활한 네트워크 연결을 유지하는 기술이다.**
2. **핸드오프(Handoff)는 사용자가 이동할 때 네트워크 연결을 유지하는 기술이며, Hard Handoff, Soft Handoff, Vertical Handoff 등이 있다.**
3. **위치 관리(Location Management)는 네트워크가 사용자의 위치를 추적하여 트래픽을 최적화하는 과정이다.**
4. **5G에서는 Multi-Connectivity, Network Slicing 등의 새로운 기술을 활용하여 이동성 관리를 최적화한다.**

🚀 **한 문장 요약:**  
**5G 및 셀룰러 네트워크에서의 이동성 관리는 핸드오프, 위치 관리, 로밍 기술을 통해 원활한 연결을 보장하며, 5G에서는 Multi-Connectivity와 Network Slicing을 통해 더욱 최적화되고 있다.**
