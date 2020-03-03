---
title: S/MIME를 사용하여 메일 서명 및 암호화 - Microsoft Intune - Azure | Microsoft Docs
description: 디바이스에서 이메일 서명 및 암호화하기 위해 Microsoft Intune에서 이메일 디지털 인증서를 사용하는 방법을 알아봅니다. 이러한 인증서는 S/MIME라고 하고 디바이스 구성 프로필을 사용하여 구성됩니다. 서명 및 암호화 인증서는 PKCS 또는 프라이빗 인증서를 사용하고 커넥터를 사용하여 인증서를 가져옵니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15147a1d9ffd82e2f900d15c4a9d2b4d23ad23e3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515155"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>Intune에서 이메일 서명 및 암호화를 위한 S/MIME 개요

S/MIME 인증서라고도 하는 이메일 인증서는 암호화 및 암호 해독을 통해 이메일 통신에 추가 보안을 제공합니다. Microsoft Intune은 S/MIME를 사용하여 다음 플랫폼을 실행하는 모바일 디바이스에 이메일을 서명하고 암호화할 수 있습니다.

- Android
- iOS/iPadOS
- macOS
- Windows 10 이상
- Windows Phone

iOS/iPadOS 디바이스에서 S/MIME 및 인증서를 사용하여 수신 및 송신 메일에 서명하고 암호화하는 Intune 관리 메일 프로필을 만들 수 있습니다. 다른 플랫폼의 경우 S/MIME가 지원되거나 지원되지 않을 수 있습니다. 지원되는 경우 S/MIME 서명 및 암호화를 사용하는 인증서를 설치할 수 있습니다. 그런 다음, 최종 사용자는 해당 이메일 애플리케이션에서 S/MIME를 활성화합니다.

Exchange를 사용한 S/MIME 이메일 서명 및 암호화에 대한 자세한 내용은 [메시지 서명 및 암호화를 위한 S/MIME](https://docs.microsoft.com/Exchange/policy-and-compliance/smime)를 참조하세요.

이 문서에서는 S/MIME 인증서를 사용하여 디바이스에서 이메일 서명 및 암호화하는 방법에 대한 개요를 제공합니다.

## <a name="signing-certificates"></a>서명 인증서

클라이언트 이메일 앱은 서명에 사용되는 인증서를 통해 이메일 서버와 안전하게 통신할 수 있습니다.

서명 인증서를 사용하려면 서명을 중점적으로 취급하는 CA(인증 기관)에서 템플릿을 만듭니다. Microsoft Active Directory 인증 기관에서 [서버 인증서 템플릿 구성](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template)은 인증서 템플릿을 만드는 단계를 나열합니다.

Intune에서 서명 인증서는 PKCS 인증서를 사용합니다. [PKCS 인증서 구성 및 사용](certficates-pfx-configure.md)에서는 Intune 환경의 PKCS 인증서를 배포하고 사용하는 방법을 설명합니다. 관련 단계는 다음과 같습니다.

- PKCS 인증서 요청을 지원하려면 Microsoft Intune Certificate Connector를 다운로드하고 설치합니다.
- 디바이스에 신뢰할 수 있는 루트 인증서 프로필을 만듭니다. 이 단계에는 인증 기관에 신뢰할 수 있는 루트 및 중간 인증서를 사용한 다음, 프로필을 디바이스에 배포하는 작업이 포함됩니다.
- 생성한 인증서 템플릿을 사용하여 PKCS 인증서 프로필을 만듭니다. 이 프로필은 디바이스에 서명 인증서를 발급하고 PKCS 인증서 프로필을 디바이스에 배포합니다.

특정 사용자에 대한 서명 인증서를 가져올 수도 있습니다. 서명 인증서는 사용자가 등록하는 모든 디바이스에 배포됩니다. 인증서를 Intune에 가져오려면 [GitHub의 PowerShell cmdlet](https://github.com/Microsoft/Intune-Resource-Access)을 사용합니다. Intune에서 가져온 PKCS 인증서를 배포하여 이메일 서명에 사용하려면 [Intune과 함께 PKCS 인증서 구성 및 사용](certficates-pfx-configure.md)의 단계를 따릅니다. 관련 단계는 다음과 같습니다.

- Microsoft Intune용 PFX 인증서 커넥터를 다운로드하여 설치합니다. 이 커넥터는 가져온 PKCS 인증서를 디바이스에 제공합니다.
- S/MIME 이메일 서명 인증서를 Intune으로 가져옵니다.
- PKCS가 가져온 인증서 프로필을 만듭니다. 이 프로필은 가져온 PKCS 인증서를 적절한 사용자의 디바이스에 제공합니다.

## <a name="encryption-certificates"></a>암호화 인증서

암호화에 사용되는 인증서는 암호화된 이메일의 암호가 의도된 수신자에 의해서만 해독될 수 있음을 확인합니다. S/MIME 암호화는 이메일 통신에 사용할 수 있는 추가 보안 계층입니다.

다른 사용자에게 암호화된 이메일을 보낼 때 해당 사용자의 암호화 인증서 공개 키를 가져오고 보내는 이메일을 암호화합니다. 수신자는 해당 디바이스의 프라이빗 키를 사용하여 이메일의 암호를 해독합니다. 사용자는 이메일을 암호화하는 데 사용되는 인증서 기록을 가질 수 있습니다. 이러한 각 인증서는 이메일의 암호가 성공적으로 해독되도록 특정 사용자의 모든 디바이스에 배포되어야 합니다.

Intune에서 이메일 암호화 인증서를 생성하지 않는 것이 좋습니다. Intune은 암호화를 지원하는 PKCS 인증서의 발급을 지원하지만 Intune은 디바이스마다 고유한 인증서를 만듭니다. 디바이스마다 고유한 인증서는 모든 사용자의 디바이스에서 암호화 인증서를 공유해야 하는 S/MIME 암호화 시나리오에는 적합하지 않습니다.

Intune을 사용하여 S/MIME 인증서를 배포하려면 사용자의 모든 암호화 인증서를 Intune으로 가져와야 합니다. 그러면, Intune에서는 사용자가 등록하는 각 디바이스에 이러한 모든 인증서를 배포합니다. 인증서를 Intune에 가져오려면 [GitHub의 PowerShell cmdlet](https://github.com/Microsoft/Intune-Resource-Access)을 사용합니다.

이메일 암호화에 사용되는 Intune에서 가져온 PKCS 인증서를 배포하려면 [Intune과 함께 PKCS 인증서 구성 및 사용](certficates-pfx-configure.md)의 단계를 따릅니다. 관련 단계는 다음과 같습니다.

- Microsoft Intune용 PFX 인증서 커넥터를 다운로드하여 설치합니다. 이 커넥터는 가져온 PKCS 인증서를 디바이스에 제공합니다.
- S/MIME 이메일 암호화 인증서를 Intune으로 가져옵니다.
- PKCS가 가져온 인증서 프로필을 만듭니다. 이 프로필은 가져온 PKCS 인증서를 적절한 사용자의 디바이스에 제공합니다.

 > [!NOTE]
 > 가져온 S/MIME 암호화 인증서는 회사 데이터가 제거되거나 사용자가 관리 대상에서 등록 취소될 때 Intune에 의해 제거됩니다. 그러나 인증서는 인증 기관에서 해지되지 않습니다.

## <a name="smime-email-profiles"></a>S/MIME 이메일 프로필

S/MIME 서명 및 암호화 인증서 프로필을 만든 후 [iOS/iPadOS 기본 메일에 S/MIME를 사용](../configuration/email-settings-ios.md)할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [인증서에 SCEP 사용](certificates-scep-configure.md)
- [PKCS 인증서 사용](certficates-pfx-configure.md)
- [파트너 CA 사용](certificate-authority-add-scep-overview.md)
- [Symantec PKI 관리자 웹 서비스에서 PKCS 인증서 발급](certificates-digicert-configure.md)
