---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
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
ms.openlocfilehash: 7bba992c79f69a126f0199d9cdac52779910ff38
ms.sourcegitcommit: 068c4e4bc6e6d778ece4a83d000128c4d2b732db
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64910321"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 5월

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


<!-- 1905 start-->


### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Apple 포털에서 디바이스를 삭제하면 Intune 포털에도 반영됩니다. <!--2489996 -->
Apple의 디바이스 등록 프로그램 또는 Apple 비즈니스 관리자 포털에서 디바이스를 삭제하면 다음 동기화 중에 Intune에서도 자동으로 삭제됩니다.

### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>키워드 검색에 대한 기준 지원  <!-- 3082036         -->
보안 기준 프로필을 만들거나 편집하는 동안 곧 *검색*을 사용하여 콘솔에 표시되는 설정을 필터링할 수 있게 됩니다.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API를 사용하여 디바이스를 대량으로 다시 설정하고 초기화 <!-- 3295288 -->
Graph API를 사용하여 최대 100대의 디바이스를 대량으로 다시 설정하고 초기화할 수 있습니다.

### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인 <!-- 3617671 -->
많은 Windows 10 이상 디바이스에는 TPM(신뢰할 수 있는 플랫폼 모듈) 칩셋이 있습니다. 이 업데이트는 디바이스에서 TPM 칩 버전을 확인하는 새 규정 준수 설정을 포함 합니다. 

[Windows 10 이상 규정 준수 정책 설정](compliance-policy-create-windows.md#device-security)에서 이 설정을 설명합니다.

적용 대상: Windows 10 이상

### <a name="intune-management-extension-powershell-scripts-----3734186------"></a>Intune 관리 확장 PowerShell 스크립트  <!-- 3734186    -->
디바이스에서 사용자의 관리자 권한으로 실행하도록 PowerShell 스크립트를 구성할 수 있습니다. 자세한 내용은 [Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용](intune-management-extension.md)을 참조하세요.

### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-supervised-devices----4097904----"></a>최종 사용자가 개인 핫스폿을 수정하지 못하게 하고 iOS 감독 모드 디바이스에서 Siri 서버 로깅을 사용하지 않음 <!-- 4097904  --> 
iOS 디바이스에서 디바이스 제한 프로필을 만듭니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 사용자가 구성할 수 있는 다음과 같은 새 설정을 포함합니다.

- 개인 핫스폿
- Siri 서버 로깅

현재 설정을 확인하려면 [기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md)으로 이동하세요. 

적용 대상: iOS 12.2 이상

### <a name="new-classroom-app-device-restriction-settings-for-dep-enrolled-macos-devices----4097905----"></a>DEP 등록 macOS 디바이스에 대한 새로운 강의식 앱 디바이스 제한 설정 <!-- 4097905  --> 
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기**  >  **macOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 DEP 등록 디바이스에 대한 새로운 강의실 앱 설정과 iCloud 사진 라이브러리를 사용하지 않도록 설정하는 옵션을 포함합니다.

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](device-restrictions-macos.md)으로 이동하세요.

적용 대상: macOS 10.14.4 이상

### <a name="android-enterprise-app-management----4459905-idready---"></a>Android Enterprise 앱 관리 <!-- 4459905 idready -->
IT 관리자가 Android Enterprise 관리를 보다 쉽게 구성하고 사용하도록 하기 위해 Intune에서는 일반적인 Android Enterprise 관련 앱을 Intune 관리 콘솔에 추가합니다. 다음과 같은 4개의 Android Enterprise 앱이 있습니다.

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise완전 관리형 시나리오에 사용합니다.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -2단계 확인을 사용하는 경우 계정에 로그인할 때 유용합니다.
- **[Intune 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - APP(앱 보호 정책) 및 Android Enterprise 작업 프로필 시나리오에 사용합니다.
- [관리형 홈 화면](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -Android Enterprise 전용/키오스크 시나리오에 사용합니다.

이전에는 IT 관리자가 설치 중에 이러한 앱을 [관리형 Google Play 스토어](https://play.google.com/store/apps)에서 수동으로 찾아서 승인해야 했습니다. 이와 같이 변경되어 이전의 수동 단계가 필요하지 않으므로 고객은 Android Enterprise 관리를 보다 쉽고 빠르게 사용할 수 있습니다.

관리자가 해당 Intune 테넌트를 관리형 Google Play에 먼저 연결하면 해당 Intune 앱 목록에 이러한 4개의 앱이 자동으로 추가됩니다. 자세한 내용은 [Intune 계정을 관리형 Google Play 계정에 연결](connect-intune-android-enterprise.md)을 참조하세요. 이미 해당 테넌트를 연결했거나 Android Enterprise를 이미 사용하고 있는 테넌트의 경우 관리자가 수행해야 할 작업이 없습니다. 이러한 4개 앱은 2019년 5월에 서비스 출시가 완료되고 7일 이내에 자동으로 표시됩니다.

<!-- 1904 start-->

### <a name="advanced-settings-for-windows-defender-firewall----1311949---"></a>Windows Defender 방화벽에 대한 고급 설정 <!-- 1311949 -->
곧 Intune을 사용하여 Windows Defender용 클라이언트의 사용자 지정 방화벽 규칙을 관리할 수 있습니다. 규칙은 애플리케이션, 네트워크 주소 및 포트에 대한 인바운드 및 아웃바운드 동작을 지정할 수 있습니다. 


### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>다바이스 사용자는 설치했거나 설치하려고 시도한 모든 관리형 앱을 볼 수 있습니다. <!-- 2352913 -->
Windows용 회사 포털은 사용자의 디바이스에 &ndash;필수 및 사용 가능한&ndash; 모든 관리형 앱을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수 있습니다. 조직에서 앱을 필수 또는 사용 가능하게 설정하지 않으면 회사 앱이 설치되지 않았다는 메시지가 사용자에게 표시됩니다. 사용자도 설치 상태별로 앱을 정렬하거나 필터링할 수 있습니다.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 -->
Windows 10 다비이스 구성 프로필을 만듭니다(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10**). 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 대상: 
- Windows 10 이상

###  <a name="intune-security-tasks-for-defender-atp-in-public-preview----3208597---"></a>Defender ATP에 대한 Intune 보안 작업(공개 미리 보기로 제공) <!-- 3208597 -->
Intune은 공개 미리 보기로 새로 발표되는 Microsoft Defender Threat & Vulnerability Management 대한 보안 작업을 곧 추가할 예정입니다.  이러한 통합을 통해 WDATP(Windows Defender ATP)의 보안 운영 관리자는 새로운 위협에 대해 권장되는 수정 사항을 Intune 관리자에게 보다 효율적으로 전달할 수 있습니다. 보안 작업을 추가하면 엔드포인트 취약점과 잘못된 구성을 검색, 우선순위 지정 및 수정하기 위한 위험 기반 접근 방식이 추가됩니다.

Intune의 보안 작업에 대한 자세한 내용은 [Intune 보안 작업을 사용하여 Microsoft Defender ATP의 위협 및 취약성 관리 확장](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-security-tasks-extend-Microsoft-Defender-ATP-s/ba-p/369857)에 대한 블로그 게시물을 참조하세요. 

### <a name="windows-defender-advanced-threat-protection-baseline----3754134---"></a>Windows Defender Advanced Threat Protection 기준 <!-- 3754134 -->
Windows Defender Advanced Threat Protection 설정을 구성하는 데 도움이 되는 새 기준선을 추가하겠습니다.



## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


