---
title: Microsoft Intune - Azure를 사용한 SCEP 인증서 사용 | Micrososft Docs
description: Microsoft Intune에서 SCEP 인증서를 사용하려면 온-프레미스 AD 도메인을 구성하고 인증 기관을 만들고 NDES 서버를 설정하고 Intune 인증서 커넥터를 설치합니다. 그런 다음, SCEP 인증서 프로필을 만든 다음, 이 프로필을 그룹에 할당합니다. 또한 다른 이벤트 ID 및 해당 설명과 Intune Connector 서비스에 대한 진단 코드도 참조합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 80b860810800ca887ac55de6fbfc41b2fded3b12
ms.sourcegitcommit: 378474debffbc85010c54e20151d81b59b7a7828
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028735"
---
# <a name="configure-and-use-scep-certificates-with-intune"></a>Intune을 사용하여 SCEP 인증서 구성 및 사용

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서에서는 Intune을 통해 인프라를 구성한 다음, SCEP(단순 인증서 등록 프로토콜) 인증서 프로필을 만들고 할당하는 방법을 보여 줍니다.

## <a name="configure-on-premises-infrastructure"></a>온-프레미스 인프라 구성

- **Active Directory 도메인**: 웹 응용 프로그램 프록시 서버를 제외하고 이 섹션에 나열된 모든 서버는 Active Directory 도메인에 가입되어 있어야 합니다.

- **인증 기관**(CA): Windows Server 2008 R2 이상에서 실행되는 엔터프라이즈 CA(인증 기관)입니다. 독립 실행형 CA는 지원되지 않습니다. 자세한 내용은 [인증 기관 설치](http://technet.microsoft.com/library/jj125375.aspx)를 참조하세요.
    CA에서 Windows Server 2008 R2를 실행하는 경우에는 [KB2483564의 핫픽스를 설치](http://support.microsoft.com/kb/2483564/)해야 합니다.

- **NDES 서버**: Windows Server 2012 R2 이상을 실행하는 서버에 NDES(네트워크 장치 등록 서비스)를 설치해야 합니다. 엔터프라이즈 CA를 실행하는 서버에 NDES가 실행되는 경우 Intune는 사용을 지원하지 않습니다. 네트워크 장치 등록 서비스를 호스트하도록 Windows Server 2012 R2를 구성하는 방법에 대한 지침은 [네트워크 장치 등록 서비스 지침](http://technet.microsoft.com/library/hh831498.aspx)을 참조하세요.
NDES 서버는 CA를 호스트하는 도메인에 가입해야 하며 CA와 동일한 서버에 있지 않아야 합니다. 별도의 포리스트, 격리된 네트워크 또는 내부 도메인에 NDES 서버를 배포하는 방법에 대한 자세한 내용은 [네트워크 장치 등록 서비스와 함께 정책 모듈 사용](https://technet.microsoft.com/library/dn473016.aspx) 항목에서 찾아볼 수 있습니다.

- **Microsoft Intune Certificate Connector**: Azure Portal을 사용하여 **인증서 커넥터** 설치 관리자(**NDESConnectorSetup.exe**)를 다운로드합니다. 그런 다음, 인증서 커넥터를 설치하려는 NDES(Network Device Enrollment Service) 역할을 호스트하는 서버에서 **NDESConnectorSetup.exe**를 실행할 수 있습니다.

  - NDES 인증서 커넥터는 FIPS(Federal Information Processing Standard) 모드도 지원합니다. FIPS가 필수는 아니지만 활성화되면 인증서를 발급하고 해지할 수 있습니다.

- **웹 응용 프로그램 프록시 서버**(선택 사항): Windows Server 2012 R2 이상을 WAP(웹 응용 프로그램 프록시) 서버로 실행하는 서버를 사용합니다. 이 구성의 특징은 다음과 같습니다.
  - 장치에서 인터넷 연결을 사용하여 인증서를 받을 수 있습니다.
  - 장치가 인터넷을 통해 연결하여 인증서를 받고 갱신하는 경우 보안상 안전합니다.

#### <a name="additional"></a>추가 정보

- WAP를 호스팅하는 서버에는 네트워크 장치 등록 서비스에서 사용하는 긴 URL을 지원할 수 있도록 하는 [업데이트를 설치](http://blogs.technet.com/b/ems/archive/2014/12/11/hotfix-large-uri-request-in-web-application-proxy-on-windows-server-2012-r2.aspx) 해야 합니다. 이 업데이트는 [2014년 12월 업데이트 롤업](http://support.microsoft.com/kb/3013769)에 포함되어 있으며, [KB3011135](http://support.microsoft.com/kb/3011135)에서 개별적으로 다운로드할 수도 있습니다.
- WAP 서버에는 외부 클라이언트에 게시된 이름과 일치하는 SSL 인증서가 있어야 하며 NDES 서버에서 사용되는 SSL 인증서를 신뢰해야 합니다. 이러한 인증서를 통해 WAP 서버는 클라이언트와의 SSL 연결을 종료하고 NDES 서버로의 새 SSL 연결을 생성할 수 있습니다.

자세한 내용은 [Plan certificates for WAP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383650(v=ws.11)#plan-certificates)(WAP에 대한 인증서 계획) 및 [general information about WAP servers](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn584113(v=ws.11))(WAP 서버에 대한 일반적인 정보)를 참조하세요.

### <a name="network-requirements"></a>네트워크 요구 사항

인터넷에서 경계 네트워크까지, NDES 서버가 연결된 인터넷에 있는 모든 호스트/IP 주소에서 포트 443을 허용해야 합니다.

경계 네트워크에서 신뢰할 수 있는 네트워크까지, 도메인에 가입된 NDES 서버에서 도메인 액세스에 필요한 모든 포트 및 프로토콜을 허용해야 합니다. NDES 서버는 인증서 서버, DNS 서버, Configuration Manager 서버 및 도메인 컨트롤러에 액세스해야 합니다.

[Azure AD 응용 프로그램 프록시](https://azure.microsoft.com/documentation/articles/active-directory-application-proxy-publish/), [웹 액세스 프록시](https://technet.microsoft.com/library/dn584107.aspx) 또는 타사 프록시와 같은 프록시를 통해 NDES 서버를 게시하는 것이 좋습니다.

### <a name="certificates-and-templates"></a>인증서 및 템플릿

|개체|세부 정보|
|----------|-----------|
|**인증서 템플릿**|발급 CA에서 이 템플릿을 구성합니다.|
|**클라이언트 인증 인증서**|발급 CA 또는 공용 CA에서 요청되었습니다. 이 인증서를 NDES 서버에 설치합니다.|
|**서버 인증 인증서**|발급 CA 또는 공용 CA에서 요청되었습니다. 이 SSL 인증서를 NDES 서버의 IIS에 설치 및 바인딩합니다.|
|**신뢰할 수 있는 루트 CA 인증서**|루트 CA 또는 루트 CA를 신뢰하는 장치에서 이 인증서를 **.cer** 파일로 내보낸 후 신뢰할 수 있는 CA 인증서 프로필을 사용하여 장치에 할당합니다.<br /><br />운영 체제 플랫폼당 하나의 신뢰할 수 있는 루트 CA 인증서를 사용하고, 새로 만드는 각 신뢰할 수 있는 루트 인증서 프로필과 연결합니다.<br /><br />필요하면 신뢰할 수 있는 루트 CA 인증서를 추가로 사용할 수 있습니다. 예를 들어, Wi-Fi 액세스 지점의 서버 인증 인증서에 서명하는 CA에 신뢰를 제공하기 위해 사용하게 될 수도 있습니다.|

### <a name="accounts"></a>계정

|이름|세부 정보|
|--------|-----------|
|**NDES 서비스 계정**|NDES 서비스 계정으로 사용할 도메인 사용자 계정을 입력합니다.|

## <a name="configure-your-infrastructure"></a>인프라 구성
인증서 프로필을 구성하려면 다음 단계를 완료해야 합니다. 이러한 단계를 완료하려면 Windows Server 2012 R2 이상 및 ADCS(Active Directory 인증서 서비스)에 대한 지식이 있어야 합니다.

#### <a name="step-1---create-an-ndes-service-account"></a>1단계 - NDES 서비스 계정 만들기

NDES 서비스 계정으로 사용할 도메인 사용자 계정을 만듭니다. NDES를 설치하고 구성하기 전에 발급하는 CA에서 템플릿을 구성할 때 이 계정을 입력합니다. 사용자에게 기본 권한(**로컬 로그온**, **서비스로 로그온** 및 **일괄 작업으로 로그온** 권한)이 있는지 확인합니다. 일부 조직에는 해당 권한을 사용하지 않도록 설정하는 보안 강화 정책이 있습니다.

#### <a name="step-2---configure-certificate-templates-on-the-certification-authority"></a>2단계 - 인증 기관에서 인증서 템플릿 구성
이 단계에서는 다음을 수행합니다.

- NDES의 인증서 템플릿 구성
- NDES의 인증서 템플릿 게시

##### <a name="configure-the-certification-authority"></a>인증 기관 구성

1. 엔터프라이즈 관리자로 로그인합니다.

2. 발급하는 CA에서 인증서 템플릿 스냅인을 사용하여 새 사용자 지정 템플릿을 만듭니다. 또는 기존 템플릿을 복사한 다음, NDES에 사용할 기존 템플릿(예: 사용자 템플릿)을 업데이트합니다.

   >[!NOTE]
   > NDES 인증서 템플릿은 v2 인증서 템플릿(Windows 2003 호환성 포함)을 기반으로 해야 합니다.

   템플릿의 다음 항목이 구성되어 있어야 합니다.

   - 템플릿에 친숙한 **템플릿 표시 이름**을 입력합니다.

   - **주체 이름**에서 **요청에 따라 제공**을 선택합니다. 보안은 NDES용 Intune 정책 모듈을 통해 적용됩니다.

   - **확장**에서 **응용 프로그램 정책 설명**에 **클라이언트 인증**이 포함되어 있는지 확인합니다.

     > [!IMPORTANT]
     > iOS 및 macOS 인증서 템플릿의 경우 **확장** 탭에서 **키 사용**을 편집하고 **서명이 원본 증명임**이 선택되어 있지 않은지 확인합니다.

   - **보안**에서 NDES 서비스 계정을 추가하고 템플릿에 **등록** 권한을 부여합니다. SCEP 프로필을 만드는 Intune 관리자는 SCEP 프로필을 만들 때 템플릿을 찾아볼 수 있도록 **읽기** 권한이 필요합니다.

     > [!NOTE]
     > 인증서를 해지하려면 NDES 서비스 계정에 인증서 프로필에서 사용하는 각 인증서 템플릿에 대한 *인증서 발급 및 관리* 권한이 필요합니다.

3. 템플릿의 **일반** 탭에서 **유효 기간** 을 검토합니다. 기본적으로 Intune은 템플릿에 구성된 값을 사용합니다. 그러나 요청자가 다른 값을 입력할 수 있도록 CA를 구성할 수도 있습니다. 이와 같이 구성하면 Intune 관리자 콘솔 내에서 다른 값을 설정할 수 있습니다. 항상 템플릿의 값을 사용하려면 이 단계의 나머지 부분을 건너뜁니다.

   > [!IMPORTANT]
   > iOS 및 macOS는 다른 구성 내용에 관계없이 항상 템플릿에 설정된 값을 사용합니다.

예제 템플릿 구성입니다.

![템플릿, 요청 처리 탭](./media/scep_ndes_request_handling.png)

![템플릿, 주체 이름 탭](./media/scep_ndes_subject_name.jpg)

![템플릿, 보안 탭](./media/scep_ndes_security.jpg)

![템플릿, 확장 탭](./media/scep_ndes_extensions.jpg)

![템플릿, 발급 요구 사항 탭](./media/scep_ndes_issuance_reqs.jpg)

> [!IMPORTANT]
> 응용 프로그램 정책의 경우 필요한 응용 프로그램 정책만 추가합니다. 보안 관리자와 선택 사항을 확인합니다.

요청자가 유효 기간을 입력할 수 있도록 CA를 구성합니다.

1. CA에서 다음 명령을 실행합니다.
   - **certutil -setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**
   - **net stop certsvc**
   - **net start certsvc**

2. 발급 CA에서 인증 기관 스냅인을 사용하여 인증서 템플릿을 게시합니다.
   **인증서 템플릿** 노드를 선택하고 **작업** > **새로 만들기** > **발급할 인증서 템플릿**을 클릭한 다음, 2단계에서 만든 템플릿을 선택합니다.

3. **인증서 템플릿** 폴더에서 게시된 템플릿을 확인하여 유효성을 검사합니다.

#### <a name="step-3---configure-prerequisites-on-the-ndes-server"></a>3단계 - NDES 서버에서 필수 구성 요소 구성
이 단계에서는 다음을 수행합니다.

- Windows Server에 NDES를 추가하고 NDES를 지원하도록 IIS 구성
- IIS_IUSR 그룹에 NDES 서비스 계정 추가
- NDES 서비스 계정의 SPN 설정

1. NDES를 호스트하는 서버에서 **엔터프라이즈 관리자**로 로그인한 다음, [역할 및 기능 추가 마법사](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831809(v=ws.11))를 사용하여 NDES를 설치합니다.

   1. 마법사에서 **Active Directory 인증서 서비스** 를 선택하여 AD CS 역할 서비스에 대한 액세스 권한을 받습니다. **네트워크 장치 등록 서비스**를 선택하고 **인증 기관**선택을 취소한 다음 마법사를 완료합니다.

      > [!TIP]
      > **설치 진행률**에서 **닫기**를 선택하지 않습니다. 대신 **대상 서버에서 Active Directory 인증서 서비스 구성** 링크를 선택하세요. 다음 단계에 사용할 **AD CS 구성** 마법사가 열립니다. AD CS 구성이 열리면 역할 및 기능 추가 마법사를 닫을 수 있습니다.

   2. NDES를 서버에 추가할 때는 마법사에서 IIS도 설치합니다. IIS에서 다음과 같은 구성을 사용하는지 확인합니다.

   3. **웹 서버** > **보안** > **요청 필터링**

   4. **웹 서버** > **응용 프로그램 개발** > **ASP.NET 3.5**. ASP.NET 3.5를 설치하면 .NET Framework 3.5가 설치됩니다. .NET Framework 3.5를 설치할 때는 핵심 **.NET Framework 3.5** 기능과 **HTTP 활성화**를 모두 설치합니다.

   5. **웹 서버** > **응용 프로그램 개발** > **ASP.NET 4.5**. ASP.NET 4.5를 설치하면 .NET Framework 4.5가 설치됩니다. .NET Framework 4.5를 설치할 때는 핵심 **.NET Framework 4.5** 기능, **ASP.NET 4.5** 및 **WCF 서비스** > **HTTP 활성화** 기능을 설치합니다.

   6. **관리 도구** > **IIS 6 관리 호환성** > **IIS 6 메타베이스 호환성**

   7. **관리 도구** > **IIS 6 관리 호환성** > **IIS 6 WMI 호환성**

   8. 서버에서 NDES 서비스 계정을 **IIS_IUSR** 그룹의 구성원으로 추가합니다.

2. 관리자 권한 명령 프롬프트에서 다음 명령을 실행하여 NDES 서비스 계정의 SPN을 설정합니다.

    `setspn -s http/<DNS name of NDES Server> <Domain name>\<NDES Service account name>`

    예를 들어 NDES 서버의 이름은 **Server01**, 도메인 이름은 **Contoso.com**, 서비스 계정 이름은 **NDESService**이면 다음 명령을 실행합니다.

    `setspn –s http/Server01.contoso.com contoso\NDESService`

#### <a name="step-4---configure-ndes-for-use-with-intune"></a>4단계 - Intune에 사용할 수 있도록 NDES 구성
이 단계에서는 다음을 수행합니다.

- 발급 CA에 사용할 수 있도록 NDES 구성
- IIS에서 서버 인증(SSL) 인증서 바인딩
- IIS에서 요청 필터링 구성

1. NDES 서버에서 AD CS 구성 마법사를 연 다음, 다음과 같이 업데이트합니다.

    > [!TIP]
    > 이전 단계에서 링크를 클릭했으면 이 마법사가 이미 열려 있습니다. 링크를 클릭하지 않은 경우에는 서버 관리자를 열어 Active Directory 인증서 서비스의 배포 후 구성에 액세스합니다.

   - **역할 서비스**에서 **네트워크 장치 등록 서비스**를 선택합니다.
   - **NDES의 서비스 계정**에서 NDES 서비스 계정을 입력합니다.
   - **NDES를 위한 CA**에서 **선택**을 클릭한 다음, 인증서 템플릿을 구성한 발급 CA를 선택합니다.
   - **NDES의 암호화**에서 회사 요구 사항에 맞는 키 길이를 설정합니다.
   - **확인**에서 **구성**을 선택하여 마법사를 완료합니다.

2. 마법사를 완료한 후 NDES 서버에서 다음 레지스트리 키를 업데이트합니다.

    `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP\`

    이 키를 업데이트하려면 인증서 템플릿의 **목적**을 확인합니다(**요청 처리** 탭에서 찾을 수 있음). 그런 다음, 기존 데이터를 2단계에서 지정한 인증서 템플릿의 이름(템플릿의 표시 이름이 아님)으로 바꾸어 해당 레지스트리 항목을 업데이트합니다. 다음 표는 인증서 템플릿 목적을 레지스트리의 값에 매핑합니다.

    |요청 처리 탭에 나와 있는 인증서 템플릿 용도|편집할 레지스트리 값|SCEP 프로필의 Intune 관리 콘솔에 표시되는 값|
    |---|---|---|
    |서명|SignatureTemplate|디지털 서명|
    |암호화|EncryptionTemplate|키 암호화|
    |서명 및 암호화|GeneralPurposeTemplate|키 암호화<br/>디지털 서명|

    예를 들어 인증서 템플릿의 용도가 **암호화**이면 **EncryptionTemplate** 값을 편집하여 인증서 템플릿의 이름으로 설정합니다.

3. NDES 서버가 긴 URL(쿼리)을 수신하며, 다음과 같은 두 개의 레지스트리 항목을 추가해야 합니다.


   |                        위치                        |      값      | 유형  |      Data       |
   |--------------------------------------------------------|-----------------|-------|-----------------|
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxFieldLength  | DWORD | 65534(10진수) |
   | HKLM\SYSTEM\CurrentControlSet\Services\HTTP\Parameters | MaxRequestBytes | DWORD | 65534(10진수) |

4. IIS 관리자에서 **기본 웹 사이트** > **요청 필터링** > **기능 설정 편집**을 선택합니다. 다음과 같이 **최대 URL 길이** 및 **최대 쿼리 문자열**을 *65534*로 변경합니다.

    ![IIS 최대 URL 및 쿼리 길이](./media/SCEP_IIS_max_URL.png)

5. 서버를 다시 시작합니다. 서버에서 **iisreset**을 실행하는 것으로 이러한 변경을 마무리하지는 못합니다.
6. 을 찾아봅니다 `http://*FQDN*/certsrv/mscep/mscep.dll` . 다음과 유사한 NDES 페이지가 표시됩니다.

    ![NDES 테스트](./media/SCEP_NDES_URL.png)

    **503 서비스를 사용할 수 없음** 오류가 발생하는 경우 이벤트 뷰어를 확인합니다. 응용 프로그램 풀이 NDES 사용자 권한에 대한 누락으로 인해 중지되었을 가능성이 높습니다. 이러한 권한은 1단계에 설명되어 있습니다.

##### <a name="install-and-bind-certificates-on-the-ndes-server"></a>NDES 서버에서 인증서를 설치 및 바인딩

1. NDES 서버에서 내부 CA 또는 공용 CA로부터 **서버 인증** 인증서를 요청하여 설치합니다. 그런 다음 IIS에서 SSL 인증서를 바인딩합니다.

    > [!TIP]
    > IIS에서 SSL 인증서를 바인딩한 후 클라이언트 인증 인증서를 설치합니다. 이 인증서는 NDES 서버에서 신뢰하는 모든 CA가 발급할 수 있습니다. 가장 적절한 방식은 아니지만 서버 및 클라이언트 인증에 같은 인증서를 사용할 수도 있습니다. 하지만 이 경우 인증서에 서버 인증과 클라이언트 인증 둘 다를 위한 EKU(확장된 키 사용) 기능이 있어야 합니다. 이러한 인증 인증서에 대한 자세한 내용을 보려면 다음 단계를 검토하세요.

   1. 서버 인증 인증서를 얻은 후 **IIS 관리자**를 열고 **기본 웹 사이트**를 선택합니다. **작업** 창에서 **바인딩**을 선택합니다.

   2. **추가**를 선택하고 **유형**을 **https**로 설정한 다음, 포트가 **443**인지 확인합니다. 독립 실행형 Intune에는 포트 443만 지원됩니다.

   3. **SSL 인증서**의 경우 서버 인증 인증서를 입력합니다.

      > [!NOTE]
      > NDES 서버가 단일 네트워크 주소에 대해 외부 및 내부 이름을 사용하는 경우 서버 인증 인증서에는 다음이 있어야 합니다.
      > - 외부 공용 서버 이름이 포함된 **주체 이름**
      > - 내부 서버 이름을 포함하는 **주체 대체 이름**

2. NDES 서버에서 내부 CA 또는 공용 인증 기관으로부터 **클라이언트 인증** 인증서를 요청하여 설치합니다. 인증서가 두 기능을 모두 포함하는 경우 서버 인증 인증서와 같은 인증서를 사용할 수 있습니다.

    클라이언트 인증 인증서는 다음 속성을 포함해야 합니다.

    - **확장된 키 사용**: 이 값에는 **클라이언트 인증**이 포함되어야 합니다.

    - **주체 이름**: 이 값은 인증서가 설치되는 서버의 DNS 이름(NDES 서버)과 같아야 합니다.

##### <a name="configure-iis-request-filtering"></a>IIS 요청 필터링 구성

1. NDES 서버에서 **IIS 관리자**를 열고 **연결** 창에서 **기본 웹 사이트**를 선택한 다음, **요청 필터링**을 엽니다.

2. **기능 설정 편집**을 선택한 다음, 값을 설정합니다.

    - **쿼리 문자열(바이트)** = **65534**
    - **최대 URL 길이(바이트)** = **65534**

3. 다음 레지스트리 키를 검토합니다.

    `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\HTTP\Parameters`

    다음 값이 DWORD 항목으로 설정되어 있는지 확인합니다.

    - 이름: **MaxFieldLength**, 십진수 값 **65534**
    - 이름: **MaxRequestBytes**, 십진수 값 **65534**

4. NDES 서버를 다시 부팅합니다. 이제 서버가 인증서 커넥터를 지원할 수 있습니다.

#### <a name="step-5---enable-install-and-configure-the-intune-certificate-connector"></a>5단계 - Intune 인증서 커넥터 사용, 설치 및 구성
이 단계에서는 다음을 수행합니다.

- Intune에서 NDES를 지원하도록 설정
- 해당 환경의 서버인 NDES(Network Device Enrollment Service) 역할을 호스트하는 서버에서 인증서 커넥터를 다운로드, 설치 및 구성합니다. 조직에서 NDES 구현의 규모를 확대하려면 각 NDES 서버에 Microsoft Intune 인증서 커넥터가 있는 여러 NDES 서버를 설치할 수 있습니다.

##### <a name="download-install-and-configure-the-certificate-connector"></a>인증서 커넥터의 다운로드, 설치 및 구성

![ConnectorDownload](./media/certificates-download-connector.png)

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성**을 선택한 다음, **인증 기관**을 선택합니다.
4. **추가**를 선택하고 **커넥터 파일을 다운로드**합니다. 설치할 서버에서 액세스할 수 있는 위치에 다운로드를 저장합니다.
5. 다운로드가 완료되면 NDES(네트워크 장치 등록 서비스) 역할을 호스트하는 서버로 이동합니다. 그런 다음:

    1. NDES 인증서 커넥터에 필요하므로 .NET 4.5 Framework가 설치되어 있는지 확인합니다. .NET 4.5 Framework는 Windows Server 2012 R2 및 최신 버전에 자동으로 포함됩니다.
    2. 설치 관리자(**NDESConnectorSetup.exe**)를 실행합니다. 설치 관리자가 NDES에 대한 정책 모듈 및 CRP 웹 서비스도 설치합니다. CRP 웹 서비스 CertificateRegistrationSvc는 IIS에서 응용 프로그램으로 실행됩니다.

    > [!NOTE]
    > 독립 실행형 Intune에 NDES를 설치하면 CRP 서비스가 인증서 커넥터와 함께 자동으로 설치됩니다. 구성 관리자와 함께 Intune을 사용할 때는 별도의 사이트 시스템 역할로 인증서 등록 지점을 설치합니다.

6. 인증서 커넥터용 클라이언트 인증서를 선택하라는 메시지가 표시되면 **선택**을 선택하고 4단계에서 NDES 서버에 설치한 **클라이언트 인증** 인증서를 선택합니다.

    클라이언트 인증 인증서를 선택하고 나면 **Microsoft Intune 인증서 커넥터용 클라이언트 인증서** 화면으로 돌아가게 됩니다. 선택한 인증서는 표시되지 않지만 **다음**을 선택하면 해당 인증서의 속성을 볼 수 있습니다. **다음**을 선택한 다음, **설치**를 선택합니다.

    > [!IMPORTANT]
    > Internet Explorer 보안 강화 구성이 사용되는 장치에는 Intune Certificate Connector를 등록할 수 없습니다. Intune Certificate Connector를 사용하려면 [IE 보안 강화 구성을 사용하지 않도록 설정](https://technet.microsoft.com/library/cc775800(v=WS.10).aspx)합니다.

7. 마법사를 완료한 후 마법사를 닫기 전에 **인증서 커넥터 UI를 시작**합니다.

    > [!TIP]
    > 인증서 커넥터 UI를 시작하기 전에 마법사를 닫은 경우에는 다음 명령을 실행하여 마법사를 다시 열 수 있습니다.
    >
    > <install_Path>\NDESConnectorUI\NDESConnectorUI.exe

8. **인증서 커넥터** UI에서:

    **로그인**을 선택하고 Intune 서비스 관리자 자격 증명 또는 전역 관리 권한이 있는 테넌트 관리자의 인증서 자격 증명을 입력합니다.

    > [!IMPORTANT]
    > 사용자 계정에 유효한 Intune 라이선스가 할당되어야 합니다. 사용자 계정에 유효한 Intune 라이선스가 없으면 NDESConnectorUI.exe가 실패합니다.

    조직에서 프록시 서버를 사용하며 NDES 서버에서 인터넷에 액세스하는 데 프록시가 필요한 경우 **프록시 서버 사용**을 선택한 다음, 프록시 서버 이름, 포트 및 계정 자격 증명을 입력하여 연결합니다.

    **고급** 탭을 선택한 다음, 발급 인증 기관에 대한 **인증서 발급 및 관리** 권한이 있는 계정의 자격 증명을 입력합니다. 변경 내용을 **적용**합니다.

    이제 인증서 커넥터 UI를 닫아도 됩니다.

9. 명령 프롬프트를 열고, **services.msc**를 입력한 다음, **Enter**를 입력합니다. **Intune 커넥터 서비스**를 마우스 오른쪽 단추로 클릭하고 **다시 시작**을 선택합니다.

서비스가 실행되고 있는지 확인하려면 브라우저를 열고 다음 URL을 입력합니다. 그러면 **403** 오류가 반환됩니다.

`http://<FQDN_of_your_NDES_server>/certsrv/mscep/mscep.dll`

> [!NOTE]
> TLS 1.2 지원은 NDES 인증서 커넥터에 포함되어 있습니다. 따라서 NDES 인증서 커넥터가 설치된 서버가 TLS 1.2를 지원하는 경우 TLS 1.2가 사용됩니다. 서버가 TLS 1.2를 지원하지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 장치와 서버 간 인증에 사용됩니다.

## <a name="create-a-scep-certificate-profile"></a>SCEP 인증서 프로필 만들기

1. Azure Portal에서 Microsoft Intune을 엽니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. SCEP 인증서 프로필에 대한 **이름** 및 **설명**을 입력합니다.
4. **플랫폼** 드롭다운 목록에서 이 SCEP 인증서에 대한 장치 플랫폼을 선택합니다. 현재, 장치 제한 설정에 대해 다음 플랫폼 중 하나를 선택할 수 있습니다.
   - **OWA(Outlook Web Access)**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 이상**
   - **Windows 10 이상**
5. **프로필** 유형 드롭다운 목록에서 **SCEP 인증서**를 선택합니다.
6. **SCEP 인증서** 창에서 다음 설정을 구성합니다.

   - **인증서 유효 기간**: 발급 CA에 대해 사용자 지정 유효 기간을 허용하는 `certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE` 명령을 실행한 경우 인증서가 만료될 때까지 남은 기간을 입력할 수 있습니다.<br>인증서 템플릿에서 유효 기간보다 작은 값은 입력할 수 있지만 높은 값은 입력할 수 없습니다. 예를 들어 인증서 템플릿의 인증서 유효 기간이 2년이면 값을 1년으로 입력할 수는 있어도 5년으로는 입력할 수 없습니다. 또한 이 값은 발급 CA 인증서의 남은 유효 기간보다 작아야 합니다. 
   - **KSP(키 저장소 공급자)**(Windows Phone 8.1, Windows 8.1, Windows 10): 인증서의 키가 저장될 위치를 입력합니다. 다음 값 중 하나를 선택합니다.
     - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈) KSP에 등록, 그렇지 않으면 소프트웨어 KSP에 등록**
     - **TPM(신뢰할 수 있는 플랫폼 모듈) KSP에 등록, 그러지 않으면 실패**
     - **Passport에 등록, 그러지 않으면 실패(Windows 10 이상)**
     - **소프트웨어 KSP에 등록**

   - **주체 이름 형식**: 인증서 요청 시 Intune에서 자동으로 주체 이름을 만드는 방식을 목록에서 선택합니다. 사용자용 인증서인 경우 주체 이름에 사용자의 전자 메일 주소를 포함할 수도 있습니다. 다음 중에서 선택합니다.
     - **구성되지 않음**
     - **일반 이름**
     - **메일이 포함된 일반 이름**
     - **메일인 일반 이름**
     - **IMEI(International Mobile Equipment Identity)**
     - **일련 번호**
     - **사용자 지정**: 이 옵션을 선택하면 다른 드롭다운 필드가 표시됩니다. 이 필드를 사용하여 사용자 지정 주체 이름 형식을 입력합니다. 사용자 지정 형식은 **CN(일반 이름)** 및 **E(이메일)** 의 두 가지 변수를 지원합니다. **CN(일반 이름)** 은 다음 변수 중 하나로 설정할 수 있습니다.
       - **CN={{UserName}}**: 사용자의 사용자 계정 이름입니다(예: janedoe@contoso.com).
       - **CN={{AAD_Device_ID}}**: Azure AD(Active Directory)에서 장치를 등록하는 경우 할당된 ID입니다. 이 ID는 일반적으로 Azure AD로 인증하는 데 사용됩니다.
       - **CN={{SERIALNUMBER}}**: 일반적으로 장치를 식별하는 제조업체에서 사용되는 고유한 SN(일련 번호)입니다.
       - **CN={{IMEINumber}}**: 휴대폰을 식별하는 데 사용되는 IMEI(International Mobile Equipment Identity) 고유 번호입니다.
       - **CN={{OnPrem_Distinguished_Name}}**: 쉼표로 구분된 상대 고유 이름의 시퀀스입니다(예: `CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com`).

          `{{OnPrem_Distinguished_Name}}` 변수를 사용하려면 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용하는 `onpremisesdistingishedname` 사용자 특성을 Azure AD와 동기화해야 합니다.

       - **CN={{onPremisesSamAccountName}}**: 관리자는 Azure AD Connect를 사용하여 Azure AD에 대한 Active Directory의 samAccountName 특성을 `onPremisesSamAccountName` 특성으로 동기화할 수 있습니다. Intune에서는 해당 변수를 SCEP 인증서의 제목에 있는 인증 발급 요청의 일부로 대체할 수 있습니다.  samAccountName 특성은 이전 버전의 Windows(Windows 2000 이전)에서 클라이언트 및 서버를 지원하는 데 사용되는 사용자 로그온 이름입니다. 사용자 로그온 이름 형식은 `DomainName\testUser`이거나 `testUser`만 사용합니다.

          `{{onPremisesSamAccountName}}` 변수를 사용하려면 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용하는 `onPremisesSamAccountName` 사용자 특성을 Azure AD와 동기화해야 합니다.

       이러한 변수와 정적 문자열을 하나 또는 여러 개 조합으로 사용하는 경우 사용자 지정 주체 이름 형식을 만들 수 있습니다(예: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**). <br/> 이 예에서는 CN 및 E 변수 외에 조직 구성 단위, 조직, 위치, 상태 및 국가 값에 해당하는 문자열을 사용하는 주체 이름 형식을 만들었습니다. [CertStrToName 함수](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx)에서는 이 함수와 지원되는 문자열을 보여 줍니다.

- **주체 대체 이름**: Intune에서 인증서 요청의 SAN(주체 대체 이름) 값을 자동으로 만드는 방법을 입력합니다. 예를 들어 사용자 인증서 유형을 선택한 경우 주체 대체 이름에 UPN(사용자 계정 이름)을 포함할 수 있습니다. 클라이언트 인증서가 네트워크 정책 서버에 대한 인증에 사용되는 경우 주체 대체 이름을 UPN으로 설정해야 합니다.
- **키 사용**: 인증서에 대한 키 사용 옵션을 입력합니다. 옵션은 다음과 같습니다.
  - **키 암호화**: 키가 암호화된 경우에만 키 교환을 허용합니다.
  - **디지털 서명**: 디지털 서명으로 키를 보호하는 경우에만 키 교환을 허용합니다.
- **키 크기(비트)**: 키에 포함된 비트 수를 선택합니다.
- **해시 알고리즘**(Android, Windows Phone 8.1, Windows 8.1, Windows 10): 이 인증서와 함께 사용할 수 있는 해시 알고리즘 유형 중 하나를 선택합니다. 연결 장치에서 지원되는 가장 강력한 보안 수준을 선택합니다.
- **루트 인증서**: 이전에 구성하고 사용자 또는 장치에 할당한 루트 CA 인증서 프로필을 선택합니다. 이 CA 인증서는 이 인증서 프로필에서 구성하려는 인증서를 발급할 CA에 대한 루트 인증서여야 합니다.
- **확장 키 사용**: 인증서의 용도에 대한 값을 **추가**합니다. 대부분의 경우 인증서는 사용자 또는 장치가 서버에 인증할 수 있도록 **클라이언트 인증**이 필요합니다. 그러나 필요에 따라 다른 키 사용을 추가할 수 있습니다.
- **등록 설정**
  - **갱신 임계값(%)**: 장치에서 인증서 갱신을 요청하기 전까지 남은 인증서 수명을 백분율로 입력합니다.
  - **SCEP 서버 URL**: SCEP를 통해 인증서를 발급하는 NDES 서버의 URL을 하나 이상 입력합니다.
  - **확인**, 프로필 **만들기**를 차례로 선택합니다.

프로필이 만들어지고 프로필 목록 창에 표시됩니다.

## <a name="assign-the-certificate-profile"></a>인증서 프로필 할당

인증서 프로필을 그룹에 할당하기 전에 다음 사항을 고려합니다.

- 인증서 프로필을 그룹에 할당할 때는 신뢰할 수 있는 CA 인증서 프로필의 인증서 파일이 장치에 설치됩니다. 장치는 SCEP 인증서 프로필을 사용하여 장치의 인증서 요청을 만듭니다.
- 인증서 프로필은 프로필을 만들 때 사용하는 플랫폼을 실행 중인 장치에만 설치됩니다.
- 사용자 컬렉션 또는 장치 컬렉션에 인증서 프로필을 할당할 수 있습니다.
- 장치를 등록한 후 인증서를 장치에 빠르게 게시하려면 인증서 프로필을 장치 그룹이 아닌 사용자 그룹에 할당합니다. 장치 그룹에 프로필을 할당하는 경우에는 장치에서 정책을 수신하기 전에 전체 장치 등록을 수행해야 합니다.
- 각 프로필을 별도로 할당하더라도 신뢰할 수 있는 루트 CA와, SCEP 또는 PKCS 프로필을 할당해야 합니다. 그렇지 않으면 SCEP 또는 PKCS 인증서 정책에서 오류가 발생합니다.

    > [!NOTE]
    > iOS의 경우 동일한 인증서 프로필을 사용하는 여러 리소스 프로필을 배포하는 경우 관리 프로필에 인증서의 여러 복사본이 표시됩니다.

프로필을 할당하는 방법에 대한 자세한 내용은 [장치 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="intune-connector-setup-verification-and-troubleshooting"></a>Intune Connector 설정 확인 및 문제 해결

문제를 해결하고 Intune Connector 설정을 확인하려면 [인증 기관 스크립트 샘플](https://aka.ms/intuneconnectorverificationscript)을 참조하세요.

## <a name="intune-connector-events-and-diagnostic-codes"></a>Intune Connector 이벤트 및 진단 코드

6.1806.x.x 버전부터 Intune Connector 서비스는 **이벤트 뷰어**(**응용 프로그램 및 서비스 로그** > **Microsoft Intune Connector**)에 이벤트를 기록합니다. 이러한 이벤트를 사용하여 Intune Connector 구성의 잠재적 문제를 해결할 수 있습니다. 이러한 이벤트는 작업의 성공과 실패를 기록하고, IT 관리자가 문제를 해결하는 데 도움이 되는 메시지와 함께 진단 코드를 포함합니다.

### <a name="event-ids-and-descriptions"></a>이벤트 ID 및 설명

> [!NOTE]
> 각 이벤트의 관련 진단 코드에 대한 자세한 내용은 이 문서의 **진단 코드** 표를 사용합니다.

| 이벤트 ID      | 이벤트 이름    | 이벤트 설명 | 관련 진단 코드 |
| ------------- | ------------- | -------------     | -------------            |
| 10010 | StartedConnectorService  | 커넥터 서비스를 시작했습니다. | 0x00000000, 0x0FFFFFFF |
| 10020 | StoppedConnectorService  | 커넥터 서비스를 중지했습니다. | 0x00000000, 0x0FFFFFFF |
| 10100 | CertificateRenewal_Success  | 커넥터 등록 인증서를 갱신했습니다. | 0x00000000, 0x0FFFFFFF |
| 10102 | CertificateRenewal_Failure  | 커넥터 등록 인증서를 갱신하지 못했습니다. 커넥터를 다시 설치하세요. | 0x00000000, 0x00000405, 0x0FFFFFFF |
| 10302 | RetrieveCertificate_Error  | 레지스트리에서 커넥터 등록 인증서를 검색하지 못했습니다. 이 이벤트와 관련된 인증서 지문에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x00000404, 0x0FFFFFFF |
| 10301 | RetrieveCertificate_Warning  | 이벤트 세부 정보에서 진단 정보를 확인합니다. | 0x00000000, 0x00000403, 0x0FFFFFFF |
| 20100 | PkcsCertIssue_Success  | PKCS 인증서를 발급했습니다. 이 이벤트와 관련된 장치 ID, 사용자 ID, CA 이름, 인증서 템플릿 이름 및 인증서 지문에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20102 | PkcsCertIssue_Failure  | PKCS 인증서를 발급하지 못했습니다. 이 이벤트와 관련된 장치 ID, 사용자 ID, CA 이름, 인증서 템플릿 이름 및 인증서 지문에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x00000400, 0x00000401, 0x0FFFFFFF |
| 20200 | RevokeCert_Success  | 인증서를 해지했습니다. 이 이벤트와 관련된 장치 ID, 사용자 ID, CA 이름 및 인증서 일련 번호에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20202 | RevokeCert_Failure | 인증서를 해지하지 못했습니다. 이 이벤트와 관련된 장치 ID, 사용자 ID, CA 이름 및 인증서 일련 번호에 대한 이벤트 세부 정보를 검토하세요. 자세한 내용은 NDES SVC 로그를 참조하세요.   | 0x00000000, 0x00000402, 0x0FFFFFFF |
| 20300 | Upload_Success | 인증서의 요청 또는 해지 데이터를 업로드했습니다. 업로드 세부 정보에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20302 | Upload_Failure | 인증서의 요청 또는 해지 데이터를 업로드하지 못했습니다. 이벤트 세부 정보 > 업로드 상태를 차례로 검토하여 실패 지점을 확인하세요.| 0x00000000, 0x0FFFFFFF |
| 20400 | Download_Success | 인증서 서명, 클라이언트 인증서 다운로드 또는 인증서 해지에 대한 요청을 다운로드했습니다. 다운로드 세부 정보에 대한 이벤트 세부 정보를 검토하세요.  | 0x00000000, 0x0FFFFFFF |
| 20402 | Download_Failure | 인증서 서명, 클라이언트 인증서 다운로드 또는 인증서 해지에 대한 요청을 다운로드하지 못했습니다. 다운로드 세부 정보에 대한 이벤트 세부 정보를 검토하세요. | 0x00000000, 0x0FFFFFFF |
| 20500 | CRPVerifyMetric_Success  | 인증서 등록 지점에서 클라이언트 요청을 확인했습니다. | 0x00000000, 0x0FFFFFFF |
| 20501 | CRPVerifyMetric_Warning  | 인증서 등록 지점에서 완료했지만 요청을 거부했습니다. 자세한 내용은 진단 코드 및 메시지를 참조하세요. | 0x00000000, 0x00000411, 0x0FFFFFFF |
| 20502 | CRPVerifyMetric_Failure  | 인증서 등록 지점에서 클라이언트 챌린지를 확인하지 못했습니다. 자세한 내용은 진단 코드 및 메시지를 참조하세요. 챌린지에 해당하는 장치 ID에 대한 이벤트 메시지 세부 정보를 참조하세요. | 0x00000000, 0x00000408, 0x00000409, 0x00000410, 0x0FFFFFFF |
| 20600 | CRPNotifyMetric_Success  | 인증서 등록 지점에서 알림 프로세스를 완료했고 인증서를 클라이언트 장치로 보냈습니다. | 0x00000000, 0x0FFFFFFF |
| 20602 | CRPNotifyMetric_Failure  | 인증서 등록 지점에서 알림 프로세스를 완료하지 못했습니다. 요청에 대한 내용은 이벤트 메시지 세부 정보를 참조하세요. NDES 서버와 CA 간의 연결을 확인하세요. | 0x00000000, 0x0FFFFFFF |

### <a name="diagnostic-codes"></a>진단 코드

| 진단 코드 | 진단 이름 | 진단 메시지 |
| -------------   | -------------   | -------------      |
| 0x00000000 | 성공  | 성공 |
| 0x00000400 | PKCS_Issue_CA_Unavailable  | 인증 기관이 유효하지 않거나 연결할 수 없습니다. 인증 기관을 사용할 수 있고 서버에서 이 인증 기관과 통신할 수 있는지 확인하세요. |
| 0x00000401 | Symantec_ClientAuthCertNotFound  | 로컬 인증서 저장소에 Symantec 클라이언트 인증 인증서가 없습니다. 자세한 내용은 [Symantec Registration Authorization 인증서 설치](https://docs.microsoft.com/intune/certificates-symantec-configure#install-the-symantec-registration-authorization-certificate) 문서를 참조하세요.  |
| 0x00000402 | RevokeCert_AccessDenied  | 지정한 계정에 CA에서 인증서를 해지할 수 있는 권한이 없습니다. 이벤트 메시지 세부 정보의 CA 이름 필드를 참조하여 발급하는 CA를 확인하세요.  |
| 0x00000403 | CertThumbprint_NotFound  | 사용자 입력과 일치하는 인증서를 찾을 수 없습니다. 인증서 커넥터를 등록하고 다시 시도하세요. |
| 0x00000404 | Certificate_NotFound  | 제공된 입력과 일치하는 인증서를 찾을 수 없습니다. 인증서 커넥터를 다시 등록하고 다시 시도하세요. |
| 0x00000405 | Certificate_Expired  | 인증서가 만료되었습니다. 인증서 커넥터를 다시 등록하여 인증서를 갱신하고 다시 시도하세요. |
| 0x00000408 | CRPSCEPCert_NotFound  | CRP 암호화 인증서를 찾을 수 없습니다. NDES 및 Intune Connector가 올바르게 설정되어 있는지 확인하세요. |
| 0x00000409 | CRPSCEPSigningCert_NotFound  | 서명 인증서를 검색할 수 없습니다. Intune Connector 서비스가 올바르게 구성되어 있고 Intune Connector 서비스가 실행되고 있는지 확인하세요. 또한 인증서 다운로드 이벤트가 성공했는지도 확인하세요. |
| 0x00000410 | CRPSCEPDeserialize_Failed  | SCEP 챌린지 요청을 역직렬화하지 못했습니다. NDES 및 Intune Connector가 올바르게 설정되어 있는지 확인하세요. |
| 0x00000411 | CRPSCEPChallenge_Expired  | 만료된 인증서 챌린지로 인해 요청이 거부되었습니다. 관리 서버에서 새 챌린지를 얻은 후에 클라이언트 장치에서 다시 시도할 수 있습니다. |
| 0x0FFFFFFFF | Unknown_Error  | 서버 쪽 오류가 발생하여 요청을 완료할 수 없습니다. 다시 시도하세요. |

## <a name="next-steps"></a>다음 단계

- [PKCS 인증서 사용](certficates-pfx-configure.md) 또는 [Symantec PKI 관리자 웹 서비스에서 PKCS 인증서 발급](certificates-symantec-configure.md)
- [Intune으로 SCEP를 사용하기 위해 타사 CA 추가](certificate-authority-add-scep-overview.md)
