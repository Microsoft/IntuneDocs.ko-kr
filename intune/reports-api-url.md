---
title: Intune 데이터 웨어하우스 API 끝점
titlesuffix: Microsoft Intune
description: 참조 항목에서는 Intune 데이터 웨어하우스 API URL 구조를 설명합니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A7A174EC-109D-4BB8-B460-F53AA2D033E6
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 6f99ce2ae7937fe0b90353037e72f453a703dd8c
ms.sourcegitcommit: 49dc405bb26270392ac010d4729ec88dfe1b68e4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/21/2018
ms.locfileid: "34224231"
---
# <a name="intune-data-warehouse-api-endpoint"></a>Intune 데이터 웨어하우스 API 끝점

특정 역할 기반 액세스 제어 및 Azure AD 자격 증명을 포함한 계정으로 Intune 데이터 웨어하우스 API를 사용할 수 있습니다. 그런 다음 OAuth 2.0을 사용하여 Azure AD와 REST 클라이언트를 승인할 수 있습니다. 마지막으로 데이터 웨어하우스 리소스를 호출할 의미 있는 URL을 형성합니다.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="authorization"></a>권한 부여

Azure AD(Azure Active Directory)는 OAuth 2.0을 사용하여 Azure AD 테넌트의 웹 응용 프로그램과 웹 API에 액세스할 권한을 부여할 수 있게 합니다. 이 가이드는 언어와 분리되어 있으며 오픈 소스 라이브러리를 사용하지 않고 HTTP 메시지를 보내고 받는 방법을 설명합니다. OAuth 2.0 인증 코드 흐름은 OAuth 2.0 사양의 [4.1섹션](https://tools.ietf.org/html/rfc6749#section-4.1)에 나와 있습니다.

자세한 내용은 [OAuth 2.0 및 Azure Active Directory를 사용하여 웹 응용 프로그램에 대한 액세스 권한 부여](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)에서 참조하세요.

## <a name="api-url-structure"></a>API URL 구조

데이터 웨어하우스 API 끝점이 각 세트에 대한 엔터티를 읽습니다. API는 **GET** HTTP 동사와 쿼리 옵션 하위 집합을 지원합니다.

Intune URL은 다음 형식을 사용합니다.  
`https://fef.{<strong><em>location</em></strong>}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{<strong><em>entity-collection</em></strong>}?api-version={<strong><em>api-version</em></strong>}`

URL에는 다음 요소가 포함됩니다.

| 요소 | 예제 | 설명 |
|-------------------|------------|--------------------------------------------------------------------------------------------------------------------|
| location | msua06 | 기본 URL은 Azure 포털에서 데이터 웨어하우스 API 블레이드를 보면 알 수 있습니다. |
| entity-collection | 날짜 | OData 엔터티 컬렉션의 이름입니다. 데이터 모델의 컬렉션 및 엔터티에 대한 자세한 내용은 [데이터 모델](reports-ref-data-model.md)을 참조하세요. |
| api-version | 베타 | 버전은 액세스할 API의 버전입니다. 자세한 내용은 [버전](#API-version-information)을 참조하세요. |


## <a name="api-version-information"></a>API 버전 정보

API 최신 버전은 `beta`입니다. 

## <a name="odata-query-options"></a>OData 쿼리 옵션

최신 버전에서는 `$filter, $orderby, $select, $skip,` 및 `$top` OData 쿼리 매개 변수를 지원합니다.
