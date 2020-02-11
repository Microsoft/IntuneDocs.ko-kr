---
title: 디바이스 등록 없이 관리되는 앱용 앱 구성 정책
titleSuffix: Microsoft Intune
description: 디바이스 등록 없이 관리되는 앱용 앱 정책 구성하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: E61C1618-79D0-41A1-B61F-4123FB6672FC
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 06c1119b474d82c4d00db3276179b962ff5b5a44
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755564"
---
# <a name="add-app-configuration-policies-for-managed-apps-without-device-enrollment"></a>디바이스 등록 없이 관리되는 앱용 앱 구성 정책 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

등록되지 않은 디바이스에도 Intune 앱 SDK를 지원하는 관리되는 앱으로 앱 구성 정책을 사용할 수 있습니다. 

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **앱 구성 정책** > **추가** > **관리형 앱**을 선택합니다.
3. **기본 사항** 페이지에서 다음 세부 정보를 설정합니다.
    - **이름**: Azure Portal에 표시되는 프로필의 이름입니다.
    - **설명**: Azure Portal에 표시되는 프로필의 설명입니다.
    - **디바이스 등록 유형**: 관리되는 앱이 선택되어 있습니다.
4. **퍼블릭 앱 선택** 또는 **사용자 지정 앱 선택**을 선택하여 구성할 앱을 선택합니다. 승인했으며 Intune과 동기화한 앱을 앱 목록에서 선택합니다.
5. **다음**을 클릭하여 **설정** 페이지를 표시합니다.
6. 앱에서 지원하는 각 구성 설정의 경우 **이름** 및 **값**을 입력합니다. 

   Intune 앱 SDK를 사용할 수 있는 앱은 키-값 쌍의 구성을 지원합니다. 지원되는 키-값 구성에 대한 자세한 내용은 각 앱의 설명서를 참조하세요. 또한 애플리케이션에 의해 생성된 데이터로 동적으로 채워지는 토큰을 사용할 수 있습니다. 자세한 내용은 [토큰 사용을 위한 구성 값](~/apps/app-configuration-policies-managed-app.md#configuration-values-for-using-tokens)을 참조하세요. iOS용 Outlook 앱 구성 정책 설정에 대한 자세한 내용은 [Microsoft Intune을 사용하여 iOS용 Outlook 앱 구성 관리](https://technet.microsoft.com/library/mt813789(v=exchg.150).aspx)를 참조하세요.

    구성을 삭제하려면 줄임표( **...** )를 선택하고 **삭제**를 선택합니다.  

7. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
8. **포함할 그룹 선택**을 클릭합니다.
9. **포함할 그룹 선택** 창에서 그룹을 선택하고 **선택**을 클릭합니다.
10. **제외할 그룹 선택**을 클릭하여 관련 창을 표시합니다.
11. 제외하려는 그룹을 클릭한 다음, **선택**을 클릭합니다.

    >[!NOTE]
    >그룹을 추가할 때 주어진 할당 유형에 이미 다른 그룹이 포함되어 있으면 다른 포함 할당 유형에 대해 사전 선택되며 변경할 수 없습니다. 따라서 사용된 해당 그룹은 제외된 그룹으로 사용할 수 없습니다.

12. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다.
13. **만들기**를 클릭하여 앱 구성 정책을 Intune에 추가합니다.

## <a name="configuration-values-for-using-tokens"></a>토큰 사용을 위한 구성 값

Intune은 특정 토큰을 생성하여 관리되는 애플리케이션에 보낼 수 있습니다. 예를 들어 앱 구성에서 전자 메일 설정을 사용할 수 있는 경우 토큰을 사용하여 동적 전자 메일을 추가할 수 있습니다. 앱에서 예상되는 이름을 **이름** 필드에 입력한 다음, **값** 필드에 `\{\{mail\}\}`을 입력합니다.

Intune은 구성 설정에서 다음과 같은 토큰 형식을 지원합니다. 다른 사용자 지정 키/값 쌍은 지원되지 않습니다.

- \{\{userprincipalname\}\}—예: John@contoso.com
- \{\{mail\}\}—예: John@contoso.com
- \{\{partialupn\}\}—예: John
- \{\{accountid\}\}—예: fc0dc142-71d8-4b12-bbea-bae2a8514c81
- \{\{userid\}\}—예: 3ec2c00f-b125-4519-acf0-302ac3761822
- \{\{username\}\}—예: John Doe
- \{\{PrimarySMTPAddress\}\}—예: testuser@ad.domain.com

> [!Note]  
> \{\{ 및 \}\} 문자는 토큰 형식에만 사용되며 다른 용도로 사용하면 안 됩니다.

## <a name="next-steps"></a>다음 단계

평소대로 앱을 계속 [할당](apps-deploy.md) 및 [모니터링](apps-monitor.md)합니다.
