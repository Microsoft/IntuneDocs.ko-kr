---
title: Intune에서 배포 하기 위해 RBAC (역할 기반 액세스 제어) 및 범위 태그를 사용 합니다. | Microsoft Docs
description: 범위 태그를 사용하여 특정 역할에 대한 구성 프로필을 필터링합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.assetid: a21d3039-f2ed-4f43-b6fa-d00c071edbc4
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e1f81d26227bb206aa55ca495f4a4ee5e8ae9907
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548131"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용

역할 기반 액세스 제어와 범위 태그를 사용하면 올바른 관리자가 올바른 Intune 개체에 대한 올바른 액세스 권한과 가시성을 갖도록 설정할 수 있습니다. 역할은 관리자가 어떤 개체에 대해 어떤 액세스 권한을 갖는지를 결정합니다. 범위 태그는 관리자가 볼 수 있는 개체를 결정합니다.

예를 들어, 시애틀 지사 관리자에게 정책 및 프로필 관리자 역할이 있다고 가정하겠습니다. 이 관리자가 시애틀 디바이스에만 적용되는 프로필과 정책만 확인하고 관리할 수 있도록 설정하려고 합니다. 이 액세스를 설정 하려면 다음을 수행 합니다.

1. 시애틀이라는 범위 태그를 만듭니다.
2. 정책 및 프로필 관리자 역할에 대한 역할 할당을 다음과 같이 만듭니다. 
    - 멤버(그룹) = 시애틀 IT 관리자라는 보안 그룹. 이 그룹의 모든 관리자는 범위(그룹)에 포함된 사용자/디바이스에 대한 정책과 프로필을 관리할 수 있는 권한을 갖게 됩니다.
    - 범위(그룹) = 시애틀 사용자라는 보안 그룹. 이 그룹의 모든 사용자/디바이스는 멤버(그룹)의 관리자가 관리하는 프로필 및 정책을 가질 수 있습니다. 
    - 범위(태그) = 시애틀. 구성원(그룹)의 관리자는 시애틀 범위 태그도 있는 Intune 개체를 볼 수 있습니다.
3. 구성원(그룹)의 관리자가 액세스할 수 있게 하려는 정책 및 프로필에 시애틀 범위 태그를 추가합니다.
4. 멤버(그룹)의 관리자에게 표시할 디바이스에 시애틀 범위 태그를 추가합니다. 

## <a name="default-scope-tag"></a>기본 범위 태그
기본 범위 태그는 범위 태그를 지 원하는 태그가 없는 모든 개체에 자동으로 추가 됩니다.

기본 범위 태그 기능은 Microsoft Endpoint Configuration Manager의 보안 범위 기능과 유사합니다. 

## <a name="to-create-a-scope-tag"></a>범위 태그를 만들려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테 넌 트 관리** > **역할** > **범위 (태그)**  > **만들기**를 선택 합니다.

    ![범위 태그 만들기 스크린샷입니다.](./media/scope-tags/create-scope-tag.png)

2. **이름** 및 **설명**(선택 사항)을 입력합니다.
3. 특정 그룹의 모든 장치를 원하는 경우 **선택한 그룹의 모든 장치에 범위 태그 할당**을 선택 합니다.
    1. **포함할 그룹 선택** 페이지에서이 범위 태그를 할당 하려는 장치를 포함 하는 그룹을 선택 합니다.
    2. **선택**을 선택합니다.
4. **만들기**를 선택합니다.

## <a name="to-assign-a-scope-tag-to-a-role"></a>범위 태그를 역할에 할당하려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테 넌 트 관리** > **역할** > 모든 역할  **> 할당** > **할당** > 할당 **역할을 선택 합니다**.
2. **할당 이름**과 **설명**을 제공합니다.
3. **멤버(그룹)**  > **추가**를 선택하고, 이 할당의 일부로 설정할 그룹을 선택하고, **선택** > **확인**을 누릅니다. 이 그룹의 사용자에 게는 범위 (그룹)에서 사용자/장치를 관리할 수 있는 권한이 부여 됩니다.

    ![멤버 그룹 선택 스크린샷입니다.](./media/scope-tags/select-member-groups.png)

4. 특정 그룹 세트로 사용자/디바이스를 관리하려면, **범위(그룹)**  > **선택된 그룹** > **포함할 그룹 선택**을 선택하고 그룹 선택 > **선택** > **확인**을 누릅니다. 이 그룹의 모든 사용자/장치는 구성원 (그룹)의 관리자가 관리 합니다.

    ![범위 그룹 선택 스크린샷입니다.](./media/scope-tags/select-scope-groups.png)

    또는 **모든 디바이스**, **모든 사용자** 또는 **모든 사용자 및 모든 디바이스**를 선택합니다.

    ![범위 그룹 선택에 대한 다른 옵션의 스크린샷입니다.](./media/scope-tags/scope-group-other-options.png)
    
5. **범위(태그)**  > **추가**를 선택하고, 이 역할에 추가할 태그를 선택하고, **선택** > **확인**을 누릅니다. 구성원 (그룹)의 사용자는 동일한 범위 태그를 가진 Intune 개체에 액세스할 수 있습니다.

    ![범위 태그 선택 스크린샷입니다.](./media/scope-tags/select-scope-tags.png)

6. **확인**을 선택합니다. 

## <a name="assign-scope-tags-to-other-objects"></a>다른 개체에 범위 태그 할당

범위 태그를 지 원하는 개체의 경우 일반적으로 범위 태그가 **속성**아래에 나타납니다. 예를 들어 구성 프로필에 범위 태그를 할당 하려면 다음 단계를 수행 합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **장치** > **구성 프로필** 을 선택 하 > 프로필을 선택 합니다.

2. **속성** > **범위(태그)**  > **추가**를 선택합니다.

    ![범위 태그 추가 스크린샷입니다.](./media/scope-tags/add-scope-tags.png)

3. **태그 선택**에서 프로필에 추가할 태그를 선택합니다.
4. **선택** > **확인** > **저장**을 선택합니다.


## <a name="scope-tag-details"></a>범위 태그 세부 정보
범위 태그를 사용하는 경우, 다음 세부 정보를 기억해야 합니다. 

- 테 넌 트가 여러 버전의 해당 개체 (예: 역할 할당 또는 앱)를 포함할 수 있는 경우 Intune 개체 유형에 범위 태그를 할당할 수 있습니다.
  다음 Intune 개체는이 규칙의 예외 이며 현재 범위 태그를 지원 하지 않습니다.
    - Windows ESP 프로필
    - 디바이스 범주
    - 등록 제한
    - Corp 장치 식별자
    - Autopilot 장치
    - 장치 준수 위치
    - Jamf 장치
- Vpp 토큰과 연결 된 vpp 앱 및 전자책는 연결 된 vpp 토큰에 할당 된 범위 태그를 상속 합니다.
- DEP 토큰과 연결 된 dep (장비 등록 프로그램) 장치 및 DEP 프로필은 연결 된 DEP 토큰에 할당 된 범위 태그를 상속 합니다.
- 관리자가 Intune에서 개체를 만들면 이 관리자에게 할당된 모든 범위 태그가 새 개체에 자동으로 할당됩니다.
- Intune RBAC는 Azure Active Directory 역할에 적용되지 않습니다. 따라서 Intune 서비스 관리자 및 전역 관리자 역할은 소유하는 범위 태그가 무엇이든 Intune에 대해 전체 관리자 액세스 권한을 갖습니다.
- 역할 할당에 범위 태그가 없는 경우 IT 관리자는 IT 관리자 권한에 따라 모든 개체를 볼 수 있습니다. 범위 태그가 없는 관리자는 기본적으로 모든 범위 태그를 포함 합니다.
- 역할 할당에 있는 범위 태그만 할당할 수 있습니다.
- 역할 할당의 범위(그룹)에 나열된 그룹만 대상으로 할 수 있습니다.
- 역할에 범위 태그가 할당되어 있으면 Intune 개체의 모든 범위 태그를 삭제할 수 없습니다. 하나 이상의 범위 태그는 필수입니다.

## <a name="next-steps"></a>다음 단계

[여러 역할 할당이](role-based-access-control.md#multiple-role-assignments)있는 경우 범위 태그가 어떻게 동작 하는지 알아보세요.
[역할](role-based-access-control.md) 및 [프로필](../configuration/device-profile-assign.md)을 관리합니다.
