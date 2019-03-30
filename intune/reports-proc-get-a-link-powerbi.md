---
title: Power BI를 통해 데이터 웨어하우스에 연결
titlesuffix: Microsoft Intune
description: Microsoft Intune 테넌트에 대해 동적으로 생성된 보고서인 인터랙티브 다운로드를 위해 Microsoft Power BI용 파일을 다운로드할 수 있습니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/28/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5E5A35D3-88F8-441B-8A0B-C5D7A1E5137B
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5b93bb9911fa93998e443a797d085a568280c278
ms.sourcegitcommit: e23e78a563928ed2b2cbc588f2aa65678f7bb409
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58618504"
---
# <a name="connect-to-the-data-warehouse-with-power-bi"></a>Power BI를 통해 데이터 웨어하우스에 연결

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 테넌트에 대해 동적으로 생성된 보고서인 인터랙티브 다운로드를 위해 Microsoft Power BI용 파일을 다운로드할 수 있습니다. 데이터 웨어하우스 Power BI 파일(pbix)은 테넌트에 대한 연결 설정과 다음 샘플 보고서 및 차트를 포함합니다.  

  -  디바이스
  -  등록
  -  앱 보호 정책
  -  준수 정책
  -  디바이스 구성 프로필
  -  소프트웨어 업데이트
  -  디바이스 인벤토리 로그

등록, 규정 준수, 디바이스 구성 프로필, 소프트웨어 업데이트에 대한 트렌드도 하이라이트되어 있습니다. 샘플 차트와 보고서는 사용하기 쉬운 필터를 캔버스에 적용합니다. 고급 필터를 사용하려면 Power BI Desktop의 **필터** 창을 확인하세요.

다음 단계는 Power BI 파일을 다운로드하고 Power BI를 통해 OData 링크를 사용하는 방법을 설명합니다.

[!INCLUDE [reports-credential-reqs](./includes/reports-credential-reqs.md)]

## <a name="install-power-bi"></a>Power BI 설치

Power BI Desktop의 최신 버전을 설치합니다. Power BI Desktop 다운로드 위치: [PowerBI.microsoft.com](https://powerbi.microsoft.com/desktop)

## <a name="load-the-data-and-reports-using-the-power-bi-file-pbix"></a>Power BI 파일(pbix)을 사용하여 데이터와 보고서를 로드

Power BI 파일(pbix)은 테넌트에 대한 연결 정보와 데이터 웨어하우스 데이터 모델 기반의 미리 작성된 보고서 세트를 포함합니다. Power BI Desktop에서 파일을 열고 Azure AD에 로그인합니다. 보고서는 Intune 테넌트에서 데이터를 로드합니다.

> [!Important]  
> 각 Power BI 파일(pbix)은 테넌트 위치에 따라 다릅니다. 여러 Intune 테넌트를 관리하는 경우 해당 테넌트에 로그인한 동안 Azure 포털에서 다운로드한 파일을 사용하세요.  

1.  Azure 포털에 로그인하고 **모니터링 + 관리** > **Intune**을 선택합니다. **Intune**에 대한 리소스를 검색할 수도 있습니다.  
2.  엽니다는 **Intune 데이터 웨어하우스 설정** 블레이드입니다.
3.  **PowerBI 파일 다운로드**를 선택합니다. (pbix) 확장명을 가진 파일이 지정한 위치로 다운로드됩니다.
4.  Power BI로 파일을 엽니다. *Intune 데이터 웨어하우스 보고서*가 로드되지만 테넌트 데이터를 가져오는 데 약간의 시간이 걸릴 수 있습니다.
5.  **새로 고침**을 선택하여 테넌트 데이터를 로드하고 보고서를 검토합니다.
6.  Power BI가 Azure Active Directory 자격 증명으로 인증되지 않은 경우 Power BI는 자격 증명을 제공하라는 메시지를 표시합니다. 자격 증명을 선택할 때 인증 방법으로 **조직 계정**을 선택합니다.

## <a name="load-the-data-in-power-bi-using-the-odata-link"></a>OData 링크를 사용하여 Power BI에서 데이터 로드

클라이언트가 Azure AD에 인증되면 OData URL이 데이터 모델을 보고하는 클라이언트에 노출하는 데이터 웨어하우스 API의 RESTful 엔드포인트에 연결합니다. 다음 지침에 따라 Power BI Desktop을 사용하여 연결하고 직접 보고서를 만드세요. Power BI Desktop으로 제한되지 않으므로 자주 사용하는 다른 분석 도구를 OData URL과 사용할 수도 있습니다. 단 클라이언트가 OAUTH2.0 인증 및 OData v4.0 표준을 지원해야 합니다.

1.  Azure 포털에 로그인하고 **모니터링 + 관리** > **Intune**을 선택합니다. **Intune**에 대한 리소스를 검색할 수도 있습니다.  
2.  엽니다는 **Intune 데이터 웨어하우스 설정** 블레이드입니다.
3. 보고 블레이드에서 사용자 지정 피드 URL을 검색합니다. 예: `https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4. **Power BI Desktop**을 엽니다.
5. **홈** > **데이터 가져오기**를 선택합니다. **OData 피드**를 선택합니다.
6. **기본**을 선택합니다.
7. **OData URL**을 URL 상자에 입력하거나 붙여넣습니다.
8. **확인**을 선택합니다.
9. Power BI 데스크톱 클라이언트에서 테넌트에 대해 Azure AD 인증을 받지 않은 경우 자격 증명을 입력합니다. 데이터에 대한 액세스 권한을 얻으려면 OAuth 2.0을 사용하여 Azure AD(Azure Active Directory)를 통해 권한을 부여해야 합니다.  
    1.  **조직 계정**을 선택합니다.  
    2.  사용자 이름과 암호를 입력합니다.  
    3.  **로그인**을 선택합니다.  
    4.  **연결**을 선택합니다.  
10. **로드**를 선택합니다.

## <a name="next-steps"></a>다음 단계

지난주 동안 하루에 등록된 디바이스 수와 같이 환경에 관한 정보를 확인할 수 있습니다. Azure의 블레이드에서 검색한 Intune 데이터 웨어하우스 Power BI 파일(pbix)을 사용하는 보고서를 통해 Intune 테넌트와 클라이언트 인구에 대한 정보를 얻을 수 있습니다. 그러나 Intune은 데이터를 확장하거나 다시 사용할 수 있는 다양한 수단을 제공합니다. Power BI와 Intune 데이터 웨어하우스 API를 통해 다음과 같은 다양한 일을 할 수 있습니다.

<!-- -  You can use Power BI Desktop to create additional report types with your data. For example, you could create a custom chart representing the ratio of device manufactures in your enterprise. For more information about creating custom reports with Power BI and the Intune Data Warehouse, see `BLOG POST ON POWER BI`. -->
 -  데이터에서 인사이트를 가져오도록 테넌트 데이터를 구성할 수 있습니다. 데이터 구성 방법에 대한 자세한 내용은 [데이터 웨어하우스 데이터 모델](reports-ref-data-model.md)을 참조하세요.
 -  RESTful 인터페이스에서 데이터에 액세스하고 데이터를 자체 앱에 통합할 수도 있습니다. 자세한 내용은 [REST 클라이언트를 사용하여 데이터 웨어하우스 API에서 데이터 가져오기](reports-proc-data-rest.md)를 참조하세요.
