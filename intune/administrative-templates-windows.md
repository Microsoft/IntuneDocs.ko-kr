---
title: Microsoft Intune에서 Windows 10 디바이스에 대한 템플릿 사용 - Azure | Microsoft Docs
description: Microsoft Intune에서 관리 템플릿을 사용하여 Windows 10 디바이스에 대한 설정 그룹을 만듭니다. 디바이스 구성 프로필에서 이러한 설정을 사용하여 Office 프로그램을 제어하고, Internet Explorer의 기능을 보호하고, OneDrive에 대한 액세스를 제어하고, 원격 데스크톱 기능을 사용하고, 자동 재생을 사용하도록 설정하고, 전원 관리 설정을 설정하고, HTTP 인쇄를 사용하고, 다른 사용자 로그온 옵션을 사용하고, 이벤트 로그 크기를 제어합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: d0426b63cb4601a73451ec9509ddea8e39271c29
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54204975"
---
# <a name="windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Microsoft Intune에서 그룹 정책 설정을 구성하는 Windows 10 템플릿

조직에서 디바이스를 관리하는 경우 다른 디바이스 그룹에 적용되는 설정 그룹을 만들려고 합니다. 예를 들어 여러 디바이스 그룹이 있습니다. GroupA의 경우 특정 설정 세트를 할당하려고 합니다. GroupB의 경우 다른 설정 세트를 할당하려고 합니다. 또한 구성할 수 있는 설정의 간단한 보기를 원합니다.

Microsoft Intune에서 **관리 템플릿**을 사용하여 이 작업을 완료할 수 있습니다. 관리 템플릿은 Internet Explorer, Microsoft Office 프로그램, 원격 데스크톱의 기능, OneDrive에 대한 액세스를 제어하고, 그림 암호 또는 PIN을 사용하여 로그인하는 등 수백 가지 설정을 포함합니다. 이러한 템플릿은 AD(Active Directory)의 GPO(그룹 정책) 설정과 유사하며, XML을 사용하는 [ADMX 백업 설정](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)입니다. 하지만 Intune의 템플릿은 100% 클라우드 기반입니다. 설정을 구성하고, 원하는 설정을 찾는 더욱 단순하고 간단한 방법을 제공합니다.

**관리 템플릿**은 Intune에 기본 제공되고, OMA-URI 사용을 포함한 사용자 지정이 필요하지 않습니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 원스톱 상점으로 이러한 템플릿 설정을 사용하여 Windows 10 디바이스를 관리합니다.

이 문서에서는 Windows 10 디바이스에 대한 템플릿을 만드는 단계를 나열하고, Microsoft Intune에서 사용 가능한 모든 설정을 필터링하는 방법을 보여줍니다. 템플릿을 만들 때 디바이스 구성 프로필을 만듭니다. 그런 다음, 조직의 Windows 10 디바이스에 이 프로필을 할당하거나 배포할 수 있습니다.

> [!NOTE]
> 독립 실행형 디바이스에 대한 관리 템플릿이 지원됩니다. 현재 SCCM(System Center Configuration Manager) 공동 관리 디바이스에 대해 지원되지 않습니다.

## <a name="create-a-template"></a>템플릿 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 > **Intune**을 기준으로 필터링하고 > **Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 프로필의 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **관리 템플릿(미리 보기)** 을 선택합니다.

4. **만들기**를 선택합니다. 새 창에서 **설정**을 선택합니다. 모든 설정이 나열되고, 화살표 앞과 뒤를 사용하여 자세한 설정을 볼 수 있습니다.

    ![설정의 샘플 목록을 보고 이전 및 다음 단추를 사용합니다.](./media/administrative-templates-windows/sample-settings-list-next-page.png)

5. 설정을 선택합니다. 예를 들어 **파일 다운로드 허용**을 선택합니다. 설정에 대한 자세한 설명이 표시됩니다. **사용**, **사용 안 함**을 선택하거나 **구성되지 않음**(기본값)으로 설정을 그대로 둡니다. 자세한 설명은 **사용**, **사용 안 함** 또는 **구성되지 않음**을 선택하는 경우 발생하는 작업을 설명합니다.
6. **확인**을 선택하여 변경 내용을 저장합니다.

설정의 목록을 계속해서 진행하고, 사용자 환경에서 원하는 설정을 구성합니다. 몇 가지 예제는 다음과 같습니다.

- **VBA 매크로 알림 설정** 설정을 사용하여 Word 및 Excel 등의 다른 Microsoft Office 프로그램에서 VBA 매크로를 처리합니다.
- **파일 다운로드 허용** 설정을 사용하여 Internet Explorer에서 다운로드를 허용하거나 금지합니다.
- **컴퓨터에서 절전 모드가 해제될 때(연결) 암호 필요** 설정을 사용하여 디바이스가 절전 모드에서 해제되는 경우 사용자에게 암호를 요청합니다.
- **서명되지 않은 ActiveX 컨트롤 다운로드** 설정을 사용하여 사용자가 Internet Explorer에서 서명되지 않은 ActiveX 컨트롤을 다운로드하는 것을 차단합니다.
- **시스템 복원 해제** 설정을 사용하여 사용자가 디바이스에서 시스템 복원을 실행하는 것을 차단합니다.
- 이외에 많은 기능이 있습니다.

## <a name="find-some-settings"></a>일부 설정 찾기

이러한 템플릿에서 사용할 수 있는 수백 가지 설정이 있습니다. 특정 설정을 쉽게 찾으려면 기본 제공 기능을 사용합니다.

- 템플릿에서 **설정**, **상태** 또는 **경로** 열을 선택하여 목록을 정렬합니다. 예를 들어 **경로** 열을 선택하여 `Microsoft Excel` 경로의 모든 설정을 봅니다.

  ![경로를 클릭하여 사전순으로 정렬](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- 템플릿에서 **검색** 상자를 사용하여 특정 설정을 찾습니다. 예를 들어 `copy`을 검색합니다. `copy`와 함께 모든 설정이 표시됩니다.

  ![경로를 클릭하여 사전순으로 정렬](./media/administrative-templates-windows/search-copy-settings.png)

  다른 예제에서 `microsoft word`를 검색합니다. Microsoft Word 프로그램에 대해 설정할 수 있는 모든 설정이 표시됩니다. `explorer`를 검색하여 템플릿에 추가할 수 있는 모든 Internet Explorer 설정을 봅니다.

## <a name="next-steps"></a>다음 단계

템플릿이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로 [프로필이라고도 하는 템플릿을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.
