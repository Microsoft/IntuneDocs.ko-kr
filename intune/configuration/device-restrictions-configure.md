---
title: Microsoft Intune에서 정책을 사용하여 디바이스 기능 제한 - Azure | Microsoft Docs
description: Microsoft Intune의 Android, macOS, iOS, iPadOS, Windows Phone 및 Windows 10 디바이스에서 기능을 제한하는 디바이스 프로필 추가
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53985a9af523ecf60efda5c5c651161c132e326c
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511224"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 제한 설정 구성



Intune에는 관리자가 Android, iOS/iPadOS, macOS 및 Windows 디바이스를 제어하는 데 도움이 되는 디바이스 제한 정책이 포함되어 있습니다. 이러한 제한을 통해 광범위한 설정과 기능을 제어하여 조직의 리소스를 보호할 수 있습니다. 예를 들어 관리자는 다음을 수행할 수 있습니다.

- 디바이스 카메라를 허용하거나 차단
- Google Play, 앱 스토어, 문서 보기, 게임에 대한 액세스 제어
- 기본 제공 앱 차단 또는 허용되거나 금지되는 앱 목록 만들기
- 클라우드 및 스토리지 계정에 파일 백업 허용 또는 금지
- 최소 암호 길이 설정 및 단순 암호 차단

이러한 기능은 Intune에서 사용할 수 있으며 관리자가 구성할 수 있습니다. Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에서 이러한 기능을 추가한 다음 해당 프로필을 조직의 디바이스에 푸시하거나 배포할 수 있습니다.

이 문서에서는 디바이스 제한 프로필을 만드는 방법을 보여줍니다. 다양한 플랫폼에 사용 가능한 모든 설정을 볼 수도 있습니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 정책에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 좋은 정책 이름의 예는 다음과 같습니다. **iOS/iPadOS: 디바이스에서 카메라를 차단합니다**.
    - **설명**: 정책에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.  

        - **OWA(Outlook Web Access)**
        - **Android 엔터프라이즈**
        - **iOS/iPadOS**
        - **macOS**
        - **Windows Phone 8.1**
        - **Windows 8.1 이상**
        - **Windows 10 이상**

    - **프로필 유형**: **디바이스 제한**을 선택합니다.

        Surface Hub와 같은 Windows 10 Team 디바이스에 대한 디바이스 제한 사항 프로필을 만들려면 **디바이스 제한 사항(Windows 10 Team)** 을 선택합니다.

4. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 자세한 설정을 위한 플랫폼을 선택합니다.

    - [Android 설정](../device-restrictions-android.md)
    - [Android 엔터프라이즈 설정](../device-restrictions-android-for-work.md)
    - [iOS/iPadOS 설정](device-restrictions-ios.md)
    - [macOS 설정](device-restrictions-macos.md)
    - [Windows Phone 8.1 설정](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 설정](device-restrictions-windows-10.md)
    - [Windows 10 Team 설정](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 설정](device-restrictions-windows-holographic.md)

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](../device-profile-assign.md)하고, [해당 상태를 모니터링](../device-profile-monitor.md)합니다.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/device-restrictions-configure/disable-android-camera.png)

-->
