---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 04b284a62076122cec70b6b455151a0377470521
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74540732"
---
# <a name="in-development-for-microsoft-intune---december-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 12월

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

### <a name="ios-user-licensed-vpp-apps---5619268-idready---"></a>iOS 사용자에 게 사용이 허가 된 VPP 앱<!-- 5619268 idready -->
사용자 등록 iOS 장치의 경우 최종 사용자에 게 사용 가능으로 배포 된 장치 라이선스 VPP 응용 프로그램이 더 이상 제공 되지 않습니다. 그러나 최종 사용자는 회사 포털 내에서 사용자가 사용이 허가 된 모든 VPP 앱을 계속 볼 수 있습니다. VPP 앱에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Apple Volume Purchase Program을 통해 구매한 iOS 및 macOS 앱을 관리하는 방법](~/apps/vpp-apps-ios.md)을 참조하세요.

### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745-idready---"></a>메모리 암호화 된 macOS 장치에서 개인 복구 키 검색<!-- 4851745 idready -->
최종 사용자는 iOS 회사 포털 앱을 사용 하 여 개인 복구 키 (대해 filevault 켭니다 키)를 검색할 수 있습니다. 개인 복구 키를 포함 하는 장치를 Intune에 등록 하 고 Intune을 통해 대해 filevault 켭니다를 사용 하 여 암호화 해야 합니다. 최종 사용자는 iOS 회사 포털 앱을 사용 하 여 Safari 웹 보기를 열고 개인 복구 키를 검색할 수 있습니다. Intune에서 *암호화 되 고 등록 된 macOS 장치를* > **장치** 를 선택 하 > **복구 키를 가져옵니다**. 대해 filevault 켭니다에 대 한 자세한 내용은 [macOS에 대 한 대해 filevault 켭니다 암호화](~/protect/encrypt-devices.md#filevault-encryption-for-macos)를 참조 하세요.

### <a name="microsoft-app-icons-update--4677605--"></a>Microsoft 앱 아이콘 업데이트<!--4677605-->
앱 보호 정책 및 앱 구성 정책에 대 한 앱 대상 지정 창의 Microsoft 앱에 사용 되는 아이콘이 업데이트 됩니다.

### <a name="smime-support-for-microsoft-outlook-mobile---2669398----"></a>Microsoft Outlook Mobile에 대 한 S/MIME 지원<!-- 2669398  -->
Intune은 iOS 및 Android의 Outlook Mobile에서 사용할 수 있는 S/MIME 서명 및 암호화 인증서 제공을 지원 합니다. 관련 정보는 [iOS 장치에 대 한 메일 설정](~/configuration/email-settings-ios.md) 및 [Android 장치에 대 한 전자 메일 설정](~/configuration/email-settings-android.md)을 참조 하세요.

### <a name="custom-settings-support-for-macos-applications---4736278----"></a>MacOS 응용 프로그램에 대 한 사용자 지정 설정 지원<!-- 4736278  -->
Intune은 사용자 지정 설정을 지원 하므로 기존 기본 설정 속성 목록 (. info.plist) 파일에 특정 키 및 값을 추가 하 여 macOS 앱 및 장치를 구성할 수 있습니다. 일부 앱은 관리 되는 기본 설정을 지원 하지 않으며 일부 경우에는 특정 설정만 관리할 수 있습니다. 설정은 장치 채널을 통해서만 배포 됩니다. 장치 채널 설정을 대상으로 하는 속성 목록 파일 또는 .xml 파일만 업로드 해야 합니다.

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Windows에서 회사 포털 앱에 대 한 알림 표시<!-- 1808082  -->
응용 프로그램이 닫힌 경우에도 사용자에 게 알림 메시지를 표시 하도록 Windows 장치의 회사 포털 앱을 업데이트 합니다. 업데이트는 설치 상태를 완료 하거나 실패 한 경우에만 사용 가능한 앱에 대 한 알림을 표시 합니다. 회사 포털 앱은 필요한 응용 프로그램에 대 한 알림을 표시 하지 않습니다.

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>회사 포털 앱에 대 한 설치 상태 메시지 표시<!-- 2514416  -->
회사 포털 앱은 최종 사용자에 게 추가 앱 설치 상태 메시지를 표시 합니다. 새 Win32 종속성 기능에는 다음과 같은 조건이 적용 됩니다.
- 앱을 설치하지 못했습니다. 관리자가 정의한 종속성이 충족 되지 않았습니다.

### <a name="configure-app-notification-content-for-organization-accounts---2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성<!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 모든 앱 사용 응용 프로그램에는이 기능을 사용할 수 없습니다. 앱에 대한 자세한 내용은 [앱 보호 정책이란?](../apps/app-protection-policy.md)을 참조하세요.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998-idready---"></a>사용자가 Android Enterprise 장치 소유자 장치에서 관리 되는 키 저장소 인증서 자격 증명을 구성 하지 못하도록 차단<!-- 3311998 idready -->
Android 엔터프라이즈 장치 소유자 장치에는 사용자가 관리 되는 키 저장소 (**장치 구성** > **프로필** > **만들기 프로필** > **Android Enterprise** for Platform > 장치 소유자는 프로필 유형 > **사용자 + 계정**에 대 한 **장치 제한 > 전용** )에서 인증서 자격 증명을 구성 하는 것을 차단 하는 새로운 설정이 있습니다.

현재 설정 목록을 보려면 Intune에서 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상:
- 전용 및 완전히 관리 되는 장치를 포함 하는 Android Enterprise 장치 소유자

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686-idready---"></a>MacOS 장치에 대 한 유선 네트워크 장치 구성 프로필<!-- 3508686 idready -->
MacOS **장치** 에서 향후 업데이트에는 **유선 네트워크 (** **장치 구성** **> >  >  > 프로필** 을 구성 하 **는 새 장치** 구성 프로필이 포함 됩니다. 이 기능을 사용 하 여 유선 네트워크를 관리 하 고 이러한 유선 네트워크를 macOS 장치에 배포 하는 802.1 x 프로필을 만듭니다.

적용 대상:
- macOS

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Android Enterprise 회사 프로필에 대 한 Wi-fi 프로필에 자동 프록시 설정 추가<!-- 4490822 idready -->
Android Enterprise Work Profile 장치에서 Wi-fi 프로필을 만들 수 있습니다. Wi-fi 엔터프라이즈 유형을 선택 하는 경우 Wi-fi 네트워크에서 사용 되는 EAP (확장할 수 있는 인증 프로토콜) 유형을 입력할 수도 있습니다.

이후 업데이트에서 엔터프라이즈 유형을 선택 하면 `proxy.contoso.com`와 같은 프록시 서버 URL을 포함 하는 자동 프록시 설정을 입력할 수 있습니다.

구성할 수 있는 현재 Wi-fi 설정을 보려면 [Microsoft Intune에서 Android Enterprise 및 android 키오스크를 실행 하는 장치에 대 한 wi-fi 설정 추가](../configuration/wi-fi-settings-android-enterprise.md)로 이동 합니다.

적용 대상:
- Android Enterprise 회사 프로필

### <a name="enable-network-access-control-nac-with-cisco-anyconnect-vpn-on-ios-devices---4860111-idready---"></a>IOS 장치에서 Cisco AnyConnect VPN을 사용 하 여 NAC (네트워크 액세스 제어) 사용<!-- 4860111 idready -->
IOS 장치에서 VPN 프로필을 만들고 Cisco AnyConnect를 비롯 한 다양 한 연결 유형 (**장치 구성** > **프로필** > > > **생성** 하는 프로필 유형 > **cisco anyconnect** **에 대** 한 프로 파일 유형 cisco **anyconnect)** 을 사용할 수 있습니다. 

이후 업데이트에서는 Cisco AnyConnect에서 NAC (네트워크 액세스 제어)를 사용 하도록 설정할 수 있습니다. 이 기능을 사용하려면

1. [Cisco Id 서비스 엔진 관리자 가이드](https://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)에서 **MDM 서버로 Microsoft Intune 구성** 의 단계를 사용 하 여 Azure에서 Cisco ISE (id 서비스 엔진)를 구성 합니다.
2. Intune 장치 구성 프로필에서 **네트워크 Access Control (NAC)** 설정을 선택 합니다.

사용 가능한 모든 VPN 설정을 보려면 [iOS 장치에서 vpn 설정 구성](../configuration/vpn-settings-ios.md)으로 이동 합니다.

적용 대상:
- iOS

### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578-idready---"></a>IOS, iPadOS 및 macOS 장치의 앱 및 웹 사이트에 대 한 업데이트 된 Single Sign-On 환경<!-- 4999578 idready -->
Intune은 iOS, iPadOS 및 macOS 장치에 대 한 Single Sign-On 설정을 추가 합니다. 현재 Intune에서 자격 증명 SSO 앱 확장 및 Apple의 기본 제공 Kerberos 확장을 구성할 수 있습니다. 이후 업데이트에서는 조직이 나 id 공급자에 의해 작성 된 리디렉션 SSO 앱 확장을 구성할 수 있습니다. 

이러한 설정을 사용 하 여 OAuth 및 SAML2와 같은 최신 인증 방법을 사용 하는 앱 및 웹 사이트에 대 한 원활한 Single Sign-On 환경을 구성할 수 있습니다. 

구성할 수 있는 SSO 앱 확장 설정을 보려면 [iOS의 sso](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) 및 [Macos의 sso](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)로 이동 합니다.

적용 대상:
- iOS/iPadOS
- macOS

### <a name="require-use-of-approved-keyboards-on-android--4761794-idready---"></a>Android에서 승인 된 키보드 사용 필요<!--4761794 IDready -->
관리 되는 Android 앱에서 사용할 승인 된 키보드 목록을 지정할 수 있습니다. 관리 되는 앱에서 사용자에 게 장치에 이미 설치 된 승인 된 키보드 중 하나로 전환 하 라는 메시지가 표시 되거나, 필요한 경우 승인 된 키보드 중 하나를 다운로드 하 고 설정 하는 Google Play 스토어으로 이동 됩니다. 활성 키보드가 승인 된 키보드 중 하나인 경우에만 사용자가 관리 되는 앱의 텍스트 필드를 편집할 수 있습니다.

### <a name="use-pkcs-certificates-with-wi-fi-profiles-on-windows-10-and-later-devices---3246388----"></a>Windows 10 이상 장치에서 Wi-fi 프로필에 PKCS 인증서 사용<!-- 3246388  -->
현재는 SCEP 인증서 (**장치 구성** > **프로필** )를 사용 하 여 windows wi-fi 프로필을 인증 하 고, **플랫폼 >에 대 한** **프로필** > **windows 10 이상** > 프로 파일 유형 > **엔터프라이즈** > **EAP 유형**)에 인증할 수 있습니다. Windows Wi-fi 프로필에 PKCS 인증서를 사용할 수 있습니다. 이 기능을 사용 하면 사용자가 테 넌 트에서 새로운 또는 기존 PKCS 인증서 프로필을 사용 하 여 Wi-fi 프로필을 인증할 수 있습니다. 

Wi-fi 프로필에 대 한 자세한 내용은 [Intune에서 Windows 10 이상 장치에 대 한 wi-fi 설정 추가](../configuration/wi-fi-settings-windows.md)를 참조 하세요.

적용 대상:
- Windows 10 이상

### <a name="new-exchangeactivesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824----"></a>iOS 디바이스에서 메일 디바이스 구성 프로필을 만들 경우 새로운 ExchangeActiveSync 설정<!-- 4892824  --> 
iOS/iPadOS 디바이스의 디바이스 구성 프로필에서 메일 연결을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해  > **iOS/iPadOS** 선택 > 프로필 유형에 대해 **메일** 선택). 

다음을 비롯 한 새로운 ExchangeActiveSync 설정이 제공 됩니다.
- 전자 메일, 일정 및 연락처와 같은 동기화 할 서비스 (또는 동기화 차단)를 선택 합니다.
- 사용자가 디바이스에서 이러한 서비스에 대한 동기화 설정을 변경할 수 있도록 허용(또는 차단)합니다. 

현재 설정을 보려면 [Intune에서 iOS 장치에 대 한 메일 프로필 설정](../configuration/email-settings-ios.md)으로 이동 합니다.

적용 대상:
- iOS 13.0 이상
- iPadOS 13.0 이상

### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-device-owner-and-dedicated-devices---5353228----"></a>사용자가 Android Enterprise 디바이스 소유자 및 전용 디바이스에 개인 Google 계정을 추가하지 못하도록 차단<!-- 5353228  -->
사용자가 Android Enterprise 디바이스 소유자 및 전용 디바이스에 개인 Google 계정을 추가하지 못하도록 차단할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대한 **Android Enterprise** > **디바이스 소유자만 > 프로필 유형에 대한 디바이스 제한** > **사용자 및 계정 설정**).

구성할 수 있는 현재 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상:
- Android Enterprise 디바이스 소유자
- Android 엔터프라이즈 전용 디바이스

### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-ios-device-restrictions-profile---5468501----"></a>Siri 명령의 서버 쪽 로깅 설정이 iOS 디바이스 제한 프로필에서 제거됨<!-- 5468501  -->
IOS 장치에서 Siri 명령에 대 한 서버 쪽 로깅을 구성 하는 장치 제한 프로필을 만들 수 있습니다 **(장치 구성** ** > 프로필 > 프로필 유형** > **기본 제공 앱**에 대 한 플랫폼 > **장치 제한** 에 대 한 **iOS/iPadOS** **프로필 > 만듭니다** ). **Siri commands 설정에 대 한 서버 쪽 로깅이** 제거 됩니다.

이 설정은 Intune 관리 콘솔에서 제거 됩니다. 이 설정이 구성 된 기존 정책에서 설정을 계속 표시 하더라도이 설정은 장치에 영향을 주지 않습니다. 기존 정책에서 설정을 제거 하려면 정책으로 이동 하 고, 사소한 편집을 수행 하 고, 저장 하 고, 정책이 업데이트 됩니다.

구성할 수 있는 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 및 iPadOS 디바이스 설정](../configuration/device-restrictions-ios.md)을 참조하세요.

적용 대상:
- iOS

<!-- ***********************************************-->
<!--## Device enrollment-->

<!-- ***********************************************-->
<!--## Device management-->


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>모니터링 및 문제 해결

### <a name="centralized-audit-logs--5603185-5697164--"></a>중앙 집중식 감사 로그<!--5603185, 5697164-->
새 중앙 집중식 감사 로그 환경에서는 모든 범주에 대 한 감사 로그를 한 페이지에 수집 합니다. 여기서는 로그를 필터링 하 여 원하는 데이터를 가져올 수 있습니다. 감사 로그를 보려면 **테 넌 트 관리** > **감사 로그**로 이동 합니다. 자세한 내용은 [Intune에서 감사 로그의 예정 된 변경 내용](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Upcoming-change-to-Audit-logs-in-Intune/ba-p/1015858)을 참조 하세요.

<!-- ***********************************************-->
<!--## Role-based access control-->


<!-- ***********************************************-->

## <a name="security"></a>보안

### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529-idready---"></a>PKCS 인증서 프로필을 사용 하 여 인증서로 장치 프로 비전<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529 IDready -->
PKCS 인증서 프로필을 사용 하 여 장치에 대 한 인증서를 발급 하 고 현재 사용자 기반 인증서 지원을 통해 확장할 수 있습니다. 장치 기반 인증서는 Android, iOS 및 Windows 플랫폼에서 지원 되며 Wi-fi 및 VPN 프로필에 사용할 수 있습니다.

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


