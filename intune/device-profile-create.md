---
title: Microsoft Intune - Azure에서 디바이스 프로필 만들기 | Microsoft Docs
description: Microsoft Intune에서 디바이스 구성 프로필을 추가 또는 구성합니다. 플랫폼 형식을 선택하고, 설정을 구성하고, 범위 태그를 추가합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 08c6ece37a4ff6eceaa4df735f365453a4bc7d88
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59570405"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 프로필 만들기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

디바이스 프로필을 사용하여 설정을 추가 및 구성한 후 조직의 디바이스에 이 설정을 밀어넣을 수 있습니다. 수행할 수 있는 작업을 포함하여 자세한 내용은 [디바이스 프로필을 사용하여 디바이스에서 기능 및 설정 적용](device-profiles.md)을 참조하세요.

이 문서의 내용은 다음과 같습니다.

- 프로필을 만드는 단계를 나열합니다.
- 범위 태그를 추가하여 프로필을 "필터링"하는 방법을 보여 줍니다.
- 디바이스가 프로필 및 프로필 업데이트를 받는 체크 인 새로 고침 주기 시간을 나열합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링하고 **Intune**을 선택합니다.

2. **디바이스 구성**을 선택합니다. 다음과 같은 옵션을 선택할 수 있습니다.

    - **개요**: 사용자 프로필의 상태를 나열하고 사용자 및 디바이스에 할당한 프로필에 관한 추가 세부 내용을 제공합니다.
    - **관리**: 디바이스 프로필을 만들어 프로필 내에서 실행할 사용자 지정 [PowerShell 스크립트](intune-management-extension.md)를 업로드하고, [eSIM](esim-device-configuration.md)을 사용하는 디바이스에 데이터 플랜을 추가합니다.
    - **모니터**: 성공 또는 실패에 대한 프로필 상태를 확인하고 프로필 로그도 봅니다.
    - **설치**: SCEP 또는 PFX 인증 기관을 추가하거나 [TEM(Telecom Expense Management)](telecom-expenses-monitor.md)을 프로필에 사용하도록 설정합니다.

3. **프로필** > **프로필 만들기**를 선택합니다. 다음 속성을 입력합니다.

   - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 WP 메일 프로필**은 좋은 프로필 이름입니다.
   - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
   - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.  

       - **OWA(Outlook Web Access)**
       - **Android 엔터프라이즈**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 이상**
       - **Windows 10 이상**

   - **프로필 유형**: 만들려는 설정 유형을 선택합니다. 표시된 목록은 선택한 **플랫폼**에 따라 달라집니다.
   - **설정**: 다음 아티클에서는 각 프로필의 설정에 대해 설명합니다.

       - [관리 템플릿](administrative-templates-windows.md)
       - [사용자 지정](custom-settings-configure.md)
       - [배달 최적화](delivery-optimization-windows.md)
       - [디바이스 기능](device-features-configure.md)
       - [디바이스 제한 사항](device-restrictions-configure.md)
       - [버전 업그레이드 및 모드 전환](edition-upgrade-configure-windows-10.md)
       - [교육](education-settings-configure.md)
       - [전자 메일](email-settings-configure.md)
       - [엔드포인트 보호](endpoint-protection-configure.md)
       - [ID 보호](identity-protection-configure.md)  
       - [키오스크](kiosk-settings.md)
       - [PKCS 인증서](certficates-pfx-configure.md)
       - [SCEP 인증서](certificates-scep-configure.md)
       - [신뢰할 수 있는 인증서](certificates-configure.md)
       - [업데이트 정책](software-updates-ios.md)
       - [VPN](vpn-settings-configure.md)
       - [Wi-Fi](wi-fi-settings-configure.md)
       - [Windows Defender ATP](advanced-threat-protection.md)
       - [Windows Information Protection](windows-information-protection-configure.md)

     예를 들어 플랫폼에 **iOS**를 선택하는 경우 프로필 유형 옵션은 다음 프로필과 비슷하게 표시됩니다.

     ![Intune에서 iOS 프로필 만들기](./media/create-device-profile.png)

4. 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 목록에 표시됩니다.

## <a name="scope-tags"></a>범위 태그

설정을 추가한 후 프로필에 범위 태그를 추가할 수도 있습니다. 범위 태그는 HR 또는 모든 US-NC 직원과 같은 특정 그룹으로 정책을 할당 및 필터링합니다.

범위 태그 및 수행할 수 있는 작업에 대한 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

### <a name="add-a-scope-tag"></a>범위 태그 추가

1. **범위(태그)** 를 선택합니다.
2. **추가**를 선택하여 새 범위 태그를 만듭니다. 또는 목록에서 기존 범위 태그를 선택합니다.
3. **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="refresh-cycle-times"></a>주기 시간 새로 고침

Intune은 다음 새로 고침 주기를 사용하여 구성 프로필의 업데이트가 있는지 확인합니다.

| 플랫폼 | 새로 고침 주기|
| --- | --- |
| iOS | 6시간마다 |
| macOS | 6시간마다 |
| Android | 8시간마다 |
| 디바이스로 등록된 Windows 10 PC | 8시간마다 |
| Windows Phone | 8시간마다 |
| Windows 8.1 | 8시간마다 |

최근 등록된 디바이스인 경우 다음과 같이 체크 인이 더 자주 실행됩니다.

| 플랫폼 | 빈도 |
| --- | --- |
| iOS | 6시간 동안 15분마다/그 이후에는 6시간마다 |  
| macOS | 6시간 동안 15분마다/그 이후에는 6시간마다 | 
| Android | 15분 동안 3분마다/그 이후 2시간 동안은 15분마다/그 이후에는 8시간마다 | 
| 디바이스로 등록된 Windows 10 PC | 30분 동안 3분마다/그 이후에는 8시간마다 | 
| Windows Phone | 15분 동안 5분마다/그 이후 2시간 동안은 15분마다/그 이후에는 8시간마다 | 
| Windows 8.1 | 15분 동안 5분마다/그 이후 2시간 동안은 15분마다/그 이후에는 8시간마다 | 

언제든 사용자는 회사 포털 앱을 열고 디바이스를 동기화하여 즉시 프로필 업데이트를 확인할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
