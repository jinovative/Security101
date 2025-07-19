[[Application Layer]]

#### **요약 (Summary)**

**Peer-to-Peer (P2P) applications**은 **centralized server(중앙 서버)** 없이 **peers(사용자들)** 간에 직접 데이터를 교환하는 네트워크 애플리케이션 모델이다.  
P2P는 **scalability(확장성), cost efficiency(비용 절감)** 등의 장점이 있지만, **security(보안 문제), management(관리 어려움)** 등의 단점도 있다.  
대표적인 P2P 애플리케이션으로 **BitTorrent(파일 공유), Skype(VoIP), Bitcoin(블록체인)** 등이 있다.

---

## **2.5.1 P2P Architecture vs. Client-Server Architecture (P2P vs. 클라이언트-서버 아키텍처 비교)**

### **설명 (Explanation)**

P2P 모델은 **Client-Server 모델**과 비교했을 때 **분산(distributed)** 구조를 가지며, 모든 노드가 동등한 역할을 수행할 수 있다.

### **1️⃣ Client-Server Model (클라이언트-서버 모델)**

- **중앙 서버(Server)가 모든 요청을 처리**
- **클라이언트(Client)는 서버에 요청만 수행**
- **확장성이 낮음 (서버 부하 증가)**
- **예시:** 웹사이트(HTTP), 이메일(SMTP), 온라인 게임

### **2️⃣ Peer-to-Peer Model (P2P 모델)**

- **모든 노드(peer)가 동등한 역할** 수행
- **서버 없이 직접 데이터를 공유**
- **사용자가 많아질수록 성능 향상 (Self-Scalability)**
- **예시:** BitTorrent, Skype, Bitcoin

##### **💡 Real-Life Example (실생활 예시)**

> - **Client-Server Model**은 **도서관 시스템**과 같다.
>     - 사람들이 중앙 서버(도서관)에서 책을 빌림.
> - **P2P Model**은 **친구들끼리 직접 책을 교환하는 것**과 같다.
>     - 중앙 서버 없이 **사용자 간 직접 파일 공유 가능**.

---

## **2.5.2 P2P File Sharing (P2P 파일 공유)**

### **설명 (Explanation)**

P2P 네트워크에서 가장 널리 사용되는 애플리케이션 중 하나는 **파일 공유(File Sharing)**이다.  
대표적인 P2P 파일 공유 프로토콜은 **BitTorrent**이며, 이를 통해 대용량 파일을 빠르게 공유할 수 있다.

### **BitTorrent File Sharing**

BitTorrent는 **파일을 작은 청크(chunk)로 나누어 여러 피어에서 동시에 다운로드**할 수 있도록 설계된 P2P 프로토콜이다.

### **BitTorrent 동작 방식**

1. **Torrent 파일 다운로드**
    - 사용자는 `.torrent` 파일을 통해 어떤 파일을 다운로드할지 결정
2. **Tracker 서버 연결**
    - Tracker는 피어들의 정보를 저장하고, 새 사용자가 네트워크에 참여하도록 돕는다.
3. **Peers 간 파일 공유**
    - Peers는 파일의 조각을 서로 공유하며, 다운로드 속도가 빨라짐.
4. **Seeding (업로드 역할 수행)**
    - 파일을 모두 다운로드한 후에도 계속 업로드하는 역할을 수행하는 사용자를 **Seeder(시더)**라고 함.

##### **💡 Real-Life Example (실생활 예시)**

> - **BitTorrent는 여러 사람에게 동시에 복사본을 받는 것과 같다.**
> - 도서관에서 한 권의 책을 차례로 빌리는 것(클라이언트-서버) 대신,
> - **여러 사람이 동시에 페이지를 복사하여 빠르게 책을 완성하는 방식(P2P)**.

---

## **2.5.3 Distributed Hash Table (DHT) – 분산 해시 테이블**

### **설명 (Explanation)**

P2P 네트워크에서 **검색(lookup)과 데이터 저장(distributed storage)**을 효율적으로 수행하기 위해 **DHT(Distributed Hash Table, 분산 해시 테이블)**이 사용된다.

### **DHT의 주요 특징**

- **Centralized Tracker 없이 데이터 위치 관리**
- **Key-Value Pair 기반 검색 시스템**
- **각 Peer가 일부 데이터를 저장하며 전체 데이터베이스를 분산 저장**

### **DHT 동작 방식 (예: Kademlia DHT 사용)**

1. **파일을 Key(해시 값)로 변환**
2. **네트워크에서 Key와 가장 가까운 Peer를 찾음**
3. **Peer가 해당 파일 조각을 가지고 있으면 다운로드 진행**

##### **💡 Real-Life Example (실생활 예시)**

> - **DHT는 도서관의 색인(index) 시스템과 같다.**
> - 특정 키워드(해시 값)를 검색하면, 관련된 책(파일)을 보유한 사람이 어디에 있는지 알 수 있다.

---

## **2.5.4 P2P Applications Beyond File Sharing (파일 공유 외의 P2P 애플리케이션)**

### **설명 (Explanation)**

P2P 기술은 **파일 공유** 외에도 다양한 분야에서 활용된다.

### **1️⃣ VoIP & Video Streaming (음성 및 영상 통화)**

- **Skype**: P2P 기반 VoIP 서비스 (일부 서버 필요)
- **Zoom, WebRTC**: 일부 P2P 기술을 활용한 영상 통화

### **2️⃣ Blockchain & Cryptocurrencies (블록체인 & 암호화폐)**

- **Bitcoin, Ethereum**: 중앙 서버 없이 **분산 원장(distributed ledger)** 관리
- **P2P 네트워크에서 트랜잭션(transaction) 검증** 수행

### **3️⃣ Cloud Storage (P2P 클라우드 저장소)**

- **IPFS (InterPlanetary File System)**: P2P 기반의 파일 저장 시스템
- **Storj, Sia**: 블록체인과 결합한 탈중앙화 클라우드 스토리지

##### **💡 Real-Life Example (실생활 예시)**

> - **Skype의 P2P 통신은 친구들끼리 직접 전화하는 것과 같다.**
> - **Bitcoin은 은행 없이 직접 송금하는 방식**.

---

## **2.5.5 Challenges of P2P Networks (P2P 네트워크의 한계점)**

### **설명 (Explanation)**

P2P 모델은 여러 가지 장점이 있지만, 몇 가지 한계점도 존재한다.

### **1️⃣ Security & Trust Issues (보안 및 신뢰 문제)**

- **악성 파일(virus, malware) 공유 가능성**
- **DHT 기반 네트워크에서 악의적인 피어가 데이터 조작 가능**

### **2️⃣ Resource Management (자원 관리 문제)**

- 사용자의 업로드 참여도가 낮아지면 **파일 공유 속도 저하**
- P2P 네트워크는 항상 안정적인 연결을 보장하지 않음

### **3️⃣ Legal & Ethical Issues (법적 문제)**

- **불법 파일 공유 (저작권 침해) 문제**
- 일부 국가에서는 P2P 네트워크 사용을 제한하거나 금지

##### **💡 Real-Life Example (실생활 예시)**

> - **P2P의 보안 문제는 마켓플레이스에서 사기를 당할 가능성과 같다.**
> - **악성 사용자(peer)가 신뢰성을 저하시킬 수 있음**.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **P2P vs. Client-Server Architecture**
    
    - P2P는 중앙 서버 없이 **Peers 간 직접 통신 가능**
    - Client-Server 모델은 서버를 중심으로 데이터 교환
2. **P2P File Sharing (BitTorrent)**
    
    - **여러 Peer에서 동시에 다운로드 → 빠른 전송 속도 제공**
3. **Distributed Hash Table (DHT)**
    
    - **중앙 서버 없이 파일 위치를 검색할 수 있는 기술**
4. **P2P Applications**
    
    - **VoIP (Skype), 블록체인(Bitcoin), P2P 클라우드(IPFS)**
5. **Challenges of P2P Networks**
    
    - **보안 문제, 자원 관리 어려움, 법적 문제 발생 가능**

🚀 **한 문장 요약:**  
P2P 애플리케이션은 **파일 공유, VoIP, 블록체인 등 다양한 분야에서 활용되며**, **확장성(Self-scalability)과 비용 절감 효과가 있지만, 보안 및 관리 문제가 존재한다.**