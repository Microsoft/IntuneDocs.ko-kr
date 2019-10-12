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
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e7c4e5ed45455dda941fb0c61c989c12c57135d
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999316"
---
# <a name="in-development-for-microsoft-intune---october-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 10월

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

### <a name="additional-app-configuration-variable-available----4969237----"></a>사용 가능한 추가 앱 구성 변수 <!-- 4969237  -->
앱 구성 정책을 만들 때 구성 설정의 일부로 `AAD Device ID` 구성 변수를 포함할 수 있습니다. Intune에서 **클라이언트 앱** > **앱 구성 정책** > **추가**를 선택합니다. 구성 정책 세부 정보를 입력 하 고 구성 **설정** 을 선택 하 여 **구성 설정** 블레이드를 확인 합니다.

### <a name="dark-mode-for-ios-company-portal----4911422----"></a>IOS 회사 포털의 어둡게 모드 <!-- 4911422  -->
진한 모드는 iOS 회사 포털에 대해 계획 됩니다. 회사 앱을 다운로드 하 고, 장치를 관리 하 고, 선택한 색 구성표에서 IT 지원을 받으세요. iOS 회사 포털에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md)을 참조하세요.

### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-devices----4760025----"></a>Android Enterprise 장치에서 알 수 없는 소스의 앱 설치 방지 <!-- 4760025  -->
Android Enterprise work profile 장치의 경우 최종 사용자가 알 수 없는 소스에서 회사 프로필로 앱을 설치할 수 없습니다. 필요에 따라 개인 프로필로 이러한 제한을 확장할 수 있습니다. 이 제한을 사용 하도록 설정 하는 경우 Android Enterprise work profile 장치에 대 한 최종 사용자도 앱을 알 수 없는 소스에서 장치의 개인 측으로 테스트용으로 로드할 수 없습니다. 

### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui----4102027-4102029----"></a>앱 보호 UI 및 iOS 앱 프로 비전 UI로 업데이트 <!-- 4102027, 4102029  -->
Intune에서 앱 보호 정책 및 iOS 앱 프로 비전 프로필을 만들고 편집 하는 UI가 업데이트 됩니다. UI 변경 사항에는 다음이 포함됩니다.
- 하나의 블레이드 내에 압축 된 마법사 스타일 형식을 사용 하 여 간소화 된 환경을 제공 합니다. 
- 할당을 포함 하는 만들기 흐름에 대 한 업데이트입니다.
- 새 정책을 만들거나 속성을 편집 하기 전에 속성을 볼 때 설정 되는 모든 항목의 요약 된 페이지입니다. 또한 속성을 편집할 때 요약에는 편집 중인 속성 범주의 항목 목록만 표시 됩니다.

### <a name="create-groups-of-management-objects-called-policy-sets----3762880----"></a>정책 집합 이라는 관리 개체 그룹 만들기 <!-- 3762880  -->
정책 집합을 사용 하면 단일 개념적 단위로 식별, 대상 지정 및 모니터링 해야 하는 기존 관리 엔터티에 대 한 참조 번들을 만들 수 있습니다. 정책 집합은 기존 개념 또는 개체를 대체 하지 않습니다. 관리자는 현재와 같이 개별 개체를 계속 할당할 수 있습니다. 개별 개체는 정책 집합에서 참조 됩니다. 따라서 해당 개별 개체에 대 한 모든 변경 내용이 정책 집합에 반영 됩니다.  Intune에서 **정책 집합** > **만들기** 를 선택 하 여 새 정책 집합을 만듭니다. 

### <a name="win32-apps-on-windows-10-s-mode-devices----3747604----"></a>Windows 10 S 모드 장치의 Win32 앱 <!-- 3747604  --> 
Windows 10 S 모드에서 관리 되는 장치에서 Win32 앱을 설치 하 고 실행할 수 있습니다. Windows Defender 응용 프로그램 제어 (WDAC) PowerShell 도구를 사용 하 여 S 모드에 대 한 하나 이상의 보조 정책을 만들 수 있습니다. Device Guard 서명 포털을 사용 하 여 보완 정책에 서명한 다음, Intune을 통해 정책을 업로드 하 고 배포 합니다. Intune에서는 **클라이언트 앱** > **Windows 10 S 보충 정책**을 선택 하 여이 기능을 찾을 수 있습니다. 

### <a name="set-app-availability-based-on-a-date-and-time----3510685----"></a>날짜 및 시간을 기준으로 앱 가용성 설정 <!-- 3510685  -->
관리자는 필수 앱에 대 한 시작 시간 및 최종 기한 시간을 구성할 수 있습니다. 시작 시 Intune 관리 확장은 앱 콘텐츠를 다운로드 하 여 캐시 합니다. 앱이 최종 기한 시간에 설치 됩니다. 사용 가능한 앱의 경우 시작 시간은 앱이 회사 포털 표시 되는 시기를 나타냅니다. Intune에서 **클라이언트 앱** > **앱**을 차례로 선택합니다. 그런 다음 목록에서 특정 앱을 선택 하거나 **추가** 를 선택 하 여 새 앱을 추가 합니다. 앱 블레이드에서 **할당** > **그룹 추가**를 선택 합니다. **할당 유형을** **필수** 로 설정 하 고 **포함 된 그룹**을 선택 합니다. **이 앱을 모든 사용자에 게 필요** 하도록 설정을 **예** 로 설정 하 고 **편집** 을 선택 하 여 **최종 사용자 환경** 옵션을 수정 합니다. **최종 사용자 환경** 블레이드에서 필요한 경우 **소프트웨어를 사용할 수 있는 시간** 을 설정 합니다. 앱을 추가하는 방법에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](../apps/apps-add.md)를 참조하세요.

### <a name="require-win32-apps-to-restart----3136567----"></a>Win32 앱을 다시 시작 해야 함 <!-- 3136567  -->
성공적으로 설치한 후에는 Win32 앱을 다시 시작 해야 할 수 있습니다. 또한 다시 시작이 발생 하기 전 까지의 시간 (유예 기간)을 선택할 수 있습니다.

### <a name="company-portal-app-on-windows----1808082----"></a>Windows의 회사 포털 앱 <!-- 1808082  -->
응용 프로그램이 닫힌 경우에도 사용자에 게 알림 메시지를 표시 하도록 Windows 장치의 회사 포털 앱이 업데이트 됩니다. 설치 상태를 완료 하거나 실패 한 경우 업데이트가 사용 가능한 앱에 대 한 알림만 표시 됩니다. 회사 포털 앱은 필요한 응용 프로그램에 대 한 알림을 표시 하지 않습니다.

### <a name="company-portal-app-installation-status-messages----2514416----"></a>앱 설치 상태 메시지 회사 포털 <!-- 2514416  -->
회사 포털 앱은 최종 사용자에 게 추가 앱 설치 상태 메시지를 표시 합니다. 새 Win32 종속성 기능에는 다음과 같은 조건이 적용 됩니다.
- 앱을 설치하지 못했습니다. 관리자가 정의한 종속성이 충족 되지 않았습니다.
- 앱이 성공적으로 설치 되었지만 다시 시작 해야 합니다.
- 앱을 설치 하는 중입니다. 계속 하려면 다시 시작 해야 합니다.

#### <a name="assign-microsoft-edge-beta-for-macos----4678761----"></a>MacOS에 대 한 Microsoft Edge beta 할당 <!-- 4678761  -->
MacOS 장치용 Intune에 최신 버전의 Microsoft Edge beta를 추가 하 고 할당할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **앱 추가** > **Microsoft Edge - macOS**를 선택합니다. 그런 다음 원하는 그룹에 Microsoft Edge beta를 할당 합니다. MAU (microsoft 자동 업데이트)는 Microsoft Edge를 최신 상태로 유지 합니다. Microsoft Edge에 대 한 자세한 내용은 [Microsoft Intune를 사용 하 여 Microsoft edge를 사용 하 여 웹 액세스 관리](../apps/manage-microsoft-edge.md)를 참조 하세요.

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱 보호 정책 (앱)을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 응용 프로그램을 사용 하도록 설정 된 응용 프로그램에는이 기능을 APP에 대한 자세한 내용은 [앱 보호 정책이란?](../apps/app-protection-policy.md)을 참조하세요.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고 <!-- 3041956  -->
Android 작업 프로필 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태 및 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](../apps/app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](../enrollment/android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](../apps/apps-add-android-for-work.md#managed-google-play-app-types)을 참조하세요.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성


### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices----5199328----"></a>감독 된 iOS 및 iPadOS 장치에 대 한 새 장치 구성 설정 <!-- 5199328  -->
IOS 및 iPadOS 장치에서 장치에 대 한 기능 및 설정을 제한 하는 프로필을 만들 수 있습니다 (**장치 구성** > **프로필** > **프로필 만들기** > **iOS/iPadOS** for platform > **장치** 프로필 형식에 대 한 제한 사항). 다음을 제어할 수 있는 새로운 설정이 있습니다. 
- 파일의 네트워크 드라이브 앱에 대 한 액세스  
- 파일 앱에서 USB 드라이브 액세스 
- Wi-fi 항상 설정 

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md)으로 이동하세요.

적용 대상:
- iOS 13.0 이상
- iPadOS 13.0 이상

### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-and-android-enterprise----5021055----"></a>Android 및 Android Enterprise의 Wi-fi 프로필에서 자동으로 연결 설정이 제거 됨 <!-- 5021055  -->
Android 및 Android Enterprise 장치에서 Wi-fi 프로필을 만들어 다양 한 설정을 구성할 수 있습니다 (**장치 구성** > **프로필** > **프로필 만들기** > **android** 또는 **android enterprise).** 플랫폼 > 프로필 유형 **으로 wi-fi** ). [Android에서 지원 하지 않으므로](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29) **자동으로 연결** 설정이 제거 됩니다. 

Wi-fi 프로필에서이 설정을 사용 하는 경우 **연결이 자동으로** 작동 하지 않는 것을 알 수 있습니다. 어떤 조치도 취할 필요가 없지만이 설정은 Intune 사용자 인터페이스에서 제거 됩니다.

현재 설정을 보려면 [Android wi-fi 설정](../configuration/wi-fi-settings-android.md) 또는 [android Enterprise wi-fi 설정](../configuration/wi-fi-settings-android-enterprise.md)으로 이동 합니다.

적용 대상:
- Android
- Android Enterprise

### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices----4816339----"></a>Android Enterprise 장치 소유자 장치에서 글로벌 HTTP 프록시 만들기 <!-- 4816339  -->
Android 엔터프라이즈 장치에서 조직의 웹 검색 표준에 맞게 전역 HTTP 프록시를 구성할 수 있습니다 (**장치 구성** > **프로필** > **프로필 만들기** > **Android Enterprise** 플랫폼 > 장치 소유자는 프로필 유형 > **연결**)에 대 한 **장치 제한을 >** 합니다. 구성 된 후에는 모든 HTTP 트래픽이이 프록시를 사용 합니다.

적용 대상:
- Android Enterprise 디바이스 소유자

### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices----2266073----"></a>Windows 10 이상 장치용 새 장치 펌웨어 구성 인터페이스 프로필 <!-- 2266073  -->
Windows 10 이상에서 장치 구성 프로필을 만들어 설정 및 기능을 제어할 수 있습니다 (**장치 구성** > **프로필** > **프로필** > **Windows 10 이상** 플랫폼). Intune이 UEFI (BIOS) 설정을 관리할 수 있도록 하는 새 장치 펌웨어 구성 인터페이스 프로필 유형이 있습니다.

구성할 수 있는 모든 현재 설정에 대 한 개요를 보려면 [Microsoft Intune에서 장치 프로필을 사용 하 여 장치에 기능 및 설정 적용](../configuration/device-profiles.md)을 참조 하세요.

적용 대상:
- 선택 장치에서 Windows 10 RS5 (1809) 이상

### <a name="pkcs-certificates-for-macos-----1333650------------------"></a>MacOS에 대 한 PKCS 인증서  <!-- 1333650                -->
MacOS를 실행 하는 장치에서 PKCS 인증서에 대 한 완전 한 지원을 추가할 예정입니다. 사용자는 사용자 지정 주체 및 주체 대체 이름 필드를 사용 하 여 사용자 및 장치 인증서를 배포할 수 있습니다. 모든 앱에 액세스할 수 있도록 허용 하는 새 설정도 있습니다 .이를 통해 모든 연결 된 앱에 개인 키에 대 한 액세스를 제공 합니다. 이 설정에 대 한 자세한 내용은 다음 Apple 설명서를 참조 하세요. https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf.

###   <a name="derived-credentials-to-provision-mobile-devices-with-certificates----------1736036-1736037-1772050--------"></a>인증서를 사용 하 여 모바일 장치를 프로 비전 하기 위한 파생 자격 증명      <!--  1736036, 1736037, 1772050      --> 
장치에 인증서를 배포 하기 위한 *NIST (표준 및 기술) 800-157* 표준을 지 원하는 파생 된 자격 증명에 대 한 지원이 추가 될 예정입니다.  파생 자격 증명은 스마트 카드와 같은 PIV (개인 Id 확인) 또는 CAC (Common Access Card) 카드의 사용을 기반으로 합니다. 사용자는 컴퓨터의 스마트 카드를 사용 하 여 인증 한 다음 파생 된 자격 증명 공급자에 필요한 프로세스에 따라 관리 되는 장치에 대 한 인증서 요청을 제출 합니다.   

파생 자격 증명을 사용 하 여 인증서를 가져오는 프로세스는 SCEP 또는 PKCS 인증서 프로필을 사용 하는 것과 다르며, 최종 결과는 앱 인증, VPN, Wi-fi 또는 전자 메일에 사용할 수 있는 인증에 대 한 인증서가 있는 모바일 장치와 동일 합니다. 파일링.   

자세한 내용은 www.nccoe.nist.gov에서 [파생 된 PIV 자격 증명](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials) 을 참조 하세요.

파생 자격 증명의 초기 릴리스는 iOS에서 Entrust Datacard, 중재 및 DISA Purebred를 지원 합니다. 추가 플랫폼과 파생 된 자격 증명 공급자는 이후 릴리스에서 지원 될 예정입니다.   

<!-- ***********************************************-->
## <a name="device-enrollment"></a>디바이스 등록

### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment----4350697---"></a>회사 프로필 또는 장치 관리자 등록에 등록 하는 Android 장치 운영 체제 버전 지정 <!-- 4350697 -->
Intune 장치 유형 제한을 사용 하면 장치의 OS 버전을 사용 하 여 Android Enterprise work 프로필 등록 또는 Android 장치 관리자 등록을 사용할 사용자 장치를 지정할 수 있습니다. 이렇게 하려면 **Intune** > **장치 등록** > **등록 제한** > **만들기 제한** > **장치 유형 제한** > **플랫폼 설정**으로 이동 합니다.

### <a name="edit-device-name-value-for-autopilot-devices----4816775---"></a>Autopilot 장치에 대 한 장치 이름 값 편집 <!-- 4816775 -->
Azure AD 가입 Autopilot 장치에 대 한 장치 이름 값을 편집할 수 있습니다. 이렇게 하려면 **Intune** > **장치 등록** > **Windows 등록** > **windows Autopilot** > **장치** > 장치를 선택 하 고 오른쪽 창에서 장치 이름 값을 변경 > 저장 > **합니다**.

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS 디바이스에서 회사 포털의 등록 프로세스 개인 정보 화면을 사용자 지정합니다 <!-- 4394993  -->
Markdown을 이용하면 iOS 등록 과정에서 최종 사용자에게 표시되는 회사 포털의 개인 정보 화면을 사용자 지정할 수 있습니다. 특히 조직이 디바이스에서 볼 수 없거나 해선 안 되는 항목 목록을 사용자 지정할 수 있습니다.

<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리


### <a name="edit-group-tag-value-for-autopilot-devices---4816775---"></a>Autopilot 장치에 대 한 그룹 태그 값 편집<!-- 4816775 -->
Autopilot 장치에 대 한 그룹 태그 값을 편집할 수 있습니다. 이렇게 하려면 **Intune** > **장치 등록** > **Windows 등록** > **windows Autopilot** > **장치** > 장치를 선택 하 > 오른쪽 창의 그룹 태그 값을 **변경 > 합니다.** .

### <a name="ui-update-for-creating-and-editing-windows-10-update-rings-----4099089------------"></a>Windows 10 업데이트 링을 만들고 편집 하기 위한 UI 업데이트  <!-- 4099089          -->   
Intune 용 Windows 10 업데이트 링에 대 한 업데이트 된 만들기 및 편집 UI 환경을 배포 합니다.  UI 변경에는 다음이 포함 됩니다.  
- 하나의 블레이드 내에서 압축 된 마법사 스타일 형식을 사용 하 여 기존 환경을 단순화 합니다. 이 UI 업데이트는 IT 전문가가 심층 블레이드 경험을 드릴 다운할 수 있도록 하는 블레이드 확산을 포함 합니다.   
- 할당을 포함 하도록 만들기 흐름을 수정 합니다.  
- 속성을 볼 때, 새 업데이트 링을 만들기 전에, 속성을 편집할 때 설정 된 모든 항목의 요약 페이지를 추가 합니다. 편집할 때는 현재 편집 중인 속성 범주 내에 설정된 항목 목록의 요약만 표시됩니다.

### <a name="ui-update-for-creating-and-editing-ios-software-updates-----4099090----------"></a>IOS 소프트웨어 업데이트를 만들고 편집 하기 위한 UI 업데이트  <!-- 4099090        -->   
Intune에 대 한 iOS 소프트웨어 업데이트에 대 한 업데이트 된 만들기 및 편집 UI 환경을 배포 합니다. UI 변경에는 다음이 포함 됩니다.
- 하나의 블레이드 내에서 압축 된 마법사 스타일 형식을 사용 하 여 기존 환경을 단순화 합니다. 이 UI 업데이트는 IT 전문가가 심층 블레이드 경험을 드릴 다운할 수 있도록 하는 블레이드 확산을 포함 합니다.  
- IOS 소프트웨어 업데이트 정책 만들기 흐름이 할당을 포함 하도록 업데이트 됩니다. 
- IOS 소프트웨어 업데이트 정책에는 속성을 볼 때 새 정책을 만들기 전과 속성을 편집할 때 설정 된 모든 항목의 요약 페이지가 포함 됩니다. 편집할 때는 현재 편집 중인 속성 범주 내에 설정된 항목 목록의 요약만 표시됩니다.

### <a name="target-macos-user-groups-to-require-jamf-management----4061739---"></a>Jamf 관리를 필요로 하는 macOS 사용자 그룹을 대상으로 합니다. <!-- 4061739 -->
특정 사용자 그룹을 대상으로 지정 하 여 Jamf에서 macOS 장치를 관리 하도록 요구할 수 있습니다. 이 대상 지정을 통해 macOS 장치 하위 집합에 Jamf 준수 통합을 적용할 수 있으며, 다른 장치는 Intune에서 계속 관리 됩니다. 또한 한 MDM에서 다른 MDM으로 사용자 장치를 점진적으로 마이그레이션할 수 있습니다.

### <a name="new-restrictions-for-renaming-windows-devices----3478938---"></a>Windows 장치 이름 바꾸기에 대 한 새로운 제한 사항 <!-- 3478938 -->
장치 이름은 다음 규칙을 따라야 합니다.
- 15 자이 하 여야 합니다 (후행 NULL을 포함 하지 않고 63 바이트 보다 작거나 같아야 함).
- Null 또는 빈 문자열 아님
- 허용 되는 ASCII: 문자 (a-z, a-z), 숫자 (0-9) 및 하이픈
- 허용 되는 유니코드: 문자 > = 0x80, 유효한 UTF8 이어야 합니다. IDN 매핑 가능 해야 합니다 (RtlIdnToNameprepUnicode 성공, RFC 3492 참조).
- 이름은 숫자만 포함 하거나 숫자로 시작할 수 없습니다.
- 이름에 공백이 없습니다.
- 허용 되지 않는 문자: {|} ~ [\] ^ ':; < = >? & @ ! " # $ % ` ( ) + / , . _ *)

### <a name="deploy-software-updates-to-macos-devices----3194876---"></a>MacOS 장치에 소프트웨어 업데이트 배포 <!-- 3194876 -->
MacOS 장치 그룹에 소프트웨어 업데이트를 배포할 수 있습니다. 이 기능에는 중요, 펌웨어, 구성 파일 및 기타 업데이트가 포함 됩니다. 다음 장치 체크 인에 업데이트를 전송 하거나 사용자가 설정한 기간 내에 업데이트를 배포 하는 주별 일정을 선택할 수 있습니다. 이 기능을 사용 하면 표준 근무 시간 외에 장치를 업데이트 하거나 지원 센터를 완전히 팀으로 구성할 때 도움이 됩니다. 또한 업데이트가 배포 된 모든 macOS 장치에 대 한 자세한 보고서를 볼 수 있습니다. 장치별로 보고서를 드릴 하 여 특정 업데이트의 상태를 확인할 수 있습니다.

<!-- ***********************************************-->
## <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

### <a name="new-android-report-on-devices-overview-page----2984353----"></a>장치에 대 한 새 Android 보고서 개요 페이지 <!-- 2984353  -->
각 장치 관리 솔루션에 등록 된 Android 장치 수를 표시 하는 새 보고서를 장치 개요 페이지에 추가할 예정입니다. 이 차트에는 회사 프로필, 완전히 관리, 전용 및 장치 관리자 등록 장치 수가 표시 됩니다. 보고서를 보려면 **Intune** > **장치** > **개요**를 선택 합니다.

### <a name="windows-autopilot-deployment-reports----3856172----"></a>Windows AutoPilot 배포 보고서 <!-- 3856172  -->
새 보고서는 Windows Autopilot를 통해 배포 된 각 장치에 대해 자세히 설명 합니다. 이 데이터는 배포 후 30 일 동안 사용할 수 있습니다. 보고서를 보려면 **Intune** > **장치 등록** > **Monitor** > **Autopilot 배포**로 이동 합니다.

### <a name="updated-support-experience-------5012398------"></a>업데이트 된 지원 환경   <!--  5012398    -->
향상 된 기능을 제공 하는 과정에서 Intune에 대 한 콘솔 내 지원 환경을 업데이트 합니다.  콘솔 내 검색 및 일반적인 문제에 대 한 피드백을 개선 하 고, 워크플로를 간소화 하 여 지원 담당자에 게 문의 합니다.     

<!-- ***********************************************-->
<!--## Security-->


<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.




