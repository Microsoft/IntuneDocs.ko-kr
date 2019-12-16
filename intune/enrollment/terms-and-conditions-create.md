---
title: Microsoft Intune에서 사용 약관 설정
titleSuffix: ''
description: Intune용 회사 포털에서 사용자에게 표시되는 사용 약관을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/20/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a3a11a8-9c0c-4334-8c6b-6fea4d0a2efb
ms.reviewer: amyro
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fb5818609763753878fec7a84fd8c19eb154f88
ms.sourcegitcommit: e75718ee6cf93c0e6c915f2776b785fe8db9f7e0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74955442"
---
# <a name="terms-and-conditions-for-user-access"></a>사용자 액세스에 대한 사용 약관

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 관리자는 회사 포털을 사용하여 다음을 수행하기 전에 사용자에게 회사의 사용 약관에 동의하도록 요청할 수 있습니다.
- 디바이스 등록
- 회사 앱 및 이메일 같은 리소스에 액세스.

사용 약관의 구성은 선택 사항입니다.

다양한 언어를 지원하는 경우와 같이 여러 약관 집합을 만들어 다양한 그룹에 할당할 수 있습니다.

두 가지 방법으로 회사 사용 약관을 만들 수 있습니다.
- 이 문서에 설명된 대로 Intune 사용.
- [Azure Active Directory 사용 약관 기능](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou) 사용

자신에게 가장 적합한 방법을 알아보려면 [조직에 적합한 사용 약관 솔루션 선택 블로그 게시물](https://go.microsoft.com/fwlink/?linkid=2010506&clcid=0x409)을 확인해 보세요. 

## <a name="create-terms-and-conditions"></a>사용 약관 만들기
사용 약관을 만들려면 다음 단계를 완료합니다. 표시 이름 및 설명은 관리용이며 약관 속성은 회사 포털의 사용자에게 표시됩니다.

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하고 **테넌트 관리** > **사용 약관**을 선택합니다.
2. **만들기**를 선택합니다.
3. **기본** 페이지에서 다음 정보를 지정합니다.

   - **이름**: Azure Portal의 약관 이름입니다. 사용자에게는 이 이름이 표시되지 않습니다.
   - **설명**: Azure Portal에서 이 약관 집합을 식별하는 데 도움이 되는 선택적 세부 정보입니다.

    ![사용 약관의 기본 페이지가 표시된 Azure Portal의 스크린샷](./media/terms-and-conditions-create/terms-basics-page.png)

4. **다음**을 선택하여 **사용 약관** 페이지로 이동하고 다음 정보를 제공합니다.

   - **제목**: 위의 회사 포털에서 사용자에게 표시되는 약관의 이름은 **요약**입니다.
   - **사용 약관**: 사용자에게 표시되며 사용자가 동의하거나 거부해야 하는 사용 약관입니다.
   - **사용 약관 요약** 사용자가 약관에 동의하는 경우 의미를 설명하는 텍스트입니다. 예를 들어 "디바이스를 등록하면 Contoso에서 설정한 사용 약관에 동의하게 됩니다. 계속하기 전에 사용 약관을 주의해서 읽어보세요."가 있습니다.

5. **다음**을 선택하여 **범위 태그** 페이지로 이동합니다.

6. **범위 태그 선택**을 선택하고, 이 사용 약관에 할당할 범위 태그를 선택한 다음 **선택**을 선택합니다. 

7. **다음**을 선택하여 **할당** 페이지로 이동하고 **할당 대상**에서 다음 옵션 중 하나를 선택합니다.
    - **모든 사용자**: 이 사용 약관을 모든 사용자에게 할당하려면 이 옵션을 선택합니다.
    - **그룹 선택**: **포함할 그룹 선택**을 선택하여 식별한 그룹의 모든 사용자에게 이 사용 약관을 할당하려면 이 옵션을 선택합니다.

8. **다음** > **만들기**를 선택합니다.

## <a name="see-how-terms-are-displayed-to-your-users"></a>약관이 사용자에게 표시되는 방식 확인
다음 예제에는 관리 콘솔과 회사 포털에 **제목** 및 **사용 약관 요약**이 표시되어 있습니다.

![관리 콘솔과 회사 포털에 표시된 제목 및 사용 약관 요약의 스크린샷](./media/terms-and-conditions-create/terms-summary-terms.png)

다음 예제에는 관리 콘솔과 회사 포털에 사용 약관이 표시되어 있습니다.

![관리 콘솔과 회사 포털에 표시된 사용 약관의 스크린샷](./media/terms-and-conditions-create/terms-properties-terms.png)


## <a name="monitor-terms-and-conditions"></a>사용 약관 모니터링

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하고 **테넌트 관리** > **사용 약관**을 선택합니다.
2. 사용 약관 목록에서 동의를 확인할 약관을 선택하고 **승인 보고**를 선택합니다.

## <a name="work-with-multiple-versions-of-terms-and-conditions"></a>여러 버전의 사용 약관 사용
사용 약관을 편집하고 버전을 관리할 수 있습니다. 사용 약관에 대대적인 변경 사항이 있을 때마다 다음을 수행해야 합니다.
- 버전 번호 올리기
- 사용자에게 새로운 사용 약관에 대한 동의 요청

오타 수정 또는 서식 변경 등을 수행하는 경우에는 현재 버전 번호를 유지합니다.

1. [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인하고 **테넌트 관리** > **사용 약관**을 선택하고 수정하려는 사용 약관을 선택한 다음 **속성**을 선택합니다.

2. **속성** 창에서 **사용 약관**을 선택하고 필요에 따라 **제목**, **사용 약관 요약**, **사용 약관**을 수정합니다. 내용을 변경하여 사용자가 새로운 사용 약관에 다시 동의해야 하는 경우 **사용자가 다시 수락하고 버전 번호를 증가시켜야 합니다.** 를 선택합니다.

3. **확인** > **저장**을 선택합니다.

사용자는 업데이트된 사용 약관에 한 번만 동의하면 됩니다. 즉, 여러 디바이스를 소유한 사용자가 각 디바이스에서 약관에 동의할 필요가 없습니다.
