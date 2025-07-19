[[Wireless and Mobile Networks]]


#### **요약 (Summary)**

**Mobility Management(모빌리티 관리)**는 **사용자가 이동하면서도 네트워크 연결을 유지할 수 있도록 지원하는 기술 및 프로세스**이다.  
모바일 네트워크에서 **핸드오프(Handoff), 로밍(Roaming), 위치 등록(Location Registration)** 등의 기능을 수행하며,  
이동 중에도 **연속적인 데이터 전송과 원활한 서비스 제공을 보장**한다.  
특히, **셀룰러 네트워크(4G LTE, 5G)와 Wi-Fi 네트워크에서 다른 방식의 모빌리티 관리가 적용**된다.

---

## **7.5.1 Mobility in Wireless Networks (무선 네트워크에서의 이동성)**

### **설명 (Explanation)**

무선 네트워크에서 **모빌리티(Mobility)**는 사용자가 **고정된 위치 없이 네트워크를 이동하면서도 연결을 유지하는 능력**을 의미한다.

### **1️⃣ Mobility의 유형 (Types of Mobility in Wireless Networks)**

|유형|설명|
|---|---|
|**Device Mobility (장치 이동성)**|사용자가 이동해도 네트워크 연결을 유지|
|**Session Mobility (세션 이동성)**|애플리케이션 세션이 끊기지 않고 유지됨|
|**Service Mobility (서비스 이동성)**|사용자가 네트워크를 변경해도 동일한 서비스 사용 가능|

📌 **예제**

- **Device Mobility → 스마트폰이 Wi-Fi에서 LTE로 전환될 때**
- **Session Mobility → VoIP 통화가 이동 중에도 끊기지 않는 경우**
- **Service Mobility → 같은 계정으로 다른 네트워크에서 동일한 클라우드 서비스를 이용**

##### **💡 Real-Life Example (실생활 예시)**

> - **Zoom 미팅을 하면서 LTE에서 Wi-Fi로 전환해도 끊기지 않는 것 (Session Mobility)**
> - **카페 Wi-Fi에서 집 Wi-Fi로 변경해도 넷플릭스 스트리밍이 유지되는 것 (Service Mobility)**

---

## **7.5.2 Handoff (핸드오프: 네트워크 간 전환 기술)**

### **설명 (Explanation)**

핸드오프(Handoff)는 **사용자가 하나의 기지국을 벗어나 다른 기지국으로 이동할 때 네트워크 연결을 유지하는 과정**이다.  
이 과정에서 연결이 끊기지 않도록 다양한 핸드오프 기술이 적용된다.

### **1️⃣ Types of Handoff (핸드오프 유형)**

|핸드오프 유형|설명|
|---|---|
|**Hard Handoff (하드 핸드오프)**|기존 연결을 끊고 새로운 연결을 설정 (LTE, 5G NSA)|
|**Soft Handoff (소프트 핸드오프)**|새로운 연결이 설정된 후 기존 연결을 해제 (3G CDMA)|
|**Horizontal Handoff (수평 핸드오프)**|같은 네트워크 기술 내에서 기지국 변경 (Wi-Fi → Wi-Fi)|
|**Vertical Handoff (수직 핸드오프)**|서로 다른 네트워크 기술 간 변경 (Wi-Fi → LTE, LTE → 5G)|

📌 **핸드오프 예제**

- **Hard Handoff → LTE 기지국 간 이동 시 발생**
- **Soft Handoff → 3G CDMA에서 통화 중에도 다중 기지국과 연결됨**
- **Vertical Handoff → Wi-Fi에서 LTE로 변경될 때 사용됨**

##### **💡 Real-Life Example (실생활 예시)**

> - **Wi-Fi 신호가 약해지면 자동으로 LTE로 전환되는 것 (Vertical Handoff)**
> - **고속도로에서 이동 중에도 전화 통화가 끊기지 않는 것 (Soft Handoff)**

---

## **7.5.3 Location Management (위치 관리: 사용자 위치 추적 기술)**

### **설명 (Explanation)**

위치 관리는 **모바일 네트워크에서 사용자의 위치를 추적하여 서비스 제공을 최적화하는 과정**이다.  
셀룰러 네트워크에서는 **위치 등록(Location Registration)과 위치 갱신(Location Update)**을 수행한다.

### **1️⃣ 주요 위치 관리 프로세스 (Key Processes in Location Management)**

|과정|설명|
|---|---|
|**Location Registration (위치 등록)**|사용자가 새로운 지역(셀)에 진입하면 네트워크에 등록|
|**Location Update (위치 갱신)**|이동 중 사용자의 위치 정보를 지속적으로 업데이트|
|**Paging (페이징)**|네트워크가 사용자의 현재 위치를 찾기 위해 신호를 전송|

📌 **위치 관리 예제**

- **휴대전화가 새로운 기지국에 연결되면 네트워크가 자동으로 위치 등록 수행**
- **전화 수신 시 네트워크가 사용자의 현재 위치를 검색(Paging)하여 연결**

##### **💡 Real-Life Example (실생활 예시)**

> - **해외에서 로밍 시, 새로운 네트워크에 자동으로 등록되는 과정 (Location Registration)**
> - **전원이 꺼진 스마트폰을 켜면 네트워크가 현재 위치를 다시 업데이트하는 과정 (Location Update)**

---

## **7.5.4 Mobility Management in Cellular Networks (셀룰러 네트워크에서의 모빌리티 관리)**

### **설명 (Explanation)**

셀룰러 네트워크에서 모빌리티 관리는 **핸드오프, 위치 등록, 트래픽 관리 등을 수행하여 안정적인 연결을 유지**한다.  
4G LTE와 5G에서는 **모빌리티를 효율적으로 처리하기 위해 다양한 기술이 사용됨**.

### **1️⃣ LTE & 5G Mobility Management (LTE 및 5G의 모빌리티 관리 기술)**

|네트워크|주요 기술|특징|
|---|---|---|
|**LTE (4G)**|EPC (Evolved Packet Core)|핸드오프 시 IP 주소 유지 가능|
|**5G**|5GC (5G Core)|네트워크 슬라이싱(Network Slicing) 지원, 초저지연 핸드오프 가능|

📌 **5G 네트워크의 모빌리티 향상 기술**  
✅ **Make-Before-Break 방식 지원 (연결 유지 후 핸드오프 수행, 끊김 최소화)**  
✅ **Network Slicing(네트워크 슬라이싱)으로 특정 애플리케이션에 맞는 연결 제공**  
✅ **Multi-Connectivity(다중 연결) 지원 → LTE 및 Wi-Fi와 동시 연결 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **LTE는 이동 중에도 IP 주소가 유지되므로 스트리밍 동영상이 끊기지 않음.**
> - **5G는 초고속 핸드오프를 지원하여 VR/AR, 자율주행차 같은 초저지연 서비스 제공 가능.**

---

## **7.5.5 Mobility in Wi-Fi Networks (Wi-Fi 네트워크에서의 모빌리티)**

### **설명 (Explanation)**

Wi-Fi 네트워크에서도 **AP(Access Point) 간 이동 시 끊김 없는 연결을 유지하기 위한 핸드오프 기술**이 사용된다.

### **1️⃣ Wi-Fi 핸드오프 기술**

|기술|설명|
|---|---|
|**802.11r (Fast Roaming)**|AP 간 빠른 핸드오프 지원 (VoIP, 게임 등에 필수)|
|**802.11k (Radio Resource Management)**|주변 AP 정보를 제공하여 최적의 핸드오프 지원|
|**802.11v (Network-Assisted Roaming)**|네트워크가 사용자의 이동을 예측하여 AP 추천|

📌 **Wi-Fi 핸드오프 예제**

- **일반 Wi-Fi 핸드오프 → 사용자가 이동하면 새로운 AP에 연결하지만, 연결이 순간적으로 끊길 수 있음**
- **802.11r Fast Roaming → 핸드오프 시 기존 연결을 유지하며 빠르게 새로운 AP로 전환 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **호텔에서 방을 이동할 때 Wi-Fi가 끊기지 않고 자동으로 새로운 AP에 연결되는 것 (Fast Roaming).**
> - **스마트폰이 최적의 Wi-Fi 신호를 찾아 자동으로 연결을 전환하는 것 (802.11k/v).**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Mobility Management(모빌리티 관리)는 사용자가 이동하면서도 네트워크 연결을 유지할 수 있도록 지원하는 기술이다.**
2. **핸드오프(Handoff)는 사용자가 이동할 때 새로운 기지국 또는 AP에 연결하는 과정이며, Hard Handoff, Soft Handoff, Vertical Handoff 등이 있다.**
3. **셀룰러 네트워크에서는 위치 등록(Location Registration)과 페이징(Paging) 기술을 통해 사용자 위치를 추적한다.**
4. **Wi-Fi 네트워크에서는 802.11r/k/v 같은 기술을 사용하여 원활한 핸드오프를 지원한다.**

🚀 **한 문장 요약:**  
**모빌리티 관리는 셀룰러 네트워크와 Wi-Fi에서 핸드오프, 위치 등록, 네트워크 최적화를 통해 이동 중에도 원활한 연결을 유지하는 핵심 기술이다.**

