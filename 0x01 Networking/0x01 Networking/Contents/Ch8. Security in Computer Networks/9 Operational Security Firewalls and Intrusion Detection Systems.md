[[Security in Computer Networks]]

#### **요약 (Summary)**

**Operational Security(운영 보안)**은 **네트워크 및 시스템을 보호하기 위한 정책, 프로세스, 보안 장비의 운영을 의미**한다.  
이 중에서 가장 중요한 보안 장비는 **Firewalls(방화벽)**과 **Intrusion Detection Systems(IDS, 침입 탐지 시스템)**이다.  
방화벽은 **네트워크 트래픽을 필터링하여 악성 트래픽을 차단**하며, IDS는 **네트워크 활동을 모니터링하여 이상 행위를 탐지**한다.

---

## **8.9.1 Firewalls (방화벽: 네트워크 트래픽 필터링 장치)**

### **설명 (Explanation)**

**Firewall(방화벽)**은 **네트워크 내부와 외부 간의 트래픽을 제어하는 보안 장비 또는 소프트웨어**이다.  
불법적인 접근을 차단하고, **악성 트래픽을 필터링하여 네트워크를 보호**한다.

### **1️⃣ 방화벽의 주요 기능 (Key Functions of Firewalls)**

|기능|설명|
|---|---|
|**Packet Filtering (패킷 필터링)**|IP 주소, 포트 번호 등을 기반으로 트래픽을 허용 또는 차단|
|**Stateful Inspection (상태 기반 검사)**|세션 정보를 분석하여 정상적인 트래픽인지 확인|
|**Application Layer Filtering (애플리케이션 계층 필터링)**|특정 애플리케이션(예: HTTP, FTP) 트래픽을 제어|
|**NAT (Network Address Translation, 네트워크 주소 변환)**|내부 IP 주소를 숨겨 외부 공격으로부터 보호|

📌 **방화벽 동작 예제**

1. **사용자가 웹사이트(http://example.com)에 접속 요청**
2. **방화벽이 트래픽을 검사하여 허용된 IP 및 포트인지 확인**
3. **정상적인 요청이면 허용, 비정상적인 요청이면 차단**

##### **💡 Real-Life Example (실생활 예시)**

> - **회사 네트워크에서 직원이 특정 웹사이트(예: SNS, 불법 사이트)에 접근하는 것을 방화벽이 차단하는 경우**
> - **방화벽이 허용되지 않은 외부 IP에서의 접근을 차단하여 해킹 공격을 방지하는 경우**

---

### **2️⃣ Types of Firewalls (방화벽의 유형)**

|방화벽 유형|설명|예제|
|---|---|---|
|**Packet Filtering Firewall**|IP, 포트 기반으로 트래픽을 필터링|Cisco ACL, iptables|
|**Stateful Firewall**|연결 상태를 기반으로 트래픽을 검사|Check Point Firewall|
|**Proxy Firewall**|클라이언트와 서버 간 트래픽을 중개하여 보안 강화|Squid Proxy|
|**Next-Generation Firewall (NGFW)**|애플리케이션 수준에서 트래픽을 분석 및 제어|Palo Alto Networks NGFW|

📌 **Packet Filtering vs. Stateful Firewall 비교**  
✅ **Packet Filtering → 단순하지만 빠름, 보안 기능 제한**  
✅ **Stateful Firewall → 더 정교한 보안 기능 제공, 더 많은 리소스 필요**

##### **💡 Real-Life Example (실생활 예시)**

> - **Packet Filtering → 회사 네트워크에서 특정 포트(예: 22, SSH) 차단**
> - **Stateful Firewall → 비정상적인 트래픽 패턴 감지 및 차단**

---

## **8.9.2 Intrusion Detection Systems (IDS: 침입 탐지 시스템)**

### **설명 (Explanation)**

**Intrusion Detection System(IDS, 침입 탐지 시스템)**은 **네트워크 또는 시스템에서 발생하는 보안 이벤트를 감지하고 경고하는 시스템**이다.  
IDS는 **네트워크 트래픽 또는 시스템 로그를 분석하여 악성 활동을 탐지**한다.

### **1️⃣ IDS의 주요 기능 (Key Functions of IDS)**

|기능|설명|
|---|---|
|**Anomaly Detection (이상 탐지)**|정상적인 트래픽 패턴과 비교하여 비정상적인 행위를 탐지|
|**Signature-Based Detection (시그니처 기반 탐지)**|알려진 공격 패턴(예: SQL Injection, DoS)을 감지|
|**Alert Generation (경고 생성)**|탐지된 보안 이벤트에 대해 관리자에게 경고|
|**Logging (로그 기록)**|침입 시도를 기록하여 사후 분석 가능|

📌 **IDS 동작 예제**

1. **네트워크에서 비정상적인 트래픽(예: 다량의 로그인 실패)이 발생**
2. **IDS가 공격 패턴을 분석하여 관리자에게 경고**
3. **보안 관리자가 로그를 분석하여 추가 조치를 수행**

##### **💡 Real-Life Example (실생활 예시)**

> - **기업 네트워크에서 IDS가 "대량의 로그인 실패"를 탐지하여 경고를 발생하는 경우**
> - **웹 서버에서 SQL Injection 공격이 탐지되어 IDS가 관리자에게 알림을 보내는 경우**

---

### **2️⃣ Types of IDS (IDS의 유형)**

|IDS 유형|설명|예제|
|---|---|---|
|**NIDS (Network-Based IDS)**|네트워크 트래픽을 분석하여 침입을 탐지|Snort, Suricata|
|**HIDS (Host-Based IDS)**|호스트(서버, PC)에서 로그를 분석하여 침입을 탐지|OSSEC, Tripwire|

📌 **NIDS vs. HIDS 비교**  
✅ **NIDS → 네트워크 전체를 모니터링 가능, 실시간 탐지 가능**  
✅ **HIDS → 특정 서버나 장치에서 침입을 감지, 로그 기반 탐지**

##### **💡 Real-Life Example (실생활 예시)**

> - **NIDS → 기업 네트워크에서 Snort가 네트워크 트래픽을 분석하여 악성 활동 탐지**
> - **HIDS → 웹 서버에서 파일이 비정상적으로 변경되었을 때 Tripwire가 경고**

---

## **8.9.3 Intrusion Prevention Systems (IPS: 침입 방지 시스템)**

### **설명 (Explanation)**

**Intrusion Prevention System(IPS, 침입 방지 시스템)**은 **IDS의 탐지 기능을 확장하여 실시간으로 공격을 차단하는 시스템**이다.  
IDS는 **탐지만 수행**하지만, IPS는 **탐지 후 공격을 차단**할 수 있다.

📌 **IDS vs. IPS 비교**

|시스템|기능|차이점|
|---|---|---|
|**IDS (Intrusion Detection System)**|공격 탐지 및 경고|공격을 차단하지 않고 관리자에게 알림|
|**IPS (Intrusion Prevention System)**|공격 탐지 및 차단|실시간으로 악성 트래픽을 차단|

✅ **IPS는 방화벽과 함께 동작하여 네트워크 보안을 더욱 강화할 수 있음**

##### **💡 Real-Life Example (실생활 예시)**

> - **IDS → 웹사이트에서 SQL Injection 공격이 탐지되었지만 차단되지 않고 로그만 남김**
> - **IPS → 동일한 공격이 발생하면 즉시 차단하여 웹 서버를 보호**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **Firewalls(방화벽)는 네트워크 트래픽을 필터링하여 악성 트래픽을 차단하는 보안 장비이다.**
2. **Intrusion Detection Systems(IDS)는 네트워크 또는 호스트에서 발생하는 보안 이벤트를 탐지하고 경고를 발생시킨다.**
3. **Intrusion Prevention Systems(IPS)는 IDS의 기능을 확장하여 공격을 실시간으로 차단하는 역할을 한다.**
4. **Packet Filtering Firewall, Stateful Firewall, Next-Generation Firewall(NGFW) 등 다양한 방화벽 유형이 존재하며, 각기 다른 보안 기능을 제공한다.**

🚀 **한 문장 요약:**  
**방화벽(Firewall)은 네트워크 트래픽을 필터링하고, IDS는 침입을 탐지하며, IPS는 침입을 실시간으로 차단하여 네트워크 보안을 강화한다.**