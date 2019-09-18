---
title: Microsoft Intune으로 SCEP 인증서 프로필을 지원하도록 인프라 구성 - Azure | Microsoft Docs
description: Microsoft Intune에서 SCEP를 사용하려면 온-프레미스 AD 도메인을 구성하고 인증 기관을 만들고 NDES 서버를 설정하고 Intune Certificate Connector를 설치합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/28/2019
ms.topic: article
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 909dba16e04b11989caa79112c5a89fbb7c52114
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061388"
---
# <a name="configure-infrastructure-to-support-scep-with-intune"></a>Intune을 사용하여 SCEP를 지원하도록 인프라 구성  
  
Intune에서는 SCEP(단순 인증서 등록 프로토콜)를 사용하여 [앱 및 회사 리소스에 대한 연결을 인증](certificates-configure.md)하도록 지원합니다. SCEP는 CA(인증 기관) 인증서를 사용하여 CSR(인증서 서명 요청)에 대한 메시지 교환을 보호합니다. 인프라가 SCEP를 지원하는 경우 intune *SCEP 인증서* 프로필(Intune의 디바이스 프로필 유형)을 사용하여 인증서를 디바이스에 배포할 수 있습니다. Microsoft Intune Certificate Connector는 Active Directory 인증서 서비스 인증 기관을 사용할 때 Intune에서 SCEP 인증서 프로필을 사용하는 데 필요합니다. [타사 인증 기관](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration)을 사용하는 경우에는 이 커넥터가 필요하지 않습니다.  

이 문서의 정보는 Active Directory 인증서 서비스를 사용하는 경우 SCEP를 지원하도록 인프라를 구성하는 데 유용할 수 있습니다. 인프라를 구성한 후에는 Intune에서 [SCEP 인증서 프로필을 만들고 배포](certificates-profile-scep.md)할 수 있습니다.  

> [!TIP]  
> 또한 Intune은 [퍼블릭 키 암호화 표준 #12 인증서](certficates-pfx-configure.md)를 사용하도록 지원합니다.  


## <a name="prerequisites-for-using-scep-for-certificates"></a>인증서에 SCEP를 사용하기 위한 필수 선행 작업  
계속하기 전에 [신뢰할 수 있는 인증서 프로필을 만든 후 SCEP 인증서 프로필을 사용할 디바이스에 배포](certificates-configure.md#export-the-trusted-root-ca-certificate)했는지 확인합니다.  SCEP 인증서 프로필은 신뢰할 수 있는 루트 CA 인증서로 디바이스를 프로비저닝하는 데 사용하는 신뢰할 수 있는 인증서 프로필을 직접 참조합니다.  

### <a name="servers-and-server-roles"></a>서버 및 서버 역할  
다음 온-프레미스 인프라는 웹 애플리케이션 프록시 서버를 제외하고 Active Directory 도메인에 가입된 서버에서 실행해야 합니다.  
- **인증 기관** - Enterprise 버전의 Windows Server 2008 R2 서비스 팩 1 이상에서 실행되는 Microsoft Active Directory 인증서 서비스 엔터프라이즈 CA(인증 기관)를 사용합니다. 사용하는 Windows Server 버전은 Microsoft에서 계속 지원해야 합니다. 독립 실행형 CA는 지원되지 않습니다. 자세한 내용은 [인증 기관 설치](http://technet.microsoft.com/library/jj125375.aspx)를 참조하세요. CA에서 Windows Server 2008 R2 SP1을 실행하는 경우에는 [KB2483564의 핫픽스를 설치](http://support.microsoft.com/kb/2483564/)해야 합니다.  

- **NDES 서버 역할** – Windows server 2012 R2 이상에서 NDES(네트워크 디바이스 등록 서비스) 서버 역할을 구성해야 합니다. 이 문서의 이후 섹션에서는 [NDES 설치](#set-up-ndes) 과정을 안내합니다.  

  - NDES를 호스트하는 서버는 도메인에 가입되어 있어야 하고 엔터프라이즈 CA와 동일한 포리스트에 있어야 합니다.  
  - 엔터프라이즈 CA를 호스트하는 서버에 설치된 NDES는 사용할 수 없습니다.  
  - NDES를 호스트하는 동일한 서버에 Microsoft Intune Certificate connector를 설치합니다.  

  NDES에 대한 자세한 내용은 Windows Server 설명서의 [네트워크 디바이스 등록 서비스 지침](http://technet.microsoft.com/library/hh831498.aspx) 및 [네트워크 디바이스 등록 서비스와 함께 정책 모듈 사용](https://technet.microsoft.com/library/dn473016.aspx)을 참조하세요.  

- **Microsoft Intune Certificate Connector** – Microsoft Intune Certificate Connector는 Intune에서 SCEP 인증서 프로필을 사용하는 데 필요합니다. 이 문서에서는 [이 커넥터의 설치 과정](#install-the-intune-certificate-connector)을 안내합니다.  

  이 커넥터는 FIPS(Federal Information Processing Standard) 모드를 지원합니다. FIPS가 필수는 아니지만, 사용하도록 설정하면 인증서를 발급하고 해지할 수 있습니다.  
  - 커넥터는 Windows Server 2012 R2 이상을 실행하는 서버인 NDES 서버 역할과 동일한 서버에서 실행해야 합니다.  
  - .NET 4.5 Framework는 커넥터에 필요하며 Windows Server 2012 R2에 자동으로 포함됩니다.  
  - Internet Explorer 보안 강화 구성은 [NDES 및 Microsoft Intune Certificate Connector를 호스트하는 서버에서 사용하지 않도록 설정해야 합니다](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx).  

다음 온-프레미스 인프라는 선택 사항입니다.  
  인터넷의 디바이스에서 인증서를 가져올 수 있도록 하려면 NDES URL을 회사 네트워크 외부에 게시해야 합니다. Azure AD 애플리케이션 프록시, 웹 애플리케이션 프록시 서버 또는 다른 역방향 프록시를 사용할 수 있습니다.
  
- **Azure AD 애플리케이션 프록시**(선택 사항) - 전용 WAP(웹 애플리케이션 프록시) 서버 대신, Azure AD 애플리케이션 프록시를 사용하여 NDES URL을 인터넷에 게시할 수 있습니다. 그러면 인트라넷 및 인터넷 연결 디바이스 모두에서 인증서를 가져올 수 있습니다. 자세한 내용은 온 [온-프레미스 애플리케이션에 보안된 원격 액세스를 제공하는 방법](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)을 참조하세요. 

- **웹 애플리케이션 프록시 서버**(선택 사항) - Windows Server 2012 R2 이상을 WAP(웹 애플리케이션 프록시) 서버로 실행하는 서버를 사용하여 NDES URL을 인터넷에 게시합니다.  그러면 인트라넷 및 인터넷 연결 디바이스 모두에서 인증서를 가져올 수 있습니다.

  WAP를 호스팅하는 서버에는 네트워크 디바이스 등록 서비스에서 사용하는 긴 URL을 지원할 수 있도록 하는 [업데이트를 설치](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) 해야 합니다. 이 업데이트는 [2014년 12월 업데이트 롤업](http://support.microsoft.com/kb/3013769)에 포함되어 있으며, [KB3011135](http://support.microsoft.com/kb/3011135)에서 개별적으로 다운로드할 수도 있습니다.  

  WAP 서버에는 외부 클라이언트에 게시된 이름과 일치하는 SSL 인증서가 있어야 하며 NDES 서비스 호스트 컴퓨터에 사용되는 SSL 인증서를 신뢰해야 합니다. 이러한 인증서를 통해 WAP 서버는 클라이언트와의 SSL 연결을 종료하고 NDES 서비스로의 새 SSL 연결을 생성할 수 있습니다.  

  자세한 내용은 [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates)(WAP에 대한 인증서 계획) 및 [general information about WAP servers](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11))(WAP 서버에 대한 일반적인 정보)를 참조하세요.

### <a name="accounts"></a>계정   
- **NDES 서비스 계정** - NDES를 설정하기 전에 NDES 서비스 계정으로 사용할 도메인 사용자 계정을 식별합니다. NDES를 구성하기 전 발급하는 CA에서 템플릿을 구성할 때 이 계정을 지정합니다.  

  이 계정에는 NDES 호스트 서버에 대해 다음 권한이 있어야 합니다.  
  - **로컬 로그온**  
  - **서비스로 로그온**  
  - **일괄 작업으로 로그온**  

  자세한 내용은 [NDES 서비스 계정 역할을 할 도메인 사용자 계정 만들기](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v=ws.11)#to-create-a-domain-user-account-to-act-as-the-ndes-service-account)를 참조하세요. 
- **NDES 서비스 호스트 컴퓨터에 대한 액세스** - NDES를 설치하는 서버에서 Windows Server 역할을 설치 및 구성할 수 있는 권한이 있는 도메인 사용자 계정이 필요합니다.  

- **인증 기관에 대한 액세스** - 인증 기관을 관리할 수 있는 권한이 있는 도메인 사용자 계정이 필요합니다.  

### <a name="network-requirements"></a>네트워크 요구 사항

[Azure AD 애플리케이션 프록시, 웹 액세스 프록시](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/) 또는 타사 프록시와 같은 역방향 프록시를 통해 NDES 서비스를 게시하는 것이 좋습니다. 역방향 프록시를 사용하지 않는 경우 인터넷의 모든 호스트 및 IP 주소에서 NDES 서비스로 보내는 포트 443의 TCP 트래픽을 허용합니다.  

환경에서 NDES 서비스와 모든 지원 인프라 간의 통신에 필요한 모든 포트 및 프로토콜을 허용합니다. 예를 들어 NDES 서비스 호스트 컴퓨터는 Configuration Manager와 같이 작업 환경 내에서 CA, DNS 서버, 도메인 컨트롤러 및 다른 서비스나 서버와 통신해야 합니다.

### <a name="certificates-and-templates"></a>인증서 및 템플릿

SCEP를 사용하는 경우 다음 인증서 및 템플릿이 사용됩니다.

|개체    |세부 정보    |
|----------|-----------|
|**SCEP 인증서 템플릿**         |디바이스 SCEP 요청을 이행하는 데 사용되는 발급 CA에서 구성할 템플릿입니다. |
|**클라이언트 인증 인증서** |발급 CA 또는 퍼블릭 CA에서 요청됩니다.<br /> NDES 서비스를 호스트하는 컴퓨터에 이 인증서를 설치하며, Intune 인증서 커넥터에서 사용됩니다.<br /> 인증서에 *클라이언트* 및 *서버 인증* 키 사용이 설정된 경우 이 인증서를 발급하는 데 사용하는 CA 템플릿에 (**고급 키 사용**)을 설정합니다. 그런 다음, 서버 및 클라이언트 인증에 동일한 인증서를 사용할 수 있습니다. |
|**서버 인증 인증서** |발급 CA 또는 퍼블릭 CA에서 요청된 웹 서버 인증서입니다.<br /> 이 SSL 인증서는 NDES를 호스트하는 컴퓨터의 IIS에서 설치하고 바인딩합니다.<br />인증서에 *클라이언트* 및 *서버 인증* 키 사용이 설정된 경우 이 인증서를 발급하는 데 사용하는 CA 템플릿에 (**고급 키 사용**)을 설정합니다. 그런 다음, 서버 및 클라이언트 인증에 동일한 인증서를 사용할 수 있습니다. |
|**신뢰할 수 있는 루트 CA 인증서**       |SCEP 인증서 프로필을 사용하려면 디바이스에서 신뢰할 수 있는 루트 CA(인증 기관)를 신뢰해야 합니다. Intune에서 *신뢰할 수 있는 인증서 프로필*을 사용하여 신뢰할 수 있는 루트 CA 인증서를 사용자 및 디바이스에 프로비저닝합니다. <br/><br/> **-**  운영 체제 플랫폼당 하나의 신뢰할 수 있는 루트 CA 인증서를 사용하고, 해당 인증서를 새로 만드는 각 신뢰할 수 있는 인증서 프로필에 연결합니다. <br /><br /> **-**  필요하면 신뢰할 수 있는 루트 CA 인증서를 추가로 사용할 수 있습니다. 예를 들어, Wi-Fi 액세스 지점의 서버 인증 인증서에 서명하는 CA에 신뢰를 제공하기 위해 추가 인증서를 사용할 수도 있습니다. 발급 CA에 대해 신뢰할 수 있는 루트 CA 인증서를 추가로 만듭니다.  Intune에서 만든 SCEP 인증서 프로필에서 발급 CA에 대한 신뢰할 수 있는 루트 CA 프로필을 지정해야 합니다.<br/><br/> 신뢰할 수 있는 인증서 프로필에 대한 내용은 *Intune에서 인증을 위해 인증서 사용*의 [신뢰할 수 있는 루트 CA 인증서 내보내기](certificates-configure.md#export-the-trusted-root-ca-certificate) 및 [신뢰할 수 있는 인증서 프로필 만들기](certificates-configure.md#create-trusted-certificate-profiles)를 참조하세요. |

## <a name="configure-the-certification-authority"></a>인증 기관 구성

이어지는 섹션에서는 다음과 같은 작업을 수행합니다.
- NDES용 필수 템플릿을 구성 및 게시합니다. 
- 인증서 해지를 위한 필수 사용 권한을 설정합니다. 

다음 섹션을 진행하려면 Windows Server 2012 R2 이상 및 AD CS(Active Directory 인증서 서비스)에 대한 지식이 필요합니다.  

### <a name="access-your-issuing-ca"></a>발급 CA에 액세스

1. CA를 관리할 수 있는 권한이 있는 도메인 계정을 사용하여 발급 CA에 로그인합니다.  
2. 인증 기관 MMC(Microsoft Management Console)를 엽니다. 'certsrv.msc'를 **실행**하거나 **서버 관리자**에서 **도구**, **인증 기관**을 차례로 클릭합니다.
3. **인증서 템플릿** 노드를 선택하고 **작업** > **관리**를 클릭합니다.

### <a name="create-the-scep-certificate-template"></a>SCEP 인증서 템플릿 만들기

1. SCEP 인증서 템플릿으로 사용할 v2 인증서 템플릿(Windows 2003 호환성 포함)을 만듭니다. 다음과 같습니다.  
   - *인증서 템플릿* 스냅인을 사용하여 새 사용자 지정 템플릿을 만듭니다.  
   - 기존 템플릿(예: 사용자 템플릿)을 복사한 다음, NDES 템플릿으로 사용할 복사본을 업데이트합니다.
 
2. 템플릿의 지정된 탭에서 다음 설정을 구성합니다.
   - **일반**:
     - **Active Directory에서 인증서 게시**를 선택 취소합니다.
     - 나중에 이 템플릿을 식별할 수 있도록 친숙한 **템플릿 표시 이름**을 지정합니다.  

   - **주체 이름**:  
     - **요청 시 제공**을 선택합니다. 보안은 NDES용 Intune 정책 모듈을 통해 적용됩니다.  

     ![템플릿, 주체 이름 탭](./media/certificates-scep-configure/scep-ndes-subject-name.jpg)
   - **확장**:  
     - **애플리케이션 정책 설명**에 **클라이언트 인증**이 포함되어 있는지 확인합니다.  
       > [!IMPORTANT]  
       > 필요한 애플리케이션 정책만 추가합니다. 보안 관리자와 선택 사항을 확인합니다.
 
     - iOS 및 macOS 인증서 템플릿의 경우 **키 사용**을 편집하고 **서명이 원본 증명임**이 선택되어 있지 않은지 확인합니다.

     ![템플릿, 확장 탭](./media/certificates-scep-configure/scep-ndes-extensions.jpg)  

   - **보안**:  
     - **NDES 서비스 계정**을 추가합니다. 이 계정에는 이 템플릿에 대한 **읽기** 및 **등록** 권한이 있어야 합니다.

     - SCEP 프로필을 만들 Intune 관리자용 추가 계정을 추가합니다. 이러한 계정에는 SCEP 프로필을 만드는 동안 이러한 관리자가 이 템플릿을 찾아볼 수 있도록 하기 위해 템플릿에 대한 **읽기** 권한이 있어야 합니다.  

     ![템플릿, 보안 탭](./media/certificates-scep-configure/scep-ndes-security.jpg)  

   - **요청 처리**:  
      다음 그림은 예제입니다. 구성은 다를 수 있습니다.  

     ![템플릿, 요청 처리 탭](./media/certificates-scep-configure/scep-ndes-request-handling.png) 

   - **발급 요구 사항**:  
     다음 그림은 예제입니다. 구성은 다를 수 있습니다.  

     ![템플릿, 발급 요구 사항 탭](./media/certificates-scep-configure/scep-ndes-issuance-reqs.jpg)  

3. 인증서 템플릿을 저장합니다.  

### <a name="create-the-client-certificate-template"></a>클라이언트 인증서 템플릿 만들기

Intune Certificate Connector에서는 *클라이언트 인증* 확장 키 사용 및 주체 이름이 커넥터가 설치된 머신의 FQDN과 동일한 인증서가 필요합니다. 다음 속성을 포함하는 템플릿이 필요합니다.

- **확장** > **애플리케이션 정책**은 **클라이언트 인증**을 포함해야 합니다.
- **주체 이름** > **요청 시 제공**.

이러한 속성을 포함하는 템플릿이 이미 있는 경우 다시 사용할 수 있습니다. 그렇지 않은 경우 기존 항목을 복제하거나 사용자 지정 템플릿을 만들어 새 템플릿을 만들 수 있습니다.

### <a name="create-the-server-certificate-template"></a>서버 인증서 템플릿 만들기

NDES 서버의 관리형 디바이스 및 IIS 간 통신에는 인증서를 사용해야 하는 HTTPS가 사용됩니다. **웹 서버** 인증서 템플릿을 사용하여 이 인증서를 발급할 수 있습니다. 또는 전용 템플릿을 사용하려는 경우 다음 속성이 필요합니다.

- **확장** > **애플리케이션 정책**은 **서버 인증**을 포함해야 합니다.
- **주체 이름** > **요청 시 제공**.

> [!NOTE]  
> 클라이언트 및 서버 인증서 템플릿의 요구 사항을 모두 충족하는 인증서가 있는 경우 IIS와 Intune Certificate Connector 모두에 단일 인증서를 사용할 수 있습니다.

### <a name="grant-permissions-for-certificate-revocation"></a>인증서 해지를 위한 사용 권한 부여

Intune에서 더 이상 필요하지 않은 인증서를 해지할 수 있도록 하려면 인증 기관에서 사용 권한을 부여해야 합니다. 

Intune Certificate Connector에서 NDES 서버 **시스템 계정** 또는 **NDES 서비스 계정**과 같은 특정 계정을 사용할 수 있습니다.

1. 인증 기관 콘솔에서 CA 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
2. **보안** 탭에서 **추가**를 클릭합니다.
3. 다음과 같이 **인증서 발급 및 관리** 권한을 부여합니다.
   - NDES 서버 **시스템 계정**을 사용하도록 선택하는 경우 NDES 서버에 대한 사용 권한을 제공합니다.
   - **NDES 서비스 계정**을 사용하도록 선택하는 경우, 대신 해당 계정에 대한 권한을 제공합니다.

### <a name="modify-the-validity-period-of-the-certificate-template"></a>인증서 템플릿의 유효 기간 수정

인증서 템플릿의 유효 기간을 수정하는 것은 선택 사항입니다.  

[SCEP 인증서 템플릿을 만든](#create-the-scep-certificate-template) 후에 **일반** 탭에서 해당 템플릿을 편집하여 **유효 기간**을 검토할 수 있습니다.  

기본적으로 Intune은 템플릿에 구성된 값을 사용합니다. 그러나 요청자가 다른 값을 입력할 수 있도록 CA를 구성할 수 있으며 해당 값은 Intune 콘솔 내에서 설정할 수 있습니다.  

> [!IMPORTANT]  
> iOS 및 macOS의 경우 항상 템플릿에 설정된 값을 사용합니다.  

#### <a name="to-configure-a-value-that-can-be-set-from-within-the-intune-console"></a>Intune 콘솔 내에서 설정할 수 있는 값을 구성하려면  
1. CA에서 다음 명령을 실행합니다.  
   -**certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**  
   -**net stop certsvc**  
   -**net start certsvc**  

2. 발급 CA에서 인증 기관 스냅인을 사용하여 인증서 템플릿을 게시합니다. **인증서 템플릿** 노드를 클릭하고 **작업** > **새로 만들기** > **발급할 인증서 템플릿**을 클릭한 다음, 이전 섹션에서 만든 인증서 템플릿을 선택합니다.  

3. **인증서 템플릿** 폴더에서 게시된 템플릿을 확인하여 유효성을 검사합니다.  

## <a name="set-up-ndes"></a>NDES 설정  
다음 절차에 따라 Intune에서 사용할 NDES(네트워크 디바이스 등록 서비스)를 구성할 수 있습니다. 자세한 내용은 [네트워크 디바이스 등록 서비스 지침](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831498(v%3dws.11))을 참조하세요.  

### <a name="install-the-ndes-service"></a>NDES 서비스 설치  
1. NDES 서비스를 호스트할 서버에서 **엔터프라이즈 관리자**로 로그온한 다음, [역할 및 기능 추가 마법사](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))를 사용하여 NDES를 설치합니다.

   1. 마법사에서 **Active Directory 인증서 서비스** 를 선택하여 AD CS 역할 서비스에 대한 액세스 권한을 받습니다. **네트워크 디바이스 등록 서비스**를 선택하고 **인증 기관**선택을 취소한 다음, 마법사를 완료합니다.  

      > [!TIP]  
      > **설치 진행률**에서 **닫기**를 선택하지 마세요. 대신 **대상 서버에서 Active Directory 인증서 서비스 구성** 링크를 선택하세요. **AD CS 구성** 마법사가 열립니다. 이 마법사에 따라 이 문서의 다음 절차인 *NDES 서비스 구성*을 진행합니다. AD CS 구성이 열리면 역할 및 기능 추가 마법사를 닫을 수 있습니다.  

   2. NDES를 서버에 추가할 때는 마법사에서 IIS도 설치합니다. IIS에서 다음과 같은 구성을 사용하는지 확인합니다.  

      - **웹 서버** > **보안** > **요청 필터링**  
      - **웹 서버** > **애플리케이션 개발** > **ASP.NET 3.5**  

        ASP.NET 3.5를 설치하면 .NET Framework 3.5가 설치됩니다. .NET Framework 3.5를 설치할 때는 핵심 **.NET Framework 3.5** 기능과 **HTTP 활성화**를 모두 설치합니다.  
      - **웹 서버** > **애플리케이션 개발** > **ASP.NET 4.5**  

        ASP.NET 4.5를 설치하면 .NET Framework 4.5가 설치됩니다. .NET Framework 4.5를 설치할 때는 핵심 **.NET Framework 4.5** 기능, **ASP.NET 4.5** 및 **WCF 서비스** > **HTTP 활성화** 기능을 설치합니다.  

      - **관리 도구** > **IIS 6 관리 호환성** > **IIS 6 메타베이스 호환성**  
      - **관리 도구** > **IIS 6 관리 호환성** > **IIS 6 WMI 호환성**  
      - 서버에서 NDES 서비스 계정을 로컬 **IIS_IUSR** 그룹의 구성원으로 추가합니다.  

2. NDES 서비스 호스트 컴퓨터의 관리자 권한 명령 프롬프트에서 다음 명령을 실행합니다. 다음 명령을 실행하여 NDES 서비스 계정의 SPN을 설정합니다.  

   `setspn -s http/<DNS name of the computer that hosts the NDES service> <Domain name>\<NDES Service account name>`
   
   예를 들어, NDES 서비스 호스트 컴퓨터의 이름이 **Server01**이고, 도메인이 **Contoso.com**이고, 서비스 계정이 **NDESService**인 경우 다음을 사용합니다.  

   `setspn –s http/Server01.contoso.com contoso\NDESService`  

### <a name="configure-the-ndes-service"></a>NDES 서비스 구성  

1. NDES 서비스 호스트 컴퓨터에서 **AD CS 구성** 마법사를 연 다음, 다음과 같이 업데이트합니다.  

   > [!TIP]  
   > 마지막 절차부터 계속 진행하고 **대상 서버에서 Active Directory 인증서 서비스 구성** 링크를 클릭한 경우 이 마법사가 이미 열려 있어야 합니다. 링크를 클릭하지 않은 경우에는 서버 관리자를 열어 Active Directory 인증서 서비스의 배포 후 구성에 액세스합니다.  

   - **역할 서비스**에서 **네트워크 디바이스 등록 서비스**를 선택합니다.
   - **NDES의 서비스 계정**에서 NDES 서비스 계정을 지정합니다.
   - **NDES를 위한 CA**에서 **선택**을 클릭한 다음, 인증서 템플릿을 구성한 발급 CA를 선택합니다.
   - **NDES의 암호화**에서 회사 요구 사항에 맞는 키 길이를 설정합니다.
   - **확인**에서 **구성**을 선택하여 마법사를 완료합니다.

2. 마법사를 완료한 후 NDES 서비스 호스트 컴퓨터에서 다음 레지스트리 키를 업데이트합니다.  
   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`  

   이 키를 업데이트하려면 인증서 템플릿의 **목적**을 확인합니다(**요청 처리** 탭에서 찾을 수 있음). 그런 다음, 기존 데이터를 [인증서 템플릿을 만들 때](#create-the-scep-certificate-template) 지정한 인증서 템플릿의 이름(템플릿의 표시 이름이 아님)으로 바꾸어 해당 레지스트리 항목을 업데이트합니다.  

   다음 표는 인증서 템플릿 목적을 레지스트리의 값에 매핑합니다.
   
   |요청 처리 탭에 나와 있는 인증서 템플릿 용도|편집할 레지스트리 값|SCEP 프로필의 Intune 관리 콘솔에 표시되는 값|
   |------------------------|-------------------------|---|
   |서명               |SignatureTemplate        |디지털 서명 |
   |암호화              |EncryptionTemplate       |키 암호화  |
   |서명 및 암호화|GeneralPurposeTemplate   |키 암호화<br/>디지털 서명 |  

   예를 들어 인증서 템플릿의 용도가 **암호화**이면 **EncryptionTemplate** 값을 편집하여 인증서 템플릿의 이름으로 설정합니다.  

3. IIS에서 NDES 서비스가 받는 긴 URL(쿼리)에 대한 지원을 추가하도록 IIS 요청 필터링을 구성합니다.
   1. IIS 관리자에서 **기본 웹 사이트** > **요청 필터링** > **기능 설정 편집**을 선택하여 **요청 필터링 설정 편집** 페이지를 엽니다.  

   2. 다음 설정을 구성합니다.  
      - **최대 URL 길이(바이트)** = 65534  
      - **최대 쿼리 문자열(바이트)** = 65534  
   3. **확인**을 선택하여 이 구성을 저장하고 IIS 관리자를 닫습니다.  
   4. 다음 레지스트리 키에서 표시된 값이 있는지 확인하여 이 구성이 유효한지 검사합니다.  

      `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`    

      다음 값은 DWORD 항목으로 설정됩니다.  
      - 이름: **MaxFieldLength**, 10진수 값 **65534**  
      - 이름: **MaxRequestBytes**, 10진수 값 **65534**  
4. NDES 서비스 서버를 다시 시작합니다. **Iisreset**은 필요한 변경을 완료하지 않으므로 사용하지 않도록 합니다.  

5. *http://* Server_FQDN */certsrv/mscep/mscep.dll*로 이동합니다. 다음 그림과 유사한 NDES 페이지가 표시됩니다.  

   ![NDES 테스트](./media/certificates-scep-configure/scep-ndes-url.png)
  
   웹 주소가 **503 서비스를 사용할 수 없음**을 반환하면 컴퓨터 이벤트 뷰어를 확인합니다. 이 오류는 일반적으로 [NDES 서비스 계정에 대한 권한](#accounts)이 없기 때문에 애플리케이션 풀이 중지될 때 발생합니다.  
  
### <a name="install-and-bind-certificates-on-the-server-that-hosts-ndes"></a>NDES 호스트 서버에 인증서 설치 및 바인딩  
> [!TIP]  
> 다음 절차에서는 두 가지 사용 조건을 충족하도록 인증서가 구성된 경우 *서버 인증* 및 *클라이언트 인증* 모두에 단일 인증서를 사용할 수 있습니다. 각 사용 조건은 다음 절차의 1단계 및 3단계에 설명되어 있습니다.  

1. 내부 CA 또는 공용 CA에서 **서버 인증** 인증서를 요청한 후 서버에 인증서를 설치합니다.  

   서버가 단일 네트워크 주소에 대해 외부 및 내부 이름을 사용하는 경우 서버 인증 인증서에는 다음이 있어야 합니다.  

   - 외부 공용 서버 이름이 포함된 **주체 이름**
   - 내부 서버 이름을 포함하는 **주체 대체 이름**  

2. 다음과 같이 IIS에서 서버 인증 인증서를 바인딩합니다.  
  
   1. 서버 인증 인증서를 설치한 후 **IIS 관리자**를 열고 **기본 웹 사이트**를 선택합니다. **작업** 창에서 **바인딩**을 선택합니다.  
   1. **추가**를 선택하고 **유형**을 **https**로 설정한 다음, 포트가 **443**인지 확인합니다.  
   1. **SSL 인증서**의 경우 서버 인증 인증서를 지정합니다.  
 
3. NDES 서버에서 내부 CA 또는 공용 인증 기관으로부터 **클라이언트 인증** 인증서를 요청하여 설치합니다.  

   클라이언트 인증 인증서는 다음 속성을 포함해야 합니다.  
   - **확장된 키 사용**: 이 값에는 **클라이언트 인증**이 포함되어야 합니다.  
   - **주체 이름**: 이 값은 인증서를 설치하는 서버(NDES 서버)의 DNS 이름과 같아야 합니다.  

4. 이제 NDES 서비스 호스트 서버에서 Intune Certificate Connector를 지원할 준비가 되었습니다.  

## <a name="install-the-intune-certificate-connector"></a>Intune Certificate Connector 설치  
Microsoft Intune Certificate Connector는 NDES 서비스를 실행하는 서버에 설치됩니다. 발급하는 CA(인증 기관)와 동일한 서버에서 NDES 또는 Intune Certificate Connector를 사용하는 것은 지원되지 않습니다.  

다음과 같이 인증서 커넥터를 설치합니다.  
1. Intune 권한이 있는 계정을 사용하여 [Intune 포털](https://aka.ms/intuneportal)에 로그인합니다.  

2. **디바이스 구성** > **인증 기관** > **추가**를 선택합니다.  

3. SCEP 파일용 커넥터를 다운로드하여 저장합니다. 커넥터를 설치하려는 서버에서 액세스할 수 있는 위치에 저장합니다.

   ![ConnectorDownload](./media/certificates-scep-configure/download-certificates-connector.png)

4. 다운로드가 완료되면 NDES(네트워크 디바이스 등록 서비스) 역할을 호스트하는 서버로 이동합니다. 그런 다음:  

   1. Intune Certificate Connector에 필요한 .NET 4.5 Framework가 설치되어 있는지 확인합니다. .NET 4.5 Framework는 Windows Server 2012 R2 및 최신 버전에 자동으로 포함됩니다.  
   2. 설치 관리자(**NDESConnectorSetup.exe**)를 실행합니다. 설치 관리자는 NDES에 대한 정책 모듈 및 IIS CRP(인증서 등록 지점) 웹 서비스도 설치합니다. CRP 웹 서비스 *CertificateRegistrationSvc*는 IIS에서 애플리케이션으로 실행됩니다.  

      - 독립 실행형 Intune에 NDES를 설치하면 CRP 서비스가 인증서 커넥터와 함께 자동으로 설치됩니다. 
      - 구성 관리자와 함께 Intune을 사용할 때는 Configuration Manager 사이트 시스템 역할로 인증서 등록 지점을 설치합니다.  
5. Certificate Connector용 클라이언트 인증서를 입력하라는 메시지가 표시되면 **선택**을 선택하고 이 문서 앞부분에 나오는 [NDES 호스트 서버에 인증서 설치 및 바인딩](#install-and-bind-certificates-on-the-server-that-hosts-ndes) 절차, 3단계 동안 NDES 서버에 설치한 **클라이언트 인증** 인증서를 선택합니다.  

   클라이언트 인증 인증서를 선택하고 나면 **Microsoft Intune Certificate Connector용 클라이언트 인증서** 화면으로 돌아가게 됩니다. 선택한 인증서는 표시되지 않지만 **다음**을 선택하면 해당 인증서의 속성을 볼 수 있습니다. **다음**을 선택한 다음, **설치**를 선택합니다.

6. 마법사를 완료한 후 마법사를 닫기 전에 **인증서 커넥터 UI를 시작**합니다.  

   Certificate Connector UI를 시작하기 전에 마법사를 닫은 경우 *<install_Path>\NDESConnectorUI\NDESConnectorUI.exe* 명령을 실행하여 마법사를 다시 열 수 있습니다.

7. **인증서 커넥터** UI에서:  
   1. **로그인**을 선택하고 Intune 서비스 관리자 자격 증명 또는 전역 관리 권한이 있는 테넌트 관리자의 인증서 자격 증명을 입력합니다.  
   2. 사용하는 계정에 유효한 Intune 라이선스가 할당되어야 합니다.  
   3. 로그인하면 Intune 인증서 커넥터가 Intune에서 인증서를 다운로드합니다. 이 인증서는 커넥터와 Intune 간의 인증에 사용됩니다. 사용한 계정에 Intune 라이선스가 없는 경우 커넥터(NDESConnectorUI.exe)는 Intune에서 인증서를 가져오지 못합니다.  

      조직에서 프록시 서버를 사용하며 NDES 서버에서 인터넷에 액세스하는 데 프록시가 필요한 경우 **프록시 서버 사용**을 선택합니다. 그런 다음, 프록시 서버 이름, 포트 및 계정 자격 증명을 입력하여 연결합니다.  

    4. **고급** 탭을 선택한 다음, 발급 인증 기관에 대한 **인증서 발급 및 관리** 권한이 있는 계정의 자격 증명을 입력합니다. 변경 내용을 **적용**합니다.  

    5. 이제 인증서 커넥터 UI를 닫아도 됩니다.  

8. 명령 프롬프트를 열고, **services.msc**를 입력한 다음, **Enter**를 입력합니다. **Intune 커넥터 서비스** > **다시 시작**을 마우스 오른쪽 단추로 클릭합니다.


서비스가 실행되고 있는지 확인하려면 브라우저를 열고 다음 URL을 입력합니다. 그러면 **403** 오류가 반환됩니다. `https://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`  

> [!NOTE]  
> Intune Certificate Connector는 TLS 1.2를 지원합니다. 커넥터를 호스트하는 서버에서 TLS 1.2를 지원하는 경우 TLS 1.2가 사용됩니다. 서버가 TLS 1.2를 지원하지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 디바이스와 서버 간 인증에 사용됩니다.

## <a name="next-steps"></a>다음 단계

[SCEP 인증서 프로필 만들기](certificates-profile-scep.md)  
[Intune Certificate Connector의 이슈 해결](troubleshoot-certificate-connector-events.md)
