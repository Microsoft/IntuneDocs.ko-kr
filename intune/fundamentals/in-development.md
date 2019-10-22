---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: ea5fae72f6e2057ef0b03a7bd295085ed1ac3bbd
ms.sourcegitcommit: 5807f4db4a45a093ce2fd6cb0c480bec384ec1ff
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601537"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 10월

준비 및 계획을 돕기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 이 페이지의 정보 외에도:

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 Office 메시지 센터에 보완 게시물을 게시할 것입니다.
- 기능이 프로덕션 환경에 들어가면 미리 보기 인지, 일반 공급 인지에 관계 없이 기능 설명이이 페이지에서 [새로운](whats-new.md)기능으로 이동 됩니다.
- 이 페이지와 [새로운 기능](whats-new.md) 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [Microsoft 365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!NOTE]
> 이 페이지에는 향후 릴리스에서 제공 되는 Intune 기능에 대 한 현재 기대치가 반영 됩니다. 날짜 및 개별 기능이 변경될 수 있습니다. 이 페이지는 개발의 모든 기능을 설명 하지는 않습니다.

**RSS 피드**: URL `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`를 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>앱 관리

### <a name="apply-dark-mode-in-ios-company-portal----4911422----"></a>IOS 회사 포털에서 어둡게 모드 적용 <!-- 4911422  -->
진한 모드는 iOS 회사 포털에 대해 계획 됩니다. 회사 앱을 다운로드 하 고, 장치를 관리 하 고, 선택한 색 구성표에서 IT 지원을 받을 수 있습니다. iOS 회사 포털에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md)을 참조하세요.

### <a name="run-win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Windows 10 S 모드 장치에서 Win32 앱 실행 <!-- 3747604  --> 
Windows 10 S 모드에서 관리 되는 장치에서 Win32 앱을 설치 하 고 실행할 수 있습니다. Windows Defender 응용 프로그램 제어 (WDAC) PowerShell 도구를 사용 하 여 S 모드에 대 한 추가 정책을 하나 이상 만듭니다. Device Guard 서명 포털을 사용 하 여 추가 정책에 서명 합니다. 그런 다음, Intune을 통해 정책을 업로드 하 고 배포 합니다. 

Intune에서 **클라이언트 앱**  > **Windows 10 S 보충 정책**을 선택 하 여이 기능을 찾을 수 있습니다. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>날짜 및 시간을 기준으로 앱 가용성 설정 <!-- 3510685  -->
관리자는 필수 앱에 대 한 시작 시간 및 최종 기한을 구성할 수 있습니다. 시작 시 Intune 관리 확장에서 앱 콘텐츠를 다운로드 하 여 캐시 합니다. 앱이 최종 기한 시간에 설치 됩니다. 사용 가능한 앱의 경우 앱이 회사 포털에 표시 되 면 시작 시간이 결정 됩니다. 

날짜 및 시간을 기준으로 앱 가용성을 설정 하려면:

1. Intune에서 **클라이언트 앱** > **앱**을 차례로 선택합니다. 
1. 목록에서 앱을 선택 하거나 **추가**를 선택 하 여 새 앱을 추가 합니다. 
1. 앱 블레이드에서 **할당** > **그룹 추가**를 선택 합니다. 
1. **할당 유형을** **필수** 로 설정 하 고 **포함 된 그룹**을 선택 합니다. 
1. **모든 사용자에 게이 앱 필요** 를 **예**로 설정 합니다. 
1. **편집** 을 선택 하 여 **최종 사용자 환경** 옵션을 수정 합니다. 
1. **최종 사용자 환경** 블레이드에서 필요한 경우 **소프트웨어를 사용할 수 있는 시간** 을 설정 합니다. 

자세한 내용은 [Microsoft Intune에 앱 추가](../apps/apps-add.md)를 참조하세요.

### <a name="require-win32-apps-to-restart----3136567----"></a>Win32 앱을 다시 시작 해야 함 <!-- 3136567  -->
성공적으로 설치한 후에는 Win32 앱을 다시 시작 해야 할 수 있습니다. 다시 시작 하기 전 까지의 시간 (유예 기간)을 선택할 수 있습니다.

### <a name="display-notifications-for-the-company-portal-app-on-windows----1808082----"></a>Windows에서 회사 포털 앱에 대 한 알림 표시 <!-- 1808082  -->
응용 프로그램이 닫힌 경우에도 사용자에 게 알림 메시지를 표시 하도록 Windows 장치의 회사 포털 앱을 업데이트 합니다. 업데이트는 설치 상태를 완료 하거나 실패 한 경우에만 사용 가능한 앱에 대 한 알림을 표시 합니다. 회사 포털 앱은 필요한 응용 프로그램에 대 한 알림을 표시 하지 않습니다.

### <a name="display-installation-status-messages-for-the-company-portal-app----2514416----"></a>회사 포털 앱에 대 한 설치 상태 메시지 표시 <!-- 2514416  -->
회사 포털 앱은 최종 사용자에 게 추가 앱 설치 상태 메시지를 표시 합니다. 새 Win32 종속성 기능에는 다음과 같은 조건이 적용 됩니다.
- 앱을 설치하지 못했습니다. 관리자가 정의한 종속성이 충족 되지 않았습니다.
- 앱이 성공적으로 설치 되었지만 다시 시작 해야 합니다.
- 앱을 설치 하는 중 이지만 계속 하려면 다시 시작 해야 합니다.

### <a name="assign-the-microsoft-edge-beta-for-macos----4678761----"></a>MacOS 용 Microsoft Edge beta 할당 <!-- 4678761  -->
MacOS 장치용 Intune에 최신 버전의 Microsoft Edge beta를 추가 하 고 할당할 수 있습니다. 

MacOS 장치에 대해 Microsoft Edge beta를 할당 하려면:
1. Intune에서 **클라이언트 앱** > **앱** > **앱 추가** > **Microsoft Edge - macOS**를 선택합니다. 
1. 원하는 그룹에 Microsoft Edge beta를 할당 합니다. MAU (microsoft 자동 업데이트)는 Microsoft Edge를 최신 상태로 유지 합니다. 
 
Microsoft Edge에 대 한 자세한 내용은 [Microsoft Intune를 사용 하 여 Microsoft edge를 사용 하 여 웹 액세스 관리](../apps/manage-microsoft-edge.md)를 참조 하세요.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 모든 앱 사용 응용 프로그램에는이 기능을 사용할 수 없습니다. 앱에 대한 자세한 내용은 [앱 보호 정책이란?](../apps/app-protection-policy.md)을 참조하세요.


<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="new-device-firmware-configuration-interface-profile-for-devices-that-run-windows-10-and-later----2266073----"></a>Windows 10 이상을 실행 하는 장치에 대 한 새 장치 펌웨어 구성 인터페이스 프로필 <!-- 2266073  -->
Windows 10 이상에서는 설정 및 기능을 제어 하는 장치 구성 프로필을 만들 수 있습니다. 

1. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
1. 플랫폼에서 **Windows 10 이상**을 선택합니다. 
 
새 장치 펌웨어 구성 인터페이스 프로필 유형을 사용 하면 Intune에서 UEFI (BIOS) 설정을 관리할 수 있습니다.

구성할 수 있는 현재 설정에 대 한 자세한 내용은 [Microsoft Intune 장치 프로필을 사용 하 여 장치에 기능 및 설정 적용](../configuration/device-profiles.md)을 참조 하세요.

이 기능은 Windows 10 RS5 (1809) 이상에서 장치 선택에 적용 됩니다.
 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>디바이스 등록

### <a name="for-ios-devices-customize-the-enrollment-privacy-window-of-company-portal----4394993----"></a>IOS 장치에 대 한 등록 개인 정보 창 사용자 지정 회사 포털 <!-- 4394993  -->
Markdown을 이용하면 iOS 등록 과정에서 최종 사용자에게 표시되는 회사 포털의 개인 정보 창을 사용자 지정할 수 있습니다. 특히, 조직에서 디바이스에 표시 또는 디바이스에서의 수행을 금지하는 항목의 목록을 사용자 지정할 수 있습니다.

<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Autopilot 장치에 대 한 그룹 태그 값 편집<!-- 4816775 -->
Autopilot 장치에 대 한 **그룹 태그** 값을 편집할 수 있습니다.

1. **Intune**  > **장치 등록**  >  Windows**등록**  > **windows Autopilot**  > **장치**를 선택 합니다.
1. 장치를 선택 합니다.
1. 오른쪽 창에서 **그룹 태그** 값을 변경 합니다.
1. **저장**을 선택합니다.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Jamf 관리를 필요로 하는 macOS 사용자 그룹을 대상으로 합니다. <!-- 4061739 -->
특정 사용자 그룹을 대상으로 지정 하 여 Jamf에서 macOS 장치를 관리 하도록 요구할 수 있습니다. 이 대상 지정을 통해 macOS 장치 하위 집합에 Jamf 준수 통합을 적용할 수 있으며, 다른 장치는 Intune에서 계속 관리 됩니다. 대상 지정을 통해 한 MDM (모바일 장치 관리) 시스템에서 다른 MDM (모바일 장치 관리) 시스템으로 사용자 장치를 점진적으로 마이그레이션할 수도 있습니다.

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>MacOS 장치에 소프트웨어 업데이트 배포 <!-- 3194876 -->
MacOS 장치 그룹에 소프트웨어 업데이트를 배포할 수 있습니다. 이 기능에는 중요, 펌웨어, 구성 파일 및 기타 업데이트가 포함 됩니다. 다음 장치 체크 인에서 업데이트를 보낼 수 있습니다. 또는 설정 된 기간 내에 업데이트를 배포 하는 주별 일정을 선택할 수 있습니다. 

이 기능을 사용 하면 표준 근무 시간 외에 장치를 업데이트 하거나 지원 센터를 완전히 팀으로 구성 하는 시간 외에 장치를 업데이트할 수 있습니다. 또한 업데이트가 배포 된 모든 macOS 장치에 대 한 자세한 보고서를 볼 수 있습니다. 장치별로 보고서를 드릴 하 여 특정 업데이트의 상태를 확인할 수 있습니다.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>모니터링 및 문제 해결

### <a name="android-report-on-the-devices-overview-page----2984353----"></a>장치 개요 페이지의 Android 보고서 <!-- 2984353  -->
**장치 개요** 페이지에 새 보고서를 추가 합니다. 이 보고서에는 각 장치 관리 솔루션에 등록 된 Android 장치 수가 표시 됩니다. 이 차트에는 회사 프로필에 대 한 장치 수, 완전히 관리 되는 전용 및 장치 관리자가 등록 된 수가 표시 됩니다. 

보고서를 보려면 **Intune** > **장치** > **개요**를 선택 합니다.

### <a name="updated-support-experience-------5012398------"></a>업데이트 된 지원 환경   <!--  5012398    -->
향상 된 기능을 제공 하는 과정에서 Intune에 대 한 콘솔 내 지원 환경을 업데이트 합니다.  콘솔 내 검색 및 일반적인 문제에 대 한 피드백을 개선 하 고 지원에 문의 하는 워크플로를 간소화 합니다.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.
