---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 72b96714e8740fe4077583cfa5d9f148c2ee0908
ms.sourcegitcommit: f41b22f65286a64a8002e2cbe80debfdd6692278
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66469594"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. [예정된 변경](in-development.md), [중요 공지](#notices) 및 [이전 릴리스](whats-new-archive.md)에 대한 정보도 확인할 수 있습니다. 

> [!Note]
> 일부 기능은 몇 주에 걸쳐 출시될 수 있고 첫 번째 주에는 모든 고객에게 제공되지 않습니다.

**RSS 피드**: 다음 URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다. `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-may-27-2019"></a>2019년 5월 27일 주 

### <a name="app-management"></a>앱 관리

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Android 디바이스에서 잠재적으로 유해한 앱 보고 <!-- 4223162 -->
Intune은 이제 Android 디바이스에서 잠재적으로 유해한 앱에 대한 정보를 제공합니다. 

## <a name="week-of-may-20-2019"></a>2019년 5월 20일 주 

### <a name="app-management"></a>앱 관리

#### <a name="windows-company-portal-app----3316993---"></a>Windows 회사 포털 앱 <!-- 3316993 -->
이제 Windows 회사 포털 앱에 **디바이스**로 레이블이 지정된 새 페이지가 생깁니다. **디바이스** 페이지는 최종 사용자에게 등록된 모든 디바이스를 보여줍니다. 사용자는 버전 10.3.4291.0 이상을 사용할 때 회사 포털에서 이 변경 사항을 볼 수 있습니다. 회사 포털 구성에 대한 정보는 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 디바이스 OrderID 특성 이름이 그룹 태그로 변경됨 <!-- 4659453 -->

더 직관적이 되도록 Autopilot 디바이스의 **OrderID** 특성 이름이 **그룹 태그**로 변경되었습니다. CSV를 사용하여 Autopilot 디바이스 정보를 업로드하는 경우 OrderID가 아닌 열 머리글로 그룹 태그를 사용해야 합니다.  

## <a name="week-of-may-13-2019"></a>2019년 5월 13일 주 

### <a name="app-management"></a>앱 관리

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359-idready-wnready--"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함  <!-- 1927359 idready wnready-->
Apple의 회사 디바이스 등록 방법 중 하나를 통해 설정 도우미에서 이미 등록한 디바이스에서는 최종 사용자가 앱 스토어에서 회사 포털 앱을 수동으로 설치하는 경우 Intune은 더 이상 해당 회사 포털 앱을 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 

또한 iOS 회사 포털 앱에서 **디바이스 식별** 화면이 제거될 예정입니다. 따라서 조건부 액세스를 사용하거나 회사 앱을 배포하려는 관리자는 DEP 등록 프로필을 업데이트해야 합니다. 이 요구 사항은 DEP 등록이 설정 도우미에서 인증된 경우에만 적용됩니다. 이러한 경우 디바이스에 회사 포털을 푸시해야 합니다. 이렇게 하려면 **Intune** > **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 토큰 > **프로필**을 선택한 후 프로필 > **속성**을 선택하고 **회사 포털 설치**를 **예**로 설정합니다.

이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>최종 사용자가 앱 보호 정책을 사용하여 LOB(기간 업무) 앱을 업데이트하는 방법 구성 <!-- 3568384 -->
이제 최종 사용자가 LOB(기간 업무) 앱의 업데이트된 버전을 다운로드할 수 있는 위치를 구성할 수 있습니다. 최종 사용자는 **최소 앱 버전** 조건부 시작 대화 상자에서 이 기능을 사용할 수 있습니다. 이 대화 상자는 최종 사용자에게 최소 버전의 LOB 앱으로 업데이트할지 묻는 메시지를 표시합니다. LOB APP(앱 보호 정책)의 일부로 이러한 업데이트 세부 정보를 제공해야 합니다. 이 기능은 iOS 및 Android에서 사용할 수 있습니다. iOS에서 이 기능을 사용하려면 앱을 iOS용 Intune SDK v. 10.0.7 이상과 통합(또는 래핑 도구를 사용하여 래핑)해야 합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 최종 사용자가 LOB 앱을 업데이트하는 방법을 구성하려면 앱에 관리형 앱 구성 정책과 키 `com.microsoft.intune.myappstore`가 함께 전송되어야 합니다. 전송된 값은 최종 사용자가 앱을 다운로드할 스토어를 정의합니다. 회사 포털을 통해 앱을 배포한 경우 값은 `CompanyPortal`이어야 합니다. 다른 스토어의 경우에는 전체 URL을 입력해야 합니다.

#### <a name="intune-management-extension-powershell-scripts-----3734186-idready---"></a>Intune 관리 확장 PowerShell 스크립트  <!-- 3734186 idready -->
디바이스에서 사용자의 관리자 권한으로 실행하도록 PowerShell 스크립트를 구성할 수 있습니다. 자세한 내용은 [Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용](intune-management-extension.md) 및 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

#### <a name="android-enterprise-app-management----4459905---"></a>Android Enterprise 앱 관리 <!-- 4459905 -->
IT 관리자가 Android Enterprise 관리를 보다 쉽게 구성하고 사용하도록 하기 위해 Intune에서는 일반적인 Android Enterprise 관련 앱을 Intune 관리 콘솔에 추가합니다. 다음과 같은 4개의 Android Enterprise 앱이 있습니다.

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise완전 관리형 시나리오에 사용합니다.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -2단계 확인을 사용하는 경우 계정에 로그인할 때 유용합니다.
- **[Intune 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - APP(앱 보호 정책) 및 Android Enterprise 작업 프로필 시나리오에 사용합니다.
- [관리형 홈 화면](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -Android Enterprise 전용/키오스크 시나리오에 사용합니다.

이전에는 IT 관리자가 설치 중에 이러한 앱을 [관리형 Google Play 스토어](https://play.google.com/store/apps)에서 수동으로 찾아서 승인해야 했습니다. 이와 같이 변경되어 이전의 수동 단계가 필요하지 않으므로 고객은 Android Enterprise 관리를 보다 쉽고 빠르게 사용할 수 있습니다.

관리자가 해당 Intune 테넌트를 관리형 Google Play에 먼저 연결하면 해당 Intune 앱 목록에 이러한 4개의 앱이 자동으로 추가됩니다. 자세한 내용은 [Intune 계정을 관리형 Google Play 계정에 연결](connect-intune-android-enterprise.md)을 참조하세요. 이미 해당 테넌트를 연결했거나 Android Enterprise를 이미 사용하고 있는 테넌트의 경우 관리자가 수행해야 할 작업이 없습니다. 이러한 4개 앱은 2019년 5월에 서비스 출시가 완료되고 7일 이내에 자동으로 표시됩니다.

### <a name="device-configuration"></a>디바이스 구성

####  <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Defender ATP에 대한 Intune 보안 작업(공개 미리 보기로 제공)     <!-- 3208597 -->
공개 미리 보기에서 Intune을 사용하여 Microsoft Defender ATP(Advanced Threat Protection)의 보안 작업을 관리할 수 있습니다. 이와 같이 ATP와 통합되면 검색부터 문제 완화까지의 기간을 단축하면서 엔드포인트 취약성 및 구성 오류를 검색하고, 우선 순위를 지정하고, 수정할 수 있는 위험 기반 접근 방식이 추가됩니다.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인 <!-- 3617671   idstaged-->
많은 Windows 10 이상 디바이스에는 TPM(신뢰할 수 있는 플랫폼 모듈) 칩셋이 있습니다. 이 업데이트는 디바이스에서 TPM 칩 버전을 확인하는 새 규정 준수 설정을 포함 합니다. 

[Windows 10 이상 규정 준수 정책 설정](compliance-policy-create-windows.md#device-security)에서 이 설정을 설명합니다.

적용 대상: Windows 10 이상

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>최종 사용자가 개인 핫스폿을 수정하지 못하게 하고 iOS 디바이스에서 Siri 서버 로깅을 사용하지 않음 <!-- 4097904   --> 
iOS 디바이스에서 디바이스 제한 프로필을 만듭니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 사용자가 구성할 수 있는 다음과 같은 새 설정을 포함합니다.

- **기본 제공 앱** Siri용 서버 쪽 로깅 명령
- **무선**: 개인 핫스폿의 사용자 수정(감독 모드에서만 해당)

이러한 설정을 보려면 [iOS용 기본 제공 앱 설정](device-restrictions-ios.md#built-in-apps) 및 [iOS용 무선 설정](device-restrictions-ios.md#wireless)로 이동합니다.

적용 대상: iOS 12.2 이상

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>macOS 디바이스에 대한 새로운 강의식 앱 디바이스 제한 설정 <!-- 4097905   --> 
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기**  >  **macOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 새로운 강의실 앱 설정, 스크린샷을 차단하는 옵션, iCloud 사진 라이브러리를 사용하지 않도록 설정하는 옵션을 포함합니다.

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](device-restrictions-macos.md)으로 이동하세요.

적용 대상: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>앱 스토어 설정에 액세스하기 위한 iOS 암호 이름이 바뀜<!-- 4557891  -->
**앱 스토어에 액세스하는 데 사용할 암호** 설정 이름이 **모든 구매에 iTunes Store 암호 필요**(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼의 경우) > **디바이스 제한**(프로필 유형의 경우) > **앱 스토어, 문서 보기 및 게임**)로 바뀌었습니다.

사용 가능한 설정을 보려면 [App Store, 문서 보기, 게임 iOS 설정](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동합니다.

적용 대상: iOS

####  <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender Advanced Threat Protection 기준(미리 보기)  <!--  3754134 -->
[Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md)의 보안 기준 미리 보기 설정을 추가했습니다. 사용자의 환경이 [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) 사용에 대한 필수 조건을 충족하는 경우 이 기준을 사용할 수 있습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows ESP(등록 상태 페이지)가 일반 공급됨 <!-- 3605348 -->
등록 상태 페이지는 이제 미리 보기가 아닙니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune 사용자 인터페이스 업데이트 - Autopilot 등록 프로필 만들기  <!-- 4593669 -->
Autopilot 등록 프로필을 만들기 위한 사용자 인터페이스가 Azure 사용자 인터페이스 스타일에 맞게 업데이트되었습니다. 자세한 내용은 [Autopilot 등록 프로필 만들기](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile)를 참조하세요. 앞으로는 추가 Intune 시나리오가 이 새 UI 스타일으로 업데이트됩니다.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>모든 Windows 디바이스에 대해 Autopilot 재설정 사용 <!-- 4225665 -->
Autopilot 재설정 기능은 등록 상태 페이지를 사용하도록 구성되지 않은 경우를 비롯한 모든 Windows 디바이스에 작동합니다. 등록 상태 페이지가 초기 디바이스 등록 중에 디바이스에 맞게 구성되지 않았으므로 디바이스는 로그인 후 바로 바탕 화면을 표시합니다. 동기화가 수행되고 Intune에서 준수 상태로 나타날 때까지 최대 8시간이 걸릴 수 있습니다. 자세한 내용은 [원격 Windows Autopilot 재설정으로 디바이스 재설정](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)을 참조하세요.

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>모든 디바이스를 검색하는 경우 정확한 IMEI 형식이 필요하지 않음 <!--30407680 -->
**모든 디바이스**를 검색할 때 IMEI 번호에 공백을 포함하지 않아도 합니다.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Apple 포털에서 디바이스를 삭제하면 Intune 포털에도 반영됩니다. <!--2489996 -->
Apple의 디바이스 등록 프로그램 또는 Apple 비즈니스 관리자 포털에서 디바이스를 삭제하면 다음 동기화 중에 Intune에서도 자동으로 삭제됩니다.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>등록 상태 페이지에서 이제 Win32 앱 추적 <!-- 2714451 -->
Windows 10 버전 1903 이상을 실행하는 디바이스에만 해당됩니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

### <a name="device-management"></a>디바이스 관리

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API를 사용하여 디바이스를 대량으로 다시 설정하고 초기화 <!-- 3295288 -->
이제 Graph API를 사용하여 최대 100대의 디바이스를 대량으로 다시 설정하고 초기화할 수 있습니다.


### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>암호화 보고서가 공개 미리 보기에서 제외됨   <!-- 4587546      -->
[BitLocker 및 디바이스 암호화 보고서](encryption-monitor.md)는 이제 일반 공급되며, 더 이상 공개 미리 보기에 포함되지 않습니다. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>iOS 및 Android 디바이스에 대한 Outlook 서명 및 생체 인식 설정 <!-- 4050557 -->
이제 iOS 및 Android 디바이스의 Outlook에서 기본 서명을 사용하도록 설정할지 여부를 지정할 수 있습니다. 또한 사용자가 iOS에서 Outlook의 생체 인식 설정을 변경할 수 있도록 선택할 수 있습니다.

## <a name="week-of-may-6-2019"></a>2019년 5월 6일 주 

### <a name="device-configuration"></a>디바이스 구성

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>iOS 디바이스용 F5 Access에 대한 NAC(네트워크 액세스 제어) 지원 <!-- 4500808 -->

F5는 Intune의 iOS에서 F5 Access를 위한 NAC 기능을 허용하는 BIG-IP 13 업데이트를 릴리스했습니다. 이 기능을 사용하려면

- BIG-IP를 13.1.1.5 새로 고침으로 업데이트합니다. BIG-IP 14는 지원되지 않습니다.
- BIG-IP와 NAC용 Intune을 통합하세요. [개요: 개요: 엔드포인트 관리 시스템을 사용하여 디바이스 상태 검사를 위한 APM 구성](https://support.f5.com/kb/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89)의 단계.
- Intune의 VPN 프로필에서 **NAC(네트워크 액세스 제어) 사용** 설정을 확인합니다.

사용 가능한 설정을 보려면 [iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)으로 이동합니다.

적용 대상: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>업데이트된 Microsoft Intune용 PFX 인증서 커넥터 <!-- doc-vso 1521237  -->  
폴링 간격을 5분에서 30초로 낮추는 [Microsoft Intune용 PFX 인증서 커넥터](certficates-pfx-configure.md#whats-new-for-connectors)에 대한 업데이트를 릴리스했습니다.

## <a name="week-of-april-22-2019"></a>2019년 4월 22일 주

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Compliance Manager를 사용하여 Microsoft Intune에 대한 평가 만들기<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager)(다른 Microsoft 사이트 열기)는 Microsoft Service Trust Portal의 워크플로 기반 위험 평가 도구입니다. 이를 통해 Microsoft 서비스와 관련된 조직의 규정 준수 활동을 추적, 할당 및 확인할 수 있습니다. Office 365, Azure, Dynamics, 전문 서비스 및 Intune을 통해 사용자 고유의 규정 준수 평가를 만들 수 있습니다. Intune에는 FFIEC와 GDPR의 두 가지 평가가 있습니다.

Compliance Manager는 Microsoft에서 관리하는 컨트롤과 조직에서 관리하는 컨트롤을 세분화하여 노력을 집중시키는 데 도움이 됩니다. 평가를 완료한 다음, 해당 평가를 내보내고 인쇄할 수 있습니다.

[FFIEC(연방 금융 기관 심사 위원회)](https://www.microsoft.com/trustcenter/compliance/FFIEC)(다른 Microsoft 사이트 열기) 규정 준수는 FFIEC에서 발표한 온라인 뱅킹 표준 세트입니다. 이는 Intune을 사용하는 금융 기관에 대해 가장 많이 요청되는 평가입니다. Intune에서 공용 클라우드 워크로드와 관련된 FFIEC 사이버 보안 지침을 충족시키는 방법을 해석합니다. Intune의 FFIEC 평가는 Compliance Manager의 두 번째 FFIEC 평가입니다.

다음 예에서는 FFIEC 컨트롤에 대한 분석을 볼 수 있습니다. Microsoft에서 64개의 컨트롤을 담당하며, 사용자는 나머지 12개의 컨트롤을 담당하고 있습니다.

![FFIEC에 대한 Intune 평가 샘플 참조(고객 작업 및 Microsoft 작업 포함)](./media/intune-ffiec-assessment-status.png)

[GDPR(일반 데이터 보호 규정)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview)(다른 Microsoft 사이트 열기)은 개인과 해당 데이터의 권한을 보호하는 데 도움이 되는 EU(유럽 연합) 법률입니다. GDPR은 개인 정보 보호 규정을 준수하도록 지원하기 위해 가장 많이 요청되는 평가입니다. 

다음 예에서는 GDPR 컨트롤에 대한 분석을 볼 수 있습니다. Microsoft에서 49개의 컨트롤을 담당하며, 사용자는 나머지 66개의 컨트롤을 담당하고 있습니다.

![GDPR에 대한 Intune 평가 샘플 참조(고객 작업 및 Microsoft 작업 포함)](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019년 4월 15일 주

### <a name="app-management"></a>앱 관리

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Android 앱 보호 정책에 대한 OpenSSL 암호화 <!-- 3747362 -->
Android 디바이스의 Intune APP(앱 보호 정책)는 이제 FIPS 140-2 준수 OpenSSL 암호화 라이브러리를 사용합니다. 자세한 내용은 [Microsoft Intune의 Android 앱 보호 정책 설정](app-protection-policy-settings-android.md)의 [암호화](app-protection-policy-settings-android.md#encryption) 섹션을 참조하세요.

#### <a name="enable-win32-app-dependencies----2617348----"></a>Win32 앱 종속성 사용 <!-- 2617348  -->
관리자는 Win32 앱을 설치하기 전에 다른 앱이 종속성으로 설치되도록 요구할 수 있습니다. 특히 디바이스는 Win32 앱을 설치하기 전에 종속 앱을 설치해야 합니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 **앱 추가** 블레이드를 표시합니다. **앱 유형**으로 **Windows 앱(Win32)** 을 선택합니다. 앱이 추가되면 **종속성**을 선택하여 Win32 앱을 설치하기 전에 설치해야 하는 종속 앱을 추가할 수 있습니다. 자세한 내용은 [Intune 독립 실행형 - Win32 앱 관리](apps-win32-app-management.md)를 참조하세요. 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>비즈니스용 Microsoft Store 앱에 대한 앱 버전 설치 정보 <!-- 3537391   -->
앱 설치 보고서에는 비즈니스용 Microsoft Store 앱에 대한 앱 버전 정보가 포함되어 있습니다. Intune에서 **클라이언트 앱** > **앱**을 차례로 선택합니다. **비즈니스용 Microsoft Store 앱**을 선택한 다음, **모니터** 섹션 아래에서 **디바이스 설치 상태**를 선택합니다.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Win32 앱 요구 사항 규칙 추가 <!-- 3676883   -->
PowerShell 스크립트, 레지스트리 값 및 파일 시스템 정보를 기반으로 하여 요구 사항 규칙을 만들 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. 그런 다음, **앱 추가** 블레이드에서 **앱 유형**으로 **Windows 앱(Win32)** 을 선택합니다.  **요구 사항** > **추가**를 차례로 선택하여 추가 요구 사항 규칙을 구성합니다. 그런 다음, **요구 사항 유형**으로 **파일 형식**, **레지스트리** 또는 **스크립트**를 선택합니다. 자세한 내용은 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

 #### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Intune에 등록된 Azure AD 조인 디바이스에 설치되도록 Win32 앱 구성 <!-- 3695227  -->
Intune에 등록된 Azure AD 조인 디바이스에 설치할 Win32 앱을 할당할 수 있습니다. Intune의 Win32 앱에 대한 자세한 내용은 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

#### <a name="device-overview-shows-primary-user---794259----"></a>디바이스 개요에 기본 사용자가 표시됨 <!--794259  -->
디바이스 개요 페이지에는 UDA(사용자 디바이스 선호도) 사용자라고도 하는 기본 사용자가 표시됩니다. 디바이스에 대한 기본 사용자를 보려면 **Intune** > **디바이스** > **모든 디바이스**를 차례로 선택한 다음, 디바이스를 선택합니다. 기본 사용자가 **개요**페이지의 위쪽에 표시됩니다.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>관리형 Google Play 앱에서 Android Enterprise 작업 프로필 디바이스에 대한 추가 보고 <!-- 4105925  -->
Android Enterprise 작업 프로필 디바이스에 배포된 관리형 Google Play 앱의 경우 디바이스에 설치된 앱의 특정 버전 번호를 볼 수 있습니다. 이는 필수 앱에만 적용됩니다.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS 타사 키보드 <!-- 4111843   -->
**타사 키보드** 설정에 대한 Intune APP(앱 보호 정책) 지원은 iOS 플랫폼 변경으로 인해 종료되었습니다. Intune Admin Console에서 이 설정을 구성할 수 없으며 Intune App SDK의 클라이언트에 적용할 수 없습니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>macOS 디바이스에서 로그인 설정 지정 및 다시 시작 옵션 제어 <!-- 1210083  -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택 > 프로필 유형에 대해 **디바이스 기능** 선택). 이 업데이트에는 사용자 지정 배너 표시, 사용자 로그인 방법 선택, 전원 설정 표시 또는 숨기기 등과 같은 새 로그인 창 설정이 포함되어 있습니다.

이러한 설정을 보려면 [macOS 디바이스 기능 설정](macos-device-features-settings.md)으로 이동하세요.

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>다중 앱 키오스크 모드로 실행되는 Android Enterprise 디바이스 소유자 전용 디바이스에서 WiFi 구성 <!--3041940  -->
다중 앱 키오스크 모드에서 전용 디바이스로 실행 중일 때 Android Enterprise, 디바이스 소유자에서 설정을 사용하도록 설정할 수 있습니다. 이 업데이트에서는 사용자가 WiFi 네트워크를 구성하고 연결할 수 있도록 설정할 수 있습니다(**Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자만, 디바이스 제한** > **전용 디바이스** > **키오스크 모드**: **다중 앱** > **WiFi 구성**). 

구성할 수 있는 모든 설정을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상: 다중 앱 키오스크 모드로 실행되는 Android Enterprise 전용 디바이스


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>다중 앱 키오스크 모드로 실행되는 Android Enterprise 디바이스 소유자 전용 디바이스에서 Bluetooth 및 페어링 구성 <!-- 3041941  -->
다중 앱 키오스크 모드에서 전용 디바이스로 실행 중일 때 Android Enterprise, 디바이스 소유자에서 설정을 사용하도록 설정할 수 있습니다. 이 업데이트에서는 최종 사용자가 Bluetooth를 사용하도록 설정하고 Bluetooth를 통해 디바이스를 페어링하도록 허용할 수 있습니다(**Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자만, 디바이스 제한** > **전용 디바이스** > **키오스크 모드**: **다중 앱** > **Bluetooth 구성**). 

구성할 수 있는 모든 설정을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상: 다중 앱 키오스크 모드로 실행되는 Android Enterprise 전용 디바이스

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Intune에서 OEMConfig 디바이스 구성 프로필 만들기 및 사용 <!-- 3305883  -->
이 업데이트에서 Intune은 OEMConfig를 사용하여 Android Enterprise 디바이스를 구성할 수 있도록 지원합니다. 특히 OEMConfig를 사용하여 디바이스 구성 프로필을 만들고, 설정을 Android Enterprise 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise**).

OEM 지원은 현재 OEM별로 제공됩니다. OEMConfig 앱 목록에서 원하는 OEMConfig 앱을 사용할 수 없는 경우 `IntuneOEMConfig@microsoft.com`에 문의하세요.

이 기능에 대한 자세한 내용을 알아보려면 [Microsoft Intune에서 OEMConfig를 사용하여 Android Enterprise 디바이스 사용 및 관리](android-oem-configuration-overview.md)로 이동하세요.

적용 대상: Android 엔터프라이즈

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows 업데이트 알림  <!-- 3316758, 3316782  -->
Intune 콘솔에서 관리할 수 있는 두 가지 *사용자 환경 설정*이 Windows 업데이트 링 구성에 추가되었습니다. 이제 다음을 수행할 수 있습니다.
- 사용자의 [Windows 업데이트 검사](windows-update-settings.md#block-user-from-scanning-for-windows-updates)를 차단하거나 허용합니다.
- 사용자에게 표시되는 [Windows 업데이트 알림 수준](windows-update-settings.md#windows-update-notification-level)을 관리합니다.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Android Enterprise 디바이스 소유자용 새 디바이스 제한 설정 <!-- 3574254  -->
Android Enterprise 디바이스에서 디바이스 제한 프로필을 만들어 기능을 허용하거나 제한하고, 암호 규칙을 설정하는 등의 작업을 수행할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** 선택 > 프로필 유형에 대해 **디바이스 소유자만 > 디바이스 제한** 선택). 

이 업데이트에는 새 암호 설정, Google Play 스토어에서의 완전 관리형 디바이스용 앱에 대한 전체 액세스 허용 등이 포함되어 있습니다. 현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다. 

적용 대상: Android Enterprise 완전 관리형 디바이스

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인 <!-- 3617671 -->

이 기능은 지연되고 있으며 나중에 출시될 예정입니다.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Windows 10 이상 디바이스의 Microsoft Edge 브라우저에서 변경되어 업데이트된 UI <!-- 3775833   -->
디바이스 구성 프로필을 만들 때 Windows 10 이상 디바이스에서 Microsoft Edge 기능을 허용하거나 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Windows 10 이상** > 프로필 유형에 대해 **디바이스 제한** > **Microsoft Edge 브라우저**). 이 업데이트에서는 Microsoft Edge 설정을 더 자세히 설명하여 더 쉽게 이해할 수 있습니다. 

이러한 기능을 확인하려면 [Microsoft Edge 브라우저 디바이스 제한 설정](device-restrictions-windows-10.md#microsoft-edge-browser)으로 이동하세요.

적용 대상: Windows 10 이상

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Android Enterprise 완전 관리형 디바이스에 대한 지원 확장(미리 보기)  <!--   3903241, 3903244, 3903246   -->
아직 공개 미리 보기에서 Android Enterprise 완전 관리형 디바이스([2019년 1월에 처음 발표](whats-new.md#week-of-january-14-2019))에 대한 지원이 다음과 같이 확장되었습니다. 

- 완전 관리형 전용 디바이스에서 [준수 정책](compliance-policy-create-android-for-work.md)을 만들어 암호 규칙 및 운영 체제 요구 사항을 포함할 수 있습니다(**디바이스 준수** > **정책** > **정책 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자**). 

  전용 디바이스의 경우 디바이스가 **비준수**로 표시될 수 있습니다. 조건부 액세스는 전용 디바이스에서 사용할 수 없습니다. 할당된 정책을 준수하는 전용 디바이스를 가져오는 모든 태스크 또는 작업을 수행해야 합니다.

- [조건부 액세스](conditional-access.md) - Android에 적용되는 조건부 액세스 정책은 Android Enterprise 완전 관리형 디바이스에도 적용됩니다. 이제 사용자는 **Microsoft Intune 앱**을 사용하여 완전 관리형 디바이스를 Azure Active Directory에 등록할 수 있습니다. 그런 다음, 규정 준수 문제를 확인하고 해결하여 조직 리소스에 액세스합니다.

- 새 최종 사용자 앱(Microsoft Intune 앱) - **Microsoft Intune**이라는 Android 완전 관리형 디바이스용 새 최종 사용자 앱이 있습니다. 이 새 앱은 최신의 간단한 앱이며 기능적으로 회사 포털 앱과 비슷하지만 완전 관리형 디바이스를 제공합니다. 자세한 내용은 [Google Play의 Microsoft Intune 앱](https://play.google.com/store/apps/details?id=com.microsoft.intune)을 참조하세요.

Android 완전 관리형 디바이스를 설정하려면 **디바이스 등록** > **Android 등록** > **회사 소유의 완전 관리형 사용자 디바이스**로 이동합니다. 완전 관리형 Android 디바이스에 대한 지원은 미리 보기로 남아 있으며, 일부 Intune 기능이 완벽하게 작동하지 않을 수 있습니다.  

이 미리 보기에 대한 자세한 내용은 [Microsoft Intune - Android Enterprise 완전 관리형 디바이스 미리 보기 2](https://aka.ms/preview2_AE_fullymanaged) 블로그를 참조하세요.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470--wnstaged--"></a>설정 도우미 수행 중에 일부 화면을 건너뛰도록 프로필 구성 <!-- 2276470  wnstaged-->
macOS 등록 프로필을 만드는 경우 사용자가 설정 도우미를 수행할 때 다음 화면 중 하나를 건너뛰도록 구성할 수 있습니다.
- 모양
- 표시 색상
- iCloudStorage 새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다.  사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.
자세한 내용은 [Apple School Manager 또는 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>회사 iOS 디바이스를 등록할 때 대량으로 디바이스 이름 지정<!--3566569  -->
Apple의 회사 등록 방법(DEP/ABM/ASM) 중 하나를 사용할 때 들어오는 iOS 디바이스의 이름을 자동으로 지정하도록 디바이스 이름 형식을 설정할 수 있습니다. 디바이스 유형과 일련 번호가 포함된 형식을 템플릿에 지정할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > **토큰 선택** >**프로필 만들기** > **디바이스 명명 형식**을 차례로 선택합니다. 기존 프로필을 편집할 수 있지만 새로 동기화된 디바이스에만 이름이 적용됩니다.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>등록 상태 페이지에서 기본 시간 제한 메시지가 업데이트됨 <!-- 3959331 -->
ESP(등록 상태 페이지)가 ESP 프로필에 지정된 시간 제한 값을 초과할 때 사용자에게 표시되는 기본 시간 제한 메시지가 업데이트되었습니다. 새 기본 메시지는 사용자에게 표시되어 ESP 배포를 통해 수행할 다음 작업을 이해하는 데 도움이 됩니다.  

### <a name="device-management"></a>디바이스 관리

#### <a name="retire-noncompliant-devices-----1827291-----"></a>비준수 디바이스 사용 중지  <!-- 1827291   -->
이 기능은 지연되고 있으며 향후 릴리스에서 제공될 예정입니다.


### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Intune 데이터 웨어하우스 V1.0에서 베타 버전을 다시 반영하도록 변경됨 <!-- 4403765 -->
V1.0은 1808에 처음 도입되었을 때 베타 API와 상당한 차이가 있었습니다. 이러한 변경 내용은 1903에서 베타 API 버전으로 다시 반영됩니다. 베타 API 버전을 사용하는 중요한 보고서가 있으면 변경 내용을 위반하지 않도록 해당 보고서를 V1.0으로 전환하는 것이 좋습니다. 자세한 내용은 [Intune 데이터 웨어하우스 API에 대한 변경 로그](reports-changelog.md#1903-part-2)를 참조하세요.

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>보안 기준 모니터링 상태(공개 미리 보기) <!-- 3082047 --> 
보안 기준 모니터링에 [범주별 보기](security-baselines-monitor.md#per-category-view)가 추가되었습니다. (보안 기준은 미리 보기로 남아 있습니다.) 범주별 보기는 해당 범주의 각 상태 그룹에 속하는 디바이스의 비율과 함께 기준의 각 범주를 표시합니다. 이제 개별 범주와 일치하지 않거나, 잘못 구성되었거나, 적용되지 않는 디바이스의 수를 확인할 수 있습니다.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP 토큰에 대한 범위 태그 <!--2371886  -->
이제 범위 태그는 Apple VPP 토큰에 추가할 수 있습니다. 동일한 범위 태그가 할당된 사용자만 해당 태그를 사용하여 Apple VPP 토큰에 액세스할 수 있습니다. 이 토큰을 사용하여 구입한 VPP 앱 및 eBook은 해당 범위 태그를 상속합니다. 범위 태그에 대한 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.







## <a name="week-of-april-1-2019"></a>2019년 4월 1일 주

### <a name="device-configuration"></a>디바이스 구성

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>업데이트된 인증서 커넥터  <!-- ICM 113304612 -->
[Intune 인증서 커넥터와 Microsoft Intune용 PFX 인증서 커넥터](certficates-pfx-configure.md#whats-new-for-connectors) 모두에 대한 업데이트가 릴리스되었습니다. 새 릴리스에서는 몇 가지 알려진 문제를 해결합니다.  

### <a name="app-management"></a>앱 관리

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS용 회사 포털 앱의 사용자 환경 업데이트 <!-- 2536024 -->
iOS 디바이스용 회사 포털 앱의 홈페이지가 다시 디자인되었습니다. 이 변경을 통해 홈페이지에서 iOS UI 패턴을 더 잘 따르고 앱과 eBook에 대한 향상된 검색 기능도 제공합니다.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>iOS 12 디바이스 사용자에 대한 회사 포털 등록 변경 <!--3448635 -->  
iOS용 회사 포털 등록 화면 및 단계가 Apple iOS 12.2에서 릴리스된 MDM 등록 변경 내용에 맞게 업데이트되었습니다. 업데이트된 워크플로는 사용자에게 다음 작업을 요청합니다.  

* Safari가 회사 포털 앱으로 돌아가기 전에 회사 포털 웹 사이트를 열어서 관리 프로필을 다운로드하도록 허용합니다.  
* 설정 앱을 열고 관리 프로필을 해당 디바이스에 설치합니다.
* 회사 포털 앱으로 돌아가서 등록을 완료합니다.  

업데이트된 등록 단계 및 화면은 [Intune에서 iOS 디바이스 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)을 참조하세요.  

## <a name="week-of-march-25-2019"></a>2019년 3월 25일 주

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Microsoft Intune의 데이터 웨어하우스 블레이드에서 Power BI 준수 앱 지원 <!-- 4260871 -->
이전에는 **Intune 데이터 웨어하우스** 블레이드의 **Power BI 파일 다운로드** 링크에서 Intune 데이터 웨어하우스 보고서(.pbix 파일)를 다운로드했습니다. 이 보고서는 Power BI 준수 앱으로 대체되었습니다. Power BI 준수 앱에는 특별한 로드 또는 설정이 필요하지 않습니다. Power BI Online 포털에서 직접 열리며, 특별히 자격 증명에 따라 Intune 테넌트에 대한 데이터를 표시합니다. Intune에서 Intune 블레이드의 오른쪽에 있는 **Intune 데이터 웨어하우스 설정** 링크를 선택합니다. 그런 다음, **Power BI 앱 다운로드**를 클릭합니다. 자세한 내용은 [Power BI를 통해 데이터 웨어하우스에 연결](reports-proc-get-a-link-powerbi.md)을 참조하세요.

## <a name="week-of-march-18-2019"></a>2019년 3월 18일 주

### <a name="app-management"></a>앱 관리

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Microsoft Visio 및 Microsoft 프로젝트 배포 <!-- 3725386  -->
해당 앱에 대한 라이선스가 있는 경우 이제 Microsoft Intune을 사용하여 Microsoft Visio Pro for Office 365 및 Microsoft Project Online 데스크톱 클라이언트를 독립 앱으로 Windows 10 디바이스에 배포할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 **앱 추가** 블레이드를 표시합니다. **앱 추가** 블레이드에서 **앱 유형**으로 **Windows 10**을 선택합니다. 그런 다음, **앱 제품군 구성**을 선택하여 설치할 앱을 선택합니다. Windows 10 디바이스용 Office 365 앱에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](apps-add-office365.md)을 참조하세요.

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 제품 이름 변경 <!-- 3593653  -->
이제 **Microsoft Visio Pro for Office 365**는 **Microsoft Visio Online 플랜 2**로 알려집니다.  Microsoft Visio에 대한 자세한 내용은 [Visio Online 플랜 2](https://products.office.com/visio/visio-online-plan-2)를 참조하세요. Windows 10 디바이스용 Office 365 앱에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](apps-add-office365.md)을 참조하세요.

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune APP(앱 보호 정책) 문자 제한 설정 <!-- 3291302  -->
Intune 관리자는 Intune APP의 **다른 앱에서 잘라내기, 복사 및 붙여넣기 제한** 정책 설정에 대한 예외를 지정할 수 있습니다.  관리자는 관리형 앱에서 잘라내거나 복사할 수 있는 문자 수를 지정할 수 있습니다. 이 설정을 사용하면 "다른 앱에서 잘라내기, 복사 및 붙여넣기 제한" 설정에 관계없이 지정된 문자 수를 모든 앱에 공유할 수 있습니다. Android용 Intune 회사 포털 앱 버전에는 5.0.4364.0 버전 이상이 필요합니다. 자세한 내용은 [iOS 데이터 보호](app-protection-policy-settings-ios.md#data-protection), [Android 데이터 보호](app-protection-policy-settings-android.md#data-protection) 및 [클라이언트 앱 보호 로그 검토](app-protection-policy-settings-log.md#app-protection-policy-settings)를 참조하세요.

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Office ProPlus용 ODT(Office 배포 도구) XML 배포 <!-- 3192477   -->
Intune 관리 콘솔에서 Office Pro Plus 인스턴스를 만들 때 ODT(Office 배포 도구) XML을 제공할 수 있습니다. 이렇게 하면 기존 Intune UI 옵션이 사용자의 요구 사항을 충족시키지 못하는 경우 사용자 지정 가능성이 향상됩니다. 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](https://docs.microsoft.com/intune/apps-add-office365) 및 [Office 배포 도구에 대한 구성 옵션](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)을 참조하세요.

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>앱 아이콘이 자동으로 생성된 배경에 표시됨 <!-- 1429026  -->
이제 Windows 회사 포털 앱에서 앱 아이콘이 아이콘의 기준 색(감지 가능한 경우)에 따라 자동으로 생성된 배경에 표시됩니다. 해당되는 경우 이 배경은 이전에 앱 타일에 표시된 회색 테두리를 대체합니다. 이 변경은 10.3.3451.0 이후 버전의 회사 포털에서 사용자에게 표시됩니다.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Windows 대량 등록 후 회사 포털 앱을 사용하여 사용 가능한 앱 설치 <!-- 2751523   -->
[Windows 대량 등록](windows-bulk-enroll.md)(프로비저닝 패키지)을 사용하여 Intune에 등록한 Windows 디바이스는 회사 포털 앱을 사용하여 사용 가능한 앱을 설치할 수 있습니다. 회사 포털 앱에 대한 자세한 내용은 [수동으로 Windows 10 회사 포털 추가](store-apps-company-portal-app.md) 및 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

> [!Note]
> 이 기능은 아직 일부 고객에게만 배포됩니다. 대량 등록된 디바이스에서 회사 포털을 사용할 수 없는 경우 이 변경이 계정에 롤아웃될 때까지 기다려야 할 수 있습니다.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams 앱을 Office 앱 제품군의 일부로 선택할 수 있음 <!-- 3828932  -->
Microsoft Teams 앱은 Office Pro Plus 앱 제품군 설치의 일부로 포함하거나 제외할 수 있습니다. 이 기능은 Office Pro Plus 빌드 번호 16.0.11328.20116 이상에서 작동합니다. 설치를 완료하려면 사용자가 로그아웃한 다음, 디바이스에 로그인해야 합니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **Office 365 제품군** 앱 유형 중 하나를 선택한 다음, **앱 제품군 구성**을 선택합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Windows 10 이상 디바이스에서 여러 앱을 키오스크 모드로 실행할 때 자동으로 앱 시작 <!-- 2351390 -->

Windows 10 이상 디바이스에서는 디바이스를 키오스크 모드로 실행하고 여러 앱을 실행할 수 있습니다. 이 업데이트에는 **자동 시작** 설정이 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Windows 10 이상** > 프로필 유형에 대해 **키오스크** > **다중 앱 키오스크**). 사용자가 디바이스에 로그인할 때 앱을 자동으로 시작하려면 이 설정을 사용합니다.

모든 키오스크 설정에 대한 목록과 설명을 보려면 [Intune에서 키오스크로 실행하는 Windows 10 이상 디바이스 설정](kiosk-settings-windows.md)을 참조하세요.

적용 대상: Windows 10 이상

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>작업 로그에는 비준수 디바이스에 대한 세부 정보도 표시됨 <!-- 4063755  -->
Intune 로그를 Azure 모니터 기능으로 라우팅할 때 작동 로그를 라우팅할 수도 있습니다. 이 업데이트에서 작업 로그는 비준수 디바이스에 대한 정보도 제공합니다. 

이 기능에 대한 자세한 내용은 [Intune에서 스토리지, 이벤트 허브 또는 로그 분석에 로그 데이터 전송](review-logs-using-azure-monitor.md)을 참조하세요.

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>더 많은 Intune 워크로드에서 로그를 Azure Monitor로 라우팅 <!-- 3804627 -->
Intune에서 Azure Monitor의 감사 및 작업 로그를 이벤트 허브, 스토리지 및 로그 분석으로 라우팅할 수 있습니다(**Intune** > **모니터링** > **진단 설정**). 이 업데이트에서 이러한 로그는 규정 준수, 구성, 클라이언트 앱 등을 포함한 Intune 워크로드에서 라우팅할 수 있습니다. 

로그를 Azure Monitor로 라우팅하는 방법에 대한 자세한 내용은 [Intune에서 스토리지, 이벤트 허브 또는 로그 분석에 로그 데이터 전송](review-logs-using-azure-monitor.md)을 참조하세요.

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Intune의 Android Zebra 디바이스에서 이동성 확장 만들기 및 사용 <!-- 3305880   -->
이 업데이트에서 Intune은 Android Zebra 디바이스 구성을 지원합니다. 특히 디바이스 구성 프로필을 만들고 StageNow에서 생성된 MX(Mobility Extensions) 프로필을 사용하여 설정을 Android Zebra 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android** > 프로필 유형에 대해 **MX 프로필(Zebra만)** ).

이 기능에 대한 자세한 내용은 [Intune에서 이동성 확장을 통해 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)를 참조하세요.

적용 대상: Android

### <a name="device-management"></a>디바이스 관리

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 디바이스에 대한 암호화 보고서(공개 미리 보기)<!-- 2351538 -->  
새 [암호화 보고서(미리 보기)](encryption-monitor.md)를 사용하여 Windows 10 디바이스에 대한 암호화 상태에 대한 세부 정보를 확인합니다. 사용 가능한 세부 정보에는 디바이스 TPM 버전, 암호화 준비 상태 및 상태, 오류 보고 등이 포함됩니다.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Intune 포털에서 BitLocker 복구 키 액세스(공개 미리 보기) <!-- 2351547   -->  
이제 Intune을 사용하여 Azure Active Directory에서 BitLocker 키 ID 및 BitLocker 복구 키에 대한 [세부 정보를 볼 수 있습니다](encryption-monitor.md).

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS 및 Android 디바이스의 Intune 시나리오에 대한 Microsoft Edge 지원 <!-- 3411007 -->
Microsoft Edge는 최종 사용자 환경에 향상된 기능을 추가하여 Intune Managed Browser와 동일한 모든 관리 시나리오를 모두 지원합니다. Intune 정책에 따라 사용하도록 설정된 Microsoft Edge 엔터프라이즈 기능에는 이중 ID, 앱 보호 정책 통합, Azure 애플리케이션 프록시 통합, 관리형 즐겨찾기 및 홈페이지 바로 가기가 포함됩니다. 자세한 내용은 [Microsoft Edge 지원](app-configuration-managed-browser.md#microsoft-edge-support)을 참조하세요.

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune Connector에서 EAS 전용 디바이스에 대한 지원 중단 <!--3105122  -->
Intune 콘솔은 Intune Connector를 사용하는 Exchange Online에 연결된 EAS 전용 디바이스를 보고 관리하는 기능을 더 이상 지원하지 않습니다. 대신 다음 옵션을 사용할 수 있습니다.
- MDM(모바일 디바이스 관리)에 디바이스 등록
- Intune 앱 보호 정책을 사용하여 디바이스 관리
- [Exchange Online의 클라이언트 및 모바일](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)에서 설명한 대로 Exchange 제어 사용

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>[name]을 사용하여 모든 디바이스 페이지에서 정확한 디바이스 검색 <!--4254930 -->
이제 정확한 디바이스 이름을 검색할 수 있습니다. **Intune** > **디바이스** > **모든 디바이스**로 차례로 이동하고, 정확히 일치하는 항목을 검색하기 위해 검색 상자에서 디바이스 이름을 {}로 묶습니다. 예를 들어 **{Device12345}** 입니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>테넌트 상태 페이지에서 추가 커넥터 지원 <!-- 3617202  -->
이제 [테넌트 상태 페이지](tenant-status.md)에서 *Windows Defender ATP(Advanced Threat Protection)* 및 다른 Mobile Threat Defense 커넥터를 포함한 추가 커넥터에 대한 상태 정보가 표시됩니다.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Intune 읽기 전용 액세스 권한을 몇 가지 Azure Active Directory 역할에 부여 <!-- 3637917  -->
Intune 읽기 전용 액세스 권한이 부여된 Azure AD 역할은 다음과 같습니다. Azure AD 역할에 부여된 권한은 Intune RBAC(역할 기반 액세스 제어)에 부여된 권한보다 우선합니다.

Intune 감사 데이터에 대한 읽기 전용 액세스:

- 규정 준수 관리자
- 준수 데이터 관리자

모든 Intune 데이터에 대한 읽기 전용 액세스:

- 보안 관리자
- 보안 운영자
- 보안 Reader

자세한 내용은 [역할 기반 액세스 제어](role-based-access-control.md)를 참조하세요.

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>iOS 앱 프로비저닝 프로필에 대한 범위 태그 <!--2934430   -->
범위 태그를 iOS 앱 프로비저닝 프로필에 추가하여 해당 범위 태그도 할당된 역할이 있는 사용자만 iOS 앱 프로비저닝 프로필에 액세스할 수 있습니다. 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>앱 구성 정책에 대한 범위 태그 <!--2371891   -->
범위 태그를 앱 구성 정책에 추가하여 해당 범위 태그도 할당된 역할이 있는 사용자만 앱 구성 정책에 액세스할 수 있습니다. 앱 구성 정책은 동일한 범위 태그가 할당된 앱만 대상으로 지정하거나 연결할 수 있습니다. 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS 및 Android 디바이스의 Intune 시나리오에 대한 Microsoft Edge 지원 <!-- 3411007 -->
Microsoft Edge는 최종 사용자 환경에 향상된 기능을 추가하여 Intune Managed Browser와 동일한 모든 관리 시나리오를 모두 지원합니다. Intune 정책에 따라 사용하도록 설정된 Microsoft Edge 엔터프라이즈 기능에는 이중 ID, 앱 보호 정책 통합, Azure 애플리케이션 프록시 통합, 관리형 즐겨찾기 및 홈페이지 바로 가기가 포함됩니다. 자세한 내용은 [Microsoft Edge 지원](app-configuration-managed-browser.md#microsoft-edge-support)을 참조하세요.

## <a name="week-of-february-25-2019"></a>2019년 2월 25일 주

### <a name="device-configuration"></a>디바이스 구성

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell 모듈 <!-- 951068  -->
Microsoft Graph를 통해 Intune API를 지원하는 Intune PowerShell 모듈은 이제 [Microsoft PowerShell 갤러리](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)에서 사용할 수 있습니다.

- [이 모듈을 사용하는 방법에 대한 세부 정보](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [이 모듈을 사용하는 시나리오 예제](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>향상된 전송 최적화 지원  <!--3183757  -->
Intune에서 전송 최적화 구성 지원이 확장되었습니다. 이제 확장된 [전송 최적화 설정](delivery-optimization-settings.md) 목록을 구성하여 Intune 콘솔에서 직접 대상을 디바이스로 지정할 수 있습니다.


## <a name="week-of-february-18-2019"></a>2019년 2월 18일 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune은 Android 디바이스에서 Google Play 보호 API를 활용함 <!-- 2577355   -->
일부 IT 관리자는 최종 사용자가 휴대폰의 루팅 또는 탈옥(jailbreaking)을 종료할 수 있는 BYOD 환경에 직면합니다. 때로는 악의가 없는 이 동작은 결국 최종 사용자 디바이스에서 조직의 데이터를 보호하기 위해 설정된 여러 Intune 정책을 무시하게 됩니다. 따라서 Intune은 등록 및 등록되지 않은 디바이스에 대한 루팅 및 탈옥 검색을 제공합니다. 이 릴리스에서 Intune은 Google Play 보호 API를 활용하여 등록되지 않은 디바이스에 대한 기존 루트 검색 검사를 추가합니다. Google은 발생하는 루트 검색 검사 전체를 공유하지 않는 반면, Intune에서는 이러한 API가 디바이스 사용자 지정을 비롯해 이전 디바이스에 최신 OS 업데이트를 가져오는 등의 갖가지 이유로 자신의 디바이스를 루팅한 사용자를 검색하기를 기대합니다. 이러한 사용자는 회사 데이터에 액세스하지 못하도록 차단되거나, 회사 계정이 앱을 사용하도록 설정된 해당 정책에서 초기화될 수 있습니다. 추가 값의 경우 IT 관리자는 Intune 앱 보호 블레이드 내에 여러 보고 업데이트를 보유하고 있습니다. "플래그가 지정된 사용자" 보고서에는 Google Play 보호의 SafetyNet API 검색을 통해 검색된 사용자가 표시되며, "잠재적으로 위험한 앱" 보고서에는 Google의 Verify Apps API 검색을 통해 검색된 앱이 표시됩니다. 이 기능은 Android에서 사용할 수 있습니다.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>문제 해결 블레이드에서 사용할 수 있는 Win32 앱 정보 <!-- 2617342   -->
이제 Intune 앱 **문제 해결** 블레이드에서 Win32 앱 설치에 대한 오류 로그 파일을 수집할 수 있습니다. 앱 설치 문제 해결에 대한 자세한 내용은 [앱 설치 문제 해결](troubleshoot-app-install.md) 및 [Win32 앱 문제 해결](apps-win32-app-management.md#troubleshoot-win32-app-issues)을 참조하세요.

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>iOS 앱에 대한 앱 상태 세부 정보 <!-- 3761235   -->
다음과 관련된 새로운 앱 설치 오류 메시지가 있습니다.
- 공유 iPad에 설치하는 경우 VPP 앱의 오류
- 앱 스토어를 사용하지 않도록 설정하는 경우의 오류
- 앱용 VPP 라이선스를 찾지 못하는 오류
- MDM 공급 기업을 통해 시스템 앱을 설치하지 못하는 오류
- 디바이스가 분실 모드 또는 키오스크 모드에 있는 경우 앱을 설치하지 못하는 오류
- 사용자가 앱 스토어에 로그인하지 않은 경우 앱을 설치하지 못하는 오류

Intune에서 **클라이언트 앱** > **앱** > "애플리케이션 이름" > **디바이스 설치 상태**를 선택합니다. 새 오류 메시지는 **상태 세부 정보** 열에서 사용할 수 있습니다.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Windows 10용 회사 포털 앱의 새 앱 범주 화면<!-- 3834780  -->
Windows 10용 회사 포털의 앱 찾아보기 및 선택 환경을 개선하기 위해 **앱 범주**라는 새 화면이 추가되었습니다. 이제 앱이 **추천**, **교육용**, **생산성** 등의 범주에 따라 정렬되어 사용자에게 표시됩니다. 이 변경은 회사 포털 버전 10.3.3451.0 이상에서 나타납니다. 새 화면을 보려면 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)을 참조하세요. 회사 포털의 앱에 대한 자세한 내용은 [디바이스에 앱 설치 및 공유](/intune-user-help/install-apps-cpapp-windows)를 참조하세요.  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI 준수 앱 <!-- 1455231 doc-work-item -->
[Intune 준수(데이터 웨어하우스)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 앱을 사용하여 Power BI Online에서 Intune 데이터 웨어하우스에 액세스합니다. 이제 이 Power BI 앱을 사용하면 설정할 필요 없이 웹 브라우저를 떠나지 않고도 미리 만들어진 보고서에 액세스하고 공유할 수 있습니다. 자세한 내용은 [변경 로그 - Power BI 준수 앱](reports-changelog.md#power-bi-compliance-app)을 참조하세요.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell 스크립트가 64비트 디바이스의 64비트 호스트에서 실행될 수 있음 <!-- 1862675   -->
디바이스 구성 프로필에 PowerShell 스크립트를 추가한 경우 해당 스크립트는 항상 32비트, 심지어 64비트 운영 체제에서도 실행됩니다. 이 업데이트를 사용하여 관리자는 64비트 디바이스의 64비트 PowerShell 호스트에서 스크립트를 실행할 수 있습니다(**디바이스 구성** > **PowerShell 스크립트** > **추가** > **구성** > **64비트 PowerShell 호스트에서에서 스크립트 실행**).

PowerShell을 사용하는 방법에 대한 자세한 내용은 [Intune의 PowerShell 스크립트](intune-management-extension.md)를 참조하세요.

적용 대상: Windows 10 이상

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS 사용자에게 암호를 업데이트하라는 메시지가 표시됨 <!-- 1873216 -->
Intune에서 **ChangeAtNextAuth** 설정을 macOS 디바이스에 적용하고 있습니다. 이 설정은 규정 준수 암호 정책 또는 디바이스 제한 암호 프로필이 있는 최종 사용자 및 디바이스에 영향을 줍니다. 최종 사용자에게 암호를 업데이트하라는 메시지가 표시됩니다. 사용자가 디바이스에 로그인하는 것처럼 인증이 필요한 작업을 처음 실행할 때마다 이 프롬프트가 발생합니다. 또한 키 집합 액세스 요청처럼 관리 권한이 필요한 작업을 수행할 때 해당 암호를 업데이트하라는 메시지가 사용자에게 표시될 수 있습니다. 

관리자가 새 암호 또는 기존 암호 정책을 변경하면 최종 사용자에게 자신의 암호를 업데이트하라는 메시지가 다시 표시됩니다.

적용 대상:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-----2340521----"></a>SCEP 인증서를 사용자가 없는 macOS 디바이스에 할당  <!-- 2340521  -->
디바이스 특성을 사용하는 SCEP(단순 인증서 등록 프로토콜) 인증서를 사용자 선호도가 없는 디바이스를 포함한 macOS 디바이스에 할당하고, 인증서 프로필을 Wi-Fi 또는 VPN 프로필에 연결할 수 있습니다. 이렇게 하면 Windows, iOS 및 Android를 실행하는 [사용자 선호도가 있거나 없는 디바이스에 SCEP 인증서를 이미 할당](certificates-scep-configure.md#create-a-scep-certificate-profile)해야 하는 지원이 확장됩니다.  이 업데이트에는 macOS에 대한 SCEP 인증서 프로필을 구성할 때 *디바이스*라는 인증서 종류를 선택하는 옵션이 추가되었습니다.

적용 대상: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune 조건부 액세스 UI 업데이트   <!-- 2432313   -->
Intune 콘솔에서 조건부 액세스 UI가 향상되었습니다. 확인할 수 있습니다.
-  Intune *조건부 액세스* 블레이드가 Azure Active Directory의 블레이드로 대체되었습니다. 이렇게 하면 Intune 콘솔 내에서 Azure AD 기술로 유지되는 [조건부 액세스](conditional-access.md)에 대한 전체 설정 및 구성에 액세스할 수 있습니다. 
- *온-프레미스 액세스* 블레이드의 이름이 *Exchange 액세스*로 변경되고, 이름이 변경된 이 블레이드에 *Exchange 서비스 커넥터* 설정이 재배치되었습니다.  이 변경은 [Exchange 온라인 및 온-프레미스와 관련된 세부 정보를 구성하고 모니터링](exchange-connector-install.md)하는 위치에서 통합됩니다.  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>키오스크 브라우저 및 Microsoft Edge 브라우저 앱은 Windows 10 디바이스에서 키오스크 모드로 실행될 수 있음 <!-- 2935135   -->
Windows 10 디바이스를 키오스크 모드에서 사용하여 하나 또는 여러 앱을 실행할 수 있습니다. 이 업데이트에는 다음을 포함하여 키오스크 모드에서 브라우저 앱 사용에 대한 몇 가지 변경 사항이 포함됩니다.

- Microsoft Edge 브라우저 또는 키오스크 브라우저를 추가하여 키오스크 디바이스에서 앱으로 실행합니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **Windows 10 이상** > 프로필 유형에 대한 **키오스크**).
- 다음을 포함하여 새로운 기능과 설정은 허용하거나 제한하는 데 사용할 수 있습니다(**디바이스 구성** > **프로필** > **새 프로필** > 플랫폼에 대해 **Windows 10 이상** > 프로필 유형에 대해 **디바이스 제한**).

  - Microsoft Edge 브라우저:
  - Microsoft Edge 키오스크 모드 사용
  - 유휴 시간 후 브라우저 새로 고침

 - 즐겨찾기 및 검색:
  - 검색 엔진 변경 허용

이러한 설정 목록은 다음을 참조하세요.

- [키오스크로 실행되는 Windows 10 이상 디바이스 설정](kiosk-settings-windows.md)
- [Microsoft Edge 브라우저 디바이스 제한](device-restrictions-windows-10.md#microsoft-edge-browser)
- [즐겨찾기 및 검색 디바이스 제한](device-restrictions-windows-10.md##favorites-and-search)

적용 대상: Windows 10 이상

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>iOS 및 macOS 디바이스에 대한 새 디바이스 제한 설정 <!-- 3448774   -->
iOS 및 macOS를 실행하는 디바이스에서 일부 설정 및 기능을 제한할 수 있습니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** 또는 **macOS** > 프로필 유형에 대한 **디바이스 제한**). 이 업데이트에는 화면 시간 설정, eSIM 설정 및 셀룰러 계획 변경 등을 포함하여 iOS 디바이스에서 제어할 수 있는 더 많은 기능과 설정이 추가되었습니다. 또한 사용자의 소프트웨어 업데이트 표시를 지연시키고 macOS 디바이스의 콘텐츠 캐싱을 차단합니다. 

제한할 수 있는 기능 및 설정을 확인하려면 다음을 참조하세요.

- [iOS 디바이스 제한 설정](device-restrictions-ios.md)
- [macOS 디바이스 제한 설정](device-restrictions-macos.md)

적용 대상:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>"키오스크" 디바이스는 이제 Android Enterprise 디바이스에서 "전용 디바이스"라고 함 <!-- 3598402   -->
Android 용어에 맞게 **키오스크**가 Android Enterprise 디바이스에 대한 **전용 디바이스**로 변경되었습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise > **디바이스 소유자만** > **디바이스 제한** > **전용 디바이스**).

사용 가능한 설정을 확인하려면 [기능을 허용하거나 제한하는 디바이스 설정](device-restrictions-android-for-work.md#dedicated-device-settings)으로 이동하세요.

적용 대상:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari 및 사용자 소프트웨어 업데이트 표시 지연 iOS 설정이 Intune UI에서 이동 중 <!-- 3640850, 3803313   -->
iOS 디바이스의 경우 Safari 설정을 설정하고 소프트웨어 업데이트를 구성할 수 있습니다. 이 업데이트에서 이러한 설정은 다음과 같이 Intune UI의 다른 파트로 이동합니다.

- Safari 설정은 **Safari**(**디바이스 구성** > **프로필** > **새 프로필** > 플랫폼에 대해 **iOS** > 프로필 유형에 대해 **디바이스 제한**)에서 **[기본 제공 앱](device-restrictions-ios.md#built-in-apps)** 으로 이동합니다.
- **감독되는 iOS 디바이스에 대한 사용자 소프트웨어 업데이트 표시 지연** 설정(**소프트웨어 업데이트** > **iOS용 정책 업데이트**)은 **디바이스 제한** >  **[일반](device-restrictions-ios.md#general)** 으로 이동합니다.  기존 정책에 미치는 영향에 대한 자세한 내용은 [iOS 소프트웨어 업데이트](software-updates-ios.md#configure-the-policy)를 참조하세요. 

설정 목록은 다음을 참조하세요.

- [iOS 디바이스 제한](device-restrictions-ios.md) 
- [iOS 소프트웨어 업데이트](software-updates-ios.md)

이 기능은 다음에 적용됩니다. 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>디바이스 설정에서 제한을 사용하도록 설정하면 iOS 디바이스에서 화면 시간으로 이름이 바뀜 <!-- 3699164   -->
감독되는 iOS 디바이스의 **디바이스 설정에서 제한의 활성화**를 구성할 수 있습니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** > 프로필 유형에 대한 **디바이스 제한** > **일반**). 이 업데이트에서 이 설정은 **화면 시간(감독 모드인 경우에만)** 으로 이름이 바뀝니다. 

동작은 동일합니다. 특히: 

- iOS 11.4.1 이하: **차단**은 최종 사용자가 디바이스 설정에서 자신만의 제한을 설정하지 못하도록 방지합니다. 
- iOS 12.0 이상: **차단**은 최종 사용자가 디바이스 설정에서 콘텐츠 및 개인정보처리 제한 사항을 비롯해 자신만의 **화면 시간**을 설정하지 못하도록 방지합니다. iOS 12.0로 업그레이드된 디바이스에는 디바이스 설정의 제한 탭이 더 이상 표시되지 않습니다. 이러한 설정은 **화면 시간**에 있습니다. 

설정 목록은 [iOS 디바이스 제한](device-restrictions-ios.md#general)을 참조하세요.

적용 대상: 
- iOS


### <a name="device-management"></a>디바이스 관리

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>등록된 Windows 디바이스 이름 바꾸기 <!-- 1911112  -->
이제 등록된 Windows 10 디바이스(RS4 이상)의 이름을 바꿀 수 있습니다. 이름을 바꾸려면 **Intune** > **디바이스** > **모든 디바이스** > 디바이스 선택 > **디바이스 이름 바꾸기**를 선택합니다. 이 기능은 현재 하이브리드 Azure AD Windows 디바이스의 이름 바꾸기를 지원하지 않습니다.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>해당 범위를 사용하여 관리자가 만든 리소스에 범위 태그 자동 할당 <!-- 3173823  -->
관리자가 리소스를 만드는 경우 관리자에게 할당된 모든 범위 태그는 새 리소스에 자동으로 할당됩니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>실패한 등록 보고서가 디바이스 등록 블레이드로 이동 <!-- 3560202  -->
**실패한 등록** 보고서는 **디바이스 등록** 블레이드의 **모니터링** 섹션으로 이동되었습니다. 두 개의 열(등록 방법 및 OS 버전)이 새로 추가되었습니다.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>회사 포털 중단 보고서 이름이 사용자 등록 미완료로 변경됨 <!--3815076 eemiss -->
**회사 포털 중단** 보고서의 이름이 **사용자 등록 미완료**로 변경되었습니다.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019년 2월 4일 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune macOS 회사 포털 어둠 모드 <!-- 3300524  -->
Intune macOS 회사 포털은 이제 macOS용 어두운 모드를 지원합니다. macOS 10.14 이상 디바이스에서 어두운 모드를 활성화하면 회사 포털은 해당 모드를 리플렉션하는 색으로 모양을 조정합니다.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019년 1월 21일 주

### <a name="app-management"></a>앱 관리

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 앱에 대한 알림 메시지 <!-- 3136566   -->
앱 할당마다 최종 사용자 토스트 알림을 표시하지 않을 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > 앱 선택 > **할당** > **포함 그룹**을 선택합니다. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 앱 보호 정책 UI 업데이트 <!-- 3251427  -->
각각 더 쉽게 이해할 수 있도록 Intune 앱 보호 설정 및 단추의 레이블을 변경했습니다. 일부 변경 내용은 다음과 같습니다.  
- 컨트롤은 **예** / **아니요** 컨트롤에서 기본 **차단** / **허용** 및 **사용 안 함** / **사용** 컨트롤로 변경됩니다. 레이블도 업데이트됩니다.  
- 설정이 다시 포맷되므로 설정과 레이블이 컨트롤에 나란히 있어 더 효율적으로 검색할 수 있습니다.   

기본 설정과 설정 수는 동일하게 유지되지만, 이 변경으로 인해 사용자가 선택한 앱 보호 정책을 적용하기 위해 설정을 더 쉽게 이해, 검색 및 활용할 수 있습니다. 자세한 내용은 [iOS 설정](app-protection-policy-settings-ios.md) 및 [Android 설정](app-protection-policy-settings-android.md)을 참조하세요.

### <a name="additional-settings-for-outlook----3301182----"></a>Outlook에 대한 추가 설정 <!-- 3301182  -->
이제 Intune을 사용하여 Android 및 iOS용 Outlook에 대한 다음과 같은 설정을 추가로 구성할 수 있습니다.

- iOS 및 Android의 Outlook에서 사용할 회사 또는 학교 계정만 허용
- Office 365 및 하이브리드 최신 인증 온-프레미스 계정에 대한 최신 인증 배포
- 기본 인증을 선택한 경우 이메일 프로필의 사용자 이름 필드에 대한 `SAMAccountName` 사용
- 저장할 연락처 허용
- 외부 받는 사람 MailTips 구성
- **중요 받은 편지함** 구성
- iOS용 Outlook에 액세스하려면 생체 인식 필요
- 외부 이미지 차단

> [!NOTE]
> 회사 ID에 대한 액세스를 관리하기 위해 Intune 앱 보호 정책을 사용하는 경우 **생체 인식 필요**를 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [iOS 액세스 요구 사항](app-protection-policy-settings-ios.md#access-requirements) 및 [Android 액세스 설정](app-protection-policy-settings-android.md#access-requirements)에 **액세스하려면 회사 자격 증명 필요**를 참조하세요.

자세한 내용은 [Microsoft Outlook 구성 설정](app-configuration-policies-outlook.md)을 참조하세요.

#### <a name="delete-android-enterprise-apps----1352553---"></a>Android Enterprise 앱 삭제 <!-- 1352553 -->
Microsoft Intune에서 관리되는 Google Play 앱을 삭제할 수 있습니다. 관리되는 Google Play 앱을 삭제하려면 Azure Portal에서 Microsoft Intune을 열고 **클라이언트 앱** > **앱**을 선택합니다. 앱 목록에서 관리되는 Google Play 앱의 오른쪽에 있는 줄임표(...)를 선택한 다음, 표시된 목록에서 **삭제**를 선택합니다. 앱 목록에서 관리되는 Google Play 앱을 삭제하면 관리되는 Google Play 앱이 자동으로 승인되지 않습니다.

#### <a name="managed-google-play-app-type----1352580---"></a>관리되는 Google Play 앱 유형 <!-- 1352580 -->
**관리되는 Google Play** 앱 형식을 사용하면 [관리되는 Google Play 앱](https://play.google.com/work/search?q=microsoft&c=apps)을 Intune에 추가할 수 있습니다. Intune 관리자는 이제 Intune 내에서 승인된 관리되는 Google Play 앱을 찾고, 검색하고, 승인하며, 동기화하고 할당할 수 있습니다.  더 이상 관리되는 Google Play 콘솔을 개별적으로 찾아보지 않아도 되며 더 이상 재인증할 필요가 없습니다.  Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 유형** 목록에서 앱 유형으로 **관리되는 Google Play**를 선택합니다.

### <a name="default-android-pin-keyboard----3802457---"></a>기본 Android PIN 키보드 <!-- 3802457 -->
'숫자' PIN 형식을 사용하여 Android 디바이스에서 Intune APP(앱 보호 정책) PIN을 설정한 최종 사용자에게는 이제 이전에 설계된 고정 Android 키보드 UI 대신 기본 Android 키보드가 표시됩니다. '숫자' 및/또는 '암호' PIN 형식 모두에 대해 iOS 및 Android 디바이스 모두에서 기본 키보드를 사용하는 경우 일치하도록 이렇게 변경되었습니다. Android에서 APP PIN과 같은 최종 사용자 액세스 설정에 대한 자세한 내용은 [Android 액세스 요구 사항](app-protection-policy-settings-android.md#access-requirements)을 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>보안 기준에 Microsoft 추천 설정 사용(공개 미리 보기) <!-- 2055484   -->

Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 엔드투엔드 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 다음, 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 디바이스가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 디바이스나 사용자에 대해 관리자에게 알립니다.

이 기능은 공개 미리 보기이므로 이제 만든 모든 프로필이 일반 공급(GA)되는 보안 기준 템플릿으로 이동하지 않습니다. 프로덕션 환경에서 이러한 미리 보기 템플릿을 사용하려고 하지 말아야 합니다.

보안 기준에 대해 자세히 알아보려면 [Intune에서 Windows 10 보안 기준 만들기](security-baselines-monitor.md)를 참조하세요.

이 기능은 다음에 적용됩니다. Windows 10 이상

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>관리자가 아닌 사용자는 Azure AD에 조인된 Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 수 있음<!-- 2147379   -->
Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **Endpoint Protection**(프로필 유형) > **Windows 암호화**) BitLocker 설정을 추가합니다. 

이 업데이트에는 표준 사용자(관리자가 아닌 사용자)가 암호화를 사용하도록 설정하게 허용하는 새 BitLocker 설정이 포함됩니다. 

설정을 보려면 [Windows 10용 엔드포인트 보호 설정](endpoint-protection-windows-10.md#windows-encryption)으로 이동합니다.

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Configuration Manager 준수 확인 <!-- 2192052  eepublished  -->
이 업데이트에는 새 System Center Configuration Manager 준수 설정(**디바이스 준수** > **정책** > **정책 만들기** > **Windows 10 이상** > **Configuration Manager 준수**)이 포함됩니다. Configuration Manager는 Intune 준수에 신호를 보냅니다. 이 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 디바이스에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 디바이스의 프로그램이 알 수 없는 상태인 경우 디바이스는 Intune에서 비준수가 됩니다.

[Configuration Manager 준수](compliance-policy-create-windows.md#configuration-manager-compliance)에 이 설정이 설명되어 있습니다.

적용 대상: Windows 10 이상

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>디바이스 구성 프로필을 사용하여 감독되는 iOS 디바이스에서 배경 화면 사용자 지정 <!-- 2809324   -->
iOS 디바이스에 대한 디바이스 구성 프로필을 만드는 경우 일부 기능(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대한 **iOS** > 프로필 유형에 대한 **디바이스 기능**)을 사용자 지정할 수 있습니다. 이 업데이트에는 관리자가 홈 화면 또는 잠금 화면에 .png, .jpg 또는 .jpeg 이미지를 사용하도록 허용하는 새 **배경 무늬** 설정이 포함됩니다. 이러한 배경 무늬 설정은 감독되는 디바이스에만 적용됩니다. 

이러한 설정의 목록은 [iOS 디바이스 기능 설정](ios-device-features-settings.md)을 참조하세요.

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 키오스크가 일반 공급됨 <!-- 3594661  -->
이 업데이트에서 Windows 10 이상 디바이스의 키오스크 기능이 일반 공급(GA)됩니다. 추가 및 구성할 수 있는 모든 설정을 보려면 [Windows 10(및 이상)에 대한 키오스크 설정](kiosk-settings.md)을 참조하세요.

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Bluetooth를 통한 연락처 공유가 디바이스 제한 > Android Enterprise에 대한 디바이스 소유자에서 제거됨 <!-- 3598396   -->
Android Enterprise 디바이스용 디바이스 제한 프로필을 만들 때 **Bluetooth를 통한 연락처 공유** 설정이 있습니다. 이 업데이트에서 **Bluetooth를 통한 연락처 공유** 설정이 제거됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android Enterprise** > **디바이스 제한 사항 > 프로필 유형에 대한 디바이스 소유자** > **일반**). 

**Bluetooth를 통한 연락처 공유** 설정은 Android Enterprise 디바이스 소유자 관리에 대해 지원되지 않습니다. 따라서 이 설정을 제거하면 사용자 환경에서 이 설정을 활성화하고 구성하더라도 디비이스나 테넌트에 영향을 주지 않습니다.

현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상: Android Enterprise 디바이스 소유자

### <a name="device-management"></a>디바이스 관리

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>등록 디바이스 없이 WIP에 대한 선택적 초기화 지원 <!-- 1434452 -->
등록 없이 Windows 정보 보호(WIP-WE) 를 사용하면 고객은 전체 MDM 등록할 필요 없이 Windows 10 디바이스에서 회사 데이터를 보호할 수 있습니다. 문서가 WIP-WE 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 디바이스를 선택하고 초기화 요청을 보내면 WIP-WE 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>새 작업 로그 및 Azure Monitor 서비스에 로그 보내기 기능 <!-- 3762211  -->
Intune에는 변경 사항이 발생할 때 이벤트를 추적하는 기본 제공 감사 로깅 기능이 있습니다. 이 업데이트에는 다음을 비롯한 새 로깅 기능이 포함됩니다. 
- 성공 및 실패한 시도를 포함한 등록된 사용자 및 디바이스의 세부 정보를 표시하는 작업 로그(미리 보기).
- 감사 로그 및 작업 로그를 스토리지 계정, Event Hubs 및 Log Analytics를 비롯한 Azure Monitor에 보낼 수 있습니다. 이러한 서비스를 통해 Splunk 및 QRadar와 같은 분석을 저장하고 사용하며 로깅 데이터의 시각화를 가져올 수 있습니다.

[Intune에서 스토리지, Event Hubs 또는 Log Analytics에 로그 데이터 전송](review-logs-using-azure-monitor.md)에 이 기능에 대한 자세한 정보가 나와 있습니다.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>iOS DEP 디바이스에서 더 많은 설정 도우미 화면 건너뛰기 <!-- 2687509  -->
현재 건너뛸 수 있는 화면 외에도 사용자가 디바이스를 등록할 때 설정 도우미에서 다음 화면을 건너뛰도록 iOS DEP 디바이스를 설정할 수 있습니다. 표시음, 개인 정보, Android 마이그레이션, 홈 단추, iMessage 및 FaceTime, 온보딩, 마이그레이션 보기, 모양, 화면 시간, 소프트웨어 업데이트, SIM 설치.
건너뛸 화면을 선택하려면 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > 토큰 선택 > **프로필** > 프로필 선택 > **속성** > **설정 도우미 사용자 지정** > 건너뛸 화면의 **숨기기** 선택 > **확인**으로 이동합니다.
새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다. 사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019년 1월 14일의 주

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Android 회사 소유의 완전 관리형 디바이스 지원에 대한 미리 보기 <!-- 1574342  -->
Intune은 이제 디바이스가 IT 부서에서 긴밀하게 관리되고 개별 사용자와 관련된 회사 소유 "디바이스 소유자" 시나리오인 완전 관리형 Android 디바이스를 지원합니다. 이를 통해 관리자는 전체 디바이스를 관리하고, 확장된 범위의 정책 제어를 회사 프로필에 사용할 수 없게 할 수 있고 사용자가 관리형 Google Play의 앱만 설치하도록 제한합니다. 자세한 내용은 [Android 완전 관리형 디바이스의 Intune 등록 설정](android-fully-managed-enroll.md) 및 [전용 디바이스 또는 완전 관리형 디바이스 등록](android-dedicated-devices-fully-managed-enroll.md)을 참조하세요.  이 기능은 미리 보기에 있습니다. 인증서, 규정 준수 및 조건부 액세스와 같은 일부 Intune 기능은 현재 Android 완전 관리형 사용자 디바이스에서 사용할 수 없습니다.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019년 1월 7일의 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-app-pin----2298397---"></a>Intune 앱 PIN <!-- 2298397 -->
IT 관리자는 이제 최종 사용자의 Intune 앱 PIN을 변경해야 할 때까지 최종 사용자가 대기할 수 있는 기간(일)을 구성할 수 있습니다. 새 설정은 *다음 일마다 PIN 다시 설정*이며 Azure Portal에서 **Intune** > **클라이언트 앱** > **앱 보호 정책** > **정책 만들기** > **설정** > **액세스 요구 사항**을 선택하여 사용할 수 있습니다. [iOS](app-protection-policy-settings-ios.md) 및 [Android](app-protection-policy-settings-android.md) 디바이스에서 사용 가능하며, 이 기능은 양의 정수 값을 지원합니다.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 디바이스 보고 필드 <!-- 2748738 -->
Intune은 앱 등록 ID, Android 제조업체, 모델 및 보안 패치 버전을 포함한 추가 디바이스 보고 필드와 iOS 모델을 제공합니다. Intune에서 이러한 필드를 사용하려면 **클라이언트 앱** > **앱 보호 상태**를 선택하고 **앱 보호 보고서: iOS, Android**를 선택합니다. 또한 이러한 매개 변수를 사용하여 디바이스 제조업체(Android)의 **허용** 목록, 디바이스 모델(Android 및 iOS)의 **허용** 목록 및 최소 Android 보안 패치 버전 설정을 구성할 수 있습니다. 


### <a name="device-configuration"></a>디바이스 구성

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 있으며 자체 구성 프로필로 이동됨 <!-- 3322847 -->

Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 공개 미리 보기로 있습니다. 이 업데이트 포함:

- 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
- 관리 템플릿은 공개 미리 보기로 제공됩니다.
- 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
- 보고가 사용하도록 설정됩니다.

이 기능에 대해 자세히 알아보려면 [그룹 정책 설정을 구성하기 위한 Windows 10 템플릿](administrative-templates-windows.md)으로 이동합니다.

적용 대상: Windows 10 이상

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>S/MIME를 사용하여 사용자에 대한 여러 디바이스 암호화 및 서명  <!-- 1333642 -->
이 업데이트에는 가져온 새 인증서 프로필을 사용하는 S/MIME 이메일 암호화가 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** &gt; 플랫폼 선택 &gt; **PKCS 가져온 인증서** 프로필 유형). Intune에서 PFX 형식의 인증서를 가져올 수 있습니다. 그런 다음, Intune은 단일 사용자에 의해 등록된 여러 디바이스에 이러한 동일한 인증서를 제공할 수 있습니다. 다음도 포함되어 있습니다.
- 네이티브 iOS 이메일 프로필은 PFX 형식의 가져온 인증서를 사용하는 S/MIME 암호화 활성화를 지원합니다.
- Windows Phone 10 디바이스의 네이티브 메일 앱은 S/MIME 인증서를 자동으로 사용합니다.
- 여러 플랫폼에서 개인 인증서를 제공할 수 있습니다. 하지만 모든 이메일 앱이 S/MIME를 지원하지는 않습니다.
- 다른 플랫폼에서 S/MIME를 활성화하도록 메일 앱을 수동으로 구성해야 할 수 있습니다.  
- S/MIME 암호화를 지원하는 이메일 앱은 해당 게시자의 인증서 저장소에서 읽기와 같은 MDM에서 지원할 수 없는 방식으로 S/MIME 이메일 암호화에 대한 인증서 가져오기를 처리할 수 있습니다.
이 기능에 대한 자세한 내용은 [이메일 서명 및 암호화를 위한 S/MIME 개요](certificates-s-mime-encryption-sign.md)를 참조하세요.
지원 됩니다. Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Windows 10 이상 디바이스에서 DNS 설정을 사용할 때 자동으로 규칙을 연결하고 유지하는 새 옵션 <!-- 1333665, 2999078 -->
Windows 10 이상 디바이스에서는 contoso.com과 같은 도메인 확인을 위한 DNS 서버 목록을 포함하는 VPN 구성 프로필을 만들 수 있습니다. 이 업데이트에는 이름 확인(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **Windows 10 이상** 선택 > 프로필 유형에서 **VPN** 선택 > **DNS 설정** >**추가**)에 대한 새 설정이 포함됩니다. 
- **자동으로 연결**: **사용하도록 설정**한 경우 디바이스가 입력한 도메인(예: contoso.com)에 연결되면 디바이스가 자동으로 VPN에 연결됩니다.
- **영구**: 기본적으로 모든 NRPT(이름 확인 정책 테이블) 규칙은 디바이스가 이 VPN 프로필을 사용하여 연결되어 있는 한 활성 상태입니다. NRPT 규칙에서 이 설정이 **사용하도록 설정**되면 VPN 연결이 끊어지더라도 디바이스에서 규칙이 활성 상태로 유지됩니다. 규칙은 VPN 프로필이 제거되거나 PowerShell을 통해 규칙을 수동으로 제거할 때까지 유지됩니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에서는 설정을 설명합니다. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Windows 10 디바이스의 VPN 프로필에 신뢰할 수 있는 네트워크 검색 사용 <!-- 1500165 -->
신뢰할 수 있는 네트워크 검색을 사용하는 경우 사용자가 이미 신뢰할 수 있는 네트워크에 있을 때 VPN 프로필에서 자동으로 VPN에 연결되지 않도록 할 수 있습니다. 이 업데이트를 사용하여 DNS 접미사를 추가하여 Windows 10 이상을 실행하는 디바이스에서 신뢰할 수 있는 네트워크 검색을 사용하도록 설정할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼의 **Windows 10 이상** > 프로필 유형의 **VPN**).
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에는 현재 VPN 설정이 나열됩니다.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>여러 사용자가 사용하는 Windows Holographic for Business 디바이스 관리 <!-- 1907917, 1063203 -->
현재는 사용자 지정 OMA-URI 설정을 사용하여 Windows 10 및 Windows Holographic for Business 디바이스에서 공유 PC 설정을 구성할 수 있습니다. 이 업데이트를 사용하여 새 프로필을 추가하여 공유 디바이스 설정을 구성합니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **공유 다중 사용자 디바이스**).
이 기능에 대해 자세히 알아보려면 [공유 디바이스를 관리하기 위한 Intune 설정](shared-user-device-settings.md)으로 이동합니다.
적용 대상: Windows 10 이상, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>새 Windows 10 업데이트 설정 <!--2626030  2512994  -->
[Windows 10 업데이트 링](windows-update-for-business-configure.md)의 경우 다음을 구성할 수 있습니다.
- **자동 업데이트 동작** - 새 옵션 사용, *2018년 10월 업데이트*를 실행 중인 머신의 Windows 10 머신에서 원래 자동 업데이트 설정을 복원하도록 *기본값으로 다시 설정*
- **사용자가 Windows 업데이트를 일시 중지하는 것을 차단** - 사용자가 머신의 *설정*에서 업데이트 설치를 일시 중지하는 기능을 차단 또는 허용할 수 있는 새 소프트웨어 업데이트 설정 구성 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 이메일 프로필에서 S/MIME 서명 및 암호화를 사용할 수 있음 <!-- 2662949 -->
다양한 설정을 포함하는 이메일 프로필을 만들 수 있습니다. 이 업데이트에는 iOS 디바이스에서 이메일 통신 서명 및 암호화에 사용할 수 있는 S/MIME 설정이 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **이메일**).
[iOS 이메일 구성 설정](email-settings-ios.md)에는 설정이 나열됩니다.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>일부 BitLocker 설정에서 Windows 10 Pro 버전을 지원함<!-- 2727036 -->
BitLocker를 포함하여 Windows 10 디바이스에서 엔드포인트 보호 설정을 설정하는 구성 프로필을 만들 수 있습니다. 이 업데이트는 일부 BitLocker 설정에 대한 Windows 10 Professional Edition 지원을 추가합니다. 이러한 보호 설정을 보려면 [Windows 10용 엔드포인트 보호 설정](endpoint-protection-windows-10.md#windows-encryption)으로 이동합니다.

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>공유 디바이스 구성의 이름이 Azure Portal에서 iOS 디바이스에 대한 잠금 화면 메시지로 변경됨<!-- 2809362 -->
iOS 디바이스용 구성 프로필을 만들 경우 **공유 디바이스 구성** 설정을 추가하여 잠금 화면에 특정 텍스트를 표시할 수 있습니다. 이 업데이트에는 다음 변경 내용이 포함됩니다. 
- Azure Portal의 **공유 디바이스 구성** 설정은 “잠금 화면 메시지(감독 모드인 경우에만)”으로 이름이 바뀝니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **디바이스 기능** 선택 > **잠금 화면 메시지**).
- 잠금 화면 메시지를 추가하면 일련 번호, 디바이스 이름 또는 또 다른 디바이스별 값을 **자산 태그 정보** 및 **잠금 화면 각주**의 변수로 삽입할 수 있습니다. 예를 들어 중괄호를 사용하여 `Device name: {{devicename}}` 또는 `Serial number is {{serialnumber}}`를 입력할 수 있습니다. [iOS 토큰](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 사용 가능한 토큰이 나열됩니다.
[잠금 화면에 메시지를 표시하기 위한 설정](shared-device-settings-ios.md)에는 설정이 나열됩니다.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>iOS 디바이스에 앱 스토어, 문서 보기, 게임 디바이스 제한 설정이 새로 추가됨 <!-- 2827760-->
**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼에 대해 > **디바이스 제한** 프로필 유형에 대해 > **앱 스토어, 문서 보기, 게임**에서 다음 설정이 추가되었습니다. 관리되는 앱이 관리되지 않는 연락처 계정에 연락처를 쓸 수 있도록 허용. 관리되지 않는 앱이 관리되는 연락처 계정에서 연락처를 읽을 수 있도록 허용. 이러한 설정을 보려면 [iOS 디바이스 제한 사항](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동합니다.

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android Enterprise 디바이스 소유자 디바이스에 대한 새로운 알림, 힌트 및 keyguard 설정 <!-- 3201839 3201843 -->
이 업데이트에는 디바이스 소유자로 실행할 경우 Android 엔터프라이즈 디바이스의 여러 가지 새로운 기능이 포함됩니다. 이러한 기능을 사용하려면 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Android 엔터프라이즈** 선택 > **프로필 유형**에서 **디바이스 소유자만** 선택 > **디바이스 제한 사항**으로 이동합니다.

새로운 기능은 다음과 같습니다. 

- 들어오는 호출, 시스템 경고, 시스템 오류 등을 포함하여 시스템 알림이 표시되지 않도록 설정
- 처음 열린 앱에 대한 시작 자습서 및 힌트 건너뛰기 제안
- 카메라, 알림, 지문 잠금 해제 등의 고급 Keyguard 설정을 사용하지 않도록 설정


설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise 디바이스 소유자 디바이스에서 Always On VPN 연결을 사용할 수 있음 <!-- 3202194 -->
이 업데이트에서는 Android 엔터프라이즈 디바이스 소유자 디바이스에서 Always on VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 디바이스를 잠금 해제한 경우, 디바이스가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **디바이스 제한 사항**(디바이스 소유자만) > **연결** 설정에서 Always-on VPN을 사용하도록 설정할 수 있습니다. 설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 디바이스의 작업 관리자에서 프로세스를 종료하는 새로운 설정 <!-- 3285177 --> 
이 업데이트에는 Windows 10 디바이스의 작업 관리자를 사용하여 프로세스를 종료하는 새로운 설정이 포함됩니다. 디바이스 구성 프로필(**디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10** 선택 > **프로필 유형**에서 **디바이스 제한 사항** 선택 > **일반** 설정)을 사용하여 이 설정을 허용하거나 차단하도록 선택합니다.
이러한 설정을 보려면 [Windows 10 디바이스 제한 사항 설정](device-restrictions-windows-10.md)으로 이동합니다.
적용 대상: Windows 10 이상


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>자세한 등록 제한 오류 메시징 <!-- 3111564 -->
등록 제한 사항이 충족되지 않으면 더 자세한 오류 메시지가 제공됩니다. 이러한 메시지를 보려면 **Intune** > **문제 해결**로 이동하고 등록 실패 테이블을 확인합니다. 자세한 내용은 [등록 실패 목록](help-desk-operators.md#enrollment-failure-reference)을 참조하세요.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="tenant-status-dashboard-----1124854---"></a>테넌트 상태 대시보드  <!-- 1124854 -->
새 [테넌트 상태 페이지](tenant-status.md)는 테넌트에 대한 상태와 관련된 세부 정보를 볼 수 있는 단일 위치를 제공합니다.  대시보드는 4개 영역으로 구분됩니다.
- **테넌트 세부 정보** - 테넌트 이름 및 위치, MDM 권한, 테넌트에 등록된 총 디바이스 수, 라이선스 수를 포함하는 정보를 포함합니다. 이 섹션은 테넌트에 대한 현재 서비스 릴리스도 나열합니다.
- **커넥터 상태** - 사용자가 구성한 사용 가능한 커넥터에 대한 정보를 표시하고 아직 활성화하지 않은 항목도 나열할 수 있습니다.  
   각 커넥터의 현재 상태에 따라 정상, 경고 또는 비정상으로 플래그가 지정됩니다. 커넥터를 선택하여 세부 정보를 드릴스루하고 보거나 추가 정보를 구성합니다.
-  **Intune Service Health** - 테넌트의 활성 인시던트 또는 중단 상태에 대한 세부 정보를 표시합니다. 이 섹션의 정보는 Office Message Center에서 직접 검색됩니다.
-  **Intune 뉴스** - 테넌트에 대한 활성 메시지를 표시합니다. 메시지는 테넌트에서 최신 Intune 기능을 받는 경우 알림과 같은 항목을 포함합니다.  이 섹션의 정보는 Office Message Center에서 직접 검색됩니다.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Windows 10용 회사 포털의 새로운 도움말 및 지원 환경 <!-- 1488939-->
새 회사 포털 도움말 및 지원 페이지는 사용자가 문제를 해결하고 앱 및 액세스 문제에 대한 도움을 요청하는 데 도움이 됩니다. 새 페이지에서 오류 및 진단 로그 세부 정보에 대한 이메일을 보내고 해당 조직의 기술 지원팀 세부 정보를 찾을 수 있습니다. 또한 관련 Intune 설명서에 대한 링크를 사용하여 FAQ 섹션을 찾을 수도 있습니다. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune에 대한 새로운 도움말 및 지원 환경   <!-- #3307080 -->
다음 며칠 동안 새 도움말 및 지원 환경을 모든 테넌트에게 롤아웃합니다. 이 새로운 환경은 Intune에 대해 사용할 수 있으며 [Azure Portal](https://portal.azure.com/)에서 Intune 블레이드를 사용하는 경우에 액세스할 수 있습니다.
새 환경을 사용하면 문제를 사용자 고유의 언어로 설명하고, 문제 해결 인사이트와 웹 기반 수정 콘텐츠를 받을 수 있습니다. 이러한 솔루션은 사용자 문의에 따라 구동되는 규칙 기반 기계 학습 알고리즘을 통해 제공됩니다. 문제별 지침 외에도 새 사례 만들기 워크플로를 사용하여 이메일 또는 전화를 통해 지원 사례를 엽니다. 이 새로운 환경은 도움말 및 지원을 열 때 제공되는 콘솔의 영역에 따라 미리 선택된 옵션의 정적 집합에 대한 이전의 도움말 및 지원 환경을 대체합니다. 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](get-support.md)을 참조하세요.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-apps----1081941---"></a>앱에 대한 범위 태그 <!-- 1081941 -->
범위 태그를 만들어 역할 및 앱에 대한 액세스를 제한할 수 있습니다. 해당 범위 태그가 할당된 역할이 있는 사용자만 앱에 액세스할 수 있도록 앱에 범위 태그를 추가할 수 있습니다. 현재는 관리되는 Google Play에서 Intune에 추가된 앱 또는 Apple VPP(Volume Purchase Program)를 통해 구매한 앱에는 범위 태그를 할당할 수 없습니다(향후 지원될 예정임). 자세한 내용은 [범위 태그를 사용하여 정책 필터링](scope-tags.md)을 참조하세요.

<!-- ########################## -->
## <a name="week-of-december-10-2018"></a>2018년 12월 10일 주

### <a name="app-management"></a>앱 관리

#### <a name="updates-for-application-transport-security----748318---"></a>애플리케이션 전송 보안 업데이트 <!-- 748318 -->

Microsoft Intune은 TLS(전송 계층 보안) 1.2 이상을 지원하여 동급 최고의 암호화 기능을 제공하고, Intune의 보안을 기본적으로 강화하며, Microsoft Office 365와 같은 다른 Microsoft 서비스와 호환될 수 있도록 합니다. 이 요구 사항을 충족하기 위해 iOS 및 macOS 회사 포털은 Apple의 업데이트된 ATS(애플리케이션 전송 보안) 요구 사항(TLS 1.2 이상도 필요)을 적용합니다. ATS는 HTTPS를 통한 모든 앱 통신에서 보다 엄격한 보안을 적용하는 데 사용됩니다. 이 변경 사항은 iOS 및 macOS 회사 포털 앱을 사용하는 Intune 고객에게 영향을 줍니다. 자세한 내용은 [Intune 지원 블로그](https://aka.ms/compportalats)를 참조하세요.

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys----1832174---"></a>Intune 앱 SDK에서 256비트 암호화 키를 지원함 <!-- 1832174 -->
이제 Android용 Intune 앱 SDK는 앱 보호 정책에서 암호화를 사용하도록 설정할 때 256비트 암호화 키를 사용합니다. SDK는 이전 SDK 버전을 사용하는 콘텐츠 및 앱과 호환성을 위해 128비트 키 지원을 계속 제공합니다.

### <a name="microsoft-auto-update-version-450-required-for-macos-devices----3503442---"></a>macOS 디바이스에 Microsoft 자동 업데이트 버전 4.5.0이 필요함 <!-- 3503442 -->
회사 포털 및 기타 Office 애플리케이션에 대한 업데이트를 계속 받으려면 Intune에서 관리하는 macOS 디바이스는 Microsoft 자동 업데이트 4.5.0으로 업그레이드해야 합니다. 사용자가 해당 Office 앱에 이미 이 버전을 사용하고 있을 수 있습니다.

### <a name="intune-requires-macos-1012-or-later----2827778---"></a>Intune에 macOS 10.12 이상이 필요함 <!-- 2827778 -->
Intune에는 이제 macOS 버전 10.12 이상이 필요합니다. 이전 macOS 버전을 사용하는 디바이스는 Intune에 등록하는 데 회사 포털을 사용할 수 없습니다. 지원 및 새로운 기능을 받으려면 사용자는 해당 디바이스를 macOS 10.12 이상으로 업그레이드하고 회사 포털을 최신 버전으로 업그레이드해야 합니다.

<!-- ########################## -->
## <a name="week-of-november-26-2018"></a>2018년 11월 26일 주

### <a name="app-management"></a>앱 관리

#### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>회사 소유의 감독되는 iOS 디바이스에서 앱 제거 <!-- 1281677 -->

회사 소유의 감독되는 iOS 디바이스에서 앱을 제거할 수 있습니다. **제거** 할당 유형을 사용하여 사용자 또는 디바이스 그룹을 대상으로 하여 앱을 제거할 수 있습니다. 개인 또는 감독되지 않은 iOS 디바이스의 경우 Intune을 사용하여 설치된 앱만 계속 제거할 수 있습니다.

#### <a name="downloading-intune-win32-app-content----2617320---"></a>Intune Win32 앱 콘텐츠 다운로드 <!-- 2617320 -->
Windows 10 RS3 이상 클라이언트는 Windows 10 클라이언트의 배달 최적화 구성 요소를 사용하여 Intune Win32 앱 콘텐츠를 다운로드합니다. 배달 최적화는 기본적으로 켜져 있는 피어 투 피어 기능을 제공합니다. 현재 배달 최적화는 그룹 정책을 통해 구성될 수 있습니다. 자세한 내용은 [Windows 10 배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)를 참조하세요. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>최종 사용자 디바이스 및 앱 콘텐츠 메뉴 <!-- 2771453 -->
최종 사용자는 이제 디바이스와 앱에서 상황에 맞는 메뉴를 사용하여 디바이스 이름 바꾸기 또는 준수 확인 같은 일반적인 작업을 트리거할 수 있습니다.

#### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>관리형 홈 화면(Managed Home Screen) 앱에서 사용자 지정 배경 설정  <!-- 3041945 -->
Android 엔터프라이즈, 다중 앱, 키오스크 모드 디바이스에서 관리 홈 화면 앱의 배경 모양을 사용자 지정할 수 있는 설정을 추가합니다.  **사용자 지정 URL 배경**을 구성하려면 Azure Portal에서 Intune &gt; 디바이스 구성으로 차례로 이동합니다. 현재 디바이스 구성 프로필을 선택하거나 새 프로필을 만들어 키오스크 설정을 편집합니다.
키오스크 설정을 확인하려면 [Android Enterprise 디바이스 제한 사항](device-restrictions-android-for-work.md)을 참조하세요.

#### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>앱 보호 정책 할당 저장 및 적용 <!-- 3104570 -->
이제 [앱 보호 정책 할당](app-protection-policies.md#deploy-a-policy-to-users)을 더 효율적으로 제어할 수 있습니다. ‘할당’을 선택하여 정책 할당을 설정하거나 편집할 경우 변경을 적용하기 전에 구성을 **저장**해야 합니다.  포함 또는 제외 목록의 변경 내용을 저장하지 않고 모든 변경 내용을 지우려면 **취소**를 사용합니다.  저장 또는 취소를 선택하도록 요구하여 의도한 사용자에게만 앱 보호 정책을 할당합니다.

#### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Windows 10 이상에 대한 새 Microsoft Edge 브라우저 설정 <!-- 3174639 -->
이 업데이트에는 디바이스에서 Microsoft Edge 브라우저를 제어하고 관리하는 데 도움이 되는 새 설정이 포함됩니다. 이러한 설정 목록은 [Windows 10(이상)에 대한 디바이스 제한](device-restrictions-windows-10.md#microsoft-edge-browser)을 참조하세요.

#### <a name="new-apps-support-with-app-protection-policies----3330037---"></a>앱 보호 정책을 사용하여 새 앱 지원 <!-- 3330037 -->
이제 [Intune 앱 보호 정책](app-protection-policies.md)을 사용하여 다음 앱을 관리할 수 있습니다.
- Stream(iOS)
- To DO(Android, iOS)
- PowerApps(Android, iOS)
- Flow(Android, iOS)

앱 보호 정책을 사용하여 회사 데이터를 보호하고 다른 Intune 정책 관리 앱과 같은 앱의 데이터 전송을 제어합니다. 참고: 콘솔에 Flow가 아직 표시되지 않으면 앱 보호 정책을 만들거나 편집할 때 Flow를 추가합니다. 이렇게 하려면 **+ 추가 앱** 옵션을 사용한 다음, 입력 필드에 Flow의 *앱 ID*를 지정합니다. Android의 경우 *com.microsoft.flow*를 사용하고 iOS의 경우 *com.microsoft.procsimo*를 사용합니다.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>iOS 및 macOS 버전 번호와 빌드 번호가 표시됨 <!-- 1892471 -->
**디바이스 준수** > **디바이스 준수**에서 iOS 및 macOS 운영체제 버전이 표시되고 준수 정책에 사용할 수 있습니다. 이 업데이트에는 두 플랫폼에 모두 구성 가능한 빌드 번호가 포함됩니다.
보안 업데이트가 릴리스되는 경우 Apple에서는 일반적으로 버전 번호는 그대로 유지하지만 빌드 번호는 업데이트합니다. 준수 정책의 빌드 번호를 사용하면 취약성 업데이트가 설치되어 있는지 쉽게 확인할 수 있습니다.
이 기능을 사용하려면 [iOS](compliance-policy-create-ios.md#device-health) 및 [macOS](compliance-policy-create-mac-os.md#device-properties) 규정 준수 정책을 참조하세요.

#### <a name="update-rings-are-being-replaced-with-delivery-optimization-settings-for-windows-10-and-later----2753807---"></a>업데이트 링이 Windows 10 이상에 대한 전송 최적화 설정으로 대체 중 <!-- 2753807 -->
배달 최적화는 Windows 10 이상의 새로운 구성 프로필입니다. 이 기능은 조직의 디바이스에 소프트웨어 업데이트를 배달하는 보다 간소화된 환경을 제공합니다. 또한 이 업데이트를 통해 구성 프로필을 사용하여 새 업데이트 링과 기존 업데이트 링의 설정을 배달할 수 있습니다.
배달 최적화 구성 프로필을 구성하려면 [Windows 10 이상 배달 최적화 설정](delivery-optimization-windows.md)을 참조하세요.

#### <a name="new-device-restriction-settings-added-to-ios-and-macos-devices----2827760---"></a>새 디바이스 제한 설정이 iOS 및 macOS 디바이스에 추가됨 <!-- 2827760 -->
이 업데이트는 iOS 12와 함께 릴리스된 iOS 및 macOS 디바이스용 새 설정을 포함합니다.

**iOS 설정**: 
- 일반: 앱 제거 차단(감독 모드인 경우에만)
- 일반: USB 제한 모드 차단(감독 모드인 경우에만)
- 일반: 자동 날짜 및 시간 강제 적용(감독 모드인 경우에만)
- 암호: 암호 자동 채우기 차단(감독 모드인 경우에만)
- 암호: 암호 근접 요청 차단(감독 모드인 경우에만)
- 암호: 암호 공유 차단(감독 모드인 경우에만)

**macOS 설정**: 
- 암호: 암호 자동 채우기 차단
- 암호: 암호 근접 요청 차단
- 암호: 암호 공유 차단

이러한 설정에 대한 자세한 내용은 [iOS](device-restrictions-ios.md) 및 [macOS](device-restrictions-macos.md) 디바이스 제한 설정을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>등록 상태 페이지에서 추적되는 앱 선택<!-- 2531007 -->
등록 상태 페이지에서 추적할 앱을 선택할 수 있습니다. 이러한 앱이 설치될 때까지 사용자는 디바이스를 사용할 수 없습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

#### <a name="search-for-autopilot-device-by-serial-number---2595788---"></a>일련 번호로 Autopilot 디바이스 검색 <!--2595788 -->
이제 일련 번호로 Autopilot 디바이스를 검색할 수 있습니다. 이렇게 하려면 **디바이스 등록** > **Windows 등록** > **디바이스**를 선택하고, **일련 번호로 검색** 상자에 일련 번호를 입력한 다음, Enter 키를 누릅니다.

#### <a name="track-installation-of-office-proplus---2620217---"></a>Office ProPlus 설치 추적 <!--2620217 -->
사용자는 [등록 상태 페이지](windows-enrollment-status.md)를 사용하여 [Office ProPlus](apps-add-office365.md)의 설치 진행률을 추적할 수 있습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

#### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133---"></a>Apple School Manager 계정에 대한 macOS 장비 등록 프로그램 지원 <!--3006133 -->
이제 Intune은 Apple School Manager 계정에 대한 macOS 디바이스에서 장비 등록 프로그램을 사용할 수 있도록 지원합니다.  자세한 내용은 [Apple School Manager 또는 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

### <a name="new-intune-device-subscription-sku---3312071--"></a>새 Intune 디바이스 구독 SKU <!--3312071-->
엔터프라이즈 내 디바이스 관리 비용을 절감하기 위해 새 디바이스 기반 구독 SKU를 이제 사용할 수 있습니다. 이 Intune 디바이스 SKU는 월별로 디바이스당 사용이 허가됩니다. 가격은 라이선스 프로그램에 따라 다릅니다. Microsoft 365 관리 센터를 통해 직접 사용하거나, [EA(기업계약)](https://www.microsoft.com/licensing/licensing-programs/enterprise?activetab=enterprise-tab:primaryr2), [MPSA(Microsoft 제품 및 서비스 계약)](https://www.microsoft.com/licensing/mpsa/default), [Microsoft 오픈 계약](https://partner.microsoft.com/licensing/licensing-agreements) 및 [CSP(클라우드 솔루션 공급자)](https://www.microsoftpartnercommunity.com/t5/Partnership-101/What-is-the-Cloud-Solution-Provider-CSP-program/td-p/2453)를 통해 사용할 수 있습니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Android 디바이스에서 키오스크 모드를 일시적으로 중지하여 변경함 <!-- 3041935 -->
다중 앱 키오스크 모드에서 Android 디바이스를 사용하는 경우 IT 관리자가 디바이스를 변경해야 할 수 있습니다. 이 업데이트에는 IT 관리자가 PIN을 사용하여 일시적으로 키오스크 모드를 중지하고 전체 디바이스에 액세스할 수 있게 하는 새 다중 앱 키오스크 설정이 포함됩니다.
키오스크 설정을 확인하려면 [Android Enterprise 디바이스 제한 사항](device-restrictions-android-for-work.md)을 참조하세요.

#### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Android Enterprise 키오스크 디바이스에서 가상 홈 단추 사용  <!-- 3042021 -->
사용자는 새 설정을 통해 해당 디바이스의 소프트 키 단추를 탭하여 관리 홈 화면 앱과 다중 앱 키오스크 디바이스에 할당된 다른 앱 간에 전환할 수 있습니다. 이 설정은 사용자의 키오스크 앱에서 "뒤로" 단추에 적절하게 응답하지 않는 시나리오에서 특히 유용합니다. 회사 소유의 단일 사용 Android 디바이스에 이 설정을 구성할 수 있습니다. **가상 홈 단추**를 사용하거나 사용하지 않도록 설정하려면 Azure Portal에서 Intune &gt; 디바이스 구성으로 차례로 이동합니다. 현재 디바이스 구성 프로필을 선택하거나 새 프로필을 만들어 키오스크 설정을 편집합니다.
키오스크 설정을 확인하려면 [Android Enterprise 디바이스 제한 사항](device-restrictions-android-for-work.md)을 참조하세요.

<!-- ########################## -->
## <a name="week-of-november-12-2018"></a>2018년 11월 12일 주

### <a name="network-access-control-nac-support-for-citrix-sso-for-ios----3259404---"></a>iOS용 Citrix SSO에 대한 NAC(네트워크 액세스 제어) 지원 <!-- 3259404 -->

Citrix는 Intune에서 iOS용 Citrix SSO에 대해 NAC(네트워크 액세스 제어)를 허용하도록 Citrix Gateway 업데이트를 출시했습니다. Intune에서 VPN 프로필 내에 디바이스 ID를 포함하도록 선택한 후 이 프로필을 iOS 디바이스에 푸시할 수 있습니다. 이 기능을 사용하려면 Citrix Gateway의 최신 업데이트를 설치해야 합니다.

[iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md#base-vpn-settings)에서는 몇 가지 추가 요구 사항을 포함하여 NAC 사용에 대한 자세한 정보를 제공합니다. 

<!-- ########################## -->
## <a name="week-of-november-5-2018"></a>2018년 11월 5일 주

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>iOS 이메일 프로필에서 iOS 12 OAuth 지원 <!--2155106 -->

Intune의 iOS 이메일 프로필은 iOS 12 OAuth(Open Authorization)를 지원합니다. 이 기능을 확인하려면 새 프로필(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** > 프로필 유형에 대한 **이메일**)을 만들거나 기존 iOS 이메일 프로필을 업데이트합니다. 사용자에게 이미 배포된 프로필에서 OAuth를 사용하도록 설정하면 사용자에게 다시 인증하고 이메일을 다시 다운로드하라는 메시지가 표시됩니다.

[iOS 이메일 프로필](email-settings-ios.md)에는 이메일 프로파일에서 OAuth 사용에 대한 자세한 정보가 있습니다.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices-preview----1048100--"></a>하이브리드 Azure Active Directory 조인 디바이스에 대한 Autopilot 지원(미리 보기) <!-- 1048100-->
이제 Autopilot을 사용하여 하이브리드 Azure Active Directory 조인 디바이스를 설정할 수 있습니다. 하이브리드 Autopilot 기능을 사용하려면 디바이스가 조직의 네트워크에 조인되어 있어야 합니다. 자세한 내용은 [Intune 및 Windows Autopilot를 사용하여 하이브리드 Azure AD 조인 디바이스 배포](windows-autopilot-hybrid.md)를 참조하세요.
이 기능은 앞으로 며칠 동안 사용자 기반 전체에 롤아웃됩니다. 따라서 계정에 롤아웃될 때까지 다음 단계를 수행하지 못할 수도 있습니다.

<!-- ########################## -->
## <a name="week-of-october-29-2018"></a>2018년 10월 29일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="require-non-biometric-pin-after-a-specified-timeout----1506985---"></a>지정된 시간 제한 이후 비생체 인식 PIN 요구 <!-- 1506985 -->
관리자가 지정한 시간 제한 후에 비생체 인식 PIN을 요구하면, Intune에서 회사 데이터에 액세스하는 데 사용하는 생체 인식 ID를 제한하여 MAM(모바일 애플리케이션 관리) 지원 앱에 향상된 보안을 제공합니다. 이 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 향후의 다른 생체 인식 인증 방법을 사용하여 APP/MAM 지원 애플리케이션에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 자세히 제어할 수 있으므로 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 디바이스로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **클라이언트 앱** > **앱 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다. 액세스 설정에 대한 자세한 내용은 [iOS 설정](app-protection-policy-settings-ios.md#access-requirements) 및 [Android 설정](app-protection-policy-settings-android.md#access-requirements)을 참조하세요.

#### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM에 등록된 디바이스의 Intune APP 데이터 전송 설정 <!-- 2244713 -->
iOS MDM 등록 디바이스의 Intune APP 데이터 전송 설정에 대한 제어를 등록된 사용자의 ID(UPN(사용자 계정 이름)이라고도 함) 지정과 분리할 수 있습니다. IntuneMAMUPN을 사용하지 않는 관리자는 동작 변경을 관찰하지 않습니다. 이 기능을 사용할 수 있게 되면 IntuneMAMUPN을 사용해 등록된 디바이스의 데이터 전송 동작을 제어하는 관리자가 새로운 설정을 살펴보고 필요에 따라 APP 설정을 업데이트해야 합니다.

#### <a name="windows-10-win32-apps----2617325---"></a>Windows 10 Win32 앱 <!-- 2617325 -->
디바이스의 모든 사용자에 대해 앱을 설치하는 대신 개별 사용자에 대해 사용자 컨텍스트에 맞게 Win32 앱을 설치하도록 구성할 수 있습니다.

#### <a name="windows-win32-apps-and-powershell-scripts----2617330---"></a>Windows Win32 앱 및 PowerShell 스크립트 <!-- 2617330 -->
최종 사용자는 더 이상 디바이스에 로그인하여 Win32 앱을 설치하거나 PowerShell 스크립트를 실행할 필요가 없습니다. 

#### <a name="troubleshooting-client-app-installation----1363711---"></a>클라이언트 앱 설치 문제 해결 <!-- 1363711 -->
**문제 해결** 블레이드에서 **앱 설치**라는 열을 검토하여 클라이언트 앱의 설치 성공 문제를 해결할 수 있습니다. **문제 해결** 블레이드를 보려면 Intune 포털의 **도움말 및 지원** 아래에서 **문제 해결**을 선택합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="network-access-control-support-on-ios-vpn-clients----1333693---"></a>iOS VPN 클라이언트에서 네트워크 액세스 제어 지원 <!-- 1333693 -->
이 업데이트를 사용하면 iOS용 Cisco AnyConnect, F5 Access 및 Citrix SSO에 대한 VPN 구성 프로필을 만들 때 NAC(네트워크 액세스 제어)를 사용하도록 설정할 수 있는 새로운 설정이 있습니다. 디바이스의 NAC ID가 이 설정을 통해 VPN 프로필에 포함될 수 있습니다. 현재 이 새로운 NAC ID를 지원하는 VPN 클라이언트 또는 NAC 파트너 솔루션이 없지만, 지원되는 경우 [지원 블로그 게시물](ttps://aka.ms/iOS12_and_vpn)을 통해 계속 알려드리겠습니다.

NAC를 사용하려면 다음을 수행해야 합니다.
1. Intune에서 VPN 프로필에 디바이스 ID를 포함할 수 있도록 옵트인합니다.
2. NAC 공급자의 지침을 직접 사용하여 NAC 공급자 소프트웨어/펌웨어를 업데이트합니다.

iOS VPN 프로필 내의 이 설정에 대한 자세한 내용은 [Microsoft Intune에서 iOS 디바이스용 VPN 설정 추가](vpn-settings-ios.md)를 참조하세요. 네트워크 액세스 제어에 대한 자세한 내용은 [Intune과 NAC(네트워크 액세스 제어) 통합](network-access-control-integrate.md)을 참조하세요. 

적용 대상: iOS

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile----1818139---"></a>하나의 이메일 프로필만 있는 경우에도 디바이스에서 이메일 프로필 제거 <!-- 1818139 -->
이전에는, 이메일 프로필이 유일한 *경우* 이 이메일 프로필을 디바이스에서 제거할 수 없었습니다. 이 업데이트를 통해 이러한 동작이 변경됩니다. 이제는 디바이스에 이메일 프로필이 유일한 경우에도 이메일 프로필을 삭제할 수 있습니다. 자세한 내용은 [Intune을 사용하여 디바이스에 이메일 설정 추가](email-settings-configure.md)를 참조하세요.

#### <a name="powershell-scripts-and-aad----2309469---"></a>PowerShell 스크립트 및 AAD <!-- 2309469 -->
Intune의 PowerShell 스크립트는 AAD 디바이스 보안 그룹을 대상으로 할 수 있습니다.

#### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Android, Android Enterprise에 대한 새 "필수 암호 유형" 기본 설정<!-- 2649963 -->
새 준수 정책을 만들 때(**Intune** > **장치 준수** > **정책** > **정책 만들기** >  플랫폼에 대한 **Android** 또는 **Android 엔터프라이즈** > 시스템 보안) **필수 암호 유형**의 기본값은 다음과 같이 변경됩니다.

변경 전: 디바이스 기본값 종료: 숫자 이상

적용 대상: Android, Android Enterprise

이러한 설정을 확인하려면 [Android](compliance-policy-create-android.md) 및 [Android 엔터프라이즈](compliance-policy-create-android-for-work.md)로 이동합니다.

#### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Windows 10 Wi-Fi 프로필에서 미리 공유한 키 사용 <!-- 2662938 -->
이 업데이트를 사용하면 WPA/WPA2-개인 보안 프로토콜을 통해 PSK(미리 공유한 키)를 사용하여 Windows 10용 Wi-Fi 구성 프로필을 인증할 수 있습니다. 또한 Windows 10 2018년 10월 업데이트에서 디바이스에 대해 계량된 네트워크의 비용 구성을 지정할 수도 있습니다.

현재, 미리 공유한 키를 사용하려면 Wi-Fi 프로필을 가져오거나 사용자 지정 프로필을 만들어야 합니다. [Windows 10의 Wi-Fi 설정](wi-fi-settings-windows.md)에는 현재 설정이 나열됩니다. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices----3218390---"></a>디바이스에서 PKCS 및 SCEP 인증서 제거 <!-- 3218390 -->
일부 시나리오에서는 그룹에서 정책을 제거하거나 구성 또는 규정 준수 배포를 삭제하거나 관리자가 기존 SCEP 또는 PKCS 프로필을 업데이트한 경우에도 PKCS 및 SCEP 인증서가 디바이스에 남아 있었습니다. 이 업데이트가 이러한 동작을 변경합니다. PKCS 및 SCEP 인증서가 디바이스에서 제거되는 경우와 이러한 인증서가 디바이스에 남아있는 시나리오가 있습니다. 이러한 시나리오의 경우 [Microsoft Intune에서 SCEP 및 PKCS 인증서 제거](remove-certificates.md)를 참조하세요.

#### <a name="use-gatekeeper-on-macos-devices-for-compliance----2504381---"></a>규정 준수에 대해 macOS 디바이스에서 게이트키퍼 사용 <!-- 2504381 -->
이 업데이트에는 디바이스의 규정 준수를 평가하는 macOS 게이트키퍼가 포함되어 있습니다. 게이트키퍼 속성을 설정하려면 [macOS 디바이스에 대한 디바이스 준수 정책을 추가](compliance-policy-create-mac-os.md)합니다.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="enrollment-abandonment-report----1382924---"></a>등록 중단 보고서 <!-- 1382924 -->
중단된 등록에 대한 세부 정보를 제공하는 새 보고서는 **디바이스 등록** > **모니터**에서 사용할 수 있습니다. 자세한 내용은[회사 포털 중단 보고서](enrollment-report-company-portal-abandon.md)를 참조하세요.

#### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>새 Azure Active Directory 사용 약관 기능 <!-- 2870393 -->
Azure Active Directory에는 기존 Intune 사용 약관을 대신 사용할 수 있는 사용 약관 기능이 있습니다. Azure AD 사용 약관은 표시할 조건 및 표시 방법에 있어서 유연성을 높이고 보다 나은 현지화 지원을 제공하며, 사용 약관을 렌더링하는 방식을 보다 잘 제어하고 보고 기능을 개선할 수 있도록 지원합니다. Azure AD 사용 약관 기능을 사용하려면 Enterprise Mobility + Security E3 도구 모음의 일부이기도 한 Azure Active Directory Premium P1이 필요합니다. 자세한 내용은 [사용자 액세스 문서에 대한 회사의 사용 약관 관리](terms-and-conditions-create.md)를 참조하세요.

#### <a name="android-device-owner-mode-support---3188762--"></a>Android 디바이스 소유자 모드 지원 <!--3188762-->
Samsung Knox 모바일 등록의 경우 이제 Intune에서 디바이스를 Android 디바이스 소유자 모드로 등록할 수 있습니다. WiFi 또는 셀룰러 네트워크의 사용자는 디바이스를 처음 켤 때 몇 번만 탭하면 등록할 수 있습니다. 자세한 내용은 [삼성 Knox 모바일 등록을 사용하여 Android 디바이스 자동 등록](android-samsung-knox-mobile-enroll.md)을 참조하세요.

### <a name="device-management"></a>디바이스 관리
#### <a name="new-settings-for-software-updates------1907869---"></a>소프트웨어 업데이트에 대한 새 설정   <!-- 1907869 -->  
- 이제 일부 알림을 구성하여 최신 소프트웨어 업데이트 설치를 완료하는 데 필요한 다시 시작 알림을 최종 사용자에게 표시할 수 있습니다.   
- 이제 BYOD 시나리오를 지원하는 작업 시간 외에 발생하는 다시 시작에 대한 다시 시작 경고 프롬프트를 구성할 수 있습니다.

#### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>관련자 ID 기준으로 Windows Autopilot에 등록된 디바이스 그룹화 <!-- 2075110 -->
Configuration Manager를 통해 [기존 디바이스에 대해 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)을 사용하여 등록할 때 이제 Intune에서 관련자 ID 기준으로 Windows 디바이스를 그룹화할 수 있도록 지원합니다. 관련자 ID는 Autopilot 구성 파일의 매개 변수입니다. Intune에서 자동으로 Azure AD 디바이스 특성인 [enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects)을 "OfflineAutopilotprofile-<correlator ID>"와 동일하게 설정합니다. 이것으로 오프라인 Autopilot 등록을 위한 enrollmentprofileName 특성을 통해 관련자 ID를 기반으로 임의의 Azure AD 동적 그룹을 만들 수 있습니다. 자세한 내용은 [기존 디바이스에 대한 Windows Autopilot](enrollment-autopilot.md#windows-autopilot-for-existing-devices)을 참조하세요.

#### <a name="intune-app-protection-policies----2984657---"></a>Intune 앱 보호 정책 <!-- 2984657 -->
Intune 앱 보호 정책을 사용하면 Microsoft Outlook 및 Microsoft Word와 같이 Intune으로 보호되는 앱에 대한 다양한 데이터 보호 설정을 구성할 수 있습니다. 개별 설정을 더 쉽게 찾을 수 있도록 [iOS](app-protection-policy-settings-ios.md) 및 [Android](app-protection-policy-settings-android.md) 모두에 대해 이러한 설정의 모양과 느낌을 변경했습니다. 정책 설정에는 다음 세 가지 범주가 있습니다.
- **데이터 재배치** - 이 그룹에는 잘라내기, 복사, 붙여넣기 및 다른 이름으로 저장 제한과 같은 DLP(데이터 손실 방지) 컨트롤이 포함되어 있습니다. 이러한 설정은 사용자가 앱의 데이터와 상호 작용하는 방식을 결정합니다.
- **액세스 요구 사항** - 이 그룹에는 최종 사용자가 작업 컨텍스트에 맞게 앱에 액세스하는 방법을 결정하는 앱별 PIN 옵션이 포함되어 있습니다.  
- **조건부 시작** - 이 그룹에는 최소 OS 설정, 탈옥 및 루팅된 디바이스 검색 및 오프라인 유예 기간과 같은 설정이 포함됩니다.  
  
설정의 기능은 변경되지 않았지만 정책 작성 흐름에서 작업할 때 더 쉽게 찾을 수 있습니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="intune-will-support-a-maximum-package-size-of-8-gb-for-lob-apps----1727158---"></a>Intune에서 LOB 앱에 대해 최대 8GB의 패키지 크기 지원 <!-- 1727158 -->
Intune에서 LOB(기간 업무) 앱의 최대 패키지 크기가 8GB로 늘어났습니다. 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)를 참조하세요.

#### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>회사 포털 앱용 사용자 지정 브랜드 이미지 추가 <!-- 1916266 -->
Microsoft Intune 관리자는 iOS 회사 포털 앱의 사용자 프로필 페이지에 배경 이미지로 표시될 사용자 지정 브랜드 이미지를 업로드할 수 있습니다. 회사 포털 앱 구성에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

#### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>최종 사용자 머신에서 Office를 업데이트할 때 Intune에서 지역화된 Office 언어 유지 관리 <!-- 2971030 -->
Intune에서 최종 사용자의 머신에 Office를 설치하면 최종 사용자가 이전 .MSI Office 설치에서 사용한 것과 동일한 언어 팩을 자동으로 얻을 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](apps-add-office365.md) 참조하세요.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="new-intune-support-experience-in-the-microsoft-365-device-management-portal----3076965---"></a>Microsoft 365 디바이스 관리 포털의 새로운 Intune 지원 환경 <!-- 3076965 -->
[Microsoft 365 디바이스 관리 포털]( http://devicemanagement.microsoft.com)에서 Intune에 대한 새로운 도움말 및 지원 환경을 롤아웃하고 있습니다. 새 환경을 사용하면 문제를 사용자 고유의 언어로 설명하고, 문제 해결 인사이트와 웹 기반 수정 콘텐츠를 받을 수 있습니다. 이러한 솔루션은 사용자 문의에 따라 구동되는 규칙 기반 기계 학습 알고리즘을 통해 제공됩니다.  

문제별 지침 외에도 새 사례 만들기 워크플로를 사용하여 이메일 또는 전화를 통해 지원 사례를 열 수도 있습니다.  

롤아웃에 참여하는 고객의 경우 이 새로운 환경은 도움말 및 지원을 열 때 제공되는 콘솔의 영역에 따라 미리 선택된 옵션의 정적 집합에 대한 현재 도움말 및 지원 환경을 대체합니다.  

*이 새로운 도움말 및 지원 환경은 일부 테넌트에만 롤아웃되며 디바이스 관리 포털에서 사용할 수 있습니다. 이 새로운 환경에 대한 참가자는 사용 가능한 Intune 테넌트 중에서 임의로 선택됩니다. 롤아웃이 확장됨에 따라 새 테넌트가 추가됩니다.*  

자세한 내용은 Microsoft Intune에 대한 지원을 받는 방법의 [도움말 및 지원 환경](get-support.md#help-and-support-experience)을 참조하세요.  

### <a name="powershell-module-for-intune--preview-available----951068---"></a>Intune용 PowerShell 모듈 - 미리 보기 사용 가능 <!-- 951068 -->
Microsoft Graph를 통해 Intune API를 지원하는 새로운 PowerShell 모듈을 이제 [GitHub]( https://aka.ms/intunepowershell)에서 미리 볼 수 있습니다. 이 모듈을 사용하는 방법에 대한 자세한 내용은 해당 위치의 추가 정보를 참조하세요. 


<!-- ########################## -->
## <a name="week-of-october-15-2018"></a>2018년 10월 15일이 있는 주

### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device-----2637704----"></a>iOS 디바이스에서 지문 또는 얼굴 ID를 변경할 때 표시되는 PIN 프롬프트  <!-- 2637704  -->
이제 iOS 디바이스에서 생체 인식 내용을 변경한 후 PIN을 입력하라는 메시지가 사용자에게 표시됩니다. 여기에는 등록된 지문 또는 얼굴 ID의 변경이 포함됩니다. 프롬프트의 타이밍은 ‘다음 시간 이후에 액세스 요구 사항 다시 확인:’ 시간 제한의 구성 방법에 따라 다릅니다.   PIN이 설정되지 않은 경우에는 설정하라는 메시지가 사용자에게 표시됩니다. 
 
이 기능은 iOS에만 제공되고 iOS용 Intune 앱 SDK, 버전 9.0.1 이상을 통합하는 애플리케이션의 참여가 필요합니다. 대상 애플리케이션에 동작이 적용될 수 있도록 SDK의 통합이 필요합니다. 이 통합은 롤링 기반으로 특정 애플리케이션 팀에서 수행합니다. 참여하는 일부 앱에는 WXP, Outlook, Managed Browser 및 Yammer가 포함됩니다.


<!-- ########################## -->
## <a name="week-of-october-1-2018"></a>2018년 10월 1일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="access-to-key-profile-properties-using-the-company-portal-app----772203---"></a>회사 포털 앱을 사용하여 주요 프로필 속성 액세스 <!-- 772203 -->
최종 사용자는 이제 회사 포털 앱에서 암호 재설정과 같은 주요 계정 속성 및 동작에 액세스할 수 있습니다. 

#### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 타사 키보드를 차단할 수 있음 <!-- 1248481 -->
iOS 디바이스에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(애플리케이션 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 디바이스 사용자에게 표시되지 않습니다. 대화 메시지가 디바이스 사용자에게 한 번만 표시됩니다. 

#### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices----1248496---"></a>관리형 Android 및 iOS 디바이스의 Intune 앱에 대한 사용자 계정 액세스 <!-- 1248496 -->
Microsoft Intune 관리자는 관리되는 장치에서 Microsoft Office 애플리케이션에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 디바이스에서 개인 계정을 차단할 수 있습니다. 

#### <a name="outlook-ios-and-android-app-configuration-policy---1828527---"></a>Outlook iOS 및 Android 앱 구성 정책 <!--1828527 -->
이제 ActiveSync 프로토콜을 사용하여 기본 인증을 활용하는 온-프레미스 사용자의 iOS 및 Android에 대한 Outlook iOS 및 Android 앱 구성 정책을 만들 수 있습니다. 추가 구성 설정은 iOS 및 Android용 Outlook에 사용하도록 설정된 경우 추가됩니다.

#### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 언어 팩 <!-- 1833450 -->
Intune 관리자는 Intune을 통해 관리되는 Office 365 Pro Plus 앱에 대한 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **클라이언트 앱** > **앱** > **추가**를 차례로 선택합니다. **앱 추가** 블레이드의**앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 블레이드에서 **언어**를 선택합니다.

####  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows LOB(기간 업무) 앱 파일 확장명 <!-- 1884873 -->
이제 Windows LOB 앱의 파일 확장명에 *.msi*, *.appx*, *.appxbundle*, *.msix* 및 *.msixbundle*이 포함됩니다. Microsoft Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 앱을 추가할 수 있습니다. **앱 유형**을 선택할 수 있는 **앱 추가** 창이 표시됩니다. Windows LOB 앱의 경우 앱 유형으로 **기간 업무** 앱을 선택하고, **앱 패키지 파일**을 선택한 다음, 적절한 확장명이 있는 설치 파일을 입력합니다.

#### <a name="windows-10-app-deployment-using-intune----2309001---"></a>Intune을 사용하여 Windows 10 앱 배포 <!-- 2309001 -->
관리자는 LOB(사업 부문) 앱 및 비즈니스용 Microsoft Store 앱에 대한 기존 지원을 토대로, Intune을 사용하여 조직의 기존 애플리케이션 대부분을 Windows 10 장치의 최종 사용자에게 배포할 수 있습니다. 관리자는 MSIs, Setup.exe 또는 MSP와 같은 다양한 형식의 Windows 10 사용자에 대한 애플리케이션을 추가, 설치 및 제거할 수 있습니다. Intune는 다운로드 및 설치 전에 요구 사항 규칙을 평가하여 최종 사용자에게 Windows 10 알림 센터를 사용하여 상태 또는 재부팅 요구 사항을 알립니다. 이 기능은 이 워크로드를 Intune로 이동하는 데 관심이 있는 조직과 클라우드를 효과적으로 차단 해제합니다. 이 기능은 현재 공개 미리 보기에 있으며, 다음 몇 달 동안 이 기능에 새로운 기능이 상당히 추가될 것입니다. 

#### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 디바이스의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다. 

#### <a name="end-user-device-and-app-content-menu----2771453---"></a>최종 사용자 디바이스 및 앱 콘텐츠 메뉴 <!-- 2771453 -->
이제 최종 사용자는 디바이스 및 앱의 컨텍스트 메뉴를 사용하여 디바이스 이름 바꾸기 또는 준수 검사와 같은 일반 작업 트리거할 수 있습니다. 

#### <a name="windows-company-portal-keyboard-shortcuts----2771518---"></a>Windows 회사 포털 바로 가기 키 <!-- 2771518 -->
최종 사용자는 바로 가기 키(액셀러레이터 키)를 사용하여 Windows 회사 포털에서 앱 및 디바이스 작업을 트리거할 수 있습니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10---1333668---"></a>Windows 10을 실행하는 디바이스의 VPN 구성 프로필에 DNS 접미사 만들기<!-- 1333668 -->
VPN 디바이스 구성 프로필을 만들 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** 플랫폼 &gt; **VPN** 프로필 유형) DNS 설정을 몇 개 입력합니다. 이 업데이트를 사용하면 Intune에서 여러 **DNS 접미사**를 입력할 수도 있습니다. DNS 접미사를 사용하는 경우 FQDN(정규화된 도메인 이름) 대신 짧은 이름을 사용해 네트워크 리소스를 검색할 수 있습니다. 이 업데이트를 설치하면 Intune에서 DNS 접미사의 순서를 변경할 수도 있습니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md#dns-settings)에는 현재 DNS 설정이 나열됩니다.
적용 대상: Windows 10 디바이스

#### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Android Enterprise 작업 프로필에 대한 Always On VPN 지원 <!-- 1333705 -->
이 업데이트에서 Android 엔터프라이즈 디바이스에서는 관리되는 작업 프로필과 함께 상시 VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 디바이스를 잠금 해제한 경우, 디바이스가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) &gt; **디바이스 제한** > **연결** 설정에서 상시 VPN을 활성화할 수 있습니다.

#### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>사용자가 없는 디바이스에 SCEP 인증서 발급 <!-- 1744554 -->
현재, 인증서가 사용자에게 발급되었습니다. 이 업데이트를 사용하면 키오스크 등과 같이 사용자가 지정되지 않은 디바이스를 포함한 디바이스에 SCEP 인증서를 발급할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** >  플랫폼용 **Windows 10 이상** &gt; 프로필용 **SCEP 인증서**). 기타 업데이트는 다음과 같습니다.
- SCEP 프로필의 **주체** 속성은 이제 사용자 지정 텍스트 상자로, 새로운 변수를 포함할 수 있습니다. 
- SCEP 프로필의 **SAN(주체 대체 이름)** 속성은 이제 테이블 형식으로 새로운 변수를 포함할 수 있습니다. 관리자는 이 테이블에서 특성을 추가하고 사용자 지정 텍스트 상자에 값을 입력할 수 있습니다. SAN은 다음 특성을 지원합니다. 
  - DNS
  - 전자 메일 주소
  - UPN

  사용자 정의 값 텍스트 상자에 정적 텍스트와 함께 새 변수를 추가할 수 있습니다. 예를 들어, DNS 특성을 `DNS = {{AzureADDeviceId}}.domain.com`으로 추가할 수 있습니다.

  > [!NOTE]
  > 중괄호, 세미콜론 및 파이프 기호 “{}; |”는 SAN의 정적 텍스트에서 작동하지 않습니다. `Subject` 또는 `Subject alternative name`에 대해 허용되도록 새 디바이스 인증서 변수 중 하나만 중괄호로 묶어야 합니다. 

새 디바이스 인증서 변수:  

```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}`은 Windows 및 도메인에 가입된 디바이스에서만 작동합니다. 
>  -  디바이스 인증서의 주체 또는 SAN에서 디바이스 속성(예: IMEI, 일련 번호 및 정규화된 도메인 이름)을 지정하는 경우 이러한 속성은 해당 디바이스의 액세스 권한을 가진 사람이 스푸핑할 수 있습니다. 

SCEP 구성 프로필을 만들 때 [SCEP 인증서 프로필 만들기](certificates-scep-configure.md#create-a-scep-certificate-profile)는 현재 변수를 나열합니다. 

적용 대상: Windows 10 이상 및 iOS, Wi-Fi 지원

#### <a name="remotely-lock-uncompliant-devices----2064495---"></a>원격으로 비준수 디바이스 잠금 <!-- 2064495 -->
비규격 디바이스인 경우 원격으로 디바이스를 잠그는 준수 정책의 작업을 생성할 수 있습니다. Intune &gt; **디바이스 준수**에서 새 정책을 생성하거나, 기존 정책 &gt; **속성**을 선택합니다. **비준수에 대한 작업** > **추가**를 선택하고 디바이스를 원격으로 잠그도록 선택합니다.
지원 됩니다. 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 이상 

#### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224---"></a>Azure Portal에서 Windows 10 이상 키오스크 프로필 기능이 향상됨 <!-- 2748224 -->
업데이트에는 Windows 10 Kiosk 디바이스 구성 프로필에 대한 다음 개선 사항이 포함되어 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Windows 10 이상** &gt; 프로필 유형의 **키오스크 미리 보기**). 
- 현재, 동일한 디바이스에서 여러 키오스크 프로필을 만들 수 있습니다. 이 업데이트를 설치하면 Intune에서는 디바이스당 키오스크 프로필을 하나만 지원합니다. 단일 디바이스에서 키오스크 프로필이 여러 개 필요한 경우 사용자 지정 URI를 사용할 수 있습니다.
- **다중 앱 키오스크** 프로필의 애플리케이션 그리드에서 **시작 메뉴 레이아웃**의 애플리케이션 타일 크기와 순서를 선택할 수 있습니다. 더 많은 부분을 사용자 지정하려는 경우 XML 파일을 계속해서 업로드할 수 있습니다.
- 키오스크 브라우저 설정은 **키오스크** 설정으로 이동합니다. 지금은 Azure Portal에 **키오스크 웹 브라우저** 설정의 고유 범주가 있습니다.
적용 대상: Windows 10 이상




### <a name="device-enrollment"></a>디바이스 등록

#### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Autopilot에는 아직 등록되지 않은 등록된 Win 10 디바이스에 Autopilot 프로필 적용 <!-- 1558983 -->
아직 Autopilot에 등록되지 않은 등록한 Win 10 디바이스에 Autopilot 프로필을 적용할 수 있습니다. Autopilot 프로필에서 **모든 대상 디바이스를 Autopilot으로 변환** 옵션을 선택하면 Autopilot 배포 서비스에 Autopilot 디바이스 이외 디바이스를 자동으로 등록합니다. 등록을 처리하는 데 48시가 가량 걸립니다. 디바이스 등록을 취소하고 재설정하면 Autopilot이 해당 디바이스를 프로비전합니다.

#### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564---"></a>여러 등록 상태 페이지 프로필을 만들어 Azure AD 그룹에 할당 <!-- 2526564 -->
이제 등록 상태 페이지 프로필을 여러 개 [만들어 Azure AD 그룹에 할당](windows-enrollment-status.md)할 수 있습니다.

#### <a name="migration-from-device-enrollment-program-to-apple-business-manager-in-intune---2748613--"></a>Intune을 통해 장비 등록 프로그램에서 Apple Business Manager로 마이그레이션 <!--2748613-->
ABM(Apple Business Manager)은 Intune에서 작동하므로, 사용 중인 계정을 DEP(장비 등록 프로그램)에서 ABM으로 업그레이드할 수 있습니다. Intune의 프로세스는 동일합니다. DEP에서 ABM으로 Apple 계정을 업그레이드하려면 [ https://support.apple.com/HT208817]( https://support.apple.com/HT208817)로 이동하세요.

### <a name="alert-and-enrollment-status-tabs-on-the-device-enrollment-overview-page---2748656--"></a>디바이스 등록 개요 페이지의 경고 및 등록 상태 탭 <!--2748656-->
이제 디바이스 등록 개요 페이지의 별도 탭에 경고 및 등록 오류가 표시됩니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="restricts-apps-and-block-access-to-company-resources-on-android-devices----2451462----"></a>Android 디바이스에서 앱 제한 및 회사 리소스에 대한 액세스 차단 <!-- 2451462  -->  
**디바이스 준수** > **정책** > **정책 만들기** > **Android** > **시스템 보안**에서 *디바이스 보안* 섹션에 **제한된 앱**이라고 하는 새로운 설정이 있습니다. **제한된 앱** 설정은 특정 앱이 디바이스에 설치되어 있는 경우 준수 정책을 사용하여 회사 리소스에 대한 액세스를 차단합니다. 제한된 응용 프로그램이 디바이스에서 제거될 때까지 디바이스는 정책을 준수하지 않는 것으로 간주됩니다.
적용 대상: 
- Android

<!-- ########################### -->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
