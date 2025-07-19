# 🧪 Chapter 7 종합 퀴즈 (10문제)

---

### **Q1.**

Which cryptographic method provides **integrity** but does not allow for decryption?

A. Symmetric Encryption  
B. Asymmetric Encryption  
C. Hashing  
D. Encoding

✅ **Answer: C. Hashing**  
➡ 해시는 단방향으로, 무결성 검증에 사용

---

### **Q2.**

Which of the following ensures that even if a key is compromised, previous session data remains protected?

A. Hashing  
B. Key Escrow  
C. Perfect Forward Secrecy  
D. Digital Signature

✅ **Answer: C. Perfect Forward Secrecy**  
➡ 과거 세션 키를 재사용하지 않아 안전함

---

### **Q3.**

Which algorithm is commonly used in mobile devices due to its smaller key size and lower computational cost?

A. AES  
B. RSA  
C. ECC  
D. SHA-256

✅ **Answer: C. ECC (Elliptic Curve Cryptography)**  
➡ 작은 키로 높은 보안 → 모바일에 적합

---

### **Q4.**

Which of the following uses **public key encryption** to send secure emails?

A. SFTP  
B. S/MIME  
C. HTTPS  
D. TLS

✅ **Answer: B. S/MIME**  
➡ 이메일 암호화 및 서명에 사용되는 프로토콜

---

### **Q5.**

Which protocol uses **port 22** and allows encrypted remote access?

A. HTTPS  
B. SFTP  
C. SSH  
D. FTPS

✅ **Answer: C. SSH**  
➡ 터미널 기반 암호화 원격 접속

---

### **Q6.**

A server uses a certificate issued by an untrusted CA. What error will likely occur?

A. The encryption fails  
B. The certificate cannot be verified  
C. The session expires early  
D. The key is too long

✅ **Answer: B. The certificate cannot be verified**  
➡ 브라우저가 경고: "이 사이트는 안전하지 않음"

---

### **Q7.**

Which is a **secure replacement** for older protocols like SSL and supports modern cipher suites?

A. S/MIME  
B. TLS 1.3  
C. FTP  
D. DES

✅ **Answer: B. TLS 1.3**  
➡ 최신 보안 표준 프로토콜

---

### **Q8.**

What is the primary purpose of a **digital signature**?

A. Encrypt large files quickly  
B. Convert binary data into readable format  
C. Ensure authenticity and integrity  
D. Increase password complexity

✅ **Answer: C. Ensure authenticity and integrity**  
➡ 서명은 발신자 확인 + 무결성 보장

---

### **Q9.**

Which technique involves **modifying code to make it harder to reverse-engineer** but still executable?

A. Hashing  
B. Encoding  
C. Encryption  
D. Obfuscation

✅ **Answer: D. Obfuscation**  
➡ 난독화: 코드를 읽기 어렵게 만듦

---

### **Q10.**

A website is using **TLS 1.0 and a 1024-bit RSA key**. What is the BEST recommendation?

A. Switch to SSH  
B. Upgrade to TLS 1.3 and use 2048-bit or higher RSA  
C. Change to Base64  
D. Use symmetric encryption only

✅ **Answer: B. Upgrade to TLS 1.3 and use 2048-bit or higher RSA**  
➡ 보안 강화를 위한 현대적 표준 적용 필요