---
title: S 모드 디바이스에서 Win32 앱 사용
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 S 모드 디바이스에서 Win32 앱을 사용하도록 설정하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d2ab21321b171c8fe8f5f9dab3032507c0e740cf
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059764"
---
# <a name="enable-win32-apps-on-s-mode-devices"></a>S 모드 디바이스에서 Win32 앱 사용

[Windows 10 S 모드](https://docs.microsoft.com/windows/deployment/s-mode)는 스토어 앱만 실행하는 잠긴 운영 체제입니다. 기본적으로 Windows S 모드 디바이스에서는 Win32 앱을 설치 및 실행할 수 없습니다. 이러한 디바이스에는 단일 *Win 10 S 기본 정책*이 포함되어 있습니다. 이 정책에 따라 S 모드 디바이스에서는 Win32 앱을 실행할 수 없습니다. 그러나 Intune에서 **S 모드 추가 정책**을 만들고 사용하여 Windows 10 S 모드 관리 디바이스에서 Win32 앱을 설치 및 실행할 수 있습니다. [WDAC(Microsoft Defender Application Control)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) PowerShell 도구를 사용하여 Windows S 모드에 대한 추가 정책을 하나 이상 만들 수 있습니다. [DGSS(Device Guard Signing Service)](https://go.microsoft.com/fwlink/?linkid=2095629) 또는 [SignTool.exe](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/signing-policies-with-signtool)를 사용하여 추가 정책에 서명한 다음, Intune을 통해 정책을 업로드 및 배포해야 합니다. 또는 조직의 코드 서명 인증서로 추가 정책에 서명할 수 있지만 DGSS를 사용하는 것이 좋습니다. 조직의 코드 서명 인증서를 사용하는 경우 코드 서명 인증서가 연결된 루트 인증서가 디바이스에 있어야 합니다.

Intune에서 S 모드 추가 정책을 할당하면 디바이스가 기존 S 모드 정책에 대한 예외를 적용할 수 있습니다. 그러면 서명된 해당 앱 카탈로그를 업로드할 수 있습니다. 이 정책은 S 모드 디바이스에서 사용할 수 있는 앱(앱 카탈로그)의 허용 목록을 설정합니다.

> [!NOTE]
> S 모드 디바이스에서 Win32 앱은 Windows 10 11월 2019 업데이트(빌드 18363) 이상 버전에서만 지원됩니다.

<!-- Add WDAC tooling diagram  -->

S 모드의 Windows 10 디바이스에서 Win32 앱을 실행하도록 허용하는 단계는 다음과 같습니다.

1. Windows 10 S 등록 프로세스의 일부로 Intune을 통해 S 모드 디바이스를 사용하도록 설정합니다.
2. Win32 앱을 허용하는 추가 정책을 만듭니다.
   - [WDAC(Microsoft Defender Application Control)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) 도구를 사용하여 추가 정책을 만들 수 있습니다. 정책 내의 기본 정책 ID는 클라이언트에서 하드 코드된 모드 기본 정책 ID와 일치해야 합니다. 또한 정책 버전이 이전 버전보다 높아야 합니다.
   - DGSS를 사용하여 추가 정책에 서명할 수 있습니다. 자세한 내용은 [Device Guard 서명을 사용하여 코드 무결성 정책 서명](https://docs.microsoft.com/microsoft-store/sign-code-integrity-policy-with-device-guard-signing)을 참조하세요.
   - Windows 10 S 모드 추가 정책(아래 참조)을 만들어 서명된 추가 정책을 Intune에 업로드합니다.
3. Intune을 통해 다음과 같이 Win32 앱 카탈로그를 허용합니다.
   - 카탈로그 파일(모든 앱에 대해 1개)을 만들고 DGSS 또는 다른 인증서 인프라를 사용하여 서명합니다.
   - [Microsoft Win32 콘텐츠 준비 도구](https://go.microsoft.com/fwlink/?linkid=2065730)를 사용하여 서명된 카탈로그를 *.intunewin* 파일에 패키지합니다. 자세한 내용은 [Win32 앱 관리 - 업로드를 위한 Win32 앱 콘텐츠 준비](~/apps/apps-win32-app-management.md#prepare-the-win32-app-content-for-upload)를 참조하세요.
   - Intune은 서명된 앱 카탈로그를 적용하여 [Intune 관리 확장](~/apps/intune-management-extension.md)을 사용하는 S 모드 디바이스에서 Win32 앱을 설치합니다.

> [!NOTE]
> Windows 10 S 모드의 LOB(기간 업무)`.appx` 및 `.appx` 번들은 MSFB(Microsoft Store for Business) 서명을 통해 지원됩니다.
>
> 앱에 대한 **S 모드 추가 정책**은 Intune 관리 확장을 통해 제공되어야 합니다.
>
> S 모드 정책은 디바이스 수준에서 적용됩니다. 여러 대상 정책이 디바이스에 병합됩니다. 병합된 정책이 디바이스에 적용됩니다.

Windows 10 S 모드 추가 정책을 만들려면 다음 단계를 수행하세요.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **Intune** 창에서 **클라이언트 앱** > **S 모드 추가 정책** > **정책 만들기**를 선택합니다.
3. **정책 파일**을 추가하기 전에 해당 파일을 만들고 서명해야 합니다. 자세한 내용은 다음을 참조하십시오.
    - [ PowerShell 도구를 사용하여 WDAC 정책을 만들고 이진 형식으로 변환](https://go.microsoft.com/fwlink/?linkid=2095387)
    - [Device Guard 서명 서비스를 사용하여 서명](https://go.microsoft.com/fwlink/?linkid=2095629) **(권장)**

4. **기본 사항** 페이지에서 다음 값을 추가합니다.

    | 값 | 설명 |
    |--------------|------------------------------------------------|
    | 정책 파일 | WDAC 정책을 포함하는 파일입니다. |
    | 이름 | 이 정책의 이름입니다. |
    | 설명 | [선택 사항] 이 정책에 대한 설명입니다. |

5. **다음: 범위 태그**를 클릭합니다.<br>
   **범위 태그** 페이지에서 필요에 따라 Intune에서 앱 정책을 볼 수 있는 사용자를 결정하도록 범위 태그를 구성할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용](~/fundamentals/scope-tags.md)을 참조하세요.

6. **다음: 할당**을 클릭합니다.<br>
   **할당** 페이지에서는 사용자 및 디바이스에 정책을 할당할 수 있습니다. Intune에서 디바이스를 관리하는지 여부에 관계없이 디바이스에 정책을 할당할 수 있다는 점에 유의해야 합니다.
7. **다음: 검토 + 만들기**를 클릭하여 프로필에 대해 입력한 값을 검토합니다.
8. 작업이 완료되면 **만들기**를 클릭하여 Intune에서 S 모드 추가 정책을 만듭니다. 

정책이 만들어지면 Intune의 S 모드 추가 정책 목록에 추가된 것을 볼 수 있습니다. 정책이 할당되면 해당 정책이 디바이스에 배포됩니다. 앱은 추가 정책과 동일한 보안 그룹에 배포해야 합니다. 이러한 디바이스에 앱 대상을 지정하고 할당을 시작할 수 있습니다. 그러면 최종 사용자가 S 모드 디바이스에서 앱을 설치 및 실행할 수 있습니다.

## <a name="removal-of-s-mode-policy"></a>S 모드 정책 제거

현재 디바이스에서 S 모드 추가 정책을 제거하려면 빈 정책을 할당 및 배포하여 기존 S 모드 추가 정책을 덮어써야 합니다.

## <a name="policy-reporting"></a>정책 보고

디바이스 수준에서 적용되는 S 모드 추가 정책에는 디바이스 수준 보고만 포함되어 있습니다. 디바이스 수준 보고는 성공 및 오류 조건에 사용할 수 있습니다. 

S 모드 보고 정책에 대해 Intune 콘솔에 표시되는 값 보고:
- **성공**: S 모드 추가 정책이 적용됩니다.
- **알 수 없음**: S 모드 추가 정책의 상태를 알 수 없습니다.
- **TokenError**: S 모드 추가 정책이 구조적으로 양호하지만 토큰을 인증하는 동안 오류가 발생했습니다.
- **NotAuthorizedByToken**: 토큰이 이 S 모드 추가 정책에 대한 권한을 부여하지 않습니다.
- **PolicyNotFound**: S 모드 추가 정책을 찾을 수 없습니다.

## <a name="next-steps"></a>다음 단계

- 자세한 내용은 [S 모드의 Win32 앱](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-control/lob-win32-apps-on-s)을 참조하세요.
- Intune의 앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.
- Win32 앱에 대한 자세한 내용은 [Intune Win32 앱 관리](~/apps/apps-win32-app-management.md)를 참조하세요.
