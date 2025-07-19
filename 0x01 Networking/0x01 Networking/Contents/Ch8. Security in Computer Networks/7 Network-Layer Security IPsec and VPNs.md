[[Security in Computer Networks]]

#### **요약 (Summary)**

**Network-Layer Security(네트워크 계층 보안)**는 **IP 네트워크에서 데이터의 기밀성(Confidentiality), 무결성(Integrity), 인증(Authentication)을 보장하는 기술**이다.  
가장 널리 사용되는 보안 프로토콜은 **IPsec(Internet Protocol Security)**이며,  
이는 **VPN(Virtual Private Network)**을 통해 원격 접속, 기업 네트워크 보호, 데이터 암호화 등에 활용된다.

---

## **8.7.1 Why Network-Layer Security? (네트워크 계층 보안의 필요성)**

### **설명 (Explanation)**

기본적인 IP 네트워크는 **데이터를 암호화하지 않고 전송하므로 도청(Eavesdropping), 패킷 변조(Tampering), 스푸핑(Spoofing) 같은 공격에 취약**하다.  
이를 방지하기 위해 **IP 계층에서 보안을 적용하는 IPsec과 같은 프로토콜이 필요**하다.

### **1️⃣ 주요 네트워크 보안 위협 (Security Threats in IP Networks)**

|보안 위협|설명|
|---|---|
|**Eavesdropping (도청 공격)**|공격자가 네트워크에서 데이터를 가로채는 공격|
|**Packet Tampering (패킷 변조)**|데이터가 전송 중 조작되거나 변경되는 공격|
|**IP Spoofing (IP 스푸핑)**|공격자가 위조된 IP 주소로 신뢰할 수 있는 장치처럼 위장|
|**Man-in-the-Middle Attack (MITM, 중간자 공격)**|공격자가 네트워크 통신을 가로채어 변경 또는 감청|

📌 **네트워크 보안 위협 예제**

- **공개 Wi-Fi에서 사용자의 비밀번호가 해커에게 도청되는 공격**
- **IP 스푸핑을 사용하여 공격자가 허가되지 않은 네트워크에 액세스하는 공격**
- **MITM 공격을 통해 은행 웹사이트의 로그인 세션을 탈취하는 공격**

##### **💡 Real-Life Example (실생활 예시)**

> - **공공 와이파이에서 이메일을 확인하는 동안 해커가 네트워크 패킷을 가로채는 경우**
> - **VPN 없이 원격으로 회사 네트워크에 접속할 때 공격자가 중간에서 데이터를 변조하는 경우**

---

## **8.7.2 What is IPsec? (IPsec이란?)**

### **설명 (Explanation)**

**IPsec (Internet Protocol Security)**은 **IP 계층에서 데이터를 암호화하고 인증하여 안전한 통신을 제공하는 프로토콜**이다.  
IPsec은 **VPN(가상 사설망) 및 보안 네트워크 통신에서 필수적으로 사용**된다.

📌 **IPsec의 주요 기능**  
✅ **Encryption (암호화): 데이터를 암호화하여 도청 방지**  
✅ **Integrity (무결성): 데이터가 변조되지 않았음을 보장**  
✅ **Authentication (인증): 송신자의 신원을 확인하여 위조 방지**

---

### **1️⃣ IPsec의 동작 방식 (How IPsec Works)**

IPsec은 **두 개의 주요 프로토콜을 사용하여 보안을 제공**한다.

|프로토콜|설명|
|---|---|
|**AH (Authentication Header, 인증 헤더)**|패킷의 출처를 인증하고 무결성을 보장하지만, 암호화 기능은 없음|
|**ESP (Encapsulating Security Payload, 보안 페이로드 캡슐화)**|패킷을 암호화하고 인증하여 보안성을 강화|

📌 **IPsec 동작 예제**

1. **데이터를 암호화(AES, 3DES 사용)**
2. **디지털 서명 또는 HMAC을 사용하여 무결성 검사**
3. **패킷을 캡슐화하여 안전한 전송 수행**

✅ **IPsec은 네트워크 계층(IP Layer)에서 동작하므로 애플리케이션 변경 없이 모든 트래픽을 보호 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **기업에서 직원들이 원격으로 VPN을 통해 사내 네트워크에 안전하게 연결하는 경우**
> - **정부 기관이 기밀 데이터를 송수신할 때 IPsec을 사용하여 보안 강화**

---

## **8.7.3 IPsec Modes (IPsec 동작 모드)**

### **설명 (Explanation)**

IPsec은 **패킷을 보호하는 방식에 따라 두 가지 모드로 동작**한다.

|IPsec 모드|설명|사용 사례|
|---|---|---|
|**Transport Mode (전송 모드)**|페이로드(데이터)만 암호화|호스트 간 보안 통신 (예: VoIP, 원격 데스크톱)|
|**Tunnel Mode (터널 모드)**|전체 IP 패킷을 암호화하여 캡슐화|VPN 연결 (예: 원격 근무, 지사 연결)|

📌 **IPsec 모드 예제**

- **Transport Mode → 두 개의 서버 간 안전한 데이터 전송**
- **Tunnel Mode → 인터넷을 통해 본사와 지사 간 VPN 연결 제공**

##### **💡 Real-Life Example (실생활 예시)**

> - **직원이 집에서 회사 네트워크에 접속할 때 VPN이 터널 모드로 동작하여 모든 데이터가 암호화됨**
> - **온라인 회의 중 VoIP 데이터가 IPsec 전송 모드로 보호됨**

---

## **8.7.4 Virtual Private Networks (VPNs) and IPsec**

### **설명 (Explanation)**

**VPN (Virtual Private Network)**은 **공용 네트워크(예: 인터넷)에서 사설 네트워크를 안전하게 연결하는 기술**이다.  
VPN은 **IPsec 또는 SSL/TLS을 사용하여 보안 터널을 구축**한다.

📌 **VPN의 주요 기능**  
✅ **Encryption (암호화): 네트워크 트래픽을 보호**  
✅ **Authentication (인증): 사용자 및 장치의 신원 확인**  
✅ **Data Integrity (무결성): 데이터 변조 방지**

### **1️⃣ VPN의 유형 (Types of VPNs)**

|VPN 유형|설명|사용 사례|
|---|---|---|
|**Remote Access VPN**|사용자가 원격에서 기업 네트워크에 접속 가능|재택근무, 출장 중 접속|
|**Site-to-Site VPN**|지사와 본사를 안전하게 연결|기업 간 내부 네트워크 연결|

📌 **VPN 동작 방식 예제**

1. **사용자가 VPN 클라이언트로 접속**
2. **IPsec 또는 SSL을 통해 보안 터널 생성**
3. **모든 데이터가 암호화된 상태로 기업 네트워크와 통신**

##### **💡 Real-Life Example (실생활 예시)**

> - **직원이 재택근무 시 회사 VPN을 사용하여 내부 문서와 시스템에 접속**
> - **다른 국가에서 공공 Wi-Fi를 사용할 때 VPN을 통해 안전한 인터넷 연결 유지**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **IPsec은 네트워크 계층에서 보안을 제공하는 프로토콜로, 암호화(Encryption), 인증(Authentication), 무결성(Integrity)을 보장한다.**
2. **IPsec은 AH(인증 헤더)와 ESP(보안 페이로드 캡슐화) 프로토콜을 사용하여 데이터 보호를 수행한다.**
3. **VPN은 공용 네트워크에서 안전한 접속을 제공하며, 원격 근무 및 기업 내부 네트워크 보호에 필수적이다.**
4. **IPsec의 Tunnel Mode는 VPN을 통한 원격 접속에, Transport Mode는 호스트 간 보안 통신에 사용된다.**

🚀 **한 문장 요약:**  
**IPsec과 VPN은 네트워크 계층에서 데이터를 보호하는 핵심 기술로, 암호화, 인증, 무결성을 제공하여 안전한 인터넷 통신을 가능하게 한다.**