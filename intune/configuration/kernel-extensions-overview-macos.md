---
title: Microsoft Intune - Azure를 사용하여 macOS 커널 확장 디바이스 프로필 만들기 | Microsoft Docs
titleSuffix: ''
description: macOS 디바이스 프로필을 추가하거나 만든 다음, 커널 확장을 구성하여 사용자가 커널 확장을 재정의하고, 팀 식별자를 추가하며, Microsoft Intune에서 번들과 팀 식별자를 추가할 수 있도록 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/16/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1075054f3812e8c40f38e705a440c46ba09fdd0e
ms.sourcegitcommit: 11cbd2a9d90dea20f6dc1f54f0a6acbeec3a71d6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76146772"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Intune에서 macOS 커널 확장 추가

macOS 디바이스에서 기능을 커널 수준에서 추가할 수 있습니다. 이러한 기능은 일반 프로그램에서 액세스할 수 없는 OS 부분에 액세스합니다. 조직에 앱, 디바이스 기능 등에서 사용할 수 없는 특정 요구 사항이나 필요 사항이 있을 수 있습니다. 

디바이스에 항상 로드할 수 있는 커널 확장을 추가하려면 Microsoft Intune에서 “커널 확장”(KEXT)을 추가한 다음, 디바이스에 이러한 확장을 배포합니다.

예를 들어 디바이스에서 악성 콘텐츠를 검사하는 바이러스 검사 프로그램이 있습니다. 이 바이러스 검사 프로그램의 커널 확장을 Intune에서 허용되는 커널 확장으로 추가할 수 있습니다. 그런 다음, macOS 디바이스에 확장을 “할당”합니다.

이 기능을 통해 관리자는 사용자가 커널 확장을 재정의하고, 팀 식별자를 추가하며, Intune에서 특정 커널 확장을 추가하도록 허용할 수 있습니다.

이 기능은 다음에 적용됩니다.

- macOS 10.13.2 이상

이 기능을 사용하려면 디바이스는 다음과 같아야 합니다.

- Apple DEP(장비 등록 프로그램)를 사용하여 Intune에 등록되어 있어야 합니다. [macOS 디바이스 자동 등록](../enrollment/device-enrollment-program-enroll-macos.md)에서 자세한 내용을 확인할 수 있습니다.

  또는

- “사용자 승인 등록”(Apple 약관)을 통해 Intune에 등록되어 있어야 합니다. [Prepare for changes to kernel extensions in macOS High Sierra](https://support.apple.com/en-us/HT208019)(macOS High Sierra에서 커널 확장 변경 준비)(Apple의 웹 사이트가 열림)에서 자세한 내용을 확인할 수 있습니다.

Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에 해당 프로필을 macOS 디바이스에 푸시하거나 배포할 수 있습니다.

이 문서에서는 Intune에서 커널 확장을 사용하여 디바이스 구성 프로필을 만드는 방법을 보여 줍니다.

> [!TIP]
> 커널 확장에 대한 자세한 내용은 [kernel extension overview](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html)(커널 확장 개요)(Apple의 웹 사이트가 열림)를 참조하세요.

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 서명되지 않은 레거시 커널 확장을 추가할 수 있습니다.
- 커널 확장의 올바른 팀 식별자와 번들 ID를 입력해야 합니다. Intune은 사용자가 입력한 값의 유효성을 검사하지 않습니다. 잘못된 정보를 입력하면 디바이스에서 확장이 작동하지 않습니다. 팀 식별자는 정확히 10자의 영숫자 문자입니다. 

> [!NOTE]
> Apple에서 모든 소프트웨어의 서명 및 공증에 대한 정보를 릴리스했습니다. macOS 10.14.5 이상에서는 Intune을 통해 배포된 커널 확장이 Apple의 공증 정책을 준수하지 않아도 됩니다.
>
> 이 공증 정책과 업데이트 또는 변경 사항에 대한 자세한 내용은 다음 리소스를 참조하세요.
>
> - [Notarizing your app before distribution](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution)(배포 전 앱 공증)(Apple의 웹 사이트가 열림) 
> - [Prepare for changes to kernel extensions in macOS High Sierra](https://support.apple.com/en-us/HT208019)(macOS High Sierra에서 커널 확장 변경 준비)(Apple의 웹 사이트가 열림)

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **macOS** 선택
    - **프로필 유형**: **확장**을 선택합니다.
    - **설정**: 구성할 설정을 입력합니다. 모든 설정 목록 및 수행할 작업은 다음을 참조하세요.

        - [macOS](kernel-extensions-settings-macos.md)

4. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다. [프로필을 할당](../device-profile-assign.md)하고 [해당 상태를 모니터링](../device-profile-monitor.md)합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](../device-profile-assign.md)하고, [해당 상태를 모니터링](../device-profile-monitor.md)합니다.
