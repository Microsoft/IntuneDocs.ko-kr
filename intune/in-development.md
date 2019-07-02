---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 633bf52084ad261f768cb4e59aaf4ce0ab5cd5bc
ms.sourcegitcommit: 46f4d3d160e18aeab9de7477eedc8351fbb78c85
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/29/2019
ms.locfileid: "67468722"
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

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>다바이스 사용자는 설치했거나 설치하려고 시도한 모든 관리형 앱을 볼 수 있습니다. <!-- 2352913 -->
Windows용 회사 포털은 사용자의 디바이스에 (필수 및 사용 가능한) 모든 관리형 앱을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수 있습니다. 조직에서 앱을 필수 또는 사용 가능하게 설정하지 않으면 회사 앱이 설치되지 않았다는 메시지가 사용자에게 표시됩니다. 사용자도 설치 상태별로 앱을 정렬하거나 필터링할 수 있습니다.

### <a name="customized-notifications-for-users-and-groups-------16766574-----"></a>사용자 및 그룹에 대 한 사용자 지정된 알림    <!-- 16766574   -->
곧 iOS 및 Android 장치의 Intune로 관리 하는 사용자에 게 회사 포털 응용 프로그램에서 사용자 지정 임시 푸시 알림을 보낼 수 있습니다. 이러한 사용자 지정 알림을 특정 Intune 기능에 연결 되지 않습니다 및 일부를 전송 하려는 일반 알림 포함 해야 하는 목적을 위해 사용할 수 있습니다 또는 모든 직원입니다.  

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠를 구성 합니다. <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱 보호 정책 (APP) 하면 제어 앱 알림 콘텐츠를 조직 계정에 대 한 합니다. 이 기능은 지원 응용 프로그램에서 필요 하 고 사용 하도록 설정 하는 앱의 모든 응용 프로그램에 사용할 수 없습니다. APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

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

### <a name="administrative-templates-for-group-policy---------3510695---"></a>그룹 정책 관리 템플릿     <!--  3510695 -->
클라우드에서 디바이스 보안을 높이기 위해 Intune을 사용하여 Windows PC용 그룹 정책 설정 선택을 구성할 수 있는 관리 템플릿을 출시할 것입니다.  이러한 템플릿은 정책 CSP(구성 서비스 공급자)를 사용하여 Office, Windows 및 OneDrive로부터 최대 2,500개의 추가 설정을 제공합니다.

### <a name="manage-filevault-for-macos-------3858502--1210104-----"></a>MacOS에 대해 FileVault를 관리 합니다.   <!--  3858502 + 1210104   -->
Intune endpoint protection 장치 구성 프로필을 사용 하 여 macOS 장치에 대해 FileVault 키 암호화를 관리할 수 있습니다. 보기 및 회사 장치의 암호화 키 회전의 에스크로 포함 됩니다. 최종 사용자가 회사 포털 웹 사이트를 통해 해당 키를 검색할 수 있습니다.

### <a name="advanced-settings-for-windows-defender-firewall-------1311949-------"></a>Windows Defender 방화벽에 대한 고급 설정   <!--  1311949     -->
곧 공개 미리 보기로 Intune을 사용하여 Windows Defender용 클라이언트의 사용자 지정 방화벽 규칙을 관리할 수 있습니다.  

### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769----"></a>Android Enterprise에 대 한 OEMConfig 프로필을 만들 때 새 구성 디자이너 <!-- 3712769  -->
Intune에서 OEMConfig 앱을 사용 하는 장치 구성 프로필을 만들 수 있습니다 (장치 구성 > 프로필 > 프로필 만들기 > 플랫폼에 대 한 Android 엔터프라이즈 > 프로필 유형에 대해 OEMConfig). 이렇게 하면 템플릿 및 변경 하는 값을 사용 하 여 JSON 편집기를 엽니다. 이 업데이트는 제목, 설명 등을 포함 하 여 앱에 포함 된 세부 정보를 표시 하는 향상 된 사용자 환경 사용 하 여 구성 디자이너를 포함 합니다. JSON 편집기를 계속 사용할 수 있으며 구성 디자이너에서 수행한 모든 변경 내용을 보여 줍니다.

현재 설정을 보려면로 이동 [사용 하 여 OEMConfig 사용 하 여 Android 엔터프라이즈 장치를 관리 하 고](android-oem-configuration-overview.md)입니다.

적용 대상: Android 엔터프라이즈


<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="improve-device-location---3855417---"></a>장치 위치를 개선 합니다.<!-- 3855417 -->
사용 하 여 장치 정확한 좌표 맞게 확대/축소할 수는 **장치 찾기** 작업 합니다. 분실된 한 iOS 장치를 찾는 방법에 대 한 자세한 내용은 참조 하세요. [분실 iOS 장치 찾기](device-locate.md)합니다.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>30 일 아래로 자동 장치 정리 시간 제한 구성 <!--4231059  -->
마지막 로그인 이후 30 일 (최대 90 일 현재) 대신 짧게 자동 장치 정리 시간 제한을 설정할 수 있습니다. 이렇게 하려면로 이동 **Intune** > **장치** > **설치** > **장치 정리 등록 규칙**합니다.


<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="import-and-export-security-baselines------3408610------------"></a>가져오기 및 보안 기준 내보내기    <!--3408610          -->  
기능을 사용자와 사용자 지정을 수행 하 고 Intune 환경 간에 공유할 수 있도록 보안 기준의 내보내고 추가 될 예정입니다.



<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


