---
title: Microsoft Intune에서 프라이빗 및 퍼블릭 키 인증서 사용 - Azure | Microsoft Docs
description: Microsoft Intune에서 루트 인증서를 내보내고, 인증서 템플릿을 구성하고, Intune Certificate Connector(NDES)를 다운로드 및 설치하고, 디바이스 구성 프로필을 만들고, Azure 및 인증 기관에서 PKCS(공개 키 암호 표준 ) 인증서 프로필을 만드는 단계를 포함하여 PKCS 인증서를 추가하거나 만듭니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/05/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1119a5681033574ec0a114442b122990da872bf
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66749805"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Intune을 사용하여 PKCS 인증서 구성 및 사용

Intune은 프라이빗 및 퍼블릭 키 쌍(PKCS) 인증서 사용을 지원합니다. 이 문서에서는 온-프레미스 인증서 커넥터 같은 필수 인프라를 구성하고 PKCS 인증서를 내보낸 다음, Intune 디바이스 구성 프로필에 인증서를 추가하는 방법을 안내합니다.

Microsoft Intune에는 조직 리소스에 대한 액세스 및 인증에 PKCS 인증서를 사용하는 기본 설정이 포함되어 있습니다. 인증서는 VPN 또는 WiFi 네트워크 같은 회사 리소스에 대한 액세스를 인증하고 보호합니다. 이러한 설정은 Intune의 디바이스 구성 프로필을 사용하여 디바이스에 배포됩니다.


## <a name="requirements"></a>요구 사항

Intune에서 PKCS 인증서를 사용하려면 다음 인프라가 필요합니다.

- **Active Directory 도메인**:  
  이 섹션에 나열된 모든 서버는 Active Directory 도메인에 조인되어 있어야 합니다.

  AD DS(Active Directory Domain Services) 설치 및 구성에 대한 자세한 내용은 [AD DS 디자인 및 계획](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)을 참조하세요.

- **인증 기관**:  
   엔터프라이즈 CA(인증 기관)

  AD CS(Active Directory 인증서 서비스) 설치 및 구성에 대한 자세한 내용은 [Active Directory 인증서 서비스 단계별 가이드](https://technet.microsoft.com/library/cc772393)를 참조하세요.

  > [!WARNING]  
  > Intune에서는 독립 실행형 CA가 아닌 엔터프라이즈 CA(인증 기관)를 사용하여 AD CS를 실행해야 합니다.

- **클라이언트**:  
  엔터프라이즈 CA에 연결하기 위한 클라이언트입니다.

- **루트 인증서**:  
  엔터프라이즈 CA에서 내보낸 루트 인증서 복사본입니다.

- **Intune Certificate Connector**(*NDES 인증서 커넥터*라고도 함):  
  Intune 포털에서 **디바이스 구성** > **인증서 커넥터** > **추가**로 이동하여 *PKCS용 커넥터 설치 단계 #12*를 따릅니다. 포털의 다운로드 링크를 사용하여 인증서 커넥터 설치 관리자 **NDESConnectorSetup.exe**의 다운로드를 시작합니다.  

  이 커넥터는 인증 또는 S/MIME 이메일 서명에 사용되는 PKCS 인증서 요청을 처리합니다.

  NDES 인증서 커넥터는 FIPS(Federal Information Processing Standard) 모드도 지원합니다. FIPS가 필수는 아니지만, 활성화되면 인증서를 발급하고 해지할 수 있습니다.

- **Microsoft Intune용 PFX 인증서 커넥터**:  
   S/MIME 이메일 암호화를 사용하려는 경우 Intune 포털을 사용하여 *PFX 인증서 가져오기*를 위한 커넥터를 다운로드합니다.  **디바이스 구성** > **인증서 커넥터** > **추가**로 이동하여 *가져온 PFX 인증서용 커넥터 설치 단계*를 따릅니다. 포털의 다운로드 링크를 사용하여 설치 관리자 **PfxCertificateConnectorBootstrapper.exe**의 다운로드를 시작합니다. 

  이 커넥터는 특정 사용자의 S/MIME 이메일 암호화를 위해 Intune으로 가져온 PFX 파일에 대한 요청을 처리합니다.  

  이 커넥터는 새 버전이 출시되면 자동으로 업데이트할 수 있습니다. 업데이트 기능을 사용하려면 다음 단계를 수행해야 합니다.
  - 가져온 PFX Certificate Connector for Microsoft Intune을 서버에 설치합니다.
  - 중요 업데이트를 자동으로 받으려면 커넥터가 포트 **443**을 통해 **autoupdate.msappproxy.net**에 연결할 수 있도록 방화벽을 열어야 합니다.  


- **Windows Server**:  
  Windows Server를 사용하여 다음 항목을 호스트합니다.

  - Microsoft Intune Certificate Connector - 인증 및 S/MIME 이메일 서명 시나리오에 사용됩니다.
  - PFX Certificate Connector for Microsoft Intune - S/MIME 이메일 암호화 시나리오에 사용됩니다.

  두 커넥터(*Microsoft Intune Certificate Connector* 및 *PFX Certificate Connector*)를 같은 서버에 설치할 수 있습니다.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>엔터프라이즈 CA에서 루트 인증서 내보내기

VPN, WiFi 또는 다른 리소스를 사용하여 디바이스를 인증하려면 디바이스에 루트 또는 중간 CA 인증서가 필요합니다. 다음 단계에서는 엔터프라이즈 CA에서 필요한 인증서를 가져오는 방법을 설명합니다.

**명령줄 사용**:  
1. 관리자 계정으로 루트 인증 기관 서버에 로그인합니다.
 
2. **시작** > **실행**으로 이동한 다음, **Cmd**를 입력하여 명령 프롬프트를 엽니다. 
    
3. **certutil  -ca.cert ca_name.cer**을 지정하여 *ca_name.cer*이라는 이름의 파일로 루트 인증서를 내보냅니다.



## <a name="configure-certificate-templates-on-the-ca"></a>CA에서 인증서 템플릿 구성

1. 관리 권한이 있는 계정으로 엔터프라이즈 CA에 로그인합니다.
2. **인증 기관** 콘솔을 열고 **인증서 템플릿**을 마우스 오른쪽 단추로 클릭하고 **관리**를 선택합니다.
3. **사용자** 인증서 템플릿을 찾아서 마우스 오른쪽 단추로 클릭하고 **템플릿 복제**를 선택합니다. **새 템플릿의 속성**이 열립니다.

    > [!NOTE]
    > S/MIME 이메일 서명 및 암호화 시나리오의 경우 많은 관리자가 서명 및 암호화를 위한 별도의 인증서를 사용합니다. Microsoft Active Directory 인증서 서비스를 사용하는 경우 S/MIME 이메일 서명 인증서의 **Exchange 서명 전용** 템플릿 및 S/MIME 암호화 인증서의 **Exchange 사용자** 템플릿을 사용할 수 있습니다.  타사 인증 기관을 사용하는 경우 해당 지침을 검토하여 서명 및 암호화 템플릿을 설정하는 것이 좋습니다.

4. **호환성** 탭에서 다음을 수행합니다.

    - **인증 기관**을 **Windows Server 2008 R2**로 설정
    - **인증서 받는 사람**을 **Windows 7/Server 2008 R2**로 설정

5. **일반** 탭에서 **템플릿 표시 이름**을 의미 있는 이름으로 설정합니다.

    > [!WARNING]
    > 기본적으로 **템플릿 이름**은 *공백 없이* **템플릿 표시 이름**과 동일합니다. 나중에 필요하므로 템플릿 이름을 참고합니다.

6. **요청 처리**에서 **프라이빗 키를 내보낼 수 있음**을 선택합니다.
7. **암호화**에서 **최소 키 크기**가 2048로 설정되었는지 확인합니다.
8. **주체 이름**에서 **요청에 따라 제공**을 선택합니다.
9. **확장**에서 **애플리케이션 정책** 아래에 파일 시스템 암호화, 메일 보안 및 클라이언트 인증이 표시되는지 확인합니다.

    > [!IMPORTANT]
    > iOS 인증서 템플릿의 경우 **확장** 탭으로 이동해서 **키 사용**을 업데이트한 다음 **서명이 원본 증명임**이 선택되지 않은 것을 확인합니다.

10. **보안**에서 Microsoft Intune Certificate Connector를 설치할 서버의 컴퓨터 계정을 추가합니다. 이 계정에 **읽기** 및 **등록** 권한을 허용합니다.
11. **적용** > **확인**을 선택하여 인증서 템플릿을 저장합니다. **인증서 템플릿 콘솔**을 닫습니다.
12. **인증 기관** 콘솔에서 **인증서 템플릿**을 마우스 오른쪽 단추로 클릭하고  >  **새로 만들기** > **발급할 인증서 템플릿**을 선택합니다. 이전 단계에서 만든 템플릿을 선택합니다. **확인**을 선택합니다.
13. 서버에서 등록된 디바이스 및 사용자에 대한 인증서를 관리하려면 다음 단계를 수행합니다.

    1. 인증 기관을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
    2. 보안 탭에서 커넥터(**Microsoft Intune Certificate Connector** 또는 **Microsoft Intune용 PFX 인증서 커넥터**)를 실행하는 서버의 컴퓨터 계정을 추가합니다. 
    3. **인증서 발급 및 관리** 및 **인증서 요청** 허용 권한을 컴퓨터 계정에 부여합니다.

14. 엔터프라이즈 CA에서 로그아웃합니다.

## <a name="download-install-and-configure-the-certificate-connectors"></a>인증서 커넥터 다운로드, 설치 및 구성

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune 인증서 커넥터

> [!IMPORTANT]  
> Microsoft Intune Certificate Connector는 발급 인증 기관(CA)에 설치할 수 없고, 별도의 Windows 서버에 설치해야 합니다.  

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **인증 커넥터** > **추가**를 선택합니다.
3. 커넥터를 설치할 서버에서 액세스할 수 있는 위치에 커넥터 파일을 다운로드하고 저장합니다.

    ![NDES 커넥터 다운로드](media/certificates-pfx-configure/download-ndes-connector.png)
 

4. 다운로드가 완료되면 서버에 로그인합니다. 그런 다음:

    1. NDES 인증서 커넥터에 필요하므로 .NET 4.5 Framework 이상이 설치되어 있는지 확인합니다. .NET 4.5 Framework는 Windows Server 2012 R2 및 최신 버전에 자동으로 포함됩니다.
    2. 설치 프로그램(NDESConnectorSetup.exe)을 실행하고 기본 위치를 적용합니다. 커넥터를 `\Program Files\Microsoft Intune\NDESConnectorUI`에 설치합니다. 설치 관리자 옵션에서 **PFX 배포**를 선택합니다. 계속하여 설치를 완료합니다.
    3. 기본적으로 커넥터 서비스는 로컬 시스템 계정으로 실행됩니다. 인터넷 액세스를 위해 프록시가 필요한 경우 로컬 서비스 계정이 서버의 프록시 설정에 액세스할 수 있는지 확인합니다.

5. NDES 커넥터가 **등록** 탭을 엽니다. Intune에 대한 연결을 사용하려면 **로그인**하고 전역 관리자 권한이 있는 계정을 입력합니다.
6. **고급** 탭에서 **이 컴퓨터의 시스템 계정 사용(기본값)** 을 선택한 상태로 두는 것이 좋습니다.
7. **적용** > **닫기**
8. Intune 포털로 돌아갑니다(**Intune** > **디바이스 구성** > **인증 커넥터**). 잠시 후에 녹색 확인 표시가 나타나고 **연결 상태**는 **활성**입니다. 커넥터 서버가 이제 Intune과 통신할 수 있습니다.
9. 네트워킹 환경에 웹 프록시가 있으면 커넥터가 작동할 수 있도록 추가 구성이 필요할 수 있습니다. 자세한 내용은 Azure Active Directory 설명서에서 [기존 온-프레미스 프록시 서버 작업](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-configure-connectors-with-proxy-servers)을 참조하세요.

> [!NOTE]  
> Microsoft Intune Certificate Connector는 TLS 1.2를 지원합니다. 커넥터를 호스트하는 서버에 TLS 1.2가 설치된 경우 해당 커넥터는 TLS 1.2를 사용합니다. 그렇지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 디바이스와 서버 간 인증에 사용됩니다.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>Microsoft Intune용 PFX 인증서 커넥터

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **인증 커넥터** > **추가**를 선택합니다.
3. Microsoft Intune용 PFX Certificate Connector을 다운로드하여 저장합니다. 커넥터를 설치하려는 서버에서 액세스할 수 있는 위치에 저장합니다.
4. 다운로드가 완료되면 서버에 로그인합니다. 그런 다음:

    1. Microsoft Intune용 PFX 인증서 커넥터에 필요하므로 .NET 4.6 Framework 이상이 설치되어 있는지 확인합니다. .NET 4.6 Framework가 설치되어 있지 않으면 설치 관리자가 자동으로 설치합니다.
    2. 설치 관리자(PfxCertificateConnectorBootstrapper.exe)를 실행하고 기본 위치를 적용합니다. 그러면 `Program Files\Microsoft Intune\PFXCertificateConnector`에 커넥터가 설치됩니다.
    3. 커넥터 서비스는 로컬 시스템 계정으로 실행됩니다. 인터넷 액세스를 위해 프록시가 필요한 경우 로컬 서비스 계정이 서버의 프록시 설정에 액세스할 수 있는지 확인합니다.

5. Microsoft Intune용 PFX 인증서 커넥터가 설치되면 **등록** 탭이 열립니다. Intune에 대한 연결을 사용하도록 설정하려면 **로그인**하고 Azure 글로벌 관리자 또는 Intune 관리자 권한이 있는 계정을 입력합니다.
6. 창을 닫습니다.
7. Azure Portal로 돌아갑니다(**Intune** > **디바이스 구성** > **인증 커넥터**). 잠시 후에 녹색 확인 표시가 나타나고 **연결 상태**는 **활성**입니다. 커넥터 서버가 이제 Intune과 통신할 수 있습니다.

## <a name="create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**로 이동합니다.
    ![Intune으로 이동하여 신뢰할 수 있는 인증서에 대한 새 프로필 만들기](media/certificates-pfx-configure/certificates-pfx-configure-profile-new.png)

2. 다음 속성을 입력합니다.

    - 프로필의 **이름**
    - 선택적으로 설명 설정
    - 프로필을 배포할 **플랫폼**
    - **프로필 형식**을 **신뢰할 수 있는 인증서**로 설정

3. **설정**으로 이동하여 이전에 내보낸 .cer 파일 루트 CA 인증서를 입력합니다.

   > [!NOTE]
   > **2단계**에서 선택한 플랫폼에 따라 인증서의 **대상 저장소**를 선택하는 옵션이 제공되거나 제공되지 않을 수 있습니다.

   ![프로필을 만들고 신뢰할 수 있는 인증서 업로드](media/certificates-pfx-configure/certificates-pfx-configure-profile-fill.png) 

4. **확인** > **만들기**를 선택하여 프로필을 저장합니다.
5. 하나 이상의 디바이스에 새 프로필을 할당하려면 [Microsoft Intune 디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 인증서 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**로 이동합니다.
2. 다음 속성을 입력합니다.

    - 프로필의 **이름**
    - 선택적으로 설명 설정
    - 프로필을 배포할 **플랫폼**
    - **프로필 형식**을 **PKCS 인증서**로 설정

3. **설정**으로 이동해 다음 속성을 입력합니다.

    - **갱신 임계값(%)** : 추천되는 값은 20%입니다.
    - **인증서 유효 기간**: 인증서 템플릿을 변경하지 않은 경우 이 옵션은 1년으로 설정할 수 있습니다.
    - **KSP(키 스토리지 공급자)** : Windows의 경우 디바이스에서 키를 저장할 위치를 선택합니다.
    - **인증 기관**: 엔터프라이즈 CA의 내부 FQDN(정규화된 도메인 이름)을 표시합니다.
    - **인증 기관 이름**: "Contoso 인증 기관"과 같은 엔터프라이즈 CA의 이름을 나열합니다.
    - **인증서 템플릿 이름**: 이전에 만든 템플릿의 이름입니다. 기본적으로 **템플릿 이름**은 *공백 없이* **템플릿 표시 이름**과 동일합니다.
    - **주체 이름 형식**: 달리 필요하지 않은 경우 이 옵션을 **일반 이름**으로 설정합니다.
    - **주체 대체 이름**: 달리 필요하지 않은 경우 이 옵션을 **UPN(사용자 계정 이름)** 으로 설정합니다.

4. **확인** > **만들기**를 선택하여 프로필을 저장합니다.
5. 하나 이상의 디바이스에 새 프로필을 할당하려면 [Microsoft Intune 디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="create-a-pkcs-imported-certificate-profile"></a>PKCS가 가져온 인증서 프로필 만들기

이전에 특정 사용자에게 발급된 인증서는 모든 CA에서 Intune으로 가져올 수 있습니다. 가져온 인증서는 사용자가 등록하는 각 디바이스에 설치됩니다. S/MIME 이메일 암호화는 기존 PFX 인증서를 Intune에 가져오는 가장 일반적인 시나리오입니다. 사용자는 이메일을 암호화하기 위한 많은 인증서를 가지고 있을 수 있습니다. 이러한 인증서의 프라이빗 키는 이전에 암호화된 이메일을 해독할 수 있도록 모든 사용자의 디바이스에 있어야 합니다.

인증서를 Intune에 가져오려면 [GitHub에서 제공하는 PowerShell cmdlet](https://github.com/Microsoft/Intune-Resource-Access)을 사용하면 됩니다.

Intune으로 인증서를 가져온 후 **PKCS가 가져온 인증서** 프로필을 생성하여 Azure Active Directory 그룹에 할당합니다.

1. [Azure Portal](https://portal.azure.com)에서 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**로 이동합니다.
2. 다음 속성을 입력합니다.

    - 프로필의 **이름**
    - 선택적으로 설명 설정
    - 프로필을 배포할 **플랫폼**
    - **프로필 형식**을 **PKCS가 가져온 인증서**로 설정

3. **설정**으로 이동해 다음 속성을 입력합니다.

    - **용도**: 이 프로필에 대해 가져온 인증서의 용도입니다. 관리자는 다양한 용도(예: 인증, S/MIME 서명 또는 S/MIME 암호화)로 인증서를 가져올 수 있습니다. 인증서 프로필에서 선택한 용도는 인증서 프로필과 가져온 인증서를 올바르게 일치시킵니다.
    - **인증서 유효 기간**: 인증서 템플릿을 변경하지 않은 경우 이 옵션은 1년으로 설정할 수 있습니다.
    - **KSP(키 스토리지 공급자)** : Windows의 경우 디바이스에서 키를 저장할 위치를 선택합니다.

4. **확인** > **만들기**를 선택하여 프로필을 저장합니다.
5. 하나 이상의 디바이스에 새 프로필을 할당하려면 [Microsoft Intune 디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="whats-new-for-connectors"></a>커넥터의 새로운 기능
두 인증서 커넥터의 업데이트가 정기적으로 릴리스됩니다. 커넥터를 업데이트할 때 여기서 변경 내용을 읽을 수 있습니다. 

*Microsoft Intune용 PFX 인증서 커넥터*는 [자동 업데이트를 지원](#requirements)하는 반면, *Intune 인증서 커넥터*는 수동으로 업데이트해야 합니다.

### <a name="may-17-2019"></a>2019년 5월 17일  
- **Microsoft Intune용 PFX 인증서 커넥터 - 버전 6.1905.0.404**  
  이 릴리스의 변경 내용:  
  - 커넥터가 새 요청 처리를 중지하게 하는 기존 PFX 인증서가 계속 재처리되는 문제가 해결되었습니다. 

### <a name="may-6-2019"></a>2019년 5월 6일  
- **Microsoft Intune용 PFX 인증서 커넥터 - 버전 6.1905.0.402**  
  이 릴리스의 변경 내용:  
  - 커넥터에 대한 폴링 간격을 5분에서 30초로 줄입니다.
 
### <a name="april-2-2019"></a>2019년 4월 2일  
- **Intune 인증서 커넥터 - 버전 6.1904.1.0**  
  이 릴리스의 변경 내용:  
  - 글로벌 관리자 계정으로 커넥터에 로그인한 후 커넥터가 Intune에 등록하지 못하는 문제가 해결되었습니다.  
  - 인증서 해지의 안정성 픽스가 포함되어 있습니다.  
  - PKCS 인증서 요청 처리 속도를 높이기 위한 성능 픽스가 포함되어 있습니다.  

- **Microsoft Intune용 PFX 인증서 커넥터 - 버전 6.1904.0.401**
  > [!NOTE]  
  > 이 PFX 커넥터 버전의 자동 업데이트는 2019년 4월 11일까지 사용할 수 없습니다.  

  이 릴리스의 변경 내용:  
  - 글로벌 관리자 계정으로 커넥터에 로그인한 후 커넥터가 Intune에 등록하지 못하는 문제가 해결되었습니다.  


## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[SCEP 인증서를 사용](certificates-scep-configure.md)하거나 [Symantec PKI 관리자 웹 서비스에서 PKCS 인증서를 발급](certificates-symantec-configure.md)합니다.

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Azure Portal에서 Intune으로 이동하여 신뢰할 수 있는 인증서에 대한 새 프로필을 만듭니다."
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "프로필을 만들고 신뢰할 수 있는 인증서를 업로드합니다."
[ConnectorDownload]: ./media/certificates-download-connector.png "Azure Portal에서 인증서 커넥터 다운로드"  
