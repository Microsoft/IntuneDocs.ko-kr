---
title: Microsoft Intune에서 Windows 10 디바이스에 PowerShell 스크립트 추가 - Azure | Microsoft Docs
description: PowerShell 스크립트를 만들고 실행하고, Azure Active Directory 그룹에 스크립트 정책을 할당하고, 보고서를 사용하여 스크립트를 모니터링하고, Microsoft Intune에서 Windows 10 디바이스에 추가한 스크립트를 삭제하는 단계를 살펴보세요. 또한 몇 가지 일반적인 문제 및 해결 방법을 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/14/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b7ea047daca5dad327b431986840a59074614d1
ms.sourcegitcommit: f8bbd9bac2016a77f36461bec260f716e2155b4a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65732629"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용

Intune에서 Microsoft Intune 관리 확장을 사용하여 Windows 10 디바이스에서 실행되는 PowerShell 스크립트를 업로드합니다. 관리 확장은 Windows 10 MDM(모바일 디바이스 관리)을 개선하며 사용자가 최신 관리로 더 손쉽게 이행할 수 있도록 합니다.

이 기능은 다음에 적용됩니다.

- Windows 10 이상

## <a name="move-to-modern-management"></a>최신 관리 기능으로 전환

최종 사용자 컴퓨팅은 디지털 변형을 거치는 중입니다. 기존의 클래식 IT는 단일 디바이스 플랫폼, 회사 소유 디바이스, 사무실에서 일하는 사용자, 여러 가지 사후 수동 IT 프로세스에 집중합니다. 최신 작업 공간에서는 사용자와 회사가 소유한 여러 플랫폼을 사용하고, 사용자가 장소에 구애받지 않고 일할 수 있으며, 자동화된 능동적 IT 프로세스를 제공합니다.

Microsoft Intune과 같은 MDM 서비스는 Windows 10을 실행하는 모바일 및 데스크톱 디바이스를 관리할 수 있습니다. 기본 제공 Windows 10 관리 클라이언트는 Intune과 통신하여 엔터프라이즈 관리 작업을 실행합니다. 고급 디바이스 구성, 문제 해결과 같은 일부 작업이 필요할 수도 있습니다. Win32 앱 관리의 경우, Windows 10 디바이스에서 [Win32 앱 관리](apps-win32-app-management.md) 기능을 사용할 수 있습니다.

Intune 관리 확장은 기본 제공 Windows 10 MDM 기능을 보완합니다. Windows 10 디바이스에서 실행할 PowerShell 스크립트를 만들 수 있습니다. 예를 들어 고급 디바이스 구성을 수행하는 PowerShell 스크립트를 만들고, Intune에 스크립트를 업로드하고, 스크립트를 Azure AD(Active Directory) 그룹에 할당하고, 스크립트를 실행할 수 있습니다. 그런 다음, 시작부터 완료까지 스크립트의 실행 상태를 모니터링할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

Intune 관리 확장에는 다음과 같은 필수 구성 요소가 있습니다.

- 디바이스가 Azure AD에 조인되거나 등록되어 있고, Azure AD 및 Intune에 대한 [자동 등록](quickstart-setup-auto-enrollment.md)이 구성되어 있어야 합니다. Intune 관리 확장은 Azure AD에 조인되고, 하이브리드 도메인에 조인되고, 등록을 마친 관리형 Windows 디바이스를 지원합니다.
- 디바이스에서 Windows 10 버전 1607 이상을 실행해야 합니다.
- Intune 관리 확장 에이전트는 PowerShell 스크립트 또는 Win32 앱이 사용자 또는 디바이스 보안 그룹에 배포될 때 설치됩니다.

## <a name="create-a-script-policy"></a>스크립트 정책 만들기 

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 > **Intune**을 기준으로 필터링하고 > **Intune**을 선택합니다.
2. **디바이스 구성** > **PowerShell 스크립트** > **추가**를 차례로 선택합니다.
3. 다음 속성을 입력합니다.
    - **이름**: PowerShell 스크립트의 이름을 입력합니다. 
    - **설명**: PowerShell 스크립트의 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다. 
    - **스크립트 위치**: PowerShell 스크립트를 찾습니다. 스크립트는 200KB(ASCII) 미만이어야 합니다.
4. **구성**를 선택하고, 다음 속성을 입력합니다.
    - **로그온된 자격 증명을 사용하여 이 스크립트 실행**: 디바이스에서 사용자의 자격 증명으로 스크립트를 실행하려면 **예**를 선택합니다. 시스템 컨텍스트에서 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다. 많은 관리자들이 **예**를 선택합니다. 스크립트를 시스템 컨텍스트에서 실행해야 하는 경우 **아니요**를 선택합니다.
    - **스크립트 서명 확인 적용**: 신뢰할 수 있는 게시자가 스크립트를 서명해야 하면 **예**를 선택합니다. 스크립트 서명에 대한 요구 사항이 없으면 **아니요**(기본값)를 선택합니다. 
    - **64비트 PowerShell 호스트에서 스크립트 실행**: 64비트 클라이언트 아키텍처의 64비트 PS(PowerShell) 호스트에서 스크립트를 실행하려면 **예**를 선택합니다. 32비트 PowerShell 호스트에서 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다.

      **예** 또는 **아니요**로 설정할 때 신규 및 기존 정책 동작에 대한 다음 표를 사용하세요.

      | 64비트 PS 호스트에서 스크립트 실행 | 클라이언트 아키텍처 | 새 PS 스크립트 | 기존 정책 PS 스크립트 |
      | --- | --- | --- | --- | 
      | 아니요 | 32비트  | 32비트 PS 호스트 지원 | 32비트 PS 호스트에서만 실행되며, 이 호스트는 32비트 및 64비트 아키텍처에서 작동합니다. |
      | 예 | 64비트 | 64비트 아키텍처용 64비트 PS 호스트에서 스크립트를 실행합니다. 32비트에서 실행하면 스크립트가 32비트 PS 호스트에서 실행됩니다. | 32비트 PS 호스트에서 스크립트를 실행합니다. 이 설정을 64비트로 변경하면 스크립트가 (실행되지 않고) 64비트 PS 호스트에서 열리고 결과를 보고합니다. 32비트에서 실행하면 스크립트가 32비트 PS 호스트에서 실행됩니다. |

    ![Microsoft Intune에서 PowerShell 스크립트 추가 및 사용](./media/mgmt-extension-add-script.png)
5. **확인** > **만들기**를 선택하여 스크립트를 저장합니다.

> [!NOTE]
> 스크립트가 사용자 컨텍스트로 설정되고 디바이스의 최종 사용자에게 관리자 권한이 있는 경우 기본적으로 PowerShell 스크립트는 관리자 권한으로 실행됩니다.

## <a name="assign-the-policy"></a>정책 할당

1. **PowerShell 스크립트**에서 할당할 스크립트를 선택한 다음, **관리** > **할당**을 차례로 선택합니다.

    ![Microsoft Intune에서 PowerShell 스크립트를 디바이스 그룹에 할당 또는 배포](./media/mgmt-extension-assignments.png)

2. **그룹 선택**을 선택하여 사용할 수 있는 Azure AD 그룹을 나열합니다. 
3. 디바이스에서 스크립트를 받는 사용자가 포함된 그룹을 하나 이상 선택합니다. 선택한 그룹에 정책을 할당하도록 **선택**합니다.

> [!NOTE]
> - 최종 사용자는 PowerShell 스크립트를 실행하기 위해 디바이스에 로그인할 필요가 없습니다.
> - Intune의 PowerShell 스크립트는 Azure AD 디바이스 보안 그룹을 대상으로 할 수 있습니다.
> - Intune의 PowerShell 스크립트는 Azure AD 사용자 보안 그룹을 대상으로 할 수 있습니다.

Intune 관리 확장 클라이언트는 1시간마다 그리고 다시 부팅될 때마다 Intune을 검사하여 새로운 스크립트 또는 변경 내용을 확인합니다. Azure AD 그룹에 정책이 지정되면 PowerShell 스크립트가 실행되고 실행 결과가 보고됩니다. 스크립트는 한 번 실행되면 스크립트 또는 정책이 변경되기 전에는 다시 실행되지 않습니다.

## <a name="monitor-run-status"></a>실행 상태 모니터링

Azure Portal에서 사용자 및 디바이스에 대한 PowerShell 스크립트의 실행 상태를 모니터링할 수 있습니다.

**PowerShell 스크립트**에서 모니터링할 스크립트를 선택하고, **모니터**를 선택한 다음, 다음 보고서 중 하나를 선택합니다.

- **디바이스 상태**
- **사용자 상태**

## <a name="troubleshoot-scripts"></a>스크립트 문제 해결

클라이언트 컴퓨터의 에이전트 로그는 일반적으로 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`에 있습니다. [CMTrace.exe](https://docs.microsoft.com/sccm/core/support/tools)를 사용하여 이러한 로그 파일을 볼 수 있습니다. 

![Microsoft Intune의 스크린샷 또는 샘플 cmtrace 에이전트 로그](./media/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>스크립트 삭제

**PowerShell 스크립트**에서 스크립트를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.

## <a name="common-issues-and-resolutions"></a>일반적인 문제 및 해결 방법

PowerShell 스크립트는 로그인할 때마다 실행되지는 않습니다. 다시 부팅 후에만 실행되거나 **Microsoft Intune 관리 확장** 서비스가 다시 시작되는 경우에만 실행됩니다. Intune 관리 확장 클라이언트는 Intune에서 스크립트 또는 정책 변경 내용을 1시간에 한 번 확인합니다.

#### <a name="issue-intune-management-extension-doesnt-download"></a>문제점: Intune 관리 확장이 다운로드되지 않음

**가능한 해결 방법**:

- 디바이스가 Azure AD에 자동으로 등록되었는지 확인합니다. 확인하려면 디바이스에서 다음을 수행합니다. 

  1. **설정** > **계정** > **회사 또는 학교 액세스**로 이동합니다.
  2. 연결된 계정 > **정보**를 선택합니다.
  3. **고급 진단 보고서** 아래에서 **보고서 만들기**를 선택합니다.
  4. 웹 브라우저에서 `MDMDiagReport`를 열고 **등록된 구성 소스** 섹션으로 이동합니다.
  5. **MDMDeviceWithAAD** 속성을 검색합니다. 이 속성이 없으면 디바이스가 자동 등록되지 않습니다.

    [Windows 10 자동 등록 사용](windows-enroll.md#enable-windows-10-automatic-enrollment)에 단계가 포함되어 있습니다.

#### <a name="issue-powershell-scripts-do-not-run"></a>문제점: PowerShell 스크립트가 실행되지 않음

**가능한 해결 방법**:

- Intune 관리 확장이 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`에 다운로드되었는지 확인합니다.
- 스크립트는 Surface Hub에 실행되지 않습니다.
- `\ProgramData\Microsoft\IntuneManagementExtension\Logs`의 로그에서 오류가 있는지 확인합니다.
- 가능한 권한 문제의 경우 PowerShell 스크립트의 속성이 `Run this script using the logged on credentials`로 설정되었는지 확인합니다. 또한 로그인한 사용자에게 스크립트를 실행할 적절한 권한이 있는지 확인합니다.
- 스크립팅 문제점을 격리하려면 샘플 스크립트를 실행합니다. 예를 들어 `C:\Scripts` 디렉터리를 만들고 모든 사용자에게 모든 권한을 제공합니다. 다음 스크립트를 실행합니다.

  ```powershell
  write-output "Script worked" | out-file c:\Scripts\output.txt
  ```

  성공하면 output.txt가 만들어지고 “Script worked” 텍스트가 포함됩니다.

- Intune 없이 스크립트 실행을 테스트하려면 로컬로 [psexec 도구](https://docs.microsoft.com/sysinternals/downloads/psexec)를 사용하여 시스템 컨텍스트에서 스크립트를 실행합니다.

  `psexec -i -s`

## <a name="next-steps"></a>다음 단계

프로필을 [모니터링](device-profile-monitor.md)하고 [문제를 해결](device-profile-troubleshoot.md)합니다.
