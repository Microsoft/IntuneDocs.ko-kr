---
title: Intune 데이터 웨어하우스 API 엔드포인트
titleSuffix: Microsoft Intune
description: 이 참조 항목에서는 Microsoft Intune 데이터 웨어하우스 API URL 구조를 설명합니다. 필터 예제가 제공됩니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 122a7eef56f2850fced164a37b518f650ed2ecdf
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66045866"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune 데이터 웨어하우스 API 엔드포인트

특정 역할 기반 액세스 제어 및 Azure AD 자격 증명을 포함한 계정으로 Intune 데이터 웨어하우스 API를 사용할 수 있습니다. 그런 다음 OAuth 2.0을 사용하여 Azure AD와 REST 클라이언트를 승인할 수 있습니다. 마지막으로 데이터 웨어하우스 리소스를 호출할 의미 있는 URL을 형성합니다.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>권한 부여

Azure AD(Azure Active Directory)는 OAuth 2.0을 사용하여 Azure AD 테넌트의 웹 애플리케이션과 웹 API에 액세스할 권한을 부여할 수 있게 합니다. 이 가이드는 언어에 독립적이며 오픈 소스 라이브러리를 사용하지 않고 HTTP 메시지를 보내고 받는 방법을 설명합니다. OAuth 2.0 인증 코드 흐름은 OAuth 2.0 사양의 [4.1섹션](https://tools.ietf.org/html/rfc6749#section-4.1)에 나와 있습니다.

자세한 내용은 [OAuth 2.0 및 Azure Active Directory를 사용하여 웹 애플리케이션에 대한 액세스 권한 부여](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)에서 참조하세요.

## <a name="api-url-structure"></a>API URL 구조

데이터 웨어하우스 API 엔드포인트가 각 세트에 대한 엔터티를 읽습니다. API는 **GET** HTTP 동사와 쿼리 옵션 하위 집합을 지원합니다.

Intune URL은 다음 형식을 사용합니다.  
`https://fef.{location}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity-collection}?api-version={api-version}`

> [!NOTE]
> 위 URL에서 아래 표에 제공된 세부 정보에 따라 `{location}`, `{entity-collection}` 및 `{api-version}`을 바꿉니다.

URL에는 다음 요소가 포함됩니다.

| 요소 | 예제 | 설명 |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | 기본 URL은 Azure 포털에서 데이터 웨어하우스 API 블레이드를 보면 알 수 있습니다. |
| entity-collection | 날짜 | OData 엔터티 컬렉션의 이름입니다. 데이터 모델의 컬렉션 및 엔터티에 대한 자세한 내용은 [데이터 모델](reports-ref-data-model.md)을 참조하세요. |
| api-version | 베타 | 버전은 액세스할 API의 버전입니다. 자세한 내용은 [버전](reports-api-url.md#api-version-information)을 참조하세요. |
| maxhistorydays | 7 | (선택 사항) 검색할 최대 기록 일수입니다. 이 매개 변수는 모든 컬렉션에 제공될 수 있지만 `dateKey`를 해당 키 속성의 일부로 포함하는 컬렉션에만 적용됩니다. 자세한 내용은 [DateKey 범위 필터](reports-api-url.md#datekey-range-filters)를 참조하세요. |

## <a name="api-version-information"></a>API 버전 정보

이제 쿼리 매개 변수  `api-version=v1.0`을(를) 설정하여 Intune 데이터 웨어하우스의 v1.0 버전을 사용할 수 있습니다. 데이터 웨어하우스에서 컬렉션 업데이트는 가산적이므로 기존 시나리오가 중단되지 않습니다.

베타 버전을 사용하여 데이터 웨어하우스의 최신 기능을 체험해 볼 수 있습니다. 베타 버전을 사용하려면 URL에 쿼리 매개 변수  `api-version=beta`을(를) 포함해야 합니다. 베타 버전에서는 정식 지원되기 전의 기능을 먼저 사용해 볼 수 있습니다. Intune에서 새로운 기능을 추가하면서 베타 버전의 동작과 데이터 계약이 달라질 수 있습니다. 베타 버전의 사용자 지정 코드 또는 보고 도구는 지속적인 업데이트와 함께 중단될 수 있습니다.

## <a name="odata-query-options"></a>OData 쿼리 옵션

최신 버전에서는 `$filter`, `$select`, `$skip,` 및 `$top` OData 쿼리 매개 변수를 지원합니다. `$filter`에서 열이 적용 가능한 경우 `DateKey` 또는 `RowLastModifiedDateTimeUTC`만 지원될 수 있으며 다른 속성은 잘못된 요청을 트리거할 수 있습니다.

## <a name="datekey-range-filters"></a>DateKey 범위 필터

`DateKey` 범위 필터는 `dateKey`를 키 속성으로 사용하여 일부 컬렉션에 다운로드할 데이터의 양을 제한하는 데 사용될 수 있습니다. `DateKey` 필터는 다음 `$filter` 쿼리 매개 변수를 지정하여 서비스 성능을 최적화하는 데 사용할 수 있습니다.

1.  `$filter`에 `DateKey`만 사용할 경우 `lt/le/eq/ge/gt` 연산자를 지정할 수 있고, 시작 날짜 및/또는 종료 날짜에 매핑할 수 있는 논리 연산자 `and`를 결합할 수 있습니다.
2.  `maxhistorydays`가 사용자 지정 쿼리 옵션으로 제공됩니다.<br>

## <a name="filter-examples"></a>필터 예제

> [!NOTE]
> 필터 예제에서는 오늘 날짜를 2019년 2월 21일로 가정합니다.

|                             Filter                             |           성능 최적화           |                                          설명                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    전체                                      |    `DateKey`가 20180214와 20180221 사이에 있는 데이터를 반환합니다.                                     |
|    `$filter=DateKey eq 20180214`                                 |    전체                                      |    `DateKey`가 20180214와 동일한 데이터를 반환합니다.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    전체                                      |    `DateKey`가 20180214와 20180220 사이에 있는 데이터를 반환합니다.                                     |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    전체                                      |    `DateKey`가 20180214와 동일한 데이터를 반환합니다. `maxhistorydays`는 무시됩니다.                            |
|    `$filter=RowLastModifiedDateTimeUTC ge 2018-02-21T23:18:51.3277273Z`                                |    전체                                       |    `RowLastModifiedDateTimeUTC`를 사용한 데이터 변환이 `2018-02-21T23:18:51.3277273Z`보다 크거나 같음                             |
