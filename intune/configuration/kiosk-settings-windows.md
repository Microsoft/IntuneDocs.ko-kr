---
title: Microsoft Intune의 Windows 10용 키오스크 설정 - Azure | Microsoft Docs
description: Windows 10(이상) 디바이스를 단일 앱 및 다중 앱 키오스크로 구성하고, 시작 메뉴를 사용자 지정하고, 앱을 추가하고, 작업 표시줄을 표시하고 웹 브라우저를 Microsoft Intune에서 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 80da0e6952c5aaab6fa8146b2d91d32259966d5d
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74691717"
---
# <a name="windows-10-and-later-device-settings-to-run-as-a-kiosk-in-intune"></a>Intune에서 키오스크로 실행하는 Windows 10 이상 디바이스 설정

Windows 10 이상 디바이스에서 이러한 디바이스가 단일 앱 키오스크 모드 또는 다중 앱 키오스크 모드에서 실행되도록 구성할 수 있습니다.

이 문서에서는 Windows 10 이상 디바이스에서 제어할 수 있는 다양한 메일 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 키오스크 모드로 실행하는 Windows 10 이상 디바이스를 구성합니다.

Intune 관리자는 이러한 설정을 만들어 디바이스에 할당할 수 있습니다.

Intune에서 Windows 키오스크 기능에 대한 자세한 내용은 [키오스크 설정 구성](../kiosk-settings.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

- [프로필을 만듭니다](kiosk-settings.md#create-the-profile).

- 이 키오스크 프로필은 [Microsoft Edge 키오스크 설정](device-restrictions-windows-10.md#microsoft-edge-browser)을 사용하여 생성한 디바이스 제한 프로필과 직접 연관이 됩니다. 요약:

  1. 이 키오스크 프로필을 만들어 디바이스를 키오스크 모드로 실행합니다.
  2. [디바이스 제한 프로필](device-restrictions-windows-10.md#microsoft-edge-browser)을 만들고 Microsoft Edge에서 허용되는 특정 기능 및 설정을 구성합니다.

- 모든 파일, 스크립트 및 바로 가기는 로컬 시스템에 있어야 합니다. 다른 Windows 요구 사항을 비롯 한 자세한 내용은 [사용자 지정 및 내보내기 시작 레이아웃](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)을 참조 하세요.

> [!IMPORTANT]
> 이 키오스크 프로필을 [Microsoft Edge 프로필](device-restrictions-windows-10.md#microsoft-edge-browser)과 동일한 디바이스에 할당해야 합니다.

## <a name="single-full-screen-app-kiosks"></a>단일 전체 화면 앱 키오스크

디바이스에서 하나의 앱만 실행됩니다.

- **키오스크 모드 선택**: **단일 앱의 전체 화면 키오스크**를 선택합니다.

- **사용자 로그온 유형**: 추가한 앱이 입력한 사용자 계정으로 실행됩니다. 옵션은 다음과 같습니다.

  - **자동 로그온(Windows 10 버전 1803 이상)** : 게스트 계정과 유사하게 사용자가 로그인할 필요가 없는 공용 환경의 키오스크에서 사용합니다. 이 설정은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 사용합니다.
  - **로컬 사용자 계정**: 로컬(디바이스 기준) 사용자 계정을 입력합니다. 입력한 계정이 키오스크에 로그인됩니다.

- **애플리케이션 유형**: 애플리케이션 유형을 선택합니다. 옵션은 다음과 같습니다.

  - **Microsoft Edge 브라우저 추가**: **Microsoft Edge 브라우저**를 선택하고 **Edge 키오스크 모드 유형**을 선택합니다.

    - **디지털/대화형 서명**: URL 전체 화면이 열리고 해당 웹 사이트에 콘텐츠가 표시됩니다. [디지털 서명 설정](https://docs.microsoft.com/windows/configuration/setup-digital-signage)은 이 기능에 대한 자세한 정보를 제공합니다.
    - **공용 검색(InPrivate)** : Microsoft Edge의 제한된 다중 탭 버전이 실행됩니다. 사용자는 공개적으로 찾아보거나 해당 검색 세션을 종료할 수 있습니다.

    이러한 옵션에 대한 자세한 내용은 [Microsoft Edge 키오스크 모드 배포](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)를 참조하세요.

    > [!NOTE]
    > 이 설정은 디바이스에서 Microsoft Edge 브라우저를 사용하도록 설정합니다. Microsoft Edge 특정 설정을 구성하려면 디바이스 구성 프로필을 만듭니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10** 플랫폼용 > **디바이스 제한** >  **Microsoft Edge 브라우저**). [Microsoft Edge 브라우저](device-restrictions-windows-10.md#microsoft-edge-browser)는 사용 가능한 설정을 나열하고 설명합니다.

  - **키오스크 브라우저 추가**: **키오스크 브라우저 설정**을 선택합니다. 이러한 설정은 키오스크에서 웹 브라우저 앱을 제어합니다. 스토어에서 [키오스크 브라우저 앱](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP) 을 가져와서 [클라이언트 앱](../apps/apps-add.md)으로 Intune에 추가 해야 합니다. 그런 다음 키오스크 장치에 앱을 할당 합니다.

    다음 설정을 입력합니다.

    - **기본 홈페이지 URL**: 키오스크 브라우저가 열리거나 브라우저가 다시 시작될 때 표시되는 기본 URL을 입력합니다. 예를 들어 `http://bing.com` 또는 `http://www.contoso.com`을 입력합니다.

    - **홈 단추**: 키오스크 브라우저의 홈 단추를 **표시**하거나 **숨깁니다**. 기본적으로 단추는 표시되지 않습니다.

    - **탐색 단추**: 앞으로 및 뒤로 단추를 **표시**하거나 **숨깁니다**. 기본적으로 탐색 단추는 표시되지 않습니다.

    - **세션 종료 단추**: 세션 종료 단추를 **표시**하거나 **숨깁니다**. 표시된 경우 사용자는 단추를 선택하고 앱은 세션을 종료하라는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터(쿠키, 캐시 등)를 지운 후 기본 URL을 엽니다. 기본적으로 단추는 표시되지 않습니다.

    - **유휴 시간 후에 브라우저 새로 고침**: 키오스크 브라우저가 새로 시작 상태에서 다시 시작될 때까지 소요되는 유휴 시간(1-1440분)을 입력합니다. 유휴 시간은 사용자의 마지막 조작 이후 소요된 시간(분)입니다. 기본적으로 이 값은 비어 있거나 공백이며, 이는 유휴 시간 제한이 없음을 나타냅니다.

    - **허용된 웹 사이트**: 특정 웹 사이트가 열리도록 허용하려면 이 설정을 사용합니다. 즉, 디바이스에서 웹 사이트를 제한하거나 차단하려면 이 기능을 사용합니다. 예를 들어 `http://contoso.com`의 모든 웹 사이트가 열리도록 허용할 수 있습니다. 기본적으로 모든 웹 사이트가 허용됩니다.

      특정 웹 사이트를 허용하려면 허용되는 웹 사이트 목록이 포함된 파일을 별도의 줄에 업로드합니다. 파일을 추가하지 않으면 모든 웹 사이트가 허용됩니다. 기본적으로 Intune은 와일드 카드를 지원 합니다. 따라서 `sharepoint.com`와 같이 도메인을 입력 하면 `contoso.sharepoint.com`, `my.sharepoint.com`등의 하위 도메인이 자동으로 허용 됩니다.

      샘플 파일은 다음 목록과 비슷해야 합니다.

      `http://bing.com`  
      `https://bing.com`  
      `http://contoso.com`  
      `https://contoso.com`  
      `office.com`

    > [!NOTE]
    > Microsoft 키오스크 브라우저를 사용 하 여 자동 로그온을 사용 하도록 설정 된 Windows 10 키오스크는 비즈니스용 Microsoft Store의 오프 라인 라이선스를 사용 해야 합니다. 자동 로그온에서 AD (Azure Active Directory) 자격 증명이 없는 로컬 사용자 계정을 사용 하기 때문입니다. 따라서 온라인 라이선스는 평가할 수 없습니다. 자세한 내용은 [오프라인 앱 배포](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)를 참조하세요.

  - **스토어 앱 추가**: **스토어 앱 추가**를 선택하고 목록에서 앱을 선택합니다.

    나열된 앱이 없나요? [클라이언트 앱](../apps/apps-add.md)의 단계를 사용하여 일부 앱을 추가합니다.
    
 - **앱 다시 시작에 대 한 유지 관리 기간 지정**: 기본값은 "구성 되지 않음"입니다. 설치를 완료 하려면 다시 시작 해야 하는 앱을 확인 하려면 "필요"를 선택 합니다.
 
     키오스크 브라우저 또는 기타 비즈니스 앱 용 Microsoft Store를 사용 하는 경우 응용 프로그램 설치를 완료 하기 위해 다시 시작 해야 하는 앱 업데이트를 확인 하는 빈도를 결정 합니다. 구성 되지 않은 경우 앱 업데이트가 설치 된 후 3 일이 지나면 기간 업무 앱에 대 한 Microsoft Store 다시 시작 됩니다.
     
     - **유지 관리 기간 시작 시간**: 클라이언트를 다시 시작 해야 하는 앱 업데이트에 대 한 검사를 시작할 날짜와 시간을 선택 합니다. 기본 시작 시간은 자정 또는 0분입니다.
     
     - **유지 관리 기간 되풀이**: 기본값은 매일입니다.
         앱 업데이트에 대 한 유지 관리 기간을 설정 합니다. 예약 되지 않은 앱 다시 시작을 방지 하기 위한 권장 사항은 매일입니다.

  [ApplicationManagement/ScheduleForceRestartForUpdateFailures CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-scheduleforcerestartforupdatefailures)

## <a name="multi-app-kiosks"></a>다중 앱 키오스크

이 모드의 앱은 시작 메뉴에서 사용할 수 있습니다. 이러한 앱은 사용자가 열 수 있는 유일한 앱입니다. 앱이 다른 앱에 종속된 경우 두 앱 모두 허용되는 앱 목록에 포함되어야 합니다. 예를 들어, Internet Explorer 64비트가 Internet Explorer 32비트에 종속된 경우 “C:\Program Files\internet explorer\iexplore.exe” 및 “C:\Program Files (x86)\Internet Explorer\iexplore.exe”를 모두 허용해야 합니다. 

- **키오스크 모드 선택**: **다중 앱 키오스크**를 선택합니다.

- **S 모드 디바이스에서 Windows 10을 대상으로 지정**:
  - **예**: 키오스크 프로필에 스토어 앱 및 AUMID 앱(Win32 앱 제외)을 허용합니다.
  - **아니요**: 키오스크 프로필에 스토어 앱, Win32 앱 및 AUMID 앱을 허용합니다. 이 키오스크 프로필이 S 모드 디바이스에 배포되지 않습니다.

- **사용자 로그온 유형**: 추가한 앱이 입력한 사용자 계정으로 실행됩니다. 옵션은 다음과 같습니다.

  - **자동 로그온(Windows 10 버전 1803 이상)** : 게스트 계정과 유사하게 사용자가 로그인할 필요가 없는 공용 환경의 키오스크에서 사용합니다. 이 설정은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 사용합니다.
  - **로컬 사용자 계정**: 로컬(디바이스 기준) 사용자 계정을 **추가**합니다. 입력한 계정이 키오스크에 로그인됩니다.
  - **Azure AD 사용자 또는 그룹(Windows 10 버전 1803 이상)** : **추가**를 선택하고 목록에서 Azure AD 사용자 또는 그룹을 선택합니다. 여러 사용자 및 그룹을 선택할 수 있습니다. **선택**을 선택하여 변경 내용을 저장합니다.
  - **HoloLens 방문자**: 방문자 계정은 [공유된 PC 모드 개념](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)에 설명된 대로 사용자 자격 증명이나 인증이 필요 없는 게스트 계정입니다.

- **브라우저 및 애플리케이션**: 키오스크 디바이스에서 실행할 앱을 추가합니다. 여러 개의 앱을 추가할 수 있습니다.

  - **브라우저**

    - **Microsoft Edge 추가**: Microsoft Edge가 앱 그리드에 추가되고 모든 애플리케이션을 이 키오스크에서 실행할 수 있습니다. **Microsoft Edge 키오스크 모드 유형**을 선택합니다.

      - **표준 모드(전체 버전의 Microsoft Edge)** : 모든 검색 기능과 함께 Microsoft Edge의 전체 버전이 실행됩니다. 세션 간에 사용자 데이터 및 상태가 저장됩니다.
      - **공용 검색(InPrivate)** : 전체 화면 모드에서 실행되는 키오스크에 맞춤화된 환경을 사용하여 Microsoft Edge InPrivate의 다중 탭 버전이 실행됩니다.

      이러한 옵션에 대한 자세한 내용은 [Microsoft Edge 키오스크 모드 배포](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)를 참조하세요.

      > [!NOTE]
      > 이 설정은 디바이스에서 Microsoft Edge 브라우저를 사용하도록 설정합니다. Microsoft Edge 특정 설정을 구성하려면 디바이스 구성 프로필을 만듭니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10** 플랫폼용 > **디바이스 제한** >  **Microsoft Edge 브라우저**). [Microsoft Edge 브라우저](device-restrictions-windows-10.md#microsoft-edge-browser)는 사용 가능한 설정을 나열하고 설명합니다.

    - **키오스크 브라우저 추가**: 이러한 설정은 키오스크의 웹 브라우저 앱을 제어합니다. [클라이언트 앱](../apps/apps-add.md)을 사용하여 키오스크 디바이스에 웹 브라우저 앱을 배포해야 합니다.

      다음 설정을 입력합니다.

      - **기본 홈페이지 URL**: 키오스크 브라우저가 열리거나 브라우저가 다시 시작될 때 표시되는 기본 URL을 입력합니다. 예를 들어 `http://bing.com` 또는 `http://www.contoso.com`을 입력합니다.

      - **홈 단추**: 키오스크 브라우저의 홈 단추를 **표시**하거나 **숨깁니다**. 기본적으로 단추는 표시되지 않습니다.

      - **탐색 단추**: 앞으로 및 뒤로 단추를 **표시**하거나 **숨깁니다**. 기본적으로 탐색 단추는 표시되지 않습니다.

      - **세션 종료 단추**: 세션 종료 단추를 **표시**하거나 **숨깁니다**. 표시된 경우 사용자는 단추를 선택하고 앱은 세션을 종료하라는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터(쿠키, 캐시 등)를 지운 후 기본 URL을 엽니다. 기본적으로 단추는 표시되지 않습니다.

      - **유휴 시간 후에 브라우저 새로 고침**: 키오스크 브라우저가 새로 시작 상태에서 다시 시작될 때까지 소요되는 유휴 시간(1-1440분)을 입력합니다. 유휴 시간은 사용자의 마지막 조작 이후 소요된 시간(분)입니다. 기본적으로 이 값은 비어 있거나 공백이며, 이는 유휴 시간 제한이 없음을 나타냅니다.

      - **허용된 웹 사이트**: 특정 웹 사이트가 열리도록 허용하려면 이 설정을 사용합니다. 즉, 디바이스에서 웹 사이트를 제한하거나 차단하려면 이 기능을 사용합니다. 예를 들어 `contoso.com*`의 모든 웹 사이트가 열리도록 허용할 수 있습니다. 기본적으로 모든 웹 사이트가 허용됩니다.

        특정 웹 사이트를 허용하려면 허용되는 웹 사이트 목록을 포함하는 .csv 파일을 업로드합니다. .csv 파일을 추가하지 않으면 모든 웹 사이트가 허용됩니다.

      > [!NOTE]
      > Microsoft 키오스크 브라우저를 사용 하 여 자동 로그온을 사용 하도록 설정 된 Windows 10 키오스크는 비즈니스용 Microsoft Store의 오프 라인 라이선스를 사용 해야 합니다. 자동 로그온에서 AD (Azure Active Directory) 자격 증명이 없는 로컬 사용자 계정을 사용 하기 때문입니다. 따라서 온라인 라이선스는 평가할 수 없습니다. 자세한 내용은 [오프라인 앱 배포](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)를 참조하세요.

  - **애플리케이션**

    - **스토어 앱 추가**: 비즈니스용 Microsoft Store에서 앱을 추가합니다. 앱이 나열되지 않으면 앱을 가져와서 [Intune에 추가](../apps/store-apps-windows.md)할 수 있습니다. 예를 들어 키오스크 브라우저, Excel, OneNote 등을 추가할 수 있습니다.

    - **Win32 앱 추가**: Win32 앱은 Visual Studio Code 또는 Google Chrome과 같은 기존 데스크톱 앱입니다. 다음 속성을 입력합니다.

      - **애플리케이션 이름**: 필수입니다. 애플리케이션의 이름을 입력합니다.
      - **로컬 경로**: 필수입니다. `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 또는 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`와 같이 실행 파일의 경로를 입력합니다.
      - **AUMID(애플리케이션 사용자 모델 ID)** : Win32 앱의 AUMID(애플리케이션 사용자 모델 ID)를 입력합니다. 이 설정에 따라 바탕 화면에 있는 타일의 시작 레이아웃이 결정됩니다. 이 ID를 구하려면 [Get-StartApps](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)를 참조하세요.

    - **AUMID로 추가**: 메모장 또는 계산기와 같은 받은 편지함 Windows 앱을 추가하려면 이 옵션을 사용합니다. 다음 속성을 입력합니다.

      - **애플리케이션 이름**: 필수입니다. 애플리케이션의 이름을 입력합니다.
      - **AUMID(애플리케이션 사용자 모델 ID)** : 필수입니다. Windows 앱의 AUMID(애플리케이션 사용자 모델 ID)를 입력합니다. 이 ID를 가져오려면 [설치된 앱의 애플리케이션 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.

    - **자동 시작**: 선택 사항입니다. 사용자가 로그인할 때 애플리케이션이 자동 시작되도록 선택합니다. 단일 앱만 자동 시작될 수 있습니다.
    - **타일 크기**: 필수입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.

  > [!TIP]
  > 모든 앱을 추가한 후 목록에서 앱을 클릭하고 끌어서 표시 순서를 변경할 수 있습니다.  

- **대체 시작 레이아웃 사용**: 시작 메뉴에 앱의 순서를 포함하여 앱이 표시되는 방법을 설명하는 XML 파일을 입력하려면 **예**를 선택합니다. 시작 메뉴에 추가 사용자 지정이 필요한 경우 이 옵션을 사용합니다. [시작 레이아웃 사용자 지정 및 내보내기](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)에는 몇 가지 지침 및 샘플 XML이 제공됩니다.

- **Windows 작업 표시줄**: 작업 표시줄을 **표시**하거나 **숨기**려면 선택합니다. 기본적으로 작업 표시줄은 표시되지 않습니다. Wi-Fi 아이콘과 같은 아이콘이 표시되지만 최종 사용자가 설정을 변경할 수 없습니다.

- **다운로드 폴더에 대한 액세스 허용**: 사용자가 Windows 탐색기에서 다운로드 폴더에 액세스할 수 있도록 하려면 **예**를 선택합니다. 기본적으로 다운로드 폴더에 대한 액세스는 비활성화되어 있습니다. 이 기능은 일반적으로 최종 사용자가 브라우저에서 다운로드된 항목에 액세스하기 위해 사용됩니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android](device-restrictions-android.md#kiosk), [Android Enterprise](device-restrictions-android-for-work.md#dedicated-device-settings) 및 [Windows Holographic for Business](kiosk-settings-holographic.md) 디바이스에 대한 키오스크 프로필을 만들 수도 있습니다.

또한 Windows 지침에서 [단일 앱 키오스크 설정](https://docs.microsoft.com/windows/configuration/kiosk-single-app) 또는 [다중 앱 키오스크 설정](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps) 을 참조 하세요.
