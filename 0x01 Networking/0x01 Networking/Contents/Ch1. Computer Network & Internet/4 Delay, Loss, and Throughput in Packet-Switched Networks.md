[[Computer Networks and the Internet]]
#### **요약 (Summary)**
**Packet-switched networks(패킷 스위칭 네트워크)**에서는 데이터가 작은 **packets(패킷)**으로 나뉘어 전송된다.  
패킷이 목적지까지 도달하는 과정에서 **delay(지연), loss(손실), throughput(처리량)**이 발생할 수 있다.  
이러한 요소들은 네트워크의 성능을 결정하는 중요한 요소이며, 이를 이해하면 네트워크 최적화가 가능하다.

---

## **1.4.1 Overview of Delay (네트워크 지연 개요)**

### **설명 (Explanation)**
패킷이 **source(발신지)**에서 **destination(목적지)**까지 도달하는 동안 여러 단계에서 **delay(지연)**이 발생한다.  
이러한 지연은 다음과 같이 네 가지 주요 요소로 나뉜다.

### **1️⃣ Processing Delay (처리 지연)**
- **패킷이 라우터(router)에서 처리되는 시간**
- 목적지 주소 확인, 오류 검사 등 수행
- 보통 수 **마이크로초(microseconds, μs)** 단위의 작은 지연 발생

### **2️⃣ Queuing Delay (큐잉 지연)**
- **라우터에서 패킷이 전송되기 전 대기하는 시간**
- 네트워크가 혼잡할수록 큐잉 지연 증가
- 트래픽이 많으면 **패킷 손실(packet loss)**이 발생할 수도 있음

### **3️⃣ Transmission Delay (전송 지연)**
- **패킷을 링크로 보내는 데 걸리는 시간**
- 계산식: **L(bits) / R(bits per second, bps)**
  - 예) 패킷 크기 \(L = 1000\) bits, 링크 속도 \(R = 1\) Mbps이면  
    → 전송 지연 = **\(1000 / 10^6 = 1\) ms**

### **4️⃣ Propagation Delay (전파 지연)**
- **신호가 링크를 따라 전달되는 시간**
- 거리와 매체(광섬유, 구리선 등)에 따라 달라짐
- 계산식: **d / s** (거리 d, 전파 속도 s)
  - 광섬유: **\(s ≈ 2 \times 10^8\) m/s**
  - 예) 거리 \(d = 10\) km → 전파 지연 = **\(10^4 / 2 \times 10^8 = 50\) μs**

---

## **1.4.2 Queuing Delay and Packet Loss (큐잉 지연과 패킷 손실)**

### **설명 (Explanation)**
**Queuing Delay(큐잉 지연)**은 패킷이 네트워크에서 대기하는 시간이며, 트래픽이 많을수록 증가한다.  
**Packet Loss(패킷 손실)**은 네트워크 혼잡으로 인해 **router buffer(라우터 버퍼)**가 꽉 차서 패킷이 삭제되는 현상이다.

### **Traffic Intensity(트래픽 강도)와 지연 관계**
트래픽 강도 = **(패킷 도착률 × 패킷 크기) / 링크 대역폭**  
\[
\frac{La}{R}
\]
- \(L\) = 패킷 크기 (bits)  
- \(a\) = 평균 패킷 도착률 (packets/sec)  
- \(R\) = 링크 속도 (bps)

#### **트래픽 강도에 따른 영향**
1. **\(La/R < 1\)** → 대기 시간이 짧고, 패킷 손실 없음
2. **\(La/R \approx 1\)** → 지연이 급격히 증가
3. **\(La/R > 1\)** → 버퍼 오버플로우 발생, **packet loss(패킷 손실)** 증가

##### **💡 Real-Life Example (실생활 예시)**
> 패킷 손실은 **마트의 계산대**와 같다.  
> 사람들이 몰려서 계산대(라우터의 버퍼)가 꽉 차면, 더 이상 줄을 설 수 없고(패킷 손실), 기다리는 시간(큐잉 지연)이 늘어난다.

---

## **1.4.3 End-to-End Delay (종단 간 지연)**

### **설명 (Explanation)**
네트워크에서 패킷이 한 **host(호스트)**에서 다른 **host(호스트)**로 이동하는 데 걸리는 전체 시간.

\[
d_{end-to-end} = N \times (d_{proc} + d_{queue} + d_{trans} + d_{prop})
\]

- \(N\) = 패킷이 거치는 라우터 개수
- \(d_{proc}\) = 처리 지연
- \(d_{queue}\) = 큐잉 지연
- \(d_{trans}\) = 전송 지연
- \(d_{prop}\) = 전파 지연

##### **💡 Real-Life Example (실생활 예시)**
> 패킷이 목적지까지 이동하는 과정은 **도시 간 버스 여행**과 유사하다.  
> 버스가 출발하면(전송 지연), 도로 위에서 이동하고(전파 지연), 휴게소(라우터)에서 잠시 정차할 수도 있다(큐잉 지연).  
> 버스가 많으면(네트워크 혼잡), 대기 시간이 길어진다.

---

## **1.4.4 Throughput in Computer Networks (네트워크 처리량)**

### **설명 (Explanation)**
Throughput(처리량)은 **네트워크를 통해 실제로 전송되는 데이터 속도**를 의미하며, 두 가지로 나뉜다.

1. **Instantaneous Throughput (순간 처리량)**  
   - 특정 순간에 측정된 데이터 전송 속도 (bps)
2. **Average Throughput (평균 처리량)**  
   - 일정 시간 동안 전송된 총 데이터량을 기반으로 계산됨

\[
\text{Average Throughput} = \frac{\text{Total Data Transferred (bits)}}{\text{Total Time (seconds)}}
\]

### **BottleNeck Link (병목 링크)**
- 네트워크에서 가장 낮은 속도를 가진 링크가 전체 처리량을 결정함.
- \(R_s, R_c\)는 각각 서버와 클라이언트의 대역폭.
- 병목 처리량:

\[
\min(R_s, R_c)
\]

##### **💡 Real-Life Example (실생활 예시)**
> Throughput은 **도로 위 자동차 흐름**과 같다.  
> 고속도로가 넓어도, 가장 좁은 길(병목 구간)이 전체 이동 속도를 결정한다.  
> 즉, 네트워크에서 가장 느린 링크가 전체 처리량을 제한한다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **네트워크 지연 (Delay)**
   - **Processing Delay**: 패킷을 처리하는 데 걸리는 시간
   - **Queuing Delay**: 패킷이 전송 대기하는 시간
   - **Transmission Delay**: 패킷을 링크로 전송하는 시간
   - **Propagation Delay**: 신호가 링크를 따라 이동하는 시간

2. **패킷 손실 (Packet Loss)**
   - 네트워크 혼잡 시 라우터의 버퍼가 가득 차면 발생

3. **종단 간 지연 (End-to-End Delay)**
   - 패킷이 발신지에서 목적지까지 이동하는 전체 시간

4. **네트워크 처리량 (Throughput)**
   - 실제 데이터가 전송되는 속도
   - 가장 낮은 속도를 가진 **병목 링크**가 전체 처리량을 결정함

🚀 **한 문장 요약:**  
패킷이 네트워크를 통해 이동할 때 **지연(Delay), 손실(Packet Loss), 처리량(Throughput)**이 발생하며, 네트워크 성능을 최적화하려면 이러한 요소들을 이해해야 한다.
