---
title: Microsoft Intune에서 클라이언트 소프트웨어로 PC 관리 - Azure | Microsoft Docs
description: Intune 클라이언트 소프트웨어를 설치하여 Windows PC를 관리합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.assetid: 3b8d22fe-c318-4796-b760-44f1ccf34312
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb9fb439bd0bc59ae2c69ec966587d58c8c97bf4
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72510108"
---
# <a name="manage-windows-pcs-as-computers-via-intune-software-client"></a>Intune 소프트웨어 클라이언트를 통해 Windows PC를 컴퓨터로 관리

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!WARNING]
> Microsoft는 [2020년 1월 14일부로 Windows 7 지원을 종료한다](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020)고 발표했습니다. 이 날짜에 Intune도 Windows 7을 실행하는 디바이스에 대한 지원을 만료합니다. 모든 서비스 또는 지원 중단을 방지하려면 Windows 10으로 이동하는 것이 가장 좋습니다.
> 
> 자세한 내용은 [Intune의 변경 계획: Windows 7 지원 종료](../fundamentals/whats-new.md#intune-plan-for-change-nearing-end-of-support-for-windows-7-)를 참조 하세요.

> [!NOTE]
> Microsoft Intune을 사용하여 Windows PC를 [MDM(모바일 디바이스 관리)가 있는 모바일 디바이스](../enrollment/windows-enroll.md)로 관리하거나, 아래 설명된 대로 Intune 소프트웨어 클라이언트가 있는 컴퓨터로 관리할 수 있습니다. 그러나 고객은 가능한 한 [MDM 관리 솔루션을 사용](../enrollment/windows-enroll.md)하는 것이 좋습니다. 자세한 내용은 [Windows PC를 컴퓨터로 관리하는 방식과 모바일 디바이스로 관리하는 방식 비교](pc-management-comparison.md)를 참조하세요. 

Intune은 조직에서 모바일 디바이스를 관리할 수 있는 포괄적 솔루션을 제공합니다. Intune에서는 Windows 10 운영 체제에 기본 제공된 최신 디바이스 관리 기능을 사용하여 Windows PC를 모바일 디바이스로 관리할 수 있습니다. 조직의 관리 요구 사항을 충족하기 위해 Intune에서는 Intune 소프트웨어 클라이언트를 사용하여 Windows PC를 컴퓨터로 관리할 수도 있습니다. 이 관리 방법에는 레거시 Windows 운영 체제의 기존 컴퓨터 관리 기능이 사용됩니다.

Intune 소프트웨어 클라이언트는 모바일 디바이스로 관리할 수 없는 Windows 7 등의 레거시 운영 체제를 실행하는 Windows PC에 가장 적합합니다. Intune 소프트웨어 클라이언트에는 클라우드에서 PC를 관리하기 위한 그룹 정책 같은 관리 기능이 사용됩니다.

Intune에서는 소프트웨어 클라이언트를 사용하여 최대 7,000대의 Windows PC를 컴퓨터로 관리하도록 지원합니다. 대규모 배포의 경우 Windows 10 PC를 모바일 디바이스로 관리합니다. Intune의 각 릴리스 및 Windows 10의 업데이트에는 모바일 디바이스 관리 아키텍처에 따른 관리 기능이 포함됩니다. 조직을 모바일 디바이스로 관리되는 Windows 10으로 이동하는 것이 좋습니다.

> [!NOTE]
> Windows 8.1 이상 디바이스는 Intune 클라이언트 소프트웨어를 사용하여 PC로 관리하거나 모바일 디바이스로 관리할 수 있습니다. 두 가지 방법을 같은 디바이스에서 사용할 수는 없습니다. Intune 클라이언트 소프트웨어를 사용하여 PC를 관리하도록 결정하기 전에 신중하게 고려하세요. 이 항목은 Intune 클라이언트 소프트웨어를 실행하여 디바이스를 PC로 관리하는 경우에만 적용됩니다.

## <a name="requirements-for-intune-pc-client-management"></a>Intune PC 클라이언트 관리를 위한 요구 사항

**하드웨어**:  
다음은 Intune 클라이언트 소프트웨어를 설치하기 위한 최소 하드웨어 요구 사항입니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|Network (네트워크)|클라이언트를 설치하려면 PC가 인터넷에 연결되어 있어야 합니다.|
|프로세서 및 메모리|PC 운영 체제의 프로세서 및 RAM 요구 사항을 참조하세요.|
|디스크 공간|클라이언트 소프트웨어를 설치하려면 먼저 200MB의 사용 가능한 디스크 공간이 필요합니다.|

**소프트웨어**:  
다음은 클라이언트 소프트웨어를 설치하기 위한 소프트웨어 요구 사항입니다.

|요구 사항|추가 정보|
|---------------|--------------------|
|운영 체제 | Windows 7 SP1 및 Windows 8.1 이상을 실행하는 Windows 디바이스 </br></br>**Home Edition 버전은 지원되지 않습니다.**|
|관리자 권한|클라이언트 소프트웨어를 설치하는 계정에는 해당 디바이스에 대한 로컬 관리자 권한이 있어야 합니다.|
|Windows Installer 3.1|PC에 최소 Windows Installer 3.1이 설치되어 있어야 합니다.<br /><br />PC의 Windows Installer 버전을 확인하려면<br /><br />  PC에서 **%windir%\System32\msiexec.exe**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.<br /><br />Windows Installer의 최신 버전은 Microsoft Developer Network 웹 사이트의 [Windows Installer Redistributables(Windows Installer 재배포 가능 구성 요소)](http://go.microsoft.com/fwlink/?LinkID=234258) 에서 다운로드할 수 있습니다.|
|호환되지 않는 클라이언트 소프트웨어를 제거합니다.|Intune 클라이언트 소프트웨어를 설치하기 전에 해당 PC에서 Configuration Manager, Operations Manager 및 Service Manager 클라이언트 소프트웨어를 모두 제거하세요.|

## <a name="deploying-the-intune-software-client"></a>Intune 소프트웨어 클라이언트 배포
Intune 관리자는 Intune 소프트웨어 클라이언트를 다양한 방법으로 사용자에게 제공할 수 있습니다. 자세한 내용은 [Windows PC에 Intune 소프트웨어 클라이언트 설치](../install-the-windows-pc-client-with-microsoft-intune.md)를 참조하세요.

## <a name="computer-management-capabilities-with-the-intune-client-software"></a>Intune 클라이언트 소프트웨어의 컴퓨터 관리 기능
대부분의 시나리오에서 Microsoft Intune에 디바이스를 등록하면 훨씬 더 많은 기능이 제공됩니다. 그러나 Intune 소프트웨어 클라이언트를 사용하여 PC를 관리할 수도 있으며, 이 경우 다음과 같은 기능이 제공됩니다.

- **[소프트웨어 업데이트 관리](../keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)** - PC를 최신 상태로 유지하고 업데이트 적용 시기를 결정할 수 있습니다.

- **[Windows 방화벽 정책](../help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune.md)** - 이 정책을 통해 회사에서 사용하는 PC 중에 Windows 방화벽이 비활성화되거나 부적절하게 구성된 PC가 없는지를 확인할 수 있습니다.

- **[맬웨어 방지 보호](../help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)** - Intune에 포함된 Endpoint Protection을 사용하면 PC를 맬웨어로부터 보호할 수 있습니다.

- **[원격 지원](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)** - Intune을 통해 IT 지원 직원에게 문의하면 해당 직원이 Intune에 포함된 원격 데스크톱 기능을 사용하여 도움을 줄 수 있습니다(TeamViewer 소프트웨어 필요).

- **[소프트웨어 라이선스 관리](../manage-license-agreements-for-windows-pc-software-in-microsoft-intune.md)** - 사용 가능한 소프트웨어 라이선스 수와 사용 가능한 라이선스 중 현재 사용 중인 라이선스 수를 추적합니다.
- **[앱 배포](add-apps-for-windows-pcs-in-microsoft-intune.md)** - 관리하는 PC에 소프트웨어를 배포합니다. 소프트웨어 클라이언트를 사용하여 PC를 관리하는 경우 일부 앱 관리 기능은 사용할 수 없습니다.

<!-- - **Compliance settings reporting** -->

## <a name="policies-and-app-deployments-for-the-intune-software-client"></a>Intune 소프트웨어 클라이언트의 정책 및 앱 배포

Intune 클라이언트 소프트웨어는 소프트웨어 업데이트, Windows 방화벽, Endpoint Protection을 관리함으로써 [PC를 보호하는 관리 기능](policies-to-protect-windows-pcs-in-microsoft-intune.md)을 지원하지만, Intune 클라이언트 소프트웨어를 통해 관리되는 PC는 모바일 디바이스 관리 관련 **Windows** 정책 설정을 비롯한 기타 Intune 정책을 사용하여 대상으로 지정할 수 없습니다.

Intune 클라이언트 소프트웨어를 사용하여 Windows PC를 관리하는 경우 **컴퓨터 관리** 섹션에 표시된 정책만 사용할 수 있습니다.

Intune에서는 Windows Server AD DS(Active Directory Domain Services) GPO(그룹 정책 개체)와 비슷한 방법으로 정책을 사용하여 Windows PC를 관리합니다. Intune에서 Active Directory 도메인에 가입된 컴퓨터를 관리하는 경우에는 조직에서 사용되는 [Intune 정책이 다른 GPO와 충돌하지 않는지 확인](resolve-gpo-and-microsoft-intune-policy-conflicts.md)해야 합니다. 자세한 내용은 [그룹 정책 입문](https://technet.microsoft.com/library/hh147307.aspx)을 참조하세요.

  ![새 Windows PC 정책에 대한 템플릿 선택](./media/manage-windows-pcs-with-microsoft-intune/select-template-for-pc-policy.png)

앱을 배포할 때 Windows Installer(.exe, .msi)만 사용할 수 있습니다.

  ![PC 클라이언트 소프트웨어 파일의 플랫폼 및 위치 선택](./media/manage-windows-pcs-with-microsoft-intune/select-platform-of-software-files-for-pc-agent.png)

## <a name="common-tasks-for-windows-pcs"></a>Windows PC의 일반 작업

클라이언트가 설치된 Windows PC에서 Intune 관리자 콘솔을 사용하여 다른 일반적인 컴퓨터 관리 작업을 수행할 수 있습니다.
- [정책을 사용하여 PC 관리 간소화](use-policies-to-simplify-windows-pc-management.md) - Intune의 **컴퓨터 관리** 정책을 설명하고 Microsoft Intune Center에 대한 설정을 나열합니다.

- [Windows PC에 대한 하드웨어 및 소프트웨어 인벤토리 보기](view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune.md) - PC의 하드웨어 기능 및 PC에 설치된 소프트웨어에 대한 정보를 나열하는 보고서를 만드는 방법을 설명합니다. 또한 PC 인벤토리를 새로 고쳐 최신 상태로 유지하는 방법을 설명합니다.
- [Windows PC 사용 중지](retire-a-windows-pc-with-microsoft-intune.md) - Windows PC를 사용 중지하기 위한 단계를 나열하고 PC를 사용 중지할 경우 발생하는 사항을 설명합니다.
- [Windows PC에 대한 사용자-디바이스 연결 관리](../manage-user-device-linking-for-windows-pcs-with-microsoft-intune.md) - 사용자에게 소프트웨어를 배포하기 전에 사용자를 PC에 연결해야 하는 경우 및 방법을 설명합니다.
- [Windows PC 원격 지원 요청 및 제공](request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune.md) - Intune PC 사용자가 원격 지원을 받는 방법을 설명하고 필수 구성 요소 및 TeamViewer 설치를 설명합니다.

위의 작업에 대한 자세한 내용은 [일반적인 컴퓨터 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)을 참조하세요.

## <a name="management-limitations-of-the-intune-client-software"></a>Intune 클라이언트 소프트웨어의 관리 제한 사항

PC를 모바일 디바이스로 관리하는 데 사용할 수 있는 일부 관리 옵션은 Intune 클라이언트 소프트웨어로 관리되는 PC에 사용할 수 없습니다.

- 전체 초기화(선택적 초기화는 사용 가능함)
- 조건부 액세스

또한 Intune 관리 콘솔에서 **업데이트**, **보호** 및 **라이선스**와 같은 특정 섹션은 Intune 클라이언트 소프트웨어를 사용하여 디바이스를 등록한 경우에만 표시됩니다.

  ![PC 클라이언트에 대해서만 표시되는 관리 콘솔 항목](./media/manage-windows-pcs-with-microsoft-intune/admin-console-settings-only-for-pc-agent.png)

## <a name="help-with-troubleshooting"></a>문제 해결 지원

Intune 클라이언트 소프트웨어는 보통 백그라운드에서 자동으로 실행되므로 많은 사용자 상호 작용 또는 문제 해결을 수행할 필요가 없습니다. PC 관리 문제를 해결해야 하는 경우 로그를 확인할 수 있습니다. Intune 클라이언트 소프트웨어 및 해당 로그는 %Program Files%\Microsoft\OnlineManagement 디렉터리에 설치됩니다.

[디바이스 등록](../enrollment/device-enrollment.md)에서 Microsoft Intune을 사용하여 디바이스를 등록하는 방법에 대한 자세한 내용을 검토할 수도 있습니다.
