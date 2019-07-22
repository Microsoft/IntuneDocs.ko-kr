---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6ee62213c9ef23302de7fa7342569e1903514699
ms.sourcegitcommit: 11a31cd39b727f2254e2705b07d18924e103bd2e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341353"
---
# <a name="in-development-for-microsoft-intune---july-2019"></a>개발 중인 Microsoft Intune 기능 - 2019년 7월

준비 및 계획을 지원하기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 또한,

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 보완적인 Office Message Center 게시물을 게시할 것입니다.
- 미리 보기 또는 일반적으로 사용할 수 있는 기능을 프로덕션 환경에서 시작하면 기능 설명이 이 페이지에서 [새로운 기능 페이지](whats-new.md)로 이동합니다.
- 이 페이지와 [새로운 기능 페이지](whats-new.md)는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [M365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!Note]
> 이러한 항목은 향후 릴리스에서 제공될 Intune 기능에 대한 Microsoft의 현재 기대를 반영합니다. 날짜 및 개별 기능이 변경될 수 있습니다. 개발 중인 모든 항목이 이 페이지에 기능 설명이 있는 것은 아닙니다.

**RSS 피드**: 다음(`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`) URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>앱 관리


### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>사용자 및 그룹에 대 한 사용자 지정 알림    <!-- 16766574   -->
곧 회사 포털 응용 프로그램에서 Intune으로 관리 하는 iOS 및 Android 장치 사용자에 게 사용자 지정 임시 푸시 알림을 보낼 수 있습니다. 이러한 사용자 지정 알림은 특정 Intune 기능에 연결 되지 않으며, 일부 또는 모든 직원에 게 전송 하려는 일반적인 알림을 포함 하 여 필요한 모든 용도에 사용할 수 있습니다.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱 보호 정책 (앱)을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 응용 프로그램을 사용 하도록 설정 된 응용 프로그램에는이 기능을 APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고 <!-- 3041956  -->
Android 작업 프로필 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태와, 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](apps-add-android-for-work.md#managed-google-play-app-type)을 참조하세요.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성


### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS용 IKEv2 VPN 프로필 지원 <!-- 1943438 -->
IKEv2 프로토콜을 사용하여 iOS 원시 VPN 클라이언트에 대한 VPN 프로필을 만들 수 있습니다. IKEv2는 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **VPN**(프로필 형식) > **설정**의 새 연결 형식입니다.

이 VPN 프로필은 원시 VPN 클라이언트를 구성합니다. 따라서 관리 디바이스에 VPN 클라이언트 앱이 설치되거나 푸시되지 않습니다. 이 기능을 사용하려면 디바이스를 Intune에 등록해야 합니다(MDM 등록).

구성할 수 있는 최신 VPN 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)을 참조하세요.

적용 대상: iOS

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 -->
Windows 10 다비이스 구성 프로필을 만듭니다(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10**). 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 대상: 
- Windows 10 이상

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Windows Defender 방화벽에 대한 고급 설정   <!--  1311949     -->
곧 공개 미리 보기로 Intune을 사용하여 Windows Defender용 클라이언트의 사용자 지정 방화벽 규칙을 관리할 수 있습니다.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Android Enterprise에 대 한 OEMConfig 프로필을 만들 때의 새 구성 디자이너 <!-- 3712769  -->
Intune에서 OEMConfig 앱 (장치 구성 > 프로필을 사용 하는 장치 구성 프로필을 만들 수 있습니다 > 프로필 > Android enterprise for platform >에 대 한 프로필 형식). 이 작업을 수행 하면 템플릿 및 값을 변경할 수 있는 JSON 편집기가 열립니다. 이 업데이트에는 제목, 설명 등을 포함 하 여 앱에 포함 된 세부 정보를 표시 하는 향상 된 사용자 환경을 제공 하는 구성 디자이너가 포함 되어 있습니다. JSON 편집기는 계속 사용할 수 있으며, 구성 디자이너에서 변경한 내용을 표시 합니다.

현재 설정을 확인 하려면 OEMConfig를 사용 하 여 [Android Enterprise 장치 사용 및 관리](android-oem-configuration-overview.md)로 이동 합니다.

적용 대상: Android 엔터프라이즈


<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="improve-device-location---3855417---"></a>장치 위치 개선<!-- 3855417 -->
**장치 찾기** 작업을 사용 하 여 장치의 정확한 좌표를 확대할 수 있습니다. 분실 한 iOS 장치를 찾는 방법에 대 한 자세한 내용은 [분실 한 ios 장치 찾기](device-locate.md)를 참조 하세요.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>자동 장치 정리 시간 제한을 30 일로 구성 <!--4231059  -->
자동 장치 정리 시간 제한은 마지막 로그인 후 30 일 (현재 제한인 90 일 대신)을 30 일로 설정할 수 있습니다. 이렇게 하려면 **Intune** > **장치** >  **설정장치** > **정리 규칙**으로 이동 합니다.


<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="import-and-export-security-baselines------3408610------------"></a>보안 기준 가져오기 및 내보내기    <!--3408610          -->  
사용자 지정을 사용 하 고 Intune 환경 사이에서 공유할 수 있도록 보안 기준을 내보내고 가져오는 기능을 추가 하 고 있습니다.



<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


