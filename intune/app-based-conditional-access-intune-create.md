---
title: Intune을 사용한 앱 기반 조건부 액세스 정책 설정
description: Intune을 사용한 앱 기반 조건부 액세스 정책 설정을 만드는 방법을 알아봅니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 05/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c505e881fe06d6f4da217533d0507731ac22a29f
ms.sourcegitcommit: 698bd1488be3a269bb88c077eb8d99df6e552a9a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34285027"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Intune을 사용한 앱 기반 조건부 액세스 정책 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 승인된 앱 목록에 포함된 앱에 대해 앱 기반 조건부 액세스 정책을 설정하는 방법을 설명합니다. 승인된 앱 목록은 Microsoft에서 테스트한 앱으로 구성됩니다.

> [!IMPORTANT]
> 이 문서는 앱 기반 조건부 액세스 정책을 추가하는 단계를 안내합니다. 승인된 앱 목록에서 SharePoint Online, Microsoft Teams 및 Microsoft Exchange Online 등의 앱을 추가할 때 동일한 단계를 사용할 수 있습니다.

## <a name="create-app-based-conditional-access-policies-in-azure-ad-workload"></a>Azure AD 워크로드에서 앱 기반 조건부 액세스 정책 만들기

IT 관리자는 Azure AD 워크로드에서 앱 기반 조건부 액세스 정책을 만들 수 있습니다. 그러면 Azure와 Intune 워크로드 간을 전환할 필요가 없으므로 편리합니다.

> [!IMPORTANT]
> Intune Azure Portal에서 Azure AD 조건부 액세스 정책을 만들려면 Azure AD Premium 라이선스가 있어야 합니다.

### <a name="to-create-an-app-based-conditional-access-policy"></a>앱 기반 조건부 액세스 정책을 만들려면

> [!IMPORTANT]
> 앱 기반 조건부 액세스 정책을 사용하기 전에 [Intune 앱 보호 정책](app-protection-policies.md)을 앱에 적용해야 합니다.

1. **Intune 대시보드**에서 **조건부 액세스**를 선택합니다.

2. **정책** 창에서 **새 정책**을 선택하여 새 앱 기반 조건부 액세스 정책을 만듭니다.

4. 정책 이름을 입력하고 **할당** 섹션에서 사용 가능한 설정을 구성한 다음 **Access controls**(액세스 제어) 섹션에서 **Grant**(권한 부여)를 선택합니다.

5. **Require approved client app**(승인된 클라이언트 앱 필요)을 선택하고 **선택**을 선택한 다음, **만들기**를 선택하여 새 정책을 저장합니다.

## <a name="next-steps"></a>다음 단계
[최신 인증이 없는 앱 차단](app-modern-authentication-block.md)

### <a name="see-also"></a>참고 항목

[앱 보호 정책을 사용하여 앱 데이터 보호](app-protection-policies.md)
[Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
