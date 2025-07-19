### 📚 모듈 2: Skyhigh Security Cloud의 핵심 기능과 아키텍처

이 모듈에서는 Skyhigh Security Cloud가 제공하는 주요 보안 기능들과 이러한 기능들을 가능하게 하는 내부 구조 및 구성 요소들을 살펴봅니다.

---

#### **강의 2.1: Skyhigh Security Cloud의 핵심 기능**

Skyhigh Security Cloud는 클라우드 보안을 위해 크게 네 가지 핵심 기능을 제공합니다.

- **가시성 (Visibility)**
    - **민감 데이터 및 사용자 그룹 식별**: 어떤 데이터가 민감한 정보인지, 그리고 다양한 사용자 그룹이 어떻게 클라우드 서비스를 활용하는지 파악합니다.
        
    - **온디맨드 스캔 (On-demand Scan) 수행**: 클라우드 서비스 내에 저장된 민감한 콘텐츠를 필요에 따라 즉시 스캔하여 식별합니다.
        
    - **지속적인 위험 평가**: 클라우드 서비스 사용에 따른 위험을 지속적으로 평가합니다.
        
    - **클라우드 서비스 레지스트리 유지**: 20,000개가 넘는 클라우드 서비스에 대한 50개 이상의 속성 기반 위험 평가 정보를 담고 있는 클라우드 레지스트리(Cloud Registry)를 유지 관리합니다. 이를 통해 서비스 분류(클라우드 스토리지, CRM 등)를 넘어 각 서비스의 속성에 따른 위험도를 평가할 수 있습니다.
        
- **위협 보호 (Threat Protection)**
    - **데이터 유출 사전 방지 목표**: 위협이 실제 데이터 유출로 이어지기 전에 차단하는 것을 목표로 합니다.
        
    - **위협 탐지**: 다음과 같은 위협을 탐지합니다:
        
        - 비정상적인 활동 (anomalous activity)
        - 내부자 위협 (insider threat) 및 계정 탈취 (compromised accounts)
        - 무차별 암호 대입 공격 (brute force login attempts)
        - 악성코드 (malware)
    - **대응 조치**: 의심스러운 비정상 활동에 대해 클라우드 접근 차단, 사용자 권한을 읽기 전용으로 제한, 암호화 서비스 제공, 추가 인증 요구 등의 조치를 취합니다.
        
- **규정 준수 (Compliance)**
    - **민감 데이터 위반 규정 설정**: 민감 데이터 관련 정책 위반 시 적용될 규정을 설정합니다.
        
    - **특정 그룹에 대한 추가 통제**: 특정 사용자 그룹에 대해서는 추가적인 보안 통제를 적용합니다.
        
    - **DLP (Data Loss Prevention, 데이터 유출 방지) 정책**: DLP 정책을 통해 데이터를 가로채거나, 삭제하거나, 격리(quarantine)할 수 있도록 지원합니다.
        
- **데이터 보안 (Data Security)**
    - **암호화**: 데이터 보호 정책에 따라 민감 데이터를 암호화하며, 이때 검색 기능을 보존하는 방식을 지원합니다.
        
    - **BYOD (Bring Your Own Device, 개인 기기 사용) 지원**: 민감 데이터의 위험 없이 직원들이 개인 기기를 사용하여 클라우드에 접근할 수 있도록 지원합니다. Skyhigh Security Cloud는 조직이 비즈니스를 가속화할 수 있도록 클라우드 내 데이터에 대한 완전한 가시성과 제어권을 제공하고 클라우드 위협으로부터 보호합니다.
        

---

#### **강의 2.2: Skyhigh Security Cloud 아키텍처 이해하기**

Skyhigh Security Cloud의 아키텍처는 다양한 구성 요소와 연결 방식을 통해 위에서 언급된 핵심 기능들을 제공합니다.

- **아키텍처 개요**
    - Skyhigh Security Cloud 솔루션은 가시성, 규정 준수, 위협 보호, 데이터 보안을 제공하기 위해 다양한 구성 요소들이 유기적으로 작동합니다.
        
    - Skyhigh Security Cloud는 기기에 새로운 에이전트를 배포하지 않으며, 최종 사용자 경험에 영향을 미치지 않도록 설계되었습니다.
        
- **배포 모드 (Deployment Modes)**
    - Skyhigh Security Cloud는 사용 사례, 사용자, 디바이스, 서비스 전반에 걸쳐 모든 상황을 포괄하는 다중 모드 배포를 제공합니다. 크게 두 가지 범주로 나뉩니다.
        
        - **대역 외 배포 모드 (Out-of-band Deployment Modes)**: 사용자-클라우드 간 트래픽뿐만 아니라 클라우드-클라우드 간 트래픽을 포괄하는 비동기식 API(Application Programming Interface)를 사용합니다.
            
        - **인라인 배포 모드 (Inline Deployment Modes)**: 사용자-클라우드 간 및 클라우드-클라우드 간 트래픽 사이에 위치하는 프록시(proxy)를 참조합니다. 인라인 통제를 구현하기 위해 CASB는 정방향(forward) 및 역방향(reverse) 프록시 모드로 구현될 수 있습니다.
            
- **주요 구성 요소**
    - **클라우드 커넥터 (Cloud Connector, CC)**
        - 기업 네트워크와 Skyhigh Security Cloud 간의 통합 지점을 제공하는 온프레미스(on-premises, 기업 내부에 설치 운영) 소프트웨어 서비스입니다.
            
        - 네트워크 토폴로지에 따라 중앙 집중식 또는 분산형으로 배포할 수 있으며, 일반적으로 가상 머신에 Windows, Linux/Unix 또는 Mac 환경으로 설치됩니다.
            
        - **주요 책임**: 보안 출구 장치 로그 수집 및 처리, AD(Active Directory)와의 LDAP(Lightweight Directory Access Protocol) 통합, 로그 데이터 사전 필터링, 기업 SIEM(Security Information and Event Management, 보안 정보 및 이벤트 관리)과의 통합, Active Directory 통합, Skyhigh Security Cloud 데이터 센터와의 로그 보안 전송, 기업 PII(Personally Identifiable Information, 개인 식별 정보) 토큰화, 웹 프록시를 사용한 폐쇄 루프 개선(Closed Loop Remediation) 등을 담당합니다.
            
    - **스카이 링크 (Sky Link - API 통합)**
        - Skyhigh Security Cloud는 SaaS 서비스에 대한 독점적인 API 연결인 스카이 링크를 활용합니다.
            
        - 이 대역 외 API 접근 방식은 모든 장치 또는 위치에서의 트랜잭션을 모니터링하고 제어합니다. 모든 개선 조치가 대역 외에서 발생하므로 API 제어는 거의 실시간으로 이루어집니다.
            
        - **두 가지 일반적인 접근 방식**:
            
            - **API 폴링 (API Poll)**: 클라우드 서비스 제공업체(Cloud Service Provider, CSP) 서비스 API를 주기적으로 폴링하여 마지막 폴링 이후 발생한 이벤트 목록을 가져오는 '풀(pull)' 방식입니다.
                
            - **웹훅 (Webhook)**: CSP가 활동 발생 시 이를 '푸시(push)'하는 모델입니다. 예를 들어 사용자가 CSP에 파일을 업로드하면 웹훅이 이벤트를 Skyhigh Security Cloud로 보내 조치를 취하거나 보고하도록 합니다.
                
        - **API 접근 방식의 이점**: CSP 변경 최소화, CSP 지원, 네트워크 전송 변경 불필요(Skyhigh Security Cloud는 대역 외 유지), 프록시나 트래픽 리디렉션 불필요, 일반적으로 설정이 쉽고 비침습적(위험 최소화)입니다.
            
        - API 통합은 클라우드 서비스에 연결하여 로그 수집 및 분석, 거의 실시간 DLP 기능 제공, 클라우드 서비스의 온디맨드 스캔(ODS) 실행, 클라우드 서비스에 대한 악성코드 스캔 제공 등이 필요할 때 배포합니다.
            
    - **라이트닝 링크 (Lightning Link)**
        - Skyhigh Security Cloud만이 제공하는 기능으로, O365 (Office 365)에서의 협업에 대한 실시간 제어를 가능하게 합니다.
            
        - 직원이 정책을 위반하여 고객 신용카드 번호와 같은 규제 대상 데이터가 포함된 문서를 알 수 없는 사용자의 개인 Gmail 주소로 공유하는 경우, 라이트닝 링크는 문서가 수신자에게 도달하기 전에 실시간으로 이를 방지할 수 있습니다.
            
        - 실시간 제어는 적용 틈새를 방지하고 즉각적인 개선을 제공합니다.
            
        - 라이트닝 링크 정책은 폴더/파일 협업, 링크를 통한 웹 공개 공유(익명 링크), 링크를 통한 회사 내 웹 공유(조직 수준 접근 권한이 있는 링크) 작업만 지원합니다. 콘텐츠(데이터 식별자, 키워드 기반 검사 등) 또는 파일 메타데이터(파일 이름, 유형, 크기) 기반 DLP 정책 적용에는 사용할 수 없습니다.
            
    - **스카이 게이트웨이 (Sky Gateway - 프록시)**
        - 접근 제어, 인라인 암호화 등 실시간 적용이 필요한 다른 제어 기능을 담당합니다.
            
        - 다른 프록시와 달리, 스카이 게이트웨이는 ID 공급자(Identity Provider, IDP)와 직접 통합하여 **역방향 프록시(Reverse Proxy)** 모드로 작동합니다. 이를 통해 모든 사용자는 인증 후 게이트웨이를 통해 라우팅됩니다. 이는 관리되지 않는 장치의 사용자 및 고객, 파트너, 공급업체와 같이 클라우드 서비스에 접근하는 제3자에 대한 실시간 제어를 적용하는 데 중요합니다.
            
        - **스카이 게이트웨이 유니버설 모드 (Universal Mode)**: 고객 정의 및 Skyhigh Security Cloud 관리 허영 도메인(vanity domain)을 사용하여 모든 장치의 트래픽을 각 승인된 SaaS로 리디렉션합니다. 주요 기능으로는 사용자 트랜잭션의 전체 감사 추적, 사용자 행동 분석을 통한 악성코드 등 위협 분석, 실시간 트랜잭션 차단을 통한 데이터 유출 방지 기능 제공, 클라우드 장치 접근 제어를 위한 장치 및 사용자 검사, 고객 소유 키 서버를 사용한 저장 데이터 암호화 등이 있습니다.
            
        - **스카이 게이트웨이 이메일 모드 (Email Mode)**: 클라우드 기반 이메일 서비스의 메일 흐름을 활용하여 모든 사용자 및 모든 프로토콜에 대해 실시간으로 정책을 적용합니다. 이메일 서비스 제공업체(Office365/Gmail)는 Send Connector를 사용하여 이메일을 Skyhigh Security Cloud로 중계합니다. Skyhigh Security Cloud는 이메일을 처리하고 DLP 정책을 적용합니다. 정책 위반이 없으면 이메일은 Receive Connector를 사용하여 O365/Gmail로 다시 중계되고, 위반 시에는 정책에 명시된 조치(예: 격리 또는 차단)가 수행됩니다.
            
- **제어 지점 (Control Points)**
    - 클라우드로 들어오고 나가는 데이터 트래픽을 제어하는 방법을 결정합니다. Skyhigh Security Cloud는 API와 프록시(Proxy)라는 두 가지 광범위한 제어 지점을 제공합니다.
        
- **접근 지점 (Access Points)**
    - 클라우드의 데이터에 접근할 수 있는 다양한 방법을 의미합니다. 데이터를 안전하게 유지하려면 먼저 모든 접근 지점을 식별한 다음 보안해야 합니다. CASB가 고려하는 세 가지 접근 지점은 다음과 같습니다:
        
        - **사용자 (Users)**: 클라우드 애플리케이션에 접근하는 주체 (직원, 파트너, 공급업체, 고객).
            
        - **디바이스 (Devices)**: 클라우드 서비스에 로그인하는 데 사용되는 장치 (데스크톱, 노트북, 스마트폰).
            
        - **네트워크 (Network)**: 클라우드 애플리케이션에 연결하는 방식 (회사 네트워크, VPN, 홈 오피스 Wi-Fi, 공용 네트워크).
            

---

### 🛠️ 모듈 2 실습 및 복습

- **생각해보기**:
    - 우리 회사의 클라우드 사용 환경을 고려할 때, API 기반(대역 외) 배포와 프록시 기반(인라인) 배포 중 어떤 방식이 더 적합할까요? 그 이유는 무엇일까요?
    - 우리 회사 직원들이 클라우드 서비스에 접근하는 주요 접근 지점(사용자, 디바이스, 네트워크 유형)은 무엇이며, 각 지점별로 어떤 보안 위협이 존재할 수 있을까요?
- **용어 정리**:
    - DLP (Data Loss Prevention, 데이터 유출 방지)
    - BYOD (Bring Your Own Device, 개인 기기 사용)
    - API (Application Programming Interface)
    - 프록시 (Proxy) - 정방향(Forward) 및 역방향(Reverse)
    - 온프레미스 (On-premises)
    - LDAP (Lightweight Directory Access Protocol)
    - SIEM (Security Information and Event Management, 보안 정보 및 이벤트 관리)
    - PII (Personally Identifiable Information, 개인 식별 정보)
    - CSP (Cloud Service Provider, 클라우드 서비스 제공업체)
    - IDP (Identity Provider, ID 공급자)
    - 허영 도메인 (Vanity Domain)