---
title: Azure Portal에 조건부 액세스 마이그레이션
titleSuffix: Microsoft Intune
description: 이전에 Intune 클래식 포털에서 만든 조건부 액세스 정책을 Azure Portal에 다시 할당합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 301159ad-5f7e-4fcc-86c7-f72a71701ff4
ms.reviewer: chrisgree
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fe1c9baac31f8709aad3f88dc42c82b35c201027
ms.sourcegitcommit: 364a7dbc7eaa414c7a9c39cf53eb4250e1ad3151
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59569820"
---
# <a name="reassign-conditional-access-policies-from-intune-classic-portal-to-the-azure-portal"></a>Intune 클래식 포털에서 Azure 포털로 조건부 액세스 정책 다시 할당

새 Azure Portal부터 조건부 액세스는 애플리케이션당 여러 정책에 대한 지원과 더 많은 사용자 지정 기능을 제공합니다. Intune 클래식 포털에서 조건부 액세스 정책을 이전에 만든 경우 이 정책을 Azure Portal에 마이그레이션할 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

새 Azure 포털로 이동할 준비가 되었으면 이 항목의 단계에 따라 이전에 Intune 클래식 포털에서 만든 조건부 액세스 정책을 다시 할당할 수 있습니다.

- 나중에 다시 할당하는 데 필요한 설정을 확인할 수 있도록 이전에 만든 조건부 액세스 정책을 수집합니다.

- Azure 포털에서 이러한 정책을 다시 만들려면 이 항목의 단계를 따르세요.

- 새 정책이 Azure Portal에서 예상대로 작동하는지 확인한 후 Intune 클래식 포털에서 조건부 정책을 사용하지 않도록 설정합니다.
<br /><br />
    - Intune 클래식 포털에서 조건부 액세스 정책을 **사용하지 않도록 설정하기 전에** 사용자를 새 정책으로 이동하는 방법을 계획합니다. 다음 두 가지 접근 방법이 있습니다.
<br /><br />
        - **동일한 포함 그룹을 사용하여 Azure 포털에서 만든 정책을 적용하고, Intune 클래식 포털에서 적용된 정책과 함께 사용할 새 예외 그룹을 만듭니다**.
            - 일부 사용자를 클래식 포털에서 지정된 예외 그룹으로 점차적으로 이동합니다. 이렇게 하면 Intune 클래식 포털에서 대상으로 지정한 정책이 적용되지 않습니다. Intune 클래식 포털에서 적용된 정책 외에도 Azure 포털에서 만들고 동일한 사용자 그룹을 대상으로 지정한 정책이 적용됩니다. 
<br /><br />
        - **Azure 포털에서 조건부 액세스 정책의 대상으로 지정할 새 그룹을 만듭니다**. 이 접근 방법을 선택하는 경우 다음을 수행해야 합니다.
            - Intune 클래식 포털에서 조건부 액세스 정책이 대상으로 하는 보안 그룹에서 점차적으로 사용자를 제거합니다.
            - 해당 사용자에 대해 새 정책이 작동하는지 확인한 후 Intune 클래식 포털에서 정책을 사용하지 않도록 설정할 수 있습니다. 
<br /><br />
- Intune 클래식 포털에서 조건부 액세스 정책 설정이 EAS(Exchange ActiveSync)를 사용하도록 구성되어 있는 경우 **Azure 포털에서 EAS 조건부 액세스 정책 설정을 다시 할당**하는 [이 항목의 지침](#reassign-intune-device-based-conditional-access-policies-for-eas-clients)을 참조하세요.

### <a name="to-verify-your-device-based-conditional-access-policies-in-the-intune-classic-portal"></a>Intune 클래식 포털에서 디바이스 기반 조건부 액세스 정책을 확인하려면

1.  [Intune 클래식 포털](https://manage.microsoft.com)로 이동한 다음 자격 증명을 사용하여 로그인합니다.

2.  왼쪽 메뉴에서 **정책**을 선택합니다.

3.  **조건부 액세스**를 선택한 다음 조건부 액세스 정책을 만든 Microsoft 클라우드 서비스(예: Exchange Online, SharePoint Online 등)를 선택합니다.

4.  조건부 액세스 설정을 기록해 두고, Azure 포털에서 동일한 조건부 액세스 정책을 만들 때 이러한 정보를 참조합니다.

### <a name="app-and-device-based-conditional-access-policies-working-together"></a>앱 및 디바이스 기반 조건부 액세스 정책의 연동

Azure 포털의 **Intune 앱 보호** 블레이드를 통해 관리자는 Intune 앱 보호 정책을 지원하는 앱만 회사 리소스에 액세스할 수 있도록 앱 기반 조건부 규칙을 설정할 수 있습니다. 디바이스 기반 조건부 액세스 정책을 사용하여 이러한 앱 기반 조건부 액세스 정책을 겹치도록 선택할 수 있습니다. 디바이스 기반 및 앱 기반 조건부 정책을 결합(논리적 AND)하거나 두 옵션 중 하나를 제공(논리적 OR)할 수 있습니다. 조건부 액세스 정책 요구 사항이 다음과 같은 경우,

- 준수 디바이스 필요 **AND** 승인된 앱 사용.
    - [Azure Active Directory 조건부 액세스 블레이드](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies) 및 [Intune 앱 보호 블레이드](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)를 사용하여 조건부 액세스 정책을 설정해야 합니다.
<br /><br />
- 준수 디바이스 필요 **OR** 승인된 앱 사용.
    - [Intune 클래식 포털](https://manage.microsoft.com) 및 [Intune 앱 보호 블레이드](https://portal.azure.com/#blade/Microsoft_Intune/SummaryBlade/0)를 사용하여 조건부 액세스 정책을 설정해야 합니다.

> [!TIP] 
> 이 항목에서는 Intune 클래식 포털과 Azure 포털의 사용자 환경을 비교하는 스크린샷을 제공합니다.

## <a name="reassign-intune-device-based-conditional-access-policies"></a>Intune 디바이스 기반 조건부 액세스 정책 다시 할당

1. [Azure 포털의 조건부 액세스](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)로 이동한 다음 사용자 자격 증명으로 로그인합니다.

2. **새 정책**을 선택합니다.

3. 정책의 이름을 제공합니다.

4. **할당 섹션**에서 **사용자 및 그룹**을 선택하여 새 조건부 액세스 정책의 대상을 지정합니다.
    
    ![Intune 및 Azure Portal 간 사용자 그룹 UI를 비교하는 이미지](./media/reassign-ca-1.png)

    > [!IMPORTANT] 
    > 클래식 포털에 대해 선택한 사항이 Azure Portal에서 선택한 사항과 일치해야 합니다. 예를 들어, Intune 클래식 포털에서 모든 사용자를 선택한 경우 Azure 포털에서 **모든 사용자**를 선택합니다. 또한 Intune 클래식 포털에서 **그룹 제외** 옵션을 선택한 경우 새 Azure 포털에서도 선택한 그룹을 제외해야 합니다.

5. 그룹을 선택한 후 **선택**, **완료**를 클릭합니다.

6. **할당** 섹션에서 **클라우드 앱**을 선택합니다.

7. **클라우드 앱** 블레이드에서 **앱 선택**을 선택합니다.

8. 새 조건부 액세스 정책을 적용할 앱을 선택한 다음 **선택**을 클릭합니다.

9. **완료**를 클릭합니다.

    ![Intune 및 Azure Portal 간 클라우드 앱 UI 비교 이미지](./media/reassign-ca-3.png)

    > [!TIP] 
    > 정책이 동일한 앱이 여러 개인 경우 Azure 포털에서 단일 정책으로 통합해 보세요.

10. **할당** 섹션에서 **조건**을 선택합니다.

11. **조건** 블레이드에서 **디바이스 플랫폼**을 선택한 다음 적용 가능한 디바이스 플랫폼을 선택합니다.

12. 디바이스 플랫폼 선택을 마쳤으면 **완료**를 두 번 클릭합니다.

    ![Intune 및 Azure Portal의 디바이스 플랫폼 UI를 비교하는 이미지](./media/reassign-ca-4.png)

    > [!TIP] 
    > Intune 클래식 포털에서 개별 플랫폼을 선택한 경우 Azure 포털에서도 개별 플랫폼을 선택합니다.

    > [!NOTE] 
    > 나중에 Windows에 대해 도메인 가입 또는 규격 옵션을 지정할 수 있습니다.

13. **할당** 섹션에서 **조건**을 선택합니다.

14. **조건** 블레이드에서 **클라이언트 앱**을 선택한 다음 적용 가능한 클라이언트 앱을 선택합니다.

15. 클라이언트 앱 선택을 마쳤으면 **완료**를 두 번 클릭합니다.

    ![Intune 및 Azure Portal 간 클라이언트 앱 UI를 비교하는 이미지](./media/reassign-ca-6.png)

16. Intune 클래식 포털에서 브라우저 설정을 선택한 경우 Azure 포털에서 **브라우저**와 **모바일 앱 및 데스크톱 클라이언트**를 둘 다 선택합니다. Intune 클래식 포털에서 브라우저 설정을 선택하지 않은 경우에는 **모바일 앱 및 데스크톱 클라이언트**만 선택합니다. 

17. **액세스 제어** 섹션에서 **부여**를 선택합니다.

18. **액세스 제어 부여**에서 **준수 상태로 표시된 디바이스 필요**를 선택한 다음 **선택**을 클릭합니다.

19. 도메인 가입 Windows 디바이스를 요구하는 정책이 있으며 Intune 등록 및 규격 Windows 디바이스도 허용하는 경우 **도메인 가입 디바이스 필요** 및 **준수 상태로 표시된 디바이스 필요**를 **선택된 컨트롤 중 하나가 필요함**과 함께 선택합니다.

20. Intune 등록 및 규격 Windows 디바이스를 허용하지 않으면 현재 정책에서 Windows 정책을 제외합니다. 그런 다음 **디바이스 플랫폼**을 **Windows**로 설정하여 별도의 정책을 만들고 다른 조건을 위에 설정된 대로 포함한 다음 **액세스 제어 부여**에서 **도메인 가입 디바이스 필요**를 선택합니다.

21. **새** 조건부 액세스 정책 블레이드에서 **정책 사용**을 설정한 다음 **만들기**를 클릭합니다.

    ![Intune과 Azure 간의 조건부 액세스 정책 UI 사용 비교](./media/reassign-ca-11.png)

## <a name="reassign-intune-device-based-conditional-access-policies-for-eas-clients"></a>EAS 클라이언트에 대해 Intune 디바이스 기반 조건부 액세스 정책 다시 할당

Intune 클래식 포털에서 Exchange Online 정책의 일부로 Exchange ActiveSync 설정을 구성한 경우 Azure 포털에서 두 번째 조건부 액세스 정책을 만들어야 합니다.

1. [Azure 포털의 조건부 액세스](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)로 이동한 다음 사용자 자격 증명으로 로그인합니다.

2. **새 정책**을 선택합니다.

3. 정책의 이름을 제공합니다.

4. **할당 섹션**에서 **사용자 및 그룹**을 선택하여 새 조건부 액세스 정책의 대상을 지정합니다.

    ![Azure와 Intune Portal 간 사용자 그룹 UI 비교를 보여주는 이미지](./media/reassign-ca-12.png)

    > [!IMPORTANT] 
    > Azure Portal에 대해 선택한 사항이 Azure Portal에서 선택한 사항과 일치해야 합니다. 예를 들어, Intune 클래식 포털에서 모든 사용자를 선택한 경우 Azure 포털에서 **모든 사용자**를 선택합니다. 또한 Intune 클래식 포털에서 **그룹 제외** 옵션을 선택한 경우 새 Azure 포털에서도 선택한 그룹을 제외해야 합니다.

5. 그룹을 선택한 후 **선택**, **완료**를 클릭합니다.

6. **할당** 섹션에서 **클라우드 앱**을 선택합니다.

7. **클라우드 앱** 블레이드에서 **앱 선택**을 클릭하고 **Exchange Online**을 선택합니다. 그런 다음 **선택**, **완료**를 순서대로 클릭합니다.

    ![Intune 및 Azure Portal 간 클라우드 앱 UI 비교 이미지](./media/reassign-ca-14.png)

    > [!IMPORTANT] 
    > EAS 클라이언트에 대한 조건부 액세스 정책에 다른 클라우드 앱을 포함할 수 없습니다.

8. **조건** 블레이드에서 **클라이언트 앱**을 선택한 다음 적용 가능한 클라이언트 앱을 선택합니다. Intune에서 지원되지 않는 클라이언트를 차단하도록 선택한 경우 **지원되는 플랫폼에만 정책 적용** 옵션을 사용합니다.

    ![Azure와 Intune Portal 간 클라이언트 앱 UI 비교를 보여주는 이미지](./media/reassign-ca-15.png)

9. 클라이언트 앱 선택을 마쳤으면 **완료**를 두 번 클릭합니다.

10. **액세스 제어** 섹션에서 **부여**를 선택합니다.

11. **액세스 제어 부여**에서 **준수 상태로 표시된 디바이스 필요**를 선택한 다음 **선택**을 클릭합니다.

    ![Intune 및 Azure Portal 액세스 허용 UI를 비교하는 이미지](./media/reassign-ca-16.png)

12. **새** 조건부 액세스 정책 블레이드에서 **정책 사용**을 설정한 다음 **만들기**를 클릭합니다.

    ![Intune과 Azure 간의 조건부 액세스 정책 UI 사용 비교](./media/reassign-ca-17.png)

> [!NOTE]
> **디바이스 플랫폼**을 구성하는 경우 정책을 저장하는 작업이 "정책 구성이 지원되지 않습니다."라는 오류로 실패합니다. Exchange ActiveSync는 연결된 디바이스에서 사용 중인 플랫폼을 식별할 수 없습니다. 따라서 Exchange ActiveSync 디바이스에 대한 정책을 만들 때 특정 디바이스 플랫폼을 구성하도록 지원하지 않습니다.

## <a name="disable-conditional-access-policies-in-the-intune-classic-portal"></a>Intune 클래식 포털에서 조건부 액세스 정책 사용 안 함

Azure 포털에서 조건부 액세스 정책을 다시 할당했으면 이전에 Intune 클래식 포털에서 만든 조건부 액세스 정책을 점차적으로 사용하지 않도록 설정해야 합니다. 또한 동일한 보안 그룹을 사용하여 Azure 포털에서 만든 조건부 액세스 정책을 적용해야 할 수도 있습니다.

> [!NOTE]
> Intune 클래식 포털에서 조건부 액세스 정책을 사용하지 않도록 설정하기 전에 이 항목의 시작 부분에 있는 [시작하기 전에](#before-you-begin) 섹션을 참조하세요.

### <a name="to-disable-the-conditional-access-policies"></a>조건부 액세스 정책을 사용하지 않도록 설정하려면

1.  [Intune 클래식 포털](https://manage.microsoft.com)로 이동한 다음 자격 증명을 사용하여 로그인합니다.

2.  왼쪽 메뉴에서 **정책**을 선택합니다.

3.  **조건부 액세스**를 선택한 다음 조건부 액세스 정책을 만든 Microsoft 클라우드 서비스(예: Exchange Online, SharePoint Online 등)를 선택합니다.

4.  **조건부 액세스 정책 사용** 옵션의 선택을 취소하고 **저장**을 클릭합니다.

    ![Intune 클래식 포털에서 조건부 액세스 정책 사용 안 함 이미지](./media/reassign-ca-18.png)

## <a name="see-also"></a>참고 항목

- [Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)
- [Intune을 사용하는 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)
- [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal-get-started)
