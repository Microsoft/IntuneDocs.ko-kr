---
title: Microsoft Intune에서 변경 및 이벤트 감사 - Azure | Microsoft Docs
description: Microsoft Intune 활동을 기록하는 감사 로그를 검토하는 방법을 알아봅니다.
keywords: ''
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d999603abc539fda4d152d15dd1ab965c465f39e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736301"
---
# <a name="use-audit-logs-to-track-and-monitor-events-in-microsoft-intune"></a>감사 로그를 사용하여 Microsoft Intune에서 이벤트를 추적하고 모니터링합니다.

감사 로그는 Microsoft Intune에서 변경을 생성하는 활동 레코드를 제공합니다. 만들기, 업데이트(편집), 삭제, 할당 및 원격 작업은 모두 관리자가 대부분의 Intune 워크로드를 검토할 수 있는 감사 이벤트를 만듭니다. 기본적으로 감사는 모든 고객에게 활성화되어 있습니다. 비활성화할 수 없습니다.

> [!NOTE]
> 감사 이벤트는 2017년 12월 기능 릴리스에서 기록을 시작했습니다. 이전 이벤트는 사용할 수 없습니다.

## <a name="who-can-access-the-data"></a>누가 데이터에 액세스할 수 있나요?

다음 권한을 가진 사용자는 감사 로그를 검토할 수 있습니다.

- 전역 관리자
- Intune 서비스 관리자
- **감사 데이터** - **읽기** 권한이 있는 Intune 역할에 할당된 관리자

## <a name="audit-logs-for-intune-workloads"></a>Intune 워크로드에 대한 감사 로그

각 Intune 워크로드에 대한 모니터링 그룹에서 감사 로그를 검토할 수 있습니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. 감사 로그를 검토하려는 워크로드를 선택합니다. 예를 들어 **디바이스**를 선택합니다.
3. **모니터링**에서 **감사 로그**를 선택합니다.

## <a name="route-logs-to-azure-monitor"></a>Azure Monitor로 로그 라우팅

감사 로그 및 작업 로그도 Azure Monitor로 라우팅될 수 있습니다. **감사 로그**에서 **데이터 내보내기 설정**을 선택합니다.

![Intune에서 데이터 내보내기 설정을 선택하여 Azure Monitor로 로그 데이터 내보내기](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

이 기능에 대한 자세한 내용은 [스토리지, Event Hubs 또는 Log Analytics에 로그 데이터 전송](review-logs-using-azure-monitor.md)을 참조하세요.

## <a name="review-audit-events"></a>감사 이벤트 검토

![이벤트가 발생하는 경우 작업 및 날짜를 확인하려면 Intune에서 감사 로그 선택](./media/monitor-audit-logs/monitor-audit-logs.png "감사 로그")

감사 로그에는 다음 항목을 표시하는 기본 목록 보기가 있습니다.

- 발생 날짜 및 시간
- 시작한 사람(행위자)
- 애플리케이션 이름
- 활동
- 대상
- Category
- 상태

이벤트에 대한 더 구체적인 정보를 보려면 목록에서 항목을 선택합니다.

![Intune의 감사 로그에서 누가 무엇을 했는지에 관해 더 구체적인 정보 얻기](./media/monitor-audit-logs/monitor-audit-log-detail.png "감사 로그 세부 정보")

> [!NOTE]
> **시작한 사람(행위자)** 에는 태스크를 실행한 사람에 대한 정보 및 실행된 위치에 대한 정보가 포함되어 있습니다. 예를 들어 Azure Portal의 Intune에서 활동을 실행하는 경우 **애플리케이션**에 항상 **Microsoft Intune 포털 확장**이 나열되고 **애플리케이션 ID**에 항상 동일한 GUID가 사용됩니다.
> 
> **대상** 섹션에는 여러 대상과 변경된 속성이 나열될 수 있습니다.  

## <a name="filter-audit-events"></a>감사 이벤트 필터링

각 워크로드에는 해당 창과 관련된 감사 이벤트 범주를 사전 필터링하는 메뉴 항목이 있습니다. 별도의 필터 옵션을 사용하여 다른 범주와 해당 범주 내의 이벤트 작업 세부 정보로 변경할 수 있습니다. UPN(예: 작업을 수행한 사용자)으로 검색할 수 있습니다. 날짜 범위 필터는 24시간, 7일 또는 30일 옵션을 허용합니다. 기본적으로 최근 30일의 감사 이벤트가 표시됩니다.

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API를 사용하여 감사 이벤트 검색

Graph API를 사용하여 최대 1년의 감사 이벤트를 검색하는 데 관한 자세한 내용은 [auditEvent 목록](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)을 참조하세요.

## <a name="next-steps"></a>다음 단계

[스토리지, 이벤트 허브 또는 로그 분석에 로그 데이터 전송](review-logs-using-azure-monitor.md)

[클라이언트 앱 보호 로그 검토](../apps/app-protection-policy-settings-log.md).
