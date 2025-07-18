[[The Link Layer and LANs]]


#### **요약 (Summary)**

**Error Detection and Correction(오류 검출 및 수정)**은 **데이터가 네트워크를 통해 전송될 때 발생할 수 있는 오류를 감지하고, 필요할 경우 수정하는 기술**이다.  
링크 계층(Link Layer)에서는 **비트 오류(Bit Errors)를 감지하고, 신뢰성을 높이기 위해 다양한 오류 검출 및 수정 기법을 사용**한다.  
주요 기법으로는 **Parity Check(패리티 체크), Checksum(체크섬), CRC(Cyclic Redundancy Check, 순환 중복 검사), Hamming Code(해밍 코드) 등이 있다.**

---

## **6.2.1 Causes of Errors in Data Transmission (데이터 전송 중 오류 발생 원인)**

### **설명 (Explanation)**

네트워크에서 **데이터가 전송되는 동안 다양한 환경적 요인으로 인해 오류가 발생할 수 있음**.

### **1️⃣ 주요 오류 발생 원인 (Key Causes of Errors)**

|원인|설명|
|---|---|
|**Electromagnetic Interference (전자기 간섭, EMI)**|전자기파(전력선, 무선 신호)로 인해 데이터가 변형됨|
|**Attenuation (감쇠)**|장거리 전송 시 신호가 약해져서 데이터가 손상됨|
|**Cross Talk (혼선)**|두 개의 신호가 서로 간섭하여 데이터 오류 발생|
|**Noise (잡음)**|환경적 요인(무선 신호 방해, 기계적 진동)으로 인해 데이터가 변형됨|

##### **💡 Real-Life Example (실생활 예시)**

> **데이터 전송 중 오류는 라디오 신호가 약해질 때 음질이 왜곡되는 것과 유사하다.**
> 
> - 신호가 약해지거나(감쇠) 다른 주파수와 섞이면(혼선) 데이터 오류가 발생할 수 있음.

---

## **6.2.2 Error Detection Techniques (오류 검출 기법)**

### **설명 (Explanation)**

**오류 검출(Error Detection)**은 **데이터 전송 중 발생한 오류를 송신자가 확인할 수 있도록 하는 방법**이다.

### **1️⃣ Parity Check (패리티 체크 – 가장 기본적인 오류 검출 기법)**

- **각 데이터 블록에 1비트를 추가하여 오류를 검출**.
- **Even Parity(짝수 패리티):** 1의 개수가 짝수가 되도록 패리티 비트 추가.
- **Odd Parity(홀수 패리티):** 1의 개수가 홀수가 되도록 패리티 비트 추가.

📌 **패리티 체크 예제 (Even Parity)**

makefile

CopyEdit

`데이터: 1010101 → 패리티 비트 추가: 10101010 (짝수 개의 1) 데이터: 1101011 → 패리티 비트 추가: 11010111 (짝수 개의 1)`

✅ **장점:** 간단하고 구현이 쉬움.  
❌ **단점:** 짝수 개의 오류 발생 시 오류 검출이 불가능함.

---

### **2️⃣ Checksum (체크섬 – 간단한 오류 검출 기법)**

- **데이터 블록의 값을 더한 후, 그 합을 전송하여 오류를 감지**.
- **수신 측에서 동일한 연산을 수행하고 값이 일치하는지 확인**.

📌 **Checksum 예제**

yaml

CopyEdit

`송신 측: Data: 1010 1100 0101 0011 → Binary Sum: 1111 1101 → Complement: 0000 0010 (Checksum)  수신 측: Data + Checksum = 1111 1111 → 값이 일치하면 오류 없음`

✅ **장점:** 네트워크 트랜스포트 계층(TCP, UDP)에서 많이 사용됨.  
❌ **단점:** 특정 유형의 오류(예: 비트가 교환되는 오류) 검출 불가능.

---

### **3️⃣ Cyclic Redundancy Check (CRC, 순환 중복 검사 – 강력한 오류 검출 기법)**

- **데이터를 다항식(Polynomial)으로 변환하고, 특정 나눗셈 연산을 수행하여 오류를 검출**.
- **하드웨어(네트워크 인터페이스 카드, NIC)에서 자동으로 처리 가능**.

📌 **CRC 연산 과정**

1. 송신자가 데이터를 특정 다항식으로 나누고 **나머지(Remainder)를 추가**하여 전송.
2. 수신자가 동일한 나눗셈을 수행하여 오류 여부를 검증.
3. 나머지가 0이면 데이터가 정상, 그렇지 않으면 오류 발생.

✅ **장점:** 매우 강력한 오류 검출 기능을 제공함.  
❌ **단점:** 하드웨어 연산이 필요하며, 단순한 패리티 체크보다 복잡함.

##### **💡 Real-Life Example (실생활 예시)**

> **CRC는 신용카드 번호 검증 방식과 유사하다.**
> 
> - 입력한 카드 번호가 올바른지 확인하기 위해 마지막 몇 자리 숫자로 오류 검출 수행.

---

## **6.2.3 Error Correction Techniques (오류 수정 기법)**

### **설명 (Explanation)**

**오류 수정(Error Correction)**은 **오류가 발생한 데이터를 재전송하지 않고, 자체적으로 복구할 수 있도록 하는 방법**이다.

### **1️⃣ Hamming Code (해밍 코드 – 오류 검출 및 수정 가능)**

- **여러 개의 패리티 비트를 추가하여 오류를 검출하고 수정 가능**.
- **단일 비트 오류(Single Bit Error)를 자동으로 수정할 수 있음**.

📌 **Hamming Code 예제**

makefile

CopyEdit

`데이터: 1011 → 해밍 코드 추가: 1011010 (패리티 비트 포함) 수신 측에서 오류 발생 시 패리티 비트를 활용해 자동 수정 가능.`

✅ **장점:** 단일 비트 오류를 자동으로 수정할 수 있음.  
❌ **단점:** 추가적인 패리티 비트가 필요하여 데이터 크기가 증가함.

---

### **2️⃣ Forward Error Correction (FEC, 전방 오류 수정 – 고속 네트워크에서 사용됨)**

- **송신 측에서 데이터에 추가 정보를 포함하여, 수신 측에서 오류를 자동으로 수정할 수 있도록 함**.
- **위성 통신, 광섬유 네트워크, 무선 네트워크 등에서 사용됨**.

📌 **FEC 예제 (Reed-Solomon Code)**

yaml

CopyEdit

`원래 데이터: 1101 0010 1011 FEC 추가 데이터: 1101 0010 1011 0110 (오류 검출 및 수정 가능)`

✅ **장점:** 데이터 재전송(ARQ) 없이 오류를 수정할 수 있음.  
❌ **단점:** 추가 데이터가 필요하여 대역폭을 더 많이 사용함.

##### **💡 Real-Life Example (실생활 예시)**

> **FEC는 스마트폰에서 음성 데이터가 손실될 경우 자동으로 보정하는 기능과 유사하다.**
> 
> - 예를 들어, **Wi-Fi가 약한 상태에서도 음성이 왜곡되지 않는 이유가 FEC 덕분**.

---

### **📌 핵심 정리 (Key Takeaways)**

1. **링크 계층에서는 오류 검출 및 수정을 위해 다양한 기술을 사용한다.**
2. **Parity Check, Checksum, CRC는 오류를 검출하는 기법이며, CRC가 가장 강력한 검출 기능을 제공한다.**
3. **Hamming Code와 FEC는 오류를 수정하는 기법이며, 특히 FEC는 무선 네트워크에서 많이 사용된다.**
4. **오류 수정 기술을 사용하면 데이터 재전송 없이 신뢰성 있는 전송이 가능하지만, 추가적인 데이터가 필요하여 대역폭을 더 많이 사용한다.**

🚀 **한 문장 요약:**  
**링크 계층에서는 패리티 체크, 체크섬, CRC 등의 오류 검출 기법과, 해밍 코드, FEC 같은 오류 수정 기법을 사용하여 데이터 전송의 신뢰성을 보장한다.**