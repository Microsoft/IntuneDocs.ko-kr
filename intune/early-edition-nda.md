---
title: 초기 버전 | Microsoft Intune
titlesuffix: ''
description: Microsoft Intune 초기 버전
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19994745a232a362d6bba0f09ed3934e492a17ed
ms.sourcegitcommit: 2f431f122ce3ee6b5d0cdb04a0b748d00f83e295
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56265675"
---
# <a name="the-early-edition-for-microsoft-intune---february-2019"></a>Microsoft Intune 초기 버전 - 2019년 2월

> [!Note]
> NDA 알림: Intune에 대해 다음 변경 사항을 개발 중입니다. 이 정보는 매우 제한된 기준에 따라 NDA에서 공유됩니다. Twitter, UserVoice, Reddit 등과 같은 소셜 미디어 또는 공개 웹 사이트에 이 정보를 게시하지 마세요. 

**초기 버전**에서는 Microsoft Intune의 향후 릴리스에서 도입될 기능(NDA로 공유됨) 목록을 제공합니다. 이 정보는 제한적으로 제공되며 변경될 수 있습니다. Twitter, UserVoice에 게시 또는 다른 방법으로 이 정보를 회사 외부에서 공유하지 마세요. 여기 나열된 일부 기능은 마감일을 맞추지 못할 위험이 있으며 다음 릴리스까지 지연될 수 있습니다. 다른 기능은 고객용 준비 상태를 확인하기 위해, 파일럿(플라이팅) 테스트 중 입니다. 질문이나 궁금한 내용이 있으면 Microsoft 제품 그룹 담당자에게 연락하세요.

이 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune
<!-- 1902 start-->

### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675----"></a>PowerShell 스크립트가 64비트 디바이스의 64비트 호스트에서 실행될 수 있음 <!-- 1862675  -->
디바이스 구성 프로필에 PowerShell 스크립트를 추가한 경우 해당 스크립트는 항상 32비트, 심지어 64비트 운영 체제에서도 실행됩니다. 이 업데이트를 사용하여 관리자는 64비트 디바이스의 64비트 PowerShell 호스트에서 스크립트를 실행할 수 있습니다(**디바이스 구성** > **PowerShell 스크립트** >  **추가** > **구성** > **64비트 PowerShell 호스트에서에서 스크립트 실행**).
PowerShell을 사용하는 방법에 대한 자세한 내용은 [Intune의 PowerShell 스크립트](intune-management-extension.md)를 참조하세요.
적용 대상: Windows 10 이상

### <a name="rename-an-enrolled-windows-device----1911112----"></a>등록된 Windows 디바이스 이름 바꾸기 <!-- 1911112  -->
등록된 Windows 10 디바이스(RS4 이상)의 이름을 바꿀 수 있습니다. 이름을 바꾸려면 **Intune** > **디바이스** > **모든 디바이스** > 디바이스 선택 > **디바이스 이름 바꾸기**를 선택합니다.

### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521-----"></a>SCEP 인증서를 사용자가 없는 macOS 디바이스에 할당 <!-- 2340521   -->
사용자가 없는 macOS 디바이스에 SCEP(단순 인증서 등록 프로토콜) 인증서를 할당하고, 해당 인증서를 Wi-Fi 또는 VPN 프로필과 연결할 수 있습니다. 이렇게 하면 [Windows, iOS 및 Android를 실행하는 사용자가 없는 디바이스에 인증서를 할당](certificates-scep-configure.md#create-a-scep-certificate-profile)해야 하는 기존 지원이 확장됩니다.

### <a name="intune-conditional-access-ui-update------2432313----"></a>Intune 조건부 액세스 UI 업데이트 <!-- 2432313  -->
Intune 콘솔에서 조건부 액세스를 위해 UI를 개선합니다. 확인할 수 있습니다.
- Intune *조건부 액세스* 블레이드를 Azure Active Directory의 블레이드로 바꿉니다. 이렇게 하면 Azure AD 기술을 유지하는 조건부 액세스에 대한 광범위한 설정 및 구성에 액세스할 수 있습니다.
- *Exchange 서비스 커넥터* 설정을 현재의 *온-프레미스 액세스* 블레이드로 재배치합니다. 해당 블레이드의 이름을 *Exchange 액세스*로 바꿉니다. 이 변경으로 Exchange 온라인 및 온-프레미스와 관련된 세부 정보를 구성하고 모니터링하는 위치가 통합됩니다.

### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355----"></a>Intune은 Android 디바이스에서 Google Play 보호 API를 활용함 <!-- 2577355  -->
일부 IT 관리자는 최종 사용자가 휴대폰의 루팅 또는 탈옥(jailbreaking)을 종료할 수 있는 BYOD 환경에 직면합니다. 때로는 악의가 없는 이 동작은 결국 최종 사용자 디바이스에서 조직의 데이터를 보호하기 위해 설정된 여러 Intune 정책을 무시하게 됩니다. 따라서 Intune은 등록 및 등록되지 않은 디바이스에 대한 루팅 및 탈옥 검색을 제공합니다. 이 릴리스에서 Intune은 Google Play 보호 API를 활용하여 등록되지 않은 디바이스에 대한 기존 루트 검색 검사를 추가합니다. Google은 발생하는 루트 검색 검사 전체를 공유하지 않는 반면, Intune에서는 이러한 API가 디바이스 사용자 지정을 비롯해 이전 디바이스에 최신 OS 업데이트를 가져오는 등의 갖가지 이유로 자신의 디바이스를 루팅한 사용자를 검색하기를 기대합니다. 이러한 사용자는 회사 데이터에 액세스하지 못하도록 차단되거나, 회사 계정이 앱을 사용하도록 설정된 해당 정책에서 초기화될 수 있습니다. 추가 값의 경우 IT 관리자는 Intune 앱 보호 블레이드 내에 여러 보고 업데이트를 보유하고 있습니다. "플래그가 지정된 사용자" 보고서에는 Google Play 보호의 SafetyNet API 검색을 통해 검색된 사용자가 표시되며, "잠재적으로 위험한 앱" 보고서에는 Google의 Verify Apps API 검색을 통해 검색된 앱이 표시됩니다. 이 기능은 Android에서 사용할 수 있습니다. 

### <a name="win32-app-information-available-in-troubleshooting-blade----2617342------"></a>문제 해결 블레이드에서 사용할 수 있는 Win32 앱 정보 <!-- 2617342    -->
Intune 앱 **문제 해결** 블레이드에서 Win32 앱 설치에 대한 오류 로그 파일을 수집할 수 있습니다. 앱 설치 문제 해결에 대한 자세한 내용은 [앱 설치 문제 해결](troubleshoot-app-install.md)을 참조하세요.

### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135----"></a>키오스크 브라우저 및 Microsoft Edge 브라우저 앱은 키오스크 모드의 Windows 10 디바이스에서 실행될 수 있음 <!-- 2935135  -->
키오스크 모드에서 Windows 10 디바이스를 사용하여 하나 또는 여러 앱을 실행할 수 있습니다. 이 업데이트에는 다음을 포함하여 키오스크 모드에서 브라우저 앱 사용에 대한 몇 가지 변경 사항이 포함됩니다.

- Microsoft Edge 브라우저 또는 키오스크 브라우저를 추가하여 키오스크 디바이스에서 앱으로 실행합니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **Windows 10 이상** > 프로필 유형에 대한 **키오스크**).
- Microsoft Edge가 키오스크 모드에서 실행될 수 있도록(또는 없도록) 제한합니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **Windows 10 이상** > 프로필 유형에 대한 **디바이스 제한** > **Microsoft Edge 브라우저**). 키오스크 모드에서 실행되지 않는 경우 Microsoft Edge 설정은 최종 사용자가 변경할 수 있습니다.

현재 설정 목록은 다음을 참조하세요.

- [키오스크로 실행되는 Windows 10 이상 디바이스 설정](kiosk-settings-windows.md)
- [Microsoft Edge 브라우저 디바이스 제한](device-restrictions-windows-10.md#microsoft-edge-browser)

적용 대상: Windows 10 이상

### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>해당 범위를 사용하여 관리자가 만든 리소스에 대한 범위 태그 자동 할당 <!-- 3173823  -->
관리자가 리소스를 만드는 경우 관리자에게 할당된 모든 범위 태그는 새 리소스에 자동으로 할당됩니다.

### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774---"></a>iOS 및 macOS 디바이스에 대한 새 디바이스 제한 설정 <!-- 3448774 -->
iOS 및 macOS를 실행하는 디바이스에서 일부 설정 및 기능을 제한할 수 있습니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** 또는 **macOS** > 프로필 유형에 대한 **디바이스 제한**). 이 업데이트는 화면 시간 설정, eSIM 설정 및 휴대폰 플랜 변경, 사용자의 소프트웨어 업데이트 표시 유형 지연, 콘텐츠 캐싱 차단 등을 비롯한 더 많은 기능 및 설정을 추가할 수 있습니다.
제한할 수 있는 현재 기능 및 설정을 확인하려면 다음을 참조하세요.
- [iOS 디바이스 제한 설정](device-restrictions-ios.md)
- [macOS 디바이스 제한 설정](device-restrictions-macos.md)

적용 대상:
- iOS
- macOS

### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202---"></a>실패한 등록 보고서가 디바이스 등록 블레이드로 이동 <!-- 3560202 -->
**실패한 등록** 보고서가 **디바이스 등록** 블레이드의 **모니터링** 섹션으로 이동합니다. 또한 두 개의 열(등록 방법 및 OS 버전)이 새로 추가됩니다.

### <a name="change-kiosk-to-dedicated-devices----3598402----"></a>"키오스크"를 "전용 디바이스"로 변경 <!-- 3598402  -->
Android 용어에 맞게 조정하려면 **키오스크**를 디바이스 구성 프로필, **Android 엔터프라이즈** > **디바이스 소유자** > **디바이스 제한**에서 **전용 디바이스**로 변경합니다.

### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850--3803313----"></a>Safari 및 사용자 소프트웨어 업데이트 표시 유형 iOS 설정 지연이 Intune UI에서 이동 중 <!-- 3640850, , 3803313  -->
iOS 디바이스의 경우 Safari 설정을 설정하고 소프트웨어 업데이트를 구성할 수 있습니다. 이 업데이트에서 이러한 설정은 다음과 같이 Intune UI의 다른 파트로 이동합니다.

- Safari 설정은 **Safari**(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** > 프로필 유형에 대한 **디바이스 제한**)에서 **기본 제공 앱**으로 이동합니다. 
- **감독되는 iOS 디바이스에 대한 사용자 소프트웨어 업데이트 표시 유형 지연** 설정(**소프트웨어 업데이트** > **iOS에 대한 업데이트 정책**)은 **디바이스 제한** > **일반**으로 이동합니다.

현재 설정 목록은 [iOS 디바이스 제한](device-restrictions-ios.md) 및 [iOS 소프트웨어 업데이트](software-updates-ios.md)를 참조하세요.

적용 대상: 
- iOS

### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164----"></a>디바이스 설정에서 제한을 사용하도록 설정하면 iOS 디바이스에서 화면 시간으로 이름이 바뀜 <!-- 3699164  -->
감독되는 iOS 디바이스의 **디바이스 설정에서 제한의 활성화**를 구성할 수 있습니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** > 프로필 유형에 대한 **디바이스 제한** > **일반**). 이 업데이트에서 이 설정은 **화면 시간(감독 모드인 경우에만)** 으로 이름이 바뀝니다. 동작은 동일합니다. 특히: 

- iOS 11.4.1 이하: **차단**은 최종 사용자가 디바이스 설정에서 자신만의 제한을 설정하지 못하도록 방지합니다. 
- iOS 12.0 이상: **차단**은 최종 사용자가 디바이스 설정에서 콘텐츠 및 개인정보처리 제한 사항을 비롯해 자신만의 **화면 시간**을 설정하지 못하도록 방지합니다. iOS 12.0로 업그레이드된 디바이스에는 디바이스 설정의 제한 탭이 더 이상 표시되지 않습니다. 이러한 설정은 **화면 시간**에 있습니다. 

현재 설정 목록은 [iOS 디바이스 제한](device-restrictions-ios.md)을 참조하세요.

적용 대상: 
- iOS

### <a name="app-status-details-for-ios-apps----3761235----"></a>iOS 앱용 앱 상태 세부 정보 <!-- 3761235  -->
다음과 관련된 새 앱 설치 오류 메시지가 있습니다.
- 공유 iPad에 설치하는 경우 VPP 앱의 오류
- 앱 스토어를 사용하지 않도록 설정하는 경우의 오류
- 앱용 VPP 라이선스를 찾지 못하는 오류
- MDM 공급 기업을 통해 시스템 앱을 설치하지 못하는 오류
- 디바이스가 분실 모드 또는 키오스크 모드에 있는 경우 앱을 설치하지 못하는 오류
- 사용자가 앱 스토어에 로그인하지 않은 경우 앱을 설치하지 못하는 오류

Intune에서 **클라이언트 앱** > **앱** > "애플리케이션 이름" > **디바이스 설치 상태**를 선택합니다. 새 오류 메시지는 **상태 세부 정보** 열에서 사용할 수 있습니다.

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱 배포 <!-- 1672660  -->
디바이스 컨텍스트에서 필요로 하는 온라인 라이선스가 부여된 비즈니스용 Microsoft Store 앱을 할당할 수 있습니다. 이 방식으로 비즈니스용 Microsoft Store 앱을 배포하면 디바이스의 모든 사용자에 대해 앱을 설치할 수 있습니다. 이 기능은 Windows 10 RS4 이상 데스크톱 디바이스에만 적용됩니다. 디바이스 컨텍스트에 설치하는 옵션은 MSFB 온라인 라이선스가 부여된 앱에 대한 클라이언트 앱 할당 페이지에서 사용할 수 있습니다.

<!-- 1812 start -->

### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 IT 부서에서는 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 최종 사용자에게 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359---"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함 <!-- 1927359 -->
Apple의 회사 디바이스 등록 방법 중 하나를 통해 설정 도우미에서 이미 등록한 디바이스에서는 최종 사용자가 앱 스토어에서 회사 포털 앱을 수동으로 설치하는 경우 Intune은 더 이상 해당 회사 포털 앱을 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator
* Apple Business Manager
* Apple School Manager
* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 또한 회사 포털 앱에서 **디바이스 식별** 화면이 더 이상 사용되지 않습니다.  
이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 이러한 단계를 수행하는 방법에 대한 자세한 내용은 이후 문서에서 간략하게 설명합니다.

### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 제공되고 자체 구성 프로필 로 이동됨 <!-- 3322847 -->
Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 비공개 미리 보기로 제공됩니다. 이 업데이트 포함: 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
관리 템플릿은 공개 미리 보기로 제공 됩니다. 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** >**프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
보고는 사용하도록 설정됩니다. 적용 대상: Windows 10 이상

### <a name="intune-macos-company-portal-dark-mode----3300524---"></a>Intune macOS 회사 포털 어두운 모드 <!-- 3300524 -->
Intune macOS 회사 포털은 이제 macOS용 어두운 모드를 지원합니다. macOS 10.14 이상 디바이스에서 어두운 모드를 활성화하면 회사 포털은 해당 모드를 리플렉션하는 색으로 모양을 조정합니다.

<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 디바이스의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>디바이스 준수 대시보드에 사용 중지된 디바이스가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 디바이스가 디바이스 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.

## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.
