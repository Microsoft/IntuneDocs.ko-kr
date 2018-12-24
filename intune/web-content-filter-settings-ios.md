---
title: iOS 디바이스에 대한 Microsoft Intune 웹 콘텐츠 필터 설정
titlesuffix: ''
description: iOS를 실행하는 디바이스에서 웹 사이트에 대한 액세스를 허용하거나 차단하는 데 사용할 수 있는 Microsoft Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: af2029fb42cf132ea8df01f1b4152653ed6e4a26
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187891"
---
# <a name="web-content-filter-settings-for-ios-devices"></a>iOS 디바이스에 대한 웹 콘텐츠 필터 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 iOS를 실행하는 디바이스에서 브라우저 URL 액세스를 제어하는 데 사용할 수 있는 Microsoft Intune 설정을 보여줍니다.

다음과 같은 두 가지 방법을 사용하여 URL을 구성할 수 있습니다.

- **URL 구성** - 불경한 언어 또는 성적으로 노골적인 언어와 같은 성인 용어를 검색하는 Apple의 기본 제공 웹 필터를 사용합니다. 이 기능을 통해 각 웹 페이지가 로드될 때 평가되어 부적절한 콘텐츠를 식별하고 차단합니다. 필터로 검사되지 않는 URL 또는 필터 설정에 관계없이 차단되는 URL을 구성할 수도 있습니다.

- **특정 웹 사이트만**(Safari 웹 브라우저만 해당) - 이 URL은 Safari 브라우저의 책갈피에 추가됩니다. 사용자는 이 사이트**만** 방문이 허용됩니다. 다른 사이트에는 액세스할 수 없습니다. 사용자가 액세스할 수 있는 URL의 정확한 목록을 알고 있는 경우에만 이 옵션을 사용합니다.
URL을 지정하지 않으면 최종 사용자는 microsoft.com, microsoft.net 및 apple.com을 제외한 다른 웹 사이트에 액세스할 수 없게 됩니다.

## <a name="get-started"></a>시작

1. 디바이스 기능 페이지에서 **웹 콘텐츠 필터(감독 모드에서만 해당)** 를 선택합니다.
2. **웹 콘텐츠 필터** 창에서 구성할 **필터 형식**을 선택합니다.
    - **구성되지 않음** - 필터링하지 않습니다.
    - **URL 구성**
    - **특정 웹사이트만**
3. 다음으로 사용하는 필터 형식에 따라 다음 절차 중 하나를 따르세요.


## <a name="configure-urls"></a>URL 구성

1. 필요한 경우 **웹 콘텐츠 필터** 페이지에서 다음 설정 중 하나를 선택합니다.
   - **허용된 URL** - **허용된 URL** 페이지에서 허용할 URL을 입력하고(Apple 웹 필터 무시) 각 URL 뒤에서 입력을 선택합니다.
     > [!NOTE]
     > 여기에 지정한 URL은 Apple 웹 필터의 적용을 원하지 않는 URL입니다. 이러한 URL은 허용되는 유일한 웹 사이트의 목록을 나타내지는 않습니다. 원하는 URL인 경우 **특정 웹 사이트만**을 사용합니다.

   - **차단된 URL** - **차단된 URL** 페이지에서 차단할 URL을 입력하고(Apple 웹 필터 설정 상관없음) 각 URL 뒤에서 입력을 선택합니다.
2. 작업을 마쳤으면 **확인**을 클릭합니다.


## <a name="specific-websites-only"></a>특정 웹사이트만

1. **웹 콘텐츠 필터** 페이지에서 허용하려는 각 웹 사이트에 대해 다음 설정을 구성합니다.
    - **URL** - 허용할 웹 사이트의 URL을 입력합니다(예: `https://www.contoso.com`).
    - **책갈피 경로** - 책갈피를 저장할 위치 경로를 입력합니다(예: **/Contoso/Business Apps**). 경로를 추가하지 않으면 디바이스의 기본 책갈피 폴더에 책갈피가 추가됩니다.
    - **제목** - 책갈피에 대한 설명이 포함된 제목을 입력합니다.
2. 각 웹 사이트에 대한 정보를 입력한 후 **추가**를 클릭합니다.
3. 작업을 마쳤으면 **확인**을 클릭합니다.

> [!IMPORTANT]
> 다음 URL은 Intune에서 자동으로 허용됩니다.
> - <www.microsoft.com>
> - <www.microsoft.net>
> - <www.apple.com>

## <a name="finish-up"></a>끝내기

**확인**을 선택하여 **프로필 만들기** 페이지로 돌아간 다음, **만들기**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이제 선택한 그룹에 디바이스 프로필을 할당할 수 있습니다. 자세한 내용은 [디바이스 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.
