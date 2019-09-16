---
title: Microsoft Intune에서 Windows 10 디바이스에 대한 템플릿 사용 - Azure | Microsoft Docs
description: Microsoft Intune에서 관리 템플릿을 사용하여 Windows 10 디바이스에 대한 설정 그룹을 만듭니다. 디바이스 구성 프로필에서 이러한 설정을 사용하여 Office 프로그램, Microsoft Edge를 제어하고, Internet Explorer의 기능을 보호하고, OneDrive에 대한 액세스를 제어하고, 원격 데스크톱 기능을 사용하고, 자동 재생을 사용하도록 설정하고, 전원 관리 설정을 설정하고, HTTP 인쇄를 사용하고, 다른 사용자 로그인 옵션을 사용하고, 이벤트 로그 크기를 제어합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c474ac2eccf90e829abe753c82d40bdfae9146ec
ms.sourcegitcommit: 5bb46d3c0bf8c5595132c4200849b1c4bcfe7cdb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70376918"
---
# <a name="use-windows-10-templates-to-configure-group-policy-settings-in-microsoft-intune"></a>Windows 10 템플릿을 사용하여 Microsoft Intune에서 그룹 정책 설정 구성

조직에서 디바이스를 관리하는 경우 다른 디바이스 그룹에 적용되는 설정 그룹을 만들려고 합니다. 예를 들어 여러 디바이스 그룹이 있습니다. GroupA의 경우 특정 설정 세트를 할당하려고 합니다. GroupB의 경우 다른 설정 세트를 할당하려고 합니다. 또한 구성할 수 있는 설정의 간단한 보기를 원합니다.

Microsoft Intune에서 **관리 템플릿**을 사용하여 이 작업을 완료할 수 있습니다. 관리 템플릿은 Microsoft Edge 버전 77 이상, Internet Explorer, Microsoft Office 프로그램, 원격 데스크톱, OneDrive, 암호 및 PIN 등에 대한 기능을 제어하는 수많은 설정을 포함합니다. 이러한 설정을 사용하여 그룹 관리자는 클라우드를 통해 그룹 정책을 관리할 수 있습니다.

Windows 설정은 AD(Active Directory)의 GPO(그룹 정책) 설정과 유사합니다. 이러한 설정은 Windows에 기본적으로 제공되며, XML을 사용하는 [ADMX 지원 설정](https://docs.microsoft.com/windows/client-management/mdm/understanding-admx-backed-policies)입니다. Office 및 Microsoft Edge 설정은 ADMX에서 수집되며, [Office 관리 템플릿 파일](https://www.microsoft.com/download/details.aspx?id=49030) 및 [Microsoft Edge 관리 템플릿 파일](https://www.microsoftedgeinsider.com/enterprise)의 ADMX 설정을 사용합니다. 그러나 Intune 템플릿은 100% 클라우드 기반입니다. 설정을 구성하고, 원하는 설정을 찾는 단순하고 간단한 방법을 제공합니다.

**관리 템플릿**은 Intune에 기본 제공되고, OMA-URI 사용을 포함한 사용자 지정이 필요하지 않습니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 원스톱 상점으로 이러한 템플릿 설정을 사용하여 Windows 10 디바이스를 관리합니다.

이 문서에서는 Windows 10 디바이스에 대한 템플릿을 만드는 단계를 나열하고, Intune에서 사용 가능한 모든 설정을 필터링하는 방법을 보여줍니다. 템플릿을 만들 때 디바이스 구성 프로필을 만듭니다. 그런 다음, 조직의 Windows 10 디바이스에 이 프로필을 할당하거나 배포할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

- 이러한 설정 중 일부는 Windows 10 버전 1703(RS2)부터 사용할 수 있습니다. 최상의 환경을 위해 Windows 10 Enterprise 버전 1903(19H1) 이상을 사용하는 것이 좋습니다.

- Windows 설정에서는 [Windows 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies)를 사용합니다. CSP는 Home, Professional, Enterprise 등과 같은 다양한 Windows 버전에서 작동합니다. CSP가 특정 버전에서 작동하는지 확인하려면 [Windows 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#admx-backed-policies)로 이동합니다.

## <a name="create-a-template"></a>템플릿 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 프로필의 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **관리 템플릿**을 선택합니다.

4. **만들기**를 선택합니다. 새 창에서 **설정**을 선택합니다. 모든 설정이 나열되고, 화살표 앞과 뒤를 사용하여 자세한 설정을 볼 수 있습니다.

    ![설정의 샘플 목록을 보고 이전 및 다음 단추를 사용합니다.](./media/administrative-templates-windows/administrative-templates-sample-settings-list.png)

    > [!TIP]
    > Intune의 Windows 설정은 로컬 그룹 정책 편집기(`gpedit`)에 표시되는 온-프레미스 그룹 정책 경로와 관련됩니다.

5. 기본적으로 드롭다운 목록에는 **모든 제품**이 표시됩니다. 이 목록에서 **Windows** 설정만 표시하거나 **Office** 설정만 표시하거나, **Edge 버전 77 이상** 설정만 표시하도록 설정을 필터링할 수도 있습니다.

    ![Intune의 관리 템플릿에서 모든 Windows 또는 모든 Office 설정을 표시하도록 목록을 필터링합니다.](./media/administrative-templates-windows/administrative-templates-choose-windows-office-all-products.png)

    > [!NOTE]
    > Microsoft Edge 설정은 다음에 적용됩니다.
    >
    > - Microsoft Edge 버전 77 이상. Microsoft Edge 45 이전 버전을 구성하려면 [Microsoft Edge 브라우저 디바이스 제한 설정](device-restrictions-windows-10.md#microsoft-edge-browser)을 참조하세요.
    > - [KB 4512509](https://support.microsoft.com/kb/4512509)가 설치된 Windows 10 RS4 이상
    > - [KB 4512534](https://support.microsoft.com/kb/4512534)가 설치된 Windows 10 RS5 이상
    > - [KB 4512941](https://support.microsoft.com/kb/4512941)이 설치된 Windows 10 19H1 이상

6. 설정을 선택합니다. 예를 들어 **Office**에 대해 필터링하고 **제한된 찾아보기 활성화**를 선택합니다. 설정에 대한 자세한 설명이 표시됩니다. **사용**이나 **사용 안 함**을 선택하거나 설정을 **구성되지 않음**(기본값) 상태로 둡니다. 자세한 설명은 **사용**, **사용 안 함** 또는 **구성되지 않음**을 선택하는 경우 발생하는 작업을 설명합니다.
7. **확인**을 선택하여 변경 내용을 저장합니다.

설정의 목록을 계속해서 진행하고, 사용자 환경에서 원하는 설정을 구성합니다. 몇 가지 예제는 다음과 같습니다.

- **VBA 매크로 알림 설정** 설정을 사용하여 Word 및 Excel 등의 다른 Microsoft Office 프로그램에서 VBA 매크로를 처리합니다.
- **파일 다운로드 허용** 설정을 사용하여 Internet Explorer에서 다운로드를 허용하거나 금지합니다.
- **컴퓨터에서 절전 모드가 해제될 때(연결) 암호 필요**를 사용하여 디바이스가 절전 모드에서 해제되는 경우 사용자에게 암호를 요청합니다.
- **서명되지 않은 ActiveX 컨트롤 다운로드** 설정을 사용하여 사용자가 Internet Explorer에서 서명되지 않은 ActiveX 컨트롤을 다운로드하는 것을 차단합니다.
- **시스템 복원 해제** 설정을 사용하여 사용자가 디바이스에서 시스템 복원을 실행하는 것을 차단합니다.
- **즐겨찾기 가져오기 허용** 설정을 사용하여 사용자가 다른 브라우저의 즐겨찾기를 Microsoft Edge로 가져오도록 허용하거나 차단합니다.
- 이외에 많은 기능이 있습니다.

## <a name="find-some-settings"></a>일부 설정 찾기

이러한 템플릿에서 사용할 수 있는 수백 가지 설정이 있습니다. 특정 설정을 쉽게 찾으려면 기본 제공 기능을 사용합니다.

- 템플릿에서 **설정**, **상태**, **설정 유형** 또는 **경로** 열을 선택하여 목록을 정렬합니다. 예를 들어 **경로** 열을 선택하여 `Microsoft Excel` 경로의 모든 설정을 봅니다.

  ![Intune의 관리 템플릿에서 그룹 정책 또는 ADMX 경로를 기준으로 그룹화한 모든 설정을 표시하려면 경로를 클릭합니다.](./media/administrative-templates-windows/path-filter-shows-excel-options.png)

- 템플릿에서 **검색** 상자를 사용하여 특정 설정을 찾습니다. 제목 또는 경로를 설정하여 검색할 수 있습니다. 예를 들어 `copy`을 검색합니다. `copy`와 함께 모든 설정이 표시됩니다.

  ![copy를 검색하면 Intune의 관리 템플릿의 모든 Windows 및 Office 설정이 표시됩니다.](./media/administrative-templates-windows/search-copy-settings.png) 

  다른 예제에서 `microsoft word`를 검색합니다. Microsoft Word 프로그램에 대해 설정할 수 있는 모든 설정이 표시됩니다. `explorer`를 검색하여 템플릿에 추가할 수 있는 모든 Internet Explorer 설정을 봅니다.

## <a name="next-steps"></a>다음 단계

템플릿이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로 [프로필이라고도 하는 템플릿을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.
