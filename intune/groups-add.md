---
title: 사용자 및 디바이스를 구성하기 위한 그룹 추가
titleSuffix: Microsoft Intune
description: 지리, 부서 또는 하드웨어 세부사항별로 사용자 및 디바이스를 구성하는 그룹을 추가합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/13/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f0a2b858-a824-4598-ab81-bdd8e62ac3b3
ms.reviewer: altsou
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bab0a33eee5f4d4856fb9d01d822236d1927a4e3
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071720"
---
# <a name="add-groups-to-organize-users-and-devices"></a>사용자 및 디바이스를 구성하기 위한 그룹 추가
Intune은 Azure AD(Active Directory) 그룹을 사용하여 디바이스 및 사용자를 관리합니다. Intune 관리자의 경우 조직의 요구에 맞게 그룹을 설정할 수 있습니다. 그룹을 만들어 지리적 위치, 부서 또는 하드웨어 특성별로 사용자 또는 디바이스를 구성합니다. 그룹을 사용하여 대규모 작업을 관리합니다. 예를 들어 많은 사용자에 대해 정책을 설정하거나 디바이스 집합에 앱을 배포할 수 있습니다.

다음 유형의 그룹을 추가할 수 있습니다.
- **할당된 그룹** - 수동으로 정적 그룹에 사용자 또는 디바이스를 추가합니다.
- **동적 그룹** - (Azure Active Directory Premium 사용) 단순 또는 고급 규칙을 사용하여 정의된 사용자 또는 디바이스 그룹을 동적으로 작성할 수 있습니다.

## <a name="add-a-new-group"></a>새 그룹 추가

새 그룹을 만들려면 다음 단계를 따르세요.
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **그룹**으로 이동한 다음, **모든 그룹** 창에서 **새로운 그룹**을 선택합니다.
   ![새 그룹이 선택된 Azure Portal의 스크린샷](./media/groups-add-new.png)
4. **그룹 유형**의 경우 다음 옵션 중 하나를 선택합니다.
    - **보안**: 보안 그룹은 사용자 그룹을 구성할 때 유용하게 사용할 수 있는 리소스입니다. 보안 그룹은 누가 어떤 리소스에 액세스할 수 있는지 정의하기 때문에 Intune 사용자 그룹으로 쉽게 변환 가능합니다. Active Directory에서 Azure Active Directory로 동기화되는 보안 그룹이나 Microsoft 365 관리 센터 또는 Azure Portal을 통해 Azure Active Directory에서 직접 만든 보안 그룹은 모두 Intune에서 사용자 그룹을 만드는 데 사용할 수 있습니다.
    - **Office 365**

5. 새 그룹의 **이름** 및 **설명**을 입력하세요. 이러한 속성은 관리 포털에만 나타나고 사용자에게 표시되지 않습니다.

6. **멤버 자격 유형**을 선택합니다.
   - **할당됨** - 수동으로 할당된 구성원으로 그룹을 만듭니다. [Azure AD 할당된 그룹](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)에 대해 자세히 알아봅니다.
   - **동적 사용자** - **동적 쿼리**로 정의된 사용자 그룹을 만듭니다.
   - **동적 디바이스** - **동적 쿼리**로 정의된 디바이스 그룹을 만듭니다.

   ![Intune 그룹 속성의 스크린샷](./media/groups-add-properties.png)

   Azure AD를 통해 멤버 자격을 정의하는 규칙에 따라 동적 그룹을 만들 수 있습니다. [특성 기반 동적 그룹을 만드는 방법](https://docs.microsoft.com/azure/active-directory/active-directory-groups-dynamic-membership-azure-portal)을 알아봅니다.

7. **Office 기능 사용**을 선택하여 사용자 그룹 구성원에게 공유 Office 365 앱에 대한 액세스 권한을 부여할 수 있습니다. [Office 365 그룹](https://support.office.com/article/Learn-about-Office-365-groups-b565caa1-5c40-40ef-9915-60fdb2d97fa2)에 대해 자세히 알아보세요.
8. 새 그룹을 추가하려면 **만들기**를 선택합니다.

## <a name="groups-and-policies"></a>그룹 및 정책

그룹을 만들 때 [정책](device-compliance-get-started.md) 적용 방법을 고려해야 합니다. 예를 들어 디바이스 운영 체제와 관련된 정책과 조직의 서로 다른 역할이나 Active Directory에 이미 정의된 조직 단위와 관련된 정책이 있을 수 있습니다. iOS, Android 및 Windows용의 개별 디바이스 그룹과 함께 각 조직 역할에 대한 사용자 그룹이 있으면 유용합니다.

또한 모든 그룹 및 디바이스에 적용되는 기본 정책을 만들어 조직의 기본 규정 준수 요구 사항을 설정해도 좋을 것입니다. 그러면 가장 넓은 범주의 사용자와 디바이스에 대해 더 구체적인 정책을 만들 수 있습니다. 예를 들어 각 디바이스 운영 체제에 대한 메일 정책을 만들 수 있습니다.



## <a name="see-also"></a>참고 항목
- [Azure Active Directory 그룹을 사용하여 리소스에 대한 액세스 관리](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
- [Azure Portal의 Intune 클래식 그룹](groups-get-started.md)
