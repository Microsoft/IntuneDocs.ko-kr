---
title: Intune 데이터 웨어하우스 사용
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스를 사용하여 기업 모바일 환경에 대한 정보를 제공하는 보고서를 만듭니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/27/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 57019B11-DF9B-4D8A-95FE-254C75398DDE
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b99c9f88fad5dfc53b07db8f01fb92d92ac4bc8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490400"
---
# <a name="use-the-microsoft-intune-data-warehouse"></a>Microsoft Intune 데이터 웨어하우스 사용

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 데이터 웨어하우스를 사용하여 기업 모바일 환경에 대한 정보를 제공하는 보고서를 만듭니다. 예를 들어 일부 보고서는 다음과 같은 내용을 포함합니다.
- 라이선스 구매 최적화를 위한 Intune 등록 사용자 추세
- 모바일 디바이스 상태를 검토하기 위한 앱 및 OS 버전 분석
- 정책 업데이트를 원활하게 롤아웃하기 위한 등록 및 디바이스 규정 준수 추세

## <a name="data-warehouse-benefits"></a>데이터 웨어하우스 혜택

데이터 웨어하우스는 Azure 포털보다 모바일 환경에 대해 더 많은 정보를 제공합니다. Intune 데이터 웨어하우스를 통해 다음에 액세스할 수 있습니다.

- 과거 Intune 데이터
- 일 단위로 새로 고침되는 데이터
- OData 표준을 사용하는 데이터 모델

> [!Note]
> System Center Configuration Manager 및 Microsoft Intune과 함께 공동 관리 MDM(모바일 디바이스 관리)을 사용하는 경우 Configuration Manager에서 데이터를 검색해야 합니다. Intune 데이터 웨어하우스에는 Intune 데이터만 포함됩니다. 사용자 지정 보고서에 대한 Configuration Manager Power BI 대시보드를 사용할 수 있습니다. 자세한 내용은 "[System Center Configuration Manager에 대한 Power BI 솔루션 템플릿 발표]( https://powerbi.microsoft.com/blog/sccm-solution-template)" 및 "[Dynamics 365의 Power BI 콘텐츠](https://docs.microsoft.com/dynamics365/unified-operations/dev-itpro/analytics/power-bi-home-page)"를 참조하세요.

> [!Important]  
> 이제 쿼리 매개 변수  `api-version=v1.0`을(를) 설정하여 Intune 데이터 웨어하우스의 v1.0 버전을 사용할 수 있습니다. 데이터 웨어하우스에서 컬렉션 업데이트는 가산적이므로 기존 시나리오가 중단되지 않습니다.<br><br>
> 베타 버전을 사용하여 데이터 웨어하우스의 최신 기능을 체험해 볼 수 있습니다. 베타 버전을 사용하려면 URL에 쿼리 매개 변수  `api-version=beta`을(를) 포함해야 합니다. 베타 버전에서는 정식 지원되기 전의 기능을 먼저 사용해 볼 수 있습니다. Intune에서 새로운 기능을 추가하면서 베타 버전의 동작과 데이터 계약이 달라질 수 있습니다. 베타 버전의 사용자 지정 코드 또는 보고 도구는 지속적인 업데이트와 함께 중단될 수 있습니다.

## <a name="next-steps"></a>다음 단계

- 링크를 받고 Power BI를 사용하여 정보를 파악합니다. 자세한 내용은 [Power BI를 통해 Intune 데이터 웨어하우스에 연결](reports-proc-get-a-link-powerbi.md)을 참조하세요.
- 링크와 함께 Power BI를 사용하여 사용자 지정 보고서를 만듭니다. 지침은 [Power BI를 사용하여 OData 피드에서 보고서 만들기](reports-proc-create-with-odata.md)를 참조하세요.
- Intune Data Warehouse API, 데이터 모델 및 엔터티 간의 관계에 대해 자세히 알아보려면<!-- , and an example of creating a custom client to retrieve data,--> [Intune Data Warehouse API](reports-nav-intune-data-warehouse.md)를 참조하세요.
