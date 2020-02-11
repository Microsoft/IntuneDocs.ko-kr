---
title: Microsoft Intune에서 디바이스 프로필 할당
description: Microsoft 엔드포인트 관리자 관리 센터를 사용해 사용자 및 디바이스에 디바이스 정책 및 프로필을 할당합니다. Microsoft Intune에서 프로필 할당으로부터 그룹을 제외하는 방법에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/28/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b61c333f41054194b44c7517e508fe1ef6d28d4
ms.sourcegitcommit: b0d683917af83170f85022b270270d8ced8e301c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76812381"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Microsoft Intune에서 사용자 및 디바이스 프로필 할당

프로필을 만들고 이 프로필에는 입력한 모든 설정이 포함됩니다. 다음 단계에서는 Azure AD(Azure Active Directory) 사용자 또는 디바이스 그룹에 프로필을 배포 또는 “할당”합니다. 할당된 경우 사용자 및 디바이스는 프로필을 수신하고 입력한 설정이 적용됩니다.

이 문서에서는 프로필을 할당하는 방법을 보여 주고 프로필에서 범위 태그를 사용하는 방법을 설명합니다.

> [!NOTE]  
> 프로필이 제거되거나 디바이스에 더 이상 할당되지 않으면 프로필의 설정에 따라 다른 상황이 발생할 수 있습니다. 설정은 CSP를 기반으로 하며, 각 CSP는 프로필 제거를 다르게 처리할 수 있습니다. 예를 들어 설정에서 기존 값을 유지하고 기본값으로 되돌리지 않을 수 있습니다. 동작은 운영 체제의 각 CSP에 의해 제어됩니다. Windows CSP 목록은 [CSP(구성 서비스 공급자) 참조](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)에서 확인하세요.
>
> 설정을 다른 값으로 변경하려면 새 프로필을 만들고 **구성되지 않음**으로 설정을 구성한 다음 프로필을 할당합니다. 사용자는 디바이스에 적용된 설정을 선호하는 값으로 변경할 수 있습니다.
>
> 이러한 설정을 구성할 때는 파일럿 그룹에 배포하는 것이 좋습니다. 자세한 Intune 출시 조언은 [출시 계획 만들기](../fundamentals/planning-guide-rollout-plan.md)를 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

프로필을 할당하려면 적절한 역할이 있어야 합니다. 자세한 내용은 [Microsoft Intune을 통한 RBAC(역할 기반 액세스 제어)](../fundamentals/role-based-access-control.md)를 참조하세요.

## <a name="assign-a-device-profile"></a>디바이스 프로필 할당

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **구성 프로필**을 선택합니다. 모든 프로필이 나열됩니다.
3. 할당하려는 프로필을 선택한 후 **할당**을 선택합니다.
4. 그룹을 **포함**하거나 **제외**하도록 선택한 다음, 그룹을 선택합니다. 그룹을 선택하면 Azure AD 그룹을 선택합니다. 여러 그룹을 선택하려면 **Ctrl** 키를 누른 상태로 그룹을 선택합니다.

    ![프로필 할당에서 그룹 제외 또는 포함하는 옵션 스크린샷](./media/device-profile-assign/group-include-exclude.png)

5. 변경 내용을 **저장**합니다.

### <a name="evaluate-how-many-users-are-targeted"></a>대상으로 지정된 사용자 수 평가

프로필을 할당하면 영향을 받는 사용자 수를 **평가**할 수도 있습니다. 이 기능은 사용자 수를 계산하며, 디바이스 수는 계산하지 않습니다.

1. 관리 센터에서 **디바이스** > **구성 프로필**을 선택합니다.
2. 프로필을 선택한 후 **할당** > **평가**를 선택합니다. 메시지는 이 프로필의 대상이 되는 사용자 수를 보여 줍니다.

**평가** 단추가 회색으로 표시되면 프로필이 하나 이상의 그룹에 할당되었는지 확인합니다.

## <a name="use-scope-tags-or-applicability-rules"></a>범위 태그 또는 적용 가능성 규칙 사용

프로필을 만들거나 업데이트하면 프로필에 범위 태그 및 적용 가능성 규칙을 추가할 수도 있습니다.

**범위 태그**는 `US-NC IT Team` 또는 `JohnGlenn_ITDepartment` 등 특정 그룹에 프로필을 필터링할 수 있는 좋은 방법입니다. 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

Windows 10 디바이스에서 **적용 가능성 규칙**을 추가하여 프로필이 특정 OS 버전 또는 특정 Windows 버전에만 적용되도록 할 수 있습니다. [적용 가능성 규칙](device-profile-create.md#applicability-rules)에 대한 추가 정보가 있습니다.

## <a name="user-groups-vs-device-groups"></a>사용자 그룹 및 디바이스 그룹

대부분의 사용자는 사용자 그룹을 사용하는 경우와 디바이스 그룹을 사용하는 경우를 알고 싶어합니다. 어떤 그룹을 사용할지는 목표에 따라 달라집니다. 다음은 시작하는 데 도움이 되는 몇 가지 지침입니다.

### <a name="device-groups"></a>Device groups

디바이스에서 로그인한 사용자에 관계없이 설정을 적용하려면 디바이스 그룹에 프로필을 할당합니다. 디바이스 그룹에 적용되는 설정은 사용자가 아니라 항상 디바이스를 따라 이동합니다.

예를 들면 다음과 같습니다.

- 디바이스 그룹은 전용 사용자가 없는 디바이스를 관리하는 데 유용합니다. 예를 들어, 티켓을 인쇄하거나 인벤토리를 검색하거나 교대 근무 작업자가 공유하는 디바이스는 특정 웨어하우스 등에 할당됩니다. 이러한 디바이스를 디바이스 그룹에 배치하고 이 디바이스 그룹에 프로필을 할당합니다.

- BIOS에서 설정을 업데이트하는 [DFCI(디바이스 펌웨어 구성 인터페이스)](device-firmware-configuration-interface-windows.md)를 만듭니다. 예를 들어, 디바이스 카메라를 사용하지 않도록 이 프로필을 구성하거나 부팅 옵션을 잠가 사용자가 다른 OS를 부팅하지 못하도록 할 수 있습니다. 이 프로필은 디바이스 그룹에 할당하기에 좋은 시나리오입니다.

- 일부 특정 Windows 디바이스에서는 디바이스를 사용하는 사용자에 관계없이 항상 일부 Microsoft Edge 설정을 제어하려고 할 수 있습니다. 예를 들어, 모든 다운로드를 차단하고 모든 쿠키를 현재 검색 세션으로 제한하고 검색 기록을 삭제하려고 합니다. 이 시나리오에서는 이러한 특정 Windows 디바이스를 디바이스 그룹에 배치합니다. 그런 다음, [Intune에서 관리 템플릿](administrative-templates-windows.md)을 만들고, 이러한 디바이스 설정을 추가한 후 이 프로필을 디바이스 그룹에 할당합니다.

요약하자면, 디바이스에 로그인한 사용자가 누군지, 로그인한 사람이 있는지 여부를 신경쓰지 않으면서 디바이스 그룹을 사용할 수 있습니다. 설정이 항상 디바이스에서 유지되는 것을 원할 것입니다.

### <a name="user-groups"></a>사용자 그룹

사용자 그룹에 적용된 프로필 설정은 항상 사용자를 따라 이동하며, 여러 디바이스에 로그인한 경우 사용자를 따라 이동합니다. 일반적으로 사용자는 업무용 Surface 및 개인 iOS 디바이스와 같은 여러 디바이스를 사용하게 됩니다. 또한 개인 사용자는 일반적으로 이러한 디바이스에서 메일 및 기타 조직 리소스에 액세스하게 됩니다.

예를 들면 다음과 같습니다.

- 모든 디바이스에 모든 사용자를 위한 지원 센터 아이콘을 배치하려고 합니다. 이 시나리오에서는 사용자 그룹에 이러한 사용자를 추가하고 이 사용자 그룹에 지원 센터 아이콘 프로필을 할당합니다.
- 사용자는 조직 소유의 새 디바이스를 받게 됩니다. 사용자는 해당 도메인 계정으로 디바이스에 로그인합니다. 디바이스는 Azure AD에 자동으로 등록되고 Intune에서 자동으로 관리됩니다. 이 프로필은 사용자 그룹에 할당하기에 좋은 시나리오입니다.
- 사용자가 디바이스에 로그인할 때마다 OneDrive 또는 Office와 같은 앱의 기능을 제어하려고 합니다. 이 시나리오에서는 사용자 그룹에 OneDrive 또는 Office 프로필 설정을 할당합니다.

  예를 들어, Office 앱에서 신뢰할 수 없는 ActiveX 컨트롤을 차단하려고 합니다. [Intune에서 관리 템플릿](administrative-templates-windows.md)을 만들고, 이러한 설정을 구성한 후 이 프로필을 사용자 그룹에 할당합니다.

요약하자면, 어떤 디바이스를 사용하든, 설정 및 규칙이 항상 사용자와 함께 이동하도록 하려는 경우에는 사용자 그룹을 사용합니다.

## <a name="exclude-groups-from-a-profile-assignment"></a>프로필 할당에서 그룹 제외

Intune 디바이스 구성 프로필을 통해 프로필 할당에 그룹을 포함하거나 반대로 제외할 수 있습니다.

사용자 그룹의 프로필을 만들고 할당하는 것이 가장 좋습니다. 그리고 디바이스 그룹에 대해 다른 프로필을 특별히 만들고 할당합니다. 그룹에 대한 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md)을 참조하세요.

프로필을 할당하는 경우 그룹을 포함하거나 제외할 때 다음 표를 사용합니다. 확인 표시가 있으면 할당이 지원됨을 의미합니다.

![지원되는 옵션에서는 프로필 할당에서 그룹이 포함 또는 제외됩니다.](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>알아야 할 사항

- 다음과 같이 동일한 그룹 유형 시나리오에서는 제외가 포함보다 우선하게 됩니다.

  - 사용자 그룹 포함 및 제외
  - 디바이스 그룹 포함 및 제외

  예를 들어 **모든 회사 사용자** 사용자 그룹에 디바이스 프로필을 할당하되 **Senior Management Staff** 사용자 그룹의 구성원을 제외할 수 있습니다. 두 그룹 모두 사용자 그룹이므로 **Senior Management Staff**를 제외한 **모든 회사 사용자**가 프로필을 가져옵니다.

- Intune은 사용자-디바이스 그룹 관계를 평가하지 않습니다. 혼합 그룹에 프로필을 할당하는 경우, 결과는 원하는 대로 표시되지 않을 수 있습니다.

  예를 들어 **모든 사용자** 사용자 그룹에 디바이스 프로필을 할당하되 **모든 개인 디바이스** 디바이스 프로필은 제외한다고 가정해 보겠습니다. 이 혼합 그룹 정책 할당에서 **모든 사용자**가 프로필을 가져옵니다. 제외는 적용되지 않습니다.

  따라서 혼합 그룹에는 프로필을 할당하지 않는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계

프로필 및 프로필을 실행하는 디바이스를 모니터링하는 방법에 대한 지침은 [디바이스 프로필 모니터링](device-profile-monitor.md)을 참조하세요.
