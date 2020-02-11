---
title: Microsoft Intune에 Windows Phone 8.1 스토어 앱 추가
titleSuffix: ''
description: 이 항목에서는 Microsoft Intune에 Windows Phone 8.1 스토어 앱을 추가하는 방법을 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/22/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d43e0f913020e3e2e8b0ac463d5983447d7c1fa2
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76754952"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Microsoft Intune에 Windows Phone 8.1 스토어 앱 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

앱은 디바이스 또는 사용자 그룹에 할당하기 전에 먼저 앱을 Microsoft Intune에 추가해야 합니다. 

## <a name="add-an-app-to-intune"></a>Intune에 앱 추가
다음 단계를 수행하여 Azure Portal에서 Windows Phone 8.1 스토어 앱을 Intune에 추가할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 사용 가능한 **스토어 앱** 유형 아래에서 **Windows Phone 8.1 스토어 앱**을 선택합니다.
4. **선택**을 클릭합니다.<br>
   **앱 추가** 단계가 표시됩니다.
5. Windows Phone 8.1 스토어 앱의 **앱 정보**를 구성하려면 [Microsoft Store](https://www.microsoft.com/store/apps/windows-phone)로 이동하여 배포하려는 앱을 검색합니다. 앱 페이지를 표시하고 앱 세부 정보를 기록합니다. 
6. **앱 정보** 페이지에서 앱 세부 정보를 추가합니다.
    - **이름**: 회사 포털에 표시하려는 앱 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 앱 이름이 중복될 경우 한 이름만 회사 포털에서 사용자에게 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 이 설명은 회사 포털에서 사용자에게 표시됩니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.
    - **앱 스토어 URL**: 만들려는 앱의 App Store URL을 입력합니다.
    - **범주**: 필요한 경우, 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이렇게 하면 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 사용자가 앱을 찾아볼 때 회사 포털의 기본 페이지에 앱 제품군을 눈에 띄게 표시하려면 이 옵션을 선택합니다.
    - **정보 URL**: 필요에 따라 이 앱에 대한 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인정보취급방침 URL**: 필요에 따라 이 앱에 대한 개인정보 관련 정보를 포함하는 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다.
    - **소유자**: 필요한 경우 이 앱의 소유자 이름을 입력합니다(예: *HR 부서*).
    - **메모**: 선택 사항으로, 이 앱과 연결할 모든 메모를 입력합니다.
    - **로고**: 필요한 경우 앱과 연결할 아이콘을 업로드합니다. 사용자가 회사 포털을 찾아볼 때 이 아이콘이 앱과 함께 표시됩니다.
7. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.
8. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](~/fundamentals/scope-tags.md)을 참조하세요.
9. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
10. 앱의 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](~/fundamentals/groups-add.md)을 참조하세요. 
11. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 앱에 대해 입력한 값과 설정을 검토합니다.
12. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

만든 앱의 **개요 블레이드**가 표시됩니다.


만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)
