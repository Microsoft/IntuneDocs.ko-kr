---
title: Microsoft Intune-Azure를 사용한 PKCS 인증서 사용 | Micrososft Docs
description: 루트 인증서 내보내기 단계, 인증서 템플릿 구성 단계, Microsoft Intune Certificate Connector(NDES) 다운로드 및 설치 단계, 장치를 구성 프로필 만들기 단계, Azure 및 인증 기관에서 PKCS 인증서 프로필 만들기 단계를 포함해 Microsoft Intune을 사용하여 공개 키 암호화 표준 인증서를 추가하거나 생성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 573cdf8746b9eaf593a33cd943b69a2dd83030ae
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391606"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Intune을 사용하여 PKCS 인증서 구성 및 사용

> [!IMPORTANT]
> 이 문서에서 설명하는 S/MIME 기능에 몇 가지 개선 사항을 적용하고 있습니다. 그 결과 Intune에서 S/MIME 기능이 일시적으로 제거되었습니다. 이 기능이 릴리스되면 본 메모를 제거하겠습니다.

인증서는 VPN 또는 WiFi 네트워크 같은 회사 리소스에 대한 액세스를 인증하고 보호합니다. 이 아티클에서는 PKCS 인증서를 내보낸 다음, 인증서를 Intune 프로필에 추가하는 방법을 설명합니다.

## <a name="requirements"></a>요구 사항

Intune에서 PKCS 인증서를 사용하려면 다음 인프라가 있어야 합니다.

- **Active Directory 도메인**: 이 섹션에 나열된 모든 서버는 Active Directory 도메인에 가입되어 있어야 합니다.

  AD DS 설치 및 구성에 대한 자세한 내용은 [AD DS 디자인 및 계획](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning)을 참조합니다.

- **인증 기관**(CA): 엔터프라이즈 CA(인증 기관)

  AD CS(Active Directory 인증서 서비스) 설치 및 구성에 대한 자세한 내용은 [Active Directory 인증서 서비스 단계별 가이드](https://technet.microsoft.com/library/cc772393)를 참조하세요.

  > [!WARNING]
  > Intune에서는 독립 실행형 CA가 아닌 엔터프라이즈 CA(인증 기관)를 사용하여 AD CS를 실행해야 합니다.

- **클라이언트**: 엔터프라이즈 CA에 연결하려면

- **루트 인증서**: 엔터프라이즈 CA에서 내보낸 루트 인증서 복사본

- **Microsoft Intune Certificate Connector**: Azure Portal을 사용하여 **인증서 커넥터** 설치 관리자(**NDESConnectorSetup.exe**)를 다운로드합니다. 

  커넥터는 인증 또는 S/MIME 이메일 서명에 사용되는 PKCS 인증서 요청을 처리합니다.

  NDES 인증서 커넥터는 FIPS(Federal Information Processing Standard) 모드도 지원합니다. FIPS가 필수는 아니지만 활성화되면 인증서를 발급하고 해지할 수 있습니다.

- **Microsoft Intune용 PFX 인증서 커넥터**: S/MIME 이메일 암호화를 사용하려는 경우 Azure Portal을 사용하여 **Microsoft Intune용 PFX 인증서 커넥터** 설치 관리자( **PfxCertificateConnectorBootstrapper.exe**)를 다운로드합니다. 커넥터는 특정 사용자에 대한 S/MIME 이메일 암호화를 위해 Intune에서 가져온 PFX 파일 요청을 처리합니다.

- **Windows Server**: 다음을 호스팅합니다.

  - 인증 및 S/MIME 이메일 서명 시나리오용 Microsoft Intune Certificate Connector(NDESConnectorSetup.exe)
  - S/MIME 이메일 암호화 시나리오를 위한 Microsoft Intune(PfxCertificateConnectorBootstrapper.exe)용 PFX 인증서 커넥터입니다.

  동일한 서버에서 두 커넥터(**Microsoft Intune Certificate Connector** 및 **Microsoft Intune용 PFX 인증서 커넥터**)를 둘 다 실행할 수 있습니다.

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>엔터프라이즈 CA에서 루트 인증서 내보내기

VPN, WiFi 또는 기타 리소스를 통해 인증하려면 각 장치에 루트 또는 중간 CA 인증서가 필요합니다. 다음 단계에서는 엔터프라이즈 CA에서 필요한 인증서를 가져오는 방법을 설명합니다.

1. 관리 권한이 있는 계정으로 엔터프라이즈 CA에 로그인합니다.
2. 관리자 권한으로 명령 프롬프트를 엽니다.
3. 루트 CA 인증서(.cer)를 나중에 액세스할 수 있는 위치로 내보냅니다.
4. 마법사를 완료한 후 마법사를 닫기 전에 **인증서 커넥터 UI 시작**을 클릭합니다.

   `certutil -ca.cert certnew.cer`

   자세한 내용은 [인증서 관리를 위한 Certutil 작업](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign)을 참조하세요.

## <a name="configure-certificate-templates-on-the-certification-authority"></a>인증 기관에서 인증서 템플릿 구성

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

6. **요청 처리**에서 **개인 키를 내보낼 수 있음**을 선택합니다.
7. **암호화**에서 **최소 키 크기**가 2048로 설정되었는지 확인합니다.
8. **주체 이름**에서 **요청에 따라 제공**을 선택합니다.
9. **확장**에서 **응용 프로그램 정책** 아래에 파일 시스템 암호화, 메일 보안 및 클라이언트 인증이 표시되는지 확인합니다.

    > [!IMPORTANT]
    > iOS 인증서 템플릿의 경우 **확장** 탭으로 이동해서 **키 사용**을 업데이트한 다음 **서명이 원본 증명임**이 선택되지 않은 것을 확인합니다.

10. **보안**에서 Microsoft Intune Certificate Connector를 설치할 서버의 컴퓨터 계정을 추가합니다. 이 계정에 **읽기** 및 **등록** 권한을 허용합니다.
11. **적용** > **확인**을 선택하여 인증서 템플릿을 저장합니다. **인증서 템플릿 콘솔**을 닫습니다.
12. **인증 기관** 콘솔에서 **인증서 템플릿**을 마우스 오른쪽 단추로 클릭하고  >  **새로 만들기** > **발급할 인증서 템플릿**을 선택합니다. 이전 단계에서 만든 템플릿을 선택합니다. **확인**을 선택합니다.
13. 서버에서 Intune 등록 장치 및 사용자를 대신하여 인증서를 관리하려면 다음 단계를 따릅니다.

    1. 인증 기관을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
    2. 보안 탭에서 커넥터(**Microsoft Intune Certificate Connector** 또는 **Microsoft Intune용 PFX 인증서 커넥터**)를 실행하는 서버의 컴퓨터 계정을 추가합니다. **인증서 발급 및 관리** 및 **인증서 요청** 허용 권한을 컴퓨터 계정에 부여합니다.

14. 엔터프라이즈 CA에서 로그아웃합니다.

## <a name="download-install-and-configure-the-certificate-connectors"></a>인증서 커넥터 다운로드, 설치 및 구성

### <a name="microsoft-intune-certificate-connector"></a>Microsoft Intune 인증서 커넥터

> [!IMPORTANT] 
> Microsoft Intune Certificate Connector를 별도의 Windows 서버에 **설치**해야 합니다. 발급 CA(인증 기관)에 설치할 수는 없습니다.

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **인증 기관** > **추가**를 선택합니다.
3. 커넥터 파일을 다운로드하여 저장합니다. 커넥터를 설치하려는 서버에서 액세스할 수 있는 위치에 저장합니다.

    ![ConnectorDownload][ConnectorDownload]

4. 다운로드가 완료되면 서버에 로그인합니다. 그런 다음:

    1. NDES 인증서 커넥터에 필요하므로 .NET 4.5 Framework 이상이 설치되어 있는지 확인합니다. .NET 4.5 Framework는 Windows Server 2012 R2 및 최신 버전에 자동으로 포함됩니다.
    2. 설치 프로그램(NDESConnectorSetup.exe)을 실행하고 기본 위치를 적용합니다. 커넥터를 `\Program Files\Microsoft Intune\NDESConnectorUI`에 설치합니다. 설치 관리자 옵션에서 **PFX 배포**를 선택합니다. 계속하여 설치를 완료합니다.
    3. 기본적으로 커넥터 서비스는 로컬 시스템 계정으로 실행됩니다. 인터넷 액세스를 위해 프록시가 필요한 경우 로컬 서비스 계정이 서버의 프록시 설정에 액세스할 수 있는지 확인합니다.

5. NDES 커넥터가 **등록** 탭을 엽니다. Intune에 대한 연결을 사용하려면 **로그인**하고 전역 관리자 권한이 있는 계정을 입력합니다.
6. **고급** 탭에서 **이 컴퓨터의 시스템 계정 사용(기본값)** 을 선택한 상태로 두는 것이 좋습니다.
7. **적용** > **닫기**
8. Azure Portal(**Intune** > **장치 구성** > **인증 기관**)로 돌아갑니다. 잠시 후에 녹색 확인 표시가 나타나고 **연결 상태**가 **활성화**됩니다. 커넥터 서버가 이제 Intune과 통신할 수 있습니다.

> [!NOTE]
> TLS 1.2 지원은 Microsoft Intune Certificate Connector에 포함되어 있습니다. 따라서 Microsoft Intune Certificate Connector가 설치된 서버가 TLS 1.2를 지원하는 경우 TLS 1.2가 사용됩니다. 서버가 TLS 1.2를 지원하지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 장치와 서버 간 인증에 사용됩니다.

### <a name="pfx-certificate-connector-for-microsoft-intune"></a>Microsoft Intune용 PFX 인증서 커넥터

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **인증 기관** > **추가** 선택
3. Microsoft Intune용 PFX Certificate Connector을 다운로드하여 저장합니다. 커넥터를 설치하려는 서버에서 액세스할 수 있는 위치에 저장합니다.
4. 다운로드가 완료되면 서버에 로그인합니다. 그런 다음:

    1. Microsoft Intune용 PFX 인증서 커넥터에 필요하므로 .NET 4.6 Framework 이상이 설치되어 있는지 확인합니다. .NET 4.6 Framework가 설치되어 있지 않으면 설치 관리자가 자동으로 설치합니다.
    2. 설치 관리자(PfxCertificateConnectorBootstrapper.exe)를 실행하고 기본 위치를 적용합니다. 커넥터를 `Program Files\Microsoft Intune\PFXCertificateConnector`에 설치합니다.
    3. 커넥터 서비스는 로컬 시스템 계정으로 실행됩니다. 인터넷 액세스를 위해 프록시가 필요한 경우 로컬 서비스 계정이 서버의 프록시 설정에 액세스할 수 있는지 확인합니다.

5. Microsoft Intune용 PFX 인증서 커넥터가 설치되면 **등록** 탭이 열립니다. Intune에 대한 연결을 사용하도록 설정하려면 **로그인**하고 Azure 글로벌 관리자 또는 Intune 관리자 권한이 있는 계정을 입력합니다.
6. 창을 닫습니다.
7. Azure Portal(**Intune** > **장치 구성** > **인증 기관**)로 돌아갑니다. 잠시 후에 녹색 확인 표시가 나타나고 **연결 상태**가 **활성화**됩니다. 커넥터 서버가 이제 Intune과 통신할 수 있습니다.

## <a name="create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**로 이동합니다.

   ![NavigateIntune][NavigateIntune]

2. 다음 속성을 입력합니다.

    - 프로필의 **이름**
    - 선택적으로 설명 설정
    - 프로필을 배포할 **플랫폼**
    - **프로필 형식**을 **신뢰할 수 있는 인증서**로 설정

3. **설정**으로 이동하여 이전에 내보낸 .cer 파일 루트 CA 인증서를 입력합니다.

   > [!NOTE]
   > **3단계**에서 선택한 플랫폼에 따라 인증서의 **대상 저장소**를 선택하는 옵션이 제공되거나 제공되지 않을 수 있습니다.

   ![ProfileSettings][ProfileSettings]

4. **확인** > **만들기**를 선택하여 프로필을 저장합니다.
5. 하나 이상의 장치에 새 프로필을 할당하려면 [Microsoft Intune 장치 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 인증서 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**로 이동합니다.
2. 다음 속성을 입력합니다.

    - 프로필의 **이름**
    - 선택적으로 설명 설정
    - 프로필을 배포할 **플랫폼**
    - **프로필 형식**을 **PKCS 인증서**로 설정

3. **설정**으로 이동해 다음 속성을 입력합니다.

    - **갱신 임계값(%)**: 권장 값은 20%입니다.
    - **인증서 유효 기간**: 인증서 템플릿을 변경하지 않은 경우 이 옵션은 1년으로 설정될 수 있습니다.
    - **KSP(키 저장소 공급자)**: Windows의 경우 장치에서 키를 저장할 위치를 선택합니다.
    - **인증 기관**: 엔터프라이즈 CA의 내부 FQDN(정규화된 도메인 이름)을 배포합니다.
    - **인증 기관 이름**: "Contoso 인증 기관"과 같은 엔터프라이즈 CA의 이름을 나열합니다.
    - **인증서 템플릿 이름**: 이전에 생성된 템플릿의 이름입니다. 기본적으로 **템플릿 이름**은 *공백 없이* **템플릿 표시 이름**과 동일합니다.
    - **주체 이름 형식**: 별도로 필요한 경우가 아니면 이 옵션을 **일반 이름**으로 설정합니다.
    - **주체 대체 이름**: 별도로 필요한 경우가 아니면 이 옵션을 **UPN(사용자 계정 이름)** 으로 설정합니다.

4. **확인** > **만들기**를 선택하여 프로필을 저장합니다.
5. 하나 이상의 장치에 새 프로필을 할당하려면 [Microsoft Intune 장치 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="create-a-pkcs-imported-certificate-profile"></a>PKCS가 가져온 인증서 프로필 만들기

특정 사용자에 대해 이전에 발급된 인증서를 모든 인증 기관에서 Intune으로 가져올 수 있습니다. 가져온 인증서는 사용자가 등록하는 각 장치에 설치됩니다. S/MIME 이메일 암호화는 기존 PFX 인증서를 Intune에 가져오는 가장 일반적인 시나리오입니다. 사용자는 이메일을 암호화하기 위한 여러 개의 인증서를 가질 수 있습니다. 이러한 인증서의 개인 키는 이전에 암호화된 이메일을 해독할 수 있도록 모든 사용자의 장치에 있어야 합니다.

인증서를 Intune에 가져오려면 [GitHub에서 제공하는 PowerShell cmdlet](https://github.com/Microsoft/Intune-Resource-Access)을 사용하면 됩니다.

Intune으로 인증서를 가져온 후 **PKCS가 가져온 인증서** 프로필을 생성하여 Azure Active Directory 그룹에 할당합니다.

1. [Azure Portal](https://portal.azure.com)에서 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**로 이동합니다.
2. 다음 속성을 입력합니다.

    - 프로필의 **이름**
    - 선택적으로 설명 설정
    - 프로필을 배포할 **플랫폼**
    - **프로필 형식**을 **PKCS가 가져온 인증서**로 설정

3. **설정**으로 이동해 다음 속성을 입력합니다.

    - **용도**: 이 프로필에 가져온 인증서의 용도. 관리자는 다양한 용도(예: 인증, S/MIME 서명 또는 S/MIME 암호화)로 인증서를 가져올 수 있습니다. 인증서 프로필에서 선택한 용도는 인증서 프로필과 가져온 인증서를 올바르게 일치시킵니다.
    - **인증서 유효 기간**: 인증서 템플릿을 변경하지 않은 경우 이 옵션은 1년으로 설정될 수 있습니다.
    - **KSP(키 저장소 공급자)**: Windows의 경우 장치에서 키를 저장할 위치를 선택합니다.

4. **확인** > **만들기**를 선택하여 프로필을 저장합니다.
5. 하나 이상의 장치에 새 프로필을 할당하려면 [Microsoft Intune 장치 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계
[SCEP 인증서를 사용](certificates-scep-configure.md)하거나 [Symantec PKI 관리자 웹 서비스에서 PKCS 인증서를 발급](certificates-symantec-configure.md)합니다.

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Azure Portal에서 Intune으로 이동하여 신뢰할 수 있는 인증서에 대한 새 프로필을 만듭니다."
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "프로필을 만들고 신뢰할 수 있는 인증서를 업로드합니다."
[ConnectorDownload]: ./media/certificates-download-connector.png "Azure Portal에서 인증서 커넥터 다운로드"  
