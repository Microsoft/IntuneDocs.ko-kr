---
title: Microsoft Intune에서 디바이스의 Wi-Fi 프로필 만들기 - Azure | Microsoft Docs
description: Microsoft Intune에서 Wi-Fi 디바이스 구성 프로필을 만드는 단계를 참조하세요. Android, Android 엔터프라이즈, Android 키오스크, iOS, macOS, Windows 10 이상 및 Windows Holographic for Business의 프로필을 만듭니다. 이러한 프로필을 사용하여 인증서 사용, EAP 유형 선택, 인증 방법 선택, 프록시 사용 설정을 위한 WiFi 연결을 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80e70db4b64770af1a96ee7f24a3cf875269adce
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723738"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Microsoft Intune에서 디바이스의 Wi-Fi 설정 추가 및 사용

Wi-Fi는 많은 모바일 디바이스가 네트워크 액세스 권한을 가져오는 데 사용되는 무선 네트워크입니다. Microsoft Intune에는 조직의 사용자 및 디바이스에 배포할 수 있는 기본 제공 Wi-Fi 설정이 포함되어 있습니다. 이 설정 그룹을 "프로필"이라고 하며 다른 사용자 및 그룹에 할당할 수 있습니다. 할당되면 사용자가 직접 구성하지 않고도 조직의 Wi-Fi 네트워크에 액세스할 수 있습니다.

예를 들어 Contoso Wi-Fi라는 새 Wi-Fi 네트워크를 설치합니다. 그런 다음, 이 네트워크에 연결할 모든 iOS 디바이스를 설정하려고 합니다. 프로세스는 다음과 같습니다.

1. Contoso Wi-Fi 무선 네트워크에 연결하는 설정을 포함하는 Wi-Fi 프로필을 만듭니다.
2. iOS 디바이스의 모든 사용자를 포함하는 그룹에 프로필을 할당합니다.
3. 사용자는 디바이스의 무선 네트워크 목록에서 새 Contoso Wi-Fi 네트워크를 찾습니다. 그런 다음, 선택한 인증 방법을 사용하여 네트워크에 연결할 수 있습니다.

이 문서에서는 Wi-Fi 프로필을 만드는 단계가 나열되어 있습니다. 각 플랫폼에 대한 여러 설정을 설명하는 링크도 포함되어 있습니다.

## <a name="supported-device-platforms"></a>지원되는 디바이스 플랫폼

Wi-Fi 프로필은 다음 디바이스 플랫폼을 지원합니다.

- Android 4 이상
- Android 엔터프라이즈 및 키오스크
- iOS 8.0 이상
- macOS X 10.11 이상
- Windows 10 이상, Windows 10 Mobile 및 Windows Holographic for Business

> [!NOTE]
> Windows 8.1을 실행하는 디바이스의 경우 이전에 다른 디바이스에서 내보낸 Wi-Fi 구성을 가져올 수 있습니다.

## <a name="create-a-device-profile"></a>디바이스 프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에서 **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
2. 다음 속성을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 WiFi 프로필**은 좋은 프로필 이름입니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.

      - **OWA(Outlook Web Access)**
      - **Android Enterprise**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows 8.1 이상**
      - **Windows 10 이상**

    - **프로필 유형**: **Wi-Fi**를 선택합니다.

      > [!TIP]
      >
      > - 전용 디바이스(키오스크)로 실행되는 **Android 엔터프라이즈** 디바이스의 경우 **디바이스 소유자만** > **Wi-Fi**를 선택합니다.
      > - **Windows 8.1 이상**에서는 **Wi-Fi 가져오기**를 선택할 수 있습니다. 이 옵션을 사용하여 이전에 다른 디바이스에서 내보낸 XML 파일로 Wi-Fi 설정을 가져올 수 있습니다.

3. 일부 Wi-Fi 설정은 플랫폼마다 다릅니다. 특정 플랫폼에 대한 설정을 보려면 플랫폼을 선택합니다.

    - [OWA(Outlook Web Access)](wi-fi-settings-android.md)
    - [Android 엔터프라이즈](wi-fi-settings-android-enterprise.md)(전용 디바이스 포함)
    - [iOS/iPadOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 이상](wi-fi-settings-windows.md)
    - [Windows 8.1 이상 설정](wi-fi-settings-import-windows-8-1.md)(Windows Holographic for Business 포함)

4. 작업이 완료되면 **프로필 만들기** > **만들기**를 선택합니다.

프로필이 만들어지고 프로필 목록(**디바이스 구성** > **프로필**)에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아무것도 하지 않습니다. 다음으로, [이 프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
