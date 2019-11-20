---
title: Microsoft Intune에서 Windows 및 Holographic 디바이스용 키오스크 설정 - Azure | Microsoft Docs
description: Windows 10(이상) 및 Windows Holographic for Business 디바이스를 단일 앱 및 다중 앱 키오스크로 구성하고, 시작 메뉴를 사용자 지정하고, 앱을 추가하고, 작업 표시줄을 표시하고, Microsoft Intune에서 웹 브라우저를 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2dede228aadac2981c38d2842f5da1369933f86
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059887"
---
# <a name="windows-10-and-windows-holographic-for-business-device-settings-to-run-as-a-dedicated-kiosk-using-intune"></a>Intune을 사용하여 Windows 10 및 Holographic for Business 디바이스를 전용 키오스크로 실행하기 위한 설정

Windows 10 디바이스에서 Intune을 사용하여 전용 디바이스라고도 하는 키오스크로 디바이스를 실행합니다. 키오스크 모드의 디바이스는 하나의 앱을 실행하거나 여러 앱을 실행할 수 있습니다. 시작 메뉴를 표시 및 사용자 지정하고, Win32 앱을 비롯한 다른 앱을 추가하고, 웹 브라우저에 특정 홈페이지를 추가할 수 있습니다. 

이 기능은 다음을 실행하는 디바이스에 적용됩니다.

- Windows 10 이상
- Windows Holographic for Business

Intune은 디바이스당 하나의 키오스크 프로필을 지원합니다. 단일 디바이스에서 여러 키오스크 프로필이 필요한 경우 [사용자 지정 OMA-URI](custom-settings-windows-10.md)를 사용할 수 있습니다.

Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후에는 이 설정을 조직의 그룹에 푸시하거나 배포합니다.

이 문서는 디바이스 구성 프로필을 만드는 방법을 보여줍니다. 모든 설정 목록과 수행할 작업은 [Windows 10 키오스크 설정](kiosk-settings-windows.md) 및 [Windows Holographic for Business 키오스크 설정](kiosk-settings-holographic.md)을 참조하세요.

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
   - **플랫폼**: **Windows 10 이상** 선택
   - **프로필 유형**: **키오스크** 선택

4. **설정**에서 **키오스크 모드**를 선택합니다. **키오스크 모드**는 정책에서 지원되는 키오스크 모드 유형을 식별합니다. 다음 옵션을 사용할 수 있습니다.

    - **구성되지 않음**(기본값): 이 정책은 키오스크 모드를 사용하도록 설정하지 않습니다.
    - **단일 앱, 전체 화면 키오스크**: 디바이스는 단일 사용자 계정으로 실행되고 해당 계정을 단일 Store 앱으로 잠급니다. 이에 따라 사용자가 로그인하면 특정 앱이 시작됩니다. 또한 이 모드는 사용자가 새 앱을 열거나 실행 중인 앱을 변경하는 것을 제한합니다.
    - **다중 앱 키오스크**: 디바이스는 AUMID(애플리케이션 사용자 모델 ID)를 사용하여 여러 Store 앱, Win32 앱 또는 받은 편지함 Windows 앱을 실행합니다. 사용자가 추가하는 앱만 디바이스에서 사용할 수 있습니다.

        다중 앱 키오스크 또는 용도가 고정된 디바이스의 장점은 필요한 앱에만 액세스하여 사용자에게 이해하기 쉬운 환경을 제공하는 것입니다. 또한 필요하지 않은 앱은 보기에서 제거됩니다.

    모든 설정 목록 및 수행할 작업은 다음을 참조하세요.
      - [Windows 10 키오스크 설정](kiosk-settings-windows.md)
      - [Windows Holographic for Business 키오스크 설정](kiosk-settings-holographic.md)

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다. 그런 다음, 프로필을 [할당](device-profile-assign.md)합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

다음 플랫폼을 실행하는 디바이스에 대한 키오스크 프로필을 만들 수 있습니다.
- [OWA(Outlook Web Access)](device-restrictions-android.md#kiosk)
- [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings)
- [Windows 10 이상](kiosk-settings-windows.md)
- [Windows Holographic for Business](kiosk-settings-holographic.md)
