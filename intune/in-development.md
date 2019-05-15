---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/15/2019
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
ms.openlocfilehash: aa38a684a32756d4f2c3be3b750f8e79b66e98f6
ms.sourcegitcommit: 8c795b041cd39e3896595f64f53ace48be0ec84c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59587385"
---
# <a name="in-development-for-microsoft-intune---april-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 4월

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

<!-- 1904 start-->

### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083---"></a>macOS 디바이스에서 로그인 설정 지정 및 다시 시작 옵션 제어 <!-- 1210083 -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택 > 프로필 유형에 대해 **디바이스 기능** 선택). 새 로그인 창 설정에는 사용자 지정 배너 표시, 사용자 로그인 방법 선택, 전원 설정 표시 또는 숨기기 등과 같은 항목이 포함됩니다.

현재 설정을 보려면 [macOS 디바이스 기능 설정](macos-device-features-settings.md)으로 이동하세요.

적용 대상: macOS

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 방화벽에 대한 고급 설정 <!-- 1311949 -->
곧 Intune을 사용하여 Windows Defender용 클라이언트의 사용자 지정 방화벽 규칙을 관리할 수 있습니다. 규칙은 애플리케이션, 네트워크 주소 및 포트에 대한 인바운드 및 아웃바운드 동작을 지정할 수 있습니다. 

### <a name="require-app-protection-conditional-access----1634317---"></a>앱 보호 조건부 액세스 필요  <!--1634317 -->
조건부 액세스로 보호하는 데이터에 사용자가 액세스하지 못하도록 로그인이 완료되기 전에 정책이 사용자의 앱에 적용되었는지 확인하는 *앱 보호 정책 필요*를 사용할 수 있습니다. 정책 보증은 첫 번째 사용 경험을 늦출 수 있지만 네트워크 문제, 잘못된 관리 구성 또는 애플리케이션 보호 정책을 저지하기 위한 의도적인 활동으로부터 보호하는 데 도움이 됩니다. 

### <a name="retire-noncompliant-devices----1827291---"></a>비준수 디바이스 사용 중지 <!-- 1827291 -->
비규격 디바이스를 사용 중지하기 위해 새 규정 준수 작업을 추가할 예정입니다. 비규격 디바이스를 사용 중지하면 모든 회사 데이터가 제거되고 Intune에서 관리되는 디바이스도 제거됩니다. 이 작업은 구성된 값(일)에 도달할 때 실행됩니다. 최소 값은 30일입니다. 

### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>macOS 디바이스에서 커널 확장에 대한 설정 구성 <!-- 2043024 -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택). 새로운 설정 그룹을 통해 디바이스에서 커널 확장을 구성하고 사용할 수 있습니다.

적용 대상: macOS 10.13.2 이상

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>설정 도우미 수행 중에 일부 화면을 건너뛰도록 프로필 구성 <!-- 2276470 -->
macOS 등록 프로필을 만들 때, 사용자가 설정 도우미를 수행할 때 다음 화면 중 하나를 건너뛰도록 구성할 수 있습니다.
- Android 마이그레이션
- 표시 색상
- 개인 정보 취급 방침
- iCloudStorage 새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다. 사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.
자세한 내용은 [Apple School Manager 또는 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>다바이스 사용자는 설치했거나 설치하려고 시도한 모든 관리형 앱을 볼 수 있습니다. <!-- 2352913 -->
Windows용 회사 포털은 사용자의 디바이스에 &ndash;필수 및 사용 가능한&ndash; 모든 관리형 앱을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수 있습니다. 조직에서 앱을 필수 또는 사용 가능하게 설정하지 않으면 회사 앱이 설치되지 않았다는 메시지가 사용자에게 표시됩니다. 사용자도 설치 상태별로 앱을 정렬하거나 필터링할 수 있습니다.

### <a name="scope-tags-for-apple-vpp-tokens---2371886---"></a>Apple VPP 토큰에 대한 범위 태그 <!--2371886 -->
Apple VPP 토큰에 범위 태그를 추가할 수 있습니다. 동일한 범위 태그가 할당된 사용자만 해당 태그를 사용하여 Apple VPP 토큰에 액세스할 수 있습니다. 이 토큰을 사용하여 구입한 VPP 앱 및 eBook은 해당 범위 태그를 상속합니다. 범위 태그에 대한 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 -->
Windows 10 다비이스 구성 프로필을 만듭니다(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10**). 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 대상: 
- Windows 10 이상

### <a name="enable-win32-app-dependencies----2617348---"></a>Win32 앱 종속성 사용 <!-- 2617348 -->
공개 미리 보기 - 관리자는 Win32 앱을 설치하기 전에 다른 앱이 종속성으로 설치되도록 요구할 수 있습니다. 특히 디바이스는 Win32 앱을 설치하기 전에 종속 앱을 설치해야 합니다. 이 기능은 Intune 관리 에이전트를 1904 버전(1.18.120.0보다 큼)으로 업그레이드한 후에만 사용할 수 있으며, 서비스를 1904로 업그레이드한 후 1~2주가 더 걸릴 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 **앱 추가** 블레이드를 표시합니다. **앱 유형**으로 **Windows 앱(Win32)** 을 선택합니다. 자세한 내용은 [Intune 독립 실행형 - Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-connect-to-wi-fi-networks-on-android-enterprise-dedicated-devices-running-multi-app-kiosk-mode---3041940---"></a>Android Enterprise, Device Owner에 대한 새로운 디바이스 제한 설정: 사용자가 다중 앱 키오스크 모드를 실행하는 Android Enterprise 전용 디바이스의 Wi-Fi 네트워크에 연결 <!--3041940 -->
관리자는 사용자가 다중 앱 키오스크 모드를 실행하는 Android Enterprise 전용 디바이스에서 Bluetooth를 구성할 수 있는 새로운 설정을 전환할 수 있습니다. Intune 콘솔에서 이 설정을 보려면 **Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android Enterprise** 선택 > **디바이스 소유자만, 디바이스 제한** 프로필 유형의 경우 > **설정**  > **전용 디바이스** > **키오스크 모드** 설정 드롭다운에서 **다중 앱**을 선택합니다. **Wi-Fi 구성**이라는 옵션을 사용하도록 활성화할 수 있습니다. 

적용 대상: 다중 앱 키오스크 모드를 실행하는 Android Enterprise 전용 디바이스. 

### <a name="new-device-restriction-setting-for-android-enterprise-device-owner-let-users-configure-bluetooth-and-pairing-on-android-enterprise-dedicated-devices---3041941---"></a>Android Enterprise, Device Owner에 대한 새로운 디바이스 제한 설정: 사용자가 Bluetooth 및 Android Enterprise 전용 디바이스에서 페어링하도록 구성할 수 있습니다. <!--3041941 -->
관리자는 사용자가 다중 앱 키오스크 모드를 실행하는 Android Enterprise 전용 디바이스에서 Bluetooth를 구성할 수 있는 새로운 설정을 전환할 수 있습니다. Intune 콘솔에서 이 설정을 보려면 **Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android Enterprise** 선택 > **디바이스 소유자만, 디바이스 제한** 프로필 유형의 경우 > **설정**  > **전용 디바이스** > **키오스크 모드** 설정 드롭다운에서 **다중 앱**을 선택합니다. **Bluetooth 구성**이라는 옵션을 사용하도록 활성화할 수 있습니다. 

적용 대상: 다중 앱 키오스크 모드를 실행하는 Android Enterprise 전용 디바이스. 

### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>보안 기준 모니터링 상태(공개 미리 보기) <!-- 3082047 --> 
보안 기준선에 대한 *디바이스 상태*를 모니터링하면 보기에서 *위 잠금*, *BitLocker* 및  *브라우저*와 같은 기준선 범주별로 상태가 구성됩니다. 사용 가능한 모든 기준선 범주가 표시됩니다. 각 범주에 대해 특정 기준선 범주와 일치하지 않거나 잘못 구성되었거나 적용되지 않은 디바이스 수를 확인할 수 있습니다.

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP에 대한 Intune 보안 작업(공개 미리 보기로 제공) <!-- 3208597 -->
Intune은 공개 미리 보기로 새로 발표되는 Microsoft Defender Threat & Vulnerability Management 대한 보안 작업을 곧 추가할 예정입니다.  이러한 통합을 통해 WDATP(Windows Defender ATP)의 보안 운영 관리자는 새로운 위협에 대해 권장되는 수정 사항을 Intune 관리자에게 보다 효율적으로 전달할 수 있습니다. 보안 작업을 추가하면 엔드포인트 취약점과 잘못된 구성을 검색, 우선순위 지정 및 수정하기 위한 위험 기반 접근 방식이 추가됩니다.

Intune의 보안 작업에 대한 자세한 내용은 [Intune 보안 작업을 사용하여 Microsoft Defender ATP의 위협 및 취약성 관리 확장](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)에 대한 블로그 게시물을 참조하세요. 

### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883---"></a>Intune에서 OEMConfig 디바이스 구성 프로필 만들기 및 사용 <!-- 3305883 -->
Intune은 OEMConfig를 사용하여 Android Enterprise 디바이스를 구성하는 것을 지원합니다. 특히 OEMConfig를 사용하여 디바이스 구성 프로필을 만들고, 설정을 Android Enterprise 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise**).

OEM 지원은 현재 OEM별로 제공됩니다. OEMConfig 앱 목록에서 원하는 OEMConfig 앱을 사용할 수 없는 경우 `IntuneOEMConfig@microsoft.com`에 문의하세요.

적용 대상: 
- Android 엔터프라이즈

### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254---"></a>Android Enterprise 디바이스 소유자용 새 디바이스 제한 설정 <!-- 3574254 -->
Android Enterprise 디바이스에서 디바이스 제한 프로필을 만들어 기능을 허용하거나 제한하고, 암호 규칙을 설정하는 등의 작업을 수행할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** 선택 > 프로필 유형에 대해 **디바이스 소유자만 > 디바이스 제한** 선택). 

암호 설정을 포함한 새로운 설정을 통해 Google Play 스토어에서의 완전 관리형 디바이스용 앱에 대한 전체 액세스 권한을 부여할 수 있습니다. 

현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다. 

적용 대상: Android Enterprise 완전 관리형 디바이스

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인 <!-- 3617671 -->
많은 Windows 10 이상 디바이스에는 TPM(신뢰할 수 있는 플랫폼 모듈) 칩셋이 있습니다. 새 규정 준수 설정은 TPM이 디바이스에 있는지 확인합니다.

[Windows 10 이상 규정 준수 정책 설정](compliance-policy-create-windows.md)은 현재 설정을 나열합니다.

적용 대상: 
- Windows 10 이상

### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227---"></a>Intune에 등록된 Azure AD 조인 디바이스에 설치되도록 Win32 앱 구성 <!-- 3695227 -->
Intune에 등록된 Azure AD 조인 디바이스에 설치할 Win32 앱을 할당할 수 있습니다. Intune의 Win32 앱에 대한 자세한 내용은 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender Advanced Threat Protection 기준 <!-- 3754134 -->
Windows Defender Advanced Threat Protection 설정을 구성하는 데 도움이 되는 새 기준선을 추가하겠습니다.

### <a name="device-overview-shows-primary-user---794259---"></a>디바이스 개요에 기본 사용자가 표시됨 <!--794259 -->
디바이스 개요 페이지에는 UDA(사용자 디바이스 선호도) 사용자라고도 하는 기본 사용자가 표시됩니다. 디바이스에 대한 기본 사용자를 보려면 **Intune** > **디바이스** > **모든 디바이스**를 차례로 선택한 다음, 디바이스를 선택합니다. 기본 사용자가 **개요**페이지의 위쪽에 표시됩니다.

### <a name="expanded-support-for-android-enterprise-fully-managed-devices----3903241-3903244-3903246---"></a>Android Enterprise 완전 관리형 디바이스에 대한 지원 확장 <!-- 3903241, 3903244, 3903246 -->
Android Enterprise 완전 관리형 디바이스([2019년 1월에 처음 발표](whats-new.md#week-of-january-14-2019))에 대한 지원을 다음과 같이 확장할 예정입니다.
- 준수
- 조건부 액세스
- 새 최종 사용자 앱

Android 완전 관리형 디바이스를 설정하려면 **디바이스 등록** > **Android 등록** > **회사 소유의 완전 관리형 사용자 디바이스**로 이동합니다. 완전 관리형 Android 디바이스에 대한 지원은 미리 보기로 남아 있으며, 일부 Intune 기능이 완벽하게 작동하지 않을 수 있습니다. 

### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925---"></a>관리형 Google Play 앱에서 Android Enterprise 작업 프로필 디바이스에 대한 추가 보고 <!-- 4105925 -->
Android Enterprise 작업 프로필 디바이스에 배포된 관리형 Google Play 앱의 경우 디바이스에 설치된 앱의 특정 버전 번호를 볼 수 있습니다. 이는 필수 앱에만 적용됩니다. 사용할 수 있는 앱에 대한 동일한 기능은 향후 릴리스에서 활성화됩니다.

### <a name="ios-third-party-keyboards----4111843---"></a>iOS 타사 키보드 <!-- 4111843 -->
**타사 키보드** 설정에 대한 Intune APP(앱 보호 정책) 지원은 iOS 플랫폼 변경으로 인해 종료됩니다. Intune Admin Console에서 이 설정을 구성할 수 없으며 Intune App SDK의 클라이언트에 적용할 수 없습니다.

<!-- 1903 start-->

### <a name="block-users-from-scanning-for-windows-updates----3316758---"></a>사용자의 Windows 업데이트 검색 차단 <!-- 3316758 -->
사용자가 Windows 업데이트를 검색하지 못하도록 차단하는 데 사용할 수 있는 새로운 Windows 업데이트 링 설정을 추가했습니다. 이 설정은 포털 내에서 사용할 수 없지만 Intune Graph API를 사용하여 구성할 수 있습니다.

### <a name="windows-update-notifications----3316782---"></a>Windows 업데이트 알림 <!-- 3316782 -->
사용자가 볼 수 있는 Windows Update 알림을 구성할 수 있도록 Windows Update 링 구성에 대한 지원을 추가하고 있습니다. 이 설정은 포털 내에서 사용할 수 없지만 Intune Graph API를 사용하여 구성할 수 있습니다.

### <a name="easier-access-to-diagnostic-settings----3804627---"></a>진단 설정에 보다 쉽게 액세스 <!-- 3804627 -->
*진단 설정* 페이지를 직접 여는 데 사용할 수 있는 Intune 콘솔의 모든 Audit Log 워크로드의 **감사 로그** 블레이드에 새 옵션을 추가하고 있습니다.

## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


