---
title: Microsoft Intune - Azure에서 디바이스 제한 설정 구성 | Microsoft Docs
description: Microsoft Intune에서 Android, macOS, iOS, Windows Phone 및 Windows 10 디바이스에서 기능을 제한하는 디바이스 프로필 추가
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e30b5fc544d67dcb9e10502d19961d1c91a3e47
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55843105"
---
# <a name="configure-device-restriction-settings-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 제한 설정 구성

디바이스 제한을 통해 다음과 같은 다양한 범주에 걸쳐 관리하는 광범위한 설정 및 기능을 제어할 수 있습니다.
- 보안
- 브라우저
- 하드웨어
- 데이터 공유 설정

예를 들어 iOS 디바이스의 사용자가 디바이스 카메라에 액세스하지 못하도록 하는 디바이스 제한 프로필을 만들 수 있습니다.

디바이스 제한 프로필 기본 사항을 학습한 다음, 각 플랫폼에 대한 더 많은 아티클을 읽어 디바이스 세부 사항을 알아봅니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고, **Intune**을 기준으로 필터링한 다음, **Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 디바이스 제한 프로필의 **이름** 및 **설명**을 입력합니다.
4. **플랫폼** 드롭다운 목록에서 사용자 지정 설정을 적용할 디바이스 플랫폼을 선택합니다. 현재 디바이스 제한 설정에 대해 다음 플랫폼 중 하나를 선택할 수 있습니다.

    - **OWA(Outlook Web Access)**
    - **Android 엔터프라이즈**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 이상**
    - **Windows 10 이상**

5. **프로필** 유형 드롭다운 목록에서 **디바이스 제한**을 선택합니다. Surface Hub와 같은 Windows 10 Team 디바이스에 대한 디바이스 제한 사항 프로필을 만들려면 **디바이스 제한 사항(Windows 10 Team)** 을 선택합니다.
6. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 자세한 설정을 위한 플랫폼을 선택합니다.

    - [Android 설정](device-restrictions-android.md)
    - [Android 엔터프라이즈 설정](device-restrictions-android-for-work.md)
    - [iOS 설정](device-restrictions-ios.md)
    - [macOS 설정](device-restrictions-macos.md)
    - [Windows Phone 8.1 설정](device-restrictions-windows-phone-8-1.md)
    - [Windows 8.1](device-restrictions-windows-8-1.md)
    - [Windows 10 설정](device-restrictions-windows-10.md)
    - [Windows 10 Team 설정](device-restrictions-windows-10-teams.md)
    - [Windows Holographic for Business 설정](device-restrictions-windows-holographic.md)

7. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->
