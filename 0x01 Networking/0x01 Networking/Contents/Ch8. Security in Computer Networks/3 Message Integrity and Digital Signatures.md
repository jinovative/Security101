[[Security in Computer Networks]]

#### **요약 (Summary)**

**Message Integrity(메시지 무결성)**는 **데이터가 전송 중 변조되지 않았음을 보장하는 기술**이다.  
이를 위해 **Cryptographic Hash Function(암호학적 해시 함수), MAC(Message Authentication Code), Digital Signatures(디지털 서명)** 같은 기법이 사용된다.  
특히, **Digital Signature(디지털 서명)**은 **메시지의 무결성을 검증할 뿐만 아니라, 송신자의 신원을 인증하고 부인 방지(Non-repudiation)를 제공**하는 중요한 기술이다.

---

## **8.3.1 Message Integrity (메시지 무결성)**

### **설명 (Explanation)**

메시지 무결성(Message Integrity)은 **데이터가 전송 중 변경되지 않았음을 보장하는 것**을 의미한다.  
이는 **악의적인 공격자에 의해 데이터가 변조되거나 조작되는 것을 방지하기 위한 보안 기술**이다.

### **1️⃣ Message Integrity를 보장하는 주요 기술 (Techniques to Ensure Message Integrity)**

|기술|설명|
|---|---|
|**Checksum (체크섬)**|데이터 오류를 감지하는 단순한 검증 방식|
|**Cryptographic Hash Function (암호학적 해시 함수)**|메시지를 고유한 해시 값으로 변환하여 무결성을 보장|
|**MAC (Message Authentication Code)**|키를 사용하여 메시지의 무결성을 보호|
|**Digital Signature (디지털 서명)**|공개 키 암호화를 사용하여 무결성과 인증을 동시에 제공|

📌 **Message Integrity 예제**

- **해시 값 비교 → 원본 메시지의 해시 값과 수신된 메시지의 해시 값이 일치하면 무결성이 보장됨**
- **MAC을 사용하여 송신자가 인증된 키를 이용해 메시지의 무결성을 보장**

##### **💡 Real-Life Example (실생활 예시)**

> - **파일 다운로드 시 SHA-256 해시 값을 제공하여 변조 여부를 확인할 수 있음**
> - **온라인 뱅킹에서 메시지가 중간에 변조되지 않았음을 검증하기 위해 MAC 사용**

---

## **8.3.2 Message Authentication Code (MAC, 메시지 인증 코드)**

### **설명 (Explanation)**

**MAC(Message Authentication Code)**는 **대칭 키를 사용하여 메시지 무결성과 인증을 보장하는 방법**이다.

### **1️⃣ MAC의 특징 (Properties of MAC)**

|특징|설명|
|---|---|
|**Integrity (무결성 보장)**|데이터가 변조되지 않았음을 검증|
|**Authentication (인증 제공)**|메시지가 신뢰할 수 있는 송신자로부터 온 것임을 증명|
|**Confidentiality (기밀성 없음)**|메시지 자체는 암호화되지 않음|

📌 **MAC 생성 및 검증 과정**

1. **송신자**: 메시지와 공유 키를 사용하여 MAC 생성
2. **수신자**: 수신한 메시지와 공유 키를 사용하여 MAC을 검증
3. **일치하면 메시지가 변조되지 않았음을 확인**

📌 **MAC 알고리즘 예제**

|알고리즘|설명|
|---|---|
|**HMAC (Hash-based MAC)**|해시 함수(SHA-256 등) 기반으로 MAC 생성|
|**CMAC (Cipher-based MAC)**|대칭 키 암호화(AES 등)를 기반으로 MAC 생성|

##### **💡 Real-Life Example (실생활 예시)**

> - **HMAC은 TLS, VPN에서 메시지가 변조되지 않았음을 보장하기 위해 사용됨**
> - **온라인 결제 시스템에서 거래 데이터가 조작되지 않았음을 검증하는 데 활용됨**

---

## **8.3.3 Digital Signatures (디지털 서명: 인증과 무결성 보장)**

### **설명 (Explanation)**

**Digital Signature(디지털 서명)**은 **공개 키 암호화를 이용하여 데이터 무결성과 송신자 인증을 동시에 제공하는 기법**이다.  
이는 **전자 문서, 이메일, 소프트웨어 인증 등에 널리 사용**된다.

### **1️⃣ Digital Signature의 특징 (Properties of Digital Signatures)**

|특징|설명|
|---|---|
|**Message Integrity (메시지 무결성 보장)**|메시지가 변조되지 않았음을 증명|
|**Authentication (송신자 인증 제공)**|메시지를 보낸 사람이 누구인지 확인|
|**Non-repudiation (부인 방지)**|송신자가 나중에 메시지를 보냈다는 사실을 부인할 수 없음|

📌 **디지털 서명 생성 및 검증 과정**

1. **송신자(Signer)**:
    - 메시지의 해시 값을 생성
    - 개인 키(Private Key)로 해시 값을 암호화하여 서명 생성
    - 원본 메시지 + 디지털 서명을 전송
2. **수신자(Verifier)**:
    - 원본 메시지의 해시 값을 계산
    - 송신자의 공개 키(Public Key)로 서명을 복호화하여 비교
    - 일치하면 메시지가 변조되지 않았음을 확인

📌 **디지털 서명 예제**

CopyEdit

`메시지 → 해시 값 생성 → 개인 키로 서명 → 메시지 + 서명 전송 → 공개 키로 검증`

📌 **디지털 서명 알고리즘 예제**

|알고리즘|설명|
|---|---|
|**RSA (Rivest-Shamir-Adleman)**|가장 널리 사용되는 디지털 서명 방식|
|**DSA (Digital Signature Algorithm)**|정부 및 금융 기관에서 주로 사용|
|**ECDSA (Elliptic Curve DSA)**|RSA보다 짧은 키 길이로 높은 보안 제공|

##### **💡 Real-Life Example (실생활 예시)**

> - **전자 계약서(예: DocuSign)에서 서명을 할 때 디지털 서명이 사용됨**
> - **소프트웨어 다운로드 시 코드 서명을 통해 변조 여부를 검증하는 것**

---

## **8.3.4 Digital Certificates and PKI (디지털 인증서 및 공개 키 인프라)**

### **설명 (Explanation)**

**디지털 인증서(Digital Certificate)**는 **공개 키가 신뢰할 수 있는 기관에 의해 발급되었음을 증명하는 전자 문서**이다.  
**PKI(Public Key Infrastructure, 공개 키 인프라)**는 **디지털 인증서를 관리하는 시스템**이다.

### **1️⃣ Digital Certificate의 역할**

✅ **공개 키가 유효한지 인증**  
✅ **웹사이트의 SSL/TLS 인증서로 사용됨 (HTTPS 보안 연결)**  
✅ **전자 서명 및 기업 네트워크 보안에서 사용**

📌 **디지털 인증서 예제**

CopyEdit

`사용자 → 웹사이트 접속(HTTPS) → SSL/TLS 인증서 확인 → 보안 통신 설정`

📌 **PKI의 주요 구성 요소**

|구성 요소|설명|
|---|---|
|**CA (Certificate Authority, 인증 기관)**|디지털 인증서를 발급하고 관리|
|**RA (Registration Authority, 등록 기관)**|사용자의 신원을 확인 후 CA에 인증 요청|
|**CRL (Certificate Revocation List, 인증서 폐기 목록)**|만료되거나 취소된 인증서를 관리|

##### **💡 Real-Life Example (실생활 예시)**

> - **웹사이트(예: Google, 은행 사이트)에 접속하면 HTTPS 인증서를 통해 신뢰성을 검증**
> - **회사에서 VPN 로그인 시 디지털 인증서를 사용하여 신원 확인**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Message Integrity(메시지 무결성)는 데이터가 변조되지 않았음을 보장하는 보안 기술이다.**
2. **MAC(Message Authentication Code)은 공유 키를 사용하여 메시지 무결성과 인증을 보장한다.**
3. **Digital Signature(디지털 서명)는 공개 키 암호화를 이용하여 무결성, 인증, 부인 방지를 제공한다.**
4. **PKI(Public Key Infrastructure)는 디지털 인증서를 관리하여 보안 통신을 지원한다.**

🚀 **한 문장 요약:**  
**디지털 서명과 암호학적 해시 함수를 사용하면 메시지 무결성을 검증할 수 있으며, 디지털 인증서(PKI)를 통해 신뢰성을 보장할 수 있다.**