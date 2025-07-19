[[Security in Computer Networks]]

#### **요약 (Summary)**

**Cryptography(암호학)**는 **데이터를 보호하기 위해 암호화(Encryption) 및 복호화(Decryption) 기술을 사용하는 방법**이다.  
암호학의 기본 목표는 **기밀성(Confidentiality), 무결성(Integrity), 인증(Authentication), 부인 방지(Non-repudiation)**를 보장하는 것이다.  
이를 위해 **대칭 키 암호화(Symmetric Key Encryption), 공개 키 암호화(Asymmetric Key Encryption), 해시 함수(Hash Function)** 등의 기술이 사용된다.

---

## **8.2.1 Goals of Cryptography (암호학의 목표)**

### **설명 (Explanation)**

암호학은 **데이터의 보안성과 신뢰성을 보장하기 위해 여러 가지 원칙을 기반으로 설계됨**.

### **1️⃣ Cryptography의 주요 목표 (Key Goals of Cryptography)**

|보안 목표|설명|
|---|---|
|**Confidentiality (기밀성)**|인가된 사용자만 데이터에 접근할 수 있도록 보호|
|**Integrity (무결성)**|데이터가 변조되지 않도록 보장|
|**Authentication (인증)**|데이터 송신자와 수신자의 신원을 확인|
|**Non-repudiation (부인 방지)**|송신자가 나중에 데이터 전송 사실을 부인하지 못하도록 보장|

📌 **암호학 적용 예제**

- **Confidentiality → 메시지를 암호화하여 해커가 내용을 볼 수 없도록 보호**
- **Integrity → 전송된 문서가 변조되지 않았음을 확인하기 위해 디지털 서명 사용**
- **Authentication → 로그인 시 사용자 인증을 위해 패스워드 및 2FA 사용**
- **Non-repudiation → 이메일 서명(Digital Signature)으로 송신자가 메일을 보냈음을 증명**

##### **💡 Real-Life Example (실생활 예시)**

> - **Confidentiality = 온라인 쇼핑몰에서 신용카드 정보를 암호화하여 저장하는 것**
> - **Integrity = 파일 다운로드 시 해시 값을 비교하여 데이터 변조 여부를 확인하는 것**
> - **Authentication = 은행 로그인 시 비밀번호 + OTP 인증을 요구하는 것**
> - **Non-repudiation = 전자 계약서에 디지털 서명을 사용하여 계약 사실을 증명하는 것**

---

## **8.2.2 Types of Cryptographic Algorithms (암호화 알고리즘의 종류)**

### **설명 (Explanation)**

암호화 알고리즘은 **키(Key) 사용 방식에 따라 대칭 키 암호화(Symmetric Key)와 공개 키 암호화(Asymmetric Key)로 구분**된다.

### **1️⃣ Symmetric Key Encryption (대칭 키 암호화)**

- **하나의 키(Key)로 데이터를 암호화하고 복호화**하는 방식.
- **속도가 빠르고 효율적이지만, 키를 안전하게 공유하는 것이 중요**.

📌 **대표적인 대칭 키 암호화 알고리즘**

|알고리즘|키 길이|특징|
|---|---|---|
|**DES (Data Encryption Standard)**|56-bit|보안성이 낮아 현재 거의 사용되지 않음|
|**AES (Advanced Encryption Standard)**|128/192/256-bit|가장 널리 사용되는 대칭 암호화 방식|
|**3DES (Triple DES)**|168-bit|DES를 3번 수행하여 보안 강화|

📌 **대칭 키 암호화 예제**

scss

CopyEdit

`[원본 메시지] → (암호화) → [암호화된 메시지] → (복호화) → [원본 메시지 복원]`

✅ **AES는 보안성이 강하고 속도가 빠르기 때문에 Wi-Fi, SSL/TLS, VPN 등 다양한 환경에서 사용됨**.

##### **💡 Real-Life Example (실생활 예시)**

> - **대칭 키 암호화는 금고의 열쇠와 유사 → 열쇠(키)가 있으면 금고를 열고 닫을 수 있음**.
> - **AES는 온라인 뱅킹에서 데이터 보호를 위해 사용됨**.

---

### **2️⃣ Asymmetric Key Encryption (비대칭 키 암호화, 공개 키 암호화)**

- **공개 키(Public Key)와 개인 키(Private Key)를 사용하여 암호화 및 복호화 수행**.
- **공개 키로 암호화된 데이터는 개인 키로만 복호화 가능 (반대로도 가능)**.
- **대칭 키 암호화보다 속도는 느리지만, 키 공유 문제를 해결함**.

📌 **대표적인 비대칭 키 암호화 알고리즘**

|알고리즘|키 길이|특징|
|---|---|---|
|**RSA (Rivest-Shamir-Adleman)**|1024/2048-bit|가장 널리 사용되는 공개 키 암호화 방식|
|**ECC (Elliptic Curve Cryptography)**|160-bit 이상|RSA보다 짧은 키 길이로 동일한 보안 제공|
|**Diffie-Hellman**|-|안전한 키 교환을 위한 알고리즘|

📌 **비대칭 키 암호화 예제**

scss

CopyEdit

`송신자 → (수신자의 공개 키로 암호화) → 메시지 전송 → (수신자가 개인 키로 복호화) → 원본 메시지 확인`

✅ **RSA는 SSL/TLS, 전자 서명, 암호화 이메일(PGP) 등에 널리 사용됨**.

##### **💡 Real-Life Example (실생활 예시)**

> - **공개 키 암호화는 우체통과 유사 → 누구나 우체통에 편지를 넣을 수 있지만, 편지를 꺼낼 수 있는 열쇠는 수신자만 가짐**.
> - **RSA는 웹사이트의 HTTPS 보안 연결(SSL/TLS)에서 사용됨**.

---

## **8.2.3 Hash Functions (해시 함수: 무결성 보장)**

### **설명 (Explanation)**

**Hash Function(해시 함수)**는 **임의의 길이의 입력 데이터를 고정된 길이의 해시 값으로 변환하는 함수**이다.  
암호학에서 해시 함수는 **데이터 무결성 검증, 디지털 서명, 패스워드 저장 등에 사용**됨.

### **1️⃣ 해시 함수의 특징 (Properties of Hash Functions)**

|특징|설명|
|---|---|
|**Deterministic (결정론적)**|동일한 입력 값은 항상 동일한 해시 값을 생성|
|**Collision-Resistant (충돌 저항성)**|서로 다른 입력 값이 같은 해시 값을 갖지 않도록 보장|
|**Irreversible (역산 불가능)**|원래 데이터를 해시 값에서 복원할 수 없음|

📌 **대표적인 해시 알고리즘**

|알고리즘|출력 길이|특징|
|---|---|---|
|**MD5 (Message Digest 5)**|128-bit|보안 취약점이 발견되어 사용 권장하지 않음|
|**SHA-1 (Secure Hash Algorithm 1)**|160-bit|더 이상 안전하지 않음|
|**SHA-256 (SHA-2 시리즈)**|256-bit|현재 가장 널리 사용됨|
|**SHA-3**|256/512-bit|차세대 해시 알고리즘|

📌 **해시 함수 예제**

arduino

CopyEdit

`입력: "Hello, World!" → SHA-256 → "c0535e4be2b79ffd93291305436bf889..."`

✅ **SHA-256은 블록체인, 디지털 서명, 패스워드 보안 등에 사용됨**.

##### **💡 Real-Life Example (실생활 예시)**

> - **해시 함수는 문서의 디지털 지문과 유사 → 문서가 변조되면 해시 값도 변경됨**.
> - **SHA-256은 비트코인 블록체인에서 무결성 보장을 위해 사용됨**.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Cryptography(암호학)는 기밀성(Confidentiality), 무결성(Integrity), 인증(Authentication), 부인 방지(Non-repudiation)을 보장하는 것이 목표이다.**
2. **대칭 키 암호화(AES)는 빠르고 효율적이지만, 키 공유 문제가 있음.**
3. **공개 키 암호화(RSA)는 보안성이 뛰어나지만 속도가 느림.**
4. **해시 함수(SHA-256)는 데이터 무결성을 보장하는 데 사용됨.**

🚀 **한 문장 요약:**  
**암호학은 데이터 보안을 위해 대칭/비대칭 암호화, 해시 함수 등을 활용하며, 이를 통해 기밀성, 무결성, 인증을 보장한다.**


