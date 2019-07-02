---
title: Microsoft Intune-Azure 사용 하 여 macOS 커널 확장 장치 프로필 만들기 | Microsoft Docs
titleSuffix: ''
description: 또는 macOS 장치 프로필을 만들 추가한 후 사용자 재정의 허용 하려면 Microsoft Intune에 팀 id 및 번들 및 팀 id를 추가 커널 확장을 구성 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fd2e03c09cb2bed49ee7607283bf63e2c3ae67da
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403908"
---
# <a name="add-macos-kernel-extensions-in-intune"></a>Intune에서 macOS 커널 확장명을 추가 합니다.

MacOS 장치에서 커널 수준에서 기능을 추가할 수 있습니다. 이러한 기능은 일반 프로그램에 액세스할 수 없는 운영 체제의 부분에 액세스 합니다. 조직의 특정 요구 사항이 나 앱, 장치 기능 등에 사용할 수 없는 요구 사항이 있을 수 있습니다. 

장치에서 로드를 항상 허용 되는 커널 확장을 추가 하려면 "커널 확장"을 추가 합니다 (KEXT) Microsoft Intune에서 다음 장치에 이러한 확장을 배포 합니다.

예를 들어, 악의적인 콘텐츠에 대 한 장치를 검색 하는 바이러스 검사 프로그램을 해야 합니다. 이 바이러스 Intune에서 허용 된 커널 확장으로 프로그램의 커널 확장 검사를 추가할 수 있습니다. 그런 다음 "" 확장에 macOS 장치를 할당 합니다.

이 기능을 사용 하 여 관리자 override 커널 확장 팀 식별자를 추가 하 고 Intune에서 특정 커널 확장명을 추가할 수 있습니다.

이 기능은 다음에 적용됩니다.

- macOS 10.13.2 이상

이 기능을 사용 하려면 장치 여야 합니다.

- Apple 등록 프로그램 DEP (장치)를 사용 하 여 Intune에 등록 합니다. [MacOS 장치를 자동으로 등록](device-enrollment-program-enroll-macos.md) 자세한 정보가 있습니다.

  또는

- "사용자 승인 등록"을 사용 하 여 Intune에 등록 (Apple의 용어). [MacOS High Sierra에서에서 커널 확장에 대 한 변경 내용을 준비](https://support.apple.com/en-us/HT208019) (Apple 웹 사이트 열기)에 자세한 정보가 있습니다.

Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에 해당 프로필을 macOS 디바이스에 푸시하거나 배포할 수 있습니다.

이 문서에서는 커널 확장을 사용 하 여 Intune에서 장치 구성 프로필을 만드는 방법을 보여 줍니다.

> [!TIP]
> 커널 확장에 대 한 자세한 내용은 참조 하세요. [커널 확장 개요](https://developer.apple.com/library/archive/documentation/Darwin/Conceptual/KernelProgramming/Extend/Extend.html) (Apple 웹 사이트 열기).

## <a name="what-you-need-to-know"></a>기억해야 하는 사항

- 부호 없는 레거시 커널 확장을 추가할 수 있습니다.
- 올바른 팀 id를 입력 하 고 번들 ID의 커널 확장 해야 합니다. Intune은 입력 하는 값의 유효성을 검사 하지 않습니다. 잘못 된 정보를 입력 하는 경우 확장은 장치에서 작동 하지 않습니다.

> [!NOTE]
> Apple 서명 및 notarization 모든 소프트웨어에 대 한 정보를 해제 합니다. 10.14.5 macos 및 Apple notarization 정책을 준수 하기 위해 Intune을 통해 배포 된 확장 없는, 커널입니다.
>
> 이 notarization 정책 및 모든 업데이트 또는 변경에 대 한 자세한 내용은 다음 리소스를 참조 하세요.
>
>  - [배포 하기 전에 앱 notarizing](https://developer.apple.com/documentation/security/notarizing_your_app_before_distribution) (Apple 웹 사이트 열기) 
>  - [MacOS High Sierra에서에서 커널 확장에 대 한 변경 내용을 준비](https://support.apple.com/en-us/HT208019) (Apple 웹 사이트 열기)

## <a name="create-the-profile"></a>프로필 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **macOS**를 선택합니다.
    - **프로필 유형**: 선택 **확장**합니다.
    - **설정**: 구성할 설정을 입력합니다. 모든 설정 목록 및 수행할 작업은 다음을 참조하세요.

        - [macOS](kernel-extensions-settings-macos.md)

4. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다. [프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
