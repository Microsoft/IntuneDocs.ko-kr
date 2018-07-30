---
title: 초기 버전
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 3aed8fcefd640e5b7df46fe1ef8cd1c973a68044
ms.sourcegitcommit: 5251a630fb2c7a2e6f86abd84ab887f8eabc1481
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39212140"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>Microsoft Intune 초기 버전 - 2018년 7월

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

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Windows <!-- 2683177 -->용 회사 포털 앱에서 더 많은 동기화 기회 제공
Windows용 회사 포털 앱은 Windows 작업 표시줄 및 시작 메뉴 점프 목록에 장치 동기화 작업을 추가합니다. 두 위치 중 하나를 클릭하면 장치를 빠르게 동기화하고 회사 리소스에 액세스할 수 있습니다.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Windows 10용 회사 포털 앱에서 장치 암호 다시 설정 <!-- 2101282 --> 
직원들은 곧 Windows 10용 회사 포털 앱에서 장치의 PIN 또는 암호를 직접 다시 설정할 수 있습니다. 이 기능은 암호 다시 설정을 지원하는 원격 및 로컬 Intune 관리 장치에서 제공됩니다. 장치의 유형에 따라 원격 장치에 대한 요청은 장치의 현재 암호를 제거하거나 임시 암호를 만듭니다. 로컬 장치에 대한 다시 설정을 요청하는 사용자는 장치의 설정 앱으로 리디렉션됩니다.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Windows <!-- 2317227 -->용 회사 포털 앱의 새 검색 환경  
Windows용 회사 포털 앱에서 앱을 탐색하거나 검색하면 기존 **타일** 보기와 새로 추가된 **세부 정보** 보기 간에 전환할 수 있습니다. 새 보기에는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 응용 프로그램 세부 정보를 나열됩니다.  

**앱** 페이지에는 완료되었거나 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있는 **설치** 보기가 있습니다. 새로운 변화에 대한 피드백이나 생각을 공유하시겠습니까? 회사 포털 앱으로 피드백을 보내주세요.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>장치 등록 관리자 사용자 <!-- 675800 -->을 위한 회사 포털 앱 환경 개선
DEM(장치 등록 관리자)이 Windows용 회사 포털 앱에 로그인하면 앱은 DEM의 현재 실행 중인 장치만 나열됩니다. 이러한 향상된 기능은 앱이 모든 DEM 등록 장치를 로드하려고 시도할 때 이전에 발생한 시간 초과를 줄입니다.  

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>S/MIME를 사용하여 사용자의 여러 장치를 암호화 및 서명 <!-- 1333642 -->
향후 업데이트에는 가져온 새 인증서 프로필을 사용하는 S/MIME 이메일 암호화가 포함됩니다(**장치 구성** > **프로필** > **프로필 만들기** > 플랫폼 > **PKCS 가져온 인증서** 프로필 유형 선택). Intune에서 PFX 형식의 인증서를 가져올 수 있습니다. 그런 다음, Intune은 단일 사용자에 의해 등록된 여러 장치에 이러한 동일한 인증서를 제공할 수 있습니다. 다음도 포함되어 있습니다.

- 네이티브 iOS 이메일 프로필은 PFX 형식의 가져온 인증서를 사용하는 S/MIME 암호화 활성화를 지원합니다.
- Windows Phone 10 장치의 네이티브 메일 앱은 S/MIME 인증서를 자동으로 사용합니다.
- 여러 플랫폼에서 개인 인증서를 제공할 수 있습니다. 하지만 모든 이메일 앱이 S/MIME를 지원하지는 않습니다.
- 다른 플랫폼에서 S/MIME를 활성화하도록 메일 앱을 수동으로 구성해야 할 수 있습니다.  
- S/MIME 암호화를 지원하는 이메일 앱은 해당 게시자의 인증서 저장소에서 읽기와 같은 MDM에서 지원할 수 없는 방식으로 S/MIME 이메일 암호화에 대한 인증서 가져오기를 처리할 수 있습니다.

지원: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP 장치 라이선스를 사용하여 DEP 등록 중 회사 포털 사전 프로비전 <!-- 1608345 -->
VPP(대량 구매 프로그램) 장치 라이선스를 사용하여 DEP(장비 등록 프로그램) 등록 중 회사 포털을 사전 프로비전할 수 있습니다. 이렇게 하려면 등록 프로필을 만들거나 편집할 때 회사 포털을 설치하는 데 사용하려는 VPP 토큰을 지정합니다. 토큰이 만료되지 않았고 회사 포털 앱에 대한 충분한 라이선스가 있는지 확인합니다. 토큰이 만료되거나 라이선스가 부족한 경우 Intune은 App Store 회사 포털을 대신 푸시합니다(Apple ID에 대한 메시지를 표시함).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>장치 블레이드의 대량 삭제 장치 <!-- 1793693 -->
장치 블레이드에서 한 번에 여러 장치를 삭제할 수 있습니다. **장치** > **모든 장치** > 삭제할 장치 > **삭제**를 선택합니다. 삭제할 수 없는 장치의 경우 경고가 표시됩니다.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 이상용 새 Wi-Fi 장치 구성 프로필 <!-- 1879077 -->
현재 XML 파일을 사용하여 Wi-Fi 프로필 가져오고 내보낼 수 있습니다. 일부 다른 플랫폼과 마찬가지로 Intune에서 직접 Wi-Fi 장치 구성 프로필을 만들 수 있습니다.

프로필을 만들려면 **장치 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **Wi-Fi**를 엽니다. 

Windows 10 이상에 적용됩니다.

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Windows LOB(기간 업무) 앱 파일 확장명<!-- 1884873 -->
이제 Windows LOB 앱에 대한 파일 확장명에는 *.msi*, *.appx*, *.appxbundle*, *.msix* 및 *.msixbundle*이 포함됩니다. **모바일 앱** > **앱** > **추가**를 선택하여 Microsoft Intune에서 앱을 추가할 수 있습니다. **앱 유형**을 선택할 수 있는 **앱 추가** 창이 표시됩니다. Windows LOB 앱의 경우 앱 유형으로 **기간 업무** 앱을 선택하고, **앱 패키지 파일**을 선택한 다음, 적절한 확장명이 있는 설치 파일을 입력합니다.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>구성 프로필에 자동으로 추가된 Windows Defender ATP 구성 패키지 <!-- 2144658 -->
Intune에서 [고급 위협 보호 및 온보딩](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) 장치를 사용하는 경우 현재 구성 패키지를 다운로드하고, 구성 프로필에 추가합니다. 향후 업데이트에서 Intune은 Windows Defender Security Center에서 패키지를 자동으로 가져오고, 프로필에 추가합니다.

Windows 10 이상에 적용됩니다.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>키오스크 - 사용되지 않음은 회색으로 처리되고, 변경할 수 없음 <!-- 2149998 -->
[키오스크 기능](device-restrictions-windows-10.md#kiosk-preview---obsolete)(**장치 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **장치 제한**)은 사용되지 않으며, [Windows 10 이상용 키오스크 설정](kiosk-settings.md)으로 대체됩니다. **Kiosk - 사용되지 않음** 기능은 회색으로 처리되고, 사용자 인터페이스를 변경하거나 업데이트할 수 없습니다. 

키오스크 모드를 활성화하려면 [Windows 10 이상용 키오스크 설정](kiosk-settings.md)을 참조하세요.

적용 대상: Windows 10 이상, Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>타사 인증 기관을 사용하는 API <!-- 2184013 -->
Intune 및 SCEP와 통합하도록 타사 인증 기관을 활성화하는 Java API가 있습니다. 그러면 사용자는 프로필에 SCEP 인증서를 추가하고, MDM을 사용하여 장치에 적용할 수 있습니다.

현재 Intune은 [Active Directory 인증서 서비스를 사용하여 SCEP 요청](certificates-scep-configure.md)을 지원합니다.

### <a name="check-for-sccm-compliance----2192052---"></a>SCCM 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 SCCM(System Center Configuration Manager) 준수 설정이 포함됩니다(**장치 준수** > **정책** > **정책 만들기** > **Windows 10**). SCCM은 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 SCCM 신호에 "준수"를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 장치에 설치해야 합니다. SCCM에서 이 요구 사항은 "설치됨" 상태를 갖습니다. 장치의 프로그램이 알 수 없는 상태에 있는 경우 장치는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>회사 포털 사전 프로비전에 사용되는 VPP 토큰을 삭제하는 데 필요한 확인 <!-- 2237634 -->
DEP 등록 중 회사 포털을 사전 프로비전하는 데 VPP(대량 구매 프로그램) 토큰이 사용되는 경우 이를 삭제하는 데 확인이 필요합니다.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>삼성 Knox 모바일 등록을 사용하여 등록된 Android 장치를 "회사"로 자동으로 표시 <!-- 2404851 -->
기본적으로 삼성 Knox 모바일 등록을 사용하여 등록된 Android 장치는**장치 소유권** 아래에 **회사**로 표시됩니다. Knox 모바일 등록을 사용하여 등록하기 전에 IMEI 또는 일련 번호를 사용하여 회사 장치를 수동으로 식별할 필요가 없습니다.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 설정/해제 <!-- 2455253 -->
키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 구성할 수 있습니다. **장치 구성** > **키오스크(미리 보기)** > **키오스크 웹 브라우저**에서 컨트롤을 볼 수 있습니다. 설정된 경우 사용자가 단추를 클릭하면 앱은 세션을 종료할지 확인하는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터를 지우고 기본 URL로 다시 이동합니다.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 셀룰러 구성 프로필 만들기 <!-- 2564077 -->
**장치 구성**에서 eSIM 셀룰러 프로필을 만들 수 있습니다. 모바일 운영자가 제공하는 셀룰러 활성화 코드를 포함하는 파일을 가져올 수 있습니다. 그런 다음, 이러한 프로필을 Surface Pro LTE 및 eSIM 지원 장치와 같은 eSIM LTE가 활성화된 Windows 10 장치에 배포할 수 있습니다.

[장치에서 eSIM 프로필을 지원](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)하는지 확인합니다.

Windows 10 이상에 적용됩니다. 




<!-- 1806 start -->


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 차단할 수 있는 타사 키보드 <!-- 1248481 -->
iOS 장치에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(응용 프로그램 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 장치 사용자에게 표시되지 않습니다. 대화 메시지가 장치 사용자에게 한 번만 표시됩니다. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS 장치에서 방화벽 설정을 사용하는 장치 준수 정책 만들기 <!-- 1497640 -->
새 macOS 준수 정책을 만들면(**장치 준수** > **정책** > **정책 만들기** > **플랫폼: macOS** > **시스템 보안**) 다음과 같은 일부 새 **방화벽** 설정을 사용할 수 있습니다. 
- **방화벽**: 사용자 환경에서 들어오는 연결을 처리하는 방법을 구성합니다.
- **들어오는 연결**: DHCP, Bonjour 및 IPSec과 같은 기본 인터넷 서비스에 필요한 연결을 제외한 모든 들어오는 연결을 **차단**합니다. 이 설정은 모든 공유 서비스도 차단합니다.
- **은폐 모드**: 장치에서 검색 요청에 응답하지 못하도록 은폐 모드를 **사용하도록 설정**합니다. 장치는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다.

적용 대상: macOS 10.12 이상

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>앱 시작 및 시간 제한 시 비생체 인식 암호 필요 <!-- 1506985 -->

앱 시작 시 및 관리자 지정 시간 제한 후에 비생체 인식 암호를 요구하면, Intune에서 회사 데이터에 액세스하는 데 생체 인식 ID를 사용하는 것을 제한하여 MAM(모바일 응용 프로그램 관리) 지원 앱에 향상된 보안을 제공합니다. 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 기타 미래의 생체 인식 인증 방법을 사용하여 APP/MAM 지원 응용 프로그램에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 세부적으로 제어하여 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 장치로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **모바일 앱** > **응용 프로그램 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 언어 팩 <!-- 1833450 -->
Intune 관리자는 Intune을 통해 관리되는 Office 365 Pro Plus 앱에 대한 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **모바일 앱** > **앱** > **추가**를 차례로 선택합니다. **앱 추가** 블레이드의**앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 블레이드에서 **언어**를 선택합니다.

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>회사 포털 웹 사이트에 대한 새 사용자 환경 업데이트 미리 보기 <!--2000968 -->
고객으로부터의 피드백에 기반한 새 기능을 회사 포털 웹 사이트/iOS 앱 카탈로그에 추가하고 있습니다. Android, iOS 및 Windows 장치의 기존 기능과 유용성이 크게 향상됩니다. 장치 세부 정보, 피드백, 지원 및 장치 개요와 같은 사이트 영역은 응답성이 높은 최신의 새로운 디자인을 제공합니다. 또한 다음을 확인할 수 있습니다.

- 모든 장치 플랫폼에서 간소화된 워크플로
- 향상된 장치 식별 및 등록 흐름
- 더 유용한 오류 메시지
- 더 친숙한 언어, 더 이해하기 쉬운 기술 용어
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 향상
- 향상된 모든 사용자에 대한 접근성

업데이트가 현재 미리 보기로 제공됩니다. http://aka.ms/webcpflighting에서 미리 보기에 조인하도록 등록할 수 있습니다


### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus 앱 배포 편집 <!-- 2150145 -->
Microsoft Intune 관리자가 Office 365 Pro Plus 앱 배포를 편집할 수 있는 기능이 향상되었습니다. Azure Portal에서 **Microsoft Intune** > **모바일 앱** > **앱**을 차례로 선택합니다. 앱 목록에서 Office 365 Pro Plus 제품군을 선택합니다.  

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>콜드 앱 시작 및 시간 제한 시 비생체 인식 암호 필요 <!-- 1506985 --> 

콜드 앱 시작 시 및 관리자 지정 시간 제한 후에 비생체 인식 암호를 요구하면, Intune에서 회사 데이터에 액세스하는 데 생체 인식 ID를 사용하는 것을 제한하여 MAM(모바일 응용 프로그램 관리) 지원 앱에 향상된 보안을 제공합니다. 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 기타 미래의 생체 인식 인증 방법을 사용하여 APP/MAM 지원 응용 프로그램에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 세부적으로 제어하여 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 장치로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **모바일 앱** > **응용 프로그램 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>승인되지 않은 장치 공급업체 및 모델을 기준으로 앱 액세스 차단 <!-- 1425689 ! -->
Intune IT 관리자는 Intune 앱 보호 정책을 통해 지정된 Android 제조업체 및/또는 iOS 모델 목록을 적용할 수 있습니다. IT 관리자는 Android 정책용 제조업체 및 iOS 정책용 장치 모델의 세미콜론으로 구분된 목록을 제공할 수 있습니다. Intune 앱 보호 정책은 Android 및 iOS에만 적용됩니다. 이 지정된 목록에서 수행할 수 있는 두 가지 작업은 다음과 같습니다.
- 지정되지 않은 장치에 대한 앱 액세스 차단
- 또는 지정되지 않은 장치에서 회사 데이터 선택적 초기화. 

정책을 통한 요구 사항이 충족되지 않으면 사용자가 대상 응용 프로그램에 액세스할 수 없습니다. 설정에 따라 사용자는 차단되거나 앱 내의 해당 회사 데이터에서 선택적으로 초기화될 수 있습니다. iOS 장치에서 이 기능을 사용하려면 응용 프로그램(즉, WXP, Outlook, Managed Browser, Yammer)에 참여하여 최소 버전 설정을 대상 응용 프로그램에 적용하도록 Intune 앱 SDK를 통합해야 합니다. 이 통합은 롤링 기반으로 특정 응용 프로그램 팀에서 수행합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 

최종 사용자 장치에서 Intune 클라이언트는 응용 프로그램 보호 정책에 대한 Intune 블레이드에 지정된 문자열의 단순 일치를 기반으로 동작을 수행합니다. 이 동작은 전적으로 장치가 보고하는 값에 따라 결정됩니다. 따라서 IT 관리자는 의도한 동작이 정확한지 확인하는 것이 좋습니다. 이를 확인하려면 작은 사용자 그룹을 대상으로 하는 다양한 장치 제조업체 및 모델을 기반으로 이 설정을 테스트하면 됩니다. Microsoft Intune에서 **모바일 앱** > **앱 보호 정책**을 선택하여 앱 보호 정책을 보고 추가합니다. 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.


<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 Desktop 장치의 모든 사용자에게 필수 LOB(기간 업무) 앱을 배포하는 기능 <!-- 1627835 RS4 -->
고객은 필수 LOB(기간 업무) Windows 10 앱을 장치 컨텍스트에 설치하도록 배포할 수 있습니다. 이렇게 하면 이러한 앱을 장치의 모든 사용자가 사용할 수 있습니다. 이 기능은 Windows 10 Desktop 장치에만 적용됩니다.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Android용 회사 포털 앱에서 도움말 및 피드백 환경 업데이트 <!--1631531 -->

Android 앱에 대한 모범 사례에 맞게 Android용 회사 포털 앱의 도움말 및 피드백 환경을 업데이트합니다. 향후 몇 개월 동안 Android용 회사 포털 앱을 업데이트하여 **도움말 및 피드백** 메뉴 항목을 별개의 **도움말** 및 **피드백 보내기** 메뉴 항목으로 나눕니다. **도움말** 페이지는 **질문과 대답** 섹션 및 **이메일 지원** 버튼이 특징적으로 최종 사용자가 Microsoft에 로그를 업로드하고 이 문제를 설명하는 고객 지원팀에 이메일을 보내도록 지원합니다. **피드백 보내기**는 사용자를 표준 Microsoft 피드백 제출 과정으로 이끌어 사용자가 "마음에 듭니다," "마음에 들지 않습니다" 또는 “잘 모르겠습니다” 여부를 선택하게 합니다.

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>앱 보호 정책 <!-- 679615 -->
Intune 앱 보호 정책은 전체 테넌트의 모든 사용자에 대해 보호를 빠르게 사용할 수 있도록 전역 기본 정책을 만드는 기능을 제공합니다.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.