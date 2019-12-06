---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ad5c26770537ce6a285989f8ca3804277616419
ms.sourcegitcommit: 16a9109b4028589c17695d41271ca4fee8b1d697
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74540783"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. 또한 [중요한 공지](#notices), [과거 릴리스](whats-new-archive.md) 및 [Intune 서비스 업데이트가 릴리스되는 방법](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)에 관한 정보도 찾을 수 있습니다.

> [!Note]
> 각 [월별 업데이트](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)는 출시에 최대 3일이 걸릴 수 있고 다음 순서로 출시됩니다.
>
> - 1일: 아시아 태평양(APAC)
> - 2일: 유럽, 중동, 아프리카(EMEA)
> - 3일: 북아메리카
>
> 일부 기능은 몇 주에 걸쳐 출시될 수 있고 첫 번째 주에는 모든 고객에게 제공되지 않습니다.
>
> [개발 페이지](in-development.md)에서 릴리스의 예정 기능 목록을 확인하세요.

**RSS 피드**: 다음 URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다. `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control
-->  

<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>2019년 11월 18일 주(1911 서비스 릴리스)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="smime-support-with-microsoft-outlook-for-ios---2669398-idready---"></a>iOS용 Microsoft Outlook의 S/MIME 지원<!-- 2669398 idready -->
Intune은 iOS 디바이스에서 iOS용 Outlook과 함께 사용할 수 있는 S/MIME 서명 및 암호화 인증서 배달을 지원합니다. 자세한 내용은 [iOS용 Outlook의 S/MIME 관리 구성](~/apps/app-configuration-policies-outlook-smime.md)을 참조하세요.

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>앱 데이터를 선택적으로 초기화하는 경우의 UI 업데이트<!-- 4102028 -->
Intune에서 앱 데이터를 선택적으로 초기화하는 UI가 업데이트되었습니다. UI 변경 사항에는 다음이 포함됩니다.
- 하나의 창 내에 압축된 마법사 스타일 형식을 사용하여 간소화된 환경
- 할당을 포함하는 만들기 흐름에 대한 업데이트
- 속성을 볼 때, 새 정책을 만들기 전에 또는 속성을 편집할 때 설정된 모든 항목의 요약된 페이지 또한 속성을 편집할 때 요약에는 편집 중인 속성 범주의 항목 목록만 표시됩니다.

자세한 내용은 [Intune 관리 앱에서 회사 데이터만 초기화하는 방법](~/apps/apps-selective-wipe.md)을 참조하세요.

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS 및 iPadOS 타사 키보드 지원<!-- 4922950 -->
2019년 3월에는 iOS 앱 보호 정책 설정 "타사 키보드"의 지원이 제거된다는 소실을 발표했습니다. 이 기능은 iOS 및 iPadOS가 모두 지원되는 Intune으로 전환될 예정입니다. 이 설정을 사용하려면 새 또는 기존 iOS/iPadOS 앱 보호 정책의 **데이터 보호** 탭으로 이동한 후 **데이터 전송** 아래의 **타사 키보드** 설정을 찾습니다.

이 정책 설정의 동작은 이전 구현과 약간 다릅니다. 이 설정이 **차단**으로 구성된 앱 보호 정책의 대상으로 지정된 SDK 버전 12.0.16 이상을 사용하는 다중 ID 앱에서 최종 사용자는 조직 및 개인 계정 모두에서 타사 키보드를 옵트인(opt in)할 수 없습니다. SDK 버전 12.0.12 이하 버전을 사용하는 앱은 블로그 게시물 제목, [알려진 문제: 타사 키보드가 개인 계정의 iOS에서 차단되지 않습니다](https://aka.ms/3rdparty_iOS_Intune)에 설명된 동작을 계속 발생합니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>디바이스 구성

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Jamf 관리가 필요한 macOS 사용자 그룹을 대상으로 지정합니다.<!-- 4061739  --> 
[macOS 디바이스를 Jamf로 관리](../protect/conditional-access-integrate-jamf.md)할 특정 사용자 그룹을 대상으로 지정할 수 있습니다. 이렇게 하면 다른 디바이스가 Intune에서 관리되는 동안 macOS 디바이스 하위 세트에 Jamf 준수 통합을 적용할 수 있습니다. Jamf 통합을 이미 사용하고 있는 경우 모든 사용자는 기본적으로 통합의 대상이 됩니다.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>iOS 디바이스에서 메일 디바이스 구성 프로필을 만들 경우 새로운 Exchange ActiveSync 설정<!-- 4892824   --> 
iOS/iPadOS 디바이스의 디바이스 구성 프로필에서 메일 연결을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해  > **iOS/iPadOS** 선택 > 프로필 유형에 대해 **메일** 선택). 

다음을 포함하는 새 Exchange ActiveSync 설정을 사용할 수 있습니다.
- **동기화할 Exchange 데이터**: 일정, 연락처, 미리 알림, 메모 및 메일에 대해 동기화(또는 동기화를 차단)할 Exchange 서비스를 선택합니다.
- **사용자가 동기화 설정을 변경할 수 있도록 허용**: 사용자가 디바이스에서 이러한 서비스에 대한 동기화 설정을 변경할 수 있도록 허용(또는 차단)합니다.  

이러한 설정에 대한 자세한 내용은 [Intune에서 iOS 디바이스에 대한 메일 프로필 설정](../configuration/email-settings-ios.md)으로 이동합니다. 

적용 대상:
- iOS 13.0 이상
- iPadOS 13.0 이상

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>사용자가 Android Enterprise 완전 관리형 및 전용 디바이스에 개인 Google 계정을 추가하지 못하도록 차단<!-- 5353228   -->
Android Enterprise 완전 관리형 및 전용 디바이스에는 사용자가 개인 Google 계정을 만들 수 없도록 하는 새로운 설정이 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자만 > 디바이스 제한** > **사용자 및 계정 설정** > **개인 Google 계정**).

구성할 수 있는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상:
- Android Enterprise 완전 관리형 디바이스
- Android 엔터프라이즈 전용 디바이스

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Siri용 서버 쪽 로깅 명령 설정이 iOS/iPadOS 디바이스 제한 프로필에서 제거됨 <!-- 5468501   -->
iOS 및 iPadOS 디바이스에서 **Siri용 서버 쪽 로깅 명령** 설정이 Microsoft Endpoint Manager 관리자 콘솔(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **iOS/iPadOS** > 프로필 유형에 대해 **디바이스 제한** > **기본 제공 앱**)에서 제거됩니다. 

이 설정은 디바이스에 영향을 주지 않습니다. 기존 프로필에서 설정을 제거하려면 프로필을 열고 원하는 대로 변경한 다음, 프로필을 저장합니다. 프로필이 업데이트되고 설정이 디바이스에서 삭제됩니다.

구성할 수 있는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 및 iPadOS 디바이스 설정](../configuration/device-restrictions-ios.md)을 참조하세요.

적용 대상:
- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 기능 업데이트(공개 미리 보기)<!-- 2384877 -->
이제 Windows 10 디바이스에 [Windows 10 기능 업데이트](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)를 배포할 수 있습니다. Windows 10 기능 업데이트는 디바이스에 설치하고 유지할 Windows 10 버전을 설정하는 새로운 소프트웨어 업데이트 정책입니다. 기존 Windows 10 업데이트 링과 함께 이 새로운 정책 유형을 사용할 수 있습니다.

Windows 10 기능 업데이트 정책이 적용되는 디바이스는 지정된 버전의 Windows를 설치하고 정책이 편집 또는 제거될 때까지 해당 버전으로 유지됩니다. 이후 버전의 Windows를 실행하는 디바이스는 현재 버전으로 유지됩니다. 특정 버전의 Windows로 유지되는 디바이스는 Windows 10 업데이트 링에서 해당 버전에 대한 품질 및 보안 업데이트를 계속 설치할 수 있습니다.

이번 주에 이 새로운 유형의 정책이 테넌트로 롤아웃되기 시작합니다. 테넌트에서 이 새로운 정책을 아직 사용할 수 없는 경우 곧 제공될 예정입니다.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>macOS 애플리케이션용 plist 파일에서 키 정보 추가 및 변경<!-- 4736278 -->
macOS 디바이스에서 이제 앱 또는 디바이스에 연결된 속성 목록 파일(.plist)을 업로드하는 디바이스 구성 프로필을 만들 수 있습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** > 프로필 유형에 대해 **기본 설정 파일**).

일부 앱에서만 관리형 기본 설정을 지원하며, 이러한 앱에서 모든 설정을 관리할 수 있는 것은 아닙니다. 사용자 채널 설정이 아니라 디바이스 채널 설정을 구성하는 속성 목록 파일을 업로드해야 합니다.

이 기능에 대한 자세한 내용은 [Microsoft Intune을 사용하여 macOS 디바이스에 속성 목록 파일 추가](../configuration/preference-file-settings-macos.md)를 참조하세요.

적용 대상:
- 10.7 이상 버전을 실행하는 macOS 디바이스

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Autopilot 디바이스에 대한 디바이스 이름 값 편집<!-- 2640074 -->
Azure AD 조인 Autopilot 디바이스에 대한 디바이스 이름 값을 편집할 수 있습니다.  자세한 내용은 [Autopilot 디바이스 특성 편집](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)을 참조하세요.

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Autopilot 디바이스에 대한 그룹 태그 값 편집<!-- 4816775   -->
Autopilot 디바이스에 대한 그룹 태그 값을 편집할 수 있습니다. 자세한 내용은 [Autopilot 디바이스 특성 편집](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="updated-support-experience---5012398---"></a>업데이트된 지원 환경<!-- 5012398 -->

오늘부터 [Intune에 대한 도움말 및 지원 받기](get-support.md)를 위한 업데이트되고 간소화된 콘솔 내 환경이 테넌트에 롤아웃됩니다. 이 새로운 환경을 아직 사용할 수 없는 경우 곧 제공될 예정입니다.

콘솔 내의 일반 문제 검색과 피드백, 그리고 고객 지원팀 연락에 이용하는 워크플로도 개선되었습니다. 지원 문제를 열 때 언제 콜백이나 이메일 회신을 받게 될지에 대한 예상 정보가 실시간으로 표시되며 프리미어 및 통합 지원 고객은 문제의 심각도를 간편히 지정해 지원을 더 신속히 받을 수 있습니다.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>향상된 Intune 보고 환경(퍼블릭 미리 보기) <!-- 3791418 -->
이제 Intune은 새로운 보고서 유형, 더 나은 보고서 구성, 더 집중된 보기, 향상 된 보고서 기능, 좀 더 일관되고 시기 적절한 데이터를 포함하는 향상된 보고 환경을 제공합니다. 새 보고서 유형은 다음에 주안점을 둡니다.
- **작동** - 음수(-) 상태 포커스가 있는 새 레코드를 제공합니다. 
- **조직** - 전반적인 상태에 대한 광범위한 요약을 제공합니다.
- **기록** - 일정 시간 동안의 패턴 및 추세를 제공합니다.
- **전문가** - 원시 데이터를 사용하여 고유한 사용자 지정 보고서를 만들 수 있습니다.

새 보고서의 첫 번째 세트는 디바이스 준수에 주안점을 둡니다. 자세한 내용은 [블로그 - Microsoft Intune 보고 프레임워크](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) 및 [Intune 보고서](~/fundamentals/reports.md)를 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>중복된 사용자 지정 또는 기본 제공 역할 <!-- 1081938   -->
이제 기본 제공 및 사용자 지정 역할을 복사할 수 있습니다. 자세한 내용은 [역할 복사](../fundamentals/create-custom-role.md#copy-a-role)를 참조하세요.

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>학교 관리자 역할에 대한 새 권한 <!-- 5621805  -->  
2개의 새 사용 권한인 **프로필 할당** 및 **디바이스 동기화**가 학교 관리자 역할 > **권한** > **등록 프로그램**에 추가되었습니다. 프로필 동기화 권한을 통해 관리자는 Windows Autopilot 디바이스를 동기화할 수 있습니다. 프로필 할당 권한을 통해 사용자가 시작한 Apple 등록 프로필을 삭제할 수 있습니다. 또한 Autopilot 디바이스 할당 및 Autopilot 배포 프로필 할당을 관리할 수 있는 권한도 부여됩니다. 모든 학교 관리자/그룹 관리자 권한 목록은 [그룹 관리자 할당](https://docs.microsoft.com/intune-education/group-admin-delegate)을 참조하세요. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>보안

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker 키 순환<!-- 2564951  -->
Intune 디바이스 작업을 사용하여 Windows 버전 1909 이상을 실행하는 관리 디바이스에 대한 [BitLocker 복구 키를 원격으로 순환](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)할 수 있습니다. 복구 키를 순환할 수 있으려면 복구 키 순환을 지원하도록 디바이스를 구성해야 합니다.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>SCEP 디바이스 인증서 배포를 지원하도록 전용 디바이스 등록 업데이트 <!-- 5198878  -->
이제 Intune은 Wi-Fi 프로필에 대한 인증서 기반 액세스를 위해 Android Enterprise 전용 디바이스에 SCEP 디바이스 인증서를 배포하도록 지원합니다. 배포가 작동하려면 디바이스에 Microsoft Intune 앱이 있어야 합니다. 따라서 Android Enterprise 전용 디바이스의 등록 환경이 업데이트되었습니다. 새 등록은 동일하게 시작되지만(QR, NFC, Zero-touch 또는 디바이스 식별자 사용), 이제 사용자에게 Intune 앱을 설치하도록 요구하는 단계가 제공됩니다. 기존 디바이스에서 롤링을 기준으로 앱을 자동으로 설치하기 시작합니다.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>기업 간 공동 작업을 위한 Intune 감사 로그<!--5670211 -->
B2B(기업 간) 공동 작업을 사용하여 회사의 애플리케이션과 서비스를 다른 조직의 게스트 사용자와 안전하게 공유하면서 자체 회사 데이터에 대한 제어를 유지할 수 있습니다. 이제 Intune에서 B2B 게스트 사용자에 대한 감사 로그를 지원합니다. 예를 들어, 게스트 사용자가 변경을 수행하는 경우 Intune에서 감사 로그를 통해이 데이터를 캡처할 수 있습니다. 자세한 내용은 [Azure Active Directory B2B의 게스트 사용자 액세스란?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)을 참조하세요.


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>2019년 11월 11일 주  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349-wnready---"></a>회사 포털의 개선된 macOS 등록 환경 <!-- 5074349 WNready -->  
macOS용 회사 포털 등록 환경은 iOS용 회사 포털 등록 환경과 보다 긴밀하게 정렬된 더 간단한 등록 프로세스를 제공합니다. 이제 디바이스 사용자에게 다음과 같은 이점이 제공됩니다.  

* 보다 간소화된 사용자 인터페이스.  
* 향상된 등록 확인 목록.  
* 보다 명확하게 설명된 디바이스 등록 방법.  
* 개선된 문제 해결 옵션.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Windows 회사 포털 앱에서 시작된 웹앱<!-- 5030972 -->
이제 최종 사용자가 Windows 회사 포털 앱에서 직접 웹앱을 시작할 수 있습니다. 최종 사용자는 웹앱을 선택한 다음 **브라우저에서 열기** 옵션을 선택할 수 있습니다. 게시된 웹 URL이 웹 브라우저에서 직접 열립니다. 이 기능은 다음 주에 출시될 예정입니다. 웹앱에 대한 자세한 내용은 [Microsoft Intune에 웹앱 추가](~/apps/web-app.md)를 참조하세요.  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950-wnready---"></a>Windows 10용 회사 포털의 새 할당 유형 열 <!-- 5459950 WNready -->
회사 포털 > **설치된 앱** > **할당 유형** 열의 이름이 **조직에서 요구**로 변경되었습니다.  이 열 아래에 **예** 또는 **아니요** 값이 표시되어 조직에서 해당 앱을 필수 또는 선택 사항으로 지정했는지 나타냅니다. 이러한 변경 사항은 디바이스 사용자가 사용 가능한 앱 개념을 혼동하기 때문에 적용된 것입니다. 최종 사용자는 [디바이스에 앱 설치 및 공유](/intune-user-help/install-apps-cpapp-windows)에서 회사 포털에서 앱을 설치하는 자세한 내용을 확인할 수 있습니다. 최종 사용자를 위해 회사 포털 앱을 구성하는 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](~/apps/company-portal-app.md)을 참조하세요.  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019년 11월 4일 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>디바이스 보안

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>보안 기준은 Microsoft Azure Government에서 지원됩니다.<!-- 4062552 -->

*Microsoft Azure Government*에서 호스트되는 Intune 인스턴스는 이제 [보안 기준](../protect/security-baselines.md)을 사용하여 사용자와 디바이스를 보호하는 데 도움이 될 수 있습니다.

<!-- ########################## -->
## <a name="week-of-october-28-2019"></a>2019년 10월 28일이 있는 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="improved-checklist-design-in-company-portal-app-for-android---5550857---"></a>Android용 회사 포털 앱의 향상된 검사 목록 디자인<!-- 5550857 -->  
Android용 회사 포털 앱의 설정 검사 목록이 간단한 디자인과 새로운 아이콘을 갖춰 업데이트되었습니다. 변경 내용은 iOS용 회사 포털 앱에 대한 최근 업데이트와 동일합니다. 변경 내용에 대한 세부 비교는 [앱 UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요. 업데이트된 등록 단계에 대한 자세한 내용은 [Android 회사 프로필로 등록](/intune-user-help/enroll-device-android-work-profile) 및 [Android 디바이스 등록](/intune-user-help/enroll-device-android-company-portal)을 참조하세요.  

#### <a name="win32-apps-on-windows-10-s-mode-devices---3747604---"></a>Windows 10 S 모드 디바이스의 Win32 앱<!-- 3747604 --> 
Windows 10 S 모드 관리 디바이스에서 Win32 앱을 설치 및 실행할 수 있습니다. 이 작업을 수행하려면 WDAC(Windows Defender Application Control) PowerShell 도구를 사용하여 S 모드에 대한 추가 정책을 하나 이상 만들면 됩니다. Device Guard 서명 포털을 사용하여 추가 정책에 서명한 다음, Intune을 통해 정책을 업로드 및 배포하세요. Intune에서 **클라이언트 앱** > **Windows 10 S 추가 정책**을 선택하여 이 기능을 찾을 수 있습니다. 자세한 내용은 [S 모드 디바이스에서 Win32 앱 사용](~/apps/apps-win32-s-mode.md)을 참조하세요.

#### <a name="set-win32-app-availability-based-on-a-date-and-time---3510685---"></a>날짜 및 시간을 기준으로 Win32 앱 가용성 설정<!-- 3510685 -->
관리자는 필요한 Win32 앱에 대한 시작 시간 및 최종 기한 시간을 구성할 수 있습니다. 시작 시간에 Intune 관리 확장은 앱 콘텐츠 다운로드를 시작하고 캐시합니다. 최종 기한 시간에는 앱이 설치됩니다. 사용 가능한 앱의 경우 시작 시간은 앱이 회사 포털에 표시되는 시기를 나타냅니다. 자세한 내용은 [Intune Win32 앱 관리](~/apps/apps-win32-app-management.md#set-win32-app-availability-and-notifications)를 참조하세요.

#### <a name="require-device-restart-based-on-grace-period-after-win32-app-install---3136567---"></a>Win32 앱 설치 후 유예 기간에 따라 디바이스를 다시 시작해야 함<!-- 3136567 -->
Win32 앱이 설치된 후 디바이스를 다시 시작하도록 지정할 수 있습니다. 자세한 내용은 [Win32 앱 관리 - 앱 설치 세부 정보 구성](~/apps/apps-win32-app-management.md#step-4-configure-app-installation-details)을 참조하세요.

#### <a name="dark-mode-for-ios-company-portal---4911422---"></a>iOS 회사 포털의 어두운 모드<!-- 4911422 -->
어두운 모드는 iOS 회사 포털에 사용할 수 있습니다. 사용자는 회사 앱을 다운로드하고, 디바이스를 관리하며, 디바이스 설정에 따라 본인이 선택한 색 구성표에 관해 IT 지원을 받을 수 있습니다. iOS 회사 포털에서는 최종 사용자의 디바이스 설정을 어두운 또는 밝은 모드에 자동으로 맞춥니다. 자세한 내용은 [iOS용 Microsoft Intune 회사 포털의 어두운 모드 소개](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Introducing-dark-mode-on-Microsoft-Intune-Company-Portal-for-iOS/ba-p/918453)를 참조하세요. iOS 회사 포털에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](~/apps/company-portal-app.md)을 참조하세요.

#### <a name="android-company-portal-enforced-minimum-app-version---2378776---"></a>Android 회사 포털 적용 최소 앱 버전<!-- 2378776 -->
앱 보호 정책의 **최소 회사 포털 버전** 설정을 통해 최종 사용자의 디바이스에 적용되는 정의된 특정 최소 버전의 회사 포털을 지정할 수 있습니다. 이 조건부 시작 설정을 통해서는 값이 일치하지 않을 때 가능한 조치로서 **액세스 차단**, **데이터 지우기**, **경고**를 설정할 수 있습니다. 이 값에 가능한 형식은 *[주].[부]* , *[주].[부].[빌드]* , or *[주].[부].[빌드].[수정]* 의 패턴을 따릅니다.

**최소 회사 포털 버전** 설정은 구성될 경우 버전 5.0.4560.0이나 그 이후의 회사 포털을 받는 최종 사용자에게 영향을 미칩니다. 이 설정은 이 기능이 릴리스되는 버전 이전의 회사 포털을 사용할 경우 영향을 미치지 않습니다. 앱 자동 업데이트를 디바이스에서 사용 중인 최종 사용자에게는 최신 버전의 회사 포털을 사용하고 있을 수 있으므로 이 기능의 대화 상자가 표시되지 않을 수도 있습니다. 이 설정은 등록 및 미등록 디바이스용 앱 보호 장치가 있는 Android로 한정됩니다. 자세한 내용은 [Android 앱 보호 정책 설정 - 조건부 시작](~/apps/app-protection-policy-settings-android.md#conditional-launch)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->

### <a name="microsoft-365-device-management"></a>Microsoft 365 장치 관리

#### <a name="introducing-endpoint-security-node-in-microsoft-365-device-management---5630102---"></a>Microsoft 365 장치 관리의 엔드포인트 보안 노드 소개<!-- 5630102 -->

현재 **엔드포인트 보안** 노드는 다음과 같은 엔드포인트 보호 기능을 그룹화하는 https://devicemanagement.microsoft.com 의 Microsoft 365 장치 관리 전문가 작업 영역에서 일반적으로 사용할 수 있습니다.

- 보안 기준:  사전 구성된 설정 구성으로서 Microsoft가 권장하는 기본값과 알려진 설정 구성을 적용하는 데 도움이 됩니다.

- 보안 작업: Microsoft Defender ATP 위협 요소 및 취약성 관리(TVM)의 이점을 활용하고 Intune을 사용해 엔드포인트의 약점을 해결합니다.

- Microsoft Defender ATP: 통합형 Microsoft Defender Advanced Threat Protection(ATP)으로서 보안 위반 문제 예방에 도움이 됩니다.

이 설정은 디바이스 같은 다른 적용 가능 노드에서 계속 액세스할 수 있으며, 현재 구성된 상태는 어디서 액세스해 이 기능을 활성화하든 동일합니다.

이러한 개선 사항에 대한 자세한 내용은 Microsoft Tech Community 웹 사이트의 [Intune 고객 성공 블로그 게시물](https://aka.ms/Endpoint_security_node)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="intune-supports-ios-11-and-later---4665324----"></a>Intune은 iOS 11 이상을 지원합니다<!-- 4665324  -->

Intune 등록과 회사 포털은 현재 iOS 버전 11 이상을 지원합니다. 이전 버전은 지원되지 않습니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>디바이스 보안

#### <a name="microsoft-edge-baseline-preview----3787164----"></a>Microsoft Edge 기준(미리 보기)<!--  3787164  -->

[Microsoft Edge 설정](../protect/security-baseline-settings-edge.md)에 대한 보안 기준 미리 보기가 추가되었습니다. 

<!-- ########################## -->
## <a name="week-of-october-21-2019-1910-service-release"></a>2019년 10월 21일 주(1910 서비스 릴리스)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="microsoft-365-device-management"></a>Microsoft 365 장치 관리

#### <a name="improved-administration-experience-in-microsoft-365-device-management---5551239---"></a>Microsoft 365 장치 관리의 개선된 관리 환경<!-- 5551239 -->

이제 새롭게 고치고 간소화한 관리 환경을 [https://devicemanagement.microsoft.com](https://devicemanagement.microsoft.com)의 Microsoft 365 장치 관리 전문가 작업 영역에서 흔히 사용할 수 있게 되었으며, 여기에는 다음이 포함됩니다.

- **탐색 업데이트**: 여러 기능을 논리적으로 그룹화하는 간소화된 첫 번째 수준 탐색을 확인할 수 있습니다.
- **새 플랫폼 필터**: 사용자는 디바이스 및 앱 페이지에서 선택된 플랫폼의 정책과 앱만 표시되는 단일 플랫폼을 선택할 수 있습니다.
- **새 홈페이지**: 서비스 상태, 테넌트 상태, 뉴스 등을 홈페이지에서 빠르게 확인할 수 있습니다.

이러한 개선 사항에 대한 자세한 내용은 Microsoft Tech Community 웹 사이트의 [Enterprise Mobility + Security 블로그 게시물](https://go.microsoft.com/fwlink/?linkid=2109094)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="add-mobile-threat-defense-apps-to-unenrolled-devices---3005337---"></a>등록되지 않은 디바이스에 Mobile Threat Defense 앱 추가<!-- 3005337 -->
사용자 회사 데이터를 디바이스 상태에 따라 차단하거나 선택적으로 지울 수 있는 Intune 앱 보호 정책을 만들 수 있습니다. 디바이스의 상태는 사용자가 선택한 MTD(Mobile Threat Defense) 솔루션으로 확인합니다. 이 기능은 현재 Intune 등록 디바이스의 디바이스 정책 준수 설정으로서 존재합니다. 이 새 기능을 통해 Mobile Threat Defense 공급업체의 위협 감지 역량을 미등록 디바이스로도 확장하게 됩니다. Android에서 이 기능을 사용하려면 디바이스에 최신 회사 포털이 있어야 합니다. iOS에서는 앱이 최신 Intune SDK(버전 12.0.15 이상)를 통합하는 경우 이 기능을 사용할 수 있습니다. 첫 번째 앱이 최신 Intune SDK를 채택하는 경우 새로운 기능 항목을 업데이트합니다. 나머지 앱은 롤링 방식으로 사용할 수 있게 됩니다. 자세한 내용은 [Intune을 사용하여 Mobile Threat Defense 앱 보호 정책 만들기](~/protect/mtd-app-protection-policy.md)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="new-device-firmware-configuration-interface-profile-for-windows-10-and-later-devices-public-preview---2266073----"></a>Windows 10 이상 디바이스용 새 디바이스 펌웨어 구성 인터페이스 프로필(공개 미리 보기)<!-- 2266073  -->

Windows 10 이상에서는 디바이스 구성 프로필을 만들어 설정 및 기능을 제어할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Windows 10 이상**). 이 업데이트에는 Intune에서 UEFI(BIOS) 설정을 관리하는 데 사용되는 새 디바이스 펌웨어 구성 인터페이스 프로필 유형이 있습니다.

이 기능에 대한 자세한 내용은 [Microsoft Intune에서 Windows 디바이스의 DFCI 프로필 사용](../configuration/device-firmware-configuration-interface-windows.md)을 참조하세요.

적용 대상:
- 지원되는 펌웨어의 Windows 10 RS5(1809) 이상

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="toggle-to-only-show-enrollment-status-page-on-devices-provisioned-by-out-of-box-experience-oobe--3959566--"></a>OOBE(첫 실행 경험)로 프로비저닝된 디바이스에 등록 상태 페이지만 표시되도록 설정합니다.<!--3959566-->
이제 Autopilot OOBE로 프로비저닝된 디바이스에 등록 상태 페이지만 표시되도록 할 수 있습니다.

새 토글을 확인하려면 **Intune** > **디바이스 등록** > **Windows 등록** > **등록 상태 페이지** > **프로필 만들기** > **설정** > **OOBE(첫 실행 경험)로 프로비저닝된 디바이스에 페이지만 표시**를 선택합니다.


<!-- ########################## -->
## <a name="week-of-october-14-2019"></a>2019년 10월 14일이 있는 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리 

#### <a name="available-google-play-app-reporting-for-android-work-profiles---3041956-----"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고<!-- 3041956   -->
Android Enterprise 회사 프로필, 전용 및 완전 관리형 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태와 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](~/apps/app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](~/enrollment/android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](~/apps/apps-add-android-for-work.md#managed-google-play-app-types)을 참조하세요.

#### <a name="microsoft-edge-version-77-and-later-for-windows-10-and-macos-public-preview---3872025-4678761----"></a>Windows 10 및 macOS용 Microsoft Edge 버전 77 이상(공개 미리 보기)<!-- 3872025, 4678761  -->
Windows 10 및 macOS를 실행하는 PC에 Microsoft Edge 버전 77 이상을 배포할 수 있습니다. 

공개 미리 보기는 Windows 10의 **개발** 및 **베타** 채널과 macOS의 **베타** 채널을 제공합니다. 배포는 영어(EN)로만 가능하지만 최종 사용자가 브라우저의 **설정** > **언어**에서 표시 언어를 변경할 수 있습니다. Microsoft Edge는 시스템 컨텍스트 및 유사한 아키텍처(x86 OS의 x86 앱 및 x64 OS의 x64 앱)에 설치된 Win32 앱입니다. 또한 브라우저의 자동 업데이트는 기본적으로 **켜지고** Microsoft Edge는 제거할 수 없습니다. 자세한 내용은 [Microsoft Intune에 Windows 10용 Microsoft Edge 추가](~/apps/apps-windows-edge.md) 및 [Microsoft Edge 설명서](https://go.microsoft.com/fwlink/?linkid=2103823)를 참조하세요.

#### <a name="update-to-app-protection-ui-and-ios-app-provisioning-ui---4102027-4102029-----"></a>앱 보호 UI 및 iOS 앱 프로비저닝 UI 업데이트<!-- 4102027, 4102029   -->
Intune에서 앱 보호 정책 및 iOS 앱 프로비저닝 프로필을 만들고 편집하는 UI가 업데이트되었습니다. UI 변경 사항에는 다음이 포함됩니다.
- 하나의 블레이드 내에 압축된 마법사 스타일 형식을 사용하여 간소화된 환경 
- 할당을 포함하는 만들기 흐름에 대한 업데이트
- 속성을 볼 때, 새 정책을 만들기 전에 또는 속성을 편집할 때 설정된 모든 항목의 요약된 페이지 또한 속성을 편집할 때 요약에는 편집 중인 속성 범주의 항목 목록만 표시됩니다.

자세한 내용은 [앱 보호 정책을 만들고 할당하는 방법](~/apps/app-protection-policies.md) 및 [iOS 앱 프로비저닝 프로필 사용](~/apps/app-provisioning-profile-ios.md)을 참조하세요.

#### <a name="intune-guided-scenarios---4850318-4831296-3610611----"></a>Intune 단계별 시나리오<!-- 4850318, 4831296, 3610611  -->
이제 intune은 Intune 내에서 특정 작업 또는 작업 세트를 완료하는 데 도움이 되는 단계별 시나리오를 제공합니다. 단계별 시나리오는 하나의 포괄적인 사용 사례를 중심으로 하는 일련의 사용자 지정된 단계(워크플로)입니다. 일반적인 시나리오는 조직에서 관리자, 사용자 또는 디바이스가 수행하는 역할을 기반으로 정의됩니다. 일반적으로 이 워크플로에는 최상의 사용자 환경 및 보안을 제공하기 위해 신중하게 오케스트레이션된 프로필, 설정, 애플리케이션 및 보안 컨트롤 컬렉션이 필요합니다. 새로운 단계별 시나리오는 다음과 같습니다.
- [모바일용 Microsoft Edge 배포](~/fundamentals/guided-scenarios-edge.md)
- [보안 Microsoft Office 모바일 앱](~/fundamentals/guided-scenarios-office-mobile.md) 
- [클라우드 관리 Modern Desktop](~/fundamentals/guided-scenarios-cloud-managed-pc.md)

자세한 내용은 [Intune 단계별 시나리오 개요](guided-scenarios-overview.md)를 참조하세요.

#### <a name="additional-app-configuration-variable-available---4969237-----"></a>사용 가능한 추가 앱 구성 변수<!-- 4969237   -->
앱 구성 정책을 만들 때 구성 설정의 일부로 `AAD Device ID` 구성 변수를 포함할 수 있습니다. Intune에서 **클라이언트 앱** > **앱 구성 정책** > **추가**를 선택합니다. 구성 정책 세부 정보를 입력하고 **구성 설정**을 선택하여 **구성 설정** 블레이드를 표시합니다. 자세한 내용은 [관리형 Android Enterprise 디바이스의 앱 구성 정책 - 구성 디자이너 사용](~/apps/app-configuration-policies-use-android.md#use-the-configuration-designer)을 참조하세요.


#### <a name="create-groups-of-management-objects-called-policy-sets---3762880----"></a>정책 세트라는 관리 개체 그룹 만들기<!-- 3762880  -->
정책 세트를 사용하면 단일 개념 단위로 식별, 대상 지정 및 모니터링해야 하는 기존 관리 엔터티에 대한 참조 번들을 만들 수 있습니다. 정책 세트는 기존 개념 또는 개체를 대체하지 않습니다. Intune에서 개별 개체를 계속 할당할 수 있으며 정책 세트의 일부로 개별 개체를 참조할 수 있습니다. 따라서 해당 개별 개체의 모든 변경 내용이 정책 세트에 반영됩니다.  Intune에서 **정책 설정** > **만들기**를 선택하여 새 정책 세트를 만듭니다. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>디바이스 구성

#### <a name="ui-update-for-creating-and-editing-windows-10-update-rings---4099089-----------"></a>Windows 10 업데이트 링을 만들고 편집하기 위한 UI 업데이트<!-- 4099089         -->
Intune용 [Windows 10 업데이트 링을 만들고 편집](../protect/windows-update-for-business-configure.md#create-and-assign-update-rings)하기 위한 UI 환경을 업데이트했습니다. UI 변경 내용은 다음과 같습니다.  
- 단일 콘솔 블레이드로 압축된 마법사 스타일 형식으로, 이전에 업데이트 링을 구성할 때 표시된 블레이드 확장이 제거됩니다.   
- 수정된 워크플로에는 링의 초기 구성을 완료하기 전 할당이 포함됩니다.
- 새 업데이트 링을 저장하고 배포하기 전에 만든 모든 구성을 검토하는 데 사용할 수 있는 요약 페이지입니다. 업데이트 링을 편집할 때 요약에는 편집한 속성 범주 내에 설정된 항목 목록만 표시됩니다.

#### <a name="ui-update-for-creating-and-editing-ios-software-update-policy---4099090---------"></a>iOS 소프트웨어 업데이트 정책을 만들고 편집하기 위한 UI 업데이트<!-- 4099090       --> 
Intune에 대한 iOS 소프트웨어 업데이트 정책을 [만들고](../protect/software-updates-ios.md#configure-the-policy) [편집](../protect/software-updates-ios.md#edit-a-policy)하기 위한 UI 환경을 업데이트했습니다.  UI 변경 내용은 다음과 같습니다.  
- 단일 콘솔 블레이드로 압축된 마법사 스타일 형식으로, 이전에 업데이트 정책을 구성할 때 표시된 블레이드 확장이 제거됩니다.   
- 수정된 워크플로에는 정책의 초기 구성을 완료하기 전 할당이 포함됩니다.
- 새 정책을 저장하고 배포하기 전에 만든 모든 구성을 검토하는 데 사용할 수 있는 요약 페이지입니다. 정책을 편집할 때 요약에는 편집한 속성 범주 내에 설정된 항목 목록만 표시됩니다.

#### <a name="engaged-restart-settings-are-removed-from-windows-update-rings----4464404---wnready-----"></a>Windows 업데이트 링의 개입형 다시 시작 설정이 제거됨<!--  4464404   WNReady   -->
이전에 발표한 대로, 이제 Intune의 Windows 10 업데이트 링은 [최종 기한 설정을 지원](../protect/windows-update-settings.md)하며 더 이상 ‘개입형 다시 시작’을 지원하지 않습니다.  Intune에서 업데이트 링을 구성하거나 관리하는 경우 ‘개입형 다시 시작’ 설정을 더 이상 사용할 수 없습니다.   

이 변경 내용은 최근 [Windows 서비스 변경 내용](https://docs.microsoft.com//windows/whats-new/whats-new-windows-10-version-1903#servicing)에 맞게 조정되며 Windows 10 1903 이상을 실행하는 디바이스에서는 ‘기한’이 ‘개입형 다시 시작’의 구성을 대체합니다.  

#### <a name="prevent-installation-of-apps-from-unknown-sources-on-android-enterprise-work-profile-devices---4760025-----"></a>Android Enterprise 회사 프로필 디바이스에서 알 수 없는 출처의 앱 설치 방지<!-- 4760025   -->
Android Enterprise 회사 프로필 디바이스에서는 사용자가 알 수 없는 출처의 앱을 설치할 수 없습니다. 이 업데이트에는 **개인 프로필에서 알 수 없는 출처의 앱 설치 방지**라는 새 설정이 있습니다. 기본적으로 이 설정은 사용자가 알 수 없는 출처의 앱을 디바이스의 개인 프로필에 테스트용으로 로드하지 못하도록 합니다.

구성할 수 있는 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상:
- Android Enterprise 회사 프로필

#### <a name="create-a-global-http-proxy-on-android-enterprise-device-owner-devices---4816339-----"></a>Android Enterprise 디바이스 소유자 디바이스에서 전역 HTTP 프록시 만들기<!-- 4816339   -->
Android Enterprise 디바이스에서 조직의 웹 검색 표준을 충족하도록 전역 HTTP 프록시를 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android Enterprise** > **디바이스 소유자 > 프로필 유형의 디바이스 제한** > **연결**). 구성된 후에는 모든 HTTP 트래픽이 이 프록시를 사용합니다.

이 기능을 구성하고 구성하는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상:
- Android Enterprise 디바이스 소유자

#### <a name="connect-automatically-setting-is-removed-in-wi-fi-profiles-on-android-device-administrator-and-android-enterprise---5021055-----"></a>Android 디바이스 관리자 및 Android Enterprise의 Wi-Fi 프로필에서 자동으로 연결 설정이 제거됨<!-- 5021055   -->
Android 디바이스 관리자 및 Android Enterprise 디바이스에서는 Wi-Fi 프로필을 만들어 다양한 설정을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android 디바이스 관리자** 또는 **Android Enterprise** > 프로필 유형용 **Wi-Fi**). 이 업데이트에서 **자동으로 연결** 설정은 [Android에서 지원되지 않으므로](https://developer.android.com/reference/android/net/wifi/WifiManager.html#enableNetwork%28int%2c%20boolean%29) 제거되었습니다. 

Wi-Fi 프로필에서 이 설정을 사용하는 경우 **자동으로 연결**이 작동하지 않는다는 것을 알 수 있습니다. 어떤 작업도 수행할 필요가 없지만 이 설정은 Intune 사용자 인터페이스에서 제거됩니다.

현재 설정을 확인하려면 [Android Wi-Fi 설정](../configuration/wi-fi-settings-android.md) 또는 [Android Enterprise Wi-Fi 설정](../configuration/wi-fi-settings-android-enterprise.md)으로 이동합니다.

적용 대상:
- Android 디바이스 관리자 
- Android Enterprise


#### <a name="new-device-configuration-settings-for-supervised-ios-and-ipados-devices---5199328-----"></a>감독 모드 iOS 및 iPadOS 디바이스의 새 디바이스 구성 설정<!-- 5199328   -->
iOS 및 iPadOS 디바이스에서는 프로필을 만들어 디바이스의 기능 및 설정을 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **iOS/iPadOS** > 프로필 유형별 **디바이스 제한**). 이 업데이트에는 제어할 수 있는 새로운 설정은 다음과 같습니다. 
- Files 앱에서 네트워크 드라이브에 액세스  
- Files 앱에서 USB 드라이브에 액세스 
- Wi-Fi 항상 켜짐 

설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md)으로 이동합니다.

적용 대상:
- iOS 13.0 이상
- iPadOS 13.0 이상

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>디바이스 등록

#### <a name="specify-which-android-device-operating-system-versions-enroll-with-work-profile-or-device-administrator-enrollment---4350697-----"></a>회사 프로필 또는 디바이스 관리자 등록에 등록되는 Android 디바이스 운영 체제 버전 지정<!-- 4350697   -->
Intune 디바이스 유형 제한을 사용하면 디바이스의 OS 버전을 사용하여 Android Enterprise 회사 프로필 등록 또는 Android 디바이스 관리자 등록을 사용할 사용자 디바이스를 지정할 수 있습니다.  자세한 내용은 [등록 제한 설정](../enrollment/enrollment-restrictions-set.md)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="new-restrictions-for-renaming-windows-devices---3478938----"></a>Windows 디바이스 이름 바꾸기에 대한 새로운 제한<!-- 3478938  -->
Windows 디바이스 이름을 바꾸는 경우 새 규칙을 따라야 합니다.
- 15자 이하(63바이트보다 작거나 같아야 함, 후행 NULL을 포함하지 않음)
- null 또는 빈 문자열이 아님
- 허용된 ASCII: 문자(a-z, A-Z), 숫자(0-9) 및 하이픈
- 허용된 유니코드: 문자 >= 0x80, 유효한 UTF8이어야 함, IDN 매핑 가능해야 함(RtlIdnToNameprepUnicode가 성공함, RFC 3492 참조)
- 이름에 숫자만 포함할 수는 없음
- 이름에 공백이 없음
- 허용되지 않는 문자: { | } ~ [ \ ] ^ ' : ; < = > ? & @ ! " # $ % ` ( ) + / , . _ *)

 자세한 내용은 [Intune에서 디바이스 이름 바꾸기](../remote-actions/device-rename.md)를 참조하세요.

### <a name="new-android-report-on-devices-overview-page---4924364---"></a>디바이스 개요 페이지의 새 Android 보고서<!-- 4924364 -->
디바이스 개요 페이지에 대한 새 보고서에는 각 장치 관리 솔루션에 등록된 Android 디바이스 수가 표시됩니다. 이 차트에는 회사 프로필, 완전 관리형, 전용 및 디바이스 관리자 등록 디바이스 수가 표시됩니다. 보고서를 보려면 **Intune** > **디바이스** > **개요**를 선택합니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>디바이스 보안

#### <a name="pkcs-certificates-for-macos---1333650---------"></a>macOS의 PKCS 인증서<!-- 1333650       -->
이제 [macOS에서 PKCS 인증서를 사용](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile)할 수 있습니다. macOS의 프로필 유형으로 PKCS 인증서를 선택하고 [사용자 지정된 주체 및 주체 대체 이름 필드](../protect/certficates-pfx-configure.md#subject-name-format-for-macos)가 있는 사용자 및 디바이스 인증서를 배포할 수 있습니다.  

도한 macOS용 PKCS 인증서는 새로운 설정인 _모든 앱 액세스 허용_을 지원합니다. 이 설정을 사용하면 연결된 모든 앱이 인증서의 프라이빗 키에 액세스하도록 설정할 수 있습니다.  이 설정에 대한 자세한 내용은 https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf 에서 Apple 설명서를 참조하세요.

####   <a name="derived-credentials-to-provision-ios-mobile-devices-with-certificates----1736036-1736037-1772050-2777333-----------"></a>인증서를 사용하여 iOS 모바일 디바이스를 프로비저닝하기 위한 파생 자격 증명<!--  1736036, 1736037, 1772050, 2777333         -->  
Intune에서는 iOS 디바이스의 S/MIME 서명 및 암호화를 위해 인증 방법으로 [파생 자격 증명](../protect/derived-credentials.md) 사용을 지원합니다. 파생 자격 증명은 디바이스에 인증서를 배포하기 위한 *NIST(National Institute of Standards and Technology) 800-157* 표준의 구현입니다.  

파생 자격 증명은 스마트 카드와 같은 PIV(Personal Identity Verification) 또는 CAC(Common Access Card) 카드의 사용을 기반으로 합니다. 모바일 디바이스의 파생 자격 증명을 가져오기 위해 사용자는 회사 포털 앱에서 시작하고 사용하는 공급자에 고유한 등록 워크플로를 따릅니다.  컴퓨터에서 스마트 카드를 사용하여 파생 자격 증명 공급자를 인증하는 것은 모든 공급자에 공통적인 요구 사항입니다. 해당 공급자는 사용자의 스마트 카드에서 파생된 디바이스에 대한 인증서를 발급합니다.  

Intune에서 지원하는 파생 자격 증명 공급자는 다음과 같습니다.
- DISA Purebred
- Entrust Datacard
- Intercede

VPN, Wi-Fi 및 메일에 대한 디바이스 구성 프로필의 인증 방법으로 파생 자격 증명을 사용합니다. 앱 인증과 S/MIME 서명 및 암호화에도 사용할 수 있습니다.  

표준에 대한 자세한 내용은 www.nccoe.nist.gov에서 [Derived PIV Credentials](https://www.nccoe.nist.gov/projects/building-blocks/piv-credentials)(파생된 PIV 자격 증명)를 참조하세요.

#### <a name="use-graph-api-to-specify-a-on-premises-user-principal-name-as-a-variable-for-scep-certificates----5437939----------"></a>Graph API를 사용하여 온-프레미스 사용자 계정 이름을 SCEP 인증서의 변수로 지정합니다.<!--  5437939        -->  
[Intune Graph API](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)를 사용하는 경우 SCEP 인증서의 SAN(주체 대체 이름)에 대한 변수로 onPremisesUserPrincipalName을 지정할 수 있습니다.



<!-- ########################## -->

## <a name="week-of-september-23-2019"></a>2019년 9월 23일이 있는 주

#### <a name="ios-user-enrollment-in-preview---4817900---"></a>iOS 사용자 등록 미리 보기<!-- 4817900 -->
Apple의 iOS 13.1 릴리스에는 iOS 디바이스를 위한 새롭고 가벼운 관리 형태인 사용자 등록이 포함됩니다. 개인적으로 소유하는 디바이스에서 디바이스 등록 또는 자동 디바이스 등록(이전의 장비 등록 프로그램) 대신 사용자 등록을 사용할 수 있습니다. Intune의 미리 보기는 다음을 허용하여 이 기능 집합을 지원합니다.

- 사용자 등록의 대상을 사용자 그룹으로 지정합니다.
- 최종 사용자가 디바이스를 등록할 때 더 가벼운 사용자 등록과 더 강력한 디바이스 등록 중에서 선택할 수 있는 기능을 제공합니다.

iOS 13.1이 릴리스되는 2019년 9월 24일부터 모든 고객에게 이러한 업데이트를 롤아웃하고 있으며, 다음주 말까지 이러한 과정이 완료될 것으로 예상합니다.
적용 대상:

iOS 13.1 이상

#### <a name="intune-support-for-ipados-and-ios-131-devices--5439574--"></a>iPadOS 및 iOS 13.1 디바이스에 대한 Intune 지원<!--5439574-->
Intune은 이제 iPadOS 및 iOS 13.1 디바이스 관리를 지원합니다. 자세한 내용은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-1-and-iPadOS/ba-p/873094)을 참조하세요.

<!-- ########################## -->

## <a name="week-of-september-16-2019-1909-service-release"></a>2019년 9월 16일 주(1909 서비스 릴리스)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리 

#### <a name="managed-google-play-private-lob-apps---1464182----"></a>관리형 Google Play 프라이빗 LOB 앱<!-- 1464182  -->
이제 intune을 통해 IT 관리자는 Intune 콘솔에 포함된 iframe을 통해 프라이빗 Android LOB 앱을 관리형 Google Play에 게시할 수 있습니다.  이전에는 IT 관리자가 여러 단계가 필요하고 시간이 많이 소요되는 Google Play 게시 콘솔에 직접 LOB 앱을 게시해야 했습니다. 이 새로운 기능을 사용하면 Intune 콘솔을 벗어날 필요 없이 최소한의 단계를 사용하여 LOB 앱을 쉽게 게시할 수 있습니다.  관리자는 Google을 사용하여 더 이상 수동으로 개발자로 등록하지 않아도 되며 Google의 $25 등록 요금을 지불할 필요가 없습니다.  관리형 Google Play를 사용하는 Android Enterprise 관리 시나리오는 이 기능(회사 프로필, 전용, 완전 관리형 및 등록되지 않은 디바이스)을 활용할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 유형** 목록에서 **관리형 Google Play**를 선택합니다. 관리형 Google Play 앱에 대한 자세한 내용은 [Intune을 사용하여 Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 추가](../apps/apps-add-android-for-work.md)를 참조하세요.

#### <a name="windows-company-portal-experience---1473353-3598357---"></a>Windows 회사 포털 환경<!-- 1473353, 3598357 -->
Windows 회사 포털을 업데이트하고 있습니다. Windows 회사 포털 내의 앱 페이지에서 여러 필터를 사용할 수 있습니다. 또한 향상된 사용자 환경으로 장치 세부 정보 페이지를 업데이트하고 있습니다. Microsoft는 모든 고객에게 이러한 업데이트를 롤아웃하고 있으며, 다음 주 말이면 이러한 과정이 완료된 것으로 예상합니다.

#### <a name="macos-support-for-web-apps---3174427---"></a>웹 앱에 대한 macOS 지원<!-- 3174427 -->
웹에서 URL에 바로 가기를 추가할 수 있는 웹 앱을 macOS 회사 포털을 이용해 독에 설치할 수 있습니다. 최종 사용자는 macos 회사 포털에서 웹 앱의 앱 세부정보 페이지로 이동하면 **설치** 작업을 이용할 수 있습니다. **웹 링크** 앱 유형에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](../apps/apps-add.md)와 [Microsoft Intune에 웹앱 추가](../apps/web-app.md)를 참조하세요.

#### <a name="macos-support-for-vpp-apps---3173501----"></a>VPP 앱에 대한 macOS 지원<!-- 3173501  -->
Apple Business Manager로 구매한 macOS 앱은 이후 Apple VPP 토큰이 동기화되면 콘솔에 표시됩니다. Intune 콘솔을 이용해 그룹용 디바이스 및 사용자 기반 라이선스를 할당, 취소, 재할당할 수 있습니다. Microsoft Intune을 이용하면 회사에서 사용할 목적으로 구매한 VPP 앱을 다음 기능을 이용해 관리할 수 있습니다.

- 앱 스토어에서 라이선스 정보 보고.
- 사용한 라이선스 수 추적.
- 소유한 양보다 많은 앱 복사본을 설치하지 않도록 방지.

Intune 및 VPP에 대한 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 앱 및 전자책 관리](../apps/vpp-apps.md)를 참조하세요.

#### <a name="managed-google-play-iframe-support---2871756----"></a>관리형 Google Play iframe 지원<!-- 2871756  -->
이제 intune은 관리형 Google Play iframe을 통해 Intune 콘솔에서 직접 웹 링크를 추가 및 관리할 수 있도록 지원합니다.  이를 통해 IT 관리자는 URL 및 아이콘 그래픽을 제출한 다음, 일반 Android 앱과 마찬가지로 해당 링크를 디바이스에 배포할 수 있습니다. 관리형 Google Play를 사용하는 Android Enterprise 관리 시나리오는 이 기능(회사 프로필, 전용, 완전 관리형 및 등록되지 않은 디바이스)을 활용할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 유형** 목록에서 **관리형 Google Play**를 선택합니다. 관리형 Google Play 앱에 대한 자세한 내용은 [Intune을 사용하여 Android 엔터프라이즈 디바이스에 관리되는 Google Play 앱 추가](../apps/apps-add-android-for-work.md)를 참조하세요.

#### <a name="silently-install-android-lob-apps-on-zebra-devices---4252734----"></a>Zebra 디바이스에 Android LOB 앱 자동 설치<!-- 4252734  -->
[Zebra 디바이스](../configuration/android-zebra-mx-overview.md)에 Android LOB(기간 업무) 앱을 설치할 경우 LOB(기간 업무) 앱을 다운로드하고 설치하라는 메시지가 표시되지 않고, 앱을 자동으로 설치할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 추가** 창에서 **기간 업무 앱**을 선택합니다. 자세한 내용은 [Microsoft Intune에 Android 기간 업무 앱 추가](../apps/lob-apps-android.md)를 참조하세요.

현재 LOB 앱을 다운로드한 후에는 **다운로드 성공** 알림이 사용자의 디바이스에 표시됩니다. 알림 음영에서 **모두 지우기**를 눌러야만 알림을 해제할 수 있습니다. 이 알림 문제는 예정된 릴리스에서 수정될 예정이며, 설치는 시각적 표시기 없이 완전히 자동으로 수행됩니다.

#### <a name="read-and-write-graph-api-operations-for-intune-apps---5031704----"></a>Intune 앱에 대한 읽기 및 쓰기 Graph API 작업<!-- 5031704  -->
애플리케이션이 사용자 자격 증명 없이 앱 ID를 사용하는 읽기 및 쓰기 작업에서 Intune Graph API를 호출할 수 있습니다. Intune에 대해 Microsoft Graph API를 액세스하는 방법에 대한 자세한 내용은 [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)(Microsoft Graph에서 Intune 사용)를 참조하세요.

#### <a name="protected-data-sharing-and-encryption-for-intune-app-sdk-for-ios---3586942----"></a>iOS용 Intune 앱 SDK에 대한 보호된 데이터 공유 및 암호화<!-- 3586942  -->
iOS용 Intune 앱 SDK는 앱 보호 정책에서 암호화를 사용하도록 설정할 때 256비트 암호화 키를 사용합니다. 모든 앱에는 보호된 데이터 공유를 허용하기 위해 SDK 버전 8.1.1이 있어야 합니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>디바이스 구성

#### <a name="support-for-ikev2-vpn-profiles-for-ios---1943438-----"></a>iOS용 IKEv2 VPN 프로필 지원<!-- 1943438   -->
이 업데이트에서 IKEv2 프로토콜을 사용하여 iOS 원시 VPN 클라이언트에 대한 VPN 프로필을 만들 수 있습니다. IKEv2는 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **VPN**(프로필 형식) > **연결 유형**의 새 연결 형식입니다.

이러한 VPN 프로필은 네이티브 VPN 클라이언트를 구성하므로, VPN 클라이언트 앱이 관리되는 디바이스에 설치되거나 푸시되지 않습니다. 이 기능을 사용하려면 디바이스를 Intune에 등록해야 합니다(MDM 등록).

구성할 수 있는 최신 VPN 설정은 [iOS 디바이스에서 VPN 설정 구성](../configuration/vpn-settings-ios.md)을 참조하세요.

적용 대상:
- iOS

#### <a name="device-features-device-restrictions-and-extension-profiles-for-ios-and-macos-settings-are-shown-by-enrollment-type---4886161-----"></a>iOS 및 macOS 설정에 대한 디바이스 기능, 디바이스 제한 및 확장 프로필은 등록 형식으로 표시됩니다.<!-- 4886161   -->

Intune에서 iOS 및 macOS 디바이스의 프로필을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 또는 **macOS**(플랫폼) > **디바이스 기능**, **디바이스 제한** 또는 **확장**(프로필 유형)]. 

이 업데이트에서 Intune 포털의 사용 가능한 설정은 적용되는 등록 유형별로 분류됩니다.

- iOS
  - 사용자 등록
  - 디바이스 등록
  - 자동 디바이스 등록(감독됨)
  - 모든 등록 유형

- macOS
  - 사용자 승인
  - 디바이스 등록
  - 자동 디바이스 등록
  - 모든 등록 유형

적용 대상:
- iOS

#### <a name="new-voice-control-settings-for-supervised-ios-devices-running-in-kiosk-mode---4892835-----"></a>키오스크 모드에서 실행되는 감독된 iOS 디바이스에 대한 새 음성 제어 설정<!-- 4892835   -->
Intune에서 감독된 iOS 디바이스를 키오스크 또는 전용 디바이스로 실행하는 정책을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 유형) > **키오스크**].

이 업데이트에는 제어할 수 있는 새로운 설정은 다음과 같습니다.
- **음성 제어**: 키오스크 모드에서 디바이스에 대한 음성 제어를 사용하도록 설정합니다.
- **음성 제어 수정**: 사용자가 키오스크 모드의 디바이스에서 음성 제어 설정을 변경할 수 있도록 허용합니다.

현재 설정을 보려면 [iOS 키오스크 설정](../configuration/device-restrictions-ios.md#kiosk)으로 이동합니다.

적용 대상:
- iOS 13.0 이상

#### <a name="use-single-sign-on-for-apps-and-websites-on-your-ios-and-macos-devices---4893175-----"></a>iOS 및 macOS 디바이스에서 앱 및 웹 사이트에 Single Sign-On 사용<!-- 4893175   -->
이 업데이트에는 iOS 및 macOS 디바이스에 대한 몇 가지 새 Single Sign-On 설정이 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 또는 **macOS**(플랫폼) > **디바이스 기능**(프로필 유형)].

이러한 설정을 사용하여 특히 Kerberos 인증을 사용하는 앱 및 웹 사이트에 대해 Single Sign-On 환경을 구성할 수 있습니다. 일반 자격 증명 Single Sign-On 앱 확장 및 Apple의 기본 제공 Kerberos 확장 중에서 선택할 수 있습니다.

구성할 수 있는 현재 디바이스 기능을 보려면 [iOS 디바이스 기능](../configuration/ios-device-features-settings.md) 및 [macOS 디바이스 기능](../configuration/macos-device-features-settings.md)으로 이동합니다.

적용 대상:
- iOS 13.0 이상
- macOS 10.15 이상

#### <a name="associate-domains-to-apps-on-macos-1015-devices---4898079-----"></a>macOS 10.15+ 디바이스에서 앱에 도메인 연결<!-- 4898079   -->
macOS 디바이스에서 여러 다양한 기능을 구성하고, 정책을 사용하여 이러한 기능을 디바이스에 푸시할 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **macOS**(플랫폼) > **디바이스 기능**(프로필 유형)]. 이 업데이트에서는 앱에 도메인을 연결할 수 있습니다. 이 기능은 앱과 관련된 웹 사이트와 자격 증명을 공유하는 데 도움이 되며 Apple의 Single Sign-On 확장, 유니버설 링크 및 암호 자동 채우기와 함께 사용할 수 있습니다. 

구성할 수 있는 최신 기능을 보려면 Intune의 [macOS 디바이스 기능 설정](../configuration/macos-device-features-settings.md)으로 이동하세요.

적용 대상:
- macOS 10.15 이상

#### <a name="use-itunes-and-apps-in-the-itunes-app-store-url-when-showing-or-hiding-apps-on-ios-supervised-devices---4928474-----"></a>iOS 감독 디바이스에서 앱을 표시하거나 숨길 때 iTunes App Store URL에서 "iTunes" 및 "앱"을 사용합니다.<!-- 4928474   --> 
Intune에서 감독된 iOS 디바이스의 앱을 표시하거나 숨기는 정책을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 유형) > **앱 표시 또는 숨기기**]. 

iTunes App Store URL(예: `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`)을 입력할 수 있습니다. 이 업데이트에서는 `apps` 및 `itunes` 둘 다를 URL에서 사용할 수 있습니다. 예를 들면 다음과 같습니다.
- `https://itunes.apple.com/us/app/work-folders/id950878067?mt=8`
- `https://apps.apple.com/us/app/work-folders/id950878067?mt=8`

이러한 설정에 대한 자세한 내용은 [앱 표시 또는 숨기기](../configuration/device-restrictions-ios.md#show-or-hide-apps)를 참조하세요.

적용 대상:
- iOS

#### <a name="windows-10-compliance-policy-password-type-values-are-clearer-and-match-csp---5138985---"></a>Windows 10 규정 준수 정책 암호 유형 값이 좀 더 명확하고 CSP와 일치합니다.<!-- 5138985 -->
Windows 10 디바이스에서 특정 암호 기능을 요구 하는 규정 준수 정책을 만들 수 있습니다[**디바이스 준수** > **정책** > **정책 만들기** > **Windows 10 이상**(플랫폼) > **시스템 보안**]. 이 업데이트에는 다음이 적용됩니다.
- **암호 유형** 값은 보다 명확하며 [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)와 일치하도록 업데이트됩니다.
- 1-730일의 값을 허용하도록 **암호 만료(일)** 설정이 업데이트됩니다. 

Windows 10 준수 설정에 대한 자세한 내용은 [디바이스를 규격 또는 비규격으로 표시하는 Windows 10 이상 설정](../protect/compliance-policy-create-windows.md)을 참조하세요. 

적용 대상:
- Windows 10 이상

 #### <a name="updated-ui-for-configuring-microsoft-exchange-on-premises-access---4092920---"></a>Microsoft Exchange 온-프레미스 액세스를 구성하기 위한 UI가 업데이트됨<!-- 4092920 -->  
[Microsoft Exchange 온-프레미스 액세스를 구성](../protect/conditional-access-exchange-create.md)하는 콘솔을 업데이트했습니다. Exchange 온-프레미스 액세스의 모든 구성은 이제 *Exchange 온-프레미스 액세스 제어를 사용하도록 설정*하는 콘솔의 동일한 창에서 사용할 수 있습니다.  

#### <a name="allow-or-restrict-adding-app-widgets-to-the-home-screen-on-android-enterprise-work-profile-devices---1109650----"></a>Android Enterprise 회사 프로필 디바이스에서 홈 화면에 대한 앱 위젯 추가 허용 또는 제한<!-- 1109650  --> 
Android Enterprise 디바이스에서 회사 프로필의 기능을 구성할 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **Android Enterprise**(플랫폼) > **회사 프로필만 > 디바이스 제한**(프로필 유형)]. 이 업데이트에서는 사용자가 회사 프로필 앱에서 제공하는 위젯을 디바이스 홈 화면에 추가할 수 있습니다.

구성할 수 있는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상:
- Android Enterprise 회사 프로필

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>디바이스 등록

#### <a name="new-tenants-will-default-away-from-android-device-administrator-management---4869790-----"></a>Android 디바이스 관리자 관리에서 새 테넌트가 기본적으로 표시되지 않습니다.<!-- 4869790   -->
Android의 디바이스 관리자 기능은 Android Enterprise로 대체되었습니다. 따라서 새로운 등록을 위해서는 Android Enterprise를 대신 사용하는 것이 좋습니다. 이후 업데이트에서는 디바이스 관리자 관리를 사용하기 위해서는 새 테넌트가 Android 등록의 다음 필수 단계를 완료해야 합니다. **Intune** > **디바이스 등록** > **Android 등록** > **디바이스 관리 권한이 있는 개인 및 회사 소유 디바이스** > **디바이스 관리자를 사용하여 디바이스를 관리합니다.** 로 이동합니다.

작업 환경의 기존 테넌트는 변경되지 않습니다.

Intune의 Android 디바이스 관리자에 대한 자세한 내용은 [Android 디바이스 관리자 등록](https://docs.microsoft.com/intune/android-enroll-device-administrator)을 참조하세요.

#### <a name="list-of-dep-devices-associated-with-a-profile---5012045-idmiss---"></a>프로필과 연결된 DEP 디바이스 목록<!-- 5012045 idmiss -->
이제 프로필에 연결된 Apple 자동 DEP(디바이스 등록 프로그램) 디바이스의 페이지 구분 목록을 볼 수 있습니다. 목록의 모든 페이지에서 목록을 검색할 수 있습니다. 이 목록을 보려면 **Intune** > **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 토큰 > **프로필**을 선택한 후 프로필 > **할당된 디바이스**(**모니터** 아래)를 선택합니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="more-android-fully-managed-support---3464667-4631425-4631440-5227935-4062195-----"></a>추가 Android 완전 관리형 지원<!-- 3464667, 4631425, 4631440, 5227935, 4062195   -->
Android 완전 관리형 디바이스에 대해 다음 지원을 추가했습니다.

- 디바이스 소유자로 관리되는 디바이스의 인증서 인증을 위해 완전 관리형 Android용 SCEP 인증서를 사용할 수 있습니다. SCEP 인증서는 회사 프로필 디바이스에서 이미 지원됩니다.  디바이스 소유자용 SCEP 인증서를 사용하여 다음을 수행할 수 있습니다. <!-- 5227935 -->
    - Android Enterprise의 DO 섹션에서 SCEP 프로필 만들기
    - 인증을 위해 DO Wi-Fi 프로필에 SCEP 인증서 연결
    - 인증을 위해 DO VPN 프로필에 SCEP 인증서 연결
    - 인증을 위해 DO 메일 프로필에 SCEP 인증서 연결(AppConfig를 통해)
- Android Enterprise 디바이스에서 시스템 앱이 지원됩니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택하여 Android Enterprise 시스템 앱을 추가합니다. **앱 유형** 목록에서 **Android Enterprise 시스템 앱**을 선택합니다. 자세한 내용은 [Microsoft Intune에 Android Enterprise 시스템 앱 추가](../apps/apps-ae-system.md)를 참조하세요. <!-- 4062195 -->
- **디바이스 준수** > **Android Enterprise** > **디바이스 소유자**에서 Google SafetyNet 증명 수준을 설정하는 규정 준수 정책을 만들 수 있습니다.   <!-- 4631425 -->
- Android Enterprise 완전 관리형 디바이스에서 모바일 위협 방어 공급자가 지원됩니다. **디바이스 준수** > **Android Enterprise** > **디바이스 소유자**에서 허용되는 위협 수준을 선택할 수 있습니다. <!-- 4631440 --> [Intune을 사용하여 디바이스를 규격 또는 비규격으로 표시하는 Android 엔터프라이즈 설정](../protect/compliance-policy-create-android-for-work.md#device-owner)은 현재 설정을 나열합니다.
- Android Enterprise 완전 관리형 디바이스에서 이제 앱 구성 정책을 통해 Microsoft 시작 관리자 앱이 완전 관리형 디바이스에서 표준화된 최종 사용자 환경을 허용하도록 구성할 수 있습니다. Microsoft 시작 관리자 앱을 사용하여 Android 디바이스를 맞춤형으로 조정할 수 있습니다. Microsoft 계정 또는 회사/학교 계정에서 해당 앱을 사용하여 맞춤형 피드에서 일정, 문서 및 최근 활동에 액세스할 수 있습니다. <!-- 5334044 -->

이 업데이트를 통해 Android Enterprise 완전 관리형에 대한 Intune 지원이 이제 일반 공급됩니다.

적용 대상:

- Android Enterprise 완전 관리형 디바이스

#### <a name="send-custom-notifications-to-a-single-device---4928910---"></a>단일 디바이스로 사용자 지정 알림 보내기<!-- 4928910 -->
이제 단일 디바이스를 선택한 후 원격 디바이스 작업을 사용하여 [해당 디바이스로만 사용자 지정 알림을 보낼 수 있습니다](../remote-actions/custom-notifications.md#send-a-custom-notification-to-a-single-device).

#### <a name="wipe-and-passcode-reset-actions-arent-available-for-ios-devices-that-are-enrolled-by-using-user-enrollment---4950491---"></a>초기화 및 암호 재설정 작업은 사용자 등록을 사용하여 등록된 iOS 디바이스에서 사용할 수 없습니다.<!-- 4950491 -->
사용자 등록은 새로운 유형의 Apple 디바이스 등록입니다. 사용자 등록을 사용하여 디바이스를 등록하는 경우 이러한 디바이스에 대해 초기화 및 암호 재설정 원격 작업을 사용할 수 없습니다.

#### <a name="intune-support-for-ios-13-and-macos-catalina-devices---4665317---"></a>iOS 13 및 macOS Catalina 디바이스에 대한 Intune 지원<!-- 4665317 -->
Intune은 이제 iOS 13 및 macOS Catalina 디바이스를 둘 다 관리하도록 지원합니다.
자세한 내용은 [iOS 13 및 iPadOS에 대한 Microsoft Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Support-for-iOS-13-and-iPadOS/ba-p/861998)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>디바이스 보안

#### <a name="bitlocker-support-for-client-driven-recovery-password-rotation----3444125---"></a>클라이언트 기반 복구 암호 순환에 대한 BitLocker 지원<!--  3444125 -->
Intune Endpoint Protection 설정을 사용하여 Windows 버전 1909 이상을 실행하는 디바이스에서 BitLocker에 대해 [클라이언트 기반 복구 암호 순환](../protect/endpoint-protection-windows-10.md#windows-encryption)을 구성할 수 있습니다.

이 설정은 고정 데이터 드라이브에서 OS 드라이브 복구(bootmgr 또는 WinRE를 사용하여) 및 복구 암호를 잠금 해제 후 클라이언트 기반 복구 암호 새로 고침을 시작합니다. 이 설정은 사용된 특정 복구 암호를 새로 고치며, 볼륨에서 사용되지 않은 다른 암호는 변경되지 않은 상태로 유지됩니다. 자세한 내용은[ConfigureRecoveryPasswordRotation](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)에 대한 BitLocker CSP 설명서를 참조하세요.

#### <a name="tamper-protection-for-windows-defender-antivirus---4705448----------"></a>Windows Defender 바이러스 백신에 대한 변조 보호<!-- 4705448        -->
Intune을 사용하여 Windows Defender 바이러스 백신의 *변조 보호*를 관리합니다. Windows 10 엔드포인트 보호를 위해 디바이스 구성 프로필을 사용하는 경우 Microsoft Defender Security Center 그룹에서 [변조 보호 설정](../protect/endpoint-protection-windows-10.md#microsoft-defender-security-center)을 찾을 수 있습니다. 변조 보호 제한을 켜려면 변조 보호를 *사용*으로 설정하고, 끄려면 *사용 안 함*으로 설정하고, 디바이스를 현재 구성 상태로 두려면 *구성되지 않음*으로 설정합니다.  

변조 보호에 대한 자세한 내용은 Windows 설명서에서 [ 변조 보호를 사용하여 보안 설정 변경 방지](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/prevent-changes-to-security-settings-with-tamper-protection)를 참조하세요.

#### <a name="advanced-settings-for-windows-defender-firewall-are-now-generally-available----5317392---------"></a>Windows Defender 방화벽의 고급 설정이 이제 일반 공급됨<!--  5317392       -->  
디바이스 구성 프로필의 일부로 구성하는 [엔드포인트 보호를 위한 Windows Defender 사용자 지정 방화벽 규칙](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)이 퍼블릭 미리 보기로 제공되지 않으며 GA(일반 공급) 상태입니다.  이러한 규칙을 사용하여 애플리케이션, 네트워크 주소 및 포트에 대한 인바운드 및 아웃바운드 동작을 지정할 수 있습니다. 이러한 규칙은 7월에 퍼블릭 미리 보기로 출시되었습니다. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-now-support-terms-of-use-policies---2358863-idmiss---"></a>이제 범위 태그가 사용 약관 정책을 지원함<!-- 2358863 idmiss -->
이제 사용 정책 약관에 [범위 태그](scope-tags.md)를 할당할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스 등록** > **사용 약관**으로 이동하고 목록에서 항목을 선택한 후 **속성** > **범위 태그**로 이동한 후 범위 태그를 선택합니다.

## <a name="week-of-september-9-2019"></a>2019년 9월 9일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="updates-to-microsoft-intune-app---4997846---"></a>Microsoft Intune 앱 업데이트<!-- 4997846 -->
Android용 Microsoft Intune 앱이 다음과 같은 향상된 기능으로 업데이트되었습니다.
- 가장 중요한 작업으로 이동할 수 있는 아래쪽 탐색 창을 포함하도록 레이아웃을 업데이트하고 개선했습니다.
- 사용자의 프로필을 표시하는 추가 페이지를 추가했습니다.
- 사용자를 위해 디바이스 설정 업데이트 필요를 알리는 등의 실행 가능한 알림의 표시를 앱에 추가했습니다.
- iOS 및 Android용 회사 포털 앱에 최근 추가된 지원 기능에 따라 앱에 사용자 지정 푸시 알림의 표시를 추가했습니다. 자세한 내용은 [Intune에서 사용자 지정 알림 보내기](../remote-actions/custom-notifications.md)를 참조하세요.

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal---4394993---"></a>IOS 디바이스에서 회사 포털의 등록 프로세스 개인 정보 화면을 사용자 지정합니다<!-- 4394993 -->
Markdown을 이용하면 iOS 등록 과정에서 최종 사용자에게 표시되는 회사 포털의 개인 정보 화면을 사용자 지정할 수 있습니다. 특히 조직이 디바이스에서 볼 수 없거나 해선 안 되는 항목 목록을 사용자 지정할 수 있습니다. 자세한 내용은 [Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md#privacy-statement-customization)을 참조하세요.


## <a name="week-of-september-2-2019"></a>2019년 9월 2일이 있는 주

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="intune-user-interface-update--tenant-status-dashboard---5273210----"></a>Intune 사용자 인터페이스 업데이트 - 테넌트 상태 대시보드<!-- 5273210  -->
테넌트 상태 대시보드의 사용자 인터페이스가 Azure 사용자 인터페이스 스타일에 맞게 업데이트되었습니다. 자세한 내용은 [테넌트 상태](../tenant-status.md)를 참조하세요.

## <a name="week-of-august-26-2019"></a>2019년 8월 26일 주

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer---5228061---"></a>Windows 10 이상에 대해 관리 템플릿을 사용하여 Microsoft Edge 설정 구성<!-- 5228061 -->

Windows 10 이상 디바이스에서는 Intune에서 그룹 정책 설정을 구성하는 관리 템플릿을 만들 수 있습니다. 이 업데이트에서는 Microsoft Edge 버전 77 이상에 적용되는 설정을 구성할 수 있습니다.

관리 템플릿에 대한 자세한 내용은 [Windows 10 템플릿을 사용하여 Intune에서 그룹 정책 설정 구성](../configuration/administrative-templates-windows.md)을 참조하세요.

적용 대상:

- Windows 10 이상(Windows RS4 이상)

## <a name="week-of-august-12-2019-1908-service-release"></a>2019년 8월 12일 주(1908 서비스 릴리스)

### <a name="app-management"></a>앱 관리

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment---3504144-----"></a>디바이스 등록 취소에서 iOS 앱 제거 동작 제어<!-- 3504144   -->
관리자는 디바이스가 사용자 또는 디바이스 그룹 수준에서 등록 취소될 때 디바이스에서 앱을 제거할지 유지할지를 관리할 수 있습니다. 

#### <a name="categorize-microsoft-store-for-business-apps---3926922---"></a>비즈니스용 Microsoft Store 앱 범주화<!-- 3926922 -->
비즈니스용 Microsoft Store 앱을 범주화할 수 있습니다. 이렇게 하려면 **Intune** > **클라이언트 앱** > **앱** > 비즈니스용 Microsoft Store 앱 선택 > **앱 정보** > **범주**를 선택합니다. 드롭다운 메뉴에서 범주를 할당합니다.

#### <a name="customized-notifications-for-microsoft-intune-app-users---4843354----"></a>Microsoft Intune 앱 사용자에 맞게 사용자 지정된 알림<!-- 4843354  -->
이제 Android용 Microsoft Intune 앱은 사용자 지정 푸시 알림의 표시를 지원하여 iOS 및 Android용 회사 포털 앱에 최근에 추가된 지원에 맞춰 정렬합니다. 자세한 내용은 [Intune에서 사용자 지정 알림 보내기](../remote-actions/custom-notifications.md)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode---3755304-3041943-3041946-----"></a>다중 앱 모드에서 Android 엔터프라이즈 전용 디바이스의 새로운 기능<!-- 3755304 3041943 3041946   -->

Intune에서는 Android 엔터프라이즈 전용 디바이스의 키오스크 스타일 환경에서 기능 및 설정을 제어할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **디바이스 소유자만, 디바이스 제한**(프로필 유형)).

이 업데이트에서는 다음과 같은 기능이 추가됩니다.

- **전용 디바이스** > **다중 앱**: **가상 홈 단추**는 디바이스에서 위로 살짝 밀거나 화면에서 부동 처리하여 표시하면 사용자가 이동할 수 있습니다.
- **전용 디바이스** > **다중 앱**: **손전등 액세스**를 통해 사용자는 손전등을 사용할 수 있습니다. 
- **전용 디바이스** > **다중 앱**: **미디어 볼륨 컨트롤**을 통해 사용자는 슬라이더를 사용하여 디바이스의 미디어 볼륨을 제어할 수 있습니다. 
- **전용 디바이스** > **다중 앱**:  **화면 보호기를 사용**하도록 설정하고, 사용자 지정 이미지를 업로드하고, 화면 보호기 표시 시기를 제어합니다.

현재 설정 목록을 보려면 Intune에서 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md#dedicated-device-settings)으로 이동합니다.

적용 대상:

- Android 엔터프라이즈 전용 디바이스

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices---3574215-3574238-3574235-3574232-----"></a>Android 엔터프라이즈 완전 관리형 디바이스에 대한 새 앱 및 구성 프로필<!-- 3574215 3574238 3574235 3574232   -->
프로필을 사용하여 Android 엔터프라이즈 디바이스 소유자(완전 관리형) 디바이스에 VPN, 메일 및 Wi-Fi 설정을 적용하는 설정을 구성할 수 있습니다. 이 업데이트에서는 다음을 수행할 수 있습니다.

- [앱 구성 정책](../apps/app-configuration-policies-use-android.md)을 사용하여 Outlook, Gmail 및 Nine Work 메일 설정을 배포합니다.
- 디바이스 구성 프로필을 사용하여 [신뢰할 수 있는 루트 인증서 설정](../protect/certificates-configure.md)을 배포합니다.
- 디바이스 구성 프로필을 사용하여 [VPN](../configuration/vpn-settings-android-enterprise.md) 및 [Wi-Fi](../configuration/wi-fi-settings-android-enterprise.md) 설정을 배포합니다.

> [!IMPORTANT]
> 이 기능을 사용하면 사용자는 VPN, Wi-Fi 및 메일 프로필에 대해 사용자 이름 및 암호를 사용하여 인증합니다. 현재는 인증서 기반 인증을 사용할 수 없습니다.

적용 대상:  
- Android 엔터프라이즈 디바이스 소유자(완전 관리형)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices--3914202-----"></a>사용자가 macOS 디바이스에 로그인할 때 열리는 앱, 파일, 문서 및 폴더를 제어합니다.<!--3914202   -->
macOS 디바이스에서 기능을 사용하도록 설정하고 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **macOS**(플랫폼) > **디바이스 기능**(프로필 유형)). 

이 업데이트에는 사용자가 등록된 디바이스에 로그인할 때 열리는 앱, 파일, 문서 및 폴더를 제어하는 새 로그인 항목 설정이 있습니다. 

현재 설정을 보려면 Intune의 [macOS 디바이스 기능 설정](../configuration/macos-device-features-settings.md)으로 이동하세요.

적용 대상:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings---4464404----------"></a>최종 기한이 Windows 업데이트 링의 개입형 다시 시작 설정 대체<!-- 4464404        -->
최신 [Windows 서비스 변경 내용](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)과 맞추기 위해 이제 Intune의 Windows 10 업데이트 링에서 [최종 기한에 대한 설정을 지원](../protect/windows-update-settings.md)합니다. ‘최종 기한’은 디바이스에서 기능 및 보안 업데이트를 설치하는 시기를 결정합니다.   Windows 10 1903 이상이 실행되는 디바이스에서 ‘최종 기한’은 ‘개입형 다시 시작’에 대한 구성을 대체합니다.    나중에 ‘최종 기한’은 이전 버전의 Windows 10에서도 ‘개입형 다시 시작’을 대체하게 됩니다.    

‘최종 기한’을 구성하지 않으면 디바이스에서 ‘개입형 다시 시작’ 설정을 계속 사용하지만 향후 업데이트에서 Intune은 개입형 다시 시작 설정을 더 이상 지원하지 않습니다.    

모든 Windows 10 디바이스에서 ‘최종 기한’을 사용하도록 계획합니다  . ‘최종 기한’에 대한 설정이 구현되면 ‘개입형 다시 시작’에 대한 Intune 구성을 [구성되지 않음]으로 변경할 수 있습니다.   [구성되지 않음]으로 설정하면 Intune은 디바이스에서 해당 설정 관리를 중지하지만 설정에 대한 마지막 구성을 디바이스에서 제거하지는 않습니다. 따라서 ‘개입형 다시 시작’에 대해 설정된 마지막 구성은 Intune 이외의 다른 방법에 의해 수정될 때까지 디바이스에서 활성화되어 사용 중인 상태로 유지됩니다.  나중에 Windows의 디바이스 버전이 변경되거나 ‘최종 기한’에 대한 Intune 지원이 디바이스 Windows 버전으로 확장되면 디바이스는 이미 구현된 새 설정을 사용하기 시작합니다. 

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors-----4704642--------"></a>여러 Microsoft Intune Certificate Connector에 대한 지원<!--   4704642      -->
이제 Intune에서 여러 [Microsoft Intune Certificate Connectors for PKCS operations](../protect/certficates-pfx-configure.md)(PKCS용 Microsoft Intune Certificate Connector 작업)의 설치 및 사용을 지원합니다. 이러한 변경은 커넥터의 부하 분산 및 고가용성을 지원합니다. 각 커넥터 인스턴스는 Intune의 인증서 요청을 처리할 수 있습니다.  한 커넥터를 사용할 수 없는 경우 다른 커넥터에서 계속 요청을 처리합니다.

여러 커넥터를 사용하기 위해 최신 버전의 커넥터 소프트웨어로 업그레이드할 필요가 없습니다.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices---4867699-4867709-----"></a>iOS 및 macOS 디바이스에서 기능을 제한하는 새 설정 및 기존 설정의 변경 내용<!-- 4867699 4867709   -->
iOS 및 macOS를 실행하는 디바이스에서 프로필을 만들어 설정을 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 또는 **macOS**(플랫폼 유형) > **디바이스 제한**). 이 업데이트에는 다음 기능이 포함됩니다.

- **macOS** > **디바이스 제한** > **클라우드 및 스토리지**에서 새 **핸드오프** 설정을 사용하여 한 macOS 디바이스에서 사용자의 작업 시작을 차단하고 다른 macOS 또는 iOS 디바이스에서는 계속 작업합니다.

  현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](../configuration/device-restrictions-macos.md)으로 이동하세요.

- **iOS** > **디바이스 제한**에는 다음과 같은 몇 가지 변경 사항이 있습니다.

  - **기본 제공 앱** > **내 iPhone 찾기(감독 모드인 경우에만)** : 내 앱 찾기 기능에서 이 기능을 차단하는 새로운 설정입니다. 
  - **기본 제공 앱** > **내 친구 찾기(감독 모드인 경우에만)** : 내 앱 찾기 기능에서 이 기능을 차단하는 새로운 설정입니다. 
  - **무선** > **Wi-Fi 상태 수정(감독 모드인 경우에만)** : 사용자가 디바이스에서 Wi-Fi를 켜거나 끌 수 없도록 하는 새로운 설정입니다.
  - **키보드 및 사전** > **QuickPath(감독 모드인 경우에만)** : QuickPath 기능을 차단하는 새로운 설정입니다.
  - **클라우드 및 스토리지**: **활동 연속**은 **핸드오프**로 이름이 바뀌었습니다.

  현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md)으로 이동하세요.

적용 대상:  
- macOS 10.15 이상
- iOS 13 이상

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release---4867809-----"></a>일부 감독되지 않은 iOS 디바이스 제한이 iOS 13.0 릴리스에서 감독 전용이 됨<!-- 4867809   -->
이 업데이트에서 일부 설정은 iOS 13.0 릴리스를 사용하는 감독 전용 디바이스에 적용됩니다. 이러한 설정이 iOS 13.0 릴리스 이전에 구성되고 감독되지 않은 디바이스에 할당되면 설정은 해당 감독되지 않은 디바이스에 계속 적용됩니다. 또한 디바이스가 iOS 13.0으로 업그레이드된 후에도 계속 적용됩니다. 이러한 제한은 백업되고 복원되는 감독되지 않은 디바이스에서 제거됩니다.

이러한 설정은 다음과 같습니다.

- 앱 스토어, 문서 보기, 게임
  - 앱 스토어
  - 유해 iTunes, 음악, 팟캐스트 또는 뉴스 콘텐츠
  - Game Center 친구 추가
  - 다중 접속 게임
- 기본 제공 앱
  - 카메라
    - FaceTime
  - Safari
    - 자동 채우기
- 클라우드 및 스토리지
  - iCloud에 백업
  - iCloud 문서 동기화 차단
  - iCloud 키 집합 동기화 차단

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md)으로 이동하세요.

적용 대상:  
- iOS 13.0 이상

#### <a name="improved-device-status-for-macos-filevault-encryption---4944983-----------"></a>macOS FileVault 암호화에 대한 디바이스 상태 개선<!-- 4944983         -->
macOS 디바이스에서 FileVault 암호화에 대한 여러 가지 [디바이스 상태 메시지](../protect/encryption-monitor.md#device-encryption-status)를 업데이트했습니다.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status---5119229---"></a>보고의 일부 Windows Defender 바이러스 백신 검사 설정에 실패 상태가 표시됨<!-- 5119229 -->
Intune에서 Windows Defender 바이러스 백신을 사용하여 Windows 10 디바이스를 검사하는 정책을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **디바이스 제한**(프로필 유형) > **Windows Defender 바이러스 백신**). **매일 빠른 검색을 수행할 시간** 및 **수행할 시스템 검사 유형** 보고에 실제로 성공 상태인 경우에도 실패 상태가 표시됩니다. 

이 업데이트에서 이러한 동작이 수정되었습니다. 따라서 **매일 빠른 검색을 수행할 시간** 및 **수행할 시스템 검사 유형** 설정에는 검사가 성공적으로 완료되면 성공 상태가 표시되고, 설정이 적용되지 않으면 실패 상태가 표시됩니다.

Windows Defender 바이러스 백신 설정에 대한 자세한 내용은 [Intune을 사용하여 기능을 허용하거나 제한하는 Windows 10 이상 디바이스 설정](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="default-scope-tags---3702875----"></a>기본 범위 태그<!-- 3702875  -->
이제 새로운 기본 제공 기본 범위 태그를 사용할 수 있습니다. 범위 태그를 지원하는 태그가 지정되지 않은 모든 Intune 개체는 기본 범위 태그에 자동으로 할당됩니다. 현재 관리자 환경에서 패리티를 유지하기 위해 **기본** 범위 태그는 기존의 모든 역할 할당에 추가됩니다. 관리자가 기본 범위 태그를 사용하여 Intune 개체를 표시하지 않도록 하려면 역할 할당에서 기본 범위 태그를 제거합니다. 이 기능은 System Center Configuration Manager의 보안 범위 기능과 유사합니다. 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

#### <a name="android-enrollment-device-administrator-support---4869749-----"></a>Android 등록 디바이스 관리자 지원<!-- 4869749   -->
Android 디바이스 관리자 등록 옵션이 Android 등록 페이지(**Intune** > **디바이스 등록** > **Android 등록**)에 추가되었습니다. Android 디바이스 관리자는 모든 테넌트에 대해 기본적으로 사용하도록 설정되어 있습니다.  자세한 내용은 [Android 디바이스 관리자 등록](../enrollment/android-enroll-device-administrator.md)을 참조하세요.

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>설정 도우미에서 더 많은 화면 건너뛰기 <!--4877451  -->
다음과 같은 설정 도우미 화면을 건너뛰도록 디바이스 등록 프로그램 프로필을 설정할 수 있습니다.
- iOS의 경우
    - 모양
    - Express 언어
    - 기본 설정 언어
    - 디바이스 간 마이그레이션
- macOS의 경우
    - 화면 시간
    - Touch ID 설정

설정 도우미 사용자 지정에 대한 자세한 내용은 [Create an Apple enrollment profile for iOS](../enrollment/device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)(iOS용 Apple 등록 프로필 만들기) 및 [Create an Apple enrollment profile for macOS](../enrollment/device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)(macOS용 Apple 등록 프로필 만들기)를 참조하세요.

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process---3823054---"></a>Autopilot 디바이스 CSV 업로드 프로세스에 사용자 열 추가<!-- 3823054 -->
이제 Autopilot 디바이스에 대한 CSV 업로드에 사용자 열을 추가할 수 있습니다. 이렇게 하면 CSV를 가져올 때 사용자를 대량으로 할당할 수 있습니다. 자세한 내용은 [Windows Autopilot을 사용하여 Intune에 Windows 디바이스 등록](../enrollment/enrollment-autopilot.md)을 참조하세요.


### <a name="device-management"></a>디바이스 관리

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days--4231059----"></a>자동 디바이스 정리 시간 제한을 30일로 구성<!--4231059  -->
자동 디바이스 정리 시간 제한은 마지막 로그인 후 30일(이전에는 90일 제한)로 설정할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스** > **설정디바이스** > **정리 규칙**으로 이동 합니다.

#### <a name="build-number-included-on-android-device-hardware-page---4461910-----"></a>Android 디바이스 하드웨어 페이지에 포함된 빌드 번호<!-- 4461910   -->
각 Android 디바이스에 대한 하드웨어 페이지의 새 항목에는 디바이스의 운영 체제 빌드 번호가 포함됩니다. 자세한 내용은 [View device details in Intune](../remote-actions/device-inventory.md)(Intune에서 디바이스 세부 정보 보기)을 참조하세요.


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>2019년 8월 5일 주

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices---4843713---"></a>Zebra Technologies는 Android 엔터프라이즈 디바이스에서 지원되는 OEMConfig OEM임<!-- 4843713 -->

Intune에서는 OEMConfig를 사용하여 디바이스 구성 프로필을 만들고, 설정을 Android 엔터프라이즈 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **OEMConfig**(프로필 유형)).

이 업데이트에서 Zebra Technologies는 지원되는 OEMConfig OEM(Original Equipment Manufacturer)입니다. OEMConfig에 대한 자세한 내용은 [Use and manage Android Enterprise devices with OEMConfig](../configuration/android-oem-configuration-overview.md)(OEMConfig를 사용하여 Android 엔터프라이즈 디바이스 사용 및 관리)를 참조하세요.

적용 대상:  
- Android 엔터프라이즈

<!-- ########################## -->

## <a name="week-of-july-22-2019-1907-service-release"></a>2019년 7월 22일 주(1907 서비스 릴리스)

### <a name="app-management"></a>앱 관리

#### <a name="customized-notifications-for-users-and-groups---16766574------------"></a>사용자 및 그룹을 위한 사용자 지정 알림<!-- 16766574          -->
Intune으로 관리하는 iOS 및 Android 디바이스를 사용하는 사용자에게 회사 포털 애플리케이션에서 푸시 알림을 보낼 수 있습니다. 모바일 푸시 알림은 무료 텍스트로 원하는 대로 사용자 지정할 수 있으며, 어떤 용도로도 사용할 수 있습니다. 조직의 여러 사용자 그룹을 대상으로 알림을 보낼 수 있습니다. 자세한 내용은 [사용자 지정 알림](../remote-actions/custom-notifications.md)을 참조하세요.

#### <a name="googles-device-policy-controller-app---3041950----"></a>Google의 디바이스 정책 컨트롤러 앱<!-- 3041950  -->
이제 Managed Home Screen 앱에서 Google의 Android 디바이스 정책 앱에 액세스할 수 있습니다. Managed Home Screen 앱은 Intune에 다중 앱 키오스크 모드를 사용하는 AE(Android 엔터프라이즈) 전용 디바이스로 등록된 디바이스에 사용되는 사용자 지정 시작 관리자입니다. Android 디바이스 정책 앱에서 액세스하거나 지원 및 디버깅을 위해 사용자를 Android 디바이스 정책 앱으로 안내할 수 있습니다. 이 시작 기능은 디바이스가 등록되고 Managed Home Screen으로 잠길 때 사용할 수 있습니다. 이 기능을 사용하기 위해 추가 설치가 필요하지 않습니다.

#### <a name="outlook-protection-settings-for-ios-and-android-devices---3212619---"></a>iOS 및 Android 디바이스의 Outlook 보호 설정<!-- 3212619 -->
이제 디바이스 등록 없이도 간단한 Intune 관리 컨트롤을 사용하여 iOS 및 Android의 Outlook 일반 앱 구성 설정과 데이터 보호 구성 설정을 구성할 수 있습니다. 일반 앱 구성 설정은 관리자가 등록된 디바이스에서 iOS 및 Android용 Outlook을 관리할 때 활성화할 수 있는 설정과 동등한 설정을 제공합니다. Outlook 설정에 대한 자세한 내용은 [iOS 및 Android용 Outlook 앱 구성 설정 배포](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 eeready   idstaged -->

Windows 10 다비이스 구성 프로필을 만듭니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼은 **Windows 10** 선택 > **적용 가능성 규칙**). 이 업데이트에서는 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 가능성 규칙을 추가하려면 [적용 가능성 규칙](../configuration/device-profile-create.md#applicability-rules)을 참조하세요.

적용 대상: Windows 10 이상

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices---3330008----"></a>토큰을 사용하여 iOS 및 macOS 디바이스의 사용자 지정 프로필에 디바이스별 정보 추가<!-- 3330008  -->
iOS 및 macOS 디바이스에서 사용자 지정 프로필을 사용하여 Intune에서 기본 제공되지 않는 설정 및 기능을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼은 **iOS** 또는 **macOS** 선택 > 프로필 유형은 **사용자 지정** 선택). 이 업데이트에서는 `.mobileconfig` 파일에 토큰을 추가하여 디바이스별 정보를 추가할 수 있습니다. 예를 들어 구성 파일에 `Serial Number: {{serialnumber}}`를 추가하여 디바이스의 일련 번호를 표시할 수 있습니다.

사용자 지정 프로필을 만들려면 [iOS 사용자 지정 설정](../configuration/custom-settings-ios.md) 또는 [macOS 사용자 지정 설정](../configuration/custom-settings-macos.md)을 참조하세요.

적용 대상:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise---3712769-----"></a>Android 엔터프라이즈용 OEMConfig 프로필을 만들 때 새로운 구성 디자이너 사용<!-- 3712769   -->
Intune에서 OEMConfig 앱을 사용하는 디바이스 구성 프로필을 만들 수 있습니다(디바이스 구성 > 프로필 > 프로필 만들기 > 플랫폼은 [Android 엔터프라이즈] 선택 > 프로필은 [OEMConfig] 선택). 이렇게 하면 템플릿 및 변경 가능한 값과 JSON 편집기가 열립니다. 

이 업데이트는 제목, 설명 등과 같은 세부 정보를 앱에 포함하여 표시하는 향상된 사용자 환경을 갖춘 구성 디자이너를 포함합니다. 기존과 같이 JSON 편집기도 사용할 수 있으며, 구성 디자이너에서 수행한 변경 사항이 모두 표시됩니다.

기존 설정을 보려면 [Use and manage Android Enterprise devices with OEMConfig](../configuration/android-oem-configuration-overview.md)(OEMConfig를 사용하여 Android 엔터프라이즈 디바이스 사용 및 관리)를 참조하세요.

적용 대상: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello---4089576--------------"></a>Windows Hello 구성을 위한 업데이트된 UI<!-- 4089576            -->
[비즈니스용 Windows Hello를 사용하여 Intune을 구성하는](../protect/windows-hello.md) 콘솔이 업데이트되었습니다. 이제 Windows Hello 지원을 활성화하는 콘솔의 동일한 창에서 모든 구성 설정을 이용할 수 있습니다.

#### <a name="intune-powershell-sdk---4924113---"></a>Intune PowerShell SDK<!-- 4924113 --> 
Microsoft Graph를 통해 Intune API를 지원하는 Intune PowerShell SDK가 버전 6.1907.1.0으로 업데이트되었습니다. Intune PowerShell SDK는 이제 다음을 지원합니다.
- Azure Automation과 작동합니다.
- App-Only Auth 읽기 작업을 지원합니다. 
- 친숙한 짧은 이름(별칭 등)을 지원합니다.
- PowerShell 명명 규칙을 준수합니다. 구체적으로, `Connect-MSGraph` cmdlet의 `PSCredential` 매개 변수 이름이 `Credential`로 변경되었습니다.
- `Invoke-MSGraphRequest` cmdlet을 사용할 때 `Content-Type` 헤더의 값을 수동으로 지정할 수 있습니다.

자세한 내용은 [PowerShell SDK for Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)(Microsoft Intune Graph API를 위한 PowerShell SDK)를 참조하세요.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="updates-for-enrollment-restrictions---2871968---"></a>등록 제한 업데이트<!-- 2871968 -->
Android 엔터프라이즈 회사 프로필이 기본적으로 허용되도록 새로운 테넌트에 대한 등록 제한이 업데이트되었습니다. 이 변경 사항은 기존 테넌트에 영향을 주지 않습니다. Android 엔터프라이즈 회사 프로필을 사용하려면 기존과 같이 [Intune 계정을 관리형 Google Play 계정에 연결](../enrollment/connect-intune-android-enterprise.md)해야 합니다.

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions--4089575-4089579----"></a>Apple 등록 및 등록 제한 UI 업데이트<!--4089575, 4089579  -->
다음 프로세스는 모두 마법사 스타일의 사용자 인터페이스를 사용합니다.
- Apple 디바이스 등록. 자세한 내용은 [Apple 디바이스 등록 프로그램을 통해 iOS 디바이스를 자동으로 등록](../enrollment/device-enrollment-program-enroll-ios.md)을 참조하세요.
- 등록 제한 만들기. 자세한 내용은 [등록 제한 설정](../enrollment/enrollment-restrictions-set.md)을 참조하세요.

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices---4711509--idmiss---"></a>Android Q 디바이스의 회사 디바이스 식별자 사전 구성 처리<!-- 4711509  idmiss -->
Google은 Android Q(v10)에서 레거시 관리형(디바이스 관리자) Android 디바이스의 MDM 에이전트가 디바이스 식별자 정보를 수집하는 기능을 제거할 예정입니다.  Intune에는 IT 관리자가 해당 디바이스를 자동으로 회사 소유로 태그 지정하기 위해 [디바이스 일련 번호 또는 IMEI 목록을 사전 구성](../enrollment/corporate-identifiers-add.md#identify-corporate-owned-devices-with-imei-or-serial-number)할 수 있도록 지원하는 기능이 있습니다. 디바이스 관리자 관리형 Android Q 디바이스에서는 이 기능이 작동하지 않게 됩니다.  디바이스의 일련 번호와 IMEI 중 어느 것이 업로드되든 관계없이 Intune 등록 중에는 해당 디바이스가 항상 개인용으로 간주됩니다.  등록 후에 소유자를 회사로 수동 전환할 수 있습니다.  이 변경 사항은 새로운 등록에만 영향을 주며, 기존에 등록된 디바이스는 영향을 받지 않습니다.  회사 프로필로 관리되는 Android 디바이스는 이 변경 사항의 영향을 받지 않으며 계속해서 기존과 같이 작동합니다.  이에 더해, 디바이스 관리자로 등록된 Android Q 디바이스는 더 이상 Intune 콘솔에 일련 번호 또는 IMEI를 디바이스 속성으로 보고할 수 없게 됩니다.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices---4977730---"></a>Android 엔터프라이즈 등록(회사 프로필, 전용 디바이스 및 완전 관리형 디바이스) 아이콘 변경<!-- 4977730 -->
Android 엔터프라이즈 등록 프로필 아이콘이 변경되었습니다. 새 아이콘을 보려면 **Intune** > **등록** > **Android 등록**으로 이동한 다음 **등록 프로필** 아래를 보세요.


#### <a name="windows-diagnostic-data-collection-change---4113859---"></a>Windows 진단 데이터 수집 변경 사항<!-- 4113859 -->
Windows 10 버전 1903 이상을 실행하는 디바이스의 진단 데이터 수집 기본값이 변경되었습니다. Windows 10 1903부터 진단 데이터 수집이 기본적으로 활성화됩니다. Windows 진단 데이터는 Windows 디바이스에서 제공하는 디바이스 관련 및 Windows와 관련 소프트웨어의 성능 관련 중요한 기술 데이터입니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)을 참조하세요. Autopilot 디바이스는 Autopilot 프로필에서 [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)가 달리 설정되지 않은 한 “전체” 원격 분석으로 옵트인됩니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="improve-device-location---3855417----"></a>디바이스 위치 개선<!-- 3855417  -->
**디바이스 찾기** 작업을 사용하여 디바이스의 정확한 좌표로 확대할 수 있습니다. 분실한 iOS 디바이스 찾기에 대한 자세한 내용은 [분실한 iOS 디바이스 찾기](../remote-actions/device-locate.md)를 참조하세요.

### <a name="device-security"></a>디바이스 보안

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview----1311949-------"></a>Windows Defender 방화벽의 고급 설정(공개 미리 보기)<!--  1311949     -->  
Intune을 사용하여 디바이스 구성 프로필의 일부로서 Windows 10 엔드포인트 보호를 위해 [사용자 지정 방화벽 규칙을 관리](../protect/endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)할 수 있습니다. 규칙은 애플리케이션, 네트워크 주소 및 포트에 대한 인바운드 및 아웃바운드 동작을 지정할 수 있습니다. 

#### <a name="updated-ui-for-managing-security-baselines---4091125-------"></a>보안 기준 관리의 업데이트된 UI<!-- 4091125     -->
Intune 콘솔의 보안 기준 [만들기 및 편집 환경](../protect/security-baselines.md#create-the-profile)이 업데이트되었습니다. 변경 사항에는 다음이 포함됩니다.

하나의 블레이드 안에서 단일 블레이드로 압축된 간단한 마법사 스타일 형식. 이 새로운 디자인에서는 IT 전문가가 몇 개의 개별 창을 드릴다운해야 했던 블레이드 확장이 사라졌습니다.  
이제 나중에 돌아가서 기준을 할당하는 대신 만들기 및 편집 환경의 일환으로 할당을 만들 수 있습니다. 새 기준을 만들거나 기존 기준을 편집하기 전에 볼 수 있는 설정 요약도 추가되었습니다. 편집할 때는 현재 편집 중인 속성 범주 내에 설정된 항목 목록의 요약만 표시됩니다.

<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019년 7월 15일 주 

### <a name="app-management"></a>앱 관리

#### <a name="managed-home-screen-and-managed-settings-icons---4918107---"></a>Managed Home Screen 및 관리형 설정 아이콘<!-- 4918107 -->
Managed Home Screen 앱 아이콘과 **관리형 설정** 아이콘이 업데이트되었습니다. Managed Home Screen 앱은 Intune에 AE(Android 엔터프라이즈) 전용 디바이스로 등록되었고 다중 앱 키오스크 모드로 실행되는 디바이스만 사용합니다. Managed Home Screen 앱에 대한 자세한 내용은 [Android 엔터프라이즈에 대해 Microsoft Managed Home Screen 앱 구성](../apps/app-configuration-managed-home-screen-app.md)을 참조하세요.

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices---4918136---"></a>Android 엔터프라이즈 전용 디바이스의 Android 디바이스 정책<!-- 4918136 -->
Managed Home Screen 앱의 디버그 화면에서 Android 디바이스 정책 애플리케이션에 액세스할 수 있습니다. Managed Home Screen 앱은 Intune에 AE(Android 엔터프라이즈) 전용 디바이스로 등록되었고 다중 앱 키오스크 모드로 실행되는 디바이스만 사용합니다. 자세한 내용은 [Android 엔터프라이즈에 대해 Microsoft Managed Home Screen 앱 구성](../apps/app-configuration-managed-home-screen-app.md)을 참조하세요.

#### <a name="ios-company-portal-updates---3902931---"></a>iOS 회사 포털 업데이트<!-- 3902931 -->
기존 “i.manage.microsoft.com” 텍스트가 iOS 앱 관리 프롬프트의 회사 이름으로 대체됩니다. 예를 들어, 사용자가 회사 포털에서 iOS 앱을 설치하려고 시도하거나 사용자가 앱의 관리를 허용할 때 “i.manage.microsoft.com” 대신 회사 이름이 표시됩니다. 이 변경 사항은 향후 며칠에 걸쳐 점진적으로 모든 고객에게 적용될 예정입니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="manage-filevault-for-macos----3858502--4557986--1210104----"></a>macOS용 FileVault 관리<!--  3858502 + 4557986 + 1210104  -->
Intune을 사용하여 [macOS 디바이스의 FileVault 키 암호화를 관리](../protect/encrypt-devices.md)할 수 있습니다. 디바이스를 암호화하려면 엔드포인트 보호 디바이스 구성 프로필을 사용해야 합니다.

FileVault에 대한 Microsoft의 지원에는 암호화되지 않은 디바이스의 암호화, 디바이스 개인 복구 키의 에스크로, 개인 암호화 키의 자동 또는 수동 회전, 회사 디바이스의 키 검색이 포함됩니다. 최종 사용자는 회사 포털 웹 사이트를 사용하여 암호화된 디바이스의 개인 복구 키를 가져올 수도 있습니다.

모든 디바이스 암호화 세부 정보를 한곳에서 볼 수 있도록 암호화 보고서에 BitLocker 정보에 더해 [FileVault 정보](../protect/encryption-monitor.md)도 표시됩니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user---4156123---"></a>Windows Autopilot 초기화 사용 시 디바이스의 기본 사용자가 제거됨<!-- 4156123 -->
디바이스에서 Autopilot 초기화를 사용하면 디바이스의 기본 사용자가 제거됩니다. 초기화 후에 로그인하는 사용자가 기본 사용자로 설정됩니다. 이 기능은 향후 며칠에 걸쳐 점진적으로 모든 고객에게 선보일 예정입니다.

## <a name="week-of-july-8-2019"></a>2019년 7월 8일 주

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 관리 템플릿의 새로운 Office, Windows 및 OneDrive 설정 <!-- 3510695 -->

Intune에서 온-프레미스 그룹 정책 관리와 비슷한 관리 템플릿을 만들 수 있습니다(**디바이스 관리** > **프로필** > **프로필 만들기** > 플랫폼은 **Windows 10 이상** 선택 > 프로필 유형은 **관리 템플릿** 선택).

이 업데이트에는 템플릿에 추가할 수 있는 더 많은 Office, Windows 및 OneDrive 설정이 포함됩니다. 새로운 설정을 통해 이제 100% 클라우드 기반인 2500여 개의 설정을 구성할 수 있습니다.

이 기능에 대해 자세히 알아보려면 [Windows 10 템플릿을 사용하여 Intune에서 그룹 정책 설정 구성](../configuration/administrative-templates-windows.md)을 참조하세요.

적용 대상: Windows 10 이상

## <a name="week-of-july-1-2019"></a>2019년 7월 1일 주 

### <a name="app-management"></a>앱 관리

#### <a name="aad-and-app-on-android-enterprise-devices---3574267---"></a>Android 엔터프라이즈 디바이스의 AAD 및 APP<!-- 3574267 -->
이제 완전 관리형 Android 엔터프라이즈 디바이스를 온보딩할 때 사용자는 새로운 디바이스 또는 초기화된 디바이스의 초기 설정 중에 AAD(Azure Active Directory)에 등록하게 됩니다. 이전에는 완전 관리형 디바이스의 설정이 완료된 후에 사용자가 Microsoft Intune 앱을 수동으로 실행해야 AAD 등록이 시작되었습니다. 이제는 초기 설정 후에 디바이스 홈페이지가 표시되면 디바이스가 등록됩니다.

AAD 업데이트에 더해, 이제 완전 관리형 Android 엔터프라이즈 디바이스에서 Intune APP(앱 보호 정책)가 지원됩니다. 이 기능은 점진적으로 적용될 예정입니다. 자세한 내용은 [Intune을 사용하여 Android 엔터프라이즈 디바이스에 관리형 Google Play 앱 추가](../apps/apps-add-android-for-work.md)를 참조하세요.

## <a name="week-of-june-24-2019-1906-service-release"></a>2019년 6월 24일 주(1906 서비스 릴리스)

### <a name="app-management"></a>앱 관리

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data---3145939---"></a>조직 데이터에 연결할 수 있는 브라우저 구성<!-- 3145939 -->
이제 Android 및 iOS 디바이스의 Intune APP(앱 보호 정책)를 사용하여 Intune Managed Browser 또는 Microsoft Edge뿐 아니라 특정 브라우저로도 조직 웹 링크를 전송할 수 있습니다.  APP에 대한 자세한 내용은 [앱 보호 정책이란?](../apps/app-protection-policy.md)을 참조하세요.

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>모든 앱 페이지에서 온라인/오프라인 비즈니스용 Microsoft 스토어 앱 식별<!--4089647 -->
이제 **모든 앱** 페이지에 MSFB(비즈니스용 Microsoft 스토어) 앱을 온라인 또는 오프라인 앱으로 식별하기 위한 레이블이 포함됩니다. 각 MSFB 앱에 이제 **Online** 또는 **Offline** 접미사가 포함됩니다. 앱 세부 정보 페이지에는 **라이선스 유형** 및 **디바이스 컨텍스트 설치 지원**(오프라인 라이선스 앱만 해당) 정보가 포함됩니다.

#### <a name="company-portal-app-on-windows-shared-devices--4393553---"></a>Windows 공유 디바이스의 회사 포털 앱<!--4393553 -->
이제 사용자가 Windows 공유 디바이스에서 회사 포털 앱에 액세스할 수 있습니다. 최종 사용자의 디바이스 타일에 **공유** 레이블이 표시됩니다. 이 변경 사항은 Windows 회사 포털 앱 버전 10.3.45609.0 이상에 적용됩니다.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page---4224326---"></a>새 회사 포털 웹 페이지에서 설치된 모든 앱 보기<!-- 4224326 -->
회사 포털 앱 사이트의 새 **설치된 앱** 페이지에는 사용자의 디바이스에 설치된 모든 관리형 앱(필수 및 사용 가능)이 나열되어 있습니다. 할당 유형 외에도 사용자는 앱의 게시자, 게시된 날짜 및 현재 설치 상태를 볼 수 있습니다. 사용자가 필요로 하거나 사용할 수 있는 앱을 만들지 않은 경우, 회사 앱이 설치되지 않았다는 메시지가 표시됩니다. 웹에서 새 페이지를 보려면 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)로 이동하여 **설치된 앱**을 클릭합니다.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device---2352913---"></a>새 보기를 통해 앱 사용자가 디바이스에 설치된 관리형 앱을 볼 수 있습니다.<!-- 2352913 -->  
이제 Windows용 회사 포털은 사용자의 디바이스에 설치된 모든 관리형 앱(필수 및 사용 가능)을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수도 있습니다. 사용자가 필요로 하거나 사용할 수 있는 앱을 만들지 않은 경우, 회사 앱이 설치되지 않았다는 메시지가 표시됩니다. 새 보기를 확인하려면 회사 포털 탐색 창으로 이동하여 **앱** > **설치된 앱**을 선택합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices---2043024---"></a>macOS 디바이스에서 커널 확장에 대한 설정 구성<!-- 2043024 -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택). 이 업데이트는 디바이스에서 커널 확장을 구성하고 사용할 수 있는 새 설정 그룹을 포함합니다. 특정 확장을 추가하거나 특정 파트너 또는 개발자의 모든 확장을 허용할 수 있습니다.

이 기능에 대해 자세히 알아보려면 [커널 확장 개요](../configuration/kernel-extensions-overview-macos.md) 및 [커널 확장 설정](../configuration/kernel-extensions-settings-macos.md)을 참조하세요.

적용 대상: macOS 10.13.2 이상

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options---2697002---"></a>Windows 10 디바이스에 대한 스토어 앱 전용 설정에 다른 구성 옵션 포함<!-- 2697002 -->
Windows 디바이스에 대한 디바이스 제한 프로필을 만들 때 **스토어의 앱만** 설정을 사용하여 사용자가 Windows 앱 스토어에서만 앱을 설치하게 할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼용) > **디바이스 제한**(프로필 유형)). 이 업데이트에서는 더 많은 옵션을 지원하도록 이 설정이 확장되었습니다.

새 설정을 보려면 [기능을 허용하거나 제한하는 Windows 10(이상) 디바이스 설정](../configuration/device-restrictions-windows-10.md#app-store)으로 이동하세요.

적용 대상: Windows 10 이상

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group---4089955---"></a>여러 Zebra 모바일 확장 디바이스 프로필을 디바이스, 동일한 사용자 그룹 또는 동일한 디바이스 그룹에 배포<!-- 4089955 -->
Intune에서는 디바이스 구성 프로필에서 Zebra MX(모바일 확장)를 사용하여 Intune에서 기본 제공하지 않는 Zebra 디바이스 설정을 사용자 지정할 수 있습니다. 현재는 한 디바이스에 한 프로필을 배포할 수 있습니다. 이 업데이트에서는 다음으로 여러 프로필을 배포할 수 있습니다.
- 동일한 사용자 그룹
- 동일한 디바이스 그룹
- 단일 디바이스

[Microsoft Intune에서 Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리](../configuration/android-zebra-mx-overview.md)는 Intune에서의 MX 사용 방법을 보여 줍니다.

적용 대상: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow---4404075----"></a>iOS 디바이스에서 일부 키오스크 설정이 “허용”이 아닌 “차단”으로 설정됩니다.<!-- 4404075  -->
iOS 디바이스에서 디바이스 제한 프로필을 만들 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **키오스크**) **자동 잠금**, **벨소리 전환**, **화면 회전**, **화면 일시 중지 단추** 및 **볼륨 단추**를 설정합니다.

이 업데이트에서는 값이 **차단**(기능 차단) 또는 **구성 안 함**(기능 허용)입니다. 설정을 보려면 [기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md#kiosk)으로 이동하세요.

적용 대상: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices---4490704---"></a>iOS 디바이스에서 암호 인증에 Face ID 사용<!-- 4490704 -->
iOS 디바이스에 대한 디바이스 제한 프로필을 만들 때 지문을 암호에 사용할 수 있습니다. 이 업데이트에서는 지문 암호 설정에서 안면 인식도 사용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼은 **iOS** 선택 > 프로필 유형은 **디바이스 제한** 선택 > **암호**). 그 결과 다음과 같은 설정이 변경되었습니다.

- **지문 잠금 해제**가 이제 **Touch ID 및 Face ID 잠금 해제**가 됩니다.
- **지문 수정(감독 모드에서만 해당)** 이 이제 **Touch ID 및 Face ID 수정(감독 모드에서만 해당)** 이 됩니다.

Face ID는 iOS 11.0 이상에서 제공됩니다. 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md#password)으로 이동하세요.

적용 대상: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region---4593948---"></a>iOS 디바이스에서 게임 및 App Store 기능을 제한할 때 등급 지역에 따라 달라짐<!-- 4593948 -->
iOS 디바이스에서는 게임, App Store, 문서 보기 관련 기능을 허용하거나 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **App Store, 문서 보기, 게임**). 또한 미국처럼 등급 지역을 선택할 수 있습니다.

이 업데이트에서는 **앱** 기능이 **등급 지역**의 자식 요소가 되며 **등급 지역**에 따라 달라집니다. 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동하세요.

적용 대상: iOS

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join---4809146--"></a>하이브리드 Azure AD 조인에 대한 Windows Autopilot 지원<!-- 4809146-->
기존 디바이스에 대한 Windows Autopilot은 이제 기존의 Azure AD 조인 지원에 더해 하이브리드 Azure AD 조인을 지원합니다. 이 변경 사항은 Windows 10 버전 1809 이상 디바이스에 적용됩니다. 자세한 내용은 [기존 디바이스에 대한 Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices)을 참조하세요.

### <a name="device-management"></a>디바이스 관리

#### <a name="see-the-security-patch-level-for-android-devices---4461911---"></a>Android 디바이스에 대한 보안 패치 수준 참조<!-- 4461911 -->
이제 Android 디바이스에 대한 보안 패치 수준을 확인할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스** > **모든 디바이스** > 디바이스 선택 > **하드웨어**를 선택하세요.
패치 수준은 **운영 체제** 섹션에 나열되어 있습니다.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group---3173810---"></a>보안 그룹의 모든 관리 디바이스에 범위 태그 할당<!-- 3173810 -->
이제 보안 그룹에 범위 태그를 할당할 수 있으며 이 보안 그룹의 모든 디바이스가 해당 범위 태그에 연결됩니다. 이 그룹의 모든 디바이스에도 해당 범위 태그가 할당됩니다. 이 기능으로 설정된 범위 태그는 현재 디바이스 범위 태그 흐름으로 설정된 범위 태그를 덮어쓰게 됩니다. 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

### <a name="device-security"></a>디바이스 보안

#### <a name="use-keyword-search-with-security-baselines------"></a>보안 기준에서 키워드 검색 사용<!--  -->
[보안 기준 프로필](../protect/security-baselines.md#create-the-profile)을 만들거나 편집할 때 새로운 *검색* 창에서 키워드를 지정하여 사용 가능한 설정 그룹에서 검색 조건을 포함하는 설정 그룹을 필터링할 수 있습니다.

#### <a name="the-security-baselines-feature-is-now-generally-available---3785395---"></a>보안 기준 기능 일반 공급<!-- 3785395 -->
**보안 기준** 기능의 미리 보기 단계가 종료되어 이제 일반 공급되었습니다.  즉, 이 기능은 프로덕션에서 사용 가능합니다. 단, 개별 기준 템플릿은 아직 미리 보기 상태일 수 있으며, 개별 일정에 따라 평가되어 일반 공급으로 릴리스됩니다.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available---3794072-4217151--3534649---"></a>MDM 보안 기준 템플릿 일반 공급<!-- 3794072, 4217151,  3534649 -->
MDM 보안 기준 템플릿의 미리 보기 단계가 종료되어 이제 일반 공급되었습니다. 일반 공급 템플릿은 **2019년 5월 MDM 보안 기준**입니다.  이는 미리 보기 버전에서의 업그레이드가 아닌 새 템플릿입니다.  새 템플릿이므로 [여기에 포함된 설정](../protect/security-baseline-settings-mdm.md)을 검토한 다음 새 프로필을 만들어서 템플릿을 디바이스에 배포해야 합니다. 다른 보안 기준 템플릿은 아직 미리 보기 상태일 수 있습니다. 사용 가능한 기준 목록은 [사용 가능한 보안 기준](../protect/security-baselines.md#available-security-baselines)을 참조하세요.  

새 템플릿인 *2019년 5월 MDM 보안 기준* 템플릿은 개발 문서에서 최근 발표된 다음과 같은 두 가지 설정을 포함합니다.  
- 잠금 화면 위: 잠긴 화면에서 음성으로 앱 활성화  
- DeviceGuard: 디바이스의 다음 재부팅 시 VBS(가상화 기반 보안) 사용  

이에 더해, *2019년 5월 MDM 보안 기준*에는 새로 추가된 설정과 제거된 설정이 있으며, 한 가지 설정의 기본값이 변경되었습니다. 미리 보기에서 일반 공급으로의 상세한 변경 사항 목록을 보려면 **새 템플릿의 변경된 내용**을 참조하세요.

#### <a name="security-baseline-versioning---3194322---"></a>보안 기준 버전 관리<!-- 3194322 -->
Intune 보안 기준에서는 버전 관리가 지원됩니다. 따라서 각 보안 기준의 새로운 버전이 릴리스되면 처음부터 새 기준을 다시 만들고 배포하지 않고도 기존 보안 기준 프로필이 새 기준 버전을 사용하도록 업데이트할 수 있습니다. 이에 더해, Intune 콘솔에서 해당 기준을 사용하는 개별 프로필의 개수, 프로필이 사용하는 여러 기준 버전의 개수, 특정 보안 기준의 최신 릴리스 날짜 등 각 기준의 정보를 볼 수 있습니다.  자세한 내용은 **보안 기준**을 참조하세요.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved---4501151---"></a>로그인 설정의 보안 사용 키가 이동됨<!-- 4501151 -->
**로그인에 대해 보안 키 사용**이라는 이름의 ID 보호 디바이스 구성 설정이 *비즈니스용 Windows Hello 구성*의 하위 설정에서 최상위 수준 설정으로 이동되었습니다. 따라서 비즈니스용 Windows Hello의 사용을 활성화하지 않아도 언제든지 사용 가능합니다. 자세한 내용은 [ID 보호](../protect/identity-protection-windows-settings.md)를 참조하세요.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="new-permissions-for-assigned-group-admins---4504437-----"></a>할당된 그룹 관리자를 위한 새로운 권한<!-- 4504437   -->
Intune에서 기본 제공되는 학교 관리자 역할이 이제 관리형 앱의 만들기, 읽기, 업데이트, 삭제(CRUD) 권한을 갖습니다. 즉, Intune for Education에서 그룹 관리자로 할당되면 이제 [기존 권한](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)에 더해 iOS MDM Push Certificate, iOS MDM 서버 토큰 및 iOS VPP 토큰을 만들고, 보고, 업데이트하고, 삭제할 수 있습니다. 이러한 작업을 수행하려면 **테넌트 설정** > **iOS 디바이스 관리**로 이동하세요.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials---4655885---"></a>애플리케이션이 Graph API를 사용하여 사용자 자격 증명 없이 읽기 작업을 호출할 수 있음<!-- 4655885 -->
애플리케이션이 사용자 자격 증명 없이 앱 ID를 통해 Intune Graph API 읽기 작업을 호출할 수 있습니다. Intune에 대해 Microsoft Graph API를 액세스하는 방법에 대한 자세한 내용은 [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)(Microsoft Graph에서 Intune 사용)를 참조하세요.

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps---4392555---"></a>비즈니스용 Microsoft 스토어 앱에 범위 태그 적용<!-- 4392555 -->
이제 비즈니스용 Microsoft 스토어 앱에 범위 태그를 적용할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](scope-tags.md)을 참조하세요.

## <a name="week-of-june-17-2019"></a>2019년 6월 17일 주

### <a name="app-management"></a>앱 관리

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 앱의 새로운 기능
Android용 Microsoft Intune 앱(미리 보기)에 새로운 기능을 추가했습니다. 이제 완전 관리형 Android 디바이스의 사용자는 다음을 수행할 수 있습니다.  

* Intune 회사 포털 또는 Microsoft Intune 앱을 통해 등록한 디바이스를 보고 관리합니다.
* 해당 조직에 지원을 문의합니다.
* Microsoft에 피드백을 보냅니다.
* 조직에서 설정한 사용 약관을 봅니다.

## <a name="week-of-june-10-2019"></a>2019년 6월 10일 주

### <a name="app-management"></a>앱 관리

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github---2653471---"></a>GitHub에서 사용할 수 있는 Intune SDK 통합을 표시하는 새로운 샘플 앱<!-- 2653471 -->
msintuneappsdk GitHub 계정에서 iOS(Swift), Android, Xamarin.iOS, Xamarin Forms 및 Xamarin.Android용 새 샘플 애플리케이션을 추가했습니다. 이러한 앱은 기존 설명서를 보완하고 Intune 앱 SDK를 사용자 모바일 앱에 통합하는 방법을 보여 주기 위한 것입니다. Intune SDK에 대한 추가 지침이 필요한 앱 개발자는 다음의 연결된 샘플을 참조하세요.
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - 조정된 인증에 ADAL(Azure Active Directory 인증 라이브러리)을 사용하는 네이티브 iOS(Swift) 인스턴트 메시징 앱입니다.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - 조정된 인증에 ADAL을 사용하는 네이티브 Android 할일 목록 앱입니다.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - 조정된 인증에 ADAL을 사용하는 Xamarin.Android 할일 목록 앱입니다. 이 리포지토리에는 Xamarin.Forms 앱도 있습니다.
- [Xamarin.iOS 샘플 앱](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 기본 Xamarin.iOS 샘플 앱입니다.

## <a name="week-of-may-27-2019"></a>2019년 5월 27일 주

### <a name="app-management"></a>앱 관리

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices---4223162---"></a>Android 디바이스에서 잠재적으로 유해한 앱 보고<!-- 4223162 -->
Intune은 이제 Android 디바이스에서 잠재적으로 유해한 앱에 대한 정보를 제공합니다. 

## <a name="week-of-may-20-2019"></a>2019년 5월 20일 주

### <a name="app-management"></a>앱 관리

#### <a name="windows-company-portal-app---3316993---"></a>Windows 회사 포털 앱<!-- 3316993 -->
이제 Windows 회사 포털 앱에 **디바이스**로 레이블이 지정된 새 페이지가 생깁니다. **디바이스** 페이지는 최종 사용자에게 등록된 모든 디바이스를 보여줍니다. 사용자는 버전 10.3.4291.0 이상을 사용할 때 회사 포털에서 이 변경 사항을 볼 수 있습니다. 회사 포털 구성에 대한 정보는 [Microsoft Intune 회사 포털 앱을 구성하는 방법](../apps/company-portal-app.md)을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 디바이스 OrderID 특성 이름이 그룹 태그로 변경됨 <!-- 4659453 -->

더 직관적이 되도록 Autopilot 디바이스의 **OrderID** 특성 이름이 **그룹 태그**로 변경되었습니다. CSV를 사용하여 Autopilot 디바이스 정보를 업로드하는 경우 OrderID가 아닌 열 머리글로 그룹 태그를 사용해야 합니다.  

## <a name="week-of-may-13-2019-1905-service-release"></a>2019년 5월 13일 주(1905 서비스 릴리스)

### <a name="app-management"></a>앱 관리

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation---1927359----"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함<!-- 1927359  -->
Apple의 회사 디바이스 등록 방법 중 하나를 통해 설정 도우미에서 이미 등록한 디바이스에서는 최종 사용자가 앱 스토어에서 회사 포털 앱을 수동으로 설치하는 경우 Intune은 더 이상 해당 회사 포털 앱을 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 

또한 iOS 회사 포털 앱에서 **디바이스 식별** 화면이 제거될 예정입니다. 따라서 조건부 액세스를 사용하거나 회사 앱을 배포하려는 관리자는 DEP 등록 프로필을 업데이트해야 합니다. 이 요구 사항은 DEP 등록이 설정 도우미에서 인증된 경우에만 적용됩니다. 이러한 경우 디바이스에 회사 포털을 푸시해야 합니다. 이렇게 하려면 **Intune** > **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 토큰 > **프로필**을 선택한 후 프로필 > **속성**을 선택하고 **회사 포털 설치**를 **예**로 설정합니다.

이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy---3568384---"></a>최종 사용자가 앱 보호 정책을 사용하여 LOB(기간 업무) 앱을 업데이트하는 방법 구성<!-- 3568384 -->
이제 최종 사용자가 LOB(기간 업무) 앱의 업데이트된 버전을 다운로드할 수 있는 위치를 구성할 수 있습니다. 최종 사용자는 **최소 앱 버전** 조건부 시작 대화 상자에서 이 기능을 사용할 수 있습니다. 이 대화 상자는 최종 사용자에게 최소 버전의 LOB 앱으로 업데이트할지 묻는 메시지를 표시합니다. LOB APP(앱 보호 정책)의 일부로 이러한 업데이트 세부 정보를 제공해야 합니다. 이 기능은 iOS 및 Android에서 사용할 수 있습니다. iOS에서 이 기능을 사용하려면 앱을 iOS용 Intune SDK v. 10.0.7 이상과 통합(또는 래핑 도구를 사용하여 래핑)해야 합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 최종 사용자가 LOB 앱을 업데이트하는 방법을 구성하려면 앱에 관리형 앱 구성 정책과 키 `com.microsoft.intune.myappstore`가 함께 전송되어야 합니다. 전송된 값은 최종 사용자가 앱을 다운로드할 스토어를 정의합니다. 회사 포털을 통해 앱을 배포한 경우 값은 `CompanyPortal`이어야 합니다. 다른 스토어의 경우에는 전체 URL을 입력해야 합니다.

#### <a name="intune-management-extension-powershell-scripts---3734186----"></a>Intune 관리 확장 PowerShell 스크립트<!-- 3734186  -->
디바이스에서 사용자의 관리자 권한으로 실행하도록 PowerShell 스크립트를 구성할 수 있습니다. 자세한 내용은 [Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용](../apps/intune-management-extension.md) 및 [Win32 앱 관리](../apps/app-management.md)를 참조하세요.

#### <a name="android-enterprise-app-management---4459905---"></a>Android Enterprise 앱 관리<!-- 4459905 -->
IT 관리자가 Android Enterprise 관리를 보다 쉽게 구성하고 사용하도록 하기 위해 Intune에서는 일반적인 Android Enterprise 관련 앱을 Intune 관리 콘솔에 추가합니다. 다음과 같은 4개의 Android 엔터프라이즈 앱이 있습니다.

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise완전 관리형 시나리오에 사용합니다.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -2단계 인증을 사용하는 경우 계정에 로그인할 수 있도록 지원합니다.
- **[Intune 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - APP(앱 보호 정책) 및 Android Enterprise 작업 프로필 시나리오에 사용합니다.
- [관리형 홈 화면](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -Android Enterprise 전용/키오스크 시나리오에 사용합니다.

이전에는 IT 관리자가 설치 중에 이러한 앱을 [관리형 Google Play 스토어](https://play.google.com/store/apps)에서 수동으로 찾아서 승인해야 했습니다. 이와 같이 변경되어 이전의 수동 단계가 필요하지 않으므로 고객은 Android Enterprise 관리를 보다 쉽고 빠르게 사용할 수 있습니다.

관리자가 해당 Intune 테넌트를 관리형 Google Play에 먼저 연결하면 해당 Intune 앱 목록에 이러한 4개의 앱이 자동으로 추가됩니다. 자세한 내용은 [Intune 계정을 관리형 Google Play 계정에 연결](../enrollment/connect-intune-android-enterprise.md)을 참조하세요. 이미 해당 테넌트를 연결했거나 Android Enterprise를 이미 사용하고 있는 테넌트의 경우 관리자가 수행해야 할 작업이 없습니다. 이러한 4개 앱은 2019년 5월에 서비스 출시가 완료되면 7일 이내에 자동으로 표시됩니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---1533038---"></a>업데이트된 Microsoft Intune용 PFX 인증서 커넥터<!-- 1533038 -->
기존 PFX 인증서가 계속 재처리되는 문제를 해결하는 [Microsoft Intune용 PFX 인증서 커넥터](../protect/certficates-pfx-configure.md#whats-new-for-connectors)에 대한 업데이트를 릴리스했습니다. 이로 인해 커넥터가 새 요청 처리를 중지하게 됩니다.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview---3208597---"></a>Defender ATP에 대한 Intune 보안 작업(공개 미리 보기로 제공)<!-- 3208597 -->
공개 미리 보기에서 Intune을 사용하여 [Microsoft Defender ATP(Advanced Threat Protection)의 보안 작업](../protect/atp-manage-vulnerabilities.md)을 관리할 수 있습니다. 이와 같이 ATP와 통합되면 검색부터 문제 완화까지의 기간을 단축하면서 엔드포인트 취약성 및 구성 오류를 검색하고, 우선 순위를 지정하고, 수정할 수 있는 위험 기반 접근 방식이 추가됩니다.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy---3617671---idstaged--"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인<!-- 3617671   idstaged-->
많은 Windows 10 이상 디바이스에는 TPM(신뢰할 수 있는 플랫폼 모듈) 칩셋이 있습니다. 이 업데이트는 디바이스에서 TPM 칩 버전을 확인하는 새 규정 준수 설정을 포함 합니다.

[Windows 10 이상 규정 준수 정책 설정](../protect/compliance-policy-create-windows.md#device-security)에서 이 설정을 설명합니다.

적용 대상: Windows 10 이상

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices---4097904-----"></a>최종 사용자가 개인 핫스폿을 수정하지 못하게 하고 iOS 디바이스에서 Siri 서버 로깅을 사용하지 않음<!-- 4097904   -->  
iOS 디바이스에서 디바이스 제한 프로필을 만듭니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 사용자가 구성할 수 있는 다음과 같은 새 설정을 포함합니다.

- **기본 제공 앱** Siri용 서버 쪽 로깅 명령
- **무선**: 개인 핫스폿의 사용자 수정(감독 모드에서만 해당)

이러한 설정을 보려면 [iOS용 기본 제공 앱 설정](../configuration/device-restrictions-ios.md#built-in-apps) 및 [iOS용 무선 설정](../configuration/device-restrictions-ios.md#wireless)로 이동합니다.

적용 대상: iOS 12.2 이상

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices---4097905-----"></a>macOS 디바이스에 대한 새로운 강의식 앱 디바이스 제한 설정<!-- 4097905   --> 
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기**  >  **macOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 새로운 강의실 앱 설정, 스크린샷을 차단하는 옵션, iCloud 사진 라이브러리를 사용하지 않도록 설정하는 옵션을 포함합니다.

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](../configuration/device-restrictions-macos.md)으로 이동하세요.

적용 대상: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>앱 스토어 설정에 액세스하기 위한 iOS 암호 이름이 바뀜<!-- 4557891  -->
**앱 스토어에 액세스하는 데 사용할 암호** 설정 이름이 **모든 구매에 iTunes Store 암호 필요**(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼의 경우) > **디바이스 제한**(프로필 유형의 경우) > **앱 스토어, 문서 보기 및 게임**)로 바뀌었습니다.

사용 가능한 설정을 보려면 [App Store, 문서 보기, 게임 iOS 설정](../configuration/device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동합니다.

적용 대상: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview----3754134---"></a>Microsoft Defender Advanced Threat Protection 기준(미리 보기)<!--  3754134 -->
[Microsoft Defender Advanced Threat Protection](../protect/security-baseline-settings-defender-atp.md)의 보안 기준 미리 보기 설정을 추가했습니다. 사용자의 환경이 [Microsoft Defender Advanced Threat Protection](../protect/advanced-threat-protection.md#prerequisites) 사용에 대한 필수 조건을 충족하는 경우 이 기준을 사용할 수 있습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available---3605348---"></a>Windows ESP(등록 상태 페이지)가 일반 공급됨<!-- 3605348 -->
등록 상태 페이지는 이제 미리 보기가 아닙니다. 자세한 내용은 [등록 상태 페이지 설정](../enrollment/windows-enrollment-status.md)을 참조하세요.


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation---4593669---"></a>Intune 사용자 인터페이스 업데이트 - Autopilot 등록 프로필 만들기<!-- 4593669 -->
Autopilot 등록 프로필을 만들기 위한 사용자 인터페이스가 Azure 사용자 인터페이스 스타일에 맞게 업데이트되었습니다. 자세한 내용은 [Autopilot 등록 프로필 만들기](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)를 참조하세요. 앞으로는 추가 Intune 시나리오가 이 새 UI 스타일으로 업데이트됩니다.

#### <a name="enable-autopilot-reset-for-all-windows-devices---4225665---"></a>모든 Windows 디바이스에 대해 Autopilot 재설정 사용<!-- 4225665 -->
Autopilot 재설정 기능은 등록 상태 페이지를 사용하도록 구성되지 않은 경우를 비롯한 모든 Windows 디바이스에 작동합니다. 등록 상태 페이지가 초기 디바이스 등록 중에 디바이스에 맞게 구성되지 않았으므로 디바이스는 로그인 후 바로 바탕 화면을 표시합니다. 동기화가 수행되고 Intune에서 준수 상태로 나타날 때까지 최대 8시간이 걸릴 수 있습니다. 자세한 내용은 [원격 Windows Autopilot 재설정으로 디바이스 재설정](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)을 참조하세요.

#### <a name="exact-imei-format-not-required-when-searching-all-devices--30407680---"></a>모든 디바이스를 검색하는 경우 정확한 IMEI 형식이 필요하지 않음<!--30407680 -->
**모든 디바이스**를 검색할 때 IMEI 번호에 공백을 포함하지 않아도 합니다.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal--2489996---"></a>Apple 포털에서 디바이스를 삭제하면 Intune 포털에도 반영됩니다.<!--2489996 -->
Apple의 디바이스 등록 프로그램 또는 Apple 비즈니스 관리자 포털에서 디바이스를 삭제하면 다음 동기화 중에 Intune에서도 자동으로 삭제됩니다.

### <a name="the-enrollment-status-page-now-tracks-win32-apps---2714451---"></a>등록 상태 페이지에서 이제 Win32 앱 추적<!-- 2714451 -->
Windows 10 버전 1903 이상을 실행하는 디바이스에만 해당됩니다. 자세한 내용은 [등록 상태 페이지 설정](../enrollment/windows-enrollment-status.md)을 참조하세요.

### <a name="device-management"></a>디바이스 관리

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api---3295288---"></a>Graph API를 사용하여 디바이스를 대량으로 다시 설정하고 초기화<!-- 3295288 -->
이제 Graph API를 사용하여 최대 100대의 디바이스를 대량으로 다시 설정하고 초기화할 수 있습니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="the-encryption-report-is-out-of-public-preview---4587546--------"></a>암호화 보고서가 공개 미리 보기에서 제외됨<!-- 4587546      -->
[BitLocker 및 디바이스 암호화 보고서](../protect/encryption-monitor.md)는 이제 일반 공급되며, 더 이상 공개 미리 보기에 포함되지 않습니다.

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices---4050557---"></a>iOS 및 Android 디바이스에 대한 Outlook 서명 및 생체 인식 설정<!-- 4050557 -->
이제 iOS 및 Android 디바이스의 Outlook에서 기본 서명을 사용하도록 설정할지 여부를 지정할 수 있습니다. 또한 사용자가 iOS에서 Outlook의 생체 인식 설정을 변경할 수 있도록 선택할 수 있습니다.

## <a name="week-of-may-6-2019"></a>2019년 5월 6일 주

### <a name="device-configuration"></a>디바이스 구성

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices---4500808---"></a>iOS 디바이스용 F5 Access에 대한 NAC(네트워크 액세스 제어) 지원<!-- 4500808 -->

F5는 Intune의 iOS에서 F5 Access를 위한 NAC 기능을 허용하는 BIG-IP 13 업데이트를 릴리스했습니다. 이 기능을 사용하려면

- BIG-IP를 13.1.1.5 새로 고침으로 업데이트합니다. BIG-IP 14는 지원되지 않습니다.
- BIG-IP와 NAC용 Intune을 통합하세요. [개요: 개요: 엔드포인트 관리 시스템을 사용하여 디바이스 상태 검사를 위한 APM 구성](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)의 단계.
- Intune의 VPN 프로필에서 **NAC(네트워크 액세스 제어) 사용** 설정을 확인합니다.

사용 가능한 설정을 보려면 [iOS 디바이스에서 VPN 설정 구성](../configuration/vpn-settings-ios.md)으로 이동합니다.

적용 대상: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune---doc-vso-1521237----"></a>업데이트된 Microsoft Intune용 PFX 인증서 커넥터<!-- doc-vso 1521237  -->  
폴링 간격을 5분에서 30초로 낮추는 [Microsoft Intune용 PFX 인증서 커넥터](../protect/certficates-pfx-configure.md#whats-new-for-connectors)에 대한 업데이트를 릴리스했습니다.




## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
