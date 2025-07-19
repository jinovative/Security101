[[Application Layer]]

#### **요약 (Summary)**

**DNS(Domain Name System)**는 **human-friendly domain names(사용자가 이해하기 쉬운 도메인 이름)**을 **IP addresses(컴퓨터가 인식하는 IP 주소)**로 변환하는 인터넷의 디렉터리 서비스이다.  
예를 들어, 사용자가 `www.google.com`을 입력하면 **DNS가 이를 IP 주소(예: 142.250.190.14)로 변환**하여 해당 서버와 연결할 수 있도록 해준다.  
DNS는 **분산형 계층 구조(distributed hierarchical system)**로 설계되어 있어, 수많은 도메인 이름을 빠르고 효율적으로 처리할 수 있다.

---

## **2.4.1 Why Not Just Use IP Addresses? (왜 IP 주소 대신 도메인 이름을 사용할까?)**

### **설명 (Explanation)**

IP 주소만으로 통신이 가능하지만, 사용자가 IP 주소를 직접 입력하는 것은 비효율적이다.

- **인간 친화적인 주소 필요**
    - `216.58.221.36` 대신 `www.google.com`을 입력하는 것이 훨씬 쉽다.
- **IP 주소는 변경될 수 있음**
    - 서버가 이동하거나 네트워크 구조가 변경되면 IP 주소가 바뀔 수 있으므로, 도메인 이름을 사용하면 유연성이 증가한다.
- **도메인 기반 서비스 제공 가능**
    - 한 IP 주소에 여러 도메인을 매핑하여 다양한 웹사이트를 운영할 수 있다.

##### **💡 Real-Life Example (실생활 예시)**

> **DNS는 스마트폰의 연락처 목록과 같다.**
> 
> - 전화번호(숫자)를 직접 외우는 대신, **이름(도메인 이름)**을 검색하여 쉽게 전화를 걸 수 있다.

---

## **2.4.2 DNS Overview (DNS 개요)**

### **설명 (Explanation)**

DNS는 **분산형(distributed) 네트워크 시스템**으로, 전 세계에 걸쳐 수많은 서버가 협력하여 작동한다.

### **DNS의 주요 기능**

1. **Host Name to IP Address Translation (호스트 이름 → IP 주소 변환)**
    - 예: `www.amazon.com` → `205.251.242.103`
2. **Load Balancing (부하 분산)**
    - 하나의 도메인에 여러 IP 주소를 할당하여 트래픽을 분산 (예: `youtube.com`이 여러 서버에 연결 가능)
3. **Email Routing (이메일 라우팅)**
    - 도메인 기반 이메일 전송 지원 (`@gmail.com` → Google의 메일 서버)

---

## **2.4.3 DNS Hierarchy (DNS 계층 구조)**

### **설명 (Explanation)**

DNS는 **계층적(hierarchical) 구조**를 가지며, 총 4단계로 이루어져 있다.

### **1️⃣ Root DNS Servers (루트 DNS 서버)**

- **전 세계에 13개 루트 서버(cluster) 존재** (`A-root`, `B-root` … `M-root`)
- 도메인의 최상위 계층(`.com`, `.org`, `.net` 등) 담당
- 사용자가 `www.google.com`을 입력하면, 루트 서버는 **`.com` TLD 서버의 위치를 알려줌**.

### **2️⃣ Top-Level Domain (TLD) Servers (최상위 도메인 서버)**

- `.com`, `.org`, `.net`, `.edu`, `.gov` 등의 TLD(최상위 도메인) 관리
- `.com` 도메인의 경우 **VeriSign**, `.org`는 **PIR(Public Interest Registry)**에서 관리

### **3️⃣ Authoritative DNS Servers (권한 DNS 서버)**

- 특정 조직이나 회사가 관리하는 **실제 도메인 정보 저장소**
- 예: Google의 `ns1.google.com`, `ns2.google.com` 서버가 `www.google.com`의 IP 주소를 반환

### **4️⃣ Local DNS Resolver (로컬 DNS 리졸버)**

- ISP(인터넷 서비스 제공자) 또는 조직 내에서 DNS 요청을 캐싱하여 속도를 향상
- 예: KT, SKT, LG U+ 등의 ISP는 자체 DNS 리졸버 운영

##### **💡 Real-Life Example (실생활 예시)**

> **DNS 계층 구조는 도서관의 책 찾기 시스템과 같다.**
> 
> 1. 도서관 안내 데스크(루트 DNS 서버)에 가서 "어떤 섹션(TLD 서버)에 있는지" 묻는다.
> 2. 해당 섹션에 가서 "책을 어디서 찾을 수 있는지(권한 DNS 서버)" 확인한다.
> 3. 마지막으로 특정 서가에서 책을 찾는다.

---

## **2.4.4 DNS Name Resolution Process (DNS 이름 변환 과정)**

### **설명 (Explanation)**

DNS를 통해 도메인 이름을 IP 주소로 변환하는 과정을 **name resolution(이름 변환)**이라고 한다.

#### **DNS Query Flow (DNS 질의 과정)**

1. **Client(클라이언트)가 URL 입력**:
    - 예: 사용자가 `www.facebook.com`을 입력.
2. **Local DNS Resolver에 요청**:
    - 브라우저나 OS가 **캐시(cache)**를 먼저 확인.
    - 캐시에 없으면 ISP의 Local DNS Resolver로 요청.
3. **Recursive Query to Root Server (루트 서버 요청)**:
    - Local DNS Resolver가 루트 서버에 `.com` TLD 서버의 위치 요청.
4. **TLD Server Query (TLD 서버 요청)**:
    - `.com` TLD 서버가 `facebook.com`의 권한 DNS 서버 위치 반환.
5. **Authoritative DNS Server Query (권한 DNS 서버 요청)**:
    - `facebook.com`의 DNS 서버가 실제 IP 주소 반환.
6. **IP Address Returned (IP 주소 반환)**:
    - Local DNS Resolver가 IP 주소를 캐싱 후, 클라이언트에 전달.
7. **Client Connects to Server (클라이언트가 서버에 연결)**:
    - 웹 브라우저가 해당 IP 주소로 접속하여 웹사이트 로딩.

##### **💡 Real-Life Example (실생활 예시)**

> **DNS 질의 과정은 지도 앱에서 목적지를 검색하는 것과 같다.**
> 
> - 사용자가 `서울 타워`(도메인)를 검색하면,
> - 앱이 먼저 캐시된 데이터를 확인하고, 없으면
> - 네트워크를 통해 서버에서 실제 위치(IP 주소)를 찾는다.

---

## **2.4.5 DNS Caching (DNS 캐싱과 성능 최적화)**

### **설명 (Explanation)**

DNS 요청이 매번 루트 서버에서 시작되면 속도가 느려질 수 있기 때문에, **DNS 캐싱(DNS Caching)**을 통해 성능을 최적화한다.

- **Local DNS Resolver Caching**: ISP(인터넷 서비스 제공자)가 자주 요청되는 도메인을 저장.
- **Operating System Caching**: Windows, macOS, Linux 등이 최근 방문한 도메인을 캐싱.
- **Browser Caching**: 크롬, 파이어폭스 등 웹 브라우저가 자체적으로 DNS 정보를 저장.

##### **💡 Real-Life Example (실생활 예시)**

> DNS 캐싱은 **네비게이션의 즐겨찾기 기능**과 같다.
> 
> - 자주 가는 목적지를 검색하면 이전 기록이 저장되어 빠르게 길을 찾을 수 있다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **DNS는 도메인 이름을 IP 주소로 변환하는 역할을 하며, 인터넷의 "전화번호부"와 같다.**
2. **DNS는 계층적 구조를 가지며, 루트 DNS 서버 → TLD 서버 → 권한 DNS 서버 순으로 질의가 진행된다.**
3. **이름 변환 과정(Name Resolution)**에서 DNS는 캐싱을 활용하여 성능을 최적화한다.
4. **DNS는 Load Balancing(부하 분산), Email Routing(이메일 라우팅) 등의 기능도 수행한다.**

🚀 **한 문장 요약:**  
DNS는 **도메인 이름을 IP 주소로 변환하는 인터넷의 핵심 서비스**이며, **분산된 계층 구조와 캐싱 기법**을 통해 빠르고 효율적인 웹 접속을 지원한다.