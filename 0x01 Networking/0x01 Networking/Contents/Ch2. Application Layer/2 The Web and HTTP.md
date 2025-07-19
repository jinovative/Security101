[[Application Layer]]
#### **요약 (Summary)**

웹은 **HyperText Transfer Protocol(HTTP)**을 사용하여 **client(클라이언트, 웹 브라우저)**와 **server(서버, 웹사이트 제공자)** 간 데이터를 주고받는다.  
HTTP는 **stateless(상태를 저장하지 않는)** 프로토콜이며, **request-response model(요청-응답 방식)**을 기반으로 작동한다.

---

## **2.2.1 Overview of HTTP (HTTP 개요)**

### **설명 (Explanation)**

**HTTP(HyperText Transfer Protocol)**는 웹에서 데이터를 전송하는 **애플리케이션 계층 프로토콜(Application Layer Protocol)**이다.  
HTTP는 **TCP 기반의 클라이언트-서버 모델**을 사용하며, 일반적으로 **port 80 (HTTP), port 443 (HTTPS)**에서 동작한다.

### **HTTP의 특징**

1. **Client-Server Model (클라이언트-서버 모델)**
    
    - 클라이언트(웹 브라우저)가 서버에 요청을 보내고, 서버는 응답을 반환.
    - **예시:** Google Chrome이 `www.google.com` 요청 → 구글 서버가 HTML 페이지 반환.
2. **Stateless (무상태 프로토콜)**
    
    - 서버는 이전 요청 정보를 저장하지 않음.
    - 로그인 정보 등 상태 유지가 필요할 경우 **cookies(쿠키)** 사용.
3. **Request-Response Model (요청-응답 모델)**
    
    - **클라이언트가 HTTP 요청(request)**을 보내면,
    - **서버가 HTTP 응답(response)**을 반환.

##### **💡 Real-Life Example (실생활 예시)**

> HTTP는 **식당에서 주문하는 과정**과 같다.
> 
> - 고객(클라이언트)이 메뉴를 주문(HTTP 요청)하면,
> - 주방(서버)이 음식을 준비해 제공(HTTP 응답)하는 방식.

---

## **2.2.2 Non-Persistent & Persistent Connections (비연결형 & 지속형 HTTP 연결)**

### **설명 (Explanation)**

HTTP는 **연결 방식(connection method)**에 따라 **비연결형(Non-Persistent)**과 **지속형(Persistent)**으로 나뉜다.

### **1️⃣ Non-Persistent HTTP (비연결형 HTTP)**

- **각 요청마다 새로운 TCP 연결을 생성**하고, 응답 후 연결 종료.
- 한 페이지에 여러 개의 요소(HTML, CSS, 이미지 등)가 있다면, 각각의 요청마다 새로운 TCP 연결을 열어야 함.
- **단점:** TCP 연결 설정/해제 과정이 많아 **지연(latency)** 증가.

### **2️⃣ Persistent HTTP (지속형 HTTP)**

- **하나의 TCP 연결을 유지한 채 여러 요청을 처리.**
- HTTP/1.1부터 기본적으로 사용됨.
- **장점:** TCP 연결 설정 비용 감소, 성능 향상.

##### **💡 Real-Life Example (실생활 예시)**

> - **Non-Persistent HTTP**는 **음식을 하나 주문할 때마다 새로 계산하는 것**과 같다.
> - **Persistent HTTP**는 **한 번에 여러 개를 주문하고 한 번만 결제하는 것**과 같다.

---

## **2.2.3 HTTP Request and Response Messages (HTTP 요청 및 응답 메시지)**

### **설명 (Explanation)**

HTTP 메시지는 **Request(요청)**과 **Response(응답)** 두 가지 형태가 있으며, **텍스트 기반의 메시지 구조**를 가진다.

### **1️⃣ HTTP Request Message (HTTP 요청 메시지)**

클라이언트(웹 브라우저)가 서버에 보내는 요청 메시지.

#### **요청 메시지 구조**
```
GET /index.html 
HTTP/1.1 Host: www.example.com 
User-Agent: Mozilla/5.0 
Accept-Language: en-us
```


- **Request Line**: 요청 방식(예: `GET /index.html HTTP/1.1`)
- **Header Fields**: 추가적인 요청 정보 (Host, User-Agent 등)
- **(Optional) Body**: 요청 데이터 (POST 요청 시 사용)

### **2️⃣ HTTP Response Message (HTTP 응답 메시지)**

서버가 클라이언트 요청에 대해 반환하는 응답 메시지.

#### **응답 메시지 구조**

```
HTTP/1.1 200 OK 
Date: Sat, 08 Mar 2025 12:00:00 GMT 
Content-Type: text/html 
Content-Length: 1024  
<html>...</html>
```

- **Status Line**: 응답 상태 코드 (예: `HTTP/1.1 200 OK`)
- **Header Fields**: 추가적인 응답 정보 (Date, Content-Type 등)
- **Body**: 실제 웹 페이지 데이터 (HTML, JSON 등)

##### **💡 Real-Life Example (실생활 예시)**

> HTTP 요청과 응답은 **편의점에서 상품을 구매하는 과정**과 같다.
> 
> - 고객(클라이언트)이 상품을 요청하면(HTTP 요청),
> - 점원(서버)이 상품을 찾아 제공하고 영수증(HTTP 응답)을 반환한다.

---

## **2.2.4 HTTP Status Codes (HTTP 상태 코드)**

### **설명 (Explanation)**

서버는 응답 메시지에서 **Status Code(상태 코드)**를 통해 요청의 처리 결과를 알린다.

### **주요 HTTP 상태 코드**

| 코드                            | 의미                        |
| ----------------------------- | ------------------------- |
| **200 OK**                    | 요청 성공                     |
| **301 Moved Permanently**     | 요청한 리소스가 영구적으로 이동됨 (리디렉션) |
| **400 Bad Request**           | 클라이언트 요청 오류               |
| **403 Forbidden**             | 접근 권한 없음                  |
| **404 Not Found**             | 요청한 리소스를 찾을 수 없음          |
| **500 Internal Server Error** | 서버 내부 오류 발생               |

##### **💡 Real-Life Example (실생활 예시)**

> - **200 OK** → **주문한 음식이 정상적으로 제공됨**
> - **404 Not Found** → **식당에서 주문한 메뉴가 없는 경우**
> - **500 Internal Server Error** → **주방에서 요리를 하다가 실수로 태운 경우**

---

## **2.2.5 Cookies and Sessions (쿠키와 세션)**

### **설명 (Explanation)**

HTTP는 **stateless(상태를 저장하지 않음)**이므로, **쿠키(Cookie)**와 **세션(Session)**을 사용하여 **사용자 정보를 유지**할 수 있다.

### **1️⃣ Cookies (쿠키)**

- 서버가 클라이언트에 작은 데이터를 저장하여 **사용자 정보를 유지**.
- **예시:** 로그인 유지, 장바구니 정보 저장.
- 클라이언트가 요청할 때마다 쿠키 정보를 서버에 자동 전송.

### **2️⃣ Sessions (세션)**

- 서버 측에서 사용자의 상태를 저장하는 방식.
- 보안이 중요한 정보(예: 로그인 상태)를 유지할 때 사용.

##### **💡 Real-Life Example (실생활 예시)**

> - **쿠키(Cookies)** → **식당에서 받은 "단골 고객 카드"** (손님이 보관)
> - **세션(Sessions)** → **식당의 예약 명부(가게가 보관)**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **HTTP는 웹에서 데이터를 주고받는 프로토콜로, 무상태(stateless)이며 클라이언트-서버 모델을 따른다.**
2. **비연결형 HTTP(Non-Persistent)는 매 요청마다 새로운 연결을 사용하고, 지속형 HTTP(Persistent)는 하나의 연결을 유지한다.**
3. **HTTP 요청(Request)과 응답(Response)은 텍스트 기반 메시지로, 상태 코드(Status Code)를 통해 요청 결과를 전달한다.**
4. **쿠키와 세션은 HTTP의 무상태성을 보완하여 사용자 정보를 유지하는 방식이다.**

🚀 **한 문장 요약:**  
웹은 **HTTP 프로토콜**을 사용하여 클라이언트와 서버가 데이터를 주고받으며, **쿠키와 세션**을 통해 상태를 유지할 수 있다.