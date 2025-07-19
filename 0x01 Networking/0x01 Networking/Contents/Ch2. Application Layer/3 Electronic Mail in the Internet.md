[[Application Layer]]

#### **요약 (Summary)**

전자 메일(E-mail)은 인터넷에서 가장 오래된 **network applications(네트워크 애플리케이션)** 중 하나로, **store-and-forward model(저장 및 전달 모델)**을 기반으로 동작한다.  
이메일 시스템은 **Mail Servers(메일 서버), Mail Clients(메일 클라이언트), Email Protocols(이메일 프로토콜)**로 구성되며, 주요 프로토콜로 **SMTP, POP3, IMAP**이 사용된다.

---

## **2.3.1 Basic Components of Electronic Mail (이메일 시스템의 기본 구성 요소)**

### **설명 (Explanation)**

이메일 시스템은 세 가지 주요 구성 요소로 이루어져 있다.

1. **Mail User Agents (MUA) – 메일 클라이언트**
    
    - 이메일을 작성하고 보내는 프로그램 (예: Outlook, Gmail, Apple Mail)
    - 사용자가 직접 이메일을 읽고 작성하는 인터페이스 제공
2. **Mail Servers (메일 서버)**
    
    - 이메일을 저장하고, 송신 및 수신을 담당하는 서버
    - 두 개의 큐(Outgoing, Incoming)를 관리하여 메일을 보관 및 전달
3. **Simple Mail Transfer Protocol (SMTP) – 이메일 전송 프로토콜**
    
    - 메일 서버 간 **전송**을 담당하는 **push-based** 프로토콜
    - 기본적으로 **TCP 포트 25** 사용

##### **💡 Real-Life Example (실생활 예시)**

> 이메일 시스템은 **우편 시스템**과 유사하다.
> 
> - MUA는 **우체국에서 편지를 작성하는 것**
> - Mail Server는 **우체국에서 편지를 보관하고 분류하는 역할**
> - SMTP는 **우편 트럭이 다른 도시로 편지를 배달하는 과정**

---

## **2.3.2 SMTP: Simple Mail Transfer Protocol (SMTP 프로토콜)**

### **설명 (Explanation)**

**SMTP(Simple Mail Transfer Protocol)**는 **메일을 서버 간 전송하는 프로토콜**로, **store-and-forward 방식**을 사용한다.  
SMTP는 **ASCII 텍스트 기반 프로토콜**이며, 메일 내용과 헤더를 전송하는 역할을 한다.

### **SMTP의 주요 특징**

- **Push-based protocol (푸시 방식 프로토콜)**
    - 클라이언트가 서버에 메일을 보내면, 즉시 다른 서버로 전송
- **Persistent TCP connection (지속적인 TCP 연결 사용)**
    - **TCP 포트 25**를 사용하여 신뢰성 있는 메일 전송
- **7-bit ASCII text only (텍스트 기반 전송)**
    - 첨부 파일(Binary Data)을 보내려면 **MIME(Multipurpose Internet Mail Extensions)** 사용

### **SMTP 메시지 포맷**

SMTP는 **메시지 헤더(Header)와 본문(Body)**으로 구성된다.

#### **SMTP 메시지 예시**

```http
MAIL FROM: <alice@example.com> 
RCPT TO: <bob@example.com> 
DATA Subject: Hello Bob Hi Bob, how are you? 
. 
QUIT
```

- `MAIL FROM`: 발신자 이메일 주소
- `RCPT TO`: 수신자 이메일 주소
- `DATA`: 본문 시작
- `QUIT`: SMTP 세션 종료

##### **💡 Real-Life Example (실생활 예시)**

> **SMTP는 우체국의 "편지 발송 시스템"과 같다.**
> 
> - 발신자(MAIL FROM)가 우체국에 가서 수신자(RCPT TO)에게 편지를 보낸다.
> - SMTP는 이 편지를 **다른 우체국(메일 서버)으로 전달하는 역할**을 한다.

---

## **2.3.3 Mail Access Protocols: POP3, IMAP (메일 접근 프로토콜)**

### **설명 (Explanation)**

SMTP가 이메일을 **전송**하는 역할을 한다면,  
**POP3(Post Office Protocol)와 IMAP(Internet Message Access Protocol)**은 이메일을 **수신하고 관리하는 프로토콜**이다.

### **1️⃣ POP3 (Post Office Protocol)**

- **다운로드 & 삭제 모델**
    - 클라이언트가 서버에서 이메일을 다운로드 후 삭제
    - 한 번 받은 이메일은 **서버에서 삭제되므로, 여러 기기에서 동기화 불가능**
- **단순한 프로토콜 (stateless)**
    - 서버는 클라이언트가 메일을 가져가면 더 이상 저장하지 않음

##### **💡 Real-Life Example (실생활 예시)**

> **POP3는 우체통에서 편지를 꺼내면 자동으로 삭제되는 방식**
> 
> - 한 번 편지를 꺼내면 다시 되돌릴 수 없음

---

### **2️⃣ IMAP (Internet Message Access Protocol)**

- **서버에서 이메일을 유지하며 동기화 지원**
    - 여러 기기에서 동일한 이메일을 확인 가능
    - 이메일을 읽거나 삭제해도 모든 기기에서 동일하게 반영됨
- **계층적 폴더 구조 지원**
    - 이메일을 폴더별로 정리 가능

##### **💡 Real-Life Example (실생활 예시)**

> **IMAP은 편지가 우체국 서버에 저장된 채, 여러 곳에서 열람할 수 있는 방식**
> 
> - 편지를 읽어도 사라지지 않고, 어느 기기에서나 확인 가능

---

## **2.3.4 Web-Based Email (웹 기반 이메일, Gmail 같은 서비스)**

### **설명 (Explanation)**

웹메일(Gmail, Yahoo Mail 등)은 별도의 클라이언트 프로그램 없이, **웹 브라우저에서 이메일을 송수신하는 방식**이다.  
웹메일 서비스는 내부적으로 **SMTP(메일 전송), IMAP/POP3(메일 수신)**을 사용하지만, 사용자는 **HTTP/HTTPS**를 통해 이메일을 관리한다.

### **웹 기반 이메일의 장점**

1. **어디서나 접근 가능 (Anywhere Access)**
    - 별도의 이메일 클라이언트 설치 없이, 브라우저만 있으면 사용 가능
2. **서버 저장 방식 (Server-side Storage)**
    - 이메일이 서버에 저장되므로, 기기 분실 시에도 데이터 보호 가능
3. **클라우드 기능 지원**
    - Google Drive, OneDrive 등과 연계 가능

##### **💡 Real-Life Example (실생활 예시)**

> **웹메일은 "공용 우체국 사서함"과 같다.**
> 
> - 어디서든 인터넷이 있으면 접속 가능하고, 데이터를 잃어버릴 걱정이 없음.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **이메일 시스템의 구성 요소**
    
    - **Mail User Agent (MUA):** 사용자가 메일을 보내고 읽는 프로그램 (Gmail, Outlook)
    - **Mail Server:** 메일을 저장하고 전송하는 서버
    - **SMTP:** 메일을 서버 간 전송하는 프로토콜 (TCP 포트 25 사용)
2. **메일 접근 프로토콜**
    
    - **POP3:** 서버에서 메일을 다운로드 후 삭제 (싱글 디바이스)
    - **IMAP:** 서버에서 메일을 유지하며 동기화 가능 (멀티 디바이스)
3. **웹 기반 이메일 (Gmail, Yahoo Mail)**
    
    - 브라우저에서 HTTP/HTTPS를 이용해 이메일 관리

🚀 **한 문장 요약:**  
이메일은 **SMTP(전송), POP3/IMAP(수신)**을 통해 동작하며, 웹메일은 HTTP를 이용하여 어디서든 이메일을 관리할 수 있다.