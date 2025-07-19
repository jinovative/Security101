### 📚 모듈 5: Skyhigh Security Cloud 사용 사례 및 실제 적용

이 모듈에서는 SaaS, IaaS, Shadow IT, 이메일 보안 등 다양한 영역에서 Skyhigh Security Cloud를 활용하는 구체적인 시나리오와 실습 예제를 다룹니다.

---

#### **강의 5.1: SaaS (Software as a Service) 애플리케이션 보안 사용 사례**

- **승인된 SaaS (Sanctioned SaaS) 사용 사례**
    - **중요 데이터 통제 (Confidential Data Control)**: 규제 대상 데이터가 클라우드에 저장되는 것을 방지합니다.
        
        - 키워드, 데이터 식별자, 사전, 정규식 등을 기반으로 DLP(데이터 유출 방지) 정책을 시행합니다.
            
        - 차단, 격리, 삭제, 사용자 교육, 알림 등 다양한 자동화된 remediation(개선 조치) 작업을 시행합니다.
            
        - 사용자 이름과 파일 이름을 포함하여 위반 사항의 전체 내용을 보여주는 강조된 발췌문을 검토합니다.
            
        - 자동화된 시행 조치를 롤백하거나 수동 조치를 취할 수 있습니다.
            
    - **협업 통제 (Collaboration Control - Realtime Data Guard)**: 승인되지 않은/민감한 데이터가 외부로 공유되는 것을 방지합니다.
        - API를 통한 실시간 공유 정책 시행으로 정보 노출을 방지합니다.
            
        - 사용자 교육, 링크 차단, 공유 제한, 관리자 알림 등의 조치를 취합니다.
            
        - 공유 및 협업 활동에 대한 시각적 요약을 제공합니다.
            
    - **상황별 접근 통제 (Contextual Access Control)**: 관리되는/관리되지 않는 디바이스에 대한 접근을 규제합니다.
        
        - 디바이스 인증서를 확인하여 적절한 엔드포인트 보안을 갖추고 있는지, 사용자-디바이스 매핑이 유효한지 검증합니다.
        - 관리되는 디바이스와 관리되지 않는 디바이스에 대해 별도의 정책을 시행합니다.
            
        - 관리되지 않는 디바이스에서 네이티브 앱을 포함한 Office 365 접근을 차단합니다.
            
        - 브라우저에서 콘텐츠 미리보기는 허용하되 다운로드는 비활성화할 수 있습니다.
            
    - **고급 위협 통제 (Advanced Threat Control)**: 계정 탈취, 내부자 위협, 권한 있는 사용자 위협을 탐지합니다.
        
        - 머신러닝 및 UEBA(User and Entity Behavior Analytics, 사용자 및 엔티티 행동 분석)를 활용합니다.
            
        - 위협 깔때기(Threat funnel)는 여러 이상 징후를 연관 분석하여 오탐(false positives)을 최소화합니다.
            
        - 사전 정의된 정책이나 임계값 없이 활동 기반의 자동 모델을 사용합니다.
            
    - **활동 모니터링 및 포렌식 (Activity Monitoring and Forensics)**: 모든 사용자 활동에 대한 감사 추적(audit trail)을 제공합니다.
        
        - 600개 이상의 모든 활동을 13개 카테고리로 분류하여 쉽게 필터링/탐색할 수 있습니다.
            
        - 조사 범위를 확장하고 지리적 위치 맵을 탐색할 수 있습니다.
            
        - 특정 사용자의 인시던트 중심 활동을 조사할 수 있습니다.
            
        - IP 평판을 사용하여 TOR 네트워크와 같은 악성 IP의 접근을 식별합니다.
            
- **SaaS를 위한 구성 감사 (Configuration Audit for SaaS - SSPM)**
    - SaaS 보안 상태 관리(SSPM - SaaS Security Posture Management) 솔루션의 일부로, 기업 SaaS 서비스의 잠재적인 잘못된 구성을 파악하고 이를 개선할 수 있도록 가시성을 제공합니다.
        
    - 현재 Microsoft 365 앱(SharePoint Online, OneDrive, Azure Active Directory, Intune, Teams) 및 Salesforce에 대한 정책을 지원합니다.
        

---

#### **강의 5.2: IaaS (Infrastructure as a Service) 플랫폼 보안 사용 사례**

IaaS 환경은 유연성을 제공하지만, 데이터, 사용자 접근, 애플리케이션, 운영 체제, 가상 네트워크 트래픽 보안에 대한 책임은 고객에게 있습니다. Skyhigh Security는 IaaS 보안을 위해 CASB, CWPP, VNSP, CSPM과 같은 솔루션을 제공합니다.

- **IaaS 보안 구성 모니터링 (Security Configuration Monitoring of IaaS Resources)**: 내부 정책 또는 보안 모범 사례를 준수하지 않는 잘못 구성된 IaaS 리소스(예: 공개적으로 읽기/쓰기가 가능한 S3 버킷)를 식별합니다.
    
    - IaaS 보안 설정의 잘못된 구성을 지속적으로 모니터링합니다.
        
    - IaaS 관리자가 잘못 구성된 설정을 수정하면 Skyhigh Security Cloud가 자동으로 인시던트를 해결합니다.
        
- **컨테이너 보안 (Container Security)**
    - Skyhigh Security Container Security는 통합 클라우드 보안 플랫폼의 일부로 AWS, GCP와 같은 주요 IaaS 제공업체를 위한 CSPM(Cloud Security Posture Management)을 제공합니다. 이는 동적 컨테이너 워크로드와 이들이 의존하는 인프라를 보호하도록 확장 및 강화되었습니다.
        
    - CIS 레벨 1 및 2 벤치마크 요구 사항을 지속적으로 확인하여 워크로드 및 컨테이너의 잘못된 구성이나 변경 사항을 탐지하고 수정합니다.
        
    - 현재 Azure Kubernetes Service (AKS), Azure Container Registry (ACR), Amazon Elastic Kubernetes Service (EKS), Amazon Elastic Container Service (ECS), Amazon Elastic Container Registry (ECR)를 지원하며 약 200개의 사전 구성된 정책 템플릿을 제공합니다.
        
    - CVS(Container Vulnerability Scan, 컨테이너 취약점 스캔)를 실행하여 취약한 코드가 프로덕션 환경에 도달하는 것을 방지합니다. CVS는 CSP 레지스트리의 이미지를 스캔하여 알려진 취약점 목록과 대조하고, 취약점이 발견된 각 이미지에 대해 인시던트를 생성합니다.
        
- **비인가 IaaS 인스턴스 발견 (Rogue IaaS Instances)**: 섀도우 IT 사용을 발견하고 위험한 IaaS 사용에 대한 통제권을 회복하도록 지원합니다.
    
    - 위험하거나 승인되지 않은 사용 중인 IaaS 플랫폼을 식별합니다.
        
    - 거버넌스 정책을 시행하고 사용자를 승인된 IaaS 플랫폼으로 유도합니다.
        
- **중요 데이터 유출 통제 (Control Confidential Data Leaks)**: 규제 대상/고가치 데이터가 IaaS 스토리지 서비스(예: Azure, AWS, GCP에 고객 신용카드 번호 저장)에 저장되는 것을 방지합니다.
    
    - 온디맨드 스캔을 수행하여 IaaS 스토리지 서비스에 저장된 민감하거나 보호되는 데이터를 식별합니다.
        
- **고급 위협 보호 (Advanced Threat Protection)**: 계정 탈취, 내부자/권한 있는 사용자 위협 및 악성코드(예: 공격자가 피싱된 암호를 사용하여 AWS 콘솔에 무단 접근)를 탐지합니다.
    
    - 위협 깔때기는 여러 이상 징후를 연관 분석하여 오탐을 최소화합니다.
        
- **활동 모니터링 및 포렌식 (Activity Monitoring and Forensics)**: 포렌식 조사를 위한 활동 감사 추적을 캡처하고 분류합니다(예: AWS 관리자가 CloudTrail 로그 삭제).
    
    - 다양한 활동을 13개 카테고리로 분류하여 쉽게 필터링/탐색할 수 있습니다.
        

---

#### **강의 5.3: 섀도우 IT (Shadow IT) 관리 사용 사례**

- **탐지 (Discovery)**: 사용 중인 모든 클라우드 서비스, 접근 횟수, 보안 위험, 시간 경과에 따른 사용 추세를 파악합니다(예: IT 부서 모르게 직원들이 클라우드 서비스 도입).
    
    - 클라우드 탐지 및 CloudTrust 레지스트리는 사용 중인 모든 클라우드 서비스에 대한 가시성을 제공합니다. 약 30,000개 이상의 클라우드 서비스에 대한 상세 보안 평가가 가능합니다.
        
- **클라우드 서비스 거버넌스 (Cloud Service Governance)**: 서비스 그룹을 사용하여 클라우드 서비스 보안 위험에 기반한 허용 가능한 클라우드 사용 거버넌스 정책을 시행합니다(예: 직원이 엑셀-PDF 변환기를 사용하여 회사 IP 유출 위험 발생).
    
    - 조직에서 사용하는 모든 클라우드 서비스에 대한 위험 점수를 제공합니다.
        
    - 위험 점수에 따라 서비스를 함께 묶는 서비스 그룹을 만듭니다.
        
    - 서비스 그룹에 기반한 클라우드 거버넌스 정책을 시행합니다.
        
- **클라우드 서비스 보안 평가 (Cloud Service Security Assessment)**: 보안 평가 프로세스를 가속화하여 클라우드 서비스 승인 요청 워크플로우를 신속하게 처리합니다(예: 직원이 IT에 새 클라우드 서비스를 요청할 때 서비스 평가 및 회신에 며칠 소요).
    
    - 약 30,000개 이상의 클라우드 서비스에 대한 위험 평가가 가능합니다.
        
    - 데이터, 법률, 사이버, 사용자/디바이스, 서비스, 비즈니스 및 인공 지능과 같은 위험 속성에 대해 요청된 클라우드 서비스를 평가합니다.
        
    - 조직의 위험 선호도에 따라 위험 평가를 사용자 지정합니다.
        
- **클라우드 적용 격차 분석 (Cloud Enforcement Gap Analysis)**: 프록시 누수로 인해 발생하는 정책 적용 격차를 탐지하고 개선합니다(예: 기존 프록시/방화벽 정책이 사용 중인 클라우드 서비스를 인지하지 못함).
    
    - 서비스 그룹을 사용하여 서비스를 승인됨, 허용됨, 거부됨으로 분류합니다.
        
    - CLR(Cloud Loop Remediation)을 사용하여 서비스 그룹을 프록시, 방화벽 및 웹 게이트웨이로 푸시합니다.
        
    - 업데이트된 URL 매핑 및 서비스 카테고리를 사용하여 프록시/방화벽/웹 게이트웨이에 거버넌스 정책을 만듭니다.
        
- **아웃바운드 데이터 인텔리전스 (Outbound Data Intelligence)**: 신뢰할 수 없는 대상으로의 업로드를 식별하고 악성 도메인 및 IP 주소를 플래그 지정합니다.
    
    - 섀도우 클라우드 서비스에 대한 모든 활동을 모니터링합니다.
        
    - Skyhigh Security Cloud의 데이터 인텔리전스 피드를 사용하여 알려진 악성 도메인 및 IP 주소로의 트래픽을 식별하고 경고합니다.
        

---

#### **강의 5.4: 이메일 보호 (Email Protection) 사용 사례**

Skyhigh Security Cloud Email DLP(Data Loss Prevention)를 사용하면 Exchange Online 또는 G Suite Gmail(Enterprise 라이선스)에 DLP 정책을 적용할 수 있습니다. 이는 고객의 클라우드 생성 이메일을 수동적 또는 능동적으로 검사하기 위한 클라우드 기반 SMTP(Simple Mail Transfer Protocol) 게이트웨이입니다.

- **작동 방식**:
    - **수동 모드 (Passive Mode)**: 아카이빙 기능(Exchange Online의 저널링, Gmail의 타사 이메일 아카이빙)을 사용합니다. 원본 이메일 흐름에 영향을 주지 않고 사본을 받아 DLP 검사를 수행하므로 지연이 발생하지 않습니다.
        
    - **능동(인라인) 모드 (Active (Inline) Mode)**: SMTP 커넥터와 메일 흐름 규칙을 사용합니다. 메일 서버는 Sky Gateway를 통해 메시지를 보내도록 구성되어 콘텐츠를 검사합니다. Sky Gateway는 SMTP 프록시 역할을 하며 메시지를 저장하거나 대기열에 넣지 않고 실시간으로 처리합니다. 최대 1분의 지연이 발생할 수 있지만, 외부 발신 메일에만 적용하면 사용자 경험에 미치는 영향은 미미합니다. 내부 메일 검사가 필요한 경우, 별도의 수동 모드 커넥터를 설정하거나 Exchange Online 사서함에 대한 온디맨드 스캔을 수행하는 것이 좋습니다.
        
- **이메일 DLP를 위한 전제 조건**:
    - Office 365 계정의 전역 관리자 역할.
        
    - 조직의 모든 이메일 도메인 목록.
        
    - 사전 구성된 격리 이메일 사서함.
        
    - 사전 구성된 보조 이메일 주소(배달 불가능한 저널 메시지용).
        
    - 테스트를 위한 Office 365의 사전 구성된 그룹.
        
    - G Suite Enterprise 계정 및 관리자 계정.
        
- **알려진 동작 (Known Behaviors)**:
    - 이메일 DLP의 파일 이름 규칙은 첨부 파일을 탐지하지 않고, 제목 줄 기반의 EML 파일 이름을 스캔합니다.
        
    - 토큰화된 사용자는 이메일 DLP에서 지원되지 않습니다.
        
- **이메일 DLP의 분류 위치 (Classification Location)**: 이메일 제목, 헤더, 본문, 첨부 파일 또는 서비스 기본값(헤더 제외 모든 콘텐츠) 등 이메일의 특정 부분에 분류 규칙을 적용할 수 있습니다.
    
- **🛠️ 실습 예제 1: 파일 크기 기반 DLP 정책 생성**
    - **목표**: SharePoint에서 3MB를 초과하는 모든 파일을 탐지하고 인시던트를 생성하는 DLP 정책을 만듭니다.
        
    - **주요 설정**:
        - 분류: Skyhigh Security Cloud Classification
            
        - 배포 유형: API
            
        - 서비스: SharePoint (또는 예시에서는 Microsoft Exchange Online: Default service 사용)
            
        - 규칙: 파일 크기 > 3MB
        - 대응: 인시던트 생성
    - (문서에서는 신용카드 번호 감지 예시를 들었으나, 파일 크기 조건으로 변형하여 적용 가능합니다.)
        
- **🛠️ 실습 예제 2: SSN 포함 이메일 격리 정책 생성**
    - **목표**: 조직에서 발신되는 이메일 중 미국 사회 보장 번호(SSN)를 포함하는 모든 이메일을 격리하는 DLP 정책을 만듭니다.
        
    - **주요 설정**:
        - 규칙: 데이터 식별자 = 북미 개인 신원 - 미국 사회 보장 번호 (North American Personal Identity - U.S. Social Security Number).
            
        - 대응: 격리(Quarantine).
            
- **🛠️ 실습 예제 3: Box 기밀 문서 협업 제한 정책 생성**
    - **목표**: Box 분류에서 "기밀(confidential)"로 분류된 문서의 모든 협업 시도를 제한하는 DLP 정책을 만듭니다.
        
    - **주요 설정**:
        - 규칙: 분류: Box, 이름: 기밀(Confidential), 협업: 모든 사용자로부터의 공유, 모든 사용자에게 공유, 모든 공유 권한.
            
        - 대응: (예시에서는 심각도 높음 시 격리) 협업 제한 조치 (예: 공유 링크 해지).
            

---

#### **강의 5.5: 역방향 프록시 (Reverse Proxy) 구성 사용 사례 (예: Azure AD를 통한 Office 365)**

역방향 프록시는 관리되지 않는 디바이스에서 승인된 애플리케이션의 접근을 제한하는 방법입니다. 일반적으로 관리되지 않는 디바이스가 SAML(Security Assertion Markup Language) 인증 프로세스를 통과하도록 허용합니다. 결과적으로 관리되거나 관리되지 않는 모든 디바이스의 승인된 애플리케이션이 Skyhigh Security Cloud 프록시로 리디렉션됩니다.

- **작동 방식 (Azure AD 조건부 접근 연동)**:
    - Azure AD 조건부 접근은 사용자가 WGCS(Web Gateway Cloud Service) IP 또는 Skyhigh Security Cloud 역방향 프록시 IP를 통해서만 Office 365에 로그인할 때 접근을 허용합니다.
        
    - 이러한 게이트웨이를 통하지 않고 Office 365에 직접 로그인하면 IP 주소가 Azure AD 조건부 접근에 의해 차단됩니다.
        
    - 관리형 디바이스의 경우, 조건부 접근 정책은 로그인 프로세스에만 적용되며, Office 365 네트워크 트래픽(office.com 등)을 WGCS를 통해 보낼 필요는 없습니다.
        
- **전제 조건**:
    - Azure AD로 인증되는 Office 365 테넌트 (라이선스 필요).
        
    - Azure AD 포털에 대한 관리자 접근 권한.
        
    - WGCS 또는 Skyhigh Security Service Edge (SSE)가 활성화된 Skyhigh Security Cloud 테넌트에 대한 접근 권한.
        
    - 클라이언트 프록시가 설치 및 구성되어 WGCS 또는 SSE를 통해 네트워크 트래픽을 전달하는 관리형 또는 비관리형 디바이스.
        
    - WGCS 또는 SSE를 통해 네트워크 트래픽을 보내지 않는 비관리형 디바이스.
        
- **구성 절차 개요**:
    1. Skyhigh Security Cloud에서 역방향 프록시 설정 (서비스 관리 > Microsoft Office 365 및 OneDrive 인스턴스 > 프록시 구성).
        
    2. Azure AD 포털에서 조건부 접근 정책 구성.
    3. Skyhigh Security Cloud에서 클라우드 접근 정책 구성.
    4. Azure AD를 통한 Office 365 역방향 프록시 유효성 검사.
- **🛠️ 실습: 역방향 프록시를 사용하는 클라우드 접근 정책 생성**
    1. Skyhigh Security Cloud에 로그인하고 인증서를 통해 디바이스 관리를 구성합니다.
        
    2. **정책 (Policy) > 접근 제어 (Access Control) > 접근 정책 (Access Policies)**으로 이동하여 '정책 만들기(Create Policy)'를 클릭합니다.
        
    3. **관리형 디바이스 직접 접근 허용 정책 생성**:
        - 조건: 서비스 IS Microsoft Office 365 and OneDrive, 에이전트(Agent) IS SCP (Skyhigh Client Proxy).
            
        - 조치: 인증서 확인 건너뛰기: 모두 리디렉션(Skip Cert Check: Redirect All).
            
    4. **비관리형 디바이스 트래픽 프록시 정책 생성**:
        - 조건: 서비스 IS Microsoft Office 365 and OneDrive.
            
        - 조치: 인증서 확인: 모두 프록시(Check Cert: Proxy All).
            
    5. 생성된 정책들이 올바른 순서로 (관리형 디바이스 정책이 위로) 배치되었는지 확인합니다.
        

---

### 🛠️ 모듈 5 실습 및 복습

- **시나리오 분석**:
    - 우리 회사에서 가장 우려되는 SaaS 애플리케이션 보안 위협은 무엇이며, 강의 내용 중 어떤 Skyhigh Security Cloud 기능/사용 사례를 적용하여 해결할 수 있을지 토론해보세요. (예: 특정 SaaS 앱에서의 과도한 외부 공유 문제 -> 협업 통제 정책 적용)
    - 현재 회사에서 IaaS를 사용하고 있다면, 어떤 종류의 데이터가 저장되어 있으며, 어떤 구성 오류가 발생할 가능성이 있을지 생각해보세요. Skyhigh Security Cloud의 IaaS 보안 기능을 어떻게 활용할 수 있을까요?
    - 직원들이 사용하는 섀도우 IT 서비스 중 가장 위험하다고 생각되는 서비스는 무엇이며, 그 이유는 무엇인가요? Skyhigh Security Cloud를 통해 어떻게 관리할 수 있을지 논의해보세요.
- **정책 아이디어 구상**:
    - 우리 회사에 필요한 이메일 DLP 정책 시나리오를 추가로 1~2가지 더 만들어보고, 필요한 규칙과 대응 조치를 간단히 정의해보세요.
- **용어 정리**:
    - SSPM (SaaS Security Posture Management) - SaaS 보안 상태 관리
    - CWPP (Cloud Workload Protection Platform) - 클라우드 워크로드 보호 플랫폼
    - CSPM (Cloud Security Posture Management) - 클라우드 보안 상태 관리
    - UEBA (User and Entity Behavior Analytics) - 사용자 및 엔티티 행동 분석
    - CLR (Cloud Loop Remediation) - 폐쇄 루프 개선
    - SMTP (Simple Mail Transfer Protocol) - 단순 메일 전송 프로토콜
    - EML (Email Message Format) - 이메일 메시지 형식
    - WGCS (Web Gateway Cloud Service) - 웹 게이트웨이 클라우드 서비스
    - SSE (Security Service Edge) - 보안 서비스 엣지
    - SCP (Skyhigh Client Proxy)