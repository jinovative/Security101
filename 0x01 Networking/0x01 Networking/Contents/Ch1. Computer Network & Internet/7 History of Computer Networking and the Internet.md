[[Computer Networks and the Internet]] 

#### **요약 (Summary)**

컴퓨터 네트워크와 인터넷은 **1960년대 초 ARPAnet(아르파넷)**에서 시작되었으며, 이후 다양한 기술적 발전을 거치며 오늘날의 글로벌 네트워크로 성장했다.  
인터넷의 발전 과정은 크게 **Packet Switching(패킷 스위칭)의 탄생, ARPAnet 구축, TCP/IP 프로토콜 개발, 인터넷의 상업화 및 웹의 등장**으로 나눌 수 있다.

---

## **1.7.1 The Development of Packet Switching (1961–1972)**

### **설명 (Explanation)**

인터넷의 기반이 되는 **Packet Switching(패킷 스위칭)** 개념은 1960년대 초반 개발되었다.

- **Leonard Kleinrock (MIT, 1961)**
    - **Packet Switching** 개념을 제안하여, **circuit switching(회선 교환)**보다 효율적임을 증명
- **Paul Baran (RAND Corporation, 1964)**
    - 군사적 목적의 **분산 네트워크(Distributed Network)** 개념을 제안
- **Donald Davies (NPL, 영국, 1965)**
    - 패킷 교환이라는 용어 **"packet switching"**을 처음 사용

이 연구들은 후에 **ARPAnet(Advanced Research Projects Agency Network)** 구축의 기반이 되었다.

### **ARPAnet (1969)**

- 미 국방부 **ARPA(Advanced Research Projects Agency)** 주도로 개발
- **첫 패킷 스위칭 네트워크**
- **UCLA, Stanford Research Institute, UCSB, University of Utah** 간 최초 연결 (1969년)
- **1972년**: ARPAnet에 첫 번째 이메일 전송

##### **💡 Real-Life Example (실생활 예시)**

> **Packet Switching**은 **택배 시스템**과 같다.  
> 대형 화물을 작은 박스로 나누어(패킷) 각각 다른 경로로 배송한 후, 목적지에서 다시 조립하는 방식.

---

## **1.7.2 Proprietary Networks and Internetworking (1972–1980)**

### **설명 (Explanation)**

ARPAnet 외에도 여러 네트워크가 등장하면서, **Internetworking(네트워크 간 연결)** 개념이 필요해졌다.

- **ALOHA Network (1970, 하와이 대학)**
    
    - 무선 패킷 라디오 네트워크 개발
    - 이후 **Ethernet(이더넷, 1973)** 개발에 영향
- **TCP/IP Protocol (1974, Vinton Cerf & Robert Kahn)**
    
    - 여러 네트워크를 연결하는 **Internetworking(인터네트워킹) 개념** 도입
    - TCP/IP는 **1983년 ARPAnet의 공식 프로토콜**로 채택됨
- **X.25 Protocol (1976)**
    
    - IBM과 유럽에서 개발된 **패킷 교환 프로토콜**
    - 전화망 기반의 데이터 통신을 지원

##### **💡 Real-Life Example (실생활 예시)**

> **TCP/IP**는 **여러 나라의 우편 시스템을 통합하는 국제 우편 규격과 같다.**  
> 각국의 시스템이 다르더라도 동일한 프로토콜(TCP/IP)을 사용하면 서로 데이터를 주고받을 수 있다.

---

## **1.7.3 A Proliferation of Networks (1980–1990)**

### **설명 (Explanation)**

1980년대는 인터넷 확산의 시기로, 다양한 네트워크가 발전하였다.

- **NSFNET (1986)**
    
    - **National Science Foundation(미국 NSF)**에서 개발한 **초고속 백본 네트워크**
    - ARPAnet을 대체하며, 상업적 인터넷의 기반이 됨
- **BITNET, CSNET (1980년대 초반)**
    
    - 대학과 연구소를 연결하는 네트워크
    - 이메일, 파일 전송 지원
- **DNS (1983)**
    
    - **도메인 네임 시스템(Domain Name System)** 도입
    - IP 주소 대신 **[www.example.com](http://www.example.com)** 같은 도메인 사용 가능
- **Minitel (1984, 프랑스)**
    
    - 전화선 기반 온라인 서비스 제공 (초기 인터넷 서비스 형태)

##### **💡 Real-Life Example (실생활 예시)**

> **DNS**는 **전화번호부와 같다.**  
> 사람들은 IP 주소(숫자)를 외우는 대신, **도메인 네임(www.google.com)**을 사용한다.

---

## **1.7.4 The Internet Explosion (1990s)**

### **설명 (Explanation)**

1990년대는 인터넷이 대중화된 시기이며, **World Wide Web(WWW)의 등장**이 가장 중요한 사건이다.

- **ARPAnet 종료 (1990)**
    - NSFNET이 인터넷 백본을 담당하며, 상업적 이용 가능해짐
- **World Wide Web (WWW, 1989–1991)**
    - **Tim Berners-Lee (CERN)**가 개발
    - **HTML, HTTP, 웹 브라우저** 개념 등장
- **Netscape (1994)**
    - 최초의 대중적 웹 브라우저
    - 인터넷 대중화를 촉진
- **Amazon, eBay, Yahoo (1995)**
    - 전자상거래(E-commerce) 시장 형성

##### **💡 Real-Life Example (실생활 예시)**

> **WWW의 탄생은 인쇄술 발명과 같다.**  
> 정보를 쉽게 공유하고 접근할 수 있게 하여 인터넷 혁명을 가져왔다.

---

## **1.7.5 The New Millennium (2000s–현재)**

### **설명 (Explanation)**

2000년대 이후 인터넷은 급격히 성장하며, **모바일 네트워크, 소셜 미디어, 클라우드 컴퓨팅** 등이 등장했다.

- **Broadband Expansion (광대역 인터넷 확산)**
    - DSL, Cable, Fiber-to-the-Home(FTTH) 보급 확대
- **Mobile Internet (모바일 인터넷)**
    - **3G(2000s), 4G LTE(2010s), 5G(2020s)**
    - 스마트폰, 태블릿 중심의 인터넷 사용 증가
- **Social Media (소셜 미디어)**
    - Facebook, Twitter, Instagram, TikTok 등
- **Cloud Computing (클라우드 컴퓨팅)**
    - AWS, Google Cloud, Microsoft Azure
    - 기업과 개인이 서버를 직접 운영할 필요 없음

##### **💡 Real-Life Example (실생활 예시)**

> **클라우드 컴퓨팅은 전기 공급 시스템과 같다.**  
> 과거에는 기업이 자체 발전기를 운영해야 했지만, 지금은 **클라우드 서비스(AWS, Google Cloud)**를 이용해 필요할 때만 컴퓨팅 자원을 사용한다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **1960s**: Packet Switching 개념 개발, ARPAnet 탄생 (최초의 패킷 스위칭 네트워크)
2. **1970s**: TCP/IP 프로토콜 개발 → 인터넷의 기초 확립
3. **1980s**: NSFNET 도입, DNS 등장 → 인터넷 확장
4. **1990s**: World Wide Web(WWW)과 웹 브라우저의 등장 → 인터넷 대중화
5. **2000s–현재**: 모바일 인터넷, 소셜 미디어, 클라우드 컴퓨팅의 발전

🚀 **한 문장 요약:**  
인터넷은 **Packet Switching(1960s) → TCP/IP(1970s) → WWW(1990s) → Mobile & Cloud(2000s~현재)**의 발전 단계를 거치며 글로벌 네트워크로 성장했다.