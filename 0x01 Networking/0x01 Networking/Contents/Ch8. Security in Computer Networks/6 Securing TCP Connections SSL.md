[[Security in Computer Networks]]

#### **요약 (Summary)**

**SSL (Secure Sockets Layer)**은 **인터넷에서 TCP 연결을 보호하기 위한 암호화 프로토콜**이다.  
현재는 **TLS (Transport Layer Security)**가 SSL의 발전된 버전으로 사용되지만, 일반적으로 SSL/TLS로 통칭된다.  
SSL/TLS는 **데이터 암호화(Encryption), 무결성(Integrity), 인증(Authentication)** 기능을 제공하여  
웹사이트(HTTPS), 이메일, VPN, 금융 거래 등의 보안을 강화한다.

---

## **8.6.1 Why Secure TCP Connections? (TCP 연결 보안의 필요성)**

### **설명 (Explanation)**

기본적인 TCP 연결은 **데이터를 평문(Plaintext)으로 전송하므로 도청(Eavesdropping), 중간자 공격(MITM), 데이터 변조(Tampering)에 취약**하다.

### **1️⃣ TCP 연결에서 발생할 수 있는 보안 위협 (Security Threats in TCP Connections)**

|보안 위협|설명|
|---|---|
|**Eavesdropping (도청 공격)**|네트워크에서 데이터를 가로채는 공격|
|**Man-in-the-Middle Attack (MITM, 중간자 공격)**|공격자가 송수신자 사이에서 데이터를 조작 또는 감청|
|**Session Hijacking (세션 하이재킹)**|공격자가 세션을 탈취하여 사용자 권한을 가로챔|
|**Data Tampering (데이터 변조)**|공격자가 패킷 내용을 변경하여 악의적인 조작 수행|

📌 **TCP 공격 시나리오 예제**

- **공개 Wi-Fi에서 사용자의 로그인 정보를 해커가 가로채는 MITM 공격**
- **온라인 쇼핑몰 결제 페이지에서 가격 정보를 변조하여 결제하는 데이터 변조 공격**
- **쿠키 탈취(Session Hijacking)로 사용자의 온라인 계정을 해킹하는 공격**

##### **💡 Real-Life Example (실생활 예시)**

> - **공공 와이파이에서 로그인 정보를 입력했는데, 해커가 데이터를 가로채 계정을 도용하는 것**
> - **은행 웹사이트에 접속할 때 HTTPS(SSL/TLS)가 활성화되지 않아 해커가 중간에서 데이터를 변조하는 경우**

---

## **8.6.2 What is SSL/TLS? (SSL/TLS란?)**

### **설명 (Explanation)**

SSL/TLS는 **TCP 연결을 암호화하여 데이터를 안전하게 전송하는 보안 프로토콜**이다.  
SSL은 초기 버전이지만, 현재는 보안이 강화된 **TLS (Transport Layer Security)**가 사용된다.

📌 **SSL vs. TLS 비교**

|프로토콜|버전|특징|
|---|---|---|
|**SSL 2.0 / SSL 3.0**|1990년대|보안 취약점으로 사용되지 않음|
|**TLS 1.0 / 1.1**|1999 / 2006|보안 강화, 현재는 사용 권장하지 않음|
|**TLS 1.2**|2008|현재 가장 널리 사용됨|
|**TLS 1.3**|2018|성능 개선, 더 강력한 암호화 지원|

📌 **SSL/TLS 적용 예제**

- **웹사이트 HTTPS 연결 (웹 브라우저 - 웹 서버 간 보안 통신)**
- **이메일 암호화 (SMTP, IMAP, POP3 보안 강화)**
- **VPN 보안 연결 (SSL VPN 사용)**

##### **💡 Real-Life Example (실생활 예시)**

> - **은행 웹사이트(https://)에 접속하면 SSL/TLS를 통해 안전한 연결이 이루어짐**
> - **온라인 쇼핑몰에서 카드 결제 정보를 보호하기 위해 TLS 1.2/1.3이 적용됨**

---

## **8.6.3 SSL/TLS Handshake (SSL/TLS 핸드셰이크 과정)**

### **설명 (Explanation)**

SSL/TLS는 **클라이언트와 서버 간의 핸드셰이크(Handshake) 과정을 거쳐 보안 세션을 설정**한다.

📌 **SSL/TLS Handshake 과정**

1. **Client Hello**: 클라이언트(브라우저)가 지원하는 암호화 알고리즘을 서버에 전송
2. **Server Hello**: 서버가 사용할 암호화 알고리즘과 인증서를 클라이언트에 제공
3. **Certificate Exchange**: 서버가 **디지털 인증서(X.509)를 전송하여 신뢰성을 증명**
4. **Key Exchange**: 세션 키(Session Key)를 안전하게 교환
5. **Finished**: 보안 연결이 설정되고 암호화된 데이터 전송 시작

📌 **SSL/TLS Handshake 예제**

arduino

CopyEdit

`사용자 → https://example.com 접속 → 브라우저가 SSL/TLS Handshake 수행 → 보안 세션 설정 → 암호화된 데이터 전송`

✅ **TLS 1.3에서는 핸드셰이크 과정이 단축되어 속도가 더 빠르고 보안성이 강화됨**

##### **💡 Real-Life Example (실생활 예시)**

> - **HTTPS 웹사이트에 처음 접속할 때 브라우저가 SSL/TLS 인증서를 확인하는 과정**
> - **VPN 연결 시 보안 키 교환을 수행하여 암호화된 터널을 설정하는 과정**

---

## **8.6.4 SSL/TLS Encryption (SSL/TLS 암호화 방식)**

### **설명 (Explanation)**

SSL/TLS는 **데이터를 암호화하여 기밀성을 보장하며, 대칭 및 비대칭 암호화 알고리즘을 조합하여 사용**한다.

📌 **SSL/TLS에서 사용되는 암호화 방식**

|암호화 유형|설명|
|---|---|
|**Symmetric Encryption (대칭 키 암호화)**|AES, ChaCha20 등을 사용하여 세션 데이터를 암호화|
|**Asymmetric Encryption (비대칭 키 암호화)**|RSA, ECDSA를 사용하여 키 교환 수행|
|**Message Authentication (무결성 보장)**|HMAC-SHA256 등을 사용하여 데이터 변조 방지|

📌 **SSL/TLS 암호화 과정**

scss

CopyEdit

`1. 클라이언트와 서버가 공개 키 교환(RSA, Diffie-Hellman) 2. 대칭 키(AES) 생성하여 데이터 암호화 3. MAC(Hash 기반 인증) 적용하여 데이터 변조 방지`

✅ **TLS 1.3에서는 RSA 대신 Diffie-Hellman 키 교환을 사용하여 보안성을 강화**

##### **💡 Real-Life Example (실생활 예시)**

> - **웹사이트에서 로그인 시 사용자 비밀번호가 암호화되어 서버로 전송됨**
> - **온라인 뱅킹에서 송금 정보를 보호하기 위해 AES 암호화가 사용됨**

---

## **8.6.5 Digital Certificates and SSL/TLS Authentication (디지털 인증서와 SSL/TLS 인증)**

### **설명 (Explanation)**

SSL/TLS는 **디지털 인증서(Digital Certificate)를 사용하여 서버의 신뢰성을 검증**한다.

📌 **디지털 인증서(X.509) 동작 방식**

1. **웹사이트(서버)가 SSL/TLS 인증서를 제공**
2. **클라이언트(브라우저)가 인증서를 검증(Certificate Authority, CA 확인)**
3. **인증서가 유효하면 HTTPS 연결 설정**

📌 **SSL/TLS 인증서 종류**

|인증서 유형|설명|
|---|---|
|**DV (Domain Validation)**|도메인 소유권만 검증|
|**OV (Organization Validation)**|기업 정보도 포함|
|**EV (Extended Validation)**|최고 보안 수준 (은행, 금융기관에서 사용)|

##### **💡 Real-Life Example (실생활 예시)**

> - **브라우저 주소창에 "🔒" 아이콘이 나타나면 SSL/TLS 인증서가 정상적으로 작동 중**
> - **"이 웹사이트의 보안 인증서가 유효하지 않습니다"라는 경고가 표시되면 인증서가 만료되었거나 위조됨**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **SSL/TLS는 TCP 연결을 보호하여 도청, 데이터 변조, 스푸핑 공격을 방지한다.**
2. **TLS 1.2와 TLS 1.3이 가장 널리 사용되며, HTTPS, 이메일, VPN 등에서 활용된다.**
3. **SSL/TLS Handshake를 통해 보안 세션을 설정하고, 대칭 및 비대칭 암호화를 조합하여 사용한다.**
4. **디지털 인증서(X.509)는 SSL/TLS에서 서버 신뢰성을 검증하는 역할을 한다.**

🚀 **한 문장 요약:**  
**SSL/TLS는 웹사이트, 이메일, VPN 보안 강화를 위해 TCP 연결을 암호화하여 데이터 기밀성, 무결성, 인증을 제공하는 필수적인 보안 프로토콜이다.**