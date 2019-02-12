---
title: Microsoft Intune의 Windows 10용 키오스크 설정 - Azure | Microsoft Docs
description: Windows 10(이상) 디바이스를 단일 앱 및 다중 앱 키오스크로 구성하고, 시작 메뉴를 사용자 지정하고, 앱을 추가하고, 작업 표시줄을 표시하고 웹 브라우저를 Microsoft Intune에서 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.openlocfilehash: 31cfa617e0ca5d8d0848d1ecb781fda701589ccd
ms.sourcegitcommit: 0142020a7cd75348c6367facf072ed94238e667f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55229953"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Intune에서 키오스크로 실행하는 Windows 10 이상 디바이스 설정

Windows 10 이상 디바이스에서 이러한 디바이스가 단일 앱 키오스크 모드 또는 다중 앱 키오스크 모드에서 실행되도록 구성할 수 있습니다.

이 문서에서는 Windows 10 이상 디바이스에서 제어할 수 있는 다양한 메일 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 키오스크 모드로 실행하는 Windows 10 이상 디바이스를 구성합니다.

Intune 관리자는 이러한 설정을 만들어 디바이스에 할당할 수 있습니다.

Intune에서 Windows 키오스크 기능에 대한 자세한 내용은 [키오스크 설정 구성](kiosk-settings.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[프로필을 만듭니다](kiosk-settings.md#create-the-profile).

## <a name="single-full-screen-app-kiosks"></a>단일 전체 화면 앱 키오스크

단일 앱 키오스크 모드를 선택하는 경우 다음 설정을 입력합니다.

- **사용자 로그온 유형**: 추가한 앱이 입력한 사용자 계정으로 실행됩니다. 옵션은 다음과 같습니다.

  - **자동 로그온(Windows 10 버전 1803 이상)**: 게스트 계정과 비슷하게, 사용자가 로그온할 필요가 없는 공용 환경의 키오스크에 해당합니다. 이 설정은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 사용합니다.
  - **로컬 사용자 계정**: 로컬(디바이스 기준) 사용자 계정을 입력합니다. 입력한 계정이 키오스크에 로그인하는 데 사용됩니다.

- **애플리케이션 유형**: **Store 앱**을 선택합니다.

- **키오스크 모드에서 실행할 앱**: **스토어 앱 추가**를 선택하고 목록에서 앱을 선택합니다.

    나열된 앱이 없나요? [클라이언트 앱](apps-add.md)의 단계를 사용하여 일부 앱을 추가합니다.

    **확인**을 선택하여 변경 내용을 저장합니다.

- **키오스크 브라우저 설정**: 이러한 설정은 키오스크에서 웹 브라우저 앱을 제어합니다. Store에서 [키오스크 브라우저 앱](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)을 가져와서 Intune에 [클라이언트 앱](apps-add.md)으로 추가한 다음, 키오스크 디바이스에 앱을 할당해야 합니다.

  다음 설정을 입력합니다.

  - **기본 홈 페이지 URL**: 키오스크 브라우저가 열리거나 브라우저가 다시 시작될 때 표시되는 기본 URL을 입력합니다. 예를 들어 `http://bing.com` 또는 `http://www.contoso.com`을 입력합니다.

  - **홈 단추**: 키오스크 브라우저의 홈 단추를 **표시**하거나 **숨깁니다**. 기본적으로 단추는 표시되지 않습니다.

  - **탐색 단추**: 앞으로 및 뒤로 단추를 **표시**하거나 **숨깁니다**. 기본적으로 탐색 단추는 표시되지 않습니다.

  - **세션 종료 단추**: 세션 종료 단추를 **표시**하거나 **숨깁니다**. 표시된 경우 사용자는 단추를 선택하고 앱은 세션을 종료하라는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터(쿠키, 캐시 등)를 지운 후 기본 URL을 엽니다. 기본적으로 단추는 표시되지 않습니다.

  - **유휴 시간 후에 브라우저 새로 고침**: 키오스크 브라우저가 새로 시작 상태에서 다시 시작될 때까지 소요되는 유휴 시간(1-1440분)을 입력합니다. 유휴 시간은 사용자의 마지막 조작 이후 소요된 시간(분)입니다. 기본적으로 이 값은 비어 있거나 공백이며, 이는 유휴 시간 제한이 없음을 나타냅니다.

  - **허용된 웹 사이트**: 특정 웹 사이트가 열리도록 허용하려면 이 설정을 사용합니다. 즉, 디바이스에서 웹 사이트를 제한하거나 차단하려면 이 기능을 사용합니다. 예를 들어 `http://contoso.com*`의 모든 웹 사이트가 열리도록 허용할 수 있습니다. 기본적으로 모든 웹 사이트가 허용됩니다.
 
      특정 웹 사이트를 허용하려면 허용되는 웹 사이트 목록이 포함된 파일을 별도의 줄에 업로드합니다. 파일을 추가하지 않으면 모든 웹 사이트가 허용됩니다. Intune은 *(별표)를 와일드카드로 지원합니다.

      샘플 파일은 다음 목록과 비슷해야 합니다.

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com/*`  
      `https://contoso.com/*`  

  **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="multi-app-kiosks"></a>다중 앱 키오스크

이 모드의 앱은 시작 메뉴에서 사용할 수 있습니다. 이러한 앱은 사용자가 열 수 있는 유일한 앱입니다.

다중 앱 키오스크 모드를 선택하면 다음 설정을 입력합니다.

- **S 모드 디바이스에서 Windows 10을 대상으로 지정**: 키오스크 프로필에서 스토어 앱 및 AUMID 앱(Win32 앱 제외)을 허용하려면 **예**를 선택합니다. 키오스크 프로필에서 스토어 앱, Win32 앱 및 AUMID 앱을 허용하려면 **아니요**를 선택합니다. **아니요**를 선택하면 이 키오스크 프로필이 S 모드 디바이스에 배포되지 않습니다.

- **사용자 로그온 유형**: 추가한 앱이 입력한 사용자 계정으로 실행됩니다. 옵션은 다음과 같습니다.

  - **자동 로그온(Windows 10 버전 1803 이상)**: 게스트 계정과 비슷하게, 사용자가 로그온할 필요가 없는 공용 환경의 키오스크에 해당합니다. 이 설정은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 사용합니다.
  - **로컬 사용자 계정**: 로컬(디바이스 기준) 사용자 계정을 **추가**합니다. 입력한 계정이 키오스크에 로그인하는 데 사용됩니다.
  - **Azure AD 사용자 또는 그룹(Windows 10 버전 1803 이상)**: **추가**를 선택하여 목록에서 Azure AD 사용자 또는 그룹을 선택합니다. 여러 사용자 및 그룹을 선택할 수 있습니다. **선택**을 선택하여 변경 내용을 저장합니다.
  - **HoloLens 방문자**: 방문자 계정은 [공유된 PC 모드 개념](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)에 설명된 대로 사용자 자격 증명이나 인증이 필요 없는 게스트 계정입니다.

- **애플리케이션**: 키오스크 디바이스에서 실행할 앱을 추가합니다. 여러 개의 앱을 추가할 수 있습니다.

  - **스토어 앱 추가**: 비즈니스용 Microsoft Store에서 앱을 추가합니다. 앱이 나열되지 않으면 앱을 가져와서 [Intune에 추가](store-apps-windows.md)할 수 있습니다. 예를 들어 키오스크 브라우저, Excel, OneNote 등을 추가할 수 있습니다.

  - **Win32 앱 추가**: Win32 앱은 Visual Studio Code 또는 Google Chrome과 같은 기존 데스크톱 앱입니다. 다음 속성을 입력합니다.

    - **애플리케이션 이름**: 필수 사항입니다. 애플리케이션의 이름을 입력합니다.
    - **로컬 경로**: 필수 사항입니다. `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 또는 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`와 같이 실행 파일의 경로를 입력합니다.
    - **AUMID(애플리케이션 사용자 모델 ID)**: Win32 앱의 AUMID(애플리케이션 사용자 모델 ID)를 입력합니다. 이 설정에 따라 바탕 화면에 있는 타일의 시작 레이아웃이 결정됩니다. 이 ID를 구하려면 [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)를 참조하세요.
    - **타일 크기**: 필수 사항입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.
  
  - **AUMID로 추가**: 메모장 또는 계산기와 같은 받은 편지함 Windows 앱을 추가하려면 이 옵션을 사용합니다. 다음 속성을 입력합니다. 

    - **애플리케이션 이름**: 필수 사항입니다. 애플리케이션의 이름을 입력합니다.
    - **AUMID(애플리케이션 사용자 모델 ID)**: 필수 사항입니다. Windows 앱의 AUMID(애플리케이션 사용자 모델 ID)를 입력합니다. 이 ID를 가져오려면 [설치된 앱의 애플리케이션 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.
    - **타일 크기**: 필수 사항입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.

  > [!TIP]
  > 모든 앱을 추가한 후 목록에서 앱을 클릭하고 끌어서 표시 순서를 변경할 수 있습니다.  

  **확인**을 선택하여 변경 내용을 저장합니다.

- **키오스크 브라우저 설정**: 이러한 설정은 키오스크에서 웹 브라우저 앱을 제어합니다. [클라이언트 앱](apps-add.md)을 사용하여 키오스크 디바이스에 웹 브라우저 앱을 배포해야 합니다.

  다음 설정을 입력합니다.

  - **기본 홈 페이지 URL**: 키오스크 브라우저가 열리거나 브라우저가 다시 시작될 때 표시되는 기본 URL을 입력합니다. 예를 들어 `http://bing.com` 또는 `http://www.contoso.com`을 입력합니다.

  - **홈 단추**: 키오스크 브라우저의 홈 단추를 **표시**하거나 **숨깁니다**. 기본적으로 단추는 표시되지 않습니다.

  - **탐색 단추**: 앞으로 및 뒤로 단추를 **표시**하거나 **숨깁니다**. 기본적으로 탐색 단추는 표시되지 않습니다.

  - **세션 종료 단추**: 세션 종료 단추를 **표시**하거나 **숨깁니다**. 표시된 경우 사용자는 단추를 선택하고 앱은 세션을 종료하라는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터(쿠키, 캐시 등)를 지운 후 기본 URL을 엽니다. 기본적으로 단추는 표시되지 않습니다.

  - **유휴 시간 후에 브라우저 새로 고침**: 키오스크 브라우저가 새로 시작 상태에서 다시 시작될 때까지 소요되는 유휴 시간(1-1440분)을 입력합니다. 유휴 시간은 사용자의 마지막 조작 이후 소요된 시간(분)입니다. 기본적으로 이 값은 비어 있거나 공백이며, 이는 유휴 시간 제한이 없음을 나타냅니다.

  - **허용된 웹 사이트**: 특정 웹 사이트가 열리도록 허용하려면 이 설정을 사용합니다. 즉, 디바이스에서 웹 사이트를 제한하거나 차단하려면 이 기능을 사용합니다. 예를 들어 `contoso.com*`의 모든 웹 사이트가 열리도록 허용할 수 있습니다. 기본적으로 모든 웹 사이트가 허용됩니다.

    특정 웹 사이트를 허용하려면 허용되는 웹 사이트 목록을 포함하는 .csv 파일을 업로드합니다. .csv 파일을 추가하지 않으면 모든 웹 사이트가 허용됩니다.

  **확인**을 선택하여 변경 내용을 저장합니다.

- **대체 시작 레이아웃 사용**: 앱의 순서를 포함하여 시작 메뉴에 앱이 표시되는 방법을 설명하는 XML 파일을 입력하려면 **예**를 선택합니다. 시작 메뉴에 추가 사용자 지정이 필요한 경우 이 옵션을 사용합니다. [시작 레이아웃 사용자 지정 및 내보내기](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)에는 몇 가지 지침 및 샘플 XML이 제공됩니다.

- **Windows 작업 표시줄**: 작업 표시줄을 **표시**하거나 **숨기**려면 선택합니다. 기본적으로 작업 표시줄은 표시되지 않습니다. Wi-Fi 아이콘과 같은 아이콘이 표시되지만 최종 사용자가 설정을 변경할 수 없습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#kiosk-settings) 및 [Windows Holographic for Business](kiosk-settings-holographic.md) 디바이스에 대한 키오스크 프로필을 만들 수도 있습니다.
