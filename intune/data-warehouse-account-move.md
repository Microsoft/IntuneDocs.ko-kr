---
title: Intune 데이터 웨어하우스 계정 데이터 이동
titlesuffix: Microsoft Intune
description: 계정을 이동할 때 Intune 데이터 웨어하우스 데이터를 백업하는 방법을 파악합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ee3ccbf9-82fc-4fbf-9d3d-8f05e431d090
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: c83ed35ab9c9c607f6283f2d5b18cf129f53cfab
ms.sourcegitcommit: d38ca1bf44e17211097aea481e00b6c1e87effae
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514367"
---
# <a name="move-your-intune-data-warehouse-account-data"></a>Intune 데이터 웨어하우스 계정 데이터 이동 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

계정 이동을 요청하면 데이터 센터가 다른 위치로 변경되도록 요청하는 것입니다. 이동 후에 데이터 웨어하우스가 다시 설정되고, 지정한 이동 시작일에 따라 새 위치에 데이터 기록을 시작합니다. 이전 데이터 웨어하우스 데이터를 백업하려면 계정 이동 **전에** 다음 단계를 완료하세요. 대부분의 데이터 웨어하우스 테이블은 30일 동안 데이터를 보존하므로 계정을 이동한 날부터 30일 후에는 이러한 테이블의 데이터 차이를 더 이상 사용할 수 없게 됩니다. 특정 테이블의 보존 기간에 대한 자세한 내용은 [데이터 웨어하우스 데이터 모델](reports-ref-data-model.md)을 참조하세요. 

## <a name="back-up-your-data-warehouse-data"></a>데이터 웨어하우스 데이터 백업 

데이터 웨어하우스 데이터를 백업하려면 데이터 웨어하우스 API를 사용하여 데이터 웨어하우스 데이터를 *.csv* 파일에 저장해야 합니다.  

1. 데이터 웨어하우스 API를 처음 사용하는 경우 [REST 클라이언트를 사용하여 Intune 데이터 웨어하우스 API에서 데이터 가져오기](reports-proc-data-rest.md) 문서에 제공된 일회성 프로세스를 따르세요.
2. [PowerShell을 사용하여 Intune 데이터 웨어하우스 액세스](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/PowerShell)라는 PowerShell 샘플을 사용하여 모든 데이터를 CSV 파일로 다운로드합니다. 

## <a name="back-up-your-trend-charts-from-the-azure-portal"></a>Azure Portal에서 추세 차트 백업

Azure Portal 보기의 일부 추세 차트가 다시 설정됩니다. **그래프**에서 다음 스크립트를 실행하여 이러한 차트를 백업할 수 있습니다.   

### <a name="terms--conditions-acceptance-reports"></a>사용 약관 동의 보고서
1. Azure Portal에서 **Microsoft Intune** -> **장치 등록** -> **사용 약관**으로 이동합니다.
2. 각 **사용 약관** 항목에 대해 **동의 보고서**, **내보내기**를 차례로 선택합니다.
3. 보고서를 로컬에 저장합니다.
 
### <a name="app-protection-reports"></a>앱 보호 보고서  
1. Azure Portal에서 **Microsoft Intune** -> **클라이언트 앱** -> **앱 보호 상태**로 이동합니다.
2. 다운로드 아이콘( ⤓ )을 클릭하여 각 보고서를 저장합니다.

### <a name="device-configuration-charts"></a>디바이스 구성 차트 
1. Azure Portal에서 **Microsoft Intune** -> **DeviceConfiguration**으로 이동합니다.
2. Microsoft [그래프 탐색기](https://developer.microsoft.com/graph/graph-explorer)를 사용하여 차트의 기본 데이터를 다운로드합니다. 
    - 모든 디바이스에 대한 모든 디바이스 구성 프로필의 배포 상태는 [디바이스 배포 상태](https://graph.microsoft.com/beta/reports/deviceConfigurationDeviceActivity/content)를 참조하세요.

    - 모든 사용자에 대한 모든 디바이스 구성 프로필의 배포 상태는 [사용자 배포 상태](https://graph.microsoft.com/beta/reports/deviceConfigurationUserActivity/content)를 참조하세요.

    - 프로필 배포 상태는 [배포 상태 제공](https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations?$select=id,displayName,lastModifiedDateTime,deviceStatusOverview&$expand=deviceStatusOverview)을 참조하세요.
  
    > [!NOTE]
    > 디바이스 구성 및 배포 상태 정보에 액세스하려면 유효한 인증 토큰이 있어야 합니다.

## <a name="device-enrollment-charts"></a>디바이스 등록 차트
1. Azure Portal에서 **Microsoft Intune** -> **DeviceEnrollment**로 이동합니다.
2. Microsoft [그래프 탐색기](https://developer.microsoft.com/graph/graph-explorer)를 사용하여 차트의 기본 데이터를 다운로드합니다.
    - 등록 상태를 보려면 이 [등록 상태 쿼리](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentFailureTrends()/content)를 복사하여 [그래프 탐색기](https://developer.microsoft.com/graph/graph-explorer)에 붙여넣습니다.
    - 이번 주의 상위 등록 실패를 보려면 이 [등록 실패 쿼리](https://graph.microsoft.com/beta/reports/managedDeviceEnrollmentTopFailures(period=null)/content)를 복사하여 [그래프 탐색기](https://developer.microsoft.com/graph/graph-explorer)에 붙여넣습니다.

    > [!NOTE]
    > 디바이스 등록 데이터에 액세스하려면 유효한 인증 토큰이 있어야 합니다. 

## <a name="after-a-data-warehouse-account-move"></a>데이터 웨어하우스 계정 이동 후

데이터 웨어하우스 계정 이동 후 데이터 웨어하우스가 다시 설정되었으며 이제 데이터가 새 위치에 저장되어 있음을 Intune에서 확인할 수 있습니다. 차트 및 내보내기 옵션이 다시 설정되고 알림이 표시됩니다. 알림을 클릭하면 차트가 다시 설정된 이유를 설명하는 문서가 표시됩니다.  

## <a name="data-warehouse-move-example"></a>데이터 웨어하우스 이동 예제 

고객 X가 2018/1/06에 계정 이동이 시작되도록 요청합니다. 요청에 대한 응답으로 고객은 이전 데이터 웨어하우스를 백업하려는 경우 수행할 단계를 자세히 설명하는 문서 링크를 받게 됩니다. 2018/1/06에 데이터 웨어하우스 및 지원되는 차트가 다시 설정되고 새 데이터 센터에 데이터를 저장하기 시작합니다. 

## <a name="next-steps"></a>다음 단계

 - [매주 Intune에 추가되는 새로운 기능](whats-new.md)에 대해 알아봅니다. 예정된 변경, 서비스 관련 중요 공지 및 이전 릴리스 관련 정보에 대해서도 알아볼 수 있습니다.
 - [Microsoft Intune 블로그](https://go.microsoft.com/fwlink/?LinkID=273882)를 읽어 보세요.
