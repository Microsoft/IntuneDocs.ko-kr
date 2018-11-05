---
title: 초기 버전
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: a13d9b6ee37dc42e90d7c99538c9fd2e5e0d1b7b
ms.sourcegitcommit: 7c80833b74a7203edc23c550d0d0b63229cda452
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50001595"
---
# <a name="the-early-edition-for-microsoft-intune---october-2018"></a>Microsoft Intune 초기 버전 - 2018년 10월

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

<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Microsoft 권장 설정을 보안 기준과 함께 사용<!-- 2055484 -->
Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 종단 간 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 후 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 장치가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 장치나 사용자에 대해 관리자에게 알립니다.

### <a name="autopilot-support-for-hybrid-azure-active-directory-joined-devices----1048100---"></a>하이브리드 Azure Active Directory가 조인된 장치에 대한 Autopilot 지원 <!-- 1048100 -->
Autopilot을 사용하여 하이브리드 Azure Active Directory가 조인된 장치를 설정할 수 있습니다. 하이브리드 Autopilot 기능을 사용하려면 장치가 조직의 네트워크에 조인되어 있어야 합니다.

### <a name="scope-tags-for-apps---1081941---"></a>앱의 범위 태그 <!--1081941 -->
범위 태그를 만들어 Intune 리소스에 대한 액세스를 제한할 수 있습니다. 역할 할당에 범위 태그를 추가한 다음, 범위 태그를 구성 프로필에 추가합니다. 역할은 일치하는 범위 태그가 있거나 범위 태그가 없는 구성 프로필이 있는 리소스에만 액세스할 수 있습니다.
범위 태그를 만들려면 **Intune 역할** > **범위(태그)** > **만들기**를 선택합니다.
역할 할당에 범위 태그를 추가하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당** > **범위(태그)** 를 차례로 선택합니다.
범위 태그를 구성 프로필에 추가하려면 **장치 구성** > **프로필** > 프로필 선택 > **속성** > **범위(태그)** 를 차례로 선택합니다.

### <a name="tenant-health-dashboard----1124854---"></a>테넌트 상태 대시보드 <!-- 1124854 -->
Intune의 테넌트 상태 페이지는 단일 위치에서 테넌트 상태 정보를 제공합니다. 페이지는 4개 섹션으로 구분됩니다.  
- **테넌트 세부사항**: MDM 권한, 테넌트에 등록된 총 장치 수, 라이선스 수와 같은 정보를 포함합니다. 이 섹션은 테넌트에 대한 최신 서비스 릴리스도 제공합니다.
- **커넥터 상태**: Apple VPP, 비즈니스용 Windows 스토어, 인증서 커넥터와 같은 구성된 커넥터에 대한 정보를 포함합니다. 현재 상태에 따라 커넥터는 ‘정상’, ‘경고’ 또는 ‘비정상’으로 플래그 지정됩니다.
- **Intune 서비스 상태**: 테넌트에 대해 활성 인시던트 또는 중단 상태가 포함됩니다. 이 섹션의 정보는 Office Message Center([https://portal.office.com](https://portal.office.com))에서 직접 검색됩니다.
- **Intune 뉴스**: 테넌트가 최신 Intune 기능을 수신했다는 알림과 같은 항목을 포함한 테넌트에 대한 활성 메시지가 포함됩니다. 이 섹션의 정보는 Office Message Center([https://portal.office.com](https://portal.office.com))에서 직접 검색됩니다.

### <a name="enrollment-abandonment-report----1382924---"></a>등록 중단 보고서 <!-- 1382924 -->
중단된 등록에 대한 세부 정보를 제공하는 새 보고서는 **장치 등록** > **모니터링**에서 사용할 수 있습니다.

### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>사용자 등록 없이 배포된 WIP 정책 <!-- 1434452 -->
WIP(Windows Information Protection) 정책은 MDM 사용자가 Windows 10 장치를 등록하지 않고 배포할 수 있습니다. 이 구성을 사용하면 회사는 WIP 구성을 기반으로 회사 문서를 보호할 수 있는 한편 사용자는 자신의 Windows 장치를 관리할 수 있습니다. 문서가 WIP 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 장치를 선택하고 초기화 요청을 보내면 WIP 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.


### <a name="add-custom-brand-image-for-company-portal-app----1916266---"></a>회사 포털 앱에 대한 사용자 지정 브랜드 이미지 추가 <!-- 1916266 -->
Microsoft Intune 관리자는 회사 포털 앱의 사용자 프로필 페이지에 배경 이미지로 표시될 사용자 지정 브랜드 이미지를 업로드할 수 있습니다. 회사 포털 앱 구성에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

### <a name="group-windows-autopilot-enrolled-devices-by-correlator-id----2075110---"></a>관련자 ID로 Windows Autopilot에 등록된 장치 그룹화 <!-- 2075110 -->
Intune에서 Configuration Manager를 통해 [기존 장치에 대해 Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)을 사용하여 등록할 때 관련자 ID로 Windows 장치를 그룹화할 수 있습니다. 관련자 ID는 Autopilot 구성 파일의 매개 변수입니다. Intune에서 [Azure AD 장치 특성 enrollmentProfileName](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership#using-attributes-to-create-rules-for-device-objects)을 "OfflineAutopilotprofile-\<관련자 ID\>"와 같게 자동 설정합니다. 이것으로 오프라인 Autopilot 등록을 위한 enrollmentprofileName 특성을 통해 관련자 ID를 기반으로 임의의 Azure AD 동적 그룹을 만들 수 있습니다. 


### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>iOS 메일 프로필에서 iOS 12 OAuth 지원 <!--2155106 -->
Intune의 iOS 메일 프로필은 iOS 12 OAuth를 지원합니다. 이 기능을 보려면 **Intune** > **장치 구성** > **프로필** > **프로필 만들기** > **OAuth**를 선택합니다. 이 설정이 켜지면 다음 두 가지 상황이 발생합니다.
1. 이미 대상으로 지정된 장치에 새 프로필이 발행됩니다.
2. 최종 사용자에게 자격 증명을 묻는 메시지가 다시 표시됩니다.

### <a name="new-required-password-type-default-setting-for-android-android-enterprise---2649963---"></a>Android, Android 엔터프라이즈에 대한 새 “필수 암호 유형” 기본 설정<!-- 2649963 -->
새 규정 준수 정책을 만들 때(플랫폼 > 시스템 보안에서 **Intune** > **장치 규정 준수** > **정책** > **정책 만들기** > **Android** 또는 **Android 엔터프라이즈** 선택) **필수 암호 유형**의 기본값이 장치 기본값에서 최소 숫자 값으로 변경됩니다. 이는 Android 및 Android 엔터프라이즈에 적용됩니다

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Autopilot 프로필을 모든 장치 가상 그룹에 할당 <!--2715522 -->
Autopilot 프로필을 모든 장치 가상 그룹에 할당할 수 있습니다. 그렇게 하려면 **장치 등록** > **Windows 등록** > **배포 프로필** > 프로필 선택 > **할당**을 선택하고 **할당 대상**에서 **모든 장치**를 선택합니다.

### <a name="new-azure-active-directory-terms-of-use-feature----2870393---"></a>새 Azure Active Directory 사용 약관 기능 <!-- 2870393 -->
Azure Active Directory는 기존 Intune 사용 약관을 사용하는 대신 사용 가능한 사용 약관 기능을 가집니다. Azure AD 사용 약관은 표시할 조건 및 표시 방법에 있어서 유연성을 높이고 보다 나은 현지화 지원을 제공하며, 사용 약관을 렌더링하는 방식을 보다 잘 제어하고 보고 기능을 개선할 수 있도록 지원합니다. Azure AD 사용 약관 기능을 사용하려면 Enterprise Mobility + Security E3 도구 모음의 일부이기도 한 Azure Active Directory Premium P1이 필요합니다.


### <a name="intune-will-maintain-the-office-localized-language-when-updating-office-on-end-users-machines----2971030---"></a>최종 사용자 컴퓨터에서 Office를 업데이트할 때 Intune에서 Office 현지화 언어 유지 관리 <!-- 2971030 -->
Intune에서 최종 사용자의 컴퓨터에 Office를 설치하면 최종 사용자는 이전 .MSI Office 설치 프로그램과 함께 갖고 있던 것과 동일한 언어 팩을 자동으로 가져옵니다. 

<!-- 1809 start -->  

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 등록 장치의 Intune APP 데이터 전송 설정 <!-- 2244713 -->
등록된 사용자의 ID를 지정하는 것과 iOS MDM 등록 장치의 Intune APP 데이터 전송 설정 제어를 구분할 수 있습니다. IntuneMAMUPN을 사용하지 않는 관리자는 동작 변경을 관찰하지 않습니다. 이 기능을 사용할 수 있게 되면 IntuneMAMUPN을 사용해 등록된 장치의 데이터 전송 동작을 제어하는 관리자가 새로운 설정을 살펴보고 필요에 따라 APP 설정을 업데이트해야 합니다.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Windows 10 Wi-Fi 프로필에서 미리 공유한 키 사용 <!-- 2662938 -->
WPA/WPA2-개인 보안 프로토콜과 함께 PSK(미리 공유한 키)를 사용해 Windows 10의 Wi-Fi 구성 프로필을 인증할 수 있습니다.
현재, 미리 공유한 키를 사용하려면 Wi-Fi 프로필을 가져오거나 사용자 지정 프로필을 만들어야 합니다. [Windows 10의 Wi-Fi 설정](wi-fi-settings-windows.md)에는 현재 설정이 나열됩니다. 

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 장치의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다.  

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Autopilot 장치 동기화 빈도가 매 12시간으로 잦아짐 <!-- 2753673 -->
Autopilot 장치가 24시간이 아닌 12시간마다 동기화됩니다.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune 방문 페이지 업데이트 및 노드 이름 바꾸기 <!--2867309 -->
Intune 방문 페이지의 업데이트에는 데이터 시각화 개선을 위해 새로 생성되거나 변경된 모니터링 타일 및 차트가 들어 있습니다. **모바일 앱** 노드가 **클라이언트 앱**으로 변경됩니다.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>회사 포털 앱을 사용해 최종 사용자의 액세스가 늘어남 <!-- 772203 -->
최종 사용자는 회사 포털 앱에서 암호 재설정 및 AAD 프로필 등과 같은 주요 계정 작업에 액세스할 수 있습니다.  

<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="ios-and-macos-version-numbers-and-build-numbers-are-shown----1892471---"></a>iOS 및 macOS 버전 번호와 빌드 번호가 <!-- 1892471 -->로 표시됩니다.
**장치 준수** > **장치 준수**에서 iOS 및 macOS 운영체제 버전이 표시됩니다. 향후 업데이트에서는 두 플랫폼에 대한 빌드 번호도 표시됩니다.

보안 업데이트가 릴리스되는 경우 Apple에서는 일반적으로 버전 번호는 그대로 유지하지만 빌드 번호는 업데이트합니다. 빌드 번호가 표시되면 취약성 업데이트가 설치되어 있는지 쉽게 확인할 수 있습니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>장치 준수 대시보드에 사용 중지된 장치가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 장치가 장치 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>온-프레미스 커넥터에 대한 업데이트 프로세스 변경 <!-- 2277554 -->
고객의 의견에 따라 온-프레미스 커넥터가 업데이트되는 방식이 변경됩니다. 온-프레미스 커넥터를 처음 설치하면 업데이트가 자동으로 수행됩니다. 이 변경은 Microsoft Intune용 새 PFX 인증서 커넥터를 사용하여 시작되며 이후에는 다른 유형의 온-프레미스 커넥터로 롤아웃됩니다. 

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>장치 등록 관리자 사용자 <!-- 675800 -->을 위한 회사 포털 앱 환경 개선
DEM(장치 등록 관리자)이 Windows용 회사 포털 앱에 로그인하면 앱은 DEM의 현재 실행 중인 장치만 나열됩니다. 이러한 향상된 기능은 앱이 모든 DEM 등록 장치를 로드하려고 시도할 때 이전에 발생한 시간 초과를 줄입니다.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 System Center Configuration Manager 준수 설정이 포함됩니다(**장치 준수** > **정책** > **정책 만들기** > **Windows 10**). Configuration Manager는 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 장치에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 장치의 프로그램이 알 수 없는 상태에 있는 경우 장치는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 차단할 수 있는 타사 키보드 <!-- 1248481 -->
iOS 장치에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(응용 프로그램 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 장치 사용자에게 표시되지 않습니다. 대화 메시지가 장치 사용자에게 한 번만 표시됩니다. 

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>지정된 시간 제한 이후에는 비생체 인식 암호 필요 <!-- 1506985 --> 

관리자 지정 시간 제한 후에 비생체 인식 암호를 요구하면, Intune에서 회사 데이터에 액세스하는 데 생체 인식 ID를 사용하는 것을 제한하여 MAM(모바일 응용 프로그램 관리) 지원 앱에 향상된 보안을 제공합니다. 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 기타 미래의 생체 인식 인증 방법을 사용하여 APP/MAM 지원 응용 프로그램에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 세부적으로 제어하여 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 장치로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **모바일 앱** > **응용 프로그램 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android용 회사 포털 앱에서 도움말 및 피드백 환경 업데이트 <!--1631531 -->

Android 앱에 대한 모범 사례에 맞게 Android용 회사 포털 앱의 도움말 및 피드백 환경을 업데이트합니다. 향후 몇 개월 동안 Android용 회사 포털 앱을 업데이트하여 **도움말 및 피드백** 메뉴 항목을 별개의 **도움말** 및 **피드백 보내기** 메뉴 항목으로 나눕니다. **도움말** 페이지는 **질문과 대답** 섹션 및 **이메일 지원** 버튼이 특징적으로 최종 사용자가 Microsoft에 로그를 업로드하고 이 문제를 설명하는 고객 지원팀에 이메일을 보내도록 지원합니다. **피드백 보내기**는 사용자를 표준 Microsoft 피드백 제출 과정으로 이끌어 사용자가 "마음에 듭니다," "마음에 들지 않습니다" 또는 “잘 모르겠습니다” 여부를 선택하게 합니다.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.



