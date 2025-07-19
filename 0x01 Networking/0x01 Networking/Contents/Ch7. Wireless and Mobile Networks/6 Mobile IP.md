[[Wireless and Mobile Networks]]


#### **요약 (Summary)**

**Mobile IP**는 **사용자가 네트워크를 이동해도 기존 IP 주소를 유지하면서 인터넷 연결을 지속할 수 있도록 지원하는 프로토콜**이다.  
기존 IP 프로토콜은 **네트워크 변경 시 새로운 IP 주소를 할당받아야 하므로 세션이 끊길 위험이 있음**.  
이를 해결하기 위해 Mobile IP는 **Home Agent(HA), Foreign Agent(FA), Care-of Address(CoA)** 등의 개념을 도입하여  
사용자가 이동 중에도 원래의 IP 주소를 유지하면서 네트워크를 사용할 수 있도록 한다.

---

## **7.6.1 The Need for Mobile IP (Mobile IP가 필요한 이유)**

### **설명 (Explanation)**

기존의 인터넷 프로토콜(IP)는 **사용자의 위치가 변할 경우 새로운 네트워크에서 IP 주소를 다시 할당받아야 함**.  
하지만 이렇게 되면 **세션이 끊기고 지속적인 연결이 불가능**하기 때문에 Mobile IP가 필요함.

### **1️⃣ 기존 IP 네트워크의 문제점**

|문제점|설명|
|---|---|
|**Fixed Addressing (고정 주소 문제)**|기존 IP 주소는 네트워크를 이동하면 유지되지 않음|
|**Connection Loss (연결 끊김 문제)**|새로운 IP가 할당되면 기존 세션(예: VoIP, VPN)이 끊김|
|**Application Disruption (애플리케이션 중단 문제)**|실시간 스트리밍, 원격 접속 등의 서비스가 불안정해짐|

📌 **Mobile IP가 해결하는 문제**  
✅ **이동 중에도 원래 IP 주소 유지 가능**  
✅ **VoIP, 스트리밍, 원격 작업이 끊김 없이 유지됨**  
✅ **보안 및 인증 기능을 통해 안전한 연결 유지 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **Wi-Fi에서 LTE로 변경될 때도 VPN이 끊기지 않고 유지되는 것 (Mobile IP 기술 활용).**
> - **고속열차에서 인터넷 연결이 유지되며 화상회의가 끊기지 않는 것.**

---

## **7.6.2 Mobile IP Architecture (Mobile IP 아키텍처)**

### **설명 (Explanation)**

Mobile IP는 **사용자가 네트워크를 변경해도 기존 IP 주소를 유지할 수 있도록 여러 가지 네트워크 요소를 활용**.

### **1️⃣ 주요 구성 요소 (Key Components of Mobile IP)**

|구성 요소|설명|
|---|---|
|**Home Address (HA, 홈 주소)**|사용자의 원래 IP 주소 (고정됨)|
|**Home Agent (HA, 홈 에이전트)**|사용자의 원래 네트워크에 위치한 라우터, 패킷을 전달함|
|**Foreign Agent (FA, 외부 에이전트)**|사용자가 이동한 새로운 네트워크의 라우터|
|**Care-of Address (CoA, 임시 주소)**|사용자가 현재 접속한 네트워크에서 할당받은 임시 IP 주소|

📌 **Mobile IP 동작 방식 예제**

1. 사용자가 Home Network에 있을 때는 **Home Address(HA)를 사용**하여 인터넷에 접속.
2. 다른 네트워크(Foreign Network)로 이동하면 **Foreign Agent(FA)가 Care-of Address(CoA)를 할당**.
3. Home Agent(HA)가 패킷을 FA로 전달하고, FA는 이를 사용자에게 전달함.

##### **💡 Real-Life Example (실생활 예시)**

> - **집(Home Network)에서는 기존 인터넷 연결 사용, 출장지(Foreign Network)에서도 원래 주소(IP)로 이메일 및 웹 서비스 사용 가능.**
> - **VPN을 사용하면 현재 위치가 달라도 원래 네트워크를 통해 데이터를 주고받는 것과 유사.**

---

## **7.6.3 Mobile IP Communication Process (Mobile IP 통신 과정)**

### **설명 (Explanation)**

Mobile IP는 **사용자가 네트워크를 이동할 때도 기존 IP 주소를 유지하기 위해 터널링(Tunneling) 기법을 사용**.

### **1️⃣ Mobile IP 패킷 전달 과정 (Packet Forwarding Process in Mobile IP)**

|단계|설명|
|---|---|
|**1. Registration (등록 단계)**|사용자가 새로운 네트워크(FA)에서 Care-of Address(CoA)를 할당받음|
|**2. Tunneling (터널링 단계)**|Home Agent(HA)가 사용자의 기존 IP 주소로 온 패킷을 FA로 전달|
|**3. Data Forwarding (데이터 전달)**|FA가 사용자의 모바일 장치로 패킷을 전송|

📌 **Mobile IP 패킷 전달 흐름**

scss

CopyEdit

`사용자 (Foreign Network) → FA (외부 에이전트) → HA (홈 에이전트) → 인터넷 서버`

→ **HA가 사용자의 현재 위치를 FA로 업데이트하고 패킷을 터널링하여 전달**

##### **💡 Real-Life Example (실생활 예시)**

> - **해외 여행 중에도 원래 휴대폰 번호(홈 네트워크)를 통해 전화/SMS를 받을 수 있는 것과 유사.**
> - **VPN을 통해 외부 네트워크에서도 회사 내부망을 사용하는 것과 비슷한 개념.**

---

## **7.6.4 Mobile IP Handoff (Mobile IP에서의 핸드오프 과정)**

### **설명 (Explanation)**

Mobile IP에서 **핸드오프(Handoff)는 사용자가 네트워크를 이동할 때 기존 연결을 유지하는 과정**이다.

### **1️⃣ Mobile IP Handoff 유형 (Types of Mobile IP Handoff)**

|핸드오프 유형|설명|
|---|---|
|**Soft Handoff (소프트 핸드오프)**|기존 네트워크와 새로운 네트워크가 동시에 연결됨 (3G)|
|**Hard Handoff (하드 핸드오프)**|기존 네트워크 연결이 끊긴 후 새로운 네트워크에 연결 (LTE, 5G)|
|**Make-Before-Break (MBB) 방식**|새로운 네트워크에 먼저 연결한 후 기존 연결을 해제|
|**Break-Before-Make (BBM) 방식**|기존 연결을 끊고 새로운 네트워크에 연결|

📌 **Mobile IP Handoff 예제**

- **Wi-Fi에서 LTE로 전환 시 네트워크 끊김 없이 연결 유지 (Make-Before-Break 방식).**
- **기지국 간 이동 시 핸드오프가 발생하며 인터넷 연결이 유지됨.**

##### **💡 Real-Life Example (실생활 예시)**

> - **지하철을 타고 이동할 때도 스마트폰이 자동으로 최적의 기지국을 선택하며 연결 유지.**
> - **VoIP(카카오톡, 줌) 통화가 Wi-Fi에서 LTE로 바뀌어도 중단되지 않음.**

---

## **7.6.5 Security Issues in Mobile IP (Mobile IP 보안 문제 및 해결 방법)**

### **설명 (Explanation)**

Mobile IP는 **사용자의 네트워크 이동성을 보장하지만, 몇 가지 보안 취약점이 존재**.

### **1️⃣ Mobile IP 보안 문제 (Security Issues in Mobile IP)**

|보안 문제|설명|
|---|---|
|**IP Spoofing (IP 스푸핑)**|공격자가 사용자의 IP 주소를 위장하여 트래픽 가로챔|
|**Session Hijacking (세션 하이재킹)**|인증된 세션을 가로채어 불법적으로 사용|
|**Denial of Service (서비스 거부 공격, DoS)**|Home Agent(HA) 또는 Foreign Agent(FA)를 대상으로 트래픽 과부하 공격|

📌 **보안 해결책**  
✅ **IPsec을 사용하여 데이터 암호화 및 인증 강화**  
✅ **AAA(Authentication, Authorization, Accounting) 시스템 적용**  
✅ **VPN 기술을 통해 데이터 보호 강화**

##### **💡 Real-Life Example (실생활 예시)**

> - **IPsec 기반 VPN을 사용하면 안전하게 네트워크를 이동하며 인터넷 사용 가능.**
> - **OTP(One-Time Password) 인증을 통해 불법적인 세션 하이재킹을 방지.**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Mobile IP는 사용자가 네트워크를 이동해도 기존 IP 주소를 유지할 수 있도록 지원하는 기술이다.**
2. **Home Agent(HA), Foreign Agent(FA), Care-of Address(CoA) 등을 통해 네트워크 변경 시에도 패킷을 전달할 수 있다.**
3. **Handoff를 통해 네트워크 변경 시 연결을 유지하며, IPsec 등 보안 기술을 적용하여 Mobile IP의 취약점을 해결할 수 있다.**

🚀 **한 문장 요약:**  
**Mobile IP는 사용자가 네트워크를 변경해도 기존 IP 주소를 유지할 수 있도록 하며, 터널링, 핸드오프, 보안 기술을 통해 안정적인 인터넷 연결을 제공한다.**
