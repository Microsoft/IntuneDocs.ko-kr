---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3c2b9429bf5b50ac5e416c4a7b356627e9cc9fb1
ms.sourcegitcommit: f75386986d24e7d5dd63a3f1a0a014cb52056063
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69560111"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 8월

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

### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱 보호 정책 (앱)을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 응용 프로그램을 사용 하도록 설정 된 응용 프로그램에는이 기능을 APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고 <!-- 3041956  -->
Android 작업 프로필 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태 및 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](apps-add-android-for-work.md#managed-google-play-app-type)을 참조하세요.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS용 IKEv2 VPN 프로필 지원 <!-- 1943438 -->
IKEv2 프로토콜을 사용하여 iOS 원시 VPN 클라이언트에 대한 VPN 프로필을 만들 수 있습니다. IKEv2는 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **VPN**(프로필 형식) > **설정**의 새 연결 형식입니다.

이 VPN 프로필은 원시 VPN 클라이언트를 구성합니다. 따라서 관리 디바이스에 VPN 클라이언트 앱이 설치되거나 푸시되지 않습니다. 이 기능을 사용하려면 디바이스를 Intune에 등록해야 합니다(MDM 등록).

구성할 수 있는 최신 VPN 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)을 참조하세요.

적용 대상: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>디바이스 등록

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS 장치에 대해 회사 포털 등록 프로세스 개인 정보 화면을 사용자 지정 합니다. <!-- 4394993  -->
Markdown를 사용 하면 iOS 등록 중 최종 사용자에 게 표시 되는 회사 포털 개인 정보 화면을 사용자 지정할 수 있습니다. 특히, 조직에서 볼 수 없거나 장치에서 수행할 수 없는 항목 목록을 사용자 지정할 수 있습니다.

<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="import-and-export-security-baselines------3408610------------"></a>보안 기준 가져오기 및 내보내기    <!--3408610          -->  
보안 기준을 내보내고 가져오는 기능을 추가 하는 중입니다. 이 기능을 사용 하면 사용자 지정 항목을 가져와서 Intune 환경 간에 공유할 수 있습니다.

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.




