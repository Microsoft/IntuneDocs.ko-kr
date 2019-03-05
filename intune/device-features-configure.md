---
title: Microsoft Intune - Azure를 사용하여 iOS 또는 macOS 디바이스 프로필 만들기 | Microsoft Docs
description: iOS 또는 macOS 디바이스 프로필을 추가하거나 만든 다음, Microsoft Intune에서 AirPrint, 홈 화면의 레이아웃, 앱 알림, 공유 디바이스, 단일 로그인 및 웹 콘텐츠 필터 설정에 대한 설정을 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 65cf52dd7984ee093966645f61b2678521e71536
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57228173"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Intune에서 iOS 및 macOS 디바이스 기능 설정 추가

Intune에는 관리자가 iOS 및 macOS 디바이스를 제어하는 데 도움이 되는 많은 기능과 설정이 포함되어 있습니다. 예를 들어 관리자는 다음을 수행할 수 있습니다.

- 네트워크의 AirPrint 프린터에 사용자 액세스 허용
- 새 페이지 추가를 포함하여 홈 화면에 앱 및 폴더 추가
- 앱 알림 표시 여부 및 방법 선택
- 특히 공유 디바이스의 경우 메시지 또는 자산 태그를 표시하도록 잠금 화면 구성
- 사용자에게 안전한 Single Sign-On 환경을 제공하여 앱 간에 자격 증명 공유
- 성인 언어를 사용하는 웹 사이트 필터링 및 특정 웹 사이트 허용 또는 차단

이러한 기능은 Intune에서 사용할 수 있으며 관리자가 구성할 수 있습니다. Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에 해당 프로필을 iOS 및 macOS 디바이스에 푸시하거나 배포할 수 있습니다.

이 문서는 디바이스 구성 프로필을 만드는 방법을 보여줍니다. [iOS](ios-device-features-settings.md) 및 [macOS](macos-device-features-settings.md) 디바이스에 사용 가능한 모든 설정을 볼 수도 있습니다.

## <a name="create-a-device-profile"></a>디바이스 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 > **Intune**을 기준으로 필터링하고 > **Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 플랫폼 선택:
        - **iOS**
        - **macOS**
    - **프로필 유형**: **디바이스 기능**을 선택합니다.
    - **설정**: 구성할 설정을 입력합니다. 모든 설정 목록 및 수행할 작업은 다음을 참조하세요.

        - [iOS](ios-device-features-settings.md)
        - [macOS](macos-device-features-settings.md)

4. 작업이 완료되면 **확인**을 선택한 다음, **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다. [프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[iOS](ios-device-features-settings.md) 및 [macOS](macos-device-features-settings.md) 디바이스에 대한 모든 디바이스 기능 설정을 봅니다.
