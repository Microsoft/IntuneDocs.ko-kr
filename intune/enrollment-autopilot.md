---
title: Windows Autopilot을 사용하여 디바이스 등록
titleSuffix: Microsoft Intune
description: Windows Autopilot을 사용하여 Windows 10 디바이스를 등록하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a2dc5594-a373-48dc-ba3d-27aff0c3f944
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 301945f96b62dce9ee1cf6caedf40fe6b03499e3
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166432"
---
# <a name="enroll-windows-devices-in-intune-by-using-the-windows-autopilot"></a>Windows Autopilot을 사용하여 Intune에 Windows 디바이스 등록  
Windows Autopilot이 Intune에 디바이스를 등록하는 작업을 간소화합니다. 사용자 지정 운영 체제 이미지 빌드 및 유지 관리는 시간이 오래 걸리는 프로세스입니다. 또한 최종 사용자에게 제공하기 전에 이러한 사용자 지정 운영 체제 이미지를 새 디바이스에 적용하여 사용 준비를 하는 데에도 시간이 걸릴 수 있습니다. Microsoft Intune 및 Autopilot을 사용하면 사용자 지정 운영 체제 이미지를 빌드 및 유지 관리하고 디바이스에 적용할 필요 없이 최종 사용자에게 새 디바이스를 제공할 수 있습니다. Intune을 사용하여 Autopilot 디바이스를 관리하는 경우 디바이스를 등록한 후에 정책, 프로필, 앱 등을 관리할 수 있습니다. 이점, 시나리오 및 필수 구성 요소에 대한 개요는 [Windows Autopilot 개요](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)를 참조하세요.

Autopilot 배포에는 다음과 같은 네 가지 유형이 있습니다.
- 키오스크, 디지털 간판 또는 공유 디바이스용 [자체 배포 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/self-deploying)
- 파트너 또는 IT 직원이 완전히 구성되고 비즈니스 준비가 완료된 Windows 10 PC를 사전에 프로비전할 수 있는 [화이트 글러브](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove), 최신 버전의 Windows 10을 기존 디바이스에 쉽게 배포할 수 있는 [기존 디바이스용 Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices)
- 기존 사용자를 위한 [사용자 구동 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) 


## <a name="prerequisites"></a>전제 조건
- [Intune 구독](licenses.md)
- [Windows 자동 등록 사용](windows-enroll.md#enable-windows-10-automatic-enrollment)
- [Azure Active Directory Premium 구독](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->

## <a name="how-to-get-the-csv-for-import-in-intune"></a>Intune에서 가져오기 위해 CSV를 얻는 방법

자세한 내용은 powershell cmdlet 이해를 참조하세요.

- [Get-WindowsAutoPilotInfo](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo)

## <a name="add-devices"></a>디바이스 추가

디바이스 정보가 포함된 CSV 파일을 가져와서 Windows Autopilot 디바이스를 추가할 수 있습니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **디바이스** > **가져오기**를 선택합니다.

    ![Windows Autopilot 디바이스 스크린샷](media/enrollment-autopilot/autopilot-import-device.png)

2. **Windows Autopilot 디바이스 추가** 에서 추가할 디바이스를 나열하는 CSV 파일로 이동합니다. CSV 파일에는 일련 번호, Windows 제품 ID, 하드웨어 해시, 선택적 그룹 태그 및 선택적 할당된 사용자가 나열되어야 합니다. 목록에 최대 500개의 행을 가질 수 있습니다. 아래 표시된 헤더 및 줄 형식을 사용합니다.

    `Device Serial Number,Windows Product ID,Hardware Hash,Group Tag,Assigned User`</br>
    `<serialNumber>,<ProductID>,<hardwareHash>,<optionalGroupTag>,<optionalAssignedUser>`

    ![Windows AutoPilot 디바이스 추가 스크린샷](media/enrollment-autopilot/autopilot-import-device2.png)

    >[!IMPORTANT]
    > CSV 업로드를 사용하여 사용자를 할당하는 경우 유효한 UPN을 할당해야 합니다. 잘못된 UPN(잘못된 사용자 이름)을 할당하는 경우 잘못된 할당을 제거할 때까지 디바이스에 액세스할 수 없습니다. CSV 업로드 중 **할당된 사용자** 열에서 수행하는 유일한 유효성 검사는 도메인 이름이 유효한지 확인하는 것입니다. 기존 또는 올바른 사용자를 할당하고 있는지 확인하기 위해 개별 UPN 유효성 검사를 수행할 수 없습니다.

3. **가져오기**를 선택하여 디바이스 정보 가져오기를 시작합니다. 가져오기는 몇 분 정도 걸릴 수 있습니다.

4. 가져오기가 완료되면 **디바이스 등록** > **Windows 등록** > **Windows Autopilot** > **디바이스** > **동기화**를 선택합니다. 동기화가 진행 중이라는 메시지가 표시됩니다. 동기화되는 디바이스의 수에 따라 프로세스가 완료되는 데 몇 분 정도 걸릴 수 있습니다.

5. 보기를 새로 고쳐 새 디바이스를 확인합니다.

## <a name="create-an-autopilot-device-group"></a>Autopilot 디바이스 그룹 만들기

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **그룹** > **새 그룹**을 선택합니다.
2. **그룹** 블레이드에서:
    1. **그룹 형식**에서 **보안**을 선택합니다.
    2. **그룹 이름** 및 **그룹 설명**을 입력합니다.
    3. **멤버 자격 형식**에서 **할당** 또는 **동적 디바이스**를 선택합니다.
3. 이전 단계에서 **멤버 자격 형식**에 대해 **할당됨**을 선택했다면 **그룹** 블레이드에서 **멤버**를 선택하고 Autopilot 디바이스를 그룹에 추가합니다.
    아직 등록되지 않은 AutoPilot 디바이스는 디바이스 이름이 디바이스의 일련 번호와 동일한 디바이스입니다.
4. 위의 **멤버 자격 형식**에 대해 **동적 디바이스**를 선택했다면 **그룹** 블레이드에서 **동적 디바이스 멤버**를 선택하고 **고급 규칙** 상자에서 다음 코드를 입력합니다. 이 규칙은 Autopilot 디바이스만 소유하는 특성을 대상으로 하므로 Autopilot 디바이스만 이러한 규칙에 의해 수집됩니다.
    - Autopilot 디바이스를 모두 포함한 그룹을 만들려는 경우 `(device.devicePhysicalIDs -any _ -contains "[ZTDId]")`를 입력합니다.
    - Intune의 그룹 태그 필드는 Azure AD 디바이스의 OrderID 특성에 해당합니다. 특정 그룹 태그(Azure AD 디바이스 OrderID)를 사용하여 모든 Autopilot 디바이스를 포함하는 그룹을 만들려는 경우 `(device.devicePhysicalIds -any _ -eq "[OrderID]:179887111881")`을 입력해야 합니다.
    - 특별 구매 주문 ID를 사용하여 Autopilot 디바이스를 모두 포함한 그룹을 만들려는 경우 `(device.devicePhysicalIds -any _ -eq "[PurchaseOrderId]:76222342342")`를 입력합니다.
    
    **고급 규칙** 코드를 추가한 후에 **저장**을 선택합니다.
5. **만들기**를 선택합니다.  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 만들기
Autopilot 배포 프로필은 Autopilot 디바이스를 구성하는 데 사용됩니다.
1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기**를 선택합니다.
2. **기본 사항** 페이지에서 **이름** 및 선택적 **설명**을 입력합니다.

    ![기본 페이 스크린샷의](media/enrollment-autopilot/create-profile-basics.png)

3. 할당된 그룹의 모든 디바이스가 자동으로 Autopilot으로 변환되도록 하려면 **모든 대상 디바이스를 다시 Autopilot으로 변환**을 **예**로 설정합니다. 할당된 그룹에서 Autopilot이 아닌 모든 디바이스는 Autopilot 배포 서비스에 등록됩니다. 등록을 처리하는 데 48시간 정도가 걸립니다. 디바이스 등록을 취소하고 재설정하면 Autopilot이 해당 디바이스를 등록합니다. 이 방법으로 디바이스를 등록한 후 이 옵션을 비활성화하거나 프로필 할당을 제거해도 디바이스가 Autopilot 배포 서비스에서 제거되지 않습니다. 대신 [디바이스를 직접 제거](enrollment-autopilot.md#delete-autopilot-devices)해야 합니다.
4. **다음**을 선택합니다.
5. **OOBE(첫 실행 경험)** 페이지에서 **배포 모드**로 다음 두 옵션 중 하나를 선택합니다.
    - **사용자 기반**: 이 프로필을 사용하는 디바이스는 디바이스를 등록한 사용자와 연결됩니다. 디바이스를 등록하려면 사용자 자격 증명이 필요합니다.
    - **자체 배포(미리 보기)** : (Windows 10, 버전 1809 이상 필요) 이 프로필을 사용하는 디바이스는 디바이스를 등록하는 사용자와 연결되지 않습니다. 디바이스를 등록하는 데 사용자 자격 증명이 필요하지 않습니다. 연결된 사용자가 없는 디바이스에는 사용자 기반 규정 준수 정책이 적용되지 않습니다. 자체 배포 모드를 사용하는 경우 디바이스를 대상으로 하는 규정 준수 정책만 적용됩니다.

    ![OOBE 페이지 스크린샷](media/enrollment-autopilot/create-profile-outofbox.png)

6. **다음으로 Azure AD에 조인** 상자에서 **Azure AD 조인됨**을 선택합니다.
7. 다음 옵션을 구성합니다.
    - **EULA(최종 사용자 사용권 계약)** : 사용자에게 EULA를 표시할지 여부를 선택합니다(Windows 10 버전 1709 이상).
    - **개인 정보 설정**: 사용자에게 개인 정보 설정을 표시할지 여부를 선택합니다.
    >[!IMPORTANT]
    >진단 데이터 설정의 기본값은 Windows 버전에 따라 다릅니다. Windows 10 버전 1903을 실행하는 디바이스의 경우, 첫 실행 경험 중에 기본값이 전체로 설정됩니다. 자세한 내용은 [Windows 진단 데이터](https://docs.microsoft.com/windows/privacy/windows-diagnostic-data)를 참조하세요. <br>
    
    - **계정 변경 옵션 숨기기(Windows 10, 버전 1809 이상 필요)** : **숨기기**를 선택하면 계정 변경 옵션이 회사 로그인 및 도메인 오류 페이지에서 표시되지 않습니다. 이러한 옵션을 사용하려면 [Azure Active Directory에서 회사 브랜딩을 구성](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding)해야 합니다.
    - **사용자 계정 유형**: 사용자 계정 유형(**관리자** 또는 **표준** 사용자)을 선택합니다.
    - **화이트 글러브 OOBE 허용**(Windows 10 1903 이상 버전 필요. [추가 물리적 요구 사항](https://docs.microsoft.com/windows/deployment/windows-autopilot/white-glove#prerequisites)): 화이트 글러브 지원을 허용하려면 **예**를 선택합니다.
    - **디바이스 이름 템플릿 적용**(Windows 10 1809 이상 버전 필요): **예**를 선택하여 등록하는 동안 디바이스의 이름을 지정할 때 사용할 템플릿을 만듭니다. 이름은 15자 이하여야 하고, 문자, 숫자 및 하이픈만 포함할 수 있습니다. 이름이 모두 숫자일 수는 없습니다. [%SERIAL% 매크로](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)를 사용하여 하드웨어별 일련 번호를 추가합니다. 또는 [%RAND:x% 매크로](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)를 사용하여 숫자의 임의 문자열을 추가합니다. 여기서 x는 추가할 자릿수입니다. 
    - **언어(지역)** \*: 디바이스에 사용할 언어를 선택합니다. 이 옵션은 **배포 모드**에 대해 **자체 배포**를 선택한 경우에만 사용할 수 있습니다.
    - **키보드 자동으로 구성**\*: **언어(지역)** 를 선택한 경우 **예**를 선택하여 키보드 선택 영역 페이지를 건너뜁니다. 이 옵션은 **배포 모드**에 대해 **자체 배포**를 선택한 경우에만 사용할 수 있습니다.
8. **다음**을 선택합니다.
9. **범위 태그** 페이지에서 필요에 따라 이 프로필에 적용하려는 범위 태그를 추가합니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 역할 기반 액세스 제어 및 범위 태그 사용](scope-tags.md)을 참조하세요.
10. **다음**을 선택합니다.
11. **할당** 페이지에서 **할당 대상**으로 **선택한 그룹**을 선택합니다.

    ![할당 페이지 스크린샷](media/enrollment-autopilot/create-profile-assignments.png)

12. **포함할 그룹 선택**을 선택하고 이 프로필에 포함하려는 그룹을 선택합니다.
13. 모든 그룹을 제외하려는 경우 **제외할 그룹 선택**을 선택하고 제외하려는 그룹을 선택합니다.
14. **다음**을 선택합니다.
15. **검토 + 만들기** 페이지에서 **만들기**를 선택하여 프로필을 만듭니다.

    ![검토 페이지 스크린샷](media/enrollment-autopilot/create-profile-review.png)

> [!NOTE]
> Intune은 할당된 그룹의 새 디바이스에 대해 주기적으로 확인한 다음, 해당 디바이스에 프로필을 할당하는 프로세스를 시작합니다. 이 프로세스를 완료하는 데 몇 분 정도 걸릴 수 있습니다. 디바이스를 배포하기 전에 이 프로세스가 완료되었는지 확인합니다.  **디바이스 등록** > **Windows 등록** > **디바이스**에서 확인할 수 있습니다. 여기에서 "할당되지 않음"에서 "할당"으로, 마지막으로 "할당됨"으로 프로필 상태 변경이 표시됩니다.

## <a name="edit-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 편집
Autopilot 배포 프로필을 만든 후에는 배포 프로필의 특정 부분을 편집할 수 있습니다.   

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록**을 선택합니다.
2. **Windows 등록** 아래의 **Windows Autopilot** 섹션에서 **배포 프로필**을 선택합니다.
3. 편집하려는 프로필을 선택합니다.
4. 왼쪽에 있는 **속성**을 클릭하여 배포 프로필의 이름이나 설명을 변경합니다. 변경한 후에 **저장**을 클릭합니다.
5. OOBE 설정을 변경하려면 **설정**을 클릭합니다. 변경한 후에 **저장**을 클릭합니다.

> [!NOTE]
> 프로필의 변경 내용은 해당 프로필에 할당된 디바이스에 적용됩니다. 그러나 디바이스를 다시 설정하고 다시 등록할 때까지는 Intune에 이미 등록되어 있는 디바이스에 업데이트된 프로필이 적용되지 않습니다.

## <a name="alerts-for-windows-autopilot-unassigned-devices-----163236---"></a>Windows Autopilot 할당되지 않은 디바이스에 대한 경고  <!-- 163236 -->  

경보에는 Autopilot 배포 프로필이 없는 Autopilot 프로그램 디바이스 수가 표시됩니다. 경고의 정보를 사용하여 프로필을 만들어서 할당되지 않은 디바이스에 할당하십시오. 경고를 클릭하면 Windows Autopilot 디바이스의 전체 목록과 해당 디바이스에 대한 자세한 정보가 표시됩니다.


할당되지 않은 디바이스에 대한 경고를 보려면 [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **개요** > **할당되지 않은 디바이스**를 선택합니다.  


## <a name="assign-a-user-to-a-specific-autopilot-device"></a>특정 Autopilot 디바이스에 사용자 할당

특정 Autopilot 디바이스에 사용자를 할당할 수 있습니다. 이렇게 할당하면 Windows를 설정하는 동안 [회사 브랜드](https://docs.microsoft.com/azure/active-directory/fundamentals/customize-branding) 로그인 페이지에 Azure Active Directory의 사용자를 미리 입력합니다. 사용자 지정 인사말 이름을 설정할 수도 있습니다. Windows 로그인을 미리 입력하거나 수정하지 않습니다. 사용이 허가된 Intune 사용자만이 이러한 방식으로 할당될 수 있습니다.

필수 조건: Windows 10, 버전 1809 이상에서 Azure Active Directory 회사 포털이 구성되었습니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록** > **Windows 등록** > **디바이스** &gt; 디바이스 선택 &gt; **사용자 할당**을 선택합니다.

    ![사용자 할당 스크린샷](media/enrollment-autopilot/assign-user.png)

2. 사용이 허가된 Azure 사용자를 선택하여 Intune을 사용하고 **선택**을 선택합니다.

    ![사용자 선택 스크린샷](media/enrollment-autopilot/select-user.png)

3. **사용자 이름** 상자에 친숙한 이름을 입력하거나 기본값을 그대로 수락합니다. 이 문자열은 Windows를 설정하는 동안 사용자가 로그인할 경우에 표시하는 친숙한 이름입니다.

    ![친숙한 이름 스크린샷](media/enrollment-autopilot/friendly-name.png)

4. **확인**을 선택합니다.


## <a name="delete-autopilot-devices"></a>Autopilot 디바이스 삭제

Intune에 등록되지 않은 Windows Autopilot 디바이스를 삭제할 수 있습니다.

- **디바이스 등록** > **Windows 등록** > **디바이스**에서 디바이스를 Windows Autopilot에서 삭제합니다. 삭제할 디바이스를 선택한 다음, **삭제**를 선택합니다. Windows Autopilot 디바이스 삭제는 몇 분 정도 걸릴 수 있습니다.

테넌트에서 디바이스를 완전히 제거하려면 Intune 디바이스, Azure Active Directory 디바이스 및 Windows Autopilot 디바이스 레코드를 삭제해야 합니다. 이 작업은 모두 Intune에서 수행할 수 있습니다.

1. 디바이스가 Intune에 등록된 경우 먼저 [Intune 모든 디바이스 블레이드에서 삭제](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)해야 합니다.

2. **디바이스** > **Azure AD 디바이스**에서 디바이스를 Azure Active Directory 디바이스에서 삭제합니다.

3. **디바이스 등록** > **Windows 등록** > **디바이스**에서 디바이스를 Windows Autopilot에서 삭제합니다. 삭제할 디바이스를 선택한 다음, **삭제**를 선택합니다. Windows Autopilot 디바이스 삭제는 몇 분 정도 걸릴 수 있습니다.

## <a name="using-autopilot-in-other-portals"></a>다른 포털에서 Autopilot 사용
모바일 디바이스 관리에 관심이 없는 경우 다른 포털에서 Autopilot을 사용할 수 있습니다. 다른 포털을 옵션으로 사용할 수 있지만, Intune만 사용하여 Autopilot 배포를 관리하는 것이 좋습니다. Intune과 다른 포털을 사용하는 경우 Intune에서 수행할 수 없는 작업은 다음과 같습니다.  

- Intune에서 만들었지만 다른 포털에서 편집한 프로필에 대한 변경 내용 표시
- 다른 포털에서 만든 프로필 동기화
- 다른 포털에서 수행한 프로필 할당에 대한 변경 내용 표시
- 다른 포털에서 수행한 프로필 할당 동기화
- 다른 포털에서 만든 디바이스 목록에 대한 변경 내용 표시

## <a name="windows-autopilot-for-existing-devices"></a>기존 디바이스에 대한 Windows Autopilot

Configuration Manager를 통해 [기존 디바이스에 대해 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)을 사용하여 등록할 때 관련자 ID로 Windows 디바이스를 그룹화할 수 있습니다. 관련자 ID는 Autopilot 구성 파일의 매개 변수입니다. Azure AD 디바이스 특성인 [enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices)은 자동으로 "OfflineAutopilotprofile-\<관련자 ID\>"와 동일하게 설정됩니다. 이렇게 하면 enrollmentprofileName 특성을 사용하여 관련자 ID에 따라 임의의 Azure AD 동적 그룹을 만들 수 있습니다.

>[!WARNING] 
> 관련자 ID는 Intune에 미리 나열되지 않으므로 디바이스에서 원하는 관련자 ID를 보고할 수 있습니다. 사용자가 Autopilot 또는 Apple DEP 프로필 이름과 일치하는 관련자 ID를 만드는 경우 enrollmentProfileName 특성을 기반으로 하는 동적 Azure AD 디바이스 그룹에 디바이스가 추가됩니다. 이 충돌을 방지하려면:
> - 항상 ‘전체’ enrollmentProfileName 값과 일치하는 동적 그룹 규칙을 생성합니다. 
> - “OfflineAutopilotprofile-”로 시작하는 Autopilot 또는 Apple DEP 프로필은 절대 이름으로 설정하지 마세요.

## <a name="next-steps"></a>다음 단계
등록한 Windows 10 디바이스에 대해 Windows Autopilot을 구성한 후에는 이러한 디바이스를 관리하는 방법을 알아봅니다. 자세한 내용은 [Microsoft Intune 디바이스 관리란?](device-management.md)을 참조하세요.
