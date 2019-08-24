---
title: 지난 달의 새로운 Microsoft Intune 기능 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune 새로운 기능 페이지에서 이전 공지 사항 검토
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 2/25/2019
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 9ba01d60-4a03-4e3e-9aba-8be905c0054c
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8df4a1d7f929301c11f577a9b7e50ef1647dda11
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423716"
---
# <a name="whats-new-in-the-microsoft-intune---previous-months"></a>Microsoft Intune의 새로운 기능 - 지난 달

[!INCLUDE [azure_portal](./includes/azure_portal.md)]


<!-- ########################## -->
## <a name="september-2018"></a>2018년 9월

### <a name="app-management"></a>앱 관리

#### <a name="remove-duplication-of-app-protection-status-tiles----3083391---"></a>앱 보호 상태 타일의 중복 제거 <!-- 3083391 -->
**iOS 사용자 상태** 및 **Android 사용자 상태** 타일은 **클라이언트 앱 - 개요** 페이지와 **클라이언트 앱 - 앱 보호 상태** 페이지에 모두 있습니다. 상태 타일은 복제되지 않도록 **클라이언트 앱 - 개요** 페이지에서 제거되었습니다. 

### <a name="device-configuration"></a>디바이스 구성

#### <a name="support-for-more-third-party-certification-authorities-ca----3093107---"></a>더 많은 타사 CA(인증 기관) 지원 <!-- 3093107 -->
이제 SCEP(단순 인증서 등록 프로토콜)를 사용하면 Windows, iOS, Android 및 macOS를 사용하는 모바일 디바이스에서 새로운 인증서를 발급하고 기존 인증서를 갱신할 수 있습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="intune-moves-to-support-ios-10-and-later----2454656---"></a>iOS 10 이상 지원을 위한 Intune 이동 <!-- 2454656 -->  
이제 Intune 등록, 회사 포털 및 관리되는 브라우저에서 iOS 10 이상을 실행하는 iOS 디바이스만 지원합니다. 조직에 영향을 주는 디바이스 또는 사용자를 확인하려면 Azure Portal &gt; **디바이스** > **모든 디바이스**에서 Intune으로 이동합니다. OS별로 필터링한 다음, **열**을 클릭하여 OS 버전 세부 사항을 표시합니다. 이러한 사용자에게 지원되는 OS 버전으로 디바이스를 업그레이드하도록 요청합니다.  

아래에 나열된 모든 디바이스가 있거나 아래에 나열된 모든 디바이스를 등록하려는 경우 이러한 디바이스가 iOS 9 이하만 지원한다는 것을 잊지 마세요.  Intune 회사 포털에 액세스를 계속하려면 이러한 디바이스를 iOS 10 이상을 지원하는 디바이스로 업그레이드해야 합니다.  

* iPhone 4S 
* iPod Touch  
* iPad 2 
* iPad(3세대) 
* iPad 미니(1세대)  

### <a name="device-management"></a>디바이스 관리

#### <a name="microsoft-365-device-management-administration-center----3078424---"></a>Microsoft 365 Device Management 관리 센터 <!-- 3078424 -->
Microsoft 365의 약속 중 하나는 단순화된 관리이며, 백엔드 Microsoft 365 서비스를 통합하여 Intune 및 Azure AD 조건부 액세스와 같은 통합형 시나리오를 제공하는 것입니다. 새 [Microsoft 365 관리 센터](http://devicemanagement.microsoft.com)는 관리 환경을 통합, 단순화 및 통합하는 작업 공간입니다. 디바이스 관리 팀의 전문가 작업 공간에서는 조직에 필요한 모든 디바이스 및 앱 관리 정보와 작업에 쉽게 액세스할 수 있습니다. 이 작업 공간은 엔터프라이즈 최종 사용자 컴퓨팅 팀의 기본 클라우드 작업 공간이 될 것으로 예상합니다.


<!-- ########################## -->
## <a name="august-2018"></a>2018년 8월

### <a name="app-management"></a>앱 관리

#### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>사용자 지정 및 Pulse Secure 연결 형식에 대한 iOS 앱당 VPN 프로필의 패킷 터널 지원 <!-- 1520957 -->
iOS 앱당 VPN 프로필을 사용할 때 앱 계층 터널링(app-proxy) 또는 패킷 수준 터널링(packet-tunnel)을 사용하도록 선택할 수 있습니다. 이러한 옵션을 사용할 수 있는 연결 형식은 다음과 같습니다.
- 사용자 지정 VPN
- Pulse Secure. 사용할 값을 모르는 경우 VPN 공급자의 설명서를 참조하세요.

#### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>디바이스에 표시될 때의 iOS 소프트웨어 업데이트 지연 <!-- 1949583 -->
Intune &gt; **소프트웨어 업데이트** > **iOS용 정책 업데이트**에서 디바이스에 업데이트를 설치하지 않으려는 일 수와 시간을 구성할 수 있습니다. 향후 업데이트에서는 소프트웨어 업데이트가 디바이스에 표시될 때 해당 업데이트를 1-90일 동안 지연시킬 수 있습니다. 
[Microsoft Intune에서 iOS 업데이트 정책 구성](software-updates-ios.md)에는 현재 설정이 나열되어 있습니다.

#### <a name="office-365-proplus-version----2213968---"></a>Office 365 ProPlus 버전 <!-- 2213968 -->
Intune을 사용하여 Office 365 ProPlus 앱을 Windows 10 디바이스에 할당하는 경우 Office 버전을 선택할 수 있습니다. Azure Portal에서 **Microsoft Intune** > **앱** > **앱 추가**를 차례로 선택합니다. 그런 다음, **형식** 드롭다운 목록에서 **Office 365 ProPlus 제품군(Windows 10)** 을 선택합니다. 연결된 블레이드를 표시하려면 **앱 제품군 설정**을 선택합니다. **업데이트 채널**을 **매월**과 같은 값으로 설정합니다. 필요에 따라 **예**를 선택하여 최종 사용자 디바이스에서 다른 버전의 Office(msi)를 제거합니다. 최종 사용자 디바이스에서 선택한 채널에 대한 특정 버전의 Office를 설치하려면 **특정**을 선택합니다. 여기서는 사용할 Office의 **특정 버전**을 선택할 수 있습니다. 사용 가능한 버전은 시간이 지남에 따라 변경됩니다. 따라서 새 배포를 만들 때 사용 가능한 버전이 최신 버전일 수 있으며 이전 버전이 제공되지 않을 수 있습니다. 현재 배포에서는 이전 버전을 계속 배포하지만, 버전 목록은 채널별로 지속적으로 업데이트됩니다. 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.

#### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN에 대한 DNS 등록 설정 지원 <!-- 2282852 -->
이 업데이트를 사용하여 사용자 지정 프로필을 사용하지 않고도 VPN 인터페이스에 할당된 IP 주소를 내부 DNS와 동적으로 등록하도록 Windows 10 VPN 프로필을 구성할 수 있습니다.
현재 사용 가능한 VPN 프로필 설정에 대한 자세한 내용은 [Windows 10 VPN 설정](vpn-settings-windows-10.md)을 참조하세요. 

#### <a name="the-macos-company-portal-installer-now-includes-the-version-number-in-the-installer-file-name---2652728--"></a>이제 macOS 회사 포털 설치 관리자는 설치 관리자 파일 이름에 버전 번호를 포함함 <!--2652728-->

#### <a name="ios-automatic-app-updates----2729759---"></a>iOS 자동 앱 업데이트 <!-- 2729759 -->
자동 앱 업데이트는 iOS 버전 11.0 이상의 디바이스 및 사용자에게 사용이 허가된 앱 모두에서 작동합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello는 사용자 및 디바이스를 대상으로 함 <!-- 1106609 -->
[비즈니스용 Windows Hello](windows-hello.md) 정책을 만들면 조직 내의 모든 사용자(테넌트 수준)에게 적용됩니다. 이 업데이트를 사용하면 디바이스 구성 정책을 사용하여 특정 사용자 또는 특정 디바이스에 정책을 적용할 수도 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **ID 보호** > **비즈니스용 Windows Hello**).
Windows Hello 구성 및 설정은 이제 Azure Portal의 Intune에서 **디바이스 등록** 및 **디바이스 구성**에 모두 존재합니다. **디바이스 등록**은 전체 조직(테넌트 수준)을 대상으로 하며 Windows AutoPilot(OOBE)을 지원합니다. **디바이스 구성**은 체크 인 중에 적용되는 정책을 사용하는 디바이스와 사용자를 대상으로 합니다.
이 기능은 다음에 적용됩니다.  
- Windows 10 이상
- Windows Holographic for Business

#### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858---"></a>Zscaler는 iOS의 VPN 프로필에 사용할 수 있는 연결입니다. <!-- 1769858 -->
iOS VPN 디바이스 구성 프로필을 만드는 경우(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼 &gt; **VPN** 프로필 유형), Cisco, Citrix 등과 같은 몇 가지 연결 형식이 있습니다. 이 업데이트는 연결 형식으로 Zscaler를 추가합니다. 
[iOS를 실행하는 디바이스에 대한 VPN 설정](vpn-settings-ios.md)에는 사용 가능한 연결 형식이 나열되어 있습니다.

#### <a name="fips-mode-for-enterprise-wi-fi-profiles-for-windows-10----1879077---"></a>Windows 10용 엔터프라이즈 Wi-Fi 프로필에 대한 FIPS 모드 <!-- 1879077 -->
이제 Intune Azure Portal에서 Windows 10용 엔터프라이즈 Wi-Fi 프로필에 대해 FIPS(Federal Information Processing Standards) 모드를 사용할 수 있습니다. Wi-Fi 프로필에서 사용하는 경우 Wi-Fi 인프라에서 FIPS 모드가 활성화되어 있어야 합니다.
[Intune에서 Windows 10 이상 디바이스에 대한 Wi-Fi 설정](wi-fi-settings-windows.md)은 Wi-Fi 프로필을 만드는 방법을 보여줍니다.

#### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 이상의 디바이스에서 S 모드 제어 - 공개 미리 보기 <!-- 1958649 -->
이 기능 업데이트를 사용하여 Windows 10 디바이스를 S 모드에서 전환하거나 사용자가 S 모드에서 디바이스를 전환하지 못하게 하는 디바이스 구성 프로필을 만들 수 있습니다. 이 기능은 Intune &gt; **디바이스 구성** > **프로필** >  **Windows 10 이상** > **버전 업그레이드 및 모드 전환**에 있습니다.
[Windows 10 S 모드 소개](https://www.microsoft.com/windows/s-mode)에서 S 모드에 대한 자세한 정보를 제공합니다.
적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)

#### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>구성 프로필에 자동으로 추가된 Windows Defender ATP 구성 패키지 <!-- 2144658 -->
Intune에서 [고급 위협 보호 및 온보딩](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) 디바이스를 사용하는 경우 이전에 구성 패키지를 다운로드하고, 구성 프로필에 추가해야 했습니다. 이 업데이트를 사용하여 Intune은 Windows Defender Security Center에서 패키지를 자동으로 가져오고, 프로필에 추가합니다.
Windows 10 이상에 적용됩니다.

#### <a name="require-users-to-connect-during-device-setup---2311457--"></a>디바이스 설정 중에 사용자가 연결하도록 요구 <!--2311457-->
이제 Windows 10을 설치하는 동안 네트워크 페이지를 지나 계속 진행하기 전에 네트워크에 디바이스를 연결하도록 요구하는 디바이스 프로필을 설정할 수 있습니다. 이 기능이 미리 보기 상태인 동안 이 설정을 사용하려면 Windows Insider build 1809 이상이 필요합니다.
적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)

#### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-enterprise-devices----2451462---"></a>iOS 및 Android Enterprise 디바이스에서 앱 제한 및 회사 리소스 차단 <!-- 2451462 -->
**디바이스 준수** > **정책** > **정책 만들기** > **iOS** > **시스템 보안**에는 새로운 **제한된 애플리케이션** 설정이 있습니다. 특정 응용 프로그램이 디바이스에 설치되어 있는 경우 이 새로운 설정은 준수 정책을 사용하여 회사 리소스에 대한 액세스를 차단합니다. 제한된 응용 프로그램이 디바이스에서 제거될 때까지 디바이스는 정책을 준수하지 않는 것으로 간주됩니다.
적용 대상: iOS

#### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>iOS용 최신 VPN 지원 업데이트 <!-- 2459928, 1819876, and 2650856 -->
이 업데이트는 다음 iOS VPN 클라이언트 지원을 추가합니다. 
- F5 Access(버전 3.0.1 이상)
- Citrix SSO
- Palo Alto Networks GlobalProtect 버전 5.0 이상 또한 이 업데이트에서는 다음과 같이 적용됩니다.
- 기존 **F5 Access** 연결 형식의 이름은 iOS에 대해 **F5 Access Legacy**로 변경됩니다.
- 기존 **Palo Alto Networks GlobalProtect** 연결 형식의 이름이 iOS에 대해 **Palo Alto Networks GlobalProtect(레거시)** 로 변경됩니다.
이러한 연결 형식의 기존 프로필은 해당 레거시 VPN 클라이언트에서 계속 사용됩니다. iOS에서 Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN 또는 Palo Alto Networks GlobalProtect 버전 4.1 이전을 사용하는 경우 새 앱으로 전환해야 합니다. iOS 디바이스에서 iOS 12로 업데이트하는 대로 가능한 한 빨리 이 작업을 수행하여 VPN 액세스를 사용할 수 있도록 합니다.
iOS 12 및 VPN 프로필에 대한 자세한 내용은 [Microsoft Intune 지원 팀 블로그](https://go.microsoft.com/fwlink/?linkid=2013806)를 참조하세요.

#### <a name="export-azure-classic-portal-compliance-policies-to-recreate-these-policies-in-the-intune-azure-portal----2469637---"></a>Intune Azure Portal에서 이러한 정책을 다시 만들도록 Azure 클래식 포털 준수 정책 내보내기 <!-- 2469637 -->
Azure 클래식 포털에서 만든 준수 정책은 더 이상 사용되지 않습니다. 기존 준수 정책을 검토하고 삭제할 수 있지만 업데이트할 수는 없습니다. 준수 정책을 현재 Intune Azure Portal로 마이그레이션하려는 경우 쉼표로 구분된 파일로 정책을 내보낼 수 있습니다( *.csv* 파일). 그런 다음, 파일의 세부 정보를 사용하여 Intune Azure Portal에서 이러한 정책을 다시 만듭니다.

> [!IMPORTANT]
> Azure 클래식 포털에서 사용 중지하는 경우 더 이상 준수 정책에 액세스하거나 볼 수 없습니다. 따라서 Azure 클래식 포털이 사용 중지되기 전에 Azure Portal에서 정책을 내보내고 다시 만들어야 합니다.

#### <a name="better-mobile---new-mobile-threat-defense-partner----22662717---"></a>향상된 모바일 - 새 Mobile Threat Defense 파트너 <!-- 22662717 -->
Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Better Mobile에서 수행된 위험 평가에 따라 조건부 액세스를 사용하여 모바일 디바이스에서 회사 리소스에 대한 액세스를 제어할 수 있습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>사용자가 로그인할 때까지 회사 포털을 단일 앱 모드로 잠금 <!--1067692 --> 
DEP 등록 중에 설정 도우미 대신 회사 포털을 통해 사용자를 인증하는 경우 이제 회사 포털을 단일 앱 모드에서 실행할 수 있습니다. 이 옵션을 사용하면 설정 도우미가 완료되는 즉시 디바이스를 잠그므로 사용자가 디바이스에 액세스하려면 로그인해야 합니다. 이 프로세스는 디바이스가 온보딩을 완료하고 사용자가 연결되지 않은 상태에서 분리되지 않도록 합니다.

#### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Autopilot 디바이스에 사용자 및 식별 이름 할당 <!--1346521 -->
이제 [단일 Autopilot 디바이스에 사용자를 할당](enrollment-autopilot.md)할 수 있습니다. 또한 관리자는 AutoPilot을 사용하여 디바이스를 설정할 때 사용자에게 친숙한 식별 이름도 지정할 수 있습니다.
적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)

#### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>VPP 디바이스 라이선스를 사용하여 DEP 등록 중 회사 포털 사전 프로비전 <!-- 1608345 -->
이제 VPP(대량 구매 프로그램) 디바이스 라이선스를 사용하여 DEP(장비 등록 프로그램) 등록 중 회사 포털을 사전 프로비전할 수 있습니다. 이렇게 하려면 [등록 프로필을 만들거나 편집](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)할 때 회사 포털을 설치하는 데 사용하려는 VPP 토큰을 지정합니다. 토큰이 만료되지 않았고 회사 포털 앱에 대한 충분한 라이선스가 있는지 확인합니다. 토큰이 만료되거나 라이선스가 부족한 경우 Intune은 App Store 회사 포털을 대신 푸시합니다(Apple ID에 대한 메시지를 표시함).

#### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>회사 포털 사전 프로비저닝에 사용되는 VPP 토큰을 삭제하는 데 필요한 확인 <!-- 2237634 -->
DEP 등록 중 회사 포털을 사전 프로비전하는 데 VPP(대량 구매 프로그램) 토큰이 사용되는 경우 이를 삭제하는 데 이제는 확인이 필요합니다.

#### <a name="block-windows-personal-device-enrollments----1849498---"></a>Windows 개인 디바이스 등록 차단 <!-- 1849498 -->
Intune에서 [모바일 디바이스 관리](windows-enroll.md)를 사용하여 [Windows 개인 디바이스를 등록하지 못하도록 차단](enrollment-restrictions-set.md#set-device-type-restrictions)할 수 있습니다. [Intune PC 에이전트](manage-windows-pcs-with-microsoft-intune.md)를 통해 등록된 디바이스는 이 기능을 사용하여 차단할 수 없습니다. 이 기능은 향후 2주 이내에 출시 예정이기 때문에 당장은 사용자 인터페이스에서 보이지 않을 수 있습니다.

#### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Autopilot 프로필에 머신 이름 패턴 지정 <!--1849855-->
Autopilot 등록 중에 [컴퓨터 이름 템플릿을 지정](enrollment-autopilot.md#create-an-autopilot-deployment-profile)하여 [컴퓨터 이름](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)을 생성하고 설정할 수 있습니다. 적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)

#### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Windows Autopilot 프로필의 경우 회사 로그인 페이지 및 도메인 오류 페이지에서 계정 변경 옵션 숨기기 <!--1901669 -->
관리자가 회사 로그인 및 도메인 오류 페이지에서 계정 변경 옵션을 숨기는 [새 Windows Autopilot 프로필 옵션](enrollment-autopilot.md#create-an-autopilot-deployment-profile)이 포함됩니다. 이러한 옵션을 숨기려면 Azure Active Directory에서 회사 브랜딩을 구성해야 합니다. 적용 대상: 최신 [Windows Insider](https://docs.microsoft.com/windows-insider/at-work-pro/) 빌드(미리 보기 중)

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple 디바이스 등록 프로그램에 대한 macOS 지원 <!-- 747651 -->
이제 Intune은 macOS 디바이스를 Apple DEP(장비 등록 프로그램)에 등록할 수 있도록 지원합니다. 자세한 내용은 [Apple 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

### <a name="device-management"></a>디바이스 관리

#### <a name="delete-jamf-devices----2653306--"></a>Jamf 디바이스 삭제 <!-- 2653306-->
**디바이스** &gt; Jamf 디바이스 선택 &gt; **삭제**로 이동하여 JAMF 관리 디바이스를 삭제할 수 있습니다.

#### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>"사용 중지" 및 "초기화" 용어 변경 <!-- 2175759 -->
Graph API와 일관성을 유지하도록 Intune 사용자 인터페이스 및 설명서에서 다음 용어가 변경됩니다.
- **회사 데이터 제거**가 "사용 중지"로 변경됩니다.
- **출하 시 설정으로 초기화**가 **초기화**로 변경됩니다.

#### <a name="confirmation-dialog-if-admin-tries-to-delete-mdm-push-certificate----297909500--"></a>관리자가 MDM Push 인증서를 삭제하려고 하는 경우 확인 대화 상자 <!-- 297909500-->
누군가 Apple MDM Push Certificate를 삭제하려고 하면 확인 대화 상자에 관련된 iOS 및 macOS 디바이스의 번호가 표시됩니다. 인증서가 삭제되는 경우 이러한 디바이스를 다시 등록해야 합니다.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows 설치 관리자에 대한 추가 보안 설정 <!-- 2282430 -->
사용자가 앱 설치를 제어하도록 허용할 수 있습니다. 사용하도록 설정한 경우 그렇지 않으면 보안 위반으로 인해 중지될 수 있는 설치를 계속 진행하도록 허용합니다. 시스템에 모든 프로그램을 설치할 경우 Windows 설치 관리자가 상승된 권한을 사용하도록 명령할 수 있습니다. 또한 인덱싱될 WIP(Windows Information Protection) 항목 및 암호화되지 않은 위치에 저장된 WIP 항목에 대한 메타데이터를 사용할 수 있습니다. 정책을 사용하지 않을 때 WIP로 보호되는 항목은 인덱싱되지 않고 Cortana 또는 파일 탐색기의 결과에도 표시되지 않습니다. 이러한 옵션에 대한 기능은 기본적으로 사용할 수 없게 설정되어 있습니다. 

#### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트 <!--2000968 -->
고객으로부터의 피드백에 기반한 새 기능을 회사 포털 웹 사이트에 추가했습니다. 디바이스의 기존 기능과 유용성이 크게 향상됩니다. 사이트 영역&ndash;예: 디바이스 세부 정보, 피드백, 지원 및 디바이스 개요&ndash;은 응답성이 높은 최신의 새로운 디자인을 제공합니다. 또한 다음을 확인할 수 있습니다.

- 모든 디바이스 플랫폼에서 간소화된 워크플로
- 향상된 디바이스 식별 및 등록 흐름
- 더 유용한 오류 메시지
- 전문 기술 용어는 줄이고 친근한 언어 사용
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 개선
- 향상된 모든 사용자에 대한 접근성  

[Intune 회사 포털 웹 사이트 설명서](https://docs.microsoft.com/intune-user-help/using-the-intune-company-portal-website)는 이러한 변경 내용을 반영하도록 업데이트되었습니다. 향상된 앱의 예제를 보려면 [Intune 최종 사용자 앱 UI 업데이트](whats-new-app-ui.md)를 참조하세요.  

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="enhanced-jailbreak-detection-in-compliance-reporting---2198738---"></a>규정 준수 보고에서 향상된 탈옥 검색<!-- 2198738 -->
향상된 탈옥 검색 상태는 이제 관리 콘솔의 모든 준수 보고에 나타납니다.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-policies---1081974---"></a>정책에 대한 범위 태그 <!--1081974 -->
[범위 태그를 만들어](scope-tags.md) Intune 리소스에 대한 액세스를 제한할 수 있습니다. 역할 할당에 범위 태그를 추가한 다음, 범위 태그를 구성 프로필에 추가합니다. 역할은 일치하는 범위 태그가 있거나 범위 태그가 없는 구성 프로필이 있는 리소스에만 액세스할 수 있습니다.





<!-- ########################## -->
## <a name="july-2018"></a>2018년 7월

### <a name="app-management"></a>앱 관리

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS에 대한 LOB(기간 업무) 앱 지원 <!-- 1895847 -->
Microsoft Intune은 macOS LOB 앱을 **요청** 또는 **등록 시 사용 가능**으로 배포하게 허용합니다. 최종 사용자는 macOS용 회사 포털 또는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)를 사용하여 **사용 가능**으로 앱을 배포할 수 있습니다.

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>키오스크 모드에 대한 기본 제공 iOS 앱 지원 <!-- 2051098 -->
스토어 앱 및 관리되는 앱 외에도 iOS 디바이스에서 키오스크 모드로 실행되는 기본 제공 앱(예: Safari)을 이제 선택할 수 있습니다.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus 앱 배포 편집 <!-- 2150145 -->
Microsoft Intune 관리자가 Office 365 Pro Plus 앱 배포를 편집할 수 있는 기능이 향상되었습니다. 또한 제품군의 속성을 변경하기 위해 더 이상 배포를 삭제할 필요가 없습니다. Azure Portal에서 **Microsoft Intune** > **클라이언트 앱** > **앱**을 차례로 선택합니다. 앱 목록에서 Office 365 Pro Plus 제품군을 선택합니다.  

#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>업데이트된 Android용 Intune 앱 SDK 사용 가능 <!-- 2744271-->
Android P 릴리스를 지원하도록 Android용 Intune 앱 SDK의 업데이트된 버전이 제공됩니다. 앱 개발자이며 Android용 Intune SDK를 사용하는 경우 업데이트된 버전의 Intune 앱 SDK를 설치하여 Android 앱 내의 Intune 기능이 Android P 디바이스에서도 계속 예상대로 작동하는지 확인해야 합니다. 이 버전의 Intune 앱 SDK에는 SDK 업데이트를 수행하는 기본 제공 플러그인을 제공합니다. 통합된 모든 기존 코드를 다시 쓸 필요가 없습니다. 자세한 내용은 [Intune SDK for Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)(Android용 Intune SDK)를 참조하세요. Intune의 이전 배지 스타일을 사용하는 경우 서류 가방 아이콘을 사용하는 것이 좋습니다. 브랜딩 세부 정보는 [this GitHub repository](https://github.com/msintuneappsdk/intune-app-partner-badge)(이 GitHub 리포지토리)를 참조하세요.

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 동기화할 수 있는 더 많은 기회  
이제 Windows용 회사 포털 앱을 사용하여 Windows 작업 표시줄 및 시작 메뉴에서 직접 동기화를 시작할 수 있습니다. 이 기능은 디바이스를 동기화하고 회사 리소스에 액세스하는 작업만 수행하는 경우에 특히 유용합니다. 새 기능에 액세스하려면 작업 표시줄 또는 시작 메뉴에 고정되어 있는 회사 포털 아이콘을 마우스 오른쪽 단추로 클릭합니다. 메뉴 옵션(점프 목록이라고도 함)에서 **이 디바이스 동기화**를 선택합니다. 회사 포털에 **설정** 페이지가 열리고 동기화가 시작됩니다. 새로운 기능에 대한 내용은 [UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.   

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱의 새 검색 환경  
이제 Windows용 회사 포털 앱에서 앱을 탐색하거나 검색하면 기존 **타일** 보기와 새로 추가된 **세부 정보** 보기 간에 전환할 수 있습니다. 새 보기에는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 애플리케이션 세부 정보가 나열됩니다.  

**앱** 페이지의 **설치됨** 보기를 통해 완료 및 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있습니다. 새 보기의 모양을 보려면 [UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.  

#### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>디바이스 등록 관리자를 위한 회사 포털 앱 환경 개선  
DEM(디바이스 등록 관리자)이 Windows용 회사 포털 앱에 로그인하면 이제 앱은 DEM의 현재 실행 중인 디바이스만 나열됩니다. 이러한 향상된 기능은 앱이 모든 DEM 등록 디바이스를 표시하려고 시도할 때 이전에 발생한 시간 초과를 줄입니다.  

#### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>승인되지 않은 디바이스 공급업체 및 모델을 기준으로 앱 액세스 차단  <!-- 1425689 ! -->
Intune IT 관리자는 Intune 앱 보호 정책을 통해 지정된 Android 제조업체 및/또는 iOS 모델 목록을 적용할 수 있습니다. IT 관리자는 Android 정책용 제조업체 및 iOS 정책용 디바이스 모델의 세미콜론으로 구분된 목록을 제공할 수 있습니다. Intune 앱 보호 정책은 Android 및 iOS에만 적용됩니다. 이 지정된 목록에서 수행할 수 있는 두 가지 개별 작업은 다음과 같습니다.
- 지정되지 않은 디바이스에 대한 앱 액세스 차단
- 또는 지정되지 않은 디바이스에서 회사 데이터 선택적 초기화. 

정책을 통한 요구 사항이 충족되지 않으면 사용자가 대상 애플리케이션에 액세스할 수 없습니다. 설정에 따라 사용자는 차단되거나 앱 내의 해당 회사 데이터에서 선택적으로 초기화될 수 있습니다. iOS 디바이스에서 이 기능을 사용하려면 애플리케이션(예: WXP, Outlook, Managed Browser, Yammer)에 참여하여 대상 애플리케이션에 이 기능을 적용하기 위해 Intune APP SDK를 통합해야 합니다. 이 통합은 롤링 기반으로 특정 애플리케이션 팀에서 수행합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 

최종 사용자 디바이스에서 Intune 클라이언트는 애플리케이션 보호 정책에 대한 Intune 블레이드에 지정된 문자열의 단순 일치를 기반으로 동작을 수행합니다. 이 동작은 전적으로 디바이스가 보고하는 값에 따라 결정됩니다. 따라서 IT 관리자는 의도한 동작이 정확한지 확인하는 것이 좋습니다. 이를 확인하려면 작은 사용자 그룹을 대상으로 하는 다양한 디바이스 제조업체 및 모델을 기반으로 이 설정을 테스트하면 됩니다. Microsoft Intune에서 **클라이언트 앱** > **앱 보호 정책**을 선택하여 앱 보호 정책을 보고 추가합니다. 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md) 및 [Intune에서 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터 초기화](app-protection-policies-access-actions.md)를 참조하세요.

#### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>macOS 회사 포털 시험판 빌드에 액세스 <!-- 1734766 -->
Microsoft 자동 업데이트를 사용하여 등록할 수 있으며 Insider 프로그램에 참여하여 빌드를 조기에 받을 수 있습니다. 등록하면 업데이트된 회사 포털을 사용해 본 이후에 최종 사용자에게 제공할 수 있습니다. 자세한 내용은 [Microsoft Intune 블로그](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS 디바이스에서 방화벽 설정을 사용하는 디바이스 규정 준수 정책 만들기 <!-- 1497640 -->
새 macOS 준수 정책을 만들면(**디바이스 준수** > **정책** > **정책 만들기** > **플랫폼: macOS** > **시스템 보안**) 다음과 같은 일부 새 **방화벽** 설정을 사용할 수 있습니다. 

- **방화벽**: 사용자 환경에서 들어오는 연결을 처리하는 방법을 구성합니다.
- **들어오는 연결**: DHCP, Bonjour 및 IPSec과 같은 기본 인터넷 서비스에 필요한 연결을 제외한 모든 들어오는 연결을 **차단**합니다. 이 설정은 모든 공유 서비스도 차단합니다.
- **은폐 모드**: 디바이스에서 검색 요청에 응답하지 못하도록 은폐 모드를 **사용하도록 설정**합니다. 디바이스는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다.

적용 대상: macOS 10.12 이상

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 이상용 새 Wi-Fi 디바이스 구성 프로필 <!-- 1879077 -->
현재 XML 파일을 사용하여 Wi-Fi 프로필 가져오고 내보낼 수 있습니다. 이 업데이트를 사용하면 일부 다른 플랫폼과 마찬가지로 Intune에서 직접 Wi-Fi 디바이스 구성 프로필을 만들 수 있습니다.

프로필을 만들려면 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **Wi-Fi**를 엽니다. 

Windows 10 이상에 적용됩니다.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>키오스크 - 사용되지 않음은 회색으로 처리되고, 변경할 수 없음 <!-- 2149998 -->
키오스크(미리 보기) 기능(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **디바이스 제한**)은 사용되지 않으며, [Windows 10 이상용 키오스크 설정](kiosk-settings.md)으로 대체됩니다. 이 업데이트를 사용하면 **Kiosk - 사용되지 않음** 기능은 회색으로 처리되고, 사용자 인터페이스를 변경하거나 업데이트할 수 없습니다. 

키오스크 모드를 활성화하려면 [Windows 10 이상용 키오스크 설정](kiosk-settings.md)을 참조하세요.

적용 대상: Windows 10 이상, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>타사 인증 기관을 사용하는 API <!-- 2184013 -->
이 업데이트에는 Intune 및 SCEP와 통합하도록 타사 인증 기관을 활성화하는 Java API가 있습니다. 그러면 사용자는 프로필에 SCEP 인증서를 추가하고, MDM을 사용하여 디바이스에 적용할 수 있습니다.

현재 Intune은 [Active Directory 인증서 서비스를 사용하여 SCEP 요청](certificates-scep-configure.md)을 지원합니다.

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 설정/해제 <!-- 2455253 -->
이제 키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 구성할 수 있습니다. **디바이스 구성** > **키오스크(미리 보기)**  > **키오스크 웹 브라우저**에서 컨트롤을 볼 수 있습니다. 설정된 경우 사용자가 단추를 클릭하면 앱은 세션을 종료할지 확인하는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터를 지우고 기본 URL로 다시 이동합니다.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 셀룰러 구성 프로필 만들기 <!-- 2564077 -->
**디바이스 구성**에서 eSIM 셀룰러 프로필을 만들 수 있습니다. 모바일 운영자가 제공하는 셀룰러 활성화 코드를 포함하는 파일을 가져올 수 있습니다. 그런 다음, 이러한 프로필을 Surface Pro LTE 및 eSIM 지원 디바이스와 같은 eSIM LTE가 활성화된 Windows 10 디바이스에 배포할 수 있습니다.

[디바이스에서 eSIM 프로필을 지원](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)하는지 확인합니다.

Windows 10 이상에 적용됩니다. 

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>회사 또는 학교 액세스 설정을 사용하여 디바이스 범주 선택 <!-- 1058963 eenotready --> 
[디바이스 그룹 매핑](https://docs.microsoft.com/intune/device-group-mapping)을 사용하도록 설정한 경우, Windows 10의 사용자에게 **설정** > **계정** > **회사 또는 학교 액세스**의 **연결** 단추를 통해 등록한 후 디바이스 범주를 선택하라는 메시지가 표시됩니다. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>sAMAccountName을 이메일 프로필에 대한 계정 사용자 이름으로 사용 <!-- 1500307 -->
온-프레미스 **sAMAccountName**을 Android, iOS 및 Windows 10용 이메일 프로필에 대한 계정 사용자 이름으로 사용할 수 있습니다. Azure AD(Azure Active Directory)의 `domain` 또는 `ntdomain` 특성에서 도메인을 가져올 수도 있습니다. 또는 사용자 지정 정적 도메인을 입력합니다.

이 기능을 사용하려면 온-프레미스 Active Directory 환경의 `sAMAccountName` 특성을 Azure AD에 동기화해야 합니다.

[Android](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 이상](email-settings-windows-10.md)에 적용

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>충돌에서 디바이스 구성 프로필 참조 <!-- 1556983 -->
**디바이스 구성**에 기존 프로필의 목록이 표시됩니다. 이 업데이트를 사용하면 충돌하는 프로필에 대한 세부 정보를 제공하는 새 열이 추가됩니다. 충돌하는 행을 선택하여 충돌이 있는 설정 및 프로필을 볼 수 있습니다. 

[구성 프로필 관리](device-profile-monitor.md#view-conflicts)에 대한 자세한 정보입니다.

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>디바이스 규정 준수의 새로운 디바이스 상태 <!-- 2308882 -->
**디바이스 준수** > **정책** &gt; 정책 선택 &gt; **개요**에서 다음과 같은 새 상태가 추가됩니다.
- 성공
- 오류
- 충돌
- 보류 중
- 해당 없음. 다른 플랫폼의 디바이스 수를 보여 주는 이미지도 표시됩니다. 예를 들어 iOS 프로필을 보고 있는 경우 이 프로필에도 할당된 비iOS 디바이스의 수가 새 타일에 표시됩니다. [디바이스 준수 정책](compliance-policy-monitor.md#view-status-of-device-policies)을 참조합니다.

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>디바이스 규정 준수에서 타사 바이러스 백신 솔루션 지원 <!-- 2325484 -->
디바이스 준수 정책(**디바이스 준수** > **정책** > **정책 만들기** > **플랫폼: Windows 10 이상** > **설정** > **시스템 보안**)을 만들면 다음과 같은 새 **[디바이스 보안](compliance-policy-create-windows.md)** 옵션이 제공됩니다. 
- **바이러스 백신**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 바이러스 백신 솔루션을 사용하여 준수를 확인할 수 있습니다. 
- **스파이웨어 방지**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 스파이웨어 방지 솔루션을 사용하여 준수를 확인할 수 있습니다. 

적용 대상: Windows 10 이상 

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>삼성 Knox 모바일 등록을 사용하여 등록된 Android 디바이스를 자동으로 "회사"로 표시합니다. <!-- 2404851 -->
기본적으로 삼성 Knox 모바일 등록을 사용하여 등록된 Android 디바이스는 이제 **디바이스 소유권** 아래에 **회사**로 표시됩니다. Knox 모바일 등록을 사용하여 등록하기 전에 IMEI 또는 일련 번호를 사용하여 회사 디바이스를 수동으로 식별할 필요가 없습니다.

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>등록 프로그램 토큰 목록에 프로필이 없는 디바이스 열 <!-- 1853904 -->
프로필이 할당되지 않는 디바이스 수를 보여주는 새 열이 등록 프로그램 토큰 목록에 제공됩니다. 이렇게 하면 관리자는 프로필을 사용자에게 전달하기 전에 이러한 디바이스에 할당할 수 있습니다. 새 열을 보려면 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**으로 이동합니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>디바이스 블레이드의 대량 삭제 디바이스 <!-- 1793693 -->
이제 디바이스 블레이드에서 한 번에 여러 디바이스를 삭제할 수 있습니다. **디바이스** > **모든 디바이스** &gt; 삭제할 디바이스 &gt; **삭제**를 선택합니다. 삭제할 수 없는 디바이스의 경우 경고가 표시됩니다.

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 및 Play for Work에 대한 Google 이름 변경 <!--842873 -->
Intune은 Google 브랜딩 변경 내용을 반영하도록 "Android for Work" 용어를 업데이트했습니다. "Android for Work" 및 "Play for Work" 용어는 더 이상 사용되지 않습니다. 컨텍스트에 따라 서로 다른 용어가 사용됩니다.
- "Android 엔터프라이즈"는 전반적인 최신 Android 관리 스택을 나타냅니다.
- "회사 프로필" 또는 "프로필 소유자"는 회사 프로필을 통해 관리되는 BYOD 디바이스를 가리킵니다.
- "관리되는 Google Play"는 Google 앱 스토어를 나타냅니다.

#### <a name="rules-for-removing-devices----1609459---"></a>디바이스 제거에 대한 규칙 <!-- 1609459 -->
설정한 일 수 동안 체크 인하지 않은 디바이스를 자동으로 제거할 수 있는 새 규칙이 제공됩니다. 새 규칙을 보려면 **Intune** 창으로 이동하여 **디바이스**를 선택하고 **디바이스 정리 규칙**을 선택합니다.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Android 디바이스에 대한 회사 소유의 일회용 지원 <!-- 1630973 -->

Intune은 이제 고도로 관리되고 잠겨 있는 키오스크 스타일의 Android 디바이스를 지원합니다. 관리자는 이를 통해 디바이스 사용을 하나의 앱 또는 작은 앱 집합에 추가로 잠그고 사용자가 다른 앱을 사용하거나 디바이스에서 다른 작업을 수행하지 못하도록 차단할 수 있습니다. Android 키오스크를 설정하려면 Intune &gt; **디바이스 등록** > **Android 등록** > **키오스크 및 작업 디바이스 등록**으로 이동합니다. 자세한 내용은 [Android 엔터프라이즈 키오스크 디바이스 등록 설정](android-kiosk-enroll.md)을 참조합니다.

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>중복된 회사 디바이스 식별자의 행 단위 검토 업로드 <!-- 2203794-->
회사 ID를 업로드할 때 Intune에서 모든 중복된 항목의 목록을 제공하고, 기존 정보를 대체하거나 유지할 수 있는 옵션을 제공합니다. **디바이스 등록** > **회사 디바이스 식별자** > **식별자 추가**를 차례로 선택한 후에 중복된 항목이 있으면 보고서가 표시됩니다. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>수동으로 회사 디바이스 식별자 추가 <!-- 2203803 -->
수동으로 회사 디바이스 ID를 추가할 수 있습니다. **디바이스 등록** > **회사 디바이스 식별자** > **추가**를 차례로 선택합니다. 


<!-- ########################## -->
## <a name="june-2018"></a>2018년 6월

### <a name="app-management"></a>앱 관리

#### <a name="microsoft-edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Intune 앱 보호 정책용 Microsoft Edge 모바일 지원 <!-- 1817882 -->
모바일 디바이스용 Microsoft Edge 브라우저는 이제 Intune에 정의된 앱 보호 정책을 지원합니다.

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>키오스크 모드에서 비즈니스용 Microsoft 스토어 앱에 대한 연결된 앱 사용자 모델 ID(AUMID) 검색 <!-- 1560077 ! -->
Intune에서는 이제 WSfB(비즈니스용 Microsoft 스토어) 앱에 대한 AUMID(앱 사용자 모델 ID)를 검색하여 향상된 키오스크 프로필 구성을 제공할 수 있습니다.

비즈니스용 Microsoft 스토어에서 앱에 대한 자세한 내용은 [비즈니스용 Microsoft 스토어에서 앱 관리](windows-store-for-business.md)를 참조하세요.

#### <a name="new-company-portal-branding-page----1916370---"></a>새 회사 포털 브랜딩 페이지 <!-- 1916370 -->
회사 포털 브랜딩 페이지에는 새로운 레이아웃, 메시지 및 도구 설명이 있습니다.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 새 Mobile Threat Defense 파트너 <!-- 1169249 -->
Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Pradeo에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 디바이스의 액세스를 제어할 수 있습니다.

#### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>NDES 인증서 커넥터에서 FIPS 모드 사용 <!-- 1333688 -->
FIPS(Federal Information Processing Standard) 모드를 사용하는 컴퓨터에 NDES 인증서 커넥터를 설치하면 인증서 발급 및 해지가 예상대로 작동하지 않았습니다. 이 업데이트에는 NDES 인증서 커넥터와 관련된 FIPS 지원이 포함되어 있습니다. 

이 업데이트에는 다음도 포함됩니다.

- NDES 인증서 커넥터에는 Windows Server 2016 및 Windows Server 2012 R2에 자동으로 포함되는 .NET 4.5 Framework가 필요합니다. 이전에는 .NET 3.5 Framework가 최소 필수 버전이었습니다.
- TLS 1.2 지원은 NDES 인증서 커넥터에 포함되어 있습니다. 따라서 NDES 인증서 커넥터가 설치된 서버가 TLS 1.2를 지원하는 경우 TLS 1.2가 사용됩니다. 서버가 TLS 1.2를 지원하지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 디바이스와 서버 간 인증에 사용됩니다.

자세한 내용은 [SCEP 인증서 구성 및 사용](certificates-scep-configure.md), [PKCS 인증서 구성 및 사용](certficates-pfx-configure.md)을 참조하세요.

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680----"></a>Palo Alto Networks GlobalProtect VPN 프로필 지원 <!-- 1333680 ! -->
이 업데이트에서는 Palo Alto Networks GlobalProtect를 Intune의 VPN 프로필에 대한 VPN 연결 형식으로 선택할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **프로필 형식** > **VPN**). 이 릴리스에서 지원되는 플랫폼은 다음과 같습니다. 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>로컬 디바이스 보안 옵션 설정에 대한 추가 <!-- 1403702 -->
Windows 10 디바이스에 대한 추가 로컬 디바이스 보안 옵션 설정을 구성할 수 있습니다. 추가 설정은 Microsoft 네트워크 클라이언트, Microsoft 네트워크 서버, 네트워크 액세스/보안 및 대화형 로그온 영역에서 사용할 수 있습니다. Windows 10 디바이스 구성 정책을 만들 때 Endpoint Protection 범주에서 이러한 설정을 찾아보세요.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 디바이스에서 키오스크 모드 사용 <!-- 1560072 ! -->
Windows 10 디바이스에서 구성 프로필을 만들고 키오스크 모드를 사용하도록 설정할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10** > **디바이스 제한 사항** > **키오스크**). 이 업데이트에서 **키오스크(미리 보기)** 설정은 **키오스크(사용되지 않음)** 로 이름이 바뀝니다. **키오스크(사용되지 않음)** 는 더 이상 사용하지 않는 것이 좋지만 7월 업데이트까지 계속 작동합니다. **키오스크(사용되지 않음)** 는 새로운 **키오스크** 프로필 유형(**프로필 만들기** > **Windows 10** > **키오스크(미리 보기)** )으로 바뀌고 이 프로필 유형에는 Windows 10 RS4 이상에서 키오스크를 구성하는 설정이 포함됩니다.

Windows 10 이상에 적용됩니다.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>디바이스 프로필 그래픽 사용자 차트가 다시 시작됨 <!-- 2160133 -->
디바이스 프로필 그래픽 차트(**디바이스 구성** > **프로필** &gt; 기존 프로필 선택 &gt; **개요**)에 표시되는 개수를 개선하기 위해 그래픽 사용자 차트가 일시적으로 제거되었습니다.

이 업데이트를 사용하면 그래픽 사용자 차트가 Azure Portal에 다시 표시됩니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118---"></a>사용자 인증이 없는 Windows Autopilot 등록 지원 <!-- 1165118 -->
Intune에서는 이제 사용자 인증 없이 Windows Autopilot 등록을 지원합니다. 여기에는 Windows Autopilot 배포 프로필인 "Autopilot 배포 모드"가 "자체 배포"로 설정된 새 옵션이 있습니다.  이 디바이스는 Windows 10 Insider Preview Build 17672 이상을 실행 중이고 TPM 2.0 칩을 가지고 있어야 이 등록 유형을 성공적으로 완료할 수 있습니다. 사용자 인증이 필요하지 않으므로 물리적으로 제어할 수 있는 디바이스에만 이 옵션을 할당해야 합니다.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Autopilot에 대한 OOBE를 구성할 경우, 새 언어 지역 설정 <!-- 1821766 -->
새 구성 설정은 독창적인 환경(Out of Box Experience)에서 Autopilot 프로필에 대한 언어와 지역을 설정하는 데 사용할 수 있습니다. 새 설정을 확인하려면 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기** > **배포 모드** = **자체 배포** > **기본값 구성됨**을 차례로 선택합니다.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>디바이스 키보드 구성을 위한 새 설정 <!-- 1821768 -->
새 설정을 통해 첫 실행 경험 중에 Autopilot 프로필에 대한 키보드를 구성할 수 있습니다. 새 설정을 확인하려면 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기** > **배포 모드** = **자체 배포** > **기본값 구성됨**을 차례로 선택합니다.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot 프로필을 대상 지정 그룹으로 이동 <!-- 1877935 -->
AutoPilot 배포 프로필을 AutoPilot 디바이스를 포함하는 Azure AD 그룹에 할당할 수 있습니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="set-compliance-by-device-location----851881----"></a>디바이스 위치별 규정 준수 설정 <!-- 851881 ! -->
상황에 따라 회사 리소스에 대한 액세스를 네트워크 연결로 정의된 특정 위치로 제한할 수 있습니다. 이제 디바이스의 IP 주소를 기반으로 하여 준수 정책을 만들 수 있습니다(**디바이스 준수** > **위치**). IP 범위를 벗어난 디바이스는 회사 리소스에 액세스할 수 없습니다.

적용 대상: 회사 포털 앱이 업데이트된 Android 디바이스 6.0 이상

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot 디바이스에서 소비자 앱 및 경험 방지<!-- 1621980 -->
Windows 10 Enterprise RS4 AutoPilot 디바이스에서 소비자 앱 및 환경을 설치하지 못하도록 방지할 수 있습니다. 이 기능을 확인하려면 **Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼** = **Windows 10 이상** > **프로필 유형** = **디바이스 제한** > **구성** > **Windows 추천** > **소비자 기능**으로 차례로 이동합니다. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948---"></a>Windows 10 소프트웨어 업데이트에서 최신 버전 제거 <!-- 1732948 -->
Windows 10 컴퓨터에서 주요 문제가 발견되면 최신 기능 업데이트 또는 최신 품질 업데이트를 제거(롤백)하도록 선택할 수 있습니다. 기능 또는 품질 업데이트의 제거는 디바이스가 켜져 있는 서비스 채널에서만 사용할 수 있습니다. 제거하면 Windows 10 컴퓨터에서 이전 업데이트를 복원하는 정책이 트리거됩니다. 특히 기능 업데이트의 경우 최신 버전 제거를 적용할 수 있는 시간을 2-60일로 제한할 수 있습니다. 소프트웨어 업데이트 제거 옵션을 설정하려면 Azure Portal의 **Microsoft Intune** 블레이드에서 **소프트웨어 업데이트**를 선택합니다. 그런 다음, **소프트웨어 업데이트** 블레이드에서 **Windows 10 업데이트 링**을 선택합니다. 그런 다음, **개요** 섹션에서 **제거** 옵션을 선택할 수 있습니다.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>모든 디바이스에서 IMEI 및 일련 번호 검색 <!-- 1793685 -->
이제 모든 디바이스 블레이드에서 IMEI 및 일련 번호를 검색할 수 있습니다(이메일, UPN, 디바이스 이름 및 관리 이름을 계속 사용할 수 있음). Intune에서 **디바이스** > **모든 디바이스**를 차례로 선택한 다음, 검색 상자에서 검색 항목을 입력합니다.

#### <a name="management-name-field-will-be-editable----1875989---"></a>관리 이름 필드 편집 가능 <!-- 1875989 -->
이제 디바이스의 **속성** 블레이드에서 관리 이름 필드를 편집할 수 있습니다. 이 필드를 편집하려면 **디바이스** > **모든 디바이스**를 선택하고, 디바이스를 선택한 다음, **속성**을 선택합니다. 관리 이름 필드를 사용하여 디바이스를 고유하게 식별할 수 있습니다.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>새로운 모든 디바이스 필터: 디바이스 범주 <!-- 1878520 -->
이제 디바이스 범주별로 **모든 디바이스** 목록을 필터링할 수 있습니다. 이렇게 하려면 **디바이스** > **모든 디바이스** > **필터** > **디바이스 범주**를 차례로 선택합니다.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer를 사용하여 iOS 및 MacOS 디바이스의 화면 공유 <!-- 1985547 -->
관리자는 이제 [TeamViewer](device-profile-android-teamviewer.md)에 연결하고 iOS 및 macOS 디바이스에서 화면 공유 세션을 시작할 수 있습니다. iPhone, iPad 및 macOS 사용자는 자신의 화면을 다른 데스크톱 또는 모바일 디바이스와 실시간으로 공유할 수 있습니다. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>여러 Exchange Connector 지원 <!-- 2070451 -->
더 이상 테넌트당 하나의 Microsoft Intune Exchange Connector로 제한되지 않습니다. Intune에서는 이제 여러 온-프레미스 Exchange 조직에서 Intune 조건부 액세스를 설정할 수 있도록 여러 Exchange Connector를 지원합니다.

Intune 온-프레미스 Exchange Connector를 사용하여 디바이스가 Intune에 등록했는지 여부 및 Intune 디바이스 준수 정책을 준수하는지 여부에 따라 온-프레미스 Exchange 사서함에 대한 디바이스 액세스를 관리할 수 있습니다. 커넥터를 설정하려면 Azure Portal에서 Intune 온-프레미스 Exchange Connector를 다운로드해 이를 Exchange 조직의 서버에 설치합니다. Microsoft Intune 대시보드에서 **온-프레미스 액세스**를 선택한 다음, **설치** 아래에서 **Exchange ActiveSync Connector**를 선택합니다. Exchange 온-프레미스 Connector를 다운로드하고 Exchange 조직의 서버에 설치합니다. 더 이상 테넌트당 하나의 Exchange Connector로 제한되지 않으므로 추가 Exchange 조직이 있는 경우 동일한 다운로드 절차를 따라 각 추가 Exchange 조직에 대해 커넥터를 설치할 수 있습니다.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>새로운 디바이스 하드웨어 세부 정보: CCID <!-- 2156657 -->
이제 각 디바이스에 대한 CCID(칩 카드 인터페이스 디바이스) 정보가 포함됩니다. 이를 확인하려면 **디바이스** > **모든 디바이스**를 차례로 선택하고, 디바이스를 선택하고, **하드웨어**를 선택한 다음, **네트워크 정보**> 아래에서 확인합니다.

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>모든 사용자 및 모든 디바이스를 범위 그룹으로 할당 <!-- 2196803 -->
이제 범위 그룹에서 모든 사용자, 모든 디바이스 및 모든 사용자/디바이스를 할당할 수 있습니다. 이렇게 하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당**을 차례로 선택하고, 할당을 선택한 다음, **범위(그룹)** 를 선택합니다.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806---"></a>iOS 및 macOS 디바이스에 대한 UDID 정보 포함 <!-- 2219806 -->
iOS 및 macOS 디바이스에 대한 UDID(고유 디바이스 식별자)를 확인하려면 **디바이스** > **모든 디바이스**로 차례로 이동하고, 디바이스를 선택한 다음, **하드웨어**를 선택합니다. UDID는 **디바이스** > **모든 디바이스** &gt; 디바이스 선택 &gt; **속성** > **디바이스 소유권** 아래에 설정한 회사 디바이스에만 사용할 수 있습니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>앱 설치에 대한 향상된 문제 해결 <!-- 928990 -->
Microsoft Intune MDM 관리 디바이스에서 앱 설치에 실패하는 경우도 있습니다. 이러한 앱 설치에 실패할 경우, 실패 이유를 파악하거나 문제를 해결하기 어려울 수 있습니다. Microsoft에서는 앱 문제 해결 기능의 공개 미리 보기를 제공합니다. 개별 디바이스 아래에서 **관리 앱**이라는 새 노드를 확인할 수 있습니다. 여기에는 Intune MDM을 통해 전달된 앱이 나열됩니다. 노드 내부에는 앱 설치 상태 목록이 표시됩니다. 개별 앱을 선택하면 해당 앱에 대한 문제 해결 보기가 표시됩니다. 문제 해결 보기에는 응용 프로그램이 언제 생성, 수정, 대상 지정 및 디바이스에 전달되었는지를 포함한 앱의 전체 수명 주기기 표시됩니다. 또한 앱 설치에 실패할 경우, 오류 코드 및 오류의 원인에 대한 유용한 메시지가 표시됩니다. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune 앱 보호 정책 및 Microsoft Edge <!-- 1818968 -->
모바일 디바이스(iOS 및 Android)용 Microsoft Edge 브라우저에서는 이제 Microsoft Intune 앱 보호 정책을 지원합니다. Microsoft Edge 애플리케이션에서 회사 Azure AD 계정으로 로그인하는 iOS 및 Android 디바이스 사용자는 Intune에서 보호됩니다. iOS 디바이스에서 **웹 콘텐츠에 대한 관리되는 요구** 정책을 사용하면 관리될 때 사용자가 Microsoft Edge에서 링크를 열 수 있습니다.

<!-- ########################## -->
## <a name="may-2018"></a>2018년 5월

### <a name="app-management"></a>앱 관리

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>앱 보호 정책 구성 <!-- 2144597 Part 2 -->

Azure Portal에서 Intune 앱 보호 서비스 블레이드로 이동하는 대신 이제 Intune으로 직접 이동하면 됩니다. 이제 Intune 내에서는 앱 보호 정책에 대한 위치가 하나입니다. 모든 앱 보호 정책은 이미 앱 구성에서 Intune의 **모바일 앱** 블레이드에서 **앱 보호 정책** 아래에 있습니다. 이 통합은 클라우드 관리를 단순화하는 데 도움이 됩니다. Intune에서 모든 앱 보호 정책이 이미 설정되어 있으므로 이전에 구성한 정책을 수정할 수 있습니다. Intune APP(앱 보호 정책) 및 CA(조건부 액세스) 정책은 이제 **조건부 액세스**에 있으며 **Microsoft Intune** 블레이드의 **관리** 섹션이나 **Azure Active Directory** 블레이드의 **보안** 섹션에서 찾을 수 있습니다. 조건부 액세스 정책을 수정하는 방법에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>정책, 앱, 인증서 및 네트워크 프로필 설치 요구 <!-- 1553555 -->
관리자는 AutoPilot 디바이스를 프로비저닝하는 동안 Intune에서 정책, 앱, 인증서 및 네트워크 프로필을 설치할 때까지 최종 사용자가 Windows 10 RS4 데스크톱에 액세스하지 못하도록 차단할 수 있습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>삼성 Knox 모바일 등록 지원 <!--1112863-->
삼성 KME(Knox 모바일 등록)와 함께 Intune을 사용하는 경우, 많은 회사 소유 Android 디바이스를 등록할 수 있습니다. WiFi 또는 셀룰러 네트워크의 사용자는 디바이스를 처음 켤 때 몇 번만 탭하면 등록할 수 있습니다. Knox 배포 앱을 사용하는 경우 Bluetooth 또는 NFC를 사용하여 디바이스를 등록할 수 있습니다. 자세한 내용은 [삼성 Knox 모바일 등록을 사용하여 Android 디바이스 자동 등록](android-samsung-knox-mobile-enroll.md)을 참조하세요.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결 

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Windows 10용 회사 포털에서 도움말 요청 <!-- 1874137 -->
이제 Windows 10용 회사 포털은 사용자가 문제에 대한 도움을 받기 위해 워크플로를 시작할 때 Microsoft에 직접 앱 로그를 전송합니다. 이렇게 하면 Microsoft에 제기된 문제를 더 쉽게 해결할 수 있습니다.

<!-- ########################## -->
## <a name="april-2018"></a>2018년 4월

### <a name="app-management"></a>앱 관리

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android에서 MAM PIN에 대한 암호 지원<!-- 1438086 -->

Intune 관리자는 숫자 MAM PIN 대신 암호를 적용하는 애플리케이션 시작 요구 사항을 설정할 수 있습니다. 항목이 구성되면 사용자는 MAM 지원 애플리케이션에 대한 액세스 권한을 가져오기 전에 메시지가 표시될 때 암호를 설정하고 사용해야 합니다. 암호는 하나 이상의 특수 문자 또는 대/소문자 알파벳을 포함한 숫자 PIN으로 정의됩니다. Intune은 기존 숫자 PIN과 유사한 방식으로 암호를 지원합니다. 즉, 최소 길이를 설정하며 관리자 콘솔을 통해 반복 문자 및 시퀀스를 허용합니다. 이 기능을 사용하려면 Android에서 회사 포털의 최신 버전이 필요합니다. 현재 iOS에서는 이 기능을 사용할 수 있습니다.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS에 대한 LOB(기간 업무) 앱 지원 <!-- 1473977 -->
Microsoft Intune은 Azure Portal에서 macOS LOB 앱을 설치하는 기능을 제공할 예정입니다. GitHub에서 사용할 수 있는 도구에서 미리 처리된 macOS LOB 앱을 Intune에 추가할 수 있습니다. Azure Portal에서 **Intune** 블레이드의 **클라이언트 앱**을 선택합니다. **클라이언트 앱** 블레이드에서 **앱** > **추가**를 선택합니다. **앱 추가** 블레이드에서 **LOB(기간 업무) 앱**을 선택합니다. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-enterprise-work-profile-app-assignment----1813073---"></a>Android Enterprise 작업 프로필 앱 할당을 위해 기본 제공된 모든 사용자 및 모든 디바이스 그룹 <!-- 1813073 -->
Android Enterprise 작업 프로필 앱 할당을 위해 기본 제공된 **모든 사용자** 및 **모든 디바이스** 그룹을 활용할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>사용자가 제거한 필수 앱을 Intune에서 다시 설치함 <!-- 1947010 -->
최종 사용자가 필수 앱을 제거할 경우 Intune에서 7일 재평가 주기를 기다리지 않고 24시간 이내에 앱을 자동으로 다시 설치합니다.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>앱 보호 정책을 구성하는 위치 업데이트 <!-- 2144597 -->

Azure Portal의 Microsoft Intune 서비스에서는 **Intune 앱 보호** 서비스 블레이드에서 **모바일 앱** 블레이드로 일시적으로 리디렉션됩니다. 모든 앱 보호 정책이 Intune의 앱 구성에 있는 **모바일 앱** 블레이드에 이미 있습니다. Intune 앱 보호로 이동하는 대신 Intune으로 이동하세요. 2018년 4월에는 리디렉션을 중지하고 **Intune 앱 보호** 서비스 블레이드를 완전히 제거하여 Intune 내 앱 보호 정책의 위치가 하나만 있도록 합니다. 

**이 변경 사항은 어떤 영향을 미치나요?**
이 변경 사항은 Intune 독립형 고객과 하이브리드(Configuration Manager와 Intune) 고객 모두에 영향을 줍니다. 이 통합은 클라우드 관리 관리를 단순화하는 데 도움이 됩니다.

**이러한 변경에 대비하려면 어떻게 해야 하나요?**
**Intune 앱 보호** 서비스 블레이드 대신 **Intune**을 즐겨찾기로 태그를 지정하고 Intune 내 **모바일** 앱 블레이드의 앱 보호 정책 워크플로에 익숙해지도록 합니다. 짧은 시간 동안 리디렉션된 다음, **앱 보호** 블레이드가 제거됩니다. Intune에서 모든 앱 보호 정책이 이미 설정되어 있으므로 조건부 액세스 정책을 수정할 수 있습니다. 조건부 액세스 정책을 수정하는 방법에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요. 

### <a name="device-configuration"></a>디바이스 구성

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153---"></a>디바이스 프로필 차트 및 상태 목록에서 그룹의 모든 디바이스 표시 <!-- 1449153 -->
디바이스 프로필을 구성할 때(**디바이스 구성** > **프로필**), iOS와 같은 디바이스 프로필을 선택합니다. iOS 디바이스 및 비 iOS 디바이스를 포함하는 그룹에 이 프로필을 할당합니다. 그래픽 차트 수는 프로필이 iOS *및* 비 iOS 디바이스에 적용되었음을 나타냅니다(**디바이스 구성** > **프로필** &gt; 기존 프로필 선택 &gt; **개요**). **개요** 탭에서 그래픽 차트를 선택하면 **디바이스 상태**에 iOS 디바이스 대신 그룹의 모든 디바이스가 나열됩니다. 

이 업데이트를 사용하면 그래픽 차트(**디바이스 구성** > **프로필** &gt; 기존 프로필 선택 &gt; **개요**)에는 특정 디바이스 프로필에 대한 개수만 표시됩니다. 예를 들어 구성 디바이스 프로필이 iOS 디바이스에 적용되는 경우 차트는 iOS 디바이스의 개수만 나열됩니다. 그래픽 차트를 선택하고 **디바이스 상태**를 열면 iOS 디바이스만 나열됩니다.

이 업데이트를 수행하는 동안 그래픽 사용자 차트는 일시적으로 제거됩니다. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Windows 10용 Always On VPN <!--1333666 -->

현재 [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)은 OMA-URI를 통해 만든 사용자 지정 VPN(가상 프라이빗 네트워크) 프로필을 사용하여 Windows 10 디바이스에서 사용할 수 있습니다.

이 업데이트를 사용하면 관리자는 Azure Portal의 Intune에서 직접 Always On for Windows 10 VPN 프로필을 사용하도록 설정할 수 있습니다. Always On VPN 프로필은 다음과 같은 경우 자동으로 연결됩니다.

- 자신의 디바이스에 사용자가 로그인하는 경우
- 디바이스의 네트워크가 변경되는 경우
- 디바이스의 화면이 꺼졌다가 다시 켜지는 경우

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>교육 프로필에 대한 새 프린터 설정 <!-- 1308900 -->

교육 프로필의 경우 **프린터** 범주의 **프린터**, **기본 프린터**, **새 프린터 추가**에서 새 설정을 사용할 수 있습니다.

#### <a name="show-caller-id-in-personal-profile---android-enterprise-work-profile---1098984---"></a>개인 프로필에 호출자 ID 표시 - Android Enterprise 작업 프로필 <!--1098984 -->
디바이스에서 개인 프로필을 사용하는 경우 회사 연락처의 발신자 ID 정보가 최종 사용자에게 표시되지 않을 수 있습니다. 

이 업데이트에서는 **Android Enterprise** > **디바이스 제한** > **작업 프로필 설정**에서 새 설정이 지정됩니다.
- 개인 프로필에 회사 연락처의 발신자 ID 표시

사용하도록 설정하면(구성하지 않음) 회사 연락처의 발신자 정보가 개인 프로필에 표시됩니다. 차단하면 회사 연락처의 발신자 번호가 개인 프로필에 표시되지 않습니다. 

적용 대상: Android OS v6.0 이상의 Android 회사 프로필 디바이스

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>엔드포인트 보호 설정에 추가된 새 Windows Defender Credential Guard 설정 <!--1102252 --><!--from 1802 and 1804-->

이 업데이트를 사용하면 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)(**디바이스 구성** > **프로필** > **Endpoint Protection**)에 다음 설정이 포함됩니다. 

- **Windows Defender Credential Guard**: 가상화 기반 보안이 포함된 Credential Guard를 켭니다. 이 기능을 사용하도록 설정하면, **Platform Security Level with Secure Boot**(보안 부팅이 사용된 플랫폼 보안 수준) 및 **가상화 기반 보안**을 둘 다 사용하도록 설정할 경우, 다음 다시 부팅 시 자격 증명을 보호하는 데 도움이 됩니다. 다음 옵션을 사용할 수 있습니다.
  - **사용 안 함**: 이전에 **잠금 없이 설정** 옵션을 사용하여 Credential Guard를 켠 경우 원격으로 Credential Guard를 끕니다.

  - **UEFI 잠금을 사용하여 설정**: 레지스트리 키 또는 그룹 정책을 사용하여 Credential Guard를 사용하지 않도록 설정할 수 없게 합니다. 이 설정을 사용한 후 Credential Guard를 사용하지 않도록 설정하려면 그룹 정책을 “사용 안 함”으로 설정해야 합니다. 그런 다음, 물리적으로 존재하는 사용자가 있는 각 컴퓨터에서 보안 기능을 제거합니다. 이러한 단계는 UEFI에서 지속되는 구성을 지웁니다. UEFI 구성이 지속되는 한, Credential Guard는 사용하도록 설정됩니다.

  - **잠금 없이 설정**: 그룹 정책을 사용하여 원격으로 Credential Guard를 사용하지 않도록 설정할 수 있게 합니다. 이 설정을 사용하는 디바이스는 Windows 10(버전 1511) 이상에서 실행되어야 합니다.

다음 종속 기술은 Credential Guard를 구성할 때 자동으로 사용하도록 설정됩니다. 

  - **VBS(가상화 기반 보안) 사용**: 다음 다시 부팅 시 VBS(가상화 기반 보안)를 켭니다. 가상화 기반 보안에서는 Windows 하이퍼바이저를 사용하여 보안 서비스에 대한 지원을 제공하며, 보안 부팅이 필요합니다.
  - **보안 부팅 및 DMA(직접 메모리 액세스)** : 보안 부팅 및 직접 메모리 액세스를 통해 VBS를 켭니다. DMA 보호는 하드웨어 지원이 필요하며 제대로 구성된 디바이스에서만 사용하도록 설정됩니다. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 인증서에서 사용자 지정 주체 이름 사용 <!-- 2064190 -->
SCEP 인증서 프로필에서 사용자 지정 주체에 **OnPremisesSamAccountName** 일반 이름을 사용할 수 있습니다. 예를 들어 `CN={OnPremisesSamAccountName})`를 사용할 수 있습니다.

####  <a name="block-camera-and-screen-captures-on-android-enterprise-work-profiles----1098977---"></a>Android Enterprise 작업 프로필에서 카메라 및 화면 캡처 차단 <!-- 1098977 -->
두 개의 새로운 속성은 Android 디바이스에 대한 디바이스 제한을 구성할 때 차단하는 데 사용할 수 있습니다. 
- 카메라: 디바이스에서 모든 카메라에 대한 액세스 차단
- 화면 캡처: 화면 캡처를 차단하고, 안전하지 않은 비디오 출력의 디스플레이 디바이스에 콘텐츠가 표시되지 않도록 방지

Android Enterprise 작업 프로필에 적용됩니다.

#### <a name="use-cisco-anyconnect-client-for-ios----1333708---"></a>iOS용 Cisco AnyConnect 클라이언트 사용 <!-- 1333708 -->

iOS용 새 VPN 프로필을 만들 때 이제 **Cisco AnyConnect** 및 **Cisco Legacy AnyConnect**의 두 가지 옵션이 있습니다. Cisco AnyConnect 프로필은 4.0.7x 이상 버전을 지원합니다. 기존 iOS Cisco AnyConnect VPN 프로필은 **Cisco Legacy AnyConnect**로 레이블이 지정되며, 현재와 마찬가지로 Cisco AnyConnect 4.0.5x 및 이전 버전에서 계속 작동합니다.

> [!NOTE]
> 이 변경 내용은 iOS에만 적용됩니다. Android, Android Enterprise 작업 프로필 및 macOS 플랫폼에는 계속해서 Cisco AnyConnect 옵션을 하나만 사용할 수 있습니다.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2+를 사용하는 디바이스에서 사용자를 위한 새로운 등록 단계 <!--1734567 -->
macOS high Sierra 10.13.2에 “사용자 승인” MDM 등록의 개념이 도입되었습니다. 승인된 등록을 사용하면 Intune에서 몇 가지 보안에 민감한 설정을 관리할 수 있습니다. 자세한 내용은 Apple의 지원 문서를 참조하세요. https://support.apple.com/HT208019

macOS 회사 포털을 사용하여 등록된 디바이스는 최종 사용자가 [시스템 기본 설정]을 열고 수동으로 승인을 제공하지 않는 한 “사용자 승인되지 않음”으로 간주됩니다. 이를 위해 macOS 회사 포털은 이제 macOS 10.13.2 이상의 사용자에게 등록 프로세스 마지막 단계에서 해당 등록을 수동으로 승인하도록 안내합니다. Intune 관리 콘솔은 등록된 디바이스가 사용자 승인되지 않은 경우 보고합니다.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>이제 Jamf에 등록된 macOS 디바이스를 Intune에 등록할 수 있음 <!-- 2370684 -->
macOS 회사 포털 버전 1.3 및 1.4에서는 Jamf 디바이스가 Intune에 등록되지 않았습니다. macOS 포털 버전 1.4.2에서 이 문제가 해결되었습니다.

#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Android용 회사 포털 앱에서 업데이트된 도움말 환경 <!-- 1631531 -->
Android 플랫폼에 대한 모범 사례에 맞추기 위해 Android용 회사 포털 앱에서 도움말 환경을 업데이트했습니다. 이제 사용자 앱에서 문제가 발생하는 경우 **메뉴** > **도움말**을 누르면 됩니다.
- 또한 진단 로그를 Microsoft에 업로드합니다.
- 회사 지원 담당자에게 문제 및 인시던트 ID를 설명하는 이메일을 보냅니다.  

업데이트된 도움말 환경을 확인하려면 [이메일을 사용하여 로그 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android) 및 [Microsoft에 오류 보내기](/intune-user-help/send-logs-to-microsoft-android)로 이동합니다.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>새 등록 실패 추세 차트 및 실패 이유 테이블 <!-- 1471783 -->
등록 개요 페이지에서 등록 실패의 추세와 실패 원인 상위 5개를 확인할 수 있습니다. 차트 또는 테이블을 클릭하면 세부 사항을 드릴스루하여 문제 해결 도움말 및 재구성 제안을 찾을 수 있습니다.


### <a name="device-management"></a>디바이스 관리

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----1629303---"></a>ATP(Advanced Threat Protection)와 Intune이 완전히 통합됨 <!-- 1629303 -->

[ATP(Advanced Threat Protection)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)는 Windows 10 디바이스의 위험 수준을 표시합니다. Windows Defender 보안 센터(ATP 포털)에서 Microsoft Intune에 대한 연결을 만들 수 있습니다. 연결이 생성되면 Intune 준수 정책을 사용하여 허용되는 위협 수준이 결정됩니다. 위협 수준을 초과할 경우 AD(Azure Active Directory) 조건부 액세스 정책을 통해 조직 내의 여러 앱에 대한 액세스를 차단할 수 있습니다.

이 기능을 사용하면 ATP가 Windows 10 디바이스에서 파일 검사, 위협 검색, 위험 보고 등을 수행할 수 있습니다.

[Intune에서 조건부 액세스로 ATP 사용](advanced-threat-protection.md)을 참조하세요.

#### <a name="support-for-user-less-devices----1637553---"></a>사용자가 지정되지 않은 디바이스에 대한 지원 <!-- 1637553 -->
Intune은 Microsoft Surface Hub와 같은 사용자가 지정되지 않은 디바이스에서 준수를 평가하는 기능을 지원합니다. 준수 정책은 특정 디바이스를 대상으로 지정할 수 있습니다. 따라서 연결된 사용자가 없는 디바이스에 대해 준수(및 비준수)를 확인할 수 있습니다.

#### <a name="delete-autopilot-devices----1713650---"></a>Autopilot 디바이스 삭제 <!-- 1713650 -->
Intune 관리자는 [Autopilot 디바이스를 삭제](enrollment-autopilot.md#delete-autopilot-devices)할 수 있습니다.

#### <a name="improved-device-deletion-experience---1832333---"></a>향상된 디바이스 삭제 환경 <!--1832333 -->
이제 [Intune에서 디바이스를 삭제](devices-wipe.md#delete-devices-from-the-intune-portal)하기 전에 회사 데이터를 제거하거나 디바이스를 출하 시 설정으로 초기화할 필요가 없습니다.

새 환경을 보려면 Intune에 로그인하고 **디바이스** > **모든 디바이스** &gt; 디바이스 이름 &gt; **삭제**를 선택합니다.

초기화/사용 중지 확인을 수행하려면 **삭제**하기 전에 **회사 데이터 제거** 및 **출하 시 설정으로 리셋**을 실행하여 표준 디바이스 수명 주기를 사용할 수 있습니다. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>분실 모드에 있을 때 iOS에서 소리 재생 <!-- 1947769 -->
감독 중인 iOS 디바이스가 MDM(모바일 디바이스 관리) [분실 모드](device-lost-mode.md)에 있는 경우 [소리를 재생](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)할 수 있습니다(**디바이스** > **모든 디바이스** &gt; iOS 디바이스 선택 &gt; **개요** > **자세히**). 소리는 디바이스가 분실 모드에서 제거되거나 사용자가 디바이스에서 소리를 사용하지 않도록 설정할 때까지 계속 재생됩니다. iOS 디바이스 9.3 이상에서 적용됩니다.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Intune 디바이스에서 수행된 검색에서 웹 결과 차단 또는 허용 <!--1972804-->

이제 관리자는 디바이스에서 수행된 검색에서 웹 결과를 차단할 수 있습니다.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM 푸시 인증서 업로드 실패에 대한 향상된 오류 메시지 <!-- 2172331 -->

오류 메시지는 기존 MDM 인증서를 갱신할 때 동일한 Apple ID를 사용해야 함을 설명합니다.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>가상 머신에서 macOS용 회사 포털 테스트 <!-- 2216679 -->

Microsoft에서는 IT 관리자가 Parallels Desktop 및 VMware Fusion에서 가상 머신의 macOS용 회사 포털 앱을 테스트하는 데 도움이 되는 지침을 게시했습니다. [테스트를 위해 macOS 가상 머신 등록](macos-enroll.md#enroll-virtual-macos-machines-for-testing)에서 자세히 알아보세요.

### <a name="intune-apps"></a>Intune 앱

#### <a name="user-experience-update-for-the-company-portal-app-for-ios---1412866---"></a>iOS용 회사 포털 앱의 사용자 환경 업데이트 <!--1412866 -->
iOS용 회사 포털 앱에 대한 주요 사용자 환경 업데이트가 릴리스되었습니다. 이 업데이트는 현대적인 모양과 느낌을 포함하여 시각적으로 완전히 새롭게 설계했습니다. 앱의 기능은 유지하면서도 유용성과 접근성을 향상시켰습니다.  

또한 다음을 확인할 수 있습니다.
- iPhone X 지원
- 더 빨라진 앱 시작과 응답 로드로 사용자 시간 단축
- 사용자에게 최신 상태 정보를 제공하는 추가 진행률 표시줄
- 문제 발생 시 이를 보고하기 쉽도록 사용자가 로그를 업로드하는 방식 개선 사항  

업데이트된 형태를 보려면 [앱 UI 의 새로운 기능](whats-new-app-ui.md)으로 이동하세요.

#### <a name="protect-on-premises-exchange-data-using-intune-app-and-ca----1056954---"></a>Intune APP 및 CA를 사용하여 온-프레미스 Exchange 데이터 보호 <!-- 1056954 -->
이제 Intune APP(앱 정책 보호) 및 CA(조건부 액세스)를 사용하여 Outlook Mobile에서 온-프레미스 Exchange 데이터에 대한 액세스를 보호할 수 있습니다. Azure Portal 내에서 앱 보호 정책을 추가하거나 수정하려면 **Microsoft Intune** > **클라이언트 앱** > **앱 보호 정책**을 선택합니다. 이 기능을 사용하기 전에 [iOS 및 Android 요구 사항에 대한 Outlook](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)을 충족하는지 확인합니다.


### <a name="user-interface"></a>사용자 인터페이스

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Windows 10 회사 포털의 개선된 디바이스 타일 <!--2213364 -->

저시력 사용자가 더 쉽게 액세스할 수 있고 화면 읽기 도구의 성능이 개선되도록 타일이 업데이트되었습니다.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS용 회사 포털 앱에 진단 보고서 보내기 <!-- 2216677 -->
사용자가 Intune 관련 오류를 보고하는 방법을 개선하기 위해 macOS 디바이스용 회사 포털 앱이 업데이트되었습니다. 회사 포털 앱에서 직원은 다음을 수행할 수 있습니다.

- Microsoft 개발자 팀에 직접 진단 보고서를 업로드합니다.
- 인시던트 ID를 회사의 IT 지원 팀에게 이메일로 전송합니다.

자세한 내용은 [macOS에 대한 오류 보내기](/intune-user-help/send-errors-macos)를 참조하세요.

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010---"></a>Windows 10용 회사 포털 앱에서 Intune이 Fluent Design System에 맞게 조정됨 <!-- 1195010 -->
Windows 10용 Intune 회사 포털 앱이 [Fluent Design System의 탐색 보기](https://docs.microsoft.com/windows/uwp/design/basics/navigation-basics)로 업데이트되었습니다. 앱의 옆쪽에 모든 최상위 페이지의 정적 세로 목록이 표시됩니다. 링크를 클릭하여 빠르게 페이지를 보고 페이지 간에 전환할 수 있습니다. 이 업데이트는 Intune에서 더욱 공감할 수 있고 친숙한 적응형 환경을 만들려는 Microsoft의 지속적인 노력의 일부로 여러 업데이트 중 첫 번째로 선보이는 것입니다. 업데이트된 형태를 보려면 [앱 UI 의 새로운 기능](whats-new-app-ui.md)으로 이동하세요.

<!-- ########################## -->
## <a name="march-2018"></a>2018년 3월

### <a name="app-management"></a>앱 관리

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune에 대해 iOS LOB(기간 업무) 애플리케이션에 만료 경고 <!-- 748789 -->

Azure Portal에서 Intune은 막 만료될 iOS LOB(기간 업무) 애플리케이션에 경고를 보냅니다. 새 버전의 iOS LOB(기간 업무) 애플리케이션을 업로드할 때 Intune은 앱 목록에서 만료 알림을 제거합니다. 새로 업로드된 iOS LOB(기간 업무) 애플리케이션에 대해 이러한 만료 알림이 활성화됩니다. 경고가 iOS LOB(기간 업무) 애플리케이션 프로비전 프로필이 만료되기 30일 전에 표시됩니다. 프로필이 만료되면 경고는 만료됨으로 변경됩니다.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>16진수 코드를 사용하여 회사 포털 테마 사용자 지정 <!--1049561 -->

16진수 코드를 사용하여 회사 포털 앱에서 테마 색을 사용자 지정할 수 있습니다. 16진수 코드를 입력하면 Intune은 텍스트 색과 배경색 간의 대비가 가장 높은 텍스트 색을 결정합니다. **클라이언트 앱** > **회사 포털**에서 텍스트 색과 회사 로고를 미리 볼 수 있습니다.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise에 대한 그룹에 따라 앱 할당 포함 및 제외 <!-- 1813081 -->

Android Enterprise(이전의 Android for Work)는 그룹 포함 및 제외를 지원하지만 미리 만들어진 **모든 사용자** 및 **모든 디바이스** 기본 제공 그룹은 지원하지 않습니다. 자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.


### <a name="device-management"></a>디바이스 관리

### <a name="export-all-devices-into-csv-files-in-ie-microsoft-edge-or-chrome----2258071---"></a>모든 디바이스를 IE, Microsoft Edge 또는 Chrome의 CSV 파일로 내보내기 <!-- 2258071 -->
**디바이스** > **모든 디바이스**에서 디바이스를 CSV로 서식이 지정된 목록으로 **내보낼** 수 있습니다. 10,000개 이상의 디바이스가 있는 IE(Internet Explorer) 사용자는 해당 디바이스를 여러 파일로 성공적으로 내보낼 수 있습니다. 각 파일에는 최대 10,000개의 디바이스가 있습니다.

30,000개 이상의 디바이스가 있는 Microsoft Edge 및 Chrome 사용자는 해당 디바이스를 여러 파일로 성공적으로 내보낼 수 있습니다. 각 파일에는 최대 30,000개의 디바이스가 있습니다.

[디바이스 관리](device-management.md)에서는 관리하는 디바이스에서 수행할 수 있는 작업에 대한 자세한 세부 정보를 제공합니다.

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune 서비스의 새로운 보안 강화 기능  <!-- 1637539 -->   

Intune 독립 실행형 고객이 **규격**(보안 기능 해제)으로 할당된 정책 없이 디바이스를 처리하거나 **비호환**(보안 기능 사용)으로 이러한 정책을 처리하는 데 사용할 수 있는 Azure의 Intune에서 토글을 추가했습니다. 이렇게 하면 디바이스 준수가 평가된 후에 리소스에 액세스할 수 있습니다.

이 기능은 할당된 준수 정책 여부에 따라 다르게 적용됩니다.

- 새로운 또는 기존 테넌트이고 준수 정책이 디바이스에 할당되지 않는 경우 설정/해제는 자동으로 **준수**로 설정됩니다. 기능은 콘솔의 기본 설정으로 꺼져 있습니다. 최종 사용자에게는 영향이 없습니다.
- 기존 테넌트이며 준수 정책이 디바이스에 할당된 경우 설정/해제는 자동으로 **비준수**로 설정됩니다. 3월 업데이트가 공개될 때 기능은 기본 설정으로 켜져 있습니다.

CA(조건부 액세스)에서 준수 정책을 사용하고 기능을 설정한 경우, 할당된 준수 정책이 하나도 없는 디바이스는 CA에 의해 차단됩니다. 이러한 디바이스에 연결되어 있으며 사전에 이메일에 대한 액세스가 허용된 최종 사용자는 모든 디바이스에 준수 정책을 하나 이상 할당하지 않는 한 액세스가 손실됩니다.   

Intune 서비스 3월 업데이트에서 기본 설정/해제 상태는 바로 UI에 표시되지만 이 설정/해제 상태는 바로 적용되지 않습니다. 토글이 작동하도록 계정을 파일럿(플라이팅) 테스트할 때까지 토글에 적용한 변경 내용은 디바이스 준수에 영향을 주지 않습니다. 계정의 파일럿(플라이팅) 테스트를 완료하면 메시지 센터를 통해 알려줍니다. 3월에 Intune 서비스를 업데이트한 후에 최대 몇 일이 걸릴 수 있습니다.

**추가 정보**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>향상된 탈옥 검색 <!-- 846515 -->

향상된 탈옥 검색은 Intune이 무단 해제된 디바이스를 평가하는 방법을 향상시키는 새 준수 설정입니다. 이 설정은 디바이스의 위치 확인 서비스를 사용하고 배터리 사용에 영향을 주도록 더 자주 Intune을 사용하여 디바이스를 체크 인합니다.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>Android O 디바이스의 암호 다시 설정 <!-- 1238299 -->
작업 프로필사용을 하여 등록된 Android 8.0 디바이스에 암호를 다시 설정할 수 있습니다. Android 8.0 디바이스에 "암호 다시 설정" 요청을 보내면 해당 디바이스는 현재 사용자의 새 디바이스 잠금 해제 암호 또는 관리되는 프로필 챌린지를 설정합니다. 암호 또는 챌린지가 전송되고 즉시 적용됩니다.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>디바이스 그룹의 디바이스를 규정 준수 정책의 대상으로 지정 <!--1307012 -->

사용자 그룹의 사용자를 준수 정책의 대상으로 지정할 수 있습니다. 이 업데이트에서는 준수 정책을 디바이스 그룹의 디바이스 대상으로 지정할 수 있습니다. 디바이스 그룹의 일부로 대상이 지정된 디바이스는 준수 작업을 수신하지 않습니다.

#### <a name="new-management-name-column----1333586---"></a>새 관리 이름 열 <!-- 1333586 -->
 **관리 이름**이라는 새 열은 디바이스 블레이드에 지원됩니다. 이 이름은 다음 수식에 따라 디바이스당 할당된 자동 생성되고 편집할 수 없는 이름입니다.
- 모든 디바이스에 대한 기본 이름: <username><em><devicetype></em><enrollmenttimestamp>
- 대량으로 추가된 디바이스에 대해: &lt;PackageId/ProfileId&gt;<em><DeviceType></em><EnrollmentTime>

이 열은 디바이스 블레이드에서 선택적입니다. 이 열은 기본으로 지원되지 않고 열 선택기를 사용해서만 액세스할 수 있습니다. 디바이스 이름은 이 새 열에서 영향을 받지 않습니다.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS 디바이스에 15분마다 PIN을 입력하라는 메시지가 표시됩니다. <!--1550837 -->
준수 또는 구성 정책을 iOS 디바이스에 적용하면 사용자에게 15분마다 PIN을 설정하라는 메시지가 표시됩니다. 사용자가 PIN을 설정할 때까지 계속 메시지가 표시됩니다.

#### <a name="schedule-your-automatic-updates---1805514---"></a>자동 업데이트 예약 <!--1805514 -->
Intune에서는 [Windows Update 링 설정](windows-update-for-business-configure.md)을 사용하여 자동 업데이트를 설치하도록 제어할 수 있습니다. 이 업데이트에서는 주, 일, 시간을 비롯한 되풀이 업데이트를 예약할 수 있습니다.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>SCEP 인증서에 대한 제목으로 정식 고유 이름 사용 <!--2221763 -->
SCEP 인증서 프로필을 만들 때 주체 이름을 입력합니다. 이 업데이트에서는 정식 고유 이름을 주체로 사용할 수 있습니다. **주체 이름**에서 **사용자 지정**을 선택한 다음, `CN={{OnPrem_Distinguished_Name}}`을 입력합니다. `{{OnPrem_Distinguished_Name}}` 변수를 사용하려면 [Azure AD(Active Directory) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용하는 `onpremisesdistingishedname` 사용자 특성을 Azure AD와 동기화해야 합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Bluetooth 연락처 공유 사용 - Android for Work <!--1098983 -->
기본적으로 Android는 작업 프로필의 연락처를 Bluetooth 디바이스와 동기화하지 않도록 방지합니다. 결과적으로 작업 프로필 연락처는 Bluetooth 디바이스의 발신자 ID에 표시되지 않습니다.

이 업데이트에서는 **Android for Work** > **디바이스 제한** > **작업 프로필 설정**에서 새 설정이 지정됩니다.
- Bluetooth를 통한 연락처 공유

Intune 관리자는 공유할 수 있도록 이러한 설정을 구성할 수 있습니다. 핸즈 프리 사용에 호출자 ID를 표시하는 자동차 기반 Bluetooth 디바이스를 사용하여 디바이스를 연결하는 경우에 유용합니다. 사용하도록 설정하면 작업 프로필 연락처가 표시됩니다. 사용하지 않도록 설정하면 작업 프로필 연락처가 표시되지 않습니다.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>macOS 앱 다운로드 원본을 제어하는 Gatekeeper 구성 <!-- 1690459 -->

해당 앱을 어디서 다운로드할 수 있는지 제어하여 앱에서 디바이스를 보호하기 위해 Gatekeeper를 구성할 수 있습니다. **Mac 앱 스토어**, **Mac 앱 스토어 및 확인된 개발자** 또는 **원격** 등의 다운로드 원본을 구성할 수 있습니다. 사용자가 이러한 Gatekeeper 제어를 재정의하기 위해 Ctrl+클릭하여 앱을 설치할지 여부를 구성할 수 있습니다.

이러한 설정은 **디바이스 구성** -> **프로필 만들기** -> **macOS** -> **엔드포인트 보호** 아래에 있습니다.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Mac 애플리케이션 방화벽 구성 <!-- 1690461 -->

Mac 애플리케이션 방화벽을 구성할 수 있습니다. 포트당이 아닌 애플리케이션당을 기반으로 연결을 제어하는 데 이 방화벽을 사용할 수 있습니다. 이렇게 하면 쉽게 방화벽 보호의 이점을 얻고 바람직하지 않은 앱이 합법적인 앱에 대해 네트워크 포트 열기를 제어하는 것을 방지할 수 있습니다.

이 기능은 **디바이스 구성** -> **프로필 만들기** -> **macOS** -> **엔드포인트 보호** 아래에서 찾을 수 있습니다.

일단 방화벽 설정을 사용하면 두 가지 전략을 사용하여 방화벽을 구성할 수 있습니다.

- 들어오는 모든 연결 차단

   대상 디바이스에 대해 들어오는 모든 연결을 차단할 수 있습니다. 이 작업 수행을 선택한 경우 모든 앱에 대해 들어오는 연결이 차단됩니다.

- 특정 앱 허용 또는 차단

   들어오는 연결을 특정 앱이 수신하는 것을 허용하거나 차단할 수 있습니다. 검색 요청에 응답하지 않도록 은폐 모드를 사용할 수도 있습니다.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>자세한 오류 코드 및 메시지 <!-- 1376342 -->

디바이스 구성에서 자세한 오류 코드 및 오류 메시지를 확인할 수 있습니다. 이 향상된 보고 기능은 설정, 설정 상태 및 자세한 문제 해결 정보를 보여 줍니다.

##### <a name="more-information"></a>추가 정보

- 들어오는 모든 연결 차단

   이는 모든 공유 서비스(예: 파일 공유, 화면 공유)가 들어오는 연결을 수신하는 것을 차단합니다. 들어오는 연결을 여전히 수신할 수 있는 시스템 서비스는 다음과 같습니다.
  - configd - DHCP 및 다른 네트워크 구성 서비스 구현
  - mDNSResponder - Bonjour 구현
  - racoon - IPSec 구현

    공유 서비스를 사용하려면 **들어오는 연결**이 **구성 되지 않음** (**차단**하지 않음)으로 설정되게 합니다.

- 은폐 모드

   이 모드를 사용하여 컴퓨터가 검색 요청에 응답하지 않게 합니다. 그래도 컴퓨터는 권한이 부여된 앱에 대해 들어오는 요청에는 응답합니다. ICMP(ping)와 같은 예기치 않은 요청은 무시합니다.

#### <a name="disable-checks-on-device-restart---1805490---"></a>디바이스 다시 시작에 대한 검사 사용 안 함 <!--1805490 -->
Intune에서는 [소프트웨어 업데이트를 관리](windows-update-for-business-configure.md)하는 컨트롤을 제공합니다. 이 업데이트에서 <strong>검사 다시 시작</strong> 속성이 지원되고 기본적으로 설정됩니다. 디바이스를 다시 시작할 때 발생하는 일반적인 검사(예: 활성 사용자, 배터리 수준 등)를 건너뛰려면 <strong>건너뛰기</strong>를 선택합니다.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>배포 링에 지원되는 새로운 Windows 10 Insider Preview 채널 <!-- 1746293 -->
Windows 10 배포 링을 만들 때 다음 Windows 10 Insider Preview 채널 서비스를 선택하는 옵션이 있습니다.
- Windows Insider 빌드 &#8208; 빠름
- Windows Insider 빌드 &#8208; 느림
- Windows Insider 빌드 릴리스 

이러한 채널에 대한 자세한 내용은 [Insider Preview 빌드 관리](https://insider.windows.com/for-business-organization-admin/)를 참조하세요.   
Intune에서 배포 채널을 만드는 방법에 대한 자세한 내용은 [Intune에서 소프트웨어 업데이트 관리](windows-update-for-business-configure.md)를 참조하세요.

### <a name="new-windows-defender-exploit-guard-settings----1631893---"></a>새로운 Windows Defender Exploit Guard 설정 <!-- 1631893 -->

이제 여섯 가지 새 <strong>공격 노출 영역 축소</strong> 설정 및 확장된 <strong>폴더 액세스 제어: 폴더 보호</strong> 기능이 제공됩니다. 이러한 설정은 Device configuration\Profiles\에서 찾을 수 있습니다.
profile\Endpoint protection\Windows Defender Exploit Guard를 만드세요.

#### <a name="attack-surface-reduction"></a>공격 노출 영역 축소

|설정 이름  |설정 옵션  |설명  |
|---------|---------|---------|
|고급 랜섬웨어 보호|사용, 감사, 구성되지 않음|적극적인 랜섬웨어 보호를 사용합니다.|
|Windows 로컬 보안 기관 하위 시스템에서 도용하는 자격 증명에 플래그 지정|사용, 감사, 구성되지 않음|Windows 로컬 보안 기관 하위 시스템(lsass.exe)에서 도용하는 자격 증명에 플래그를 지정합니다.|
|PSExec 및 WMI 명령에서 프로세스 만들기|차단, 감사, 구성되지 않음|PSExec 및 WMI 명령에서 발생하는 프로세스 만들기를 차단합니다.|
|USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스|차단, 감사, 구성되지 않음|USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스를 차단합니다.|
|출현율, 나이 또는 신뢰할 수 있는 목록 기준을 충족하지 않는 실행 파일|차단, 감사, 구성되지 않음|실행 파일이 출현율, 나이 또는 신뢰할 수 있는 목록 기준을 충족하지 않으면 실행을 차단합니다.|

#### <a name="controlled-folder-access"></a>폴더 액세스 제어

|              설정 이름               |                                                              설정 옵션                                                              | 설명 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 폴더 보호(이미 구현됨) | 구성되지 않음, 사용, 감사만(이미 구현됨)<br><br> <strong>새 항목</strong><br>디스크 수정 차단, 디스크 수정 감사 |             |

인증되지 않은 앱이 파일 및 폴더를 무단으로 변경할 수 없도록 보호합니다.<br><br>**사용**: 신뢰할 수 없는 앱이 보호되는 폴더의 파일을 수정 또는 삭제하거나 디스크 섹터에 쓰는 것을 차단합니다.<br><br>
**디스크 수정만 차단**:<br>신뢰할 수 없는 앱이 디스크 섹터에 쓰는 것을 차단합니다. 신뢰할 수 없는 앱이 보호되는 폴더의 파일을 여전히 수정하거나 삭제할 수 있습니다.|

### <a name="intune-apps"></a>Intune 앱

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 웹 사이트에는 Intune Managed Browser 앱이 필요하고 Managed Browser(공개 미리 보기)에 대해 Single Sign-On을 지원할 수 있습니다. <!-- 710595 -->

이제 Azure AD(Azure Active Directory)를 사용하여 모바일 디바이스의 Intune Managed Browser 앱에 대한 웹 사이트 액세스를 제한할 수 있습니다. Managed Browser에서 웹 사이트 데이터는 최종 사용자 개인 데이터와 별도로 안전하게 유지됩니다. 또한 Managed Browser는 Azure AD에서 보호하는 사이트에 Single Sign-On 기능을 지원합니다. Managed Browser에 로그인하거나 Intune에서 관리하는 다른 앱과 함께 디바이스에서 Managed Browser를 사용하면 사용자에게 자격 증명을 입력하지 않고도 Azure AD에서 보호되는 회사 사이트에 액세스할 수 있습니다. 이 기능은 OWA(Outlook Web Access) 및 SharePoint Online과 같은 사이트뿐만 아니라 Azure 앱 프록시를 통해 액세스되는 인트라넷 리소스와 같은 다른 회사 사이트에도 적용됩니다. 자세한 내용은 [Azure Active Directory 조건부 액세스의 액세스 제어](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls)를 참조하세요.

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Android용 회사 포털 앱 시각적 개체 업데이트 <!--976944 -->

Android의 [자료 디자인](https://material.io/) 지침에 따르도록 Android용 회사 포털 앱을 업데이트했습니다. [앱 UI의 새로운 기능](whats-new-app-ui.md) 아티클에서 새 아이콘의 이미지를 볼 수 있습니다.

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>회사 포털 등록 향상 <!-- 1874230 eeready-->
Windows 10 Build 1703 이상에서 회사 포털을 사용하여 디바이스를 등록하는 사용자는 이제 해당 앱을 종료하지 않고 등록의 첫 번째 단계를 완료할 수 있습니다.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens 및 Surface Hub가 이제 디바이스 목록에 표시됩니다. <!--1725868 -->
Intune에 등록된 HoloLens 및 Surface Hub 디바이스를 Android용 회사 포털 앱에 표시하는 지원을 추가했습니다.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>VPP(대량 구매 프로그램) eBook에 대한 사용자 지정 책 범주 <!-- 1488911 -->
사용자 지정 전자책 범주를 만든 다음, 해당 사용자 지정 전자책 범주에 VPP 전자책을 할당할 수 있습니다. 그러면 최종 사용자는 새로 만든 전자책 범주 및 해당 범주에 할당된 책을 확인할 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 앱 및 전자책 관리](vpp-apps.md)를 참조하세요.  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Windows용 회사 포털 앱 피드백 보내기 옵션에 대한 지원 변경 내용 <!-- 2070166 -->
2018년 4월 30일부터 Windows용 회사 포털 앱의 **피드백 보내기** 옵션은 Windows 10 1주년 업데이트(1607) 이상을 실행하는 디바이스에서만 작동합니다. 다음 환경에서 Windows용 회사 포털 앱을 사용하는 경우 피드백 보내기 옵션이 더 이상 지원되지 않습니다.  
- Windows 10, 1507 릴리스  
- Windows 10, 1511 릴리스  
- Windows Phone 8.1 

Windows 10 RS1 이상에서 디바이스가 실행 중인 경우 스토어에서 Windows 회사 포털 앱의 최신 버전을 다운로드하세요. 지원되지 않는 버전을 실행 중인 경우 다음 채널을 통해 피드백을 계속 보내세요. 
- Windows 10의 피드백 허브 앱
- 메일 WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>새 Windows Defender Application Guard 설정 <!-- 1631890 -->

- **그래픽 가속 사용**: 관리자는 Windows Defender Application Guard에 그래픽 가상 프로세서를 사용할 수 있습니다. 이 설정은 CPU가 그래픽 렌더링을 vGPU에 오프로드하는 것을 허용합니다. 이렇게 하면 컨테이너 내에서 그래픽 집약적인 웹 사이트를 작업하거나 비디오를 볼 때 성능을 향상할 수 있습니다.

- **SaveFilestoHost**: 관리자는 컨테이너에서 실행되는 Microsoft Edge에서 호스트 파일 시스템으로 파일을 전달하도록 설정할 수 있습니다. 이 설정을 켜면 사용자가 컨테이너의 Microsoft Edge에서 호스트 파일 시스템으로 파일을 다운로드할 수 있습니다.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>관리 상태에 따라 대상으로 지정된 MAM 보호 정책 <!-- 1665993 -->
디바이스의 관리 상태에 따라 MAM 정책을 대상으로 지정할 수 있습니다.
- **Android 디바이스** - 관리되지 않는 디바이스, Intune 관리 디바이스 및 Intune 관리 Android Enterprise 프로필(이전의 Android for Work)을 대상으로 지정할 수 있습니다.
- **iOS 디바이스** - 관리되지 않는 디바이스(MAM만 해당) 또는 Intune 관리 디바이스를 대상으로 지정할 수 있습니다.

    > [!NOTE]
    > - 이 기능에 대한 iOS 지원은 2018년 4월까지 출시됩니다.

자세한 내용은 [디바이스 관리 상태에 따른 대상 응용 프로그램 보호 정책](app-protection-policies.md)을 참조하세요.

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows용 회사 포털 앱의 언어 개선 사항 <!-- 1683758 -->
귀사에 더욱 친숙하고 구체적이 되도록 Windows 10용 회사 포털에서 언어를 개선하였습니다. 수행한 몇 가지 샘플 이미지를 보려면 [앱 UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>사용자 개인 정보 보호에 대한 문서에 새로 추가된 기능 <!-- 1440709 -->
최종 사용자에게 해당 데이터 및 개인 정보 보호에 대한 제어를 제공하려는 노력의 일환으로 회사 포털 앱에서 로컬로 저장된 데이터를 보고 제거하는 방법을 설명하는 문서에 업데이트를 게시했습니다. 다음에서 이러한 업데이트를 찾을 수 있습니다.

- **Android**: [Intune에서 Android 디바이스를 제거하는 방법](/intune-user-help/unenroll-your-device-from-intune-android)
- **사용자가 사용 약관을 거부한 경우 Android**: ["사용 약관" 거부한 경우 디바이스 관리를 제거합니다.](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android)
- **iOS**: [Intune에서 iOS 디바이스 제거](/intune-user-help/unenroll-your-device-from-intune-ios)
- **Windows**: [Intune에서 Windows 디바이스 제거](/intune-user-help/unenroll-your-device-from-intune-windows)

<!-- ########################## -->
## <a name="february-2018"></a>2018년 2월

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>여러 Apple DEP/Apple School Manager 계정에 대한 Intune 지원 <!-- 747685 -->

이제 Intune은 최대 100개의 다른 [Apple DEP(장비 등록 프로그램)](device-enrollment-program-enroll-ios.md) 또는 [Apple School Manager](apple-school-manager-set-up-ios.md) 계정의 디바이스 등록을 지원합니다. 업로드된 각 토큰을 등록 프로필과 디바이스에 대해 별도로 관리할 수 있습니다. 업로드된 DEP/School Manager 토큰마다 다른 등록 프로필을 자동으로 할당할 수 있습니다. School Manager 토큰이 여러 개 업로드된 경우 한 번에 하나의 토큰만 Microsoft School Data Sync와 공유할 수 있습니다.

Graph를 통해 Apple DEP 또는 ASM을 관리하기 위한 베타 Graph API 및 게시된 스크립트는 마이그레이션 후 더 이상 작동하지 않습니다. 새 베타 Graph API가 개발 중이며 마이그레이션 후 릴리스될 예정입니다.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>사용자별 등록 제한 보기 <!-- 1634444 eeready wnready -->
이제 **할당** 목록에서 **등록 제한**을 선택함으로써 각 사용자에게 적용되는 [등록 제한](enrollment-restrictions-set.md)을 **문제 해결** 블레이드에 표시할 수 있습니다.

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Apple 대량 등록을 위한 새로운 사용자 인증 옵션 <!-- 747625 eeready -->

> [!NOTE]
> 새 테넌트는 바로 제공됩니다. 기존 테넌트의 경우 이 기능은 4월 중 공개됩니다. 이 출시가 완료될 때까지는 이러한 새 기능에 액세스하지 못할 수 있습니다.

Intune은 다음 등록 방법에 대해 회사 포털 앱을 사용하여 디바이스를 인증하는 옵션을 제공합니다.

- Apple 장비 등록 프로그램
- Apple School Manager
- Apple Configurator 등록

회사 포털 옵션을 사용하면 이러한 등록 방법을 차단하지 않고 Azure Active Directory 다단계 인증을 적용할 수 있습니다.

회사 포털 옵션을 사용할 경우 Intune은 사용자 선호도 등록을 위한 iOS 설정 도우미의 사용자 인증을 건너뜁니다. 따라서 처음에는 디바이스가 사용자 없는 디바이스로 등록되므로 사용자 그룹의 구성 또는 정책을 받지 않습니다. 디바이스 그룹의 구성과 정책만 받습니다. 그러나 Intune이 디바이스에 회사 포털 앱을 자동으로 설치합니다. 회사 포털 앱을 시작하고 로그인하는 첫 번째 사용자가 Intune에서 해당 디바이스와 연결됩니다. 사용자는 이때 사용자 그룹의 구성과 정책을 받습니다. 사용자 연결을 변경하려면 다시 등록해야 합니다.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>여러 Apple DEP/Apple School Manager 계정에 대한 Intune 지원 <!-- 747685 eeready -->

이제 Intune은 최대 100개의 다른 Apple DEP(장비 등록 프로그램) 또는 Apple School Manager 계정의 디바이스 등록을 지원합니다. 업로드된 각 토큰을 등록 프로필과 디바이스에 대해 별도로 관리할 수 있습니다. 업로드된 DEP/School Manager 토큰마다 다른 등록 프로필을 자동으로 할당할 수 있습니다. School Manager 토큰이 여러 개 업로드된 경우 한 번에 하나의 토큰만 Microsoft School Data Sync와 공유할 수 있습니다.

Graph를 통해 Apple DEP 또는 ASM을 관리하기 위한 베타 Graph API 및 게시된 스크립트는 마이그레이션 후 더 이상 작동하지 않습니다. 새 베타 Graph API가 개발 중이며 마이그레이션 후 릴리스될 예정입니다.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>보안 네트워크를 통한 원격 인쇄 <!-- 1709994  -->
PrinterOn의 무선 모바일 인쇄 솔루션을 사용하면 사용자가 보안 네트워크를 통해 언제 어디서나 원격으로 인쇄할 수 있습니다. PrinterOn은 iOS 및 Android용 Intune 앱 SDK와 둘 다 통합됩니다. 관리 콘솔의 Intune **앱 보호 정책** 블레이드를 통해 이 앱을 앱 보호 정책의 대상으로 지정할 수 있습니다. 최종 사용자는 Intune 에코시스템에서 사용하기 위해 Play 스토어 또는 iTunes를 통해 'PrinterOn for Microsoft' 앱을 다운로드할 수 있습니다.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>디바이스 등록 관리자를 사용하는 등록에 대한 macOS 회사 포털 지원 <!-- 1352411 -->

사용자는 macOS 회사 포털에 등록할 때 디바이스 등록 관리자를 사용할 수 있습니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 상태 및 위협 상태 보고서 <!--854704 -->

Windows Defender의 상태를 이해하는 것은 Windows PC 관리의 핵심입니다.  이 업데이트를 사용해 Intune은 Windows Defender 에이전트의 상태에 새 보고서와 작업을 추가합니다. [디바이스 정책 준수 워크로드](compliance-policy-monitor.md)에 상태 롤업 보고서를 사용하면 다음 작업이 필요한 디바이스를 볼 수 있습니다.
- 서명 업데이트
- 다시 시작
- 수동 작업
- 전체 검사
- 개입이 필요한 기타 에이전트 상태

각 상태 범주에 대한 드릴인 보고서에는 주의가 필요한 개별 PC 또는 **정리**로 보고되는 PC가 나열됩니다.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>디바이스 제안에 대한 새로운 개인 정보 설정 <!--1308926 -->
디바이스에 [두 가지 새로운 개인 정보 설정](device-restrictions-windows-10.md#privacy)이 제공됩니다.
- **사용자 작업 게시**: 작업 전환기에서 공유 경험 및 최근에 사용된 리소스 검색을 차단하려면 이 옵션을 **차단**으로 설정합니다.
- **로컬 작업만**: 로컬 작업에 대해서만 작업 전환기에서 공유 경험 및 최근에 사용된 리소스 검색을 차단하려면 이 옵션을 **차단**으로 설정합니다.

#### <a name="new-settings-for-the-microsoft-edge-browser---1469166---"></a>Microsoft Edge 브라우저에 대한 새 설정 <!--1469166 -->
Microsoft Edge 브라우저가 있는 디바이스에 대해 이제 [두 가지 새로운 설정](device-restrictions-windows-10.md#microsoft-edge-browser)인 **자주 사용하는 파일 경로** 및 **즐겨찾기에 대한 변경**을 사용할 수 있습니다.

### <a name="app-management"></a>앱 관리

#### <a name="protocol-exceptions-for-applications---1035509---"></a>애플리케이션에 대한 프로토콜 예외 <!--1035509 -->

Intune MAM(모바일 애플리케이션 관리) 데이터 전송 정책에 대한 예외를 만들어서 관리되지 않는 애플리케이션을 열 수 있습니다. 이러한 애플리케이션은 IT가 신뢰할 수 있는 것이어야 합니다. 관리자가 만드는 예외를 제외하고, 데이터 전송 정책을 **관리되는 앱만**으로 설정하는 경우 데이터 전송은 Intune에서 관리하는 애플리케이션으로 계속 제한됩니다. 프로토콜(iOS) 또는 패키지(Android)를 사용하여 제한을 만들 수 있습니다.

예를 들어 Webex 패키지를 MAM 데이터 전송 정책의 예외로 추가할 수 있습니다. 이렇게 하면 관리되는 Outlook 이메일 메시지의 Webex 링크가 Webex 애플리케이션에서 바로 열립니다. 관리되지 않는 다른 애플리케이션에서는 데이터 전송이 계속 제한됩니다. 자세한 내용은 [앱에 대한 데이터 전송 정책 예외](app-protection-policies-exception.md)를 참조합니다.

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 검색 결과의 WIP(Windows Information Protection) 암호화된 데이터 <!-- 1469193 -->
WIP(Windows Information Protection) 정책의 설정을 사용하면 WIP 암호화된 데이터를 Windows 검색 결과에 포함할지 여부를 제어할 수 있습니다. Windows 정보 보호 정책의 **고급 설정**에서 **Windows Search Indexer로 암호화된 항목 검색 가능**을 선택해 앱 보호 정책 옵션을 설정합니다. 앱 보호 정책은 *Windows 10* 플랫폼에 설정돼야 하며 해당 앱 정책 **등록 상태**는 **등록을 통해** 설정돼야 합니다. 자세한 내용은 [Windows Search Indexer로 암호화된 항목 검색 가능](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)을 참조합니다.

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>자체 업데이트 모바일 MSI 앱 구성 <!-- 1740840 -->
버전 확인 프로세스를 무시하도록 알려진 자체 업데이트 모바일 MSI 앱을 구성할 수 있습니다. 이 기능은 경합 상태를 방지하는 데 유용합니다. 예를 들어 이런 유형의 경합 상태는 앱 개발자가 앱을 자동 업데이트하는 동시에 Intune에서도 앱을 업데이트하는 경우 발생할 수 있습니다. 둘 다 Windows 클라이언트에서 앱 버전을 적용하려 시도할 수 있으며, 이로 인해 충돌이 발생할 수 있습니다. 이러한 자동으로 업데이트된 MSI 앱의 경우 **앱 정보** 블레이드에서 **앱 버전 무시** 설정을 구성할 수 있습니다. 이 설정이 **예**로 전환될 경우 Microsoft Intune에서 Windows 클라이언트에 설치 된 앱 버전을 무시하게 됩니다.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune에서 지원되는 관련 앱 라이선스 세트 <!-- 1864117 -->
이제 Azure Portal의 Intune은 관련 앱 라이선스 집합을 UI에서 단일 앱 항목으로 지원합니다. 또한 비즈니스용 Microsoft 스토어에서 동기화되는 오프라인 라이선스 앱은 단일 앱 항목으로 통합되고, 개별 패키지의 배포 세부 정보는 단일 항목으로 마이그레이션됩니다. Azure Portal에서 관련 앱 라이선스 집합을 보려면 **클라이언트 앱** 블레이드에서 **앱 라이선스**를 선택합니다.

### <a name="device-configuration"></a>디바이스 구성
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>자동 암호화를 위한 WIP(Windows Information Protection) 파일 확장명 <!-- 1463582 -->
WIP(Windows Information Protection) 정책의 설정으로 이제 WIP 정책에서 정의된 대로 회사 경계 내부의 SMB(Server Message Block) 공유에서 복사하는 경우 파일 확장명은 자동으로 암호화되도록 지정할 수 있습니다.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Surface Hub에 대한 리소스 계정 설정 구성

Surface Hub에 대한 리소스 계정 설정을 원격으로 구성할 수 있습니다.

리소스 계정은 Surface Hub가 Skype/Exchange에 인증하는 데 사용되므로 모임에 참여할 수 있습니다.
Surface Hub가 모임에서 회의실로 표시되도록 고유한 리소스 계정을 만들 수 있습니다.
예를 들어 **회의실 B41/6233**이라는 리소스 계정을 만들 수 있습니다.

> [!NOTE]
> - 필드를 비워 두면 디바이스에서 이전에 구성된 특성이 재정의됩니다.
>
> - 리소스 계정 속성은 Surface Hub에서 동적으로 변경할 수 있습니다. 예를 들어 암호 순환이 켜져 있으면 Azure 콘솔의 값이 디바이스에서 현실을 반영할 때까지 다소 시간이 걸릴 수 있습니다.
>
>   리소스 계정 정보를 하드웨어 인벤토리에(이미 7일 간격이 있음) 또는 읽기 전용 속성으로 포함하면 현재 Surface Hub에 구성된 내용을 이해할 수 있습니다. 원격 작업을 실행한 후 정확도를 높이려면 Surface Hub에서 계정/매개 변수 업데이트 작업을 실행하는 즉시 매개 변수 상태를 가져오면 됩니다.

##### <a name="attack-surface-reduction"></a>공격 노출 영역 축소

|설정 이름  |설정 옵션  |설명  |
|---------|---------|---------|
|이메일에서 암호로 보호된 실행 가능한 콘텐츠의 실행|차단, 감사, 구성되지 않음|이메일로 다운로드된 암호로 보호된 실행 파일이 실행되는 것을 방지합니다.|
|고급 랜섬웨어 보호|사용, 감사, 구성되지 않음|적극적인 랜섬웨어 보호를 사용합니다.|
|Windows 로컬 보안 기관 하위 시스템에서 도용하는 자격 증명에 플래그 지정|사용, 감사, 구성되지 않음|Windows 로컬 보안 기관 하위 시스템(lsass.exe)에서 도용하는 자격 증명에 플래그를 지정합니다.|
|PSExec 및 WMI 명령에서 프로세스 만들기|차단, 감사, 구성되지 않음|PSExec 및 WMI 명령에서 발생하는 프로세스 만들기를 차단합니다.|
|USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스|차단, 감사, 구성되지 않음|USB에서 실행되는 신뢰할 수 없고 서명되지 않은 프로세스를 차단합니다.|
|출현율, 나이 또는 신뢰할 수 있는 목록 기준을 충족하지 않는 실행 파일|차단, 감사, 구성되지 않음|실행 파일이 출현율, 나이 또는 신뢰할 수 있는 목록 기준을 충족하지 않으면 실행을 차단합니다.|

##### <a name="controlled-folder-access"></a>폴더 액세스 제어

|              설정 이름               |                                                              설정 옵션                                                              | 설명 |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| 폴더 보호(이미 구현됨) | 구성되지 않음, 사용, 감사만(이미 구현됨)<br><br> <strong>새 항목</strong><br>디스크 수정 차단, 디스크 수정 감사 |             |

인증되지 않은 앱이 파일 및 폴더를 무단으로 변경할 수 없도록 보호합니다.<br><br>**사용**: 신뢰할 수 없는 앱이 보호되는 폴더의 파일을 수정 또는 삭제하거나 디스크 섹터에 쓰는 것을 차단합니다.<br><br>
**디스크 수정만 차단**:<br>신뢰할 수 없는 앱이 디스크 섹터에 쓰는 것을 차단합니다. 신뢰할 수 없는 앱이 보호되는 폴더의 파일을 여전히 수정하거나 삭제할 수 있습니다.|

#### <a name="additions-to-system-security-settings-for-windows-10-and-later-compliance-policies---1704133--"></a>Windows 10 및 향후 규정 준수 정책에 대한 시스템 보안 설정 추가 <!--1704133-->

방화벽과 Windows Defender 바이러스 백신을 반드시 사용하게 하는 것을 포함하여 Windows 10 규정 준수 설정이 추가됩니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>비즈니스용 Microsoft 스토어의 오프라인 앱 지원 <!--1222672-->
이제 비즈니스용 Microsoft 스토어에서 구매한 오프라인 앱이 Azure Portal에 동기화됩니다. 그런 다음, 이러한 앱을 디바이스 그룹 또는 사용자 그룹에 배포할 수 있습니다. 오프라인 앱은 스토어가 아닌 Intune을 통해 설치됩니다.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>최종 사용자가 작업 프로필의 계정을 수동으로 추가 또는 삭제하지 못하게 방지 <!-- 1728700 -->

Gmail 앱을 Android for Work 프로필에 배포하면, Android for Work 디바이스 제한 프로필에서 **계정 추가 및 제거** 설정을 사용하여 최종 사용자가 작업 프로필에 계정을 수동으로 추가하거나 삭제하지 못하게 할 수 있습니다.

<!-- ########################## -->
## <a name="january-2018"></a>2018년 1월

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>만료된 토큰 및 곧 만료되는 토큰에 대한 경고 <!-- 1639263 -->
개요 페이지에는 이제 만료된 토큰과 곧 만료되는 토큰에 대한 경고가 표시됩니다. 단일 토큰에 대한 경고를 클릭하면 토큰의 세부 정보 페이지로 이동합니다.  여러 토큰이 포함된 경고를 클릭하면 해당 상태의 모든 토큰 목록으로 이동합니다. 관리자는 만료 날짜 전에 해당 토큰을 갱신해야 합니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS 디바이스를 위한 원격 "지우기" 명령 지원 <!-- 1438084 -->

관리자는 macOS 디바이스에 지우기 명령을 원격으로 실행할 수 있습니다.

> [!IMPORTANT]
> 지우기 명령은 취소할 수 없으며 주의해서 사용해야 합니다.

지우기 명령은 디바이스에서 운영 체제를 비롯한 모든 데이터를 제거합니다. 또한 Intune 관리에서 디바이스를 제거합니다. 사용자에게 경고가 표시되지 않으며, 명령을 실행하는 즉시 지우기가 수행됩니다.

6자리 복구 PIN을 구성해야 합니다. 이 PIN을 사용하여 지워진 디바이스의 잠금을 해제할 수 있으며, 이때 운영 체제의 재설치가 시작됩니다. 지우기가 시작된 후에는 Intune의 디바이스 개요 블레이드에 있는 상태 표시줄에 PIN이 표시됩니다. 지우기가 진행되는 동안 PIN이 계속 유지됩니다. 지우기가 완료되면 디바이스가 Intune 관리에서 완전히 사라집니다. 디바이스를 복원하는 누구든지 사용할 수 있도록 복구 PIN을 기록해야 합니다.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program 토큰에 대한 라이선스 철회 <!-- 820870 -->
지정된 VPP 토큰에 대한 모든 iOS VPP(Volume-Purchase Program) 앱의 라이선스를 철회할 수 있습니다.

### <a name="app-management"></a>앱 관리

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program 앱 철회  <!-- 820863 -->
하나 이상의 iOS VPP(Volume-Purchase Program) 앱이 설치된 지정된 디바이스의 경우 디바이스의 관련 디바이스 기반 앱 라이선스를 철회할 수 있습니다. 앱 라이선스를 철회해도 디바이스에서 관련 VPP 앱이 제거되지 않습니다. VPP 앱을 제거하려면 할당 작업을 **제거**로 변경해야 합니다. 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법](vpp-apps-ios.md)을 참조하세요.

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>기본 제공 앱 유형을 사용하여 iOS 및 Android 디바이스에 Office 365 모바일 앱 할당 <!-- 1332318 -->
**기본 제공** 앱 유형을 사용하면 사용자가 관리하는 iOS 및 Android 디바이스에 Office 365 앱을 손쉽게 만들고 할당할 수 있습니다. 이러한 앱에는 Word, Excel, PowerPoint 및 OneDrive와 같은 0365 앱이 포함됩니다. 특정 앱을 앱 유형에 할당하고, 앱 정보 구성을 편집할 수 있습니다.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>그룹에 따라 앱 할당 포함 및 제외 <!-- 1406920 -->

앱 할당 중이나 할당 유형을 선택한 후 포함할 그룹과 제외할 그룹을 선택할 수 있습니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>할당을 포함하거나 제외하여 애플리케이션 구성 정책을 그룹에 할당할 수 있습니다.  <!-- 1480316 -->

포함 및 제외 할당의 조합을 사용하여 사용자 및 디바이스 그룹에 애플리케이션 구성 정책을 할당할 수 있습니다. 할당을 그룹의 사용자 정의 선택 또는 가상 그룹으로 선택할 수 있습니다. 가상 그룹은 **모든 사용자**, **모든 디바이스** 또는 **모든 사용자 + 모든 디바이스**를 포함할 수 있습니다.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 버전 업그레이드 정책에 대한 지원   <!-- 903672(archived), 1119689 -->  
Windows 10 디바이스를 Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education 및 Windows 10 Professional Education N으로 업그레이드하는 Windows 10 버전 업그레이드 정책을 만들 수 있습니다. Windows 10 버전 업그레이드에 대한 자세한 내용은 [Windows 10 버전 업그레이드 구성 방법](edition-upgrade-configure-windows-10.md)을 참조하세요.

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune에 대한 조건부 액세스 정책은 Azure Portal에서만 사용할 수 있습니다.  <!-- 1737088 1634311 -->

이 릴리스부터 **Azure Active Directory** > **조건부 액세스**에서 [Azure Portal](https://portal.azure.com)의 조건부 액세스 정책을 구성하고 관리해야 합니다. 편의상, **Intune** > **조건부 액세스**를 통해 Azure Portal의 Intune에서 이 블레이드에 액세스할 수도 있습니다.

#### <a name="updates-to-compliance-emails---1637547---"></a>규정 준수 이메일 업데이트 <!--1637547 -->

비준수 디바이스를 보고하기 위해 메일을 보낼 때 비준수 디바이스에 대한 세부 정보가 포함됩니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android 디바이스의 "해결" 작업을 위한 새로운 기능 <!--1583480-->

Android용 회사 포털 앱은 **디바이스 설정 업데이트**에 대한 "해결" 작업을 확장하여 [디바이스 암호화 문제](/intune-user-help/encrypt-your-device-android)를 해결합니다.

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10용 회사 포털 앱에서 원격 잠금 사용 가능 <!--676506-->
이제 최종 사용자가 Windows 10용 회사 포털 앱에서 자신의 디바이스를 원격으로 잠글 수 있습니다. 최종 사용자가 적극적으로 사용하는 로컬 디바이스에는 이것이 표시되지 않습니다.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Windows 10용 회사 포털 앱의 규정 준수 문제 해결 용이 <!--676546-->
Windows 디바이스를 사용하는 최종 사용자는 회사 포털 앱에서 비준수 이유를 탭할 수 있습니다. 가능하면 문제를 해결하기 위해 설정 앱의 올바른 위치로 직접 이동시킵니다.

<!-- ########################## -->
## <a name="december-2017"></a>2017년 12월

### <a name="device-configuration"></a>디바이스 구성

#### <a name="new-automatic-redeployment-setting----1469168---"></a>새 자동 재배포 설정 <!-- 1469168 -->
**자동 재배포** 설정은 관리 권한을 가진 사용자가 디바이스 잠금 화면에서 **CTRL + Win + R**을 사용하여 모든 사용자 데이터 및 설정을 삭제할 수 있습니다. 디바이스가 자동으로 재구성되고 관리에 다시 등록됩니다. 이 설정은 Windows 10 &gt; [디바이스 제한] &gt; [일반] &gt; [자동 재배포]에서 찾을 수 있습니다. 자세한 내용은 [Windows 10에 대한 Intune 디바이스 제한 설정](device-restrictions-windows-10.md#general)을 참조하세요.

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Windows 10 버전 업그레이드 정책에서 추가 소스 버전 지원  <!-- 903672,  1119689 -->
이제 Windows 10 버전 업그레이드 정책을 사용하여 추가 Windows 10 버전(Windows 10 Pro, Windows 10 Pro for Education, Windows 10 클라우드 등)에서 업그레이드할 수 있습니다. 이 릴리스 이전에는 지원되는 버전 업그레이드 경로가 더 제한적이었습니다. 자세한 내용은 [Windows 10 버전 업그레이드를 구성하는 방법](edition-upgrade-configure-windows-10.md)을 참조하세요.

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>새 WDSC(Windows Defender 보안 센터) 디바이스 구성 프로필 설정 <!-- 1335507 -->

Intune은 **Windows Defender 보안 센터**라는 엔드포인트 보호가 적용되는 디바이스 구성 프로필 설정의 새 섹션을 추가합니다. IT 관리자는 최종 사용자가 액세스할 수 있는 Windows Defender 보안 센터 앱 영역을 구성할 수 있습니다. IT 관리자가 Windows Defender 보안 센터 앱 영역을 숨기면 숨겨진 영역에 관련된 모든 알림이 사용자 디바이스에 표시되지 않습니다.

관리자는 Windows Defender 보안 센터 디바이스 구성 프로필 설정에서 이러한 영역을 숨길 수 있습니다.
- 바이러스 및 위협 방지
- 디바이스 성능 및 상태
- 방화벽 및 네트워크 보호
- 앱 및 브라우저 제어
- 패밀리 옵션

IT 관리자는 사용자가 받는 알림을 사용자 지정할 수도 있습니다. 예를 들어, 사용자가 WDSC의 표시되는 영역에서 생성되는 모든 알림을 수신할지, 아니면 중요 알림만 수신할지 구성할 수 있습니다. 중요하지 않은 알림에는 스캔이 완료되었을 경우 생성되는 Windows Defender 바이러스 백신 작업 및 알림에 대한 주기적 요약이 포함됩니다. 다른 모든 알림은 중요 알림으로 간주합니다. 또한 알림 콘텐츠 자체를 사용자 지정할 수 있습니다. 예를 들어, 사용자의 디바이스에 표시되는 알림에 포함할 IT 담당자 정보를 제공할 수 있습니다.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP 및 PFX 인증서 처리에 대한 여러 커넥터 지원 <!-- 1361755 -->

이제 온-프레미스 NDES 커넥터를 사용하여 인증서를 디바이스에 전달하는 고객이 단일 테넌트에 여러 커넥터를 구성할 수 있습니다.

이 새로운 기능은 다음 시나리오를 지원합니다.

- **고가용성**

각 NDES Connector는 Intune에서 인증서 요청을 풀합니다.  하나의 NDES Connector가 오프라인으로 전환될 경우 다른 커넥터는 계속 요청을 처리할 수 있습니다.

#### <a name="customer-subject-name-can-use-aad_device_id-variable-----1468599---"></a>고객 주체 이름은 AAD_DEVICE_ID 변수를 사용할 수 있습니다.  <!-- 1468599 -->

Intune에서 SCEP 인증서 프로필을 만드는 경우 이제 사용자 지정 주체 이름을 만들 때 AAD_DEVICE_ID 변수를 사용할 수 있습니다.   이 SCEP 프로필을 사용하여 인증서를 요청하면 해당 변수가 인증서 요청을 만드는 디바이스의 AAD 디바이스 ID로 바뀝니다.


### <a name="device-management"></a>디바이스 관리

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Intune의 디바이스 규정 준수 엔진을 사용하여 Jamf에 등록된 macOS 디바이스 관리 <!-- 1592747 -->
이제 Jamf를 사용하여 macOS 디바이스 상태 정보를 Intune에 전송할 수 있으며, Intune은 Intune 콘솔에 정의된 정책을 사용하여 디바이스의 준수 여부를 평가합니다. 디바이스 준수 상태 및 기타 조건(예: 위치, 사용자 위험 등)에 기반을 둔 조건부 액세스는 Office 365를 비롯하여 Azure AD와 연결된 클라우드 및 온-프레미스 애플리케이션에 액세스하는 macOS 디바이스에 대한 준수를 적용합니다. [Jamf 통합 설정](conditional-access-integrate-jamf.md) 및 [Jamf 관리 디바이스에 대해 준수 적용](conditional-access-assign-jamf.md)에 대해 자세히 알아보세요.

#### <a name="new-ios-device-action------1424701---"></a>새 iOS 디바이스 작업   <!-- 1424701 -->

이제 iOS 10.3 감독 디바이스를 종료할 수 있습니다. 이 작업을 수행하면 최종 사용자에게 경고하지 않고 디바이스가 즉시 종료됩니다. **디바이스** 워크로드에서 디바이스를 선택하면 디바이스 속성에서 **시스템 종료(감독 모드인 경우에만)** 작업을 찾을 수 있습니다.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Samsung Knox 디바이스의 날짜/시간 변경 허용 안 함 <!-- 1468103 -->

Samsung Knox 디바이스의 날짜 및 시간 변경을 차단할 수 있는 새로운 기능이 추가되었습니다. 이 기능은 **디바이스 구성 프로필** > **디바이스 제한 사항(Android)**  > **일반**에서 확인할 수 있습니다.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Surface Hub 리소스 계정 지원됨 <!-- 1566442  -->

관리자가 Surface Hub와 연결된 리소스 계정을 정의하고 업데이트할 수 있도록 새 디바이스 작업이 추가되었습니다.

리소스 계정은 Surface Hub에서 Skype/Exchange로 인증하는 데 사용되므로 모임에 참여할 수 있습니다. Surface Hub는 모임에서 회의실로 표시되도록 고유한 리소스 계정을 만들 수 있습니다. 예를 들어, 리소스 계정은 *회의실 B41/6233*으로 표시될 수 있습니다. Surface Hub의 리소스 계정(디바이스 계정이라고 함)은 일반적으로 회의실 위치에 대해 구성되고 다른 리소스 계정 매개 변수를 변경해야 할 경우 구성되어야 합니다.

관리자가 디바이스에서 리소스 계정을 업데이트하려는 경우 디바이스와 연결된 현재 Active Directory/Azure Active Directory 자격 증명을 제공해야 합니다. 디바이스에 대한 암호 순환이 켜져 있는 경우 관리자는 Azure Active Directory로 이동하여 암호를 찾아야 합니다.

> [!NOTE]
> 모든 필드는 번들로 전송되며 이전에 구성된 모든 필드를 덮어씁니다. 빈 필드도 기존 필드를 덮어씁니다.

설정 관리자가 다음을 구성할 수 있습니다.

- **리소스 계정**
   - **Active Directory 사용자**

      Domainname\username 또는 UPN(사용자 계정 이름): user@domainname.com

   - **암호**

- **선택적 리소스 계정 매개 변수**(지정된 리소스 계정을 사용하여 설정해야 함)

   - **암호 순환 기간**

     보안상의 이유로 Surface Hub에서 자동으로 계정 암호를 업데이트하도록 합니다. 이 옵션을 사용하도록 설정한 후에 매개 변수를 구성하려면 먼저 Azure Active Directory의 계정에서 암호를 재설정해야 합니다.

   - **SIP(Session Initiation Protocol) 주소**

     자동 검색이 실패할 경우에만 사용됩니다.

   - **전자 메일**

     디바이스/리소스 계정의 메일 주소입니다.

   - **Exchange Server**

     자동 검색이 실패할 경우에만 필요합니다.

   - **일정 동기화**

     일정 동기화 및 기타 Exchange Server 서비스를 사용할지 여부를 지정합니다. 예: 모임 동기화.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>macOS 디바이스에 Office 앱 설치 <!-- 1494311 -->
이제 macOS 디바이스에 Office 앱을 설치할 수 있습니다. 새 앱 유형을 사용하여 Word, Excel, PowerPoint, Outlook 및 OneNote를 설치할 수 있습니다. 또한 이러한 앱은 MAU(Microsoft 자동 업데이트)와 함께 제공되므로 앱을 안전하게 최신 상태로 유지할 수 있습니다.

### <a name="app-management"></a>앱 관리

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>iOS Volume Purchasing Program 토큰 삭제 <!-- 820879 -->
콘솔을 사용하여 iOS VPP(Volume-Purchase Program) 토큰을 삭제할 수 있습니다. VPP 토큰의 중복 인스턴스가 있는 경우 이 기능이 필요할 수 있습니다.

### <a name="intune-apps"></a>Intune 앱


### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>현재 사용자라는 새 엔터티 컬렉션은 현재 활성 사용자 데이터로 제한됨 <!-- 1667026 -->

**사용자** 엔터티 컬렉션에는 엔터프라이즈에서 할당된 라이선스를 가진 모든 Azure AD(Azure Active Directory) 사용자가 포함됩니다. 예를 들어, 사용자가 Intune에 추가된 다음 지난달 중에 제거되었을 수 있습니다. 보고 시점에는 이 사용자가 없지만 데이터에는 사용자와 상태가 있습니다. 데이터에 있는 사용자의 현재 상태 기록에 대한 기간을 보여 주는 보고서를 만들 수 있습니다.

이와 달리 새 **현재 사용자** 엔터티 컬렉션에는 제거되지 않은 사용자만 포함됩니다. **현재 사용자** 엔터티 컬렉션에는 현재 활성 사용자만 포함됩니다. **현재 사용자** 엔터티 컬렉션에 대한 자세한 내용은 [현재 사용자 엔터티에 대한 참조](reports-ref-current-user.md)를 참조하세요.


### <a name="updated-graph-apis----1736360---"></a>Graph API 업데이트됨 <!-- 1736360 -->

이 릴리스에서는 베타 상태인 몇 가지 Intune용 Graph API가 업데이트되었습니다. 자세한 내용은 월별 [Graph API 변경 로그](https://developer.microsoft.com/graph/docs/concepts/changelog)를 참조하세요.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune은 WIP(Windows Information Protection)가 거부된 앱을 지원합니다. <!-- 1479103 -->
Intune에서 거부된 앱을 지정할 수 있습니다. 앱이 거부되면 회사 정보에 액세스할 수 없도록 차단되므로 허용된 앱 목록의 반대가 됩니다. 자세한 내용은 [Windows Information Protection에 대한 권장 거부 목록](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)을 참조하세요.

<!-- ########################## -->
## <a name="november-2017"></a>2017년 11월

### <a name="troubleshoot-enrollment-issues-----746324---"></a>등록 문제 해결  <!-- 746324 -->

**문제 해결** 작업 영역에 이제 사용자 등록 문제가 표시됩니다. 문제 및 제안된 수정 단계에 대한 세부 정보를 통해 관리자 및 도움말 지원 센터 운영자가 문제를 해결할 수 있습니다. 특정 등록 문제는 캡처되지 않고 일부 오류에는 수정 제안이 없을 수 있습니다.

### <a name="group-assigned-enrollment-restrictions----747598---"></a>그룹 할당 등록 제한 <!-- 747598 -->

Intune 관리자가 이제 [사용자 그룹에 대한 사용자 지정 디바이스 유형 및 디바이스 수 등록 제한을 만들](enrollment-restrictions-set.md) 수 있습니다.

Intune Azure Portal에서 각 제한 유형의 인스턴스를 25개까지 만들 수 있으며 나중에 사용자 그룹에 할당할 수 있습니다. 그룹 할당 제한은 기본 제한을 재정의합니다.

제한 유형의 모든 인스턴스는 엄격하게 정렬된 목록으로 유지됩니다. 이 순서는 충돌 해결을 위한 우선 순위 값을 정의합니다. 둘 이상의 제한 인스턴스의 영향을 받는 사용자는 우선 순위가 가장 높은 값의 인스턴스에 의해서만 제한됩니다. 지정된 인스턴스의 우선 순위를 목록에서 다른 위치로 끌어서 변경할 수 있습니다.

이 기능은 Android for Work 설정이 Android for Work 등록 메뉴에서 등록 제한 메뉴로 마이그레이션되면서 릴리스될 예정입니다. 이 마이그레이션은 며칠이 걸릴 수 있으므로 계정이 11월 릴리스의 다른 일부로 업그레이드된 후에 등록 제한에서 그룹 할당을 사용할 수 있습니다.

### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>여러 NDES(네트워크 디바이스 등록 서비스) 커넥터에 대한 지원 <!-- 1528104 -->

NDES를 사용하면 도메인 자격 증명 없이 실행되는 모바일 디바이스에서 SCEP(단순 인증서 등록 프로토콜)를 기반으로 인증서를 가져올 수 있습니다.
이 업데이트를 통해 여러 NDES 커넥터가 지원됩니다.

### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android 디바이스와는 독립적으로 Android for Work 디바이스 관리 <!-- 1490731 EEready-->

Intune은 Android 플랫폼과는 독립적으로 Android for Work 디바이스의 등록 관리를 지원합니다. 이러한 설정은 **디바이스 등록** > **등록 제한** > **디바이스 유형 제한**에서 관리됩니다. (이전에는 **디바이스 등록** > **Android for Work 등록** > **Android for Work 등록 설정**에 있었음)

기본적으로 Android for Work 디바이스 설정은 Android 디바이스에 대한 설정과 동일합니다. 그러나 Android for Work 설정을 변경하면 달라집니다.

개인적인 Android for Work 등록을 차단하는 경우 회사 Android 디바이스만 Android for Work로 등록할 수 있습니다.

새 설정으로 작업할 때는 다음 사항을 고려합니다.

#### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>이전에 등록된 Android for Work 등록이 없는 경우

새 Android for Work 플랫폼이 기본 디바이스 유형 제한에서 차단됩니다. 기능을 등록한 후에 Android for Work로 등록하도록 디바이스를 허용할 수 있습니다. 이렇게 하려면 기본값을 변경하거나 기본 디바이스 유형 제한을 대체할 새 디바이스 유형 제한을 만듭니다.

#### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>등록된 Android for Work 등록이 있는 경우

이전에 등록한 경우 상황은 사용자가 선택한 설정에 따라 다릅니다.

| Setting | 기본 디바이스 유형 제한에서의 Android for Work 상태 | 참고 |
| --- | --- | --- |
| **모든 디바이스를 Android로 관리** | 차단 | 모든 Android 디바이스는 Android for Work 없이 등록해야 합니다. |
| **지원되는 디바이스를 Android for Work로 관리** | 허용됨 | Android for Work를 지원하는 모든 Android 디바이스는 Android for Work로 등록해야 합니다. |
| **이러한 그룹의 사용자만을 위해 지원되는 디바이스를 Android for Work로 관리** | 차단 | 기본값을 재정의하기 위해 별도 디바이스 유형 제한 정책이 만들어졌습니다. 이 정책은 Android for Work 등록을 허용하도록 이전에 선택한 그룹을 정의합니다. 선택된 그룹 내 사용자는 Android for Work 디바이스를 등록할 수 있도록 계속 허용됩니다. 다른 모든 사용자는 Android for Work 등록에 제한을 받습니다. |

모든 경우에 사용자의 의도한 규정이 유지됩니다. 사용자 환경에서 Android for Work의 전역 또는 그룹별 허용 한도를 유지하기 위한 별도의 작업은 필요하지 않습니다.

### <a name="google-play-protect-support-on-android----908720---"></a>Android에서 Google Play 보호 지원 <!-- 908720 -->

Android Oreo가 출시되면서 Google은 사용자와 조직이 보안 앱과 보안 Android 이미지를 실행할 수 있는 Google Play 보호라는 보안 기능 제품군을 소개합니다. 이제 Intune은 SafetyNet 원격 증명을 비롯하여 Google Play 보호 기능을 지원합니다. 관리자는 Google Play 보호를 구성하고 정상 상태를 유지하는 데 필요한 준수 정책 요구 사항을 설정할 수 있습니다.
**SafetyNet 디바이스 증명** 설정은 디바이스가 정상 상태이고 손상되지 않았음을 확인하기 위해 디바이스를 Google 서비스에 연결하도록 합니다. 또한 관리자는 Google Play 서비스에서 설치된 앱을 확인하도록 하기 위해 Android for Work에 대한 구성 프로필 설정을 설정할 수 있습니다. 디바이스가 Google Play 보호 요구 사항을 준수하지 않는 경우 조건부 액세스는 사용자가 회사 리소스에 액세스하는 것을 차단합니다.

- [Google Play 보호를 사용하도록 설정하기 위해 디바이스 준수 정책을 만드는 방법](https://docs.microsoft.com/intune/compliance-policy-create-android)을 알아봅니다.

### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>관리되는 앱에서 허용하는 텍스트 프로토콜 <!-- 1414050  -->

Intune 앱 SDK로 관리되는 앱에서 SMS 메시지를 보낼 수 있습니다.


### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>설치 보류 중 상태를 포함하도록 앱 설치 보고서 업데이트 <!-- 1249446 -->  

**클라이언트 앱**의 **앱** 목록을 통해 각 앱에 액세스할 수 있는 **앱 설치 상태** 보고서에 이제 사용자와 디바이스에 대한 **설치 보류 중** 수가 포함됩니다.

### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>모바일 위협 탐지를 위한 iOS 11 앱 인벤토리 API <!-- 1391759 -->

Intune은 개인 및 회사 소유 디바이스 모두에서 앱 인벤토리 정보를 수집하며 Lookout for Work와 같은 페치할 MTD(모바일 위협 검색) 공급자에서 사용할 수 있도록 합니다. iOS 11+ 디바이스의 사용자로부터 앱 인벤토리를 수집할 수 있습니다.

**앱 인벤토리**  
회사 소유의 iOS 11+ 및 개인적으로 소유한 디바이스 모두의 인벤토리가 사용자의 MTD 서비스 공급자에게 전송됩니다. 앱 인벤토리의 데이터에는 다음이 포함됩니다.

 - 앱 ID
 - 앱 버전
 - 앱 짧은 버전
 - 앱 이름
 - 앱 번들 크기
 - 앱 동적 크기
 - 앱의 유효성 검사 여부
 - 앱의 관리 여부

### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션 <!-- 1463747 wnready -->
새 프로세스와 도구를 사용하여 사용자와 해당 디바이스를 하이브리드 MDM에서 Azure Portal의 Intune으로 이동할 수 있으며, 다음과 같은 작업을 수행할 수 있습니다.
- Configuration Manager 콘솔에서 Azure Portal의 Intune으로 정책 및 프로필 복사
- Azure Portal의 Intune으로 사용자 하위 집합을 이동하고 나머지는 하이브리드 MDM에 유지
- 다시 등록할 필요 없이 Azure Portal의 Intune으로 디바이스 마이그레이션

자세한 내용은 [하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.

### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>온-프레미스 Exchange Connector 고가용성 지원  <!-- 676614 -->
이제 Exchange Connector가 지정된 CAS를 사용하여 Exchange에 연결한 후 다른 CAS를 검색할 수 있습니다. 기본 CAS를 사용할 수 없게 되면 커넥터는 기본 CAS를 사용할 수 있을 때까지 다른 CAS(사용 가능한 경우)로 장애 조치(failover)됩니다. 자세한 내용은 [온-프레미스 Exchange Connector 고가용성 지원](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)을 참조하세요.

### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS 디바이스를 원격으로 다시 시작(감독 모드만 해당) <!-- 1424595 -->

이제 디바이스 동작을 사용하여 다시 시작하도록 감독되는 iOS 10.3+ 디바이스를 트리거할 수 있습니다. 디바이스 다시 시작 동작 사용에 대한 자세한 내용은 [Intune으로 디바이스를 원격으로 다시 시작](device-restart.md)을 참조하세요.

> [!Note]
> 이 명령은 감독되는 디바이스 및 **디바이스 잠금** 액세스 권한에 필요합니다. 디바이스를 즉시 다시 시작합니다. 암호로 잠긴 iOS 디바이스는 다시 시작한 후 Wi-Fi 네트워크에 다시 가입되지 않습니다. 다시 시작한 후 서버와 통신하지 못할 수도 있습니다.

### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS을 위한 Single Sign-On 지원 <!-- 1333645 -->  

iOS 사용자에 대해 Single Sign-On을 사용할 수 있습니다. Single Sign On 페이로드에서 사용자 자격 증명을 검색하도록 코딩되는 iOS 앱은 이 페이로드 구성 업데이트로 작동합니다. 또한 UPN 및 Intune 디바이스 ID를 사용하여 사용자 이름 및 영역을 구성할 수 있습니다. 자세한 내용은 [iOS 디바이스 Single Sign-On용 Intune 구성](sso-ios.md)을 참조하세요.

### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>개인 디바이스를 위한 "내 iPhone 찾기" 추가 <!--1427287-->
이제 iOS 디바이스가 활성화 잠금이 설정되어 있는지 여부를 확인할 수 있습니다. 이전에 이 기능은 클래식 포털의 Intune에서 찾을 수 있었습니다.

### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Intune을 사용하여 관리되는 macOS 디바이스 원격 잠금 <!-- 1437691 -->

손실된 macOS 디바이스를 잠그고 6자리 복구 PIN을 설정할 수 있습니다. 잠기면 **디바이스 개요** 블레이드에 다른 디바이스 작업이 전송될 때까지 PIN이 표시됩니다.

자세한 내용은 [Intune을 사용하여 관리되는 디바이스 원격 잠금](device-remote-lock.md)을 참조하세요.

### <a name="new-scep-profile-details-supported----1559808---"></a>지원되는 새 SCEP 프로필 세부 정보 <!-- 1559808 -->

관리자는 Windows, iOS, macOS 및 Android 플랫폼에서 SCEP 프로필을 만들 때 추가 설정을 지정할 수 있습니다.  관리자는 IMEI, 일련 번호 또는 주체 이름 형식의 전자 메일을 포함한 일반 이름을 설정할 수 있습니다.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

### <a name="retain-data-during-a-factory-reset----1588489---"></a>출하 시 설정으로 리셋하는 동안 데이터 유지  <!--1588489 -->
Windows 10 버전 1709 이상을 출하 시 설정으로 재설정하면 새로운 기능을 사용할 수 있습니다. 관리자는 출하 시 설정으로 리셋하는 동안 디바이스 등록 및 프로비전된 기타 데이터를 디바이스에 보존할지 여부를 지정할 수 있습니다.

다음 데이터는 출하 시 설정으로 리셋되는 동안 유지됩니다.
- 디바이스와 연결된 사용자 계정
- 컴퓨터 상태(도메인 가입, Azure Active Directory 가입)
- MDM 등록
- OEM이 설치한 앱(저장소 및 Win32 앱)
- 사용자 프로필
- 사용자 프로필 외부의 사용자 데이터
- 사용자 자동 로그온

다음 데이터는 보존되지 않습니다.
- 사용자 파일
- 사용자가 설치한 앱(저장소 및 Win32 앱)
- 기본 설정 이외의 디바이스 설정


### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 업데이트 링 할당이 표시됩니다. <!-- 1621837 -->
확인 중인 사용자를 위해 **문제 해결** 중인 경우 모든 Windows 10 업데이트 링 할당을 확인할 수 있습니다.  

### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender Advanced Threat Protection 보고 주기 설정  <!-- 1455974  -->
WDATP(Windows Defender Advanced Threat Protection) 서비스를 사용하면 관리자가 관리되는 디바이스에 대한 보고 주기를 관리할 수 있습니다. 새 **원격 보고 빈도 가속화** 옵션을 사용하면 WDATP는 더 자주 데이터를 수집하고 위험을 평가합니다. 보고에 대한 기본값은 속도 및 성능을 최적화합니다. 보고 빈도를 늘리는 것은 위험 수준이 높은 디바이스에 유용할 수 있습니다. 이 설정은 **디바이스 구성**의 **Windows Defender ATP** 프로필에서 확인할 수 있습니다.

### <a name="audit-updates----1412961---"></a>감사 업데이트 <!-- 1412961 -->  
Intune 감사는 Intune과 관련된 변경 작업에 대한 레코드를 제공합니다.  모든 만들기, 업데이트, 삭제 및 원격 작업 조작은 캡처되고 1년 동안 보존됩니다.  Azure Portal은 각 워크로드에서 최근 30일 동안의 감사 데이터에 대한 뷰를 제공하며 필터링할 수 있습니다.  해당 Graph API를 사용하면 마지막 연도에 저장된 감사 데이터를 검색할 수 있습니다.

감사는 **모니터** 그룹에서 찾을 수 있습니다. 각 워크로드에 **감사 로그** 메뉴 항목이 있습니다.

### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS용 회사 포털 앱 사용 가능 <!--1541700-->
macOS용 Intune 회사 포털에는 사용자가 등록한 모든 디바이스에 필요한 모든 정보 및 준수 알림을 분명히 표시하도록 최적화된 업데이트된 환경이 있습니다. 또한 Intune 회사 포털이 디바이스에 배포된 후에 macOS용 Microsoft 자동 업데이트에서는 이에 대한 업데이트를 제공합니다. macOS 디바이스에서 Intune 회사 포털 웹 사이트에 로그인하여 새로운 macOS용 Intune 회사 포털을 다운로드할 수 있습니다.

### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner는 이제 승인된 앱의 MAM(모바일 앱 관리) 목록에 포함됩니다.  <!-- 1248473 -->
iOS 및 Android용 Microsoft Planner 앱은 이제 MAM(모바일 앱 관리)에 대한 승인된 앱에 포함됩니다. 모든 테넌트에 대해 Azure Portal의 Intune 앱 보호 블레이드를 통해 앱을 구성할 수 있습니다.
- [승인된 앱의 MAM 목록](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 자세히 알아보세요.

### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS 디바이스에 대한 앱당 VPN 요구 사항 업데이트 빈도   <!-- 1547061 -->  
관리자는 이제 iOS 디바이스의 앱에 대한 앱당 VPN 요구 사항을 제거할 수 있습니다. 일반적으로 15분 내에 수행되는 다음 Intune 체크 인 후에 디바이스에 영향을 줍니다.  

### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector용 System Center Operations Manager 관리 팩에 대한 지원 <!-- 885457 -->
Exchange Connector 로그를 구문 분석하는 데 도움이 되도록 이제 Exchange Connector용 System Center Operations Manager 관리 팩이 제공됩니다. 이렇게 하면 문제를 해결해야 할 때 서비스를 모니터링하는 여러 가지 방법이 있습니다.

### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 디바이스의 공동 관리  <!-- 1243445 -->
공동 관리는 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다. 기본적으로 공동 관리는 Windows 10 디바이스를 Configuration Manager와 Microsoft Intune에서 동시에 관리할 수 있는 솔루션입니다. 뿐만 아니라 AD(Active Directory) 및 Azure AD(Azure Active Directory)에 조인되됩니다.  이 구성을 통해 한 번에 경로로 이동할 수 없는 경우 조직에 적합한 속도로 시간이 지남에 따라 현대화하는 경로를 제공합니다.  

### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>OS 버전별 Windows 등록 제한 <!-- 245498 -->
Intune 관리자는 디바이스 등록을 위한 Windows 10의 최소 및 최대 버전을 지정할 수 있습니다. 이러한 제한은 **플랫폼 구성** 블레이드에서 설정할 수 있습니다.

Intune은 Windows 8.1 PC 및 Phone 등록을 계속 지원할 예정입니다. 하지만, Windows 10 버전만 최소 및 최대 제한을 설정할 수 있습니다. 8\.1 디바이스의 등록을 허용하려면 최소 한도를 비워 두십시오.

### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 할당되지 않은 디바이스에 대한 경고  <!-- 1631236 -->
Windows AutoPilot 할당되지 않은 디바이스에 대한 새 경고는 **Microsoft Intune** > **디바이스 등록** > **개요** 페이지에 제공됩니다. 이 경고에는 AutoPilot 배포 프로필이 할당되지 않는 AutoPilot 프로그램의 디바이스 수가 표시됩니다. 경고의 정보를 사용하여 프로필을 만들어서 할당되지 않은 디바이스에 할당하십시오. 경고를 클릭하면 Windows AutoPilot 디바이스의 전체 목록과 해당 디바이스에 대한 자세한 정보가 표시됩니다. 자세한 내용은 [Windows AutoPilot 배포 프로그램을 사용하여 Windows 디바이스 등록](https://docs.microsoft.com/intune/enrollment-autopilot)을 참조하세요.


### <a name="refresh-button-for-devices-list-------1333581---"></a>디바이스 목록의 새로 고침 단추    <!-- 1333581 -->
디바이스 목록이 자동으로 새로 고쳐지지 않으므로 새로운 새로 고침 단추를 사용하여 목록에 표시되는 디바이스를 업데이트할 수 있습니다.

### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec 클라우드 CA(인증 기관)에 대한 지원  <!-- 1333638 -->    
이제 Intune은 지원 Symantec 클라우드 CA 클라우드를 지원합니다. 이 기능을 사용하면 Intune 인증서 커넥터가 Symantec 클라우드 CA에서 Intune 관리 디바이스에 PKCS 인증서를 발급할 수 있습니다. Microsoft CA(인증 기관)에서 이미 Intune 인증서 커넥터를 사용하는 경우 기존 Intune 인증서 커넥터 설정을 활용하여 Symantec CA 지원을 추가할 수 있습니다.

### <a name="new-items-added-to-device-inventory-----1404455---"></a>디바이스 인벤토리에 추가된 새 항목   <!--1404455 -->
이제 다음과 같은 새 항목을 [등록된 디바이스에서 가져온 인벤토리](device-inventory.md)에 사용할 수 있습니다.

- Wi-Fi MAC 주소
- 총 스토리지 공간
- 사용 가능한 총 공간
- MEID
- 구독자의 통신사

### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>디바이스에 대한 최소 Android 보안 패치를 기준으로 앱에 대한 액세스 권한 설정<!-- 1278463 -->   
관리자는 관리되는 계정 아래에서 관리되는 애플리케이션에 대한 액세스 권한을 얻기 위해 디바이스에 설치해야 하는 최소 Android 보안 패치를 정의할 수 있습니다.

> [!Note]  
> 이 기능은 Android 6.0 이상 디바이스에서 Google에 의해 릴리스된 보안 패치만을 제한합니다.

### <a name="app-conditional-launch-support----1193313---"></a>앱 조건부 시작 지원 <!-- 1193313 -->
이제 IT 관리자는 Azure 관리 포털을 통해 요구 사항을 설정하여 애플리케이션을 시작하는 경우 MAM(모바일 앱 관리)를 통해 숫자 PIN이 아닌 암호를 적용할 수 있습니다. 항목이 구성되면 사용자는 MAM 지원 애플리케이션에 대한 액세스 권한을 가져오기 전에 메시지가 표시될 때 암호를 설정하고 사용해야 합니다. 암호는 하나 이상의 특수 문자 또는 대/소문자 알파벳을 포함한 숫자 PIN으로 정의됩니다. Intune의 이번 릴리스에서는 **iOS에서만** 이 기능을 활성화합니다. Intune은 숫자 PIN과 유사한 방식으로 암호를 지원합니다. 즉, 최소 길이를 설정하며 반복 문자 및 시퀀스를 허용합니다. 이 기능을 사용하려면 애플리케이션(즉, WXP, Outlook, Managed Browser, Yammer)에 참여하여 나중에 대상 애플리케이션에 적용할 암호 설정을 준비하기 위해 코드와 Intune 앱 SDK를 통합해야 합니다.

### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>디바이스 설치 상태 보고서에서 기간 업무의 앱 버전 번호 <!-- 1233999 -->
이 릴리스에서는 디바이스 설치 상태 보고서에 iOS 및 Android용 기간 업무 앱의 앱 버전 번호가 표시됩니다. 이 정보를 사용하여 앱 문제를 해결하거나 오래된 앱 버전을 실행하는 디바이스를 찾을 수 있습니다.

### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>이제 관리자는 디바이스 구성 프로필을 사용하여 디바이스에서 방화벽 설정을 구성할 수 있습니다. <!-- 951708 -->   
관리자는 디바이스에 방화벽을 설정하고, 도메인, 프라이빗 및 퍼블릭 네트워크에 다양한 프로토콜을 구성할 수도 있습니다.  이러한 방화벽 설정은 "Endpoint Protection" 프로필에서 찾을 수 있습니다.

### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard를 통해 조직에서 정의한 대로 신뢰할 수 없는 웹 사이트로부터 디바이스를 보호할 수 있습니다. <!-- 958257 -->   
관리자는 Windows Information Protection 워크플로 또는 디바이스 구성에서 새 "네트워크 경계" 프로필을 사용하여 사이트를 "신뢰할 수 있음" 또는 "협력"으로 정의할 수 있습니다. 64비트 Windows 10 디바이스의 신뢰할 수 있는 네트워크 경계에 나열되지 않은 사이트가 Microsoft Edge에 표시되는 경우 Hyper-V 가상 머신 내에서 브라우저를 대신 엽니다.

"Endpoint Protection" 프로필의 디바이스 구성 프로필에서 Application Guard를 찾을 수 있습니다. 여기에서부터 관리자는 가상화된 브라우저와 호스트 컴퓨터, 트러스트되지 않은 사이트와 신뢰할 수 있는 사이트 간에 상호 작용을 구성하고 가상화된 브라우저에서 생성된 데이터를 저장할 수 있습니다. 디바이스에서 Application Guard를 사용하려면 네트워크 경계를 먼저 구성해야 합니다. 디바이스에 네트워크 경계를 하나만 정의해야 합니다.  

### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise에서 Windows Defender 애플리케이션 제어는 인증된 앱만 신뢰하는 모드를 제공합니다. <!-- 1031096 -->    
수천 개의 새로운 악성 파일이 매일 생성되기 때문에 바이러스 백신 서명 기반 감지를 사용하여 맬웨어에 대항하는 방법은 더 이상 새로운 공격에 대한 적절한 방어를 제공할 수 없습니다. Windows 10 Enterprise에서 Windows Defender 애플리케이션 제어를 사용하면 디바이스 구성을 변경할 수 있습니다(변경 전: 앱을 바이러스 백신 또는 기타 보안 솔루션으로 차단하지 않으면 신뢰할 수 있는 모드, 변경 후: 운영 체제가 기업에서 권한을 부여한 앱만을 신뢰하는 모드). Windows Defender 애플리케이션 제어에서 앱에 트러스트를 할당합니다.

Intune을 사용하면 "감사 전용" 모드 또는 적용 모드에서 애플리케이션 제어 정책을 구성할 수 있습니다. 앱을 “감사 전용” 모드로 실행하면 차단되지 않습니다. "감사 전용" 모드는 로컬 클라이언트 로그에 있는 모든 이벤트를 기록합니다. Windows 구성 요소 및 Microsoft 스토어 앱만 실행할 수 있는지 아니면 Intelligent Security Graph에서 정의한 대로 평판이 좋은 추가 앱도 실행할 수 있는지 여부를 구성할 수 있습니다.

### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender Exploit Guard는 Windows 10의 새로운 침입 방지 기능 세트입니다. <!-- 1063615 -->   
dow Defender Exploit Guard는 애플리케이션의 악용 가능성을 줄이는 사용자 지정 규칙을 포함하고, 매크로 및 스크립트 위협을 방지하고, 평판이 좋지 않은 IP 주소에 대한 네트워크 연결을 자동으로 차단하고, 랜섬웨어 및 알 수 없는 위협으로부터 데이터를 보호할 수 있습니다. Windows Defender Exploit Guard는 다음과 같은 구성 요소로 구성됩니다.

- **공격 노출 영역 축소**는 매크로, 스크립트 및 이메일 위협을 방지할 수 있도록 하는 규칙을 제공합니다.
- **제어된 폴더 액세스**는 보호된 폴더의 콘텐츠에 대한 액세스를 자동으로 차단합니다.
- **네트워크 필터**는 앱에서 평판이 낮은 IP/도메인으로의 아웃바운드 연결을 차단합니다.
- **악용 보호**는 악용으로부터 애플리케이션을 보호하는 데 사용할 수 있는 메모리, 제어 흐름 및 정책 제한을 제공합니다.

### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Windows 10 디바이스를 위한 Intune에서의 PowerShell 스크립트 관리 <!-- 790537 -->

Intune 관리 확장을 사용하면 Windows 10 디바이스에서 실행되도록 Intune에서 PowerShell 스크립트를 업로드할 수 있습니다. 이 확장은 Windows 10 MDM(모바일 디바이스 관리) 기능을 보완하며 사용자가 최신 관리로 더 손쉽게 이행할 수 있도록 합니다. 자세한 내용은 [Windows 10 디바이스의 Intune에서 PowerShell 스크립트 관리](intune-management-extension.md)를 참조하세요.

### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10의 새 디바이스 제한 설정      <!-- 1308850 -->
-    메시지(모바일 전용) - 테스트 또는 MMS 메시지 사용 안 함
-    암호 - FIPS 사용하기 위한 설정 및 인증에 Windows Hello 보조 디바이스 사용 
-    표시 - 레거시 앱에 GDI Scaling 켜기 또는 끄기 설정

### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 키오스크 모드 디바이스 제한 <!-- 1308872 -->   
Windows 10 디바이스 사용자를 키오스크 모드로 제한하여 미리 정의된 앱의 집합으로 사용자를 제한할 수 있습니다.  이렇게 하려면 Windows 10 디바이스 제한 프로필을 만들고 키오스크 설정을 설정합니다.

키오스크 모드는 **단일 앱**(사용자가 하나의 앱을 실행하도록 허용) 또는 **다중 앱**(앱 집합에 대한 액세스 권한 허용)이라는 두 가지 모드를 지원합니다.  사용자 계정 및 디바이스 이름을 정의합니다. 여기서는 지원되는 앱을 결정합니다.  사용자는 정의된 앱에만 로그인할 수 있습니다.  자세한 내용은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 참조하세요. 

키오스크 모드에는 다음 항목이 필요합니다.

- Intune는 MDM 기관이어야 합니다.
- 앱은 이미 대상 디바이스에 설치되어 있어야 합니다.
- 디바이스는 [제대로 프로비전](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)되어야 합니다.

### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>네트워크 경계를 만들기 위한 새 디바이스 구성 프로필 <!-- 1311967 -->   
**네트워크 경계**라는 새 디바이스 구성 프로필은 다른 디바이스 구성 프로필을 통해 찾을 수 있습니다. 이 프로필을 사용하여 협력 및 신뢰할 수 있도록 하려는 온라인 리소스를 정의합니다. Windows Defender Application Guard 및 Windows Information Protection과 같은 기능을 디바이스에서 사용하기 *전에* 디바이스의 네트워크 경계를 정의해야 합니다. 각 디바이스에 네트워크 경계를 하나만 정의해야 합니다.

엔터프라이즈 클라우드 리소스, IP 주소 범위 및 내부 프록시 서버를 신뢰할 수 있다고 정의할 수 있습니다. 네트워크 경계를 정의하면 Windows Defender Application Guard 및 Windows Information Protection과 같은 다른 기능에서 사용할 수 있습니다.

###  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender Antivirus의 두 가지 추가 설정 <!-- 1338409 -->  
**파일 차단 수준**

| | |
|---|---|
| 구성되지 않음 | **구성되지 않음**에서는 기본 Windows Defender Antivirus 차단 수준을 사용하고 올바른 파일을 감지하는 위험을 늘리지 않고도 강력한 감지 기능을 제공합니다. |
| 높은 | **높음**은 강력한 검색 수준에 적용됩니다.
| 높음 +  | **높음 +** 은 클라이언트 성능에 영향을 줄 수 있는 추가 보호 수단으로 높음 수준을 제공합니다.
| 허용 오차 제로  | **허용 오차 제로**는 알 수 없는 실행 파일을 모두 차단합니다. |

가능성은 낮지만 **높음**으로 설정하면 올바른 파일 일부를 감지할 수도 있습니다.
파일 차단 수준을 기본인 **구성되지 않음**으로 설정하는 것이 좋습니다.

**클라우드에 의한 파일 검사의 제한 시간 확장**  

| | |
|--|--|
| 시간(초, 0~50) | Windows Defender Antivirus가 클라우드의 결과를 기다리는 동안 파일을 차단해야 하는 최대 시간을 지정합니다. 기본 시간은 10초입니다. 여기에서 지정된 추가 시간(최대 50초)은 해당 10초에 추가됩니다. 대부분의 경우에 검사는 최대값보다 훨씬 적은 시간이 걸립니다. 시간을 확장하면 클라우드가 의심스러운 파일을 철저하게 조사할 수 있습니다. 이 설정을 사용하고 추가로 적어도 20초를 지정하는 것이 좋습니다. |

### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 디바이스에 추가된 Citrix VPN <!-- 1512457 -->  
Windows 10 디바이스에 Citrix VPN을 구성할 수 있습니다. Windows 10 이상에 VPN을 구성하는 경우 **기본 VPN** 블레이드의 *연결 형식 선택* 목록에서 Citrix VPN을 선택할 수 있습니다.

> [!Note]
> iOS 및 Android용 Citrix 구성이 있습니다.

### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi 연결은 iOS에서 사전 공유 키를 지원합니다. <!-- 1550823 -->
고객이 iOS 디바이스의 WPA/WPA2 개인 연결에 PSK(미리 공유한 키)를 사용하도록 Wi-Fi 프로필을 구성할 수 있습니다. 이 프로필은 디바이스가 Intune에 등록될 때 사용자의 디바이스로 푸시됩니다.

프로필이 디바이스로 푸시되면 다음 단계는 프로필 구성에 따라 달라집니다.  자동으로 연결되도록 설정하면 다음에 네트워크가 필요할 때 자동으로 연결됩니다.  프로필이 수동 연결이면 사용자는 연결을 수동으로 활성화해야 합니다.  

### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>iOS의 관리되는 앱 로그에 액세스 <!-- 1469920 -->
관리되는 브라우저를 설치한 최종 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있고 관리된 iOS 앱 문제를 해결하도록 로그를 보낼 수 있습니다.

iOS 디바이스의 Managed Browser에서 문제 해결 모드를 사용하도록 설정하는 방법을 알아보려면 [iOS의 Managed Browser를 사용하여 관리되는 앱 로그에 액세스하는 방법](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)을 참조하세요.

### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>버전 2.9.0에 대한 iOS 회사 포털의 향상된 디바이스 설정 워크플로 기능 <!-- 1417174 -->

iOS용 회사 포털 앱에서 디바이스 설정 워크플로가 개선되었습니다. 언어는 더욱 친숙하게 변경되었으며, 최대한 화면을 결합했습니다. 전체 설정 텍스트에서 회사 이름을 사용하여 언어가 회사에 더욱 구체적으로 변경되었습니다. 이 업데이트된 워크플로는  [앱 UI의 새로운 기능 페이지](whats-new-app-ui.md)에서 확인할 수 있습니다.


### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>데이터 웨어하우스 데이터 모델의 마지막 사용자 데이터를 포함하는 사용자 엔터티 <!-- 1544273 -->
Intune 데이터 웨어하우스 데이터 모델의 첫 번째 버전에는 최신 과거 Intune 데이터만 포함되어 있습니다. 보고서 결정권자는 사용자의 현재 상태를 캡처할 수 없습니다. 이 업데이트에서 **사용자 엔터티**는 최신 사용자 데이터로 채워집니다.

<!-- ########################## -->
## <a name="october-2017"></a>2017년 10월

### <a name="ios-and-android-line-of-business-app-version-number-is-visible----1380712---"></a>iOS 및 Android 기간 업무 앱 버전 번호가 표시됩니다. <!-- 1380712 -->

Intune의 앱은 이제 iOS 및 Android 기간 업무 앱의 버전 번호를 표시합니다. 번호는 Azure Portal, 앱 목록 및 앱 개요 블레이드에 표시됩니다. 최종 사용자는 회사 포털 앱 및 웹 포털에서 앱 번호를 확인할 수 있습니다.

__전체 버전 번호__ 전체 버전 번호는 앱의 특정 릴리스를 식별합니다. 번호는 _버전_(_빌드_)으로 표시됩니다. 예: 2.2(2.2.17560800)

전체 버전 번호는 다음과 같은 두 구성 요소로 이루어져 있습니다.

 - **버전**  
   버전 번호는 사람이 읽을 수 있는 앱의 릴리스 번호입니다. 이는 최종 사용자가 앱의 다양한 릴리스를 식별하는 데 사용합니다.

 - **빌드 번호**  
    빌드 번호는 앱 검색에 사용하고 프로그래밍 방식으로 앱을 관리하기 위한 내부 번호입니다. 빌드 번호는 코드에서 변경 내용을 참조하는 앱의 반복을 가리킵니다.

[Microsoft Intune 앱 SDK 시작](app-sdk-get-started.md#line-of-business-app-version-numbers)에서 버전 번호 및 기간 업무 앱 개발에 대한 자세한 정보를 알아 보세요.

### <a name="device-and-app-management-integration----677972---"></a>디바이스 및 앱 관리 통합 <!-- 677972 -->   
이제 Azure Portal에서 Intune의 MDM(모바일 디바이스 관리) 및 MAM(모바일 애플리케이션 관리)에 모두 액세스할 수 있습니다. Intune은 애플리케이션 및 디바이스 관리와 관련된 IT 관리자 환경을 통합하기 시작했습니다. 이러한 변경 내용을 통해 디바이스 및 앱 관리 환경을 단순화할 수 있습니다.

[Intune 지원팀 블로그](https://blogs.technet.microsoft.com/intunesupport/2017/09/19/support-tip-setting-up-communication-between-mam-managed-and-mdm-managed-apps/)에서 발표된 MAM 및 MDM 변경 내용에 대해 자세히 알아봅니다.

### <a name="new-enrollment-alerts-for-apple-devices----1471790---"></a>Apple 디바이스를 위한 새 등록 경고 <!-- 1471790 -->
등록을 위한 개요 페이지에 Apple 디바이스 관리에 관한 IT 관리자용 유용한 경고가 표시됩니다. Apple MDM 푸시 인증서가 곧 만료되거나 이미 만료된 경우, 디바이스 등록 프로그램 토큰이 곧 만료되거나 이미 만료된 경우, 디바이스 등록 프로그램에 할당하지 않은 디바이스가 있는 경우 개요 페이지에 경고가 표시됩니다.

### <a name="support-token-replacement-for-app-configuration-without-device-enrollment----1080364---"></a>디바이스를 등록하지 않는 앱 구성을 위한 토큰 대체 지원 <!-- 1080364 -->

등록되지 않은 디바이스에서 앱에 대한 앱 구성에서 동적 값에 대한 토큰을 사용할 수 있습니다. 자세한 내용은 [디바이스 등록 없이 관리되는 앱용 앱 구성 정책 추가](app-configuration-policies-managed-app.md)를 참조하세요.

### <a name="updates-to-the-company-portal-app-for-windows-10---1299474--"></a>Windows 10용 회사 포털 앱에 대한 업데이트 <!--1299474-->
설정과 의도된 사용자 작업이 모든 설정에서 더욱 일관되도록 Windows 10용 회사 포털 앱의 설정 페이지가 업데이트되었습니다. 또한 다른 Windows 앱의 레이아웃과 일치하도록 업데이트되었습니다. [앱 UI 페이지의 새로운 기능](whats-new-app-ui.md) 페이지에서 이전 및 이후 이미지를 찾을 수 있습니다.

### <a name="inform-end-users-what-device-information-can-be-seen-for-windows-10-devices---1337920--"></a>Windows 10 디바이스에 대해 표시되는 디바이스 정보를 최종 사용자에게 알리기 <!--1337920-->
Windows 10용 회사 포털 앱에서 디바이스 세부 정보 화면에 **소유권 형식**을 추가했습니다. 그러면 이 페이지를 통해 Intune 최종 사용자 문서에서 직접 정책에 대한 자세한 내용을 찾아볼 수 있습니다. **정보** 화면에서도 이 정보를 찾을 수 있습니다.

### <a name="feedback-prompts-for-the-company-portal-app-for-android---1165249--"></a>Android용 회사 포털 앱의 피드백 프롬프트 <!--1165249-->
Android용 회사 포털 앱이 이제 최종 사용자 피드백을 요청합니다. 이 피드백은 Microsoft에 직접 전송되고 최종 사용자에게 공개 Google Play 스토어에서 앱을 검토할 기회를 제공합니다. 피드백이 필요하지 않으면 사용자가 계속 앱을 사용할 수 있도록 쉽게 해제할 수 있습니다.

<!-- #### Update to what device details an organization can see 1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources.-->

### <a name="helping-your-users-help-themselves-with-the-company-portal-app-for-android----1573324-1573150-1558616-1564878---"></a>Android용 회사 포털 앱을 사용하는 사용자가 스스로 해결책을 찾도록 지원 <!-- 1573324, 1573150, 1558616, 1564878 -->

사용자의 이해를 돕고 가능한 경우 새로운 사용 사례에서 자체적으로 해결할 수 있도록 최종 사용자를 위한 지침이 Android용 회사 포털 앱에 추가되었습니다.
- 최종 사용자는 추가가 허용된 최대 디바이스 수에 도달한 경우 디바이스를 제거하도록 [Azure Active Directory 포털](https://account.activedirectory.windowsazure.com/r/#/profile)로 안내됩니다.
- 최종 사용자에게는 [Samsung Knox 디바이스에서 활성화 오류 수정](https://go.microsoft.com/fwlink/?linkid=859718) 또는 [절전 모드 끄기](/intune-user-help/power-saving-mode-android)에 유용한 단계가 제공됩니다. 그러한 해결책이 문제를 해결하지 못하는 경우 [Microsoft에 로그를 제출](/intune-user-help/send-logs-to-microsoft-android)하는 방법에 대한 설명이 제공됩니다.

### <a name="new-resolve-action-available-for-android-devices----1583480---"></a>Android 디바이스에서 사용할 수 있는 새로운 '해결' 작업 <!-- 1583480 -->

Android용 회사 포털 앱은 _디바이스 설정 업데이트_ 페이지에서 ‘해결’ 작업을 소개하고 있습니다. 이 옵션을 선택하면 최종 사용자는 디바이스의 비호환 상태를 유발하는 설정으로 바로 이동할 수 있습니다. Android용 회사 포털 앱은 현재 이 작업을 [디바이스 암호](/intune-user-help/set-your-pin-or-password-android), [USB 디버깅](/intune-user-help/you-need-to-turn-off-usb-debugging-android)[알 수 없는 소스](/intune-user-help/you-need-to-turn-off-unknown-sources-android) 설정에 대해 지원합니다.

### <a name="device-setup-progress-indicator-in-android-company-portal----1565657---"></a>Android 회사 포털의 디바이스 설정 진행률 표시기 <!-- 1565657 -->
Android용 회사 포털 앱은 사용자가 디바이스를 등록하는 동안 디바이스 설정 진행률 표시기를 표시합니다. 이 표시기에는 “디바이스 설정 중...”부터 “디바이스 등록 중...”, “디바이스 등록 완료 중...”, “디바이스 설정 완료 중...”까지 차례로 새로운 상태가 표시됩니다.

### <a name="certificate-based-authentication-support-on-the-company-portal-for-ios---1029830--"></a>iOS용 회사 포털에서 인증서 기반 인증 지원 <!--1029830-->
iOS용 회사 포털 앱에서 CBA(인증서 기반 인증)에 대한 지원을 추가했습니다. CBA를 사용하는 사용자는 사용자 이름을 입력한 후 "인증서를 사용하여 로그인" 링크를 누릅니다. CBA는 이미 Android 및 Windows용 회사 포털 앱에서 지원되고 있습니다. [회사 포털 앱에 로그인](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) 페이지에서 자세히 알아볼 수 있습니다.

### <a name="apps-that-are-available-with-or-without-enrollment-can-now-be-installed-without-being-prompted-for-enrollment----1334712---"></a>등록을 하거나 등록을 하지 않고 사용할 수 있는 앱이 이제 등록을 묻는 메시지가 표시되지 않고 설치될 수 있습니다. <!-- 1334712 -->

Android 회사 포털 앱에서 등록을 하거나 등록을 하지 않고 사용할 수 있는 회사 앱이 등록을 묻는 메시지가 표시되지 않고 설치될 수 있습니다.

### <a name="windows-autopilot-deployment-program-support-in-microsoft-intune----747617---"></a>Microsoft Intune의 Windows AutoPilot Deployment 프로그램 지원  <!-- 747617  -->
이제 Windows AutoPilot Deployment 프로그램과 함께 Microsoft Intune을 사용하여 사용자가 IT를 수반하지 않고도 회사 디바이스를 프로비전할 수 있습니다. OOBE(첫 실행 경험)를 사용자 지정하고, 사용자가 디바이스를 Azure AD에 조인하고 Intune에 등록하도록 안내할 수 있습니다. Microsoft Intune 및 Windows AutoPilot을 함께 사용하면 운영 체제 이미지를 배포, 유지 및 관리할 필요가 없습니다. 자세한 내용은 [Windows AutoPilot Deployment 프로그램을 사용하여 Windows 디바이스 등록](https://docs.microsoft.com/intune/enrollment-autopilot)을 참조하세요.

### <a name="quickstart-for-device-enrollment----1425655---"></a>디바이스 등록에 대한 빠른 시작  <!-- 1425655 --> 
빠른 시작은 이제 **디바이스 등록**에서 사용할 수 있으며, 플랫폼 관리 및 등록 프로세스 구성에 대한 참조 테이블을 제공합니다. 각 항목에 대한 간략한 설명과 단계별 지침이 포함된 설명서에 대한 링크는 시작을 간소화하는 데 유용한 설명서를 제공합니다.

### <a name="device-categorization----1427491---"></a>디바이스 분류 <!-- 1427491 -->
**디바이스 &gt; 개요** 블레이드의 등록된 디바이스 플랫폼 차트는 Android, iOS, macOS, Windows 및 Windows Mobile을 포함하여 플랫폼별로 디바이스를 구성합니다.  다른 운영 체제를 실행하는 디바이스는 "기타"로 그룹화됩니다.  여기에는 Blackberry, NOKIA 및 기타 업체에서 제조하는 디바이스가 포함됩니다.  

테넌트에서 영향을 받는 디바이스를 알아보려면 **관리 &gt; 모든 디바이스**를 차례로 선택한 다음 **필터**를 사용하여 **OS** 필드를 제한합니다.

### <a name="zimperium---new-mobile-threat-defense-partner-----954681---"></a>Zimperium - 새 Mobile Threat Defense 파트너   <!-- 954681 -->  
Microsoft Intune과 통합되는 MTD(Mobile Threat Defense) 솔루션인 Zimperium에서 수행된 위험 평가에 기반하는 조건부 액세스를 사용하여 모바일 디바이스에서 회사 리소스에 대한 액세스를 제어할 수 있습니다.

#### <a name="how-integration-with-intune-works"></a>Intune과 통합하는 방법
위험은 Zimperium을 실행하는 디바이스에서 수집된 원격 분석에 따라 평가됩니다. Intune 디바이스 준수 정책을 통해 사용하도록 설정된 Zimperium 위험 평가에 따라 EMS 조건부 액세스 정책을 구성할 수 있습니다. 이 정책을 사용하여 회사 리소스에 액세스하는 미준수 디바이스를 감지된 위협에 따라 허용하거나 차단할 수 있습니다.

### <a name="new-settings-for-windows-10-device-restriction-profile------978575-1308849---"></a>Windows 10 디바이스 제한 프로필에 대한 새로운 설정  <!--- 978575, 1308849, -->  
Windows Defender SmartScreen 범주의 Windows 10 디바이스 제한 프로필에 새 설정을 추가합니다.

Windows 10 디바이스 제한 프로필에 대한 세부 정보는 [Windows 10 이상 디바이스 제한 설정]( device-restrictions-windows-10.md)을 참조하세요.

### <a name="remote-support-for-windows-and-windows-mobile-devices-----1070473---"></a>Windows 및 Windows Mobile 디바이스에 대한 원격 지원   <!-- 1070473 -->  
Intune에서 이제 [TeamViewer](https://www.teamviewer.com) 소프트웨어(별매)를 사용하여 Windows 및 Windows Mobile 디바이스를 실행하는 사용자에게 원격 지원을 제공할 수 있습니다.

### <a name="scan-devices-with-windows-defender----1280988-1280990---"></a>Windows Defender로 디바이스 검사 <!-- 1280988  1280990   -->
관리되는 Windows 10 디바이스에서 이제 Windows Defender 바이러스 백신을 사용하여 **빠른 검사**, **전체 검사** 및 **서명 업데이트**를 실행할 수 있습니다. 디바이스의 개요 블레이드에서 디바이스에서 실행할 작업을 선택합니다. 명령을 디바이스로 전송하기 전에 작업을 확인하는 메시지가 표시됩니다. 

**빠른 검사**: 빠른 검사는 레지스트리 키 및 알려진 Windows 시작 폴더처럼 맬웨어 레지스터가 시작하는 위치를 검사합니다. 빠른 검사에는 평균 5분이 걸립니다. 파일을 열고 닫을 때와 사용자가 폴더를 탐색할 때마다 파일을 검사하는 **항상 실시간 보호** 설정과 결합된 빠른 검사는 시스템이나 커널에 있을 수 있는 맬웨어로부터 보호합니다. 검사가 완료되면 디바이스에 검사 결과가 표시됩니다. 

**전체 검사**: 전체 검사는 맬웨어 위협이 발생한 디바이스에서 더 철저한 정리가 필요한 비활성 구성 요소가 있는지 확인할 때 유용할 수 있으며, 주문형 검사 실행에 유용합니다. 전체 검사는 실행하는 데 1시간이 걸릴 수 있습니다. 검사가 완료되면 디바이스에 검사 결과가 표시됩니다. 

**서명 업데이트**: 서명 업데이트 명령은 Windows Defender 바이러스 백신 맬웨어 정의 및 서명을 업데이트합니다. 이렇게 하면 Windows Defender 바이러스 백신에서 맬웨어를 검색하는 데 효과적입니다. 이 기능은 디바이스 인터넷 연결을 기다리는 Windows 10 디바이스 전용입니다. 

### <a name="the-enabledisable-button-is-removed-from-the-intune-certificate-authority-page-of-the-intune-azure-portal-----1400455---"></a>Intune Azure Portal의 Intune 인증 기관 페이지에서 설정/해제 단추 제거  <!-- 1400455 -->
 Intune에서 인증서 커넥터를 설정하는 추가 단계를 제거하고 있습니다. 현재 인증서 커넥터를 다운로드한 다음 Intune 콘솔에서 이를 사용하도록 설정합니다. 그러나 Intune 콘솔에서 커넥터를 사용하지 않도록 설정하더라도 커넥터에서 인증서를 계속 발급합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
설정/해제 단추는 10월부터 Azure Portal의 인증 기관 페이지에서 표시되지 않습니다. 커넥터 기능은 동일하게 그대로 유지됩니다. Intune에서 등록한 디바이스에는 인증서가 여전히 배포됩니다. 인증서 커넥터는 계속 다운로드하여 설치할 수 있습니다. 인증서 발급을 중지하려면 이제 인증서 커넥터를 사용하지 않도록 설정하는 대신 제거합니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
현재 인증서 커넥터를 사용할 수 없도록 설정되어 있으면 제거해야 합니다.

### <a name="new-settings-for-windows-10-team-device-restriction-profile-------1308838---"></a>Windows 10 Team 디바이스 제한 프로필에 대한 새로운 설정   <!--- 1308838 -->
이 릴리스에서는 Surface Hub 디바이스를 제어할 수 있도록 Windows 10 Team 디바이스 제한 프로필에 많은 새로운 설정을 추가했습니다.

이 프로필에 대한 자세한 내용은 [Windows 10 Team 디바이스 제한 설정](device-restrictions-windows-10-teams.md)을 참조하세요.

### <a name="prevent-users-of-android-devices-from-changing-their-device-date-and-time----1333292---"></a>Android 디바이스 사용자가 디바이스 날짜 및 시간을 변경하지 못하도록 방지  <!-- 1333292 -->
[Android 사용자 지정 디바이스 정책](custom-settings-android.md)을 사용하여 Android 디바이스 사용자가 디바이스 날짜 및 시간을 변경하지 못하도록 할 수 있습니다.

그렇게 하려면 URI ./Vendor/MSFT/PolicyManager/My/System/AllowDateTimeChange를**TRUE**로 설정하여 Android 사용자 지정 정책을 구성한 다음 필요한 그룹에 할당합니다.

### <a name="bitlocker-device-configuration---1397398---"></a>BitLocker 디바이스 구성 <!-- 1397398 -->
**Windows 암호화 &gt; 기본 설정**에는 사용자의 디바이스에서 사용될 수 있는 다른 디스크 암호화에 대해 [경고 메시지](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp#allowarningforotherdiskencryption)를 사용하지 않도록 설정할 수 있는 **다른 디스크 암호화에 대한 경고** 설정이 새로 포함되었습니다.  경고 메시지는 디바이스에 BitLocker를 설정하기 전에 최종 사용자 동의가 필요하며 최종 사용자가 확인할 때까지 BitLocker 설정이 차단됩니다.  새 설정을 통해 최종 사용자 경고를 사용하지 않도록 할 수 있습니다.


### <a name="volume-purchase-program-for-business-apps-will-now-sync-to-your-intune-tenant----800882---"></a>Intune 테넌트로 동기화되는 비즈니스용 Volume Purchase Program 앱 <!-- 800882 -->  
타사 개발자가 앱을 iTunes Connect에서 지정한 권한 있는 비즈니스용 VPP(Volume Purchase Program) 구성원에 프라이빗으로 배포할 수 있습니다. 이러한 VPP for Business 멤버는 Volume Purchase Program 앱 스토어에 로그인하고 해당 앱을 구입할 수 있습니다.

이 릴리스에서는 이제 최종 사용자가 구매한 비즈니스용 VPP 앱이 Intune 테넌트로 동기화됩니다.

### <a name="select-apple-country-store-to-sync-vpp-apps-----1332311---"></a>Apple 국가 스토어를 선택하여 VPP 앱 동기화  <!-- 1332311 -->  
VPP 토큰을 업로드할 때 VPP(Volume Purchase Program) 국가 스토어를 구성할 수 있습니다. Intune은 지정된 VPP 국가 스토어의 모든 로캘에 대해 VPP 앱을 동기화합니다.

> [!NOTE]  
> 현재 Intune은 Intune 테넌트가 생성된 Intune 로캘과 일치하는 VPP 국가 스토어의 VPP 앱만 동기화합니다.


### <a name="block-copy-and-paste-between-work-and-personal-profiles-in-android-for-work----1098994---"></a>Android for Work에서 회사 및 개인 프로필 간의 복사 및 붙여넣기 차단 <!-- 1098994 -->
이 릴리스에서는 Android for Work에 대한 회사 프로필을 구성하여 회사와 개인 앱 간에 복사 및 붙여넣기를 차단할 수 있습니다. **회사 프로필 설정**의 **Android for Work** 플랫폼에 대한 **디바이스 제한** 프로필에서 이 새 설정을 찾을 수 있습니다.

### <a name="create-ios-apps-limited-to-specific-regional-apple-app-stores----1281692---"></a>특정 지역 Apple 앱 스토어로 제한된 iOS 앱 만들기 <!-- 1281692 -->
Apple 앱 스토어 관리되는 앱을 만드는 동안 국가 로캘을 지정할 수 있습니다.

> [!Note]  
> 현재 미국 국가별 스토어에 있는 Apple 앱 스토어 관리되는 앱만 만들 수 있습니다.

###  <a name="update-ios-vpp-user-and-device-licensed-apps-----1305564---"></a>iOS VPP 사용자 및 디바이스 라이선스 앱 업데이트  <!-- 1305564 -->  
iOS VPP 토큰을 구성하여 Intune 서비스를 통해 해당 토큰에 대해 구입한 모든 앱을 업데이트할 수 있습니다. Intune은 앱 스토어 내의 VPP 앱 업데이트를 검색하고 디바이스가 체크 인하면 자동으로 디바이스에 푸시합니다.

VPP 토큰을 설정하고 자동 업데이트를 사용하도록 설정하는 단계는 [Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법] (/intune/vpp-apps-ios)을 참조하세요.


### <a name="user-device-association-entity-collection-added-to-intune-data-warehouse-data-model----1187917---"></a>Intune Data Warehouse 데이터 모델에 추가된 사용자 디바이스 연결 엔터티 컬렉션 <!-- 1187917 -->
이제 사용자와 디바이스 엔터티 컬렉션을 연결하는 사용자 디바이스 연결 정보를 사용하여 보고서 및 데이터 시각화를 작성할 수 있습니다. 데이터 모델은 데이터 웨어하우스 Intune 페이지에서 검색한 Power BI 파일(PBIX)이나 OData 엔드포인트를 통해 액세스하거나 사용자 지정 클라이언트를 개발하여 액세스할 수 있습니다.

### <a name="review-policy-compliance-for-windows-10-update-rings----1067886---"></a>Windows 10 업데이트 링에 대한 정책 규정 준수 검토 <!-- 1067886 -->
소프트웨어 업데이트 > 업데이트 링 배포 상태별에서 Windows 10 업데이트 링에 대한 정책 보고서를 검토할 수 있습니다. 정책 보고서에는 구성한 업데이트 링에 대한 배포 상태가 포함됩니다. 

### <a name="new-report-that-lists-ios-devices-with-older-ios-versions----1352223---"></a>이전 iOS 버전을 사용하는 iOS 디바이스를 나열하는 새 보고서   <!-- 1352223 -->
**오래된 iOS 디바이스** 보고서는 **소프트웨어 업데이트** 작업 영역에서 사용할 수 있습니다. iOS 업데이트 정책에서 대상으로 지정했으며 업데이트가 사용 가능한 감독된 iOS 디바이스 목록이 보고서에 표시됩니다. 디바이스가 자동으로 업데이트되지 않은 이유를 나타내는 각 디바이스의 상태를 볼 수 있습니다. 

### <a name="view-app-protection-policy-assignments-for-troubleshooting----1475003---"></a>문제 해결을 위해 앱 보호 정책 할당 보기 <!--  1475003 -->
이 예정된 릴리스에서는 **앱 보호 정책** 옵션이 문제 해결 블레이드에서 사용할 수 있는 **할당** 드롭다운 목록에 추가됩니다. 이제 앱 보호 정책을 선택하여 선택한 사용자에게 할당된 앱 보호 정책을 확인할 수 있습니다.



### <a name="improvements-to-device-setup-workflow-in-company-portal---1490692--"></a>회사 포털의 향상된 디바이스 설정 워크플로 기능 <!--1490692-->
Android용 회사 포털 앱에서 디바이스 설치 워크플로를 개선했습니다. 언어는 귀사를 위해 더욱 친숙하고 구체적으로 변경되었으며, 최대한 화면을 결합했습니다. 이러한 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md#week-of-october-2-2017) 페이지에서 확인할 수 있습니다.

### <a name="improved-guidance-around-the-request-for-access-to-contacts-on-android-devices---1484985--"></a>Android 디바이스에서 연락처 액세스 요청에 대한 지침 개선 <!--1484985-->

Android용 회사 포털 앱은 최종 사용자가 연락처 사용 권한을 허용하도록 해야 합니다. 최종 사용자가 이 액세스 권한을 거절하는 경우 조건부 액세스에 대한 권한을 부여한다고 경고하는 앱 내 알림이 표시됩니다. 

### <a name="secure-startup-remediation-for-android---1490712--"></a>Android용 시작 업데이트 관리 보호 <!--1490712-->

Android 디바이스를 가진 최종 사용자는 회사 포털 앱에서 비준수 이유를 누를 수 있습니다 가능하면 문제를 해결하기 위해 설정 앱의 올바른 위치로 직접 이동시킵니다. 

### <a name="additional-push-notifications-for-end-users-on-the-company-portal-app-for-android-oreo---1475932--"></a>Android Oreo용 회사 포털 앱에서 최종 사용자를 위한 추가 푸시 알림 <!--1475932-->

최종 사용자는 Android Oreo용 회사 포털 앱에서 Intune 서비스로부터 정책을 검색하는 것과 같은 백그라운드 작업을 수행할 때 이를 나타내는 추가 알림을 받게 됩니다. 그러면 회사 포털이 해당 디바이스에서 관리 작업을 수행할 때 최종 사용자에 대한 투명도가 증가합니다. 이는 Android Oreo용 회사 포털 앱에 대한 [회사 포털 UI 최적화](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) 전체의 일부입니다. 

Android Oreo에서 설정된 새로운 UI 요소를 추가로 최적화합니다.  최종 사용자는 회사 포털이 Intune 서비스로부터 정책을 검색하는 등 백그라운드 작업을 수행하는 시기를 나타내는 추가 알림을 받게 됩니다.  그러면 회사 포털이 해당 디바이스에서 관리 작업을 수행할 때 최종 사용자에 대한 투명도가 증가합니다.

### <a name="new-behaviors-for-the-company-portal-app-for-android-with-work-profiles----1485783---"></a>회사 프로필을 사용하는 Android용 회사 포털 앱의 새로운 동작 <!-- 1485783 -->

회사 프로필을 사용하여 Android for Work 디바이스를 등록하면 회사 프로필의 회사 포털 앱이 디바이스에서 관리 작업을 수행합니다. 

개인 프로필에서 MAM 지원 앱을 사용하는 경우가 아니면 Android용 회사 포털 앱은 더 이상 사용되지 않습니다. 회사 프로필 환경을 향상하기 위해 Intune이 회사 프로필을 등록한 후 개인 회사 포털 앱을 자동으로 숨깁니다.

Android용 회사 포털 앱은 [Play 스토어에서 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)을 검색하고 **사용**을 탭하여 개인 프로필에서 언제든지 사용할 수 있습니다.

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode---1428681--"></a>Windows 8.1 및 Windows Phone 8.1용 회사 포털이 지속 모드로 전환 <!--1428681-->

2017년 10월부터 Windows 8.1 및 Windows Phone 8.1용 회사 포털 앱이 유지 모드로 전환됩니다. 앱과 등록 및 준수 같은 기존 시나리오가 이러한 플랫폼에서 계속 지원된다는 뜻입니다. 이러한 앱은 Microsoft 스토어 같은 기존 릴리스 채널을 통해 계속 다운로드할 수 있습니다. 

유지 모드가 되면 이러한 앱은 중요 보안 업데이트만 수신합니다. 이러한 앱에 대해 릴리스되는 추가 업데이트 또는 기능은 없습니다. 새 기능의 경우 디바이스를 Windows 10 또는 Windows 10 Mobile로 업데이트하는 것이 좋습니다. 


### <a name="block-unsupported-samsung-knox-device-enrollment----1490695---"></a>지원되지 않는 Samsung Knox 디바이스 등록 차단  <!-- 1490695 -->

회사 포털 앱은 지원되는 Samsung KNOX 디바이스만을 등록하려고 합니다. Knox 활성화 오류로 인해 MDM 등록이 차단되는 경우를 방지하기 위해 디바이스가 [Samsung에서 게시한 디바이스 목록](https://www.samsungknox.com/knox-supported-devices/knox-workspace)에 나타나는 경우에만 디바이스 등록을 시도합니다. 모든 Samsung 디바이스에 Knox를 지원하는 모델 번호가 있는 것은 아닙니다. 구매하고 배포하기 전에 디바이스 재판매인과 함께 KNOX 호환성을 검사합니다. [Android 및 Samsung Knox Standard 정책 설정](supported-devices-browsers.md#intune-supported-web-browsers)에서 확인된 디바이스의 전체 목록을 찾을 수 있습니다.

### <a name="end-of-support-for-android-43-and-lower----1171126-1326920---"></a>Android 4.3 이하에 대한 지원 종료 <!-- 1171126, 1326920 -->
관리되는 앱과 Android용 회사 포털 앱이 회사 리소스에 액세스하려면 Android 4.4 이상이 필요합니다. 12월까지 등록된 모든 디바이스는 12월에 강제 사용 중지되며, 따라서 회사 리소스에 액세스할 수 없게 됩니다. MDM 없이 앱 보호 정책을 사용 중인 경우 앱이 업데이트를 받지 못하며 해당 환경 품질이 시간이 흐름에 따라 저하됩니다.

### <a name="inform-end-users-what-device-information-can-be-seen-on-enrolled-devices---1165314--"></a>등록된 디바이스에 표시되는 디바이스 정보를 최종 사용자에게 알리기 <!--1165314-->
모든 회사 포털 앱의 디바이스 세부 정보 화면에 **소유권 형식**을 추가합니다. 그러면 [회사가 볼 수 있는 정보는 무엇인가요?](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) 문서에서 직접 개인 정보에 대한 자세한 내용을 찾아볼 수 있습니다. 이 기능은 나중에 모든 회사 포털 앱에 롤아웃될 예정입니다. [9월](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)에 iOS에서 이 기능을 발표했습니다.

<!-- ########################## -->
## <a name="september-2017"></a>2017년 9월

### <a name="intune-supports-ios-11---1428975--"></a>Intune은 iOS 11을 지원합니다. <!--1428975-->
Intune은 iOS 11을 지원합니다. [Intune 지원 블로그](https://blogs.technet.microsoft.com/intunesupport/2017/09/12/support-tip-intune-support-for-ios-11/)에서 이전에 발표되었습니다.

### <a name="end-of-support-for-ios-80----1164477---"></a>iOS 8.0에 대한 지원 종료 <!-- 1164477 -->
관리되는 앱 및 iOS용 회사 포털 앱이 회사 리소스에 액세스하려면 iOS 9.0 이상이 필요합니다. 올해 9월 이전에 업데이트되지 않은 디바이스는 회사 포털 또는 해당 앱에 더 이상 액세스할 수 없게 됩니다. 

### <a name="refresh-action-added-to-the-company-portal-app-for-windows-10---1132468--"></a>Windows 10용 회사 포털 앱에 추가된 새로 고침 작업 <!--1132468-->
사용자는 Windows 10용 회사 포털 앱을 사용하여 새로 고침으로 끌어오거나 데스크톱에서 F5 키를 눌러서 앱에서 데이터를 새로 고칠 수 있습니다.

### <a name="inform-end-users-what-device-information-can-be-seen-for-ios---739894--"></a>iOS에 대해 표시되는 디바이스 정보를 최종 사용자에게 알리기 <!--739894-->

iOS용 회사 포털 앱에서 디바이스 세부 정보 화면에 **소유권 형식**을 추가했습니다. 그러면 이 페이지를 통해 Intune 최종 사용자 문서에서 직접 정책에 대한 자세한 내용을 찾아볼 수 있습니다. 정보 화면에서도 이 정보를 찾을 수 있습니다.

### <a name="allow-end-users-to-access-the-company-portal-app-for-android-without-enrollment----1169910---"></a>최종 사용자가 등록 없이 Android용 회사 포털 앱에 액세스하도록 허용 <!---1169910--->

머지 않아 최종 사용자가 디바이스를 등록하지 않고도 Android용 회사 포털 앱에 액세스할 수 있게 됩니다. 앱 보호 정책을 사용하는 조직의 최종 사용자는 회사 포털 앱을 열 때 디바이스를 등록하라는 메시지를 더 이상 받지 않습니다. 최종 사용자가 디바이스를 등록하지 않고 회사 포털에서 앱을 설치할 수도 있습니다. 


### <a name="easier-to-understand-phrasing-for-the-company-portal-app-for-android----1396349---"></a>Android용 회사 포털 앱의 구문을 쉽게 이해 <!---1396349--->  

최종 사용자가 쉽게 등록할 수 있도록 새로운 텍스트가 포함되어 Android용 회사 포털 앱의 등록 프로세스가 간소화되었습니다. 사용자 지정 등록 설명서가 있는 경우 새 화면을 반영하도록 업데이트할 수 있습니다. [Intune에 대한 UI 업데이트 및 최종 사용자 앱](whats-new-app-ui.md#week-of-september-11-2017) 페이지에서 샘플 이미지를 찾을 수 있습니다.

### <a name="windows-10-company-portal-app-added-to-windows-information-protection-allow-policy----677129---"></a>Windows Information Protection 허용 정책에 추가된 Windows 10 회사 포털 앱 <!-- 677129 -->

Windows 10 회사 포털 앱이 WIP(Windows Information Protection)를 지원하도록 업데이트되었습니다. WIP 허용 정책에 앱을 추가할 수 있습니다. 이러한 변경으로 이제 앱을 **제외** 목록에 추가하지 않아도 됩니다.


<!-- ########################## -->
## <a name="august-2017"></a>2017년 8월

### <a name="improvements-to-device-overview----1404453---"></a>디바이스 개요의 향상된 기능 <!-- 1404453 -->  
디바이스 개요의 향상된 기능에 이제 등록된 디바이스가 표시되지만 Exchange ActiveSync에서 관리하는 디바이스는 제외됩니다. Exchange ActiveSync 디바이스에는 등록된 디바이스와 동일한 관리 옵션이 없습니다. Azure Portal에서 Intune에 등록된 디바이스 수 및 플랫폼별 등록된 디바이스 수를 보려면 **디바이스** > **개요**로 이동합니다.

### <a name="improvements-to-device-inventory-collected-by-intune"></a>Intune에서 수집하는 디바이스 인벤토리의 향상된 기능
<!-- 961134, 1104426, 1281327, 1333543 -->
이 릴리스에서는 관리하는 디바이스에서 수집하는 인벤토리에 대해 다음과 같은 기능이 향상되었습니다.
 
-   Android 디바이스의 경우, 각 디바이스에 대한 최신 패치 수준을 표시하는 디바이스 인벤토리에 이제 열을 추가할 수 있습니다. 확인하려면 디바이스 목록에 **보안 패치 수준** 열을 추가합니다.
-   디바이스 보기를 필터링할 때 이제 등록 날짜별로 디바이스를 필터링할 수 있습니다. 예를 들어 지정한 날짜 후에 등록한 디바이스만 표시할 수 있습니다.
-   **Last Check-in Date**(마지막 체크인 날짜) 항목에서 사용하는 필터가 향상되었습니다.
-   디바이스 목록에서 이제 회사 소유 디바이스의 전화 번호를 표시할 수 있습니다.
또한 필터 창을 사용하여 전화 번호로 디바이스를 검색할 수 있습니다.

디바이스 인벤토리에 대한 자세한 내용은 [Intune 디바이스 인벤토리를 확인하는 방법](device-inventory.md)을 참조하세요.

### <a name="conditional-access-support-for-macos-devices"></a>macOS 디바이스에 대한 조건부 액세스 지원 
<!-- 720172 -->
이제 Mac 디바이스를 Intune에 등록하고 해당 디바이스 준수 정책을 준수하도록 요구하는 조건부 액세스 정책을 설정할 수 있습니다. 예를 들어 사용자가 macOS용 Intune 회사 포털 앱을 다운로드하고 해당 Mac 디바이스를 Intune에 등록할 수 있습니다. Intune은 Mac 디바이스가 PIN, 암호화, OS 버전, 시스템 무결성 등의 요구 사항을 준수하는지 여부를 평가합니다.

- [macOS 디바이스에 대한 조건부 액세스 지원](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)에 대해 알아보세요.

### <a name="company-portal-app-for-macos-is-in-public-preview----1484796---"></a>macOS용 회사 포털 앱이 공개 미리 보기에서 제공됩니다. <!---1484796--->
macOS용 회사 포털 앱이 지금 Enterprise Mobility + Security의 조건부 액세스에 대한 공개 미리 보기의 일부로 제공됩니다. 이 릴리스에서는 macOS 10.11 이상을 지원합니다. [https://aka.ms/macOScompanyportal](https://aka.ms/macOScompanyportal)에 가져옵니다. 


### <a name="new-device-restriction-settings-for-windows-10"></a>Windows 10의 새 디바이스 제한 설정    
<!--1063965, 1308850  -->
이 릴리스에서는 [Windows 10 디바이스 제한 프로필](/intune/device-restrictions-windows-10)에 대한 새로운 설정이 다음 범주에 추가되었습니다.

-   Windows Defender SmartScreen
-   앱 스토어

### <a name="updates-to-the-windows-10-endpoint-protection-device-profile-for-bitlocker-settings"></a>BitLocker 설정에 대한 Windows 10 Endpoint Protection 디바이스 프로필 업데이트
<!--1459533 -->     이 릴리스에서는 Windows 10 Endpoint Protection 디바이스 프로필에서 BitLocker 설정을 적용하는 방법에 대해 다음과 같은 기능이 향상되었습니다.
 
-   **Bitlocker OS 드라이브 설정** 아래의 **호환되지 않는 TPM 칩과 BitLocker** 설정의 경우 **차단**을 선택하면 이전에는 BitLocker가 실제로는 허용되었습니다. 이제 [차단]을 선택하면 BitLocker를 차단하도록 이 문제를 해결했습니다.
-   **Bitlocker OS 드라이브 설정** 아래의 **인증서 기반 데이터 복구 에이전트** 설정의 경우 이제 인증서 기반 데이터 복구 에이전트를 분명히 차단할 수 있습니다. 그러나 기본적으로 에이전트는 허용됩니다.
-   **Bitlocker 고정 데이터 드라이브 설정**아래의 **데이터 복구 에이전트** 설정의 경우 이제 데이터 복구 에이전트를 분명히 차단할 수 있습니다.
자세한 내용은 [Windows 10에 대한 Endpoint Protection 설정](endpoint-protection-windows-10.md)을 참조하세요.


### <a name="new-signed-in-experience-for-android-company-portal-users-and-app-protection-policy-users----621669---"></a>Android 회사 포털 사용자와 앱 보호 정책 사용자의 새로 로그인된 환경 <!-- 621669 -->
이제 최종 사용자가 Android 디바이스를 등록하지 않고 Android 회사 포털 앱을 사용하여 앱을 찾아보고, 디바이스를 관리하며, IT 연락처 정보를 볼 수 있습니다. 또한 최종 사용자가 이미 Intune 앱 보호 정책을 통해 보호된 앱을 사용하고, Android 회사 포털을 시작하는 경우 최종 사용자에게 더 이상 디바이스를 등록하라는 메시지가 표시되지 않습니다.

### <a name="new-setting-in-the-android-company-portal-app-to-toggle-battery-optimization---1405990--"></a>배터리 최적화를 전환하는 Android 회사 포털 앱의 새 설정 <!--1405990-->
Android용 회사 포털 앱의 **설정** 페이지에는 사용자가 회사 포털 및 Microsoft Authenticator 앱의 배터리 최적화를 쉽게 해제할 수 있는 새 설정이 있습니다. 설정에 표시된 앱 이름은 회사 계정을 관리하는 앱에 따라 달라집니다. 메일과 데이터를 동기화하는 회사 앱의 성능을 향상시키기 위해 배터리 최적화를 끄는 것이 좋습니다. 

### <a name="multi-identity-support-for-onenote-for-ios----1234281---"></a>iOS용 OneNote에 대한 다중 ID 지원      <!-- 1234281 -->
최종 사용자는 이제 iOS용 Microsoft OneNote에서 여러 계정(회사 및 개인)을 사용할 수 있습니다. 개인 전자 필기장에 영향을 미치지 않고 회사 전자 필기장의 회사 데이터에 앱 보호 정책을 적용할 수 있습니다. 예를 들어 정책을 통해 사용자가 회사 전자 필기장에서 정보를 찾을 수는 있지만 회사 전자 필기장에서 개인 전자 필기장으로 회사 데이터를 복사하여 붙여넣을 수는 없도록 할 수 있습니다.
 
- Intune을 통해 [앱 보호 및 다중 ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)를 지원하는 앱에 대해 자세히 알아봅니다.

### <a name="new-settings-to-allow-and-block-apps-on-samsung-knox-standard-devices"></a>Samsung Knox Standard 디바이스에서 앱을 허용 및 차단하는 새로운 설정
<!-- 1305423 822899-->  
이 릴리스에서는 다음 앱 목록을 지정할 수 있는 새로운 [디바이스 제한 설정](device-restrictions-android.md)이 추가되었습니다.
 
- 사용자 설치가 허용된 앱
- 사용자 실행이 차단된 앱
- 디바이스에서 사용자로부터 숨겨진 앱  
URL, 패키지 이름 또는 관리하는 앱 목록을 통해 앱을 지정할 수 있습니다.

### <a name="new-azure-ad-app-based-conditional-access-policy-ui-link-from-intune"></a>Intune의 새 Azure AD 앱 기반 조건부 액세스 정책 UI 링크
<!-- 1016201 -->
IT 관리자는 이제 Azure AD 워크로드에서 새 조건부 액세스 정책 UI를 통해 앱 기반 조건부 정책을 설정할 수 있습니다. Azure Portal의 Intune 앱 보호 섹션에 있는 앱 기반 조건부 액세스는 그대로 남아 있으며 나란히 함께 적용됩니다. Intune 워크로드에서 새 조건부 액세스 정책 UI에 연결하는 편리한 링크도 있습니다.

- [Azure AD 앱 기반 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)에 대해 자세히 알아보세요.

<!-- ########################## -->
## <a name="july-2017"></a>2017년 7월

### <a name="restrict-android-and-ios-device-enrollment-restriction-by-os-version-----1333256-1245463----"></a>OS 버전별 Android 및 iOS 디바이스 등록 제한  <!--- 1333256,  1245463 --->
이제 Intune에서 운영 체제 버전 번호로 iOS 및 Android 등록을 제한하는 기능을 지원합니다. IT 관리자는 **디바이스 유형 제한** 아래에서 최소 운영 체제 값과 최대 운영 체제 값 사이의 범위에서 등록을 제한하는 플랫폼 구성을 설정할 수 있습니다. Android 운영 체제 버전은 Major.Minor.Build.Rev로 지정해야 하며 여기서 Minor, Build, Rev는 선택 사항입니다. iOS 버전을 Major.Minor.Build로 지정해야 하며, 여기서 Minor와 Build는 선택 사항입니다. [디바이스 등록 제한 사항](enrollment-restrictions-set.md)에 대해 자세히 알아보세요.

>[!NOTE]
>Apple 등록 프로그램이나 Apple Configurator를 통해 등록을 제한하지 않습니다.

### <a name="restrict-android-ios-and-macos-device-personally-owned-device-enrollment-----1333272-1333275-1245709---"></a>Android, iOS 및 macOS 디바이스에 대한 개인 소유 디바이스 등록 제한  <!--- 1333272,  1333275, 1245709 --->
Intune은 회사 디바이스 IMEI 번호를 허용 목록에 추가하여 개인 디바이스 등록을 제한할 수 있습니다. 이제 이 기능이 iOS, Android 및 macOS에서 디바이스 일련 번호를 사용하는 방법으로 확장되었습니다. 일련 번호를 Intune에 업로드하면 디바이스를 회사 소유로 미리 선언할 수 있습니다. 등록 제한을 사용하여 개인 소유(BYOD) 디바이스를 차단하고 회사 소유 디바이스에 대해서만 등록을 허용할 수 있습니다. [디바이스 등록 제한 사항](enrollment-restrictions-set.md)에 대해 자세히 알아보세요.

일련 번호를 가져오려면 **디바이스 등록** > **회사 디바이스 식별자**로 이동한 다음 **추가**를 클릭하고 .CSV 파일(헤더 없음, 일련 번호와 IMEI 번호 등의 세부 정보를 위한 두 개의 열)을 업로드합니다. 개인 소유 디바이스를 제한하려면 **디바이스 등록** > **등록 제한**으로 이동합니다. **디바이스 유형 제한**에서 **기본값**을 선택한 다음 **플랫폼 구성**을 선택합니다. iOS, Android 및 macOS에 대해 개인 소유 디바이스를 **허용** 또는 **차단**할 수 있습니다.


### <a name="new-device-action-to-force-devices-to-sync-with-intune----711369---"></a>디바이스가 Intune과 동기화되도록 강제하는 새 디바이스 작업 <!-- 711369 -->
이번 릴리스에서는 선택한 디바이스가 Intune을 사용하여 즉시 체크 인하도록 강제하는 새 디바이스 작업이 추가되었습니다. 디바이스가 체크 인하면 디바이스에 할당된 보류 중인 작업 또는 정책을 즉시 받게 됩니다.  이 작업을 사용하면 예약된 다음 체크 인을 기다리지 않고 즉시 할당한 정책의 유효성을 검사하고 문제를 해결할 수 있습니다.
자세한 내용은 [디바이스 동기화](device-sync.md)를 참조하세요.

### <a name="force-supervised-ios-devices-to-automatically-install-the-latest-available-software-update----777100---"></a>감독된 iOS 디바이스에서 사용 가능한 최신 소프트웨어 업데이트를 자동으로 설치하도록 강제 <!-- 777100 -->
감독된 iOS 디바이스에서 사용 가능한 최신 소프트웨어 업데이트를 자동으로 설치하도록 강제할 수 있는 소프트웨어 업데이트 작업 영역에서 새 정책을 사용할 수 있습니다. 자세한 내용은 [iOS 업데이트 정책 구성](/intune/software-updates-ios)을 참조하세요.

### <a name="check-point-sandblast-mobile---new-mobile-threat-defense-partner----954651-1172027---"></a>Check Point SandBlast Mobile - 새 Mobile Threat Defense 파트너  <!-- 954651, 1172027 -->
Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Checkpoint SandBlast Mobile에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 디바이스 액세스를 제어할 수 있습니다.

#### <a name="how-integration-with-intune-works"></a>Intune과 통합은 어떻게 작동하나요?
Checkpoint SandBlast Mobile을 실행하는 디바이스에서 수집된 원격 분석에 따라 위험이 평가됩니다. Intune 디바이스 준수 정책을 통해 사용하도록 설정된 Checkpoint SandBlast Mobile 위험 평가에 따라 EMS 조건부 액세스 정책을 구성할 수 있습니다. 검색된 위협에 따라 회사 리소스에 대한 비규격 디바이스 액세스를 허용하거나 차단할 수 있습니다.


### <a name="deploy-an-app-as-available-in-the-microsoft-store-for-business----748101---"></a>비즈니스용 Microsoft 스토어에서 사용 가능한 앱 배포 <!-- 748101 -->
이번 릴리스에서는 관리자가 비즈니스용 Microsoft 스토어를 사용 가능으로 할당할 수 있습니다. 사용 가능으로 할당하면 최종 사용자는 Microsoft 스토어로 리디렉션 없이 회사 포털 앱이나 웹 사이트에서 앱을 설치할 수 있습니다.

### <a name="ui-updates-to-the-company-portal-website---1313244-part-1--"></a>회사 포털 웹 사이트의 UI 업데이트 <!--1313244 part 1-->
최종 사용자 경험을 향상시키기 위해 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)의 UI를 여러 개 업데이트했습니다.

- __앱 타일 향상__ 앱 아이콘을 감지할 수 없는 경우 아이콘이 아이콘의 주요 색상을 기반으로 자동 생성된 배경과 함께 표시됩니다. 해당되는 경우 이 배경이 이전에 앱 타일에 표시된 회색 테두리를 대체합니다.

    회사 포털 웹 사이트는 향후 릴리스에서 가능하면 큰 아이콘을 표시합니다. IT 관리자가 최소 크기가 120x120픽셀인 고해상도 아이콘을 사용하여 앱을 게시하는 것이 좋습니다. 

- __탐색 변경 내용__: 탐색 모음 항목이 왼쪽 상단에 있는 햄버거 메뉴로 이동되었습니다. 범주 페이지가 제거되었습니다. 이제 사용자가 찾아보는 동안 범주별로 콘텐츠를 필터링할 수 있습니다.

- __추천 앱 업데이트__ 사용자가 추천하기 위해 선택한 앱을 찾아볼 수 있는 사이트에 전용 페이지를 추가하고 홈페이지의 추천 섹션에서 UI를 일부 조정했습니다.

### <a name="ibooks-support-for-the-company-portal-website---1231841--"></a>회사 포털 웹 사이트에 대한 iBooks 지원 <!--1231841-->
사용자가 iBooks를 찾고 다운로드할 수 있도록 회사 포털 웹 사이트에 전용 페이지를 추가했습니다. 


### <a name="additional-help-desk-troubleshooting-details-----applies-to-1263399-1326964-1341642----"></a>추가 지원 센터 문제 해결 세부 정보 <!---  Applies to 1263399, 1326964, 1341642 --->
Intune의 문제 해결 표시가 업데이트되고 관리자 및 지원 센터 직원에게 제공하는 정보에 문제 해결 표시가 추가되었습니다. 이제 그룹 멤버 자격을 기반으로 사용자의 모든 할당을 요약하는 **할당** 표를 볼 수 있습니다. 이 목록에는 다음이 포함됩니다.
- 모바일 앱
- 규정 준수 정책
- 구성 프로필

또한 이제 **디바이스** 표에는 **Azure AD 조인 유형** 및 **Azure AD 준수** 열이 포함됩니다. 자세한 내용은 [사용자가 문제 해결할 수 있도록 도움](help-desk-operators.md)을 참조하세요.



### <a name="intune-data-warehouse-public-preview"></a>Intune 데이터 웨어하우스(공개 미리 보기)
Intune 데이터 웨어하우스 샘플 데이터는 테넌트에 대한 과거 보기를 제공합니다. 여러 분석 도구와 호환 가능한 OData 링크인 Power BI 파일(PBIX)을 사용하거나 REST API를 사용하여 데이터에 액세스할 수 있습니다. 자세한 내용은 [Intune 데이터 웨어하우스 사용](reports-nav-create-intune-reports.md)을 참조하세요.


### <a name="light-and-dark-modes-available-for-the-company-portal-app-for-windows-10----676547---"></a>Windows 10용 회사 포털 앱에 밝은 모드와 어두운 모드 사용 가능 <!---676547--->
최종 사용자가 Windows 10용 회사 포털 앱에 대한 색 모드를 사용자 지정할 수 있게 됩니다. 사용자는 회사 포털 앱의 설정 섹션에서 변경할 수 있습니다. 사용자가 앱을 다시 시작하면 변경 내용이 표시됩니다. Windows 10 버전 1607 이상에서는 앱 모드가 기본적으로 시스템 설정으로 지정됩니다. Windows 10 버전 1511 이상에서는 앱 모드가 기본적으로 밝은 모드로 설정됩니다.

### <a name="enable-end-users-to-tag-their-device-group-in-the-company-portal-app-for-windows-10----807046--"></a>최종 사용자가 Windows 10용 회사 포털 앱에서 디바이스 그룹에 태그를 지정하도록 허용 <!---807046-->
이제 최종 사용자가 Windows 10용 회사 포털 앱 내에서 직접 태그를 지정하여 디바이스가 속하는 그룹을 선택할 수 있게 됩니다.

<!-- ########################## -->
## <a name="june-2017"></a>2017년 6월

### <a name="new-role-based-administration-access-for-intune-admins------1099990---"></a>Intune 관리자를 위한 새로운 역할 기반 관리 액세스 기능   <!-- 1099990 -->  
Azure AD 조건부 액세스 정책 확인, 작성, 수정 및 삭제를 위한 새로운 조건부 액세스 관리자 역할이 추가될 예정입니다. 이전에는 전역 관리자 및 보안 관리자에게만 이 권한이 있었습니다. 이제는 Intune 관리자에게도 이 역할 권한을 부여할 수 있으며, 그러면 관리자가 조건부 액세스 정책에 액세스할 수 있습니다.


### <a name="tag-corporate-owned-devices-with-serial-number----1215070---"></a>일련 번호를 사용하여 회사 소유 디바이스 태그 지정 <!-- 1215070 -->  
이제 Intune에서 회사 디바이스 식별자로 iOS, macOS 및 Android 일련 번호 업로드를 지원합니다. 지금은 일련 번호를 사용하여 개인용 디바이스의 등록을 차단할 수 없습니다. 등록 중에 일련 번호를 확인하지 않기 때문입니다. 일련 번호로 개인용 디바이스를 차단하는 기능은 조만간 공개될 예정입니다.


### <a name="new-remote-actions-for-ios-devices----854689---"></a>iOS 디바이스에 대한 새 원격 작업 <!-- 854689 -->
이 릴리스에서는 Apple 교실 앱을 관리하는 공유 iPad 디바이스에 대한 새로운 두 가지 원격 디바이스 작업이 추가되었습니다.

-   [현재 사용자 로그아웃](device-logout-user.md) - 선택한 iOS 디바이스의 현재 사용자를 로그아웃합니다.
-   [사용자 제거](device-remove-user.md) - iOS 디바이스의 로컬 캐시에서 선택한 사용자를 삭제합니다.


### <a name="support-for-shared-ipads-with-the-ios-classroom-app----1044681---"></a>iOS 교실 앱을 통해 공유 iPads 지원 <!-- 1044681 -->
이 릴리스에서는 관리되는 Apple ID를 사용하여 공유 iPad에 로그인하는 학생을 포함하도록 iOS 교실 앱 관리 지원이 확장되었습니다.


### <a name="changes-to-intune-built-in-apps----1332306---"></a>Intune 기본 제공 앱에 대한 변경 내용 <!-- 1332306 -->
이전에는 Intune에 신속하게 할당할 수 있는 많은 기본 제공 앱이 포함되어 있었습니다. 사용자 의견에 따라 이 목록은 제거되었으며 더 이상 기본 제공 앱은 표시되지 않습니다.
그러나 이미 기본 제공 앱을 할당한 경우 이러한 앱은 여전히 앱 목록에 표시됩니다. 필요에 따라 이러한 앱을 계속 할당할 수 있습니다.
이후 릴리스에는 Azure Portal에서 기본 제공 앱을 더 쉽게 선택하고 할당하는 방법이 추가될 예정입니다.

### <a name="easier-installation-of-office-365-apps-----1121362----"></a>Office 365 앱의 간편한 설치 <!--- 1121362 --->
새 **Office 365 ProPlus** 앱 유형을 통해 최신 버전의 Windows 10을 실행하는, 관리하는 디바이스에 Office 365 ProPlus 2016 앱을 쉽게 할당할 수 있습니다. 또한 라이선스가 있는 경우 Microsoft Project 및 Microsoft Visio를 설치할 수 있습니다. 원하는 앱이 모두 번들로 묶여 Intune 콘솔의 앱 목록에 하나의 앱으로 표시됩니다.
자세한 내용은 [Windows 10용 Office 365 앱을 추가하는 방법](apps-add-office365.md)을 참조하세요.


### <a name="support-for-offline-apps-from-the-microsoft-store-for-business-----777044----"></a>비즈니스용 Microsoft 스토어의 오프라인 앱 지원 <!--- 777044 --->
이제 비즈니스용 Microsoft 스토어에서 구매한 오프라인 앱이 Azure Portal에 동기화됩니다. 그런 다음 이러한 앱을 디바이스 그룹 또는 사용자 그룹에 배포할 수 있습니다. 즉, 오프라인 앱이 스토어가 아닌 Intune을 통해 설치됩니다.

### <a name="microsoft-teams-is-now-part-of-the-app-based-ca-list-of-approved-apps------1257019---"></a>이제 Microsoft 팀이 승인된 앱의 앱 기반 CA 목록에 포함됨   <!-- 1257019 -->
이제 iOS 및 Android용 Microsoft Teams 앱이 Exchange 및 SharePoint Online용 앱 기반 조건부 액세스 정책에 대해 승인된 앱에 포함됩니다. 현재 앱 기반 조건부 액세스를 사용하는 모든 테넌트에 대해 Azure Portal의 Intune 앱 보호 블레이드를 통해 앱을 구성할 수 있습니다.

### <a name="managed-browser-and-app-proxy-integration----1287310---"></a>Managed Browser 및 앱 프록시 통합 <!-- 1287310 -->
이제 Intune Managed Browser가 Azure AD 애플리케이션 프록시 서비스와 통합되어 사용자가 원격으로 작업하는 경우에도 내부 웹 사이트에 액세스하도록 허용할 수 있습니다. 브라우저의 사용자는 일반적인 방법으로 사이트 URL을 입력하면 되고, Managed Browser가 애플리케이션 프록시 웹 게이트웨이를 통해 요청을 라우팅합니다. 자세한 내용은 [Managed Browser 정책을 사용하여 인터넷 액세스 관리](app-configuration-managed-browser.md)를 참조하세요.

### <a name="new-app-configuration-settings-for-the-intune-managed-browser----682951---"></a>Intune Managed Browser에 대한 새로운 앱 구성 설정 <!-- 682951 -->
이 릴리스에서는 iOS 및 Android용 Intune Managed Browser 앱에 대한 구성이 더 추가되었습니다. 이제 앱 구성 정책을 사용하여 브라우저의 책갈피와 기본 홈페이지를 구성할 수 있습니다.
자세한 내용은 [Managed Browser 정책을 사용하여 인터넷 액세스 관리](app-configuration-managed-browser.md)를 참조하세요.

### <a name="bitlocker-settings-for-windows-10-----951707---"></a>Windows 10에 대한 BitLocker 설정  <!-- 951707 -->
이제 새로운 Intune 디바이스 프로필을 사용하여 Windows 10 디바이스에 대한 BitLocker 설정을 구성할 수 있습니다. 예를 들어 디바이스가 암호화되도록 요구하고 BitLocker를 켤 때 적용되는 설정을 더 구성할 수도 있습니다.
자세한 내용은 [Windows 10에 대한 Endpoint Protection 설정](endpoint-protection-windows-10.md)을 참조하세요.

### <a name="new-settings-for-windows-10-device-restriction-profile-----978527--978550-978569-1050031-1058611-----"></a>Windows 10 디바이스 제한 프로필에 대한 새로운 설정 <!--- 978527,  978550, 978569, 1050031, 1058611,  --->
이 릴리스에서는 Windows 10 디바이스 제한 프로필에 대한 새로운 설정이 다음 범주에 추가되었습니다.

-  Windows Defender
-  셀룰러 및 연결
-  잠긴 화면 환경
-  개인 정보 취급 방침
-  검색
-  Windows 추천
-  Microsoft Edge 브라우저

Windows 10 설정에 대한 자세한 내용은 [Windows 10 이상 디바이스 제한 설정](device-restrictions-windows-10.md)을 참조하세요.


### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>이제 Android용 회사 포털 앱에는 앱 보호 정책에 대한 새로운 최종 사용자 환경이 있습니다. <!--1305217-->
고객 의견에 따라 Android용 회사 포털 앱에 **회사 콘텐츠 액세스** 단추가 표시됩니다. 이러한 작업은 최종 사용자가 Intune 모바일 애플리케이션 관리의 기능인 앱 보호 정책을 지원하는 앱에만 액세스하면 될 경우 불필요하게 등록 프로세스를 거치지 않도록 하기 위한 것입니다. 이러한 변경 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지에서 확인할 수 있습니다.

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>회사 포털을 쉽게 제거할 수 있는 새로운 메뉴 작업 <!--1164569-->
사용자 여러분의 의견에 따라 디바이스에서 회사 포털 제거를 시작할 수 있는 새로운 메뉴 작업이 Android용 회사 포털 앱에 추가되었습니다. 이 작업을 수행하면 Intune 관리에서 디바이스가 제거되므로 사용자가 디바이스에서 앱을 제거할 수 있습니다. 이러한 변경 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지 및 [Android 최종 사용자 설명서](/intune-user-help/unenroll-your-device-from-intune-android)에서 확인할 수 있습니다.

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Windows 10 크리에이터스 업데이트와 동기화하는 앱 개선 사항 <!--676505-->
Windows 10용 회사 포털 앱은 이제 Windows 10 크리에이터스 업데이트(버전 1703)가 설치되어 있는 디바이스의 앱 설치 요청 동기화를 자동으로 시작합니다. 이렇게 하면 "동기화 보류 중" 상태에 있는 동안의 앱 설치 지연 문제를 줄일 수 있습니다. 또한 사용자는 앱 내에서 수동으로 동기화를 시작할 수 있습니다. 이러한 변경 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지에서 확인할 수 있습니다.

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Windows 10 회사 포털에 대한 새로운 단계별 환경 <!---1058938--->
Windows 10용 회사 포털 앱에 식별되거나 등록되지 않은 디바이스에 대한 단계별 Intune 연습 환경이 포함될 예정입니다. 새 환경에서는 Azure Active Directory 등록(조건부 액세스 기능에 필요) 및 MDM 등록(디바이스 관리 기능에 필요) 과정을 사용자에게 안내하는 단계별 지침을 제공합니다. 회사 포털 홈 페이지에서 안내 방식 환경에 액세스할 수 있습니다. 사용자는 이러한 등록을 완료하지 않아도 앱을 계속 사용할 수 있지만 제한된 기능만 사용할 수 있습니다.

이 업데이트는 Windows 10 1주년 업데이트(빌드 1607) 이상을 실행하는 디바이스에서만 표시됩니다. 이러한 변경 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지에서 확인할 수 있습니다.


### <a name="microsoft-intune-and-conditional-access-admin-consoles-are-generally-available"></a>Microsoft Intune 및 조건부 액세스 관리 콘솔 일반 공급
Azure Portal 관리 콘솔과 조건부 액세스 관리 콘솔에서 새로운 Intune이 일반 공급됩니다. 이제 Azure Portal의 Intune을 통해 모든 Intune MAM 및 MDM 기능을 통합된 단일 관리 환경에서 관리하고 Azure AD 그룹화 및 대상 지정 기능을 활용할 수 있습니다. Azure의 조건부 액세스 기능은 통합된 단일 콘솔에서 Azure AD와 Intune의 다양한 기능을 함께 제공합니다. 그리고 관리 측면에서 볼 때 Azure 플랫폼으로 이전하면 최신 브라우저를 사용할 수 있습니다.

이제 Intune은 Azure Portal(portal.azure.com)에서 **미리 보기** 레이블 없이 표시됩니다.

그룹을 마이그레이션할 수 있도록 작업 수행을 요청하는 일련의 메시지 중 하나가 메시지 센터에 수신된 경우가 아니면 현재 기존 고객이 수행해야 하는 작업은 없습니다. Microsoft에서 발생한 버그로 인해 마이그레이션이 오래 걸린다는 메시지 센터 공지가 수신되었을 수도 있습니다. Microsoft는 영향받는 모든 고객의 마이그레이션을 정상적으로 완료하기 위해 지속적으로 노력하고 있습니다.

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>iOS 용 회사 포털 앱의 앱 타일 개선 사항
사용자가 회사 포털에 대해 설정하는 브랜딩 색을 반영하도록 홈 페이지의 앱 타일 디자인이 업데이트되었습니다. 자세한 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>이제 iOS용 회사 포털 앱에서 계정 선택기 사용 가능
iOS 디바이스 사용자가 회사 또는 학교 계정을 사용하여 다른 Microsoft 앱에 로그인하는 경우 회사 포털에 로그인할 때 새로운 계정 선택기가 표시될 수 있습니다. 자세한 내용은 [앱 UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.

<!-- ########################## -->
## <a name="may-2017"></a>2017년 5월

### <a name="change-your-mdm-authority-without-unenrolling-managed-devices---1103950--"></a>관리되는 디바이스를 등록 취소하지 않고 MDM 기관 변경 <!--1103950-->
이제 Microsoft 지원에 문의하여 기존의 관리 디바이스를 등록 취소했다가 다시 등록할 필요 없이 MDM 기관을 변경할 수 있습니다. Configuration Manager 콘솔에서 MDM 기관을 Configuration Manager로 설정(하이브리드)에서 Microsoft Intune(독립 실행형)으로 또는 그 반대로 [변경](/sccm/mdm/deploy-use/change-mdm-authority)할 수 있습니다.


### <a name="improved-notification-for-samsung-knox-startup-pins---1087143--"></a>Samsung Knox 시작 PIN 알림 향상 <!--1087143-->
암호화를 준수하기 위해 최종 사용자가 Samsung Knox 디바이스에서 시작 PIN을 설정해야 하는 경우 최종 사용자에게 표시되는 알림을 탭하면 최종 사용자가 설정 앱의 정확한 위치로 이동하게 됩니다.  이전에는 최종 사용자가 알림을 통해 암호 변경 화면으로 이동했습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="apple-school-manager-asm-support-with-shared-ipad----748864-770395--"></a>공유 iPad에 대한 ASM(Apple School Manager) 지원 <!-- 748864, 770395-->

이제 Intune은 Apple 장비 등록 프로그램 대신 ASM(Apple School Manager)을 사용하도록 지원하여 iOS 디바이스 기본 등록 기능을 제공합니다. 공유 iPad에 대해 교실 앱을 사용하고 Microsoft SDS(학교 데이터 동기화)를 통해 ASM에서 Azure Active Directory로 데이터를 동기화할 수 있도록 설정하려면 ASM 온보딩이 필요합니다. 자세한 내용은 [Apple School Manager를 통해 iOS 디바이스 등록 기능 사용](apple-school-manager-set-up-ios.md)을 참조하세요.

> [!NOTE]
> 교실 앱을 사용할 수 있도록 공유 iPad를 구성하려면 Azure의 iOS Education 구성(아직 제공되지 않음)이 필요합니다.  이 기능은 곧 추가될 예정입니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="provide-remote-assistance-to-android-devices-using-teamviewer----675418---"></a>TeamViewer를 사용하여 Android 디바이스에 대한 원격 지원 제공 <!-- 675418 -->

이제 Intune에서는 [TeamViewer](https://www.teamviewer.com) 소프트웨어(별매)를 사용하여 Android 디바이스를 실행하는 사용자에게 원격 지원을 제공할 수 있도록 지원합니다. 자세한 내용은 [Intune Android 관리 디바이스에 대한 원격 지원 제공](device-profile-android-teamviewer.md)을 참조하세요.

### <a name="app-management"></a>앱 관리

#### <a name="new-app-protection-policies-conditions-for-mam----679864---"></a>MAM의 새 앱 보호 정책 조건 <!-- 679864 -->

이제 등록 사용자가 없는 MAM에 대해 다음 정책을 적용하는 요구 사항을 설정할 수 있습니다.

- 최소 애플리케이션 버전
- 최소 운영 체제 버전
- 대상 애플리케이션의 최소 Intune 앱 SDK 버전(iOS에만 해당)

이 기능은 Android 및 iOS 둘 다에서 제공됩니다. Intune은 OS 플랫폼 버전, 애플리케이션 버전 및 Intune 앱 SDK에 대해 최소 버전 적용을 지원합니다. iOS에서는 SDK가 통합된 애플리케이션도 SDK 수준에서 최소 버전 적용을 설정할 수 있습니다. 위에 언급된 세 가지 수준에서 앱 보호 정책을 통한 최소 요구 사항이 충족되지 않으면 사용자가 대상 애플리케이션에 액세스할 수 없습니다. 이때 사용자는 계정을 제거하거나(다중 ID 애플리케이션의 경우), 애플리케이션을 닫거나, 해당 OS 또는 애플리케이션 버전을 업데이트할 수 있습니다.

또한 추가 설정을 구성하여 OS 또는 애플리케이션 업그레이드를 권장하는 비차단 알림을 제공할 수도 있습니다. 이 알림은 닫을 수 있고 애플리케이션을 정상적으로 사용할 수 있습니다.

자세한 내용은 [iOS 앱 보호 정책 설정](app-protection-policy-settings-ios.md) 및 [Android 앱 보호 정책 설정](app-protection-policy-settings-android.md)을 참조하세요.

#### <a name="configure-app-configurations-for-android-for-work----621621---"></a>Android for Work용 앱 구성을 위한 구성 작업 <!-- 621621 -->
스토어에서 제공되는 일부 Android 앱은 IT 관리자가 작업 프로필에서 앱이 실행되는 방법을 제어할 수 있는 관리되는 구성 옵션을 지원합니다. Intune에서는 이제 앱이 지원하는 구성을 확인하고 구성 디자이너 또는 JSON 편집기를 사용하여 Azure Portal에서 구성을 수행할 수 있습니다. 자세한 내용은 [Android for Work용 앱 구성 사용](app-configuration-policies-use-android.md)을 참조하세요.

#### <a name="new-app-configuration-capability-for-mam-without-enrollment----677969---"></a>등록 없이도 MAM에 대해 새로운 앱 구성 기능 사용 가능 <!-- 677969 -->
이제 등록 채널이 없는 MAM을 통해서 앱 구성 정책을 만들 수 있습니다. 이 기능은 MDM(모바일 디바이스 관리) 앱 구성에서 제공되는 앱 구성 정책과 동일합니다. 등록 없이 MAM을 사용하여 앱을 구성하는 예를 확인하려면 [Microsoft Intune에서 Managed Browser를 사용하여 인터넷 액세스 관리](app-configuration-managed-browser.md)를 참조하세요.

#### <a name="configure-allowed-and-blocked-url-lists-for-the-managed-browser----682960---"></a>Managed Browser에 대해 허용 및 차단된 URL 목록 구성 <!-- 682960 -->
이제 Azure 포털에서 앱 구성 설정을 사용하여 Intune Managed Browser용으로 허용 도메인/URL 및 차단 도메인/URL 목록을 구성할 수 있습니다. Managed Browser를 사용 중인 디바이스(관리 디바이스 또는 관리되지 않는 디바이스)에 관계없이 이러한 설정을 구성할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 Managed Browser 정책을 사용하여 인터넷 액세스 관리](app-configuration-managed-browser.md)를 참조하세요.

#### <a name="app-protection-policy-helpdesk-view----1069473---"></a>앱 보호 정책 기술 지원팀 보기 <!-- 1069473 -->
IT 기술 지원팀 사용자는 이제 문제 해결 블레이드에서 사용자에게 할당된 앱 보호 정책 앱의 상태와 사용자 라이선스 상태를 확인할 수 있습니다. 자세한 내용은 [문제 해결](./help-desk-operators.md)을 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="control-website-visits-on-ios-devices----723832---"></a>iOS 디바이스에서 웹 사이트 방문 제어 <!-- 723832 -->
이제 iOS 디바이스 사용자가 방문할 수 있는 웹 사이트를 다음 두 가지 방법 중 하나를 사용하여 제어할 수 있습니다.

- Apple 기본 제공 웹 콘텐츠 필터를 사용하여 허용된 URL 및 차단된 URL을 추가합니다.

- Safari 브라우저에서 지정한 웹 사이트만 액세스할 수 있도록 허용합니다. 지정한 각 사이트에 대한 책갈피가 Safari에서 만들어집니다.

자세한 내용은 [iOS 디바이스에 대한 웹 콘텐츠 필터 설정](web-content-filter-settings-ios.md)을 참조하세요.

#### <a name="preconfigure-device-permissions-for-android-for-work-apps----621614---"></a>Android for Work 앱에 대한 디바이스 권한 미리 구성 <!-- 621614 -->
Android for Work 디바이스 작업 프로필에 배포된 앱의 경우 이제 개별 앱에 대해 권한 상태를 구성할 수 있습니다.  기본적으로 위치 또는 디바이스 카메라에 대한 액세스와 같이 디바이스 권한이 필요한 Android 앱에서는 권한을 허용할 것인지 거부할 것인지 묻는 메시지를 사용자에게 표시합니다.  예를 들어, 앱에서 디바이스의 마이크를 사용하는 경우 앱에 마이크 사용 권한을 부여할 것인지 묻는 메시지가 최종 사용자에게 표시됩니다. 이 기능을 사용하면 최종 사용자 대신 권한을 정의할 수 있습니다.  a) 사용자에게 알리지 않고 자동으로 거부하거나, b) 사용자에게 알리지 않고 자동으로 승인하거나, c) 수락/거부 여부를 선택하라는 메시지를 사용자에게 표시하도록 권한을 구성할 수 있습니다. 자세한 내용은 [Microsoft Intune의 Android for Work 디바이스 제한 설정](device-restrictions-android-for-work.md)을 참조하세요.

#### <a name="define-app-specific-pin-for-android-for-work-devices----728976-1102534---"></a>Android for Work 디바이스의 앱별 PIN 정의 <!-- 728976, 1102534 -->
관리자는 Android for Work 디바이스로 관리되는 작업 프로필이 있는 Android 7.0 이상 디바이스에 대해 작업 프로필에 있는 앱에만 적용되는 암호 정책을 정의할 수 있습니다.  다음 옵션을 사용할 수 있습니다.

- 디바이스 전체 암호 정책만 정의 - 사용자가 전체 디바이스를 잠금 해제하는 데 사용해야 하는 암호입니다.
- 작업 프로필 암호 정책만 정의 - 작업 프로필의 앱이 열릴 때마다 사용자에게 암호를 입력하라는 메시지가 표시됩니다.
- 디바이스 및 작업 프로필 정책 모두 정의 - IT 관리자가 디바이스 암호 정책 및 작업 프로필 암호 정책을 서로 다른 강도로 정의하도록 선택할 수 있습니다(예: 디바이스를 잠금 해제하려면 4자리 PIN을 사용하지만 작업 앱을 열려면 6자리 PIN을 사용하도록 정의).

자세한 내용은 [Microsoft Intune의 Android for Work 디바이스 제한 설정](device-restrictions-android-for-work.md)을 참조하세요.

> [!NOTE]
> 이 기능은 Android 7.0 이상에서만 사용할 수 있습니다.  기본적으로 최종 사용자는 2개의 별도로 정의된 PIN을 사용하거나 정의된 2개의 PIN을 둘 중 더 강도가 높은 PIN으로 결합하도록 선택할 수 있습니다.

#### <a name="new-settings-for-windows-10-devices----978585---"></a>Windows 10 디바이스의 새로운 설정 <!-- 978585 -->
무선 표시, 디바이스 검색, 작업 전환 및 SIM 카드 오류 메시지와 같은 기능을 제어하는 새로운 [Windows 디바이스 제한 설정](device-restrictions-windows-10.md)이 추가되었습니다.

#### <a name="updates-to-certificate-configuration----918991-and-823198---"></a>인증서 구성 업데이트 <!-- 918991 and 823198 -->
SCEP 인증서 프로필을 만들 때 iOS, Android 및 Windows 디바이스에 대해 <strong>주체 이름 형식</strong>에서 <strong>사용자 지정</strong> 옵션을 사용할 수 있습니다. 이 업데이트 전에는 iOS 디바이스에서만 <strong>사용자 지정</strong> 필드가 제공되었습니다. 자세한 내용은 [SCEP 인증서 프로필 만들기](certificates-scep-configure.md#create-a-scep-certificate-profile)를 참조하세요.

PKCS 인증서 프로필을 만들 때 **주체 대체 이름**에서 **사용자 지정 Azure AD 특성**을 사용할 수 있습니다. **사용자 지정 Azure AD 특성**을 선택하면 **부서** 옵션을 사용할 수 있습니다. 자세한 내용은 [PKCS 인증서 프로필 만들기](certficates-pfx-configure.md#create-a-pkcs-certificate-profile)를 참조하세요.

#### <a name="configure-multiple-apps-that-can-run-when-an-android-device-is-in-kiosk-mode----662059---"></a>Android 디바이스가 키오스크 모드일 때 실행할 수 있는 여러 앱 구성 <!-- 662059 -->
이전에는 ndroid 디바이스가 키오스크 모드일 때 실행하도록 허용된 앱 하나만 구성할 수 있었습니다. 이제는 앱 ID 또는 토어 URL을 사용하거나 이미 관리 중인 Android 앱을 선택하여 여러 앱을 구성할 수 있습니다. 자세한 내용은 [키오스크 모드 설정](device-restrictions-android.md#kiosk)을 참조하세요.



<!-- ########################## -->
## <a name="april-2017"></a>2017년 4월

### <a name="support-for-managing-the-apple-classroom-app"></a>Apple 교실 앱 관리 지원
이제 iPad 디바이스에서 iOS 교실 앱을 관리할 수 있습니다. 교사 iPad에서 정확한 수업 및 학생 데이터를 사용하여 교실 앱을 설정하고 수업에 등록된 학생 iPad를 구성하면 앱을 사용하여 학생 iPad를 제어할 수 있습니다.
자세한 내용은 [iOS 교육 설정 구성](education-settings-configure-ios.md)을 참조하세요.

### <a name="support-for-managed-configuration-options-for-android-apps----621621---"></a>Android 앱에 대해 관리되는 구성 옵션 지원 <!-- 621621 -->
관리되는 구성 옵션을 지원하는 Play 스토어의 Android 앱을 이제 Intune에서 구성할 수 있습니다.  이 기능을 통해 IT에서는 앱에서 지원하는 구성 값 목록을 볼 수 있으며, 이 기능에서는 이러한 값을 구성할 수 있도록 하는 최고의 단계별 UI를 제공합니다.

### <a name="new-android-policy-for-complex-pins----722069---"></a>복합 PIN에 대한 새 Android 정책 <!-- 722069 -->
Android 5.0 이상을 실행하는 디바이스에 대한 Android 디바이스 프로필에서 복합 숫자의 필수 [암호](device-restrictions-android.md#password) 유형을 설정할 수 있습니다.  이 설정을 사용하면 디바이스 사용자가 1111 또는 1234와 같은 반복되거나 연속되는 숫자를 포함하는 PIN을 만들지 못하도록 할 수 있습니다.

### <a name="additional-support-for-android-for-work-devices"></a>Android for Work 디바이스에 대한 추가 지원
- **암호 및 회사 프로필 설정 관리** <!-- 612808 -->

  이제 이 새로운 Android for Work 디바이스 제한 정책을 사용하여, 관리하는 Android for Work 디바이스에서 암호 및 회사 프로필 설정을 관리할 수 있습니다.

- **회사 및 개인 프로필 간의 데이터 공유 허용** <!-- 1045102 -->

이제 이 Android for Work 디바이스 제한 프로필에는 회사 및 개인 프로필 간의 데이터 공유를 구성할 수 있도록 하는 새 옵션이 포함되어 있습니다.

- **회사 및 개인 프로필 간의 복사 및 붙여넣기 제한** <!-- 1046094 -->

  이제 새로운 Android for Work 디바이스용 사용자 지정 디바이스 프로필을 사용하여 회사 및 개인 앱 간에 복사 및 붙여넣기 작업을 허용할지 여부를 제한할 수 있습니다.

자세한 내용은 [Android for Work용 디바이스 제한](device-restrictions-android-for-work.md)을 참조하세요.

### <a name="assign-lob-apps-to-ios-and-android-devices----1057568---"></a>iOS 및 Android 디바이스에 LOB 앱 할당 <!-- 1057568 -->
이제 [iOS](lob-apps-ios.md)용 LOB(기간 업무) 앱(.ipa 파일)과 [Android](lob-apps-android.md)용 LOB 앱(.apk 파일)을 사용자 또는 디바이스에 할당할 수 있습니다.


###  <a name="new-device-policies-for-ios----723774-723815-723826-723830---"></a>iOS에 대한 새 디바이스 정책 <!-- 723774, 723815, 723826, 723830 -->
- **Apps on Home screen**(홈 화면의 앱) - 앱 사용자가 [iOS 디바이스의 홈 화면](home-screen-settings-ios.md)에서 어떤 앱을 보게 할지 제어할 수 있습니다. 이 정책은 홈 화면의 레이아웃을 변경하지만 앱을 배포하지 않습니다.

- **Connections to AirPrint devices**(AirPrint 디바이스에 대한 연결) - iOS 디바이스의 최종 사용자가 연결할 수 있는 [AirPrint](air-print-settings-ios-macos.md) 디바이스(네트워크 프린터)를 제어할 수 있습니다.

- **Connections to AirPlay devices**(AirPlay 디바이스에 대한 연결) - iOS 디바이스의 최종 사용자가 연결할 수 있는 [AirPlay 디바이스](airplay-settings-ios.md)(Apple TV 등)를 제어할 수 있습니다.

- **Custom lock screen message**(사용자 지정 잠금 화면 메시지) - 사용자 iOS 디바이스의 잠금 화면에 표시할 사용자 지정 메시지를 구성하여 기본 잠금 화면 메시지를 대체할 수 있습니다. 자세한 내용은 [iOS 디바이스에서 분실 모드 활성화](device-lost-mode.md)를 참조하세요.

### <a name="restrict-push-notifications-for-ios-apps----723767---"></a>iOS 앱에 대한 푸시 알림 제한 <!-- 723767 -->
Intune 디바이스 제한 프로필에서 이제 iOS 디바이스에 대해 다음과 같은 [알림 설정](app-notification-settings-ios.md)을 구성할 수 있습니다.

- 지정된 앱에 대한 알림을 완전히 켜거나 끕니다.
- 지정한 앱에 대해 알림 센터의 알림을 켜거나 끕니다.
- 경고 유형을 **없음**, **배너** 또는 **Modal Alert**(모달 경고)로 지정합니다.
- 이 앱에 대해 배지를 허용할지 여부를 지정합니다.
- 알림 소리를 허용할지 여부를 지정합니다.

### <a name="configure-ios-apps-to-run-in-single-app-mode-autonomously----737837---"></a>iOS 앱이 자체적으로 단일 앱 모드로 실행되도록 구성 <!-- 737837 -->
이제 Intune 디바이스 프로필을 사용하여 iOS 디바이스에서 지정된 앱을 [자체 단일 앱 모드](device-restrictions-ios.md#autonomous-single-app-mode-supervised-only)로 실행하도록 구성할 수 있습니다. 이 모드를 구성하고 앱이 실행되면 디바이스가 잠기므로 해당 앱만 실행할 수 있습니다. 이 모드의 예로 사용자가 디바이스에서 테스트를 수행할 수 있도록 앱을 구성하는 경우를 들 수 있습니다. 앱의 작업이 완료되거나 이 정책을 제거하면 디바이스가 일반 상태로 돌아옵니다.

### <a name="configure-trusted-domains-for-email-and-web-browsing-on-ios-devices----723765---"></a>iOS 디바이스에서 이메일 및 웹 검색을 위해 신뢰할 수 있는 도메인 구성 <!-- 723765 -->
이제 iOS 디바이스 제한 프로필에서 다음과 같은 [도메인 설정](device-restrictions-ios.md#domains)을 구성할 수 있습니다.

- **표시되지 않은 메일 도메인** - 사용자가 보내거나 받는 메일 중 여기에 지정하는 도메인과 일치하지 않는 메일은 신뢰할 수 없는 것으로 표시됩니다.

- **관리되는 웹 도메인** - 여기에 지정하는 URL에서 다운로드한 문서는 관리되는 문서로 간주됩니다(Safari에만 해당).  

- **Safari 암호 자동 채우기 도메인** - 여기에 지정하는 패턴과 일치하는 URL에서만 사용자가 Safari에 암호를 저장할 수 있습니다. 이 설정을 사용하려면 디바이스가 감독 모드여야 하며 여러 사용자용으로 구성되어 있지 않아야 합니다. (iOS 9.3 이상)


### <a name="vpp-apps-available-in-ios-company-portal----748782---"></a>iOS 회사 포털에서 사용할 수 있는 VPP 앱 <!-- 748782 -->
이제 iOS VPP(대량 구매) 앱을 **사용 가능한** 설치로 최종 사용자에게 할당할 수 있습니다. 최종 사용자는 앱을 설치하려면 Apple 스토어 계정이 필요합니다.

### <a name="synchronize-ebooks-from-apple-vpp-store----800878---"></a>Apple VPP 스토어에서 eBook 동기화 <!-- 800878 -->
이제 Apple 대량 구매 프로그램 스토어에서 구매한 책을 [Intune과 동기화](vpp-apps-ios.md)하고 사용자에게 책을 할당할 수 있습니다.

### <a name="multi-user-management-for-samsung-knox-standard-devices----971988---"></a>Samsung Knox Standard 디바이스에 대한 다중 사용자 관리 <!-- 971988 -->
Samsung Knox Standard를 실행하는 디바이스가 이제 Intune의 [다중 사용자 관리](android-enroll.md)에서 지원됩니다. 따라서 최종 사용자가 Azure Active Directory 자격 증명을 사용하여 디바이스에서 로그인 및 로그아웃할 수 있고 디바이스는 사용 여부와 관계없이 중앙에서 관리됩니다.  최종 사용자는 로그인하면 앱에 액세스할 수 있고 앱에 정책을 적용할 수도 있습니다. 사용자가 로그아웃하면 모든 앱 데이터가 지워집니다.

### <a name="additional-windows-device-restriction-settings----818566---"></a>추가 Windows 디바이스 제한 설정 <!-- 818566 -->
추가 Microsoft Edge 브라우저 지원, 디바이스 잠금 화면 사용자 지정, 시작 메뉴 사용자 지정, Windows 추천 검색이 설정된 배경 화면, 프록시 설정 등과 같은 추가 [Windows 디바이스 제한 설정](device-restrictions-windows-10.md)에 대한 지원을 추가했습니다.

### <a name="multi-user-support-for-windows-10-creators-update----822547---"></a>Windows 10 크리에이터스 업데이트에 대한 다중 사용자 지원 <!-- 822547 -->
Windows 10 크리에이터 업데이트를 실행하고 Azure Active Directory 도메인에 가입된 디바이스에 대한 [다중 사용자 관리](windows-enroll.md) 지원을 추가했습니다. 따라서 여러 표준 사용자가 Azure AD 자격 증명을 사용하여 디바이스에 로그인할 때 각 사용자는 자신의 사용자 이름에 할당된 앱과 정책을 수신합니다. 현재 사용자가 앱 설치와 같은 셀프 서비스의 경우 회사 포털을 사용할 수 없습니다.

### <a name="fresh-start-for-windows-10-pcs---1004830---"></a>Windows 10 PC의 새로운 시작<!-- 1004830 -->
Windows 10 PC에 대한 [새로운 시작 디바이스 작업](device-fresh-start.md)을 이제 사용 가능합니다.  이 작업을 실행하면 PC에 설치된 모든 앱이 제거되고 PC가 자동으로 최신 버전의 Windows로 업데이트됩니다. 이 작업은 종종 새 PC와 함께 제공되는 미리 설치된 OEM 앱을 제거하는 데 사용할 수 있습니다. 이 디바이스 작업을 실행할 때 사용자 데이터를 유지할지 여부를 구성할 수 있습니다.

### <a name="additional-windows-10-upgrade-paths----903672---"></a>추가 Windows 10 업그레이드 경로 <!-- 903672 -->
이제 [버전 업그레이드 정책을 만들어 디바이스를 다음과 같은 추가 Windows 10 버전으로 업그레이드](edition-upgrade-configure-windows-10.md)할 수 있습니다.

- Windows 10 Professional
- Windows 10 Professional KN
- Windows 10 Professional Education
- Windows 10 Professional Education N

### <a name="bulk-enroll-windows-10-devices----747607---"></a>Windows 10 디바이스 대량 등록 <!-- 747607 -->
이제 WCD(Windows 구성 디자이너)를 사용하여 Azure Active Directory 및 Intune에 대한 Windows 10 크리에이터스 업데이트를 실행하는 많은 디바이스를 연결할 수 있습니다. Azure AD 테넌트에 대한 [대량 MDM 등록](windows-bulk-enroll.md)을 사용하도록 설정하려면 Windows 구성 디자이너를 사용하여 Azure AD 테넌트에 디바이스를 연결하는 프로비전 패키지를 만들고, 이 패키지를 대량으로 등록 및 관리할 회사 소유 디바이스에 적용합니다. 패키지가 디바이스에 적용되면, Azure AD에 조인되고, Intune에 등록되며, Azure AD 사용자가 로그인할 준비가 됩니다.  Azure AD 사용자는 이러한 디바이스에서 표준 사용자이며 할당된 정책 및 필수 앱을 수신합니다. 셀프 서비스 및 회사 포털 시나리오의 경우 현재 지원되지 않습니다.

### <a name="new-mam-settings-for-pin-and-managed-storage-locations----581122-736644---"></a>PIN 및 관리되는 스토리지 위치에 대한 새 MAM 설정 <!-- 581122, 736644 -->
이제 MAM(모바일 애플리케이션 관리) 시나리오에 도움이 되는 두 가지 새 앱 설정이 제공됩니다.

- **Disable app PIN when device PIN is managed**(디바이스 PIN이 관리되는 경우 앱 PIN 사용 안 함) - 등록된 디바이스에 디바이스 PIN이 있는지 검색하고 있으면 앱 보호 정책에 따라 트리거되는 앱 PIN을 건너뜁니다. 이 설정을 사용하면 등록된 디바이스에서 MAM 지원 애플리케이션을 여는 사용자에게 PIN 프롬프트가 표시되는 횟수를 줄일 수 있습니다. 이 기능은 Android 및 iOS 모두에 제공됩니다.

- **Select which storage services corporate data can be saved to**(회사 데이터를 저장할 스토리지 서비스 선택) - 회사 데이터를 저장할 스토리지 위치를 지정할 수 있습니다. 사용자가 선택된 스토리지 위치 서비스에 저장할 수 있으므로 나열되지 않은 다른 스토리지 위치는 모두 차단됩니다.

  지원되는 스토리지 위치 서비스 목록:

  - OneDrive
  - 비즈니스 SharePoint Online
  - 로컬 스토리지

### <a name="help-desk-troubleshooting-portal----907448---"></a>기술 지원팀의 문제 해결 포털 <!-- 907448 -->
새로운 [문제 해결 포털](help-desk-operators.md)을 사용하면 도움말 센터 운영자 및 Intune 관리자가 사용자와 디바이스를 확인하고 Intune 기술 문제를 해결하는 작업을 수행할 수 있습니다.

<!-- ########################## -->
## <a name="march-2017"></a>2017년 3월

### <a name="support-for-ios-lost-mode---431695--"></a>iOS 분실 모드 지원 <!--431695-->
iOS 9.3 이상 디바이스에 대해 Intune은 **분실 모드**를 추가 지원합니다. 디바이스를 잠가 모든 사용을 방지할 수 있으며 디바이스 잠금 화면의 메시지 및 연락처 전화 번호를 표시할 수 있습니다.

최종 사용자는 관리자가 분실 모드를 사용하지 않도록 설정할 때까지 디바이스의 잠금을 해제할 수 없습니다. 분실 모드가 설정된 경우 Intune 콘솔에서 **디바이스 찾기** 작업을 사용하여 디바이스의 지리적 위치를 지도에 표시할 수 있습니다.

디바이스는 DEP를 통해 등록되고 감독 모드 상태인 회사 소유의 iOS 디바이스여야 합니다.

자세한 내용은 [Microsoft Intune 디바이스 관리란?](device-management.md)을 참조하세요.

### <a name="improvements-to-device-actions-report---677150--"></a>디바이스 작업 보고서의 향상된 기능 <!--677150-->
성능 향상을 위해 디바이스 작업 보고서를 개선했습니다. 또한 아제 상태별로 보고서를 필터링 수 있습니다. 예를 들어 완료된 디바이스 동작만 표시하도록 보고서를 필터링할 수 있습니다.

### <a name="custom-app-categories---748805--"></a>사용자 지정 앱 범주 <!--748805-->
이제 Intune에 추가하는 앱의 범주를 만들고, 편집하고, 할당할 수 있습니다. 현재 범주는 영어로만 지정할 수 있습니다.
[Intune에 앱을 추가하는 방법](apps-add.md)을 참조하세요.

### <a name="assign-lob-apps-to-users-with-unenrolled-devices---748823--"></a>등록 취소된 디바이스 사용자에게 LOB 앱 할당 <!--748823-->
디바이스가 Intune에 등록되었는지 여부와 상관없이 이제 저장소에서 사용자에게 LOB(기간 업무) 앱을 할당할 수 있습니다. 사용자 디바이스가 Intune에 등록되지 않은 경우 회사 포털 앱 대신에 회사 포털 웹 사이트로 이동하여 설치해야 합니다.

### <a name="new-compliance-reports---846671--"></a>새로운 규정 준수 보고서 <!--846671-->
이제 준수 보고서에 회사 디바이스의 준수 포스처가 제공되므로 사용자에게 발생한 준수 관련 문제를 신속하게 해결할 수 있습니다. 확인할 수 있는 정보

- 디바이스의 전체 준수 상태
- 개별 설정에 대한 준수 상태
- 개별 정책에 대한 준수 상태

또한 이러한 보고서에서 개별 디바이스로 드릴다운하여 해당 디바이스에 영향을 주는 특정 설정 및 정책을 볼 수 있습니다.

<!--- You can now create an edition upgrade policy to upgrade devices to the following additional Windows 10 editions:

- Windows 10 Professional
- Windows 10 Professional N
- Windows 10 Professional Education
- Windows 10 Professional Education N --->

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 등록 시나리오에 직접 액세스 <!--951869-->
2017년 1월 이후에 만든 Intune 계정은 Azure 포털에서 디바이스 등록 워크로드를 사용하여 Apple 등록 시나리오에 직접 액세스할 수 있습니다. 이전에는 Azure Portal의 링크를 통해서만 Apple 등록 미리 보기에 액세스할 수 있었습니다. 2017년 1월 이전에 만든 Intune 계정은 일회성 마이그레이션을 수행해야 Azure에서 이러한 기능을 사용할 수 있습니다. 마이그레이션 일정은 아직 공지되지 않았지만 가능한 한 빠른 시일 내에 세부 정보가 제공될 예정입니다. 기존 계정에서 미리 보기에 액세스할 수 없는 경우 평가판 계정을 만들어 새로운 경험을 테스트해 보는 것이 좋습니다.


<!-- ########################## -->
## <a name="february-2017"></a>2017 년 2월

### <a name="ability-to-restrict-mobile-device-enrollment---747600-795782--"></a>모바일 디바이스 등록을 제한하는 기능 <!--747600, 795782-->
Intune은 등록할 수 있는 모바일 디바이스 플랫폼을 제어하는 새로운 등록 제한을 추가합니다. Intune은 모바일 디바이스 플랫폼을 iOS, macOS, Android, Windows 및 Windows Mobile로 구분합니다.

* 모바일 디바이스 등록을 제한해도 PC 클라이언트 등록은 제한되지 않습니다.  
* iOS 및 Android에 한해, 개인 소유 디바이스의 등록을 차단하는 한 가지 추가 옵션이 있습니다.

Intune은 [이 문서](device-enrollment.md)에 설명된 대로 IT 관리자가 회사 소유로 표시하기 위한 조치를 취하지 않은 한 모든 새 디바이스를 개인 소유 디바이스로 표시합니다.

### <a name="view-all-actions-on-managed-devices---677150--"></a>관리 되는 디바이스에 관한 모든 작업 보기 <!--677150-->
새 __디바이스 작업__ 보고서에는 디바이스의 공장 재설정과 같은 원격 작업을 수행한 사람이 누구인지 표시되며, 추가로 작업의 상태도 표시됩니다. [디바이스 관리란?](device-management.md)을 참조하세요.

### <a name="non-managed-devices-can-access-assigned-apps---664691--"></a>관리되지 않은 디바이스에서 할당된 앱에 액세스 가능 <!--664691-->
회사 포털 웹 사이트 디자인 변경의 일환으로, iOS 및 Android 사용자가 자기에게 할당된 앱을 관리되지 않는 디바이스에 "등록 없이 사용 가능"으로 설치할 수 있습니다. 사용자는 Intune 자격 증명을 사용하여 회사 포털 웹 사이트에 로그인하고 자기에게 할당된 앱의 목록을 볼 수 있습니다. "등록 없이 사용 가능" 앱의 앱 패키지는 회사 포털 웹 사이트를 통해 다운로드할 수 있습니다. 설치하려면 등록이 필요한 앱은 사용자가 앱을 설치하려 할 때 등록하라는 메시지가 표시되므로 이 변경의 영향을 받지 않습니다.

### <a name="custom-app-categories---748805--"></a>사용자 지정 앱 범주 <!--748805-->
이제 Intune에 추가하는 앱의 범주를 만들고, 편집하고, 할당할 수 있습니다. 현재 범주는 영어로만 지정할 수 있습니다.
[Intune에 앱을 추가하는 방법](apps-add.md)을 참조하세요.

### <a name="display-device-categories---814654--"></a>디바이스 범주 표시 <!--814654-->
이제 디바이스 목록에서 디바이스 범주를 열로 표시할 수 있습니다. 디바이스 속성 블레이드의 속성 섹션에서 범주를 편집할 수도 있습니다. [Intune에 앱을 추가하는 방법](apps-add.md)을 참조하세요.

### <a name="configure-windows-update-for-business-settings---776716--"></a>비즈니스용 Windows 업데이트 설정 구성 <!--776716-->

Windows as a Service는 Windows 10 업데이트를 제공하는 새로운 서비스입니다. Windows 10부터는 새로운 기능 업데이트나 품질 업데이트에 모든 이전 업데이트의 내용이 포함됩니다. 따라서 최신 업데이트를 설치하면 Windows 10 디바이스가 완전히 최신 상태가 됩니다. 이전 버전의 Windows와 달리, 이제는 일부 업데이트가 아니라 전체 업데이트를 설치해야 합니다.

비즈니스용 Windows 업데이트를 사용하면 디바이스 그룹의 개별 업데이트를 승인할 필요가 없도록 업데이트 관리 환경을 단순화할 수 있습니다. 업데이트 출시 전략을 구성하여 현재 환경의 위험을 관리할 수 있으며 Windows 업데이트를 통해 적시에 업데이트가 설치됩니다. Microsoft Intune에서는 디바이스에서 업데이트 설정을 구성하는 기능 및 업데이트 설치를 지연하는 기능을 제공합니다. Intune에서는 업데이트를 저장하지 않고 업데이트 정책 할당만 저장합니다. 디바이스는 업데이트를 위해 Windows 업데이트에 직접 액세스합니다. Intune을 사용하여 **Windows 10 업데이트 링**을 구성 및 관리합니다. 업데이트 링에는 Windows 10 업데이트 설치 시기와 방법을 구성하는 설정 그룹이 포함됩니다. 자세한 내용은 [비즈니스용 Windows 업데이트 설정 구성](windows-update-for-business-configure.md)을 참조하세요.
