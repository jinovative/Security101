[[Security in Computer Networks]]

#### **요약 (Summary)**

**Network Security(네트워크 보안)**는 **네트워크와 데이터를 보호하여 무단 접근, 공격, 데이터 유출을 방지하는 기술과 프로세스**를 의미한다.  
네트워크 보안의 목표는 **기밀성(Confidentiality), 무결성(Integrity), 가용성(Availability)**을 보장하는 것이다.  
이를 위해 **방화벽(Firewall), 암호화(Encryption), 인증(Authentication), 침입 탐지 시스템(IDS)** 등의 다양한 보안 기술이 사용된다.

---

## **8.1.1 Goals of Network Security (네트워크 보안의 목표: CIA 트라이어드)**

### **설명 (Explanation)**

네트워크 보안은 **CIA Triad(기밀성, 무결성, 가용성)을 중심으로 설계되며, 이를 통해 데이터와 시스템을 보호**한다.

### **1️⃣ CIA Triad (기밀성, 무결성, 가용성)**

|보안 목표|설명|
|---|---|
|**Confidentiality (기밀성)**|데이터가 인가된 사용자만 접근 가능하도록 보호|
|**Integrity (무결성)**|데이터가 변조되지 않도록 보장|
|**Availability (가용성)**|네트워크 및 서비스가 항상 정상적으로 운영되도록 유지|

📌 **CIA 트라이어드 예제**

- **Confidentiality → 데이터가 암호화되어 인가되지 않은 사용자는 읽을 수 없음**
- **Integrity → 전송 중 데이터가 변경되지 않도록 디지털 서명을 추가**
- **Availability → DDoS 공격을 방어하여 네트워크 다운타임 최소화**

##### **💡 Real-Life Example (실생활 예시)**

> - **Confidentiality = 이메일이 암호화되어 해커가 내용을 볼 수 없는 것**
> - **Integrity = 은행 송금 내역이 변조되지 않도록 디지털 서명을 사용하는 것**
> - **Availability = 클라우드 서비스가 DDoS 공격을 받아도 정상 작동하는 것**

---

## **8.1.2 Types of Network Attacks (네트워크 공격 유형)**

### **설명 (Explanation)**

네트워크 보안의 목표를 달성하기 위해 **다양한 보안 위협을 방어해야 하며, 주요 네트워크 공격 유형을 이해하는 것이 중요**하다.

### **1️⃣ 주요 네트워크 공격 유형 (Types of Network Attacks)**

|공격 유형|설명|
|---|---|
|**Denial of Service (DoS/DDoS, 서비스 거부 공격)**|네트워크 트래픽을 과부하 상태로 만들어 서비스 중단 유발|
|**Man-in-the-Middle (MITM, 중간자 공격)**|공격자가 두 당사자 간 통신을 가로채고 변조|
|**Phishing (피싱 공격)**|신뢰할 수 있는 기관을 가장하여 사용자 정보를 탈취|
|**Malware (악성 코드, 바이러스, 트로이 목마 등)**|시스템을 감염시키고 데이터 탈취 및 파괴|
|**SQL Injection (SQL 인젝션)**|웹사이트의 데이터베이스에 악성 SQL 명령어 삽입|
|**Zero-Day Attack (제로데이 공격)**|보안 패치가 적용되지 않은 취약점을 악용하는 공격|

📌 **네트워크 공격 예제**

- **DDoS → 특정 웹사이트(예: 온라인 쇼핑몰)에 과도한 요청을 보내 서버 다운**
- **MITM → Wi-Fi 네트워크에서 해커가 은행 로그인 정보를 가로챔**
- **Phishing → 이메일을 통해 가짜 로그인 페이지로 유도하여 비밀번호 탈취**

##### **💡 Real-Life Example (실생활 예시)**

> - **DDoS = 유명 티켓 예매 사이트가 갑자기 트래픽 폭주로 다운되는 것**
> - **MITM = 카페 Wi-Fi에서 로그인 정보를 도청당하는 것**
> - **Phishing = 은행을 사칭한 가짜 이메일을 받고 로그인 정보를 입력하는 것**

---

## **8.1.3 Network Security Techniques (네트워크 보안 기법)**

### **설명 (Explanation)**

네트워크 보안을 유지하기 위해 **다양한 기술과 기법이 사용되며, 이를 통해 악의적인 공격을 방어할 수 있음**.

### **1️⃣ 주요 네트워크 보안 기술 (Key Network Security Techniques)**

|보안 기술|설명|
|---|---|
|**Firewall (방화벽)**|네트워크 트래픽을 필터링하여 악성 트래픽 차단|
|**Intrusion Detection System (IDS, 침입 탐지 시스템)**|네트워크에서 이상 행위를 감지하여 경고|
|**Intrusion Prevention System (IPS, 침입 방지 시스템)**|네트워크 공격을 실시간 차단|
|**Encryption (암호화)**|데이터 전송 시 암호화하여 도청 방지 (예: TLS, VPN)|
|**Authentication (인증)**|사용자의 신원을 확인하는 보안 절차 (예: 2FA, OTP)|
|**VPN (Virtual Private Network, 가상 사설망)**|안전한 네트워크 통신을 위한 터널링 기술|
|**Access Control (접근 제어)**|특정 사용자가 네트워크 및 데이터에 접근할 수 있도록 제한|

📌 **보안 기술 예제**

- **방화벽 → 특정 IP 주소에서 들어오는 불법 트래픽을 차단**
- **VPN → 원격 근무 시 보안이 강화된 네트워크를 통해 회사 서버에 접속**
- **암호화 → 이메일을 TLS 암호화하여 데이터 유출 방지**

##### **💡 Real-Life Example (실생활 예시)**

> - **Firewall = 아파트 현관에서 외부인이 무단 출입하는 것을 방지하는 출입 보안 시스템**
> - **VPN = 공공 Wi-Fi를 사용할 때 해커로부터 데이터를 보호하는 것**
> - **2FA Authentication = 온라인 계정 로그인 시 추가 인증을 요구하는 것 (OTP, 생체 인증 등)**

---

## **8.1.4 Security Policies and Best Practices (보안 정책 및 모범 사례)**

### **설명 (Explanation)**

보안 기술뿐만 아니라 **보안 정책(Security Policies)과 모범 사례(Best Practices)를 적용하여 네트워크 보안을 강화할 수 있음**.

### **1️⃣ 보안 정책 및 모범 사례 (Security Policies & Best Practices)**

|보안 정책|설명|
|---|---|
|**Least Privilege Principle (최소 권한 원칙)**|사용자에게 필요한 최소한의 권한만 부여|
|**Regular Software Updates (정기적인 소프트웨어 업데이트)**|보안 취약점을 패치하여 제로데이 공격 방지|
|**Strong Password Policy (강력한 비밀번호 정책)**|비밀번호 복잡성 요구 및 주기적인 변경|
|**Multi-Factor Authentication (MFA, 다중 인증)**|2단계 인증(OTP, 생체 인증) 적용|
|**Security Awareness Training (보안 교육 실시)**|피싱, 소셜 엔지니어링 공격 예방을 위한 사용자 교육|
|**Network Segmentation (네트워크 분리)**|내부망과 외부망을 분리하여 보안 강화|

📌 **보안 정책 예제**

- **MFA → 회사 로그인 시 비밀번호 + OTP 입력 요구**
- **정기 업데이트 → 윈도우 및 서버 보안 패치 적용**
- **네트워크 분리 → 회사 내부망과 게스트 Wi-Fi를 분리하여 보안 강화**

##### **💡 Real-Life Example (실생활 예시)**

> - **은행 앱 로그인 시 OTP를 추가로 입력하는 것 (Multi-Factor Authentication).**
> - **사무실 네트워크에서 직원용과 방문자용 Wi-Fi를 분리하는 것 (Network Segmentation).**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Network Security(네트워크 보안)는 기밀성(Confidentiality), 무결성(Integrity), 가용성(Availability)을 보장하는 것이 목표이다.**
2. **DDoS, MITM, Phishing, Malware 같은 다양한 네트워크 공격을 방어해야 한다.**
3. **방화벽(Firewall), IDS/IPS, 암호화(Encryption), VPN, 인증(Authentication) 등의 기술을 활용하여 보안을 강화할 수 있다.**
4. **보안 정책(Security Policies)과 모범 사례(Best Practices)를 적용하여 네트워크 보안을 유지해야 한다.**

🚀 **한 문장 요약:**  
**네트워크 보안은 방화벽, 암호화, 인증 등 다양한 보안 기술을 활용하여 해킹, 데이터 유출, 서비스 장애를 방지하고, 안전한 인터넷 환경을 구축하는 것을 목표로 한다.**