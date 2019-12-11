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
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 6ee841cc-5694-4ba1-8f66-1d58edec30a4
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: d6af0718f2b926383bb943b6321b4d5839346ce7
ms.sourcegitcommit: df8e2c052fafb2d5d4e9b4fcd831ae0ecf7f8d16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991984"
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

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **감사 로그** > **테 넌 트 관리** 를 선택 합니다.
3. 결과를 필터링 하려면 다음 옵션을 사용 하 여 **필터** 를 선택 하 고 결과를 구체화 합니다.
    - **범주**: **규정 준수**, **장치**및 **역할**입니다.
    - **활동**: 여기에 나열 된 옵션은 **범주**아래에서 선택한 옵션에 의해 제한 됩니다.
    - **날짜 범위**: 이전 월, 주 또는 날짜에 대 한 로그를 선택할 수 있습니다.
4. **적용**을 선택합니다.
4. 활동 세부 정보를 보려면 목록에서 항목을 선택 합니다.

## <a name="route-logs-to-azure-monitor"></a>Azure Monitor로 로그 라우팅

감사 로그 및 작업 로그도 Azure Monitor로 라우팅될 수 있습니다. **감사 로그**에서 **데이터 내보내기 설정**을 선택합니다.

![Intune에서 데이터 내보내기 설정을 선택하여 Azure Monitor로 로그 데이터 내보내기](./media/monitor-audit-logs/audit-logs-export-data-settings.png)

> [!NOTE]
> 이 기능에 대 한 자세한 내용 및 사용을 위한 필수 구성 요소를 검토 하려면 [저장소, 이벤트 허브 또는 log analytics로 로그 데이터 보내기](review-logs-using-azure-monitor.md)를 참조 하세요.

> [!NOTE]
> **시작한 사람(행위자)** 에는 태스크를 실행한 사람에 대한 정보 및 실행된 위치에 대한 정보가 포함되어 있습니다. 예를 들어 Azure Portal의 Intune에서 활동을 실행하는 경우 **애플리케이션**에 항상 **Microsoft Intune 포털 확장**이 나열되고 **애플리케이션 ID**에 항상 동일한 GUID가 사용됩니다.
>
> **대상** 섹션에는 여러 대상과 변경된 속성이 나열될 수 있습니다.  

## <a name="use-graph-api-to-retrieve-audit-events"></a>Graph API를 사용하여 감사 이벤트 검색

Graph API를 사용하여 최대 1년의 감사 이벤트를 검색하는 데 관한 자세한 내용은 [auditEvent 목록](https://docs.microsoft.com/graph/api/intune-auditing-auditevent-list?view=graph-rest-1.0)을 참조하세요.

## <a name="next-steps"></a>다음 단계

[스토리지, 이벤트 허브 또는 로그 분석에 로그 데이터 전송](review-logs-using-azure-monitor.md)

[클라이언트 앱 보호 로그 검토](../apps/app-protection-policy-settings-log.md).
