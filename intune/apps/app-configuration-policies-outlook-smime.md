---
title: Microsoft Intune에서 iOS용 Outlook을 사용하여 S/MIME 구성
description: Microsoft Intune에서 iOS용 Outlook을 사용하는 S/MIME을 이해합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lance
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c9572f4accb1be232d4667d99b98beff90d81379
ms.sourcegitcommit: edd06a494a241d198ca9b0d3030c92195976e0d3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2019
ms.locfileid: "75000417"
---
# <a name="configure-smime-with-outlook-for-ios"></a>iOS용 Outlook을 사용하여 S/MIME 구성

S/MIME(Secure/Multipurpose Internet Mail Extensions)은 EAS(Exchange ActiveSync) 계정에서 송수신되는 메일에 대해 추가적인 보안 계층을 제공합니다. [Microsoft Outlook](https://aka.ms/omsmime)은 S/MIME을 활용하여 사용자가 보내는 메시지와 첨부 파일을 모두 암호화할 수 있도록 함으로써 의도한 받는 사람만 Office 365 계정을 사용하여 메시지 내용을 읽고 액세스할 수 있도록 합니다. 또한 사용자는 메시지에 디지털로 서명하여 받는 사람이 보낸 사람의 ID를 확인하고 메시지가 변조되지 않았는지 확인하도록 할 수 있습니다. 이 기능은 인증서를 활용하여 가능합니다. 자세한 내용은 [S/MIME 이해](https://docs.microsoft.com/previous-versions/tn-archive/aa995740(v=exchg.65)?redirectedfrom=MSDN)를 참조하세요.

> [!NOTE]
> 이 기능은 지연되었지만 곧 릴리스될 예정입니다.

> [!NOTE]
> 이 항목에서는 [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431)를 통해 신뢰할 수 있는 루트 인증서를 배포하는 방법을 설명합니다. Microsoft Endpoint Manager는 모든 엔드포인트를 관리하기 위한 단일 통합형 엔드포인트 관리 플랫폼입니다. 이 Microsoft Endpoint Manager 관리 센터는 ConfigMgr와 Microsoft Intune에 연결됩니다.

## <a name="about-message-encryption"></a>메시지 암호화 정보
사용자는 조직의 사용자와 암호화 인증서의 퍼블릭 부분을 보유하는 조직 외부 사용자에게 암호화된 메시지를 보낼 수 있습니다. 암호화 인증서와 연결된 퍼블릭 키는 항상 암호화된 메시지 받는 사람이 보호해야 합니다. 암호화 인증서의 퍼블릭 키는 받는 사람이 메시지를 해독하는 데 사용합니다.

암호화된 메시지는 메시지를 암호화할 때 사용한 인증서가 있는 받는 사람만 읽을 수 있습니다. 암호화 인증서를 사용할 수 없는 받는 사람에게 암호화된 메시지를 보내려고 하면 메일을 보내기 전에 앱에서 이러한 받는 사람을 제거할지 묻는 메시지를 표시합니다.

## <a name="about-digital-signatures"></a>디지털 서명 정보
디지털 서명된 메시지는 메시지가 변조되지 않았으며 보낸 사람의 ID가 진짜임을 받는 사람에게 다시 보장해 줍니다. 받는 사람은 S/MIME을 지원하는 메일 클라이언트를 사용하는 경우에만 디지털 서명을 확인할 수 있습니다.

## <a name="prerequisites"></a>전제 조건
- iOS용 Outlook은 Office 365 계정에서 S/MIME만 지원합니다.
- Office 365에 대해 S/MIME을 구성해야 합니다. 자세한 내용은 [Office 365에서 S/MIME을 구성하는 방법](https://techcommunity.microsoft.com/t5/Exchange-Team-Blog/How-to-Configure-S-MIME-in-Office-365/ba-p/584516)을 참조하세요.
- 서명 및 암호화에 사용할 수 있는 인증서를 발급할 수 있는 인증 기관이 있어야 합니다.
- Endpoint Manager를 통해 신뢰할 수 있는 루트 인증서를 배포합니다. 자세한 내용은 [신뢰할 수 있는 인증서 프로필 만들기](~/protect/certificates-configure.md#create-trusted-certificate-profiles)를 참조하세요.
- 암호화 인증서를 Endpoint Manager로 가져와야 합니다. 자세한 내용은 [가져온 PKCS 인증서를 Intune을 사용하여 구성 및 사용](~/protect/certificates-imported-pfx-configure.md)을 참조하세요.
- Microsoft Intune용 PFX 인증서 커넥터를 설치하고 구성합니다. 자세한 내용은 [Microsoft Intune용 PFX 인증서 커넥터 다운로드, 설치 및 구성](~/protect/certificates-imported-pfx-configure.md#download-install-and-configure-the-pfx-certificate-connector-for-microsoft-intune)을 참조하세요.
- Endpoint Manager에서 자동으로 신뢰할 수 있는 루트 및 S/MIME 인증서를 받으려면 디바이스를 MDM에 등록해야 합니다.

> [!IMPORTANT]
> iOS용 Outlook에서 S/MIME 암호화 인증서를 사용하려면 Microsoft Intune용 업데이트된 PFX 커넥터(버전 6.1911.11.0 이상)를 다운로드하여 설치해야 합니다.

## <a name="smime-support-in-outlook-for-ios"></a>iOS용 Outlook의 S/MIME 지원
iOS용 Outlook은 인증서를 사용하여 메시지의 S/MIME 서명 및 암호화를 지원합니다. 많은 고객들은 서명 및 암호화를 모두 지원하는 단일 인증서를 보유하지 않고 별도의 서명 및 암호화 인증서를 보유합니다. 암호화 인증서는 개별 사용자의 등록된 디바이스 간에 공유되지만, 서명 인증서는 일반적으로 개별 사용자의 등록된 디바이스에서 고유합니다. 사용자는 종종 S/MIME을 수년 동안 사용하게 되며, 인증서가 갱신됨에 따라 점점 다른 암호화 인증서를 사용하게 됩니다. 이전에 해당 인증서를 사용하여 암호화한 메일을 읽을 수 있도록 프라이빗 키를 비롯한 암호화 인증서 기록이 사용자의 디바이스에 존재해야 합니다. 서명 및 암호화를 지원하는 단일 인증서를 사용할 수도 있습니다.

iOS용 Outlook에서는 S/MIME에 사용할 수 있도록 디바이스에 인증서를 제공하는 다음과 같은 두 가지 방법을 지원합니다.

- **사용자**는 S/MIME 인증서를 자신에게 메일로 보낸 후 모바일 디바이스의 iOS용 Outlook 내에서 첨부 파일의 인증서를 설치할 수 있습니다.
- **관리자**는 모든 인증 기관에서 Endpoint Manager로 암호화 인증서 기록을 가져올 수 있습니다. 그러면 Endpoint Manager는 사용자가 등록하는 모든 디바이스에 해당 인증서를 자동으로 배달합니다. 일반적으로 인증서 서명에는 SCEP(단순 인증서 등록 프로토콜)가 사용됩니다. SCEP를 사용하면 프라이빗 키가 생성된 후 등록된 디바이스에 저장되며, 사용자가 등록하는 각 디바이스에 고유한 인증서가 전달되어 부인 방지에 사용될 수 있습니다. 관리자는 사용자의 암호화 인증서 기록을 Endpoint Manager로 가져옵니다. 그러면 Endpoint Manager에서 사용자의 모든 암호화 인증서를 해당 사용자가 등록한 모든 디바이스로 전달합니다. 마지막으로, Endpoint Manager는 NIST 800-157 표준을 지원해야 하는 고객에 대해 파생 자격 증명을 지원합니다. iOS에서 회사 포털은 Intune에서 서명 및 암호화 인증서를 검색하는 데 사용됩니다.

## <a name="configuring-outlook-for-ios-smime-in-endpoint-manager"></a>Endpoint Manager에서 iOS S/MIME에 대해 Outlook 구성
iOS용 Outlook에서 사용할 수 있는 S/MIME 인증서를 자동으로 배달하는 것을 포함하여 Endpoint Manager에서 iOS S/MIME에 대해 Outlook을 구성하려면 다음 단계를 사용합니다.

### <a name="add-the-microsoft-outlook-app"></a>Microsoft Outlook 앱 추가
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. 앱 스토어의 iOS용 Microsoft Outlook 앱을 Endpoint Manager에 추가하거나 Apple Volume Purchase Program에서 iOS용 Outlook을 동기화합니다. 자세한 내용은 [Microsoft Intune에 iOS 스토어 앱 추가](~/apps/store-apps-ios.md) 또는 [Microsoft Intune을 사용하여 Apple Volume Purchase Program을 통해 구매한 iOS 및 macOS 앱을 관리하는 방법](~/apps/vpp-apps-ios.md)을 참조하세요.

### <a name="create-the-outlook-for-ios-smime-configuration-policy"></a>iOS용 Outlook S/MIME 구성 정책 만들기

다음 단계를 사용하여 Endpoint Manager에서 iOS용 Outlook S/MIME 정책을 만들고 구성할 수 있습니다. 이러한 설정은 서명 및 암호화 인증서의 자동 배달 기능을 제공합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **앱** > **앱 구성 정책** > **추가**를 선택합니다.<br>
**구성 정책 추가** 창이 표시됩니다.
2. 구성 정책의 **이름** 및 **설명**을 입력합니다.
3. **디바이스 등록 유형**에서 **관리되는 디바이스**를 선택합니다.
4. **플랫폼**으로 **iOS/iPadOS**를 선택합니다.
5. **필요한 앱 선택**을 클릭하여 이전에 추가한 iOS용 Microsoft Outlook 앱을 찾아 연결합니다. 
6. **구성 설정**을 클릭하여 구성 설정을 추가합니다. 
    - **구성 설정 형식** 옆에 있는 **구성 디자이너 사용**을 선택하고 기본 설정을 적용합니다. 자세한 내용은 [Microsoft Outlook 구성 설정](~/apps/app-configuration-policies-outlook.md)을 참조하세요.
7. **S/MIME**을 클릭하여 **Outlook S/MIME 설정**을 표시합니다.
8. **S/MIME 사용**을 **예**로 설정합니다.
9. **Intune에서 S/MIME 인증서 배포**를 **예**로 설정합니다.
10. **인증서 프로필 유형** 옆에 있는 **서명 인증서**에서 다음 옵션 중 하나를 선택합니다.
    - **SCEP** – Microsoft Outlook에서 서명하는 데 사용할 수 있는 디바이스 및 사용자에 대해 고유한 인증서를 만듭니다. 관련 내용은 [Intune을 사용하여 SCEP를 지원하도록 인프라 구성](~/protect/certificates-scep-configure.md) 및 [SCEP 인증서 프로필 만들기](~/protect/certificates-profile-scep.md#create-a-scep-certificate-profile)를 참조하세요. 
    - **PKCS 가져온 인증서** – 사용자에게 고유하지만 디바이스 간에 공유 가능하고, 관리자가 사용자를 대신해서 Endpoint Manager로 가져올 수 있는 인증서를 사용합니다. 인증서는 사용자가 등록하는 모든 디바이스로 배달됩니다. Endpoint Manager는 등록된 사용자에 해당하는 디바이스에 배달할 서명을 지원하는 가져온 인증서를 자동으로 선택합니다.
    - **파생된 자격 증명** – 디바이스에 이미 있으며 서명에 사용할 수 있는 인증서를 사용합니다. Intune의 파생된 자격 증명 흐름을 사용하여 디바이스에서 인증서를 검색해야 합니다.
11. **인증서 프로필 유형** 옆에 있는 **암호화 인증서**에서 다음 옵션 중 하나를 선택합니다.
    - **PKCS 가져온 인증서** – 사용자가 등록하는 모든 디바이스에서 관리자가 Endpoint Manager로 가져온 모든 암호화 인증서를 배달합니다. Endpoint Manager는 가져온 인증서 또는 등록된 사용자에게 해당하는 디바이스로 전달할 암호화를 지원하는 인증서를 자동으로 선택합니다.
    - **파생된 자격 증명** – 디바이스에 이미 있으며 서명에 사용할 수 있는 인증서를 사용합니다. Intune의 파생된 자격 증명 흐름을 사용하여 디바이스에서 인증서를 검색해야 합니다.
12. **최종 사용자 알림** 옆에서 **회사 포털** 또는 **메일**을 선택하여 최종 사용자에게 iOS용 Outlook의 S/MIME 인증서를 검색할 것을 알리도록 선택합니다.

    iOS에서 사용자는 회사 포털 앱을 사용하여 S/MIME 인증서를 검색해야 합니다. Endpoint Manager는 회사 포털의 알림 섹션, 푸시 알림 및/또는 메일을 통해 S/MIME 인증서를 검색하기 위해 회사 포털을 시작해야 함을 사용자에게 알립니다. 알림 중 하나를 클릭하면 사용자에게 인증서 검색 진행 상태를 알려 주는 방문 페이지가 표시됩니다. 인증서가 검색되면 사용자는 iOS용 Microsoft Outlook에서 S/MIME을 사용하여 메일에 서명하고 암호화할 수 있습니다.
    
    최종 사용자 알림에는 다음과 같은 옵션이 있습니다.
       - **회사 포털** – 이 옵션을 선택하는 경우 사용자가 디바이스에서 푸시 알림을 받게 됩니다. 이 알림을 통해 S/MIME 인증서를 검색할 회사 포털의 방문 페이지로 이동됩니다.
        - **메일** – 최종 사용자에게 S/MIME 인증서를 검색하기 위해 회사 포털을 시작해야 함을 사실을 알리는 메일을 보냅니다. 사용자가 등록된 iOS 디바이스에서 메일의 링크를 클릭하면 인증서를 검색하기 위한 회사 포털로 리디렉션됩니다.
    
13. **할당**을 선택하여 Azure AD 그룹에 앱 구성 정책을 할당합니다. 자세한 내용은 [Microsoft Intune을 사용하여 그룹에 앱 할당](~/apps/apps-deploy.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- 자세한 내용은 [Microsoft Intune용 앱 구성 정책](app-configuration-policies-overview.md)을 참조하세요.
