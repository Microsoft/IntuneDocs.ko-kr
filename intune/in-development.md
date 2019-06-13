---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc5ea7076e77e5071724168fab58fa78f59601c4
ms.sourcegitcommit: 7ceae61e036ccf8b33704751b0b39fee81944072
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744296"
---
# <a name="in-development-for-microsoft-intune---june-2019"></a>개발 중인 Microsoft Intune 기능 - 2019년 6월

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
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune

<!-- ***********************************************-->
### <a name="app-management"></a>앱 관리

#### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>다바이스 사용자는 설치했거나 설치하려고 시도한 모든 관리형 앱을 볼 수 있습니다. <!-- 2352913 -->
Windows용 회사 포털은 사용자의 디바이스에 (필수 및 사용 가능한) 모든 관리형 앱을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수 있습니다. 조직에서 앱을 필수 또는 사용 가능하게 설정하지 않으면 회사 앱이 설치되지 않았다는 메시지가 사용자에게 표시됩니다. 사용자도 설치 상태별로 앱을 정렬하거나 필터링할 수 있습니다.

#### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956---"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고 <!-- 3041956 -->
Android 작업 프로필 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태와, 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](apps-add-android-for-work.md#managed-google-play-app-type)을 참조하세요.

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>조직 데이터에 연결할 수 있는 브라우저 구성 <!-- 3145939 -->
Android 및 iOS 디바이스의 Intune APP(앱 보호 정책)를 사용하면 Intune Managed Browser 또는 Microsoft Edge를 망라한 특정 브라우저에 조직 웹 링크를 전송할 수 있습니다.  APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

#### <a name="installed-apps-page-on-the-company-portal-website-----4224326---"></a>회사 포털 웹 사이트에 설치된 앱 페이지  <!-- 4224326 -->
[회사 포털 웹 사이트](https://portal.manage.microsoft.com/)가 디바이스에 설치된 모든 앱을 사용자에게 표시하는 새 페이지를 포함하게 됩니다. 이 목록에는 사용 가능한 앱과 조직에서 요구하는 앱이 모두 포함됩니다. 이 페이지에서 사용자가 디바이스의 앱 설치와 요구 사항 상태를 확인할 수 있습니다. 회사 포털 웹 사이트에 대한 자세한 정보는 [Intune 회사 포털 웹 사이트 사용](/intune-user-help/using-the-intune-company-portal-website.md) 및 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

#### <a name="call-graph-api-read-operations-from-an-application-without-user-credentials----4655885---"></a>사용자 자격 증명 없이 애플리케이션에서 Graph API 읽기 작업 호출 <!-- 4655885 -->
애플리케이션이 사용자 자격 증명 없이 앱 ID를 통해 Intune Graph API 읽기 작업을 호출할 수 있습니다. 자세한 내용은 [사용자 없이 액세스 얻기](https://docs.microsoft.com/graph/auth-v2-service)를 참조하세요.

<!-- ***********************************************-->
### <a name="device-configuration"></a>디바이스 구성


#### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS용 IKEv2 VPN 프로필 지원 <!-- 1943438 -->
IKEv2 프로토콜을 사용하여 iOS 원시 VPN 클라이언트에 대한 VPN 프로필을 만들 수 있습니다. IKEv2는 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **VPN**(프로필 형식) > **설정**의 새 연결 형식입니다.

이 VPN 프로필은 원시 VPN 클라이언트를 구성합니다. 따라서 관리 디바이스에 VPN 클라이언트 앱이 설치되거나 푸시되지 않습니다. 이 기능을 사용하려면 디바이스를 Intune에 등록해야 합니다(MDM 등록).

구성할 수 있는 최신 VPN 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)을 참조하세요.

적용 대상: iOS

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----20430240---"></a>macOS 디바이스에서 커널 확장에 대한 설정 구성 <!-- 20430240 -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택). 향후 업데이트에는 디바이스에서 커널 확장을 구성하고 사용할 수 있는 새 설정 그룹이 포함됩니다.

적용 대상: macOS 10.13.2 이상

#### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>키워드 검색에 대한 기준 지원  <!-- 3082036         -->
보안 기준 프로필을 만들거나 편집하는 동안 곧 *검색*을 사용하여 콘솔에 표시되는 설정을 필터링할 수 있게 됩니다.   

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 -->
Windows 10 다비이스 구성 프로필을 만듭니다(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10**). 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 대상: 
- Windows 10 이상

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002----"></a>Windows 10 디바이스에 대한 스토어 앱 전용 설정에 다른 구성 옵션 포함 <!-- 2697002  -->

Windows 디바이스에 대한 디바이스 제한 프로필을 만들 때 **스토어의 앱만** 설정을 사용하여 사용자가 Windows 앱 스토어에서만 앱을 설치하게 할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼용) > **디바이스 제한**(프로필 유형)). 향후 업데이트에서는 이 설정이 더 많은 옵션을 지원하도록 확장됩니다. 

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Windows 10(이상) 디바이스 설정](device-restrictions-windows-10.md#app-store)으로 이동하세요.

적용 대상: Windows 10 이상

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>여러 Zebra 모바일 확장 디바이스 프로필을 디바이스, 동일한 사용자 그룹 또는 동일한 디바이스 그룹에 배포 <!-- 4089955 -->
Intune에서는 디바이스 구성 프로필에서 Zebra 모바일 확장(MX)을 사용하여 설정을 사용자 지정하거나, Intune에서 기본 제공하지 않는 설정을 추가할 수 있습니다. 현재는 한 디바이스에 한 프로필을 배포할 수 있습니다. 향후 업데이트에서는 여러 프로필을 다음에 배포할 수 있게 됩니다.

- 동일한 사용자 그룹
- 동일한 디바이스 그룹
- 단일 디바이스

[Microsoft Intune에서 Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)는 Intune에서의 MX 사용 방법을 보여 줍니다.

적용 대상: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS 디바이스에서 일부 키오스크 설정이 “허용”이 아닌 “차단”으로 설정됩니다. <!-- 4404075  -->
iOS 디바이스에서 디바이스 제한 프로필을 만들 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **키오스크**) **자동 잠금**, **벨소리 전환**, **화면 회전**, **화면 일시 중지 단추** 및 **볼륨 단추**를 설정합니다. 

현재 이 설정은 **허용**(기능 차단) 또는 **구성 안 함**(기능 허용)을 통해 구성됩니다. 향후 업데이트에서는 값이 **차단**(기능 차단) 또는 **구성 안 함**(기능 허용)으로 업데이트됩니다.

현재 설정을 확인하려면 [기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md)으로 이동하세요. 

적용 대상: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704----"></a>iOS 디바이스에서 암호 인증에 Face ID 사용 <!-- 4490704  -->
iOS 디바이스에 대한 디바이스 제한 프로필을 만들 때 지문을 암호에 사용할 수 있습니다. 향후 업데이트에서는 지문 암호 설정에서 안면 인식도 사용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **암호**). 결과적으로 다음 설정을 변경합니다.

- **지문 잠금 해제**가 이제 **Touch ID 및 Face ID 잠금 해제**가 됩니다.
- **지문 수정(감독 모드에서만 해당)** 이 이제 **Touch ID 및 Face ID 수정(감독 모드에서만 해당)** 이 됩니다.

Face ID는 iOS 11.0 이상에서 제공됩니다. 현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md#password)으로 이동하세요.

적용 대상: iOS

#### <a name="apps-feature-is-dependent-on-ratings-region-when-restricting-gaming-and-app-store-features-on-ios-devices----4593948----"></a>iOS 디바이스에서 게임 및 App Store 기능을 제한할 때 앱 기능은 등급 지역에 따라 다릅니다. <!-- 4593948  -->
iOS 디바이스에서는 게임, App Store, 문서 보기 관련 기능을 허용하거나 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **App Store, 문서 보기, 게임**). 또한 미국처럼 등급 지역을 선택할 수 있습니다. 향후 업데이트에서는 **앱** 기능이 **등급 역**의 자식 요소가 되며 **등급 지역**에 따라 달라집니다.

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동하세요.

적용 대상: iOS

#### <a name="administrative-templates-for-group-policy---------3510695---"></a>그룹 정책 관리 템플릿     <!--  3510695 -->
클라우드에서 디바이스 보안을 높이기 위해 Intune을 사용하여 Windows PC용 그룹 정책 설정 선택을 구성할 수 있는 관리 템플릿을 출시할 것입니다.  이러한 템플릿은 정책 CSP(구성 서비스 공급자)를 사용하여 Office, Windows 및 OneDrive로부터 최대 2,500개의 추가 설정을 제공합니다.

####  <a name="new-settings-for-the-windows-security-baseline-----3534649-4217151------------"></a>Windows 보안 기준에 대한 새 설정  <!-- 3534649, 4217151          -->
Windows 보안 기준에 대한 새 설정을 추가합니다. 첫 번째 설정은 가상화 기반 보안에 대한 것으로, Secure Boot가 필요합니다. 두 번째 설정은 화면이 잠겼을 때 Windows 앱의 음성 활성화를 관리하기 위한 것입니다.

#### <a name="security-baselines-will-be-generally-available------3785395---------"></a>보안 기준 일반 제공  <!--  3785395       -->
보안 기준 기능이 곧 미리 보기로 일반 제공될 예정입니다. 

#### <a name="the-windows-security-baseline-template-will-be-generally-available-------3794072---------"></a>Windows 보안 기준 템플릿 일반 제공   <!--  3794072       -->
Windows 보안 기준 템플릿이 곧 미리 보기로 일반 제공될 예정입니다. 템플릿의 미리 보기 버전이 사용 중지되며 새 템플릿이 제공됩니다.

<!-- ***********************************************-->
### <a name="device-management"></a>디바이스 관리

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>보안 그룹의 모든 관리 디바이스에 범위 태그 할당 <!-- 3173810 -->
현재 각 개별 디바이스의 **속성** 페이지에서 범위 태그를 선택하여 디바이스에 범위 태그를 할당할 수 있습니다. 향후 업데이트에서는 보안 그룹에 범위 태그를 할당할 수 있으며 이 보안 그룹의 모든 디바이스가 해당 범위 태그에 연결됩니다. 이를 위해 **Intune** > **역할** > **범위(태그)**  > **만들기** > **범위(태그)** 에서 범위 태그를 할당하려는 그룹을 선택합니다. 이 그룹의 모든 디바이스에도 해당 범위 태그가 할당됩니다. 이 기능으로 설정된 범위 태그는 현재 디바이스 범위 태그 흐름으로 설정된 범위 태그를 덮어쓰게 됩니다. 향후 업데이트에서는 디바이스에 범위 태그를 할당하는 현재 흐름이 읽기 전용이 됩니다.

#### <a name="see-the-security-patch-level-for-android-devices----4461911----"></a>Android 디바이스에 대한 보안 패치 수준 참조 <!-- 4461911  -->
Android 디바이스에 대한 보안 패치 수준을 확인할 수 있습니다. 이를 위해 **Intune** > **디바이스** > **모든 디바이스** > 디바이스 선택 > **모니터** > **하드웨어**를 선택합니다.


<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


