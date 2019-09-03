---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2b96fa9fac25f6de4180d3dcc9ee4022a2cc43fe
ms.sourcegitcommit: 7484ef8006f6b81d8976c328dd704512a31872ec
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70190240"
---
# <a name="in-development-for-microsoft-intune---september-2019"></a>Microsoft Intune용으로 개발 중 - 2019년 9월

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

### <a name="managed-google-play-private-lob-apps----1464182----"></a>관리 되는 Google Play 개인 LOB 앱 <!-- 1464182  -->
Intune을 통해 IT 관리자는 Intune 콘솔에 포함 된 iframe을 통해 개인 Android LOB 앱을 관리 되는 Google Play에 게시할 수 있습니다.  현재 IT 관리자는 많은 단계가 필요 하 고 시간이 많이 소요 되는 Google Play 게시 콘솔에 직접 LOB 앱을 게시 해야 합니다.  이 새로운 기능을 사용 하면 Intune 콘솔을 벗어날 필요 없이 최소한의 단계 집합을 사용 하 여 LOB 앱을 쉽게 게시할 수 있습니다.  관리 되는 Google Play을 사용 하는 Android Enterprise 관리 시나리오는이 기능 (회사 프로필, 전용, 완전히 관리 및 등록 되지 않은 장치)을 활용할 수 있습니다.  Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. 그런 다음 **앱 유형** 목록에서 **관리 Google Play** 를 선택 합니다. 관리 되는 Google Play 앱에 대 한 자세한 내용은 [Intune을 사용 하 여 Android Enterprise 장치에 관리 되는 Google Play 앱 추가](apps-add-android-for-work.md)를 참조 하세요.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>앱 설치 상태 메시지 회사 포털 <!-- 2514416  -->
회사 포털 앱은 최종 사용자에 게 추가 앱 설치 상태 메시지를 표시 합니다. 새 Win32 종속성 기능에는 다음과 같은 조건이 적용 됩니다.
- 앱을 설치하지 못했습니다. 관리자가 정의한 종속성이 충족 되지 않았습니다.
- 앱이 성공적으로 설치 되었지만 다시 시작 해야 합니다.
- 앱을 설치 하는 중입니다. 계속 하려면 다시 시작 해야 합니다.

### <a name="managed-google-play-iframe-support----2871756----"></a>관리 되는 Google Play iframe 지원 <!-- 2871756  -->
Intune은 관리 되는 Google Play iframe을 통해 Intune 콘솔에서 직접 웹 링크를 추가 하 고 관리할 수 있도록 지원 합니다.  이를 통해 IT 관리자는 URL 및 아이콘 그래픽을 제출한 다음 일반 Android 앱과 마찬가지로 이러한 링크를 장치에 배포할 수 있습니다. 관리 되는 Google Play을 사용 하는 Android Enterprise 관리 시나리오는이 기능 (회사 프로필, 전용, 완전히 관리 및 등록 되지 않은 장치)을 활용할 수 있습니다.  Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. 그런 다음 **앱 유형** 목록에서 **관리 Google Play** 를 선택 합니다. 관리 되는 Google Play 앱에 대 한 자세한 내용은 [Intune을 사용 하 여 Android Enterprise 장치에 관리 되는 Google Play 앱 추가](apps-add-android-for-work.md)를 참조 하세요.

### <a name="macos-support-for-vpp-apps----3173501----"></a>VPP 앱에 대 한 macOS 지원 <!-- 3173501  -->
apple VPP 토큰을 Intune에서 동기화 할 때 Apple Business Manager를 사용 하 여 구매한 macOS 앱이 콘솔에 표시 됩니다. 콘솔을 사용 하 여 그룹에 대 한 장치 및 사용자 기반 라이선스를 할당, 해지 및 재할당할 수 있습니다. Microsoft Intune는 회사에서 사용 하기 위해 구매한 VPP 앱을 관리 하는 데 도움이 됩니다.
- 앱 스토어에서 라이선스 정보 보고.
- 사용한 라이선스 수 추적.
- 소유한 것보다 많은 앱 복사본을 설치하지 않도록 도움.
Intune 및 VPP에 대한 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 앱 및 전자책 관리](vpp-apps.md)를 참조하세요.

### <a name="macos-support-for-web-apps----3174427----"></a>웹 앱에 대 한 macOS 지원 <!-- 3174427  -->
웹 앱을 설치할 수 있습니다 .이를 통해 웹의 URL에 대 한 바로 가기를 macOS 회사 포털를 사용 하는 도크에 추가할 수 있습니다. 최종 사용자는 macOS 회사 포털의 웹 앱에 대 한 앱 세부 정보 페이지에서 **설치** 작업에 액세스할 수 있습니다. **웹 링크** 앱 유형에 대 한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조 하세요.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>MacOS에 대 한 Microsoft Edge beta 할당 <!-- 4678761  -->
MacOS 장치용 Intune에 최신 버전의 Microsoft Edge beta를 추가 하 고 할당할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **앱** > **추가MicrosoftEdge-macos**를선택합니다. 그런 다음 원하는 그룹에 Microsoft Edge beta를 할당 합니다. MAU (microsoft 자동 업데이트)는 Microsoft Edge를 최신 상태로 유지 합니다. Microsoft Edge에 대 한 자세한 내용은 [Microsoft Intune를 사용 하 여 Microsoft edge를 사용 하 여 웹 액세스 관리](manage-microsoft-edge.md)를 참조 하세요.

### <a name="read-and-write-graph-api-operations-for-intune-apps----5031704----"></a>Intune 앱에 대 한 읽기 및 쓰기 Graph API 작업 <!-- 5031704  -->
응용 프로그램은 사용자 자격 증명 없이 앱 id를 사용 하 여 읽기 및 쓰기 작업을 모두 사용 하 여 Intune Graph API를 호출할 수 있습니다. Intune에 대해 Microsoft Graph API를 액세스하는 방법에 대한 자세한 내용은 [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)(Microsoft Graph에서 Intune 사용)를 참조하세요.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱 보호 정책 (앱)을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 응용 프로그램을 사용 하도록 설정 된 응용 프로그램에는이 기능을 APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고 <!-- 3041956  -->
Android 작업 프로필 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태 및 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](apps-add-android-for-work.md#managed-google-play-app-type)을 참조하세요.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type----4886161----"></a>IOS 및 macOS 설정에 대 한 장치 기능, 장치 제한 및 확장 프로필은 등록 형식으로 표시 됩니다. <!-- 4886161  -->

Intune에서 ios 및 macos 장치에 대 한 프로필을 만듭니다 (**장치 구성** > **프로필** > 은 플랫폼 > **장치 기능을 위한 프로필** > **iOS** 또는 **macos** 만들기). **,** **장치 제한**또는 프로필 형식에 대 한 **확장** ). 현재 이러한 프로필에서 사용 가능한 설정이 나열 됩니다. 

이후 업데이트에서 Intune 포털의 사용 가능한 설정은 적용 되는 등록 유형에 따라 분류 됩니다.

- iOS
  - 모든 등록 유형
  - 장치 등록 및 자동화 된 장치 등록
  - 자동 장치 등록

- macOS
  - 모든 등록 유형
  - 디바이스 등록
  - 사용자 승인 및 자동 장치 등록
  - 자동 장치 등록

적용 대상:

- iOS
  - [디바이스 기능](ios-device-features-settings.md)
  - [디바이스 제한 사항](device-restrictions-ios.md)

- macOS
  - [디바이스 기능](macos-device-features-settings.md)
  - [디바이스 제한 사항](device-restrictions-macos.md)
  - [확장](kernel-extensions-settings-macos.md)

### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode----4892835----"></a>키오스크 모드에서 실행 되는 감독 된 iOS 장치에 대 한 새 음성 제어 설정 <!-- 4892835  -->

Intune에서 감독 된 iOS 장치를 키오스크 또는 전용 장치로 실행 하는 정책을 만들 수 있습니다.**장치 구성** > **프로필** > 은 플랫폼에 대 한**프로필** > **iOS** 를 만듭니다 > **프로필 유형** > **키오스크 (감독**모드인 경우에만)에 대 한 장치 제한 

향후 업데이트에는 다음을 제어할 수 있는 새로운 설정이 있습니다.

- **음성 컨트롤**: 키오스크 모드에서 장치에 대 한 음성 제어를 사용 하도록 설정 합니다.
- **음성 컨트롤 수정**: 사용자가 키오스크 모드에서 장치에 대 한 음성 제어 설정을 변경할 수 있습니다.

현재 설정을 보려면 [IOS 키오스크 (감독 모드인 경우에만) 설정](device-restrictions-ios.md#kiosk-supervised-only)으로 이동 합니다.

적용 대상:

- iOS 13.0 이상

### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices----4893175----"></a>IOS 및 macOS 장치에서 앱 및 웹 사이트에 Single Sign-On 사용 <!-- 4893175  -->
향후 업데이트에는 ios 및 macos 장치에 대 한 몇 가지 새로운 Single Sign-On 설정이 있습니다 (**장치 구성** > **프로필** > 은 다음에 대 한**프로필** > **ios** 또는 **macos** 만들기). 프로필 형식에 대 한 플랫폼 > **장치 기능** ).

이러한 설정을 사용 하 여 특히 Kerberos 인증을 사용 하는 앱 및 웹 사이트에 대 한 Single Sign-On 환경을 구성할 수 있습니다. 일반 자격 증명 Single Sign-On 앱 확장 및 Apple의 기본 제공 Kerberos 확장 중에서 선택할 수 있습니다.

구성할 수 있는 현재 장치 기능을 보려면 [iOS 장치 기능](ios-device-features-settings.md) 및 [macos 장치 기능](macos-device-features-settings.md)으로 이동 합니다.

적용 대상:

- iOS 13.0 이상
- macOS 10.15 이상

### <a name="associate-domains-to-apps-on-macos-1015-devices----4898079----"></a>MacOS 10.15 + 장치에서 앱에 도메인 연결 <!-- 4898079  -->
Macos 장치에서 다양 한 기능을 구성 하 고, 정책을 사용 하 여 장치에 이러한 기능을 푸시할 수 있습니다.**장치 구성** > **프로필** > 만들기에 대 한**프로필** > **macos** 프로필 형식에 대 한 플랫폼 > **장치 기능** ). 향후 업데이트에서 도메인을 앱에 연결할 수 있습니다. 이 기능은 앱과 관련 된 웹 사이트와 자격 증명을 공유 하는 데 도움이 되며 Apple의 Single Sign-On 확장, 범용 링크 및 암호 자동 채우기와 함께 사용할 수 있습니다. 

구성할 수 있는 현재 기능을 확인 하려면 [Intune에서 Macos 장치 기능 설정](macos-device-features-settings.md)으로 이동 합니다.

적용 대상:

- macOS 10.15 이상

### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices----4928474----"></a>IOS 감독 장치에서 앱을 표시 하거나 숨길 때 iTunes 앱 스토어 URL에서 "itunes" 및 "apps"를 사용 합니다. <!-- 4928474  --> 
Intune에서 감독 된 iOS 장치에서 앱을 표시 하거나 숨기는 정책을 만들 수 있습니다 (**장치 구성** > **프로필** > 플랫폼 > 장치용**iOS** **프로필 만들기** >  **앱 유형** > **앱 표시/숨기기 (감독**모드인 경우에만)에 대 한 제한 사항입니다. 

ITunes 앱 스토어 URL (예: `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`)을 입력할 수 있습니다. 이후 업데이트에서는 URL에 및 `apps` `itunes` 를 모두 사용할 수 있습니다. 예를 들면 다음과 같습니다.

- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

이러한 설정에 대 한 자세한 내용은 [앱 표시 또는 숨기기 (감독](device-restrictions-ios.md#show-or-hide-apps-supervised-only)모드인 경우에만)를 참조 하세요.

적용 대상:

- iOS

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS용 IKEv2 VPN 프로필 지원 <!-- 1943438 -->
IKEv2 프로토콜을 사용하여 iOS 원시 VPN 클라이언트에 대한 VPN 프로필을 만들 수 있습니다. IKEv2는 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **VPN**(프로필 형식) > **설정**의 새 연결 형식입니다.

이 VPN 프로필은 원시 VPN 클라이언트를 구성합니다. 따라서 관리 디바이스에 VPN 클라이언트 앱이 설치되거나 푸시되지 않습니다. 이 기능을 사용하려면 디바이스를 Intune에 등록해야 합니다(MDM 등록).

구성할 수 있는 최신 VPN 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)을 참조하세요.

적용 대상: iOS


<!-- ***********************************************-->
## <a name="device-enrollment"></a>디바이스 등록

### <a name="new-tenants-will-default-away-from-android-device-administrator-management----4869790----"></a>Android 장치 관리자 관리에서 새 테 넌 트가 기본적으로 사라집니다. <!-- 4869790  -->
Android의 장치 관리자 기능은 Android Enterprise로 대체 되었습니다. 따라서 새로운 등록 Android Enterprise를 대신 사용 하는 것이 좋습니다. 이후 업데이트에서는 새 테 넌 트가 android 등록에서 장치 관리자 관리를 사용 하기 위해 다음 필수 구성 요소 단계를 완료 해야 합니다. **Intune** > **장치 등록** > **android 등록** 으로 이동 합니다. 장치 관리권한이 >  **있는 개인 및 회사 소유 장치는**장치**관리자를 사용 하 여 장치를 관리**합니다.  > 

기존 테 넌 트가 환경에서 변경 되지 않습니다. 

Intune의 Android 장치 관리자에 대 한 자세한 내용은 [android 장치 관리자 등록](https://docs.microsoft.com/intune/android-enroll-device-administrator)을 참조 하세요.

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS 장치에 대해 회사 포털 등록 프로세스 개인 정보 화면을 사용자 지정 합니다. <!-- 4394993  -->
Markdown를 사용 하면 iOS 등록 중 최종 사용자에 게 표시 되는 회사 포털 개인 정보 화면을 사용자 지정할 수 있습니다. 특히, 조직에서 볼 수 없거나 장치에서 수행할 수 없는 항목 목록을 사용자 지정할 수 있습니다.

<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>MacOS 장치에 소프트웨어 업데이트 배포 <!-- 3194876 -->
MacOS 장치 그룹에 소프트웨어 업데이트를 배포할 수 있습니다. 이 기능에는 중요, 펌웨어, 구성 파일 및 기타 업데이트가 포함 됩니다. 다음 장치 체크 인에 업데이트를 전송 하거나 사용자가 설정한 기간 내에 업데이트를 배포 하는 주별 일정을 선택할 수 있습니다. 이를 통해 표준 근무 시간 외에 장치를 업데이트 하거나 지원 센터를 완전히 팀으로 구성할 수 있습니다. 또한 업데이트가 배포 된 모든 macOS 장치에 대 한 자세한 보고서를 볼 수 있습니다. 장치별로 보고서를 드릴 하 여 특정 업데이트의 상태를 확인할 수 있습니다.

### <a name="send-custom-notifications-to-a-device----4928910----"></a>장치에 사용자 지정 알림 보내기 <!-- 4928910  -->
회사 포털 또는 Intune 앱이 설치 된 특정 장치에 사용자 지정 알림을 보낼 수 있습니다. 이렇게 하려면 **Intune** > **장치** > **모든 장치로 이동 하 여 장치** > **다른 사용자 지정 알림 보내기** > **선택 합니다**. 

### <a name="updates-to-android-enterprise-fully-managed-features----3464667-5227935-4062195-4631425-4631440---"></a>Android Enterprise 완전히 관리 되는 기능에 대 한 업데이트 <!-- 3464667, 5227935, 4062195, 4631425, 4631440 -->

Android 완전히 관리 되는 장치에 대해 다음과 같은 지원이 추가 될 예정입니다.

- 완전히 관리 되는 Android 용 SCEP 인증서는 장치 소유자로 관리 되는 장치의 인증서 인증에 사용할 수 있습니다. SCEP 인증서는 회사 프로필 장치에서 이미 지원 됩니다.  장치 소유자 용 SCEP 인증서를 사용 하 여 다음을 수행할 수 있습니다. <!-- 5227935 -->
    - Android Enterprise의 DO 섹션에서 SCEP 프로필 만들기
    - SCEP 인증서를 인증을 위해 Wi-fi 프로필에 연결
    - SCEP 인증서를 연결 하 여 인증을 위해 VPN 프로필 수행
    - SCEP 인증서를 연결 하 여 인증을 위한 전자 메일 프로필 수행 (AppConfig를 통해)
- Android 엔터프라이즈 장치에서 시스템 앱이 지원 됩니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택 하 여 Android Enterprise 시스템 앱을 추가 합니다. **앱 유형** 목록에서 **Android Enterprise system App**을 선택 합니다. Intune의 앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요. <!-- 4062195 -->
- **장치 준수** > **Android 엔터프라이즈** > **장치 소유자**에서 Google safetynet 증명 수준을 설정 하는 규정 준수 정책을 만들 수 있습니다.   <!-- 4631425 -->
- Android Enterprise 완전히 관리 되는 장치에서 모바일 위협 방어 공급자가 지원 됩니다. **장치 준수** > **Android 엔터프라이즈** > **장치 소유자**에서 허용 되는 위협 수준을 선택할 수 있습니다. <!-- 4631440 --> [Intune을 사용하여 디바이스를 규격 또는 비규격으로 표시하는 Android 엔터프라이즈 설정](compliance-policy-create-android-for-work.md#device-owner)은 현재 설정을 나열합니다.


적용 대상: 
- Android Enterprise 완전 관리형 디바이스

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

### <a name="updated-support-experience-------5012398------"></a>업데이트 된 지원 환경   <!--  5012398    -->
향상 된 기능을 제공 하는 과정에서 Intune에 대 한 콘솔 내 지원 환경을 업데이트 합니다.  콘솔 내 검색 및 일반적인 문제에 대 한 피드백을 개선 하 고, 워크플로를 간소화 하 여 지원 담당자에 게 문의 합니다.     

<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="tamper-protection-for-windows-defender-antivirus-----4705448---------"></a>Windows Defender 바이러스 백신의 변조 방지  <!-- 4705448       -->
Windows Defender 바이러스 백신에 대해 Intune에서 관리할 수 있는 설정에 *변조 방지* 를 추가 합니다. Windows 10 endpoint protection 용 장치 구성 프로필을 사용 하 여 변조 방지를 설정 하거나 해제할 수 있습니다.  변조 방지에 대 한 자세한 내용은 Windows 설명서에서 [변조 방지를 사용 하 여 보안 설정 변경 방지](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection) 를 참조 하세요. 


<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.




