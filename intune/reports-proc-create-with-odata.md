---
title: Power BI를 사용하여 OData 피드에서 보고서 만들기
titlesuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API의 대화형 필터와 함께 Power BI Desktop을 사용하여 트리맵 시각화를 만듭니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: A2C8A336-29D3-47DF-BB4A-62748339391D
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 9c93554fd6750459aacc154165e7a58e160534fb
ms.sourcegitcommit: 1c9ef5cfac2fc024528d2cfc9d590fa68dd58080
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53429715"
---
# <a name="create-a-report-from-the-odata-feed-with-power-bi"></a>Power BI를 사용하여 OData 피드에서 보고서 만들기

이 아티클에서는 대화형 필터와 함께 Power BI Desktop을 사용하여 트리맵 시각화를 만드는 방법을 설명합니다. 예를 들어 CFO는 전체적인 디바이스 분포에서 회사 소유 디바이스와 개인 디바이스를 대조한 결과를 원할 수 있습니다. 트리맵은 전체 디바이스 유형 수에 대한 정보를 제공합니다. 회사 소유이거나 개인 소유인 iOS, Android 및 Windows 디바이스의 수를 검토할 수 있습니다.

### <a name="overview-of-creating-the-chart"></a>차트 만들기 개요

이 차트를 만들려면 다음을 수행해야 합니다.
1. 아직 없는 경우 Power BI Desktop을 설치합니다.
2. Intune 데이터 웨어하우스 데이터 모델에 연결하고 모델의 현재 데이터를 검색합니다.
3. 데이터 모델 관계를 만들거나 관리합니다.
4. **devices** 테이블의 데이터를 사용하여 차트를 만듭니다.
5. 대화형 필터를 만듭니다.
6. 완성된 차트를 봅니다.

### <a name="a-note-about-tables-and-entities"></a>테이블과 엔터티에 대한 참고 사항

Power BI의 테이블에서 작업합니다. 테이블에는 데이터 필드가 있습니다. 각 데이터 필드에는 데이터 형식이 있습니다. 필드에는 데이터 형식의 데이터만 포함될 수 있습니다. 데이터 형식은 숫자, 텍스트, 날짜 등입니다. Power BI의 테이블은 모델을 로드할 때 테넌트의 최근 기록 데이터로 채워집니다. 특정 데이터는 시간에 따라 변경되더라도 기본 데이터 모델이 업데이트되지 않으면 테이블 구조가 변경되지 않습니다.

_엔터티_ 및 _테이블_이라는 용어를 사용하면 혼란스러울 수 있습니다. 데이터 모델은 OData 피드를 통해 액세스할 수 있습니다. OData의 유니버스에서 Power BI의 테이블이라고 하는 컨테이너를 엔터티라고 합니다. 이 두 용어는 모두 데이터를 보유하는 것과 동일한 의미를 나타냅니다.

## <a name="install-power-bi-desktop"></a>Power BI Desktop 설치

Power BI Desktop의 최신 버전을 설치합니다. Power BI Desktop은 [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)에서 다운로드할 수 있습니다.

## <a name="connect-to-the-odata-feed-for-the-intune-data-warehouse-for-your-tenant"></a>테넌트에 대한 Intune 데이터 웨어하우스의 OData 피드에 연결합니다.

> [!Note]  
> Intune에서는 **보고서**에 대한 권한이 필요합니다. 자세한 내용은 [권한 부여](reports-api-url.md)를 참조하세요.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune 데이터 웨어하우스** 창을 엽니다.
4. 사용자 지정 피드 URL을 복사합니다. 예를 들어 `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`를 구성할 수 있습니다.
5. Power BI Desktop을 엽니다.
6. **데이터 가져오기** > **Odata 피드**를 차례로 선택합니다.
7. **OData 피드** 창의 URL 상자에 사용자 지정 피드 URL을 붙여넣습니다.
8. **기본**을 선택합니다.

    ![OData 피드](media/reports-create-01-odatafeed.png)

9. **확인**을 선택합니다.
10. **조직 계정**을 선택한 다음 Intune 자격 증명으로 로그인합니다.

    ![조직 계정 자격 증명](media/reports-create-02-org-account.png)

11. **연결**을 선택합니다. 탐색기가 열리고 Intune 데이터 웨어하우스에 있는 테이블 목록이 표시됩니다.

    ![탐색기](media/reports-create-02-loadentities.png)

12. **devices** 및 **ownerTypes** 테이블을 선택합니다.  **로드**를 선택합니다. Power BI에서 데이터를 모델에 로드합니다.

## <a name="create-a-relationship"></a>관계 만들기

여러 테이블을 가져와서 단일 테이블의 데이터뿐만 아니라 여러 테이블의 관련 데이터도 분석할 수 있습니다.  PowerBI에는 관계를 찾고 만들 수 있는 **자동 검색**이라는 기능이 있습니다. 데이터 웨어하우스의 테이블은 PowerBI의 자동 검색 기능을 사용하도록 빌드되어 있습니다. 그러나 PowerBI에서 자동으로 관계를 찾지 않더라도 관계는 계속 관리할 수 있습니다.

![관계 관리](media/reports-create-03-managerelationships.png)

1. **관계 관리**를 선택합니다.
2. PowerBI에서 아직 관계를 검색하지 못했으면 **자동 검색 중...** 을 선택합니다.

관계는 [대상] 열에 대한 [원본] 열에 표시됩니다. 이 예에서 **devices** 테이블의 **ownerTypeKey** 데이터 필드는 **ownerTypes** 테이블의 **ownerTypeKey** 데이터 필드에 연결됩니다. 관계를 사용하여 **devices** 테이블에서 디바이스 유형 코드의 일반 이름을 찾습니다.

## <a name="create-a-treemap-visualization"></a>트리맵 시각화 만들기

트리맵 차트에서 계층적 데이터는 상자 내의 상자로 표시됩니다. 계층 구조의 각 분기는 하위 분기를 표시하는 더 작은 상자가 포함된 상자입니다. Power BI Desktop을 사용하여 Intune 데이터의 트리맵을 만들 수 있습니다.

![시각화 > 트리맵](media/reports-create-03-treemap.png)

1. 차트 종류를 선택합니다. **트리맵**을 선택합니다.
2. 데이터 모델에서 **devices** 테이블을 찾습니다.
3. **devices 테이블**을 펼치고, **필드** 패널에서 **제조업체** 데이터 필드를 선택합니다.
4. **제조업체** 데이터 필드를 보고서 캔버스의 트리맵 차트로 끕니다.
5. **devices** 테이블의 **deviceKey** 데이터 필드를 **시각화** 창 아래의 **값** 섹션으로 끌어서 **여기로 데이터 필드 끌기** 레이블이 있는 상자에 놓습니다.  

이제 조직 내의 디바이스 제조업체의 분포를 보여 주는 시각적 개체가 준비되었습니다.

![데이터가 있는 트리맵](media/reports-create-06-treemapwdata.png)

## <a name="add-a-filter"></a>필터 추가

앱을 사용하여 추가 질문에 답변할 수 있도록 트리맵에 필터를 추가할 수 있습니다.


1. 필터를 추가하려면 보고서 캔버스를 선택하고 **시각화** 아래의 **슬라이서 아이콘**(![데이터 모델 및 지원되는 관계가 있는 트리 맵](media/reports-create-slicer.png))을 선택합니다.
2. **ownerTypes** 테이블을 찾고 **시각화** 패널의 **필터** 섹션 아래에서 **ownerTypeName** 데이터 필드를 끕니다.  

   devices 테이블 아래에는 디바이스가 회사 소유인지 또는 개인 소유인지 여부를 나타내는 코드가 포함된 **OwnerTypeKey**라고 하는 데이터 필드가 있습니다. 이 필터에 친숙한 이름을 표시하려면 **ownerTypes** 테이블을 찾고 **ownerTypeName**을 끕니다. 이 예는 데이터 모델에서 테이블 간의 관계를 지원하는 방법을 보여줍니다.

![필터가 있는 트리맵](media/reports-create-08_ownertype.png)

이제 회사 소유 디바이스와 개인 소유 디바이스 간에 이동하여 사용할 수 있는 대화형 필터가 준비되었습니다. 이 필터를 사용하여 분포가 변경되는 상태를 확인합니다.

1. **회사**를 선택하여 회사 소유 디바이스의 분포를 확인합니다.
2. **개인**을 선택하여 개인 소유 디바이스를 확인합니다.

## <a name="next-steps"></a>다음 단계

 - Power BI 설명서에서 Power BI Desktop의 [관계 만들기 및 관리](https://powerbi.microsoft.com/documentation/powerbi-desktop-create-and-manage-relationships/)에 대해 자세히 알아봅니다.
 - [Intune 데이터 웨어하우스 모델](https://docs.microsoft.com/intune/reports-ref-data-model)을 참조합니다.
