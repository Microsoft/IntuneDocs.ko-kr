---
title: Microsoft Intune에 Windows Phone 8.1 스토어 앱 추가
titleSuffix: ''
description: Microsoft Intune에 Windows Phone 8.1 스토어 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4a95e575-2c63-4bfc-b9c4-f0a132eef618
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1ae7723e29d23575314fc632c75af01eb9e59f72
ms.sourcegitcommit: 2d1e89fa5fa721e79648e41fde147a035e7b047d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43347663"
---
# <a name="add-windows-phone-81-store-apps-to-microsoft-intune"></a>Microsoft Intune에 Windows Phone 8.1 스토어 앱 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

앱은 장치 또는 사용자 그룹에 할당하기 전에 먼저 앱을 Microsoft Intune에 추가해야 합니다. 

## <a name="add-an-app-to-intune"></a>Intune에 앱 추가
다음 단계를 수행하여 Azure Portal에서 Windows Phone 8.1 스토어 앱을 Intune에 추가할 수 있습니다.

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다.  
    Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 워크로드 창의 **관리** 아래에서 **앱**을 선택합니다.
5. **앱** 창에서 **추가**를 선택합니다.
6. **앱 추가** 창에서 **앱 형식**을 **Windows Phone 8.1**로 선택하고 **앱 정보**를 선택합니다.
7. **앱 정보** 창에서 앱 정보를 추가합니다. 선택한 앱에 따라 이 창의 일부 값이 자동으로 채워질 수 있습니다.
    - **이름**: 회사 포털에 표시되는 앱 이름을 입력합니다. 사용하는 모든 앱 이름이 고유한지 확인합니다. 앱 이름이 중복될 경우 한 이름만 회사 포털에서 사용자에게 표시됩니다.
    - **설명**: 앱에 대한 설명을 입력합니다. 이 설명은 회사 포털에서 사용자에게 표시됩니다.
    - **게시자**: 앱의 게시자 이름을 입력합니다.
    - **앱 스토어 URL**: 만들려는 앱의 앱 스토어 URL을 입력합니다.
    - **범주**: 필요한 경우 기본 제공 앱 범주 중 하나 이상 또는 사용자가 만든 범주를 선택합니다. 이렇게 하면 사용자가 회사 포털을 찾아볼 때 앱을 더 쉽게 찾을 수 있습니다.
    - **회사 포털에서 이 항목을 추천 앱으로 표시**: 이 옵션을 선택하면 사용자가 앱을 찾을 때 회사 포털의 기본 페이지에 앱 제품군이 눈에 띄게 표시됩니다.
    - **정보 URL**: 선택적으로, 이 앱에 대한 정보가 포함된 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개인 정보 URL**: 선택적으로, 이 앱에 대한 개인 정보 관련 정보가 포함된 웹 사이트의 URL을 입력합니다. URL은 회사 포털에서 사용자에게 표시됩니다.
    - **개발자**: 선택적으로, 앱 개발자의 이름을 입력합니다.
    - **소유자**: 필요한 경우 이 앱의 소유자 이름을 입력합니다(예: *HR 부서*).
    - **메모**: 선택 사항으로, 이 앱과 연결할 모든 메모를 입력합니다.
    - **아이콘**: 필요한 경우 앱과 연결할 아이콘을 업로드합니다. 사용자가 회사 포털을 찾아볼 때 이 아이콘이 앱과 함께 표시됩니다.
8. **확인**을 선택합니다.
9. **추가**를 선택합니다.

만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)
