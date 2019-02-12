---
title: Microsoft Intune을 사용하여 Windows 10 디바이스에 로그인하기 위해 PIN 사용 - Azure | Microsoft Docs
description: Windows Hello for Business를 사용하면 사용자가 PIN, 지문 등을 통해 디바이스에 로그인할 수 있습니다. 이러한 설정을 사용하여 Intune for Windows 10 디바이스에 ID 보호 구성 프로필을 만들고 해당 프로필을 사용자 그룹 및 디바이스 그룹에 할당합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c6ca040c91437a35d12626f54b8385311d6631eb
ms.sourcegitcommit: e0d55bdda1a818ffe4cfc0ef0592833e22f65a89
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55290658"
---
# <a name="use-windows-hello-for-business-on-windows-10-devices-with-microsoft-intune"></a>Microsoft Intune을 사용하는 Windows 10 디바이스에서 Windows Hello for Business 사용

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows Hello for Business는 암호, 스마트 카트 및 가상 스마트 카트를 대체하여 Windows 디바이스에 로그인하는 방법입니다. Intune에는 관리자가 Windows Hello for Business를 구성하고 사용할 수 있도록 기본 제공 설정이 포함되어 있습니다. 예를 들어 다음 설정을 사용할 수 있습니다.

- 디바이스 및 사용자에 대한 Windows Hello for Business 사용
- 최소 또는 최대 PIN 길이를 포함하여 디바이스 PIN 요구 사항 설정
- 사용자가 디바이스에 로그인할 수 있는(또는 할 수 없는) 지문과 같은 제스처 허용

이 기능은 다음을 실행하는 디바이스에 적용됩니다.

- Windows 10 이상
- Windows 10 Mobile
- Windows Holographic for Business

Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에는 이 설정을 조직의 사용자 및 디바이스 그룹에 푸시하거나 배포합니다.

이 문서는 디바이스 구성 프로필을 만드는 방법을 보여줍니다. 모든 설정 목록 및 수행할 작업은 [Windows Hello for Business를 사용하기 위한 Windows 10 디바이스 설정](identity-protection-windows-settings.md)을 참조하세요.

## <a name="create-the-device-profile"></a>디바이스 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고, **Intune**을 기준으로 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다. 비즈니스용 Windows Hello는 Windows 10 이상을 실행하는 디바이스에서만 지원됩니다.
    - **프로필 유형**: **ID 보호**를 선택합니다.
    - **Windows Hello for Business 구성**: Windows Hello for Business를 구성할 방법을 선택합니다. 옵션은 다음과 같습니다.

        - **구성되지 않음** 디바이스에서 [Windows Hello for Business 프로비전](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning). 사용자에게만 ID 보호 프로필을 할당하는 경우 디바이스 컨텍스트 기본값은 **구성되지 않음**으로 지정됩니다.
        - **사용 안 함**: Windows Hello for Business를 사용하지 않으려면 이 옵션을 선택합니다. 이 옵션은 모든 사용자에 대해 Windows Hello for Business를 비활성화합니다.
        - **사용**: [프로비전]((https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-how-it-works-provisioning))에 대해 이 옵션을 선택하고 Intune에서 Windows Hello for Business 설정을 구성합니다. 구성할 설정을 입력합니다. 모든 설정 목록 및 수행할 작업은 다음을 참조하세요.

            - [Windows Hello for Business를 사용하기 위한 Windows 10 디바이스 설정](identity-protection-windows-settings.md)

4. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다. 그런 다음, 요구에 맞도록 사용자와 디바이스 그룹에 이 프로필을 [할당](device-profile-assign.md)합니다.

<!--  Removing image as part of design review; retaining source until we known the disposition.

## Example of device restriction settings

In this high-level example, you'll create a device restriction policy that blocks the use of the built-in camera app on Android devices.

![How to disable the camera on Android devices](./media/disable-android-camera.png)

-->

## <a name="next-steps"></a>다음 단계

- 모든 [설정 및 수행할 작업](identity-protection-windows-settings.md)의 목록을 참조하세요.
- [프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.