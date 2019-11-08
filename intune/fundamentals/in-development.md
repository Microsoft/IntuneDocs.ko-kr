---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/28/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3720b0b9a67f0c3462993feef4162ef35f7f3f92
ms.sourcegitcommit: d1b36501186e867355843ddd67c795ade800b76a
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73182932"
---
# <a name="in-development-for-microsoft-intune---november-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 11월

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

### <a name="smime-support-for-microsoft-outlook-mobile----2669398----"></a>Microsoft Outlook Mobile에 대 한 S/MIME 지원 <!-- 2669398  -->
Intune은 iOS 및 Android의 Outlook Mobile에서 사용할 수 있는 S/MIME 서명 및 암호화 인증서 제공을 지원 합니다. 관련 정보는 [iOS 장치에 대 한 메일 설정](~/configuration/email-settings-ios.md) 및 [Android 장치에 대 한 전자 메일 설정](~/configuration/email-settings-android.md)을 참조 하세요.

### <a name="custom-settings-support-for-macos-applications----4736278----"></a>MacOS 응용 프로그램에 대 한 사용자 지정 설정 지원 <!-- 4736278  -->
Intune은 사용자 지정 설정을 지원 하므로 기존 기본 설정 속성 목록 (. info.plist) 파일에 특정 키 및 값을 추가 하 여 macOS 앱 및 장치를 구성할 수 있습니다. 일부 앱은 관리 되는 기본 설정을 지원 하지 않으며 일부 경우에는 특정 설정만 관리할 수 있습니다. 설정은 장치 채널을 통해서만 배포 됩니다. 장치 채널 설정을 대상으로 하는 속성 목록 파일 또는 .xml 파일만 업로드 해야 합니다.

### <a name="assignment-type-value-in-windows-company-portal----5459950----"></a>Windows 회사 포털의 할당 유형 값 <!-- 5459950  -->
Windows 회사 포털 앱의 **설치 된 앱** 페이지가 업데이트 됩니다. **설치 된 앱** 페이지의 **할당 유형** 열을 "조직에서 필요로 함"으로 업데이트 했습니다. 사용 가능한 값은 **예** 또는 **아니요** 이며 필수 및 사용 가능한 앱을 지정 합니다. 이러한 변경은 일부 최종 사용자 혼동에 대응 하 여 수행 됩니다. Windows 회사 포털에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](~/apps/company-portal-app.md)을 참조하세요.

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 모든 앱 사용 응용 프로그램에는이 기능을 사용할 수 없습니다. 앱에 대한 자세한 내용은 [앱 보호 정책이란?](../apps/app-protection-policy.md)을 참조하세요.


<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices----3246388----"></a>Windows 10 이상 장치에서 Wi-fi 프로필에 PKCS 인증서 사용 <!-- 3246388  -->
현재 SCEP 인증서 (**장치 구성** ** > > >  > ** **프로필** ) **를 사용 하** **여 windows wi-fi** 프로필을 인증할 수 있습니다. 프로필 유형 > **Enterprise** > **EAP 유형**). Windows Wi-fi 프로필에 PKCS 인증서를 사용할 수 있습니다. 이 기능을 사용 하면 사용자가 테 넌 트에서 새로운 또는 기존 PKCS 인증서 프로필을 사용 하 여 Wi-fi 프로필을 인증할 수 있습니다. 

Wi-fi 프로필에 대 한 자세한 내용은 [Intune에서 Windows 10 이상 장치에 대 한 wi-fi 설정 추가](../configuration/wi-fi-settings-windows.md)를 참조 하세요.

적용 대상:
- Windows 10 이상

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices----4892824----"></a>IOS 장치에서 전자 메일 장치 구성 프로필을 만들 때 새 ExchangeActiveSync 설정 <!-- 4892824  --> 
IOS/iPadOS 장치에서 장치 구성 프로필에서 전자 메일 연결을 구성할 수 있습니다. 장치 **구성 프로필 (** **장치 구성** > 프로필 > **Create profile** > **iOS/iPadOS** for platform > **email** 프로필 형식). 

다음을 비롯 한 새로운 ExchangeActiveSync 설정이 제공 됩니다.
- 전자 메일, 일정 및 연락처와 같은 동기화 할 서비스 (또는 동기화 차단)를 선택 합니다.
- 사용자가 자신의 장치에서 이러한 서비스에 대 한 동기화 설정을 변경할 수 있도록 허용 하거나 차단 합니다. 

현재 설정을 보려면 [Intune에서 iOS 장치에 대 한 메일 프로필 설정](../configuration/email-settings-ios.md)으로 이동 합니다.

적용 대상:
- iOS 13.0 이상
- iPadOS 13.0 이상

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices----5353228----"></a>사용자가 Android Enterprise 장치 소유자 및 전용 장치에 개인 Google 계정을 추가 하지 못하도록 설정 <!-- 5353228  -->
사용자가 Android Enterprise 장치 소유자 및 전용 장치 (**장치 구성** > **프로필** > **프로필** > **android enterprise에서 개인 Google 계정을 만들지 못하도록 할 수 있습니다.** 플랫폼 > 장치 소유자는 프로필 유형 > **사용자 및 계정 설정**)에 대 한 **장치 제한만 >** 합니다.

구성할 수 있는 현재 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상:
- Android Enterprise 디바이스 소유자
- Android 엔터프라이즈 전용 디바이스

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile----5468501----"></a>Siri commands 설정에 대 한 서버 쪽 로깅은 iOS 장치 제한 프로필에서 제거 됩니다. <!-- 5468501  -->
IOS 장치에서 Siri 명령에 대 한 서버 쪽 로깅을 구성 하는 장치 제한 프로필을 만들 수 있습니다. 장치**구성** > **프로필** > 프로필 > **iOS/iPadOS** for platform을 **만듭니다** . 프로필 형식 > **기본 제공 앱**)에 대 한 **장치 제한 사항을** > 합니다. **Siri commands 설정에 대 한 서버 쪽 로깅이** 제거 됩니다.

이 설정은 Intune 관리 콘솔에서 제거 됩니다. 이 설정이 구성 된 기존 정책에서 설정을 계속 표시 하더라도이 설정은 장치에 영향을 주지 않습니다. 기존 정책에서 설정을 제거 하려면 정책으로 이동 하 고, 사소한 편집을 수행 하 고, 저장 하 고, 정책이 업데이트 됩니다.

구성할 수 있는 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 및 iPadOS 디바이스 설정](../configuration/device-restrictions-ios.md)을 참조하세요.

적용 대상:
- iOS


<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="edit-device-name-value-for-autopilot-devices---2640074----"></a>Autopilot 장치에 대 한 장치 이름 값 편집<!-- 2640074  -->
Azure AD 가입 Autopilot 장치에 대 한 장치 이름 값을 편집할 수 있습니다. 이렇게 하려면 **Intune** > **장치 등록** > Windows **등록** > windows **Autopilot** > **장치** 로 이동 하 > 장치를 선택 하 > 오른쪽 창에서 **장치 이름** 값을 변경 합니다. **저장**을 > 합니다.


### <a name="edit-the-group-tag-value-for-autopilot-devices---4816775---"></a>Autopilot 장치에 대 한 그룹 태그 값 편집<!-- 4816775 -->
Autopilot 장치에 대 한 **그룹 태그** 값을 편집할 수 있습니다.

1. **Intune**  > **장치 등록**  >  Windows**등록**  > **windows Autopilot**  > **장치**를 선택 합니다.
1. 장치를 선택 합니다.
1. 오른쪽 창에서 **그룹 태그** 값을 변경 합니다.
1. **저장**을 선택합니다.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Jamf 관리를 필요로 하는 macOS 사용자 그룹을 대상으로 합니다. <!-- 4061739 -->
특정 사용자 그룹을 대상으로 지정 하 여 Jamf에서 macOS 장치를 관리 하도록 요구할 수 있습니다. 이 대상 지정을 통해 macOS 장치 하위 집합에 Jamf 준수 통합을 적용할 수 있으며, 다른 장치는 Intune에서 계속 관리 됩니다. 대상 지정을 통해 한 MDM (모바일 장치 관리) 시스템에서 다른 MDM (모바일 장치 관리) 시스템으로 사용자 장치를 점진적으로 마이그레이션할 수도 있습니다.

<!-- ***********************************************-->
## <a name="intune-apps"></a>Intune 앱

### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>회사 포털에서 macOS 등록 환경이 개선 됨 <!-- 5074349  -->
MacOS 등록 환경에 대 한 회사 포털에는 iOS 등록 환경에 대 한 회사 포털 보다 긴밀 하 게 맞는 등록 프로세스가 포함 됩니다. 장치 사용자에 게 표시 되는 항목:  

* Sleeker 사용자 인터페이스입니다.  
* 향상 된 등록 검사 목록.  
* 장치를 등록 하는 방법에 대 한 자세한 지침입니다.  
* 향상 된 문제 해결 옵션  

### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857----"></a>Android 용 회사 포털 앱의 향상 된 검사 목록 디자인<!-- 5550857  -->
Android 용 회사 포털 앱의 설치 검사 목록이 경량 디자인 및 새 아이콘으로 업데이트 됩니다. 변경 내용은 iOS 용 회사 포털 앱에 대 한 최근 업데이트에 맞게 정렬 됩니다.

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>모니터링 및 문제 해결

### <a name="updated-support-experience-------5012398------"></a>업데이트 된 지원 환경   <!--  5012398    -->
향상 된 기능을 제공 하는 과정에서 Intune에 대 한 콘솔 내 지원 환경을 업데이트 합니다.  콘솔 내 검색 및 일반적인 문제에 대 한 피드백을 개선 하 고 지원에 문의 하는 워크플로를 간소화 합니다.     

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>역할 기반 액세스 제어

### <a name="duplicate-custom-or-built-in-roles----1081938---"></a>중복 사용자 지정 또는 기본 제공 역할 <!-- 1081938 -->
기본 제공 및 사용자 지정 역할을 복사할 수 있습니다. 이렇게 하려면 **Intune** > **역할** > **모든 역할** 로 이동 하 > 목록에서 역할을 선택 하 > **복제**를 선택 합니다. 고유한 새 이름을 입력 해야 합니다.

<!-- ***********************************************-->

## <a name="security"></a>보안

### <a name="bitlocker-key-rotation--------2564951--------"></a>BitLocker 키 회전     <!-- 2564951      -->
Intune을 사용 하 여 Windows 버전 1909 이상을 실행 하는 관리 장치에 대 한 BitLocker 복구 키를 회전할 수 있습니다. 

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.
