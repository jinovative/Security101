# 🧪 Chapter 9 종합 퀴즈 (10문제)

---

### **Q1.**

Which log would BEST help detect multiple failed login attempts?

A. Firewall log  
B. Authentication log  
C. DNS log  
D. System boot log

✅ **Answer: B. Authentication log**  
➡ 로그인 성공/실패 이벤트 기록

---

### **Q2.**

An analyst detects repeated SQL injection attempts. Which control should be updated?

A. Firewall rule  
B. IDS signature  
C. WAF configuration  
D. SIEM correlation rule

✅ **Answer: C. WAF configuration**  
➡ WAF는 웹 공격 차단 담당 → SQLi 룰 업데이트

---

### **Q3.**

Which tool aggregates logs from multiple sources and can trigger alerts?

A. VPN  
B. IDS  
C. SIEM  
D. IPS

✅ **Answer: C. SIEM**  
➡ 수집, 분석, 경고 생성까지 담당

---

### **Q4.**

What is the primary difference between IDS and IPS?

A. IDS prevents, IPS only detects  
B. IDS is network-based, IPS is host-based  
C. IDS detects, IPS blocks  
D. IDS is for email, IPS is for firewalls

✅ **Answer: C. IDS detects, IPS blocks**  
➡ IDS: 탐지 전용 / IPS: 실시간 차단 가능

---

### **Q5.**

Which is the BEST control to prevent brute-force attacks?

A. Antivirus  
B. Password complexity policy  
C. Account lockout policy  
D. Web proxy

✅ **Answer: C. Account lockout policy**  
➡ 반복 실패 시 계정 자동 잠금

---

### **Q6.**

What should be collected FIRST during forensic evidence gathering?

A. System log files  
B. Network configuration  
C. RAM contents  
D. Archived backups

✅ **Answer: C. RAM contents**  
➡ 휘발성이 가장 높음 → 가장 먼저 확보해야 함

---

### **Q7.**

An attacker compromises a system. What is the FIRST action in the containment phase?

A. Reboot the system  
B. Disconnect from the network  
C. Delete malicious files  
D. Reimage the system

✅ **Answer: B. Disconnect from the network**  
➡ 격리 단계에서 가장 빠르고 중요한 조치

---

### **Q8.**

Which document tracks who accessed digital evidence and when?

A. Incident Response Report  
B. Log Retention Policy  
C. Chain of Custody  
D. Acceptable Use Policy

✅ **Answer: C. Chain of Custody**  
➡ 증거 신뢰성을 보장하는 핵심 문서

---

### **Q9.**

Which of the following BEST helps prevent file tampering on critical systems?

A. IDS  
B. FIM  
C. ACL  
D. Antivirus

✅ **Answer: B. FIM (File Integrity Monitoring)**  
➡ 파일 변경 여부 추적

---

### **Q10.**

A security team wants to detect unusual behavior from users over time. Which tool is BEST for this?

A. VPN  
B. UEBA  
C. IPS  
D. NAT

✅ **Answer: B. UEBA (User and Entity Behavior Analytics)**  
➡ 사용자의 평소 행위 기반 탐지