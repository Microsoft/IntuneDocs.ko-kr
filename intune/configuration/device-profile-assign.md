---
title: Microsoft Intune에서 디바이스 프로필 할당
description: Azure Portal을 사용하여 사용자 및 디바이스에 디바이스 프로필 및 정책을 할당합니다. Microsoft Intune에서 프로필 할당으로부터 그룹을 제외하는 방법에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
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
ms.openlocfilehash: 50b91251572e45669f197df7ac4e5ff94caf47a1
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755326"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Microsoft Intune에서 사용자 및 디바이스 프로필 할당

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

프로필을 만들고 이 프로필에는 입력한 모든 설정이 포함됩니다. 다음 단계에서는 Azure AD(Azure Active Directory) 사용자 또는 디바이스 그룹에 프로필을 배포 또는 “할당”합니다. 할당된 경우 사용자 및 디바이스는 프로필을 수신하고 입력한 설정이 적용됩니다.

이 문서에서는 프로필을 할당하는 방법을 보여 주고 프로필에서 범위 태그를 사용하는 방법을 설명합니다.

> [!NOTE]  
> 정책이 제거되거나 더 이상 디바이스에 할당되지 않을 때 설정이 기존 값을 유지할 수도 있습니다. 설정은 기본값으로 되돌아가지 않습니다. 설정을 다른 값으로 변경하려면 새 정책을 만들고 할당합니다.

## <a name="before-you-begin"></a>시작하기 전에

정책을 할당하려면 적절한 역할이 있어야 합니다. 자세한 내용은 [Microsoft Intune을 통한 RBAC(역할 기반 액세스 제어)](../fundamentals/role-based-access-control.md)를 참조하세요.

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

**범위 태그**는 인사 관리 또는 모든 US-NC 직원과 같은 특정 그룹으로 정책을 할당 및 필터링할 수 있는 좋은 방법입니다. 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

Windows 10 디바이스에서 **적용 가능성 규칙**을 추가하여 프로필이 특정 OS 버전 또는 특정 Windows 버전에만 적용되도록 할 수 있습니다. [적용 가능성 규칙](device-profile-create.md#applicability-rules)에 대한 추가 정보가 있습니다.

## <a name="exclude-groups-from-a-profile-assignment"></a>프로필 할당에서 그룹 제외

Intune 디바이스 구성 프로필을 통해 정책 할당에 그룹을 포함하거나 반대로 제외할 수 있습니다.

사용자 그룹의 정책을 만들고 할당하는 것이 가장 좋습니다. 그리고 디바이스 그룹에 대해 다른 정책을 특별히 만들고 할당합니다. 그룹에 대한 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](../fundamentals/groups-add.md)을 참조하세요.

정책을 할당하는 경우 그룹을 포함하거나 제외할 때 다음 표를 사용합니다. 확인 표시가 있으면 할당이 지원됨을 의미합니다.

![지원되는 옵션에서는 프로필 할당에서 그룹이 포함 또는 제외됩니다.](./media/device-profile-assign/include-exclude-user-device-groups.png)

### <a name="what-you-should-know"></a>알아야 할 사항

- 다음과 같이 동일한 그룹 유형 시나리오에서는 제외가 포함보다 우선하게 됩니다.

  - 사용자 그룹 포함 및 제외
  - 디바이스 그룹 포함 및 제외

  예를 들어 **모든 회사 사용자** 사용자 그룹에 디바이스 프로필을 할당하되 **Senior Management Staff** 사용자 그룹의 구성원을 제외할 수 있습니다. 두 그룹 모두 사용자 그룹이므로 **Senior Management Staff**를 제외한 **모든 회사 사용자**가 정책을 가져옵니다.

- Intune은 사용자-디바이스 그룹 관계를 평가하지 않습니다. 혼합 그룹에 정책을 할당하는 경우, 결과는 원하는 대로 표시되지 않을 수 있습니다.

  예를 들어 **모든 사용자** 사용자 그룹에 디바이스 프로필을 할당하되 **모든 개인 디바이스** 디바이스 프로필은 제외한다고 가정해 보겠습니다. 이 혼합 그룹 정책 할당에서 **모든 사용자**가 정책을 가져옵니다. 제외는 적용되지 않습니다.

  따라서 혼합 그룹에 정책을 할당하지 않는 것이 좋습니다.

## <a name="next-steps"></a>다음 단계

프로필 및 프로필을 실행하는 디바이스를 모니터링하는 방법에 대한 지침은 [디바이스 프로필 모니터링](device-profile-monitor.md)을 참조하세요.
