[[Application Layer]]

#### **요약 (Summary)**

비디오 스트리밍(Video Streaming)은 네트워크를 통해 실시간 또는 주문형(VoD, Video on Demand) 방식으로 동영상을 전송하는 방식이다.  
이 과정에서 **latency(지연), buffering(버퍼링), network congestion(네트워크 혼잡)** 등의 문제가 발생할 수 있으며, 이를 해결하기 위해 **Content Distribution Networks (CDNs, 콘텐츠 전송 네트워크)**가 사용된다.  
CDN은 **전 세계 여러 서버에 콘텐츠를 분산 저장**하여, 사용자가 가까운 서버에서 데이터를 받아볼 수 있도록 최적화된 구조를 제공한다.

---

## **2.6.1 Video Streaming Basics (비디오 스트리밍 기초 개념)**

### **설명 (Explanation)**

비디오 스트리밍은 데이터를 **연속적으로 다운로드하며 재생하는 방식**으로, 크게 **Live Streaming(실시간 스트리밍)**과 **On-Demand Streaming(주문형 스트리밍, VoD)**으로 나뉜다.

### **1️⃣ Live Streaming (라이브 스트리밍)**

- **실시간(Real-time)으로 동영상 전송**
- 예: YouTube Live, Twitch, Facebook Live
- **지연(latency)이 중요한 요소**

### **2️⃣ Video on Demand (VoD, 주문형 스트리밍)**

- 사용자가 원할 때 동영상을 요청하여 재생
- 예: Netflix, YouTube, Disney+
- 일반적으로 **adaptive streaming(적응형 스트리밍)**을 사용하여 네트워크 상태에 맞게 품질을 조정

##### **💡 Real-Life Example (실생활 예시)**

> **Live Streaming**은 **생방송 TV 중계**와 같다.
> 
> - 모든 사용자가 같은 콘텐츠를 **동시에 시청**  
>     **VoD(주문형 스트리밍)**은 **영화관에서 원하는 영화를 선택해서 보는 것**과 같다.

---

## **2.6.2 Challenges in Video Streaming (비디오 스트리밍의 문제점)**

### **설명 (Explanation)**

비디오 스트리밍은 **네트워크 상태에 따라 품질이 달라질 수 있으며**, 다양한 문제가 발생할 수 있다.

### **1️⃣ High Bandwidth Requirement (높은 대역폭 요구)**

- 비디오 데이터는 용량이 크기 때문에 **많은 네트워크 대역폭(Bandwidth)이 필요**
- 4K, 8K 같은 고해상도 영상은 **수백 Mbps의 속도**가 필요함

### **2️⃣ Delay and Buffering (지연 및 버퍼링 문제)**

- 네트워크 속도가 느리거나 불안정하면, **버퍼링(buffering)**이 발생하여 영상이 끊길 수 있음
- **latency(지연)**이 높으면 라이브 스트리밍의 경우 시청자 경험이 나빠짐

### **3️⃣ Network Congestion (네트워크 혼잡)**

- 특정 시간대(예: 저녁 시간)에 많은 사용자가 스트리밍하면, 네트워크 부하 증가
- 여러 사용자가 **동일한 서버에 요청**하면 서버가 과부하될 수 있음

##### **💡 Real-Life Example (실생활 예시)**

> 비디오 스트리밍에서 발생하는 **버퍼링**은 **인터넷이 느릴 때 웹 페이지 로딩이 오래 걸리는 것**과 같다.

---

## **2.6.3 Adaptive Streaming (적응형 스트리밍)**

### **설명 (Explanation)**

네트워크 상태에 따라 동영상 품질을 동적으로 조정하는 기술을 **Adaptive Streaming(적응형 스트리밍)**이라고 한다.  
가장 많이 사용되는 두 가지 방식은 **DASH(Dynamic Adaptive Streaming over HTTP)**와 **HLS(HTTP Live Streaming)**이다.

### **Adaptive Streaming 방식**

1. **DASH (MPEG-DASH, Dynamic Adaptive Streaming over HTTP)**
    
    - 네트워크 상태에 따라 **비디오 품질을 자동으로 조정**
    - 여러 개의 해상도(1080p, 720p, 480p 등)로 영상을 준비해둠
    - 클라이언트가 자신의 네트워크 속도에 맞는 품질을 선택
2. **HLS (HTTP Live Streaming, 애플 개발)**
    
    - 주로 Apple 기기에서 사용되며, **비슷한 원리로 동작**
    - 비디오를 여러 개의 작은 청크(chunk)로 분할하여 전송

##### **💡 Real-Life Example (실생활 예시)**

> **Adaptive Streaming**은 **자동차 네비게이션이 교통 상황에 따라 최적 경로를 자동으로 선택하는 것**과 같다.
> 
> - 네트워크가 빠르면 **고해상도(1080p, 4K)로 재생**
> - 네트워크가 느리면 **저해상도(480p)로 조정**

---

## **2.6.4 Content Distribution Networks (CDNs, 콘텐츠 전송 네트워크)**

### **설명 (Explanation)**

CDN(Content Distribution Network)은 **전 세계 여러 서버에 콘텐츠를 분산 저장하여 사용자가 가까운 서버에서 데이터를 받아볼 수 있도록 하는 네트워크**이다.  
Netflix, YouTube, Amazon 같은 대형 스트리밍 서비스는 **CDN을 통해 트래픽을 분산**하여 스트리밍 품질을 개선한다.

### **CDN의 주요 특징**

1. **Caching(캐싱) & Replication(복제)**
    - **자주 요청되는 콘텐츠를 전 세계 CDN 서버에 저장**하여 빠르게 제공
2. **Load Balancing(부하 분산)**
    - 사용자 요청을 **가장 가까운 서버로 자동 분산**
3. **Latency Reduction(지연 최소화)**
    - **사용자와 가장 가까운 CDN 서버에서 콘텐츠 제공 → 스트리밍 속도 향상**

### **CDN의 동작 과정**

1. 사용자가 `www.netflix.com`에 접속
2. DNS가 사용자의 위치를 파악하고, 가장 가까운 CDN 서버로 연결
3. CDN 서버에서 비디오 콘텐츠 제공 → **빠른 로딩 & 버퍼링 최소화**

##### **💡 Real-Life Example (실생활 예시)**

> **CDN은 음식 배달 서비스의 "지역 지점"과 같다.**
> 
> - 사용자가 피자를 주문하면, **가장 가까운 피자 가게에서 배달**하여 빠르게 제공

---

## **2.6.5 Peer-Assisted Video Streaming (P2P 스트리밍)**

### **설명 (Explanation)**

일부 스트리밍 서비스는 **P2P(peer-to-peer) 기술을 활용하여 비디오를 공유**함으로써 네트워크 부하를 줄인다.  
이 방식은 BitTorrent와 유사하며, 사용자가 서로 데이터를 공유하여 서버 부하를 줄인다.

### **P2P Streaming의 장점**

- **서버 부담 감소** (사용자가 직접 콘텐츠를 공유)
- **비용 절감** (중앙 서버 유지 비용 감소)
- **확장성 향상** (사용자가 많아질수록 네트워크 속도 증가)

##### **💡 Real-Life Example (실생활 예시)**

> P2P 스트리밍은 **친구들끼리 파일을 공유하는 것과 같다.**
> 
> - 모든 사용자가 동시에 콘텐츠를 제공하고 다운로드할 수 있음.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **비디오 스트리밍의 종류**
    
    - **Live Streaming(실시간 스트리밍)**: YouTube Live, Twitch
    - **Video on Demand(주문형 스트리밍)**: Netflix, YouTube
2. **비디오 스트리밍의 문제점**
    
    - 높은 대역폭 요구, 버퍼링 문제, 네트워크 혼잡 발생
3. **Adaptive Streaming(적응형 스트리밍)**
    
    - **DASH, HLS**를 사용하여 네트워크 상태에 맞게 자동으로 해상도 조정
4. **Content Distribution Network (CDN) 활용**
    
    - **가장 가까운 서버에서 콘텐츠 제공 → 스트리밍 품질 개선 & 지연 최소화**

🚀 **한 문장 요약:**  
비디오 스트리밍은 **Adaptive Streaming & CDN**을 활용하여 네트워크 부하를 줄이고 **빠른 콘텐츠 전송**을 가능하게 한다.