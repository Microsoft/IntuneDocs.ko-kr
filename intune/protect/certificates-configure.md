---
title: Microsoft Intune - Azure에서 인증서 프로필 만들기 | Microsoft Docs
description: Microsoft Intune을 통해 SCEP(단순 인증서 등록 프로토콜) 또는 PKCS(공개 키 암호 표준) 인증서 및 인증서 프로필을 사용하는 방법에 대해 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5092fa37f0bf6bd1320fa06fa58ac5e36f55aa3c
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74410192"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Microsoft Intune의 인증에 인증서 사용

Intune에서 인증서를 사용하여 VPN, Wi-Fi 또는 메일 프로필을 통해 애플리케이션 및 회사 리소스에서 사용자를 인증합니다. 인증서를 사용하여 해당 연결을 인증하는 경우 최종 사용자가 사용자 이름과 암호를 입력하지 않아도 되므로 원활하게 액세스할 수 있습니다. S/MIME을 사용하여 메일을 서명 및 암호화하는 데도 인증서가 사용됩니다.

## <a name="intune-supported-certificates-and-usage"></a>Intune에서 지원하는 인증서 및 용도

| 유형              | 인증 | S/MIME 서명 | S/MIME 암호화  |
|--|--|--|--|
| PKCS(공개 키 암호화 표준)에 따라 가져온 인증서 |  | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png)|
| PKCS #12(또는 PFX)    | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) |  |
| SCEP(단순 인증서 등록 프로토콜)  | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | |

이러한 인증서를 배포하려면 인증서 프로필을 만들어 디바이스에 할당합니다.

사용자가 만드는 각 개별 인증서 프로필은 단일 플랫폼을 지원합니다. 예를 들어, PKCS 인증서를 사용하는 경우 Android용 PKCS 인증서 프로필과 별도의 iOS용 PKCS 인증서 프로필을 만듭니다. 또한 이러한 두 플랫폼에 SCEP 인증서를 사용하는 경우 Android용 SCEP 인증서 프로필과 iOS용 프로필을 따로 만듭니다.

### <a name="general-considerations-when-you-use-a-microsoft-certification-authority"></a>Microsoft 인증 기관을 사용하는 경우의 일반적인 고려 사항

Microsoft CA(인증 기관)를 사용하는 경우:

- SCEP 인증서 프로필을 사용하려면 Intune에서 사용할 [NDES(네트워크 디바이스 등록 서비스) 서버를 설정](certificates-scep-configure.md#set-up-ndes)해야 합니다.
- 다음 인증서 프로필 유형을 사용하려면 [Microsoft Intune 인증서 커넥터를 설치](certificates-scep-configure.md#install-the-intune-certificate-connector)해야 합니다.
  - SCEP 인증 프로필
  - PKCS 인증서 프로필

- PKCS 가져온 인증서를 사용하려면
  - [Microsoft Intune용 PFX 인증서 커넥터를 설치합니다](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune).
  - 인증 기관에서 인증서를 내보낸 후 Microsoft Intune으로 가져옵니다. [PFXImport PowerShell 프로젝트](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)를 참조하세요.

- 다음 메커니즘을 사용하여 인증서를 배포합니다.
  - 루트 또는 중간(발급) CA에서 디바이스에 신뢰할 수 있는 루트 CA 인증서를 배포하기 위한 [신뢰할 수 있는 인증서 프로필](certificates-configure.md#create-trusted-certificate-profiles)
  - SCEP 인증서 프로필
  - PKCS 인증서 프로필
  - PKCS 가져온 인증서 프로필

### <a name="general-considerations-when-you-use-a-third-party-certification-authority"></a>타사 인증 기관을 사용하는 경우의 일반적인 고려 사항

타사 CA(인증 기관)를 사용하는 경우:

- SCEP 인증서 프로필을 만들려면
  - [지원되는 파트너 중 하나](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners)에서 제공한 타사 CA와의 연결을 설정합니다. 설정에는 타사 CA의 지침에 따라 Intune과 CA의 연결을 완료하는 과정이 포함됩니다.
  - SCEP 인증서 챌린지 유효성 검사를 수행할 수 있도록 Intune에 권한을 위임하는 [애플리케이션을 Azure AD에서 만듭니다](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).

- PKCS에 따라 가져온 인증서를 사용하려면 [Microsoft Intune용 PFX 인증서 커넥터를 설치](certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)해야 합니다.

- 다음 메커니즘을 사용하여 인증서를 배포합니다.
  - 루트 또는 중간(발급) CA에서 디바이스에 신뢰할 수 있는 루트 CA 인증서를 배포하기 위한 [신뢰할 수 있는 인증서 프로필](certificates-configure.md#create-trusted-certificate-profiles)
  - SCEP 인증서 프로필
  - PKCS 인증서 프로필 *([Digicert PKI 플랫폼](certificates-digicert-configure.md)에서만 지원됨)*
  - PKCS 가져온 인증서 프로필

## <a name="supported-platforms-and-certificate-profiles"></a>지원되는 플랫폼 및 인증서 프로필

| 플랫폼              | 신뢰할 수 있는 인증서 프로필 | PKCS 인증서 프로필 | SCEP 인증서 프로필 | PKCS 가져온 인증서 프로필  |
|--|--|--|--|---|
| Android 디바이스 관리자 | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png)|  ![지원됨](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> - 완전 관리형(장치 소유자)   | ![지원됨](./media/certificates-configure/green-check.png) |   | ![지원됨](./media/certificates-configure/green-check.png) |   |
| Android Enterprise <br> - 전용(장치 소유자)   | ![지원됨](./media/certificates-configure/green-check.png)  |   | ![지원됨](./media/certificates-configure/green-check.png)  |   |
| Android Enterprise <br> - 회사 프로필    | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) |
| iOS                   | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) |
| macOS                 | ![지원됨](./media/certificates-configure/green-check.png) |  ![지원됨](./media/certificates-configure/green-check.png) |![지원됨](./media/certificates-configure/green-check.png)|![지원됨](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![지원됨](./media/certificates-configure/green-check.png)  |  | ![지원됨](./media/certificates-configure/green-check.png)| ![지원됨](./media/certificates-configure/green-check.png) |
| Windows 8.1 이상 |![지원됨](./media/certificates-configure/green-check.png)  |  |![지원됨](./media/certificates-configure/green-check.png) |   |
| Windows 10 이상  | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) | ![지원됨](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>신뢰할 수 있는 루트 CA 인증서 내보내기

PKCS, SCEP 및 PKCS 가져온 인증서를 사용하려면 디바이스가 루트 인증 기관을 신뢰해야 합니다. 트러스트를 설정하기 위해 신뢰할 수 있는 루트 CA 인증서뿐만 아니라 중간 또는 발급 인증 기관 인증서를 퍼블릭 인증서(.cer)로서 내보냅니다. 발급 CA 또는 발급 CA를 신뢰하는 디바이스에서 이러한 인증서를 가져올 수 있습니다.

인증서를 내보내려면 인증 기관에 대한 설명서를 참조하세요. 공용 인증서를 .cer 파일로 내보내야 합니다.  프라이빗 키인 .pfx 파일은 내보내지 마세요.

해당 인증서를 디바이스에 배포하기 위해 [신뢰할 수 있는 인증서 프로필을 만들 때는 ](#create-trusted-certificate-profiles) 이 .cer 파일을 사용합니다.

## <a name="create-trusted-certificate-profiles"></a>신뢰할 수 있는 인증서 프로필 만들기

SCEP, PKCS 또는 PKCS 가져온 인증서 프로필을 만들려면 먼저 신뢰할 수 있는 인증서 프로필을 만듭니다. 신뢰할 수 있는 인증서 프로필을 배포하면 각 디바이스가 CA의 합법성을 인정합니다. SCEP 인증서 프로필은 신뢰할 수 있는 인증서 프로필을 직접 참조합니다. PKCS 인증서 프로필은 신뢰할 수 있는 인증서 프로필을 직접 참조하지 않고, CA를 호스트하는 서버를 직접 참조합니다. PKCS 가져온 인증서 프로필은 신뢰할 수 있는 인증서 프로필을 직접 참조하지 않고, 디바이스에서 이 프로필을 사용할 수 있습니다. 디바이스에 신뢰할 수 있는 인증서 프로필을 배포하면 이 트러스트가 설정됩니다. 디바이스에서 루트 CA를 신뢰하지 않는 경우 SCEP 또는 PKCS 인증서 프로필 정책이 실패합니다.

SCEP, PKCS 및 PKCS 가져온 인증서 프로필의 경우처럼 지원하려는 각 디바이스 플랫폼에 대해 별도의 신뢰할 수 있는 인증서 프로필을 만듭니다.

### <a name="to-create-a-trusted-certificate-profile"></a>신뢰할 수 있는 인증서 프로필을 만들려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

   ![Intune으로 이동하여 신뢰할 수 있는 인증서에 대한 새 프로필 만들기](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. 다음 속성을 입력합니다.

   - 프로필의 **이름**
   - 선택적으로 **설명** 설정
   - 프로필을 배포할 **플랫폼**
   - **프로필 형식**을 **신뢰할 수 있는 인증서**로 설정

4. **설정**을 선택한 후 이 인증서 프로필에서 사용하기 위해 내보낸 신뢰할 수 있는 루트 CA 인증서 .cer 파일을 찾은 다음, **확인**을 선택합니다.

5. Windows 8.1 및 Windows 10 디바이스에 한해 신뢰할 수 있는 인증서의 **대상 저장소**를 선택합니다.

   - **컴퓨터 인증서 저장소 - 루트**
   - **컴퓨터 인증서 저장소 - 중간**
   - **사용자 인증서 저장소 - 중간**

6. 작업이 완료되면 **확인**을 선택하고 **프로필 만들기** 창으로 돌아와서 **만들기**를 선택합니다.

프로필은 *디바이스 구성 - 구성 프로필* 창의 프로필 목록에 나타나며, 프로필 유형은 **신뢰할 수 있는 인증서**입니다. SCEP 또는 PKCS 인증서를 사용하는 디바이스에 이 프로필을 할당해야 합니다. 이 프로필을 그룹에 할당하려면 [디바이스 프로필 할당](../configuration/device-profile-assign.md)을 참조하세요.

> [!NOTE]
> Android 디바이스에 제3자가 신뢰할 수 있는 인증서를 설치했다는 메시지가 표시될 수 있습니다.

## <a name="additional-resources"></a>추가 리소스

- [디바이스 프로필 할당](../configuration/device-profile-assign.md)  
- [S/MIME를 사용하여 이메일 서명 및 암호화](certificates-s-mime-encryption-sign.md)  
- [타사 인증 기관 사용](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>다음 단계

사용하려는 각 플랫폼용으로 SCEP, PKCS 또는 PKCS 가져온 인증서 프로필을 만듭니다. 계속하려면 다음 문서를 참조하세요.

- [Intune을 사용하여 SCEP 인증서를 지원하도록 인프라 구성](certificates-scep-configure.md)  
- [Intune을 사용하여 PKCS 인증서 구성 및 관리](certficates-pfx-configure.md)  
- [PKCS 가져온 인증서 프로필 만들기](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)
