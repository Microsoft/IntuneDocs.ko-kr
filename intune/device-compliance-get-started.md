---
title: Microsoft Intune에서 장치 준수 정책 - Azure | Microsoft Docs
description: 장치 준수 정책을 사용하기 위한 요구 사항, 상태 및 심각도 수준의 개요, InGracePeriod 상태 사용, 조건부 액세스 작업, 할당된 정책 없이 장치 처리 및 Microsoft Intune에서 Azure Portal과 클래식 포털의 준수 차이
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/17/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a70b6369bab130918bad472172995e6296ee4a6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49391572"
---
# <a name="get-started-with-device-compliance-policies-in-intune"></a>Intune에서 장치 준수 정책 시작

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

준수 요구 사항은 기본적으로 장치 PIN을 요구하거나 암호화를 요구하는 등의 규칙입니다. 장치 준수 정책은 장치가 준수되는 것으로 간주하기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 이러한 규칙은 다음과 같습니다.

- 장치에 액세스하는 데 암호 사용

- 암호화

- 장치의 무단 해제 또는 루팅 여부

- 필요한 최소 OS 버전

- 허용된 최대 OS 버전

- 장치가 Mobile Threat Defense 수준 이하여야 함

장치 준수 정책을 사용하여 장치에서 준수 상태를 모니터링할 수도 있습니다.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

-   When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

-   3 days after initial noncompliance state, a follow up reminder is sent to the user.

-   5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

-   7 days after initial noncompliance state, access to company resources is blocked. This requires that you have conditional access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement conditional access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="prerequisites"></a>전제 조건
장치 준수 정책을 사용하려면 다음 사항이 필요합니다.

- 다음 구독을 사용합니다.

  - Intune
  - Azure AD(Active Directory) Premium

- 지원되는 플랫폼을 사용합니다.

  - Android
  - iOS
  - macOS(미리 보기)
  - Windows 8.1
  - Windows Phone 8.1
  - Windows 10

- 준수 상태를 보고하려면 장치가 Intune에 등록되어야 합니다.

- 한 사용자에 등록된 장치 또는 기본 사용자가 없는 장치는 지원됩니다. 하지만 다중 사용자 컨텍스트는 지원되지 않습니다.

## <a name="how-intune-device-compliance-policies-work-with-azure-ad"></a>Azure AD에서 Intune 장치 준수 정책이 사용되는 방식

장치가 Intune에 등록되면 Azure AD 등록 프로세스가 시작되고 장치 특성이 Azure AD로 업데이트됩니다. 주요 정보 중 하나는 장치 준수 상태입니다. 이 장치 준수 상태는 조건부 액세스 정책에서 이메일 및 기타 회사 리소스에 대한 액세스를 차단하거나 허용하는 데 사용됩니다.

[Azure AD 등록 프로세스](https://docs.microsoft.com/azure/active-directory/device-management-introduction)에 자세한 정보가 나와 있습니다.

### <a name="assign-a-resulting-device-configuration-profile-status"></a>결과 장치 구성 프로필 상태 할당

장치에 여러 구성 프로필이 있고 장치에 두 개 이상의 할당된 구성 프로필에 대한 다양한 준수 상태가 있는 경우 단일 결과 준수 상태가 할당됩니다. 이 할당은 각 호환성 상태에 할당된 개념적 심각도 수준을 기반으로 합니다. 각 호환성 상태에는 다음과 같은 심각도 수준이 있습니다.

|상태  |심각도  |
|---------|---------|
|Pending     |1|
|성공     |2|
|Failed     |3|
|오류     |4|

장치에 여러 구성 프로필이 있는 경우 모든 프로필의 가장 높은 수준의 심각도가 해당 장치에 할당됩니다.

예를 들어, 장치에 할당된 프로필이 보류 중 상태 하나(심각도 = 1), 성공 상태 하나(심각도 = 2), 오류 상태 하나(심각도 = 4)와 같이 세 가지가 있습니다. 오류 상태가 가장 높은 심각도 수준이므로 세 개의 프로필 모두에 오류 준수 상태가 있습니다.

### <a name="assign-an-ingraceperiod-status"></a>InGracePeriod 상태 할당

준수 정책에 대한 InGracePeriod 상태는 값입니다. 이 값은 장치의 유예 기간과 해당 준수 정책에 대한 장치의 실제 상태의 조합에 의해 결정됩니다.

특히 장치에 할당된 준수 정책에 대한 NonCompliant 상태가 있고,

- 장치에 할당된 유예 기간이 없는 경우 준수 정책에 할당된 값은 NonCompliant입니다.
- 장치에 유예 기간이 만료된 경우 준수 정책에 할당된 값은 NonCompliant입니다.
- 장치에 향후 유예 기간이 있는 경우 준수 정책에 할당된 값은 InGracePeriod입니다.

다음 표에 이러한 지점이 요약되어 있습니다.

|실제 준수 상태|할당된 유예 기간의 값|유효 준수 상태|
|---------|---------|---------|
|NonCompliant |할당된 유예 시간 없음 |NonCompliant |
|NonCompliant |어제 날짜|NonCompliant|
|NonCompliant |향후 날짜|InGracePeriod|

장치 준수 정책 모니터링에 대한 자세한 내용은 [Intune 장치 준수 정책 모니터링](compliance-policy-monitor.md)을 참조하세요.

### <a name="assign-a-resulting-compliance-policy-status"></a>결과 준수 정책 상태 할당

장치에 여러 준수 정책이 있고 장치에 두 개 이상의 할당된 준수 정책에 대한 다양한 준수 상태가 있는 경우, 단일 결과 준수 상태가 할당됩니다. 이 할당은 각 호환성 상태에 할당된 개념적 심각도 수준을 기반으로 합니다. 각 호환성 상태에는 다음과 같은 심각도 수준이 있습니다.

|상태  |심각도  |
|---------|---------|
|Unknown     |1|
|NotApplicable     |2|
|규정|3|
|InGracePeriod|4|
|NonCompliant|5|
|오류|6|

장치에 여러 준수 정책이 있는 경우 모든 정책의 가장 높은 수준의 심각도가 해당 장치에 할당됩니다.

예를 들어, 장치에는 할당된 준수 정책이 알 수 없는 상태 하나(심각도 = 1), 호환 상태 하나(심각도 = 3), InGracePeriod 상태 하나(심각도 = 4)와 같이 세 가지가 있습니다. InGracePeriod 상태는 가장 높은 심각도 수준이므로 세 개의 정책 모두에 InGracePeriod 준수 상태가 있습니다.

## <a name="ways-to-use-device-compliance-policies"></a>장치 준수 정책을 사용하는 방법

#### <a name="with-conditional-access"></a>조건부 액세스 사용
정책 규칙을 준수하는 장치의 경우 이메일 및 기타 회사 리소스에 해당 장치 액세스를 제공할 수 있습니다. 장치가 정책 규칙을 따르는 않는 경우 회사 리소스에 대한 액세스를 가져오지 않습니다. 이를 조건부 액세스라고 합니다.

#### <a name="without-conditional-access"></a>조건부 액세스 사용 안 함
또한 조건부 액세스 없이 장치 준수 정책을 사용할 수 있습니다. 준수 정책을 독립적으로 사용하는 경우 대상 장치는 평가되고 준수 상태와 함께 보고됩니다. 예를 들어 암호화되지 않은 장치의 수나 무단 해제 또는 루팅된 장치에 대한 보고서를 가져올 수 있습니다. 조건부 액세스 없이 준수 정책을 사용하는 경우 회사 리소스에 대한 액세스 제한이 없습니다.

## <a name="ways-to-deploy-device-compliance-policies"></a>장치 준수 정책을 배포하는 방법
준수 정책을 사용자 그룹의 사용자 또는 장치 그룹의 장치에 배포할 수 있습니다. 준수 정책을 사용자에게 배포하면 사용자의 모든 장치에서 준수가 확인됩니다. Windows 10 버전 1803 이상 장치에서 기본 사용자가 장치를 등록하지 않은 *경우* 장치 그룹에 배포하는 것이 좋습니다. 이 시나리오에서 장치 그룹을 사용하면 준수 보고에 도움이 됩니다.

기본 **준수 정책 설정**(Azure Portal > 장치 준수)에는 다음이 포함됩니다.

- **준수 정책 없이 장치를 다음으로 표시**: 이 속성에는 두 개의 값이 있습니다.

  - **준수**: 보안 기능 해제
  - **비준수**(기본값): 보안 기능 켜기

  장치에 할당된 준수 정책이 없으면 이 장치는 준수하지 않음으로 간주됩니다. 기본적으로 장치는 **준수**로 표시됩니다. 조건부 액세스를 사용하는 경우 **비준수**로 설정을 변경하는 것이 좋습니다. 정책이 할당되지 않아 최종 사용자가 준수하지 않으면, 회사 포털에 `No compliance policies have been assigned`가 나열합니다.

- **향상된 탈옥 검색**: 이 설정을 사용하도록 지정하면 iOS 장치에서 Intune으로 더 자주 체크 인할 수 있습니다. 이 속성을 사용하면 장치의 위치 서비스를 사용하고 배터리 사용에 영향을 줍니다. 사용자 위치 데이터는 Intune에서 저장되지 않습니다.

  이 설정을 사용하면 장치를 다음과 같이 설정해야 합니다.
  - OS 수준에서 위치 서비스 사용
  - 회사 포털에서 위치 서비스를 사용하도록 허용
  - 최소 72시간에 한 번 Intune에 해당 탈옥 상태를 평가 및 보고합니다. 그렇지 않은 경우 장치가 준수하지 않음으로 표시됩니다. 평가는 회사 포털 앱을 열거나 장치를 500미터 이상 물리적으로 이동하면 트리거됩니다.

- **준수 상태 유효 기간(일)**: 장치가 모든 수신된 준수 정책에 대한 상태를 보고하는 시간 간격을 입력합니다. 이 기간 내에 상태를 반환하지 않는 장치는 비준수로 처리됩니다. 기본값은 30일입니다.

모든 장치에는 **기본 장치 준수 정책**(Azure Portal > 장치 준수 > 정책 준수)이 있습니다. 이 기본 정책을 사용하여 이러한 설정을 모니터링합니다.

정책이 배포된 후 모바일 장치가 정책을 수신하기까지 걸리는 시간에 대해 알아보려면 [ 장치 프로필 문제 해결](device-profile-troubleshoot.md#how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned)을 참조하세요.

준수 보고서는 장치의 상태를 확인하는 좋은 방법입니다. [준수 정책 모니터링](compliance-policy-monitor.md)에서 지침을 참조하세요.

### <a name="actions-for-noncompliance"></a>비준수에 대한 작업
준수 정책 기준을 충족하지 않는 장치에 적용되는 작업을 시간순으로 구성할 수 있습니다. [비준수에 대한 작업 자동화](actions-for-noncompliance.md)에 설명된 대로 이러한 비준수에 대한 작업을 자동화할 수 있습니다.

## <a name="azure-classic-portal-vs-azure-portal"></a>Azure 클래식 포털 대 Azure 포털

Azure Portal에서 장치 준수 정책을 사용하는 경우 주요 차이점은 다음과 같습니다.

- Azure Portal에서 준수 정책은 지원되는 각 플랫폼에 대해 개별적으로 생성됩니다.
- Azure 클래식 포털에서는 하나의 장치 준수 정책이 지원되는 모든 플랫폼에 공통적으로 적용됩니다.

<!--- -   In the Azure portal, you have the ability to specify actions and notifications that are intiated when a device is determined to be noncompliant. This ability does not exist in the Intune admin console.

-   In the Azure portal, you can set a grace period to allow time for the end-user to get their device back to compliance status before they completely lose the ability to get company data on their device. This is not available in the Intune admin console.--->

## <a name="device-compliance-policies-in-the-classic-portal-and-azure-portal"></a>클래식 포털과 Azure Portal의 장치 준수 정책

[클래식 포털](https://manage.microsoft.com)에서 생성된 장치 준수가 [Azure Portal](https://portal.azure.com)에는 표시되지 않습니다. 그러나 해당 정책은 여전히 사용자를 대상으로 하며 클래식 포털을 통해 관리할 수 있습니다.

Azure Portal에서 장치 준수와 관련된 기능을 사용하려는 경우 Azure Portal에서 새로운 장치 준수 정책을 만들어야 합니다. 클래식 포털에서도 장치 준수 정책을 할당받은 사용자에게 Azure Portal의 장치 준수 정책을 할당하는 경우 Azure Portal의 장치 준수 정책이 클래식 포털에서 만든 정책보다 우선합니다.

## <a name="next-steps"></a>다음 단계

- 다음 플랫폼에 대한 장치 준수 정책을 만듭니다.

  - [OWA(Outlook Web Access)](compliance-policy-create-android.md)
  - [Android 회사 프로필](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows](compliance-policy-create-windows.md)

- Intune 데이터 웨어하우스 정책 엔터티에 대한 자세한 내용은 [정책 엔터티에 대한 참조](reports-ref-policy.md)를 확인하세요.
