---
title: 가져온 PFX 인증서를 Microsoft Intune에서 사용 - Azure | Microsoft Docs
description: 가져온 PKCS(Public Key Cryptography Standards) 인증서를 Microsoft Intune에서 사용합니다. 여기에는 인증서 가져오기, 인증서 템플릿 구성, Intune 가져온 PFX 인증서 커넥터 설치, 가져온 PKCS 인증서 프로필 만들기가 포함됩니다.
keywords: ''
author: ralms
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: d54c58523fdb44080b6c4210d639f9ad0ce476e2
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801540"
---
# <a name="configure-and-use-imported-pkcs-certificates-with-intune"></a>가져온 PKCS 인증서를 Intune을 사용하여 구성 및 사용

Microsoft Intune은 주로 이메일 프로필을 이용한 S/MIME 암호화에 사용하는, 가져온 공개 키 쌍 (PKCS) 인증서 사용을 지원합니다. Intune의 특정 이메일 프로필은 S/MIME를 활성화해 S/MIME 서명 인증서와 S/MIME 암호화 인증서를 정의하는 기능을 지원합니다.

S/MIME 암호화는 이메일을 특정 인증서로 암호화하기 때문에 해독하기가 어렵습니다. 암호를 해독하려면 이메일을 읽는 디바이스에서 이메일을 암호화한 인증서의 개인 키가 있어야 합니다. 암호화 인증서는 정기적으로 갱신됩니다. 따라서 이전 메일을 읽으려면 모든 디바이스에서의 암호화 기록이 필요할 수도 있습니다.  모든 디바이스에서 동일한 인증서를 사용해야 하므로, [SCEP](certificates-scep-configure.md)나 [PKCS](certficates-pfx-configure.md) 인증서 프로필은 이 목적으로 사용할 수 없습니다. 디바이스마다 고유한 인증서를 전달하기 때문입니다.

S/MIME를 Intune에서 사용하는 방법에 대한 자세한 내용은 [S/MIME를 사용하여 메일 암호화](certificates-s-mime-encryption-sign.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

가져온 PKCS 인증서를 Intune에서 사용하려면 다음 인프라가 필요합니다.

- **Microsoft Intune용 PFX 인증서 커넥터**:

  각 Intune 테넌트는 이 커넥터의 단일 인스턴스를 지원합니다. 이 커넥터를 Microsoft Intune Certificate Connector 인스턴스와 동일한 서버에 설치할 수 있습니다.

  이 커넥터는 특정 사용자의 S/MIME 이메일 암호화를 위해 Intune으로 가져온 PFX 파일에 대한 요청을 처리합니다.

  이 커넥터는 새 버전이 출시되면 자동으로 업데이트할 수 있습니다. 업데이트 기능을 사용하려면 커넥터가 포트 **443**을 통해 **autoupdate.msappproxy.net**에 연결할 수 있도록 방화벽을 열어야 합니다.

  커넥터에서 액세스하는 모든 네트워크 엔드포인트에 대한 자세한 내용은 [Intune 네트워크 구성 요구 사항 및 대역폭](../fundamentals/network-bandwidth-use.md)을 참조하세요.

- **Windows Server**:  
  Microsoft Intune용 PFX 인증서 커넥터를 호스트하려면 Windows Server를 사용해야 합니다.  커넥터는 Intune으로 가져온 인증서 관련 요청을 처리하는 데 사용합니다.

  Intune은 *Microsoft Intune Certificate Connector*를 *Microsoft Intune용 PFX 인증서 커넥터*와 같은 서버에 설치하는 기능을 지원합니다.

  커넥터를 지원하려면 서버는 .NET 4.6 Framework 이상을 실행해야 합니다. 커넥터 설치를 시작할 때 .NET 4.6 Framework가 설치되어 있지 않다면, 커넥터 설치 과정으로 자동으로 설치됩니다.

- **Visual Studio 2015 이상**(선택 사항): 도우미 PowerShell 모듈을 cmdlet으로 빌드해 PFX 인증서를 Microsoft Intune으로 가져오려면 Visual Studio를 사용해야 합니다. 도우미 PowerShell cmdlet을 가져오는 방법은 [ GitHub의 PFXImport PowerShell 프로젝트](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)를 참조하세요.

## <a name="how-it-works"></a>작동 방식

**가져온 PFX 인증서**를 Intune을 사용해 사용자에게 배포할 때는 디바이스 외에 다음과 같은 두 요소도 사용합니다.

- **Intune 서비스**: PFX 인증서를 암호화된 상태로 보관하고 사용자 디바이스에 대한 인증서 배포를 처리합니다.  인증서의 개인 키를 보호하는 암호는 HSM(하드웨어 보안 모듈)이나 Windows 암호화를 이용해 업로드되기 전에 암호화되기 때문에, Intune은 절대로 개인 키에 액세스할 수 없습니다.

- **Microsoft Intune용 PFX 인증서 커넥터**: Intune으로 가져온 PFX 인증서를 디바이스가 요청하면, 암호화된 암호와 인증서 및 디바이스의 공개 키가 커넥터에 전송됩니다.  커넥터는 온-프레미스 개인 키를 이용해 암호를 해독하고, 디바이스 키를 이용해 암호를 다시 암호화한 다음(iOS 사용 시에는 plist 프로필도 암호화) 인증서를 Intune으로 재전송합니다.  그러면 Intune은 인증서를 디바이스에 전송하고, 디바이스는 디바이스의 개인 키를 이용해 인증서 암호를 해독한 다음 인증서를 설치합니다.

## <a name="download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune"></a>Microsoft Intune용 PFX 인증서 커넥터 다운로드, 설치 및 구성

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **테넌트 관리** > **커넥터 및 토큰** > **인증서 커넥터** > **추가**를 선택합니다.

   ![Microsoft Intune용 PFX 인증서 커넥터 다운로드](./media/certificates-imported-pfx-configure/download-imported-pfxconnector.png)

3. 지침에 따라 *Microsoft Intune용 PFX 인증서 커넥터*를 커넥터를 설치할 서버에서 액세스할 수 있는 위치에 다운로드합니다.

4. 다운로드가 끝나면 서버에 로그인하고 설치 관리자(PfxCertificateConnectorBootstrapper.exe)를 실행합니다.  
   - 기본 설치 위치를 사용하면 커넥터는 `Program Files\Microsoft Intune\PFXCertificateConnector`에 설치됩니다.
   - 커넥터 서비스는 로컬 시스템 계정으로 실행됩니다. 인터넷 액세스를 위해 프록시가 필요하다면 로컬 서비스 계정이 서버의 프록시 설정에 액세스할 수 있는지 확인합니다.

5. Microsoft Intune용 PFX 인증서 커넥터가 설치되면 **등록** 탭이 열립니다. Intune에 대한 연결을 사용하도록 설정하려면 **로그인**하고 Azure 글로벌 관리자 또는 Intune 관리자 권한이 있는 계정을 입력합니다.

   > [!WARNING]
   > 기본적으로 Windows Server에서는 **IE 보안 강화 구성**이 **설정** 상태이며, 따라서 Office 365 로그인에 문제가 발생할 수 있습니다.

6. 창을 닫습니다.

7. Microsoft Endpoint Manager 관리 센터에서 **테넌트 관리** > **커넥터 및 토큰** > **인증서 커넥터**로 돌아갑니다. 잠시 후에 녹색 확인 표시가 나타나고 연결 상태가 업데이트됩니다. 이제 커넥터 서버가 Intune과 통신할 수 있습니다.

## <a name="import-pfx-certificates-to-intune"></a>PFX 인증서를 Intune으로 가져오기

사용자 PFX 인증서를 Intune으로 가져올 때는 [Microsoft Graph](https://docs.microsoft.com/graph)를 사용합니다. 도우미 [GitHub PFXImport PowerShell Project](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)를 이용하면 cmdlet을 이용해 작업을 쉽게 진행할 수 있습니다.

Graph를 이용하는 자체 사용자 지정 솔루션을 사용하고 싶다면 [userPFXCertificate 리소스 종류](https://docs.microsoft.com/graph/api/resources/intune-raimportcerts-userpfxcertificate?view=graph-rest-beta)를 사용하세요.

### <a name="build-pfximport-powershell-project-cmdlets"></a>'PFXImport PowerShell Project' cmdlet 빌드

PowerShell cmdlet을 사용하려면 Visual Studio를 이용해 프로젝트를 직접 빌드해야 합니다. 프로세스는 간단하며, 서버에서 실행할 때는 워크스테이션에서 실행하는 것이 좋습니다.  

1. GitHub에서 [Intune-Resource-Access](https://github.com/microsoft/Intune-Resource-Access) 리포지토리로 이동한 다음, 리포지토리를 Git와 함께 컴퓨터에 다운로드하거나 복제하세요.

   ![GitHub 다운로드 단추](./media/certificates-imported-pfx-configure/github-download.png)

2. `.\Intune-Resource-Access-develop\src\PFXImportPowershell\`로 이동한 다음 **PFXImportPS.sln** 파일을 이용해 Visual Studio로 프로젝트를 엽니다.

3. 상단 메뉴에서 **디버그**를 **릴리스**로 변경합니다.

4. **빌드**로 이동해 **Build PFXImportPS**를 선택합니다. 잠시 후 Visual Studio 왼쪽 아래에 **빌드 성공** 확인 메시지가 표시됩니다.

   ![Visual Studio 빌드 옵션](./media/certificates-imported-pfx-configure/vs-build-release.png)

5. 빌드 프로세스는 `.\Intune-Resource-Access-develop\src\PFXImportPowershell\PFXImportPS\bin\Release`에서 PowerShell Module을 사용해 새 폴더를 만듭니다.

   이 **릴리스** 폴더는 다음 단계에서 사용합니다.

### <a name="create-the-encryption-public-key"></a>암호화 공개 키 만들기

PFX 인증서 및 관련 개인 키를 Intune으로 가져옵니다. 개인 키를 보호하는 암호는 온-프레미스에 저장된 공개 키로 암호화됩니다. Windows 암호화, 하드웨어 보안 모듈 또는 다른 암호화 유형을 이용해 공개/개인 키 쌍을 생성하고 저장할 수 있습니다.  사용하는 암호화 유형에 따라 공개/개인 키 쌍을 파일 형식으로 내보내 백업할 수도 있습니다.

PowerShell 모듈은 Windows 암호화를 사용하여 키를 만드는 메서드를 제공합니다. 다른 도구를 이용해 키를 만들 수도 있습니다.  

#### <a name="to-create-the-encryption-key-using-windows-cryptography"></a>Windows 암호화를 이용해 암호화 키 만들기

1. Visual Studio가 만든 *릴리스* 폴더를 **Microsoft Intune용 PFX 인증서 커넥터**를 설치한 서버에 복사합니다. 이 폴더에는 PowerShell 모듈이 있습니다.

2. 서버에서 관리자 권한으로 *PowerShell*을 열고 PowerShell 모듈이 있는 *릴리스* 폴더로 이동합니다.

3. 모듈을 가져오려면 `Import-Module .\IntunePfxImport.psd1`을 실행해 모듈을 가져옵니다.

4. 그런 다음 `Add-IntuneKspKey "Microsoft Software Key Storage Provider" "PFXEncryptionKey"`를 실행합니다.

   > [!TIP]
   > PFX 인증서를 가져올 때 사용한 공급자를 다시 선택해야 합니다. **Microsoft 소프트웨어 키 저장소 공급자**를 이용할 수 있지만, 다른 공급자를 사용할 수도 있습니다. 키 이름도 예제로 제공되며, 원하는 다른 키 이름을 사용해도 됩니다.

   워크스테이션에서 인증서를 가져오고 싶다면, 다음 명령어를 이용해 이 키를 파일로 내보낼 수 있습니다.  `Export-IntunePublicKey -ProviderName "<ProviderName>" -KeyName "<KeyName>" -FilePath "<File path to write to>"`

   가져온 PFX 인증서를 제대로 처리하려면, Microsoft Intune용 PFX 인증서 커넥터를 호스트하는 서버로 개인 키를 가져와야 합니다.

#### <a name="to-use-a-hardware-security-module-hsm"></a>HSM(하드웨어 보안 모듈) 사용

HSM(하드웨어 보안 모듈)을 사용하여 공개/개인 키 쌍을 생성하고 저장할 수 있습니다. 자세한 내용은 HSM 공급자의 설명서를 참조하세요.

### <a name="import-pfx-certificates"></a>PFX 인증서 가져오기

다음 프로세스는 PFX 인증서를 가져오는 예제로 PowerShell cmdlet을 사용합니다. 요구 사항에 맞는 다양한 옵션을 선택할 수 있습니다.

다음 옵션을 사용할 수 있습니다.  
- 용도(태그를 기준으로 인증서를 그룹화):  
  - 할당되지 않음
  - smimeEncryption
  - smimeSigning

- 패딩 체계:  
  - pkcs1
  - oaepSha1
  - oaepSha256
  - oaepSha384
  - oaepSha512

키를 만들 때 사용한 공급자와 일치하는 키 저장소 공급자를 선택합니다.

#### <a name="to-import-the-pfx-certificate"></a>.pfx 인증서 가져오기  

1. 공급자가 제공한 설명서에 따라 아무 CA(인증 기관)에서 인증서를 내보냅니다.  Microsoft Active Directory 인증서 서비스의 경우에는 [이 샘플 스크립트](https://gallery.technet.microsoft.com/Export-CMPfxCertificatesFro-d55f687b)를 사용하면 됩니다.

2. 서버에서 관리자 권한으로 *PowerShell*을 열고 PowerShell 모듈이 있는 *릴리스* 폴더로 이동합니다.

3. 모듈을 가져오려면 `Import-Module .\IntunePfxImport.psd1`을 실행합니다.

4. Intune Graph에 인증하려면 `$authResult = Get-IntuneAuthenticationToken -AdminUserName "<Admin-UPN>"`을 실행합니다.

   > [!NOTE]
   > 인증은 Graph를 대상으로 실행하기 때문에 AppID 사용 권한을 제공해야 합니다. 이 유틸리티를 처음 사용한다면 *전역 관리자*가 필요합니다. PowerShell cmdle은 [PowerShell Intune 샘플](https://github.com/microsoftgraph/powershell-intune-samples)이 사용하는 것과 같은 AppID를 사용합니다.

5. 가져오는 각 PFX 파일의 암호를 `$SecureFilePassword = ConvertTo-SecureString -String "<PFXPassword>" -AsPlainText -Force`를 실행해 안전한 문자열로 변환합니다.

6. **UserPFXCertificate** 개체를 만들려면 `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>"`을 실행합니다.

   예를 들어 `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "C:\temp\userA.pfx" $SecureFilePassword "userA@contoso.com" "Microsoft Software Key Storage Provider" "PFXEncryptionKey" "smimeEncryption" "pkcs1"`를 구성할 수 있습니다.

   > [!NOTE]
   > 커넥터를 설치한 서버가 아닌 다른 시스템에서 인증서를 가져올 때는, 키 파일 경로를 포함하는 다음 명령을 사용해야 합니다. `$userPFXObject = New-IntuneUserPfxCertificate -PathToPfxFile "<FullPathPFXToCert>" $SecureFilePassword "<UserUPN>" "<ProviderName>" "<KeyName>" "<IntendedPurpose>" "<PaddingScheme>" "<File path to public key file>"`

7. `Import-IntuneUserPfxCertificate -AuthenticationResult $authResult -CertificateList $userPFXObject`를 실행해 **UserPFXCertificate** 개체를 Intune으로 가져옵니다.

8. 인증서를 가져왔는지 확인하려면 `Get-IntuneUserPfxCertificate -AuthenticationResult $authResult -UserList "<UserUPN>"`을 실행합니다.

사용 가능한 다른 명령에 대한 자세한 내용은 [GitHub의 PFXImport PowerShell 프로젝트](https://github.com/microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)에 있는 추가 정보 파일을 참조하세요.

## <a name="create-a-pkcs-imported-certificate-profile"></a>PKCS가 가져온 인증서 프로필 만들기

Intune으로 인증서를 가져온 후 **PKCS가 가져온 인증서** 프로필을 생성하여 Azure Active Directory 그룹에 할당합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

3. 다음 속성을 입력합니다.

   - 프로필의 **이름**
   - 선택적으로 설명 설정
   - 프로필을 배포할 **플랫폼**
   - **프로필 형식**을 **PKCS가 가져온 인증서**로 설정

4. **설정**을 선택하고 다음 속성을 입력합니다.

   - **용도**: 이 프로필로 가져온 인증서의 용도를 지정합니다. 관리자는 자신이 원하는 다양한 용도(S/MIME 서명, S/MIME 암호화 등)로 인증서를 가져올 수 있습니다. 인증서 프로필에서 선택한 용도는 인증서 프로필과 가져온 인증서를 올바르게 일치시킵니다. 용도는 가져온 인증서를 그룹화하는 태그이며, 태그와 함께 가져온 인증서가 용도를 반드시 충족하는 것은 아닙니다.  
   - **인증서 유효 기간**: 인증서 템플릿에서 유효 기간을 변경하지 않는 한, 이 옵션의 기본값은 1년입니다.
   - **KSP(키 스토리지 공급자)** : Windows의 경우 디바이스에서 키를 저장할 위치를 선택합니다.

5. **확인** > **만들기**를 선택하여 프로필을 저장합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 새 디바이스 프로필을 [할당](../configuration/device-profile-assign.md)합니다.
