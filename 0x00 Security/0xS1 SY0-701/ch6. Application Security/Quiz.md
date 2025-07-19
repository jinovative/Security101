# 🧪 Chapter 6 종합 퀴즈 (10문제)

---

### **Q1.**

A developer fails to validate user input in a form. An attacker injects SQL commands through the input field and gains unauthorized access. What type of attack occurred?

A. XSS  
B. SQL Injection  
C. IDOR  
D. CSRF

✅ **Answer: B. SQL Injection**  
➡ DB 쿼리를 조작해 인증 우회

---

### **Q2.**

A web app displays full stack traces and database errors to the user when an exception occurs. Which security principle is being violated?

A. Least Privilege  
B. Secure Defaults  
C. Error Handling  
D. Output Encoding

✅ **Answer: C. Error Handling**  
➡ 민감 정보 노출 없이 일반 오류만 표시해야 안전

---

### **Q3.**

Which of the following is BEST for testing an application **without access to the source code**?

A. SAST  
B. DAST  
C. Manual Code Review  
D. Unit Testing

✅ **Answer: B. DAST (Dynamic Application Security Testing)**  
➡ 실행 중인 앱의 취약점을 분석 → 소스코드 없이 가능

---

### **Q4.**

Which of the following techniques is used to **sanitize output** displayed in a web browser to prevent XSS attacks?

A. Encryption  
B. Output Encoding  
C. Input Validation  
D. Authentication

✅ **Answer: B. Output Encoding**  
➡ `<script>` 등 HTML 특수문자를 무해하게 표시

---

### **Q5.**

A system allows users to modify the URL and access other users’ data by changing a parameter. What vulnerability does this represent?

A. SQL Injection  
B. XSS  
C. CSRF  
D. IDOR

✅ **Answer: D. Insecure Direct Object Reference (IDOR)**  
➡ 권한 확인 없이 리소스를 직접 지정해 접근

---

### **Q6.**

An attacker forces a user’s browser to submit a request to their bank to transfer funds while they’re logged in. What type of attack is this?

A. CSRF  
B. XSS  
C. Buffer Overflow  
D. Brute Force

✅ **Answer: A. Cross-Site Request Forgery (CSRF)**  
➡ 사용자 의도 없이 요청을 자동 실행시킴

---

### **Q7.**

Which principle ensures that a user has only the minimum access necessary to perform their job functions?

A. Zero Trust  
B. Defense in Depth  
C. Least Privilege  
D. Segmentation

✅ **Answer: C. Least Privilege**  
➡ 최소한의 권한만 부여

---

### **Q8.**

A penetration tester enters `../../etc/passwd` into a file download parameter and gains access to server files. What vulnerability is this?

A. XSS  
B. SQL Injection  
C. Directory Traversal  
D. Command Injection

✅ **Answer: C. Directory Traversal**  
➡ 상위 디렉토리 접근 → 파일 노출

---

### **Q9.**

What is the BEST method to prevent sensitive data from being exposed in log files?

A. Encrypt the logs  
B. Disable logging  
C. Use secure logging practices  
D. Avoid storing timestamps

✅ **Answer: C. Use secure logging practices**  
➡ 민감 정보가 로그에 저장되지 않도록 필터링

---

### **Q10.**

Which testing method analyzes application code for vulnerabilities **before execution**?

A. DAST  
B. SAST  
C. Penetration Testing  
D. Fuzzing

✅ **Answer: B. Static Application Security Testing (SAST)**  
➡ 소스코드 자체를 분석 → 실행 전 검사