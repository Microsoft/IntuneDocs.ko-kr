---
title: Microsoft Intune에서 Windows 10 디바이스에 PowerShell 스크립트 추가 - Azure | Microsoft Docs
description: PowerShell 스크립트를 만들고 실행하고, Azure Active Directory 그룹에 스크립트 정책을 할당하고, 보고서를 사용하여 스크립트를 모니터링하고, Microsoft Intune에서 Windows 10 디바이스에 추가한 스크립트를 삭제하는 단계를 살펴보세요. 또한 몇 가지 일반적인 문제 및 해결 방법을 참조하세요.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/26/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 768b6f08-3eff-4551-b139-095b3cfd1f89
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8af7a756d95051be52a5380467cb4f9be2533b3
ms.sourcegitcommit: fab685b22a010fe231b27a0c5eda34a6f22f4c8d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2020
ms.locfileid: "78216192"
---
# <a name="use-powershell-scripts-on-windows-10-devices-in-intune"></a>Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용

Intune에서 Microsoft Intune 관리 확장을 사용하여 Windows 10 디바이스에서 실행되는 PowerShell 스크립트를 업로드합니다. 관리 확장은 Windows 10 MDM(모바일 디바이스 관리)을 개선하며 사용자가 최신 관리로 더 손쉽게 이행할 수 있도록 합니다.

이 기능은 다음에 적용됩니다.

- Windows 10 이상

## <a name="move-to-modern-management"></a>최신 관리 기능으로 전환

최종 사용자 컴퓨팅은 디지털 변형을 거치는 중입니다. 기존의 클래식 IT는 단일 디바이스 플랫폼, 회사 소유 디바이스, 사무실에서 일하는 사용자, 여러 가지 사후 수동 IT 프로세스에 집중합니다. 최신 작업 공간에서는 사용자와 회사가 소유한 여러 플랫폼을 사용하고, 사용자가 장소에 구애받지 않고 일할 수 있으며, 자동화된 능동적 IT 프로세스를 제공합니다.

Microsoft Intune과 같은 MDM 서비스는 Windows 10을 실행하는 모바일 및 데스크톱 디바이스를 관리할 수 있습니다. 기본 제공 Windows 10 관리 클라이언트는 Intune과 통신하여 엔터프라이즈 관리 작업을 실행합니다. 고급 디바이스 구성, 문제 해결과 같은 일부 작업이 필요할 수도 있습니다. Win32 앱 관리의 경우, Windows 10 디바이스에서 [Win32 앱 관리](app-management.md) 기능을 사용할 수 있습니다.

Intune 관리 확장은 기본 제공 Windows 10 MDM 기능을 보완합니다. Windows 10 디바이스에서 실행할 PowerShell 스크립트를 만들 수 있습니다. 예를 들어 고급 디바이스 구성을 수행하는 PowerShell 스크립트를 만듭니다. 그리고 스크립트를 Intune에 업로드하고 Azure AD(Active Directory) 그룹에 스크립트를 할당하고 스크립트를 실행합니다. 그런 다음, 시작부터 완료까지 스크립트의 실행 상태를 모니터링할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

Intune 관리 확장에는 다음과 같은 필수 구성 요소가 있습니다. 필수 조건이 충족되면, Intune 관리 확장은 PowerShell 스크립트 또는 Win32 앱이 사용자 또는 디바이스에 할당될 때 자동으로 설치됩니다.

- Windows 10 버전 1607 이상을 실행하는 디바이스. 디바이스가 [대량 자동 등록](../enrollment/windows-bulk-enroll.md)을 통해 등록된 경우 디바이스는 Windows 10 버전 1703 이상을 실행해야 합니다. Intune 관리 확장은 S 모드의 Windows 10에서 지원되지 않습니다. S 모드는 스토어 이외의 앱 실행을 허용하지 않기 때문입니다. 
  
- Azure AD(Active Directory)에 조인한 디바이스는 다음을 포함합니다.  
  
  - 하이브리드 Azure AD 조인: 디바이스는 Azure AD(Active Directory)에 조인되어 있고 온-프레미스 AD(Active Directory)에도 조인되어 있습니다. 지침은 [하이브리드 Azure Active Directory 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)을 참조하세요.

- Intune에 등록된 디바이스는 다음을 포함합니다.

  - 그룹 정책(GPO)에 등록된 디바이스. 지침은 [그룹 정책을 사용하여 Windows 10 디바이스 자동 등록](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)을 참조하세요.
  
  - Intune에 수동으로 디바이스를 등록하는 경우:
  
    - Azure AD에서 [Intune에 자동 등록](../enrollment/quickstart-setup-auto-enrollment.md)을 사용하도록 설정했습니다. 최종 사용자는 로컬 사용자 계정을 사용하여 디바이스에 로그인하고 디바이스를 Azure AD에 수동으로 조인한 다음 Azure AD 계정을 사용하여 디바이스에 로그인합니다.
    
    또는  
    
    - 사용자는 Azure AD 계정을 사용하여 디바이스에 로그인한 다음, Intune에 등록합니다.

  - Configuration Manager 및 Intune을 사용하는 공동 관리 디바이스. **앱** 워크로드가 **파일럿 Intune** 또는 **Intune**으로 설정되어 있어야 합니다. 지침은 다음 문서를 참조하세요. 
  
    - [What is co-management](https://docs.microsoft.com/configmgr/comanage/overview)(공동 관리란?) 
    - [클라이언트 앱 워크로드](https://docs.microsoft.com/configmgr/comanage/workloads#client-apps)
    - [Configuration Manager 워크로드를 Intune으로 전환하는 방법](https://docs.microsoft.com/configmgr/comanage/how-to-switch-workloads)
  
> [!TIP]
> 디바이스가 Azure AD에 [조인](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)되어 있어야 합니다. Azure AD에 [등록](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)만 되어 있는 디바이스는 스크립트를 받지 않습니다.

## <a name="create-a-script-policy-and-assign-it"></a>스크립트 정책 만들기 및 할당

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **PowerShell 스크립트** > **추가**를 선택합니다.

    ![Microsoft Intune에서 PowerShell 스크립트 추가 및 사용](./media/intune-management-extension/mgmt-extension-add-script.png)

3. **기본**에서 다음 속성을 입력하고 **다음**을 선택합니다.
    - **이름**: PowerShell 스크립트의 이름을 입력합니다. 
    - **설명**: PowerShell 스크립트의 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
4. **스크립트 설정**에 다음 속성을 입력하고 **다음**을 선택합니다.
    - **스크립트 위치**: PowerShell 스크립트를 찾습니다. 스크립트는 200KB(ASCII) 미만이어야 합니다.
    - **로그온된 자격 증명을 사용하여 이 스크립트 실행**: 디바이스에서 사용자의 자격 증명으로 스크립트를 실행하려면 **예**를 선택합니다. 시스템 컨텍스트에서 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다. 많은 관리자들이 **예**를 선택합니다. 스크립트를 시스템 컨텍스트에서 실행해야 하는 경우 **아니요**를 선택합니다.
    - **스크립트 서명 확인 적용**: 신뢰할 수 있는 게시자가 스크립트를 서명해야 하면 **예**를 선택합니다. 스크립트 서명에 대한 요구 사항이 없으면 **아니요**(기본값)를 선택합니다. 
    - **64비트 PowerShell 호스트에서 스크립트 실행**: 64비트 클라이언트 아키텍처의 64비트 PS(PowerShell) 호스트에서 스크립트를 실행하려면 **예**를 선택합니다. 32비트 PowerShell 호스트에서 스크립트를 실행하려면 **아니요**(기본값)를 선택합니다.

      **예** 또는 **아니요**로 설정할 때 신규 및 기존 정책 동작에 대한 다음 표를 사용하세요.

      | 64비트 PS 호스트에서 스크립트 실행 | 클라이언트 아키텍처 | 새 PS 스크립트 | 기존 정책 PS 스크립트 |
      | --- | --- | --- | --- | 
      | 아니요 | 32비트  | 32비트 PS 호스트 지원 | 32비트 PS 호스트에서만 실행되며, 이 호스트는 32비트 및 64비트 아키텍처에서 작동합니다. |
      | 예 | 64비트 | 64비트 아키텍처용 64비트 PS 호스트에서 스크립트를 실행합니다. 32비트에서 실행하면 스크립트가 32비트 PS 호스트에서 실행됩니다. | 32비트 PS 호스트에서 스크립트를 실행합니다. 이 설정을 64비트로 변경하면 스크립트가 (실행되지 않고) 64비트 PS 호스트에서 열리고 결과를 보고합니다. 32비트에서 실행하면 스크립트가 32비트 PS 호스트에서 실행됩니다. |

5. **범위 태그**를 선택합니다. 범위 태그는 선택 사항입니다. 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

    범위 태그를 추가하려면:

    1. **범위 태그 선택** > 목록에서 기존 범위 태그 선택 > **선택**을 선택합니다.

    2. 완료되면 **다음**을 선택합니다.

6. **할당** > **포함할 그룹 선택**을 선택합니다. 기존 Azure AD 그룹 목록이 표시됩니다.

    1. 디바이스에서 스크립트를 받는 사용자가 포함된 그룹을 하나 이상 선택합니다. **선택**을 선택합니다. 선택한 그룹은 목록에 표시되고 정책을 받습니다.

        > [!NOTE]
        > Intune의 PowerShell 스크립트는 Azure AD 디바이스 보안 그룹 또는 Azure AD 사용자 보안 그룹을 대상으로 할 수 있습니다.

    2. **다음**을 선택합니다.

        ![Microsoft Intune에서 PowerShell 스크립트를 디바이스 그룹에 할당 또는 배포](./media/intune-management-extension/mgmt-extension-assignments.png)

7. **검토 + 추가**에 구성한 설정의 요약이 표시됩니다. **추가**를 선택하여 스크립트를 저장합니다. **추가**를 선택하면 선택한 그룹에 정책이 배포됩니다.

## <a name="important-considerations"></a>중요한 고려 사항

- 스크립트가 사용자 컨텍스트로 설정되어 있고 최종 사용자에게 관리자 권한이 있으면 기본적으로 PowerShell 스크립트가 관리자 권한으로 실행됩니다.

- 최종 사용자는 PowerShell 스크립트를 실행하기 위해 디바이스에 로그인할 필요가 없습니다.

- Intune 관리 확장 클라이언트는 1시간마다 한 번씩 새로운 스크립트나 변경 사항을 Intune에서 확인합니다. Azure AD 그룹에 정책이 지정되면 PowerShell 스크립트가 실행되고 실행 결과가 보고됩니다. 스크립트는 한 번 실행되면 스크립트 또는 정책이 변경되기 전에는 다시 실행되지 않습니다.

## <a name="monitor-run-status"></a>실행 상태 모니터링

Azure Portal에서 사용자 및 디바이스에 대한 PowerShell 스크립트의 실행 상태를 모니터링할 수 있습니다.

**PowerShell 스크립트**에서 모니터링할 스크립트를 선택하고, **모니터**를 선택한 다음, 다음 보고서 중 하나를 선택합니다.

- **디바이스 상태**
- **사용자 상태**

## <a name="intune-management-extension-logs"></a>Intune 관리 확장 로그

클라이언트 컴퓨터의 에이전트 로그는 일반적으로 `\ProgramData\Microsoft\IntuneManagementExtension\Logs`에 있습니다. [CMTrace.exe](https://docs.microsoft.com/configmgr/core/support/cmtrace)를 사용하여 이러한 로그 파일을 볼 수 있습니다.

![Microsoft Intune의 스크린샷 또는 샘플 cmtrace 에이전트 로그](./media/apps-win32-app-management/apps-win32-app-10.png)  

## <a name="delete-a-script"></a>스크립트 삭제

**PowerShell 스크립트**에서 스크립트를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.

## <a name="common-issues-and-resolutions"></a>일반적인 문제 및 해결 방법

### <a name="issue-intune-management-extension-doesnt-download"></a>문제: Intune 관리 확장이 다운로드되지 않음

**가능한 해결 방법**:

- 디바이스가 Azure AD에 조인되어 있지 않습니다. 디바이스가 [필수 구성 요소](#prerequisites)(이 문서의)를 충족하는지 확인하세요. 
- 사용자 또는 디바이스가 속한 그룹에 할당된 PowerShell 스크립트나 Win32 앱이 없습니다.
- 인터넷 액세스 권한 없음, Windows Push Notification Services(WNS)에 대한 액세스 권항 없음 등으로 인해 디바이스가 Intune 서비스에 체크 인할 수 없습니다.
- 디바이스가 S 모드에 있습니다. S 모드에서 실행 중인 디바이스에서는 Intune 관리 확장이 지원되지 않습니다. 

디바이스가 자동 등록되었는지 확인하려면 다음을 수행합니다.

  1. **설정** > **계정** > **회사 또는 학교 액세스**로 이동합니다.
  2. 연결된 계정 > **정보**를 선택합니다.
  3. **고급 진단 보고서** 아래에서 **보고서 만들기**를 선택합니다.
  4. 웹 브라우저에서 `MDMDiagReport`를 엽니다.
  5. **MDMDeviceWithAAD** 속성을 검색합니다. 속성이 있으면 디바이스가 자동 등록됩니다. 이 속성이 없으면 디바이스가 자동 등록되지 않습니다.

[Windows 10 자동 등록 사용](../enrollment/windows-enroll.md#enable-windows-10-automatic-enrollment)에는 Intune에서 자동 등록을 구성하는 단계가 포함됩니다.

### <a name="issue-powershell-scripts-do-not-run"></a>문제: PowerShell 스크립트가 실행되지 않음

**가능한 해결 방법**:

- PowerShell 스크립트는 로그인할 때마다 실행되지는 않습니다. 실행:

  - 스크립트가 디바이스에 할당된 경우
  - 스크립트를 변경하는 경우 업로드하고 스크립트를 사용자 또는 디바이스에 할당
  
    > [!TIP]
    > **Microsoft Intune 관리 확장**은 서비스 앱(services.msc)에 나열된 다른 서비스와 마찬가지로 디바이스에서 실행되는 서비스입니다. 디바이스를 다시 부팅한 후 이 서비스를 다시 시작하고 Intune 서비스를 사용하여 할당된 PowerShell 스크립트를 확인할 수도 있습니다. **Microsoft Intune 관리 확장** 서비스가 수동으로 설정된 경우 디바이스를 다시 부팅한 후 서비스가 다시 시작되지 않을 수 있습니다.

- 디바이스가 [Azure AD에 조인](https://docs.microsoft.com/azure/active-directory/user-help/user-help-join-device-on-network)되어 있어야 합니다. 작업 공간 또는 조직에만 조인된(Azure AD에 [등록된](https://docs.microsoft.com/azure/active-directory/user-help/user-help-register-device-on-network)) 디바이스는 스크립트를 받지 않습니다.
- Intune 관리 확장 클라이언트는 Intune에서 스크립트 또는 정책 변경 내용을 시간당 한 번씩 확인합니다.
- Intune 관리 확장이 `%ProgramFiles(x86)%\Microsoft Intune Management Extension`에 다운로드되었는지 확인합니다.
- 스크립트는 Surface Hubs 또는 S 모드의 Windows 10에서 실행되지 않습니다.
- 로그에 오류가 있는지 검토합니다. 이 문서 내의 [Intune 관리 확장 로그](#intune-management-extension-logs)를 참조하세요.
- 가능한 권한 문제의 경우 PowerShell 스크립트의 속성이 `Run this script using the logged on credentials`로 설정되었는지 확인합니다. 또한 로그인한 사용자에게 스크립트를 실행할 적절한 권한이 있는지 확인합니다.

- 스크립팅 문제를 격리하는 방법은 다음과 같습니다.

  - 디바이스에서 PowerShell 실행 구성을 검토합니다. 지침은 [PowerShell 실행 정책](https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-executionpolicy?view=powershell-6)을 참조하세요.
  - Intune 관리 확장을 사용하여 샘플 스크립트를 실행합니다. 예를 들어 `C:\Scripts` 디렉터리를 만들고 모든 사용자에게 모든 권한을 제공합니다. 다음 스크립트를 실행합니다.

    ```powershell
    write-output "Script worked" | out-file c:\Scripts\output.txt
    ```

    성공하면 output.txt가 만들어지고 “Script worked” 텍스트가 포함됩니다.

  - Intune 없이 스크립트 실행을 테스트하려면 로컬로 [psexec 도구](https://docs.microsoft.com/sysinternals/downloads/psexec)를 사용하여 시스템 계정에서 스크립트를 실행합니다.

    `psexec -i -s`  
    
  - 스크립트가 성공했다고 보고하지만 실제로는 실패했다면, 바이러스 백신 서비스가 AgentExecutor를 샌드박스 처리하고 있을지도 모릅니다. 다음 스크립트는 Intune에서 항상 실패를 보고합니다. 테스트를 위해 이 스트립트를 사용하세요.
  
    ```powershell
    Write-Error -Message "Forced Fail" -Category OperationStopped
    mkdir "c:\temp" 
    echo "Forced Fail" | out-file c:\temp\Fail.txt
    ```

    스크립트에서 성공했다고 보고한다면 `AgentExecutor.log`를 참조해 오류 출력을 확인하세요. 스크립트가 실행된다면 길이는 2보다 커야 합니다.

  - .error 및 .output 파일을 캡처하려면 다음 코드 조각이 스크립트를 AgentExecutor를 통해 PSx86(`C:\Windows\SysWOW64\WindowsPowerShell\v1.0`)으로 실행해야 합니다. 이렇게 해야 로그가 유지되어 검토할 수 있게 됩니다. Intune 관리 확장은 스크립트가 실행되면 로그를 삭제한다는 점에 유의하세요.
  
    ```powershell
    $scriptPath = read-host "Enter the path to the script file to execute"
    $logFolder = read-host "Enter the path to a folder to output the logs to"
    $outputPath = $logFolder+"\output.output"
    $errorPath =  $logFolder+"\error.error"
    $timeoutPath =  $logFolder+"\timeout.timeout"
    $timeoutVal = 60000 
    $PSFolder = "C:\Windows\SysWOW64\WindowsPowerShell\v1.0"
    $AgentExec = "C:\Program Files (x86)\Microsoft Intune Management Extension\agentexecutor.exe"
    &$AgentExec -powershell  $scriptPath $outputPath $errorPath $timeoutPath $timeoutVal $PSFolder 0 0
    ```

## <a name="next-steps"></a>다음 단계

프로필을 [모니터링](../device-profile-monitor.md)하고 [문제를 해결](../device-profile-troubleshoot.md)합니다.
