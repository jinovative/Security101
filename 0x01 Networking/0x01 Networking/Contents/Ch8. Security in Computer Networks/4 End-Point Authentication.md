[[Security in Computer Networks]]


#### **요약 (Summary)**

**End-Point Authentication(종단 간 인증)**은 **네트워크에서 통신을 시작하는 두 개체(사용자, 기기, 서버 등)가 서로 신원을 확인하는 과정**이다.  
이는 **무단 접근, 스푸핑(위장 공격), 중간자 공격(Man-in-the-Middle Attack)을 방지**하기 위해 필수적이다.  
대표적인 인증 방식으로는 **Passwords(비밀번호), Two-Factor Authentication(2FA), Digital Certificates(디지털 인증서), Challenge-Response Protocols(도전-응답 프로토콜)** 등이 있다.

---

## **8.4.1 The Importance of End-Point Authentication (종단 간 인증의 중요성)**

### **설명 (Explanation)**

네트워크 보안에서 **신뢰할 수 있는 개체만이 네트워크에 접근하도록 보장하는 것이 필수적**이며,  
이를 위해 **사용자 및 장치의 신원을 검증하는 인증(Authentication) 과정이 필요**하다.

### **1️⃣ End-Point Authentication의 주요 목표 (Key Goals of End-Point Authentication)**

|보안 목표|설명|
|---|---|
|**Identity Verification (신원 검증)**|접속하려는 사용자가 실제로 본인이 맞는지 확인|
|**Access Control (접근 제어)**|인가된 사용자만 시스템과 데이터를 사용할 수 있도록 제한|
|**Prevention of Spoofing (위장 공격 방지)**|공격자가 다른 사용자 또는 시스템을 가장하는 것을 방지|
|**Secure Communication (보안 통신 보장)**|신뢰할 수 있는 사용자 간 안전한 데이터 교환 보장|

📌 **End-Point Authentication 예제**

- **웹사이트 로그인 시 사용자 이름과 비밀번호 입력**
- **은행 앱에서 OTP(일회용 비밀번호)를 입력하여 본인 인증 수행**
- **VPN 연결 시 디지털 인증서를 사용하여 신원을 검증**

##### **💡 Real-Life Example (실생활 예시)**

> - **ATM에서 현금 인출 시 카드+PIN 번호를 입력하는 것**
> - **온라인 쇼핑몰에서 로그인 시 2FA(OTP 코드)를 추가로 입력하는 것**

---

## **8.4.2 Authentication Methods (인증 방법)**

### **설명 (Explanation)**

사용자와 장치의 신원을 확인하기 위해 **다양한 인증 방식이 사용**된다.  
각 방식은 보안 수준, 편의성, 적용 범위에 따라 선택된다.

### **1️⃣ 주요 인증 방식 (Types of Authentication Methods)**

|인증 방식|설명|보안 수준|
|---|---|---|
|**Password-based Authentication (비밀번호 인증)**|사용자가 설정한 비밀번호를 입력하여 인증|낮음|
|**Two-Factor Authentication (2FA, 다중 요소 인증)**|비밀번호 + 추가 인증(OTP, 생체 인증) 사용|높음|
|**Digital Certificates (디지털 인증서 인증)**|X.509 기반의 공개 키 인증서를 이용하여 신원 확인|높음|
|**Challenge-Response Authentication (도전-응답 인증)**|서버가 랜덤 값을 전송하고, 사용자가 올바른 응답을 반환해야 인증|중간|

📌 **Authentication Example**

- **비밀번호 로그인 → 단순하지만 보안성이 낮음**
- **2FA → 비밀번호+OTP 또는 생체 인식으로 보안 강화**
- **디지털 인증서 → VPN, HTTPS 웹사이트 보안 연결에 사용**

##### **💡 Real-Life Example (실생활 예시)**

> - **스마트폰에서 페이스 ID(생체 인증)를 사용하여 앱을 여는 것**
> - **회사 네트워크에 접속할 때 보안 토큰을 사용하여 추가 인증하는 것**

---

## **8.4.3 Challenge-Response Authentication (도전-응답 방식 인증)**

### **설명 (Explanation)**

**Challenge-Response Authentication(도전-응답 인증)**은 **서버가 클라이언트에게 임의의 값을 전송하고, 클라이언트가 이에 대해 올바른 응답을 반환하는 방식**이다.  
이 방식은 **비밀번호를 직접 전송하지 않으므로 도청(Man-in-the-Middle Attack) 방지에 효과적**이다.

### **1️⃣ Challenge-Response Authentication의 동작 과정**

1. **서버**가 랜덤 Challenge(도전 값)를 클라이언트에게 전송
2. **클라이언트**가 비밀 키 또는 해시 함수를 사용하여 Challenge에 대한 Response(응답) 생성
3. **서버**가 수신된 Response를 검증하여 인증 승인 또는 거부

📌 **Challenge-Response Authentication Example**

arduino

CopyEdit

`서버: "랜덤 값 12345를 보내니, 올바른 응답을 계산해서 보내라!" 클라이언트: "12345를 암호화하여 응답 67890을 반환" 서버: "응답이 일치하므로 인증 성공!"`

📌 **Challenge-Response 인증 알고리즘 예제**

|알고리즘|설명|
|---|---|
|**CHAP (Challenge Handshake Authentication Protocol)**|PPP(Point-to-Point Protocol)에서 사용되는 인증 방식|
|**Kerberos**|티켓을 사용하여 인증을 수행하는 프로토콜|
|**SRP (Secure Remote Password Protocol)**|패스워드 기반 도전-응답 프로토콜|

##### **💡 Real-Life Example (실생활 예시)**

> - **온라인 게임에서 로그인 시 해커가 패스워드를 훔쳐도 실제 비밀번호가 노출되지 않도록 보호하는 방식**
> - **무선 네트워크(WPA2-Enterprise)에서 사용자 인증 시 도전-응답 방식 사용**

---

## **8.4.4 Digital Certificates and PKI (디지털 인증서 및 공개 키 인프라)**

### **설명 (Explanation)**

디지털 인증서는 **사용자의 신원을 검증하는 전자 문서**이며, **PKI(Public Key Infrastructure)**는 **디지털 인증서를 관리하는 시스템**이다.

### **1️⃣ Digital Certificates의 역할**

✅ **SSL/TLS 보안 연결(HTTPS)에서 웹사이트 인증**  
✅ **VPN 및 기업 네트워크 로그인 시 사용자 인증**  
✅ **전자 서명(Digital Signature)에서 사용자 신원 검증**

📌 **PKI 구성 요소**

|구성 요소|설명|
|---|---|
|**CA (Certificate Authority, 인증 기관)**|디지털 인증서를 발급 및 검증|
|**RA (Registration Authority, 등록 기관)**|사용자의 신원을 확인하고 인증 요청 수행|
|**CRL (Certificate Revocation List, 인증서 폐기 목록)**|만료되거나 취소된 인증서를 관리|

📌 **디지털 인증서 예제**

- **HTTPS 웹사이트에 접속할 때 브라우저가 SSL/TLS 인증서를 확인하여 웹사이트의 신뢰성을 검증**
- **VPN 로그인 시 디지털 인증서를 사용하여 사용자 신원을 인증**

##### **💡 Real-Life Example (실생활 예시)**

> - **은행 웹사이트(HTTPS)에 접속할 때 인증서를 확인하여 가짜 사이트인지 검증하는 것**
> - **회사 내부망에 접속할 때 VPN 인증서를 사용하여 로그인하는 것**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **End-Point Authentication(종단 간 인증)은 네트워크에 접속하는 사용자 및 장치의 신원을 검증하는 과정이다.**
2. **비밀번호, 2FA, 디지털 인증서, Challenge-Response 같은 다양한 인증 방식이 사용된다.**
3. **Challenge-Response Authentication은 서버가 임의의 Challenge 값을 보내고 클라이언트가 Response를 계산하여 인증을 수행하는 방식이다.**
4. **디지털 인증서(PKI)는 HTTPS, VPN, 기업 네트워크에서 신뢰할 수 있는 인증을 제공한다.**

🚀 **한 문장 요약:**  
**종단 간 인증은 네트워크 보안을 위해 사용자의 신원을 검증하는 과정이며, 비밀번호, 2FA, 디지털 인증서, Challenge-Response 같은 다양한 기법이 적용된다.**
