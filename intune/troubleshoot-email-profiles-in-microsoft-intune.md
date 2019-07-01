---
title: Microsoft Intune의 이메일 프로필 문제 해결 - Azure | Microsoft Docs
description: Microsoft Intune에서 Samsung KNOX Standard Android 디바이스의 중복된 메일 프로필과 오류 등 일반적인 문제와 해결 방법을 확인하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/17/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2246e3f6faa853f620327558a7faf4dc9d6a6e85
ms.sourcegitcommit: 43ba5a05b2e1dc1997126d3574884f65cde449c7
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67197504"
---
# <a name="common-issues-and-resolutions-with-email-profiles-in-microsoft-intune"></a>Microsoft Intune에서 메일 프로필 관련 일반적인 문제와 해결 방법

몇 가지 일반적인 이메일 프로필 문제와 이 문제를 해결하는 방법을 검토합니다.

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 장치를 등록 한 사용자에 대 한 전자 메일 프로필 배포 됩니다. 전자 메일 프로필을 구성 하려면 Intune 등록 중 사용자의 전자 메일 프로필에 Azure Active Directory (AD) 속성을 사용 하 여 합니다. [장치에 전자 메일 설정을 추가](email-settings-configure.md) 은 좋은 리소스일 수 있습니다.
- Configuration Manager 하이브리드에서 Intune 독립 실행형으로 마이그레이션한 후 7 일 동안 Configuration Manager 하이브리드에서 전자 메일 프로필을 장치에 남아 있습니다. 이는 예상된 동작입니다. 더 빨리 제거 전자 메일 프로필이 필요한 경우에 문의 [Intune 지원](get-support.md)합니다.
- Android Enterprise에 대 한 Gmail 또는 관리 되는 Google Play 스토어를 사용 하 여 작업에 대 한 9를 배포 합니다. [관리 되는 Google Play 앱 추가](apps-add-android-for-work.md) 단계를 나열 합니다.
- Android 및 iOS 용 Microsoft Outlook 전자 메일 프로필을 지원 하지 않습니다. 대신, 앱 구성 정책을 배포 합니다. 자세한 내용은 [Outlook 구성 설정을](app-configuration-policies-outlook.md)합니다.
- 장치에 전자 메일 프로필 (사용자 그룹이 아닌) 장치 그룹을 대상으로 배달할 수 있습니다. 장치 기본 사용자가 하는 경우 다음 장치를 대상으로 작동 해야 합니다. 전자 메일 프로필에서 사용자 인증서를 포함 하는 경우에 대상 사용자 그룹을 해야 합니다.
- 사용자는 반복적으로 전자 메일 프로필에 대 한 암호를 입력 하 라는 메시지가 될 수 있습니다. 이 시나리오에서는 전자 메일 프로필에서 참조 하는 모든 인증서를 확인 합니다. 사용자에 게 목표가 아닌 인증서 중 하나를 하는 경우 Intune 전자 메일 프로필 배포를 다시 시도 합니다.

## <a name="device-already-has-an-email-profile-installed"></a>디바이스에 메일 프로필이 이미 설치되어 있음

사용자가 Intune 또는 Office 365 MDM에 등록 하기 전에 전자 메일 프로필을 만들거나, Intune에서 배포 된 전자 메일 프로필 예상 대로 작동 하지 않을 수 있습니다.

- **iOS**: Intune에서는 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. 사용자가 만든 메일 프로필이 Intune에서 만든 프로필의 배포를 차단합니다. iOS 사용자는 일반적으로 이메일 프로필을 만든 후에 등록을 하므로 이것은 일반적인 문제입니다. 회사 포털 앱에서 사용자가 규정을 준수하지 않으며, 메일 프로필을 제거하라는 메시지를 표시할 수 있습니다.

  사용자는 Intune 프로필을 배포할 수 있도록 메일 프로필을 제거해야 합니다. 이 문제를 방지하려면 사용자에게 등록하도록 지시하고 Intune에서 메일 프로필을 배포하도록 허용합니다. 그러면 사용자는 메일 프로필을 만들 수 있습니다.

- **Windows**: Intune에서는 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. Intune은 사용자가 만든 기존 전자 메일 프로필을 덮어씁니다.

- **Samsung KNOX Standard**: Intune에서는 이메일 주소를 기반으로 중복된 이메일 계정을 식별하고 Intune 프로필로 덮어씁니다. 사용자가 해당 계정을 구성하는 경우 Intune 프로필에 의해 다시 덮어쓰게 됩니다. 이로 인해 계정 구성을 덮어쓰는 사용자에게 혼동이 발생할 수 있습니다.

삼성 KNOX는 호스트 이름을 사용하여 프로필을 식별하지 않습니다. 서로 다른 호스트의 동일한 메일 주소로 배포할 여러 메일 프로필을 만들지 말고 서로 덮어쓰는 것이 좋습니다.

## <a name="error-0x87d1fde8-for-knox-standard-device"></a>KNOX Standard 디바이스에 대한 오류 0x87D1FDE8

**문제**: 다양한 Android 디바이스에 대한 Samsung KNOX Standard 용 Exchange Active Sync 메일 프로필을 만들고 배포한 후 디바이스의 [속성] > [정책] 탭에 **0x87D1FDE8** 또는 **수정 실패**라는 오류가 표시됩니다.

삼성 KNOX 및 소스 정책에 대한 EAS 프로필 구성을 확인하세요. Samsung Notes 동기화 옵션은 더 이상 지원되지 않으며, 해당 옵션은 프로필에서 선택하면 안 됩니다. 디바이스가 최대 24시간까지 정책을 처리하기에 충분한 시간을 갖도록 합니다.

## <a name="unable-to-send-images-from--email-account"></a>전자 메일 계정에서 이미지를 보낼 수 없습니다.

자동으로 구성된 메일 계정이 있는 사용자가 디바이스에서 그림이나 이미지를 보낼 수 없습니다. 이 시나리오는 **타사 애플리케이션에서 이메일을 보내도록 허용** 옵션이 활성화되지 않은 경우에 발생할 수 있습니다.

### <a name="intune-solution"></a>Intune 솔루션

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필**을 선택합니다.
3. 전자 메일 프로필 선택 > **속성** > **설정을**합니다.
4. 설정 합니다 **타사 응용 프로그램에서 보내는 전자 메일** 로 설정 **사용 하도록 설정**합니다.

### <a name="configuration-manager-hybrid"></a>Configuration Manager 하이브리드

1. Configuration Manager 콘솔 > **자산 및 호환성**을 엽니다.

2. **개요** > **호환성 설정** > **회사 리소스 액세스**를 확장하고 **이메일 프로필**을 선택합니다.

3. 전자 메일 프로필을 마우스 오른쪽 단추로 클릭하고 **속성**을 엽니다.

4. **동기화 설정** 탭에서 **타사 애플리케이션에서 전자 메일을 보내도록 허용**을 선택합니다.

## <a name="next-steps"></a>다음 단계

[Microsoft의 지원 도움말](get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.
