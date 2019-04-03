---
title: Microsoft Intune에서 범위 태그를 사용하여 정책 필터링 - Azure | Microsoft Docs
description: 범위 태그를 사용하여 특정 역할에 대한 구성 프로필을 필터링합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/08/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fb57ea2ef5c99c58968ee25b3a75b2165ece787a
ms.sourcegitcommit: 0adb41c0640743d5cb726e66ad2427e3ad6faf20
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658552"
---
# <a name="use-role-based-access-control-rbac-and-scope-tags-for-distributed-it"></a>배포에 대 한 역할 기반 access control (RBAC) 및 범위 태그를 사용 하 여 IT

올바른 관리자 권한 액세스 및 오른쪽 Intune 개체에 대 한 가시성 있는지 확인 하려면 역할 기반 액세스 제어 및 범위 태그를 사용할 수 있습니다. 어떤 액세스를 결정 하는 역할 관리자가 개체를 해야 합니다. 범위 태그는 관리자가 볼 수 있는 개체를 결정 합니다.

예를 들어 시애틀 지사 관리 정책 및 프로필 관리자 역할에 할당 되어 있는지을 가정해 보겠습니다. 이 관리자를 확인 하 여 프로필 및 시애틀 장치에만 적용 되는 정책을 관리 해야 합니다. 이렇게 하려면 어떻게 해야 합니까?

1. 시애틀 라는 범위 태그를 만듭니다.
2. 사용 하 여 정책 및 프로필 관리자 역할에 대 한 역할 할당을 만듭니다. 
    - 구성원 (그룹) = 시애틀 IT 관리자 라는 보안 그룹입니다. 이 그룹의 모든 관리자에는 정책 및 범위 (그룹)에서 사용자/장치에 대 한 프로필을 관리할 수 있는 권한을 갖게 됩니다.
    - 범위 (그룹)는 보안 = 사용자가 시애틀 이라는 그룹입니다. 이 그룹의 모든 사용자/장치는 해당 프로필 및 멤버 (그룹)에서 관리자가 관리 되는 정책을 가질 수 있습니다. 
    - 범위 (태그) = 시애틀 합니다. 멤버 (그룹)에서 관리자는 또한 시애틀 범위 태그는 장치를 확인할 수 있습니다.
3. 정책 및 프로필 관리자 구성원 (그룹)에 액세스할 수 있게 되기를 원하는 시애틀 범위 태그를 추가 합니다.
4. 구성원 (그룹)에서 관리자에 게 표시 하려는 장치에 시애틀 범위 태그를 추가 합니다. 


## <a name="to-create-a-scope-tag"></a>범위 태그를 만들려면

1. Intune **역할** > **범위 (태그)** > **만들기**합니다.

    ![스크린샷 범위 태그를 만듭니다.](./media/scope-tags/create-scope-tag.png)

2. **이름** 및 **설명**을 제공합니다.
3. **만들기**를 선택합니다.

## <a name="to-assign-a-scope-tag-to-a-role"></a>범위 태그를 역할에 할당하려면

1. Intune **역할** > **모든 역할** > 역할 선택 > **할당** > **할당**합니다.

    ![역할에 범위를 할당 하는 스크린샷.](./media/scope-tags/assign-scope-to-role.png)

2. 제공 된 **할당 이름** 및 **설명**합니다.
3. 선택할 **구성원 (그룹)** > **추가** >이 할당의 일부로 원하는 그룹 선택 > **선택**  >   **확인**합니다. 이 그룹의 mUsers 정책 및 범위 (그룹)에서 사용자/장치에 대 한 프로필을 관리할 권한을 갖게 됩니다.

    ![멤버 선택 그룹의 스크린샷입니다.](./media/scope-tags/select-member-groups.png)

4. 사용자/장치 그룹의 특정 집합에서을 관리 하려는 경우 선택 **범위 (그룹)** > **선택한 그룹** > **포함할그룹선택**> 그룹 선택 > **선택** > **확인**합니다. 이 그룹의 모든 사용자/장치는 해당 프로필 및 멤버 (그룹)에서 관리자가 관리 되는 정책이 있을 수 있습니다.

    ![선택 범위 그룹의 스크린샷입니다.](./media/scope-tags/select-scope-groups.png)

    또는 선택할 수 있습니다 **모든 장치**하십시오 **모든 사용자**, 또는 **모든 사용자 및 모든 장치**합니다.

    ![선택 범위 그룹에 대 한 다른 옵션의 스크린샷입니다.](./media/scope-tags/scope-group-other-options.png)
    
5. 선택할 **범위 (태그)** > **추가** >이 역할에 추가 하려는 태그 선택 > **선택** > **확인**. 구성원 (그룹)에서 사용자는 정책 및도 같은 범위 태그를 포함 하는 프로필에 대 한 액세스를 갖게 됩니다.

    ![선택 범위 태그의 스크린샷입니다.](./media/scope-tags/select-scope-tags.png)

6. **확인**을 선택합니다. 

## <a name="to-add-a-scope-tag-to-a-configuration-profile"></a>범위 태그를 구성 프로필에 추가하려면
1. Intune **장치 구성** > **프로필** > 프로필을 선택 합니다.

    ![선택 프로필의 스크린샷입니다.](./media/scope-tags/choose-profile.png)

2. 선택할 **속성** > **범위 (태그)** > **추가**합니다.

    ![범위 태그 추가 스크린샷입니다.](./media/scope-tags/add-scope-tags.png)

3. 아래 **태그 선택**, 프로필에 추가할 태그를 선택 합니다.
4. 선택할 **선택** > **확인** > **저장**합니다.

## <a name="to-assign-a-scope-tag-to-an-app-configuration-policy"></a>범위 태그는 앱 구성 정책을 할당할
사용 하 여 장치에 대 한 **장치 등록 유형** 로 설정 **관리 되는 장치**:
1. 선택할 **클라이언트 앱** > **앱 구성 정책을** > 앱 구성 정책을 선택 합니다.
2. 선택할 **속성** > **범위 (태그)** > 정책에 할당 하려는 태그를 선택 합니다.

사용 하 여 장치에 대 한 **장치 등록 유형** 로 설정 **관리 되는 앱**:
1. 선택할 **클라이언트 앱** > **앱 구성 정책을** > 앱 구성 정책을 선택 합니다.
2. 선택할 **범위 (태그)** > 정책에 할당 하려는 태그를 선택 합니다.


## <a name="to-assign-a-scope-tag-to-an-ios-app-provisioning-profile"></a>범위 태그는 iOS 앱 프로비저닝 프로필을 할당 하려면
1. Intune **클라이언트 앱** > **iOS 앱 프로비저닝 프로필** > 프로필을 선택 합니다.
2. 선택할 **속성** > **범위 (태그)** > 프로필에 할당 하려는 태그를 선택 합니다.
3. 선택할 **선택** > **확인** > **저장**합니다.

## <a name="scope-tag-details"></a>범위 태그 세부 정보
범위 태그를 사용할 때는 이러한 세부 정보를 기억해 야 합니다.

- 현재 범위 태그를 할당할 수 있습니다.
    - 역할 할당
    - 디바이스 준수 정책
    - 디바이스 구성 프로필
    - Windows 10 업데이트 링
    - 관리되는 디바이스
    - 앱
    - 앱 구성 정책을 – 관리 되는 장치
    - Powershell 스크립트
    - DEP 토큰
    - iOS 앱 프로비전 프로필
- 관리자가 Intune에서 개체를 만들면, 새 개체에 해당 관리자에 할당 된 모든 범위 태그를 자동으로 할당 됩니다.
- Intune RBAC는 Azure Active Directory 역할에 적용 되지 않습니다. 따라서 Intune 서비스 관리자 및 전역 관리자 역할이 포함 된 어떤 범위 태그에 관계 없이 Intune에 대 한 전체 관리자 액세스 경우
- 범위 태그를 사용 하 여 역할 할당에는 관리자에는 없는 범위 태그를 사용 하 여 Intune 개체도 볼 수 있습니다.
- 역할 할당에 있는 범위 태그를 할당할 수 있습니다.
- 대상 그룹에만 역할 할당의 범위 (그룹)에 나와 있는 수 있습니다.
- 범위 태그는 사용자의 역할을 할당할 경우 Intune 개체의 모든 범위 태그를 삭제할 수 없습니다. 하나 이상의 범위 태그는 필수입니다.

## <a name="next-steps"></a>다음 단계

[역할](role-based-access-control.md) 및 [프로필](device-profile-assign.md)을 관리합니다.
