---
title: Microsoft Intune에서 장치의 Wi-Fi 프로필 만들기 - Azure | Microsoft Docs
description: Microsoft Intune에서 Wi-Fi 장치 구성 프로필을 만드는 단계를 참조하세요. Android, Android 엔터프라이즈, Android 키오스크, iOS, macOS, Windows 10 이상 및 Windows Holographic for Business의 프로필을 만듭니다. 이러한 프로필을 사용하여 인증서 사용, EAP 유형 선택, 인증 방법 선택, 프록시 사용 설정을 위한 WiFi 연결을 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16273910220dae238e15910af0557dd8b73646b9
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49425260"
---
# <a name="add-and-use-wi-fi-settings-on-your-devices-in-microsoft-intune"></a>Microsoft Intune에서 장치의 Wi-Fi 설정 추가 및 사용

Microsoft Intune Wi-Fi 프로필을 사용하여 무선 네트워크 설정을 조직의 사용자와 장치에 할당합니다. Wi-Fi 프로필을 할당하면 사용자가 직접 구성하지 않고도 조직의 Wi-Fi 네트워크에 액세스할 수 있습니다.

예를 들어 Contoso Wi-Fi라는 새 Wi-Fi 네트워크를 설치합니다. 그런 다음, 이 네트워크에 연결할 모든 iOS 장치를 설정하려고 합니다. 프로세스는 다음과 같습니다.

1. Contoso Wi-Fi 무선 네트워크에 연결하기 위한 설정을 포함하는 Wi-Fi 프로필을 만듭니다.
2. iOS 장치의 모든 사용자를 포함하는 그룹에 프로필을 할당합니다.
3. 사용자는 장치의 무선 네트워크 목록에서 새 Contoso Wi-Fi 네트워크를 찾습니다. 그런 다음, 선택한 인증 방법을 사용하여 네트워크에 연결할 수 있습니다.

이 문서의 단계를 사용하여 Wi-Fi 프로필을 만듭니다. 그런 다음, 플랫폼 특정 설정 및 세부 정보에 대한 항목을 검토합니다.

## <a name="supported-device-platforms"></a>지원되는 장치 플랫폼

Wi-Fi 프로필은 다음 장치 플랫폼을 지원합니다.

- Android 4 이상
- Android 엔터프라이즈 및 키오스크
- iOS 8.0 이상
- macOS(Mac OS X 10.11 이상)
- Windows 10 이상, Windows 10 Mobile 및 Windows Holographic for Business

> [!NOTE]
> Windows 8.1을 실행하는 장치의 경우 이전에 다른 장치에서 내보낸 Wi-Fi 구성을 가져올 수 있습니다.

## <a name="create-a-wi-fi-device-profile"></a>Wi-Fi 장치 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고, **Intune**을 기준으로 필터링한 다음, **Microsoft Intune**을 선택합니다. 
2. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. Wi-Fi 프로필의 **이름**과 **설명**을 입력합니다.
4. **플랫폼** 드롭다운 목록에서 Wi-Fi 설정을 적용할 장치 플랫폼을 선택합니다. 옵션은 다음과 같습니다.

    - **OWA(Outlook Web Access)**
    - **Android 엔터프라이즈**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 이상**
    - **Windows 10 이상**

5. **프로필 유형**에서 **Wi-Fi**를 선택합니다.

    - 키오스크로 실행되는 **Android 엔터프라이즈** 장치의 경우 **장치 소유자만** > **Wi-Fi**를 선택할 수 있습니다.
    - **Windows 8.1 이상**에서는 **Wi-Fi 가져오기**를 선택할 수 있습니다. 이 옵션을 사용하여 이전에 다른 장치에서 내보낸 XML 파일로 Wi-Fi 설정을 가져올 수 있습니다.

6. 일부 Wi-Fi 설정은 플랫폼마다 다릅니다. 특정 플랫폼의 설정을 보려면 다음을 선택합니다.

    - [OWA(Outlook Web Access)](wi-fi-settings-android.md)
    - [Android 엔터프라이즈 및 키오스크](wi-fi-settings-android-enterprise.md)
    - [iOS](wi-fi-settings-ios.md)
    - [macOS](wi-fi-settings-macos.md)
    - [Windows 10 이상](wi-fi-settings-windows.md)
    - [Windows 8.1 이상 설정](wi-fi-settings-import-windows-8-1.md)(Windows Holographic for Business 포함)

    대부분의 플랫폼에는 **기본** 및 **엔터프라이즈** 설정이 있습니다. **기본**에는 네트워크 이름 및 SSID와 같은 기능이 포함됩니다. **엔터프라이즈**에서는 EAP(확장할 수 있는 인증 프로토콜)와 같은 고급 정보를 제공할 수 있습니다.

7. Wi-Fi 설정 추가를 완료하면 **프로필 만들기** > **만들기**를 선택하여 구성 프로필을 추가합니다. 프로필이 만들어지고 프로필 목록(**장치 구성** > **프로필**)에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아무것도 하지 않습니다. 그런 다음, [이 프로필을 할당](device-profile-assign.md)합니다.
