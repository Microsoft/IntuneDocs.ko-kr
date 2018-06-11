---
title: 초기 버전
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 95ad588b084319cd8a0f5f5c5d92da0e892eed50
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34745046"
---
# <a name="the-early-edition-for-microsoft-intune---june-2018"></a>Microsoft Intune 초기 버전 - 2018년 6월

**초기 버전**에서는 Microsoft Intune의 향후 릴리스에서 도입될 기능의 목록을 제공합니다. 이 정보는 제한적으로 제공되며 변경될 수 있습니다. 회사 외부에서 이 정보를 공유하지 마세요. 여기 나열된 일부 기능은 마감일을 맞추지 못할 위험이 있으며 다음 릴리스까지 지연될 수 있습니다. 다른 기능은 고객용 준비 상태를 확인하기 위해, 파일럿(플라이팅) 테스트 중 입니다. 질문이나 궁금한 내용이 있으면 Microsoft 제품 그룹 담당자에게 연락하세요.

이 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.

> [!Note]
>Intune에 대해 다음 변경 사항을 개발 중입니다. 새로운 하이브리드 기능에 대한 자세한 내용은 [Hybrid What’s New](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)(하이브리드의 새로운 기능) 페이지를 참조하세요.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune

<!-- 1806 start -->

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Android 장치에 대한 COSU(회사 소유, 단일 사용) 지원 <!-- 1630973 -->

Intune은 고도로 관리되고 잠겨 있는 키오스크 스타일의 Android 장치를 지원합니다. 관리자는 이를 통해 장치 사용을 하나의 앱 또는 작은 앱 집합에 추가로 잠그고 사용자가 다른 앱을 사용하거나 장치에서 다른 작업을 수행하지 못하도록 차단할 수 있습니다.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Apple 장비 등록 프로그램에 대한 macOS 지원 <!-- 747651 -->

Intune은 macOS 장치를 Apple DEP(Apple 장비 등록 프로그램)에 등록할 수 있도록 지원합니다. 확인 방법은 다음과 같습니다.

1. deploy.apple.com에서 macOS 일련 번호를 MDM 서버에 할당합니다.
2. 일련 번호를 Intune으로 가져옵니다.
3. macOS 장치와 관련된 등록 프로그램 프로필을 만듭니다.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 및 Play for Work에 대한 Google 이름 변경 <!--842873 -->
Intune은 Google 브랜딩 변경 내용을 반영하도록 "Android for Work" 용어를 업데이트합니다.  "Android for Work" 및 "Play for Work" 용어는 더 이상 사용되지 않습니다. 컨텍스트에 따라 서로 다른 용어가 사용됩니다.

- "Android 엔터프라이즈"는 전반적인 최신 Android 관리 스택을 나타냅니다.
- "회사 프로필" 또는 "소유자 프로필 소유자"는 회사 프로필을 통해 관리되는 BYOD 장치를 나타냅니다.
- "관리되는 Google Play"는 Google 앱 스토어를 나타냅니다.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>장치별 iOS 앱 구성 상태 모니터링 <!-- 880037 eeready eestaged -->

Microsoft Intune 관리자는 각 관리 장치에 대한 iOS 앱 구성 상태를 모니터링할 수 있습니다. Azure Portal의 **Microsoft Intune**에서 **장치** > **모든 장치**를 차례로 선택합니다. 관리 장치 목록에서 장치에 대한 블레이드를 표시할 특정 장치를 선택합니다. 장치 블레이드에서 **앱 구성**을 선택합니다.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>iOS의 APP 설정으로 차단할 수 있는 타사 키보드 <!-- 1248481 -->
iOS 장치에서 Intune 관리자는 정책으로 보호된 앱에서 조직 데이터에 액세스할 때 타사 키보드 사용을 차단할 수 있습니다. 타사 키보드를 차단하도록 APP(응용 프로그램 보호 정책)를 설정하면, 타사 키보드를 사용하여 처음으로 회사 데이터와 상호 작용할 때 장치 사용자가 메시지를 받습니다. 기본 키보드 이외의 모든 옵션이 차단되고 장치 사용자에게 표시되지 않습니다. 대화 메시지가 장치 사용자에게 한 번만 표시됩니다. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS 장치에서 방화벽 설정을 사용하는 장치 준수 정책 만들기 <!-- 1497640 -->
새 macOS 준수 정책을 만들면(**장치 준수** > **정책** > **정책 만들기** > **플랫폼: macOS** > **시스템 보안**) 다음과 같은 일부 새 **방화벽** 설정을 사용할 수 있습니다. 
- **방화벽**: 사용자 환경에서 들어오는 연결을 처리하는 방법을 구성합니다.
- **들어오는 연결**: DHCP, Bonjour 및 IPSec과 같은 기본 인터넷 서비스에 필요한 연결을 제외한 모든 들어오는 연결을 **차단**합니다. 이 설정은 모든 공유 서비스도 차단합니다.
- **은폐 모드**: 장치에서 검색 요청에 응답하지 못하도록 은폐 모드를 **사용하도록 설정**합니다. 장치는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다.

적용 대상: macOS 10.12 이상

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>sAMAccountName을 이메일 프로필에 대한 계정 사용자 이름으로 사용 <!-- 1500307 -->

온-프레미스 **sAMAccountName**은 Android, iOS 및 Windows 10용 이메일 프로필에 대한 계정 사용자 이름으로 사용할 수 있습니다. Azure AD(Azure Active Directory)의 `domain` 또는 `ntdomain` 특성에서 도메인을 가져올 수도 있습니다. 또는 사용자 지정 정적 도메인을 입력합니다.

이 기능을 사용하려면 온-프레미스 Active Directory 환경의 `sAMAccountName` 특성을 Azure AD에 동기화해야 합니다.

적용 대상: Android, iOS, Windows 10 이상

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>앱 시작 및 시간 제한 시 비생체 인식 암호 필요 <!-- 1506985 -->

앱 시작 시 및 관리자 지정 시간 제한 후에 비생체 인식 암호를 요구하면, Intune에서 회사 데이터에 액세스하는 데 생체 인식 ID를 사용하는 것을 제한하여 MAM(모바일 응용 프로그램 관리) 지원 앱에 향상된 보안을 제공합니다. 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 기타 미래의 생체 인식 인증 방법을 사용하여 APP/MAM 지원 응용 프로그램에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 세부적으로 제어하여 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 장치로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **모바일 앱** > **응용 프로그램 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>선택적으로 조직의 앱 데이터 지우기 <!-- 1507030 -->
APP(응용 프로그램 보호 정책) 액세스 설정 조건이 충족되지 않으면 관리자가 조직의 데이터를 선택적으로 지우도록 구성할 수 있습니다.  이 기능을 사용하면 관리자가 미리 구성된 기준에 따라 응용 프로그램에서 중요한 조직 데이터를 자동으로 보호하고 제거할 수 있습니다.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>VPP를 통해 구매한 iOS 앱 해지 <!-- 1777384 -->
Microsoft Intune 관리자는 VPP(대량 구매 프로그램)를 통해 구매한 iOS 앱에 대한 라이선스를 선택적으로 해지할 수 있습니다. 앱이 더 이상 할당되지 않는 경우 사용자에게 알릴 수 있습니다. 앱 라이선스를 철회해도 장치에서 관련 VPP 앱이 제거되지 않습니다. VPP 앱을 제거하려면 할당 작업을 **제거**로 변경해야 합니다. 회수된 라이선스 수는 Intune의 **앱** 워크로드의 **사용이 허가된 앱** 노드에 반영됩니다. iOS VPP 앱과 관련된 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법](vpp-apps-ios.md)을 참조하세요.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Office 365 Pro Plus 언어 팩 <!-- 1833450 -->
Intune 관리자는 Intune을 통해 관리되는 Office 365 Pro Plus 앱에 대한 추가 언어를 배포할 수 있습니다. 사용 가능한 언어 목록에는 언어 팩 **유형**(코어, 부분 및 언어 교정)이 포함되어 있습니다. Azure Portal에서 **Microsoft Intune** > **모바일 앱** > **앱** > **추가**를 차례로 선택합니다. **앱 추가** 블레이드의**앱 유형** 목록에 있는 **Office 365 제품군** 아래에서 **Windows 10**을 선택합니다. **앱 제품군 설정** 블레이드에서 **언어**를 선택합니다.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>iOS VPP 앱 라이선스 해지 <!-- 1863797 -->
관리자는 사용자 또는 장치에 할당된 iOS VPP 앱 라이선스를 회수할 수 있습니다. iOS VPP 앱을 제거하면 앱 라이선스를 회수할 수도 있습니다. 그런 다음, 해당 앱 라이선스를 다른 사용자 또는 장치에 할당하도록 선택할 수 있습니다. iOS VPP 앱 라이선스에 대한 자세한 내용은 [Microsoft Intune에서 iOS 볼륨을 구매한 앱 관리](vpp-apps-ios.md)를 참조하세요.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968---"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트<!--2000968 -->
고객으로부터의 피드백에 기반한 새 기능을 회사 포털 웹 사이트에 추가하고 있습니다. Android, iOS 및 Windows 장치의 기존 기능과 유용성이 크게 향상됩니다. 장치 세부 정보, 피드백, 지원 및 장치 개요와 같은 사이트 영역은 응답성이 높은 최신의 새로운 디자인을 제공합니다. 또한 다음을 확인할 수 있습니다.

- 모든 장치 플랫폼에서 간소화된 워크플로
- 향상된 장치 식별 및 등록 흐름
- 더 유용한 오류 메시지
- 더 친숙한 언어, 더 이해하기 쉬운 기술 용어
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 향상
- 향상된 모든 사용자에 대한 접근성

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus 앱 배포 편집 <!-- 2150145 -->
Microsoft Intune 관리자가 Office 365 Pro Plus 앱 배포를 편집할 수 있는 기능이 향상되었습니다. Azure Portal에서 **Microsoft Intune** > **모바일 앱** > **앱**을 차례로 선택합니다. 앱 목록에서 Office 365 Pro Plus 제품군을 선택합니다.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>중복된 회사 장치 식별자의 행 단위 검토 업로드 <!-- 2203794 -->
회사 ID를 업로드할 때 Intune에서 모든 중복된 항목의 목록을 제공하고, 기존 정보를 대체하거나 유지할 수 있는 옵션을 제공합니다. **장치 등록** > **회사 장치 식별자** > **식별자 추가**를 차례로 선택한 후에 중복된 항목이 있으면 보고서가 표시됩니다. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>수동으로 회사 장치 식별자 추가 <!-- 2203803 -->
회사 장치 ID를 수동으로 추가할 수 있습니다. **장치 등록** > **회사 장치 식별자** > **추가**를 차례로 선택합니다.

### <a name="new-status-for-devices-in-device-configuration----2308882---"></a>장치 구성의 새로운 장치 상태 <!-- 2308882 -->
**장치 구성** > **개요**에 추가되는 새 상태는 다음과 같습니다.
- 성공
- 오류
- 충돌
- 보류 중
- 해당 없음. 다른 플랫폼의 장치 수를 보여 주는 이미지도 표시됩니다. 예를 들어 iOS 프로필을 보고 있는 경우 이 프로필에도 할당된 비iOS 장치의 수가 새 타일에 표시됩니다. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>장치 준수에서 타사 바이러스 백신 솔루션 지원 <!-- 2325484 -->
장치 준수 정책(**장치 준수** > **정책** > **정책 만들기** > **플랫폼: Windows 10 이상** > **설정** > **시스템 보안**)을 만들면 다음과 같은 새 **장치 보안** 옵션이 제공됩니다. 
- **바이러스 백신**: **필수**로 설정하면 Symantec과 같은 Windows 보안 센터에 등록된 바이러스 백신 솔루션을 사용하여 준수를 확인할 수 있습니다. 
- **스파이웨어 방지**: **필수**로 설정하면 Symantec과 같은 Windows 보안 센터에 등록된 스파이웨어 방지 솔루션을 사용하여 준수를 확인할 수 있습니다. 

적용 대상: Windows 10 이상 

<!-- 1805 start -->

### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GlobalProtect VPN 프로필 <!-- 1333680 eeready ! --> 지원

이 업데이트에서는 Palo Alto Networks GlobalProtect를 Intune의 VPN 프로필에 대한 VPN 연결 형식으로 선택할 수 있습니다(**장치 구성** > **프로필** > **프로필 만들기** > **프로필 형식** > **VPN**). 이 릴리스에서 지원되는 플랫폼은 다음과 같습니다. 

- iOS
- Windows 10

### <a name="set-compliance-by-device-location----851881----"></a>장치 위치별 준수 설정 <!-- 851881 ! -->
상황에 따라 회사 리소스에 대한 액세스를 네트워크 연결로 정의된 특정 위치로 제한할 수 있습니다. 장치의 IP 주소를 기반으로 준수 정책(**장치 준수** > **위치**)을 만들 수 있습니다. IP 범위를 벗어난 장치는 회사 리소스에 액세스할 수 없습니다.

적용 대상: 회사 포털 앱이 업데이트된 Android 장치 6.0 이상 

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>앱 설치에 대한 향상된 문제 해결 <!-- 928990 -->
Microsoft Intune MDM 관리 장치에서 앱 설치에 실패하는 경우도 있습니다. 이러한 앱 설치에 실패할 경우, 실패 이유를 파악하거나 문제를 해결하기 어려울 수 있습니다. Microsoft에서는 앱 문제 해결 기능의 공개 미리 보기를 제공합니다. 개별 장치 아래에서 **관리 앱**이라는 새 노드를 확인할 수 있습니다. 여기에는 Intune MDM을 통해 전달된 앱이 나열됩니다. 노드 내부에는 앱 설치 상태 목록이 표시됩니다. 개별 앱을 선택하면 해당 앱에 대한 문제 해결 보기가 표시됩니다. 문제 해결 보기에는 응용 프로그램이 언제 생성, 수정, 대상 지정 및 장치에 전달되었는지를 포함한 앱의 전체 수명 주기기 표시됩니다. 또한 앱 설치에 실패할 경우, 오류 코드 및 오류의 원인에 대한 유용한 메시지가 표시됩니다.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>콜드 앱 시작 및 시간 제한 시 비생체 인식 암호 필요 <!-- 1506985 --> 

콜드 앱 시작 시 및 관리자 지정 시간 제한 후에 비생체 인식 암호를 요구하면, Intune에서 회사 데이터에 액세스하는 데 생체 인식 ID를 사용하는 것을 제한하여 MAM(모바일 응용 프로그램 관리) 지원 앱에 향상된 보안을 제공합니다. 설정은 Touch ID(iOS), Face ID(iOS), Android 생체 인식 또는 기타 미래의 생체 인식 인증 방법을 사용하여 APP/MAM 지원 응용 프로그램에 액세스하는 사용자에게 영향을 줍니다. 이러한 설정을 사용하면 Intune 관리자가 사용자 액세스를 더 세부적으로 제어하여 여러 지문 또는 다른 생체 인식 액세스 방법을 사용하는 장치로 인해 회사 데이터가 잘못된 사용자에게 노출될 수 있는 경우를 제거할 수 있습니다. Azure Portal에서 **Microsoft Intune**을 엽니다. **모바일 앱** > **응용 프로그램 보호 정책** > **정책 추가** > **설정**을 차례로 선택합니다. 특정 설정에 대한 **액세스** 섹션을 찾습니다.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>승인되지 않은 장치 공급업체 및 모델을 기준으로 앱 액세스 차단 <!-- 1425689 ! -->
Intune IT 관리자는 Intune 앱 보호 정책을 통해 지정된 Android 제조업체 및/또는 iOS 모델 목록을 적용할 수 있습니다. IT 관리자는 Android 정책용 제조업체 및 iOS 정책용 장치 모델의 세미콜론으로 구분된 목록을 제공할 수 있습니다. Intune 앱 보호 정책은 Android 및 iOS에만 적용됩니다. 이 지정된 목록에서 수행할 수 있는 두 가지 작업은 다음과 같습니다.
- 지정되지 않은 장치에 대한 앱 액세스 차단
- 또는 지정되지 않은 장치에서 회사 데이터 선택적 초기화. 

정책을 통한 요구 사항이 충족되지 않으면 사용자가 대상 응용 프로그램에 액세스할 수 없습니다. 설정에 따라 사용자는 차단되거나 앱 내의 해당 회사 데이터에서 선택적으로 초기화될 수 있습니다. iOS 장치에서 이 기능을 사용하려면 응용 프로그램(즉, WXP, Outlook, Managed Browser, Yammer)에 참여하여 최소 버전 설정을 대상 응용 프로그램에 적용하도록 Intune 앱 SDK를 통합해야 합니다. 이 통합은 롤링 기반으로 특정 응용 프로그램 팀에서 수행합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 

최종 사용자 장치에서 Intune 클라이언트는 응용 프로그램 보호 정책에 대한 Intune 블레이드에 지정된 문자열의 단순 일치를 기반으로 동작을 수행합니다. 이 동작은 전적으로 장치가 보고하는 값에 따라 결정됩니다. 따라서 IT 관리자는 의도한 동작이 정확한지 확인하는 것이 좋습니다. 이를 확인하려면 작은 사용자 그룹을 대상으로 하는 다양한 장치 제조업체 및 모델을 기반으로 이 설정을 테스트하면 됩니다. Microsoft Intune에서 **모바일 앱** > **앱 보호 정책**을 선택하여 앱 보호 정책을 보고 추가합니다. 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 장치에서 키오스크 모드 사용 <!-- 1560072 ! -->
Windows 10 장치에서 구성 프로필을 만들고 키오스크 모드를 사용하도록 설정할 수 있습니다(**장치 구성** > **프로필** > **프로필 만들기** > **Windows 10** > **장치 제한 사항** > **키오스크**). 이 업데이트에서 **키오스크(미리 보기)** 설정은 **키오스크(사용되지 않음)** 로 이름이 바뀝니다. **키오스크(사용되지 않음)** 는 더 이상 사용하지 않는 것이 좋지만 7월 업데이트까지 계속 작동합니다. **키오스크(사용되지 않음)** 는 새로운 **키오스크** 프로필 유형(**프로필 만들기** > **Windows 10** > **키오스크(미리 보기)**)으로 바뀌고 이 프로필 유형에는 Windows 10 RS4 이상에서 키오스크를 구성하는 설정이 포함됩니다.

Windows 10 이상에 적용됩니다.

### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>키오스크 모드에서 비즈니스용 Microsoft 스토어 앱에 대한 연결된 앱 사용자 모델 ID(AUMID) 검색 <!-- 1560077 ! -->
Intune에서는 WSfB(비즈니스용 Microsoft 스토어) 앱의 앱 사용자 모델 ID(AUMID)를 검색하여 향상된 키오스크 프로필 구성을 제공할 수 있습니다.

비즈니스용 Microsoft 스토어에서 앱에 대한 자세한 내용은 [비즈니스용 Microsoft 스토어에서 앱 관리](windows-store-for-business.md)를 참조하세요.

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>앱 보호 정책에 대한 액세스 작업 <!-- 1483510 EEready -->
곧 호환되지 않는 장치를 명시적으로 초기화, 차단 또는 경고하도록 앱 보호 정책을 구성할 수 있게 됩니다. 최신 작업인 ‘초기화’는 장치에서 회사의 회사 데이터를 제거합니다. 초기화가 수행되면 장치 사용자에게는 초기화 및 수정 단계의 이유가 포함된 알림이 제공됩니다. 최소 OS 버전과 같은 일부 설정의 경우 차단 및 초기화와 같은 여러 작업을 적용할 수 있습니다. 앱이 시작되면 이러한 작업이 트리거됩니다.

### <a name="new-inventory-information-for-windows-devices----1333569-eeready---"></a>Windows 장치에 대한 새 인벤토리 정보 <!-- 1333569 eeready -->

Windows 장치의 경우 **하드웨어** 탭(**그룹** > **모든 모바일 장치** > **장치** > 사용자 장치 선택 > **속성 보기** > **하드웨어**)에서 다음 인벤토리 정보를 장치별로 사용할 수 있습니다.
- TPM
- 바이러스 백신
- 스파이웨어 방지
- 방화벽
- UAC
- 배터리
- 도메인 이름

CSP가 이 데이터를 검색하는 방법에 대한 자세한 내용은 [DeviceStatus CSP](https://docs.microsoft.com/en-us/windows/client-management/mdm/devicestatus-csp) 문서의 DeviceStatus 항목을 참조하세요.

### <a name="intune-and-the-microsoft-edge-browser----1818969---"></a>Intune 및 Microsoft Edge 브라우저 <!-- 1818969 -->
모바일 장치용 Microsoft Edge 브라우저(iOS 및 Android)는 이제 Intune 앱 보호 정책을 지원합니다. Edge 브라우저 응용 프로그램에서 회사 Azure AD 계정으로 로그인하는 사용자는 Intune에서 보호됩니다. 

### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766---"></a>Autopilot에 대한 OOBE를 구성할 경우, 새 언어 지역 설정 <!-- 1821766 -->
새 구성 설정을 통해 첫 실행 경험 중에 Autopilot 프로필에 대한 언어 및 지역을 설정할 수 있습니다.

### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>장치 키보드 구성에 대한 새 설정 <!-- 1821768 -->
새 설정을 통해 첫 실행 경험 중에 Autopilot 프로필에 대한 키보드를 구성할 수 있습니다.

### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer를 사용하여 iOS 및 MacOS 장치의 화면 공유 <!-- 1985547 -->
현재 TeamViewer를 사용하여 [Intune에서 관리되는 Android 및 Windows 장치](device-profile-android-teamviewer.md)를 원격으로 관리할 수 있습니다.

관리자는 TeamViewer에 연결하고 iOS 및 macOS 장치와 화면 공유 세션을 시작할 수 있습니다. iPhone, iPad 및 macOS 사용자는 자신의 화면을 다른 데스크톱 또는 모바일 장치와 실시간으로 공유할 수 있습니다. 

### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>장치 프로필 그래픽 사용자 차트가 다시 표시됨 <!-- 2160133 -->
장치 프로필 그래픽 차트(**장치 구성** > **프로필** > 기존 프로필 선택 > **개요**)에 표시되는 개수를 개선하기 위해 그래픽 사용자 차트가 일시적으로 제거되었습니다.

이 업데이트를 사용하면 그래픽 사용자 차트가 Azure Portal에 다시 표시됩니다.

### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>모든 사용자 및 모든 장치를 범위 그룹으로 할당 <!-- 2196803 -->
범위 그룹에서 모든 사용자, 모든 장치 및 모든 사용자/모든 장치를 할당할 수 있습니다. 이렇게 하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당**을 차례로 선택하고, 할당을 선택한 다음, **범위(그룹)** 를 선택합니다.

### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot 프로필을 대상 지정 그룹으로 이동 <!-- 1877935 -->
현재 AutoPilot 배포 프로필을 선택된 장치에 할당할 수 있습니다. 이 기능이 릴리스된 후 이러한 프로필을 할당하기 위해 다음 작업을 수행합니다.
- AutoPilot 장치가 포함된 (Azure AD) 그룹을 만듭니다.
- Azure AD 그룹에 원하는 프로필을 할당합니다. 이제 AutoPilot 프로필을 해당 그룹의 AutoPilot 장치에 할당할 수 있습니다.

### <a name="management-name-field-will-be-editable----1875989---"></a>관리 이름 필드를 편집할 수 있음 <!-- 1875989 -->
장치의 **속성** 블레이드에서 관리 이름 필드를 편집할 수 있습니다. 이 필드를 편집하려면 **장치** > **모든 장치**를 선택하고, 장치를 선택한 다음, **속성**을 선택합니다. 관리 이름 필드를 사용하여 장치를 고유하게 식별할 수 있습니다.

<!-- 1804 start -->

### <a name="additions-to-local-device-security-options-settings----1403702---"></a>로컬 장치 보안 옵션 설정에 대한 추가 <!-- 1403702 -->
Windows 10 장치에 대한 추가 로컬 장치 보안 옵션 설정을 구성할 수 있습니다. 추가 설정은 Microsoft Network Client, Microsoft Network Server, 네트워크 액세스 및 보안 및 대화형 로그온의 영역에서 사용될 수 있습니다. Windows 10 장치 구성 정책을 만들 때 Endpoint Protection 범주에서 이러한 설정을 찾아보세요.

### <a name="rules-for-removing-devices----1609459---"></a>장치 제거에 대한 규칙 <!-- 1609459 -->
설정한 일 수 동안 체크 인하지 않은 장치를 자동으로 제거할 수 있는 새 규칙이 제공됩니다. 새 규칙을 보려면 **Intune** 창으로 이동하여 **장치**를 선택하고 **장치 제거 규칙**을 선택합니다.

### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot 장치에서 소비자 앱과 경험을 방지<!-- 1621980 -->
Windows 10 Enterprise RS4 AutoPilot 장치에서 소비자 앱 및 환경을 설치하지 못하도록 방지할 수 있습니다. 이 기능을 확인하려면 **Intune** > **장치 등록** > **Windows 등록** > **Windows AutoPilot 프로필** > **새로 만들기** > **등록 설정**으로 이동합니다. 

<!-- 1803 start -->

#### <a name="multiple-exchange-connector-support----2070451---"></a>여러 Exchange Connector 지원 <!-- 2070451 -->

더 이상 테넌트당 하나의 Microsoft Intune Exchange Connector로 제한되지 않습니다. 여러 온-프레미스 Exchange 조직을 사용하여 Intune 조건부 액세스를 설치할 수 있도록 Intune은 여러 Exchange Connector를 지원합니다.

Intune 온-프레미스 Exchange Connector를 사용하여 장치가 Intune에 등록했는지 여부 및 Intune 장치 준수 정책을 준수하는지 여부에 따라 온-프레미스 Exchange 사서함에 대한 장치 액세스를 관리할 수 있습니다. 커넥터를 설정하려면 Azure Portal에서 Intune 온-프레미스 Exchange Connector를 다운로드해 이를 Exchange 조직의 서버에 설치합니다. Microsoft Intune 대시보드에서 **온-프레미스 액세스**를 선택한 다음, **설치** 아래에서 **Exchange ActiveSync Connector**를 선택합니다. Exchange 온-프레미스 Connector를 다운로드하고 Exchange 조직의 서버에 설치합니다. 더 이상 테넌트당 하나의 Exchange Connector로 제한되지 않으므로 추가 Exchange 조직이 있는 경우 동일한 다운로드 절차를 따라 각 추가 Exchange 조직에 대해 커넥터를 설치할 수 있습니다.

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Windows 10 Desktop 장치의 모든 사용자에게 필수 LOB(기간 업무) 앱을 배포하는 기능 <!-- 1627835 RS4 -->
고객은 필수 LOB(기간 업무) Windows 10 앱을 장치 컨텍스트에 설치하도록 배포할 수 있습니다. 이렇게 하면 이러한 앱을 장치의 모든 사용자가 사용할 수 있습니다. 이 기능은 Windows 10 Desktop 장치에만 적용됩니다.

### <a name="company-portal-enrollment-improved----1874230--"></a>회사 포털 등록 향상<!-- 1874230-->
Windows 10 Build 1703 이상에서 회사 포털을 사용하여 장치를 등록하는 사용자는 해당 앱을 종료하지 않고 등록의 첫 번째 단계를 완료할 수 있습니다.

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



