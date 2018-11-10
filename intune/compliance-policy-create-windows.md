---
title: Microsoft Intune에서 Windows 장치 규정 준수 정책 만들기 - Azure | Microsoft Docs
description: Windows Phone 8.1, Windows 8.1 이상, Windows 10 이상 장치에 대한 Microsoft Intune 장치 준수 정책을 만들거나 구성합니다. 최소 및 최대 운영 체제에서 준수 확인, 암호 제한 및 길이 설정, bitlocker 요구, 타사 AV 솔루션, 허용되는 위협 수준 설정, Surface Hub 및 Windows Holographic for Business를 비롯한 데이터 저장소에서 암호화 사용 등을 수행합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 359f423e7b1bd098136670db1d43b2ddec6031a3
ms.sourcegitcommit: cac71802b2782700f0d52ea114089d73620cd1ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50679324"
---
# <a name="add-a-device-compliance-policy-for-windows-devices-in-intune"></a>Intune에서 Windows 장치에 대한 장치 준수 정책 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows에 대한 Intune 장치 준수 정책은 Windows 장치가 준수하는 것으로 간주되려면 충족해야 하는 규칙과 설정을 지정합니다. 이러한 정책을 조건부 액세스와 함께 사용하여 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다. 장치 보고서를 가져오 고 비준수에 대해 조치를 할 수 있습니다. Intune Azure Portal에서 각 플랫폼에 대해 장치 준수 정책을 만듭니다. 준수 정책 및 모든 필수 조건에 대한 자세한 내용은 [장치 준수 시작](device-compliance-get-started.md)을 참조하세요.

다음 표에서는 준수 정책을 조건부 액세스 정책과 함께 사용할 경우 비준수 설정을 관리하는 방법을 설명합니다.

---------------------------

| **정책 설정** | **Windows 8.1 이상** | **Windows Phone 8.1 이상** |
|----| ----| --- |
| **PIN 또는 암호 구성** | 재구성됨 | 재구성됨 |   
| **장치 암호화** | 해당 없음 | 재구성됨 |   
| **무단 해제 또는 루팅된 장치** | 해당 없음 | 해당 없음 |  
| **전자 메일 프로필** | 해당 없음 | 해당 없음 |   
| **최소 OS 버전** | 격리됨 | 격리됨 |   
| **최대 OS 버전** | 격리됨 | 격리됨 |   
| **Windows 상태 증명** | 격리됨: Windows 10 및 Windows 10 Mobile|해당 없음: Windows 8.1 |

-------------------------------

**재구성됨** = 장치 운영 체제에서 준수를 적용하도록 요구합니다. (예를 들어 사용자에게 PIN을 설정하도록 강제합니다.)

**격리됨** = 장치 운영 체제에서 준수를 적용하도록 요구하지 않습니다. (예를 들어, Android 장치에서 사용자에게 장치를 암호화하도록 강제하지 않습니다.) 장치가 호환되지 않으면 다음 작업이 수행됩니다.

- 조건부 액세스 정책이 사용자에게 적용될 경우 장치가 차단됩니다.
- 회사 포털은 모든 준수 문제에 대해 사용자에게 알립니다.

## <a name="create-a-device-compliance-policy"></a>장치 준수 정책 만들기

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
5. **플랫폼**에서 **Windows Phone 8.1**, **Windows 8.1 이상** 또는 **Windows 10 이상**을 선택합니다.
6. **설정 구성**을 선택하고 **장치 상태**, **장치 속성** 및 **시스템 보안** 설정을 입력합니다. 작업을 마쳤으면 **확인**, **만들기**를 차례로 선택합니다.

<!--- 4. Choose **Actions for noncompliance** to say what actions should happen when a device is determined as noncompliant with this policy.
5. In the **Actions for noncompliance** pane, choose **Add** to create a new action.  The action parameters pane allows you to specify the action, email recipients that should receive the notification in addition to the user of the device, and the content of the notification that you want to send.
6. The message template option allows you to create several custom emails depending on when the action is set to take. For example, you can create a message for notifications that are sent for the first time and a different message for final warning before access is blocked. The custom messages that you create can be used for all your device compliance policy.
7. Specify the **Grace period** which determines when that action to take place.  For example, you may want to send a notification as soon as the device is evaluated as noncompliant, but allow some time before enforcing the conditional access policy to block access to company resources like SharePoint online.
8. Choose **Add** to finish creating the action.
9. You can create multiple actions and the sequence in which they should occur. Choose **Ok** when you are finished creating all the actions.--->

## <a name="windows-81-devices-policy-settings"></a>Windows 8.1 장치 정책 설정

이러한 정책 설정은 다음 플랫폼을 실행하는 장치에 적용됩니다.

- Windows Phone 8.1
- Windows 8.1 이상

### <a name="device-properties"></a>장치 속성

- **필요한 최소 OS**: 장치가 OS 최소 버전 요구 사항을 충족하지 못할 경우 비규격 장치로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 해당 장치를 업그레이드한 후 회사 리소스에 액세스할 수 있습니다.
- **허용된 최대 OS 버전**: 장치가 규칙에 지정된 버전보다 최신 OS 버전을 사용하는 경우 회사 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 이 장치는 회사 리소스에 액세스할 수 없습니다.

Windows 8.1 PC는 **3** 버전을 반환합니다. Windows에 대한 OS 버전 규칙이 Windows 8.1로 설정된 경우 장치에 Windows 8.1이 있어도 장치가 호환되지 않는 것으로 보고됩니다.

### <a name="system-security"></a>시스템 보안

#### <a name="password"></a>암호

- **모바일 장치의 잠금을 해제하는 데 암호 필요**: **필요**로 설정하면 사용자가 암호를 입력해야 장치에 액세스할 수 있습니다.
- **단순 암호**: **차단**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 단순 암호를 만들 수 없습니다. **구성되지 않음**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 암호를 만들 수 있습니다.
- **최소 암호 길이**: 암호에 포함해야 하는 최소 자릿수 또는 문자 수를 입력합니다.

  Windows를 실행하고 Microsoft 계정으로 액세스하는 장치에서는 다음과 같은 경우 준수 정책이 올바르게 평가하지 못합니다.
  - 최소 암호 길이가 8자를 초과하는 경우
  - 또는 최소 문자 집합 수가 3개 이상인 경우

- **암호 유형**: 암호에 **숫자**만 사용해야 하는지 또는 숫자와 기타 문자(**영숫자**)를 함께 사용해야 하는지 선택합니다.
  
  - **암호에 포함해야 하는 영숫자가 아닌 문자 수**: **필수 암호 유형**이 **영숫자**로 설정된 경우 이 설정은 암호에 포함해야 하는 최소 문자 집합 수를 지정합니다. 4가지 문자 집합은 다음과 같습니다.
    - 소문자
    - 대문자
    - 기호
    - 숫자

    더 큰 값을 설정하면 사용자는 더욱 복잡한 암호를 만들어야 합니다. Windows를 실행하고 Microsoft 계정으로 액세스되는 장치의 경우 최소 암호 길이가 8자보다 길거나 최소 문자 집합 수가 2보다 크면 준수 정책 평가가 올바르게 이루어지지 않습니다.

- **암호를 요구하기 전까지 최대 비활성 시간(분)**: 사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.
- **암호 만료(일)**: 암호가 만료되기 전에 새로 만들어야 하는 일수를 선택합니다.
- **재사용을 방지하기 위한 이전 암호 수**: 사용할 수 없는, 이전에 사용된 암호 수를 입력합니다.

#### <a name="encryption"></a>암호화

- **모바일 장치 암호화 필요**: **필요**로 설정하면 장치가 데이터 저장소 리소스에 연결하기 위해 암호화되어야 합니다.

## <a name="windows-10-and-later-policy-settings"></a>Windows 10 이상 정책 설정

### <a name="device-health"></a>Device health

- **BitLocker 필요**: BitLocker가 켜져 있으면 시스템이 꺼지거나 최대 절전 모드로 전환될 때 장치에서 드라이브에 저장된 데이터를 무단 액세스로부터 보호할 수 있습니다. Windows BitLocker 드라이브 암호화는 Windows 운영 체제 볼륨에 저장된 모든 데이터를 암호화합니다. BitLocker는 TPM을 사용하여 Windows 운영 체제 및 사용자 데이터 보호를 지원합니다. 또한 컴퓨터를 방치하거나 분실하거나 도난당하더라도 변조를 방지할 수 있습니다. 컴퓨터에 호환되는 TPM이 장착되어 있으면 BitLocker는 TPM을 사용하여 데이터를 보호하는 암호화 키를 잠급니다. 결과적으로, TPM이 컴퓨터의 상태를 확인할 때까지 키를 액세스할 수 없습니다.
- **장치에서 보안 부팅을 사용하도록 설정해야 함**: 보안 부팅을 사용하도록 설정하면 시스템이 공장에서 신뢰할 수 있는 상태로 강제로 부팅됩니다. 또한 보안 부팅을 사용하면 컴퓨터를 부팅하는 데 사용되는 핵심 구성 요소에 장치를 제조한 조직에서 신뢰할 수 있는 올바른 암호화 서명이 있어야 합니다. UEFI 펌웨어에서 컴퓨터가 시작되도록 허용하기 전에 서명을 확인합니다. 파일이 변조되어 해당 서명이 손상된 경우에는 시스템이 부팅되지 않습니다.

  > [!NOTE]
  > **장치에서 보안 부팅을 사용하도록 설정해야 합니다** 설정은 TPM 1.2 및 2.0 장치에서 지원됩니다. TPM 2.0 이상을 지원하지 않는 장치의 경우 Intune의 정책 상태가 **호환되지 않음**으로 표시됩니다. Windows 10에서 [장치 상태 증명](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation) 서비스의 제한 사항입니다.

- **코드 무결성 필요**: 코드 무결성은 메모리에 로드될 때마다 드라이버 또는 시스템 파일의 무결성을 확인하는 기능입니다. 코드 무결성은 서명되지 않은 드라이버 또는 시스템 파일이 커널로 로드되고 있는지 여부를 검색합니다. 또는 관리자 권한을 가진 사용자 계정으로 실행된 악성 소프트웨어가 시스템 파일을 수정했는지 여부를 검색합니다.

HAS 서비스의 작동 방식에 대한 자세한 내용은 [상태 증명 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)를 참조하세요.

### <a name="device-properties"></a>장치 속성

- **최소 OS 버전**: 허용되는 최소 버전을 **주 버전.부 버전.빌드.CU 번호** 형식으로 입력합니다. 올바른 값을 얻으려면 명령 프롬프트를 열고 `ver`을 입력합니다. `ver` 명령은 버전을 다음 형식으로 반환합니다.

  `Microsoft Windows [Version 10.0.17134.1]`

  지정된 OS 버전보다 이전 버전이 장치에 있으면 호환되지 않는 것으로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 회사 리소스에 액세스할 수 있으면 장치를 업그레이드하도록 선택할 수 있습니다.

- **최대 OS 버전**: 허용되는 최대 버전을 **주 버전.부 버전.빌드.수정 번호** 형식으로 입력합니다. 올바른 값을 얻으려면 명령 프롬프트를 열고 `ver`을 입력합니다. `ver` 명령은 버전을 다음 형식으로 반환합니다.

  `Microsoft Windows [Version 10.0.17134.1]`

  장치가 규칙에 지정된 버전 이후의 OS를 사용하는 경우 회사 리소스에 대한 액세스가 차단되고 사용자는 IT 관리자에게 문의하라는 메시지가 표시됩니다. OS 버전 허용 규칙이 변경될 때까지 회사 리소스에 액세스하는 데 이 장치를 사용할 수 없습니다.

- **모바일 장치에 필요한 최소 OS**: 주 버전.부 버전.빌드 번호 형식으로 최소 허용 버전을 입력합니다.

  지정된 OS 버전보다 이전 버전이 장치에 있으면 호환되지 않는 것으로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 회사 리소스에 액세스할 수 있으면 장치를 업그레이드하도록 선택할 수 있습니다.

- **모바일 장치에 필요한 최대 OS**: 주 버전.부 버전.빌드 번호 형식으로 최대 허용 버전을 입력합니다.

  장치가 규칙에 지정된 버전 이후의 OS를 사용하는 경우 회사 리소스에 대한 액세스가 차단되고 사용자는 IT 관리자에게 문의하라는 메시지가 표시됩니다. OS 버전 허용 규칙이 변경될 때까지 회사 리소스에 액세스하는 데 이 장치를 사용할 수 없습니다.

- **유효한 운영 체제 빌드**: 최소 버전과 최대 버전을 포함하여 허용되는 운영 체제 버전의 범위를 입력합니다. 이러한 허용되는 OS 빌드 번호의 CSV(쉼표로 구분된 값) 파일 목록을 **내보낼** 수도 있습니다.

### <a name="system-security-settings"></a>시스템 보안 설정

#### <a name="password"></a>암호

- **모바일 장치의 잠금을 해제하는 데 암호 필요**: **필요**로 설정하면 사용자가 암호를 입력해야 장치에 액세스할 수 있습니다.
- **단순 암호**: **차단**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 단순 암호를 만들 수 없습니다. **구성되지 않음**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 암호를 만들 수 있습니다.
- **암호 유형**: 암호에 **숫자**만 사용해야 하는지 또는 숫자와 기타 문자(**영숫자**)를 함께 사용해야 하는지 선택합니다.

  - **암호에 포함해야 하는 영숫자가 아닌 문자 수**: **필수 암호 유형**이 **영숫자**로 설정된 경우 이 설정은 암호에 포함해야 하는 최소 문자 집합 수를 지정합니다. 4가지 문자 집합은 다음과 같습니다.
    - 소문자
    - 대문자
    - 기호
    - 숫자

    더 큰 값을 설정하면 사용자는 더욱 복잡한 암호를 만들어야 합니다.

- **최소 암호 길이**: 암호에 포함해야 하는 최소 자릿수 또는 문자 수를 입력합니다.
- **암호를 요구하기 전까지 최대 비활성 시간(분)**: 사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.
- **암호 만료(일)**: 암호가 만료되기 전에 새로 만들어야 하는 일수를 선택합니다.
- **재사용을 방지하기 위한 이전 암호 수**: 사용할 수 없는, 이전에 사용된 암호 수를 입력합니다.
- **장치가 유휴 상태에서 되돌아올 때 암호 요구(Mobile 및 Holographic)**: 장치가 유휴 상태에서 돌아올 때마다 사용자가 암호를 입력해야 합니다.

#### <a name="encryption"></a>암호화

- **장치의 데이터 저장소 암호화**: **필요**를 선택하면 장치의 데이터 저장소가 암호화됩니다.

  > [!NOTE]
  > **장치에서 데이터 저장소 암호화** 설정은 일반적으로 장치가 암호화되었는지 확인합니다. 보다 강력한 암호화 설정을 위해 **BitLocker 필요**를 사용하는 것이 좋습니다. 그러면 Windows 장치 상태 증명을 활용하여 TPM 수준에서 Bitlocker 상태의 유효성을 검사합니다.

#### <a name="device-security"></a>장치 보안

- **바이러스 백신**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 바이러스 백신 솔루션을 사용하여 준수를 확인할 수 있습니다. **구성되지 않은** 경우 Intune은 장치에 설치된 모든 AV 솔루션을 확인하지 않습니다.
- **스파이웨어 방지**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 스파이웨어 방지 솔루션을 사용하여 준수를 확인할 수 있습니다. **구성되지 않은** 경우 Intune은 장치에 설치된 스파이웨어 방지 솔루션을 확인하지 않습니다.

### <a name="windows-defender-atp"></a>Windows Defender ATP

- **장치가 머신 위험 점수나 그 아래에 있어야 함**: 이 설정을 사용하여 위협 방지 서비스에서 준수 조건에 따라 위험 평가를 수행할 수 있습니다. 허용된 최대 위협 수준을 선택합니다.
  - **지우기**: 장치에 어떤 위협도 없으므로 이 옵션이 가장 안전합니다. 수준에 관계없이 위협이 발견된 장치는 규정 비준수로 평가됩니다.
  - **낮음**: 낮은 수준의 위협만 있는 경우 장치가 규정 준수로 평가됩니다. 더 높은 수준의 위협이 발생하면 장치는 규정 비준수 상태가 됩니다.
  - **보통**: 장치의 기존 위협이 낮음 또는 보통 수준인 경우 장치가 규격으로 평가됩니다. 높은 수준의 위협이 있는 것으로 감지되면 장치가 규정 비준수로 결정됩니다.
  - **높음**: 이 옵션은 최소 보안이며 모든 위협 수준을 허용합니다. 이 수준은 이 솔루션을 보고 용도로만 사용하는 경우에 유용할 수 있습니다.
  
  방어 위협 서비스로 Windows Defender ATP(Advanced Threat Protection)를 설정하려면[조건부 액세스로 Windows Defender ATP 사용](advanced-threat-protection.md)을 참조하세요.

## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business는 **Windows 10 이상** 플랫폼을 사용합니다. Windows Holographic for Business는 다음과 같은 설정을 지원합니다.

- **시스템 보안** > **암호화** > **장치의 데이터 저장소 암호화**.

Microsoft HoloLens에서 장치 암호화를 확인하려면 [장치 암호화 확인](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)을 참조하세요.

## <a name="surface-hub"></a>Surface Hub
Surface Hub는 **Windows 10 이상** 플랫폼을 사용합니다. Surface Hub는 준수 및 조건부 액세스 둘 다에서 지원됩니다. Surface Hub에서 이러한 기능을 사용하려면 Intune에서 [Windows 10 자동 등록을 사용하도록 설정](windows-enroll.md)하고(AAD(Azure Active Directory)도 필요함), 장치 그룹인 Surface Hub 장치를 대상으로 지정하는 것이 좋습니다. 준수 및 조건부 액세스가 작동하려면 Surface Hub가 Azure Active Directory에 연결되어야 합니다.

지침은 [Windows 장치에 대한 등록 설정](windows-enroll.md)을 참조하세요.

## <a name="assign-user-or-device-groups"></a>사용자 또는 장치 그룹 할당

1. 구성한 정책을 선택합니다. 기존 정책은 **장치 준수** > **정책**에 있습니다.
2. 정책을 선택한 다음 **할당**을 선택합니다. Azure AD 보안 그룹을 포함하거나 제외할 수 있습니다.
3. **선택된 그룹**을 선택하면 Azure AD 보안 그룹이 표시됩니다. 이 정책을 적용할 사용자 또는 장치 그룹을 선택한 다음 **저장**을 선택하여 정책을 배포합니다.

정책을 적용했습니다. 정책의 대상이 되는 사용자가 사용하는 장치에 대한 규정 준수 여부가 평가됩니다.

## <a name="next-steps"></a>다음 단계
[메일 자동화 및 비규격 장치에 대한 작업 추가](actions-for-noncompliance.md)  
[Intune 장치 준수 정책 모니터링](compliance-policy-monitor.md)
