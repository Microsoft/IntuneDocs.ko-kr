---
title: Microsoft Intune을 사용하여 DigiCert PKCS 인증서 발급
titleSuffix: Microsoft Intune
description: DigiCert PKI 플랫폼에서 Intune 관리 디바이스로 PKCS 인증서를 발급하려면 Intune Certificate Connector를 설치 및 구성합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca76ffe0c8fa42f1c2cf24fcdefd287140231220
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73801639"
---
# <a name="set-up-intune-certificate-connector-for-digicert-pki-platform"></a>DigiCert PKI 플랫폼용 Intune Certificate Connector 설정

Intune Certificate Connector를 사용하여 DigiCert PKI 플랫폼에서 Intune 관리 디바이스로 PKCS 인증서를 발급합니다. 이 커넥터는 DigiCert 인증 기관(CA)에만 사용할 수도 있고 DigiCert CA와 Microsoft CA 모두에 사용할 수도 있습니다.

> [!TIP]
> DigiCert는 Symantec의 웹 사이트 보안 및 관련 PKI 솔루션 비즈니스를 인수했습니다. 이 변경에 대한 자세한 내용은 [Symantec 기술 지원 문서](https://support.symantec.com/en_US/article.INFO4722.html)를 참조하세요.

이미 Intune Certificate Connector를 사용하여 Microsoft CA에서 PKCS 또는 System Center Endpoint Protection을 사용해 인증서를 발급하는 경우, 동일한 커넥터를 사용하여 DigiCert CA에서 PKCS 인증서를 구성하고 발급할 수 있습니다. DigiCert CA를 지원하도록 구성을 완료한 후 Intune Certificate Connector에서 다음 인증서를 발급할 수 있습니다.

* Microsoft CA의 PKCS 인증서
* DigiCert CA의 PKCS 인증서
* Microsoft CA의 Endpoint Protection 인증서

커넥터를 설치하지 않았지만 Microsoft CA와 DigiCert CA 모두에 커넥터를 사용할 계획인 경우 먼저 Microsoft CA에 대한 커넥터 구성을 완료합니다. 그런 다음 이 문서로 돌아와서 DigiCert도 지원하도록 구성합니다. 인증서 프로필과 커넥터에 대한 자세한 내용은 [Microsoft Intune에서 디바이스에 대한 인증서 프로필 구성](certificates-configure.md)을 참조하세요.  

DigiCert CA에만 커넥터를 사용하는 경우 이 문서의 지침을 사용하여 커넥터를 설치하고 구성할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

- **DigiCert CA 활성 구독**: DigiCert CA에서 RA(등록 기관) 인증서를 가져오려면 구독이 필요합니다.

## <a name="install-the-digicert-ra-certificate"></a>DigiCert RA 인증서 설치

1. 다음 코드 조각을 **certreq.ini** 파일에 저장하고 필요에 따라 업데이트합니다(예: ‘CN 형식의 주체 이름’). 

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

2. 관리자 권한 명령 프롬프트를 열고 다음 명령을 사용하여 인증서 서명 요청(CSR)을 생성합니다.

   `Certreq.exe -new certreq.ini request.csr`

3. Notepad에서 request.csr 파일을 열고 다음 형식의 CSR 콘텐츠를 복사합니다.

        -----BEGIN NEW CERTIFICATE REQUEST-----
        MIID8TCCAtkCAQAwbTEMMAoGA1UEBhMDVVNBMQswCQYDVQQIDAJXQTEQMA4GA1UE
        …
        …
        fzpeAWo=
        -----END NEW CERTIFICATE REQUEST-----


4. DigiCert CA에 로그인하고 작업에서 **RA 인증서 가져오기**로 이동합니다.

   a. 텍스트 상자에 3단계의 CSR 콘텐츠를 제공합니다.

   b. 인증서의 식별 이름을 제공합니다.

   c. **계속**을 선택합니다.

   d. 제공된 링크를 사용하여 RA 인증서를 로컬 컴퓨터에 다운로드합니다.

5. RA 인증서를 Windows 인증서 저장소로 가져옵니다.

   a. MMC 콘솔을 엽니다.

   b. **파일** > **스냅인 추가/제거** > **인증서** > **추가**를 선택합니다.

   c. **컴퓨터 계정** > **다음**을 선택합니다.

   d. **로컬 컴퓨터** > **마침**을 선택합니다.

   e. **스냅인 추가/제거** 창에서 **확인**을 선택합니다. **인증서(로컬 컴퓨터)**  > **개인** > **인증서**를 확장합니다.

   f. **인증서** 노드를 마우스 오른쪽 단추로 클릭하고 **모든 작업** > **가져오기**를 선택합니다.

   g. DigiCert CA에서 다운로드한 RA 인증서의 위치를 선택하고 **다음**을 선택합니다.

   h. **개인 인증서 저장소** > **다음**을 선택합니다.

   i. **마침**을 선택하여 RA 인증서와 프라이빗 키를 **로컬 컴퓨터-개인** 저장소로 가져옵니다.

6. 프라이빗 키 인증서를 내보내고 가져옵니다.

   a. **인증서(로컬 컴퓨터)**  > **개인** > **인증서**를 확장합니다.

   b. 이전 단계에서 가져온 인증서를 선택합니다.

   c. 인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업** > **내보내기**를 선택합니다.

   d. **다음**을 선택한 후 암호를 입력합니다.

   e. 내보낼 위치를 선택한 후 **마침**을 선택합니다.

   f. 5단계의 절차를 사용하여 프라이빗 키 인증서를 **로컬 컴퓨터-개인** 저장소로 가져옵니다.

   g. 공백 없이 RA 인증서 지문을 복사합니다. 다음은 지문의 예입니다.

        RA Cert Thumbprint: “EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5”

    > [!NOTE]
    > DigiCert CA에서 RA 인증서를 가져오는 데 도움이 필요하면 [DigiCert 고객 지원](mailto:enterprise-pkisupport@digicert.com)에 문의하세요.

## <a name="prepare-to-install-intune-certificate-connector"></a>Intune Certificate Connector 설치 준비

> [!TIP]
> 이 섹션은 DigiCert CA에만 Intune Certificate Connector를 사용하는 경우에 적용됩니다. Microsoft CA에 Intune Certificate Connector를 사용하고 DigiCert CA 지원을 추가하려는 경우 [DigiCert를 지원하도록 커넥터 구성](#configure-the-connector-to-support-digicert)으로 건너뜁니다.

1. 다음 목록에서 Windows 운영 체제 버전 중 하나를 선택하여 컴퓨터에 설치합니다.
   * Windows Server 2012 R2 Datacenter
   * Windows Server 2012 R2 Standard
   * Windows Server 2016 Datacenter
   * Windows Server 2016 Standard

2. 관리자 권한이 있는 사용자를 만들고 이를 사용하여 아래 단계를 완료합니다.

3. 최신 Windows 업데이트를 확인하여 사용 가능한 경우 설치합니다. Windows 업데이트를 설치한 후 컴퓨터를 다시 시작합니다.

4. .NET Framework 3.5를 설치합니다.

   a. **제어판** > **프로그램 및 기능** > **Windows 기능 켜기/끄기**를 엽니다.

   b. **.NET Framework 3.5**를 선택하고 설치합니다.

## <a name="install-intune-certificate-connector-for-use-with-digicert"></a>DigiCert에 사용하기 위해 Intune Certificate Connector 설치

> [!TIP]
> Microsoft CA에 Intune Certificate Connector를 사용하고 DigiCert CA 지원을 추가하려는 경우 [DigiCert를 지원하도록 커넥터 구성](#configure-the-connector-to-support-digicert)으로 건너뜁니다.

Intune 관리 포털에서 최신 Intune Certificate Connector 버전을 다운로드하고 아래 지침을 따릅니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **테넌트 관리** > **커넥터 및 토큰** > **인증서 커넥터** >  **+추가**를 선택합니다.

3. PKCS #12용 커넥터에 대해 *인증서 커넥터 소프트웨어 다운로드*를 클릭하고 커넥터를 설치할 서버에서 액세스할 수 있는 위치에 해당 파일을 저장합니다.

   ![커넥터 소프트웨어 다운로드](./media/certificates-digicert-configure/connector-download.png)

4. 커넥터를 설치할 서버에서 관리자 권한으로 **NDESConnectorSetup.exe**를 실행합니다.

5. **설치 옵션** 페이지에서 **PFX 배포**를 선택합니다.

   ![PFX 배포 선택](./media/certificates-digicert-configure/digicert-ca-connector-install.png)

   > [!IMPORTANT]
   > Intune Certificate Connector를 사용하여 Microsoft CA 및 DigiCert CA에서 인증서를 발급하려면 **SCEP 및 PFX 프로필 배포**를 선택합니다.

6. 기본 선택 항목을 사용하여 커넥터 설정을 마칩니다.

## <a name="configure-the-connector-to-support-digicert"></a>DigiCert를 지원하도록 커넥터 구성

기본적으로 Intune Certificate Connector는 **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc**에 설치됩니다.

1. **NDESConnectorSvc** 폴더에서 Notepad로 **NDESConnector.exe.config** 파일을 엽니다.

   a. 이전 섹션에서 복사한 인증서 지문 값으로 `RACertThumbprint` 키 값을 업데이트합니다. 예를 들면 다음과 같습니다.

        <add key="RACertThumbprint"
        value="EA7A4E0CD1A4F81CF0740527C31A57F6020C17C5"/>

   b. 파일을 저장하고 닫습니다.

2. **services.msc**를 엽니다.

   a. **Intune Connector 서비스**를 선택합니다.

   b. 서비스를 중지한 후 서비스를 시작합니다.

   c. 서비스 창을 닫습니다.

## <a name="set-up-the-intune-administrator-account"></a>Intune 관리자 계정 설정  

> [!TIP]
> Microsoft CA에 Intune Certificate Connector를 사용하고 DigiCert CA 지원을 추가하려는 경우 [신뢰할 수 있는 인증서 프로필 만들기](#create-a-trusted-certificate-profile)로 건너뜁니다.
 
1. **%ProgramFiles%\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe**에서 NDES Connector 사용자 인터페이스를 엽니다.

2. **등록** 탭에서 **로그인**을 선택합니다.

3. Intune 테넌트 관리자 자격 증명을 제공합니다.

4. **로그인**을 선택한 다음 **확인**을 선택하여 성공적으로 등록되었는지 확인합니다. 그런 다음 NDES Connector 사용자 인터페이스를 닫을 수 있습니다.

   ![“등록 성공” 메시지가 있는 NDES Connector 인터페이스](./media/certificates-digicert-configure/certificates-digicert-configure-connector-configure.png)

## <a name="create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필 만들기

Intune 관리 디바이스용으로 배포할 PKCS 인증서는 신뢰할 수 있는 루트 인증서와 연결되어야 합니다. 이 연결을 설정하려면 DigiCert CA의 루트 인증서를 사용하여 Intune 신뢰할 수 있는 인증서 프로필을 만듭니다.

1. DigiCert CA에서 신뢰할 수 있는 루트 인증서를 가져옵니다.

   a. DigiCert CA 관리 포털에 로그인합니다.

   b. **작업**에서 **CA 관리**를 선택합니다.

   c. 목록에서 적합한 CA를 선택합니다.

   d. **루트 인증서 다운로드**를 선택하여 신뢰할 수 있는 루트 인증서를 다운로드합니다.

2. Intune 포털에서 신뢰할 수 있는 인증서 프로필을 만듭니다.

   a. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

   b. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

   c. 다음 속성을 입력합니다.

      - 프로필의 **이름**
      - 선택적으로 **설명** 설정
      - 프로필을 배포할 **플랫폼**
      - **프로필 형식**을 **신뢰할 수 있는 인증서**로 설정

   d. **설정**을 선택한 후 이 인증서 프로필에서 사용하기 위해 내보낸 신뢰할 수 있는 루트 CA 인증서 .cer 파일을 찾은 다음, **확인**을 선택합니다.

   e. Windows 8.1 및 Windows 10 디바이스에 한해 신뢰할 수 있는 인증서의 **대상 저장소**를 선택합니다.
      - **컴퓨터 인증서 저장소 - 루트**
      - **컴퓨터 인증서 저장소 - 중간**
      - **사용자 인증서 저장소 - 중간**

   f. 작업이 완료되면 **확인**을 선택하고 **프로필 만들기** 창으로 돌아와서 **만들기**를 선택합니다.  

  프로필은 **디바이스 구성 - 프로필** 창의 프로필 목록에 나타나며, 프로필 유형은 **신뢰할 수 있는 인증서**입니다.  인증서를 받는 디바이스에 이 프로필을 할당해야 합니다. 이 프로필을 그룹에 할당하려면 [디바이스 프로필 할당](../configuration/device-profile-assign.md)을 참조하세요.


## <a name="get-the-certificate-profile-oid"></a>인증서 프로필 OID 가져오기  

인증서 프로필 OID는 DigiCert CA의 인증서 프로필 템플릿과 연결됩니다. Intune에서 PKCS 인증서 프로필을 만들려면 인증서 템플릿 이름이 DigiCert CA의 인증서 템플릿과 연결된 인증서 프로필 OID 형식이어야 합니다.

1. DigiCert CA 관리 포털에 로그인합니다.
2. **인증서 프로필 관리**를 선택합니다.
3. 사용할 인증서 프로필을 선택합니다.
4. 인증서 프로필 OID를 복사합니다. 다음 예제와 같이 표시됩니다.

       Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109 

> [!NOTE]
> 인증서 프로필 OID를 가져오는 데 도움이 필요한 경우 [DigiCert 고객 지원](mailto:enterprise-pkisupport@digicert.com)에 문의하세요.

## <a name="create-a-pkcs-certificate-profile"></a>PKCS 인증서 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

3. 다음 속성을 입력합니다.

   - 프로필의 **이름**
   - 선택적으로 **설명** 설정
   - 프로필을 배포할 **플랫폼**
   - **프로필 형식**을 **PKCS 인증서**로 설정

4. **PKCS 인증서** 창에서 다음 표의 값을 사용하여 매개 변수를 구성합니다. 이러한 값은 Intune Certificate Connector를 통해 DigiCert CA에서 PKCS 인증서를 발급하는 데 필요합니다.

   |PKCS 인증서 매개 변수 | 값 | 설명 |
   | --- | --- | --- |
   | 인증 기관 | pki-ws.symauth.com | 이 값은 후행 슬래시 없이 DigiCert CA 기본 서비스 FQDN이어야 합니다. 이것이 DigiCert CA 구독의 올바른 기본 서비스 FQDN인지 모르는 경우 DigiCert 고객 지원에 문의하세요. <br><br>*Symantec에서 DigiCert로 바뀌었지만 이 URL은 변경되지 않았습니다*. <br><br> 이 FQDN이 잘못된 경우 Intune Certificate Connector는 DigiCert CA에서 PKCS 인증서를 발급하지 않습니다.| 
   | 인증 기관 이름 | Symantec | 이 값은 **Symantec** 문자열이어야 합니다. <br><br> 이 값에 변경이 있는 경우 Intune Certificate Connector는 DigiCert CA에서 PKCS 인증서를 발급하지 않습니다.|
   | 인증서 템플릿 이름 | DigiCert CA의 인증서 프로필 OID입니다. 예를 들면 다음과 같습니다. **2.16.840.1.113733.1.16.1.2.3.1.1.61904612**| 이 값은 [이전 섹션에서 얻은](#get-the-certificate-profile-oid) DigiCert CA 인증서 프로필 템플릿의 인증서 프로필 OID여야 합니다. <br><br> Intune Certificate Connector가 DigiCert CA에서 이 인증서 프로필 OID와 연결된 인증서 템플릿을 찾을 수 없는 경우 DigiCert CA에서 PKCS 인증서를 발급하지 않습니다.|

   ![CA 및 인증서 템플릿 선택 항목](./media/certificates-digicert-configure/certificates-digicert-pkcs-example.png)

   > [!NOTE]
   > Windows 플랫폼용 PKCS 인증서 프로필은 신뢰할 수 있는 인증서 프로필과 연결할 필요가 없습니다. 그러나 Android와 같은 Windows 이외의 플랫폼 프로필에는 필요합니다.

5. 비즈니스 요구에 맞게 프로필 구성을 완료한 다음 **만들기**를 선택하여 프로필을 저장합니다.

6. 새 프로필의 *개요* 페이지에서 **할당**을 선택하고 이 프로필을 받을 적절한 그룹을 구성합니다. 하나 이상의 사용자 또는 디바이스는 할당된 그룹의 일부여야 합니다.
 
이전 단계를 완료한 후 Intune Certificate Connector는 DigiCert CA에서 할당된 그룹의 Intune 관리 디바이스에 PKCS 인증서를 발급합니다. 이러한 인증서는 Intune 관리 디바이스에 있는 **현재 사용자** 인증서 저장소의 **개인** 저장소에서 사용할 수 있습니다.

### <a name="supported-attributes-for-the-pkcs-certificate-profile"></a>PKCS 인증서 프로필에 지원되는 특성

|특성 | Intune 지원 형식 | DigiCert Cloud CA 지원 형식 | result |
| --- | --- | --- | --- |
| 주체 이름 |Intune은 다음 세 가지 형식으로만 주체 이름을 지원합니다. <br><br> 1. 일반 이름 <br> 2. 메일이 포함되는 일반 이름 <br> 3. 메일인 일반 이름 <br><br> 예를 들면 다음과 같습니다. <br><br> `CN = IWUser0 <br><br> E = IWUser0@samplendes.onmicrosoft.com` | DigiCert CA는 더 많은 특성을 지원합니다.  추가 특성을 선택하려면 DigiCert 인증서 프로필 템플릿에서 고정 값으로 해당 특성을 정의해야 합니다.| PKCS 인증서 요청에서 일반 이름 또는 메일을 사용합니다. <br><br> Intune 인증서 프로필과 DigiCert 인증서 프로필 템플릿 간의 특성 선택 사항이 일치하지 않으면 DigiCert CA에서 인증서가 발급되지 않습니다.|
| SAN | Intune은 다음 SAN 필드 값만 지원합니다. <br><br> **AltNameTypeEmail** <br> **AltNameTypeUpn** <br> **AltNameTypeOtherName**(인코딩된 값) | DigiCert Cloud CA도 이러한 매개 변수를 지원합니다. 추가 특성을 선택하려면 DigiCert 인증서 프로필 템플릿에서 고정 값으로 해당 특성을 정의해야 합니다. <br><br> **AltNameTypeEmail**: 이 형식을 SAN에서 찾을 수 없으면 Intune Certificate Connector는 **AltNameTypeUpn**의 값을 사용합니다.  **AltNameTypeUpn**도 SAN에서 찾을 수 없으면 Intune Certificate Connector는 주체 이름의 값을 사용합니다(메일 형식인 경우).  그래도 형식을 찾을 수 없으면 Intune Certificate Connector가 인증서를 발급하지 못합니다. <br><br> 예: `RFC822 Name=IWUser0@ndesvenkatb.onmicrosoft.com`  <br><br> **AltNameTypeUpn**: 이 형식을 SAN에서 찾을 수 없으면 Intune Certificate Connector는 **AltNameTypeEmail**의 값을 사용합니다. **AltNameTypeEmail**도 SAN에서 찾을 수 없으면 Intune Certificate Connector는 주체 이름의 값을 사용합니다(메일 형식인 경우). 그래도 형식을 찾을 수 없으면 Intune Certificate Connector가 인증서를 발급하지 못합니다.  <br><br> 예: `Other Name: Principal Name=IWUser0@ndesvenkatb.onmicrosoft.com` <br><br> **AltNameTypeOtherName**: 이 형식을 SAN에서 찾을 수 없으면 Intune Certificate Connector가 인증서를 발급하지 못합니다. <br><br> 예: `Other Name: DS Object Guid=04 12 b8 ba 65 41 f2 d4 07 41 a9 f7 47 08 f3 e4 28 5c ef 2c` <br><br>  이 필드의 값은 DigiCert CA에서 인코딩된 형식(16진수 값)으로만 지원됩니다. 이 필드에 있는 값의 경우 Intune Certificate Connector는 인증서 요청을 제출하기 전에 base64 인코딩된 값으로 변환합니다. *Intune Certificate Connector는 이 값이 이미 인코딩되었는지 여부를 확인하지 않습니다.* | 없음 |

## <a name="troubleshooting"></a>문제 해결

Intune Certificate Connector 서비스 로그는 NDES Connector 컴퓨터의 **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\Logs\Logs**에서 사용할 수 있습니다. [SvcTraceViewer](https://docs.microsoft.com/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe)에서 로그를 열고 예외 또는 오류 메시지를 검색합니다.

| 문제/오류 메시지 | 해결 단계 |
| --- | --- |
| NDES Connector UI에서 Intune 테넌트 관리자 계정으로 로그인할 수 없습니다. | 이 문제는 Microsoft Endpoint Manager 관리 센터에서 온-프레미스 인증서 커넥터가 사용하도록 설정되지 않은 경우 발생할 수 있습니다. 이 문제를 해결하려면 <br><br> 1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다. <br> 2. **테넌트 관리** > **커넥터 및 토큰** > **인증서 커넥터**를 선택합니다. <br> 3. 인증서 커넥터를 찾은 후 사용하도록 설정되어 있는지 확인합니다. <br><br> 이전 단계를 완료한 후 NDES Connector UI에서 동일한 Intune 테넌트 관리자 계정으로 로그인해 보세요. |
| NDES Connector 인증서를 찾을 수 없습니다. <br><br> System.ArgumentNullException: 값은 null일 수 없습니다. | Intune 테넌트 관리자 계정이 NDES Connector UI에 로그인한 적이 없는 경우 Intune Certificate Connector가 이 오류를 표시합니다. <br><br> 이 오류가 지속되면 Intune Service Connector를 다시 시작합니다. <br><br> 1. **services.msc**를 엽니다. <br> 2. **Intune Connector 서비스**를 선택합니다. <br> 3. 마우스 오른쪽 단추를 클릭하고 **다시 시작**을 선택합니다.|
| NDES Connector - IssuePfx-Generic 예외: <br> System.NullReferenceException: 개체 참조가 개체의 인스턴스로 설정되지 않았습니다. | 이 오류는 일시적입니다. Intune Service Connector를 다시 시작합니다. <br><br> 1. **services.msc**를 엽니다. <br> 2. **Intune Connector 서비스**를 선택합니다. <br> 3. 마우스 오른쪽 단추를 클릭하고 **다시 시작**을 선택합니다. |
| DigiCert 공급자 - DigiCert 정책을 가져오지 못했습니다. <br><br>“작업 시간이 초과되었습니다.” | Intune Certificate Connector가 DigiCert CA와 통신하는 동안 작업 시간 초과 오류가 발생했습니다. 이 오류가 계속 발생하면 연결 제한 시간 값을 늘리고 다시 시도합니다. <br><br> 연결 제한 시간을 늘리려면: <br> 1. NDES Connector 컴퓨터로 이동합니다. <br>2. Notepad에서 **%ProgramFiles%\Microsoft Intune\NDESConnectorSvc\NDESConnector.exe.config** 파일을 엽니다. <br> 3. 다음 매개 변수의 제한 시간 값을 늘립니다. <br><br> `CloudCAConnTimeoutInMilliseconds` <br><br> 4. Intune Certificate Connector 서비스를 다시 시작합니다. <br><br> 문제가 계속되면 DigiCert 고객 지원에 문의하세요. |
| DigiCert 공급자 - 클라이언트 인증서를 가져오지 못했습니다. | Intune Certificate Connector가 로컬 컴퓨터-개인 인증서 저장소에서 리소스 권한 부여 인증서를 검색하지 못했습니다. 이 문제를 해결하려면 로컬 컴퓨터-개인 인증서 저장소에 프라이빗 키와 함께 리소스 권한 부여 인증서를 설치합니다. <br><br> DigiCert CA에서 리소스 권한 부여 인증서를 받아야 합니다. 자세한 내용은 DigiCert 고객 지원에 문의하세요. | 
| DigiCert 공급자 - DigiCert 정책을 가져오지 못했습니다. <br><br>“요청이 중단되었습니다. SSL/TLS 보안 채널을 만들 수 없음”을 가져오지 못함 | 이 오류는 다음과 같은 경우에 발생합니다. <br><br> 1. Intune Certificate Connector 서비스에 로컬 컴퓨터-개인 인증서 저장소에서 프라이빗 키와 함께 리소스 권한 부여 인증서를 읽을 권한이 없습니다. 이 문제를 해결하려면 services.msc에서 커넥터 서비스의 실행 중인 컨텍스트 계정을 확인합니다. 커넥터 서비스는 NT AUTHORITY\SYSTEM 컨텍스트에서 실행되어야 합니다. <br><br> 2. Intune 관리 포털의 PKCS 인증서 프로필이 DigiCert CA의 잘못된 기본 서비스 FQDN으로 구성되었을 수 있습니다. FQDN은 **pki-ws.symauth.com**과 비슷합니다. 이 문제를 해결하려면 해당 URL이 구독에 적합한지 DigiCert 고객 지원에 확인합니다. <br><br> 3. Intune Certificate Connector가 프라이빗 키를 검색할 수 없으므로 리소스 권한 부여 인증서를 통해 DigiCert CA에 인증하지 못했습니다. 이 문제를 해결하려면 로컬 컴퓨터-개인 인증서 저장소에 프라이빗 키와 함께 리소스 권한 부여 인증서를 설치합니다. <br><br> 문제가 계속되면 DigiCert 고객 지원에 문의하세요. |
| DigiCert 공급자 - DigiCert 정책을 가져오지 못했습니다. <br><br>“요청 요소가 인식되지 않습니다.” | 클라이언트 프로필 OID가 Intune 인증서 프로필과 일치하지 않으므로 Intune Certificate Connector가 DigiCert 인증서 프로필 템플릿을 가져오지 못했습니다. 다른 경우에 Intune Certificate Connector가 DigiCert CA에서 클라이언트 프로필 OID와 연결된 인증서 프로필 템플릿을 찾을 수 없습니다. <br><br> 이 문제를 해결하려면 DigiCert CA의 DigiCert 인증서 템플릿에서 올바른 클라이언트 프로필 OID를 얻습니다. 그런 다음 Intune 관리 포털에서 PKCS 인증서 프로필을 업데이트합니다. <br><br> DigiCert CA에서 클라이언트 프로필 OID 얻기: <br> 1. DigiCert CA 관리 포털에 로그인합니다. <br> 2. **인증서 프로필 관리**를 선택합니다. <br> 3. 사용할 인증서 프로필을 선택합니다. <br> 4. 인증서 프로필 OID 가져옵니다. 다음 예제와 같이 표시됩니다. <br> `Certificate Profile OID = 2.16.840.1.113733.1.16.1.2.3.1.1.47196109` <br><br> 올바른 인증서 프로필 OID를 사용하여 PKCS 인증서 프로필 업데이트: <br>1. Intune 관리 포털에 로그인합니다. <br> 2. PKCS 인증서 프로필로 이동하여 **편집**을 선택합니다. <br> 3. 인증서 템플릿 이름 필드에서 인증서 프로필 OID를 업데이트합니다. <br> 4. PKCS 인증서 프로필을 저장합니다. |
| DigiCert 공급자 - 정책 확인에 실패했습니다. <br><br> 특성이 DigiCert 지원 인증서 템플릿 특성 목록에 포함되지 않습니다. | DigiCert CA는 DigiCert 인증서 프로필 템플릿과 Intune 인증서 프로필이 일치하지 않을 경우 이 메시지를 표시합니다. 이 문제는 **SubjectName** 또는 **SubjectAltName**의 특성 불일치로 인해 발생했을 수 있습니다. <br><br> 이 문제를 해결하려면 DigiCert 인증서 프로필 템플릿에서 **SubjectName** 및 **SubjectAltName**에 대한 Intune 지원 특성을 선택합니다. 자세한 내용은 **인증서 매개 변수** 섹션에서 Intune 지원 특성을 참조하세요. |
| 일부 사용자 디바이스가 DigiCert CA에서 PKCS 인증서를 수신하지 않습니다. | 사용자 UPN에 밑줄 같은 특수 문자가 포함된 경우(예: `global_admin@intune.onmicrosoft.com`) 이 문제가 발생합니다. <br><br> DigiCert CA는 **mail_firstname** 및 **mail_lastname**에서 특수 문자를 지원하지 않습니다. <br><br> 이 문제를 해결하려면 다음 단계를 따릅니다. <br><br> 1. DigiCert CA 관리 포털에 로그인합니다. <br> 2. **인증서 프로필 관리**로 이동합니다. <br> 3. Intune에 사용되는 인증서 프로필을 선택합니다. <br> 4. **옵션 사용자 지정** 링크를 선택합니다. <br> 5. **고급 옵션** 단추를 선택합니다. <br> 6. **인증서 필드 - 주체 DN** 아래에 **CN(일반 이름)** 필드를 추가하고 기존 **CN(일반 이름)** 필드를 삭제합니다. 추가 및 삭제 작업은 함께 수행해야 합니다. <br> 7. **저장**을 선택합니다. <br><br> 이전 변경에 따라 DigiCert 인증서 프로필이 **mail_firstname** 및 **mail_lastname** 대신 **“CN=<upn>”** 을 요청합니다. |
| 사용자가 디바이스에서 이미 배포된 인증서를 수동으로 삭제했습니다. | Intune은 다음 체크 인 또는 정책 적용 중에 동일한 인증서를 다시 배포합니다. 이 경우 NDES Connector는 PKCS 인증서 요청을 수신하지 않습니다. |

## <a name="next-steps"></a>다음 단계

[Microsoft Intune 디바이스 프로필은 무엇인가요?](../configuration/device-profiles.md)의 정보 외에 이 문서의 정보를 사용하여 조직의 디바이스 및 인증서를 관리합니다.
