---
title: Microsoft Intune을 사용하여 Symantec PKCS 인증서 발급
titlesuffix: ''
description: Symantec PKI 관리자 웹 서비스에서 Intune으로 관리되는 장치에 대한 PKCS 인증서를 발급하려면 Intune Certificate Connector를 설치 및 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cf5146946fef464d2d74271e0ad801dabbdce13e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52186871"
---
# <a name="set-up-intune-certificate-connector-for-symantec-pki-manager-web-service"></a>Symantec PKI 관리자 웹 서비스에 대한 Intune Certificate Connector 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서에서는 Symantec PKI 관리자 웹 서비스에서 Intune으로 관리되는 장치에 대한 PKCS 인증서를 발급하려면 Intune Certificate Connector를 설치 및 구성하는 방법을 보여 줍니다.

이 문서에서는 Symantec PKI 관리자 웹 서비스를 Symantec CA라고 합니다. Microsoft CA(인증 기관)에서 PKCS 인증서와 SCEP 인증서를 발급하도록 이미 Intune Certificate Connector를 구성한 경우 동일한 Connector를 사용하여 PKCS 인증서를 구성하고 Symantec CA에서 발급할 수 있습니다. 이 경우 Intune Certificate Connector는 다음 인증서를 발급할 수 있습니다.

* Microsoft CA의 PKCS 인증서
* Microsoft CA의 SCEP 인증서
* Symantec CA의 PKCS 인증서

Microsoft CA 및 Symantec CA에 Intune Certificate Connector를 사용하려면 먼저 Microsoft CA에 대한 Intune Certificate Connector 구성을 완료한 후 아래 단계에 따라 Symantec CA에 대해 구성해야 합니다.  Microsoft CA에 대한 Intune Certificate Connector를 구성하는 방법에 대한 자세한 내용은 [Microsoft Intune에서 인증서를 구성하는 방법](certificates-configure.md)을 참조하세요.

## <a name="prepare-to-install-intune-certificate-connector"></a>Intune Certificate Connector 설치 준비

기존 Microsoft CA에 대해 Intune Certificate Connector를 이미 사용 중이고 Symantec CA 지원을 추가하려면 이 단계를 건너뛰고 Intune 관리 포털에서 최신 Intune Certificate Connector를 설치한 후 나머지 단계를 계속 진행합니다. 이 단계는 Symantec CA에만 Intune Certificate Connector를 사용하려는 경우에만 필요합니다.

1. 다음 목록에서 Windows 운영 체제 버전 중 하나를 선택하고 컴퓨터에 설치합니다.
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. 관리자 권한이 있는 사용자를 만들고 이를 사용하여 아래 단계를 완료합니다.

3. 최신 Windows 업데이트를 검색하여 사용 가능한 경우 설치합니다.

   > [!IMPORTANT]
   > Windows 업데이트를 설치한 후 컴퓨터를 다시 시작합니다.

4. .NET Framework 3.5를 설치합니다.

    a. **제어판** > **프로그램 및 기능**을 열고  > **Windows 기능을 켜거나 끕니다.**

    b. **.NET Framework 3.5**를 선택하고 설치합니다.

## <a name="install-the-symantec-registration-authorization-certificate"></a>Symantec Registration Authorization 인증서 설치

다음 단계에 따라 Symantec CA에서 RA(Registration Authorization) 인증서를 받습니다. RA 인증서를 받으려면 Symantec CA에 활성 구독이 있어야 합니다.

1. 다음 코드 조각을 **certreq.ini** 파일에 저장하고 필요에 따라 업데이트합니다(예: *CN 형식의 주체 이름*).

   ```
    [Version] 
    Signature="$Windows NT$" 

    [NewRequest] 
    ;Change to your,country code, company name and common name 
    Subject = "Subject Name in CN format"

    KeySpec = 1 
    KeyLength = 2048 
    Exportable = TRUE 
    MachineKeySet = TRUE 
    SMIME = False 
    PrivateKeyArchive = FALSE 
    UserProtected = FALSE 
    UseExistingKeySet = FALSE 
    ProviderName = "Microsoft RSA SChannel Cryptographic Provider" 
    ProviderType = 12 
    RequestType = PKCS10 
    KeyUsage = 0xa0 

    [EnhancedKeyUsageExtension] 
    OID=1.3.6.1.5.5.7.3.2 ; Client Authentication  // Uncomment if you need a mutual TLS authentication

    ;----------------------------------------------- 
   ```

2. 관리자 권한으로 명령 프롬프트를 열고 다음 명령을 사용하여 CSR 콘텐츠를 생성합니다.

   `Certreq.exe -new certreq.ini request.csr`

3. 메모장에서 request.csr 파일을 열고 다음 형식의 CSR 콘텐츠를 복사합니다.

    ```
    -----BEGIN NEW CERTIFICATE REQUEST-----
    MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
    …
    …
    fzpeAWo=
    -----END NEW CERTIFICATE REQUEST-----
    ```

4. Symantec CA에 로그온하고 작업에서 **Get an RA Cert**(RA 인증서 가져오기)로 이동합니다.

   a. 지정된 텍스트 상자에 3단계의 CSR 콘텐츠를 제공합니다.

   b. 지정된 텍스트 상자에 인증서 이름을 제공합니다.

   c. **Continue(계속)** 를 클릭합니다.

      RA 인증서에 대한 다운로드 가능한 링크가 표시됩니다.

   d. RA 인증서를 로컬 컴퓨터에 다운로드합니다.

5. RA 인증서를 Windows 인증서 저장소로 가져옵니다.

    a. MMC 콘솔을 엽니다.

    b. **파일** > **스냅인 추가/제거** > **인증서**를 클릭한 다음 **추가**를 클릭합니다.

    c. **컴퓨터 계정**을 선택하고 **다음**을 클릭합니다.

    d. **로컬 컴퓨터**를 선택하고 **마침**을 클릭합니다.

    e. **스냅인 추가/제거** 창에서 **확인**을 클릭합니다. **인증서(로컬 컴퓨터)** > **개인** > **인증서**를 확장합니다.

    f. **인증서** 노드를 마우스 오른쪽 단추로 클릭하고 **모든 작업** > **가져오기**를 선택합니다.

    g. Symantec CA에서 다운로드한 RA 인증서의 위치를 선택하고 **다음**을 클릭합니다.

    h. **개인 인증서 저장소**를 선택하고 **다음**을 클릭합니다.

    i. **마침**을 클릭합니다. 그러면 RA 인증서를 개인 키와 함께 로컬 컴퓨터-개인 저장소로 가져옵니다.  

6. 개인 키 인증서를 내보내고 가져옵니다.

    a. **인증서(로컬 컴퓨터)** > **개인** > **인증서**를 확장합니다.

    b. 이전 단계에서 가져온 인증서를 선택합니다.

    c. 인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업** > **내보내기**를 선택합니다.

    d. **다음**을 클릭하고 암호를 입력합니다.

    e. 내보낼 위치를 선택하고 **마침**을 클릭합니다.

    f. 5단계의 동일한 절차에 따라 개인 키 인증서를 로컬 컴퓨터-개인 저장소로 가져옵니다.

7. 공백 없이 RA 인증서 지문을 복사합니다.  다음은 지문의 예입니다.

   ```
   RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”
   ```


   > [!NOTE]
   > Symantec CA에서 RA 인증서를 받은 데 문제가 있는 경우 Symantec 고객 지원에 문의하세요.

## <a name="install-intune-certificate-connector"></a>Intune Certificate Connector 설치

기존 Microsoft CA에 대해 최신 Intune Certificate Connector를 이미 사용 중이고 Symantec CA 지원을 추가하려면 이 단계를 건너뜁니다. 이외의 경우에는 Intune 관리 포털에서 최신 Intune Certificate Connector를 다운로드하고 아래 지침을 따릅니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **장치 구성**을 선택합니다.
4. **장치 구성** 창에서 **인증 기관**을 선택합니다.
5. **추가**를 클릭하고 **커넥터 파일 다운로드**를 선택합니다. 설치할 서버에서 액세스할 수 있는 위치에 다운로드를 저장합니다. 
3. 관리자 권한으로 NDESConnectorSetup.exe를 실행합니다.

    a. **설치 옵션** 화면에서 다음 스크린샷에 표시된 대로 **PFX 배포**를 선택합니다.  기본 선택 사항을 사용하여 나머지 설정을 완료합니다.

   > [!IMPORTANT]
   > Microsoft CA 및 Symantec CA에서 인증서를 발급하도록 Intune Certificate Connector를 구성하려면 **SCEP 및 PFX 프로필 배포**를 선택합니다. 기본 선택 사항을 사용하여 나머지 설정을 완료합니다.

   ![InstallConnector][InstallConnector]
 
## <a name="configure-intune-certificate-connector"></a>Intune Certificate Connector 구성

Intune Certificate Connector는 기본적으로 `%ProgramFiles%\Microsoft Intune`에 설치됩니다.

1. 메모장에서 %ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config 파일을 엽니다.

    a. 이전 섹션에서 복사한 인증서 지문 값으로 RACertThumbprint 키 값을 업데이트합니다.  예를 들면 다음과 같습니다.

   ```
   <add key="RACertThumbprint"
   value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>
   ```

    b. 파일을 저장한 후 닫습니다.

2. services.msc를 엽니다.

    a. **Intune Connector 서비스**를 선택합니다.

    b. 서비스를 중지한 후 서비스를 시작합니다.

    c. 서비스 창을 닫습니다.

## <a name="setup-the-intune-administrator-account"></a>Intune 관리자 계정 설정

기존 Microsoft CA에 대해 Intune Certificate Connector를 이미 사용 중이고 Symantec CA 지원을 추가하려면 이 단계를 건너뛰고 나머지 단계를 계속 진행합니다. 

1. ` %ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe `에서 NDES Connector 사용자 인터페이스를 시작합니다.

    a. **등록** 탭을 클릭한 다음 **로그인**을 클릭합니다.

    b. 지정된 텍스트 상자에 Intune 테넌트 관리자 자격 증명을 제공합니다.

    c. **로그인**을 클릭합니다.  다음 스크린샷과 같이 **등록 성공** 메시지가 있는 확인 대화 상자가 표시됩니다.
2. NDES Connector 사용자 인터페이스를 닫습니다.

![ConfigureConnector][ConfigureConnector]
 
## <a name="create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필 만들기

Intune 관리 장치용으로 배포된 PKCS 인증서는 신뢰할 수 있는 루트 인증서와 연결되어야 합니다. 이렇게 하려면 Symantec CA에서 얻은 루트 인증서를 사용하여 Intune 신뢰할 수 있는 인증서 프로필을 만들어야 합니다.

1. Symantec CA에서 신뢰할 수 있는 루트 인증서를 가져옵니다.

    a. Symantec CA 관리 포털에 로그온합니다.

    b. 작업에서 [CA 관리]를 클릭합니다.

    c. CA 목록에서 적합한 CA를 선택합니다.

    d. [루트 인증서 다운로드]를 클릭하여 신뢰할 수 있는 루트 인증서를 다운로드합니다.

2. Intune 관리 포털에서 신뢰할 수 있는 인증서 프로필을 만듭니다.

    a. Intune 테넌트 관리자 자격 증명을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인하고 Intune 리소스를 검색합니다.

    b. **Microsoft Intune** > **장치 구성** > **프로필** > **프로필 만들기**에서 신뢰할 수 있는 인증서 프로필을 만듭니다.

    c. **이름** 및 **설명** 필드에 필수 정보를 제공한 다음 대상 플랫폼을 선택합니다. 

    d. [프로필 유형] 드롭다운 목록에서 신뢰할 수 있는 인증서 프로필을 선택합니다.

    e. 이전 단계에서 Symantec CA에서 받은 신뢰할 수 있는 루트 인증서를 업로드합니다.

    f. 프로필 만들기의 나머지 단계를 완료합니다. 

    g. **할당**을 클릭하고 해당하는 그룹을 선택합니다.  하나 이상의 사용자 또는 장치는 할당된 그룹의 일부여야 합니다.

## <a name="get-the-certificate-profile-oid"></a>인증서 프로필 OID 가져오기

인증서 프로필 OID는 Symantec CA의 인증서 프로필 템플릿과 연결됩니다.  Intune 관리 포털에서 PKCS 인증서 프로필을 만들려면 Symantec CA의 인증서 템플릿과 연결된 인증서 프로필 OID 형식으로 인증서 템플릿 이름을 제공해야 합니다.

1. Symantec CA 관리 포털에 로그인합니다.
2. [인증서 프로필 관리]를 클릭합니다.
3. 사용할 인증서 프로필을 선택합니다.
4. 인증서 프로필 OID를 복사합니다. 다음 예제와 같이 표시됩니다.

   ```
   Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 
   ```

   > [!NOTE]
   > 인증서 프로필 OID를 받는 데 문제가 있으면 Symantec 고객 지원에 문의하세요.

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 인증서 프로필 만들기

1. Intune 테넌트 관리자 자격 증명을 사용하여 [Azure Portal](https://portal.azure.com)에 로그인하고 Intune 리소스를 검색합니다.
2. **Microsoft Intune** > **장치 구성 > 프로필** > **프로필 만들기**에서 PKCS 인증서 프로필을 만듭니다.

    a. **이름** 및 **설명** 필드에 필수 정보를 입력한 다음 대상 플랫폼을 선택합니다.

    b. **프로필 유형** 드롭다운 목록에서 **PKCS 인증서 프로필**을 선택합니다.  

    c. 나머지 단계를 완료하여 프로필을 만듭니다.

   ![ConfigureProfile][ConfigureProfile]

   > [!IMPORTANT]
   > Symantec CA에서 Intune Certificate Connector를 통해 PKCS 인증서를 발급하려면 스크린샷에 표시된 대로 다음 표의 지정된 값을 사용하여 PKCS 인증서 프로필의 다음 매개 변수를 구성해야 합니다. 

    |PKCS 인증서 매개 변수 | 값 | 설명 |
    | --- | --- | --- |
    | 인증 기관 | pki-ws.symauth.com | 이 값은 후행 슬래시 없이 Symantec CA 기본 서비스 FQDN이어야 합니다.  이것이 Symantec CA 구독의 올바른 기본 서비스 FQDN인지 모르는 경우 Symantec 고객 지원에 문의하세요. <br><br> 이 FQDN이 잘못된 경우 Intune Certificate Connector는 Symantec CA에서 PKCS 인증서를 발급하지 않습니다.| 
    | 인증 기관 이름 | Symantec | 이 값은 **Symantec** 문자열이어야 합니다. <br><br> 이 값을 변경한 경우 Intune Certificate Connector는 Symantec CA에서 PKCS 인증서를 발급하지 않습니다.|
    | 인증서 템플릿 이름 | Symantec CA의 인증서 프로필 OID입니다. <br><br> 예: `2.16.840.1.113733.1.16.1.2.3.1.1.61904612`| 이 값은 Symantec CA 인증서 프로필 템플릿의 이전 섹션에서 얻은 인증서 프로필 OID여야 합니다. <br><br> Intune Certificate Connector가 Symantec CA에서 이 인증서 프로필 OID와 연결된 인증서 템플릿을 찾을 수 없는 경우 Symantec CA에서 PKCS 인증서를 발급하지 않습니다.|

   > [!NOTE]
   > Windows 플랫폼용 PKCS 인증서 프로필은 신뢰할 수 있는 인증서 프로필과 연결할 필요가 없습니다. 그러나 Android와 같은 Windows 이외의 플랫폼 프로필에는 필요합니다.

3. **할당**을 클릭하고 해당하는 그룹을 선택합니다.  하나 이상의 사용자 또는 장치는 할당된 그룹의 일부여야 합니다.
 
이전 단계를 완료한 후 Intune Certificate Connector는 Symantec CA에서 할당된 그룹의 Intune 관리 장치에 PKCS 인증서를 발급합니다. 이러한 인증서는 Intune 관리 장치에 있는 현재 사용자 인증서 저장소의 개인 저장소에서 사용할 수 있습니다.

### <a name="pkcs-certificate-profile-supported-attributes"></a>PKCS 인증서 프로필 지원 특성

|특성 | Intune 지원 형식 | Symantec Cloud CA 지원 형식 | 결과 |
| --- | --- | --- | --- |
| 주체 이름 |Intune은 다음 세 가지 형식으로만 주체 이름을 지원합니다. <br><br> 1. 일반 이름 <br> 2. 일반 이름에는 메일이 포함됨 <br> 3. 메일인 일반 이름 <br><br> 예를 들면 다음과 같습니다. <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | Symantec CA는 추가 특성을 지원합니다.  추가 특성을 선택하려면 Symantec 인증서 프로필 템플릿에서 고정 값으로 해당 특성을 정의해야 합니다.| PKCS 인증서 요청에서 일반 이름 또는 메일을 사용합니다. <br><br> Intune 인증서 프로필과 Symantec 인증서 프로필 템플릿 간의 특성 선택 사항이 일치하지 않으면 Symantec CA에서 인증서가 발급되지 않습니다.|
| SAN | Intune은 다음 SAN 필드 값만 지원합니다. <br><br> AltNameTypeEmail <br><br> AltNameTypeUpn <br><br> AltNameTypeOtherName(인코딩된 값) | Symantec Cloud CA는 이러한 매개 변수를 지원합니다. 추가 특성을 선택하려면 Symantec 인증서 프로필 템플릿에서 고정 값으로 해당 특성을 정의해야 합니다. <br><br> AltNameTypeEmail: 이 유형을 SAN에서 찾을 수 없으면 AltNameTypeUpn의 값을 사용합니다.  AltNameTypeUpn도 SAN에서 찾을 수 없으면 주체 이름의 값을 사용합니다(메일 형식인 경우).  그래도 찾을 수 없으면 Intune Certificate Connector가 인증서를 발급하지 못합니다. <br><br> 예: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> AltNameTypeUpn: 이 유형을 SAN에서 찾을 수 없으면 AltNameTypeEmail의 값을 사용합니다. AltNameTypeEmail도 SAN에서 찾을 수 없으면 주체 이름의 값을 사용합니다(메일 형식인 경우).  그래도 찾을 수 없으면 Intune Certificate Connector가 인증서를 발급하지 못합니다.  <br><br> 예: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> AltNameTypeOtherName: 이 유형을 SAN에서 찾을 수 없으면 Intune Certificate Connector가 인증서를 발급하지 못합니다. <br><br> 예: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  **중요 참고:** 이 필드의 값은 Symantec CA에서 인코딩된 형식(16진수 값)으로만 지원됩니다. 따라서 이 필드에 있는 값의 경우 Intune Certificate Connector는 인증서 요청을 제출하기 전에 base 64 인코딩된 값으로 변환합니다. **Intune Certificate Connector는 이 값이 이미 인코딩되었는지 여부를 확인하지 않습니다.** | 없음 |

## <a name="troubleshooting"></a>문제 해결

Intune Certificate Connector 서비스 로그는 NDES Connector 컴퓨터의 `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs`에서 사용할 수 있습니다. [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)에서 로그를 열고 예외 또는 오류 메시지를 검색합니다.

| 문제/오류 메시지 | 해결 단계 |
| --- | --- |
| NDES Connector UI에서 Intune 테넌트 관리자 계정으로 로그인할 수 없음 | 이 문제는 Intune 관리 포털에서 온-프레미스 인증서 커넥터가 활성화되지 않은 경우 발생할 수 있습니다. 이 문제를 해결하려면 다음 단계를 따르십시오. <br><br> SilverLight UI에서: <br> 1. [Intune 관리 포털](https://admin.manage.microsoft.com)에 로그온합니다. <br> 2. [관리]를 클릭합니다. <br> 3. [모바일 장치 관리] > [인증서 커넥터]를 선택합니다. <br> 4. **온-프레미스 인증서 커넥터 구성**을 클릭합니다. <br> 5. **인증서 커넥터 사용** 확인란을 선택합니다. <br> 6. **확인**을 클릭합니다. <br><br>또는 <br><br> Azure Portal UI에서: <br> 1. [Azure Portal](https://portal.azure.com)에 로그인합니다. <br> 2. Microsoft Intune으로 이동합니다. <br> 3. **장치 구성** > **인증 기관**을 선택합니다. <br> 4. **사용**을 클릭합니다. <br><br> SilverLight UI 또는 Azure Portal에서 이전 단계를 완료한 후 NDES Connector UI에서 동일한 Intune 테넌트 관리자 계정으로 로그인해 보세요. |
| NDES Connector 인증서를 찾을 수 없습니다. <br><br> System.ArgumentNullException: 값은 null일 수 없습니다. | Intune 테넌트 관리자 계정이 NDES Connector UI에 로그인한 적이 없는 경우 Intune Certificate Connector가 이 오류를 표시합니다. <br><br> 이 오류가 지속되면 Intune Service Connector를 다시 시작합니다. <br><br> 1. services.msc를 엽니다. <br> 2. **Intune Connector 서비스**를 선택합니다. <br> 3. 마우스 오른쪽 단추를 클릭하고 **다시 시작**을 선택합니다.|
| NDES Connector - IssuePfx-Generic 예외: <br> System.NullReferenceException: 개체 참조가 개체의 인스턴스로 설정되지 않았습니다. | 이 오류는 일시적입니다. Intune Service Connector를 다시 시작합니다. <br><br> 1. services.msc를 엽니다. <br> 2. **Intune Connector 서비스**를 선택합니다. <br> 3. 마우스 오른쪽 단추를 클릭하고 **다시 시작**을 선택합니다. |
| Symantec 공급자 - Symantec 정책 “작업 제한 시간이 초과됨”을 가져오지 못함 | Intune Certificate Connector가 Symantec CA와 통신하는 동안 작업 시간 초과 오류가 발생했습니다. 이 오류가 계속 발생하면 연결 제한 시간 값을 늘리고 다시 시도합니다. <br><br> 연결 제한 시간을 늘리려면: <br> 1. NDES Connector 컴퓨터로 이동합니다. <br>2. 메모장에서 `%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config` 파일을 엽니다. <br> 3. 다음 매개 변수의 제한 시간 값을 늘립니다. <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Intune Connector 서비스를 다시 시작합니다. <br><br> 문제가 계속되면 Symantec 고객 지원에 문의하세요. |
| Symantec 공급자 - 클라이언트 인증서를 가져오지 못함 | Intune Certificate Connector가 로컬 컴퓨터-개인 인증서 저장소에서 리소스 권한 부여 인증서를 검색하지 못했습니다. 이 문제를 해결하려면 로컬 컴퓨터-개인 인증서 저장소에 개인 키와 함께 리소스 권한 부여 인증서를 설치해야 합니다. <br><br> **참고:** Symantec CA에서 리소스 권한 부여 인증서를 받아야 합니다. 자세한 내용은 Symantec 고객 지원에 문의하세요. | 
| Symantec 공급자 - Symantec 정책 “요청이 중단됨: SSL/TLS 보안 채널을 만들 수 없음”을 가져오지 못함 | 이 오류는 다음과 같은 경우에 발생합니다. <br><br> 1. Intune Certificate Connector 서비스에는 로컬 컴퓨터-개인 인증서 저장소에서 개인 키와 함께 리소스 권한 부여 인증서를 읽을 권한이 없습니다. 이 문제를 해결하려면 services.msc에서 컨텍스트 계정을 실행하는 커넥터 서비스를 확인합니다. 커넥터 서비스는 NT AUTHORITY\SYSTEM 컨텍스트에서 실행해야 합니다. <br><br> 2. Intune 관리 포털의 PKCS 인증서 프로필이 잘못된 Symantec CA 기본 서비스 FQDN으로 구성되었을 수 있습니다. FQDN은 `pki-ws.symauth.com`과 유사합니다. 이 문제를 해결하려면 Symantec 고객 지원과 함께 해당 URL이 구독에 적합한지 확인합니다. <br><br> 3. Intune Certificate Connector가 개인 키를 검색할 수 없으므로 리소스 권한 부여 인증서를 사용하여 Symantec CA로 인증하지 못했습니다. 이 문제를 해결하려면 로컬 컴퓨터-개인 인증서 저장소에 개인 키와 함께 리소스 권한 부여 인증서를 설치해야 합니다. <br><br> 문제가 계속되면 Symantec 고객 지원에 문의하세요. |
| Symantec 공급자 - Symantec 정책 “요청 요소를 이해할 수 없음”을 가져오지 못함 | 클라이언트 프로필 OID가 Intune 인증서 프로필과 일치하지 않으므로 Intune Certificate Connector가 Symantec 인증서 프로필 템플릿을 가져오지 못했습니다. 다른 경우에 Intune Certificate Connector가 Symantec CA에서 지정된 클라이언트 프로필 OID와 연결된 인증서 프로필 템플릿을 찾을 수 없습니다. <br><br> 이 문제를 해결하려면 Symantec CA의 Symantec 인증서 템플릿에서 올바른 클라이언트 프로필 OID를 얻습니다. 그런 다음 Intune 관리 포털에서 PKCS 인증서 프로필을 업데이트합니다. <br><br> Symantec CA에서 클라이언트 프로필 OID를 얻습니다. <br> 1. Symantec CA 관리 포털에 로그온합니다. <br> 2. [인증서 프로필 관리]를 클릭합니다. <br> 3. 사용할 인증서 프로필을 선택합니다. <br> 4. 인증서 프로필 OID를 얻습니다. 다음 예제와 같이 표시됩니다. <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 올바른 인증서 프로필 OID를 사용하여 PKCS 인증서 프로필 업데이트: <br>1. Intune 관리 포털에 로그온합니다. <br> 2. PKCS 인증서 프로필로 이동하여 **편집**을 클릭합니다. <br> 3. 인증서 템플릿 이름 필드의 업데이트에서 인증서 프로필 OID를 업데이트합니다. <br> 4. PKCS 인증서 프로필을 저장합니다. |
| Symantec 공급자 - 정책 확인에 실패했습니다. <br><br> 특성이 Symantec 지원 인증서 템플릿 특성 목록에 포함되지 않음 | Symantec 인증서 프로필 템플릿과 Intune 인증서 프로필이 일치하지 않을 경우 Symantec CA가 이 메시지를 표시함 이 문제는 SubjectName 또는 SubjectAltName의 특성 불일치로 인해 발생했을 수 있습니다. <br><br> 이 문제를 해결하려면 Symantec 인증서 프로필 템플릿에서 SubjectName 및 SubjectAltName에 대한 Intune 지원 특성을 선택해야 합니다. 자세한 내용은 인증서 매개 변수 섹션에서 Intune 지원 특성을 참조하세요. |
| 일부 사용자 장치가 Symantec CA에서 PKCS 인증서를 수신하지 않습니다. | 사용자 UPN에 밑줄 같은 특수 문자가 포함된 경우(예: `global_admin@intune.onmicrosoft.com`) 이 문제가 발생합니다. <br><br> Symantec CA는mail_firstname 및 mail_lastname에서 특수 문자를 지원하지 않습니다. <br><br> 이 문제를 해결하려면 다음 단계를 따릅니다. <br><br> 1.   Symantec CA 관리 포털에 로그온합니다. <br> 2. [인증서 프로필 관리]로 이동합니다. <br> 3.   Intune에 사용되는 인증서 프로필을 클릭합니다. <br> 4.  [옵션 사용자 지정] 링크를 클릭합니다. <br> 5.   [고급 옵션] 단추를 클릭합니다. <br> 6.  인증서 필드 - 주체 DN 아래에 CN(일반 이름) 필드를 추가하고 기존 CN(일반 이름) 필드를 삭제합니다. 추가 및 삭제는 함께 수행해야 합니다. <br> 7.    저장을 클릭합니다. <br><br> 이전 변경에 따라 Symantec 인증서 프로필이 mail_firstname 및 mail_lastname 대신 “CN=<upn>”을 요청합니다. |
| 사용자가 장치에서 이미 배포된 인증서를 수동으로 삭제했습니다. | Intune은 다음 체크 인 또는 정책 적용 중에 동일한 인증서를 다시 배포합니다. 이 경우 NDES Connector는 PKCS 인증서 요청을 수신하지 않습니다. |

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune 장치 프로필은 무엇인가요?](device-profiles.md)의 정보 외에 이 문서에 제공된 정보를 사용하여 조직의 장치 및 인증서를 관리합니다.

[InstallConnector]:  ./media/certificates-symantec-connector-install.png "Intune Certificate Connector 설치 및 PFX 배포 선택"
[ConfigureConnector]: ./media/certificates-symantec-configure-connector-configure.png "Intune Certificate Connector 구성"
[ConfigureProfile]: ./media/certificates-symantec-pkcs-example.png "Azure Portal에서 PKCS 인증서 프로필 만들기"
