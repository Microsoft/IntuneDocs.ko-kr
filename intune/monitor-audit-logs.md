---
title: Microsoft Intune 활동에 대한 감사 로그
description: Microsoft Intune 활동을 기록하는 감사 로그를 검토하는 방법을 알아봅니다.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
ms.openlocfilehash: c7c8b860be9722138f8bd804a66131328b592022
ms.sourcegitcommit: e30fb2375fb79f67e5c1e4ed7b2c21fb9ca80c59
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/17/2018
ms.locfileid: "29962449"
---
# <a name="audit-logs-for-intune-activities"></a>Intune 활동에 대한 감사 로그
감사 로그는 Microsoft Intune에서 변경을 생성하는 활동 레코드를 제공합니다. 만들기, 업데이트(편집), 삭제 및 할당 작업이나 원격 태스크는 검토할 수 있는 감사 이벤트를 생성합니다. 대부분의 Intune 워크로드에 대한 감사 로그를 검토할 수 있습니다. 감사는 기본적으로 모든 고객에 대해 사용 가능하며 사용 불가능하게 할 수 없습니다. 감사 이벤트는 2017년 12월의 기능 릴리스 날짜에 기록되기 시작했으며, 이전 이벤트는 사용할 수 없습니다.

## <a name="who-can-access-the-data"></a>누가 데이터에 액세스할 수 있나요?
다음 권한을 가진 사용자는 감사 로그를 검토할 수 있습니다.
- 전역 관리자
- Intune 서비스 관리자
- **감사 데이터** - **읽기** 권한이 있는 Intune 역할에 할당된 관리자

## <a name="audit-logs-for-intune-workloads"></a>Intune 워크로드에 대한 감사 로그
각 Intune 워크로드에 대한 모니터링 그룹에서 감사 로그를 검토할 수 있습니다.  
1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 감사 로그를 검토하려는 워크로드를 선택합니다(예: **장치**).
4. 워크로드에 대한 **모니터링** 그룹에서 **감사 로그**를 선택합니다.

## <a name="review-audit-events"></a>감사 이벤트 검토
![감사 로그](./media/monitor-audit-logs.png "감사 로그")

감사 로그에는 다음 항목을 표시하는 기본 목록 보기가 있습니다.    

- 발생 날짜 및 시간
- 시작한 사람(행위자)
- 응용 프로그램 이름
- 활동
- 대상
- Category
- 상태

목록 보기에서 항목을 클릭하면 사용 가능한 모든 세부 정보가 표시됩니다.

![감사 로그](./media/monitor-audit-log-detail.png "감사 로그")

> [!Note]    
> 감사 로그 세부 정보의 **시작한 사람(행위자)** 섹션에는 활동을 수행한 사람과 수행된 위치에 대한 정보가 제공됩니다. 예를 들어 Azure Portal의 Intune에서 활동을 수행하는 경우 **응용 프로그램**에 항상 **Microsoft Intune 포털 확장**이 나열되고 **응용 프로그램 ID**에 항상 동일한 GUID가 사용됩니다. 
>    
> **대상** 섹션에는 여러 대상과 변경된 속성이 나열될 수 있습니다.  


## <a name="filter-audit-events"></a>감사 이벤트 필터링
각 워크로드에는 해당 창과 관련된 감사 이벤트 범주를 사전 필터링하는 메뉴 항목이 있습니다. 별도의 필터 옵션을 사용하여 다른 범주와 해당 범주 내의 이벤트 작업 세부 정보로 변경할 수 있습니다. UPN(예: 작업을 수행한 사용자)으로 검색할 수 있습니다. 날짜 범위 필터는 24시간, 7일 또는 30일 옵션을 허용합니다. 기본적으로 최근 30일의 감사 이벤트가 표시됩니다.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API를 사용하여 감사 이벤트 검색
Graph API를 사용하여 최대 1년의 감사 이벤트를 검색하는 방법에 대한 자세한 내용은 [auditEvent 목록](https://developer.microsoft.com/en-us/graph/docs/api-reference/beta/api/intune_auditing_auditevent_list)을 참조하세요.