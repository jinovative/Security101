[[Transport Layer]]

#### **요약 (Summary)**

**Congestion Control(혼잡 제어)**는 **네트워크가 과부하 상태가 되는 것을 방지**하고, 패킷 손실과 지연을 최소화하는 기법이다.  
네트워크에서 **Too many sources sending too much data too fast**(너무 많은 송신자가 너무 많은 데이터를 너무 빠르게 보내면) → **Congestion(혼잡) 발생**.  
TCP와 같은 프로토콜은 **혼잡을 감지하고, 전송 속도를 조절하여 네트워크가 원활하게 동작하도록 한다**.

---

## **3.6.1 The Causes and Effects of Congestion (혼잡 발생 원인 및 영향)**

### **설명 (Explanation)**

네트워크에서 **Congestion(혼잡)**이 발생하면, **패킷 손실, 긴 전송 지연, 처리량(Throughput) 감소**가 나타날 수 있다.

### **1️⃣ Congestion 발생 원인**

|원인|설명|
|---|---|
|**High Traffic Load (과도한 트래픽 부하)**|너무 많은 송신자가 데이터를 동시에 보냄|
|**Insufficient Buffer Space (라우터 버퍼 부족)**|라우터에서 패킷을 저장할 공간이 부족|
|**Slow Receiver (느린 수신자)**|수신자의 처리 속도가 송신자의 전송 속도를 따라가지 못함|
|**Network Link Bottleneck (네트워크 링크 병목 현상)**|특정 링크의 용량이 부족하여 데이터가 쌓임|

### **2️⃣ Congestion이 미치는 영향**

- **Queueing Delay 증가 (대기 시간 증가)**
    - 패킷이 라우터에서 대기해야 하므로 전송 속도가 느려짐.
- **Packet Loss (패킷 손실 증가)**
    - 라우터의 버퍼가 가득 차면 **패킷이 손실(drop)** 됨.
- **Throughput 감소 (처리량 감소)**
    - 너무 많은 패킷 손실이 발생하면 재전송이 필요하여 네트워크 성능이 저하됨.

##### **💡 Real-Life Example (실생활 예시)**

> **혼잡은 교통 체증과 같다.**
> 
> - 도로에 너무 많은 차가 몰리면 **정체(대기 시간 증가)**가 발생하고,
> - 일부 차가 길을 벗어나거나 사고(패킷 손실)로 이어질 수 있음.

---

## **3.6.2 Approaches to Congestion Control (혼잡 제어 방식)**

### **설명 (Explanation)**

혼잡 제어는 **네트워크가 과부하되지 않도록 전송 속도를 조절하는 방법**이며, 크게 **Network-assisted 방식**과 **End-to-end 방식**으로 나뉜다.

### **1️⃣ Network-assisted Congestion Control (네트워크 지원 혼잡 제어)**

- **네트워크 장비(라우터, 스위치)가 혼잡 상태를 감지하고 송신자에게 알림**
- 예: **Explicit Congestion Notification (ECN)**
    - 라우터가 패킷에 "혼잡 발생" 플래그를 설정하여 송신자에게 전송 속도 조절 요청.

### **2️⃣ End-to-End Congestion Control (종단 간 혼잡 제어)**

- **송신자와 수신자 간의 통신만으로 혼잡 상태를 감지하고 조절**
- TCP가 사용하는 방식 (라우터의 도움 없이 송신자가 네트워크 상태를 스스로 판단).

##### **💡 Real-Life Example (실생활 예시)**

> - **Network-assisted Control**: 경찰이 교통 정리를 하면서 차량 속도를 조절.
> - **End-to-End Control**: 운전자가 스스로 도로 상황을 보고 속도를 줄임.

---

## **3.6.3 TCP Congestion Control Mechanism (TCP 혼잡 제어 메커니즘)**

### **설명 (Explanation)**

TCP는 네트워크에서 혼잡이 발생하면 **전송 속도를 자동으로 조절**하는 **Congestion Control(혼잡 제어) 알고리즘**을 사용한다.  
TCP의 혼잡 제어는 **Additive Increase, Multiplicative Decrease(AIMD)** 원리를 따른다.

### **1️⃣ TCP Congestion Control 단계**

#### **① Slow Start (느린 시작)**

- **처음에는 작은 윈도우 크기(1 MSS)로 시작**
- ACK을 받을 때마다 윈도우 크기를 **2배씩 증가**(Exponentially Increase)
- **혼잡이 감지될 때까지 계속 증가**

#### **② Congestion Avoidance (혼잡 회피)**

- **임계값(ssthresh, Slow Start Threshold)에 도달하면 증가 속도를 줄임**
- **윈도우 크기를 선형적으로 증가 (Additive Increase)**

#### **③ Multiplicative Decrease (혼잡 발생 시 감소)**

- **패킷 손실이 발생하면 전송 속도를 반으로 줄임 (Multiplicative Decrease)**
- 다시 **Slow Start** 또는 **Congestion Avoidance** 단계로 돌아감.

##### **💡 Real-Life Example (실생활 예시)**

> **TCP 혼잡 제어는 고속도로에서 차량이 속도를 조절하는 것과 같다.**
> 
> - 차량이 처음에는 천천히(느린 시작) 출발하고,
> - 도로 상황이 괜찮으면 점진적으로 속도를 올리며(혼잡 회피),
> - 갑자기 차가 많아지면 속도를 줄임(혼잡 발생 시 감소).

---

## **3.6.4 TCP Congestion Control Algorithms (TCP 혼잡 제어 알고리즘 종류)**

### **1️⃣ TCP Tahoe**

- **패킷 손실 발생 시, 윈도우 크기를 1 MSS로 줄이고 Slow Start 다시 시작**
- 즉, 패킷 손실이 감지되면 **초기 상태로 돌아감**.

### **2️⃣ TCP Reno**

- **Fast Recovery(빠른 복구) 기능 추가**
- 손실이 감지되면 **윈도우 크기를 절반으로 줄이고 혼잡 회피로 전환**
- **TCP Tahoe보다 더 효율적**.

### **3️⃣ TCP Vegas**

- RTT(Round Trip Time)을 분석하여 **혼잡이 발생하기 전에 전송 속도를 조절**
- **Tahoe & Reno보다 더 정교한 방식**

---

## **3.6.5 Explicit Congestion Notification (ECN, 명시적 혼잡 알림)**

### **설명 (Explanation)**

TCP와 IP에서는 혼잡을 감지하고 송신자에게 알릴 수 있도록 **ECN(Explicit Congestion Notification)**을 지원한다.

### **ECN 동작 방식**

1. 라우터가 혼잡을 감지하면 **ECN 비트를 1로 설정**.
2. 수신자는 송신자에게 **ECN이 설정된 패킷을 받았음을 알림**.
3. 송신자는 전송 속도를 줄여 혼잡을 완화.

##### **💡 Real-Life Example (실생활 예시)**

> **ECN은 신호등과 유사하다.**
> 
> - 신호등이 **빨간불(혼잡 플래그 설정)**이 되면 차량이 속도를 줄이는 것과 같음.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Congestion(혼잡)은 네트워크에서 너무 많은 패킷이 전송될 때 발생하며, 패킷 손실과 지연을 초래한다.**
2. **Congestion Control(혼잡 제어) 방식**
    - **Network-assisted Control**: 네트워크 장비(라우터)가 혼잡을 감지하여 송신자에게 알림.
    - **End-to-End Control**: 송신자가 패킷 손실을 기반으로 혼잡을 감지하고 조절 (TCP 방식).
3. **TCP Congestion Control (혼잡 제어 기법)**
    - **Slow Start → Congestion Avoidance → Multiplicative Decrease** 과정을 거쳐 혼잡을 조절.
4. **TCP Tahoe, Reno, Vegas 등의 알고리즘이 혼잡 제어 방식으로 사용된다.**
5. **ECN(Explicit Congestion Notification)은 네트워크가 혼잡 상태임을 송신자에게 알리는 방식이다.**

🚀 **한 문장 요약:**  
**TCP 혼잡 제어는 네트워크 과부하를 방지하기 위해 Slow Start, Congestion Avoidance, Multiplicative Decrease 기법을 사용하며, ECN을 통해 혼잡 상태를 송신자에게 알릴 수 있다.**