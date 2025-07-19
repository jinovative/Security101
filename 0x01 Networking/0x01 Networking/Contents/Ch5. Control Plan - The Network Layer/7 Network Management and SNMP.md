[[The Network Layer – Control Plane]]


#### **요약 (Summary)**

**Network Management(네트워크 관리)**는 **네트워크의 성능을 모니터링하고, 장애를 감지 및 해결하며, 보안을 유지하는 과정**이다.  
이를 위해 **SNMP(Simple Network Management Protocol)**가 사용되며,  
네트워크 장치(라우터, 스위치, 서버 등)의 정보를 수집하고, 원격으로 관리할 수 있도록 한다.  
SNMP는 **Manager-Agent 구조**로 동작하며, **MIB(Management Information Base)**를 이용해 네트워크 장치의 상태를 저장 및 조회한다.

---

## **5.7.1 The Role of Network Management (네트워크 관리의 역할)**

### **설명 (Explanation)**

네트워크 관리는 **기업 및 ISP가 네트워크의 성능을 최적화하고, 장애를 빠르게 해결할 수 있도록 지원**한다.

### **1️⃣ Key Functions of Network Management (네트워크 관리의 핵심 기능)**

|기능|설명|
|---|---|
|**Fault Management (장애 관리)**|네트워크 오류를 탐지하고 문제를 해결|
|**Configuration Management (설정 관리)**|네트워크 장비의 설정 변경 및 최적화|
|**Performance Management (성능 관리)**|트래픽 분석 및 네트워크 성능 모니터링|
|**Security Management (보안 관리)**|네트워크 보안 정책 적용 및 침입 탐지|
|**Accounting Management (과금 관리)**|사용자별 네트워크 사용량 측정 및 청구|

##### **💡 Real-Life Example (실생활 예시)**

> **네트워크 관리는 대형 쇼핑몰의 운영과 유사하다.**
> 
> - **Fault Management** = 엘리베이터 고장 시 즉시 수리
> - **Performance Management** = 방문객 수와 혼잡도 분석
> - **Security Management** = CCTV 및 보안 요원을 통해 도난 방지

---

## **5.7.2 SNMP: Simple Network Management Protocol (간단한 네트워크 관리 프로토콜)**

### **설명 (Explanation)**

**SNMP(Simple Network Management Protocol)**는 **네트워크 장치의 정보를 수집하고, 원격 관리할 수 있도록 하는 프로토콜**이다.

### **1️⃣ SNMP Architecture (SNMP 아키텍처 – Manager-Agent 구조)**

|구성 요소|역할|
|---|---|
|**SNMP Manager**|중앙에서 네트워크 장치를 모니터링 및 관리|
|**SNMP Agent**|네트워크 장비(라우터, 스위치, 서버 등)에 설치되어 데이터를 수집|
|**MIB (Management Information Base)**|네트워크 장치의 상태 및 설정 정보를 저장하는 데이터베이스|

### **2️⃣ SNMP Workflow (SNMP 동작 방식)**

1. **SNMP Manager(관리자)가 SNMP Agent(에이전트)에게 정보를 요청 (GET Request)**
2. **SNMP Agent는 MIB 데이터를 조회하여 응답 (GET Response)**
3. **장애 발생 시 SNMP Agent가 Manager에게 경고 메시지 전송 (Trap Message)**

##### **💡 Real-Life Example (실생활 예시)**

> **SNMP는 IT 부서에서 사무실의 모든 컴퓨터를 원격으로 관리하는 것과 유사하다.**
> 
> - **관리자(SNMP Manager)**가 **직원 PC(SNMP Agent)의 성능을 모니터링**하고,
> - **문제가 발생하면 자동으로 알림을 받음 (Trap Message).**

---

## **5.7.3 SNMP Message Types (SNMP 메시지 유형)**

### **설명 (Explanation)**

SNMP는 네트워크 장치와 정보를 주고받기 위해 **5가지 메시지 유형**을 사용한다.

### **1️⃣ SNMP Message Types (SNMP 메시지 유형별 역할)**

|메시지 타입|설명|
|---|---|
|**GET Request**|SNMP Manager가 Agent에게 데이터를 요청|
|**GET Response**|SNMP Agent가 요청된 정보를 Manager에게 응답|
|**SET Request**|SNMP Manager가 Agent의 설정을 변경|
|**Trap (경고 메시지)**|SNMP Agent가 네트워크 장애 발생 시 Manager에게 알림|
|**Inform**|Trap 메시지를 Manager가 확인했음을 응답|

##### **💡 Real-Life Example (실생활 예시)**

> - **GET Request = 직원이 관리자에게 “오늘 출근 시간 알려주세요”라고 요청**
> - **GET Response = 관리자가 “오전 9시”라고 응답**
> - **Trap = 직원이 “지금 네트워크가 다운됐어요!”라고 즉시 알림**

---

## **5.7.4 Management Information Base (MIB – 관리 정보 데이터베이스)**

### **설명 (Explanation)**

MIB는 **SNMP Agent가 관리하는 네트워크 장치의 설정 및 성능 데이터를 저장하는 데이터베이스**이다.

### **1️⃣ MIB Structure (MIB의 구조 및 OID)**

MIB는 **OID(Object Identifier)**를 사용하여 네트워크 장치의 정보를 계층적으로 저장한다.

📌 **예제: OID 구조**

scss

CopyEdit

`1.3.6.1.2.1.1.3.0  → 시스템 가동 시간 (sysUpTime) 1.3.6.1.2.1.2.2.1.10 → 인터페이스의 수신 바이트 수 (ifInOctets)`

|OID 예제|설명|
|---|---|
|**1.3.6.1.2.1.1.3.0**|장비의 현재 가동 시간|
|**1.3.6.1.2.1.2.2.1.10**|네트워크 인터페이스의 수신된 바이트 수|
|**1.3.6.1.2.1.4.20.1.1**|장비의 IP 주소|

##### **💡 Real-Life Example (실생활 예시)**

> **MIB는 회사의 인사 데이터베이스와 같다.**
> 
> - 직원 ID(OID)를 통해 **이름, 부서, 근무 시간 등** 다양한 정보를 저장 및 조회 가능.

---

## **5.7.5 SNMP Versions (SNMP 버전별 차이점)**

### **설명 (Explanation)**

SNMP는 보안 및 기능이 개선되면서 **SNMPv1 → SNMPv2 → SNMPv3**로 발전했다.

### **1️⃣ SNMP Version Comparison (SNMP 버전별 비교)**

|SNMP 버전|주요 특징|보안 수준|
|---|---|---|
|**SNMPv1**|기본적인 모니터링 기능, 보안 취약|낮음|
|**SNMPv2c**|성능 향상 및 일부 기능 개선|낮음|
|**SNMPv3**|암호화 및 인증 기능 추가|높음 ✅|

📌 **현재 대부분의 네트워크 장치는 SNMPv3를 권장하며, 보안이 강화된 환경을 제공함**

##### **💡 Real-Life Example (실생활 예시)**

> **SNMPv1 = 오래된 비밀번호 없이 로그인하는 시스템**  
> **SNMPv3 = 2단계 인증과 암호화된 로그인 시스템**

---

## **5.7.6 Security Concerns in SNMP (SNMP 보안 문제 및 해결 방법)**

### **설명 (Explanation)**

SNMP는 네트워크 관리에 필수적이지만, 보안 위협에도 취약할 수 있다.

### **1️⃣ SNMP Security Risks (SNMP 보안 위협)**

|보안 위협|설명|
|---|---|
|**SNMP Brute-Force Attack**|공격자가 SNMP Community String을 알아내어 장치를 제어|
|**SNMP Data Interception**|네트워크 관리 정보가 암호화되지 않아 도청 가능|
|**Misconfigured SNMP**|잘못된 설정으로 인해 불필요한 정보가 외부로 유출|

### **2️⃣ SNMP Security Best Practices (보안 강화 방법)**

✅ **SNMPv3 사용 (암호화 및 인증 지원)**  
✅ **SNMP Read-Only 설정하여 변경 권한 제한**  
✅ **방화벽에서 SNMP 포트(UDP 161,162) 차단**

##### **💡 Real-Life Example (실생활 예시)**

> **SNMP 보안 문제는 건물 출입 시스템과 유사하다.**
> 
> - **보안이 약하면 누구나 쉽게 출입 가능 (SNMPv1 사용)**
> - **강력한 보안 시스템이 있으면 승인된 관리자만 접근 가능 (SNMPv3 사용)**

---

### **📌 핵심 정리 (Key Takeaways)**

1. **SNMP는 네트워크 장치를 원격으로 관리하고 모니터링하는 프로토콜이다.**
2. **SNMP는 Manager-Agent 구조로 동작하며, MIB를 통해 장치 정보를 저장하고 조회한다.**
3. **SNMPv3는 암호화 및 인증 기능을 제공하여 보안을 강화한다.**
4. **SNMP 보안 문제를 방지하려면 SNMPv3를 사용하고, 방화벽 및 권한 관리를 철저히 해야 한다.**

🚀 **한 문장 요약:**  
**SNMP는 네트워크 장치의 원격 모니터링 및 관리를 위한 핵심 프로토콜이며, SNMPv3를 통해 보안을 강화하는 것이 중요하다.**