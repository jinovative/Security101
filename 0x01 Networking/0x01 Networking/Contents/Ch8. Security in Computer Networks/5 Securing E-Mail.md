[[Security in Computer Networks]]

#### **요약 (Summary)**

**Securing E-Mail(이메일 보안)**은 **이메일을 통해 발생할 수 있는 보안 위협(스푸핑, 피싱, 도청, 무단 변경 등)을 방지하는 기술과 프로토콜**을 의미한다.  
이를 위해 **End-to-End Encryption(종단 간 암호화), Digital Signatures(디지털 서명), Authentication Protocols(인증 프로토콜), Anti-Phishing Techniques(피싱 방지 기술)** 등이 사용된다.  
대표적인 이메일 보안 기술로는 **PGP(Pretty Good Privacy), S/MIME(Secure/Multipurpose Internet Mail Extensions), SPF(Sender Policy Framework), DKIM(DomainKeys Identified Mail), DMARC(Domain-based Message Authentication, Reporting & Conformance)**가 있다.

---

## **8.5.1 Threats to E-Mail Security (이메일 보안 위협)**

### **설명 (Explanation)**

이메일은 **인터넷에서 가장 널리 사용되는 통신 수단 중 하나이지만, 보안 취약점이 많아 다양한 공격의 대상이 될 수 있음**.

### **1️⃣ 주요 이메일 보안 위협 (Key E-Mail Security Threats)**

|보안 위협|설명|
|---|---|
|**Eavesdropping (도청 공격)**|이메일이 전송되는 중간에 공격자가 내용을 가로채는 공격|
|**Phishing (피싱 공격)**|신뢰할 수 있는 기관을 사칭하여 사용자의 민감한 정보를 탈취|
|**Spoofing (이메일 위장 공격)**|발신자가 속인 이메일 주소로 메시지를 보냄|
|**Malware (악성 코드 전파)**|이메일 첨부 파일이나 링크를 통해 바이러스, 랜섬웨어 유포|
|**Man-in-the-Middle Attack (MITM, 중간자 공격)**|공격자가 이메일 송수신 중간에서 내용을 변경 또는 탈취|

📌 **E-Mail Attack Example**

- **Phishing → 사용자가 은행을 사칭한 이메일을 받고 가짜 로그인 페이지에 비밀번호 입력**
- **Spoofing → 공격자가 CEO의 이메일을 위장하여 직원에게 송금을 요청**
- **MITM → 공공 Wi-Fi에서 이메일을 가로채어 로그인 정보 탈취**

##### **💡 Real-Life Example (실생활 예시)**

> - **가짜 이메일(피싱)에서 "비밀번호가 만료되었습니다. 새 비밀번호를 설정하세요"라는 메시지를 클릭하는 경우**
> - **공공 와이파이에서 이메일을 보낼 때 해커가 데이터를 가로채는 경우**

---

## **8.5.2 E-Mail Encryption (이메일 암호화: 기밀성 보장)**

### **설명 (Explanation)**

이메일 암호화는 **이메일 내용이 전송 중에 도청되지 않도록 보호하는 보안 기술**이다.  
이를 위해 **PGP(Pretty Good Privacy)와 S/MIME(Secure/Multipurpose Internet Mail Extensions)** 같은 기술이 사용됨.

### **1️⃣ 주요 이메일 암호화 방식 (E-Mail Encryption Methods)**

|암호화 방식|설명|
|---|---|
|**PGP (Pretty Good Privacy)**|공개 키 암호화(RSA)를 사용하여 이메일을 종단 간 암호화|
|**S/MIME (Secure/Multipurpose Internet Mail Extensions)**|X.509 인증서를 이용하여 이메일 암호화 및 디지털 서명 제공|
|**TLS (Transport Layer Security) for E-Mail**|이메일 서버 간 전송 보안을 제공 (STARTTLS)|

📌 **PGP Encryption Example**

1. **송신자**: 수신자의 공개 키로 이메일을 암호화
2. **수신자**: 자신의 개인 키로 이메일을 복호화

scss

CopyEdit

`[원본 메시지] → (송신자의 PGP 공개 키로 암호화) → [암호화된 이메일 전송] → (수신자가 개인 키로 복호화) → [메시지 복원]`

✅ **Gmail, Outlook 같은 이메일 서비스는 기본적으로 TLS 암호화를 지원하지만, 추가적인 보호를 위해 PGP, S/MIME을 활용할 수 있음**.

##### **💡 Real-Life Example (실생활 예시)**

> - **외교 기관, 금융 기업에서 기밀 정보를 이메일로 보낼 때 PGP 암호화를 사용하여 보호**
> - **회사 내부에서 중요한 계약서를 이메일로 전송할 때 S/MIME을 사용하여 디지털 서명 포함**

---

## **8.5.3 Digital Signatures for E-Mail (이메일 디지털 서명: 무결성 및 인증 보장)**

### **설명 (Explanation)**

디지털 서명(Digital Signature)은 **이메일이 변조되지 않았음을 보장하고, 송신자의 신원을 확인하는 보안 기술**이다.

### **1️⃣ Digital Signature의 특징 (Properties of Digital Signatures in E-Mail)**

|특징|설명|
|---|---|
|**Message Integrity (무결성 보장)**|이메일 내용이 변조되지 않았음을 증명|
|**Sender Authentication (송신자 인증)**|이메일이 신뢰할 수 있는 발신자로부터 왔음을 확인|
|**Non-Repudiation (부인 방지)**|발신자가 이메일을 보냈다는 사실을 부인할 수 없음|

📌 **Digital Signature Example**

1. **송신자**: 이메일 내용의 해시 값을 생성하고, 개인 키로 암호화하여 서명 추가
2. **수신자**: 송신자의 공개 키로 서명을 검증하여 무결성 확인

✅ **S/MIME과 PGP는 이메일에 디지털 서명을 포함하여 보안을 강화할 수 있음**.

##### **💡 Real-Life Example (실생활 예시)**

> - **회사에서 임원이 직원에게 공식 이메일을 보낼 때 디지털 서명을 사용하여 위조 방지**
> - **정부 기관에서 중요한 문서를 이메일로 전송할 때 디지털 서명을 적용하여 무결성 보장**

---

## **8.5.4 Authentication Protocols for E-Mail Security (이메일 인증 프로토콜: 스푸핑 방지)**

### **설명 (Explanation)**

스푸핑(Spoofing)과 피싱(Phishing)을 방지하기 위해 이메일 송신자의 신원을 검증하는 인증 프로토콜이 사용됨.

### **1️⃣ 주요 이메일 인증 프로토콜 (E-Mail Authentication Protocols)**

|프로토콜|설명|
|---|---|
|**SPF (Sender Policy Framework)**|발신자가 승인된 이메일 서버를 사용하고 있는지 확인|
|**DKIM (DomainKeys Identified Mail)**|이메일에 디지털 서명을 포함하여 무결성 보장|
|**DMARC (Domain-based Message Authentication, Reporting & Conformance)**|SPF 및 DKIM을 기반으로 피싱 이메일을 차단|

📌 **SPF, DKIM, DMARC 동작 예제**

markdown

CopyEdit

`이메일 수신 시 → SPF 검사: 발신 IP가 도메인과 일치하는지 확인            → DKIM 검사: 디지털 서명을 확인하여 메시지 변조 여부 검증            → DMARC 검사: SPF/DKIM이 실패한 경우 정책 적용 (차단 또는 경고)`

✅ **SPF, DKIM, DMARC는 Gmail, Yahoo, Outlook 같은 이메일 서비스에서 사용되며, 피싱 방지 기능을 강화함**.

##### **💡 Real-Life Example (실생활 예시)**

> - **은행에서 발송한 이메일이 SPF, DKIM, DMARC 검사를 통과하지 못하면 스팸 처리됨**
> - **회사 이메일 서버에서 SPF 설정을 하지 않으면 공격자가 쉽게 이메일을 위장하여 사칭 가능**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **이메일 보안은 피싱, 스푸핑, 도청, 악성 코드 전파 등의 위협을 방지하기 위해 필요하다.**
2. **PGP, S/MIME을 활용하여 이메일 암호화를 수행하고, TLS를 사용하여 서버 간 안전한 전송을 보장한다.**
3. **디지털 서명은 이메일 무결성과 송신자 인증을 보장하여 위조 및 변조를 방지한다.**
4. **SPF, DKIM, DMARC 같은 이메일 인증 프로토콜을 사용하여 스푸핑 및 피싱 공격을 방어할 수 있다.**

🚀 **한 문장 요약:**  
**이메일 보안을 위해 암호화(PGP, S/MIME), 디지털 서명, 인증 프로토콜(SPF, DKIM, DMARC)을 활용하여 무결성, 인증, 기밀성을 보장해야 한다.**