---
title: Microsoft Intune의 Windows 10용 키오스크 설정 - Azure | Microsoft Docs
description: 시작 메뉴 사용자 지정, 앱 및 작업 표시줄 추가, 웹 브라우저 구성을 포함하여 Windows 10(이상) 디바이스를 단일 앱 및 다중 앱 키오스크로 구성합니다. 또한 Windows Holographic for Business 디바이스를 Microsoft Intune에서 다중 앱 키오스크로 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 574bc38fb9ce47d2b051a74f3f931139c0de7224
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728840"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune의 Windows 10(이상)용 키오스크 설정

Windows 10 디바이스에서 Intune을 사용하여 이러한 디바이스를 키오스크로 실행할 수 있습니다. 키오스크는 하나의 앱을 실행하거나 여러 앱을 실행할 수 있습니다. 또한 시작 메뉴를 표시 및 사용자 지정하고, Win32 앱을 비롯 한 다른 앱을 추가하고, 웹 브라우저에 특정 홈페이지를 추가할 수도 있습니다. 

이 문서에서는 아래 단계에 따라 Intune에서 단일 앱 키오스크 또는 다중 앱 키오스크를 만듭니다.

Intune은 디바이스당 하나의 키오스크 프로필을 지원합니다. 단일 디바이스에서 여러 키오스크 프로필이 필요한 경우 [사용자 지정 OMA-URI](custom-settings-windows-10.md)를 사용할 수 있습니다.

## <a name="kiosk-settings"></a>키오스크 설정

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.
3. 다음 속성을 입력합니다.

   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 설정에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
   - **플랫폼**: **Windows 10 이상**을 선택합니다.
   - **프로필 유형**: **키오스크(미리 보기)** 를 선택합니다.

4. **키오스크 모드**를 선택합니다. **키오스크 모드**는 정책에서 지원되는 키오스크 모드 유형을 식별합니다. 다음 옵션을 사용할 수 있습니다.

    - **구성되지 않음**(기본값): 키오스크 모드를 사용하도록 설정하지 않는 정책입니다.
    - **단일 앱, 전체 화면 키오스크**: 장치는 단일 사용자 계정으로 실행되고 해당 계정을 단일 Store 앱으로 잠급니다. 이에 따라 사용자가 로그인하면 특정 앱이 시작됩니다. 또한 이 모드는 사용자가 새 앱을 열거나 실행 중인 앱을 변경하는 것을 제한합니다.
    - **다중 앱 키오스크**: 장치는 AUMID(응용 프로그램 사용자 모델 ID)를 사용하여 여러 Store 앱, Win32 앱 또는 받은 편지함 Windows 앱을 실행합니다. 사용자가 추가하는 앱만 디바이스에서 사용할 수 있습니다.

        다중 앱 키오스크 또는 용도가 고정된 디바이스의 장점은 필요한 앱에만 액세스하여 사용자에게 이해하기 쉬운 환경을 제공하는 것입니다. 또한 필요하지 않은 앱은 보기에서 제거됩니다.

## <a name="single-full-screen-app-kiosks"></a>단일 전체 화면 앱 키오스크
단일 앱 키오스크 모드를 선택하는 경우 다음 설정을 입력합니다.

- **사용자 로그온 유형**: 추가한 앱이 입력한 사용자 계정으로 실행됩니다. 옵션은 다음과 같습니다.

  - **자동 로그온(Windows 10 버전 1803 이상)**: 게스트 계정과 비슷하게, 사용자가 로그온할 필요가 없는 공용 환경의 키오스크에 해당합니다. 이 설정은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 사용합니다.
  - **로컬 사용자 계정**: 로컬(장치 기준) 사용자 계정을 입력합니다. 입력한 계정이 키오스크에 로그인하는 데 사용됩니다.

- **응용 프로그램 유형**: **Store 앱**을 선택합니다.

- **키오스크 모드에서 실행할 앱**: **스토어 앱 추가**를 선택하고 목록에서 앱을 선택합니다.

    나열된 앱이 없나요? [클라이언트 앱](apps-add.md)의 단계를 사용하여 일부 앱을 추가합니다.

    **확인**을 선택하여 변경 내용을 저장합니다.

- **키오스크 브라우저 설정**: 이러한 설정은 키오스크에서 웹 브라우저 앱을 제어합니다. Store에서 [키오스크 브라우저 앱](https://businessstore.microsoft.com/store/details/kiosk-browser/9NGB5S5XG2KP)을 가져오고, Intune에 [클라이언트 앱](apps-add.md)으로 추가한 후, 키오스크 디바이스에 앱을 할당합니다.

  다음 설정을 입력합니다.

  - **기본 홈페이지 URL**: 키오스크 브라우저가 열리거나 브라우저가 다시 시작될 때 표시되는 기본 URL을 입력합니다. 예를 들어 `http://bing.com` 또는 `http://www.contoso.com`을 입력합니다.

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

- **S 모드 장치에서 Windows 10을 대상으로 지정**: 키오스크 프로필에서 스토어 앱 및 AUMID 앱(Win32 앱 제외)을 허용하려면 **예**를 선택합니다. 키오스크 프로필에서 스토어 앱, Win32 앱 및 AUMID 앱을 허용하려면 **아니요**를 선택합니다. **아니요**를 선택하면 이 키오스크 프로필이 S 모드 장치에 배포되지 않습니다.

- **사용자 로그온 유형**: 추가한 앱이 입력한 사용자 계정으로 실행됩니다. 옵션은 다음과 같습니다.

  - **자동 로그온(Windows 10 버전 1803 이상)**: 게스트 계정과 비슷하게, 사용자가 로그온할 필요가 없는 공용 환경의 키오스크에 해당합니다. 이 설정은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 사용합니다.
  - **로컬 사용자 계정**: 로컬(장치 기준) 사용자 계정을 **추가**합니다. 입력한 계정이 키오스크에 로그인하는 데 사용됩니다.
  - **Azure AD 사용자 또는 그룹(Windows 10 버전 1803 이상)**: **추가**를 선택하여 목록에서 Azure AD 사용자 또는 그룹을 선택합니다. 여러 사용자 및 그룹을 선택할 수 있습니다. **선택**을 선택하여 변경 내용을 저장합니다.
  - **HoloLens 방문자**: 방문자 계정은 [공유된 PC 모드 개념](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)에 설명된 대로 사용자 자격 증명이나 인증이 필요 없는 게스트 계정입니다.

- **응용 프로그램**: 키오스크 장치에서 실행할 앱을 추가합니다. 여러 개의 앱을 추가할 수 있습니다.

  - **스토어 앱 추가**: 비즈니스용 Microsoft Store에서 앱을 추가합니다. 앱이 나열되지 않으면 앱을 가져와서 [Intune에 추가](store-apps-windows.md)할 수 있습니다. 예를 들어 키오스크 브라우저, Excel, OneNote 등을 추가할 수 있습니다.

  - **Win32 앱 추가**: Win32 앱은 Visual Studio Code 또는 Google Chrome과 같은 기존 데스크톱 앱입니다. 다음 속성을 입력합니다.

    - **응용 프로그램 이름**: 필수입니다. 응용 프로그램의 이름을 입력합니다.
    - **로컬 경로**: 필수입니다. `C:\Program Files (x86)\Microsoft VS Code\Code.exe` 또는 `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`와 같이 실행 파일의 경로를 입력합니다.
    - **AUMID(응용 프로그램 사용자 모델 ID)**: Win32 앱의 AUMID(응용 프로그램 사용자 모델 ID)를 입력합니다. 이 설정에 따라 바탕 화면에 있는 타일의 시작 레이아웃이 결정됩니다. 이 ID를 가져오려면 [설치된 앱의 응용 프로그램 사용자 모델 ID 찾기](https://docs.microsoft.com/powershell/module/startlayout/get-startapps?view=win10-ps)를 참조하세요.
    - **타일 크기**: 필수입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.
  
  - **AUMID로 추가**: 메모장 또는 계산기와 같은 받은 편지함 Windows 앱을 추가하려면 이 옵션을 사용합니다. 다음 속성을 입력합니다. 

    - **응용 프로그램 이름**: 필수입니다. 응용 프로그램의 이름을 입력합니다.
    - **AUMID(응용 프로그램 사용자 모델 ID)**: 필수입니다. Windows 앱의 AUMID(응용 프로그램 사용자 모델 ID)를 입력합니다. 이 ID를 가져오려면 [설치된 앱의 응용 프로그램 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.
    - **타일 크기**: 필수입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.

  > [!TIP]
  > 모든 앱을 추가한 후 목록에서 앱을 클릭하고 끌어서 표시 순서를 변경할 수 있습니다.  

  **확인**을 선택하여 변경 내용을 저장합니다.

- **키오스크 브라우저 설정**: 이러한 설정은 키오스크에서 웹 브라우저 앱을 제어합니다. [클라이언트 앱](apps-add.md)을 사용하여 키오스크 장치에 웹 브라우저 앱을 배포해야 합니다.

  다음 설정을 입력합니다.

  - **기본 홈페이지 URL**: 키오스크 브라우저가 열리거나 브라우저가 다시 시작될 때 표시되는 기본 URL을 입력합니다. 예를 들어 `http://bing.com` 또는 `http://www.contoso.com`을 입력합니다.

  - **홈 단추**: 키오스크 브라우저의 홈 단추를 **표시**하거나 **숨깁니다**. 기본적으로 단추는 표시되지 않습니다.

  - **탐색 단추**: 앞으로 및 뒤로 단추를 **표시**하거나 **숨깁니다**. 기본적으로 탐색 단추는 표시되지 않습니다.

  - **세션 종료 단추**: 세션 종료 단추를 **표시**하거나 **숨깁니다**. 표시된 경우 사용자는 단추를 선택하고 앱은 세션을 종료하라는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터(쿠키, 캐시 등)를 지운 후 기본 URL을 엽니다. 기본적으로 단추는 표시되지 않습니다.

  - **유휴 시간 후에 브라우저 새로 고침**: 키오스크 브라우저가 새로 시작 상태에서 다시 시작될 때까지 소요되는 유휴 시간(1-1440분)을 입력합니다. 유휴 시간은 사용자의 마지막 조작 이후 소요된 시간(분)입니다. 기본적으로 이 값은 비어 있거나 공백이며, 이는 유휴 시간 제한이 없음을 나타냅니다.

  - **허용된 웹 사이트**: 특정 웹 사이트가 열리도록 허용하려면 이 설정을 사용합니다. 즉, 디바이스에서 웹 사이트를 제한하거나 차단하려면 이 기능을 사용합니다. 예를 들어 `contoso.com*`의 모든 웹 사이트가 열리도록 허용할 수 있습니다. 기본적으로 모든 웹 사이트가 허용됩니다.

    특정 웹 사이트를 허용하려면 허용되는 웹 사이트 목록을 포함하는 .csv 파일을 업로드합니다. .csv 파일을 추가하지 않으면 모든 웹 사이트가 허용됩니다.

  **확인**을 선택하여 변경 내용을 저장합니다.

- **대체 시작 레이아웃 사용**: 시작 메뉴에 앱의 순서를 포함하여 앱이 표시되는 방법을 설명하는 XML 파일을 입력하려면 **예**를 선택합니다. 시작 메뉴에 추가 사용자 지정이 필요한 경우 이 옵션을 사용합니다. [시작 레이아웃 사용자 지정 및 내보내기](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)에는 몇 가지 지침 및 샘플 XML이 제공됩니다.

- **Windows 작업 표시줄**: 작업 표시줄을 **표시**하거나 **숨기**려면 선택합니다. 기본적으로 작업 표시줄은 표시되지 않습니다.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business 디바이스에서 이러한 디바이스가 단일 앱 키오스크 모드 또는 다중 앱 키오스크 모드에서 실행되도록 구성할 수 있습니다. Windows Holographic for Business에서는 일부 기능이 지원되지 않습니다.

#### <a name="single-full-screen-app-kiosks"></a>단일 전체 화면 앱 키오스크
단일 앱 키오스크 모드를 선택하는 경우 다음 설정을 입력합니다.

- **사용자 로그온 유형**: **로컬 사용자 계정**을 선택하여 로컬(장치 기준) 사용자 계정 또는 키오스크 앱과 연결된 MSA(Microsoft 계정) 계정을 입력합니다. **자동 로그온** 사용자 계정 유형은 Windows Holographic for Business에서 지원되지 않습니다.

- **응용 프로그램 유형**: **Store 앱**을 선택합니다.

- **키오스크 모드에서 실행할 앱**: **스토어 앱 추가**를 선택하고 목록에서 앱을 선택합니다.

    나열된 앱이 없나요? [클라이언트 앱](apps-add.md)의 단계를 사용하여 일부 앱을 추가합니다.

    **확인**을 선택하여 변경 내용을 저장합니다.

#### <a name="multi-app-kiosks"></a>다중 앱 키오스크
이 모드의 앱은 시작 메뉴에서 사용할 수 있습니다. 이러한 앱은 사용자가 열 수 있는 유일한 앱입니다. 다중 앱 키오스크 모드를 선택하면 다음 설정을 입력합니다.

- **S 모드 장치에서 Windows 10을 대상으로 지정**: **아니요**를 선택합니다. Windows Holographic for Business에서는 S 모드가 지원되지 않습니다.

- **사용자 로그온 유형**: 추가하는 앱을 사용할 수 있는 사용자 계정을 하나 이상 추가합니다. 옵션은 다음과 같습니다. 

  - **자동 로그온**: Windows Holographic for Business에서 지원되지 않습니다.
  - **로컬 사용자 계정**: 로컬(장치 기준) 사용자 계정을 **추가**합니다. 입력한 계정이 키오스크에 로그인하는 데 사용됩니다.
  - **Azure AD 사용자 또는 그룹(Windows 10, 버전 1803 이상)**: 장치에 로그인할 사용자 자격 증명이 필요합니다. **추가**를 선택하여 목록에서 Azure AD 사용자 또는 그룹을 선택합니다. 여러 사용자 및 그룹을 선택할 수 있습니다. **선택**을 선택하여 변경 내용을 저장합니다.
  - **HoloLens 방문자**: 방문자 계정은 [공유된 PC 모드 개념](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc#shared-pc-mode-concepts)에 설명된 대로 사용자 자격 증명이나 인증이 필요 없는 게스트 계정입니다.

- **응용 프로그램**: 키오스크 장치에서 실행할 앱을 추가합니다. 여러 개의 앱을 추가할 수 있습니다.

  - **Store 앱 추가**: [클라이언트 앱](apps-add.md)을 사용하여 추가한 기존 앱을 선택합니다. 앱이 나열되지 않으면 앱을 가져와서 [Intune에 추가](store-apps-windows.md)할 수 있습니다.
  - **Win32 앱 추가**: Windows Holographic for Business에서 지원되지 않습니다.
  - **AUMID로 추가**: 받은 편지함 Windows 앱을 추가하려면 이 옵션을 사용합니다. 다음 속성을 입력합니다. 

    - **응용 프로그램 이름**: 필수입니다. 응용 프로그램의 이름을 입력합니다.
    - **AUMID(응용 프로그램 사용자 모델 ID)**: 필수입니다. Windows 앱의 AUMID(응용 프로그램 사용자 모델 ID)를 입력합니다. 이 ID를 가져오려면 [설치된 앱의 응용 프로그램 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.
    - **타일 크기**: 필수입니다. 작은, 중간 크기, 넓은 또는 큰 앱 타일 크기를 선택합니다.

- **키오스크 브라우저 설정**: Windows Holographic for Business에서 지원되지 않습니다.

- **대체 시작 레이아웃 사용**: 시작 메뉴에 앱의 순서를 포함하여 앱이 표시되는 방법을 설명하는 XML 파일을 입력하려면 **예**를 선택합니다. 시작 메뉴에 추가 사용자 지정이 필요한 경우 이 옵션을 사용합니다. [시작 레이아웃 사용자 지정 및 내보내기](https://docs.microsoft.com/hololens/hololens-kiosk#start-layout-for-hololens)는 몇 가지 지침을 제공하며, Windows Holographic for Business 장치에 대한 특정 XML 파일을 포함합니다.

- **Windows 작업 표시줄**: Windows Holographic for Business에서 지원되지 않습니다.



## <a name="next-steps"></a>다음 단계
[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android](device-restrictions-android.md#kiosk) 및 [Android 엔터프라이즈](device-restrictions-android-for-work.md#kiosk-settings) 디바이스에 대한 키오스크 프로필을 만들 수도 있습니다.