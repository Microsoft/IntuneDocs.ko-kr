---
title: Microsoft Intune에서 Windows Holographic for Business에 대한 키오스크 설정 - Azure | Microsoft Docs
description: Windows Holographic for Business 디바이스를 단일 앱 및 다중 앱 키오스크로 구성하고, 시작 메뉴를 사용자 지정하고, 앱을 추가하고, 작업 표시줄을 표시하고, Microsoft Intune에서 웹 브라우저를 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: e555c62030cede57e98e34034367831c298c0ced
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72492407"
---
# <a name="windows-holographic-for-business-device-settings-to-run-as-a-kiosk-in-intune"></a>Intune에서 Windows Holographic for Business 디바이스를 키오스크로 실행하기 위한 설정

Windows Holographic for Business 디바이스에서 이러한 디바이스가 단일 앱 키오스크 모드 또는 다중 앱 키오스크 모드에서 실행되도록 구성할 수 있습니다. Windows Holographic for Business에서는 일부 기능이 지원되지 않습니다.

이 문서에서는 Windows Holographic for Business 디바이스에서 제어할 수 있는 다양한 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 키오스크 모드로 실행하기 위해 Windows Holographic for Business 디바이스를 구성합니다.

Intune 관리자는 이러한 설정을 만들어 디바이스에 할당할 수 있습니다.

Intune에서 Windows 키오스크 기능에 대한 자세한 내용은 [키오스크 설정 구성](kiosk-settings.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[프로필을 만듭니다](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>단일 전체 화면 앱 키오스크

단일 앱 키오스크 모드를 선택하는 경우 다음 설정을 입력합니다.

- **사용자 로그온 유형**: **로컬 사용자 계정**을 선택하여 로컬(디바이스 기준) 사용자 계정 또는 키오스크 앱과 연결된 MSA(Microsoft 계정) 계정을 입력합니다. **자동 로그온** 사용자 계정 유형은 Windows Holographic for Business에서 지원되지 않습니다.

- **애플리케이션 유형**: **Store 앱**을 선택합니다.

- **키오스크 모드에서 실행할 앱**: **스토어 앱 추가**를 선택하고 목록에서 앱을 선택합니다.

    나열된 앱이 없나요? [클라이언트 앱](../apps/apps-add.md)의 단계를 사용하여 일부 앱을 추가합니다.

    **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="multi-app-kiosks"></a>다중 앱 키오스크

이 모드의 앱은 시작 메뉴에서 사용할 수 있습니다. 이러한 앱은 사용자가 열 수 있는 유일한 앱입니다. 다중 앱 키오스크 모드를 선택하면 다음 설정을 입력합니다.

- **S 모드 디바이스에서 Windows 10을 대상으로 지정**: **아니요**를 선택합니다. Windows Holographic for Business에서는 S 모드가 지원되지 않습니다.

- **사용자 로그온 유형**: 추가하는 앱을 사용할 수 있는 사용자 계정을 하나 이상 추가합니다. 옵션은 다음과 같습니다. 

  - **자동 로그온**: Windows Holographic for Business에서 지원되지 않습니다.
  - **로컬 사용자 계정**: 로컬(디바이스 기준) 사용자 계정을 **추가**합니다. 입력한 계정이 키오스크에 로그인하는 데 사용됩니다.
  - **Azure AD 사용자 또는 그룹(Windows 10, 버전 1803 이상)** : 디바이스에 로그인할 사용자 자격 증명이 필요합니다. **추가**를 선택하여 목록에서 Azure AD 사용자 또는 그룹을 선택합니다. 여러 사용자 및 그룹을 선택할 수 있습니다. **선택**을 선택하여 변경 내용을 저장합니다.
  - **HoloLens 방문자**: 방문자 계정은 [공유된 PC 모드 개념](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)에 설명된 대로 사용자 자격 증명이나 인증이 필요 없는 게스트 계정입니다.

- **애플리케이션**: 키오스크 디바이스에서 실행할 앱을 추가합니다. 여러 개의 앱을 추가할 수 있습니다.

  - **스토어 앱 추가**: LOB 앱을 포함 하 여 Intune에 [클라이언트 앱](../apps/apps-add.md)으로 추가 하거나 배포한 기존 앱을 선택 합니다. 앱이 나열 되지 않은 경우 Intune은 [intune에 추가](../apps/store-apps-windows.md)하는 많은 [앱 유형을](../apps/apps-add.md) 지원 합니다.
  - **Win32 앱 추가**: Windows Holographic for Business에서 지원되지 않습니다.
  - **AUMID로 추가**: 받은 편지함 Windows 앱을 추가하려면 이 옵션을 사용합니다. 다음 속성을 입력합니다. 

    - **애플리케이션 이름**: 필수입니다. 애플리케이션의 이름을 입력합니다.
    - **AUMID(애플리케이션 사용자 모델 ID)** : 필수입니다. Windows 앱의 AUMID(애플리케이션 사용자 모델 ID)를 입력합니다. 이 ID를 가져오려면 [설치된 앱의 애플리케이션 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.
    - **타일 크기**: 필수입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.

- **키오스크 브라우저 설정**: Windows Holographic for Business에서 지원되지 않습니다.

- **대체 시작 레이아웃 사용**: 시작 메뉴에 앱의 순서를 포함하여 앱이 표시되는 방법을 설명하는 XML 파일을 입력하려면 **예**를 선택합니다. 시작 메뉴에 추가 사용자 지정이 필요한 경우 이 옵션을 사용합니다. [시작 레이아웃 사용자 지정 및 내보내기](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)는 몇 가지 지침을 제공하며, Windows Holographic for Business 디바이스에 대한 특정 XML 파일을 포함합니다.

- **Windows 작업 표시줄**: Windows Holographic for Business에서 지원되지 않습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) 및 [Windows 10 이상](kiosk-settings-windows.md) 디바이스에 대한 키오스크 프로필을 만들 수도 있습니다.
