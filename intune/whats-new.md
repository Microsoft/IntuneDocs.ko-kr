---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: ff2774b76bceeeeaecec7a4dc74876b11706d574
ms.sourcegitcommit: 56a8a3c8974f54f0f9ecc1e5b43581502ecc348e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2018
ms.locfileid: "39614516"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. [예정된 변경](#whats-coming), 서비스 관련 [중요 공지](#notices) 및 [이전 릴리스](whats-new-archive.md) 관련 정보에 대해서도 알아볼 수 있습니다. 일부 기능은 몇 주에 걸쳐 출시될 수 있고 첫 번째 주에는 모든 고객에게 제공되지 않습니다.

> [!Note]
> 하이브리드 MDM(모바일 장치 관리)의 새로운 기능에 대한 자세한 내용은 [하이브리드의 새로운 기능 페이지](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)를 참조하세요.


<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

## <a name="week-of-july-23-2018"></a>2018년 7월 23일 주

### <a name="app-management"></a>앱 관리

####  <a name="windows-apps-file-extensions----1884873---"></a>Windows 앱 파일 확장명 <!-- 1884873 -->
이제 Windows 앱에 대한 파일 확장명에는 *.msi*, *.appx*, *.appxbundle*, *.msix* 및 *.msixbundle*이 포함됩니다. **모바일 앱** > **앱** > **추가**를 선택하여 Microsoft Intune에서 앱을 추가할 수 있습니다. **앱 유형**을 선택할 수 있는 **앱 추가** 창이 표시됩니다. 앱 패키지 파일을 업로드할 수 있는 앱 유형을 선택하고 **앱 패키지 파일**을 선택한 다음, 적절한 확장명이 있는 설치 파일을 입력합니다.

#### <a name="line-of-business-lob-app-support-for-macos----1895847---"></a>macOS에 대한 LOB(기간 업무) 앱 지원 <!-- 1895847 -->
Microsoft Intune은 macOS LOB 앱을 **요청** 또는 **등록 시 사용 가능**으로 배포하게 허용합니다. 최종 사용자는 macOS용 회사 포털 또는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)를 사용하여 **사용 가능**으로 앱을 배포할 수 있습니다.

#### <a name="ios-built-in-app-support-for-kiosk-mode----2051098---"></a>키오스크 모드 <!-- 2051098 -->에 대한 기본 제공 iOS 앱 지원
스토어 앱 및 관리되는 앱 외에도 iOS 장치에서 키오스크 모드로 실행되는 기본 제공 앱(예: Safari)을 이제 선택할 수 있습니다.

#### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Office 365 Pro Plus 앱 배포 편집 <!-- 2150145 -->
Microsoft Intune 관리자가 Office 365 Pro Plus 앱 배포를 편집할 수 있는 기능이 향상되었습니다. 또한 제품군의 속성을 변경하기 위해 더 이상 배포를 삭제할 필요가 없습니다. Azure Portal에서 **Microsoft Intune** > **모바일 앱** > **앱**을 차례로 선택합니다. 앱 목록에서 Office 365 Pro Plus 제품군을 선택합니다.  


#### <a name="updated-intune-app-sdk-for-android-is-now-available----2744271--"></a>업데이트된 Android용 Intune 앱 SDK 사용 가능 <!-- 2744271-->

Android P 릴리스를 지원하도록 Android용 Intune 앱 SDK의 업데이트된 버전이 제공됩니다. 앱 개발자이며 Android용 Intune SDK를 사용하는 경우 업데이트된 버전의 Intune 앱 SDK를 설치하여 Android 앱 내의 Intune 기능이 Android P 장치에서도 계속 예상대로 작동하는지 확인해야 합니다. 이 버전의 Intune 앱 SDK에는 SDK 업데이트를 수행하는 기본 제공 플러그인을 제공합니다. 통합된 모든 기존 코드를 다시 쓸 필요가 없습니다. 자세한 내용은 [Intune SDK for Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)(Android용 Intune SDK)를 참조하세요. Intune의 이전 배지 스타일을 사용하는 경우 서류 가방 아이콘을 사용하는 것이 좋습니다. 브랜딩 세부 정보는 [this GitHub repository](https://github.com/msintuneappsdk/intune-app-partner-badge)(이 GitHub 리포지토리)를 참조하세요.


### <a name="device-configuration"></a>장치 구성

#### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>S/MIME를 사용하여 사용자의 여러 장치를 암호화 및 서명 <!-- 1333642 -->
이 업데이트에는 가져온 새 인증서 프로필을 사용하는 S/MIME 이메일 암호화가 포함됩니다(**장치 구성** > **프로필** > **프로필 만들기** > 플랫폼 선택 > **PKCS 가져온 인증서** 프로필 유형). Intune에서 PFX 형식의 인증서를 가져올 수 있습니다. 그런 다음, Intune은 단일 사용자에 의해 등록된 여러 장치에 이러한 동일한 인증서를 제공할 수 있습니다. 다음도 포함되어 있습니다.

- 네이티브 iOS 이메일 프로필은 PFX 형식의 가져온 인증서를 사용하는 S/MIME 암호화 활성화를 지원합니다.
- Windows Phone 10 장치의 네이티브 메일 앱은 S/MIME 인증서를 자동으로 사용합니다.
- 여러 플랫폼에서 개인 인증서를 제공할 수 있습니다. 하지만 모든 이메일 앱이 S/MIME를 지원하지는 않습니다.
- 다른 플랫폼에서 S/MIME를 활성화하도록 메일 앱을 수동으로 구성해야 할 수 있습니다.  
- S/MIME 암호화를 지원하는 이메일 앱은 해당 게시자의 인증서 저장소에서 읽기와 같은 MDM에서 지원할 수 없는 방식으로 S/MIME 이메일 암호화에 대한 인증서 가져오기를 처리할 수 있습니다.

지원: Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>macOS 장치에서 방화벽 설정을 사용하는 장치 준수 정책 만들기 <!-- 1497640 -->
새 macOS 준수 정책을 만들면(**장치 준수** > **정책** > **정책 만들기** > **플랫폼: macOS** > **시스템 보안**) 다음과 같은 일부 새 **방화벽** 설정을 사용할 수 있습니다. 

- **방화벽**: 사용자 환경에서 들어오는 연결을 처리하는 방법을 구성합니다.
- **들어오는 연결**: DHCP, Bonjour 및 IPSec과 같은 기본 인터넷 서비스에 필요한 연결을 제외한 모든 들어오는 연결을 **차단**합니다. 이 설정은 모든 공유 서비스도 차단합니다.
- **은폐 모드**: 장치에서 검색 요청에 응답하지 못하도록 은폐 모드를 **사용하도록 설정**합니다. 장치는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다.

적용 대상: macOS 10.12 이상

#### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Windows 10 이상용 새 Wi-Fi 장치 구성 프로필 <!-- 1879077 -->
현재 XML 파일을 사용하여 Wi-Fi 프로필 가져오고 내보낼 수 있습니다. 이 업데이트를 사용하면 일부 다른 플랫폼과 마찬가지로 Intune에서 직접 Wi-Fi 장치 구성 프로필을 만들 수 있습니다.

프로필을 만들려면 **장치 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **Wi-Fi**를 엽니다. 

Windows 10 이상에 적용됩니다.

#### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998-eeready---"></a>키오스크 - 사용되지 않음은 회색으로 처리되고, 변경할 수 없음 <!-- 2149998 eeready -->
[키오스크 기능](device-restrictions-windows-10.md#kiosk-preview---obsolete)(**장치 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **장치 제한**)은 사용되지 않으며, [Windows 10 이상용 키오스크 설정](kiosk-settings.md)으로 대체됩니다. 이 업데이트를 사용하면 **Kiosk - 사용되지 않음** 기능은 회색으로 처리되고, 사용자 인터페이스를 변경하거나 업데이트할 수 없습니다. 

키오스크 모드를 활성화하려면 [Windows 10 이상용 키오스크 설정](kiosk-settings.md)을 참조하세요.

적용 대상: Windows 10 이상, Windows Holographic for Business

#### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>타사 인증 기관을 사용하는 API <!-- 2184013 -->
이 업데이트에는 Intune 및 SCEP와 통합하도록 타사 인증 기관을 활성화하는 Java API가 있습니다. 그러면 사용자는 프로필에 SCEP 인증서를 추가하고, MDM을 사용하여 장치에 적용할 수 있습니다.

현재 Intune은 [Active Directory 인증서 서비스를 사용하여 SCEP 요청](certificates-scep-configure.md)을 지원합니다.

#### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 설정/해제 <!-- 2455253 -->
이제 키오스크 브라우저에서 세션 종료 단추를 표시할지 여부를 구성할 수 있습니다. **장치 구성** > **키오스크(미리 보기)** > **키오스크 웹 브라우저**에서 컨트롤을 볼 수 있습니다. 설정된 경우 사용자가 단추를 클릭하면 앱은 세션을 종료할지 확인하는 메시지를 표시합니다. 확인한 경우 브라우저는 모든 검색 데이터를 지우고 기본 URL로 다시 이동합니다.

#### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>eSIM 셀룰러 구성 프로필 만들기 <!-- 2564077 -->
**장치 구성**에서 eSIM 셀룰러 프로필을 만들 수 있습니다. 모바일 운영자가 제공하는 셀룰러 활성화 코드를 포함하는 파일을 가져올 수 있습니다. 그런 다음, 이러한 프로필을 Surface Pro LTE 및 eSIM 지원 장치와 같은 eSIM LTE가 활성화된 Windows 10 장치에 배포할 수 있습니다.

[장치에서 eSIM 프로필을 지원](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data)하는지 확인합니다.

Windows 10 이상에 적용됩니다. 




### <a name="device-enrollment"></a>장치 등록

#### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>삼성 Knox 모바일 등록을 사용하여 등록된 Android 장치를 자동으로 "회사"로 표시합니다. <!-- 2404851 -->
기본적으로 삼성 Knox 모바일 등록을 사용하여 등록된 Android 장치는 이제 **장치 소유권** 아래에 **회사**로 표시됩니다. Knox 모바일 등록을 사용하여 등록하기 전에 IMEI 또는 일련 번호를 사용하여 회사 장치를 수동으로 식별할 필요가 없습니다.

### <a name="device-management"></a>장치 관리

#### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>장치 블레이드의 대량 삭제 장치 <!-- 1793693 -->

이제 장치 블레이드에서 한 번에 여러 장치를 삭제할 수 있습니다. **장치** > **모든 장치** > 삭제할 장치 > **삭제**를 선택합니다. 삭제할 수 없는 장치의 경우 경고가 표시됩니다.

## <a name="week-of-july-16-2018"></a>2018년 7월 16일 주  

### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 동기화할 수 있는 더 많은 기회  
이제 Windows용 회사 포털 앱을 사용하여 Windows 작업 표시줄 및 시작 메뉴에서 직접 동기화를 시작할 수 있습니다. 이 기능은 장치를 동기화하고 회사 리소스에 액세스하는 작업만 수행하는 경우에 특히 유용합니다. 새 기능에 액세스하려면 작업 표시줄 또는 시작 메뉴에 고정되어 있는 회사 포털 아이콘을 마우스 오른쪽 단추로 클릭합니다. 메뉴 옵션(점프 목록이라고도 함)에서 **이 장치 동기화**를 선택합니다. 회사 포털에 **설정** 페이지가 열리고 동기화가 시작됩니다. 새로운 기능에 대한 내용은 [UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.   

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱의 새 검색 환경  

이제 Windows용 회사 포털 앱에서 앱을 탐색하거나 검색하면 기존 **타일** 보기와 새로 추가된 **세부 정보** 보기 간에 전환할 수 있습니다. 새 보기에는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 응용 프로그램 세부 정보가 나열됩니다.  

**앱** 페이지의 **설치됨** 보기를 통해 완료 및 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있습니다. 새 보기의 모양을 보려면 [UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.  
### <a name="improved-company-portal-app-experience-for-device-enrollment-managers"></a>장치 등록 관리자를 위한 회사 포털 앱 환경 개선  
DEM(장치 등록 관리자)이 Windows용 회사 포털 앱에 로그인하면 이제 앱은 DEM의 현재 실행 중인 장치만 나열됩니다. 이러한 향상된 기능은 앱이 모든 DEM 등록 장치를 표시하려고 시도할 때 이전에 발생한 시간 초과를 줄입니다.  


## <a name="week-of-july-9-2018"></a>2018년 7월 9일 주

### <a name="app-management"></a>앱 관리

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>승인되지 않은 장치 공급업체 및 모델을 기준으로 앱 액세스 차단 <!-- 1425689 ! -->
Intune IT 관리자는 Intune 앱 보호 정책을 통해 지정된 Android 제조업체 및/또는 iOS 모델 목록을 적용할 수 있습니다. IT 관리자는 Android 정책용 제조업체 및 iOS 정책용 장치 모델의 세미콜론으로 구분된 목록을 제공할 수 있습니다. Intune 앱 보호 정책은 Android 및 iOS에만 적용됩니다. 이 지정된 목록에서 수행할 수 있는 두 가지 개별 작업은 다음과 같습니다.
- 지정되지 않은 장치에 대한 앱 액세스 차단
- 또는 지정되지 않은 장치에서 회사 데이터 선택적 초기화. 

정책을 통한 요구 사항이 충족되지 않으면 사용자가 대상 응용 프로그램에 액세스할 수 없습니다. 설정에 따라 사용자는 차단되거나 앱 내의 해당 회사 데이터에서 선택적으로 초기화될 수 있습니다. iOS 장치에서 이 기능을 사용하려면 응용 프로그램(예: WXP, Outlook, Managed Browser, Yammer)에 참여하여 대상 응용 프로그램에 이 기능을 적용하기 위해 Intune APP SDK를 통합해야 합니다. 이 통합은 롤링 기반으로 특정 응용 프로그램 팀에서 수행합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 

최종 사용자 장치에서 Intune 클라이언트는 응용 프로그램 보호 정책에 대한 Intune 블레이드에 지정된 문자열의 단순 일치를 기반으로 동작을 수행합니다. 이 동작은 전적으로 장치가 보고하는 값에 따라 결정됩니다. 따라서 IT 관리자는 의도한 동작이 정확한지 확인하는 것이 좋습니다. 이를 확인하려면 작은 사용자 그룹을 대상으로 하는 다양한 장치 제조업체 및 모델을 기반으로 이 설정을 테스트하면 됩니다. Microsoft Intune에서 **모바일 앱** > **앱 보호 정책**을 선택하여 앱 보호 정책을 보고 추가합니다. 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md) 및 [Intune에서 앱 보호 정책 액세스 작업을 사용하여 선택적으로 데이터 초기화](app-protection-policies-access-actions.md)를 참조하세요.

### <a name="access-to-macos-company-portal-pre-release-build----1734766---"></a>macOS 회사 포털 시험판 빌드에 액세스 <!-- 1734766 -->
Microsoft 자동 업데이트를 사용하여 등록할 수 있으며 Insider 프로그램에 참여하여 빌드를 조기에 받을 수 있습니다. 등록하면 업데이트된 회사 포털을 사용해 본 이후에 최종 사용자에게 제공할 수 있습니다. 자세한 내용은 [Microsoft Intune 블로그](https://blogs.technet.microsoft.com/intunesupport/2018/07/13/use-microsoft-autoupdate-for-early-access-to-the-macos-company-portal-app/)를 참조하세요.

## <a name="week-of-july-2-2018"></a>2018년 7월 2일 주

### <a name="app-management"></a>앱 관리

#### <a name="monitor-ios--app-configuration-status-per-device----880037---"></a>장치별 iOS 앱 구성 상태 모니터링 <!-- 880037 -->
Microsoft Intune 관리자는 각 관리 장치에 대한 iOS 앱 구성 상태를 모니터링할 수 있습니다. Azure Portal의 **Microsoft Intune**에서 **장치** > **모든 장치**를 차례로 선택합니다. 관리 장치 목록에서 장치에 대한 블레이드를 표시할 특정 장치를 선택합니다. 장치 블레이드에서 **앱 구성**을 선택합니다.

#### <a name="access-actions-for-app-protection-policies----1483510---"></a>앱 보호 정책에 대한 액세스 작업 <!-- 1483510 -->
규정을 준수하지 않는 장치를 명시적으로 초기화, 차단 또는 경고하도록 앱 보호 정책을 구성할 수 있습니다. *초기화* 작업은 장치에서 회사의 회사 데이터를 제거합니다. 초기화가 수행되면 장치 사용자에게는 초기화 및 수정 단계의 이유가 포함된 알림이 제공됩니다. 최소 OS 버전과 같은 일부 설정의 경우 차단 및 초기화와 같은 여러 작업을 적용할 수 있습니다. 앱이 시작되면 이러한 작업이 트리거됩니다.

#### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>선택적으로 조직의 앱 데이터 지우기 <!-- 1507030 -->
APP(응용 프로그램 보호 정책) 액세스 설정 조건이 충족되지 않으면 관리자가 이제 조직의 데이터를 선택적으로 지우도록 구성할 수 있습니다.  이 기능을 사용하면 관리자가 미리 구성된 기준에 따라 응용 프로그램에서 중요한 조직 데이터를 자동으로 보호하고 제거할 수 있습니다.

#### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>VPP를 통해 구매한 iOS 앱 해지 <!-- 1777384 -->
Microsoft Intune 관리자는 VPP(대량 구매 프로그램)를 통해 구매한 iOS 앱에 대한 모든 라이선스를 선택적으로 해지할 수 있습니다. 사용자 라이선스된 앱이 더 이상 할당되지 않는 경우 사용자에게 알릴 수 있습니다. 앱 라이선스를 철회해도 장치에서 관련 VPP 앱이 제거되지 않습니다. VPP 앱을 제거하려면 할당 작업을 **제거**로 변경해야 합니다. 회수된 라이선스 수는 Intune의 **앱** 워크로드의 **사용이 허가된 앱** 노드에 반영됩니다. iOS VPP 앱과 관련된 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법](vpp-apps-ios.md)을 참조하세요.

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>회사 포털 앱의 규정을 준수하지 않는 메시지 업데이트 <!-- 1832222 -->
장치가 규정을 준수하지 않을 때 장치 사용자에게 표시되는 메시지를 수정했습니다. 메시지의 원래 의미는 그대로 유지되지만 더 친숙한 언어와 덜 전문적인 용어로 업데이트되었습니다. 또한 설명서 및 수정 단계에 대한 링크를 최신 상태로 유지하기 위해 새로 고쳤습니다.
다음에서 볼 수 있는 전후 텍스트는 메시징 향상 기능의 한 예입니다.
- **이전**: *이 장치는 IT 관리자가 요구한 특정 기간 내에 Intune 서비스에 연결되지 않았습니다 이 문제를 해결하려면 장치에서 회사 포털 앱을 열고 준수 확인 단추를 클릭합니다.*
- **이후**: *장치가 얼마 동안 조직에 체크 인되지 않았습니다. 연결을 다시 설정하려면 장치에서 회사 포털 앱을 열고 장치의 설정 확인을 누릅니다.*

#### <a name="revoke-ios-vpp-app-license----1863797---"></a>iOS VPP 앱 라이선스 해지 <!-- 1863797 -->
관리자는 사용자 또는 장치에 할당된 iOS VPP 앱 라이선스를 회수할 수 있습니다. iOS VPP 앱을 제거하면 앱 라이선스를 회수할 수도 있습니다. 앱을 제거하기 전에 먼저 사용자 또는 장치가 앱의 대상인 그룹에서 제거되어야 합니다. 사용자 또는 장치를 그룹에서 제거하면 앱의 재설치를 방지할 수 있습니다. 이러한 단계가 완료되면 해당 앱 라이선스를 다른 사용자 또는 장치에 할당하도록 선택할 수 있습니다. iOS VPP 앱 라이선스에 대한 자세한 내용은 [Microsoft Intune에서 iOS 볼륨을 구매한 앱 관리](vpp-apps-ios.md)를 참조하세요.

### <a name="device-configuration"></a>장치 구성

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings----1058963-eenotready---"></a>회사 또는 학교 액세스 설정을 사용하여 장치 범주 선택 <!-- 1058963 eenotready --> 
[장치 그룹 매핑](https://docs.microsoft.com/en-us/intune/device-group-mapping)을 사용하도록 설정한 경우, Windows 10의 사용자에게 **설정** > **계정** > **회사 또는 학교 액세스**의 **연결** 단추를 통해 등록한 후 장치 범주를 선택하라는 메시지가 표시됩니다. 

#### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>sAMAccountName을 이메일 프로필에 대한 계정 사용자 이름으로 사용 <!-- 1500307 -->
온-프레미스 **sAMAccountName**을 Android, iOS 및 Windows 10용 이메일 프로필에 대한 계정 사용자 이름으로 사용할 수 있습니다. Azure AD(Azure Active Directory)의 `domain` 또는 `ntdomain` 특성에서 도메인을 가져올 수도 있습니다. 또는 사용자 지정 정적 도메인을 입력합니다.

이 기능을 사용하려면 온-프레미스 Active Directory 환경의 `sAMAccountName` 특성을 Azure AD에 동기화해야 합니다.

[Andoid](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 이상](email-settings-windows-10.md)에 적용

#### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a><!-- 1556983 --> 충돌에서 장치 구성 프로필 참조
**장치 구성**에 기존 프로필의 목록이 표시됩니다. 이 업데이트를 사용하면 충돌하는 프로필에 대한 세부 정보를 제공하는 새 열이 추가됩니다. 충돌하는 행을 선택하여 충돌이 있는 설정 및 프로필을 볼 수 있습니다. 

[구성 프로필 관리](device-profile-monitor.md#view-conflicts)에 대한 자세한 정보입니다.

#### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>장치 준수의 새로운 장치 상태 <!-- 2308882 -->
**장치 준수** > **정책** > 정책 선택 > **개요**에서 다음과 같은 새 상태가 추가됩니다.
- 성공
- 오류
- 충돌
- 보류 중
- 해당 없음. 다른 플랫폼의 장치 수를 보여 주는 이미지도 표시됩니다. 예를 들어 iOS 프로필을 보고 있는 경우 이 프로필에도 할당된 비iOS 장치의 수가 새 타일에 표시됩니다. [장치 준수 정책](compliance-policy-monitor.md#view-status-of-device-policies)을 참조합니다.

#### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>장치 준수에서 타사 바이러스 백신 솔루션 지원 <!-- 2325484 -->
장치 준수 정책(**장치 준수** > **정책** > **정책 만들기** > **플랫폼: Windows 10 이상** > **설정** > **시스템 보안**)을 만들면 다음과 같은 새 **[장치 보안](compliance-policy-create-windows.md#windows-10-and-later-policy-settings)** 옵션이 제공됩니다. 
- **바이러스 백신**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 바이러스 백신 솔루션을 사용하여 준수를 확인할 수 있습니다. 
- **스파이웨어 방지**: **필수**로 설정하면 Symantec 및 Windows Defender와 같은 Windows Security Center에 등록된 스파이웨어 방지 솔루션을 사용하여 준수를 확인할 수 있습니다. 

적용 대상: Windows 10 이상 

### <a name="device-enrollment"></a>장치 등록

####  <a name="devices-without-profiles-column-in-the-list-of-enrollment-program-tokens----1853904---"></a>등록 프로그램 토큰 목록에서 프로필이 없는 장치 열 <!-- 1853904 -->
프로필이 할당되지 않는 장치 수를 보여주는 새 열이 등록 프로그램 토큰 목록에 제공됩니다. 이렇게 하면 관리자는 프로필을 사용자에게 전달하기 전에 이러한 장치에 할당할 수 있습니다. 새 열을 보려면 **장치 등록** > **Apple 등록** > **등록 프로그램 토큰**으로 이동합니다.

### <a name="device-management"></a>장치 관리

#### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Android for Work 및 Play for Work에 대한 Google 이름 변경 <!--842873 -->
Intune은 Google 브랜딩 변경 내용을 반영하도록 "Android for Work" 용어를 업데이트했습니다. "Android for Work" 및 "Play for Work" 용어는 더 이상 사용되지 않습니다. 컨텍스트에 따라 서로 다른 용어가 사용됩니다.
- "Android 엔터프라이즈"는 전반적인 최신 Android 관리 스택을 나타냅니다.
- "회사 프로필" 또는 "프로필 소유자"는 회사 프로필을 통해 관리되는 BYOD 장치를 가리킵니다.
- "관리되는 Google Play"는 Google 앱 스토어를 나타냅니다.

#### <a name="rules-for-removing-devices----1609459---"></a>장치 제거에 대한 규칙 <!-- 1609459 -->
설정한 일 수 동안 체크 인하지 않은 장치를 자동으로 제거할 수 있는 새 규칙이 제공됩니다. 새 규칙을 보려면 **Intune** 창으로 이동하여 **장치**를 선택하고 **장치 정리 규칙**을 선택합니다.

#### <a name="corporate-owned-single-use-support-for-android-devices----1630973---"></a>Android 장치에 대한 회사 소유의 일회용 지원 <!-- 1630973 -->

Intune은 이제 고도로 관리되고 잠겨 있는 키오스크 스타일의 Android 장치를 지원합니다. 관리자는 이를 통해 장치 사용을 하나의 앱 또는 작은 앱 집합에 추가로 잠그고 사용자가 다른 앱을 사용하거나 장치에서 다른 작업을 수행하지 못하도록 차단할 수 있습니다. Android 키오스크를 설정하려면 Intune > **장치 등록** > **Android 등록** > **키오스크 및 작업 장치 등록**으로 이동합니다. 자세한 내용은 [Android 엔터프라이즈 키오스크 장치 등록 설정](android-kiosk-enroll.md)을 참조합니다.

#### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794--"></a>중복된 회사 장치 식별자의 행 단위 검토 업로드 <!-- 2203794-->
회사 ID를 업로드할 때 Intune에서 모든 중복된 항목의 목록을 제공하고, 기존 정보를 대체하거나 유지할 수 있는 옵션을 제공합니다. **장치 등록** > **회사 장치 식별자** > **식별자 추가**를 차례로 선택한 후에 중복된 항목이 있으면 보고서가 표시됩니다. 

#### <a name="manually-add-corporate-device-identifiers----2203803---"></a>수동으로 회사 장치 식별자 추가 <!-- 2203803 -->
수동으로 회사 장치 ID를 추가할 수 있습니다. **장치 등록** > **회사 장치 식별자** > **추가**를 차례로 선택합니다. 

## <a name="week-of-june-25-2018"></a>2018년 6월 25일 주

### <a name="pradeo---new-mobile-threat-defense-partner----1169249---"></a>Pradeo - 새 Mobile Threat Defense 파트너 <!-- 1169249 -->

Microsoft Intune과 통합된 Mobile Threat Defense 솔루션인 Pradeo에서 수행한 위험 평가에 따라 조건부 액세스를 사용하여 회사 리소스에 대한 모바일 장치의 액세스를 제어할 수 있습니다.

## <a name="week-of-june-18-2018"></a>2018년 6월 18일 주

### <a name="edge-mobile-support-for-intune-app-protection-policies----1817882---"></a>Intune 앱 보호 정책용 Edge 모바일 지원<!-- 1817882 -->

모바일 장치용 Microsoft Edge 브라우저는 이제 Intune에 정의된 앱 보호 정책을 지원합니다.

## <a name="week-of-june-11-2018"></a>2018년 6월 11일 주

### <a name="use-fips-mode-with-the-ndes-certificate-connector----1333688---"></a>NDES 인증서 커넥터에서 FIPS 모드 사용 <!-- 1333688 -->
FIPS(Federal Information Processing Standard) 모드를 사용하는 컴퓨터에 NDES 인증서 커넥터를 설치하면 인증서 발급 및 해지가 예상대로 작동하지 않았습니다. 이 업데이트에는 NDES 인증서 커넥터와 관련된 FIPS 지원이 포함되어 있습니다. 

이 업데이트에는 다음도 포함됩니다.

- NDES 인증서 커넥터에는 Windows Server 2016 및 Windows Server 2012 R2에 자동으로 포함되는 .NET 4.5 Framework가 필요합니다. 이전에는 .NET 3.5 Framework가 최소 필수 버전이었습니다.
- TLS 1.2 지원은 NDES 인증서 커넥터에 포함되어 있습니다. 따라서 NDES 인증서 커넥터가 설치된 서버가 TLS 1.2를 지원하는 경우 TLS 1.2가 사용됩니다. 서버가 TLS 1.2를 지원하지 않으면 TLS 1.1이 사용됩니다. 현재 TLS 1.1은 장치와 서버 간 인증에 사용됩니다.

자세한 내용은 [SCEP 인증서 구성 및 사용](certificates-scep-configure.md), [PKCS 인증서 구성 및 사용](certficates-pfx-configure.md)을 참조하세요.

## <a name="week-of-june-4-2018"></a>2018년 6월 4일 주

### <a name="app-management"></a>앱 관리

#### <a name="retrieve-the-associated-app-user-model-id-aumid-for-microsoft-store-for-business-apps-in-kiosk-mode----1560077----"></a>키오스크 모드에서 비즈니스용 Microsoft 스토어 앱에 대한 연결된 앱 사용자 모델 ID(AUMID) 검색 <!-- 1560077 ! -->
Intune에서는 이제 WSfB(비즈니스용 Microsoft 스토어) 앱에 대한 AUMID(응용 프로그램 사용자 모델 ID)를 검색하여 향상된 키오스크 프로필 구성을 제공할 수 있습니다.

비즈니스용 Microsoft 스토어에서 앱에 대한 자세한 내용은 [비즈니스용 Microsoft 스토어에서 앱 관리](windows-store-for-business.md)를 참조하세요.

#### <a name="new-company-portal-branding-page----1916370---"></a>새 회사 포털 브랜딩 페이지 <!-- 1916370 -->
회사 포털 브랜딩 페이지에는 새로운 레이아웃, 메시지 및 도구 설명이 있습니다.


### <a name="device-configuration"></a>장치 구성

#### <a name="support-for-palo-alto-networks-globalprotect-vpn-profiles----1333680-eeready----"></a>Palo Alto Networks GlobalProtect VPN 프로필 <!-- 1333680 eeready ! --> 지원
이 업데이트에서는 Palo Alto Networks GlobalProtect를 Intune의 VPN 프로필에 대한 VPN 연결 형식으로 선택할 수 있습니다(**장치 구성** > **프로필** > **프로필 만들기** > **프로필 형식** > **VPN**). 이 릴리스에서 지원되는 플랫폼은 다음과 같습니다. 

- iOS
- Windows 10

#### <a name="additions-to-local-device-security-options-settings----1403702---"></a>로컬 장치 보안 옵션 설정에 대한 추가 <!-- 1403702 -->
Windows 10 장치에 대한 추가 로컬 장치 보안 옵션 설정을 구성할 수 있습니다. 추가 설정은 Microsoft 네트워크 클라이언트, Microsoft 네트워크 서버, 네트워크 액세스/보안 및 대화형 로그온 영역에서 사용할 수 있습니다. Windows 10 장치 구성 정책을 만들 때 Endpoint Protection 범주에서 이러한 설정을 찾아보세요.

#### <a name="enable-kiosk-mode-on-windows-10-devices----1560072----"></a>Windows 10 장치에서 키오스크 모드 사용 <!-- 1560072 ! -->
Windows 10 장치에서 구성 프로필을 만들고 키오스크 모드를 사용하도록 설정할 수 있습니다(**장치 구성** > **프로필** > **프로필 만들기** > **Windows 10** > **장치 제한 사항** > **키오스크**). 이 업데이트에서 **키오스크(미리 보기)** 설정은 **키오스크(사용되지 않음)** 로 이름이 바뀝니다. **키오스크(사용되지 않음)** 는 더 이상 사용하지 않는 것이 좋지만 7월 업데이트까지 계속 작동합니다. **키오스크(사용되지 않음)** 는 새로운 **키오스크** 프로필 유형(**프로필 만들기** > **Windows 10** > **키오스크(미리 보기)**)으로 바뀌고 이 프로필 유형에는 Windows 10 RS4 이상에서 키오스크를 구성하는 설정이 포함됩니다.

Windows 10 이상에 적용됩니다.

#### <a name="device-profile-graphical-user-chart-is-back----2160133---"></a>장치 프로필 그래픽 사용자 차트가 다시 표시됨 <!-- 2160133 -->
장치 프로필 그래픽 차트(**장치 구성** > **프로필** > 기존 프로필 선택 > **개요**)에 표시되는 개수를 개선하기 위해 그래픽 사용자 차트가 일시적으로 제거되었습니다.

이 업데이트를 사용하면 그래픽 사용자 차트가 Azure Portal에 다시 표시됩니다.

### <a name="device-enrollment"></a>장치 등록

#### <a name="support-for-windows-autopilot-enrollment-without-user-authentication----1165118-wnready---"></a>사용자 인증이 없는 Windows Autopilot 등록 지원 <!-- 1165118 wnready -->
Intune에서는 이제 사용자 인증 없이 Windows Autopilot 등록을 지원합니다. 여기에는 Windows Autopilot 배포 프로필인 "Autopilot 배포 모드"가 "자체 배포"로 설정된 새 옵션이 있습니다.  이 장치는 Windows 10 Insider Preview Build 17672 이상을 실행 중이고 TPM 2.0 칩을 가지고 있어야 이 등록 유형을 성공적으로 완료할 수 있습니다. 사용자 인증이 필요하지 않으므로 물리적으로 제어할 수 있는 장치에만 이 옵션을 할당해야 합니다.

#### <a name="new-languageregion-setting-when-configuring-oobe-for-autopilot----1821766-eeready---"></a>Autopilot에 대한 OOBE를 구성할 경우, 새 언어 지역 설정 <!-- 1821766 eeready -->
새 구성 설정은 독창적인 환경(Out of Box Experience)에서 Autopilot 프로필에 대한 언어와 지역을 설정하는 데 사용할 수 있습니다. 새 설정을 확인하려면 **장치 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기** > **배포 모드** = **자체 배포** > **기본값 구성됨**을 차례로 선택합니다.

#### <a name="new-setting-for-configuring-device-keyboard----1821768---"></a>장치 키보드 구성에 대한 새 설정 <!-- 1821768 -->
새 설정을 통해 첫 실행 경험 중에 Autopilot 프로필에 대한 키보드를 구성할 수 있습니다. 새 설정을 확인하려면 **장치 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기** > **배포 모드** = **자체 배포** > **기본값 구성됨**을 차례로 선택합니다.

#### <a name="autopilot-profiles-moving-to-group-targeting----1877935---"></a>Autopilot 프로필을 대상 지정 그룹으로 이동 <!-- 1877935 -->
AutoPilot 배포 프로필을 AutoPilot 장치를 포함하는 Azure AD 그룹에 할당할 수 있습니다.

### <a name="device-management"></a>장치 관리

#### <a name="set-compliance-by-device-location----851881----"></a>장치 위치별 준수 설정 <!-- 851881 ! -->
상황에 따라 회사 리소스에 대한 액세스를 네트워크 연결로 정의된 특정 위치로 제한할 수 있습니다. 이제 장치의 IP 주소를 기반으로 하여 준수 정책을 만들 수 있습니다(**장치 준수** > **위치**). IP 범위를 벗어난 장치는 회사 리소스에 액세스할 수 없습니다.

적용 대상: 회사 포털 앱이 업데이트된 Android 장치 6.0 이상 

#### <a name="prevent-consumer-apps-and-experiences-on-windows-10-enterprise-rs4-autopilot-devices---1621980---"></a>Windows 10 Enterprise RS4 Autopilot 장치에서 소비자 앱과 경험을 방지<!-- 1621980 -->
Windows 10 Enterprise RS4 AutoPilot 장치에서 소비자 앱 및 환경을 설치하지 못하도록 방지할 수 있습니다. 이 기능을 확인하려면 **Intune** > **장치 구성** > **프로필** > **프로필 만들기** > **플랫폼** = **Windows 10 이상** > **프로필 유형** = **장치 제한** > **구성** > **Windows 추천** > **소비자 기능**으로 차례로 이동합니다. 

#### <a name="uninstall-the-latest-from-windows-10-software-updates----1732948-eeready---"></a>Windows 10 소프트웨어 업데이트에서 최신 버전 제거 <!-- 1732948 eeready -->
Windows 10 컴퓨터에서 주요 문제가 발견되면 최신 기능 업데이트 또는 최신 품질 업데이트를 제거(롤백)하도록 선택할 수 있습니다. 기능 또는 품질 업데이트의 제거는 장치가 켜져 있는 서비스 채널에서만 사용할 수 있습니다. 제거하면 Windows 10 컴퓨터에서 이전 업데이트를 복원하는 정책이 트리거됩니다. 특히 기능 업데이트의 경우 최신 버전 제거를 적용할 수 있는 시간을 2-60일로 제한할 수 있습니다. 소프트웨어 업데이트 제거 옵션을 설정하려면 Azure Portal의 **Microsoft Intune** 블레이드에서 **소프트웨어 업데이트**를 선택합니다. 그런 다음, **소프트웨어 업데이트** 블레이드에서 **Windows 10 업데이트 링**을 선택합니다. 그런 다음, **개요** 섹션에서 **제거** 옵션을 선택할 수 있습니다.

#### <a name="search-all-devices-for-imei-and-serial-number----1793685---"></a>모든 장치에서 IMEI 및 일련 번호 검색 <!-- 1793685 -->
이제 모든 장치 블레이드에서 IMEI 및 일련 번호를 검색할 수 있습니다(이메일, UPN, 장치 이름 및 관리 이름을 계속 사용할 수 있음). Intune에서 **장치** > **모든 장치**를 차례로 선택한 다음, 검색 상자에서 검색 항목을 입력합니다.

#### <a name="management-name-field-will-be-editable----1875989---"></a>관리 이름 필드를 편집할 수 있음 <!-- 1875989 -->
이제 장치의 **속성** 블레이드에서 관리 이름 필드를 편집할 수 있습니다. 이 필드를 편집하려면 **장치** > **모든 장치**를 선택하고, 장치를 선택한 다음, **속성**을 선택합니다. 관리 이름 필드를 사용하여 장치를 고유하게 식별할 수 있습니다.

#### <a name="new-all-devices-filter-device-category----1878520---"></a>새로운 모든 장치 필터: 장치 범주 <!-- 1878520 -->
이제 장치 범주별로 **모든 장치** 목록을 필터링할 수 있습니다. 이렇게 하려면 **장치** > **모든 장치** > **필터** > **장치 범주**를 차례로 선택합니다.

#### <a name="use-teamviewer-to-screen-share-ios-and-macos-devices----1985547---"></a>TeamViewer를 사용하여 iOS 및 MacOS 장치의 화면 공유 <!-- 1985547 -->
관리자는 이제 [TeamViewer](device-profile-android-teamviewer.md)에 연결하고 iOS 및 macOS 장치에서 화면 공유 세션을 시작할 수 있습니다. iPhone, iPad 및 macOS 사용자는 자신의 화면을 다른 데스크톱 또는 모바일 장치와 실시간으로 공유할 수 있습니다. 

#### <a name="multiple-exchange-connector-support----2070451---"></a>여러 Exchange Connector 지원 <!-- 2070451 -->
더 이상 테넌트당 하나의 Microsoft Intune Exchange Connector로 제한되지 않습니다. Intune에서는 이제 여러 온-프레미스 Exchange 조직에서 Intune 조건부 액세스를 설정할 수 있도록 여러 Exchange Connector를 지원합니다.

Intune 온-프레미스 Exchange Connector를 사용하여 장치가 Intune에 등록했는지 여부 및 Intune 장치 준수 정책을 준수하는지 여부에 따라 온-프레미스 Exchange 사서함에 대한 장치 액세스를 관리할 수 있습니다. 커넥터를 설정하려면 Azure Portal에서 Intune 온-프레미스 Exchange Connector를 다운로드해 이를 Exchange 조직의 서버에 설치합니다. Microsoft Intune 대시보드에서 **온-프레미스 액세스**를 선택한 다음, **설치** 아래에서 **Exchange ActiveSync Connector**를 선택합니다. Exchange 온-프레미스 Connector를 다운로드하고 Exchange 조직의 서버에 설치합니다. 더 이상 테넌트당 하나의 Exchange Connector로 제한되지 않으므로 추가 Exchange 조직이 있는 경우 동일한 다운로드 절차를 따라 각 추가 Exchange 조직에 대해 커넥터를 설치할 수 있습니다.

#### <a name="new-device-hardware-detail-ccid----2156657---"></a>새로운 장치 하드웨어 세부 정보: CCID <!-- 2156657 -->
이제 각 장치에 대한 CCID(칩 카드 인터페이스 장치) 정보가 포함됩니다. 이를 확인하려면 **장치** > **모든 장치**를 차례로 선택하고, 장치를 선택하고, **하드웨어**를 선택한 다음, **네트워크 정보**> 아래에서 확인합니다.

#### <a name="assign-all-users-and-all-devices-as-scope-groups----2196803---"></a>모든 사용자 및 모든 장치를 범위 그룹으로 할당 <!-- 2196803 -->
이제 범위 그룹에서 모든 사용자, 모든 장치 및 모든 사용자/장치를 할당할 수 있습니다. 이렇게 하려면 **Intune 역할** > **모든 역할** > **정책 및 프로필 관리자** > **할당**을 차례로 선택하고, 할당을 선택한 다음, **범위(그룹)** 를 선택합니다.

#### <a name="udid-information-now-included-for-ios-and-macos-devices----2219806-wnready--"></a>iOS 및 macOS 장치에 대한 UDID 정보 포함 <!-- 2219806 wnready-->
iOS 및 macOS 장치에 대한 UDID(고유 장치 식별자)를 확인하려면 **장치** > **모든 장치**로 차례로 이동하고, 장치를 선택한 다음, **하드웨어**를 선택합니다. UDID는 **장치** > **모든 장치** > 장치 선택 > **속성** > **장치 소유권** 아래에 설정한 회사 장치에만 사용할 수 있습니다.

### <a name="intune-apps"></a>Intune 앱

#### <a name="improved-troubleshooting-for-app-installation----928990---"></a>앱 설치에 대한 향상된 문제 해결 <!-- 928990 -->
Microsoft Intune MDM 관리 장치에서 앱 설치에 실패하는 경우도 있습니다. 이러한 앱 설치에 실패할 경우, 실패 이유를 파악하거나 문제를 해결하기 어려울 수 있습니다. Microsoft에서는 앱 문제 해결 기능의 공개 미리 보기를 제공합니다. 개별 장치 아래에서 **관리 앱**이라는 새 노드를 확인할 수 있습니다. 여기에는 Intune MDM을 통해 전달된 앱이 나열됩니다. 노드 내부에는 앱 설치 상태 목록이 표시됩니다. 개별 앱을 선택하면 해당 앱에 대한 문제 해결 보기가 표시됩니다. 문제 해결 보기에는 응용 프로그램이 언제 생성, 수정, 대상 지정 및 장치에 전달되었는지를 포함한 앱의 전체 수명 주기기 표시됩니다. 또한 앱 설치에 실패할 경우, 오류 코드 및 오류의 원인에 대한 유용한 메시지가 표시됩니다. 

#### <a name="intune-app-protection-policies-and-microsoft-edge----1818968---"></a>Intune 앱 보호 정책 및 Microsoft Edge <!-- 1818968 -->
모바일 장치(iOS 및 Android)용 Microsoft Edge 브라우저에서는 이제 Microsoft Intune 앱 보호 정책을 지원합니다. Edge 응용 프로그램에서 회사 Azure AD 계정으로 로그인하는 iOS 및 Android 장치 사용자는 Intune에서 보호됩니다. iOS 장치에서 **웹 콘텐츠에 대한 Managed Browser 필요** 정책을 사용하면 사용자가 관리되는 Edge에서 링크를 열 수 있습니다.

## <a name="week-of-may-14-2018"></a>2018년 5월 14일 주

### <a name="app-management"></a>앱 관리

#### <a name="require-installation-of-policies-apps-certificate-and-network-profiles----1553555---"></a>정책, 앱, 인증서 및 네트워크 프로필의 설치 필요 <!-- 1553555 -->

관리자는 AutoPilot 장치를 프로비전하는 동안 Intune에서 정책, 앱, 인증서 및 네트워크 프로필을 설치할 때까지 최종 사용자가 Windows 10 RS4 데스크톱에 액세스하지 못하도록 차단할 수 있습니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

#### <a name="configuring-your-app-protection-policies----2144597-part-2---"></a>앱 보호 정책 <!-- 2144597 Part 2 --> 구성

Azure Portal에서 Intune 앱 보호 서비스 블레이드로 이동하는 대신 이제 Intune으로 직접 이동하면 됩니다. 이제 Intune 내에서는 앱 보호 정책에 대한 위치가 하나입니다. 모든 앱 보호 정책은 이미 앱 구성에서 Intune의 **모바일 앱** 블레이드에서 **앱 보호 정책** 아래에 있습니다. 이 통합은 클라우드 관리를 단순화하는 데 도움이 됩니다. Intune에서 모든 앱 보호 정책이 이미 설정되어 있으므로 이전에 구성한 정책을 수정할 수 있습니다. Intune APP(앱 보호 정책) 및 CA(조건부 액세스) 정책은 이제 **조건부 액세스**에 있으며 **Microsoft Intune** 블레이드의 **관리** 섹션이나 **Azure Active Directory** 블레이드의 **보안** 섹션에서 찾을 수 있습니다. 조건부 액세스 정책을 수정하는 방법에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

## <a name="week-of-may-7-2018"></a>2018년 5월 7일 주

### <a name="app-management"></a>앱 관리

#### <a name="samsung-knox-mobile-enrollment-support---1112863--"></a>삼성 Knox 모바일 등록 지원 <!--1112863-->

삼성 KME(Knox 모바일 등록)와 함께 Intune을 사용하는 경우, 많은 회사 소유 Android 장치를 등록할 수 있습니다. WiFi 또는 셀룰러 네트워크의 사용자는 장치를 처음 켤 때 몇 번만 탭하면 등록할 수 있습니다. Knox 배포 앱을 사용하는 경우 Bluetooth 또는 NFC를 사용하여 장치를 등록할 수 있습니다. 자세한 내용은 [삼성 Knox 모바일 등록을 사용하여 Android 장치 자동 등록](android-samsung-knox-mobile-enroll.md)을 참조하세요.

#### <a name="requesting-help-in-the-company-portal-for-windows-10----1874137---"></a>Windows 10용 회사 포털에서 도움말 요청 <!-- 1874137 -->

이제 Windows 10용 회사 포털은 사용자가 문제에 대한 도움을 받기 위해 워크플로를 시작할 때 Microsoft에 직접 앱 로그를 전송합니다. 이렇게 하면 Microsoft에 제기된 문제를 더 쉽게 해결할 수 있습니다.

## <a name="week-of-april-23-2018"></a>2018년 4월 23일 주간

### <a name="app-management"></a>앱 관리

#### <a name="passcode-support-for-mam-pin-on-android---1438086---"></a>Android에서 MAM PIN에 대한 암호 지원<!-- 1438086 -->

Intune 관리자는 숫자 MAM PIN 대신 암호를 적용하는 응용 프로그램 시작 요구 사항을 설정할 수 있습니다. 항목이 구성되면 사용자는 MAM 지원 응용 프로그램에 대한 액세스 권한을 가져오기 전에 메시지가 표시될 때 암호를 설정하고 사용해야 합니다. 암호는 하나 이상의 특수 문자 또는 대/소문자 알파벳을 포함한 숫자 PIN으로 정의됩니다. Intune은 기존 숫자 PIN과 유사한 방식으로 암호를 지원합니다. 즉, 최소 길이를 설정하며 관리자 콘솔을 통해 반복 문자 및 시퀀스를 허용합니다. 이 기능을 사용하려면 Android에서 회사 포털의 최신 버전이 필요합니다. 현재 iOS에서는 이 기능을 사용할 수 있습니다.

#### <a name="line-of-business-lob-app-support-for-macos----1473977---"></a>macOS에 대한 LOB(기간 업무) 앱 지원 <!-- 1473977 -->
Microsoft Intune은 Azure Portal에서 macOS LOB 앱을 설치하는 기능을 제공할 예정입니다. GitHub에서 사용할 수 있는 도구에서 미리 처리된 macOS LOB 앱을 Intune에 추가할 수 있습니다. Azure Portal에서 **Intune** 블레이드의 **모바일 앱**을 선택합니다. **모바일 앱** 블레이드에서 **앱** > **추가**를 선택합니다. **앱 추가** 블레이드에서 **LOB(기간 업무) 앱**을 선택합니다. 

#### <a name="built-in-all-users-and-all-devices-group-for-android-for-work-afw-app-assignment----1813073---"></a>AFW(Android for Work) 앱 할당을 위한 기본 제공된 모든 사용자 및 모든 장치 그룹 <!-- 1813073 -->
AFW 앱 할당을 위해 기본 제공 **모든 사용자** 및 **모든 장치** 그룹을 활용할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.

#### <a name="intune-will-reinstall-required-apps-that-are-uninstalled-by-users----1947010---"></a>사용자가 제거한 필수 앱을 Intune에서 다시 설치함 <!-- 1947010 -->
최종 사용자가 필수 앱을 제거할 경우 Intune에서 7일 재평가 주기를 기다리지 않고 24시간 이내에 앱을 자동으로 다시 설치합니다.

### <a name="device-configuration"></a>장치 구성

####  <a name="device-profile-chart-and-status-list-show-all-devices-in-a-group----1449153-eeready---"></a>장치 프로필 차트 및 상태 목록에서 그룹의 모든 장치를 표시 <!-- 1449153 eeready -->
장치 프로필을 구성할 때(**장치 구성** > **프로필**), iOS와 같은 장치 프로필을 선택합니다. iOS 장치 및 비 iOS 장치를 포함하는 그룹에 이 프로필을 할당합니다. 그래픽 차트 수는 프로필이 iOS *및* 비 iOS 장치에 적용되었음을 나타냅니다(**장치 구성** > **프로필** > 기존 프로필 선택 > **개요**). **개요** 탭에서 그래픽 차트를 선택하면 **장치 상태**에 iOS 장치 대신 그룹의 모든 장치가 나열됩니다. 

이 업데이트를 사용하면 그래픽 차트(**장치 구성** > **프로필** > 기존 프로필 선택 > **개요**)에는 특정 장치 프로필에 대한 개수만 표시됩니다. 예를 들어 구성 장치 프로필이 iOS 장치에 적용되는 경우 차트는 iOS 장치의 개수만 나열됩니다. 그래픽 차트를 선택하고 **장치 상태**를 열면 iOS 장치만 나열됩니다.

이 업데이트를 수행하는 동안 그래픽 사용자 차트는 일시적으로 제거됩니다. 

#### <a name="always-on-vpn-for-windows-10---1333666---"></a>Always On VPN for Windows 10 <!--1333666 -->

현재 [Always On](https://docs.microsoft.com/windows/security/identity-protection/vpn/vpn-auto-trigger-profile#always-on)은 OMA-URI를 통해 만든 사용자 지정 VPN(가상 사설망) 프로필을 사용하여 Windows 10 장치에서 사용할 수 있습니다.

이 업데이트를 사용하면 관리자는 Azure Portal의 Intune에서 직접 Always On for Windows 10 VPN 프로필을 사용하도록 설정할 수 있습니다. Always On VPN 프로필은 다음과 같은 경우 자동으로 연결됩니다.

- 자신의 장치에 사용자가 로그인하는 경우
- 장치의 네트워크가 변경되는 경우
- 장치의 화면이 꺼졌다가 다시 켜지는 경우

#### <a name="new-printer-settings-for-education-profiles----1308900---"></a>교육 프로필에 대한 새 프린터 설정 <!-- 1308900 -->

교육 프로필의 경우 **프린터** 범주의 **프린터**, **기본 프린터**, **새 프린터 추가**에서 새 설정을 사용할 수 있습니다.

#### <a name="show-caller-id-in-personal-profile---android-for-work---1098984---"></a>개인 프로필에 발신자 ID 표시 - Android for Work <!--1098984 -->
장치에서 개인 프로필을 사용하는 경우 회사 연락처의 발신자 ID 정보가 최종 사용자에게 표시되지 않을 수 있습니다. 

이 업데이트에서는 **Android for Work** > **장치 제한** > **작업 프로필 설정**에서 새 설정이 지정됩니다.
- 개인 프로필에 회사 연락처의 발신자 ID 표시

사용하도록 설정하면(구성하지 않음) 회사 연락처의 발신자 정보가 개인 프로필에 표시됩니다. 차단하면 회사 연락처의 발신자 번호가 개인 프로필에 표시되지 않습니다. 

적용 대상: Android OS v6.0 이상의 Android 회사 프로필 장치

#### <a name="new-windows-defender-credential-guard-settings-added-to-endpoint-protection-settings---1102252-----from-1802-and-1804--"></a>엔드포인트 보호 설정에 추가된 새 Windows Defender Credential Guard 설정 <!--1102252 --><!--from 1802 and 1804-->

이 업데이트를 사용하면 [Windows Defender Credential Guard](https://docs.microsoft.com/windows/access-protection/credential-guard/credential-guard)(**장치 구성** > **프로필** > **Endpoint Protection**)에 다음 설정이 포함됩니다. 

- **Windows Defender Credential Guard**: 가상화 기반 보안이 포함된 Credential Guard를 켭니다. 이 기능을 사용하도록 설정하면, **Platform Security Level with Secure Boot**(보안 부팅이 사용된 플랫폼 보안 수준) 및 **가상화 기반 보안**을 둘 다 사용하도록 설정할 경우, 다음 다시 부팅 시 자격 증명을 보호하는 데 도움이 됩니다. 다음 옵션을 사용할 수 있습니다.
  - **사용 안 함**: 이전에 **잠금 없이 설정** 옵션을 사용하여 Credential Guard를 켠 경우 원격으로 Credential Guard를 끕니다.

  - **UEFI 잠금을 사용하여 설정**: 레지스트리 키 또는 그룹 정책을 사용하여 Credential Guard를 사용하지 않도록 설정할 수 없게 합니다. 이 설정을 사용한 후 Credential Guard를 사용하지 않도록 설정하려면 그룹 정책을 “사용 안 함”으로 설정해야 합니다. 그런 다음, 물리적으로 존재하는 사용자가 있는 각 컴퓨터에서 보안 기능을 제거합니다. 이러한 단계는 UEFI에서 지속되는 구성을 지웁니다. UEFI 구성이 지속되는 한, Credential Guard는 사용하도록 설정됩니다.

  - **잠금 없이 설정**: 그룹 정책을 사용하여 원격으로 Credential Guard를 사용하지 않도록 설정할 수 있게 합니다. 이 설정을 사용하는 장치는 Windows 10(버전 1511) 이상에서 실행되어야 합니다.

다음 종속 기술은 Credential Guard를 구성할 때 자동으로 사용하도록 설정됩니다. 

  - **VBS(가상화 기반 보안) 사용**: 다음 다시 부팅 시 VBS(가상화 기반 보안)를 켭니다. 가상화 기반 보안에서는 Windows 하이퍼바이저를 사용하여 보안 서비스에 대한 지원을 제공하며, 보안 부팅이 필요합니다.
  - **보안 부팅 및 DMA(직접 메모리 액세스)**: 보안 부팅 및 직접 메모리 액세스를 통해 VBS를 켭니다. DMA 보호는 하드웨어 지원이 필요하며 제대로 구성된 장치에서만 사용하도록 설정됩니다. 

#### <a name="use-a-custom-subject-name-on-scep-certificate----2064190---"></a>SCEP 인증서에서 사용자 지정 주체 이름 사용 <!-- 2064190 -->
SCEP 인증서 프로필에서 사용자 지정 주체에 **OnPremisesSamAccountName** 일반 이름을 사용할 수 있습니다. 예를 들어 `CN={OnPremisesSamAccountName})`를 사용할 수 있습니다.

####  <a name="block-camera-and-screen-captures-on-android-for-work----1098977-eeready--"></a>Android for Work에서 카메라 및 화면 캡처 차단 <!-- 1098977 eeready-->
두 개의 새로운 속성은 Android 장치에 대한 장치 제한을 구성할 때 차단하는 데 사용할 수 있습니다. 
- 카메라: 장치에서 모든 카메라에 대한 액세스 차단
- 화면 캡처: 화면 캡처를 차단하고, 안전하지 않은 비디오 출력의 디스플레이 장치에 콘텐츠가 표시되지 않도록 방지

Android for Work에 적용됩니다.


### <a name="device-enrollment"></a>장치 등록

#### <a name="new-enrollment-steps-for-users-on-devices-with-macos-high-sierra-10132---1734567---"></a>macOS High Sierra 10.13.2+를 사용하는 장치에서 사용자를 위한 새로운 등록 단계 <!--1734567 -->
macOS high Sierra 10.13.2에 “사용자 승인” MDM 등록의 개념이 도입되었습니다. 승인된 등록을 사용하면 Intune에서 몇 가지 보안에 민감한 설정을 관리할 수 있습니다. 자세한 내용은 Apple의 지원 문서를 참조하세요. https://support.apple.com/HT208019

macOS 회사 포털을 사용하여 등록된 장치는 최종 사용자가 [시스템 기본 설정]을 열고 수동으로 승인을 제공하지 않는 한 “사용자 승인되지 않음”으로 간주됩니다. 이를 위해 macOS 회사 포털은 이제 macOS 10.13.2 이상의 사용자에게 등록 프로세스 마지막 단계에서 해당 등록을 수동으로 승인하도록 안내합니다. Intune 관리 콘솔은 등록된 장치가 사용자 승인되지 않은 경우 보고합니다.



### <a name="device-management"></a>장치 관리

#### <a name="advanced-threat-protection-atp-and-intune-are-fully-integrated----eeready-1629303---"></a>ATP(Advanced Threat Protection)와 Intune이 완전히 통합됨 <!-- EEready 1629303 -->

[ATP(Advanced Threat Protection)](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/dashboard-windows-defender-advanced-threat-protection)는 Windows 10 장치의 위험 수준을 표시합니다. Windows Defender 보안 센터(ATP 포털)에서 Microsoft Intune에 대한 연결을 만들 수 있습니다. 연결이 생성되면 Intune 준수 정책을 사용하여 허용되는 위협 수준이 결정됩니다. 위협 수준을 초과할 경우 AD(Azure Active Directory) 조건부 액세스 정책을 통해 조직 내의 여러 앱에 대한 액세스를 차단할 수 있습니다.

이 기능을 사용하면 ATP가 Windows 10 장치에서 파일 검사, 위협 검색, 위험 보고 등을 수행할 수 있습니다.

[Intune에서 조건부 액세스로 ATP 사용](advanced-threat-protection.md)을 참조하세요.

#### <a name="support-for-user-less-devices----1637553---"></a>사용자가 지정되지 않은 장치에 대한 지원 <!-- 1637553 -->
Intune은 Microsoft Surface Hub와 같은 사용자가 지정되지 않은 장치에서 준수를 평가하는 기능을 지원합니다. 준수 정책은 특정 장치를 대상으로 지정할 수 있습니다. 따라서 연결된 사용자가 없는 장치에 대해 준수(및 비준수)를 확인할 수 있습니다.

#### <a name="delete-autopilot-devices----1713650---"></a>Autopilot 장치 삭제 <!-- 1713650 -->
Intune 관리자는 [Autopilot 장치를 삭제](enrollment-autopilot.md#delete-autopilot-devices)할 수 있습니다.

#### <a name="improved-device-deletion-experience---1832333---"></a>향상된 장치 삭제 환경 <!--1832333 -->
이제 [Intune에서 장치를 삭제](devices-wipe.md#delete-devices-from-the-intune-portal)하기 전에 회사 데이터를 제거하거나 장치를 출하 시 설정으로 초기화할 필요가 없습니다.

새 환경을 보려면 Intune에 로그인하고 **장치** > **모든 장치** > 장치 이름 > **삭제**를 선택합니다.

초기화/사용 중지 확인을 수행하려면 **삭제**하기 전에 **회사 데이터 제거** 및 **출하 시 설정으로 리셋**을 실행하여 표준 장치 수명 주기를 사용할 수 있습니다. 

#### <a name="play-sounds-on-ios-when-in-lost-mode----1947769---"></a>분실 모드에 있을 때 iOS에서 소리 재생 <!-- 1947769 -->
감독 중인 iOS 장치가 MDM(모바일 장치 관리) [분실 모드](device-lost-mode.md)에 있는 경우 [소리를 재생](device-locate.md#activate-lost-mode-sound-alert-on-an-ios-device)할 수 있습니다(**장치** > **모든 장치** > iOS 장치 선택 > **개요** > **자세히**). 소리는 장치가 분실 모드에서 제거되거나 사용자가 장치에서 소리를 사용하지 않도록 설정할 때까지 계속 재생됩니다. iOS 장치 9.3 이상에서 적용됩니다.

#### <a name="block-or-allow-web-results-in-searches-made-on-an-intune-device---1972804--"></a>Intune 장치에서 수행된 검색에서 웹 결과 차단 또는 허용 <!--1972804-->

이제 관리자는 장치에서 수행된 검색에서 웹 결과를 차단할 수 있습니다.

#### <a name="improved-error-messaging-for-apple-mdm-push-certificate-upload-failure----2172331---"></a>Apple MDM 푸시 인증서 업로드 실패에 대한 향상된 오류 메시지 <!-- 2172331 -->

오류 메시지는 기존 MDM 인증서를 갱신할 때 동일한 Apple ID를 사용해야 함을 설명합니다.

#### <a name="test-the-company-portal-for-macos-on-virtual-machines----2216679---"></a>가상 머신에서 macOS용 회사 포털 테스트 <!-- 2216679 -->

Microsoft에서는 IT 관리자가 Parallels Desktop 및 VMware Fusion에서 가상 머신의 macOS용 회사 포털 앱을 테스트하는 데 도움이 되는 지침을 게시했습니다. [테스트를 위해 macOS 가상 머신 등록](macos-enroll.md#enroll-virtual-macos-machines-for-testing)에서 자세히 알아보세요.


### <a name="user-interface"></a>사용자 인터페이스

#### <a name="improved-device-tiles-in-the-windows-10-company-portal---2213364---"></a>Windows 10 회사 포털의 개선된 장치 타일 <!--2213364 -->

저시력 사용자가 더 쉽게 액세스할 수 있고 화면 읽기 도구의 성능이 개선되도록 타일이 업데이트되었습니다.

#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos----2216677---"></a>macOS용 회사 포털 앱에 진단 보고서 보내기 <!-- 2216677 -->
사용자가 Intune 관련 오류를 보고하는 방법을 개선하기 위해 macOS 장치용 회사 포털 앱이 업데이트되었습니다. 회사 포털 앱에서 직원은 다음을 수행할 수 있습니다.

- Microsoft 개발자 팀에 직접 진단 보고서를 업로드합니다.
- 인시던트 ID를 회사의 IT 지원 팀에게 이메일로 전송합니다.

자세한 내용은 [macOS에 대한 오류 보내기](/intune-user-help/send-errors-macos)를 참조하세요.

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10----1195010-wnready---"></a>Windows 10용 회사 포털 앱에서 Intune이 Fluent Design System에 적응함 <!-- 1195010 WNready -->
Windows 10용 Intune 회사 포털 앱이 [Fluent Design System의 탐색 보기](https://docs.microsoft.com/en-us/windows/uwp/design/basics/navigation-basics)로 업데이트되었습니다. 앱의 옆쪽에 모든 최상위 페이지의 정적 세로 목록이 표시됩니다. 링크를 클릭하여 빠르게 페이지를 보고 페이지 간에 전환할 수 있습니다. 이 업데이트는 Intune에서 더욱 공감할 수 있고 친숙한 적응형 환경을 만들려는 Microsoft의 지속적인 노력의 일부로 여러 업데이트 중 첫 번째로 선보이는 것입니다. 업데이트된 형태를 보려면 [앱 UI 의 새로운 기능](whats-new-app-ui.md)으로 이동하세요.

## <a name="week-of-april-16-2018"></a>2018년 4월 16일 주간

#### <a name="use-cisco-anyconnect-client-for-ios----eeready-1333708---"></a>iOS용 Cisco AnyConnect 클라이언트 사용 <!-- EEready 1333708 -->

iOS용 새 VPN 프로필을 만들 때 이제 **Cisco AnyConnect** 및 **Cisco Legacy AnyConnect**의 두 가지 옵션이 있습니다. Cisco AnyConnect 프로필은 4.0.7x 이상 버전을 지원합니다. 기존 iOS Cisco AnyConnect VPN 프로필은 **Cisco Legacy AnyConnect**로 레이블이 지정되며, 현재와 마찬가지로 Cisco AnyConnect 4.0.5x 및 이전 버전에서 계속 작동합니다.

> [!NOTE]
> 이 변경 내용은 iOS에만 적용됩니다. Android, Android for Work 및 macOS 플랫폼에는 계속해서 Cisco AnyConnect 옵션 하나만 사용할 수 있습니다.

#### <a name="jamf-enrolled-macos-devices-can-now-register-with-intune----2370684---"></a>이제 Jamf에 등록된 macOS 장치를 Intune에 등록할 수 있음 <!-- 2370684 -->

macOS 회사 포털 버전 1.3 및 1.4에서는 Jamf 장치가 Intune에 등록되지 않았습니다. macOS 포털 버전 1.4.2에서 이 문제가 해결되었습니다.


## <a name="week-of-april-9-2018"></a>2018년 4월 9일 주간  
#### <a name="updated-help-experience-in-company-portal-app-for-android----1631531---"></a>Android용 회사 포털 앱에서 업데이트된 도움말 환경 <!-- 1631531 -->

Android 플랫폼에 대한 모범 사례에 맞추기 위해 Android용 회사 포털 앱에서 도움말 환경을 업데이트했습니다. 이제 사용자 앱에서 문제가 발생하는 경우 **메뉴** > **도움말**을 누르면 됩니다.
- 또한 진단 로그를 Microsoft에 업로드합니다.
- 회사 지원 담당자에게 문제 및 인시던트 ID를 설명하는 이메일을 보냅니다.  

업데이트된 도움말 환경을 확인하려면 [이메일을 사용하여 로그 보내기](/intune-user-help/send-logs-to-your-it-admin-by-email-android) 및 [Microsoft에 오류 보내기](/intune-user-help/send-logs-to-microsoft-android)로 이동합니다.


#### <a name="new-enrollment-failure-trend-chart-and-failure-reasons-table----1471783---"></a>새 등록 실패 추세 차트 및 실패 이유 테이블 <!-- 1471783 -->

등록 개요 페이지에서 등록 실패의 추세와 실패 원인 상위 5개를 확인할 수 있습니다. 차트 또는 테이블을 클릭하면 세부 사항을 드릴스루하여 문제 해결 도움말 및 재구성 제안을 찾을 수 있습니다.

#### <a name="update-where-to-configure-your-app-protection-policies----2144597---"></a>앱 보호 정책을 구성한 업데이트 <!-- 2144597 -->

Azure Portal의 Microsoft Intune 서비스에서는 **Intune 앱 보호** 서비스 블레이드에서 **모바일 앱** 블레이드로 일시적으로 리디렉션됩니다. 모든 앱 보호 정책이 Intune의 앱 구성에 있는 **모바일 앱** 블레이드에 이미 있습니다. Intune 앱 보호로 이동하는 대신 Intune으로 이동하세요. 2018년 4월에는 리디렉션을 중지하고 **Intune 앱 보호** 서비스 블레이드를 완전히 제거하여 Intune 내 앱 보호 정책의 위치가 하나만 있도록 합니다. 

**이 변경 사항은 어떤 영향을 미치나요?**
이 변경 사항은 Intune 독립형 고객과 하이브리드(Configuration Manager와 Intune) 고객 모두에 영향을 줍니다. 이 통합은 클라우드 관리 관리를 단순화하는 데 도움이 됩니다.

**이러한 변경에 대비하려면 어떻게 해야 하나요?**
**Intune 앱 보호** 서비스 블레이드 대신 **Intune**을 즐겨찾기로 태그를 지정하고 Intune 내 **모바일** 앱 블레이드의 앱 보호 정책 워크플로에 익숙해지도록 합니다. 짧은 시간 동안 리디렉션된 다음, **앱 보호** 블레이드가 제거됩니다. Intune에서 모든 앱 보호 정책이 이미 설정되어 있으므로 조건부 액세스 정책을 수정할 수 있습니다. 조건부 액세스 정책을 수정하는 방법에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요. 


## <a name="week-of-april-2-2018"></a>2018년 4월 2일의 주간

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
이제 Intune APP(앱 정책 보호) 및 CA(조건부 액세스)를 사용하여 Outlook Mobile에서 온-프레미스 Exchange 데이터에 대한 액세스를 보호할 수 있습니다. Azure Portal 내에서 앱 보호 정책을 추가하거나 수정하려면 **Microsoft Intune** > **모바일 앱** > **앱 보호 정책**을 선택합니다. 이 기능을 사용하기 전에 [iOS 및 Android 요구 사항에 대한 Outlook](https://technet.microsoft.com/en-us/library/mt846639(v=exchg.160).aspx)을 충족하는지 확인합니다.

## <a name="week-of-march-26-2018"></a>2018년 3월 26일 주간

### <a name="app-management"></a>앱 관리

#### <a name="alerts-for-expiring-ios-line-of-business-lob-apps-for-microsoft-intune----748789---"></a>Microsoft Intune에 대해 iOS LOB(기간 업무) 애플리케이션에 만료 경고 <!-- 748789 -->

Azure Portal에서 Intune은 막 만료될 iOS LOB(기간 업무) 애플리케이션에 경고를 보냅니다. 새 버전의 iOS LOB(기간 업무) 애플리케이션을 업로드할 때 Intune은 앱 목록에서 만료 알림을 제거합니다. 새로 업로드된 iOS LOB(기간 업무) 애플리케이션에 대해 이러한 만료 알림이 활성화됩니다. 경고가 iOS LOB(기간 업무) 애플리케이션 프로비전 프로필이 만료되기 30일 전에 표시됩니다. 프로필이 만료되면 경고는 만료됨으로 변경됩니다.

#### <a name="customize-your-company-portal-themes-with-hex-codes---1049561---"></a>16진수 코드를 사용하여 회사 포털 테마 사용자 지정 <!--1049561 -->

16진수 코드를 사용하여 회사 포털 앱에서 테마 색을 사용자 지정할 수 있습니다. 16진수 코드를 입력하면 Intune은 텍스트 색과 배경색 간의 대비가 가장 높은 텍스트 색을 결정합니다. **모바일 앱** > **회사 포털**에서 텍스트 색과 회사 로고를 미리 볼 수 있습니다.

### <a name="including-and-excluding-app-assignment-based-on-groups-for-android-enterprise----1813081---"></a>Android Enterprise에 대한 그룹에 따라 앱 할당 포함 및 제외 <!-- 1813081 -->

Android Enterprise(이전의 Android for Work)는 그룹 포함 및 제외를 지원하지만 미리 만들어진 **모든 사용자** 및 **모든 장치** 기본 제공 그룹은 지원하지 않습니다. 자세한 내용은 [Microsoft Intune에서 앱 할당 포함 및 제외](apps-inc-exl-assignments.md)를 참조하세요.


### <a name="device-management"></a>장치 관리

#### <a name="new-security-enhancements-in-the-intune-service-----1637539---"></a>Intune 서비스의 새로운 보안 강화 기능 <!-- 1637539 -->   

Intune 독립 실행형 고객이 **규격**(보안 기능 해제)으로 할당된 정책 없이 장치를 처리하거나 **비호환**(보안 기능 사용)으로 이러한 정책을 처리하는 데 사용할 수 있는 Azure의 Intune에서 토글을 추가했습니다. 이렇게 하면 장치 준수가 평가된 후에 리소스에 액세스할 수 있습니다.

이 기능은 할당된 준수 정책 여부에 따라 다르게 적용됩니다.

- 새로운 또는 기존 테넌트이고 준수 정책이 장치에 할당되지 않는 경우 설정/해제는 자동으로 **준수**로 설정됩니다. 기능은 콘솔의 기본 설정으로 꺼져 있습니다. 최종 사용자에게는 영향이 없습니다.
- 기존 테넌트이며 준수 정책이 장치에 할당된 경우 설정/해제는 자동으로 **비준수**로 설정됩니다. 3월 업데이트가 공개될 때 기능은 기본 설정으로 켜져 있습니다.

CA(조건부 액세스)에서 준수 정책을 사용하고 기능을 설정한 경우, 할당된 준수 정책이 하나도 없는 장치는 CA에 의해 차단됩니다. 이러한 장치에 연결되어 있으며 사전에 이메일에 대한 액세스가 허용된 최종 사용자는 모든 장치에 준수 정책을 하나 이상 할당하지 않는 한 액세스가 손실됩니다.   

Intune 서비스 3월 업데이트에서 기본 설정/해제 상태는 바로 UI에 표시되지만 이 설정/해제 상태는 바로 적용되지 않습니다. 토글이 작동하도록 계정을 파일럿(플라이팅) 테스트할 때까지 토글에 적용한 변경 내용은 장치 준수에 영향을 주지 않습니다. 계정의 파일럿(플라이팅) 테스트를 완료하면 메시지 센터를 통해 알려줍니다. 3월에 Intune 서비스를 업데이트한 후에 최대 몇 일이 걸릴 수 있습니다.

**추가 정보**: [https://aka.ms/compliance_policies](https://aka.ms/compliance_policies)

#### <a name="enhanced-jailbreak-detection----846515---"></a>향상된 탈옥 검색 <!-- 846515 -->

향상된 탈옥 검색은 Intune이 무단 해제된 장치를 평가하는 방법을 향상시키는 새 준수 설정입니다. 이 설정은 장치의 위치 확인 서비스를 사용하고 배터리 사용에 영향을 주도록 더 자주 Intune을 사용하여 장치를 체크 인합니다.

#### <a name="reset-passwords-for-android-o-devices----1238299---"></a>O Android 장치의 암호 다시 설정<!-- 1238299 -->
작업 프로필사용을 하여 등록된 Android 8.0 장치에 암호를 다시 설정할 수 있습니다. Android 8.0 장치에 "암호 다시 설정" 요청을 보내면 해당 장치는 현재 사용자의 새 장치 잠금 해제 암호 또는 관리되는 프로필 챌린지를 설정합니다. 암호 또는 챌린지가 전송되고 즉시 적용됩니다.

#### <a name="targeting-compliance-policies-to-devices-in-device-groups---1307012---"></a>장치 그룹의 장치를 준수 정책의 대상으로 지정 <!--1307012 -->

사용자 그룹의 사용자를 준수 정책의 대상으로 지정할 수 있습니다. 이 업데이트에서는 준수 정책을 장치 그룹의 장치 대상으로 지정할 수 있습니다. 장치 그룹의 일부로 대상이 지정된 장치는 준수 작업을 수신하지 않습니다.

#### <a name="new-management-name-column----1333586---"></a>새 관리 이름 열 <!-- 1333586 -->
 **관리 이름**이라는 새 열은 장치 블레이드에 지원됩니다. 이 이름은 다음 수식에 따라 장치당 할당된 자동 생성되고 편집할 수 없는 이름입니다.
- 모든 장치에 대한 기본 이름: <username><em><devicetype></em><enrollmenttimestamp>
- 대량으로 추가된 장치에 대해: <PackageId/ProfileId><em><DeviceType></em><EnrollmentTime>

이 열은 장치 블레이드에서 선택적입니다. 이 열은 기본으로 지원되지 않고 열 선택기를 사용해서만 액세스할 수 있습니다. 장치 이름은 이 새 열에서 영향을 받지 않습니다.

#### <a name="ios-devices-are-prompted-for-a-pin-every-15-minutes---1550837---"></a>iOS 장치에 15분마다 PIN을 입력하라는 메시지가 표시됩니다.<!--1550837 -->
준수 또는 구성 정책을 iOS 장치에 적용하면 사용자에게 15분마다 PIN을 설정하라는 메시지가 표시됩니다. 사용자가 PIN을 설정할 때까지 계속 메시지가 표시됩니다.

#### <a name="schedule-your-automatic-updates---1805514---"></a>자동 업데이트를 예약합니다.<!--1805514 -->
Intune에서는 [Windows Update 링 설정](windows-update-for-business-configure.md)을 사용하여 자동 업데이트를 설치하도록 제어할 수 있습니다. 이 업데이트에서는 주, 일, 시간을 비롯한 되풀이 업데이트를 예약할 수 있습니다.

#### <a name="use-fully-distinguished-name-as-subject-for-scep-certificate---2221763---"></a>SCEP 인증서에 대한 제목으로 정식 고유 이름 사용<!--2221763 -->
SCEP 인증서 프로필을 만들 때 주체 이름을 입력합니다. 이 업데이트에서는 정식 고유 이름을 주체로 사용할 수 있습니다. **주체 이름**에서 **사용자 지정**을 선택한 다음, `CN={{OnPrem_Distinguished_Name}}`을 입력합니다. `{{OnPrem_Distinguished_Name}}` 변수를 사용하려면 [Azure AD(Active Directory) Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)를 사용하는 `onpremisesdistingishedname` 사용자 특성을 Azure AD와 동기화해야 합니다.

### <a name="device-configuration"></a>장치 구성

#### <a name="enable-bluetooth-contact-sharing---android-for-work---1098983---"></a>Bluetooth 연락처 공유 사용 - Android for Work<!--1098983 -->
기본적으로 Android는 작업 프로필의 연락처를 Bluetooth 장치와 동기화하지 않도록 방지합니다. 결과적으로 작업 프로필 연락처는 Bluetooth 장치의 발신자 ID에 표시되지 않습니다.

이 업데이트에서는 **Android for Work** > **장치 제한** > **작업 프로필 설정**에서 새 설정이 지정됩니다.
- Bluetooth를 통한 연락처 공유

Intune 관리자는 공유할 수 있도록 이러한 설정을 구성할 수 있습니다. 핸즈 프리 사용에 호출자 ID를 표시하는 자동차 기반 Bluetooth 장치를 사용하여 장치를 연결하는 경우에 유용합니다. 사용하도록 설정하면 작업 프로필 연락처가 표시됩니다. 사용하지 않도록 설정하면 작업 프로필 연락처가 표시되지 않습니다.

#### <a name="configure-gatekeeper-to-control-macos-app-download-source----1690459---"></a>macOS 앱 다운로드 원본을 제어하려면 Gatekeeper 구성 <!-- 1690459 -->

해당 앱을 어디서 다운로드할 수 있는지 제어하여 앱에서 장치를 보호하기 위해 Gatekeeper를 구성할 수 있습니다. **Mac 앱 스토어**, **Mac 앱 스토어 및 확인된 개발자** 또는 **원격** 등의 다운로드 원본을 구성할 수 있습니다. 사용자가 이러한 Gatekeeper 제어를 재정의하기 위해 Ctrl+클릭하여 앱을 설치할지 여부를 구성할 수 있습니다.

이러한 설정은 **장치 구성** -> **프로필 만들기** -> **macOS** -> **끝점 보호** 아래에 있습니다.

#### <a name="configure-the-mac-application-firewall----1690461---"></a>Mac 응용 프로그램 방화벽 구성 <!-- 1690461 -->

Mac 응용 프로그램 방화벽을 구성할 수 있습니다. 포트당이 아닌 응용 프로그램당을 기반으로 연결을 제어하는 데 이 방화벽을 사용할 수 있습니다. 이렇게 하면 쉽게 방화벽 보호의 이점을 얻고 바람직하지 않은 앱이 합법적인 앱에 대해 네트워크 포트 열기를 제어하는 것을 방지할 수 있습니다.

이 기능은 **장치 구성** -> **프로필 만들기** -> **macOS** -> **끝점 보호** 아래에서 찾을 수 있습니다.

일단 방화벽 설정을 사용하면 두 가지 전략을 사용하여 방화벽을 구성할 수 있습니다.

- 들어오는 모든 연결 차단

   대상 장치에 대해 들어오는 모든 연결을 차단할 수 있습니다. 이 작업 수행을 선택한 경우 모든 앱에 대해 들어오는 연결이 차단됩니다.

- 특정 앱 허용 또는 차단

   들어오는 연결을 특정 앱이 수신하는 것을 허용하거나 차단할 수 있습니다. 검색 요청에 응답하지 않도록 은폐 모드를 사용할 수도 있습니다.

####  <a name="detailed-error-codes-and-messages----1376342---"></a>자세한 오류 코드 및 메시지 <!-- 1376342 -->

장치 구성에서 자세한 오류 코드 및 오류 메시지를 확인할 수 있습니다. 이 향상된 보고 기능은 설정, 설정 상태 및 자세한 문제 해결 정보를 보여 줍니다.

##### <a name="more-information"></a>추가 정보

- 들어오는 모든 연결 차단

   이는 모든 공유 서비스(예: 파일 공유, 화면 공유)가 들어오는 연결을 수신하는 것을 차단합니다. 들어오는 연결을 여전히 수신할 수 있는 시스템 서비스는 다음과 같습니다.
  - configd - DHCP 및 다른 네트워크 구성 서비스 구현
  - mDNSResponder - Bonjour 구현
  - racoon - IPSec 구현

    공유 서비스를 사용하려면 **들어오는 연결**이 **구성 되지 않음** (**차단**하지 않음)으로 설정되게 합니다.

- 은폐 모드

   이 모드를 사용하여 컴퓨터가 검색 요청에 응답하지 않게 합니다. 그래도 컴퓨터는 권한이 부여된 앱에 대해 들어오는 요청에는 응답합니다. ICMP(ping)와 같은 예기치 않은 요청은 무시합니다.

#### <a name="disable-checks-on-device-restart---1805490---"></a>장치를 다시 시작에 대한 검사를 사용하지 않습니다.<!--1805490 -->
Intune에서는 [소프트웨어 업데이트 관리]](windows-update-for-business-configure.md)를 제어합니다. 이 업데이트에서 <strong>검사 다시 시작</strong> 속성이 지원되고 기본적으로 설정됩니다. 장치를 다시 시작할 때 발생하는 일반적인 검사(예: 활성 사용자, 배터리 수준 등)를 건너뛰려면 <strong>건너뛰기</strong>를 선택합니다.

#### <a name="new-windows-10-insider-preview-channels-available-for-deployment-rings----1746293---"></a>배포 링에 지원되는 새로운 Windows 10 Insider Preview 채널 <!-- 1746293 -->
Windows 10 배포 링을 만들 때 다음 Windows 10 Insider Preview 채널 서비스를 선택하는 옵션이 있습니다.
- Windows Insider 빌드 &#8208; 빠름
- Windows Insider 빌드 &#8208; 느림
- Windows Insider 빌드 릴리스 

이러한 채널에 대한 자세한 내용은 [Insider Preview 빌드 관리](https://insider.windows.com/en-us/for-business-organization-admin/)를 참조하세요.   
Intune에서 배포 채널을 만드는 방법에 대한 자세한 내용은 [Intune에서 소프트웨어 업데이트 관리](windows-update-for-business-configure.md)를 참조하세요.

### <a name="intune-apps"></a>Intune 앱

#### <a name="company-portal-enrollment-improved----1874230-eeready--"></a>회사 포털 등록 향상<!-- 1874230 eeready-->
Windows 10 Build 1703 이상에서 회사 포털을 사용하여 장치를 등록하는 사용자는 이제 해당 앱을 종료하지 않고 등록의 첫 번째 단계를 완료할 수 있습니다.
#### <a name="hololens-and-surface-hub-now-appear-in-device-lists---1725868---"></a>HoloLens 및 Surface Hub가 이제 장치 목록에 표시됩니다. <!--1725868 -->
Intune에 등록된 HoloLens 및 Surface Hub 장치를 Android용 회사 포털 앱에 표시하는 지원을 추가했습니다.

#### <a name="custom-book-categories-for-volume-purchase-program-vpp-ebooks----1488911---"></a>VPP(대량 구매 프로그램) 전자책에 대한 사용자 지정 책 범주 <!-- 1488911 -->
사용자 지정 전자책 범주를 만든 다음, 해당 사용자 지정 전자책 범주에 VPP 전자책을 할당할 수 있습니다. 그러면 최종 사용자는 새로 만든 전자책 범주 및 해당 범주에 할당된 책을 확인할 수 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 앱 및 전자책 관리](vpp-apps.md)를 참조하세요.  

#### <a name="support-changes-for-company-portal-app-for-windows-send-feedback-option----2070166---"></a>Windows용 회사 포털 앱 피드백 보내기 옵션에 대한 지원 변경 내용 <!-- 2070166 -->
2018년 4월 30일부터 Windows용 회사 포털 앱의 **피드백 보내기** 옵션은 Windows 10 1주년 업데이트(1607) 이상을 실행하는 장치에서만 작동합니다. 다음 환경에서 Windows용 회사 포털 앱을 사용하는 경우 피드백 보내기 옵션이 더 이상 지원되지 않습니다.  
- Windows 10, 1507 릴리스  
- Windows 10, 1511 릴리스  
- Windows Phone 8.1 

Windows 10 RS1 이상에서 장치가 실행 중인 경우 스토어에서 Windows 회사 포털 앱의 최신 버전을 다운로드하세요. 지원되지 않는 버전을 실행 중인 경우 다음 채널을 통해 피드백을 계속 보내세요. 
- Windows 10의 피드백 허브 앱
- 메일 WinCPfeedback@microsoft.com  

#### <a name="new-windows-defender-application-guard-settings----1631890---"></a>새 Windows Defender Application Guard 설정 <!-- 1631890 -->

- **그래픽 가속 사용**: 관리자는 Windows Defender Application Guard에 그래픽 가상 프로세서를 사용할 수 있습니다. 이 설정은 CPU가 그래픽 렌더링을 vGPU에 오프로드하는 것을 허용합니다. 이렇게 하면 컨테이너 내에서 그래픽 집약적인 웹 사이트를 작업하거나 비디오를 볼 때 성능을 향상할 수 있습니다.

- **SaveFilestoHost**: 관리자는 컨테이너에서 실행되는 Microsoft Edge에서 호스트 파일 시스템으로 파일을 전달하도록 설정할 수 있습니다. 이 설정을 켜면 사용자가 컨테이너의 Microsoft Edge에서 호스트 파일 시스템으로 파일을 다운로드할 수 있습니다.

#### <a name="mam-protection-policies-targeted-based-on-management-state----1665993---"></a>관리 상태에 따라 대상으로 지정된 MAM 보호 정책 <!-- 1665993 -->
장치의 관리 상태에 따라 MAM 정책을 대상으로 지정할 수 있습니다.
- **Android 장치** - 관리되지 않는 장치, Intune 관리 장치 및 Intune 관리 Android Enterprise 프로필(이전의 Android for Work)을 대상으로 지정할 수 있습니다.
- **iOS 장치** - 관리되지 않는 장치(MAM만 해당) 또는 Intune 관리 장치를 대상으로 지정할 수 있습니다.

    > [!NOTE]
    > - 이 기능에 대한 iOS 지원은 2018년 4월까지 출시됩니다.

자세한 내용은 [장치 관리 상태에 따른 대상 응용 프로그램 보호 정책](app-protection-policies.md)을 참조하세요.

#### <a name="improvements-to-the-language-in-the-company-portal-app-for-windows----1683758---"></a>Windows용 회사 포털 앱의 언어 개선 사항 <!-- 1683758 -->
귀사에 더욱 친숙하고 구체적이 되도록 Windows 10용 회사 포털에서 언어를 개선하였습니다. 수행한 몇 가지 샘플 이미지를 보려면 [앱 UI의 새로운 기능](whats-new-app-ui.md)을 참조하세요.

#### <a name="new-additions-to-our-docs-about-user-privacy----1440709---"></a>사용자 개인 정보 보호에 대한 문서에 새로 추가된 기능 <!-- 1440709 -->
최종 사용자에게 해당 데이터 및 개인 정보 보호에 대한 제어를 제공하려는 노력의 일환으로 회사 포털 앱에서 로컬로 저장된 데이터를 보고 제거하는 방법을 설명하는 문서에 업데이트를 게시했습니다. 다음에서 이러한 업데이트를 찾을 수 있습니다.

- **Android**: [Intune에서 Android 장치를 제거하는 방법](/intune-user-help/unenroll-your-device-from-intune-android.md)
- **사용자가 사용 약관을 거부한 경우 Android**: ["사용 약관" 거부한 경우 장치 관리를 제거합니다.](/intune-user-help/unenroll-your-device-from-intune-if-you-declined-terms-of-use-android.md)
- **iOS**: [Intune에서 iOS 장치 제거](/intune-user-help/unenroll-your-device-from-intune-ios.md)
- **Windows**: [Intune에서 Windows 장치 제거](/intune-user-help/unenroll-your-device-from-intune-windows.md)

## <a name="week-of-march-19-2018"></a>2018년 3월 19일 주간

### <a name="export-all-devices-into-csv-files-in-ie-edge-or-chrome----2258071---"></a>모든 장치를 IE, Edge 또는 Chrome의 CSV 파일로 내보내기 <!-- 2258071 -->
**장치** > **모든 장치**에서 장치를 CSV로 서식이 지정된 목록으로 **내보낼** 수 있습니다. 10,000개 이상의 장치가 있는 IE(Internet Explorer) 사용자는 해당 장치를 여러 파일로 성공적으로 내보낼 수 있습니다. 각 파일에는 최대 10,000개의 장치가 있습니다.

30,000개 이상의 장치가 있는 Edge 및 Chrome 사용자는 해당 장치를 여러 파일로 성공적으로 내보낼 수 있습니다. 각 파일에는 최대 30,000개의 장치가 있습니다.

[장치 관리](device-management.md)에서는 관리하는 장치에서 수행할 수 있는 작업에 대한 자세한 세부 정보를 제공합니다.

## <a name="week-of-march-12-2018"></a>2018년 3월 12일 주

### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview----710595---"></a>Azure Active Directory 웹 사이트에는 Intune Managed Browser 앱이 필요하고 Managed Browser(공개 미리 보기)에 Single Sign-On을 지원할 수 있습니다.<!-- 710595 -->

이제 Azure AD(Azure Active Directory)를 사용하여 모바일 장치의 Intune Managed Browser 앱에 대한 웹 사이트 액세스를 제한할 수 있습니다. Managed Browser에서 웹 사이트 데이터는 최종 사용자 개인 데이터와 별도로 안전하게 유지됩니다. 또한 Managed Browser는 Azure AD에서 보호하는 사이트에 Single Sign-On 기능을 지원합니다. Managed Browser에 로그인하거나 Intune에서 관리하는 다른 앱과 함께 장치에서 Managed Browser를 사용하면 사용자에게 자격 증명을 입력하지 않고도 Azure AD에서 보호되는 회사 사이트에 액세스할 수 있습니다. 이 기능은 OWA(Outlook Web Access) 및 SharePoint Online과 같은 사이트뿐만 아니라 Azure 앱 프록시를 통해 액세스되는 인트라넷 리소스와 같은 다른 회사 사이트에도 적용됩니다. 자세한 내용은 [Azure Active Directory 조건부 액세스의 액세스 제어](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-controls)를 참조하세요.

#### <a name="company-portal-app-for-android-visual-updates---976944---"></a>Android용 회사 포털 앱 시각적 업데이트 <!--976944 -->

Android의 [자료 디자인](https://material.io/) 지침에 따르도록 Android용 회사 포털 앱을 업데이트했습니다. [앱 UI의 새로운 기능](whats-new-app-ui.md) 아티클에서 새 아이콘의 이미지를 볼 수 있습니다.

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

## <a name="week-of-february-19-2018"></a>2018년 2월 19일부터 시작되는 주

### <a name="device-enrollment"></a>장치 등록

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685---"></a>여러 Apple DEP/Apple School Manager 계정에 대한 Intune 지원 <!-- 747685 -->

이제 Intune은 최대 100개의 다른 [Apple DEP(장비 등록 프로그램)](device-enrollment-program-enroll-ios.md) 또는 [Apple School Manager](apple-school-manager-set-up-ios.md) 계정의 장치 등록을 지원합니다. 업로드된 각 토큰을 등록 프로필과 장치에 대해 별도로 관리할 수 있습니다. 업로드된 DEP/School Manager 토큰마다 다른 등록 프로필을 자동으로 할당할 수 있습니다. School Manager 토큰이 여러 개 업로드된 경우 한 번에 하나의 토큰만 Microsoft School Data Sync와 공유할 수 있습니다.

Graph를 통해 Apple DEP 또는 ASM을 관리하기 위한 베타 Graph API 및 게시된 스크립트는 마이그레이션 후 더 이상 작동하지 않습니다. 새 베타 Graph API가 개발 중이며 마이그레이션 후 릴리스될 예정입니다.

#### <a name="see-enrollment-restrictions-per-user----1634444-eeready-wnready---"></a>사용자별 등록 제한 보기 <!-- 1634444 eeready wnready -->
이제 **할당** 목록에서 **등록 제한**을 선택함으로써 각 사용자에게 적용되는 [등록 제한](enrollment-restrictions-set.md)을 **문제 해결** 블레이드에 표시할 수 있습니다.

### <a name="device-management"></a>장치 관리
#### <a name="windows-defender-health-status-and-threat-status-reports---854704---"></a>Windows Defender 상태 및 위협 상태 보고서 <!--854704 -->

Windows Defender의 상태를 이해하는 것은 Windows PC 관리의 핵심입니다.  이 업데이트를 사용해 Intune은 Windows Defender 에이전트의 상태에 새 보고서와 작업을 추가합니다. [장치 정책 준수 워크로드](compliance-policy-monitor.md)에 상태 롤업 보고서를 사용하면 다음 작업이 필요한 장치를 볼 수 있습니다.
- 서명 업데이트
- 다시 시작
- 수동 작업
- 전체 검사
- 개입이 필요한 기타 에이전트 상태

각 상태 범주에 대한 드릴인 보고서에는 주의가 필요한 개별 PC 또는 **정리**로 보고되는 PC가 나열됩니다.

#### <a name="new-privacy-settings-for-device-restrictions---1308926---"></a>장치 제안에 대한 새로운 개인 정보 설정 <!--1308926 -->
장치에 [두 가지 새로운 개인 정보 설정](device-restrictions-windows-10.md#privacy)이 제공됩니다.
- **사용자 작업 게시**: 작업 전환기에서 공유 경험 및 최근에 사용된 리소스 검색을 차단하려면 이 옵션을 **차단**으로 설정합니다.
- **로컬 작업만**: 로컬 작업에 대해서만 작업 전환기에서 공유 경험 및 최근에 사용된 리소스 검색을 차단하려면 이 옵션을 **차단**으로 설정합니다.

#### <a name="new-settings-for-the-edge-browser---1469166---"></a>Microsoft Edge 브라우저에 대한 새 설정 <!--1469166 -->
Microsoft Edge 브라우저에서는 [두 가지 새로운 설정](device-restrictions-windows-10.md#edge-browser)인 **자주 사용하는 파일 경로** 및 **즐겨찾기에 대한 변경**을 사용할 수 있습니다.

### <a name="app-management"></a>앱 관리
#### <a name="protocol-exceptions-for-applications---1035509---"></a>응용 프로그램에 대한 프로토콜 예외 <!--1035509 -->

Intune MAM(모바일 응용 프로그램 관리) 데이터 전송 정책에 대한 예외를 만들어서 관리되지 않는 응용 프로그램을 열 수 있습니다. 이러한 응용 프로그램은 IT가 신뢰할 수 있는 것이어야 합니다. 관리자가 만드는 예외를 제외하고, 데이터 전송 정책을 **관리되는 앱만**으로 설정하는 경우 데이터 전송은 Intune에서 관리하는 응용 프로그램으로 계속 제한됩니다. 프로토콜(iOS) 또는 패키지(Android)를 사용하여 제한을 만들 수 있습니다.

예를 들어 Webex 패키지를 MAM 데이터 전송 정책의 예외로 추가할 수 있습니다. 이렇게 하면 관리되는 Outlook 이메일 메시지의 Webex 링크가 Webex 응용 프로그램에서 바로 열립니다. 관리되지 않는 다른 응용 프로그램에서는 데이터 전송이 계속 제한됩니다. 자세한 내용은 [앱에 대한 데이터 전송 정책 예외](app-protection-policies-exception.md)를 참조합니다.

#### <a name="windows-information-protection-wip-encrypted-data-in-windows-search-results----1469193---"></a>Windows 검색 결과의 WIP(Windows Information Protection) 암호화된 데이터 <!-- 1469193 -->
WIP(Windows Information Protection) 정책의 설정을 사용하면 WIP 암호화된 데이터를 Windows 검색 결과에 포함할지 여부를 제어할 수 있습니다. Windows 정보 보호 정책의 **고급 설정**에서 **Windows Search Indexer로 암호화된 항목 검색 가능**을 선택해 앱 보호 정책 옵션을 설정합니다. 앱 보호 정책은 *Windows 10* 플랫폼에 설정돼야 하며 해당 앱 정책 **등록 상태**는 **등록을 통해** 설정돼야 합니다. 자세한 내용은 [Windows Search Indexer로 암호화된 항목 검색 가능](windows-information-protection-policy-create.md#allow-windows-search-indexer-to-search-encrypted-items)을 참조합니다.

#### <a name="configuring-a-self-updating-mobile-msi-app----1740840---"></a>자체 업데이트 모바일 MSI 앱 구성 <!-- 1740840 -->
버전 확인 프로세스를 무시하도록 알려진 자체 업데이트 모바일 MSI 앱을 구성할 수 있습니다. 이 기능은 경합 상태를 방지하는 데 유용합니다. 예를 들어 이런 유형의 경합 상태는 앱 개발자가 앱을 자동 업데이트하는 동시에 Intune에서도 앱을 업데이트하는 경우 발생할 수 있습니다. 둘 다 Windows 클라이언트에서 앱 버전을 적용하려 시도할 수 있으며, 이로 인해 충돌이 발생할 수 있습니다. 이러한 자동으로 업데이트된 MSI 앱의 경우 **앱 정보** 블레이드에서 **앱 버전 무시** 설정을 구성할 수 있습니다. 이 설정이 **예**로 전환될 경우 Microsoft Intune에서 Windows 클라이언트에 설치 된 앱 버전을 무시하게 됩니다.

#### <a name="related-sets-of-app-licenses-supported-in-intune----1864117---"></a>Intune에서 지원되는 관련 앱 라이선스 집합 <!-- 1864117 -->
이제 Azure Portal의 Intune은 관련 앱 라이선스 집합을 UI에서 단일 앱 항목으로 지원합니다. 또한 비즈니스용 Microsoft 스토어에서 동기화되는 오프라인 라이선스 앱은 단일 앱 항목으로 통합되고, 개별 패키지의 배포 세부 정보는 단일 항목으로 마이그레이션됩니다. Azure Portal에서 관련 앱 라이선스 집합을 보려면 **모바일 앱** 블레이드에서 **앱 라이선스**를 선택합니다.

### <a name="device-configuration"></a>장치 구성
#### <a name="windows-information-protection-wip-file-extensions-for-automatic-encryption----1463582---"></a>자동 암호화를 위한 WIP(Windows Information Protection) 파일 확장명 <!-- 1463582 -->
WIP(Windows Information Protection) 정책의 설정으로 이제 WIP 정책에서 정의된 대로 회사 경계 내부의 SMB(Server Message Block) 공유에서 복사하는 경우 파일 확장명은 자동으로 암호화되도록 지정할 수 있습니다.

#### <a name="configure-resource-account-settings-for-surface-hubs"></a>Surface Hub에 대한 리소스 계정 설정 구성

Surface Hub에 대한 리소스 계정 설정을 원격으로 구성할 수 있습니다.

리소스 계정은 Surface Hub가 Skype/Exchange에 인증하는 데 사용되므로 모임에 참여할 수 있습니다.
Surface Hub가 모임에서 회의실로 표시되도록 고유한 리소스 계정을 만들 수 있습니다.
예를 들어 **회의실 B41/6233**이라는 리소스 계정을 만들 수 있습니다.

> [!NOTE]
> - 필드를 비워 두면 장치에서 이전에 구성된 특성이 재정의됩니다.
>
> - 리소스 계정 속성은 Surface Hub에서 동적으로 변경할 수 있습니다. 예를 들어 암호 순환이 켜져 있으면 Azure 콘솔의 값이 장치에서 현실을 반영할 때까지 다소 시간이 걸릴 수 있습니다.
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


### <a name="role-based-access-control"></a>역할 기반 액세스 제어
### <a name="intune-apps"></a>Intune 앱
#### <a name="support-for-offline-apps-from-the-microsoft-store-for-business---1222672--"></a>비즈니스용 Microsoft 스토어의 오프라인 앱 지원 <!--1222672-->
이제 비즈니스용 Microsoft 스토어에서 구매한 오프라인 앱이 Azure Portal에 동기화됩니다. 그런 다음, 이러한 앱을 장치 그룹 또는 사용자 그룹에 배포할 수 있습니다. 오프라인 앱은 스토어가 아닌 Intune을 통해 설치됩니다.

#### <a name="prevent-end-users-from-manually-adding-or-removing-accounts-in-the-work-profile----1728700---"></a>최종 사용자가 작업 프로필의 계정을 수동으로 추가 또는 삭제하지 못하게 방지 <!-- 1728700 -->

Gmail 앱을 Android for Work 프로필에 배포하면, Android for Work 장치 제한 프로필에서 **계정 추가 및 제거** 설정을 사용하여 최종 사용자가 작업 프로필에 계정을 수동으로 추가하거나 삭제하지 못하게 할 수 있습니다.

## <a name="week-of-february-5-2018"></a>2018년 2월 5일부터 시작되는 주

### <a name="device-enrollment"></a>장치 등록

#### <a name="new-option-for-user-authentication-for-apple-bulk-enrollment----747625-eeready---"></a>Apple 대량 등록을 위한 새로운 사용자 인증 옵션 <!-- 747625 eeready -->

> [!NOTE]
> 새 테넌트는 바로 제공됩니다. 기존 테넌트의 경우 이 기능은 4월 중 공개됩니다. 이 출시가 완료될 때까지는 이러한 새 기능에 액세스하지 못할 수 있습니다.

Intune은 다음 등록 방법에 대해 회사 포털 앱을 사용하여 장치를 인증하는 옵션을 제공합니다.

- Apple 장비 등록 프로그램
- Apple School Manager
- Apple Configurator 등록

회사 포털 옵션을 사용하면 이러한 등록 방법을 차단하지 않고 Azure Active Directory 다단계 인증을 적용할 수 있습니다.

회사 포털 옵션을 사용할 경우 Intune은 사용자 선호도 등록을 위한 iOS 설정 도우미의 사용자 인증을 건너뜁니다. 따라서 처음에는 장치가 사용자 없는 장치로 등록되므로 사용자 그룹의 구성 또는 정책을 받지 않습니다. 장치 그룹의 구성과 정책만 받습니다. 그러나 Intune이 장치에 회사 포털 앱을 자동으로 설치합니다. 회사 포털 앱을 시작하고 로그인하는 첫 번째 사용자가 Intune에서 해당 장치와 연결됩니다. 사용자는 이때 사용자 그룹의 구성과 정책을 받습니다. 사용자 연결을 변경하려면 다시 등록해야 합니다.

#### <a name="intune-support-for-multiple-apple-dep--apple-school-manager-accounts----747685-eeready---"></a>여러 Apple DEP/Apple School Manager 계정에 대한 Intune 지원 <!-- 747685 eeready -->

이제 Intune은 최대 100개의 다른 Apple DEP(장비 등록 프로그램) 또는 Apple School Manager 계정의 장치 등록을 지원합니다. 업로드된 각 토큰을 등록 프로필과 장치에 대해 별도로 관리할 수 있습니다. 업로드된 DEP/School Manager 토큰마다 다른 등록 프로필을 자동으로 할당할 수 있습니다. School Manager 토큰이 여러 개 업로드된 경우 한 번에 하나의 토큰만 Microsoft School Data Sync와 공유할 수 있습니다.

Graph를 통해 Apple DEP 또는 ASM을 관리하기 위한 베타 Graph API 및 게시된 스크립트는 마이그레이션 후 더 이상 작동하지 않습니다. 새 베타 Graph API가 개발 중이며 마이그레이션 후 릴리스될 예정입니다.

### <a name="remote-printing-over-a-secure-network----1709994----"></a>보안 네트워크를 통한 원격 인쇄 <!-- 1709994  -->
PrinterOn의 무선 모바일 인쇄 솔루션을 사용하면 사용자가 보안 네트워크를 통해 언제 어디서나 원격으로 인쇄할 수 있습니다. PrinterOn은 iOS 및 Android용 Intune 앱 SDK와 둘 다 통합됩니다. 관리 콘솔의 Intune **앱 보호 정책** 블레이드를 통해 이 앱을 앱 보호 정책의 대상으로 지정할 수 있습니다. 최종 사용자는 Intune 에코시스템에서 사용하기 위해 Play 스토어 또는 iTunes를 통해 'PrinterOn for Microsoft' 앱을 다운로드할 수 있습니다.

### <a name="macos-company-portal-support-for-enrollments-that-use-the-device-enrollment-manager----1352411---"></a>macOS 회사 포털은 장치 등록 관리자를 사용한 등록을 지원 <!-- 1352411 -->

사용자는 macOS 회사 포털에 등록할 때 장치 등록 관리자를 사용할 수 있습니다.

## <a name="week-of-january-29-2018"></a>2018년 1월 29일

### <a name="device-enrollment"></a>장치 등록

#### <a name="alerts-for-expired-tokens-and-tokens-that-will-soon-expire----1639263---"></a>만료된 토큰 및 곧 만료되는 토큰에 대한 경고 <!-- 1639263 -->
개요 페이지에는 이제 만료된 토큰과 곧 만료되는 토큰에 대한 경고가 표시됩니다. 단일 토큰에 대한 경고를 클릭하면 토큰의 세부 정보 페이지로 이동합니다.  여러 토큰이 포함된 경고를 클릭하면 해당 상태의 모든 토큰 목록으로 이동합니다. 관리자는 만료 날짜 전에 해당 토큰을 갱신해야 합니다.

### <a name="device-management"></a>장치 관리

#### <a name="remote-erase-command-support-for-macos-devices----1438084---"></a>macOS 장치를 위한 원격 “지우기” 명령 지원 <!-- 1438084 -->

관리자는 macOS 장치에 지우기 명령을 원격으로 실행할 수 있습니다.

> [!IMPORTANT]
> 지우기 명령은 취소할 수 없으며 주의해서 사용해야 합니다.

지우기 명령은 장치에서 운영 체제를 비롯한 모든 데이터를 제거합니다. 또한 Intune 관리에서 장치를 제거합니다. 사용자에게 경고가 표시되지 않으며, 명령을 실행하는 즉시 지우기가 수행됩니다.

6자리 복구 PIN을 구성해야 합니다. 이 PIN을 사용하여 지워진 장치의 잠금을 해제할 수 있으며, 이때 운영 체제의 재설치가 시작됩니다. 지우기가 시작된 후에는 Intune의 장치 개요 블레이드에 있는 상태 표시줄에 PIN이 표시됩니다. 지우기가 진행되는 동안 PIN이 계속 유지됩니다. 지우기가 완료되면 장치가 Intune 관리에서 완전히 사라집니다. 장치를 복원하는 누구든지 사용할 수 있도록 복구 PIN을 기록해야 합니다.

#### <a name="revoke-licenses-for-an-ios-volume-purchasing-program-token----820870---"></a>iOS Volume Purchasing Program 토큰에 대한 라이선스 철회 <!-- 820870 -->
지정된 VPP 토큰에 대한 모든 iOS VPP(Volume-Purchase Program) 앱의 라이선스를 철회할 수 있습니다.

### <a name="app-management"></a>앱 관리

#### <a name="revoking-ios-volume-purchase-program-apps-----820863---"></a>iOS Volume-Purchase Program 앱 철회 <!-- 820863 -->
하나 이상의 iOS VPP(Volume-Purchase Program) 앱이 설치된 지정된 장치의 경우 장치의 관련 장치 기반 앱 라이선스를 철회할 수 있습니다. 앱 라이선스를 철회해도 장치에서 관련 VPP 앱이 제거되지 않습니다. VPP 앱을 제거하려면 할당 작업을 **제거**로 변경해야 합니다. 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 프로그램을 통해 구매한 iOS 앱을 관리하는 방법](vpp-apps-ios.md)을 참조하세요.

#### <a name="assign-office-365-mobile-apps-to-ios-and-android-devices-using-built-in-app-type----1332318---"></a>기본 제공 앱 유형을 사용하여 iOS 및 Android 장치에 Office 365 모바일 앱 할당<!-- 1332318 -->
**기본 제공** 앱 유형을 사용하면 사용자가 관리하는 iOS 및 Android 장치에 Office 365 앱을 손쉽게 만들고 할당할 수 있습니다. 이러한 앱에는 Word, Excel, PowerPoint 및 OneDrive와 같은 0365 앱이 포함됩니다. 특정 앱을 앱 유형에 할당하고, 앱 정보 구성을 편집할 수 있습니다.

#### <a name="including-and-excluding-app-assignment-based-on-groups----1406920---"></a>그룹에 따라 앱 할당 포함 및 제외 <!-- 1406920 -->

앱 할당 중이나 할당 유형을 선택한 후 포함할 그룹과 제외할 그룹을 선택할 수 있습니다.

### <a name="device-configuration"></a>장치 구성

#### <a name="you-can-assign-an-application-configuration-policy-to-groups-by-including-and-excluding-assignments-----1480316---"></a>할당을 포함하거나 제외하여 응용 프로그램 구성 정책을 그룹에 할당할 수 있습니다. <!-- 1480316 -->

포함 및 제외 할당의 조합을 사용하여 사용자 및 장치 그룹에 응용 프로그램 구성 정책을 할당할 수 있습니다. 할당을 그룹의 사용자 정의 선택 또는 가상 그룹으로 선택할 수 있습니다. 가상 그룹은 **모든 사용자**, **모든 장치** 또는 **모든 사용자 + 모든 장치**를 포함할 수 있습니다.

#### <a name="support-for-windows-10-edition-upgrade-policy------903672archived-1119689---"></a>Windows 10 버전 업그레이드 정책에 대한 지원  <!-- 903672(archived), 1119689 -->  
Windows 10 장치를 Windows 10 Education, Windows 10 Education N, Windows 10 Professional, Windows 10 Professional N, Windows 10 Professional Education 및 Windows 10 Professional Education N으로 업그레이드하는 Windows 10 버전 업그레이드 정책을 만들 수 있습니다. Windows 10 버전 업그레이드에 대한 자세한 내용은 [Windows 10 버전 업그레이드 구성 방법](edition-upgrade-configure-windows-10.md)을 참조하세요.

#### <a name="conditional-access-policies-for-intune-is-only-available-from-the-azure-portal-----1737088-1634311---"></a>Intune에 대한 조건부 액세스 정책은 Azure Portal에서만 사용할 수 있음 <!-- 1737088 1634311 -->

이 릴리스부터 **Azure Active Directory** > **조건부 액세스**에서 [Azure Portal](https://portal.azure.com)의 조건부 액세스 정책을 구성하고 관리해야 합니다. 편의상, **Intune** > **조건부 액세스**를 통해 Azure Portal의 Intune에서 이 블레이드에 액세스할 수도 있습니다.

#### <a name="updates-to-compliance-emails---1637547---"></a>준수 메일 업데이트 <!--1637547 -->

비준수 장치를 보고하기 위해 메일을 보낼 때 비준수 장치에 대한 세부 정보가 포함됩니다.


## <a name="week-of-january-22-2018"></a>2018년 1월 22일

### <a name="intune-apps"></a>Intune 앱

#### <a name="new-functionality-for-the-resolve-action-for-android-devices---1583480--"></a>Android 장치의 "해결" 작업을 위한 새로운 기능 <!--1583480-->

Android용 회사 포털 앱은 **장치 설정 업데이트**에 대한 "해결" 작업을 확장하여 [장치 암호화 문제](/intune-user-help/encrypt-your-device-android)를 해결합니다.

#### <a name="remote-lock-available-in-company-portal-app-for-windows-10---676506--"></a>Windows 10용 회사 포털 앱에서 원격 잠금 사용 가능 <!--676506-->
이제 최종 사용자가 Windows 10용 회사 포털 앱에서 자신의 장치를 원격으로 잠글 수 있습니다. 최종 사용자가 적극적으로 사용하는 로컬 장치에는 이것이 표시되지 않습니다.

#### <a name="easier-resolution-of-compliance-issues-for-the-company-portal-app-for-windows-10---676546--"></a>Windows 10용 회사 포털 앱의 준수 문제 해결 용이 <!--676546-->
Windows 장치를 사용하는 최종 사용자는 회사 포털 앱에서 비준수 이유를 탭할 수 있습니다. 가능하면 문제를 해결하기 위해 설정 앱의 올바른 위치로 직접 이동시킵니다.

## <a name="week-of-december-11-2017"></a>2017년 12월 11일 주

### <a name="device-configuration"></a>장치 구성

#### <a name="new-automatic-redeployment-setting----1469168---"></a>새 자동 재배포 설정 <!-- 1469168 -->
**자동 재배포** 설정은 관리 권한을 가진 사용자가 장치 잠금 화면에서 **CTRL + Win + R**을 사용하여 모든 사용자 데이터 및 설정을 삭제할 수 있습니다. 장치가 자동으로 재구성되고 관리에 다시 등록됩니다. 이 설정은 Windows 10 > [장치 제한] > [일반] > [자동 재배포]에서 찾을 수 있습니다. 자세한 내용은 [Windows 10에 대한 Intune 장치 제한 설정](device-restrictions-windows-10.md#general)을 참조하세요.

#### <a name="support-for-additional-source-editions-in-the-windows-10-edition-upgrade-policy-----903672--1119689---"></a>Windows 10 버전 업그레이드 정책에서 추가 소스 버전 지원 <!-- 903672,  1119689 -->
이제 Windows 10 버전 업그레이드 정책을 사용하여 추가 Windows 10 버전(Windows 10 Pro, Windows 10 Pro for Education, Windows 10 클라우드 등)에서 업그레이드할 수 있습니다. 이 릴리스 이전에는 지원되는 버전 업그레이드 경로가 더 제한적이었습니다. 자세한 내용은 [Windows 10 버전 업그레이드를 구성하는 방법](edition-upgrade-configure-windows-10.md)을 참조하세요.

#### <a name="new-windows-defender-security-center-wdsc-device-configuration-profile-settings----1335507---"></a>새 WDSC(Windows Defender 보안 센터) 장치 구성 프로필 설정 <!-- 1335507 -->

Intune은 **Windows Defender 보안 센터**라는 끝점 보호가 적용되는 장치 구성 프로필 설정의 새 섹션을 추가합니다. IT 관리자는 최종 사용자가 액세스할 수 있는 Windows Defender 보안 센터 앱 영역을 구성할 수 있습니다. IT 관리자가 Windows Defender 보안 센터 앱 영역을 숨기면 숨겨진 영역에 관련된 모든 알림이 사용자 장치에 표시되지 않습니다.

관리자는 Windows Defender 보안 센터 장치 구성 프로필 설정에서 이러한 영역을 숨길 수 있습니다.
- 바이러스 및 위협 방지
- 장치 성능 및 상태
- 방화벽 및 네트워크 보호
- 앱 및 브라우저 제어
- 패밀리 옵션

IT 관리자는 사용자가 받는 알림을 사용자 지정할 수도 있습니다. 예를 들어, 사용자가 WDSC의 표시되는 영역에서 생성되는 모든 알림을 수신할지, 아니면 중요 알림만 수신할지 구성할 수 있습니다. 중요하지 않은 알림에는 스캔이 완료되었을 경우 생성되는 Windows Defender 바이러스 백신 작업 및 알림에 대한 주기적 요약이 포함됩니다. 다른 모든 알림은 중요 알림으로 간주합니다. 또한 알림 콘텐츠 자체를 사용자 지정할 수 있습니다. 예를 들어, 사용자의 장치에 표시되는 알림에 포함할 IT 담당자 정보를 제공할 수 있습니다.

#### <a name="multiple-connector-support-for-scep-and-pfx-certificate-handling----1361755---"></a>SCEP 및 PFX 인증서 처리에 대한 여러 커넥터 지원 <!-- 1361755 -->

이제 온-프레미스 NDES 커넥터를 사용하여 인증서를 장치에 전달하는 고객이 단일 테넌트에 여러 커넥터를 구성할 수 있습니다.

이 새로운 기능은 다음 시나리오를 지원합니다.

- **고가용성**

각 NDES Connector는 Intune에서 인증서 요청을 풀합니다.  하나의 NDES Connector가 오프라인으로 전환될 경우 다른 커넥터는 계속 요청을 처리할 수 있습니다.

#### <a name="customer-subject-name-can-use-aaddeviceid-variable-----1468599---"></a>고객 주체 이름이 AAD_DEVICE_ID 변수를 사용할 수 있음 <!-- 1468599 -->

Intune에서 SCEP 인증서 프로필을 만드는 경우 이제 사용자 지정 주체 이름을 만들 때 AAD_DEVICE_ID 변수를 사용할 수 있습니다.   이 SCEP 프로필을 사용하여 인증서를 요청하면 해당 변수가 인증서 요청을 만드는 장치의 AAD 장치 ID로 바뀝니다.


### <a name="device-management"></a>장치 관리

#### <a name="manage-jamf-enrolled-macos-devices-with-intunes-device-compliance-engine----1592747---"></a>Intune의 장치 준수 엔진을 사용하여 Jamf에 등록된 macOS 장치 관리 <!-- 1592747 -->
이제 Jamf를 사용하여 macOS 장치 상태 정보를 Intune에 전송할 수 있으며, Intune은 Intune 콘솔에 정의된 정책을 사용하여 장치의 준수 여부를 평가합니다. 장치 준수 상태 및 기타 조건(예: 위치, 사용자 위험 등)에 기반을 둔 조건부 액세스는 Office 365를 비롯하여 Azure AD와 연결된 클라우드 및 온-프레미스 응용 프로그램에 액세스하는 macOS 장치에 대한 준수를 적용합니다. [Jamf 통합 설정](conditional-access-integrate-jamf.md) 및 [Jamf 관리 장치에 대해 준수 적용](conditional-access-assign-jamf.md)에 대해 자세히 알아보세요.

#### <a name="new-ios-device-action------1424701---"></a>새로운 iOS 장치 작업 <!-- 1424701 -->

이제 iOS 10.3 감독 장치를 종료할 수 있습니다. 이 작업을 수행하면 최종 사용자에게 경고하지 않고 장치가 즉시 종료됩니다. **장치** 워크로드에서 장치를 선택하면 장치 속성에서 **시스템 종료(감독 모드인 경우에만)** 작업을 찾을 수 있습니다.

#### <a name="disallow-datetime-changes-to-samsung-knox-devices----1468103---"></a>Samsung Knox 장치의 날짜/시간 변경 허용 안함 <!-- 1468103 -->

Samsung Knox 장치의 날짜 및 시간 변경을 차단할 수 있는 새로운 기능이 추가되었습니다. 이 기능은 **장치 구성 프로필** > **장치 제한 사항(Android)** > **일반**에서 확인할 수 있습니다.

#### <a name="surface-hub-resource-account-supported----1566442----"></a>Surface Hub 리소스 계정 지원됨 <!-- 1566442  -->

관리자가 Surface Hub와 연결된 리소스 계정을 정의하고 업데이트할 수 있도록 새 장치 작업이 추가되었습니다.

리소스 계정은 Surface Hub에서 Skype/Exchange로 인증하는 데 사용되므로 모임에 참여할 수 있습니다. Surface Hub는 모임에서 회의실로 표시되도록 고유한 리소스 계정을 만들 수 있습니다. 예를 들어, 리소스 계정은 *회의실 B41/6233*으로 표시될 수 있습니다. Surface Hub의 리소스 계정(장치 계정이라고 함)은 일반적으로 회의실 위치에 대해 구성되고 다른 리소스 계정 매개 변수를 변경해야 할 경우 구성되어야 합니다.

관리자가 장치에서 리소스 계정을 업데이트하려는 경우 장치와 연결된 현재 Active Directory/Azure Active Directory 자격 증명을 제공해야 합니다. 장치에 대한 암호 순환이 켜져 있는 경우 관리자는 Azure Active Directory로 이동하여 암호를 찾아야 합니다.

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

     장치/리소스 계정의 메일 주소입니다.

   - **Exchange Server**

     자동 검색이 실패할 경우에만 필요합니다.

   - **일정 동기화**

     일정 동기화 및 기타 Exchange Server 서비스를 사용할지 여부를 지정합니다. 예: 모임 동기화.

#### <a name="install-office-apps-on-macos-devices----1494311---"></a>macOS 장치에 Office 앱 설치 <!-- 1494311 -->
이제 macOS 장치에 Office 앱을 설치할 수 있습니다. 새 앱 유형을 사용하여 Word, Excel, PowerPoint, Outlook 및 OneNote를 설치할 수 있습니다. 또한 이러한 앱은 MAU(Microsoft 자동 업데이트)와 함께 제공되므로 앱을 안전하게 최신 상태로 유지할 수 있습니다.

### <a name="app-management"></a>앱 관리

#### <a name="delete-an-ios--volume-purchasing-program-token----820879---"></a>iOS Volume Purchasing Program 토큰 삭제 <!-- 820879 -->
콘솔을 사용하여 iOS VPP(Volume-Purchase Program) 토큰을 삭제할 수 있습니다. VPP 토큰의 중복 인스턴스가 있는 경우 이 기능이 필요할 수 있습니다.

### <a name="intune-apps"></a>Intune 앱


### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="a-new-entity-collection-named-current-user-is-limited-to-currently-active-user-data----1667026---"></a>현재 사용자라는 새 엔터티 컬렉션은 현재 활성 사용자 데이터로 제한됨<!-- 1667026 -->

**사용자** 엔터티 컬렉션에는 엔터프라이즈에서 할당된 라이선스를 가진 모든 Azure AD(Azure Active Directory) 사용자가 포함됩니다. 예를 들어, 사용자가 Intune에 추가된 다음 지난달 중에 제거되었을 수 있습니다. 보고 시점에는 이 사용자가 없지만 데이터에는 사용자와 상태가 있습니다. 데이터에 있는 사용자의 현재 상태 기록에 대한 기간을 보여 주는 보고서를 만들 수 있습니다.

이와 달리 새 **현재 사용자** 엔터티 컬렉션에는 제거되지 않은 사용자만 포함됩니다. **현재 사용자** 엔터티 컬렉션에는 현재 활성 사용자만 포함됩니다. **현재 사용자** 엔터티 컬렉션에 대한 자세한 내용은 [현재 사용자 엔터티에 대한 참조](reports-ref-current-user.md)를 참조하세요.


### <a name="updated-graph-apis----1736360---"></a>Graph API 업데이트됨 <!-- 1736360 -->

이 릴리스에서는 베타 상태인 몇 가지 Intune용 Graph API가 업데이트되었습니다. 자세한 내용은 월별 [Graph API 변경 로그](https://developer.microsoft.com/graph/docs/concepts/changelog)를 참조하세요.

## <a name="week-of-december-4-2017"></a>2017년 12월 4일 주

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="intune-supports-windows-information-protection-wip-denied-apps----1479103---"></a>Intune은 WIP(Windows Information Protection)가 거부된 앱을 지원함 <!-- 1479103 -->
Intune에서 거부된 앱을 지정할 수 있습니다. 앱이 거부되면 회사 정보에 액세스할 수 없도록 차단되므로 허용된 앱 목록의 반대가 됩니다. 자세한 내용은 [Windows Information Protection에 대한 권장 거부 목록](https://docs.microsoft.com/windows/client-management/mdm/applocker-csp?f=255&MSPPError=-2147217396#recommended-deny-list-for-windows-information-protection)을 참조하세요.



## <a name="notices"></a>알림

### <a name="plan-for-change-change-password-at-next-auth-added-to-intune---1873216---"></a>변경 계획: Intune에 추가되는 다음 인증에서 암호 변경<!-- 1873216 -->
9월 서비스 릴리스에서 Intune은 macOS 버전 10.13 이상을 실행하는 장치에 대해 새로 릴리스된 Apple의 **다음 인증에서 암호 변경** 설정을 통합할 계획입니다. 이 설정을 사용하기 전에 MDM 공급자는 장치 암호가 호환되도록 변경되었는지 확인할 수 없습니다. Intune의 구성 및 준수 정책은 다음에 장치 암호가 변경될 때 해당 암호가 준수 상태로 표시되는지만 검증합니다. 이 새로운 Apple 기능이 추가되면 암호가 호환되는 경우에도 macOS 사용자는 암호를 업데이트하라는 요청을 받게 됩니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
Intune 또는 하이브리드 MDM을 사용하는 macOS 장치 정책이 있는 환경에 영향을 줍니다. 이제 Apple에서 **새 인증에서 암호 변경** 설정을 사용하므로 Intune은 암호 정책을 적용할 때 사용자가 암호를 업데이트하도록 강제할 수 있습니다. 장치가 준수 상태로 표시될 때까지 회사 리소스를 차단하면 최종 사용자가 암호를 재설정할 때까지 이메일 또는 SharePoint 사이트와 같은 회사 리소스에 액세스하지 못하도록 차단될 수 있습니다. 앞으로 구성 및 규정 준수 암호 정책을 모두 업데이트하면 대상 사용자가 자신의 암호를 강제로 업데이트해야 합니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
기술 지원팀에 알려주세요. 이 macOS 장치 정책을 적용하지 않으려면 기존 macOS 정책을 할당 해제하거나 삭제하는 것이 좋습니다. 고객 조사에 따르면 대부분의 고객이 이 변경으로 인해 영향을 받지 않습니다. 대부분의 최종 사용자는 암호를 등록하도록 요청을 받은 후에 암호를 업데이트하거나, 암호를 재설정하여 준수 상태를 유지합니다.


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september----2454656---"></a>변경 계획: Intune 9월에 iOS 10 이상 지원하기 위해 이동 예정 <!-- 2454656 -->
9월에 Apple은 iOS 12를 릴리스할 예정입니다. 릴리스 직후 Intune 등록, 회사 포털 및 관리 브라우저를 이동하여 iOS 10 이상을 지원할 것입니다.  

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?  
Office 365 모바일 앱은 iOS 10 이상에서 지원되므로 OS 또는 장치를 이미 업그레이드했을 수도 있습니다. 업그레이드했으면 이 이동은 영향을 주지 않습니다.  

그러나 아래에 나열된 모든 장치가 있거나 아래에 나열된 모든 장치를 등록하려는 경우 iOS 9 이하만 지원한다는 것을 잊지 마세요.  Intune 회사 포털에 액세스를 계속하려면 이러한 장치를 9월까지 iOS 10 이상을 지원하는 장치로 업그레이드해야 합니다.  

* iPhone 4S  
* iPod Touch  
* iPad 2  
* iPad(3세대)  
* iPad 미니(1세대)  

7월부터 iOS 9 및 회사 포털 모두를 사용하는 MDM 등록 장치에는 해당 OS 또는 장치를 업그레이드하라는 메시지가 표시됩니다. 앱 보호 정책을 사용하는 경우 "최소 iOS 운영 체제 필수(경고만)" 액세스 설정을 설정할 수 있습니다.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?   
조직에서 영향을 받는 장치 또는 사용자를 확인합니다. Azure Portal의 Intune에서 장치 > 모든 장치로 이동하고 OS로 필터링합니다.  OS 버전과 같은 세부 정보를 노출하려면 열을 클릭합니다. 사용자는 9월 전에 지원되는 OS 버전으로 자신의 장치를 업그레이드하도록 요청합니다.  

### <a name="plan-for-change-intune-moving-to-tls-12"></a>변경 계획: Intune이 TLS 1.2로 이동
2018년 10월 31일부터 Intune은 TLS(전송 계층 보안) 프로토콜 버전 1.2를 지원하여 동급 최강의 암호화 기능을 제공하고, 서비스가 기본적으로 더 안전하며, Microsoft Office 365와 같은 다른 Microsoft 서비스와 일치하도록 보장할 예정입니다. Office는 MC128929에서 이러한 변경 내용을 전달했습니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
2018년 10월 31일부터 Intune은 더 이상 TLS 프로토콜 버전 1.0 또는 1.1을 지원하지 않습니다. 모든 클라이언트-서버 및 브라우저-서버 조합은 Intune에 문제없이 연결하기 위해 TLS 버전 1.2를 사용해야 합니다. 이 변경 내용은 Intune에서 더 이상 지원되지 않지만, Intune을 통해 정책을 수신 중이며 TLS 버전 1.2를 사용할 수 없는 최종 사용자 장치에 영향을 줍니다. 여기에는 Android 4.3 이하 버전을 실행하는 장치가 포함됩니다. 영향을 받는 장치 및 브라우저의 목록은 아래 추가 정보를 참조하세요.

2018년 10월 31일 이후 이전 TLS 버전의 사용과 관련된 문제가 발생하면 문제 해결 과정에서 TLS 1.2 또는 TLS 1.2를 지원하는 장치로 업데이트해야 합니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
사용자 환경에서 TLS 1.0 및 1.1 종속성을 사전에 제거하고, 가능한 경우 운영 체제 수준에서 TLS 1.0 및 1.1을 사용하지 않는 것이 좋습니다. 지금 TLS 1.2로의 마이그레이션 계획을 시작하세요. 현재 Intune에서 지원되지 않지만 여전히 정책을 수신 중이며 TLS 버전 1.2를 사용하여 통신할 수 없는 장치 목록은 아래 지원 블로그 게시물을 참조하세요. 해당 최종 사용자에게 회사 리소스에 대한 액세스 권한을 잃을 수 있음을 알릴 필요가 있습니다.

**추가 정보**: [Intune이 암호화를 위해 TLS 1.2로 이동](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)

### <a name="plan-for-change-new-windows-10-setting-for-kiosk-configuration-in-intune----1560072---"></a>변경 계획: Intune에서 키오스크 구성에 대한 새로운 Windows 10 설정 <!-- 1560072 -->
Intune Azure Portal에서 Windows 10 1709 이상(RS3 이상) 데스크톱을 구성하는 방법 및 위치를 변경할 예정입니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요? 
레코드에서는 Windows 10 > 장치 제한 사항 > 키오스크(미리 보기) 설정을 사용한다고 나타냅니다. 5월에 UI에서 Windows 10 > 장치 제한 사항 > 키오스크(사용되지 않음)로 이름이 바뀌어서 더 이상 사용하지 않는 것이 좋음을 의미합니다. 하지만 Intune에 대한 7월 업데이트까지는 계속 작동합니다. 이후에는 백 엔드에서 사용되지 않고 더 이상 작동하지 않습니다. 대신 5월 Windows 10 > 키오스크에서는 Windows 10 RS4 이상에서 키오스크를 구성하는 설정을 비롯하여 새 장치 구성 프로필을 릴리스할 예정입니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?  
Intune이 5월 말에 5월 서비스 업데이트를 릴리스하는 경우 Windows 10 RS3에서 Windows 10 RS4로 키오스크 구성을 마이그레이션할 수 있는지 테스트하고 확인하는 지침을 공유합니다. 키오스크에 대한 새 장치 구성 프로필을 사용하여 장치를 키오스크로 구성하려면 이러한 지침을 사용합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이 변경 사항은 Intune 독립 실행형 고객 및 하이브리드(Configuration Manager를 사용하는 Intune) 고객 모두에게 영향을 미칩니다. 이 통합은 클라우드 관리를 단순화하는 데 도움이 됩니다. 이제, 그룹, 정책, 앱 및 모바일 장치 관리를 제어할 때 Azure에서 Intune 블레이드 하나만 이용하면 됩니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대해 준비하려면 어떻게 해야 하나요?
Intune 앱 보호 서비스 블레이드 대신 Intune을 즐겨찾기로 태그를 지정하고 Intune 내 모바일 앱 블레이드의 앱 보호 정책 워크플로에 익숙해지도록 합니다. 짧은 시간 동안 리디렉션된 다음, 앱 보호 블레이드가 제거됩니다. Intune에서 모든 앱 보호 정책은 이미 설정되어 있으며, 다음 설명서를 수행하면 조건부 액세스 정책을 수정할 수 있습니다. [https://aka.ms/azuread_ca](https://aka.ms/azuread_ca)

**추가 정보**: [https://aka.ms/intuneapppolicy](https://aka.ms/intuneapppolicy)

### <a name="plan-for-change-change-in-support-for-the-microsoft-intune-app-sdk-for-cordova-plugin"></a>변경 계획: Microsoft Intune App SDK for Cordova 플러그인 지원의 변경
Intune은 2018년 5월 1일 [Microsoft Intune App SDK Cordova 플러그인](app-sdk-cordova.md)에 대한 지원을 종료합니다. Intune에서 관리 및 가용성을 위해 Cordova 기반 앱을 준비하려면 Intune 앱 래핑 도구를 대신 사용하는 것이 좋습니다. 이 변경 내용이 적용되면 Cordova 플러그인용 Microsoft Intune APP SDK가 더 이상 유지 관리되지 않거나 업데이트를 수신하지 않습니다. 앱 개발자는 이 플러그인을 사용할 수 없습니다. Intune은 Cordova로 빌드된 앱을 계속 지원할 계획입니다. 그러나 Cordova 플러그인용 Microsoft Intune APP SDK를 사용하여 빌드된 앱은 Intune에서 기능이 저하될 수 있습니다. Intune 앱 래핑 도구로 래핑하면 평소처럼 최종 사용자에게 앱을 배포할 수 있습니다. Google Play 스토어에 릴리스된 Cordova 기반 Android 앱의 경우:
- 최종 사용자는 처음 실행할 때 Intune 정책을 수신하기 위한 자격 증명을 묻는 메시지가 표시됩니다.
- 앱은 Intune 사용자를 대상으로 앱 스토어에 릴리스되어야 합니다(예: "Contoso App for Intune").

앱 래핑 도구에 대한 자세한 내용은 [iOS용 앱 래핑 도구](app-wrapper-prepare-ios.md) 및 [Android용 앱 래핑 도구](app-wrapper-prepare-android.md)를 참조하세요. 문제 또는 질문이 있는 경우 [msintuneappsdk@microsoft.com](mailto:msintuneappsdk@microsoft.com)에 문의하세요.

### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management----1227338---"></a>변경 계획: MDM 관리를 위해 Azure에서 Intune 사용 <!-- 1227338 -->
1년 전, [Azure에서 Intune의 공개 미리 보기](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)를 발표한 후, 6개월 전 Intune에 대한 [새 관리자 환경의 일반 공급](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)을 발표했습니다. 2018년 8월 31일부터는 Intune 독립 실행형을 사용하는 고객에 대해 클래식 Silverlight 콘솔에서 MDM(모바일 장치 관리) 기능을 해제합니다. 대신, MDM 요구 사항에 따라 [Azure에서 Intune](https://aka.ms/Intune_on_Azure)을 사용할 수 있습니다. MDM용 클래식 콘솔을 아직 사용 중이라면 사용을 중지하고 Azure에서 Intune을 숙지하세요. 이러한 변경으로 최종 사용자에게 어떤 영향이 있지는 않을 것입니다. 클래식 PC 관리는 Silverlight에서 그대로 유지됩니다. 이 변경 사항과 변경 사항이 미치는 영향은 [여기](https://aka.ms/Intune_on_Azure_mdm)에서 자세히 알아볼 수 있습니다.

### <a name="direct-access-to-apple-enrollment-scenarios---951869--"></a>Apple 등록 시나리오에 대한 직접 액세스 <!--951869-->
2017년 1월 이후에 만든 Intune 계정은 Azure 포털에서 장치 등록 워크로드를 사용하여 Apple 등록 시나리오에 직접 액세스할 수 있습니다. 이전에는 Intune 클래식 포털의 링크를 통해서만 Apple 등록 미리 보기에 액세스할 수 있었습니다. 2017년 1월 이전에 만든 Intune 계정은 일회성 마이그레이션을 수행해야 Azure에서 이러한 기능을 사용할 수 있습니다. 마이그레이션 일정은 아직 공지되지 않았지만 가능한 한 빠른 시일 내에 세부 정보가 제공될 예정입니다. 기존 계정에서 Azure Portal에 액세스할 수 없는 경우 평가판 계정을 만들어 새로운 환경을 테스트해 보는 것이 좋습니다.

## <a name="whats-coming"></a>향후 예정 사항

### <a name="local-device-security-option-settings----1251887---"></a>로컬 장치 보안 옵션 설정 <!-- 1251887 -->
새 로컬 장치 보안 옵션 설정을 사용하여 Windows 10 장치에서 보안 설정을 사용하도록 설정할 수 있습니다. Windows 10 장치 구성 정책을 만들 때 Endpoint Protection 범주에서 이러한 설정을 찾아보세요.

### <a name="new-user-experience-update-for-the-company-portal-website---2000968--"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트<!--2000968-->

UI 업데이트, 간소화된 워크플로 및 향상된 접근성 기능을 통해 8월부터 새로운 회사 포털 웹 사이트 환경을 도입할 예정입니다. 여기에는 앱 공유 및 전반적인 성능 향상과 같은 고객 기반 고급 기능이 포함되어 보다 편리한 사용자 환경을 제공합니다.
고객의 의견에 따라 몇 가지 새로운 기능을 추가했습니다. 그러면 다음과 같은 기존 기능과 유용성을 크게 향상시킵니다.

* 웹 사이트 전체 UI 개선 사항
* 앱에 대한 직접 링크를 공유하는 기능
* 대규모 앱 카탈로그의 성능 향상

이 변경 내용을 준비하기 위해 조치를 취할 필요가 없습니다. 업데이트된 회사 포털 웹 사이트가 제공될 때 알려드리겠습니다. 그러나 결국 업데이트된 스크린샷을 포함한 최종 사용자 문서를 업데이트해야 할 수 있습니다. 웹 사이트에서 iOS 앱의 **앱** 섹션을 제공하므로 iOS에서 회사 포털 앱에 대한 설명서를 업데이트해야 할 수도 있습니다. [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지에서 이에 대한 샘플 이미지를 확인할 수 있습니다.

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple의 Application Transport Security 업데이트 요구 <!--748318-->
Apple에서는 ATS(Application Transport Security)에 대한 특정 요구 사항을 적용할 것이라고 발표했습니다. ATS는 HTTPS를 통한 모든 앱 통신에서 보다 엄격한 보안을 적용하는 데 사용됩니다. 이 변경 사항은 iOS 회사 포털 앱을 사용하는 Intune 고객에게 영향을 줍니다. [Intune 지원 블로그](https://aka.ms/compportalats)에 세부 정보가 포함됩니다.



## <a name="see-also"></a>참고 항목
* [Microsoft Intune 블로그](http://go.microsoft.com/fwlink/?LinkID=273882)
* [클라우드 플랫폼 로드맵](https://www.microsoft.com/cloud-platform/roadmap)
* [What's new in the Company Portal UI](whats-new-app-ui.md)(회사 포털 UI의 새로운 기능)
* [지난 달의 새로운 기능](whats-new-archive.md)
