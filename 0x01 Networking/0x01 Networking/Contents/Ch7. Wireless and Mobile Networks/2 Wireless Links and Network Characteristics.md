[[Wireless and Mobile Networks]]

#### **요약 (Summary)**

**Wireless Links(무선 링크)**는 **유선 네트워크와 달리 전파(Radio Waves)를 이용하여 데이터를 전송하는 방식**이다.  
무선 네트워크의 특성상 **전파 간섭(Interference), 신호 감쇠(Path Loss), 다중 경로 전파(Multipath Propagation)** 등의 문제가 발생할 수 있다.  
무선 링크는 **Wi-Fi, 셀룰러 네트워크(4G, 5G), 위성 통신 등 다양한 환경에서 활용**되며,  
이를 극복하기 위해 **Error Correction(오류 수정), Adaptive Modulation(적응형 변조), Power Control(전력 제어) 기술이 적용된다.**

---

## **7.2.1 Characteristics of Wireless Links (무선 링크의 특성)**

### **설명 (Explanation)**

무선 링크는 **물리적 케이블 없이 공기를 통해 데이터를 전송하는 방식**이므로, 여러 가지 제약과 특성을 가진다.

### **1️⃣ Wireless Link의 주요 특징 (Key Characteristics of Wireless Links)**

|특성|설명|
|---|---|
|**Broadcast Communication (브로드캐스트 전송)**|무선 신호는 특정 장치뿐만 아니라 주변 장치에서도 수신 가능|
|**Interference (신호 간섭)**|다른 무선 신호, 전자기기, 환경적 요인에 의해 데이터 손실 발생 가능|
|**Path Loss (신호 감쇠)**|거리가 멀어질수록 신호 강도가 약해짐|
|**Multipath Propagation (다중 경로 전파)**|신호가 벽, 건물 등에 반사되어 여러 경로로 도착, 간섭을 유발|
|**Limited Bandwidth (대역폭 제한)**|무선 대역폭은 유선보다 제한적이며, 사용자 수 증가 시 속도 저하 가능|

##### **💡 Real-Life Example (실생활 예시)**

> - **Wi-Fi 신호가 벽을 지나면서 약해지는 것은 Path Loss 때문**
> - **주변에서 여러 개의 Wi-Fi 신호가 잡히는 것은 Broadcast Communication의 특징**
> - **라디오 방송이 다른 주파수와 겹쳐 잡음이 발생하는 것은 Interference 문제와 유사**

---

## **7.2.2 Wireless Transmission Impairments (무선 전송에서 발생하는 문제점)**

### **설명 (Explanation)**

무선 네트워크에서는 유선 네트워크보다 **더 많은 전송 문제**가 발생할 수 있으며,  
이를 해결하기 위한 다양한 기술이 적용된다.

### **1️⃣ 주요 무선 전송 문제 (Key Transmission Issues in Wireless Networks)**

|문제|설명|
|---|---|
|**Path Loss (경로 손실)**|거리가 멀어질수록 신호 강도가 약해짐|
|**Interference (신호 간섭)**|같은 주파수 대역에서 여러 신호가 겹쳐 데이터 오류 발생|
|**Multipath Propagation (다중 경로 문제)**|신호가 반사, 회절, 산란되어 여러 경로로 도착, 지연 및 간섭 유발|
|**Shadow Fading (그림자 페이딩)**|건물, 나무 등의 장애물로 인해 특정 지역에서 신호가 약해짐|
|**Doppler Effect (도플러 효과)**|송신자 또는 수신자가 이동할 때 주파수가 변화하여 신호 품질이 저하됨|

##### **💡 Real-Life Example (실생활 예시)**

> - **터널 안에서 휴대전화 신호가 약해지는 것은 Shadow Fading 때문**
> - **고속열차에서 LTE 신호가 순간적으로 끊기는 것은 Doppler Effect의 영향**
> - **Wi-Fi가 멀리 갈수록 속도가 느려지는 것은 Path Loss 때문**

---

## **7.2.3 Wireless Transmission Techniques (무선 전송 기법 및 기술)**

### **설명 (Explanation)**

무선 네트워크의 문제점을 해결하고, 신뢰성을 높이기 위해 다양한 기술이 사용된다.

### **1️⃣ 주요 무선 전송 기법 (Key Wireless Transmission Techniques)**

|기술|설명|
|---|---|
|**Error Correction (오류 수정)**|FEC(Forward Error Correction) 등을 사용하여 오류 발생 시 자동 복구|
|**Adaptive Modulation (적응형 변조)**|신호 품질에 따라 변조 방식(BPSK, QAM 등) 자동 조절|
|**Power Control (전력 제어)**|송신 전력을 최적화하여 신호 간섭과 배터리 소모를 줄임|
|**MIMO (Multiple Input Multiple Output)**|여러 개의 안테나를 사용하여 데이터 속도 향상 및 신호 간섭 감소|
|**Beamforming (빔포밍)**|특정 방향으로 신호를 집중하여 송출하여 신호 강도를 극대화|

##### **💡 Real-Life Example (실생활 예시)**

> - **Adaptive Modulation = 인터넷 속도가 느려질 때 자동으로 해상도를 낮춰 동영상을 재생하는 것**
> - **MIMO = 여러 개의 도로를 동시에 사용하여 차량 흐름을 최적화하는 것**
> - **Beamforming = 레이저 포인터처럼 특정 방향으로 신호를 집중해서 전송하는 것**

---

## **7.2.4 Frequency Bands and Spectrum Allocation (주파수 대역 및 스펙트럼 할당)**

### **설명 (Explanation)**

무선 네트워크는 **전파(주파수 대역)를 사용하여 데이터를 전송하며, 이를 효율적으로 관리하기 위해 주파수 할당이 필요**하다.

### **1️⃣ 주요 주파수 대역 (Key Frequency Bands for Wireless Networks)**

|주파수 대역|사용 사례|
|---|---|
|**2.4 GHz**|Wi-Fi (802.11b/g/n), 블루투스|
|**5 GHz**|Wi-Fi (802.11a/ac/ax), 일부 무선 통신|
|**Sub-6 GHz (4G, 5G NR)**|셀룰러 네트워크 (LTE, 5G)|
|**mmWave (밀리미터파, 24~100 GHz)**|초고속 5G, 위성 통신|

📌 **주파수 대역별 특징**  
✅ **2.4 GHz** → 도달 범위가 넓지만 속도가 상대적으로 낮음  
✅ **5 GHz** → 속도가 빠르지만 벽을 통과하는 능력이 약함  
✅ **mmWave(밀리미터파, 24GHz 이상)** → 초고속이지만 장애물에 취약

##### **💡 Real-Life Example (실생활 예시)**

> - **2.4 GHz Wi-Fi = 아파트 전체를 커버할 수 있지만 속도는 느림**
> - **5 GHz Wi-Fi = 속도가 빠르지만 벽을 지나면서 신호가 약해짐**
> - **5G mmWave = 다운로드 속도는 매우 빠르지만 건물 내부에서는 신호가 잘 잡히지 않음**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **무선 링크는 신호 간섭(Interference), 신호 감쇠(Path Loss), 다중 경로 전파(Multipath) 등의 문제를 가짐.**
2. **MIMO, Beamforming, Adaptive Modulation 등의 기술을 통해 무선 네트워크 성능을 향상시킴.**
3. **무선 네트워크는 2.4GHz, 5GHz, mmWave 등의 주파수 대역을 사용하며, 각 대역은 속도와 도달 범위가 다름.**

🚀 **한 문장 요약:**  
**무선 링크는 신호 감쇠, 간섭, 다중 경로 문제를 해결하기 위해 MIMO, 빔포밍, 전력 제어 등의 기술을 적용하며, Wi-Fi, 4G, 5G 네트워크에서 다양한 주파수 대역을 활용한다.**
