---
title: 조건부 액세스로 최종 사용자 도입 촉진
titleSuffix: Microsoft Intune
description: 조건부 액세스를 사용하여 Microsoft Intune에서 등록을 촉진하는 방법에 대해 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c2d7ce3f-fe97-4044-ad9e-25ac8fa301c9
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: a37d6dac24049a10b5abaed41a44c0c391b095e6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050469"
---
# <a name="drive-end-user-adoption-with-conditional-access-in-microsoft-intune"></a>Microsoft Intune에서 조건부 액세스로 최종 사용자 도입 촉진

등록 취소된 디바이스에 대한 메일 차단과 같은 조건부 액세스 기능을 Intune에서 사용하도록 설정하면 등록 및 준수를 촉진하는 데 도움이 될 수 있지만, 마이그레이션 성공에 필요한 과정은 아닙니다. 마이그레이션 도입 목표 및 보안 요구 사항에서 성공 여부를 결정해야 합니다.

## <a name="migration-campaign-with-conditional-access"></a>조건부 액세스로 마이그레이션 캠페인

다음은 조건부 액세스로 마이그레이션 캠페인을 강화하는 일반적인 방법입니다.

1.  모든 사용자에 적용할 조건부 액세스 규칙을 설정하지만, 특별히 이전 MDM 공급자에서 마이그레이션해야 하는 사용자는 제외합니다. 모든 조건부 액세스 제외 사용자가 포함된 Azure AD 사용자 그룹을 만들 수 있습니다.

2.  사용자 마이그레이션 시 조건부 액세스 제외 그룹에서 해당 사용자를 제거합니다.

3.  마이그레이션이 완료되면 Intune에서 액세스를 허용하지 않는 한 기본적으로 차단하도록 모든 조건부 액세스 정책을 구성합니다.

### <a name="advantages"></a>장점

-   새 사용자 계정 또는 이전 솔루션으로 관리되지 않는 사용자 계정에 대한 액세스 제어를 제공합니다.

-   이전 솔루션의 사용자가 마이그레이션할 수 있도록 유예 기간을 제공합니다.

-   생산성 저하를 최소화합니다.

### <a name="disadvantages"></a>단점

-   이전 솔루션의 사용자가 조건부 액세스를 사용할 수 있게 될 때까지 해당 사용자는 관리되지 않는 디바이스를 사용하여 리소스에 액세스할 수 있습니다.


이는 여러 방법 중 하나입니다. 모든 단계에서 등록 지시를 받은 이후까지 모든 조건부 액세스를 지연하는 간단한 프로세스를 선택하거나 처음부터 조건부 액세스를 적용하고 모든 액세스에 대한 완전한 준수를 요구하는 엄격한 프로세스를 선택할 수 있습니다.

-   [조건부 액세스](conditional-access.md)에 대해 자세히 알아보세요.

## <a name="task-list-for-conditional-access"></a>조건부 액세스에 대한 작업 목록

### <a name="task-1-decide-how-you-are-going-to-implement-conditional-access"></a>태스크 1: 조건부 액세스를 구현할 방법 결정

[조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md).

### <a name="task-2-set-up-intune-conditional-access"></a>태스크 2: Intune 조건부 액세스 설정

다음 옵션 중 하나를 선택합니다.

-   [Azure Active Directory에서 조건부 액세스 구성](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

-   [Intune과 함께 온-프레미스 Exchange 커넥터 설치](exchange-connector-install.md)

-   [Exchange Online에 대한 앱 기반 조건부 액세스 정책 설정](app-based-conditional-access-intune-create.md)

-   [SharePoint Online에 대한 앱 기반 조건부 액세스 정책 설정](app-based-conditional-access-intune-create.md)

-   [최신 인증(ADAL)을 사용하지 않는 앱 차단](app-modern-authentication-block.md)

## <a name="next-steps"></a>다음 단계

[일반적인 마이그레이션 주기](migration-guide-cycle.md)에 대해 자세히 알아보세요.
