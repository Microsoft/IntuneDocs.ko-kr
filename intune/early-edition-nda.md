---
title: 초기 버전
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bacaf8ff4119d4cd40483b65ea45e283d98a51f1
ms.sourcegitcommit: 814d1d473de2de2e735efab826b1091de2b093f5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51025205"
---
# <a name="the-early-edition-for-microsoft-intune---november-2018"></a>Microsoft Intune 초기 버전 - 2018년 11월

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

<!-- 1811 start -->

### <a name="uninstalling-apps-on-corporate-owned-supervised-ios-devices----1281677---"></a>회사 소유의 감독되는 iOS 장치에서 앱 제거 <!-- 1281677 -->
회사 소유의 감독되는 iOS 장치에서 앱을 제거할 수 있습니다. **제거** 할당 유형을 사용하여 사용자 또는 장치 그룹을 대상으로 하여 앱을 제거할 수 있습니다. 개인 또는 감독되지 않은 iOS 장치의 경우 Intune을 사용하여 설치된 앱만 계속 제거할 수 있습니다.

### <a name="support-for-ios-12-oauth-in-ios-email-profiles---2155106---"></a>iOS 메일 프로필에서 iOS 12 OAuth 지원 <!--2155106 -->
Intune의 iOS 메일 프로필은 iOS 12 OAuth를 지원합니다. 이 기능을 표시하려면 **Intune** > **장치 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다. 프로필 만들기 블레이드에서 **OAuth**를 사용하거나 사용하지 않도록 설정할 수 있습니다. 이 설정이 작동되면 발생하는 두 가지 상황은 다음과 같습니다.
1. 이미 대상으로 지정된 장치에 새 프로필이 발행됩니다.
2. 최종 사용자에게 자격 증명을 묻는 메시지가 다시 표시됩니다.

### <a name="track-installation-of-office-proplus---2620217--"></a>Office ProPlus 설치 추적 <!--2620217-->
[등록 상태 페이지](windows-enrollment-status.md)를 사용하여 [Office ProPlus](apps-add-office365.md)의 설치 진행률을 추적할 수 있습니다.

### <a name="macos-device-enrollment-program-support-for-apple-school-manager-accounts---3006133--"></a>Apple School Manager 계정에 대한 macOS 장비 등록 프로그램 지원 <!--3006133-->
Intune은 Apple School Manager 계정에 대한 macOS 장치에서 장비 등록 프로그램을 사용할 수 있도록 지원합니다.

### <a name="temporarily-pause-kiosk-mode-on-android-devices-to-make-changes----3041935---"></a>Android 장치에서 키오스크 모드를 일시적으로 중지하여 변경 <!-- 3041935 -->
다중 앱 키오스크 모드에서 Android 장치를 사용하는 경우 IT 관리자가 장치를 변경해야 할 수 있습니다. 새 다중 앱 키오스크 설정은 IT 관리자가 PIN을 사용하여 일시적으로 키오스크 모드를 중지하고 전체 장치에 액세스할 수 있게 합니다.
현재 키오스크 설정을 확인하려면 [Android 키오스크 설정](android-kiosk-settings.md)을 참조하세요.

### <a name="set-custom-background-in-managed-home-screen-app-----3041945---"></a>관리 홈 화면(Managed Home Screen) 앱에서 사용자 지정 배경 설정 <!-- 3041945 -->
Android 엔터프라이즈, 다중 앱, 키오스크 모드 장치에서 관리 홈 화면 앱의 배경 모양을 사용자 지정할 수 있는 설정을 추가합니다.  **사용자 지정 URL 배경**을 구성하려면 Azure Portal에서 Intune > 장치 구성으로 차례로 이동합니다. 현재 장치 구성 프로필을 선택하거나 새 프로필을 만들어 키오스크 설정을 편집합니다.

### <a name="enable-virtual-home-button-on-android-enterprise-kiosk-devices-----3042021---"></a>Android 엔터프라이즈 키오스크 장치에서 가상 홈 단추 사용 <!-- 3042021 -->
사용자는 새 설정을 통해 해당 장치의 소프트 키 단추를 탭하여 관리 홈 화면 앱과 다중 앱 키오스크 장치에 할당된 다른 앱 간에 전환할 수 있습니다. 이 설정은 사용자의 키오스크 앱에서 "뒤로" 단추에 적절하게 응답하지 않는 시나리오에서 특히 유용합니다. 회사 소유의 단일 사용 Android 장치에 이 설정을 구성할 수 있습니다. **가상 홈 단추**를 사용하거나 사용하지 않도록 설정하려면 Azure Portal에서 Intune > 장치 구성으로 차례로 이동합니다. 현재 장치 구성 프로필을 선택하거나 새 프로필을 만들어 키오스크 설정을 편집합니다.

### <a name="app-protection-policy-assignment-save-and-apply----3104570---"></a>앱 보호 정책 할당 저장 및 적용 <!-- 3104570 -->
앱 보호 정책 할당은 더 효율적으로 제어할 수 있습니다. 앱 보호 정책 할당을 저장하고 적용하면 의도한 사용자만 앱 보호 할당 정책의 영향을 직접 받습니다.

### <a name="new-microsoft-edge-browser-settings-for-windows-10-and-later----3174639---"></a>Windows 10 이상에 대한 새 Microsoft Edge 브라우저 설정 <!-- 3174639 -->
장치에서 Microsoft Edge 브라우저를 제어하고 관리하는 데 도움이 되는 새 설정이 추가됩니다. 현재 설정 목록은 [Windows 10(이상)에 대한 장치 제한](device-restrictions-windows-10.md#edge-browser)을 참조하세요.

### <a name="select-apps-tracked-on-the-enrollment-status-page---2531007---"></a>등록 상태 페이지에서 추적되는 앱 선택 <!-- 2531007 -->
등록 상태 페이지에서 추적할 앱을 선택할 수 있습니다.

### <a name="intune-app-protection-policies-ui-update----3251427---"></a>Intune 앱 보호 정책 UI 업데이트 <!-- 3251427 -->

Intune 앱 보호 정책을 사용하면 Microsoft Outlook 및 Word와 같이 Intune으로 보호되는 앱에 대한 다양한 데이터 보호 설정을 구성할 수 있습니다. 설정과 단추 레이블을 변경하여 각각을 더 쉽게 이해할 수 있게 합니다. **예**/**아니요** 컨트롤에서 기본 **차단**/**허용** 및 **사용 안 함**/**사용** 컨트롤로 변경되고, 레이블도 쉽게 구별할 수 있도록 업데이트됩니다. 설정도 다시 포맷되므로 설정과 레이블이 컨트롤에 나란히 있어 탐색이 더 효율적으로 향상됩니다. 기본 설정과 설정 수는 동일하게 유지되지만, 이 변경으로 인해 사용자가 선택한 앱 보호 정책을 적용하기 위해 설정을 더 쉽게 이해, 탐색 및 활용할 수 있습니다.



<!-- 1810 start -->

### <a name="use-microsoft-recommended-settings-with-security-baselines----2055484---"></a>Microsoft 권장 설정을 보안 기준과 함께 사용<!-- 2055484 -->
Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 종단 간 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 후 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 장치가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 장치나 사용자에 대해 관리자에게 알립니다.

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


### <a name="deployed-wip-policies-without-user-enrollment----1434452---"></a>사용자 등록 없이 배포된 WIP 정책 <!-- 1434452 -->
WIP(Windows Information Protection) 정책은 MDM 사용자가 Windows 10 장치를 등록하지 않고 배포할 수 있습니다. 이 구성을 사용하면 회사는 WIP 구성을 기반으로 회사 문서를 보호할 수 있는 한편 사용자는 자신의 Windows 장치를 관리할 수 있습니다. 문서가 WIP 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 장치를 선택하고 초기화 요청을 보내면 WIP 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.


<!-- 1809 start -->  

### <a name="app-protection-policy-app-settings-for-web-data----2662995---"></a>웹 데이터에 대한 APP(앱 보호 정책) 설정 <!-- 2662995 -->
Android 및 iOS 장치의 웹 콘텐츠에 대한 APP 정책 설정은 iOS 유니버설 링크 및 Android 앱 링크를 통한 데이터 전송을 비롯하여 http 및 https 웹 링크를 모두 더 잘 처리하기 위해 업데이트됩니다.  

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

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Configuration Manager 준수 확인 <!-- 2192052 -->
향후 업데이트에는 새 System Center Configuration Manager 준수 설정이 포함됩니다(**장치 준수** > **정책** > **정책 만들기** > **Windows 10**). Configuration Manager는 Intune 준수에 신호를 보냅니다. Intune 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 장치에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 장치의 프로그램이 알 수 없는 상태에 있는 경우 장치는 Intune에서 비준수가 됩니다.

적용 대상: Windows 10 이상

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>VPP 토큰 만료 또는 회사 포털 라이선스 부족에 대한 경고 <!-- 2237572 -->
VPP(대량 구매 프로그램)를 사용하여 DEP 등록 중 회사 포털을 사전 프로비전하는 경우 Intune은 VPP 토큰이 만료되려고 하는 경우 및 회사 포털에 대한 라이선스가 부족한 경우 경고를 표시합니다.



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>알림

이번에는 활성 알림이 없습니다.

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.



