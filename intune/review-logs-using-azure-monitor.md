---
title: Microsoft Intune을 사용하여 Azure Monitor에서 경로 감사 로그 - Azure | Microsoft Docs
description: 진단 설정을 사용하여 Microsoft Intune에서 감사 로그 및 작업 로그를 Azure Storage 계정, Event Hubs 또는 Log Analytics로 보냅니다. 데이터를 유지하려는 기간을 선택하고 다양한 크기 테넌트에 대한 예상 비용을 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: d95b37d18fa609f1c4e98d4fad5cfa600333b90a
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354530"
---
# <a name="send-log-data-to-storage-event-hubs-or-log-analytics-in-intune-preview"></a>Intune에서 스토리지, Event Hubs 또는 Log Analytics에 로그 데이터 전송(미리 보기)

Microsoft Intune에는 사용자 환경에 대한 정보를 제공하는 기본 제공 로그가 포함되어 있습니다. **감사 로그**는 Intune에서 발생하는 다른 이벤트 또는 작업에 대한 세부 정보를 표시합니다. **작업 로그(미리 보기)** 는 비규격 디바이스에 대한 세부 정보뿐만 아니라 등록에 성공(또는 실패)한 사용자 및 디바이스에 대한 세부 정보를 표시합니다.

또한 이러한 로그를 스토리지 계정, Event Hubs 및 Log Analytics를 비롯한 Azure Monitor 서비스에 전송할 수 있습니다. 특히 다음을 수행할 수 있습니다.

* 데이터를 유지하거나 설정된 시간 동안을 보관하도록 Azure Storage 계정에 Intune 로그를 보관합니다.
* Splunk 및 QRadar와 같은 인기 있는 SIEM(보안 정보 및 이벤트 관리)을 사용하여 분석에 대한 Azure 이벤트 허브에 Intune 로그를 스트리밍합니다.
* 이벤트 허브로 스트리밍하여 사용자 고유의 사용자 지정 로그 솔루션을 사용하여 Intune 로그를 통합합니다.
* Log Analytics에 Intune 로그를 전송하여 연결된 데이터에 다양한 시각화, 모니터링 및 경고를 사용하도록 설정합니다.

이러한 기능은 Intune **진단 설정**의 일부분입니다.

이 문서에서는 **진단 설정**을 사용하여 다른 서비스에 로그 데이터를 보내는 방법을 설명하고, 예제 및 예상 비용을 제공하며, 몇 가지 일반적인 질문에 대해 답변합니다.

## <a name="prerequisites"></a>전제 조건

이 기능을 사용하려면 다음이 필요합니다.

* Azure 구독: Azure 구독이 없으면 [평가판에 등록](https://azure.microsoft.com/free/)할 수 있습니다.
* Azure에서 Microsoft Intune 환경(테넌트)
* Intune 테넌트에 대한 **글로벌 관리자** 또는 **Intune 서비스 관리자**인 사용자.

감사 로그 데이터를 라우팅하려는 대상에 따라 다음 서비스 중 하나가 필요합니다.

* *ListKeys* 권한이 있는 [Azure Storage 계정](https://docs.microsoft.com/azure/storage/common/storage-account-overview). Blob 스토리지 계정이 아닌 일반 스토리지 계정을 사용하는 것이 좋습니다. 스토리지 가격 책정 정보는 [Azure Storage 가격 책정 계산기](https://azure.microsoft.com/pricing/calculator/?service=storage)를 참조하세요. 
* 타사 솔루션과 통합하기 위한 [Azure Event Hubs 네임스페이스](https://docs.microsoft.com/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace).
* Log Analytics에 로그를 보내기 위한 [Azure Log Analytics 작업 영역](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace).

## <a name="send-logs-to-azure-monitor"></a>Azure Monitor로 로그 보내기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **모니터링**에서 **진단 설정**을 선택합니다. 처음으로 여는 경우 다음과 같이 켭니다.

    ![Intune에서 진단 설정을 켜서 Azure Monitor로 로그 보내기](media/diagnostics-settings-turn-on.png)

3. 다음 속성을 입력합니다.

    - **이름**: 진단 설정의 이름을 입력합니다. 이 설정에는 입력한 모든 속성이 포함됩니다. 예를 들어 다음과 같이 입력합니다. `Route audit logs to storage account`
    - **스토리지 계정에 보관**: Azure Storage 계정에 로그 데이터를 저장합니다. 데이터를 저장하거나 보관하려는 경우 이 옵션을 사용합니다.

        1. 이 옵션 > **구성**을 선택합니다. 
        2. 목록에서 기존 스토리지 계정 > **확인**을 선택합니다.

    - **Event Hub로 스트림**: Azure Event Hub로 로그를 스트리밍합니다. Splunk 등 QRadar와 같은 SIEM 도구를 사용하여 로그 데이터를 분석하려는 경우 이 옵션을 선택합니다.

        1. 이 옵션 > **구성**을 선택합니다. 
        2. 목록에서 기존 Event Hub 네임스페이스 및 정책 > **확인**을 선택합니다.

    - **Log Analytics에 보내기**: Azure Log Analytics에 데이터를 보냅니다. 로그에 대해 시각화, 모니터링 및 경고를 사용하려면 이 옵션을 선택합니다.

        1. 이 옵션 > **구성**을 선택합니다. 
        2. 새 작업 영역을 만들고 작업 영역 세부 정보를 입력합니다. 또는 목록에서 기존 작업 영역 > **확인**을 선택합니다.

            [Azure Log Analytics 작업 영역](https://docs.microsoft.com/azure/azure-monitor/learn/quick-create-workspace)에는 이러한 설정의 세부 정보가 제공됩니다.

    - **LOG** > **AuditLogs**: [Intune 감사 로그](monitor-audit-logs.md)를 스토리지 계정, Event Hub 또는 Log Analytics로 보내려면 이 옵션을 선택합니다. 감사 로그는 작업자 및 작업 시기를 포함한 Intune에서 변경을 생성하는 모든 작업의 기록을 표시합니다.

      스토리지 계정을 사용하려는 경우 데이터를 유지(보존)하려는 기간(일)을 입력합니다. 데이터를 영구적으로 유지하려면 **보존(일)** 을 `0`(영)으로 설정합니다.

    - **LOG** > **OperationalLogs**: 작업 로그(미리 보기)는 비규격 디바이스에 대한 세부 정보뿐만 아니라 Intune에 등록하는 사용자 및 디바이스의 성공 또는 실패를 표시합니다. 스토리지 계정, Event Hub 또는 Log Analytics에 등록 로그를 보내려면 이 옵션을 선택합니다.

      스토리지 계정을 사용하려는 경우 데이터를 유지(보존)하려는 기간(일)을 입력합니다. 데이터를 영구적으로 유지하려면 **보존(일)** 을 `0`(영)으로 설정합니다.

      > [!NOTE]
      > 작업 로그는 미리 보기로 제공됩니다. 작업 로그에 포함된 정보를 비롯한 피드백을 제공하려면 [UserVoice](https://microsoftintune.uservoice.com/forums/291681-ideas/suggestions/36613948-diagnostics-settings-feedback)로 이동합니다(새 웹 사이트 열기).

    완료되면 설정이 다음 설정과 유사하게 표시됩니다. 

    ![Azure Storage 계정에 Intune 감사 로그를 전송하는 간단한 이미지](media/diagnostics-settings-example.png)

4. 변경 내용을 **저장**합니다. 설정이 목록에 표시됩니다. 만든 후 **설정 편집** > **저장**을 선택하여 설정을 변경할 수 있습니다.

## <a name="use-audit-logs-throughout-intune"></a>Intune 전체에서 감사 로그 사용

등록, 규정 준수, 구성, 디바이스, 클라이언트 앱 등을 포함하여 Intune의 다른 부분에 감사 로그를 내보낼 수도 있습니다.

예를 들어 디바이스 규정 준수를 사용할 때 감사 로그를 내보내려면 다음을 수행합니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 규정 준수** > **모니터** > **감사 로그**를 선택합니다.

    ![감사 로그를 선택하여 Intune 데이터를 Azure Monitor 스토리지, 이벤트 허브 또는 분석으로 라우팅](media/audit-logs-under-monitor-in-compliance.png)

3. **데이터 내보내기 설정**을 선택합니다. 활성화되어 있지 않은 경우 **진단 설정**을 켤 수 있습니다. [Azure 모니터로 로그 보내기](#send-logs-to-azure-monitor)(이 문서)에서 설명된 대로 로그를 보낼 위치를 선택할 수도 있습니다.

## <a name="cost-considerations"></a>비용 고려 사항

Microsoft Intune 라이선스가 이미 있는 경우 스토리지 계정 및 Event Hub를 설정하려면 Azure 구독이 필요합니다. Azure 구독은 일반적으로 무료입니다. 하지만 저장을 위한 스토리지 계정 및 스트리밍을 위한 Event Hub를 포함한 Azure 리소스를 사용하려면 비용을 지불해야 합니다. 데이터의 양과 비용은 테넌트 크기에 따라 달라집니다.

### <a name="storage-size-for-activity-logs"></a>활동 로그에 대한 스토리지 크기

모든 감사 로그 이벤트는 약 2KB의 데이터 스토리지를 사용합니다. 사용자가 100,000명인 테넌트의 경우 하루에 약 150만 개 이벤트를 가질 수도 있습니다. 일별 약 3GB의 데이터 스토리지가 필요할 수도 있습니다. 쓰기는 일반적으로 5분 단위로 발생하기 때문에 월별 약 9,000개 쓰기 작업을 예상할 수 있습니다.

다음 표에 테넌트의 크기에 따른 예상 비용이 나와 있습니다. 최소 1년 데이터 보존에 대해 미국 서부의 범용 v2 스토리지 계정이 포함되어 있습니다. 로그에 예상하는 데이터 볼륨의 예상치를 가져오려면 [Azure Storage 가격 책정 계산기](https://azure.microsoft.com/pricing/details/storage/blobs/)를 사용합니다.

**사용자가 100,000명인 감사 로그**

| | |
|---|---|
|일별 이벤트| 150만|
|월별 예상 데이터 볼륨| 90GB|
|월별 예상 비용(USD)| $1.93|
|연간 예상 비용(USD)| $23.12|

**사용자가 1,000명인 감사 로그**

| | |
|---|---|
|일별 이벤트| 15,000|
|월별 예상 데이터 볼륨| 900MB|
|월별 예상 비용(USD)| $0.02|
|연간 예상 비용(USD)| $0.24|

### <a name="event-hub-messages-for-activity-logs"></a>활동 로그에 대한 Event Hub 메시지

이벤트는 일반적으로 5분 간격으로 일괄 처리되며 해당 시간대 내에서 모든 이벤트를 사용하여 단일 메시지로 전송됩니다. Event Hub 메시지의 최대 크기는 256KB입니다. 시간대 내의 모든 메시지의 총 크기가 해당 볼륨을 초과하는 경우 메시지가 여러 개 전송됩니다.

예를 들어, 사용자가 100,000명 이상인 대규모 테넌트의 경우 일반적으로 초당 약 18개 이벤트가 발생합니다. 이는 5분당 5,400개 이벤트와 동일합니다(300초 x 18개 이벤트). 감사 로그는 이벤트당 약 2KB입니다. 이는 10.8MB의 데이터와 같습니다. 따라서 43개 메시지가 5분 간격으로 Event Hub에 전송됩니다.

다음 표에는 이벤트 데이터의 볼륨에 따른 미국 서부의 기본 Event Hub에 대한 월별 예상 비용이 포함되어 있습니다. 로그에 대해 예상하는 데이터 볼륨의 예상치를 가져오려면 [Event Hubs 가격 책정 계산기](https://azure.microsoft.com/pricing/details/event-hubs/)를 사용합니다.

**사용자가 100,000명인 감사 로그**

| | |
|---|---|
|초당 이벤트 수| 18|
|5분당 이벤트 수| 5,400|
|간격당 볼륨| 10.8MB|
|간격당 메시지 수| 43|
|월별 메시지 수| 371,520|
|월별 예상 비용(USD)| $10.83|

**사용자가 1,000명인 감사 로그**

| | |
|---|---|
|초당 이벤트 수|0.1 |
|5분당 이벤트 수| 52|
|간격당 볼륨|104KB |
|간격당 메시지 수|1 |
|월별 메시지 수|8,640 |
|월별 예상 비용(USD)|$10.80 |

### <a name="log-analytics-cost-considerations"></a>Log Analytics 비용 고려 사항

Log Analytics 작업 영역 관리와 관련된 비용을 검토하려면 [Log Analytics에서 데이터 볼륨 및 보존을 제어하여 비용 관리](https://docs.microsoft.com/azure/log-analytics/log-analytics-manage-cost-storage)를 참조하세요.

## <a name="frequently-asked-questions"></a>질문과 대답

자주 묻는 질문에 대한 답변을 확인하고 Azure Monitor의 Intune 로그와 관련된 알려진 문제에 대해 알아봅니다.

### <a name="which-logs-are-included"></a>어떤 로그가 포함되나요?

감사 로그 및 운영(미리 보기) 로그는 모두 이 기능을 통해 라우팅에 사용할 수 있습니다.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-event-hub"></a>작업 후에 해당 로그는 언제 Event Hub에 표시되나요?

로그는 일반적으로 작업이 수행된 후 몇 분 안에 Event Hub에 표시됩니다. [Azure Event Hubs란?](https://docs.microsoft.com/azure/event-hubs/)에 자세한 정보가 나와 있습니다.

### <a name="after-an-action-when-do-the-corresponding-logs-show-up-in-the-storage-account"></a>작업 후에 해당 로그는 언제 스토리지 계정에 표시되나요?

Azure Storage 계정의 경우 작업이 실행 된 후 대기 시간은 5~15분입니다.

### <a name="what-happens-if-an-administrator-changes-the-retention-period-of-a-diagnostic-setting"></a>관리자가 진단 설정의 보존 기간을 변경하는 경우 어떻게 되나요?

새 보존 정책은 변경 후 수집된 로그에 적용됩니다. 정책 변경 전에 수집된 로그는 영향을 받지 않습니다.

### <a name="how-much-does-it-cost-to-store-my-data"></a>내 데이터를 저장하는 비용은 얼마인가요?

스토리지 비용은 사용자가 선택하는 로그 크기 및 보존 기간에 따라 달라집니다. 생성된 로그 볼륨에 따른 테넌트에 대한 예상 비용의 목록은 [활동 로그에 대한 스토리지 크기](#storage-size-for-activity-logs)(이 문서에 있음)를 참조하세요.

### <a name="how-much-does-it-cost-to-stream-my-data-to-an-event-hub"></a>내 데이터를 Event Hub로 스트리밍하는 비용은 얼마인가요?

스트리밍 비용은 분당 수신하는 메시지의 수에 따라 달라집니다. 메시지의 수에 따른 비용 계산 방법 및 예상 비용에 대한 자세한 내용은 [활동 로그에 대한 Event Hub 메시지](#event-hub-messages-for-activity-logs)(이 문서에 있음)를 참조하세요.

### <a name="how-do-i-integrate-intune-audit-logs-with-my-siem-system"></a>Intune 감사 로그를 내 SIEM 시스템과 통합하려면 어떻게 해야 하나요?

로그를 SIEM 시스템으로 스트리밍하려면 Event Hubs와 함께 Azure Monitor를 사용합니다. 먼저 [Event Hub로 로그를 스트리밍](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)합니다. 그런 다음, 구성된 Event Hub를 사용하여 [SIEM 도구를 설정](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub#access-data-from-your-event-hub)합니다. 

### <a name="what-siem-tools-are-currently-supported"></a>현재 지원되는 SIEM 도구는 무엇인가요?

현재 [Splunk](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-integrate-activity-logs-with-splunk), QRadar 및 [Sumo Logic](https://help.sumologic.com/Send-Data/Applications-and-Other-Data-Sources/Azure_Active_Directory)에서 Azure Monitor가 지원됩니다(새 웹 사이트 열기). 커넥터 작동 방식에 대한 자세한 내용은 [외부 도구에서 사용하도록 Event Hub로 Azure 모니터링 데이터를 스트리밍](https://docs.microsoft.com/azure/azure-monitor/platform/stream-monitoring-data-event-hubs)을 참조하세요.

### <a name="can-i-access-the-data-from-an-event-hub-without-using-an-external-siem-tool"></a>외부 SIEM 도구를 사용하지 않고 Event Hub에서 데이터에 액세스할 수 있나요?

예. 사용자 지정 애플리케이션에서 로그에 액세스하려면 [Event Hubs API](https://docs.microsoft.com/azure/event-hubs/event-hubs-dotnet-standard-getstarted-receive-eph)를 사용할 수 있습니다.

### <a name="what-data-is-stored"></a>어떤 데이터가 저장되나요?

Intune은 파이프라인을 통해 전송되는 데이터를 모두 저장하지는 않습니다. Intune은 테넌트의 인증 기관에서 Azure Monitor 파이프라인으로 데이터를 라우팅합니다. 자세한 내용은 [Azure Monitor 개요](https://docs.microsoft.com/azure/azure-monitor/overview)를 참조하세요.

## <a name="next-steps"></a>다음 단계

* [스토리지 계정에 활동 로그 보관](https://docs.microsoft.com/azure/active-directory/reports-monitoring/quickstart-azure-monitor-route-logs-to-storage-account)
* [Event Hub로 활동 로그 라우팅](https://docs.microsoft.com/azure/active-directory/reports-monitoring/tutorial-azure-monitor-stream-logs-to-event-hub)
* [활동 로그를 Log Analytics와 통합](https://docs.microsoft.com/azure/active-directory/reports-monitoring/howto-integrate-activity-logs-with-log-analytics)
