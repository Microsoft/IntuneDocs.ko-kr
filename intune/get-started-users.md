---
title: 사용자 관리 시작
titlesuffix: Microsoft Intune
description: 모바일 디바이스에서 회사 리소스에 액세스할 수 있도록 라이선스 할당하고 Intune에 사용자를 추가합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 22a232de-ab93-44ab-b0b5-d2b3ccb007fe
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4c401110799202bd0c8aafc62bfda6d8827247be
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57234765"
---
# <a name="get-started-managing-users"></a>사용자 관리 시작

조직에 있는 각기 다른 사람에 대해 생각해 보세요. 회사 데이터를 사용하는 이러한 모든 사람은 Intune에서 회사 데이터에 대한 액세스를 관리할 사용자가 필요합니다.

## <a name="how-do-i-create-a-user"></a>사용자를 만들려면 어떻게 하나요?

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Microsoft Intune** 창을 열면 **사용자**를 선택합니다. **모든 사용자** 페이지에서 **+ 새 사용자**를 선택합니다.
4. **이름** 및 **사용자 이름**과 같은 사용자 정보를 입력합니다. 사용자 이름의 도메인 이름 부분은 다음 도메인 중 하나여야 합니다.
    - 초기 기본 도메인 이름은 'contoso.onmicrosoft.com' 도메인 이름 또는
    - 확인된 비 연합 도메인 이름(예: “contoso.com.”)
5. **그룹**에서 사용자를 추가할 [그룹](get-started-groups.md)을 선택합니다.
6. 테스트 디바이스에 로그인하는 데 사용할 수 있도록 자동으로 생성된 사용자 암호를 저장합니다. 기억할 수 있는 일반적인 암호로 변경할 수 있도록 이 암호를 사용자에게 제공해야 합니다.
7. **사용자** 창에서 **만들기**를 선택합니다.

## <a name="assigning-licenses-to-users"></a>사용자에게 라이선스 할당

사용자를 만든 후 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)을 사용하여 해당 사용자에게 Intune 라이선스를 할당해야 합니다. 라이선스를 할당하지 않으면 해당 디바이스를 관리에 등록할 수 없습니다.

1. Intune에 로그인하는 데 사용한 것과 동일한 자격 증명으로 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)에 로그인합니다.
2. **사용자** > **활성 사용자**를 선택한 다음 이전에 만든 사용자를 선택합니다.
3. 사용자 정보가 모두 로드될 때까지 잠시 기다려야 할 수도 있습니다. 로드되고 나면 사용자의 **제품 라이선스**에 대해 **편집**을 선택합니다.
4. 사용자에게 **위치**를 할당한 다음 Intune을 **켜기**로 전환합니다.

   > [!NOTE]
   > 그러면 라이선스 중 하나가 이 사용자에 사용됩니다. 라이브 환경을 사용하는 경우 나중에 실제 사용자에게 다시 할당하기 위해 이 라이선스 사용을 해제할 수 있습니다.

5. **저장**을 선택합니다.

## <a name="next-steps"></a>다음 단계

[그룹 시작](get-started-groups.md) - 사용자가 액세스할 수 있는 정책 및 앱을 더 쉽게 관리할 수 있도록 사용자를 그룹으로 구성합니다.
