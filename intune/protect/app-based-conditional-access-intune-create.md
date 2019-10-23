---
title: Intune을 사용해 앱 기반 조건부 액세스 정책 설정
titleSuffix: Microsoft Intune
description: Intune을 사용해 앱 기반 조건부 액세스 정책을 만드는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 94e9fcc77f8260c4a63150b5d0aef033677c524a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509681"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Intune을 사용해 앱 기반 조건부 액세스 정책 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

승인된 앱 목록에 포함된 앱에 대해 앱 기반 조건부 액세스 정책을 설정합니다. 승인된 앱 목록은 Microsoft에서 테스트한 앱으로 구성됩니다.

> [!IMPORTANT]
> 이 문서에서는 앱 기반 조건부 액세스 정책을 추가하는 단계를 안내합니다. 승인된 앱 목록에서 SharePoint Online, Microsoft Teams 및 Microsoft Exchange Online 등의 앱을 추가할 때 동일한 단계를 사용할 수 있습니다.

## <a name="create-app-based-conditional-access-policies"></a>앱 기반 조건부 액세스 정책 만들기
조건부 액세스는 Azure AD(Azure Active Directory) 기술입니다. *Intune*에서 액세스되는 조건부 액세스 노드는 *Azure AD*에서 액세스한 것과 동일한 노드입니다. 따라서 정책을 구성하기 위해 Intune 및 Azure AD 간에 전환할 필요가 없습니다.

> [!IMPORTANT]
> Intune 포털에서 조건부 액세스 정책을 만들려면 Azure AD Premium 라이선스가 있어야 합니다.

### <a name="to-create-an-app-based-conditional-access-policy"></a>앱 기반 조건부 액세스 정책을 만들려면

> [!IMPORTANT]
> 먼저 [Intune 앱 보호 정책](../apps/app-protection-policies.md)을 앱에 적용해야 앱 기반 조건부 액세스 정책을 사용할 수 있습니다.

1. **Intune 대시보드**에서 **조건부 액세스**를 선택합니다.

2. **정책** 창에서 **새 정책**을 선택하여 새로운 앱 기반 조건부 액세스 정책을 만듭니다.

4. 정책 이름을 입력하고 **할당** 섹션에서 사용 가능한 설정을 구성한 다음 **Access controls**(액세스 제어) 섹션에서 **Grant**(권한 부여)를 선택합니다.

5. **Require approved client app**(승인된 클라이언트 앱 필요)을 선택하고 **선택**을 선택한 다음, **만들기**를 선택하여 새 정책을 저장합니다.

## <a name="next-steps"></a>다음 단계
[최신 인증이 없는 앱 차단](app-modern-authentication-block.md)

## <a name="see-also"></a>참고 항목

[앱 보호 정책을 사용하여 앱 데이터 보호](../apps/app-protection-policies.md)
[Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
