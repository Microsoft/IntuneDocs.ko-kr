---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titlesuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/04/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
/ms.custom: intune-azure
ms.openlocfilehash: f1f6cac720e753e78bbabe091ce1c68cc58b7917
ms.sourcegitcommit: 21b08737c3366b81b0f3b981b29008563f63f036
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34758153"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. [예정된 변경](#whats-coming), 서비스 관련 [중요 공지](#notices) 및 [이전 릴리스](whats-new-archive.md) 관련 정보에 대해서도 알아볼 수 있습니다. 일부 기능은 몇 주에 걸쳐 출시될 수 있고 첫 번째 주에는 모든 고객에게 제공되지 않습니다.

> [!Note]
> 하이브리드 MDM(모바일 장치 관리)의 새로운 기능에 대한 자세한 내용은 [하이브리드의 새로운 기능 페이지](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management)를 참조하세요.


<!-- Common categories:  
### App management
### Device enrollment
### Device management
### Device configuration
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->   

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
Intune에서는 이제 사용자 인증 없이 Windows Autopilot 등록을 지원합니다. 여기에는 Windows Autopilot 배포 프로필인 "Autopilot 배포 모드"가 "자체 배포"로 설정된 새 옵션이 있습니다.  이러한 유형의 등록을 인증하려면 장치에서 Windows 10 빌드 1803 이상을 실행하고 TPM 2.0을 갖추고 있어야 합니다. 사용자 인증이 필요하지 않으므로 물리적으로 제어할 수 있는 장치에만 이 옵션을 할당해야 합니다.

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

#### <a name="protect-on-premise-exchange-data-using-intune-app-and-ca----1056954---"></a>Intune APP 및 CA를 사용하여 온-프레미스 Exchange 데이터 보호 <!-- 1056954 -->
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

#### <a name="custom-book-categories-for-volume-purchase-progream-vpp-ebooks----1488911---"></a>VPP(대량 구매 프로그램) 전자책에 대한 사용자 지정 책 범주 <!-- 1488911 -->
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

30,000개 이상의 장치가 있는 Microsoft Edge 및 Chrome 사용자는 해당 장치를 여러 파일로 성공적으로 내보낼 수 있습니다. 각 파일에는 최대 30,000개의 장치가 있습니다.

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

이제 온-프레미스 NDES Connector를 사용하여 인증서를 장치에 전달하는 고객이 단일 테넌트에 여러 커넥터를 구성할 수 있습니다.

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


## <a name="week-of-november-27-2017"></a>2017년 11월 27일 주

### <a name="device-enrollment"></a>장치 등록

#### <a name="troubleshoot-enrollment-issues-----746324---"></a>등록 문제 해결<!-- 746324 -->

**문제 해결** 작업 영역에 이제 사용자 등록 문제가 표시됩니다. 문제 및 제안된 수정 단계에 대한 세부 정보를 통해 관리자 및 도움말 지원 센터 운영자가 문제를 해결할 수 있습니다. 특정 등록 문제는 캡처되지 않고 일부 오류에는 수정 제안이 없을 수 있습니다.

#### <a name="group-assigned-enrollment-restrictions----747598---"></a>그룹 할당 등록 제한 <!-- 747598 -->

Intune 관리자가 이제 [사용자 그룹에 대한 사용자 지정 장치 유형 및 장치 수 등록 제한을 만들](enrollment-restrictions-set.md) 수 있습니다.

Intune Azure Portal에서 각 제한 유형의 인스턴스를 25개까지 만들 수 있으며 나중에 사용자 그룹에 할당할 수 있습니다. 그룹 할당 제한은 기본 제한을 재정의합니다.

제한 유형의 모든 인스턴스는 엄격하게 정렬된 목록으로 유지됩니다. 이 순서는 충돌 해결을 위한 우선 순위 값을 정의합니다. 둘 이상의 제한 인스턴스의 영향을 받는 사용자는 우선 순위가 가장 높은 값의 인스턴스에 의해서만 제한됩니다. 지정된 인스턴스의 우선 순위를 목록에서 다른 위치로 끌어서 변경할 수 있습니다.

이 기능은 Android for Work 설정이 Android for Work 등록 메뉴에서 등록 제한 메뉴로 마이그레이션되면서 릴리스될 예정입니다. 이 마이그레이션은 며칠이 걸릴 수 있으므로 계정이 11월 릴리스의 다른 일부로 업그레이드된 후에 등록 제한에서 그룹 할당을 사용할 수 있습니다.

#### <a name="support-for-multiple-network-device-enrollment-service-ndes-connectors----1528104---"></a>여러 NDES(네트워크 장치 등록 서비스) 커넥터에 대한 지원 <!-- 1528104 -->

NDES를 사용하면 도메인 자격 증명 없이 실행되는 모바일 장치에서 SCEP(단순 인증서 등록 프로토콜)를 기반으로 인증서를 가져올 수 있습니다.
이 업데이트를 통해 여러 NDES 커넥터가 지원됩니다.

#### <a name="manage-android-for-work-devices-independently-from-android-devices----1490731-eeready--"></a>Android 장치와는 독립적으로 Android for Work 장치 관리 <!-- 1490731 EEready-->

Intune은 Android 플랫폼과는 독립적으로 Android for Work 장치의 등록 관리를 지원합니다. 이러한 설정은 **장치 등록** > **등록 제한** > **장치 유형 제한**에서 관리됩니다. (이전에는 **장치 등록** > **Android for Work 등록** > **Android for Work 등록 설정**에 있었음)

기본적으로 Android for Work 장치 설정은 Android 장치에 대한 설정과 동일합니다. 그러나 Android for Work 설정을 변경하면 달라집니다.

개인적인 Android for Work 등록을 차단하는 경우 회사 Android 장치만 Android for Work로 등록할 수 있습니다.

새 설정으로 작업할 때는 다음 사항을 고려합니다.

##### <a name="if-you-have-never-previously-onboarded-android-for-work-enrollment"></a>이전에 등록된 Android for Work 등록이 없는 경우

새 Android for Work 플랫폼이 기본 장치 유형 제한에서 차단됩니다. 기능을 등록한 후에 Android for Work로 등록하도록 장치를 허용할 수 있습니다. 이렇게 하려면 기본값을 변경하거나 기본 장치 유형 제한을 대체할 새 장치 유형 제한을 만듭니다.

##### <a name="if-you-have-onboarded-android-for-work-enrollment"></a>등록된 Android for Work 등록이 있는 경우

이전에 등록한 경우 상황은 사용자가 선택한 설정에 따라 다릅니다.

| Setting | 기본 장치 유형 제한에서의 Android for Work 상태 | 참고 |
| --- | --- | --- |
| **모든 장치를 Android로 관리** | 차단됨 | 모든 Android 장치는 Android for Work 없이 등록해야 합니다. |
| **지원되는 장치를 Android for Work로 관리** | 허용됨 | Android for Work를 지원하는 모든 Android 장치는 Android for Work로 등록해야 합니다. |
| **이러한 그룹의 사용자만을 위해 지원되는 장치를 Android for Work로 관리** | 차단됨 | 기본값을 재정의하기 위해 별도 장치 유형 제한 정책이 만들어졌습니다. 이 정책은 Android for Work 등록을 허용하도록 이전에 선택한 그룹을 정의합니다. 선택된 그룹 내 사용자는 Android for Work 장치를 등록할 수 있도록 계속 허용됩니다. 다른 모든 사용자는 Android for Work 등록에 제한을 받습니다. |

모든 경우에 사용자의 의도한 규정이 유지됩니다. 사용자 환경에서 Android for Work의 전역 또는 그룹별 허용 한도를 유지하기 위한 별도의 작업은 필요하지 않습니다.

### <a name="app-management"></a>앱 관리

#### <a name="app-install-report-updated-to-include-install-pending-status----1249446---"></a>설치 보류 중 상태를 포함하도록 앱 설치 보고서 업데이트 <!-- 1249446 -->  

**모바일 앱**의 **앱** 목록을 통해 각 앱에 액세스할 수 있는 **앱 설치 상태** 보고서에 이제 사용자와 장치에 대한 **설치 보류 중** 수가 포함됩니다.

#### <a name="ios-11-app-inventory-api-for-mobile-threat-detection----1391759---"></a>모바일 위협 요소 탐지를 위한 iOS 11 앱 인벤토리 API<!-- 1391759 -->

Intune은 개인 및 회사 소유 장치 모두에서 앱 인벤토리 정보를 수집하며 Lookout for Work와 같은 페치할 MTD(모바일 위협 검색) 공급자에서 사용할 수 있도록 합니다. iOS 11+ 장치의 사용자로부터 앱 인벤토리를 수집할 수 있습니다.

**앱 인벤토리**  
회사 소유의 iOS 11+ 및 개인적으로 소유한 장치 모두의 인벤토리가 사용자의 MTD 서비스 공급자에게 전송됩니다. 앱 인벤토리의 데이터에는 다음이 포함됩니다.

 - 앱 ID
 - 앱 버전
 - 앱 짧은 버전
 - 앱 이름
 - 앱 번들 크기
 - 앱 동적 크기
 - 앱의 유효성 검사 여부
 - 앱의 관리 여부


### <a name="device-management"></a>장치 관리

#### <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone----1463747-wnready---"></a>하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션 <!-- 1463747 wnready -->
새 프로세스와 도구를 사용하여 사용자와 해당 장치를 하이브리드 MDM에서 Azure Portal의 Intune으로 이동할 수 있으며, 다음과 같은 작업을 수행할 수 있습니다.
- Configuration Manager 콘솔에서 Azure Portal의 Intune으로 정책 및 프로필 복사
- Azure Portal의 Intune으로 사용자 하위 집합을 이동하고 나머지는 하이브리드 MDM에 유지
- 다시 등록할 필요 없이 Azure Portal의 Intune으로 장치 마이그레이션

자세한 내용은 [하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.

#### <a name="on-premises-exchange-connector-high-availability-support-----676614---"></a>온-프레미스 Exchange Connector 고가용성 지원 <!-- 676614 -->
이제 Exchange Connector가 지정된 CAS를 사용하여 Exchange에 연결한 후 다른 CAS를 검색할 수 있습니다. 기본 CAS를 사용할 수 없게 되면 커넥터는 기본 CAS를 사용할 수 있을 때까지 다른 CAS(사용 가능한 경우)로 장애 조치(failover)됩니다. 자세한 내용은 [온-프레미스 Exchange Connector 고가용성 지원](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)을 참조하세요.

#### <a name="remotely-restart-ios-device-supervised-only----1424595---"></a>iOS 장치를 원격으로 다시 시작(감독 모드만 해당) <!-- 1424595 -->

이제 장치 동작을 사용하여 다시 시작하도록 감독되는 iOS 10.3+ 장치를 트리거할 수 있습니다. 장치 다시 시작 동작 사용에 대한 자세한 내용은 [Intune으로 장치를 원격으로 다시 시작](device-restart.md)을 참조하세요.

> [!Note]
> 이 명령은 감독되는 장치 및 **장치 잠금** 액세스 권한에 필요합니다. 장치를 즉시 다시 시작합니다. 암호로 잠긴 iOS 장치는 다시 시작한 후 Wi-Fi 네트워크에 다시 가입되지 않습니다. 다시 시작한 후 서버와 통신하지 못할 수도 있습니다.

#### <a name="single-sign-on-support-for-ios----1333645---"></a>iOS을 위한 Single Sign-On 지원 <!-- 1333645 -->  

iOS 사용자에 대해 Single Sign-On을 사용할 수 있습니다. Single Sign On 페이로드에서 사용자 자격 증명을 검색하도록 코딩되는 iOS 앱은 이 페이로드 구성 업데이트로 작동합니다. 또한 UPN 및 Intune 장치 ID를 사용하여 사용자 이름 및 영역을 구성할 수 있습니다. 자세한 내용은 [iOS 장치 Single Sign-On용 Intune 구성](sso-ios.md)을 참조하세요.

#### <a name="add-find-my-iphone-for-personal-devices---1427287--"></a>개인 장치를 위한 “내 iPhone 찾기” 추가 <!--1427287-->
이제 iOS 장치가 활성화 잠금이 설정되어 있는지 여부를 확인할 수 있습니다. 이전에 이 기능은 클래식 포털의 Intune에서 찾을 수 있었습니다.


#### <a name="remotely-lock-managed-macos-device-with-intune----1437691---"></a>Intune을 사용하여 관리되는 macOS 장치 원격 잠금 <!-- 1437691 -->

손실된 macOS 장치를 잠그고 6자리 복구 PIN을 설정할 수 있습니다. 잠기면 **장치 개요** 블레이드에 다른 장치 작업이 전송될 때까지 PIN이 표시됩니다.

자세한 내용은 [Intune을 사용하여 관리되는 장치 원격 잠금](device-remote-lock.md)을 참조하세요.

#### <a name="new-scep-profile-details-supported----1559808---"></a>지원되는 새 SCEP 프로필 세부 정보 <!-- 1559808 -->

관리자는 Windows, iOS, macOS 및 Android 플랫폼에서 SCEP 프로필을 만들 때 추가 설정을 지정할 수 있습니다.  관리자는 IMEI, 일련 번호 또는 주체 이름 형식의 전자 메일을 포함한 일반 이름을 설정할 수 있습니다.

<!-- #### Update to what device details your company may see -1616825
The Company Portal app for Android can now use geofencing to protect access to company resources. It uses network details such as IP address, default gateway address, and Domain Name System (DNS) to determine whether to allow access to protected company resources. -->

#### <a name="retain-data-during-a-factory-reset----1588489---"></a>출하 시 설정으로 리셋하는 동안 데이터 유지 <!--1588489 -->
Windows 10 버전 1709 이상을 출하 시 설정으로 재설정하면 새로운 기능을 사용할 수 있습니다. 관리자는 출하 시 설정으로 리셋하는 동안 장치 등록 및 프로비전된 기타 데이터를 장치에 보존할지 여부를 지정할 수 있습니다.

다음 데이터는 출하 시 설정으로 리셋되는 동안 유지됩니다.
- 장치와 연결된 사용자 계정
- 컴퓨터 상태(도메인 가입, Azure Active Directory 가입)
- MDM 등록
- OEM이 설치한 앱(저장소 및 Win32 앱)
- 사용자 프로필
- 사용자 프로필 외부의 사용자 데이터
- 사용자 자동 로그온

다음 데이터는 보존되지 않습니다.
- 사용자 파일
- 사용자가 설치한 앱(저장소 및 Win32 앱)
- 기본 설정 이외의 장치 설정

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결
#### <a name="window-10-update-ring-assignments-are-displayed----1621837---"></a>Windows 10 업데이트 링 할당 표시 <!-- 1621837 -->
확인 중인 사용자를 위해 **문제 해결** 중인 경우 모든 Windows 10 업데이트 링 할당을 확인할 수 있습니다.  

#### <a name="windows-defender-advanced-threat-protection-reporting-frequency-settings-----1455974----"></a>Windows Defender Advanced Threat Protection 보고 주기 설정 <!-- 1455974  -->
WDATP(Windows Defender Advanced Threat Protection) 서비스를 사용하면 관리자가 관리되는 장치에 대한 보고 주기를 관리할 수 있습니다. 새 **원격 보고 빈도 가속화** 옵션을 사용하면 WDATP는 더 자주 데이터를 수집하고 위험을 평가합니다. 보고에 대한 기본값은 속도 및 성능을 최적화합니다. 보고 빈도를 늘리는 것은 위험 수준이 높은 장치에 유용할 수 있습니다. 이 설정은 **장치 구성**의 **Windows Defender ATP** 프로필에서 확인할 수 있습니다.

#### <a name="audit-updates----1412961---"></a>감사 업데이트 <!-- 1412961 -->  
Intune 감사는 Intune과 관련된 변경 작업에 대한 레코드를 제공합니다.  모든 만들기, 업데이트, 삭제 및 원격 작업 조작은 캡처되고 1년 동안 보존됩니다.  Azure Portal은 각 워크로드에서 최근 30일 동안의 감사 데이터에 대한 뷰를 제공하며 필터링할 수 있습니다.  해당 Graph API를 사용하면 마지막 연도에 저장된 감사 데이터를 검색할 수 있습니다.

감사는 **모니터** 그룹에서 찾을 수 있습니다. 각 워크로드에 **감사 로그** 메뉴 항목이 있습니다.




## <a name="week-of-november-20-2017"></a>2017년 11월 20일 주

### <a name="app-management"></a>앱 관리

#### <a name="google-play-protect-support-on-android----908720---"></a>Android에서 Google Play 보호 지원 <!-- 908720 -->

Android Oreo가 출시되면서 Google은 사용자와 조직이 보안 앱과 보안 Android 이미지를 실행할 수 있는 Google Play 보호라는 보안 기능 제품군을 소개합니다. 이제 Intune은 SafetyNet 원격 증명을 비롯하여 Google Play 보호 기능을 지원합니다. 관리자는 Google Play 보호를 구성하고 정상 상태를 유지하는 데 필요한 준수 정책 요구 사항을 설정할 수 있습니다.
**SafetyNet 장치 증명** 설정은 장치가 정상 상태이고 손상되지 않았음을 확인하기 위해 장치를 Google 서비스에 연결하도록 합니다. 또한 관리자는 Google Play 서비스에서 설치된 앱을 확인하도록 하기 위해 Android for Work에 대한 구성 프로필 설정을 설정할 수 있습니다. 장치가 Google Play 보호 요구 사항을 준수하지 않는 경우 조건부 액세스는 사용자가 회사 리소스에 액세스하는 것을 차단합니다.

- [Google Play 보호를 사용하도록 설정하기 위해 장치 준수 정책을 만드는 방법](https://docs.microsoft.com/intune/compliance-policy-create-google-play-protect)을 알아봅니다.

#### <a name="text-protocol-allowed-from-managed-apps----1414050----"></a>관리되는 앱에서 허용하는 텍스트 프로토콜 <!-- 1414050  -->

Intune 앱 SDK로 관리되는 앱에서 SMS 메시지를 보낼 수 있습니다.

## <a name="week-of-november-13-2017"></a>2017년 11월 13일 주

### <a name="intune-apps"></a>Intune 앱
#### <a name="company-portal-app-for-macos-is-available---1541700--"></a>macOS용 회사 포털 앱 사용 가능 <!--1541700-->
macOS용 Intune 회사 포털에는 사용자가 등록한 모든 장치에 필요한 모든 정보 및 준수 알림을 분명히 표시하도록 최적화된 업데이트된 환경이 있습니다. 또한 Intune 회사 포털이 장치에 배포된 후에 macOS용 Microsoft 자동 업데이트에서는 이에 대한 업데이트를 제공합니다. macOS 장치에서 Intune 회사 포털 웹 사이트에 로그인하여 새로운 macOS용 Intune 회사 포털을 다운로드할 수 있습니다.

#### <a name="microsoft-planner-is-now-part-of-the-mobile-app-management-mam-list-of-approved-apps-----1248473---"></a>Microsoft Planner는 이제 승인된 앱의 MAM(모바일 앱 관리) 목록에 포함됨 <!-- 1248473 -->
iOS 및 Android용 Microsoft Planner 앱은 이제 MAM(모바일 앱 관리)에 대한 승인된 앱에 포함됩니다. 모든 테넌트에 대해 Azure Portal의 Intune 앱 보호 블레이드를 통해 앱을 구성할 수 있습니다.
- [승인된 앱의 MAM 목록](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 자세히 알아보세요.

#### <a name="per-app-vpn-requirement-update-frequency-on-ios-devices------1547061---"></a>iOS 장치에 대한 앱당 VPN 요구 사항 업데이트 빈도 <!-- 1547061 -->  
관리자는 이제 iOS 장치의 앱에 대한 앱당 VPN 요구 사항을 제거할 수 있습니다. 일반적으로 15분 내에 수행되는 다음 Intune 체크 인 후에 장치에 영향을 줍니다.  

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결
#### <a name="support-for-system-center-operations-manager-management-pack-for-exchange-connector----885457---"></a>Exchange Connector용 System Center Operations Manager 관리 팩에 대한 지원 <!-- 885457 -->
Exchange Connector 로그를 구문 분석하는 데 도움이 되도록 이제 Exchange Connector용 System Center Operations Manager(SCOM) 관리 팩이 제공됩니다. 이렇게 하면 문제를 해결해야 할 때 서비스를 모니터링하는 여러 가지 방법이 있습니다.

## <a name="week-of-november-6-2017"></a>2017년 11월 6일 주

### <a name="device-enrollment"></a>장치 등록
#### <a name="co-management-for-windows-10-devices-----1243445---"></a>Windows 10 장치의 공동 관리<!-- 1243445 -->
공동 관리는 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다. 기본적으로 공동 관리는 Windows 10 장치를 Configuration Manager와 Microsoft Intune에서 동시에 관리할 수 있는 솔루션입니다. 뿐만 아니라 AD(Active Directory) 및 Azure AD(Azure Active Directory)에 조인되됩니다.  이 구성을 통해 한 번에 경로로 이동할 수 없는 경우 조직에 적합한 속도로 시간이 지남에 따라 현대화하는 경로를 제공합니다.  

#### <a name="restrict-windows-enrollment-by-os-version----245498---"></a>OS 버전별 Windows 등록 제한 <!-- 245498 -->
Intune 관리자는 장치 등록을 위한 Windows 10의 최소 및 최대 버전을 지정할 수 있습니다. 이러한 제한은 **플랫폼 구성** 블레이드에서 설정할 수 있습니다.

Intune은 Windows 8.1 PC 및 Phone 등록을 계속 지원할 예정입니다. 하지만, Windows 10 버전만 최소 및 최대 제한을 설정할 수 있습니다. 8.1 장치의 등록을 허용하려면 최소 한도를 비워 두십시오.

#### <a name="alerts-for-windows-autopilot-unassigned-devices-----1631236---"></a>Windows AutoPilot 할당되지 않은 장치에 대한 경고 <!-- 1631236 -->
Windows AutoPilot 할당되지 않은 장치에 대한 새 경고는 **Microsoft Intune** > **장치 등록** > **개요** 페이지에 제공됩니다. 이 경고에는 AutoPilot 배포 프로필이 할당되지 않는 AutoPilot 프로그램의 장치 수가 표시됩니다. 경고의 정보를 사용하여 프로필을 만들어서 할당되지 않은 장치에 할당하십시오. 경고를 클릭하면 Windows AutoPilot 장치의 전체 목록과 해당 장치에 대한 자세한 정보가 표시됩니다. 자세한 내용은 [Windows AutoPilot 배포 프로그램을 사용하여 Windows 장치 등록](https://docs.microsoft.com/intune/enrollment-autopilot)을 참조하세요.

### <a name="device-management"></a>장치 관리

#### <a name="refresh-button-for-devices-list-------1333581---"></a>장치 목록의 새로 고침 단추    <!-- 1333581 -->
장치 목록이 자동으로 새로 고쳐지지 않으므로 새로운 새로 고침 단추를 사용하여 목록에 표시되는 장치를 업데이트할 수 있습니다.

#### <a name="support-for-symantec-cloud-certification-authority-ca-----1333638---"></a>Symantec 클라우드 CA(인증 기관)에 대한 지원<!-- 1333638 -->    
이제 Intune은 지원 Symantec 클라우드 CA 클라우드를 지원합니다. 이 기능을 사용하면 Intune 인증서 커넥터가 Symantec 클라우드 CA에서 Intune 관리 장치에 PKCS 인증서를 발급할 수 있습니다. Microsoft CA(인증 기관)에서 이미 Intune 인증서 커넥터를 사용하는 경우 기존 Intune 인증서 커넥터 설정을 활용하여 Symantec CA 지원을 추가할 수 있습니다.

#### <a name="new-items-added-to-device-inventory-----1404455---"></a>장치 인벤토리에 추가된 새 항목   <!--1404455 -->
이제 다음과 같은 새 항목을 [등록된 장치에서 가져온 인벤토리](device-inventory.md)에 사용할 수 있습니다.

- Wi-Fi MAC 주소
- 총 저장소 공간
- 사용 가능한 총 공간
- MEID
- 구독자의 통신사


### <a name="app-management"></a>앱 관리
#### <a name="set-access-for-apps-by-minimum-android-security-patch-on-the-device---1278463---"></a>장치에 대한 최소 Android 보안 패치를 기준으로 앱에 대한 액세스 권한 설정<!-- 1278463 -->   
관리자는 관리되는 계정 아래에서 관리되는 응용 프로그램에 대한 액세스 권한을 얻기 위해 장치에 설치해야 하는 최소 Android 보안 패치를 정의할 수 있습니다.

> [!Note]  
> 이 기능은 Android 6.0 이상 장치에서 Google에 의해 릴리스된 보안 패치만을 제한합니다.

#### <a name="app-conditional-launch-support----1193313---"></a>앱 조건부 시작 지원<!-- 1193313 -->
이제 IT 관리자는 Azure 관리 포털을 통해 요구 사항을 설정하여 응용 프로그램을 시작하는 경우 MAM(모바일 앱 관리)를 통해 숫자 PIN이 아닌 암호를 적용할 수 있습니다. 항목이 구성되면 사용자는 MAM 지원 응용 프로그램에 대한 액세스 권한을 가져오기 전에 메시지가 표시될 때 암호를 설정하고 사용해야 합니다. 암호는 하나 이상의 특수 문자 또는 대/소문자 알파벳을 포함한 숫자 PIN으로 정의됩니다. Intune의 이번 릴리스에서는 **iOS에서만** 이 기능을 활성화합니다. Intune은 숫자 PIN과 유사한 방식으로 암호를 지원합니다. 즉, 최소 길이를 설정하며 반복 문자 및 시퀀스를 허용합니다. 이 기능을 사용하려면 응용 프로그램(즉, WXP, Outlook, Managed Browser, Yammer)에 참여하여 나중에 대상 응용 프로그램에 적용할 암호 설정을 준비하기 위해 코드와 Intune 앱 SDK를 통합해야 합니다.

#### <a name="app-version-number-for-line-of-business-in-device-install-status-report----1233999---"></a>장치 설치 상태 보고서에서 기간 업무의 앱 버전 번호<!-- 1233999 -->
이 릴리스에서는 장치 설치 상태 보고서에 iOS 및 Android용 기간 업무 앱의 앱 버전 번호가 표시됩니다. 이 정보를 사용하여 앱 문제를 해결하거나 오래된 앱 버전을 실행하는 장치를 찾을 수 있습니다.


### <a name="device-configuration"></a>장치 구성
#### <a name="admins-can-now-configure-the-firewall-settings-on-a-device-using-a-device-configuration-profile----951708---"></a>관리자는 장치 구성 프로필을 사용하여 장치에서 방화벽 설정을 구성할 수 있습니다.<!-- 951708 -->   
관리자는 장치에 방화벽을 설정하고, 도메인, 개인 및 공용 네트워크에 다양한 프로토콜을 구성할 수도 있습니다.  이러한 방화벽 설정은 "Endpoint Protection" 프로필에서 찾을 수 있습니다.

#### <a name="windows-defender-application-guard-helps-protect-devices-from-untrusted-websites-as-defined-by-your-organization----958257---"></a>Windows Defender Application Guard를 통해 조직에서 정의한 대로 신뢰할 수 없는 웹 사이트로부터 장치를 보호할 수 있습니다.<!-- 958257 -->   
관리자는 Windows Information Protection 워크플로 또는 장치 구성에서 새 "네트워크 경계" 프로필을 사용하여 사이트를 "신뢰할 수 있음" 또는 "협력"으로 정의할 수 있습니다. 64비트 Windows 10 장치의 신뢰할 수 있는 네트워크 경계에 나열되지 않은 사이트가 Microsoft Edge에 표시되는 경우 Hyper-V 가상 머신 내에서 브라우저를 대신 엽니다.

"Endpoint Protection" 프로필의 장치 구성 프로필에서 Application Guard를 찾을 수 있습니다. 여기에서부터 관리자는 가상화된 브라우저와 호스트 컴퓨터, 트러스트되지 않은 사이트와 신뢰할 수 있는 사이트 간에 상호 작용을 구성하고 가상화된 브라우저에서 생성된 데이터를 저장할 수 있습니다. 장치에서 Application Guard를 사용하려면 네트워크 경계를 먼저 구성해야 합니다. 장치에 네트워크 경계를 하나만 정의해야 합니다.  

#### <a name="windows-defender-application-control-on-windows-10-enterprise-provides-mode-to-trust-only-authorized-apps----1031096---"></a>Windows 10 Enterprise에서 Windows Defender 응용 프로그램 제어는 인증된 앱만 신뢰하는 모드를 제공합니다.<!-- 1031096 -->    
수천 개의 새로운 악성 파일이 매일 생성되기 때문에 바이러스 백신 서명 기반 감지를 사용하여 맬웨어에 대항하는 방법은 더 이상 새로운 공격에 대한 적절한 방어를 제공할 수 없습니다. Windows 10 Enterprise에서 Windows Defender 응용 프로그램 제어를 사용하면 장치 구성을 변경할 수 있습니다(변경 전: 앱을 바이러스 백신 또는 기타 보안 솔루션으로 차단하지 않으면 신뢰할 수 있는 모드, 변경 후: 운영 체제가 기업에서 권한을 부여한 앱만을 신뢰하는 모드). Windows Defender 응용 프로그램 제어에서 앱에 트러스트를 할당합니다.

Intune을 사용하면 "감사 전용" 모드 또는 적용 모드에서 응용 프로그램 제어 정책을 구성할 수 있습니다. 앱을 “감사 전용” 모드로 실행하면 차단되지 않습니다. "감사 전용" 모드는 로컬 클라이언트 로그에 있는 모든 이벤트를 기록합니다. Windows 구성 요소 및 Microsoft 스토어 앱만 실행할 수 있는지 아니면 Intelligent Security Graph에서 정의한 대로 평판이 좋은 추가 앱도 실행할 수 있는지 여부를 구성할 수 있습니다.

#### <a name="window-defender-exploit-guard-is-a-new-set-of-intrusion-prevention-capabilities-for-windows-10----1063615---"></a>Window Defender Exploit Guard는 Windows 10의 새로운 침입 방지 기능 집합입니다.<!-- 1063615 -->   
dow Defender Exploit Guard는 응용 프로그램의 악용 가능성을 줄이는 사용자 지정 규칙을 포함하고, 매크로 및 스크립트 위협을 방지하고, 평판이 좋지 않은 IP 주소에 대한 네트워크 연결을 자동으로 차단하고, 랜섬웨어 및 알 수 없는 위협으로부터 데이터를 보호할 수 있습니다. Windows Defender Exploit Guard는 다음과 같은 구성 요소로 구성됩니다.

- **ASR(Attack Surface Reduction)** 은 매크로, 스크립트 및 전자 메일 위협을 방지할 수 있도록 하는 규칙을 제공합니다.
- **제어된 폴더 액세스**는 보호된 폴더의 콘텐츠에 대한 액세스를 자동으로 차단합니다.
- **네트워크 필터**는 앱에서 평판이 낮은 IP/도메인으로의 아웃바운드 연결을 차단합니다.
- **악용 보호**는 악용으로부터 응용 프로그램을 보호하는 데 사용할 수 있는 메모리, 제어 흐름 및 정책 제한을 제공합니다.


#### <a name="manage-powershell-scripts-in-intune-for-windows-10-devices----790537---"></a>Windows 10 장치의 Intune에서 PowerShell 스크립트 관리 <!-- 790537 -->

Intune 관리 확장을 사용하면 Windows 10 장치에서 실행되도록 Intune에서 PowerShell 스크립트를 업로드할 수 있습니다. 이 확장은 Windows 10 MDM(모바일 장치 관리) 기능을 보완하며 사용자가 최신 관리로 더 손쉽게 이행할 수 있도록 합니다. 자세한 내용은 [Windows 10 장치의 Intune에서 PowerShell 스크립트 관리](intune-management-extension.md)를 참조하세요.

#### <a name="new-device-restriction-settings-for-windows-10---------1308850---"></a>Windows 10의 새 장치 제한 설정<!-- 1308850 -->
-    메시지(모바일 전용) - 테스트 또는 MMS 메시지 사용 안 함
-    암호 - FIPS 사용하기 위한 설정 및 인증에 Windows Hello 보조 장치 사용 
-    표시 - 레거시 앱에 GDI Scaling 켜기 또는 끄기 설정

#### <a name="windows-10-kiosk-mode-device-restrictions----1308872---"></a>Windows 10 키오스크 모드 장치 제한<!-- 1308872 -->   
Windows 10 장치 사용자를 키오스크 모드로 제한하여 미리 정의된 앱의 집합으로 사용자를 제한할 수 있습니다.  이렇게 하려면 Windows 10 장치 제한 프로필을 만들고 키오스크 설정을 설정합니다.

키오스크 모드는 **단일 앱**(사용자가 하나의 앱을 실행하도록 허용) 또는 **다중 앱**(앱 집합에 대한 액세스 권한 허용)이라는 두 가지 모드를 지원합니다.  사용자 계정 및 장치 이름을 정의합니다. 여기서는 지원되는 앱을 결정합니다.  사용자는 정의된 앱에만 로그인할 수 있습니다.  자세한 내용은 [AssignedAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/assignedaccess-csp)를 참조하세요. 

키오스크 모드에는 다음 항목이 필요합니다.

- Intune는 MDM 기관이어야 합니다.
- 앱은 이미 대상 장치에 설치되어 있어야 합니다.
- 장치는 [제대로 프로비전](https://docs.microsoft.com/windows/configuration/set-up-a-kiosk-for-windows-10-for-desktop-editions)되어야 합니다.

#### <a name="new-device-configuration-profile-for-creating-network-boundaries----1311967---"></a>네트워크 경계를 만들기 위한 새 장치 구성 프로필<!-- 1311967 -->   
**네트워크 경계**라는 새 장치 구성 프로필은 다른 장치 구성 프로필을 통해 찾을 수 있습니다. 이 프로필을 사용하여 협력 및 신뢰할 수 있도록 하려는 온라인 리소스를 정의합니다. Windows Defender Application Guard 및 Windows Information Protection과 같은 기능을 장치에서 사용하기 *전에* 장치의 네트워크 경계를 정의해야 합니다. 각 장치에 네트워크 경계를 하나만 정의해야 합니다.

엔터프라이즈 클라우드 리소스, IP 주소 범위 및 내부 프록시 서버를 신뢰할 수 있다고 정의할 수 있습니다. 네트워크 경계를 정의하면 Windows Defender Application Guard 및 Windows Information Protection과 같은 다른 기능에서 사용할 수 있습니다.

####  <a name="two-additional-settings-for-windows-defender-antivirus----1338409---"></a>Windows Defender Antivirus의 두 가지 추가 설정<!-- 1338409 -->  
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

#### <a name="citrix-vpn-added-for-windows-10-devices----1512457---"></a>Windows 10 장치에 추가된 Citrix VPN<!-- 1512457 -->  
Windows 10 장치에 Citrix VPN을 구성할 수 있습니다. Windows 10 이상에 VPN을 구성하는 경우 **기본 VPN** 블레이드의 *연결 형식 선택* 목록에서 Citrix VPN을 선택할 수 있습니다.

> [!Note]
> iOS 및 Android용 Citrix 구성이 있습니다.

#### <a name="wi-fi-connections-support-pre-shared-keys-on-ios----1550823---"></a>Wi-Fi 연결은 iOS에서 사전 공유 키를 지원합니다. <!-- 1550823 -->
고객이 iOS 장치의 WPA/WPA2 개인 연결에 PSK(미리 공유한 키)를 사용하도록 Wi-Fi 프로필을 구성할 수 있습니다. 이 프로필은 장치가 Intune에 등록될 때 사용자의 장치로 푸시됩니다.

프로필이 장치로 푸시되면 다음 단계는 프로필 구성에 따라 달라집니다.  자동으로 연결되도록 설정하면 다음에 네트워크가 필요할 때 자동으로 연결됩니다.  프로필이 수동 연결이면 사용자는 연결을 수동으로 활성화해야 합니다.  

### <a name="intune-apps"></a>Intune 앱

#### <a name="access-to-managed-app-logs-for-ios----1469920---"></a>iOS의 관리되는 앱 로그에 액세스 <!-- 1469920 -->
관리되는 브라우저를 설치한 최종 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있고 관리된 iOS 앱 문제를 해결하도록 로그를 보낼 수 있습니다.

iOS 장치의 Managed Browser에서 문제 해결 모드를 사용하도록 설정하는 방법을 알아보려면 [iOS의 Managed Browser를 사용하여 관리되는 앱 로그에 액세스하는 방법](app-configuration-managed-browser.md#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)을 참조하세요.

#### <a name="improvements-to-device-setup-workflow-in-the-company-portal-for-ios-in-version-290----1417174---"></a>버전 2.9.0에 대한 iOS 회사 포털의 향상된 장치 설정 워크플로 기능<!-- 1417174 -->

iOS용 회사 포털 앱에서 장치 설정 워크플로가 개선되었습니다. 언어는 더욱 친숙하게 변경되었으며, 최대한 화면을 결합했습니다. 전체 설정 텍스트에서 회사 이름을 사용하여 언어가 회사에 더욱 구체적으로 변경되었습니다. 이 업데이트된 워크플로는  [앱 UI의 새로운 기능 페이지](whats-new-app-ui.md)에서 확인할 수 있습니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="user-entity-contains-latest-user-data-in-data-warehouse-data-model----1544273---"></a>데이터 웨어하우스 데이터 모델의 마지막 사용자 데이터를 포함하는 사용자 엔터티<!-- 1544273 -->
Intune 데이터 웨어하우스 데이터 모델의 첫 번째 버전에는 최신 과거 Intune 데이터만 포함되어 있습니다. 보고서 결정권자는 사용자의 현재 상태를 캡처할 수 없습니다. 이 업데이트에서 **사용자 엔터티**는 최신 사용자 데이터로 채워집니다.


## <a name="notices"></a>알림

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

UI 업데이트, 간소화된 워크플로 및 내게 필요한 옵션 기능 향상을 사용하여 4월에 새로운 회사 포털 웹 사이트 환경을 도입할 예정입니다. 여기에는 앱 공유 및 전반적인 성능 향상과 같은 고객 기반 고급 기능이 포함되어 보다 편리한 사용자 환경을 제공합니다.
고객의 의견에 따라 몇 가지 새로운 기능을 추가했습니다. 그러면 다음과 같은 기존 기능과 유용성을 크게 향상시킵니다.

-   웹 사이트 전체 UI 개선 사항
-   앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 향상

이 변경 내용을 준비하기 위해 조치를 취할 필요가 없습니다. 업데이트된 회사 포털 웹 사이트가 제공될 때 알려드리겠습니다. 그러나 결국 업데이트된 스크린샷을 포함한 최종 사용자 문서를 업데이트해야 할 수 있습니다. 웹 사이트에서 iOS 앱의 **앱** 섹션을 제공하므로 iOS에서 회사 포털 앱에 대한 설명서를 업데이트해야 할 수도 있습니다. [앱 UI의 새로운 기능](whats-new-app-ui.md) 페이지에서 이에 대한 샘플 이미지를 확인할 수 있습니다.

### <a name="apple-to-require-updates-for-application-transport-security---748318--"></a>Apple의 Application Transport Security 업데이트 요구 <!--748318-->
Apple에서는 ATS(Application Transport Security)에 대한 특정 요구 사항을 적용할 것이라고 발표했습니다. ATS는 HTTPS를 통한 모든 앱 통신에서 보다 엄격한 보안을 적용하는 데 사용됩니다. 이 변경 사항은 iOS 회사 포털 앱을 사용하는 Intune 고객에게 영향을 줍니다. [Intune 지원 블로그](https://aka.ms/compportalats)에 세부 정보가 포함됩니다.



## <a name="see-also"></a>참고 항목
* [Microsoft Intune 블로그](http://go.microsoft.com/fwlink/?LinkID=273882)
* [클라우드 플랫폼 로드맵](https://www.microsoft.com/cloud-platform/roadmap)
* [What's new in the Company Portal UI](whats-new-app-ui.md)(회사 포털 UI의 새로운 기능)
* [지난 달의 새로운 기능](whats-new-archive.md)
