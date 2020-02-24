---
title: Microsoft Intune에서 디바이스 준수 정책 - Azure | Microsoft Docs
description: 디바이스 준수 정책 및 상태와 심각도 수준의 개요 사용, InGracePeriod 상태 사용, 조건부 액세스 작업, 할당된 정책 없는 디바이스 처리를 시작합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/13/2020
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
ms.openlocfilehash: 867873c78b34d5573084a3a6e44d7d4d67846423
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77413640"
---
# <a name="set-rules-on-devices-to-allow-access-to-resources-in-your-organization-using-intune"></a>Intune을 사용하여 조직의 리소스 액세스를 허용하도록 디바이스에서 규칙을 설정합니다.

많은 MDM(모바일 디바이스 관리) 솔루션은 사용자와 디바이스가 일부 요구 사항을 충족해야 하므로 조직 데이터를 보호하는 데 도움이 됩니다. Intune에서 이 기능을 “준수 정책”이라고 합니다. 준수 정책은 사용자 및 디바이스가 준수하려면 충족해야 하는 규칙 및 설정을 정의합니다. 조건부 액세스를 함께 사용하면 관리자가 규칙을 충족하지 않는 사용자 및 디바이스를 차단할 수 있습니다.

예를 들어, Intune 관리자는 다음이 필요할 수 있습니다.

- 최종 사용자는 암호를 사용하여 모바일 디바이스에서 조직 데이터에 액세스
- 디바이스가 탈옥 또는 루팅되어 있지 않음
- 디바이스의 최소 또는 최대 운영 체제 버전
- 디바이스를 위협 수준 이하로 유지

또한 이 기능을 사용하여 조직에 있는 디바이스에서 준수 상태를 모니터링할 수 있습니다.

> [!IMPORTANT]
> Intune은 디바이스의 모든 규정 준수 평가에 대한 디바이스 체크 인 일정을 따릅니다. [정책 및 프로필 새로 고침 주기](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)에는 예상 새로 고침 시간이 나열됩니다.

<!---### Actions for noncompliance

You can specify what needs to happen when a device is determined as noncompliant. This can be a sequence of actions during a specific time.
When you specify these actions, Intune will automatically initiate them in the sequence you specify. See the following example of a sequence of
actions for a device that continues to be in the noncompliant status for
a week:

- When the device is first determined to be noncompliant, an email with noncompliant notification is sent to the user.

- 3 days after initial noncompliance state, a follow up reminder is sent to the user.

- 5 days after initial noncompliance state, a final reminder with a notification that access to company resources will be blocked on the device in 2 days if the compliance issues are not remediated is sent to the user.

- 7 days after initial noncompliance state, access to company resources is blocked. This requires that you have Conditional Access policy that specifies that access from noncompliant devices should    be blocked for services such as Exchange and SharePoint.

### Grace Period

This is the time between when a device is first determined as
noncompliant to when access to company resources on that device is blocked. This time allows for time that the user has to resolve
compliance issues on the device. You can also use this time to create your action sequences to send notifications to the user before their access is blocked.

Remember that you need to implement Conditional Access policies in addition to compliance policies in order for access to company resources to be blocked.--->

## <a name="device-compliance-policies-work-with-azure-ad"></a>디바이스 준수 정책이 Azure AD에서 사용됨

Intune에서는 준수를 적용하는 데 도움이 되는 Azure AD(Active Directory) [조건부 액세스](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)(다른 문서 웹 사이트가 열림)를 사용합니다. 디바이스가 Intune에 등록되면 Azure AD 등록 프로세스가 시작되고 디바이스 정보가 Azure AD에서 업데이트됩니다. 주요 정보 중 하나는 디바이스 준수 상태입니다. 이 준수 상태는 조건부 액세스 정책에서 이메일 및 기타 조직 리소스에 대한 액세스를 차단하거나 허용하는 데 사용합니다.

- [Azure Active Directory에서 디바이스 관리란?](https://docs.microsoft.com/azure/active-directory/device-management-introduction)은 디바이스가 Azure AD에 등록되는 이유와 방법에 대한 좋은 리소스입니다.

- [조건부 액세스](conditional-access.md) 및 [조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)에서는 Intune과의 관련성 속에서 이 기능을 설명합니다.

## <a name="ways-to-use-device-compliance-policies"></a>디바이스 준수 정책을 사용하는 방법

### <a name="with-conditional-access"></a>조건부 액세스 사용

정책 규칙을 준수하는 디바이스의 경우 메일 및 기타 조직 리소스에 대한 액세스를 해당 디바이스에 제공할 수 있습니다. 디바이스가 정책 규칙을 따르는 않는 경우 조직 리소스에 대한 액세스를 가져오지 않습니다. 이를 조건부 액세스라고 합니다.

### <a name="without-conditional-access"></a>조건부 액세스 사용 안 함

또한 조건부 액세스 없이 디바이스 준수 정책을 사용할 수 있습니다. 준수 정책을 독립적으로 사용하는 경우 대상 디바이스는 평가되고 준수 상태와 함께 보고됩니다. 예를 들어 암호화되지 않은 디바이스의 수 또는 탈옥이나 루팅된 디바이스에 대한 보고서를 가져올 수 있습니다. 조건부 액세스 없이 준수 정책을 사용하는 경우 조직 리소스에 대한 액세스 제한이 없습니다.

## <a name="ways-to-deploy-device-compliance-policies"></a>디바이스 준수 정책을 배포하는 방법

준수 정책을 사용자 그룹의 사용자 또는 디바이스 그룹의 디바이스에 배포할 수 있습니다. 준수 정책을 사용자에게 배포하면 사용자의 모든 디바이스에서 준수가 확인됩니다. Windows 10 버전 1803 이상 디바이스에서 기본 사용자가 디바이스를 등록하지 않은 *경우* 디바이스 그룹에 배포하는 것이 좋습니다. 이 시나리오에서 디바이스 그룹을 사용하면 준수 보고에 도움이 됩니다.

Intune에는 기본 제공 준수 정책 설정 세트도 포함됩니다. 다음 기본 제공 정책은 Intune에 등록된 모든 디바이스에서 평가됩니다.

- **준수 정책이 할당되지 않은 디바이스를 다음으로 표시**: 이 속성에는 두 개의 값이 있습니다.

  - **준수**(*기본값*): 보안 기능 끄기
  - **비준수**: 보안 기능 켜기

  디바이스에 할당된 준수 정책이 없으면 이 디바이스는 기본적으로 준수함으로 간주됩니다. 준수 정책과 함께 조건부 액세스를 사용하는 경우 기본 설정을 **비준수**로 변경하는 것이 좋습니다. 정책이 할당되지 않아 최종 사용자가 준수하지 않으면, [회사 포털 앱](../apps/company-portal-app.md)에 `No compliance policies have been assigned`가 표시됩니다.


> [!NOTE]
> iOS 디바이스의 향상된 탈옥 검색이 Intune에서 일시적으로 사용하지 않도록 설정되었습니다.

- **향상된 탈옥 검색**: 이 설정을 사용하도록 지정하면 iOS 디바이스에서 Intune으로 더 자주 체크 인할 수 있습니다. 이 속성을 사용하면 디바이스의 위치 서비스를 사용하고 배터리 사용에 영향을 줍니다. 사용자 위치 데이터는 Intune에서 저장되지 않습니다.

  이 설정을 사용하면 디바이스를 다음과 같이 설정해야 합니다.
  - OS 수준에서 위치 서비스를 사용하도록 설정합니다.
  - 회사 포털에서 위치 서비스를 사용하도록 허용합니다.
  - 최소 72시간에 한 번 Intune에 해당 탈옥 상태를 평가 및 보고합니다. 그렇지 않은 경우 디바이스가 준수하지 않음으로 표시됩니다. 평가는 회사 포털 앱을 열거나 디바이스를 500미터 이상 물리적으로 이동하면 트리거됩니다. 디바이스가 72시간 내에 500m를 이동하지 않을 경우 사용자는 향상된 탈옥 평가를 위해 회사 포털 앱을 열어야 합니다.

- **준수 상태 유효 기간(일)** : 디바이스가 수신된 모든 준수 정책의 상태를 보고하는 기간을 입력합니다. 이 기간 내에 상태를 반환하지 않는 디바이스는 비준수로 처리됩니다. 기본값은 30일입니다. 최솟값은 1일입니다.

  이 설정은 **활성 여부** 기본 준수 정책(**디바이스** > **모니터** > **설정 준수**)으로 표시됩니다. 이 정책의 백그라운드 작업은 하루 1회 실행됩니다.

이 기본 제공 정책을 사용하여 이 설정을 모니터링할 수 있습니다. 또한 Intune에서는 디바이스 플랫폼에 따라 다른 간격으로 [업데이트를 새로 고치거나 확인](create-compliance-policy.md#refresh-cycle-times)합니다. [Microsoft Intune의 디바이스 정책 및 프로필을 통한 일반적인 질문, 이슈 및 해결 방법](../configuration/device-profile-troubleshoot.md)은 좋은 리소스입니다.

준수 보고서는 디바이스의 상태를 확인하는 좋은 방법입니다. [준수 정책 모니터링](compliance-policy-monitor.md)에 몇 가지 지침이 포함됩니다.

## <a name="non-compliance-and-conditional-access-on-the-different-platforms"></a>다양한 플랫폼에 대한 비준수 및 조건부 액세스

다음 표에서는 준수 정책을 조건부 액세스 정책과 함께 사용할 경우 비준수 설정을 관리하는 방법을 설명합니다.

---------------------------

|**정책 설정**| **플랫폼** |
| --- | ----|
| **PIN 또는 암호 구성** | - **Android 4.0 이상**: 격리됨<br>- **Samsung Knox Standard 4.0 이상**: 격리됨<br>- **Android 엔터프라이즈**: 격리됨  <br>  <br>- **iOS 8.0 이상**: 재구성됨<br>- **macOS 10.11 이상**: 재구성됨  <br>  <br>- **Windows 8.1 이상**: 재구성됨<br>- **Windows Phone 8.1 이상**: 재구성됨|
| **디바이스 암호화** | - **Android 4.0 이상**: 격리됨<br>- **Samsung Knox Standard 4.0 이상**: 격리됨<br>- **Android 엔터프라이즈**: 격리됨<br><br>- **iOS 8.0 이상**: 재구성됨(PIN 설정)<br>- **macOS 10.11 이상**: 재구성됨(PIN 설정)<br><br>- **Windows 8.1 이상**: 해당 없음<br>- **Windows Phone 8.1 이상**: 재구성됨 |
| **무단 해제 또는 루팅된 디바이스** | - **Android 4.0 이상**: 격리됨(설정 아님)<br>- **Samsung Knox Standard 4.0 이상**: 격리됨(설정 아님)<br>- **Android 엔터프라이즈**: 격리됨(설정 아님)<br><br>- **iOS 8.0 이상**: 격리됨(설정 아님)<br>- **macOS 10.11 이상**: 해당 없음<br><br>- **Windows 8.1 이상**: 해당 없음<br>- **Windows Phone 8.1 이상**: 해당 없음 |
| **전자 메일 프로필** | - **Android 4.0 이상**: 해당 없음<br>- **Samsung Knox Standard 4.0 이상**: 해당 없음<br>- **Android 엔터프라이즈**: 해당 없음<br><br>- **iOS 8.0 이상**: 격리됨<br>- **macOS 10.11 이상**: 격리됨<br><br>- **Windows 8.1 이상**: 해당 없음<br>- **Windows Phone 8.1 이상**: 해당 없음 |
| **최소 OS 버전** | - **Android 4.0 이상**: 격리됨<br>- **Samsung Knox Standard 4.0 이상**: 격리됨<br>- **Android 엔터프라이즈**: 격리됨<br><br>- **iOS 8.0 이상**: 격리됨<br>- **macOS 10.11 이상**: 격리됨<br><br>- **Windows 8.1 이상**: 격리됨<br>- **Windows Phone 8.1 이상**: 격리됨 |
| **최대 OS 버전** | - **Android 4.0 이상**: 격리됨<br>- **Samsung Knox Standard 4.0 이상**: 격리됨<br>- **Android 엔터프라이즈**: 격리됨<br><br>- **iOS 8.0 이상**: 격리됨<br>- **macOS 10.11 이상**: 격리됨<br><br>- **Windows 8.1 이상**: 격리됨<br>- **Windows Phone 8.1 이상**: 격리됨 |
| **Windows 상태 증명** | - **Android 4.0 이상**: 해당 없음<br>- **Samsung Knox Standard 4.0 이상**: 해당 없음<br>- **Android 엔터프라이즈**: 해당 없음<br><br>- **iOS 8.0 이상**: 해당 없음<br>- **macOS 10.11 이상**: 해당 없음<br><br>- **Windows 10 및 Windows 10 Mobile**: 격리됨<br>- **Windows 8.1 이상**: 격리됨<br>- **Windows Phone 8.1 이상**: 해당 없음 |

---------------------------

**재구성됨**: 디바이스 운영 체제에서 준수를 적용하도록 요구합니다. 예를 들어 사용자에게 PIN을 설정하도록 강제합니다.

**격리됨**: 디바이스 운영 체제에서 준수를 적용하도록 요구하지 않습니다. 예를 들어, Android 및 Android 엔터프라이즈 디바이스는 사용자에게 디바이스를 암호화하도록 강제하지 않습니다. 디바이스가 규정을 준수하지 않으면 다음 작업이 수행됩니다.

- 조건부 액세스 정책이 사용자에게 적용될 경우 디바이스가 차단됩니다.
- 회사 포털 앱은 모든 준수 문제에 대해 사용자에게 알립니다.

## <a name="next-steps"></a>다음 단계

- [정책을 만들고](create-compliance-policy.md) 필수 구성 요소를 확인합니다.
- 다양한 디바이스 플랫폼에 대한 준수 설정을 참조하세요.

  - [OWA(Outlook Web Access)](compliance-policy-create-android.md)
  - [Android Enterprise](compliance-policy-create-android-for-work.md)
  - [iOS](compliance-policy-create-ios.md)
  - [macOS](compliance-policy-create-mac-os.md)
  - [Windows Holographic for Business](compliance-policy-create-windows.md#windows-holographic-for-business)
  - [Windows Phone 8.1](compliance-policy-create-windows-8-1.md)
  - [Windows 8.1 이상](compliance-policy-create-windows-8-1.md)
  - [Windows 10 이상](compliance-policy-create-windows.md)

- [정책 엔터티에 대한 참조](../reports-ref-policy.md)에는 Intune Data Warehouse 정책 엔터티에 대한 정보가 있습니다.
