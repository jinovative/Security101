[[Multimedia Networking]]

#### **요약 (Summary)**

**Real-Time Conversational Applications(실시간 대화형 애플리케이션)**은 **VoIP, 화상 회의(Video Conferencing), 온라인 게임, 원격 교육 등과 같이 실시간 상호작용이 필요한 애플리케이션**을 의미한다.  
이러한 애플리케이션에서는 **낮은 지연(Low Latency), 패킷 손실 최소화(Packet Loss), 지터(Jitter) 보정이 중요**하다.  
이를 위해 **SIP(Session Initiation Protocol), RTP(Real-Time Transport Protocol), RTCP(Real-Time Control Protocol), WebRTC(Web Real-Time Communication)** 등의 프로토콜이 사용된다.

---

## **9.4.1 Characteristics of Real-Time Conversational Applications (실시간 대화형 애플리케이션의 특징)**

### **설명 (Explanation)**

실시간 대화형 애플리케이션은 **실시간 음성 및 비디오 데이터를 전송하므로 일반적인 데이터 트래픽과 다른 특성을 가짐**.

### **1️⃣ 주요 특징 (Key Characteristics of Real-Time Conversational Applications)**

|특징|설명|
|---|---|
|**Low Latency (낮은 지연 요구)**|네트워크 지연이 길어지면 대화가 어색해지고, 사용자 경험이 저하됨|
|**Jitter Sensitivity (지터 민감성)**|패킷 도착 시간이 일정하지 않으면 오디오 및 비디오 품질이 저하됨|
|**Packet Loss Handling (패킷 손실 처리 필요)**|패킷 손실이 발생하면, 복구 없이도 원활한 통신 유지 필요|
|**Adaptive Streaming (적응형 스트리밍 사용)**|네트워크 상태에 따라 음성 및 영상 품질 자동 조정|
|**Interactivity (상호작용성 요구됨)**|실시간 통신이므로 즉각적인 반응이 필요함|

📌 **예제**

- **Zoom에서 음성이 지연되면 대화가 어색해지는 이유 → Latency 문제**
- **온라인 게임에서 상대방 캐릭터가 순간이동하는 현상 → Jitter & Packet Loss 문제**

##### **💡 Real-Life Example (실생활 예시)**

> - **VoIP 전화 통화 중 상대방의 목소리가 밀리거나 끊기는 현상 (Latency & Packet Loss 문제).**
> - **Zoom 화상 회의에서 영상과 음성이 싱크가 맞지 않는 현상 (Jitter 문제).**

---

## **9.4.2 Session Initiation Protocol (SIP: 세션 초기화 프로토콜)**

### **설명 (Explanation)**

**SIP(Session Initiation Protocol)**은 **VoIP 및 화상 회의에서 통화 세션을 설정, 관리, 종료하는 프로토콜**이다.  
SIP는 **전화번호 또는 이메일 주소를 기반으로 IP 네트워크에서 호출을 설정**하며,  
음성 및 비디오 데이터를 전송하는 **RTP(Real-Time Transport Protocol)와 함께 동작**한다.

### **1️⃣ SIP의 주요 기능 (Key Functions of SIP)**

|기능|설명|
|---|---|
|**Session Establishment (세션 설정)**|발신자와 수신자 간 연결을 설정|
|**Session Management (세션 관리)**|통화 중 네트워크 상태 변경, 미디어 전환 등을 처리|
|**Session Termination (세션 종료)**|통화가 끝나면 세션을 정상적으로 종료|

📌 **SIP 동작 과정**

1. **Caller (발신자)** → "전화 걸기" 요청 (SIP INVITE)
2. **Callee (수신자)** → "전화 받기" 응답 (SIP 200 OK)
3. **통화 세션 시작 (RTP를 통해 음성 데이터 전송)**
4. **통화 종료 (BYE 메시지를 전송하여 세션 종료)**

✅ **SIP는 Zoom, Microsoft Teams, WhatsApp Call 등 다양한 VoIP 및 화상 회의 서비스에서 사용됨**

##### **💡 Real-Life Example (실생활 예시)**

> - **Skype에서 전화를 걸면 SIP가 세션을 설정하고, RTP가 오디오 데이터를 전송.**
> - **Zoom 미팅에서 사용자가 회의를 나가면 SIP를 통해 세션이 종료됨.**

---

## **9.4.3 Real-Time Transport Protocol (RTP: 실시간 전송 프로토콜)**

### **설명 (Explanation)**

**RTP(Real-Time Transport Protocol)**은 **음성 및 비디오 데이터를 실시간으로 전송하는 프로토콜**이다.  
RTP는 **UDP(User Datagram Protocol) 기반으로 동작하며, 패킷 손실 복구보다는 낮은 지연을 우선시함**.

📌 **RTP의 주요 기능**  
✅ **Sequencing (패킷 순서 유지)** → 패킷 도착 순서가 엉킬 경우 원래 순서대로 재정렬  
✅ **Timestamping (타임스탬프 사용)** → 패킷 간의 시간 간격을 유지하여 동기화 보장  
✅ **Payload Type Indication (페이로드 타입 지정)** → 오디오, 비디오 코덱을 구분하여 적절한 처리를 수행

📌 **RTP 동작 과정**

1. **음성 데이터를 패킷화하여 전송 (UDP 사용)**
2. **패킷에 Timestamp와 Sequence Number 추가**
3. **수신 측에서 패킷 순서 복원 및 동기화**
4. **버퍼링을 통해 지연 및 지터 보정 후 재생**

✅ **RTP는 VoIP, 화상 회의, 온라인 게임, 라이브 스트리밍에서 사용됨**

##### **💡 Real-Life Example (실생활 예시)**

> - **WhatsApp Call에서 음성이 실시간으로 전송될 때 RTP가 사용됨.**
> - **Zoom에서 화면 공유를 할 때 비디오 데이터가 RTP를 통해 실시간으로 전송됨.**

---

## **9.4.4 Real-Time Control Protocol (RTCP: 실시간 제어 프로토콜)**

### **설명 (Explanation)**

**RTCP(Real-Time Control Protocol)**은 **RTP와 함께 동작하며, 네트워크 상태를 모니터링하고 품질을 개선하는 역할**을 수행한다.

📌 **RTCP의 주요 기능**  
✅ **QoS Monitoring (QoS 품질 모니터링)** → 패킷 손실, 지연, 지터 등을 측정  
✅ **Synchronization (동기화 제공)** → 오디오 및 비디오의 싱크를 유지  
✅ **Session Statistics (세션 통계 제공)** → 네트워크 성능 데이터를 수집하여 피드백 제공

📌 **RTCP 동작 과정**

1. **송신 측이 패킷 전송 상태를 RTCP 리포트로 보고**
2. **수신 측이 품질 데이터(지연, 패킷 손실)를 분석**
3. **네트워크 상태에 따라 Adaptive Streaming 적용 (비트레이트 조정 등)**

✅ **RTCP는 VoIP 및 화상 회의에서 음성 및 영상 품질을 자동 조정하는 데 사용됨**

##### **💡 Real-Life Example (실생활 예시)**

> - **Zoom 미팅에서 네트워크 상태가 좋지 않을 때 "Your Internet Connection is Unstable" 메시지가 표시되는 것 (RTCP가 네트워크 품질을 모니터링).**
> - **Microsoft Teams에서 네트워크 속도에 따라 자동으로 비디오 품질이 조정되는 것.**

---

## **9.4.5 WebRTC (Web Real-Time Communication)**

### **설명 (Explanation)**

**WebRTC(Web Real-Time Communication)**은 **브라우저에서 별도 플러그인 없이 실시간 음성 및 비디오 통신을 제공하는 기술**이다.  
WebRTC는 **SIP 없이도 P2P(피어 투 피어) 연결을 사용하여 낮은 지연으로 통신 가능**.

📌 **WebRTC의 주요 특징**  
✅ **Plugin-Free (플러그인 불필요)** → Chrome, Firefox 등 브라우저에서 기본 지원  
✅ **P2P Communication (피어 투 피어 연결 지원)** → 서버를 거치지 않고 직접 통신  
✅ **End-to-End Encryption (종단 간 암호화)** → 보안 강화를 위해 기본 암호화 적용

✅ **WebRTC는 Google Meet, Facebook Messenger, Discord 같은 웹 기반 화상 통화 서비스에서 사용됨**

##### **💡 Real-Life Example (실생활 예시)**

> - **Google Meet이 별도 소프트웨어 없이 브라우저에서 바로 실행되는 것 (WebRTC 사용).**
> - **Discord에서 웹 브라우저로 바로 음성 채팅을 할 수 있는 것.**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **실시간 대화형 애플리케이션(VoIP, 화상 회의)은 낮은 지연과 패킷 손실 최소화가 중요하다.**
2. **SIP는 세션 설정, RTP는 데이터 전송, RTCP는 품질 모니터링을 담당한다.**
3. **WebRTC는 브라우저 기반 실시간 통신을 제공하며, P2P 연결을 지원한다.**