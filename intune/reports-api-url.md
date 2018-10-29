---
title: Intune 데이터 웨어하우스 API 엔드포인트
titlesuffix: Microsoft Intune
description: 참조 항목에서는 Intune 데이터 웨어하우스 API URL 구조를 설명합니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/09/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d552ec61d148d0489dc263405eac52448c10f9ef
ms.sourcegitcommit: 24d9ae0396ca410f72cc061a3c4c402835ef32a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49642906"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune 데이터 웨어하우스 API 엔드포인트

특정 역할 기반 액세스 제어 및 Azure AD 자격 증명을 포함한 계정으로 Intune 데이터 웨어하우스 API를 사용할 수 있습니다. 그런 다음 OAuth 2.0을 사용하여 Azure AD와 REST 클라이언트를 승인할 수 있습니다. 마지막으로 데이터 웨어하우스 리소스를 호출할 의미 있는 URL을 형성합니다.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>권한 부여

Azure AD(Azure Active Directory)는 OAuth 2.0을 사용하여 Azure AD 테넌트의 웹 응용 프로그램과 웹 API에 액세스할 권한을 부여할 수 있게 합니다. 이 가이드는 언어에 독립적이며 오픈 소스 라이브러리를 사용하지 않고 HTTP 메시지를 보내고 받는 방법을 설명합니다. OAuth 2.0 인증 코드 흐름은 OAuth 2.0 사양의 [4.1섹션](https://tools.ietf.org/html/rfc6749#section-4.1)에 나와 있습니다.

자세한 내용은 [OAuth 2.0 및 Azure Active Directory를 사용하여 웹 응용 프로그램에 대한 액세스 권한 부여](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)에서 참조하세요.

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
| api-version | 베타 | 버전은 액세스할 API의 버전입니다. 자세한 내용은 [버전](#API-version-information)을 참조하세요. |
| maxhistorydays | 7 | (선택 사항) 검색할 최대 기록 일수입니다. 이 매개 변수는 모든 컬렉션에 제공될 수 있지만 `dateKey`를 해당 키 속성의 일부로 포함하는 컬렉션에만 적용됩니다. 자세한 내용은 [DateKey 범위 필터](reports-api-url.md#datekey-range-filters)를 참조하세요. |

## <a name="api-version-information"></a>API 버전 정보

API 최신 버전은 `beta`입니다. 

## <a name="odata-query-options"></a>OData 쿼리 옵션

최신 버전에서는 `$filter, $orderby, $select, $skip,` 및 `$top` OData 쿼리 매개 변수를 지원합니다.

## <a name="datekey-range-filters"></a>DateKey 범위 필터

`DateKey` 범위 필터는 `dateKey`를 키 속성으로 사용하여 일부 컬렉션에 다운로드할 데이터의 양을 제한하는 데 사용될 수 있습니다. `DateKey` 필터는 다음 `$filter` 쿼리 매개 변수를 지정하여 서비스 성능을 최적화하는 데 사용할 수 있습니다.

1.  `$filter`에 `DateKey`만 사용할 경우 `lt/le/eq/ge/gt` 연산자를 지정할 수 있고, 시작 날짜 및/또는 종료 날짜에 매핑할 수 있는 논리 연산자 `and`를 결합할 수 있습니다.
2.  `maxhistorydays`가 사용자 지정 쿼리 옵션으로 제공됩니다.<br>

## <a name="filter-examples"></a>필터 예제

> [!NOTE]
> 필터 예제에서는 오늘 날짜를 2018년 2월 21일로 가정합니다.

|                             Filter                             |           성능 최적화           |                                          설명                                          |
|:--------------------------------------------------------------:|:--------------------------------------------:|:---------------------------------------------------------------------------------------------:|
|    `maxhistorydays=7`                                            |    전체                                      |    `DateKey`가 20180214와 20180221 사이에 있는 데이터를 반환합니다.                                     |
|    `$filter=DateKey eq 20180214`                                 |    전체                                      |    `DateKey`가 20180214와 동일한 데이터를 반환합니다.                                                    |
|    `$filter=DateKey ge 20180214 and DateKey lt 20180221`         |    전체                                      |    `DateKey`가 20180214와 20180220 사이에 있는 데이터를 반환합니다.                                     |
|    `maxhistorydays=7&$filter=Id gt 1`                            |    부분, Id gt 1이 최적화되지 않음    |    `DateKey`가 20180214와 20180221 사이이고, ID가 1보다 큰 데이터를 반환합니다.             |
|    `maxhistorydays=7&$filter=DateKey eq 20180214`                |    전체                                      |    `DateKey`가 20180214와 동일한 데이터를 반환합니다. `maxhistorydays`는 무시됩니다.                            |
|    `$filter=DateKey eq 20180214 and Id gt 1`                     |    없음                                      |    `DateKey` 범위 지정 필터로 간주되지 않으므로 성능이 향상되지 않습니다.                              |
|    `$filter=DateKey ne 20180214`                                 |    없음                                      |    `DateKey` 범위 지정 필터로 간주되지 않으므로 성능이 향상되지 않습니다.                              |
|    `maxhistorydays=7&$filter=DateKey eq 20180214 and Id gt 1`    |    없음                                      |    `DateKey` 범위 지정 필터로 간주되지 않으므로 성능이 향상되지 않습니다. `maxhistorydays`가 무시됩니다.    |
