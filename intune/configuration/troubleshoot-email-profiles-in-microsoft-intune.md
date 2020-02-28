---
title: Microsoft Intune의 이메일 프로필 문제 해결 - Azure | Microsoft Docs
description: Microsoft Intune에서 Samsung KNOX Standard Android 디바이스의 중복된 메일 프로필과 오류 등 일반적인 문제와 해결 방법을 확인하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: a19830130f992a002b73402f5e13a8f062539917
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77512673"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Microsoft Intune에서 메일 프로필 관련 일반적인 문제와 해결 방법

몇 가지 일반적인 이메일 프로필 문제와 이 문제를 해결하는 방법을 검토합니다.

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 디바이스를 등록한 사용자에 대한 이메일 프로필이 배포됩니다. 이메일 프로필을 구성하기 위해 Intune은 등록 진행 중 사용자의 이메일 프로필에서 Azure AD(Active Directory) 속성을 사용합니다. [디바이스에 이메일 설정 추가](email-settings-configure.md)를 참고하면 도움이 될 수 있습니다.
- Android Enterprise의 경우, 관리되는 Google Play 스토어를 사용하여 Gmail 또는 Nine for Work를 배포합니다. 해당 단계는 [관리되는 Google Play 앱 추가](../apps/apps-add-android-for-work.md)에 나와 있습니다.
- iOS/iPadOS 및 Android용 Microsoft Outlook은 이메일 프로필을 지원하지 않습니다. 그 대신, 앱 구성 정책을 배포합니다. 자세한 내용은 [Outlook 구성 설정](../apps/app-configuration-policies-outlook.md)을 참조하세요.
- 디바이스 그룹(사용자 그룹 아님)을 대상으로 하는 이메일 프로필이 디바이스에 전달되지 않을 수 있습니다. 디바이스에 기본 사용자가 있는 경우, 디바이스 대상 지정이 작동해야 합니다. 이메일 프로필에 사용자 인증서가 포함된 경우, 사용자 그룹을 대상으로 지정해야 합니다.
- 사용자에게 이메일 프로필에 대한 암호를 입력하라는 요청 메시지가 반복해서 표시될 수 있습니다. 이 시나리오에서는 이메일 프로필에서 참조되는 모든 인증서를 확인합니다. 인증서 중 하나가 사용자를 대상으로 하지 않는 경우, Intune에서 이메일 프로필 배포를 다시 시도합니다.

## <a name="device-already-has-an-email-profile-installed"></a>디바이스에 메일 프로필이 이미 설치되어 있음

사용자가 Intune 또는 Office 365 MDM에 등록하기 전에 이메일 프로필을 만든 경우, Intune에서 배포한 이메일 프로필이 제대로 작동하지 않을 수 있습니다.

- **iOS/iPadOS**: Intune에서는 호스트 이름 및 이메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. 사용자가 만든 메일 프로필이 Intune에서 만든 프로필의 배포를 차단합니다. iOS/iPadOS 사용자는 일반적으로 메일 프로필을 만든 후에 등록을 하므로 이것은 일반적인 문제에 속합니다. 회사 포털 앱에서 사용자가 규정을 준수하지 않으며, 메일 프로필을 제거하라는 메시지를 표시할 수 있습니다.

  사용자는 Intune 프로필을 배포할 수 있도록 메일 프로필을 제거해야 합니다. 이 문제를 방지하려면 사용자에게 등록하도록 지시하고 Intune에서 메일 프로필을 배포하도록 허용합니다. 그러면 사용자는 메일 프로필을 만들 수 있습니다.

- **Windows**: Intune에서는 호스트 이름 및 이메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. Intune은 사용자가 만든 기존 전자 메일 프로필을 덮어씁니다.

- **Samsung KNOX Standard**: Intune에서는 메일 주소를 기반으로 중복된 메일 계정을 식별하고 이를 Intune 프로필로 덮어씁니다. 사용자가 해당 계정을 구성하는 경우 Intune 프로필에 의해 다시 덮어쓰게 됩니다. 이로 인해 계정 구성을 덮어쓰는 사용자에게 혼동이 발생할 수 있습니다.

삼성 KNOX는 호스트 이름을 사용하여 프로필을 식별하지 않습니다. 서로 다른 호스트의 동일한 메일 주소로 배포할 여러 메일 프로필을 만들지 말고 서로 덮어쓰는 것이 좋습니다.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>KNOX Standard 디바이스에 대한 오류 0x87D1FDE8

**문제**: 다양한 Android 디바이스에 대한 Samsung KNOX Standard용 Exchange Active Sync 메일 프로필을 만들고 배포한 후, 디바이스의 속성 > 정책 탭에 **0x87D1FDE8** 또는 **수정 실패**라는 오류가 표시됩니다.

삼성 KNOX 및 소스 정책에 대한 EAS 프로필 구성을 확인하세요. Samsung Notes 동기화 옵션은 더 이상 지원되지 않으며, 해당 옵션은 프로필에서 선택하면 안 됩니다. 디바이스가 최대 24시간까지 정책을 처리하기에 충분한 시간을 갖도록 합니다.

## <a name="unable-to-send-images-from--email-account"></a>전자 메일 계정에서 이미지를 보낼 수 없습니다.

자동으로 구성된 메일 계정이 있는 사용자가 디바이스에서 그림이나 이미지를 보낼 수 없습니다. 이 시나리오는 **타사 애플리케이션에서 이메일을 보내도록 허용** 옵션이 활성화되지 않은 경우에 발생할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **구성 프로필**을 선택합니다.
3. 메일 프로필 > **속성** > **설정**을 선택합니다.
4. **타사 애플리케이션에서 메일을 보내도록 허용** 설정을 **사용**으로 설정합니다.

## <a name="next-steps"></a>다음 단계

[Microsoft의 지원 도움말](../fundamentals/get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.
