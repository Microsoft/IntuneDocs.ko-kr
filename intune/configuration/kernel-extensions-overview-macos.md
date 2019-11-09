---
title: Microsoft Intune를 사용 하 여 macOS 커널 확장 장치 프로필 만들기-Azure | Microsoft Docs
titleSuffix: ''
description: MacOS 장치 프로필을 추가 하거나 만든 다음, Microsoft Intune에서 사용자 재정의를 허용 하도록 커널 확장을 구성 하 고, 팀 식별자와 번들 및 팀 식별자를 추가 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e69f1b11833da0906aaf831f8bb82b04241e442f
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755176"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Intune에서 macOS 커널 확장 추가

MacOS 장치에서 커널 수준에 기능을 추가할 수 있습니다. 이러한 기능은 일반 프로그램에서 액세스할 수 없는 OS 부분에 액세스 합니다. 조직에는 앱, 장치 기능 등에서 제공 하지 않는 특정 요구 사항이 나 요구 사항이 있을 수 있습니다. 

항상 장치에 로드할 수 있는 커널 확장을 추가 하려면 Microsoft Intune에 "커널 확장" (KEXT)을 추가 하 고 이러한 확장을 장치에 배포 합니다.

예를 들어 장치에서 악성 콘텐츠를 검색 하는 바이러스 검사 프로그램이 있을 수 있습니다. Intune에서이 바이러스 검색 프로그램의 커널 확장을 허용 된 커널 확장으로 추가할 수 있습니다. 그런 다음 macOS 장치에 확장을 "할당" 합니다.

이 기능을 사용 하면 관리자가 사용자가 커널 확장을 재정의 하 고, 팀 식별자를 추가 하 고, Intune에서 특정 커널 확장을 추가할 수 있습니다.

이 기능은 다음에 적용됩니다.

- macOS 10.13.2 이상

이 기능을 사용 하려면 장치는 다음과 같아야 합니다.

- Apple DEP (장비 등록 프로그램)를 사용 하 여 Intune에 등록 되었습니다. [MacOS 장치를 자동으로 등록](../enrollment/device-enrollment-program-enroll-macos.md) 하면 자세한 정보가 포함 됩니다.

  또는

- "사용자 승인 등록" (Apple 약관)을 통해 Intune에 등록 되었습니다. [MacOS에서 커널 확장에 대 한 변경 준비-시에라리온](https://support.apple.com/en-us/HT208019) (Apple의 웹 사이트 열림)에 자세한 정보가 있습니다.

Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에 해당 프로필을 macOS 디바이스에 푸시하거나 배포할 수 있습니다.

이 문서에서는 Intune에서 커널 확장을 사용 하 여 장치 구성 프로필을 만드는 방법을 보여 줍니다.

> [!TIP]
> 커널 확장에 대 한 자세한 내용은 [커널 확장 개요](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (Apple의 웹 사이트 열림)를 참조 하세요.

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 서명 되지 않은 레거시 커널 확장을 추가할 수 있습니다.
- 커널 확장의 올바른 팀 식별자와 번들 ID를 입력 해야 합니다. Intune은 사용자가 입력 한 값의 유효성을 검사 하지 않습니다. 잘못 된 정보를 입력 하면 장치에서 확장이 작동 하지 않습니다.

> [!NOTE]
> 모든 소프트웨어에 대 한 서명 및 notarization 관련 된 Apple 정보입니다. MacOS 10.14.5 이상에서 Intune을 통해 배포 된 커널 확장은 Apple의 notarization 정책을 충족 하지 않아도 됩니다.
>
> 이 notarization 정책과 업데이트 또는 변경 내용에 대 한 자세한 내용은 다음 리소스를 참조 하세요.
>
> - [배포 전에 앱 Notarizing](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (Apple의 웹 사이트 열기) 
> - [MacOS에서 커널 확장의 변경 내용 준비-시에라리온](https://support.apple.com/en-us/HT208019) (Apple 웹 사이트 열림)

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인 합니다.
2. **장치** > **구성 프로필** 을 선택 하 > **프로필 만들기**를 선택 합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **macOS**를 선택합니다.
    - **프로필 유형**: **확장**을 선택 합니다.
    - **설정**: 구성할 설정을 입력합니다. 모든 설정 목록 및 수행할 작업은 다음을 참조하세요.

        - [macOS](kernel-extensions-settings-macos.md)

4. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다. [프로필을 할당](../device-profile-assign.md)하고 [해당 상태를 모니터링](../device-profile-monitor.md)합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](../device-profile-assign.md)하고, [해당 상태를 모니터링](../device-profile-monitor.md)합니다.
