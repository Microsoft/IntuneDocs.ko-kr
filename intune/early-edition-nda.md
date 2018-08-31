---
title: 초기 버전
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e24414d28b8adeae7dfbedb606ca1a7d21497a3f
ms.sourcegitcommit: 698af815f6de2c4f003f6da428bbfb0680daafa0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43093200"
---
# <a name="the-early-edition-for-microsoft-intune---august-2018"></a>Microsoft Intune 초기 버전 - 2018년 8월

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

<!-- 1808 start -->

### <a name="windows-hello-will-target-users-and-devices----1106609---"></a>Windows Hello는 사용자 및 장치를 대상으로 함 <!-- 1106609 -->
[비즈니스용 Windows Hello](windows-hello.md) 정책을 만들면 조직 내의 모든 사용자(테넌트 수준)에게 적용됩니다. 이 업데이트를 사용하면 장치 구성 정책을 사용하여 특정 사용자 또는 특정 장치에 정책을 적용할 수도 있습니다(**장치 구성** > **프로필** > **프로필 만들기** > **ID 보호** > **비즈니스용 Windows Hello**).

Windows Hello 구성 및 설정은 Azure Portal의 Intune에서 **장치 등록** 및 **장치 구성**에 모두 존재합니다. **장치 등록**은 전체 조직(테넌트 수준)을 대상으로 하며 Windows AutoPilot(OOBE)을 지원합니다. **장치 구성**은 체크 인 중에 적용되는 정책을 사용하는 장치와 사용자를 대상으로 합니다.

적용 대상:  
- Windows 10 이상
- Windows Holographic for Business

### <a name="control-s-mode-on-windows-10-and-later-devices---public-preview----1958649---"></a>Windows 10 이상의 장치에서 S 모드 제어 - 공개 미리 보기 <!-- 1958649 -->
Windows 10 장치를 S 모드에서 전환하거나 사용자가 S 모드에서 장치를 전환하지 못하게 하는 장치 구성 프로필을 만들 수 있습니다. 이 기능은 Intune > **장치 구성** > **프로필** >  **Windows 10 이상** > **버전 업그레이드 및 모드 전환**에 있습니다.
[Windows 10 S 모드 소개](https://www.microsoft.com/windows/s-mode)에서 S 모드에 대한 자세한 정보를 제공합니다.
적용 대상: Windows 10 이상(1809 이상)

### <a name="modern-vpn-support-updates-for-ios----2459928-1819876-and-2650856---"></a>iOS에 대한 최신 VPN 지원 업데이트 <!-- 2459928, 1819876, and 2650856 -->
향후 업데이트에서 지원하는 iOS VPN 클라이언트는 다음과 같습니다. 
- F5 Access(버전 3.0.1 이상)
- Citrix SSO
- Palo Alto Networks GlobalProtect(버전 5.0 이상). 또한 향후 업데이트에서는 다음과 같이 적용됩니다.
- F5 브랜딩 업데이트에 따라 기존 **F5 Access** 연결 형식의 이름이 **F5 Access Legacy**로 변경됩니다.
- Palo Alto 브랜딩 업데이트에 따라 기존 **Palo Alto Networks GlobalProtect** 연결 형식의 이름이 **Legacy Palo Alto Networks GlobalProtect**로 변경됩니다. 

이러한 연결 형식의 기존 프로필은 레거시 VPN 클라이언트에서 계속 사용됩니다. iOS에서 Cisco Legacy AnyConnect, F5 Access Legacy, Citrix VPN 또는 Legacy Palo Alto Networks GlobalProtect를 사용하는 경우 새 앱으로 전환해야 합니다. iOS 장치에서 iOS 12로 업데이트하는 대로 가능한 한 빨리 이 작업을 수행하여 VPN 액세스를 사용할 수 있도록 합니다.

### <a name="lock-the-company-portal-in-single-app-mode-until-user-sign-in---1067692---"></a>사용자가 로그인할 때까지 회사 포털을 단일 앱 모드로 잠금 <!--1067692 --> 
DEP 등록 중에 설정 도우미 대신 회사 포털을 통해 사용자를 인증하는 경우 회사 포털은 단일 앱 모드에서 실행할 수 있습니다. 이 옵션을 사용하면 설정 도우미가 완료되는 즉시 장치를 잠그므로 사용자가 장치에 액세스하려면 로그인해야 합니다. 이 프로세스는 장치가 온보딩을 완료하고 사용자가 연결되지 않은 상태에서 분리되지 않도록 합니다.

### <a name="scope-tags-for-policies---1081974-eeready--"></a>정책에 대한 범위 태그 <!--1081974 eeready-->

범위 태그를 만들어 Intune 리소스에 대한 액세스를 제한할 수 있습니다. 역할 할당에 범위 태그를 추가한 다음, 범위 태그를 구성 프로필에 추가합니다. 역할은 일치하는 범위 태그가 있거나 범위 태그가 없는 구성 프로필이 있는 리소스에만 액세스할 수 있습니다.
범위 태그를 만들려면 **Intune 역할** > **범위(태그)** > **만들기**를 선택합니다.
역할 할당에 범위 태그를 추가하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당** > **범위(태그)** 를 차례로 선택합니다.
범위 태그를 구성 프로필에 추가하려면 **장치 구성** > **프로필** > 프로필 선택 > **속성** > **범위(태그)** 를 차례로 선택합니다.

### <a name="assign-a-user-and-friendly-name-to-an-autopilot-device---1346521---"></a>Autopilot 장치에 사용자 및 식별 이름 할당 <!--1346521 -->
향후의 공개 미리 보기를 통해 관리자는 사용자를 단일 AutoPilot 장치에 할당할 수 있습니다.  또한 관리자는 AutoPilot을 사용하여 장치를 설정할 때 사용자에게 친숙한 식별 이름도 지정할 수 있습니다.

적용 대상: Windows 참가자 1809 이상 빌드(미리 보기 동안).

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>다른 MDM에서 사용하는 Apple VPP 토큰 <!-- 1488946 -->
Intune과 다른 MDM에서 모두 Apple VPP(대량 구매 프로그램) 토큰을 사용하고 있으면 Intune에서 세부 정보를 검색하고 표시합니다.

### <a name="packet-tunnel-support-for-ios-per-app-vpn-profiles-for-custom-and-pulse-secure-connection-types----1520957---"></a>사용자 지정 및 Pulse Secure 연결 형식에 대한 iOS 앱당 VPN 프로필의 패킷 터널 지원 <!-- 1520957 -->
iOS 앱당 VPN 프로필을 사용할 때 앱 계층 터널링(app-proxy) 또는 패킷 수준 터널링(packet-tunnel)을 사용할 수 있습니다. 이러한 옵션을 사용할 수 있는 연결 형식은 다음과 같습니다.
- 사용자 지정 VPN
- Pulse Secure. 사용할 값을 모르는 경우 VPN 공급자의 설명서를 참조하세요.
적용 대상: iOS

### <a name="zscaler-is-an-available-connection-for-vpn-profiles-on-ios----1769858-eeready---"></a>Zscaler는 iOS의 VPN 프로필에 사용할 수 있는 연결임 <!-- 1769858 eeready -->
iOS VPN 장치 구성 프로필을 만드는 경우(**장치 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼 > **VPN** 프로필 유형), Cisco, Citrix 등과 같은 몇 가지 연결 형식이 있습니다. Zscaler는 향후 업데이트에서 연결 형식으로 추가됩니다. 
[iOS를 실행하는 장치에 대한 VPN 설정](vpn-settings-ios.md)에는 사용 가능한 연결 형식이 나열되어 있습니다.

### <a name="block-windows-personal-device-enrollments----1849498---"></a>Windows 개인 장치 등록 차단 <!-- 1849498 -->
Intune에서 [모바일 장치 관리](windows-enroll.md)를 사용하여 Windows 개인 장치를 등록하지 못하도록 차단할 수 있습니다. [Intune PC 에이전트](manage-windows-pcs-with-microsoft-intune.md)를 통해 등록된 장치는 이 기능을 사용하여 차단할 수 없습니다.
이 기능을 확인하려면 **장치 등록** > **장치 제한 사항**을 선택합니다.
이 제한 사항을 설정하더라도 이미 등록된 장치에는 아무런 영향을 주지 않습니다.
제한 사항이 설정되면 Intune에서 각각의 새 Windows 등록 요청이 회사 등록 권한으로 부여되었는지 확인합니다. 다음은 회사 등록 권한으로 부여된 것으로 인정되는 방법입니다.
- 등록하는 사용자가 [장치 등록 관리자 계정]( device-enrollment-manager-enroll.md)을 사용하고 있습니다.
- 장치에서 [Windows Autopilot](enrollment-autopilot.md)을 통해 등록합니다.
- 장치의 IMEI 번호가 **장치 등록** > **[회사 장치 식별자]( corporate-identifiers-add.md)** 에 나열되어 있습니다.
- 장치에서 [대량 프로비전 패키지](windows-bulk-enroll.md)를 통해 등록합니다.
- 장치에서 [SCCM에서 공동 관리를 위한 자동 등록](https://docs.microsoft.com/sccm/core/clients/manage/co-management-overview#how-to-configure-co-management)을 통해 등록합니다.

권한이 없는 등록은 차단됩니다. Intune에서 회사로 표시되지만 Intune 관리자가 장치별 제어를 제공하지 않으므로 차단되는 등록은 다음과 같습니다.
- [Windows 설치 중에 Azure Active Directory 조인](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)을 사용한 [자동 MDM 등록](windows-enroll.md#enable-windows-10-automatic-enrollment).
- [Windows 설치 프로그램에서 Azure Active Directory 조인](https://docs.microsoft.com/azure/active-directory/device-management-azuread-joined-devices-frx.md)을 사용한 [자동 MDM 등록](windows-enroll.md#enable-windows-10-automatic-enrollment).

또한 차단되는 개인 등록 방법도 다음과 같습니다.
- [Windows 설정에서 회사 계정 추가](https://docs.microsoft.com/azure/active-directory/user-help/device-management-azuread-registered-devices-windows10-setup)를 사용한 [자동 MDM 등록](windows-enroll.md#enable-windows-10-automatic-enrollment)
- Windows 설정의 [MDM 등록만]( https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device) 옵션

### <a name="specify-machine-name-patterns-in-an-autopilot-profile---1849855--"></a>Autopilot 프로필에 머신 이름 패턴 지정 <!--1849855-->
Autopilot 등록 중에 컴퓨터 이름 템플릿을 지정하여 [컴퓨터 이름](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp)을 생성하고 설정할 수 있습니다. 이 패턴은 **장치 등록** > **Windows 등록** > **Windows Autopilot 배포 서비스** > **프로필**에 있는 Autopilot 프로필에서 지정해야 합니다. 영숫자 및 하이픈 문자만 사용할 수 있습니다.
적용 대상: Windows 참가자 1809 이상 빌드(미리 보기 동안).

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>iOS 버전 번호 및 빌드 번호 표시 <!-- 1892471 -->
**준수 준수** > **장치 준수**에서 iOS 운영체제 버전이 표시됩니다. 향후 업데이트에서는 빌드 번호도 표시됩니다.
보안 업데이트가 릴리스되는 경우 Apple에서는 일반적으로 버전 번호는 그대로 유지하지만 빌드 번호는 업데이트합니다. 빌드 번호가 표시되면 취약성 업데이트가 설치되어 있는지 쉽게 확인할 수 있습니다.

### <a name="for-windows-autopilot-profiles-hide-the-change-account-options-on-the-company-sign-in-page-and-domain-error-page---1901669---"></a>Windows Autopilot 프로필의 경우 회사 로그인 페이지 및 도메인 오류 페이지에서 계정 변경 옵션을 숨김 <!--1901669 -->
공개 미리 보기에는 관리자가 회사 로그인 및 도메인 오류 페이지에서 계정 변경 옵션을 숨기는 새 Windows Autopilot 프로필 옵션이 포함됩니다. 이러한 옵션을 숨기려면 Azure Active Directory에서 회사 브랜딩을 구성해야 합니다. 적용 대상: Windows 참가자 1809 이상 빌드(미리 보기 동안).

### <a name="delay-when-ios-software-updates-are-shown-on-the-device----1949583---"></a>장치에 표시될 때의 iOS 소프트웨어 업데이트 지연 <!-- 1949583 -->
Intune > **소프트웨어 업데이트** > **iOS용 정책 업데이트**에서 장치에 업데이트를 설치하지 않으려는 일 수와 시간을 구성할 수 있습니다. 향후 업데이트에서는 소프트웨어 업데이트가 장치에 표시될 때 해당 업데이트를 1-90일 동안 지연시킬 수 있습니다. 
[Microsoft Intune에서 iOS 업데이트 정책 구성](software-updates-ios.md)에는 현재 설정이 나열되어 있습니다.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>장치 준수 대시보드에 사용 중지된 장치가 있음 <!-- 1981119 -->
향후 업데이트에서는 사용 중지된 장치가 장치 준수 대시보드에서 제거됩니다. 이에 따라 규정 준수 번호도 변경됩니다.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트<!--2000968 -->
고객의 의견에 따라 새로운 기능이 회사 포털 웹 사이트에 추가됩니다. Android, iOS 및 Windows 장치의 기존 기능과 유용성이 크게 향상됩니다. 장치 세부 정보, 피드백, 지원 및 장치 개요와 같은 사이트 영역은 응답성이 높은 최신의 새로운 디자인을 제공합니다. 또한 다음을 확인할 수 있습니다.
- 모든 장치 플랫폼에서 간소화된 워크플로
- 향상된 장치 식별 및 등록 흐름
- 더 유용한 오류 메시지
- 더 친숙한 언어, 더 이해하기 쉬운 기술 용어
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 향상
- 향상된 모든 사용자에 대한 접근성

### <a name="office-365-proplus-version----2213968-eeready---"></a>Office 365 ProPlus 버전 <!-- 2213968 eeready -->
Intune을 사용하여 Office 365 ProPlus 앱을 Windows 10 장치에 할당하는 경우 Office 버전을 선택할 수 있습니다. Azure Portal에서 **Microsoft Intune** > **앱** > **앱 추가**를 차례로 선택합니다. 그런 다음, **형식** 드롭다운 목록에서 **Office 365 ProPlus 제품군(Windows 10)** 을 선택합니다. 연결된 블레이드를 표시하려면 **앱 제품군 설정**을 선택합니다. **업데이트 채널**을 **매월**과 같은 값으로 설정합니다. 필요에 따라 **예**를 선택하여 최종 사용자 장치에서 다른 버전의 Office(msi)를 제거합니다. 최종 사용자 장치에서 선택한 채널에 대한 특정 버전의 Office를 설치하려면 **특정**을 선택합니다. 여기서는 사용할 Office의 **특정 버전**을 선택할 수 있습니다. 사용 가능한 버전은 시간이 지남에 따라 변경됩니다. 따라서 새 배포를 만들 때 사용 가능한 버전이 최신 버전일 수 있으며 이전 버전이 제공되지 않을 수 있습니다. 현재 배포에서는 이전 버전을 계속 배포하지만, 버전 목록은 채널별로 지속적으로 업데이트됩니다. 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://docs.microsoft.com/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.

### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470---"></a>설정 도우미 수행 중에 일부 화면을 건너뛰도록 프로필 구성 <!-- 2276470 -->
macOS 등록 프로필을 만들 때, 사용자가 설정 도우미를 수행할 때 다음 화면 중 하나를 건너뛰도록 구성할 수 있습니다.
- Android 마이그레이션
- 표시 색상
- 개인 정보 취급 방침
- iCloudStorage

### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>온-프레미스 커넥터에 대한 업데이트 프로세스 변경 <!-- 2277554 -->
고객의 의견에 따라 온-프레미스 커넥터가 업데이트되는 방식이 변경됩니다. 온-프레미스 커넥터를 처음 설치하면 업데이트가 자동으로 수행됩니다. 이 변경은 Microsoft Intune용 새 PFX 인증서 커넥터를 사용하여 시작되며 이후에는 다른 유형의 온-프레미스 커넥터로 롤아웃됩니다. 

### <a name="support-for-register-dns-setting-for-windows-10-vpn----2282852---"></a>Windows 10 VPN에 대한 DNS 등록 설정 지원 <!-- 2282852 -->
사용자 지정 프로필을 사용하지 않고도 VPN 인터페이스에 할당된 IP 주소를 내부 DNS와 동적으로 등록하도록 Windows 10 VPN 프로필을 구성할 수 있습니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에는 현재 사용 가능한 VPN 프로필 설정이 나열되어 있습니다. 

### <a name="restricts-apps-and-block-access-to-company-resources-on-ios-and-android-for-work-devices----2451462---"></a>응용 프로그램을 제한하고, iOS 및 Android for Work 장치의 회사 리소스에 대한 액세스를 차단함 <!-- 2451462 -->
**장치 준수** > **정책** > **정책 만들기** > **Android for Work** > **시스템 보안**에는 새로운 **제한된 응용 프로그램** 설정이 있습니다. 특정 응용 프로그램이 장치에 설치되어 있는 경우 이 새로운 설정은 준수 정책을 사용하여 회사 리소스에 대한 액세스를 차단합니다. 제한된 응용 프로그램이 장치에서 제거될 때까지 장치는 정책을 준수하지 않는 것으로 간주됩니다.
적용 대상: 
- iOS

### <a name="export-azure-classic-portal-compliance-policies-to-csv-file----2469637---"></a>Azure 클래식 포털 준수 정책을 .csv 파일로 내보내기 <!-- 2469637 -->
Azure 클래식 포털에서 만든 준수 정책은 더 이상 사용되지 않습니다.  이 경우 기존 정책은 검토하여 삭제할 수 있지만 업데이트할 수는 없습니다. 정책을 쉼표로 구분된 파일(.csv 파일)로 내보낼 수 있습니다. 그런 다음, 파일의 세부 정보를 사용하여 Intune Azure Portal에서 이러한 정책을 다시 만듭니다.
> [!IMPORTANT]
> Azure 클래식 포털이 사용 중지되면 정책을 볼 수 없는 경우를 포함하여 정책에 액세스할 수 없습니다. 따라서 Azure 클래식 포털이 사용 중지되기 전에 Azure Portal에서 이러한 정책을 내보내고 다시 만들어야 합니다.

### <a name="change-terminology-to-retire-and-wipe----2175759---"></a>“사용 중지” 및 “초기화” 용어 변경 <!-- 2175759 -->
Graph API와 일관성을 유지하도록 Intune 사용자 인터페이스 및 설명서에서 다음 용어가 변경됩니다.
- **회사 데이터 제거**가 **사용 중지**로 변경됩니다.
- **출하 시 설정으로 초기화**가 **초기화**로 변경됩니다.

### <a name="delete-jamf-devices----2653306---"></a>Jamf 장치 삭제 <!-- 2653306 -->
**장치** > Jamf 장치 선택 > **삭제**로 이동하여 JAMF 관리 장치를 삭제할 수 있습니다.

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

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>구성 프로필에 자동으로 추가된 Windows Defender ATP 구성 패키지 <!-- 2144658 -->
Intune에서 [고급 위협 보호 및 온보딩](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) 장치를 사용하는 경우 현재 구성 패키지를 다운로드하고, 구성 프로필에 추가합니다. 향후 업데이트에서 Intune은 Windows Defender Security Center에서 패키지를 자동으로 가져오고, 프로필에 추가합니다.

Windows 10 이상에 적용됩니다.

### <a name="check-for-sccm-compliance----2192052---"></a>SCCM 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 SCCM(System Center Configuration Manager) 준수 설정이 포함됩니다(**장치 준수** > **정책** > **정책 만들기** > **Windows 10**). SCCM은 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 SCCM 신호에 "준수"를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 장치에 설치해야 합니다. SCCM에서 이 요구 사항은 "설치됨" 상태를 갖습니다. 장치의 프로그램이 알 수 없는 상태에 있는 경우 장치는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>회사 포털 사전 프로비전에 사용되는 VPP 토큰을 삭제하는 데 필요한 확인 <!-- 2237634 -->
DEP 등록 중 회사 포털을 사전 프로비전하는 데 VPP(대량 구매 프로그램) 토큰이 사용되는 경우 이를 삭제하는 데 확인이 필요합니다.

#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Windows 설치 관리자에 대한 보안 설정 추가 <!-- 2282430 -->
사용자가 앱 설치를 제어하도록 허용할 수 있습니다. 사용하도록 설정한 경우 그렇지 않으면 보안 위반으로 인해 중지될 수 있는 설치를 계속 진행하도록 허용합니다. 시스템에 모든 프로그램을 설치할 때 Windows 설치 관리자가 상승된 권한을 사용하도록 지시할 수 있습니다. 또한 인덱싱될 WIP(Windows Information Protection) 항목 및 암호화되지 않은 위치에 저장된 WIP 항목에 대한 메타데이터를 사용할 수 있습니다. 정책을 사용하지 않을 때 WIP로 보호되는 항목은 인덱싱되지 않고 Cortana 또는 파일 탐색기의 결과에 표시되지 않습니다. 이러한 옵션에 대한 기능은 기본적으로 사용할 수 없게 설정됩니다. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 차단할 수 있는 타사 키보드 <!-- 1248481 -->
iOS 장치에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(응용 프로그램 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 장치 사용자에게 표시되지 않습니다. 대화 메시지가 장치 사용자에게 한 번만 표시됩니다. 

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

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>콜드 앱 시작 및 시간 제한 시 비생체 인식 암호 필요 <!-- 1506985 --> 

콜드 앱 시작 시 및 관리자 지정 시간 제한 후에 비생체 인식 암호를 요구하면, Intune에서 회사 데이터에 액세스하는 데 생체 인식 ID를 사용하는 것을 제한하여 MAM(모바일 응용 프로그램 관리) 지원 앱에 향상된 보안을 제공합니다. 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 기타 미래의 생체 인식 인증 방법을 사용하여 APP/MAM 지원 응용 프로그램에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 세부적으로 제어하여 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 장치로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **모바일 앱** > **응용 프로그램 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다.

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



