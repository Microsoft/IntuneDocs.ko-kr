---
title: 데이터 웨어하우스 사용자 엔터티 타임라인
titleSuffix: Microsoft Intune
description: Microsoft Intune 데이터 웨어하우스가 타임라인에서 사용자를 나타내는 방법을 알아봅니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/26/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 363D148E-688F-4830-B6DE-AB4FE3648817
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3fa483a49ad7fa44172a83f024540a75d1d881dc
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66040915"
---
# <a name="user-lifetime-representation-in-the-microsoft-intune-data-warehouse"></a>Microsoft Intune 데이터 웨어하우스의 사용자 수명 표시

Intune 데이터 웨어하우스에 저장된 데이터 스냅숏의 월을 사용하여 시간 기반 추세에 대한 질문에 대답할 수 있습니다. 예를 들어, 한 달 동안 추가되는 사용자 수를 확인할 수 있습니다. 시스템에서 제거된 사용자 수에 대해 질문할 수도 있습니다.

이 형식 정보를 제공하기 위해 데이터 웨어하우스는 기록 정보를 저장합니다. 데이터 웨어하우스는 엔터티의 수명을 추적할 수 있습니다. 엔터티가 만들어질 때, 엔터티 상태가 변경될 때, 그리고 엔터티가 삭제될 때의 웨어하우스 레코드입니다. 정량 측정값의 일일 스냅숏으로 캡처된 기록을 사용하여 날짜별로 비교할 수 있습니다.

엔터티는 상태가 변경되기 때문에 엔터티 수명 작업은 혼동될 수 있습니다. 즉, 30일의 스냅숏을 보면 데이터에 활성 상태의 사용자 레코드가 없을 수 있습니다. 29~28일에는 활성 상태의 엔터티 레코드가 있을 수 있습니다. 그리고 28일 이전에는 사용자가 전혀 없습니다.

엔터티의 수명을 살펴보면 이 시나리오를 더 분명히 알 수 있습니다.

사용자인 **John Smith**에게 2017/06/01에 라이선스가 할당된다고 가정하면 **User** 테이블에 다음 항목이 생기게 됩니다. 
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 12/31/9999 | TRUE
 
John Smith는 2017/07/25에 라이선스를 포기합니다. **User** 테이블에는 다음 항목이 있습니다. 기존 레코드의 변경 내용은 `marked`입니다. 

| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | `07/26/2017` | `FALSE` 
| John Smith | TRUE | 07/26/2017 | 12/31/9999 | TRUE 

첫 번째 행은 2017/06/01부터 2017/07/25까지 John Smith가 Intune에 있었음을 나타냅니다. 두 번째 레코드는 2017/07/25에 사용자가 삭제되었고 더 이상 Intune에 없음을 나타냅니다.

이제 2017/08/31에 John Smith에게 새 라이선스가 할당된다고 가정하면 User 테이블에는 다음 항목이 생기게 됩니다.
 
| DisplayName | IsDeleted | StartDateInclusiveUTC | EndDateExclusiveUTC | IsCurrent 
| -- | -- | -- | -- | -- |
| John Smith | FALSE | 06/01/2017 | 07/26/2017 | FALSE 
| John Smith | TRUE | 07/26/2017 | `08/31/2017` | `FALSE` 
| John Smith | FALSE | 08/31/2017 | 12/31/9999 | TRUE 
 
모든 사용자의 현재 상태를 보려는 사용자는 `IsCurrent = TRUE`인 필터를 적용할 수 있습니다. 
 
기존 사용자만 보려는 사용자는 `IsCurrent = TRUE AND IsDeleted = FALSE`인 필터를 적용할 수 있습니다.

## <a name="dimension-tables-in-the-entity-lifetime"></a>엔터티 수명의 차원 테이블

엔터티의 상태 변경 기록을 저장하기 위해 Intune이 레코드를 삭제하지는 않습니다. 대신에 레코드를 삭제됨으로 표시합니다. 이를 일시 삭제라고 합니다. 차원 테이블은 다양한 메타데이터 열을 사용하여 레코드 수명을 추적합니다. 

가장 일반적으로 사용되는 메타데이터 열은 다음과 같습니다. 

| 메타데이터 속성 이름  | 값 해석 |
|--|--|
| IsDeleted | 엔터티가 Intune에서 삭제되었는지 여부를 나타냅니다. |
| StartDateInclusiveUTC  | 엔터티가 Intune 데이터 웨어하우스에 로드된 UTC 날짜입니다. 엔터티가 Intune 데이터 웨어하우스로 가져오기 전에 만들어졌을 수 있습니다. |
| DeletedDateUTC  | 엔터티가 Intune에서 삭제된 UTC 날짜입니다. |  

접두사가 **Row**로 시작하는 메타데이터 열(예: **RowLastModifiedDateTimeUTC**)은 데이터가 Intune 데이터 웨어하우스에서 만들어지거나 수정된 시간을 나타냅니다. 웨어하우스는 Intune 데이터의 다운스트림입니다. 이 값은 Intune에서 엔터티의 수명과 관계가 없습니다.  
 
현재 존재하는 차원 엔터티만 보려는 사용자는 **IsDeleted = FALSE**인 필터를 적용할 수 있습니다.

## <a name="next-steps"></a>다음 단계

 - **현재 사용자** 엔터티에 대한 자세한 내용은 [현재 사용자 엔터티에 대한 참조](reports-ref-current-user.md)를 참조하세요.
 - **사용자** 엔터티에 대한 자세한 내용은 [사용자 엔터티에 대한 참조](reports-ref-user.md)를 참조하세요.
