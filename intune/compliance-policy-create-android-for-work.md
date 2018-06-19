---
title: Microsoft Intune에서 Android for Work 장치 준수 정책 만들기 - Azure | Microsoft Docs
description: Android for Work 장치에 대한 Microsoft Intune 장치 준수 정책을 만들거나 구성합니다. 탈옥 상태의 장치 허용, 허용되는 위협 수준 설정, Google Play 확인, 최소 및 최대 운영 체제 버전 입력, 암호 요구 사항 선택, 테스트용으로 응용 프로그램 로드 허용 등을 수행합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/16/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c1d438aa7416b1629af7ab2b899afa06720e2b49
ms.sourcegitcommit: 6a9830de768dd97a0e95b366fd5d2f93980cee05
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34047988"
---
# <a name="add-a-device-compliance-policy-for-android-for-work-devices-in-intune"></a>Intune에서 Android for Work 장치에 대한 장치 준수 정책 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Android for Work에 대한 Intune 장치 준수 정책은 규격 장치로 간주되기 위해 충족해야 하는 규칙과 설정을 지정합니다. 이러한 정책을 조건부 액세스와 함께 사용하여 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다. 장치 보고서를 가져오고 비규격에 대한 조치를 취할 수도 있습니다. Intune Azure Portal에서 여러 플랫폼에 대한 장치 준수 정책을 만듭니다. 준수 정책 및 모든 필수 조건에 대한 자세한 내용은 [장치 준수 시작](device-compliance-get-started.md)을 참조하세요.

다음 표에서는 준수 정책을 조건부 액세스 정책과 함께 사용할 경우 비준수 설정을 관리하는 방법을 설명합니다.

--------------------------

|**정책 설정**| **Android for Work** |
| --- | --- |
| **PIN 또는 암호 구성** |  격리됨 |
| **장치 암호화** |  격리됨 |
| **무단 해제 또는 루팅된 장치** | 격리됨(설정 아님) |
| **메일 프로필** | 해당 없음 |
| **최소 OS 버전** | 격리됨 |
| **최대 OS 버전** | 격리됨 |
| **Windows 상태 증명** |해당 없음 |

**재구성됨** = 장치 운영 체제에서 준수를 적용하도록 요구합니다. (예를 들어 사용자에게 PIN을 설정하도록 강제합니다.)

**격리됨** = 장치 운영 체제에서 준수를 적용하도록 요구하지 않습니다. (예를 들어, Android 장치에서 사용자에게 장치를 암호화하도록 강제하지 않습니다.) 장치가 호환되지 않으면 다음 작업이 수행됩니다.

- 조건부 액세스 정책이 사용자에게 적용될 경우 장치가 차단됩니다.
- 회사 포털은 모든 준수 문제에 대해 사용자에게 알립니다.

## <a name="create-a-device-compliance-policy"></a>장치 준수 정책 만들기

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. **플랫폼**에서 **Android for Work**를 선택합니다. **설정 구성**을 선택하고 **장치 상태**, **장치 속성** 및 **시스템 보안** 설정을 입력합니다. 작업을 마쳤으면 **확인**, **만들기**를 차례로 선택합니다.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="device-health"></a>Device health

- **루팅 상태의 장치**: 이 설정을 사용하도록 설정하면 탈옥 상태의 장치가 비규격으로 평가됩니다.
- **장치가 장치 위협 수준이나 그 아래에 있어야 함**: 이 설정을 통해 Lookout MTP 솔루션의 위험 평가를 준수 조건으로 사용할 수 있습니다. 허용된 최대 위협 수준을 선택합니다.
  - **보안**: 이 옵션은 가장 안전하며, 장치가 어떠한 위협에도 노출되지 않았음을 의미합니다. 수준에 관계없이 위협이 발견된 장치는 규정 비준수로 평가됩니다.
  - **낮음**: 낮은 수준의 위협만 있는 경우 장치가 규정 준수로 평가됩니다. 더 높은 수준의 위협이 발생하면 장치는 규정 비준수 상태가 됩니다.
  - **보통**: 장치에 있는 위협이 낮거나 중간 수준인 경우 장치가 규정 준수로 평가됩니다. 높은 수준의 위협이 있는 것으로 감지되면 장치가 규정 비준수로 결정됩니다.
  - **높음**: 이 옵션은 최소 보안이며 모든 위협 수준을 허용합니다. 이 수준은 이 솔루션을 보고 용도로만 사용하는 경우에 유용할 수 있습니다.
- **Google Play 서비스가 구성됨**: Google Play 서비스 앱이 설치되어 사용할 수 있어야 합니다. Google Play 서비스는 보안 업데이트를 허용하며, 인증된 Google 장치의 많은 보안 기능에 대한 기본 수준 종속성입니다.
- **최신 보안 공급자**: 최신 보안 공급자가 알려진 취약성으로부터 장치를 보호할 수 있어야 합니다.
- **SafetyNet 장치 증명**: 충족해야 하는 [SafetyNet 증명](https://developer.android.com/training/safetynet/attestation.html) 수준을 입력합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**
  - **기본 무결성 확인**
  - **기본 무결성 및 인증된 장치 확인**

#### <a name="threat-scan-on-apps"></a>앱에서 위협 검색

회사 프로필(Android for Work)이 있는 장치에서, **앱에서 위협 검색** 설정은 구성 정책 설정으로 찾을 수 있습니다. 관리자는 장치에 대해 이 설정을 사용하도록 설정할 수 있습니다.

엔터프라이즈에서 Android 회사 프로필을 사용하는 경우 등록된 장치에 대해 **앱에서 위협 검색**을 사용하도록 설정할 수 있습니다. 장치 프로필을 설정하고 시스템 보안 설정이 필요합니다. 자세한 내용은 [Intune의 Android for Work 장치 제한 설정](device-restrictions-android-for-work.md)을 참조하세요.

## <a name="device-property-settings"></a>장치 속성 설정

- **최소 OS 버전**: 장치가 OS 최소 버전 요구 사항을 충족하지 못할 경우 비규격 장치로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 해당 장치를 업그레이드한 후 회사 리소스에 액세스할 수 있습니다.
- **최대 OS 버전**: 장치가 규칙에 있는 버전보다 최신 OS 버전을 사용하는 경우 회사 리소스에 대한 액세스가 차단됩니다. 그런 다음, IT 관리자에게 문의하라는 메시지가 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 장치에서 회사 리소스에 액세스할 수 없습니다.

## <a name="system-security-settings"></a>시스템 보안 설정

### <a name="password"></a>암호

- **모바일 장치의 잠금을 해제하는 데 암호 필요**: **필요**로 설정하면 사용자가 암호를 입력해야 장치에 액세스할 수 있습니다.
- **최소 암호 길이**: 사용자 암호에 포함해야 하는 최소 숫자 또는 문자 수를 입력합니다.
- **필수 암호 유형**: 암호에 숫자만 사용해야 하는지 또는 숫자와 기타 문자를 함께 사용해야 하는지 선택합니다. 다음 중에서 선택합니다.
  - **장치 기본값**
  - **낮은 보안 생체 인식**
  - **최소 숫자**
  - **복합 숫자**
  - **최소 알파벳**
  - **최소 영숫자**
  - **기호가 포함된 최소 영숫자**
- **암호를 요구하기 전까지 최대 비활성 시간(분)**: 사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.
- **암호 만료(일)**: 암호가 만료되기 전에 새로 만들어야 하는 일수를 선택합니다.
- **재사용을 방지하기 위한 이전 암호 수**: 사용할 수 없는 최근 암호 수를 입력합니다. 이 설정을 통해 사용자가 이전에 사용한 암호를 만들지 못하도록 제한할 수 있습니다.

### <a name="encryption"></a>암호화

- **모바일 장치 암호화 필요:** Android for Work 장치에는 암호화가 시행되므로 이 설정을 구성하지 않아도 됩니다.

### <a name="device-security"></a>장치 보안

- **알 수 없는 출처의 앱 차단**: Android for Work 장치는 알 수 없는 소스에서의 설치를 항상 제한하므로 이 설정을 구성할 필요가 없습니다.
- **회사 포털 앱 런타임 무결성**: 회사 포털 앱에 기본 런타임 환경이 설치되어 있고, 제대로 서명되었으며, 디버그 모드가 아니고, 알려진 소스에서 설치되었는지 확인합니다.
- **장치에서 USB 디버깅 차단**: Android for Work 장치에서는 USB 디버깅을 사용할 수 없으므로 이 설정을 구성할 필요가 없습니다.
- **최소 보안 패치 수준**: 장치에서 사용할 수 있는 가장 오래된 보안 패치 수준을 선택합니다. 최소한 이 패치 수준이 아닌 장치는 비규격 장치가 됩니다. `YYYY-MM-DD` 형식으로 날짜를 입력해야 합니다.

## <a name="assign-user-groups"></a>사용자 그룹 할당

1. 구성한 정책을 선택합니다. 기존 정책은 **장치 준수** > **정책**에 있습니다.
2. 정책을 선택한 다음 **할당**을 선택합니다. Azure AD(Active Directory) 보안 그룹을 포함하거나 제외할 수 있습니다.
3. **선택된 그룹**을 선택하면 Azure AD 보안 그룹이 표시됩니다. 이 정책을 적용할 사용자 그룹을 선택한 다음 **저장**을 선택하여 정책을 사용자에게 배포합니다.

사용자에게 정책을 적용했습니다. 정책의 대상이 되는 사용자가 사용하는 장치에 대한 규정 준수 여부가 평가됩니다.

## <a name="next-steps"></a>다음 단계
[메일 자동화 및 비규격 장치에 대한 작업 추가](actions-for-noncompliance.md)  
[Intune 장치 준수 정책 모니터링](compliance-policy-monitor.md)
