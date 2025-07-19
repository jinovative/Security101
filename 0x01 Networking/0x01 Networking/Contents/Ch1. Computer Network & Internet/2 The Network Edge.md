[[Computer Networks and the Internet]]

### **1.2 The Network Edge**

#### **요약 (Summary)**

인터넷의 가장자리, 즉 **Network Edge**는 우리가 직접 사용하는 **End Systems(종단 시스템)**과 이를 인터넷에 연결하는 **Access Networks(접속 네트워크)**로 구성된다.  
End Systems에는 컴퓨터, 스마트폰, IoT 기기 등이 포함되며, 이들은 인터넷을 통해 서로 데이터를 주고받는다.  
Access Networks는 인터넷과 사용자를 연결하는 네트워크로, **Wi-Fi, Ethernet, DSL, Cable, 4G/5G** 같은 다양한 기술이 존재한다.

---

### **1.2.1 Access Networks (접속 네트워크)**

#### **설명 (Explanation)**

**Access Network**는 사용자의 **End System**을 인터넷에 연결하는 네트워크이다.  
이 네트워크의 종류에 따라 속도와 성능이 달라지며, 일반적으로 세 가지 주요 카테고리로 나뉜다.

#### **1️⃣ Home Access (가정용 네트워크)**

집에서 인터넷을 사용할 때 접속하는 네트워크로, 대표적인 기술은 다음과 같다.

- **DSL (Digital Subscriber Line, 디지털 가입자 회선)**  
    전화선(Twisted-pair copper wire)을 이용해 인터넷을 연결하는 방식.
    
    - **다운로드 속도:** 10~100 Mbps
    - **업로드 속도:** 1~10 Mbps
- **Cable (케이블 인터넷)**  
    TV 케이블(Coaxial cable)을 사용하여 인터넷을 제공. 여러 사용자가 대역폭을 공유함.
    
    - **다운로드 속도:** 50~1000 Mbps
    - **업로드 속도:** 10~50 Mbps
- **Fiber to the Home (FTTH, 광섬유 인터넷)**  
    광섬유(Optical Fiber)를 집까지 직접 연결하여 빠른 인터넷 속도를 제공.
    
    - **다운로드 속도:** 최대 10 Gbps
- **Satellite Internet (위성 인터넷)**  
    위성을 이용하여 인터넷을 제공. 지연 시간(Latency)이 높아 빠른 응답이 필요한 서비스에는 부적절.
    
    - **다운로드 속도:** 10~100 Mbps
    - **Latency:** 500ms 이상

---

#### **2️⃣ Enterprise Access (기업 및 학교 네트워크)**

기업과 학교에서는 빠르고 안정적인 네트워크 연결이 필요하며, 보통 **Ethernet(이더넷)**과 **Wi-Fi**가 사용된다.

- **Ethernet (이더넷)**
    
    - 유선 네트워크로 높은 속도와 안정성을 제공.
    - **속도:** 100 Mbps ~ 100 Gbps
- **Wi-Fi (Wireless LAN, 무선 랜)**
    
    - 무선으로 인터넷 연결을 제공하며, 기업, 학교, 공공장소에서 많이 사용됨.
    - **속도:** 50~1000 Mbps (Wi-Fi 6 기준)

---

#### **3️⃣ Wide-Area Wireless Access (광역 무선 네트워크)**

이동 중에도 인터넷을 사용할 수 있도록 하는 네트워크.

- **3G, 4G LTE, 5G Cellular Networks**
    - 3G: 1~10 Mbps
    - 4G LTE: 10~100 Mbps
    - 5G: 1~10 Gbps (저지연, 고속 전송 지원)

##### **💡 Real-Life Example (실생활 예시)**

> Access Network는 **고속도로 입구**와 같다.  
> 가정에서는 집 앞 도로(DSL, Cable, Fiber)를 통해 고속도로(인터넷 백본)로 진입하고, 회사에서는 전용 차선(Ethernet)을 이용해 빠르게 이동한다.  
> Wi-Fi는 주차장과 같아서 여러 장치들이 공유하고, 4G/5G는 이동 중에도 인터넷을 사용할 수 있도록 한다.

---

### **1.2.2 End Systems (종단 시스템)**

#### **설명 (Explanation)**

**End Systems(호스트, Host)**는 네트워크에 연결된 장치들로, 사용자들이 직접 사용하는 기기들이다.

- **PC, 노트북**
- **스마트폰, 태블릿**
- **서버 (Web Server, Email Server 등)**
- **IoT(Internet of Things) 기기**: 스마트 TV, 스마트워치, 홈 자동화 시스템

End Systems는 데이터를 주고받을 수 있도록 네트워크에 연결되며, 인터넷을 통해 통신한다.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Network Edge**는 인터넷의 최종 사용자 장치(End Systems)와 인터넷 연결 방식(Access Networks)으로 구성된다.
2. **Access Networks**는 인터넷 연결을 담당하며, 대표적인 기술로 **DSL, Cable, Fiber, Wi-Fi, 4G/5G**가 있다.
3. **End Systems**는 인터넷을 사용하는 장치들(PC, 스마트폰, 서버, IoT 기기)로, 네트워크를 통해 서로 데이터를 주고받는다.

🚀 **한 문장 요약:**  
**Network Edge**는 사용자가 인터넷을 접하는 부분으로, **Access Network**를 통해 **End System**이 인터넷에 연결되는 구조이다.
