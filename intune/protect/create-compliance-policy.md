---
title: Microsoft Intune에서 디바이스 준수 정책 만들기 - Azure | Microsoft Docs
description: 디바이스 준수 정책 만들기, 상태 및 심각도 수준의 개요, InGracePeriod 상태 사용, 조건부 액세스 작업, 할당된 정책 없이 디바이스 처리 및 Microsoft Intune에서 Azure Portal과 클래식 포털의 준수 차이
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76998c32f09b20e624359cc8a38231e14a70399b
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72786070"
---
# <a name="create-a-compliance-policy-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 준수 정책 만들기

디바이스 준수 정책은 Intune을 사용하여 조직의 리소스를 보호할 때 핵심적인 기능입니다. Intune에서 디바이스가 규정을 준수하는 것으로 간주되기 위해 충족해야 하는 규칙 및 설정(예: 최소 OS 버전)을 만들 수 있습니다. 디바이스가 규정을 준수하지 않을 경우 [조건부 액세스](conditional-access.md)를 사용하여 데이터 및 리소스에 대한 액세스를 차단할 수 있습니다.

또한 비준수에 대한 조치를 취할 수도 있습니다(예: 사용자에게 알림 메일 보내기). 준수 정책의 역할 개요 및 준수 정책 사용 방법에 대해서는 [디바이스 준수 시작](device-compliance-get-started.md)을 참조하세요.

이 문서의 내용은 다음과 같습니다.

- 준수 정책을 만들기 위한 필수 구성 요소 및 단계를 나열합니다.
- 사용자 및 디바이스 그룹에 정책을 할당하는 방법을 보여 줍니다.
- 정책을 “필터링”하는 범위 태그를 포함한 추가 기능과 비준수 디바이스에서 수행할 수 있는 단계를 설명합니다.
- 디바이스가 정책 업데이트를 받는 체크 인 새로 고침 주기 시간을 나열합니다.

## <a name="before-you-begin"></a>시작하기 전에

디바이스 준수 정책을 사용하려면 다음을 확인합니다.

- 다음 구독을 사용합니다.

  - Intune
  - 조건부 액세스를 사용하는 경우 Azure AD(Active Directory) 프리미엄 버전이 필요합니다. [Azure Active Directory 가격 책정](https://azure.microsoft.com/pricing/details/active-directory/)에는 다양한 버전에 포함되는 사항이 나열됩니다. Intune 준수에는 Azure AD가 필요하지 않습니다.

- 지원되는 플랫폼을 사용합니다.

  - Android 디바이스 관리자
  - Android Enterprise
  - iOS
  - macOS
  - Windows 10
  - Windows 8.1
  - Windows Phone 8.1

- Intune에서 디바이스 등록(준수 상태를 확인하려면 필요함)

- 한 사용자에게 디바이스를 등록하거나 기본 사용자 없이 등록합니다. 여러 사용자에게 등록된 디바이스는 지원되지 않습니다.

## <a name="create-the-policy"></a>정책 만들기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **디바이스 준수**를 선택합니다. 다음과 같은 옵션을 선택할 수 있습니다.

    - **개요**: 준수 디바이스, 평가되지 않는 디바이스 등 디바이스의 요약 및 개수를 보여 줍니다. 또한 정책 및 정책의 개별 설정을 나열합니다. [Intune 디바이스 준수 정책 모니터링](compliance-policy-monitor.md)에서는 몇 가지 유용한 정보를 제공합니다.
    - **관리**: 디바이스 정책을 만들고, [알림](quickstart-send-notification.md)을 비준수 디바이스에 보내고, [네트워크 펜싱](use-network-locations.md)을 사용하도록 설정합니다.
    - **모니터**: 디바이스, 설정 및 정책 수준에서 디바이스의 준수 상태를 확인합니다. [Intune 디바이스 준수 정책 모니터링](compliance-policy-monitor.md)은 좋은 리소스입니다. 또한 로그를 확인하고 디바이스의 위협 에이전트 상태를 확인합니다.
    - **설치**: [기본 제공 준수 정책](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)을 사용하고, [Microsoft Defender ATP(Advanced Threat Protection)](advanced-threat-protection.md)를 사용하도록 설정하고, [Mobile Threat Defense 커넥터](mobile-threat-defense.md)를 추가하고, [Jamf](conditional-access-integrate-jamf.md)를 사용합니다.

3. **정책** > **정책 만들기**를 선택합니다. 다음 속성을 입력합니다.

   - **이름**: 정책에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 예를 들어 **iOS 무단 해제 디바이스를 비준수로 표시**는 좋은 정책 이름입니다.  

   - **설명**: 정책에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.  

   - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.
     - **Android 디바이스 관리자**
     - **Android Enterprise**
     - **iOS/iPadOS**
     - **macOS**
     - **Windows Phone 8.1**
     - **Windows 8.1 이상**
     - **Windows 10 이상**

     *Android Enterprise*의 경우 **프로필 유형**을 선택해야 합니다.
     - **디바이스 소유자**
     - **회사 프로필**

   - **설정**: 다음 문서에서는 각 플랫폼의 설정을 나열 및 설명합니다.
     - [Android 디바이스 관리자](compliance-policy-create-android.md)
     - [Android Enterprise](compliance-policy-create-android-for-work.md)
     - [iOS/iPadOS](compliance-policy-create-ios.md)
     - [macOS](compliance-policy-create-mac-os.md)
     - [Windows Phone 8.1, Windows 8.1 이상](compliance-policy-create-windows-8-1.md)
     - [Windows 10 이상](compliance-policy-create-windows.md)  

   - **위치**’(Android 디바이스 관리자)’:  정책에서 디바이스의 위치에 따라 규정 준수를 강제 적용할 수 있습니다. 기존 위치에서 선택합니다. 아직 위치가 없나요? Intune에서 [위치(네트워크 펜스) 사용](use-network-locations.md)에는 몇 가지 지침이 제공됩니다.  

   - **비준수에 대한 작업**: 준수 정책을 따르지 않는 디바이스의 경우 자동으로 적용할 작업 시퀀스를 추가할 수 있습니다. 디바이스가 비준수로 표시되면 일정을 변경할 수 있습니다(예: 하루 후). 디바이스가 준수하지 않으면 사용자에게 이메일을 보내는 두 번째 작업을 구성할 수도 있습니다.
    
     [비규격 디바이스에 대한 작업 추가](actions-for-noncompliance.md)는 사용자에게 알림 이메일을 생성하는 작업을 비롯한 자세한 정보를 제공합니다.

     예를 들어 위치 기능을 사용하고 규정 준수 정책에서 위치를 추가합니다. 비준수에 대한 기본 작업은 하나 이상의 위치를 선택하는 경우에 적용됩니다. 디바이스가 선택한 위치에 연결되지 않으면 즉시 비준수로 간주됩니다. 사용자에게 하루와 같은 유예 기간을 지정할 수 있습니다.

   - **범위(태그)** : 범위 태그는 영업, HR, 모든 US-NC 직원 등과 같은 특정 그룹으로 정책을 할당 및 필터링할 수 있는 좋은 방법입니다. 설정을 추가한 후 준수 정책에 범위 태그를 추가할 수도 있습니다. [범위 태그를 사용하여 정책 필터링](../fundamentals/scope-tags.md)은 좋은 리소스입니다.

4. 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 정책이 만들어지고 목록에 표시됩니다. 다음으로, 그룹에 정책을 할당합니다.

## <a name="assign-the-policy"></a>정책 할당

정책이 만들어지면 다음 단계에서 그룹에 정책을 할당합니다.

1. 직접 만든 정책을 선택합니다. 기존 정책은 **디바이스 준수** > **정책**에 있습니다.
2. 정책 > **할당**을 선택합니다. Azure AD(Active Directory) 보안 그룹을 포함하거나 제외할 수 있습니다.
3. **선택된 그룹**을 선택하면 Azure AD 보안 그룹이 표시됩니다. 이 정책을 적용할 그룹을 선택한 후 **저장**을 선택하여 정책을 배포합니다.

정책의 대상으로 지정된 사용자 또는 디바이스는 Intune을 사용하여 체크 인할 때 준수 여부가 평가됩니다.

### <a name="evaluate-how-many-users-are-targeted"></a>대상으로 지정된 사용자 수 평가

정책을 할당하면 영향을 받는 사용자 수를 **평가**할 수도 있습니다. 이 기능은 사용자 수를 계산하며, 디바이스 수는 계산하지 않습니다.

1. Intune에서 **디바이스 준수** > **정책**을 선택합니다.
2. 정책을 선택한 후 **할당** > **평가**를 선택합니다. 메시지는 이 정책의 대상이 되는 사용자 수를 보여 줍니다.

**평가** 단추가 회색으로 표시되면 정책이 하나 이상의 그룹에 할당되었는지 확인합니다.

<!-- ## Actions for noncompliance

For devices that don't meet your compliance policies, you can add a sequence of actions to apply automatically. You can change the schedule when the device is marked non-compliant, such as after one day. You can also configure a second action that sends an email to the user when the device isn't compliant.

[Add actions for noncompliant devices](actions-for-noncompliance.md) provides more information, including creating a notification email to your users.

For example, you're using the Locations feature, and add a location in a compliance policy. The default action for noncompliance applies when you select at least one location. If the device isn't connected to the selected locations, it's immediately considered not compliant. You can give your users a grace period, such as one day.

## Scope tags

Scope tags are a great way to assign and filter policies to specific groups, such as Sales, HR, All US-NC employees, and so on. After you add the settings, you can also add a scope tag to your compliance policies. [Use scope tags to filter policies](../fundamentals/scope-tags.md) is a good resource.
-->

## <a name="refresh-cycle-times"></a>주기 시간 새로 고침

Intune은 다양한 새로 고침 주기를 사용하여 준수 정책에 대한 업데이트를 확인합니다. 최근 등록된 디바이스인 경우 다음과 같이 체크 인이 더 자주 실행됩니다. [정책 및 프로필 새로 고침 주기](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)에는 예상 새로 고침 시간이 나열됩니다.

언제든 사용자는 회사 포털 앱을 열고 디바이스를 동기화하여 즉시 정책 업데이트를 확인할 수 있습니다.

### <a name="assign-an-ingraceperiod-status"></a>InGracePeriod 상태 할당

준수 정책에 대한 InGracePeriod 상태는 값입니다. 이 값은 디바이스의 유예 기간과 해당 준수 정책에 대한 디바이스의 실제 상태의 조합에 의해 결정됩니다.

특히 디바이스에 할당된 준수 정책에 대한 NonCompliant 상태가 있고,

- 디바이스에 할당된 유예 기간이 없는 경우 준수 정책에 할당된 값은 NonCompliant입니다.
- 디바이스의 유예 기간이 만료된 경우 준수 정책에 할당된 값은 NonCompliant입니다.
- 디바이스에 향후 유예 기간이 있는 경우 준수 정책에 할당된 값은 InGracePeriod입니다.

다음 표에 이러한 지점이 요약되어 있습니다.

|실제 준수 상태|할당된 유예 기간의 값|유효 준수 상태|
|---------|---------|---------|
|NonCompliant |할당된 유예 시간 없음 |NonCompliant |
|NonCompliant |어제 날짜|NonCompliant|
|NonCompliant |향후 날짜|InGracePeriod|

디바이스 준수 정책 모니터링에 대한 자세한 내용은 [Intune 디바이스 준수 정책 모니터링](compliance-policy-monitor.md)을 참조하세요.

### <a name="assign-a-resulting-compliance-policy-status"></a>결과 준수 정책 상태 할당

디바이스에 여러 준수 정책이 있고 디바이스에 두 개 이상의 할당된 준수 정책에 대한 다양한 준수 상태가 있는 경우, 단일 결과 준수 상태가 할당됩니다. 이 할당은 각 호환성 상태에 할당된 개념적 심각도 수준을 기반으로 합니다. 각 호환성 상태에는 다음과 같은 심각도 수준이 있습니다.

|상태  |심각도  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|규정|3|
|InGracePeriod|4|
|NonCompliant|5|
|오류|6|

디바이스에 여러 준수 정책이 있는 경우 모든 정책의 가장 높은 수준의 심각도가 해당 디바이스에 할당됩니다.

예를 들어, 디바이스에는 할당된 준수 정책이 알 수 없는 상태 하나(심각도 = 1), 호환 상태 하나(심각도 = 3), InGracePeriod 상태 하나(심각도 = 4)와 같이 세 가지가 있습니다. InGracePeriod 상태는 가장 높은 심각도 수준입니다. 따라서 세 개의 정책 모두에 InGracePeriod 준수 상태가 있습니다.

## <a name="next-steps"></a>다음 단계

[사용자 정책을 모니터링](compliance-policy-monitor.md)합니다.
