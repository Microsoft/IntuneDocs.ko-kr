---
title: Microsoft Intune에서 디바이스 준수 정책 모니터링 - Azure | Microsoft Docs
description: 디바이스 준수 대시보드를 사용하여 전반적인 디바이스 준수를 모니터링하고, 보고서를 보고, 정책별 및 설정별 디바이스 준수를 봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: fc97e9884fbcd23c599c917c181e29cdbc3708ee
ms.sourcegitcommit: 78ae22b1a7cb221648fc7346db751269d9c898b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66374032"
---
# <a name="monitor-intune-device-compliance-policies"></a>Intune 디바이스 준수 정책 모니터링

준수 보고서를 통해 디바이스 준수를 검토하고 조직에서 준수 관련 문제를 해결할 수 있습니다. 이러한 보고서를 사용하여 다음의 정보를 볼 수 있습니다.

- 디바이스의 전체 준수 상태
- 개별 설정에 대한 준수 상태
- 개별 정책에 대한 준수 상태
- 디바이스에 영향을 주는 특정 설정 및 정책을 보도록 개별 디바이스 드릴다운

## <a name="open-the-compliance-dashboard"></a>준수 대시보드 열기

**Intune 디바이스 준수 대시보드**를 엽니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.

2. **디바이스 준수** > **개요**를 선택합니다. **디바이스 준수 대시보드**가 열립니다.

> [!IMPORTANT]
> 디바이스 Intune에 등록해야 디바이스 준수 정책을 수신할 수 있습니다.

## <a name="dashboard-overview"></a>대시보드 개요

대시보드가 열리면 모든 준수 보고서를 사용하여 개요를 가져옵니다. 이러한 보고서에서 다음에 대해 보고 확인할 수 있습니다.

- 전체 디바이스 준수
- 정책별 디바이스 준수
- 설정별 디바이스 준수
- 디바이스 보호 상태
- 위협 에이전트 상태

![대시보드 이미지는 디바이스 준수 대시보드 및 다른 보고서를 보여줍니다.](./media/compliance-policy-monitor/idc-1.png)

이 보고를 살펴보면서 각 설정에 대한 준수 상태를 포함하여 특정 디바이스에 적용되는 모든 특정 준수 정책 및 설정을 볼 수도 있습니다.

### <a name="device-compliance-status-report"></a>디바이스 준수 상태 보고서

차트에서는 Intune에 등록된 모든 디바이스에 대한 준수 상태를 보여줍니다. 디바이스 준수 상태는 2개의 데이터베이스, 즉 Intune 및 Azure Active Directory에 보관됩니다. 

> [!IMPORTANT]
> Intune은 디바이스의 모든 규정 준수 평가에 대한 디바이스 체크 인 일정을 따릅니다. [디바이스 체크 인 일정에 대해 자세히 알아봅니다](https://docs.microsoft.com/intune/device-profile-troubleshoot#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned).

다양한 디바이스 준수 정책 상태의 설명:

- **준수**: 하나 이상의 디바이스 준수 정책 설정이 디바이스에서 적용되었습니다.

- **유예 기간:** 디바이스에 하나 이상의 디바이스 준수 정책 설정이 대상으로 지정되었습니다. 그러나 사용자는 정책을 아직 적용하지 않았습니다. 즉 디바이스는 규정을 준수하지 않지만 관리자가 정의한 유예 기간에 있습니다.

  - [비규격 디바이스에 대한 작업](actions-for-noncompliance.md)에 대해 자세히 알아보세요.

- **평가되지 않음**: 새로 등록된 디바이스에 대한 초기 상태입니다. 이 상태의 가능한 원인은 다음과 같습니다.

  - 디바이스가 규정 준수 정책이 할당되지 않고 규정 준수 여부를 확인하는 트리거가 없습니다.
  - 규정 준수 정책을 마지막으로 업데이트한 후 디바이스를 체크 인하지 않았습니다.
  - 특정 사용자에게 연결되지 않은 디바이스, 예:
    - 사용자 선호도가 없는 Apple의 DEP(장비 등록 프로그램)를 통해 구매한 iOS 디바이스
    - Android 키오스크 또는 Android Enterprise 전용 디바이스
  - 디바이스를 DEM(디바이스 등록 관리자) 계정을 사용하여 등록했습니다.

- **비준수:** 하나 이상의 디바이스 준수 정책 설정을 디바이스에서 적용하지 못했습니다. 또는 사용자가 정책을 준수하지 않았습니다.

- **디바이스 동기화 안 됨**: 다음 중 하나의 이유로 인해 디바이스에서 디바이스 준수 정책 상태를 보고하지 못했습니다.

  - **알 수 없음**: 디바이스가 오프라인이거나 다른 이유로 인해 Intune 또는 Azure AD와 통신하지 못했습니다.

  - **오류**: 디바이스가 Intune 및 Azure AD와 통신하지 못했으며 이유가 포함된 오류 메시지를 받았습니다.

> [!IMPORTANT]
> Intune에 등록되었지만 디바이스 준수 정책의 대상으로 지정되지 않은 디바이스는 이 보고서에서 **준수** 버킷 아래에 포함됩니다.

#### <a name="drill-down-for-more-details"></a>자세한 내용 드릴다운

**디바이스 준수 상태** 차트에서 상태를 선택합니다. 예를 들어 **비준수** 상태를 선택합니다.

![비준수 상태 선택](./media/compliance-policy-monitor/select-not-compliant-status.png)

운영 체제 플랫폼, 마지막 체크 인 날짜 등을 포함하여 해당 상태의 디바이스에 대한 자세한 정보를 보여줍니다. 

![해당 특정 상태의 디바이스에 대한 자세한 정보를 보여주는 대시보드 이미지](./media/compliance-policy-monitor/drill-down-details.png)

특정 사용자가 소유하는 모든 디바이스를 보려는 경우 사용자의 이메일을 입력하여 차트 보고서를 필터링할 수도 있습니다.

#### <a name="filter-and-columns"></a>필터 및 열

![차트에서 결과를 변경하려는 필터 및 열 선택](./media/compliance-policy-monitor/filter-columns.png)

**필터** 단추를 선택하는 경우 준수 상태, 무단 해제 디바이스 등을 포함한 더 많은 옵션과 함께 필터 플라이아웃이 열립니다. 결과를 업데이트하려는 필터를 **적용**합니다.

**열** 속성을 사용하여 차트 출력에서 열을 추가 또는 제거합니다. 예를 들어 **사용자 계정 이름**은 디바이스에서 등록된 이메일 주소를 표시할 수 있습니다. 결과를 업데이트하려는 열을 **적용**합니다.

#### <a name="device-details"></a>디바이스 세부 정보

차트에서 특정 디바이스를 선택한 다음, **디바이스 준수**를 선택합니다.

![특정 디바이스를 선택한 다음, 디바이스 준수를 선택하여 적용된 준수 정책을 확인합니다.](./media/compliance-policy-monitor/see-policies-applied-specific-device.png)

여기서는 해당 디바이스에 적용된 디바이스 준수 정책 설정에 대한 자세한 정보를 제공합니다. 특정 정책을 선택하면 정책에서 모든 설정을 보여줍니다.

### <a name="devices-without-compliance-policy"></a>준수 정책 없는 디바이스
**디바이스 준수** > **개요**에서 보고서는 할당된 준수 정책이 없는 디바이스를 식별합니다.

![준수 정책이 없는 디바이스 확인](./media/compliance-policy-monitor/devices-without-policies.png)

타일을 선택하면 준수 정책이 없는 모든 디바이스를 표시합니다. 또한 디바이스의 사용자, 정책 배포 상태 및 디바이스 모델을 보여줍니다.

#### <a name="what-you-need-to-know"></a>기억해야 하는 사항

- **할당된 준수 정책이 없는 디바이스 표시** 보안 설정을 사용하여 준수 정책이 없는 디바이스를 식별하는 것은 중요합니다. 최소 하나 이상의 준수 정책을 장치에 할당할 수 있습니다.

  보안 설정은 Intune 포털에서 구성할 수 있습니다. **디바이스 준수** > **준수 정책 설정**을 선택합니다. 그런 다음, **할당된 준수 정책이 없는 디바이스 표시**를 **준수** 또는 **비준수**로 설정합니다. 

  [Intune 서비스에서 보안 강화](https://blogs.technet.microsoft.com/intunesupport/2018/02/09/updated-upcoming-security-enhancements-in-the-intune-service/)를 자세히 읽어보세요.

- 모든 유형의 준수 정책이 할당된 사용자는 디바이스 플랫폼에 관계 없이 보고서에 표시되지 않습니다. 예를 들어 Android 디바이스를 사용하여 Windows 준수 정책을 사용자에게 할당한 경우 디바이스는 보고서에 표시되지 않습니다. 그러나 Intune은 해당 Android 디바이스를 비준수로 간주합니다. 문제를 방지하려면 각 디바이스 플랫폼에 대한 정책을 만들어 모든 사용자에게 배포하는 것 좋습니다.

### <a name="per-policy-device-compliance-report"></a>정책별 디바이스 준수 보고서

**디바이스 준수** > **정책 준수** 보고서는 정책 및 준수 및 비준수의 디바이스 수를 표시합니다. 

![정책의 목록, 해당 정책에 대한 준수 및 비준수 디바이스의 수 확인](./media/compliance-policy-monitor/idc-8.png)

특정 정책을 선택하면 해당 준수 정책에서 대상으로 지정한 각 디바이스에 대한 **준수 상태**, **사용자의 이메일 별칭**, **디바이스 모델** 및 **위치**를 볼 수 있습니다.

## <a name="setting-compliance-report"></a>준수 보고서 설정

**디바이스 준수** > **준수 설정** 보고서에서는 준수 설정별, 각 준수 상태에 속한 디바이스의 총 수를 보여줍니다. 모든 준수 정책의 모든 디바이스 준수 정책 설정, 디바이스 설정이 적용되는 플랫폼 및 비준수 디바이스의 수를 표시합니다.

![다른 정책에서 모든 설정의 목록 확인](./media/compliance-policy-monitor/idc-10.png)

특정 설정을 선택하면 해당 설정에서 대상으로 지정한 각 디바이스에 대한 **준수 상태**, **사용자의 이메일 별칭**, **디바이스 모델** 및 **위치**를 볼 수 있습니다.

> [!NOTE]
> Azure AD에 가입된 Windows 10 디바이스는 시스템 계정을 준수하지 않는 사용자로 표시할 수 있습니다. 이는 예상되는 동작이고 전체 디바이스 준수에 영향을 주지 않습니다. 

## <a name="view-status-of-device-policies"></a>디바이스 정책 상태 보기

플랫폼에서 사용자 정책의 다양한 상태를 확인할 수 있습니다. 예를 들어 macOS 준수 정책이 있습니다. 이 정책의 영향을 받는 디바이스를 확인하고 충돌 또는 오류가 있는지 알고 싶습니다.

이 기능은 디바이스 상태 보고에 포함됩니다.

1. **디바이스 준수** > **정책**을 선택합니다. 정책이 할당된 경우 플랫폼 및 자세한 세부 정보를 포함하여 정책 목록이 표시됩니다.
2. 정책 > **개요**를 선택합니다. 이 보기에서 정책 할당은 다음 상태를 포함합니다.

    - 성공: 정책이 적용됩니다.
    - 오류: 정책을 적용하지 못했습니다. 메시지는 일반적으로 설명으로 연결되는 오류 코드와 함께 표시됩니다. 
    - 충돌: 두 설정이 같은 디바이스에 적용되고, Intune에서 충돌을 해결할 수 없습니다. 관리자가 검토해야 합니다.
    - 보류 중: 아직 정책을 받기 위해 디바이스가 Intune을 사용하여 체크 인되지 않았습니다. 
    - 해당 없음: 디바이스가 치가 정책을 받을 수 없습니다. 예를 들어 정책이 iOS 11.1에 관련된 설정을 업데이트하지만, 디바이스에서 iOS 10이 사용되고 있습니다. 

3. 이 정책을 사용하여 디바이스의 세부 정보를 확인하려면 상태 중 하나를 선택합니다. 예를 들어 **성공**을 선택합니다. 다음 창에서 디바이스 이름 및 배포 상태를 포함한 특정 디바이스 세부 정보가 나열됩니다.

## <a name="how-intune-resolves-policy-conflicts"></a>Intune에서 정책 충돌을 해결하는 방법
정책 충돌은 디바이스에 여러 Intune 정책을 적용할 때 발생할 수 있습니다. 정책 설정이 겹치면 Intune에서는 다음 규칙을 사용하여 충돌을 해결합니다.

- Intune 구성 정책과 준수 정책에 충돌하는 설정이 있는 경우 구성 정책 설정보다 준수 정책 설정이 우선합니다. 이 문제는 구성 정책 설정이 더 안전하더라도 발생합니다.

- 여러 준수 정책을 배포한 경우 Intune은 이러한 정책 중 가장 안전한 정책을 사용합니다.
