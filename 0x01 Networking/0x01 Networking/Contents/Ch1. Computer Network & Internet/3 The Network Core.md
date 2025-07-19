[[Computer Networks and the Internet]]

#### **요약 (Summary)**

**Network Core(네트워크 코어)**는 인터넷의 중심부로, **packet switches(패킷 스위치)**와 **communication links(통신 링크)**로 구성된다.  
이곳에서 데이터는 목적지까지 이동하기 위해 여러 라우터(router)와 스위치(switch)를 거친다.  
네트워크 코어의 핵심 개념은 **packet switching(패킷 스위칭)**과 **circuit switching(회선 스위칭)**이며, 대부분의 현대 인터넷은 패킷 스위칭을 기반으로 동작한다.

---

## **1.3.1 Packet Switching (패킷 스위칭)**

### **설명 (Explanation)**

인터넷에서 데이터는 **packet(패킷)**이라는 작은 조각들로 나뉘어 전송된다.  
각 패킷은 독립적으로 **routers(라우터)**를 거쳐 목적지로 전달되며, 경로는 상황에 따라 동적으로 결정된다.

- **Store-and-Forward Transmission (저장 및 전달 방식)**
    
    - 각 라우터는 패킷을 완전히 수신한 후, 다음 목적지로 전달한다.
    - 패킷을 전송하기 전에 전체 패킷을 받아야 하므로, **transmission delay(전송 지연)**가 발생한다.
- **Routing (라우팅)**
    
    - 라우터는 목적지 주소를 확인한 후, 가장 적절한 경로를 선택하여 패킷을 전달한다.
    - 각 패킷은 서로 다른 경로로 이동할 수도 있으며, 이로 인해 **out-of-order delivery(순서 변경된 데이터 도착)**가 발생할 수 있다.
- **Queuing Delay & Packet Loss (큐잉 지연 & 패킷 손실)**
    
    - 패킷이 라우터에서 대기열(queue)에 쌓일 경우, **queuing delay(대기 지연)**가 발생한다.
    - 네트워크가 혼잡하면, 버퍼(buffer)가 가득 차 패킷이 손실(loss)될 수도 있다.

##### **💡 Real-Life Example (실생활 예시)**

> 패킷 스위칭은 **택배 배송 시스템**과 비슷하다.  
> 큰 짐(데이터)은 작은 상자(패킷)로 나뉘고, 각각 다른 경로를 통해 최종 목적지에 도착한다.  
> 어떤 상자는 먼저 도착할 수도 있고, 중간에 사라질 수도 있지만, 최종적으로 모두 도착하면 원래의 데이터로 재조립된다.

---

## **1.3.2 Circuit Switching (회선 스위칭)**

### **설명 (Explanation)**

**Circuit Switching(회선 스위칭)**은 **전화를 거는 방식과 유사한 네트워크 통신 방법**이다.  
데이터 전송을 시작하기 전에 **end-to-end(종단 간) 연결을 설정**하여 고정된 경로를 예약한다.

- **Dedicated Resources (전용 자원 할당)**
    
    - 연결이 설정되면, 전송이 끝날 때까지 해당 회선은 오직 하나의 통신만을 위해 사용된다.
    - 이는 **guaranteed bandwidth(보장된 대역폭)**을 제공하지만, 사용하지 않는 동안에도 자원이 낭비될 수 있다.
- **Multiplexing (다중화 방식)**
    
    - 여러 사용자가 동시에 네트워크를 이용하기 위해 **FDM(Frequency Division Multiplexing, 주파수 분할 다중화)** 또는  
        **TDM(Time Division Multiplexing, 시간 분할 다중화)** 기법을 사용한다.

##### **💡 Real-Life Example (실생활 예시)**

> 회선 스위칭은 **일반 전화 통화**와 유사하다.  
> 전화를 걸면 두 사람 사이에 전용 회선이 연결되고, 통화가 끝날 때까지 유지된다.  
> 하지만 한 사람이 침묵하고 있어도 회선은 여전히 차지하고 있어, 다른 사람들은 사용할 수 없다.

---

## **1.3.3 A Network of Networks (네트워크의 네트워크)**

### **설명 (Explanation)**

인터넷은 단일 네트워크가 아니라 **ISP(Internet Service Provider, 인터넷 서비스 제공자)**들의 **network of networks(네트워크의 네트워크)**이다.

### **인터넷 구조**

1. **Access ISPs (엑세스 ISP)**
    
    - 일반 사용자를 인터넷에 연결하는 ISP (예: KT, SKT, LG U+)
    - 사용자는 DSL, 케이블, 광섬유, Wi-Fi, 4G/5G 등을 통해 ISP에 접속한다.
2. **Regional ISPs (지역 ISP)**
    
    - 여러 **Access ISPs**를 연결하는 중간 네트워크
    - 하나의 국가나 특정 지역 내에서 운영됨.
3. **Tier-1 ISPs (글로벌 ISP)**
    
    - 전 세계적인 백본(backbone) 네트워크를 운영하는 거대 ISP
    - 예: AT&T, NTT, Level 3, Sprint
4. **IXP (Internet Exchange Point, 인터넷 교환 지점)**
    
    - 여러 ISP들이 서로 데이터를 교환하는 거점
    - ISP 간 **peering(피어링)**을 통해 직접 데이터를 교환하여 비용 절감 가능
5. **Content Provider Networks (콘텐츠 제공자 네트워크)**
    
    - 구글(Google), 아마존(Amazon), 넷플릭스(Netflix) 등 대형 콘텐츠 제공자가 자체 네트워크를 운영
    - 트래픽 비용을 줄이고 빠른 서비스 제공을 위해 자체 데이터 센터 구축

##### **💡 Real-Life Example (실생활 예시)**

> 인터넷 구조는 **전국 고속도로 시스템**과 비슷하다.  
> 각 도시(Access ISP)는 지방도로(Regional ISP)를 통해 고속도로(Tier-1 ISP)로 연결된다.  
> IXP는 주요 교차로처럼 여러 고속도로가 만나는 지점이며, 대형 콘텐츠 제공업체는 자신들만의 고속도로를 만든다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Network Core(네트워크 코어)**는 인터넷의 중심이며, 데이터는 **packet switching(패킷 스위칭)**을 통해 전송된다.
2. **Packet Switching(패킷 스위칭)**은 데이터를 작은 패킷으로 나누어 동적으로 전달하는 방식이다.
3. **Circuit Switching(회선 스위칭)**은 데이터를 전송하기 전에 고정된 경로를 설정하는 방식이며, 자원 낭비가 발생할 수 있다.
4. **Internet Structure(인터넷 구조)**는 계층적인 ISP들로 이루어진 **network of networks(네트워크의 네트워크)**이다.

🚀 **한 문장 요약:**  
**Network Core**는 인터넷의 중심으로 **packet switching** 방식으로 데이터를 전송하며, 다양한 ISP가 연결된 **네트워크의 네트워크**로 구성된다.