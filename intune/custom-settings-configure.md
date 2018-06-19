---
title: Microsoft Intune - Azur에서 사용자 지정 장치 설정 사용 | Microsoft Docs
description: Microsoft Intune을 사용하여 Windows, Android 및 iOS 장치에 대한 사용자 지정 설정을 사용할 프로필 추가 또는 만들기
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ce7c263435f92a041b93dc5d34ffa912c6fa87fb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021883"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Intune에서 사용자 지정 설정을 사용하여 프로필 만들기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune에는 필요하거나 원하는 모든 기본 제공 설정이 없을 수 있습니다. 또는 다른 장치 프로필에서 사용 가능한 설정을 사용하기를 원할 수도 있습니다. 이러한 설정을 추가하려면 장치 프로필을 만들고 사용자 지정 장치 설정을 사용하여 프로필을 구성합니다.

이 아티클에서는 사용자 지정 설정을 사용하여 프로필을 만드는 기본 단계를 표시합니다. 또한 다른 플랫폼을 사용하여 사용자 지정 설정 만들기의 심층 분석에 대한 링크를 포함합니다.

## <a name="custom-settings-on-different-platforms"></a>다른 플랫폼에서 사용자 지정 설정
사용자 지정 설정은 플랫폼마다 다르게 구성됩니다. 예를 들어 Android 및 Windows 장치에서 기능을 제어하려면 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 값을 입력할 수 있습니다. Apple 장치의 경우 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12)를 사용하여 만든 파일을 가져올 수 있습니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성**을 선택하고 **프로필**을 선택한 다음, **프로필 만들기**를 선택합니다.
4. 사용자 지정 프로필에 대한 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 사용자 지정 설정을 적용할 장치 플랫폼을 선택합니다. 다음 플랫폼 중 하나를 선택할 수 있습니다.

    - **OWA(Outlook Web Access)**
    - **Android for Work**
    - **Android**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 이상**
    - **Windows 10 이상**

6. **프로필** 유형 드롭다운 목록에서 선택 **사용자 지정**을 선택합니다.
7. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 다음 링크는 각 플랫폼에 대해 사용자 지정 설정에 관한 자세한 세부 정보를 제공합니다.

    - [Android 설정](custom-settings-android.md)
    - [iOS 설정](custom-settings-ios.md)
    - [macOS 설정](custom-settings-macos.md)
    - [Windows Phone 8.1 설정](custom-settings-windows-phone-8-1.md)
    - [Windows 10 설정](custom-settings-windows-10.md)
    - [Windows Holographic for Business 설정](custom-settings-windows-holographic.md)
    - [Android for Work 설정](custom-settings-android-for-work.md)

8. 작업이 완료되면 **만들기**를 선택합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다. 이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.
