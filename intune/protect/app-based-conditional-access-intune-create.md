---
title: Intune을 사용해 앱 기반 조건부 액세스 정책 설정
titleSuffix: Microsoft Intune
description: Intune을 사용해 앱 기반 조건부 액세스 정책을 만드는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d1693515-de18-4553-91ef-801976cd3ec7
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 465f8b0001e5e2a049a3ffe12469bdb5057854ec
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73712842"
---
# <a name="set-up-app-based-conditional-access-policies-with-intune"></a>Intune을 사용해 앱 기반 조건부 액세스 정책 설정

승인된 앱 목록에 포함된 앱에 대해 앱 기반 조건부 액세스 정책을 설정합니다. 승인된 앱 목록은 Microsoft에서 테스트한 앱으로 구성됩니다.

먼저 [Intune 앱 보호 정책](../apps/app-protection-policies.md)을 앱에 적용해야 앱 기반 조건부 액세스 정책을 사용할 수 있습니다.

> [!IMPORTANT]
> 이 문서에서는 앱 기반 조건부 액세스 정책을 추가하는 단계를 안내합니다. 승인된 앱 목록에서 SharePoint Online, Microsoft Teams 및 Microsoft Exchange Online 등의 앱을 추가할 때 동일한 단계를 사용할 수 있습니다.

## <a name="create-app-based-conditional-access-policies"></a>앱 기반 조건부 액세스 정책 만들기

조건부 액세스는 Azure AD(Azure Active Directory) 기술입니다. *Intune*에서 액세스하는 조건부 액세스 노드는 *Azure AD*에서 액세스하는 것과 동일한 노드입니다. 동일한 노드이므로 정책을 구성하기 위해 Intune 및 Azure AD 간에 전환할 필요가 없습니다.

Microsoft Endpoint Manager 관리 센터에서 조건부 액세스 정책을 만들려면 먼저 Azure AD Premium 라이선스가 있어야 합니다.

### <a name="to-create-an-app-based-conditional-access-policy"></a>앱 기반 조건부 액세스 정책을 만들려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **엔드포인트 보안** > **조건부 액세스** > **새 정책**을 선택합니다.

3. 정책 **이름**을 입력하고 *할당*에서 **사용자 및 그룹**을 선택합니다. 포함 또는 제외 옵션을 사용하여 정책에 대한 그룹을 추가하고 **완료**를 선택합니다.

4. **클라우드 앱 또는 작업**을 선택한 다음, 보호할 앱을 선택합니다. 예를 들어 **앱 선택**을 선택한 다음 **Office 365 SharePoint Online** 및 **Office 365 Exchange Online**을 선택합니다.

   **완료**를 선택하여 변경 내용을 저장합니다.

5. **조건** > **클라이언트 앱**을 선택하여 앱과 브라우저에 정책을 적용합니다. 예를 들어 **예**를 선택한 다음 **브라우저**와 **모바일 앱 및 데스크톱 클라이언트**를 사용하도록 설정합니다.

   **완료**를 선택하여 변경 내용을 저장합니다.

6. *액세스 제어*에서 **권한 부여**를 선택하여 디바이스 준수에 따라 조건부 액세스를 적용합니다. 예를 들어 **액세스 권한 부여** > **디바이스가 규격으로 표시되어야 함**을 선택합니다.

   **선택**을 선택하여 변경 내용을 저장합니다.

7. **정책 사용**에서 **On**을 선택한 다음, **만들기**를 선택하여 변경 내용을 저장합니다.





## <a name="next-steps"></a>다음 단계
[최신 인증이 없는 앱 차단](app-modern-authentication-block.md)

## <a name="see-also"></a>참고 항목

[앱 보호 정책을 사용하여 앱 데이터 보호](../apps/app-protection-policies.md)
[Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
