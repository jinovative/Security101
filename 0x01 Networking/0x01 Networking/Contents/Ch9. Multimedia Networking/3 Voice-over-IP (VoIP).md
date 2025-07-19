[[Multimedia Networking]]

#### **요약 (Summary)**

**VoIP (Voice over IP, 인터넷 전화)**는 **음성 데이터를 디지털 패킷으로 변환하여 인터넷을 통해 전송하는 기술**이다.  
기존 전화망(PSTN, Public Switched Telephone Network)과 달리, **IP 네트워크를 사용하여 더 저렴하고 유연한 통신 서비스 제공**이 가능하다.  
대표적인 VoIP 애플리케이션으로는 **Skype, Zoom, Microsoft Teams, WhatsApp Call, Google Meet** 등이 있다.  
VoIP는 **패킷 손실(Packet Loss), 지연(Latency), 지터(Jitter) 등의 문제를 해결하기 위해 QoS(Quality of Service) 및 RTP(Real-Time Transport Protocol) 같은 기술을 사용**한다.

---

## **9.3.1 How VoIP Works (VoIP의 동작 원리)**

### **설명 (Explanation)**

VoIP는 **음성을 디지털 데이터로 변환하여 패킷 단위로 전송하고, 수신 측에서 이를 다시 음성으로 변환하여 전달하는 방식**으로 동작한다.

📌 **VoIP의 주요 동작 과정**

1. **Analog-to-Digital Conversion (음성의 디지털 변환)** → 마이크로폰을 통해 입력된 아날로그 음성을 디지털 신호로 변환
2. **Packetization (패킷화)** → 디지털 음성을 작은 패킷으로 나누어 IP 네트워크를 통해 전송
3. **Transport (전송)** → 패킷이 인터넷을 통해 목적지로 전달 (UDP 사용)
4. **Reassembly & Playback (재조합 및 재생)** → 패킷을 원래의 음성 신호로 변환하여 수신자에게 전달

✅ **VoIP는 기존 회선 기반 전화망보다 비용이 낮고, 데이터와 음성을 동시에 전송 가능**

##### **💡 Real-Life Example (실생활 예시)**

> - **Skype 또는 WhatsApp Call을 사용하여 무료 인터넷 통화를 하는 것**
> - **회사에서 Zoom을 이용하여 원격 회의를 진행하는 것**

---

## **9.3.2 VoIP Protocols (VoIP에서 사용되는 프로토콜)**

### **설명 (Explanation)**

VoIP는 **음성 데이터를 IP 네트워크에서 안정적으로 전송하기 위해 여러 프로토콜을 사용**한다.

### **1️⃣ 주요 VoIP 프로토콜 (Key VoIP Protocols)**

|프로토콜|설명|사용 사례|
|---|---|---|
|**SIP (Session Initiation Protocol)**|VoIP 세션을 설정, 관리, 종료하는 프로토콜|Skype, Microsoft Teams|
|**H.323**|VoIP 및 비디오 컨퍼런싱을 위한 ITU-T 표준|기업 전화 시스템|
|**RTP (Real-Time Transport Protocol)**|음성 및 영상 데이터를 실시간으로 전송하는 프로토콜|Zoom, WhatsApp Call|
|**RTCP (Real-Time Control Protocol)**|RTP의 품질을 모니터링하고 제어|통화 품질 모니터링|
|**MGCP (Media Gateway Control Protocol)**|VoIP 게이트웨이를 제어하는 프로토콜|VoIP 게이트웨이 장비|

📌 **VoIP 프로토콜의 역할**

- **SIP → 통화 세션 설정/종료**
- **RTP → 음성 데이터 실시간 전송**
- **RTCP → 품질 모니터링 (패킷 손실, 지연 측정)**

##### **💡 Real-Life Example (실생활 예시)**

> - **Skype에서 친구에게 전화를 걸면 SIP가 통화 연결을 설정하고, RTP가 음성 데이터를 전송**
> - **Zoom 미팅 중 네트워크 상태가 나빠지면 RTCP가 패킷 손실을 감지하고 음질을 조정**

---

## **9.3.3 Challenges in VoIP (VoIP의 주요 문제점)**

### **설명 (Explanation)**

VoIP는 **기존 회선 교환 방식(PSTN)과 다르게 패킷 기반 네트워크에서 동작하므로 몇 가지 기술적 문제를 해결해야 함**.

### **1️⃣ VoIP의 주요 문제점 (Challenges in VoIP)**

|문제점|설명|
|---|---|
|**Latency (지연 문제)**|패킷이 전송되는 동안 발생하는 지연으로 인해 음성이 늦게 전달될 수 있음|
|**Jitter (지터 문제)**|패킷 도착 시간이 일정하지 않으면 음성이 깨지거나 끊길 수 있음|
|**Packet Loss (패킷 손실 문제)**|패킷이 손실되면 음성이 중간에 사라지거나 왜곡됨|
|**Echo (에코 문제)**|송신자의 음성이 수신자 쪽에서 다시 들리는 현상|
|**Security Issues (보안 문제)**|도청(Eavesdropping), 스푸핑(Spoofing), DoS 공격 등의 보안 위협 발생 가능|

📌 **VoIP 품질 저하 예제**

- **네트워크 속도가 느릴 때 Zoom 통화가 딜레이 되는 이유 → Latency**
- **WhatsApp Call 중 상대방 음성이 로봇처럼 들리는 이유 → Jitter & Packet Loss**
- **기업 VoIP 시스템이 해커에 의해 도청되는 사례 → 보안 문제**

##### **💡 Real-Life Example (실생활 예시)**

> - **화상 회의 중 인터넷 속도가 느려지면서 목소리가 지연되는 현상 (Latency 문제)**
> - **전화 통화 중 상대방 음성이 끊기거나 깨지는 문제 (Packet Loss & Jitter 문제)**

---

## **9.3.4 Solutions to VoIP Challenges (VoIP 품질 개선 방법)**

### **설명 (Explanation)**

VoIP 서비스의 품질을 개선하기 위해 **QoS(Quality of Service), Jitter Buffer, Packet Loss Concealment(PLC)** 같은 기술이 적용된다.

### **1️⃣ VoIP 품질 개선 기술 (Solutions to VoIP Challenges)**

|해결 방법|설명|
|---|---|
|**QoS (Quality of Service)**|VoIP 패킷을 우선적으로 처리하여 음성 지연 및 손실 최소화|
|**Jitter Buffer (지터 버퍼링)**|패킷 도착 시간 변동을 조절하여 음성이 깨지지 않도록 함|
|**Packet Loss Concealment (PLC, 패킷 손실 보정)**|손실된 패킷을 예측하여 음성 품질 유지|
|**Echo Cancellation (에코 제거)**|마이크와 스피커 간 반사된 소리를 제거|
|**Secure VoIP (보안 강화)**|TLS 및 SRTP(Secure RTP)로 VoIP 트래픽 암호화|

📌 **VoIP 품질 개선 예제**

- **QoS → VoIP 패킷을 다른 데이터보다 우선 처리하여 음성 지연 방지**
- **Jitter Buffer → 네트워크 변동이 있어도 일정한 속도로 음성을 출력**
- **SRTP → 통화 데이터를 암호화하여 도청 방지**

##### **💡 Real-Life Example (실생활 예시)**

> - **Zoom, Skype에서 통화 품질이 안정적인 이유 → QoS 적용 및 Jitter Buffer 사용**
> - **WhatsApp Call이 보안이 강한 이유 → SRTP 암호화를 사용하여 도청 방지**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **VoIP는 음성 데이터를 패킷으로 변환하여 인터넷을 통해 전송하는 기술로, 기존 전화망보다 비용이 낮고 유연성이 높다.**
2. **VoIP는 SIP(세션 설정), RTP(음성 데이터 전송), RTCP(통화 품질 모니터링) 등의 프로토콜을 사용한다.**
3. **VoIP는 패킷 손실, 지연(Latency), 지터(Jitter) 등의 문제에 취약하지만, QoS, Jitter Buffer, PLC 등의 기술로 품질을 개선할 수 있다.**
4. **VoIP 보안을 강화하기 위해 SRTP, TLS 암호화, VPN 접속 등의 기술이 사용된다.**

🚀 **한 문장 요약:**  
**VoIP(인터넷 전화)는 SIP, RTP 같은 프로토콜을 사용하여 음성을 패킷으로 전송하며, QoS, Jitter Buffer, SRTP 등의 기술을 활용하여 품질을 개선하고 보안을 강화한다.**
