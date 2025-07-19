[[Security in Computer Networks]]

#### **요약 (Summary)**

**Securing Wireless LANs(무선 LAN 보안)**은 **Wi-Fi 네트워크에서 발생할 수 있는 보안 위협을 방지하고 안전한 연결을 보장하는 기술과 프로토콜**을 의미한다.  
무선 네트워크는 **전파(Radio Waves)를 사용하여 데이터를 전송하기 때문에 도청(Eavesdropping), 스푸핑(Spoofing), 중간자 공격(MITM, Man-in-the-Middle Attack) 같은 보안 위협에 취약**하다.  
이를 방지하기 위해 **WPA3(Wi-Fi Protected Access 3), IEEE 802.1X 인증, VPN, MAC Filtering, Firewalls** 등의 보안 기술이 사용된다.

---

## **8.8.1 Security Threats in Wireless LANs (무선 LAN 보안 위협)**

### **설명 (Explanation)**

무선 LAN(WLAN)은 **전파를 이용하여 데이터를 전송하므로 유선 네트워크보다 더 많은 보안 위협에 노출됨**.

### **1️⃣ 주요 무선 LAN 보안 위협 (Key Security Threats in WLANs)**

|보안 위협|설명|
|---|---|
|**Eavesdropping (도청 공격)**|공격자가 Wi-Fi 트래픽을 가로채 데이터를 탈취|
|**Rogue Access Points (불법 액세스 포인트, Rogue AP)**|공격자가 네트워크에 무단으로 설치한 AP를 통해 사용자 트래픽을 가로채거나 조작|
|**Man-in-the-Middle Attack (MITM, 중간자 공격)**|공격자가 사용자와 네트워크 간 트래픽을 가로채고 변조|
|**Deauthentication Attack (인증 해제 공격)**|공격자가 무선 사용자 세션을 강제로 종료하여 재연결을 유도 (예: Wi-Fi 핸드셰이크 크래킹)|
|**Evil Twin Attack (악성 쌍둥이 공격)**|공격자가 합법적인 Wi-Fi와 동일한 SSID를 가진 가짜 네트워크를 만들어 사용자 정보를 탈취|

📌 **WLAN 공격 시나리오 예제**

- **해커가 카페 Wi-Fi에서 패킷을 감청하여 사용자의 로그인 정보를 탈취**
- **공항에서 공식 Wi-Fi와 동일한 이름의 가짜 Wi-Fi(Evil Twin)를 만들어 사용자를 속이는 공격**
- **공격자가 강제로 무선 사용자를 로그아웃 시켜 다시 연결하는 과정에서 암호화 키를 탈취하는 공격**

##### **💡 Real-Life Example (실생활 예시)**

> - **공공 와이파이에서 로그인 정보를 입력했는데, 해커가 이를 감청하여 계정을 도용하는 경우**
> - **공항에서 "Free Wi-Fi"를 제공하는 가짜 네트워크에 연결하여 개인 정보가 유출되는 경우**

---

## **8.8.2 Wi-Fi Security Protocols (Wi-Fi 보안 프로토콜)**

### **설명 (Explanation)**

Wi-Fi 보안을 강화하기 위해 **다양한 무선 보안 프로토콜(WEP, WPA, WPA2, WPA3)이 사용됨**.  
초기 보안 프로토콜(WEP)은 보안성이 취약하며, 현재는 **WPA2와 WPA3가 가장 널리 사용됨**.

### **1️⃣ 주요 Wi-Fi 보안 프로토콜 (Wi-Fi Security Protocols)**

|프로토콜|암호화 방식|보안 수준|설명|
|---|---|---|---|
|**WEP (Wired Equivalent Privacy)**|RC4|낮음|128-bit 암호화 지원하지만 매우 취약|
|**WPA (Wi-Fi Protected Access)**|TKIP|중간|WEP보다 개선되었지만 여전히 보안 취약|
|**WPA2 (Wi-Fi Protected Access 2)**|AES|높음|현재 대부분의 Wi-Fi에서 사용|
|**WPA3 (Wi-Fi Protected Access 3)**|AES-GCMP|매우 높음|최신 보안 기능(SAE, 192-bit 암호화) 추가|

📌 **WPA3의 주요 보안 기능**  
✅ **SAE (Simultaneous Authentication of Equals): 보안성이 강화된 핸드셰이크 방식**  
✅ **Forward Secrecy: 세션 키가 유출되어도 이전 통신 내용 보호**  
✅ **Protected Management Frames(PMF): 디어센티케이션 공격(Deauthentication Attack) 방지**

##### **💡 Real-Life Example (실생활 예시)**

> - **WEP을 사용하는 구형 공유기는 쉽게 해킹될 수 있음 → WPA2/WPA3로 업그레이드 필요**
> - **최신 스마트폰과 노트북은 WPA3를 지원하여 더 강력한 보안 제공**

---

## **8.8.3 IEEE 802.1X and RADIUS Authentication (무선 네트워크 인증: 802.1X 및 RADIUS)**

### **설명 (Explanation)**

**기업 및 공공 Wi-Fi 네트워크에서는 사용자의 신원을 검증하기 위해 802.1X 및 RADIUS 기반 인증 시스템을 사용**.  
이 방식은 **SSID 및 패스워드 입력 방식(WPA-Personal)보다 높은 보안성을 제공**.

📌 **802.1X + RADIUS 인증 과정**

1. **사용자가 네트워크에 접속 시도**
2. **AP가 RADIUS 서버에 사용자 인증 요청**
3. **RADIUS 서버가 사용자 인증 후 네트워크 접속 승인**

📌 **802.1X 인증 방식**

|인증 방식|설명|
|---|---|
|**EAP-TLS (Extensible Authentication Protocol - TLS)**|디지털 인증서 기반의 강력한 인증 방식|
|**EAP-PEAP (Protected EAP)**|TLS 터널 내에서 사용자 이름/비밀번호 인증|
|**EAP-MSCHAPv2**|마이크로소프트 네트워크에서 주로 사용|

##### **💡 Real-Life Example (실생활 예시)**

> - **회사 Wi-Fi에 접속할 때 개인 계정 인증이 필요하도록 설정된 경우**
> - **대학 캠퍼스에서 보안 Wi-Fi를 이용할 때 인증서를 사용하여 로그인하는 경우**

---

## **8.8.4 Best Practices for Securing Wireless LANs (무선 LAN 보안을 위한 모범 사례)**

### **설명 (Explanation)**

Wi-Fi 네트워크를 보호하기 위해 **보안 프로토콜 외에도 다양한 보안 조치를 적용해야 함**.

### **1️⃣ Wi-Fi 보안 모범 사례 (Best Practices for WLAN Security)**

|보안 조치|설명|
|---|---|
|**Use WPA3 or WPA2-Enterprise**|보안이 취약한 WEP/WPA 대신 최신 보안 프로토콜 사용|
|**Disable SSID Broadcasting**|네트워크 SSID를 숨겨서 불필요한 접속 방지|
|**Enable MAC Filtering**|신뢰할 수 있는 장치만 Wi-Fi에 접속 허용|
|**Use Strong Passwords**|Wi-Fi 패스워드를 복잡하고 강력하게 설정|
|**Enable Firewall & IDS/IPS**|무선 네트워크를 보호하기 위해 방화벽 및 침입 탐지 시스템 사용|
|**Use VPN on Public Wi-Fi**|공공 Wi-Fi 사용 시 VPN을 통해 보안 강화|

📌 **Wi-Fi 보안 적용 예제**

- **공용 네트워크에서는 VPN을 활성화하여 데이터를 보호**
- **기업 네트워크에서는 802.1X 기반 RADIUS 인증을 적용하여 보안 강화**

##### **💡 Real-Life Example (실생활 예시)**

> - **카페에서 공용 Wi-Fi를 사용할 때 VPN을 켜서 보안을 강화하는 것**
> - **집 Wi-Fi에서 WPA3 암호화를 설정하고, 관리자 비밀번호를 복잡하게 변경하는 것**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Wi-Fi 네트워크는 도청, MITM 공격, 스푸핑 등의 보안 위협에 취약하므로 강력한 보안 조치가 필요하다.**
2. **WPA2 및 WPA3를 사용하여 무선 네트워크의 보안을 강화해야 한다.**
3. **802.1X 및 RADIUS 인증을 활용하면 기업 및 공공 Wi-Fi 네트워크의 보안을 높일 수 있다.**
4. **SSID 숨기기, MAC 필터링, 방화벽 활성화, VPN 사용 등의 추가 보안 조치를 적용하는 것이 중요하다.**

🚀 **한 문장 요약:**  
**Wi-Fi 네트워크 보안을 위해 WPA3, 802.1X 인증, VPN, 방화벽 등을 적용하여 도청, 스푸핑, MITM 공격을 방지해야 한다.**