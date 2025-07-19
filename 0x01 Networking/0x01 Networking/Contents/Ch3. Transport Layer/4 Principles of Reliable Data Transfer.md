[[Transport Layer]]

#### **요약 (Summary)**

**Reliable Data Transfer(신뢰성 있는 데이터 전송, RDT)**는 송신 측(Sender)에서 전송한 데이터가 **손실(loss), 오류(error), 중복(duplicate), 순서 변경(out-of-order)** 없이 정확하게 수신 측(Receiver)에 도착하도록 보장하는 전송 방식이다.  
**ARQ (Automatic Repeat reQuest, 자동 재전송 요청) 기법**을 사용하여 신뢰성을 유지하며, **ACK(수신 확인 응답), NAK(수신 실패 응답), Timeout(타임아웃 재전송)** 등의 메커니즘을 포함한다.  
**Stop-and-Wait, Go-Back-N, Selective Repeat** 같은 프로토콜이 RDT를 구현하는 방식이다.

---

## **3.4.1 The Concept of Reliable Data Transfer (신뢰성 있는 데이터 전송 개념)**

### **설명 (Explanation)**

네트워크에서는 **패킷 손실, 오류, 중복 수신**이 발생할 수 있기 때문에, 신뢰성 있는 데이터 전송(RDT)이 필요하다.

### **1️⃣ 주요 신뢰성 문제 (Challenges in Data Transfer)**

|문제|설명|
|---|---|
|**Packet Loss (패킷 손실)**|송신된 패킷이 네트워크에서 사라짐|
|**Bit Errors (비트 오류)**|전송 중 데이터가 손상됨 (예: 0 → 1로 바뀜)|
|**Out-of-Order Delivery (순서 변경됨)**|패킷이 순서대로 도착하지 않음|
|**Duplicate Packets (중복 패킷)**|동일한 패킷이 여러 번 수신됨|

### **2️⃣ 신뢰성 보장을 위한 핵심 기술**

|기술|설명|
|---|---|
|**ACK (Acknowledgment, 확인 응답)**|수신 측이 패킷을 정상적으로 받았음을 알림|
|**NAK (Negative Acknowledgment, 오류 응답)**|수신 측이 패킷이 손상되었음을 알림|
|**Timeout (타임아웃 재전송)**|송신 측이 일정 시간 동안 ACK을 받지 못하면 패킷을 재전송|
|**Checksums (체크섬)**|데이터의 무결성을 확인하는 오류 검출 기법|

##### **💡 Real-Life Example (실생활 예시)**

> **RDT는 택배 배송 시스템과 같다.**
> 
> - 고객이 상품(데이터)을 주문하면,
> - 배송사가 물건을 보낸 후 **고객의 확인(ACK)**을 받아야 한다.
> - 만약 상품이 분실되거나 손상되면(패킷 손실/오류) **재배송(Timeout 재전송)**이 필요하다.

---

## **3.4.2 Stop-and-Wait Protocol (정지-대기 프로토콜)**

### **설명 (Explanation)**

**Stop-and-Wait Protocol(정지-대기 프로토콜)**은 송신 측이 **한 번에 하나의 패킷만 전송하고, ACK을 받을 때까지 대기하는 방식**이다.

### **1️⃣ Stop-and-Wait 동작 방식**

1. **Sender(송신자):** 패킷을 전송한 후 **ACK을 받을 때까지 대기**.
2. **Receiver(수신자):** 정상적인 패킷을 받으면 **ACK을 보냄**.
3. **Timeout 발생:** 송신자가 일정 시간 내에 ACK을 받지 못하면 **패킷을 재전송**.

### **2️⃣ Stop-and-Wait의 문제점**

- **전송 속도가 느림** (한 번에 한 패킷만 전송 가능)
- **대기 시간이 길어짐** (네트워크 대역폭을 비효율적으로 사용)

##### **💡 Real-Life Example (실생활 예시)**

> **Stop-and-Wait은 택배를 한 번에 하나씩 보내는 것과 같다.**
> 
> - 고객이 한 개의 상품을 주문하면,
> - 상품을 받은 후 확인(ACK)을 해야 다음 상품을 보낼 수 있음.

---

## **3.4.3 Go-Back-N Protocol (GBN, N-단계 되돌아가기 프로토콜)**

### **설명 (Explanation)**

**Go-Back-N (GBN) Protocol**은 **여러 개의 패킷을 연속적으로 전송**할 수 있도록 개선된 프로토콜이다.

### **1️⃣ Go-Back-N 동작 방식**

1. 송신자는 **N개의 패킷을 연속적으로 전송**.
2. 수신자는 **패킷이 정상적으로 도착하면 ACK을 보냄**.
3. 만약 패킷이 손실되거나 오류 발생 시, **해당 패킷 이후의 모든 패킷을 재전송**.

### **2️⃣ GBN의 문제점**

- 하나의 패킷이 손실되면 **그 이후 모든 패킷을 다시 전송** → 비효율적
- 불필요한 패킷 재전송이 많아질 수 있음.

##### **💡 Real-Life Example (실생활 예시)**

> **Go-Back-N은 학교에서 숙제를 제출하는 방식과 비슷하다.**
> 
> - 학생이 5개의 숙제를 제출했는데,
> - **세 번째 숙제에서 오류(패킷 손실)가 발생하면**
> - **세 번째 숙제 이후 모든 숙제를 다시 제출해야 한다(재전송).**

---

## **3.4.4 Selective Repeat Protocol (SR, 선택적 재전송 프로토콜)**

### **설명 (Explanation)**

**Selective Repeat (SR) Protocol**은 **오류가 발생한 패킷만 재전송하는 방식**으로, GBN의 비효율성을 해결한다.

### **1️⃣ Selective Repeat 동작 방식**

1. 송신자는 **여러 개의 패킷을 연속적으로 전송**.
2. 수신자는 **손상된 패킷만 NAK을 보내고, 나머지는 ACK을 보냄**.
3. 송신자는 **손상된 패킷만 다시 전송**.

### **2️⃣ Selective Repeat의 장점**

- **GBN보다 효율적** (정상적인 패킷은 재전송하지 않음)
- **네트워크 대역폭 절약**

### **3️⃣ Selective Repeat의 문제점**

- **복잡한 버퍼링(Buffering) 필요** (각 패킷을 개별적으로 추적해야 함)

##### **💡 Real-Life Example (실생활 예시)**

> **Selective Repeat은 시험에서 틀린 문제만 다시 푸는 것과 같다.**
> 
> - 학생이 시험에서 5문제 중 3문제를 맞고, 2문제를 틀림.
> - **틀린 문제(손실된 패킷)만 다시 풀면 됨(Selective Repeat).**
> - **하지만 Go-Back-N 방식이면, 5문제를 전부 다시 풀어야 함.**

---

## **3.4.5 Comparison of RDT Protocols (RDT 프로토콜 비교)**

|**프로토콜**|**특징**|**장점**|**단점**|
|---|---|---|---|
|**Stop-and-Wait**|한 번에 하나의 패킷 전송 후 ACK 대기|구현이 간단|속도가 느림|
|**Go-Back-N (GBN)**|여러 개의 패킷을 전송, 손실 발생 시 이후 패킷 모두 재전송|높은 전송률|불필요한 패킷 재전송 많음|
|**Selective Repeat (SR)**|오류가 발생한 패킷만 재전송|대역폭 절약, 효율적|구현이 복잡|

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Reliable Data Transfer(RDT)는 패킷 손실, 오류, 중복을 방지하기 위한 전송 기법이다.**
2. **Stop-and-Wait, Go-Back-N(GBN), Selective Repeat(SR) 같은 프로토콜이 RDT를 구현한다.**
3. **GBN은 손실된 패킷 이후 모든 패킷을 재전송하지만, SR은 손실된 패킷만 재전송하여 더 효율적이다.**

🚀 **한 문장 요약:**  
Reliable Data Transfer(RDT)는 **패킷 손실과 오류를 방지하는 기술**이며, **Stop-and-Wait(기본), Go-Back-N(비효율적 재전송), Selective Repeat(효율적 재전송)** 같은 프로토콜이 사용된다.