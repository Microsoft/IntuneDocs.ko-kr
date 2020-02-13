---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/03/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: cafe9d3036a727d79de88eda050399138da55675
ms.sourcegitcommit: 24487f078349795922dc497c952e8358cf767a1a
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76977753"
---
# <a name="in-development-for-microsoft-intune---february-2020"></a>개발 중인 Microsoft Intune 기능 - 2020년 2월

준비 및 계획을 돕기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 이 페이지의 정보 외에 다음을 참조할 수 있습니다. 

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 Office 메시지 센터에 보완 게시물을 게시할 것입니다.
- 미리 보기 또는 일반적으로 사용할 수 있는 기능이 프로덕션 단계에 들어가면 기능 설명이 이 페이지에서 [새로운 기능](whats-new.md)으로 이동합니다.
- 이 페이지와 [새로운 기능](whats-new.md) 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [Microsoft 365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!NOTE]
> 이 페이지는 향후 릴리스에서 제공될 Intune 기능에 대한 Microsoft의 현재 기대를 반영합니다. 날짜 및 개별 기능이 변경될 수 있습니다. 이 페이지는 개발의 일부 기능만 설명합니다.

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

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Windows에서 회사 포털 앱에 대한 알림 표시<!-- 1808082  -->
애플리케이션이 닫힌 경우에도 사용자에게 알림 메시지를 표시하도록 Windows 디바이스의 회사 포털 앱을 업데이트할 예정입니다. 이 업데이트에서는 설치 상태가 완료 또는 실패인 경우에만 사용 가능한 앱에 대한 알림을 표시합니다. 회사 포털 앱은 필요한 애플리케이션에 대한 알림을 표시하지 않습니다. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>회사 포털 앱에 대한 설치 상태 메시지 표시<!-- 2514416  -->
회사 포털 앱은 최종 사용자에게 앱 설치 상태 메시지를 추가로 표시합니다. 새 Win32 종속성 기능에는 다음과 같은 조건이 적용됩니다.
- 앱을 설치하지 못했습니다. 관리자가 정의한 종속성이 충족되지 않았습니다.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276---"></a>iOS 디바이스에서 Microsoft Edge로 웹 클립의 대상 변경<!-- 5455276 -->
웹 클립은 iOS 디바이스에서 고정된 웹앱 역할을 하는 것으로, 업데이트가 필요합니다. 보호되는 브라우저에서 열어야 하는 경우 새로 배포된 웹 클립은 Intune Managed Browser 대신 Microsoft Edge에서 열립니다. Managed Browser 대신 Microsoft Edge에서 열리도록 기존 웹 클립의 대상을 변경해야 합니다.

### <a name="macos-company-portal-user-experience-improvements---5568987---"></a>macOS 회사 포털 사용자 환경 향상<!-- 5568987 -->
Microsoft에서는 macOS 디바이스 등록 환경 및 Mac용 회사 포털 앱을 개선하고 있습니다. 다음을 기대할 수 있습니다.
- 등록하는 동안 사용자에게 최신 회사 포털 버전을 제공하게 될 향상된 Microsoft **AutoUpdate** 환경.
- 등록하는 동안 향상된 준수 검사 단계.
- 사용자가 디바이스에서 회사 지원 팀으로 오류를 더 빠르게 보낼 수 있도록 복사된 인시던트 ID 지원.

등록 및 Mac용 회사 포털 앱에 대한 자세한 내용은 회사 포털 앱을 사용하여 macOS 디바이스 등록(https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp) 을 참조하세요. 


### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>회사 포털에서 화면이 제거됨, Android 회사 프로필 등록<!--6103987 -->
사용자 환경을 간소화하기 위해 회사 포털의 Android 회사 프로필 등록 흐름에서 **새로운 기능** 화면이 제거됩니다. [Android 회사 프로필에 등록]( https://docs.microsoft.com/intune-user-help/enroll-device-android-work-profile)으로 이동하여 현재 Android 회사 프로필 등록 흐름을 확인합니다.

### <a name="microsoft-defender-advanced-threat-protection-atp-app-for-macos---5424518-idready---"></a>macOS용 Microsoft Defender ATP(Advanced Threat Protection) 앱<!-- 5424518 idready -->
Intune에서는 macOS용 Microsoft Defender ATP(Advanced Threat Protection) 앱을 관리형 Mac 디바이스에 배포하는 간편한 방법을 제공합니다. 자세한 내용은 [Mac용 Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac)을 참조하세요. 

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 디바이스의 유선 네트워크 디바이스 구성 프로필<!-- 3508686  -->
유선 네트워크를 구성하는 새로운 macOS 디바이스 구성 프로필을 사용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **macOS**(플랫폼) > **유선 네트워크**(프로필 유형) 선택). 이 기능을 사용하여 유선 네트워크를 관리하는 802.1x 프로필을 만들고 이 유선 네트워크를 macOS 디바이스에 배포합니다.

적용 대상:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>IKEv2 VPN 연결이 포함된 VPN 프로필이 iOS 디바이스에서 항상 사용할 수 있음 <!-- 1947932 idready -->
iOS 디바이스에서 IKEv2 연결을 사용하는 VPN 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS/iPadOS**(플랫폼) > **VPN**(프로필 유형) 선택). 이후 업데이트에서는 IKEv2에 대해 항상 사용하도록 구성할 수 있습니다. 구성된 경우 IKEv2 VPN 프로필은 자동으로 연결되며 VPN에 연결된 상태를 유지합니다(또는 빠르게 다시 연결). 네트워크 간에 이동하거나 디바이스를 다시 시작하는 경우에도 연결된 상태를 유지합니다.

iOS에서 항상 사용 VPN은 IKEv2 프로필로 제한됩니다.

구성할 수 있는 최신 IKEv2 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 추가](../configuration/vpn-settings-ios.md#ikev2-settings)를 참조하세요.

적용 대상:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>iOS 및 macOS 디바이스에서 구성 프로필을 만들 때 향상된 사용자 인터페이스 환경<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
iOS 또는 macOS 디바이스용 프로필을 만들면 Endpoint Management 관리 센터의 환경이 업데이트됩니다. 이 변경의 영향을 받는 디바이스 구성 프로필은 다음과 같습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > **iOS** 또는 **macOS**(플랫폼) 선택).

- 사용자 지정: iOS, macOS
- 디바이스 기능: iOS, macOS
- 디바이스 제한: iOS, macOS
- Endpoint Protection: macOS
- 확장: macOS
- 기본 설정 파일: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Android Enterprise 디바이스에서 OEMConfig 구성 프로필을 만들 때 향상된 사용자 인터페이스 환경<!-- 5568645 idready  -->
Android Enterprise 디바이스용 OEMConfig 프로필을 만들거나 편집하면 Endpoint Management 관리 센터의 환경이 업데이트됩니다. 업데이트된 환경에서는 구성한 설정을 한눈에 요약하여 제공합니다. 이 변경의 영향을 받는 OEMConfig 디바이스 구성 프로필은 다음과 같습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > **Android Enterprise**(플랫폼) > **OEMConfig**(프로필 유형) 선택).

이 기능은 다음에 적용됩니다.
- Android Enterprise 


<!-- ***********************************************-->
<!--## Device enrollment-->


<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="change-primary-user-for-windows-devices----3794742---"></a>Windows 디바이스의 기본 사용자 변경 <!-- 3794742 -->
Windows 하이브리드 및 Azure AD 조인 디바이스의 기본 사용자를 변경할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스** > **모든 디바이스**로 이동하고, 디바이스를 선택한 다음, **속성** > **기본 사용자**를 선택합니다. 

### <a name="serial-number-on-the-apple-mdm-push-certificate-page--5947765---"></a>Apple MDM Push Certificate 페이지의 일련 번호<!--5947765 -->
Apple MDM Push Certificate 페이지에 일련 번호가 표시됩니다. 인증서를 만든 Apple ID에 대한 액세스 권한이 손실된 경우 Apple MDM Push Certificate에 대한 액세스 권한을 다시 얻으려면 일련 번호가 필요합니다. 일련 번호를 확인하려면 **디바이스** > **iOS** > **iOS 등록** > **Apple MDM Push Certificate**로 이동합니다.

### <a name="choose-which-iosipados-updates-to-push-to-enrolled-devices--5879689---"></a>등록된 디바이스로 푸시할 iOS/iPadOS 업데이트 선택<!--5879689 -->
Apple Business Manager 또는 Apple School Manager 중 하나를 사용하여 등록한 디바이스에 푸시할 특정 iOS/iPadOS 업데이트를 선택할 수 있습니다. 해당 디바이스에서는 일정 기간(일) 동안 소프트웨어 업데이트 표시를 연기하도록 디바이스 구성 정책을 설정해야 합니다. 이 기능을 확인하려면 MEM > **디바이스** > **iOS** > **iOS/iPadOS용 업데이트 정책** > **프로필 만들기**로 이동합니다.

### <a name="new-update-schedule-options-for-pushing-os-updates-to-enrolled-iosipados-devices--5879689--"></a>등록된 iOS/iPadOS 디바이스로 OS 업데이트를 푸시하기 위한 새로운 업데이트 일정 옵션<!--5879689-->
iOS/iPadOS 디바이스의 운영 체제 업데이트를 예약할 때 다음 옵션을 사용할 수 있습니다. 이 내용은 Apple Business Manager 또는 Apple School Manager 등록 유형을 사용한 디바이스에 적용됩니다.
- 다음 체크 인 시 업데이트
- 예약된 시간 동안 업데이트
- 예약된 시간 외의 시간에 업데이트

두 번째 옵션의 경우 여러 기간을 만들 수 있습니다.

새 옵션을 확인하려면 MEM > **디바이스** > **iOS** > **iOS/iPadOS용 업데이트 정책** > **프로필 만들기**로 이동합니다.


<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->
## <a name="monitoring-and-troubleshooting"></a>모니터링 및 문제 해결

### <a name="improved-intune-reporting-experience---3791418-idready---"></a>향상된 Intune 보고 환경<!-- 3791418 idready -->
이제 Intune은 새로운 보고서 유형, 더 나은 보고서 구성, 더 집중된 보기, 향상 된 보고서 기능, 좀 더 일관되고 시기 적절한 데이터를 포함하는 향상된 보고 환경을 제공합니다. 보고 환경은 공개 미리 보기에서 GA(일반 공급)로 전환됩니다. 또한 GA 릴리스는 [Microsoft 엔드포인트 관리자 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)의 타일에서 지역화 지원, 버그 수정, 디자인 개선 및 집계 디바이스 준수 데이터를 제공합니다.

새 보고서 유형은 다음에 주안점을 둡니다.
- **작동** - 음수(-) 상태 포커스가 있는 새 레코드를 제공합니다. 
- **조직** - 전반적인 상태에 대한 광범위한 요약을 제공합니다.
- **기록** - 일정 시간 동안의 패턴 및 추세를 제공합니다.
- **전문가** - 원시 데이터를 사용하여 고유한 사용자 지정 보고서를 만들 수 있습니다.

새 보고서의 첫 번째 세트는 디바이스 준수에 주안점을 둡니다. 자세한 내용은 [블로그 - Microsoft Intune 보고 프레임워크](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) 및 [Intune 보고서](~/fundamentals/reports.md)를 참조하세요.



<!-- ***********************************************-->
## <a name="role-based-access-control"></a>역할 기반 액세스 제어

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune 역할 사용자 인터페이스 변경 예정<!--5801612 idready-->
[Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431) > **테넌트 관리** > **역할**의 사용자 인터페이스는 보다 사용자에게 친숙하고 직관적인 디자인으로 변경될 예정입니다. 이 환경에서는 지금 사용하는 것과 동일한 설정 및 세부 정보를 제공하지만, 새로운 환경에서는 마법사 같은 프로세스를 채택합니다.


<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 디바이스에서 파생된 자격 증명 지원<!--4839592-->
Android Enterprise 완전 관리형 디바이스에서 파생된 자격 증명을 사용할 수 있습니다. Entrust Datacard, Intercede 및 DISA Purebred에 대해 파생된 자격 증명을 검색하기 위한 지원이 포함됩니다. 지원하는 앱에서 앱 인증, Wi-Fi, VPN 또는 S/MIME 서명 및/또는 암호화를 위해 파생된 자격 증명을 사용할 수 있습니다.

### <a name="use-antivirus-policy-to-manage-settings-for-microsoft-defender-antivirus-and-the-windows-security-experience--6131401---"></a>바이러스 백신 정책을 사용하여 Microsoft Defender 바이러스 백신 및 Windows 보안 환경의 설정을 관리합니다.<!--6131401 -->
‘Endpoint security’ 노드에서 **바이러스 백신**의 설정을 구성할 수 있습니다.  바이러스 백신 정책을 구성할 때 다음 두 가지 프로필 유형을 통해 Windows 10 디바이스의 설정을 정의합니다.

- Microsoft Defender 바이러스 백신: 클라우드 보호, 바이러스 백신 제외, 업데이트 관리, 검사 옵션 등의 설정을 관리합니다.
- Windows 보안 환경: 사용자가 디바이스에서 Windows 보안 설정을 사용하는 방식을 관리합니다. 최종 사용자가 Microsoft Defender 보안 센터에서 볼 수 있는 항목과 수신하는 알림을 구성할 수 있습니다. 

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


