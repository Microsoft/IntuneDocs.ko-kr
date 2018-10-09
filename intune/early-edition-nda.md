---
title: 초기 버전
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: beee1462c1b6e683287b4d304df386ce525be820
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141646"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Microsoft Intune 초기 버전 - 2018년 9월

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>관리되는 Android 및 iOS 장치에서 Intune 앱의 사용자 계정 액세스 <!-- ! 1248496  -->

Microsoft Intune 관리자는 관리되는 장치에서 Microsoft Office 응용 프로그램에 추가할 사용자 계정을 제어할 수 있습니다. 허용되는 조직 사용자 계정만 액세스하도록 제한하고 등록된 장치에서 개인 계정을 차단할 수 있습니다. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Windows 10을 실행하는 장치의 VPN 구성 프로파일에서 DNS 접미사 생성 <!-- 1333668 -->
VPN 장치 구성 프로필을 만들 때(**장치 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** 플랫폼 > **VPN** 프로필 유형) DNS 설정을 몇 개 입력합니다. 또한 Intune에서 **DNS 접미사**를 여러 개 입력할 수 있습니다. DNS 접미사를 사용하는 경우 FQDN(정규화된 도메인 이름) 대신 짧은 이름을 사용해 네트워크 리소스를 검색할 수 있습니다. 이 업데이트를 설치하면 Intune에서 DNS 접미사의 순서를 변경할 수도 있습니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md#dns-settings)에는 현재 DNS 설정이 나열됩니다.
적용 대상: Windows 10 장치

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Android 엔터프라이즈 작업 프로필의 상시 VPN에 대한 지원<!-- 1333705 -->
Android 엔터프라이즈 장치에서는 관리되는 작업 프로필과 함께 상시 VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 장치를 잠금 해제한 경우, 장치가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
상시 VPN 설정은 프로필 유형의 **작업 프로필만** > **연결성** 설정에서 **장치 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대한 **Android enterprise** > **장치 제한**에서 지정합니다. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>iOS용 Outlook 및 Android 앱 구성 정책 <!--1828527 -->
iOS용 Outlook과 iOS의 Android 앱 구성 정책을 만들 수 있습니다. Android 및 iOS용 Outlook에 사용하도록 설정된 경우 구성 설정이 더 추가됩니다.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>원격으로 비호환 장치 잠그기 <!-- 2064495 -->
장치가 호환되지 않는 경우 원격으로 장치를 잠그는 준수 정책의 작업을 생성할 수 있습니다. Intune > **장치 준수**에서 새 정책을 생성하거나 기존 정책을 선택합니다. **비준수에 대한 작업** > **추가**를 선택하고 장치를 원격으로 잠그도록 선택합니다.
지원 됩니다. 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 이상 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>iOS MDM 등록 장치의 Intune APP 데이터 전송 설정 <!-- 2244713 -->
등록된 사용자의 ID를 지정하는 것과 iOS MDM 등록 장치의 Intune APP 데이터 전송 설정 제어를 구분할 수 있습니다. IntuneMAMUPN을 사용하지 않는 관리자는 동작 변경을 관찰하지 않습니다. 이 기능을 사용할 수 있게 되면 IntuneMAMUPN을 사용해 등록된 장치의 데이터 전송 동작을 제어하는 관리자가 새로운 설정을 살펴보고 필요에 따라 APP 설정을 업데이트해야 합니다.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Windows 10 Wi-Fi 프로필에서 미리 공유한 키 사용 <!-- 2662938 -->
WPA/WPA2-개인 보안 프로토콜과 함께 PSK(미리 공유한 키)를 사용해 Windows 10의 Wi-Fi 구성 프로필을 인증할 수 있습니다.
현재, 미리 공유한 키를 사용하려면 Wi-Fi 프로필을 가져오거나 사용자 지정 프로필을 만들어야 합니다. [Windows 10의 Wi-Fi 설정](wi-fi-settings-windows.md)에는 현재 설정이 나열됩니다. 

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Autopilot 장치 동기화 빈도가 매 12시간으로 잦아짐 <!-- 2753673 -->
Autopilot 장치가 24시간이 아닌 12시간마다 동기화됩니다.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>아직 Autopilot에는 등록하지 않았지만 등록된 Win 10 장치에 Autopilot 프로필 적용 <!-- 1558983 -->
아직 Autopilot에 등록되지 않은 등록한 Win 10 장치에 Autopilot 프로필을 적용할 수 있습니다. Autopilot 프로필에서 **모든 대상 장치를 Autopilot으로 변환** 옵션을 선택하면 Autopilot 배포 서비스에 Autopilot 장치 이외 장치를 자동으로 등록합니다. 등록을 처리하는 데 48시가 가량 걸립니다. 장치 등록을 취소하고 재설정하면 Autopilot이 해당 장치를 프로비전합니다. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>등록 상태 페이지 프로필을 여러 개 만들어 Azure AD 그룹에 할당 <!-- 2526564-->
여러 등록 상태 페이지 프로필을 만들어 Azure AD 사용자 그룹에 할당할 수 있습니다.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Intune 방문 페이지 업데이트 및 노드 이름 바꾸기 <!--2867309 -->
Intune 방문 페이지의 업데이트에는 데이터 시각화 개선을 위해 새로 생성되거나 변경된 모니터링 타일 및 차트가 들어 있습니다. **모바일 앱** 노드가 **클라이언트 앱**으로 변경됩니다.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>회사 포털 앱을 사용해 최종 사용자의 액세스가 늘어남 <!-- 772203 -->
최종 사용자는 회사 포털 앱에서 암호 재설정 및 AAD 프로필 등과 같은 주요 계정 작업에 액세스할 수 있습니다.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>사용자가 지정되지 않은 장치에 SCEP 인증서 발급 <!-- 1744554 -->
현재, 인증서가 사용자에게 발급되었습니다. 키오스크 등과 같이 사용자가 지정되지 않은 장치를 포함한 장치에 SCEP 인증서를 발급할 수 있습니다(**장치 구성** > **프로필** > **프로필 만들기** >  플랫폼용 **Windows 10 이상** > 프로필용 **SCEP 인증서**). 기타 업데이트는 다음과 같습니다.
- SCEP 프로필의 **주체** 속성은 이제 사용자 지정 텍스트 상자로, 새로운 변수를 포함할 수 있습니다. 
- SCEP 프로필의 **SAN(주체 대체 이름)** 속성은 이제 테이블 형식으로 새로운 변수를 포함할 수 있습니다. 관리자는 이 테이블에서 특성을 추가하고 사용자 지정 텍스트 상자에 값을 입력할 수 있습니다. SAN은 다음 특성을 지원합니다. 
  - DNS
  - 전자 메일 주소
  - UPN 사용자 정의 값 텍스트 상자에 정적 텍스트와 함께 새 변수를 추가할 수 있습니다. 예를 들어, DNS 특성을 `DNS = {{AzureADDeviceId}}.domain.com`으로 추가할 수 있습니다.
  > [!NOTE]
  > 중괄호, 세미콜론 및 파이프 기호 “{}; |”는 SAN의 정적 텍스트에서 작동하지 않습니다. `Subject` 또는 `Subject alternative name`에 대해 허용되도록 새 장치 인증서 변수 중 하나만 중괄호로 묶어야 합니다. 새 장치 인증서 변수:  
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
>  - `{{FullyQualifiedDomainName}}`은 Windows 및 도메인에 가입된 장치에서만 작동합니다. 
>  -  장치 인증서의 주체 또는 SAN에서 장치 속성(예: IMEI, 일련 번호 및 정규화된 도메인 이름)을 지정하는 경우 이러한 속성은 해당 장치의 액세스 권한을 가진 사람이 스푸핑할 수 있습니다. 

SCEP 구성 프로필을 만들 때 [SCEP 인증서 프로필 만들기](certificates-scep-configure.md#create-a-scep-certificate-profile)는 현재 변수를 나열합니다. 

적용 대상: Windows 10 이상 및 iOS, Wi-Fi 지원



<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS 버전 번호 및 빌드 번호 표시 <!-- 1892471 -->
**준수 준수** > **장치 준수**에서 iOS 운영체제 버전이 표시됩니다. 향후 업데이트에서는 빌드 번호도 표시됩니다.
보안 업데이트가 릴리스되는 경우 Apple에서는 일반적으로 버전 번호는 그대로 유지하지만 빌드 번호는 업데이트합니다. 빌드 번호가 표시되면 취약성 업데이트가 설치되어 있는지 쉽게 확인할 수 있습니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>장치 준수 대시보드에 사용 중지된 장치가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 장치가 장치 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>온-프레미스 커넥터에 대한 업데이트 프로세스 변경 <!-- 2277554 -->
고객의 의견에 따라 온-프레미스 커넥터가 업데이트되는 방식이 변경됩니다. 온-프레미스 커넥터를 처음 설치하면 업데이트가 자동으로 수행됩니다. 이 변경은 Microsoft Intune용 새 PFX 인증서 커넥터를 사용하여 시작되며 이후에는 다른 유형의 온-프레미스 커넥터로 롤아웃됩니다. 

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Azure Portal에서 Windows 10 이상 키오스크 프로필 개선 사항 <!-- 2748224 eeready -->
Windows 10 Kiosk 장치 구성 프로필(**장치 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Windows 10 이상** > 프로필 유형의 **키오스크 미리 보기**)이 개선됩니다. 
- 현재, 동일한 장치에서 여러 키오스크 프로필을 만들 수 있습니다. 이 업데이트를 설치하면 Intune에서는 장치당 키오스크 프로필을 하나만 지원합니다. 단일 장치에서 키오스크 프로필이 여러 개 필요한 경우 사용자 지정 URI를 사용할 수 있습니다.
-**다중 앱 키오스크** 프로필의 응용 프로그램 그리드에서 **시작 메뉴 레이아웃**의 응용 프로그램 타일 크기와 순서를 선택할 수 있습니다. 더 많은 부분을 사용자 지정하려는 경우 XML 파일을 계속해서 업로드할 수 있습니다.
- 키오스크 브라우저 설정은 **키오스크** 설정으로 이동합니다. 지금은 Azure Portal에 **키오스크 웹 브라우저** 설정의 고유 범주가 있습니다.
적용 대상: Windows 10 이상

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>장치 등록 관리자 사용자 <!-- 675800 -->을 위한 회사 포털 앱 환경 개선
DEM(장치 등록 관리자)이 Windows용 회사 포털 앱에 로그인하면 앱은 DEM의 현재 실행 중인 장치만 나열됩니다. 이러한 향상된 기능은 앱이 모든 DEM 등록 장치를 로드하려고 시도할 때 이전에 발생한 시간 초과를 줄입니다.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 System Center Configuration Manager 준수 설정이 포함됩니다(**장치 준수** > **정책** > **정책 만들기** > **Windows 10**). Configuration Manager는 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 장치에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 장치의 프로그램이 알 수 없는 상태에 있는 경우 장치는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows 설치 관리자에 대한 보안 설정 추가 <!-- 2282430 -->
사용자가 앱 설치를 제어하도록 허용할 수 있습니다. 사용하도록 설정한 경우 그렇지 않으면 보안 위반으로 인해 중지될 수 있는 설치를 계속 진행하도록 허용합니다. 시스템에 모든 프로그램을 설치할 때 Windows Installer가 상승된 권한을 사용하도록 지시할 수 있습니다. 또한 인덱싱될 WIP(Windows Information Protection) 항목 및 암호화되지 않은 위치에 저장된 WIP 항목의 메타데이터를 사용할 수 있습니다. 정책을 사용하지 않을 때 WIP로 보호되는 항목은 인덱싱되지 않고 Cortana 또는 파일 탐색기의 결과에 표시되지 않습니다. 이러한 옵션에 대한 기능은 기본적으로 사용할 수 없게 설정됩니다. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 차단할 수 있는 타사 키보드 <!-- 1248481 -->
iOS 장치에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(응용 프로그램 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 장치 사용자에게 표시되지 않습니다. 대화 메시지가 장치 사용자에게 한 번만 표시됩니다. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 언어 팩 <!-- 1833450 -->
Intune 관리자는 Intune을 통해 관리되는 Office 365 Pro Plus 앱의 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **모바일 앱** > **앱** > **추가**를 차례로 선택합니다. **앱 추가** 블레이드의**앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 블레이드에서 **언어**를 선택합니다.

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



