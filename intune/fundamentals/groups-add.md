---
title: 사용자 및 디바이스를 구성하기 위한 그룹 추가
titleSuffix: Microsoft Intune
description: 지리, 부서 또는 하드웨어 세부사항별로 사용자 및 디바이스를 구성하는 그룹을 추가합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe37ac412d01d3032685a0e66827d20e13b0db64
ms.sourcegitcommit: 42183c87b137710b8529049f8710d47127e99900
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75303071"
---
# <a name="add-groups-to-organize-users-and-devices"></a>사용자 및 디바이스를 구성하기 위한 그룹 추가

Intune은 Azure AD(Active Directory) 그룹을 사용하여 디바이스 및 사용자를 관리합니다. Intune 관리자의 경우 조직의 요구에 맞게 그룹을 설정할 수 있습니다. 그룹을 만들어 지리적 위치, 부서 또는 하드웨어 특성별로 사용자 또는 디바이스를 구성합니다. 그룹을 사용하여 대규모 작업을 관리합니다. 예를 들어 많은 사용자에 대해 정책을 설정하거나 디바이스 세트에 앱을 배포할 수 있습니다.

다음 유형의 그룹을 추가할 수 있습니다.

- **할당된 그룹** - 수동으로 정적 그룹에 사용자 또는 디바이스를 추가합니다. 
- **동적 그룹**(Azure AD Premium 필요) - 만든 식에 따라, 사용자 또는 디바이스를 사용자 그룹 또는 디바이스 그룹에 자동으로 추가합니다.

  예를 들어, 제목이 관리자인 사용자를 추가하는 경우 해당 사용자는 **모든 관리자** 사용자 그룹에 자동으로 추가됩니다. 또는 디바이스에 iOS 디바이스 OS 유형이 있는 경우 해당 디바이스는 **모든 iOS 디바이스** 디바이스 그룹에 자동으로 추가됩니다.

## <a name="add-a-new-group"></a>새 그룹 추가

새 그룹을 만들려면 다음 단계를 따르세요.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **그룹** > **새 그룹**을 선택합니다.

   ![새 그룹이 선택된 Azure Portal 스크린샷](./media/groups-add/groups-add-new.png)

3. **그룹 유형**에서 다음 옵션 중 하나를 선택합니다.

    - **보안**: 보안 그룹은 리소스에 액세스할 수 있는 사용자를 정의하며, Intune의 그룹에 권장됩니다. 예를 들어, **모든 Charlotte 직원** 또는 **원격 작업자** 등의 사용자 그룹을 만들 수 있습니다. **모든 iOS 디바이스** 또는 **모든 Windows 10 학생용 디바이스** 등의 디바이스 그룹도 만들 수 있습니다.

        > [!TIP]
        > 만든 사용자 및 그룹은 [Microsoft 365 관리 센터](https://admin.microsoft.com), Azure Active Directory 관리 센터 및 [Azure Portal의 Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에도 표시될 수 있습니다. 조직 테넌트에서 이러한 모든 영역에서 그룹을 만들고 관리할 수 있습니다.
        >
        > 기본 역할이 디바이스 관리인 경우 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)를 사용하는 것이 좋습니다.

    - **Office 365**: 이러한 그룹은 액세스를 제어하고 Office 365 리소스를 공유하도록 디자인되었습니다. 예를 들어, Outlook 받은 편지함 또는 일정을 공유하는 Office 365 그룹을 만들 수 있습니다. 자세한 내용은 [Office 365 그룹에 대해 알아보기](https://support.office.com/article/learn-about-office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)를 참조하세요.

4. 새 그룹의 **그룹 이름** 및 **그룹 설명**을 입력합니다. 다른 사람이 어떤 그룹인지 알 수 있도록 구체적으로 지정하고 정보를 포함하세요.

    예를 들어, 그룹 이름으로 **모든 Windows 10 학생용 디바이스**를 입력하고 그룹 설명으로 **Contoso의 고등학교 9-12학년 학생이 사용하는 모든 Windows 10 디바이스**를 입력합니다.

5. **멤버 자격 유형**을 입력합니다. 옵션은 다음과 같습니다.

    - **할당됨**: 관리자는 이 그룹에 사용자 또는 디바이스를 수동으로 할당하고 사용자 또는 디바이스를 수동으로 제거합니다.
    - **동적 사용자**: 관리자는 멤버 자격 규칙을 만들어 멤버를 자동으로 추가하고 제거합니다.
    - **동적 디바이스**: 관리자는 동적 그룹 규칙을 만들어 디바이스를 자동으로 추가하고 제거합니다.

        ![Intune 그룹 속성의 스크린샷](./media/groups-add/groups-add-properties.png)

    이러한 멤버 자격 형식과 동적 식을 만드는 방법에 대한 자세한 내용은 다음을 참조하세요.

    - [Azure AD를 사용하여 기본 그룹 만들기 및 멤버 추가](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal)
    - [Azure AD의 그룹에 대한 동적 멤버 자격 규칙](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership)

    > [!NOTE]
    > 이 관리 센터에서 사용자 또는 그룹을 만들 때 **Azure Active Directory** 브랜딩이 표시되지 않을 수 있습니다. 그러나 이 기능을 사용하게 될 것입니다.

6. 새 그룹을 추가하려면 **만들기**를 선택합니다. 그룹이 목록에 표시됩니다.

> [!TIP]
> 다음과 같이 만들 수 있는 다른 동적 사용자 및 디바이스 그룹 중 일부를 고려해 보세요.
>
> - Contoso 고등학교의 모든 학생
> - 모든 Android 엔터프라이즈 디바이스
> - 모든 iOS 11 이하 디바이스
> - Marketing
> - 인적 자원
> - 모든 Charlotte 직원
> - 모든 WA 직원

## <a name="groups-and-policies"></a>그룹 및 정책

조직의 리소스에 대한 액세스는 만든 사용자 및 조직에서 제어합니다.

그룹을 만들 때 [준수 정책](../protect/device-compliance-get-started.md) 및 [구성 프로필](../configuration/device-profiles.md)을 적용하는 방법을 고려합니다. 예를 들어, 다음 정책이 있을 수 있습니다.

- 디바이스 운영 체제와 관련된 정책
- 조직의 다른 역할과 관련된 정책
- Active Directory에서 정의한 조직 구성 단위와 관련된 정책

조직의 기본 규정 준수 요구 사항을 만들려면 모든 그룹 및 디바이스에 적용되는 기본 정책을 만들 수 있습니다. 그런 후에 가장 넓은 범주의 사용자와 디바이스에 대해 더 구체적인 정책을 만듭니다. 예를 들어 각 디바이스 운영 체제에 대한 메일 정책을 만들 수 있습니다.

구성 프로필 권장 사항 및 지침은 [사용자 그룹 또는 디바이스 그룹에 정책 할당](../configuration/device-profile-assign.md#user-groups-vs-device-groups) 및 [프로필 권장 사항](../configuration/device-profile-create.md#recommendations)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [Microsoft Intune을 사용하는 RBAC(역할 기반 액세스 제어)](role-based-access-control.md)
- [Azure AD 그룹으로 리소스에 대한 액세스 관리](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
