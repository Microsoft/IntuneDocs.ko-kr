---
title: 변경 및 Microsoft Intune-Azure에서에서 이벤트를 감사 | Microsoft Docs
description: Microsoft Intune 활동을 기록하는 감사 로그를 검토하는 방법을 알아봅니다.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 93072ba4730de0252f54d93fa1169062d496ce38
ms.sourcegitcommit: 1069b3b1ed593c94af725300aafd52610c7d8f04
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58394904"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>추적 하 고 Microsoft Intune에서 이벤트를 모니터링할 감사 로그를 사용 하 여

감사 로그는 Microsoft Intune에서 변경을 생성하는 활동 레코드를 제공합니다. 만들기, 업데이트 (편집), 삭제, 할당 하 고, 원격 작업 모든 대부분의 Intune 워크 로드에 대 한 관리자가 검토할 수 있는 이벤트를 감사를 만듭니다. 기본적으로 감사 모든 고객에 게 사용 됩니다. 해제할 수 없습니다.

> [!NOTE]
> 감사 이벤트는 2017 년 12 월 기능 릴리스 기록을 시작합니다. 이전 이벤트를 사용할 수 없습니다.

## <a name="who-can-access-the-data"></a>누가 데이터에 액세스할 수 있나요?

다음 권한을 가진 사용자는 감사 로그를 검토할 수 있습니다.

- 전역 관리자
- Intune 서비스 관리자
- **감사 데이터** - **읽기** 권한이 있는 Intune 역할에 할당된 관리자

## <a name="audit-logs-for-intune-workloads"></a>Intune 워크로드에 대한 감사 로그

각 Intune 워크로드에 대한 모니터링 그룹에서 감사 로그를 검토할 수 있습니다.

1. [Azure Portal](https://portal.azure.com/)에서 **모든 서비스**를 선택하고 > **Intune**을 기준으로 필터링하고 > **Intune**을 선택합니다.
2. 감사 로그를 검토 하려는 워크 로드를 선택 합니다. 예를 들어 선택할 **장치**합니다.
3. 아래 **모니터링**, 선택 **감사 로그**합니다.

## <a name="route-logs-to-azure-monitor"></a>Azure Monitor로 로그 라우팅

감사 로그 및 작업 로그도 Azure Monitor로 라우팅할 수 있습니다. **감사 로그**를 선택 **데이터 설정 내보내기**:

![Azure 로그 데이터를 내보내려면 내보낼 데이터 설정을 Intune에서 선택 하 여 모니터](./media/audit-logs-export-data-settings.png)

이 기능에 대한 자세한 내용은 [스토리지, Event Hubs 또는 Log Analytics에 로그 데이터 전송](review-logs-using-azure-monitor.md)을 참조하세요.

## <a name="review-audit-events"></a>감사 이벤트 검토

![작업 및 이벤트가 발생 하는 경우 날짜를 확인 하려면 Intune에서 감사 로그를 선택](./media/monitor-audit-logs.png "감사 로그")

감사 로그에는 다음 항목을 표시하는 기본 목록 보기가 있습니다.

- 발생 날짜 및 시간
- 시작한 사람(행위자)
- 응용 프로그램 이름
- 활동
- 대상
- Category
- 상태

이벤트에 대 한 보다 구체적인 정보를 보려면 목록에서 항목을 선택 합니다.

![감사 로그를 Intune에서 누가에 보다 구체적인 정보를 가져올](./media/monitor-audit-log-detail.png "감사 로그 세부 정보")

> [!NOTE]
> **시작한 사람 (행위자)** 태스크를 실행 한 사용자가 실행 된 위치에 대 한 정보가 포함 되어 있습니다. 예를 들어 Azure Portal의 Intune에서 활동을 실행하는 경우 **애플리케이션**에 항상 **Microsoft Intune 포털 확장**이 나열되고 **애플리케이션 ID**에 항상 동일한 GUID가 사용됩니다.
> 
> **대상** 섹션에는 여러 대상과 변경된 속성이 나열될 수 있습니다.  

## <a name="filter-audit-events"></a>감사 이벤트 필터링

각 워크로드에는 해당 창과 관련된 감사 이벤트 범주를 사전 필터링하는 메뉴 항목이 있습니다. 별도의 필터 옵션을 사용하여 다른 범주와 해당 범주 내의 이벤트 작업 세부 정보로 변경할 수 있습니다. 예: 작업을 수행한 사용자 UPN으로 검색할 수 있습니다. 날짜 범위 필터는 24시간, 7일 또는 30일 옵션을 허용합니다. 기본적으로 최근 30일의 감사 이벤트가 표시됩니다.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API를 사용하여 감사 이벤트 검색

Graph API를 사용 하 여 감사 이벤트의 최대 1 년을 가져오기에 대 한 내용은 참조 하세요 [Auditevent 목록](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)합니다.

## <a name="next-steps"></a>다음 단계

[Storage, event hubs에 로그 데이터를 전송 또는 log analytics](review-logs-using-azure-monitor.md)합니다.

[클라이언트 앱 보호 로그 검토](app-protection-policy-settings-log.md).
