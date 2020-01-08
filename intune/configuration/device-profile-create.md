---
title: Microsoft Intune - Azure에서 디바이스 프로필 만들기 | Microsoft Docs
description: Microsoft Intune에서 디바이스 구성 프로필을 추가 또는 구성합니다. 플랫폼 형식을 선택하고, 설정을 구성하고, 범위 태그를 추가합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c8748639f0407de7b1bb83f646b7decf8c838766
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75206672"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 프로필 만들기

디바이스 프로필을 사용하여 설정을 추가 및 구성한 후 조직의 디바이스에 이 설정을 밀어넣을 수 있습니다. 수행할 수 있는 작업을 포함하여 자세한 내용은 [디바이스 프로필을 사용하여 디바이스에서 기능 및 설정 적용](device-profiles.md)을 참조하세요.

이 문서의 내용은 다음과 같습니다.

- 프로필을 만드는 단계를 나열합니다.
- 범위 태그를 추가하여 프로필을 "필터링"하는 방법을 보여 줍니다.
- Windows 10 디바이스의 적용 가능성 규칙에 대해 설명하고 규칙을 만드는 방법을 보여 줍니다.
- 디바이스가 프로필 및 프로필 업데이트를 받는 체크 인 새로 고침 주기 시간을 나열합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **구성 프로필**을 선택합니다. 다음과 같은 옵션을 선택할 수 있습니다.

    - **개요**: 사용자 프로필의 상태를 나열하고 사용자 및 디바이스에 할당한 프로필에 관한 추가 세부 내용을 제공합니다.
    - **관리**: 디바이스 프로필을 만들어 프로필 내에서 실행할 사용자 지정 [PowerShell 스크립트](../apps/intune-management-extension.md)를 업로드하고, [eSIM](esim-device-configuration.md)을 사용하는 디바이스에 데이터 플랜을 추가합니다.
    - **모니터**: 성공 또는 실패에 대한 프로필 상태를 확인하고 프로필 로그도 봅니다.
    - **설치**: SCEP 또는 PFX 인증 기관을 추가하거나 [TEM(Telecom Expense Management)](telecom-expenses-monitor.md)을 프로필에 사용하도록 설정합니다.

3. **프로필 만들기**를 선택합니다. 다음 속성을 입력합니다.

   - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 WP 메일 프로필**은 좋은 프로필 이름입니다.
   - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
   - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.  

       - **OWA(Outlook Web Access)**
       - **Android 엔터프라이즈**
       - **iOS/iPadOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 이상**
       - **Windows 10 이상**

   - **프로필 유형**: 만들려는 설정 유형을 선택합니다. 표시된 목록은 선택한 **플랫폼**에 따라 달라집니다.
   - **설정**: 다음 아티클에서는 각 프로필의 설정에 대해 설명합니다.

       - [관리 템플릿](administrative-templates-windows.md)
       - [사용자 지정](../custom-settings-configure.md)
       - [배달 최적화](../delivery-optimization-windows.md)
       - [디바이스 기능](../device-features-configure.md)
       - [디바이스 제한 사항](device-restrictions-configure.md)
       - [버전 업그레이드 및 모드 전환](edition-upgrade-configure-windows-10.md)
       - [교육](education-settings-configure.md)
       - [전자 메일](email-settings-configure.md)
       - [엔드포인트 보호](../protect/endpoint-protection-configure.md)
       - [ID 보호](../protect/identity-protection-configure.md)  
       - [키오스크](kiosk-settings.md)
       - [PKCS 인증서](../protect/certficates-pfx-configure.md)
       - [PKCS 가져온 인증서](../protect/certificates-imported-pfx-configure.md)
       - [기본 설정 파일](preference-file-settings-macos.md)
       - [SCEP 인증서](../protect/certificates-scep-configure.md)
       - [신뢰할 수 있는 인증서](../protect/certificates-configure.md)
       - [업데이트 정책](../software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Microsoft Defender ATP](../protect/advanced-threat-protection.md)
       - [Windows Information Protection](../protect/windows-information-protection-configure.md)

     예를 들어 플랫폼에 **iOS/iPadOS**를 선택하는 경우 프로필 유형 옵션은 다음 프로필과 비슷하게 표시됩니다.

     ![Intune에서 iOS 프로필 만들기](./media/device-profile-create/create-device-profile.png)

4. 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 목록에 표시됩니다.

## <a name="scope-tags"></a>범위 태그

설정을 추가한 후 프로필에 범위 태그를 추가할 수도 있습니다. 범위 태그는 프로필을 특정 IT 그룹(예: `US-NC IT Team` 또는 `JohnGlenn_ITDepartment`)으로 필터링합니다.

범위 태그 및 수행할 수 있는 작업에 대한 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](../fundamentals/scope-tags.md)을 참조하세요.

### <a name="add-a-scope-tag"></a>범위 태그 추가

1. **범위(태그)** 를 선택합니다.
2. **추가**를 선택하여 새 범위 태그를 만듭니다. 또는 목록에서 기존 범위 태그를 선택합니다.
3. **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="applicability-rules"></a>적용 가능성 규칙

적용 대상:

- Windows 10 이상

적용 가능성 규칙을 통해 관리자는 특정 조건을 충족하는 그룹의 디바이스를 대상으로 지정할 수 있습니다. 예를 들어 **모든 Windows 10 디바이스** 그룹에 적용되는 디바이스 제한 프로필을 만들 수 있습니다. 그리고 Windows 10 Enterprise를 실행하는 디바이스에만 프로필을 할당해야 하는 경우가 있습니다.

이 작업을 수행하려면 **적용 가능성 규칙**을 만듭니다. 이러한 규칙은 다음 시나리오에 유용합니다.

- Windows 10 교육(EDU)을 사용합니다. Bellows college에서는 RS3와 RS4 사이에 있는 모든 Windows 10 EDU 디바이스를 대상으로 지정하려 합니다.
- Contoso의 인사 관리 부서에 있는 모든 사용자를 대상으로 지정하지만 Windows 10 Professional 또는 Enterprise 디바이스만 사용하려 합니다.

이러한 시나리오를 사용하려면 다음을 수행합니다.

- Bellows college의 모든 디바이스를 포함하는 디바이스 그룹을 만듭니다. 프로필에서 OS 최소 버전이 `16299`이고 최대 버전이 `17134`인 경우 적용 되도록 적용 가능성 규칙을 추가합니다. Bellows college 디바이스 그룹에 이 프로필을 할당합니다.

  할당된 후에는 프로필이 입력한 최소 및 최대 버전 사이의 디바이스에 적용됩니다. 입력하는 최소 및 최대 버전 사이에 있지 않은 디바이스의 경우 상태가 **적용할 수 없음**으로 표시됩니다.

- Contoso에서 HR(인사 관리 부서)의 모든 사용자를 포함하는 사용자 그룹을 만듭니다. 프로필에서 Windows 10 Professional 또는 Enterprise를 실행하는 디바이스에 적용되는 적용 가능성 규칙을 추가합니다. HR 사용자 그룹에 이 프로필을 할당합니다.

  할당된 프로필은 Windows 10 Professional 또는 Enterprise를 실행하는 디바이스에 적용됩니다. 이러한 버전을 실행하지 않는 장치의 경우 상태가 **적용할 수 없음**으로 표시됩니다.

- 동일한 설정을 사용하는 프로필이 두 개 있으면 적용 가능성 규칙이 없는 프로필이 적용됩니다. 

  예를 들어, 프로필 A는 Windows 10 디바이스 그룹을 대상으로 하고, BitLocker를 사용하도록 설정하고, 적용 가능성 규칙이 없습니다. 프로필 B는 동일한 Windows 10 디바이스 그룹을 대상으로 하며, BitLocker를 사용하도록 설정하고, Windows 10 Enterprise에만 프로필을 적용하는 적용 가능성 규칙이 있습니다.

  두 프로필을 모두 할당하는 경우 프로필 A에 적용 가능성 규칙이 없기 때문에 프로필 A가 작용됩니다. 

그룹에 프로필을 할당하는 경우 적용 가능성 규칙은 필터 역할을 하며 조건을 충족하는 디바이스만 대상으로 합니다.

### <a name="add-a-rule"></a>규칙 추가

1. **적용 가능성 규칙**을 선택합니다. **규칙**, **속성** 및 **OS 버전**을 선택할 수 있습니다.

    ![적용 가능성 규칙을 Microsoft Intune의 디바이스 구성 프로필에 추가합니다.](./media/device-profile-create/applicability-rules.png)

2. **규칙**에서 사용자 또는 그룹을 포함할지 아니면 제외할지를 선택합니다. 옵션은 다음과 같습니다.

    - **다음의 경우 프로필을 할당합니다**. 입력한 조건을 충족하는 사용자 또는 그룹을 포함합니다.
    - **다음의 경우 프로필을 할당하지 않습니다**. 입력한 조건을 충족하는 사용자 또는 그룹을 제외합니다.

3. **속성**에서 필터를 선택합니다. 옵션은 다음과 같습니다. 

    - **OS 버전**: 목록에서 규칙에 포함하거나 제외하려는 Windows 10 버전을 선택합니다.
    - **OS 버전**: 규칙에 포함하거나 제외하려는 **최소** 및 **최대** Windows 10 버전 번호를 입력합니다. 두 값 모두 필수 항목입니다.

      예를 들어 최소 버전으로 `10.0.16299.0`(RS3 or 1709)을 입력하고 최대 버전으로 `10.0.17134.0`(RS4 또는 1803)을 입력할 수 있습니다. 또는 보다 세부적으로 최소 버전으로 `10.0.16299.001`을 입력하고 최대 버전으로 `10.0.17134.319`를 입력할 수 있습니다.

4. **추가**를 선택하여 변경 내용을 저장합니다.

## <a name="refresh-cycle-times"></a>주기 시간 새로 고침

Intune은 다양한 새로 고침 주기를 사용하여 구성 프로필에 대한 업데이트를 확인합니다. 최근 등록된 디바이스인 경우 다음과 같이 체크 인이 더 자주 실행됩니다. [정책 및 프로필 새로 고침 주기](device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)에는 예상 새로 고침 시간이 나열됩니다.

언제든 사용자는 회사 포털 앱을 열고 디바이스를 동기화하여 즉시 프로필 업데이트를 확인할 수 있습니다.

## <a name="recommendations"></a>권장 사항

프로필을 만들 때 다음 권장 사항을 고려합니다.

- 어떤 정책인지와 어떤 작업을 수행하는지 알 수 있는 이름을 정책에 지정합니다. 모든 [준수 정책](../protect/create-compliance-policy.md) 및 [구성 프로필](../configuration/device-profile-create.md)에는 선택적 **설명** 속성이 있습니다. **설명**은 다른 사람이 어떤 정책인지 알 수 있도록 구체적으로 지정하고 정보를 포함합니다.

  일부 구성 프로필 예제는 다음과 같습니다.

  **프로필 이름**: 관리 템플릿 - 모든 Windows 10 사용자를 위한 OneDrive 구성 프로필  
  **프로필 설명**: 모든 Windows 10 사용자에 대한 최소 및 기본 설정이 포함된 OneDrive 관리 템플릿 프로필입니다. 사용자가 조직 데이터를 개인 OneDrive 계정과 공유하지 못하도록 하기 위해 user@contoso.com에서 생성합니다.

  **프로필 이름**: 모든 iOS 사용자의 VPN 프로필  
  **프로필 설명**: 모든 iOS 사용자가 Contoso VPN에 연결하는 데 필요한 최소 및 기본 설정이 포함된 VPN 프로필입니다. 사용자 이름과 암호를 묻는 메시지를 표시하는 대신, 사용자가 VPN에서 자동으로 인증되도록 하기 위해 user@contoso.com에서 생성합니다.

- Microsoft Edge 설정 구성, Microsoft Defender 바이러스 백신 설정 사용, iOS 탈 옥 디바이스 차단 등의 작업에 따라 프로필을 만듭니다.

- 마케팅, 영업, IT 관리자, 위치 또는 학교 시스템 등의 특정 그룹에 적용되는 프로필을 만듭니다.

- 디바이스 정책에서 사용자 정책을 분리합니다.

  예를 들어, [Intune의 관리 템플릿](administrative-templates-windows.md)에는 수백 개의 ADMX 설정이 있습니다. 이러한 템플릿은 설정이 사용자 또는 디바이스에 적용되는지 여부를 표시합니다. 관리 템플릿을 만들 때 사용자 설정을 사용자 그룹에 할당하고 디바이스 그룹에 디바이스 설정을 할당합니다.

  다음 이미지는 사용자 및/또는 디바이스에 적용될 수 있는 설정의 예를 보여 줍니다.

  ![사용자 및 디바이스에 적용되는 Intune 관리 템플릿](./media/device-profile-create/setting-applies-to-user-and-device.png)

- 제한적인 정책을 만들 때마다 사용자에게 이러한 변경 사항을 알려야 합니다. 예를 들어 암호 요구 사항을 4자에서 6자로 변경하는 경우 정책을 할당하기 전에 사용자에게 알립니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](../device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
