---
title: Power BI를 통해 데이터 웨어하우스에 연결
titleSuffix: Microsoft Intune
description: Microsoft Intune 테넌트에 대해 동적으로 생성된 보고서인 인터랙티브 다운로드를 위해 Microsoft Power BI용 파일을 다운로드할 수 있습니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/07/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8d7a5f67dfd8f7256559cb54d873ed48205ad751
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490417"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Power BI를 통해 데이터 웨어하우스에 연결

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Power BI Compliance 앱을 사용하여 Intune 테넌트에 대해 동적으로 생성된 대화형 보고서를 로드할 수 있습니다. 또한 OData 링크를 사용하여 Power BI에 테넌트 데이터를 로드할 수 있습니다. Intune은 다음 샘플 보고서 및 관련 차트를 볼 수 있도록 테넌트에 대한 연결 설정을 제공합니다.  

- 디바이스
- 등록
- 앱 보호 정책
- 준수 정책
- 디바이스 구성 프로필
- 소프트웨어 업데이트
- 디바이스 인벤토리 로그

등록, 규정 준수, 디바이스 구성 프로필, 소프트웨어 업데이트에 대한 트렌드도 하이라이트되어 있습니다. 샘플 차트와 보고서는 사용하기 쉬운 필터를 캔버스에 적용합니다. 고급 필터를 사용하려면 Power BI Desktop의 **필터** 창을 확인하세요.

다음 단계는 Power BI 파일을 다운로드하고 Power BI를 통해 OData 링크를 사용하는 방법을 설명합니다.

[!INCLUDE [reports-credential-reqs](../includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Power BI 설치

[Power BI Desktop](https://aka.ms/intune/datawarehouseapi/installpowerbi)의 최신 버전을 설치합니다. 자세한 내용은 [Power BI Desktop](https://powerbi.microsoft.com/desktop)을 참조하세요.

## <a name="load-the-data-and-reports-using-the-power-bi-intune-compliance-data-warehouse-app"></a>Power BI Intune Compliance Data Warehouse App을 사용하여 데이터 및 보고서 로드

Power BI [Intune Compliance(Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 앱에는 테넌트에 대한 정보와 Data Warehouse 데이터 모델을 기반으로 하는 미리 빌드된 보고서 세트가 포함되어 있습니다.

1. [Intune Compliance(Data Warehouse)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 앱의 **AppSource** 페이지로 이동하여 설치 프로세스를 시작합니다.
2. **지금 가져오기** 단추를 클릭 한 다음 **계속**을 클릭 합니다.
3. Power BI 앱을 설치 하 라는 메시지가 표시 되 면 **설치**를 클릭 합니다.
4. 설치가 완료 되 면 **Intune 준수 (데이터 웨어하우스)** 앱 타일을 클릭 합니다.
5. **연결** 단추를 클릭합니다. **Intune Compliance(Data Warehouse)에 연결** 대화 상자가 표시됩니다.
6. **로그인** 단추를 클릭합니다.
7. 보려는 보고서가 있는 테넌트에 대한 Intune Data Warehous에 액세스할 수 있는 사용자 계정으로 로그인합니다.
8. 포함 된 대시보드를 보려면 **대시보드** 탭을 클릭 한 다음 **준수 개요** 대시보드를 클릭 합니다.
9. 사용 가능한 모든 보고서를 보려면 **보고서** 탭을 클릭 한 다음 **준수** v1.0 보고서를 클릭 합니다. 아래쪽에 있는 탭을 클릭 하 여 보고서 페이지를 탐색 합니다.
10. 나중에 이러한 보고서로 쉽게 다시 이동하려면 **Compliance V1.0** 보고서 옆에 있는 별표를 클릭합니다. 그러면 보고서가 Power BI 즐겨찾기에 추가됩니다.

또는 Intune 포털에서 앱을 설치할 수 있습니다.

1. Azure 포털에 로그인하고 **모니터링 + 관리** > **Intune**을 선택합니다. Intune에 대한 리소스를 검색할 수도 있습니다.
2. **Intune Data Warehouse 설정** 블레이드를 엽니다.
3. **Power BI 앱 가져오기**를 선택하면 브라우저에서 테넌트에 대해 미리 작성된 Power BI 보고서에 액세스하여 공유할 수 있습니다.
4. 위의 2-10단계를 수행합니다.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>OData 링크를 사용하여 Power BI에서 데이터 로드

클라이언트가 Azure AD에 인증되면 OData URL이 데이터 모델을 보고하는 클라이언트에 노출하는 데이터 웨어하우스 API의 RESTful 엔드포인트에 연결합니다. 다음 지침에 따라 Power BI Desktop을 사용하여 연결하고 직접 보고서를 만드세요. Power BI Desktop으로 제한되지 않으므로 자주 사용하는 다른 분석 도구를 OData URL과 사용할 수도 있습니다. 단 클라이언트가 OAUTH2.0 인증 및 OData v4.0 표준을 지원해야 합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. 개요 블레이드의 오른쪽에 있는 **기타 작업** 섹션에서 **Intune 데이터 웨어하우스 설정** 을 클릭 합니다. **Intune 데이터 웨어하우스** 블레이드가 표시 됩니다.
3. 보고 블레이드에서 사용자 지정 피드 URL을 검색합니다. 예:<br>
    `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=v1.0`
4. **Power BI Desktop**을 엽니다.
5. **파일** > **데이터 가져오기**를 선택 합니다. **OData 피드**를 선택합니다.
6. **기본**을 선택합니다.
7. **OData URL**을 URL 상자에 입력하거나 붙여넣습니다.
8. **확인**을 선택합니다.
9. Power BI 데스크톱 클라이언트에서 테넌트에 대해 Azure AD 인증을 받지 않은 경우 자격 증명을 입력합니다. 데이터에 대한 액세스 권한을 얻으려면 OAuth 2.0을 사용하여 Azure AD(Azure Active Directory)를 통해 권한을 부여해야 합니다.  
    1. **조직 계정**을 선택합니다.  
    2. 사용자 이름과 암호를 입력합니다.  
    3. **로그인**을 선택합니다.  
    4. **연결**을 선택합니다.  
10. **로드**를 선택합니다.

## <a name="next-steps"></a>다음 단계

지난주 동안 하루에 등록된 디바이스 수와 같이 환경에 관한 정보를 확인할 수 있습니다. Azure의 블레이드에서 검색된 Intune Data Warehouse Power BI 보고서를 사용하여 Intune 테넌트와 클라이언트 인구에 대한 인사이트를 얻을 수 있습니다. 그러나 Intune은 데이터를 확장하거나 다시 사용할 수 있는 다양한 수단을 제공합니다. Power BI 및 Intune Data Warehouse API는 다음과 같은 추가 기능을 제공합니다.

<!-- - You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
- 데이터에서 인사이트를 가져오도록 테넌트 데이터를 구성할 수 있습니다. 데이터 구성 방법에 대한 자세한 내용은 [데이터 웨어하우스 데이터 모델](reports-ref-data-model.md)을 참조하세요.
- RESTful 인터페이스에서 데이터에 액세스하고 데이터를 자체 앱에 통합할 수도 있습니다. 자세한 내용은 [REST 클라이언트를 사용하여 데이터 웨어하우스 API에서 데이터 가져오기](../reports-proc-data-rest.md)를 참조하세요.
