[[Multimedia Networking]]


#### **요약 (Summary)**

**Streaming Stored Video(저장된 비디오 스트리밍)**은 **이미 저장된 비디오 파일을 네트워크를 통해 실시간으로 재생하는 기술**이다.  
사용자는 **전체 비디오 파일을 다운로드하지 않고도 즉시 재생(Streaming)**할 수 있으며,  
Netflix, YouTube, Disney+ 같은 **VOD(Video On Demand) 서비스에서 널리 사용**된다.  
이 과정에서 **Buffering(버퍼링), Adaptive Streaming(적응형 스트리밍), CDN(Content Delivery Network) 같은 기술이 적용**된다.

---

## **9.2.1 Characteristics of Streaming Stored Video (저장된 비디오 스트리밍의 특징)**

### **설명 (Explanation)**

비디오 스트리밍은 **일반적인 파일 다운로드와 다르게, 데이터가 전송되면서 실시간으로 재생됨**.  
따라서 **연속적인 데이터 전송이 필수적이며, 네트워크 품질(QoS)에 영향을 받음**.

### **1️⃣ Streaming Stored Video의 주요 특징 (Key Characteristics of Streaming Stored Video)**

|특징|설명|
|---|---|
|**Progressive Download vs. Streaming (점진적 다운로드 vs. 스트리밍)**|다운로드 완료 후 재생이 아닌, 실시간 재생 지원|
|**Continuous Playback (연속 재생 가능)**|사용자 입력 없이 자동으로 비디오가 재생됨|
|**Adaptive Bitrate Streaming (적응형 비트레이트 스트리밍)**|네트워크 상태에 따라 화질 자동 조정|
|**Buffering (버퍼링 활용)**|네트워크 지연이나 패킷 손실을 보완하기 위해 일정량의 데이터 미리 로드|

📌 **비디오 스트리밍 vs. 다운로드 비교**

|방식|설명|예제|
|---|---|---|
|**다운로드 방식**|파일을 완전히 다운로드한 후 재생 가능|이메일 첨부 파일 다운로드|
|**스트리밍 방식**|데이터를 실시간으로 받아서 즉시 재생 가능|YouTube, Netflix|

✅ **Netflix, YouTube는 스트리밍 방식을 사용하여 사용자 경험을 향상시킴**

##### **💡 Real-Life Example (실생활 예시)**

> - **유튜브에서 동영상을 클릭하면 즉시 재생되는 것 (Streaming).**
> - **동영상을 파일로 다운로드한 후 재생하는 것 (Download 방식).**

---

## **9.2.2 Architecture of a Video Streaming System (비디오 스트리밍 시스템의 아키텍처)**

### **설명 (Explanation)**

비디오 스트리밍 시스템은 **사용자가 요청하면 서버에서 비디오 데이터를 지속적으로 전송하는 방식**으로 동작한다.

📌 **Streaming System의 주요 구성 요소**

1. **Client (클라이언트)** → 스트리밍을 요청하고 비디오를 재생 (예: YouTube 앱, 웹 브라우저)
2. **Video Server (비디오 서버)** → 사용자의 요청에 따라 비디오 파일을 전송
3. **CDN (Content Delivery Network, 콘텐츠 전송 네트워크)** → 전 세계 서버를 통해 빠른 콘텐츠 제공
4. **Adaptive Streaming (적응형 스트리밍 기술)** → 네트워크 상태에 따라 화질 조정

📌 **Video Streaming 과정**

1. **사용자가 스트리밍 요청** (YouTube, Netflix에서 동영상 클릭)
2. **CDN 또는 원본 서버에서 데이터 전송 시작**
3. **클라이언트에서 버퍼링 후 즉시 재생 시작**
4. **재생 중 네트워크 품질 변화에 따라 Adaptive Streaming 적용**

✅ **Netflix, YouTube, Twitch 같은 서비스는 CDN을 사용하여 서버 부하를 줄이고 사용자에게 빠르게 콘텐츠 제공**

##### **💡 Real-Life Example (실생활 예시)**

> - **넷플릭스에서 영화를 클릭하면, 가장 가까운 CDN 서버에서 데이터를 가져와 빠르게 재생**
> - **유튜브에서 화질을 자동으로 조정하여 끊김 없이 시청 가능 (Adaptive Streaming 적용)**

---

## **9.2.3 Adaptive Bitrate Streaming (적응형 비트레이트 스트리밍)**

### **설명 (Explanation)**

Adaptive Bitrate Streaming(적응형 비트레이트 스트리밍)은 **사용자의 네트워크 상태를 실시간으로 분석하여 최적의 비디오 화질을 제공하는 기술**이다.

### **1️⃣ Adaptive Streaming의 핵심 원리 (How Adaptive Streaming Works)**

|특징|설명|
|---|---|
|**Dynamic Bitrate Adjustment (동적 비트레이트 조정)**|네트워크 속도에 따라 자동으로 비디오 화질 조정|
|**Multiple Versions of Video (다중 화질 파일 제공)**|서버에 여러 화질의 비디오 파일이 저장됨 (1080p, 720p, 480p 등)|
|**Client-Side Decision (클라이언트 측 선택)**|비디오 플레이어가 현재 네트워크 속도를 측정하여 최적의 화질 선택|

📌 **Adaptive Streaming Protocols (적응형 스트리밍 프로토콜)**

|프로토콜|설명|사용 사례|
|---|---|---|
|**HLS (HTTP Live Streaming)**|Apple이 개발, 대부분의 스트리밍 서비스에서 사용|YouTube, Netflix|
|**MPEG-DASH (Dynamic Adaptive Streaming over HTTP)**|오픈 표준 기반, 다양한 기기에서 지원|YouTube, Twitch|
|**Microsoft Smooth Streaming**|Microsoft의 HTTP 기반 스트리밍|Xbox, Windows Media Services|

📌 **Adaptive Streaming 동작 예제**

1. **Wi-Fi가 빠를 때 → 1080p 고화질 재생**
2. **Wi-Fi가 느려지면 → 720p 또는 480p로 화질 자동 조정**
3. **4G/LTE에서 데이터 절약 모드 사용 시 → 360p로 낮은 품질 스트리밍**

##### **💡 Real-Life Example (실생활 예시)**

> - **넷플릭스에서 영화를 재생할 때 네트워크 속도에 따라 자동으로 4K → 1080p → 720p로 화질 변경**
> - **유튜브에서 모바일 데이터를 사용할 때 화질이 자동으로 조정되는 것**

---

## **9.2.4 Content Delivery Networks (CDN) for Video Streaming (CDN을 활용한 비디오 스트리밍 최적화)**

### **설명 (Explanation)**

**CDN(Content Delivery Network)**은 **전 세계 여러 지역에 분산된 서버를 사용하여 빠르게 콘텐츠를 제공하는 네트워크**이다.  
CDN을 활용하면 **서버 부하를 줄이고, 지연(Latency)을 최소화하여 비디오 스트리밍을 최적화**할 수 있음.

📌 **CDN의 주요 역할**  
✅ **Latency Reduction (지연 최소화)** → 사용자와 가까운 CDN 서버에서 콘텐츠 제공  
✅ **Load Balancing (부하 분산)** → 여러 서버에 트래픽을 분산하여 성능 향상  
✅ **Fault Tolerance (장애 대응)** → 한 서버가 다운되면 다른 서버에서 콘텐츠 제공

📌 **CDN을 사용하는 스트리밍 서비스 예제**

- **YouTube → 전 세계에 분산된 CDN 서버를 통해 빠른 스트리밍 제공**
- **Netflix → AWS CloudFront CDN을 사용하여 영화 및 TV 쇼 전송**

##### **💡 Real-Life Example (실생활 예시)**

> - **미국에서 만든 유튜브 영상을 한국에서 볼 때, 미국 서버가 아닌 한국 CDN 서버에서 콘텐츠를 다운로드하여 빠르게 재생됨**
> - **넷플릭스에서 영화가 끊기지 않는 이유 → CDN을 사용하여 가까운 서버에서 데이터를 전송**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Streaming Stored Video는 사용자가 전체 파일을 다운로드하지 않고도 비디오를 실시간으로 재생하는 방식이다.**
2. **Adaptive Bitrate Streaming(HLS, MPEG-DASH)을 사용하여 네트워크 상태에 따라 자동으로 비디오 품질을 조정한다.**
3. **CDN(Content Delivery Network)을 활용하여 서버 부하를 줄이고, 사용자에게 빠르게 콘텐츠를 제공한다.**

🚀 **한 문장 요약:**  
**비디오 스트리밍 서비스(YouTube, Netflix)는 Adaptive Bitrate Streaming과 CDN을 활용하여 네트워크 상태에 따라 최적의 품질을 제공하고 지연을 최소화한다.**