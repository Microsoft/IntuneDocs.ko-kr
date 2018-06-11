---
title: Microsoft Intune의 Windows 10용 키오스크 설정 - Azure | Microsoft Docs
description: Windows 10을 실행하는 장치에서 장치 설정 및 기능을 제어하는 데 사용할 수 있는 Microsoft Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 897ff48253961d6e1aa83bf36113c362d4548fbf
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745179"
---
# <a name="kiosk-settings-for-windows-10-and-later-in-intune"></a>Intune의 Windows 10(이상)용 키오스크 설정

키오스크 프로필을 사용하여 Windows 10 장치에서 하나 또는 여러 앱을 실행하도록 구성할 수 있습니다. 또한 키오스크 프로필을 구성할 때 시작 메뉴가 표시되는지 여부, 웹 브라우저가 설치되는지 여부 및 더 많은 옵션을 선택할 수 있습니다.

## <a name="kiosk-settings"></a>키오스크 설정

1. 키오스크 환경을 만들려면 **추가**를 선택합니다.
2. 키오스크에 대한 **키오스크 구성 이름**을 입력합니다. 이 이름은 응용 프로그램 그룹, 시작 메뉴 상의 이러한 앱에 대한 레이아웃 및 이 키오스크 구성에 할당된 사용자를 식별합니다.
3. **키오스크 모드**를 선택합니다. **키오스크 모드**는 정책에서 지원되는 키오스크 모드 유형을 식별합니다. 다음 옵션을 사용할 수 있습니다.

  - **구성되지 않음**(기본값): 키오스크 모드를 사용하도록 설정하지 않는 정책입니다.
  - **단일 전체 화면 앱 키오스크**: 프로필을 사용하면 장치를 단일 사용자 계정으로 실행하고, 단일 UWP(유니버설 Windows 플랫폼) 앱에 잠글 수 있습니다. 이에 따라 사용자가 로그인하면 특정 앱이 시작됩니다. 또한 이 모드는 사용자가 새 앱을 열거나 실행 중인 앱을 변경하는 것을 제한합니다.
  - **다중 앱 키오스크**: 프로필을 사용하면 장치에서 여러 UWP(유니버설 Windows 플랫폼) 앱 또는 Win32 앱을 실행할 수 있습니다. 또한 다른 사용자 계정에 다른 앱을 할당할 수도 있습니다. 추가한 앱만 사용자가 사용할 수 있습니다. 다중 앱 키오스크 또는 용도가 고정된 장치의 장점은 필요한 앱에만 액세스하여 사용자에게 이해하기 쉬운 환경을 제공하는 것입니다. 또한 필요하지 않은 앱은 보기에서 제거됩니다.

#### <a name="single-full-screen-app-kiosks"></a>단일 전체 화면 앱 키오스크
다음 설정을 입력합니다.

- **UWP(유니버설 Windows 플랫폼) 앱 식별자**: 키오스크 앱의 **AUMID(응용 프로그램 사용자 모델 ID)** 를 입력합니다. 또는 [모바일 앱](apps-add.md)을 사용하여 추가한 기존 관리되는 앱을 선택합니다.

    [설치된 앱의 응용 프로그램 사용자 모델 ID 찾기](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)를 참조하세요.

- **사용자 계정 유형**: 다음과 같은 옵션이 있습니다.

  - **자동 로그온**: 자동 로그온을 사용하도록 설정된 공용 환경의 키오스크에서는 최소한의 권한이 있는 사용자(예: 로컬 표준 사용자 계정)를 사용해야 합니다. 키오스크 모드에 대해 Azure AD(Active Directory) 계정을 구성하려면 `AzureAD\user@contoso.com` 형식을 사용합니다.
  - **로컬 사용자 계정** - 키오스크 앱과 연결된 로컬(장치에 대한) 사용자 계정 또는 Azure AD 계정 로그인을 입력합니다. Azure AD 도메인에 가입된 계정의 경우 `domain\username@tenant.org` 형식을 사용하여 계정을 입력합니다.

#### <a name="multi-app-kiosks"></a>다중 앱 키오스크
이 모드의 앱은 시작 메뉴에서 사용할 수 있습니다. 이러한 앱은 사용자가 열 수 있는 유일한 앱입니다. 

[다중 앱 키오스크](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#configure-a-kiosk-in-microsoft-intune)는 허용되는 앱 및 기타 설정을 나열하는 키오스크 구성을 사용합니다.

다음 설정을 입력합니다.

- **Win32 앱 추가**: Win32 앱은 기존의 데스크톱 앱입니다. **앱 이름** 및 **식별자**를 입력합니다. **식별자**는 장치와 관련하여 실행 파일의 정규화된 경로 이름입니다.
- **관리되는 앱 추가**: [Intune의 모바일 앱](apps-add.md)을 사용하여 추가한 기존 관리되는 앱을 선택합니다.
- **AUMID로 앱 추가**: [앱의 AUMID](https://docs.microsoft.com/windows-hardware/customize/enterprise/find-the-application-user-model-id-of-an-installed-app)(UWP 앱)를 입력합니다.
- **작업 표시줄**: 키오스크에서 작업 표시줄을 **사용**(표시)하도록 선택하거나 **구성되지 않음**(숨김)으로 유지합니다.
- **시작 메뉴 레이아웃**: 시작 메뉴에 앱의 순서를 포함하여 앱이 표시되는 방법을 설명하는 XML 파일을 입력합니다. [시작 레이아웃 사용자 지정 및 내보내기](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout)에는 몇 가지 지침 및 샘플 XML이 제공됩니다.

  [다중 앱을 실행하는 Windows 10 키오스크 만들기](https://docs.microsoft.com/windows/configuration/lock-down-windows-10-to-specific-apps#create-xml-file)에서는 XML 파일의 사용 및 만들기에 관한 자세한 세부 정보를 제공합니다.

- **사용자 계정 유형**: 추가하는 앱을 사용할 수 있는 사용자 계정을 하나 이상 추가합니다. 계정이 로그인하면 구성에 정의된 앱만 사용할 수 있습니다. 계정은 장치에 로컬이거나 키오스크 앱과 연결된 Azure AD 계정 로그인일 수도 있습니다.

    자동 로그온을 사용하도록 설정된 공용 환경의 키오스크에서는 최소한의 권한이 있는 사용자 유형(예: 로컬 표준 사용자 계정)을 사용해야 합니다. 키오스크 모드에 대해 Azure AD(Active Directory) 계정을 구성하려면 `domain\user@tenant.com` 형식을 사용합니다.

## <a name="kiosk-web-browser-settings"></a>키오스크 웹 브라우저 설정

이러한 설정은 키오스크에서 웹 브라우저 앱을 제어합니다. [모바일 앱](apps-add.md)을 사용하여 키오스크 장치에 웹 브라우저 앱을 배포했는지 확인합니다.

1. 다음 설정을 입력합니다.

  - **기본 홈페이지 URL**: 브라우저가 열리거나 다시 시작할 때 키오스크 브라우저가 열리는 기본 URL을 입력합니다.

  - **홈 단추 표시**: 키오스크 브라우저의 홈 단추를 표시하거나(**필수**) 숨깁니다(**구성되지 않음**). 기본적으로 이 단추는 [구성되지 않음]입니다.

  - **탐색 단추 표시**: 앞으로 및 뒤로 단추를 표시하거나(**필수**) 숨깁니다(**구성되지 않음**). 기본적으로 탐색 단추는 [구성되지 않음]입니다.

  - **사용자가 유휴 시간 제한을 초과하면 브라우저를 새로 고침**: 키오스크 브라우저가 새로 시작 상태에서 다시 시작될 때까지의 세션 유휴 상태 시간(분)을 입력합니다. 값은 1-1440분의 정수입니다. 기본적으로 이 값은 비어 있거나 공백이며, 이는 유휴 시간 제한이 없음을 나타냅니다.

  - **차단된 웹 사이트**: 차단된 웹 사이트 URL 목록입니다(와일드카드 지원). 브라우저에서 특정 사이트를 열지 못하도록 하려면 이 설정을 사용합니다. 목록이 포함된 .csv 파일을 **가져올** 수도 있습니다. 또는 추가하는 사이트가 포함된 .csv 파일을 만듭니다(**내보내기**).

  - **웹 사이트 예외**: 차단된 웹 사이트 URL에 대한 예외 목록입니다(와일드카드 지원). 브라우저에서 특정 사이트를 열 수 있도록 하려면 이 설정을 사용합니다. 이러한 예외는 차단된 URL의 하위 집합입니다. URL이 차단된 웹 사이트 목록 및 웹 사이트 예외 목록에 있으면 예외가 적용됩니다.

    목록이 포함된 .csv 파일을 **가져올** 수도 있습니다. 또는 추가하는 사이트가 포함된 .csv 파일을 만듭니다(**내보내기**).

2. **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="next-steps"></a>다음 단계
[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.