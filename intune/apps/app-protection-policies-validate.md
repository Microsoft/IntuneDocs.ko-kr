---
title: 앱 보호 정책 설정의 유효성 검사
titleSuffix: Microsoft Intune
description: 앱 보호 정책이 Microsoft Intune에서 제대로 설정되고 작동하는지 테스트하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.topic: conceptual
ms.technology: ''
ms.assetid: 15f8a838-0b69-412b-a42e-c6edb61f0cae
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9c3e775773ab08721cb3a65858f3d8c8402104f
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563734"
---
# <a name="how-to-validate-your-app-protection-policy-setup-in-microsoft-intune"></a>Microsoft Intune에서 앱 보호 정책 설정의 유효성을 검사하는 방법

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

앱 보호 정책이 제대로 설정되고 작동하는지 유효성을 검사합니다. 이 지침은 Azure Portal의 앱 보호 정책에 적용됩니다.

## <a name="checking-for-symptoms"></a>증상 확인
앱 보호는 데이터 보호 도구이므로 사용자가 문제를 보고할 가능성은 거의 없습니다. 앱 보호 구성에 문제가 있는 경우 사용자는 앱 보호 없이 액세스하고 문제가 있음을 알 수 없으므로 제한 없이 액세스하게 됩니다. 따라서 앱 보호 제한을 의도적으로 테스트할 수 있는 소규모 사용자 그룹에 대해 앱 보호 정책을 파일럿 적용해 앱 보호 구성의 유효성을 검사하는 것이 좋습니다.

## <a name="what-to-check"></a>확인할 사항

테스트 후에 앱 보호 정책 동작이 예상대로 작동하지 않는 경우에는 다음 항목을 확인하세요.

- 사용자에게 앱 보호 사용이 허가되었는지 여부
- 사용자에게 O365 사용이 허가되었는지 여부
- 각 사용자의 앱 보호 앱 상태가 예상대로 나타나는지 여부 앱의 가능한 상태는 **체크 인됨** 및 **체크 인되지 않음**입니다.

### <a name="user-app-protection-status"></a>사용자 앱 보호 상태
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **앱** >  **앱 보호 상태**를 선택하고 **할당된 사용자** 타일을 선택합니다. 
4. **앱 보고** 페이지에서 **사용자 선택**을 선택하여 사용자 및 그룹 목록을 표시합니다. 
5. 목록에서 사용자를 검색한 후 선택하고 **사용자 선택**을 선택합니다. **앱 보고** 창 맨 위에 사용자에게 앱 보호 사용이 허가되었는지 여부가 표시됩니다. 사용자에게 O365 사용이 허가되었는지 여부와 해당 사용자의 모든 디바이스에 대한 앱 상태가 표시되는지 여부를 확인할 수 있습니다.

## <a name="what-to-do"></a>수행할 작업
사용자 상태에 따라 수행할 작업은 다음과 같습니다.

- 사용자에게 앱 보호 사용이 허가되지 않은 경우 해당 사용자에게 [Intune 라이선스](../fundamentals/licenses.md)를 할당합니다.
- O365 용 라이선스가 없는 것을 하는 경우 사용자용 [라이선스](../fundamentals/licenses.md)를 가져옵니다.
- 사용자의 앱이 목록에서 **체크 인되지 않음**으로 표시되는 경우 해당 앱에 대해 [앱 보호 정책](app-protection-policies-validate.md)을 올바르게 구성했는지 확인합니다.
- [앱 보호 정책](app-protection-policies-monitor.md)을 적용할 모든 사용자에게 이러한 조건이 적용되는지 확인합니다.

## <a name="see-also"></a>참고 항목

- [Intune 앱 보호 정책이란?](app-protection-policies.md)
- [Intune을 포함하는 라이선스](../fundamentals/licenses.md)
- [Intune에 디바이스를 등록할 수 있도록 사용자에게 라이선스 할당](../fundamentals/licenses-assign.md)
- [앱 보호 정책 설정의 유효성을 검사하는 방법](app-protection-policies-validate.md)
- [앱 보호 정책을 모니터링하는 방법](app-protection-policies-monitor.md)

