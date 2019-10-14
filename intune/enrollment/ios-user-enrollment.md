---
title: iOS 디바이스 등록 - 사용자 등록
titleSuffix: Microsoft Intune
description: iOS 및 iPadOS 사용자 등록 설정 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/2/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 57162664d6ca3a35696e56088c4e86acadf45371
ms.sourcegitcommit: 223d64a72ec85fe222f5bb10639da729368e6d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955329"
---
# <a name="set-up-ios-and-ipados-user-enrollment-preview"></a>iOS 및 iPadOS 사용자 등록 설정(미리 보기)

Apple의 사용자 등록 프로세스를 사용하여 iOS 및 iPadOS 디바이스를 등록하도록 Intune을 설정할 수 있습니다. 사용자 등록에서는 다른 등록 방법과 달리 관리자에게 간소화된 관리 옵션 하위 집합을 제공합니다.

사용자 등록에서 사용할 수 있는 옵션에 대한 자세한 내용은 [사용자 등록에서 지원하는 작업, 암호 및 기타 옵션](ios-user-enrollment-supported-actions.md)을 참조하세요.

> [!NOTE]
> Intune에서 Apple의 사용자 등록에 대한 지원은 현재 미리 보기 상태입니다.

## <a name="prerequisites"></a>전제 조건
- [MDM(모바일 디바이스 관리) 기관](../fundamentals/mdm-authority-set.md)
- [Apple MDM Push certificate](apple-mdm-push-certificate-get.md)
- [관리 Apple ID](https://support.apple.com/guide/apple-business-manager/mdm1c9622977/web).

## <a name="create-a-user-enrollment-profile-in-intune"></a>Intune에서 사용자 등록 프로필 만들기

등록 프로필에서는 등록 중에 디바이스 그룹에 적용되는 설정을 정의합니다. 

1. Intune 포털에서 **디바이스 등록** > **Apple 등록** > **등록 유형(미리 보기)**  > **프로필 만들기** > **iOS**를 선택합니다. 이 프로필은 iOS 및 iPadOS 최종 사용자가 Apple사의 방법을 통해 등록되지 않은 디바이스에서 사용할 등록 환경을 표시하는 곳입니다. 변경하려면 이 프로필을 만든 후 편집할 수 있습니다.

    ![Apple 등록 프로필 만들기](./media/ios-user-enrollment/create-profile.png)

2. **기본 사항** 페이지에서 관리용 프로필의 **이름** 및 **설명**을 입력합니다. 사용자는 이러한 세부 정보를 볼 수 없습니다. 이 **이름** 필드를 사용하여 Azure Active Directory에 동적 그룹을 만들 수 있습니다. 이 등록 프로필로 디바이스를 할당하기 위해 프로필 이름을 사용하여 enrollmentProfileName 매개 변수를 정의합니다. [Azure Active Directory 동적 그룹](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal#rules-for-devices)에 대해 자세히 알아보세요.

    ![기본 페이지](./media/ios-user-enrollment/basics-page.png)


3. **다음**을 선택합니다.

4. **설정** 페이지에서 등록 유형에 대한 선택권을 사용자에게 부여하는 설정을 선택할 수 있습니다. 또는 기본값을 설정할 수도 있습니다.

    ![설정 페이지](./media/ios-user-enrollment/settings-page.png)

    - 이 프로필의 모든 사용자가 사용자 등록을 사용할 수 있게 하려면 다음 단계를 수행합니다.
        1. **사용자가 디바이스 유형을 선택해야 함**에서 **구성되지 않음**을 선택합니다.
        2. **기본 등록 유형**에서 **사용자 등록**을 선택합니다.
    - 이 프로필의 모든 사용자가 디바이스 등록을 사용할 수 있게 하려면 다음 단계를 수행합니다.
        1. **사용자가 디바이스 유형을 선택해야 함**에서 **구성되지 않음**을 선택합니다.
        2. **기본 등록 유형**에서 **디바이스 등록**을 선택합니다.
    - 이 그룹의 모든 사용자가 사용할 등록 유형을 선택할 수 있게 하려면 **사용자가 디바이스 유형을 선택해야 함**에서 **필수**를 선택합니다. 사용자가 디바이스를 등록할 때 **이 디바이스의 소유자임**과 **(회사)이(가) 이 디바이스를 소유함** 중에서 선택할 수 있는 옵션이 제공됩니다. 전자를 선택하는 경우 디바이스는 사용자 등록을 사용해 등록됩니다. 후자를 선택하는 경우 디바이스는 디바이스 등록을 사용해 등록됩니다. 사용자가 **이 디바이스의 소유자임**을 선택하는 경우 전체 디바이스 보호와 작업 관련 앱 및 데이터 보호 중에서 선택할 수 있는 또 다른 옵션이 제공됩니다. 최종 사용자가 자신이 디바이스의 소유자인지 여부를 선택하면 해당 디바이스에 구현되는 등록 유형만 결정됩니다. 사용자가 선택한 내용은 Intune의 디바이스 소유권 특성에 반영되지 않습니다. 사용자 환경에 대해 자세히 알아보려면 [회사 리소스에 대한 IOS 디바이스 액세스 설정](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)을 참조하세요.
    
    > [!NOTE]
    > 다음 알림은 부정확하므로 UI에서 제거됩니다.
    > "사용자 등록에서 대상으로 지정한 디바이스에서 조건부 액세스가 작동하려면 이 사용자 그룹이 Single Sign-on 및 Workplace Join을 사용하도록 설정하는 데 필요한 앱인 Azure Authenticator 앱을 푸시해야 합니다."
    > 관리자는 이 Authenticator 앱을 사용자에게 푸시하는 작업을 수행할 필요가 없습니다. 사용자는 사용자 등록 프로세스를 완료하기 위해 이 Authenticator 앱을 설치하여 이러한 시나리오가 제대로 작동하는지 확인하라는 지침을 회사 포털 내에서 받습니다.

5. **다음**을 선택합니다.

6. **할당** 페이지에서 이 프로필을 할당할 사용자가 포함된 사용자 그룹을 선택합니다. 모든 사용자 또는 특정 그룹에 프로필을 할당하도록 선택할 수 있습니다. 선택한 그룹의 모든 사용자는 위에서 선택한 등록 유형을 사용합니다. 이 기능은 디바이스가 아닌 사용자 ID를 기반으로 하기 때문에 사용자 등록 시나리오에서는 장치 그룹을 지원하지 않습니다. 모든 사용자 또는 특정 그룹에 프로필을 할당하도록 선택할 수 있습니다.

    ![할당 페이지](./media/ios-user-enrollment/assignments-page.png)

7. **다음**을 선택합니다.

8. **검토 및 만들기** 페이지에서 선택 사항을 검토한 다음 **만들기**를 선택하여 사용자에게 프로필을 할당합니다.

    ![할당 페이지](./media/ios-user-enrollment/assignments-page.png)


## <a name="profile-priority"></a>프로필 우선 순위

둘 이상의 등록 유형 프로필을 만든 후에는 이 프로필이 적용되는 우선 순위를 변경할 수 있습니다.

1. Azure Portal의 Intune에서 **디바이스 등록** > **Apple 등록** > **등록 유형(미리 보기)** 을 선택합니다.
2. 목록에서 프로필을 적용하려는 순서대로 끌어서 놓습니다.

사용자에 대한 프로필 간에 충돌이 발생하는 경우 해당 사용자에게 우선 순위가 높은 프로필이 적용됩니다.


