[[The Link Layer and LANs]]


#### **요약 (Summary)**

네트워크에서 **Multiple Access Links(다중 접속 링크)**는 **여러 장치가 동일한 통신 매체를 공유하는 방식**을 의미한다.  
이때 **누가, 언제 데이터를 전송할 것인지 조정하는 역할**을 하는 것이 **Multiple Access Protocols(다중 접속 프로토콜)**이다.  
이 프로토콜은 **Collision(충돌)을 방지하고, 효율적으로 데이터 전송을 조절하는 기법**을 제공한다.  
주요 프로토콜에는 **Channel Partitioning(채널 분할), Random Access(경쟁 기반), Taking Turns(순차적 접근)** 방식이 있다.

---

## **6.3.1 Multiple Access Links (다중 접속 링크의 종류)**

### **설명 (Explanation)**

네트워크 링크는 **Point-to-Point(점대점 연결)**과 **Broadcast(공유 매체 연결)**로 구분된다.

### **1️⃣ Point-to-Point Links (점대점 링크)**

- **두 개의 장치가 직접 연결된 형태**.
- **데이터 전송 시 충돌(Collision)이 발생하지 않음**.
- **예:** **직렬 연결, 광섬유 링크, PPP(Point-to-Point Protocol) 연결**.

### **2️⃣ Broadcast Links (브로드캐스트 링크, 공유 매체 연결)**

- **여러 장치가 하나의 공통 매체(예: 무선 네트워크, 이더넷)를 공유**.
- **한 장치가 전송할 때, 다른 장치는 이를 수신할 수 있음**.
- **Collision(충돌) 문제 해결을 위해 Multiple Access Protocol이 필요함**.
- **예:** **Wi-Fi, Ethernet, 위성 네트워크**.

#### **📌 Point-to-Point vs. Broadcast Links 비교**

|구분|Point-to-Point|Broadcast|
|---|---|---|
|**연결 방식**|1:1 (두 장치 간 연결)|1:N (여러 장치가 공유)|
|**충돌 가능성**|없음|있음 (충돌 회피 필요)|
|**예제**|광섬유 연결, PPP|Ethernet, Wi-Fi|

##### **💡 Real-Life Example (실생활 예시)**

> - **Point-to-Point = 두 사람이 전화로 직접 대화하는 것**
> - **Broadcast = 무전기로 여러 사람이 같은 채널을 공유하는 것**

---

## **6.3.2 Multiple Access Protocols (다중 접속 프로토콜)**

### **설명 (Explanation)**

다중 접속 링크에서 **Collision(충돌) 문제를 해결하고, 네트워크 효율을 높이기 위해 다양한 프로토콜이 사용됨**.

### **1️⃣ Channel Partitioning (채널 분할 방식 – 정적 분할 기법)**

- **주어진 대역폭을 여러 사용자에게 나누어 사용하도록 함**.
- **사용자가 많을수록 비효율적일 수 있음**.

#### **📌 주요 Channel Partitioning 기법**

|기법|설명|예제|
|---|---|---|
|**FDMA (Frequency Division Multiple Access)**|주파수 대역을 나누어 각 사용자에게 할당|AM/FM 라디오|
|**TDMA (Time Division Multiple Access)**|시간 슬롯을 나누어 각 사용자에게 할당|2G GSM 통신|
|**CDMA (Code Division Multiple Access)**|각 사용자가 고유한 코드로 데이터를 구분|3G 모바일 네트워크|

##### **💡 Real-Life Example (실생활 예시)**

> - **FDMA = 여러 개의 라디오 방송국이 다른 주파수를 사용하는 것**
> - **TDMA = 전화 회선이 시간 단위로 나뉘어 여러 통화를 처리하는 것**

---

### **2️⃣ Random Access Protocols (경쟁 기반 프로토콜 – 충돌 허용 방식)**

- **장치가 필요할 때 데이터를 전송하되, 충돌이 발생하면 이를 해결하는 방식**.
- **네트워크 부하가 낮을 때는 효율적이지만, 사용자가 많아지면 충돌이 증가하여 성능 저하 가능**.

#### **📌 주요 Random Access 기법**

|기법|설명|예제|
|---|---|---|
|**ALOHA**|단순한 충돌 해결 방식 (송신 후 응답이 없으면 재전송)|초기 위성통신|
|**Slotted ALOHA**|시간 슬롯을 활용하여 충돌을 줄이는 방식|위성 및 RFID 시스템|
|**CSMA/CD (Carrier Sense Multiple Access with Collision Detection)**|전송 전 채널을 감지하고, 충돌 발생 시 재전송 (Ethernet 사용)|유선 LAN (Ethernet)|
|**CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance)**|충돌을 미리 회피하는 방식 (Wi-Fi 사용)|Wi-Fi (802.11)|

##### **💡 Real-Life Example (실생활 예시)**

> - **ALOHA = 사람들이 동시에 말하면 충돌이 발생하는 것과 같음 (누군가 말하기를 기다리지 않음)**
> - **CSMA/CD = 사람들이 말하기 전에 방이 조용한지 확인하고, 충돌이 발생하면 다시 시도하는 것**
> - **CSMA/CA = 손을 들어 발언 기회를 요청하는 것 (Wi-Fi의 충돌 방지 방식과 유사함)**

---

### **3️⃣ Taking Turns Protocols (순차적 접근 방식 – 충돌 방지 방식)**

- **모든 장치가 순서를 정하고, 정해진 시간 동안만 전송 가능하도록 함**.
- **경쟁이 없으므로 충돌이 발생하지 않음**.
- **사용자가 많을 경우, 대기 시간이 길어질 수 있음**.

#### **📌 주요 Taking Turns 기법**

|기법|설명|예제|
|---|---|---|
|**Polling (폴링 방식)**|중앙 컨트롤러가 각 장치에게 차례로 전송 기회를 제공|블루투스, 공항 관제 시스템|
|**Token Passing (토큰 방식)**|전송 권한을 가진 "토큰"이 네트워크를 순환하며 데이터 전송 허용|Token Ring 네트워크|

##### **💡 Real-Life Example (실생활 예시)**

> - **Polling = 선생님이 학생을 차례로 지목하여 발표시키는 방식**
> - **Token Passing = 회의 중 발언권을 가진 사람이 말하고, 끝나면 다음 사람에게 발언권(토큰)을 전달하는 것**

---

## **6.3.3 Comparison of Multiple Access Protocols (다중 접속 프로토콜 비교)**

|기법|충돌 발생 가능성|장점|단점|사용 예제|
|---|---|---|---|---|
|**Channel Partitioning**|없음|안정적인 대역폭 제공|사용자가 적으면 비효율적|FDMA, TDMA, CDMA|
|**Random Access**|있음|낮은 부하에서 높은 효율|충돌 발생 시 성능 저하|Ethernet (CSMA/CD), Wi-Fi (CSMA/CA)|
|**Taking Turns**|없음|충돌 방지, 네트워크 안정성 높음|사용자가 많으면 대기 시간 증가|Bluetooth (Polling), Token Ring|

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Multiple Access Links(다중 접속 링크)는 여러 장치가 동일한 네트워크 매체를 공유하는 환경에서 데이터를 전송하는 방식이다.**
2. **Multiple Access Protocols(다중 접속 프로토콜)은 충돌을 방지하고 네트워크 효율을 높이기 위해 사용된다.**
3. **Channel Partitioning(채널 분할), Random Access(경쟁 기반), Taking Turns(순차적 접근) 방식이 있으며, 각각의 방식이 특정 네트워크 환경에 적합하다.**
4. **Ethernet은 CSMA/CD 방식을, Wi-Fi는 CSMA/CA 방식을 사용하여 충돌을 감지하거나 방지한다.**

🚀 **한 문장 요약:**  
**다중 접속 프로토콜은 여러 장치가 동일한 네트워크를 공유할 때 충돌을 방지하고 데이터를 효율적으로 전송하는 방법을 제공하며, Ethernet(유선)과 Wi-Fi(무선)에서 각각 CSMA/CD, CSMA/CA 방식을 사용한다.**