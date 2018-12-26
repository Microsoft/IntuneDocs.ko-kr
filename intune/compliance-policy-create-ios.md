---
title: Microsoft Intune에서 iOS 디바이스 규정 준수 정책 만들기 - Azure | Microsoft Docs
description: iOS 디바이스에 대한 Microsoft Intune 디바이스 준수 정책을 만들거나 구성하여 메일 계정 입력, 탈옥 상태의 디바이스 확인, 최소 및 최대 운영 체제 확인, 암호 길이 및 디바이스 비활성 기간을 비롯한 암호 제한 설정을 수행합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3cfb8222-d05b-49e3-ae6f-36ce1a16c61d
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 41ae1ffc17eee93b45f00e4eef5590f6a5d0b7b4
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112513"
---
# <a name="add-a-device-compliance-policy-for-ios-devices-in-intune"></a>Intune에서 iOS 디바이스에 대한 디바이스 준수 정책 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune iOS 디바이스 준수 정책은 iOS 디바이스가 준수하도록 충족해야 하는 규칙과 설정을 결정합니다. 조건부 액세스 정책을 사용하여 디바이스 준수 정책을 사용하는 경우 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다. 디바이스 보고서를 가져오 고 비준수에 대해 조치를 할 수 있습니다. Intune Azure Portal에서 각 플랫폼에 대한 디바이스 준수 정책을 만듭니다. 준수 정책 및 모든 필수 조건에 대한 자세한 내용은 [디바이스 준수 시작](device-compliance-get-started.md)을 참조하세요.

다음 표에서는 준수 정책을 조건부 액세스 정책과 함께 사용할 경우 비준수 설정을 관리하는 방법을 설명합니다.

---------------------------

| **정책 설정** | **iOS 8.0 이상** |
| --- | --- |
| **PIN 또는 암호 구성** | 재구성됨 |
| **장치 암호화** | 재구성됨(PIN 설정) |
| **무단 해제 또는 루팅된 장치** | 격리됨(설정 아님)
| **전자 메일 프로필** | 격리됨 |
|**최소 OS 버전** | 격리됨 |
| **최대 OS 버전** | 격리됨 |
| **Windows 상태 증명** | 해당 없음 |

---------------------------

**재구성됨** = 장치 운영 체제에서 준수를 적용하도록 요구합니다. (예를 들어 사용자에게 PIN을 설정하도록 강제합니다.)

**격리됨** = 장치 운영 체제에서 준수를 적용하도록 요구하지 않습니다. (예를 들어, Android 디바이스에서 사용자에게 디바이스를 암호화하도록 강제하지 않습니다.) 디바이스가 호환되지 않으면 다음 작업이 수행됩니다.

- 조건부 액세스 정책이 사용자에게 적용될 경우 디바이스가 차단됩니다.
- 회사 포털은 모든 준수 문제에 대해 사용자에게 알립니다.

## <a name="create-a-device-compliance-policy"></a>디바이스 준수 정책 만들기

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. **플랫폼**에서 **iOS**를 선택합니다. 
5. **설정 구성**을 선택하고 이 항목에 설명된 **메일**, **디바이스 상태**, **디바이스 속성** 및 **시스템 보안** 설정을 입력합니다. 작업을 마쳤으면 **확인**, **만들기**를 차례로 선택합니다.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
7. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="email"></a>메일

- **모바일 디바이스에 관리되는 메일 프로필이 있어야 함**: 필요로 설정할 경우 Intune에서 관리하는 메일 프로필이 없는 디바이스는 비규격으로 간주됩니다. 디바이스가 올바르게 대상으로 지정되지 않았거나 사용자가 디바이스에서 메일 계정을 수동으로 설정한 경우에는 디바이스에 관리되는 메일 프로필이 없을 수도 있습니다.

  디바이스는 다음과 같은 상황에서 비규격으로 간주됩니다.
  - 메일 프로필은 준수 정책의 대상으로 지정된 사용자 그룹 이외의 사용자 그룹에 배포됩니다.
  - 사용자가 디바이스에 배포된 Intune 메일 프로필과 일치하는 메일 계정을 이미 디바이스에서 설정했습니다. Intune은 사용자가 프로비전한 프로필을 덮어쓸 수 없으므로 이러한 프로필을 관리할 수 없습니다. 장치의 준수 상태를 유지하려면 사용자는 기존 메일 설정을 제거해야 합니다. 그런 다음 Intune이 관리되는 메일 프로필을 설치할 수 있습니다.

- **Intune에서 관리해야 하는 메일 프로필 선택**: **Intune에서 메일 계정을 관리해야 함** 설정을 선택할 경우 **선택**을 선택하여 Intune 메일 프로필을 지정합니다. 디바이스에 전자 메일 프로필이 있어야 합니다.

메일 프로필에 대한 자세한 내용은 [Microsoft Intune에서 메일 프로필을 사용하여 회사 메일에 대한 액세스 구성](email-settings-configure.md)을 참조하세요.

## <a name="device-health"></a>Device health

- **무단 해제된 디바이스**: 이 설정을 사용하도록 설정하면 무단 해제된 디바이스는 규정을 준수하지 않습니다.
- **디바이스를 디바이스 위협 수준 이하로 유지**(iOS 8.0 이상): 최대 위협 수준을 선택하여 디바이스를 비규격으로 표시합니다. 이 위협 수준을 초과하는 디바이스는 비규격으로 표시됩니다.
  - **보안**: 이 옵션은 디바이스가 어떠한 위협에도 노출되지 않았으므로 가장 안전합니다. 수준에 관계없이 위협이 발견된 디바이스는 규정 비준수로 평가됩니다.
  - **낮음**: 낮은 수준의 위협만 있는 경우 디바이스가 준수로 평가됩니다. 더 높은 수준의 위협이 발생하면 디바이스는 규정 비준수 상태가 됩니다.
  - **보통**: 디바이스의 기존 위협이 낮음 또는 보통 수준인 경우 디바이스가 준수로 평가됩니다. 높은 수준의 위협이 있는 것으로 감지되면 디바이스가 규정 비준수로 결정됩니다.
  - **높음**: 이 옵션은 최소 보안이며 모든 위협 수준을 허용합니다. 이 수준은 이 솔루션을 보고 용도로만 사용하는 경우에 유용할 수 있습니다.

## <a name="device-properties"></a>디바이스 속성

- **필요한 최소 OS**: 디바이스가 OS 최소 버전 요구 사항을 충족하지 못하면 비규격 디바이스로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 사용자는 디바이스를 업그레이드하도록 선택할 수 있습니다. 그런 다음 회사 리소스에 액세스할 수 있습니다.
- **허용된 최대 OS 버전**: 디바이스가 규칙에 지정된 버전 이상의 OS 버전을 사용하는 경우 회사 리소스에 대한 액세스가 차단됩니다. 그런 다음, 사용자에게는 IT 관리자에게 문의하라는 메시지가 표시됩니다. OS 버전 허용 규칙이 변경될 때까지 이 디바이스는 회사 리소스에 액세스할 수 없습니다.
- **최소 OS 빌드 버전**: Apple이 보안 업데이트를 게시하면 일반적으로 OS 버전이 아니라 빌드 번호가 업데이트됩니다. 이 기능을 사용하여 디바이스에 허용되는 최소 빌드 번호를 입력합니다. 이 규정 준수 확인은 iOS 8.0 이상을 실행하는 디바이스를 지원합니다. 
- **최대 OS 빌드 버전**: Apple이 보안 업데이트를 게시하면 일반적으로 OS 버전이 아니라 빌드 번호가 업데이트됩니다. 이 기능을 사용하여 디바이스에 허용되는 최대 빌드 번호를 입력합니다. 이 규정 준수 확인은 iOS 8.0 이상을 실행하는 디바이스를 지원합니다.

## <a name="system-security"></a>시스템 보안

### <a name="password"></a>암호

> [!NOTE]
> 준수 또는 구성 정책을 iOS 디바이스에 적용하면 사용자에게 15분마다 암호를 설정하라는 메시지가 표시됩니다. 사용자가 암호를 설정할 때까지 계속 메시지가 표시됩니다.

- **모바일 디바이스의 잠금을 해제하는 데 암호 필요**: **필요**를 선택하면 사용자가 디바이스에 액세스하려면 먼저 암호를 입력해야 합니다. 암호를 사용하는 iOS 디바이스는 암호화됩니다.
- **단순 암호**: **차단**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 단순 암호를 만들 수 없습니다. **구성되지 않음**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 암호를 만들 수 있습니다.
- **최소 암호 길이**: 암호에 포함해야 하는 최소 자릿수 또는 문자 수를 입력합니다.
- **필수 암호 유형**: 암호에 **숫자**만 사용해야 하는지 또는 숫자와 기타 문자(**영숫자**)를 함께 사용해야 하는지 선택합니다.
- **암호에 포함해야 하는 영숫자가 아닌 문자 수**: 암호에 포함해야 하는 특수 문자(&, #, %, ! 등)의 최소 개수를 입력합니다.

    더 큰 값을 설정하면 사용자는 더욱 복잡한 암호를 만들어야 합니다.

- **암호를 요구하기 전까지 최대 비활성 시간(분)**: 사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.
- **암호 만료(일)**: 암호가 만료되기 전에 새로 만들어야 하는 일수를 선택합니다.
- **재사용을 방지하기 위한 이전 암호 수**: 사용할 수 없는, 이전에 사용된 암호 수를 입력합니다.

### <a name="restricted-applications"></a>제한된 애플리케이션 
정책에 해당 번들 ID를 추가하여 앱을 제한할 수 있습니다. 그런 다음, 디바이스에 앱이 설치되어 있으면 디바이스는 비준수로 표시됩니다. 
- **앱 이름**: 번들 ID를 식별할 수 있도록 친숙한 이름을 입력합니다. 
- **앱 번들 ID**: 앱 공급자가 할당한 고유한 번들 식별자를 입력합니다. 번들 ID를 찾으려면 [iOS 앱에 대한 번들 ID를 찾는 방법](https://support.microsoft.com/help/4294074/how-to-find-the-bundle-id-for-an-ios-app)을 참조하세요.  

## <a name="assign-user-groups"></a>사용자 그룹 할당

1. 구성한 정책을 선택합니다. 기존 정책은 **디바이스 준수** > **정책**에 있습니다.
2. 정책을 선택한 다음 **할당**을 선택합니다. Azure AD(Active Directory) 보안 그룹을 포함하거나 제외할 수 있습니다.
3. **선택된 그룹**을 선택하면 Azure AD 보안 그룹이 표시됩니다. 이 정책을 적용할 사용자 그룹을 선택한 다음 **저장**을 선택하여 정책을 사용자에게 배포합니다.

사용자에게 정책을 적용했습니다. 정책의 대상이 되는 사용자가 사용하는 디바이스에 대한 규정 준수 여부가 평가됩니다.

## <a name="next-steps"></a>다음 단계
[메일 자동화 및 비규격 장치에 대한 작업 추가](actions-for-noncompliance.md)  
[Intune 장치 준수 정책 모니터링](compliance-policy-monitor.md)
