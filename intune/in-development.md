---
title: 개발-Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 기능 개발
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e068e2c9834290b705e8e7bc2f895636415f9ba
ms.sourcegitcommit: 69aaf89140f82f344404e75a69dc59d8a1585b10
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675445"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>-2019 년 4 월 Microsoft Intune 용 개발

준비 및 계획,이 페이지를 지원 하기 위해 목록 Intune UI 업데이트 및 기능을 개발은 있지만 아직 릴리스되지 않은 경우. 또한,

- 변경 하기 전에 작업을 수행 해야 하는 것이 예정, 경우 무료 Office 메시지 센터 게시물을 게시 하겠습니다.
- 경우 기능을 프로덕션 환경에서 미리 보기로 하거나 시작 일반 공급 기능 설명 됩니다 및 또는 이동이 페이지에 [새로운 기능 페이지](whats-new.md)합니다.
- 이 페이지와 [새로운 기능 페이지](whats-new.md) 정기적으로 업데이트 됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 참조 된 [M365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) 전략적 결과물 및 타임 라인에 대 한 합니다.

> [!Note]
> 이러한 항목에는 이후 릴리스에서 제공 하는 Intune 기능에 대 한 Microsoft의 현재 예상 반영 합니다. 날짜 및 개별 기능이 변경 될 수 있습니다. 개발의 모든 항목 경우 기능 설명 페이지

**RSS 피드**: 다음(`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`) URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>로그인 설정 설정 하 고 macOS 장치에서 다시 시작 옵션 제어 <!-- 1210083 -->
MacOS 장치에서 장치 구성 프로필을 만들 수 있습니다 (**장치 구성** > **프로필** > **프로필을 만들** > 선택할 **macOS** 플랫폼용 > **장치 기능** 프로필 유형에 대해). 새 로그인 창 설정 사용자 지정 배너를 표시 하는 등이 포함 됩니다, 그리고 사용자를 로그인, 표시 또는 전원 설정 등을 숨기려면 어떻게 선택 됩니다.

현재 설정을 보려면로 이동 [macOS 장치 기능 설정](macos-device-features-settings.md)합니다.

적용 대상: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 방화벽에 대 한 고급 설정 <!-- 1311949 -->
곧 Intune을 사용 하 여 Windows Defender에 대 한 클라이언트에서 사용자 지정 방화벽 규칙을 관리할 수 있습니다. 규칙 응용 프로그램, 네트워크 주소 및 포트에 인바운드 및 아웃 바운드 동작을 지정할 수 있습니다. 

### <a name="require-app-protection-conditional-access----1634317---"></a>앱 보호 조건부 액세스가 필요한  <!--1634317 -->
사용할 수 있습니다 *필요한 앱 보호 정책*, 조건부 액세스를 사용 하 여 보호 하는 데이터를 액세스 하지 못하게 하려면 로그인을 완료 하기 전에 사용자의 앱에 적용 되는 것이 정책을 확인 합니다. 정책 assurance 처음 사용 하 여 속도가 느려질 수 있습니다, 있지만 네트워크 문제, 잘못 된 구성 관리, 또는 응용 프로그램 보호 정책을 저지 하 의도적인 활동 으로부터 보호 하기 위해 수 있습니다. 

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----16726660---"></a>온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱 배포 <!-- 16726660 -->
디바이스 컨텍스트에서 필요로 하는 온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱을 할당할 수 있습니다. 이 방식으로 비즈니스용 Microsoft Store 앱을 배포하면 디바이스의 모든 사용자에 대해 앱을 설치할 수 있습니다. 이 기능은 Windows 10 RS4 이상 데스크톱 디바이스에만 적용됩니다. 디바이스 컨텍스트에 설치하는 옵션은 MSFB 온라인 라이선스가 부여된 앱에 대한 클라이언트 앱 할당 페이지에서 사용할 수 있습니다.

### <a name="include-and-exclude-mixture-of-user-groups-and-device-groups-when-assigning-policies-and-profiles----1807547---"></a>정책 및 프로필을 할당할 때 사용자 그룹과 장치 그룹의 혼합을 제외 및 포함 <!-- 1807547 -->
준수 정책 또는 구성 프로필에 할당할 때 사용자 또는 장치를 사용 하 여 보안 그룹 할당할 수 있습니다. 포함 사용자 그룹만 제외 하는 현재 *또는* 만 장치 그룹 포함 및 제외 합니다. 포함 및 제외 그룹의 혼합와 같은 사용자 그룹을 포함할 수 없습니다 *고* 장치 그룹을 제외 합니다.

포함 하거나 다양 한 사용자 그룹 및 장치 그룹을 제외할 수 있습니다. 사용자, 그룹에 포함할 수 있으며 장치 그룹을 제외할 수 있습니다. 예를 들어, 할당 또는 사용자 그룹에 장치 구성 프로필을 배포 따르면 개인 장치를 제외 합니다.

[장치 구성 프로필을 할당](device-profile-assign.md) 사용자 그룹 및 장치 그룹에 프로필을 할당 하는 방법은 포함 되어 있습니다.

적용 대상: 모든 플랫폼

### <a name="retire-noncompliant-devices----1827291---"></a>비규격 장치 사용 중지 <!-- 1827291 -->
비규격 장치 사용 중지 하려면 새 준수 동작을 추가 하겠습니다. 비규격 장치 사용 중지에서 모든 회사 데이터를 제거 하 고도 Intune에 의해 관리에서 장치를 제거 합니다. 이 작업은 일 이내에 구성 된 값에 도달한 경우를 실행 합니다. 최소 값은 30일입니다. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>MacOS 장치에서 커널 확장에 대 한 설정 구성 <!-- 2043024 -->
MacOS 장치에서 장치 구성 프로필을 만들 수 있습니다 (**장치 구성** > **프로필** > **프로필을 만들** > 선택할 **macOS** 플랫폼에 대 한). 설정의 새 그룹을 구성 하 고 장치에서 커널 확장을 사용할 수 있습니다.

적용 대상: macOS 10.13.2 이상

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>설정 도우미 수행 중에 일부 화면을 건너뛰도록 프로필 구성 <!-- 2276470 -->
macOS 등록 프로필을 만들 때, 사용자가 설정 도우미를 수행할 때 다음 화면 중 하나를 건너뛰도록 구성할 수 있습니다.
- Android 마이그레이션
- 표시 색상
- 개인 정보 취급 방침
- iCloudStorage 새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다. 사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.
자세한 내용은 [Apple School Manager 또는 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>장치 사용자는 설치 했거나 설치 하려고 했습니다. 이러한 모든 관리 되는 앱을 볼 수 있습니다. <!-- 2352913 -->
Windows 회사 포털에 대 한 모든 관리 되는 앱 표시&ndash; 필수 및 사용 가능&ndash; 사용자의 장치에 설치 되어 있는 합니다. 보기를 시도 하 고 보류 중인 앱 설치 및 해당 현재 상태에는 사용자 수 수도 있습니다. 조직의 필수 또는 사용 가능 앱을 확인 하지 않습니다, 경우 사용자가 회사 앱 설치 되어 있는지 설명 하는 메시지가 나타납니다. 사용자가 정렬 하거나 설치 상태에서 해당 앱을 필터링 할 수 있습니다.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP 토큰에 대 한 범위 태그 <!--2371886 -->
Apple VPP 토큰 범위 태그를 추가할 수 있습니다. 동일한 범위 태그를 사용 하 여 할당 된 사용자만 해당 태그를 사용 하 여 Apple VPP 토큰에 대 한 액세스를 해야 합니다. VPP 앱 및 해당 토큰을 사용 하 여 구매 전자책 범위 태그를 상속 합니다. 범위 태그에 대 한 자세한 내용은 참조 하세요. [태그를 사용 하 여 RBAC 및 범위](scope-tags.md)합니다.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>경우 "적용 가능성 규칙"을 사용 하 여 Windows 10 장치 구성 프로필 만들기 <!-- 2549910 -->
Windows 10 장치 구성 프로필 만들기 (**장치 구성** > **프로필** > **프로필을 만들려면**  >  **Windows 10** 플랫폼에 대 한). 만들 수는 **적용 가능성 규칙** 하므로 프로필 특정 버전 또는 특정 버전에만 적용 됩니다. 예를 들어, 일부 BitLocker 설정을 사용 하도록 설정 하는 프로필을 만들 있습니다. 프로필에 추가한 후 프로필을 Windows 10 Enterprise 실행 하는 장치에만 적용 됩니다 있도록 적용 가능성 규칙을 사용 합니다.

적용 대상: 
- Windows 10 이상

### <a name="enable-win32-app-dependencies----2617348---"></a>Win32 앱 종속성을 사용 하도록 설정 <!-- 2617348 -->
공개 미리 보기-관리자로 있습니다 수 Win32 앱을 설치 하기 전에 다른 앱 종속성으로 설치 되어 있는지 필요 합니다. 특히 장치 Win32 앱을 설치 하기 전에 종속 된 앱을 설치 해야 합니다. Intune 관리 에이전트 1 또는 2 개의 추가 몇 주 서비스 1904로 업그레이드 한 후 원하는 1904 버전 (1.18.120.0 보다 큼)으로 업그레이드 한 후에이 기능이 제공 됩니다. Intune에서 선택 **클라이언트 앱** > **앱** > **추가** 표시 하는 **앱 추가** 블레이드입니다. 선택 **Windows 앱 (Win32)** 으로 **앱 유형**합니다. 자세한 내용은 [Intune 독립 실행형-Win32 앱 관리](apps-win32-app-management.md)합니다.

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Android 엔터프라이즈 장치 소유자에 대 한 새 장치 제한 설정: 사용자가 다중 앱 키오스크 모드를 실행 하는 전용 Android 엔터프라이즈 장치에서 Wi-fi 네트워크에 연결 <!--3041940 -->
관리자는 사용자가 다중 앱 키오스크 모드를 실행 하는 전용 Android 엔터프라이즈 장치에서 Bluetooth를 구성할 수 있는 새 설정을 전환 수 있습니다. Intune 콘솔에서이 설정을 보려면 **Intune** > **장치 구성을** > **프로필**  >  **프로필 만들기** > 선택 **Android Enterprise** 플랫폼용 > **장치 소유자만, 장치 제한** 프로필 유형에 대해 > **설정**   >  **장치 전용** > 선택 **다중 앱** 에서 **키오스크 모드** 설정 드롭다운 목록입니다. 옵션을 호출 **Wi-fi 구성** 수 있도록 제공 됩니다. 

적용 대상: Android 엔터프라이즈 전용 다중 앱 키오스크 모드를 실행 하는 장치입니다. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android 엔터프라이즈 장치 소유자에 대 한 새 장치 제한 설정: Bluetooth 및 전용 Android 엔터프라이즈 장치 쌍을 구성 하는 사용자가 <!--3041941 -->
관리자는 사용자가 다중 앱 키오스크 모드를 실행 하는 전용 Android 엔터프라이즈 장치에서 Bluetooth를 구성할 수 있는 새 설정을 전환 수 있습니다. Intune 콘솔에서이 설정을 보려면 **Intune** > **장치 구성을** > **프로필**  >  **프로필 만들기** > 선택 **Android Enterprise** 플랫폼용 > **장치 소유자만, 장치 제한** 프로필 유형에 대해 > **설정**   >  **장치 전용** > 선택 **다중 앱** 에서 **키오스크 모드** 설정 드롭다운 목록입니다. 옵션을 호출 **Bluetooth 구성** 수 있도록 제공 됩니다. 

적용 대상: Android 엔터프라이즈 전용 다중 앱 키오스크 모드를 실행 하는 장치입니다. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>보안 기준 상태 (공개 미리 보기) 모니터링 <!-- 3082047 --> 
모니터링 하는 경우는 *장치 상태* 에 보안 기준에 대 한 뷰는 구성 상태 기준 범주별 같은 *잠금 위에*에 *BitLocker*, 및  *브라우저*합니다. 모든 사용 가능한 기준 범주가 표시 됩니다. 각 범주에 대해 얼마나 많은 장치가 특정 기준 범주에 맞지 않는, 잘못 구성 되 또는 적용 되지 않습니다 볼 수 있습니다.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP에 대 한 Intune 보안 작업 (공개 미리 보기로 제공) <!-- 3208597 -->
공개 미리 보기로 제공 될 예정, Intune는 새로 발표 된 Microsoft Defender 위협 및 취약성 관리에 대 한 보안 작업을 곧 추가 됩니다.  이 통합을 사용 하 여 보안 작업 관리자에서 Windows Defender ATP WDATP () Intune 관리자에 게 새로운 위협 요소에 대 한 권장 되는 관리를 보다 효율적으로 통신할 수 있습니다. 보안 작업의 추가 검색 우선 순위를 지정 하 고 끝점 취약점 및 구성 오류를 해결 하는 위험 기반 접근 방식을 추가 합니다.

Intune에서 보안 작업에 대 한 자세한 내용은 블로그 게시물에 대 한 참조 [Intune 보안 작업을 사용 하 여 Microsoft Defender ATP의 위협 요소 및 취약성 관리를 확장 하려면](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)합니다. 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>만들고 OEMConfig 장치 구성 프로필을 사용 하 여 Intune에서 <!-- 3305883 -->
Intune는 OEMConfig 사용 하 여 구성 Android 엔터프라이즈 장치를 지원 합니다. 장치 구성 프로필을 만들고 OEMConfig를 사용 하 여 Android 엔터프라이즈 장치에 설정을 적용 하는 특히 (**장치 구성** > **프로필**  >  **프로필 만들기** > **Android 엔터프라이즈** 플랫폼에 대 한).

Oem에 대 한 지원은 현재 OEM 당 기준입니다. 원하는 OEMConfig 앱 OEMConfig 앱 목록에서 사용할 수 없으면 문의 `IntuneOEMConfig@microsoft.com`합니다.

적용 대상: 
- Android 엔터프라이즈

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Android 엔터프라이즈 장치 소유자에 대 한 새 장치 제한 설정 <!-- 3574254 -->
Android 엔터프라이즈 장치에서 허용 하거나, 암호 규칙을 설정 하 고, 기능과 더 제한 하는 장치 제한 프로필을 만들 수 있습니다 (**장치 구성** > **프로필**  >  **프로필 만들기** > 선택 **Android Enterprise** 플랫폼용 > **장치 소유자만 > 장치 제한** 프로필 유형에 대해). 

완전히 관리 되는 장치에 대 한 Google Play 스토어에서 앱에 대 한 액세스 허용 전체 암호 설정을 비롯 한 새로운 설정 및 더 사용할 수 있습니다. 

현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다. 

적용 대상: Android 엔터프라이즈 장치를 완벽 하 게 관리

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 장치 준수 정책에는 TPM 칩세트에 확인 <!-- 3617671 -->
많은 Windows 10 이상 장치에 게 모듈 TPM (Trusted Platform) 칩셋 합니다. 새 준수 설정은 TPM 장치가 켜져 있는지 확인 합니다.

[Windows 10 및 이후 규정 준수 정책 설정](compliance-policy-create-windows.md#windows-10-and-later-policy-settings) 현재 설정을 표시 합니다.

적용 대상: 
- Windows 10 이상

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Win32 앱을 Intune에 등록 된 설치를 구성 합니다. Azure AD 가입 장치 <!-- 3695227 -->
있습니다 수 할당 Win32 앱을 Intune에 설치할 Azure AD 등록 장치를 조인 합니다. Intune에서 Win32 앱에 대 한 자세한 내용은 참조 하세요. [Win32 앱 관리](apps-win32-app-management.md)합니다.

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender Advanced Threat Protection 기준 <!-- 3754134 -->
Windows Defender Advanced Threat Protection 설정을 구성 하는 데 새 기준을 추가할 하겠습니다.

### <a name="device-overview-shows-primary-user---794259---"></a>장치 개요 기본 사용자를 보여 줍니다. <!--794259 -->
장치 개요 페이지에는 기본 사용자 라고도 함은 사용자 장치 선호도 사용자 UDA () 표시 됩니다. 선택 된 장치에 대 한 기본 사용자를 보려면 **Intune** > **장치** > **모든 장치** > 장치를 선택 합니다. 기본 사용자의 위쪽에 표시 됩니다는 **개요** 페이지입니다.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>완전히 관리 되는 Android 엔터프라이즈 장치에 대 한 지원 확장된 <!-- 3903241, 3903244, 3903246 -->
완전히 관리 되는 Android 엔터프라이즈 장치 지원을 확장 하도록 하겠습니다 ([2019 1 월에에서 처음 발표](whats-new.md#week-of-january-14-2019) 다음을 포함 합니다.
- 준수
- 조건부 액세스
- 새 최종 사용자 앱

Android 완전 관리형 디바이스를 설정하려면 **디바이스 등록** > **Android 등록** > **회사 소유의 완전 관리형 사용자 디바이스**로 이동합니다. 미리 보기에 남아 있는 완전히 관리 되는 Android 장치에 대 한 지원 및 일부 Intune 기능이 완벽 하 게 작동 하지 않을 수 있습니다. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>Android 엔터프라이즈 작업 프로필 장치에 대 한 보고는 추가 관리 되는 Google Play 앱 <!-- 4105925 -->
Android 엔터프라이즈 작업 프로필 장치에 배포 된 관리 되는 Google Play 앱을 장치에 설치 된 앱의 특정 버전 번호를 볼 수 됩니다. 이 필수 앱에만 적용 됩니다. 이후 릴리스에서 사용할 수 있는 앱에 대 한 동일한 기능을 활성화 됩니다.

### <a name="ios-third-party-keyboards----4111843---"></a>iOS 타사 키보드 <!-- 4111843 -->
Intune 앱 보호 정책 (앱)에 대해 지원 합니다 **타사 키보드** 설정은 iOS 플랫폼 변경 때문에 종료 됩니다. Intune 관리 콘솔에서이 설정을 구성할 수 없습니다 하 고 Intune 앱 SDK에서 클라이언트에 적용 되지 않습니다.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>사용자의 Windows 업데이트에 대 한 검사 차단 <!-- 3316758 -->
Windows 업데이트에 대 한 검색에서 사용자를 차단 하는 데 사용할 수 있는 새 Windows update 링 설정을 추가 될 예정입니다. 이 설정은 포털 내에서 사용할 수 없지만 Intune Graph API를 사용 하 여 구성할 수 있습니다.

### <a name="windows-update-notifications----3316782---"></a>Windows 업데이트 알림 <!-- 3316782 -->
사용자에 게 표시 하는 Windows 업데이트 알림을 구성 하는 일을 할 수 있도록 지원 Windows 업데이트 링 구성에 추가 될 예정입니다. 이 설정은 포털 내에서 사용할 수 없지만 Intune Graph API를 사용 하 여 구성할 수 있습니다.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>IOS 용 회사 포털 등록 12 장치 사용자 변경 <!--3448635 --> 
IOS 용 회사 포털 앱 등록 화면 및 Apple iOS 12.2에에서 릴리스된 MDM 등록 변경 내용에 맞게 단계를 업데이트할 예정입니다. 업데이트 된 워크플로를 사용자에 게 이제 됩니다.

- Safari (Safari)를 통해 회사 포털 웹 사이트를 열고 회사 포털 앱에 반환 하기 전에 관리 프로필을 다운로드할 수 있습니다.
- 장치에서 관리 프로필을 설치 하려면 설정 앱을 엽니다.
- 등록을 완료 하려면 회사 포털 앱에 반환 합니다.

이러한 변경 내용을 준비 하는 방법에 대 한 자세한 내용은 참조는 [Microsoft 기술 커뮤니티 게시물](https://aka.ms/CP_changes_iOS12)합니다. 한편, 회사 포털에서 새 iOS 등록을 지원 하려면 업데이트 했습니다의 단계 [Intune에서 iOS 장치 등록](https://docs.microsoft.com/en-us/intune/ios-enroll)합니다. 이러한 문서 변경 내용을 Apple iOS 버전 12.2 출시 후 라이브 상태가 됩니다. 

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>진단 설정에 쉽게 액세스할 수 있도록 <!-- 3804627 -->
하는 새로운 옵션이 추가 될 예정 된 **감사 로그** 블레이드를 열려면 직접 사용할 수 있는 Intune 콘솔에서 모든 감사 로그 작업에는 *진단 설정* 페이지입니다.

## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


