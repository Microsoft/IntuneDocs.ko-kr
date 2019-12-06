---
title: Microsoft Intune reports
titleSuffix: Microsoft Intune
description: Intune은 일관되고 시기 적절한 데이터를 포함하는 중요 보기의 특정 보고서 유형을 제공합니다.
keywords: ''
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 05258c5363b43398dee1815bb91c50878803e426
ms.sourcegitcommit: 2fddb293d37453736ffa54692d03eca642f3ab58
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74391944"
---
# <a name="intune-reports"></a>Intune 보고서
Microsoft Intune 보고서를 사용하면 조직 전체에서 엔드포인트의 상태와 활동을 보다 효과적으로 사전에 모니터링할 수 있으며 Intune의 다른 보고서 데이터도 사용할 수 있습니다. 예를 들어, 디바이스 준수, 디바이스 상태 및 디바이스 추세에 대한 보고서를 볼 수 있습니다. 또한 보다 구체적인 데이터를 얻기 위해 사용자 지정 보고서를 만들 수도 있습니다. 

> [!NOTE]
> 새로운 구조를 준비하고 적응할 수 있도록 하기 위해 Intune 보고 기능은 일정 기간에 걸쳐 서서히 변경됩니다.

보고서 유형은 다음과 같은 주요 영역으로 구성됩니다.
- **작동** - 집중하고 작업을 수행하는 데 도움이 되는 대상이 지정된 시기 적절한 데이터를 제공합니다. 이러한 보고서는 관리자, 실무 전문가 및 기술 지원팀에서 가장 유용하게 활용할 수 있습니다.
- **조직** - 디바이스 관리 상태와 같은 전체 보기에 대한 광범위한 요약을 제공합니다. 이러한 보고서는 관리자와 운영자가 가장 유용하게 가장 유용하게 활용할 수 있습니다.
- **기록** - 일정 시간 동안의 패턴 및 추세를 제공합니다. 이러한 보고서는 관리자와 운영자가 가장 유용하게 활용할 수 있습니다.
- **전문가** - 원시 데이터를 사용하여 고유한 사용자 지정 보고서를 만들 수 있습니다. 이러한 보고서는 관리자가 가장 유용하게 활용할 수 있습니다.

보고 프레임워크는 일관적이고 보다 포괄적인 보고 환경을 제공합니다. 사용 가능한 보고서는 다음과 같은 기능을 제공합니다.
- **검색 및 정렬** – 데이터 세트의 크기에 관계없이 모든 열에서 검색하고 정렬할 수 있습니다.
- **데이터 페이징** – 페이징에 따라, 페이지별로 또는 특정 페이지로 이동하여 데이터를 검색할 수 있습니다.
- **성능** - 대량 테넌트에서 만든 보고서를 신속하게 생성하고 볼 수 있습니다.
- **내보내기** – 대량 테넌트에서 생성된 보고 데이터를 신속하게 내보낼 수 있습니다.

### <a name="who-can-access-the-data"></a>누가 데이터에 액세스할 수 있나요?

다음 권한을 가진 사용자는 감사 로그를 검토할 수 있습니다.

- 전역 관리자
- Intune 서비스 관리자
- **읽기** 권한이 있는 Intune 역할에 할당된 관리자

## <a name="non-compliant-devices-report-operational"></a>비규격 디바이스 보고서(작동)
비규격 디바이스는 일반적으로 기술 지원팀 또는 관리자 역할이 문제를 식별하고 문제를 해결하는 데 사용하는 표면적인 데이터를 보고합니다. 이러한 보고서에 있는 데이터는 시기 적절하며, 예기치 않은 동작을 알리고, 조치를 취할 수 있도록 합니다. 이 보고서는 워크로드와 함께 사용할 수 있으며, 활성 워크플로를 벗어나지 않고도 비규격 디바이스에 액세스할 수 있도록 합니다. 이 보고서는 필터링, 검색, 페이징 및 정렬 기능을 제공합니다. 또한 문제 해결에 도움이 되도록 드릴다운할 수 있습니다.

다음 단계를 사용하여 **비규격 디바이스** 보고서를 볼 수 있습니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수** > **비규격 디바이스**를 선택합니다.

    ![비규격 디바이스 보고서](./media/intune-reports/intune-reports-02.png)

## <a name="device-compliance-report-organizational"></a>디바이스 준수 보고서(조직)
디바이스 준수 보고서는 기본적으로 광범위한 내용을 담고 있으며, 집계된 메트릭을 식별하기 위해 보다 일반적인 데이터 보고 보기를 제공합니다. 이 보고서는 대형 데이터 세트를 사용하여 디바이스 준수에 대한 전반적인 상황을 제공하도록 디자인되었습니다. 예를 들어, 디바이스 준수에 대한 디바이스 준수 보고서는 데이터 세트의 크기에 관계없이, 디바이스의 모든 준수 상태를 표시하여 보다 광범위한 데이터 보기를 제공합니다. 이 보고서는 집계된 메트릭에 대한 편리한 시각화 뿐만 아니라 레코드의 완전한 분석 결과를 보여 줍니다. 이 보고서에 필터를 적용하고 "보고서 생성" 단추를 선택하여 이 보고서를 생성할 수 있습니다. 이렇게 하면 데이터를 새로 고쳐 집계 데이터를 구성하는 개별 레코드를 볼 수 있는 기능을 통해 최신 상태를 확인할 수 있습니다. 새 프레임워크의 대부분의 보고서와 마찬가지로, 이러한 레코드를 정렬하고 검색하여 필요한 정보를 집중적으로 제공할 수 있습니다. 

생성된 디바이스 상태 보고서를 보려면 다음 단계를 사용할 수 있습니다.
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **보고서**를 선택하여 보고서 요약을 확인합니다.
3. **디바이스 준수**를 선택합니다.
4. **준수 상태**, **OS** 및 **소유권** 필터를 선택하여 보고서를 미세 조정합니다.
5. **보고서 생성**(또는 **다시 생성**)을 클릭하여 현재 데이터를 검색합니다.

    ![디바이스 준수 보고서](./media/intune-reports/intune-reports-02a.png)

    > [!NOTE]
    > 이 **디바이스 준수** 보고서는 보고서를 마지막으로 생성한 시간의 타임스탬프를 제공합니다. 

관련 정보에 대해서는 [Intune에서 조건부 액세스로 Microsoft Defender ATP에 대한 규정 준수 적용](~/protect/advanced-threat-protection.md)을 참조하세요.

## <a name="reports-summary"></a>보고서 요약 

디바이스 준수 보고서는 **보고서** 워크로드의 요약 보고서로 사용할 수 있습니다. 다음 단계를 사용하여 디바이스 준수 보고서를 확인합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **보고서**를 선택하여 보고서 요약을 확인합니다.

    ![Intune 보고서 요약](./media/intune-reports/intune-reports-01.png)

## <a name="device-compliance-trend-report-historical"></a>디바이스 준수 추세 보고서(기록)
디바이스 준수 추세 보고서는 관리자와 설계자가 디바이스 준수에 대한 장기적인 추세를 식별하는 데 사용할 수 있습니다. 특정 기간 동안의 집계된 데이터가 표시되며, 향후의 투자 결정을 내리거나, 프로세스 개선을 추진하거나, 비정상 상황에 대한 조사를 촉구하는 데 유용합니다. 필터를 적용하여 특정 추세를 확인할 수도 있습니다. 이 보고서에서 제공하는 데이터는 현재 테넌트 상태의 스냅샷입니다(근 실시간). 

디바이스 준수 추세에 대한 디바이스 준수 추세 보고서는 특정 기간 동안의 디바이스 준수 상태 추세를 나타낼 수 있습니다. 준수가 최대에 도달한 경우를 파악하고 이 부분에 사용자의 시간과 노력을 집중할 수 있습니다.

다음 단계를 사용하여 **추세** 보고서를 볼 수 있습니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. 60일 추세에 대한 디바이스 준수를 보려면 **보고서** > **추세**를 선택합니다.

    ![Intune 추세 보고서](./media/intune-reports/intune-reports-03.png)

## <a name="azure-monitor-integration-reports-specialist"></a>Azure Monitor 통합 보고서(전문가)
사용자 고유의 보고서를 사용자 지정하여 원하는 데이터를 가져올 수 있습니다. 보고서의 데이터는 [Log Analytics](reports.md#log-analytics) 및 [Azure Monitor 통합 문서](reports.md#workbooks)를 사용하여 [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)를 통해 선택적으로 사용할 수 있습니다. 이러한 솔루션을 사용하면 사용자 지정 쿼리를 만들고, 경고를 구성하고, 대시보드를 만들어 원하는 방식으로 디바이스 준수 데이터를 표시할 수 있습니다. 또한 Azure Storage 계정에 활동 로그를 유지하고, [SIEM(보안 정보 및 이벤트 관리) 도구](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)를 사용하여 보고서에 연결하고, 보고서와 Azure AD 활동 로그 간의 상관 관계를 파악할 수 있습니다. 사용자 지정 보고 요구에 맞게 대시보드를 가져오는 것 외에도 Azure Monitor 통합 문서를 사용할 수 있습니다.

> [!NOTE]
> 복잡한 보고 기능을 사용하려면 Azure 구독이 필요합니다.

예제 전문가 보고서는 사용자 지정 보고서에서 디바이스 소유권 데이터와 플랫폼 등록 데이터 간의 상관 관계를 파악합니다. 그런 다음, 이 사용자 지정 보고서를 Azure Active Directory 포털의 기존 대시보드에 표시할 수 있습니다.

다음 단계를 사용하여 사용자 지정 보고서를 만들고 볼 수 있습니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **보고서** > **진단 설정**을 선택하고 [진단 설정](reports.md#diagnostic-settings)을 추가합니다.

    ![Intune 보고서 요약](./media/intune-reports/intune-reports-04.png)

3. **진단 설정 추가**를 클릭하여 **진단 설정** 창을 표시합니다. 
4. 진단 설정의 **이름**을 추가합니다. 
5. **Log Analytics에 보내기** 및 **DeviceComplianceOrg** 설정을 선택합니다.

    ![Intune 보고서 요약](./media/intune-reports/intune-reports-04a.png)

6. **저장**을 클릭합니다.
7. 그런 다음, **Log analytics**를 선택하여 [Log Analytics](reports.md#log-analytics)에서 새 로그 쿼리를 만들고 실행합니다.

   ![Log Analytics - 로그 쿼리](./media/intune-reports/intune-reports-05.png)

8. **통합 문서**를 선택하여 [Azure Monitor 통합 문서](reports.md#workbooks)를 사용하여 대화형 보고서를 만들거나 엽니다.

   ![통합 문서 - 대화형 보고서](./media/intune-reports/intune-reports-07.png)

### <a name="diagnostic-settings"></a>진단 설정
각 Azure 리소스에는 자체 진단 설정이 필요합니다. 진단 설정은 리소스에 대해 다음을 정의합니다.

- 설정에 정의된 대상으로 전송되는 로그 및 메트릭 데이터의 범주. 사용 가능한 범주는 리소스 유형에 따라 달라집니다.
- 로그를 보낼 하나 이상의 대상. 현재 대상에는 Log Analytics 작업 영역, Event Hubs 및 Azure Storage가 포함됩니다.
- Azure Storage에 저장된 데이터에 대한 보존 정책.

단일 진단 설정으로 각 대상 중 하나를 정의할 수 있습니다. 데이터를 2개 이상의 특정 대상 유형(예: 두 개의 다른 Log Analytics 작업 영역) 으로 보내려면 여러 개의 설정을 만듭니다. 각 리소스는 진단 설정을 5개까지 포함할 수 있습니다.

진단 설정에 대한 자세한 내용은 [Azure에서 플랫폼 로그 및 메트릭을 수집하는 진단 설정 만들기](https://docs.microsoft.com/azure/azure-monitor/platform/diagnostic-settings)를 참조하세요.

### <a name="log-analytics"></a>분석 로그
Log Analytics는 로그 쿼리를 작성하고 쿼리 결과를 대화형으로 분석하기 위한 Azure Portal의 기본 도구입니다. 로그 쿼리는 Azure Monitor의 다른 위치에서도 사용되지만, 일반적으로 Log Analytics를 사용하여 쿼리를 작성하고 테스트합니다. Log Analytics 사용 및 로그 쿼리 만들기에 대한 자세한 내용은 [Azure Monitor의 로그 쿼리 개요](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)를 참조하세요. 

### <a name="workbooks"></a>통합 문서
통합 문서는 텍스트, 분석 쿼리, Azure 메트릭 및 매개 변수를 풍부한 대화형 보고서로 결합합니다. 동일한 Azure 리소스에 대해 액세스 권한이 있는 다른 모든 팀 멤버가 통합 문서를 편집할 수 있습니다. 통합 문서에 대한 자세한 내용은 [Azure Monitor 통합 문서](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)를 참조하세요. 또한 통합 문서 템플릿을 사용하고 기여할 수 있습니다. 자세한 내용은 [Azure Monitor 통합 문서 템플릿](https://go.microsoft.com/fwlink/?linkid=867045)을 참조하세요.

## <a name="next-steps"></a>다음 단계

다음 기술에 대해 자세히 알아보세요.
- [블로그 - Microsoft Intune 보고 프레임워크](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553)
- [Azure Monitor](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-activity-logs-azure-monitor)
- [Log Analytics란?](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview#what-is-log-analytics)
- [로그 쿼리](https://docs.microsoft.com/azure/azure-monitor/log-query/log-query-overview)
- [Azure Monitor에서 Log Analytics 시작](https://docs.microsoft.com/azure/azure-monitor/log-query/get-started-portal)
- [Azure Monitor 통합 문서](https://docs.microsoft.com/azure/azure-monitor/app/usage-workbooks)
- [(보안 정보 및 이벤트 관리) 도구](https://docs.microsoft.com/microsoft-365/security/office-365-security/siem-server-integration)
