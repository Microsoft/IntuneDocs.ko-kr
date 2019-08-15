---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/30/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95eede7c62e728aa0dbade4478eb87f31c252558
ms.sourcegitcommit: a6775522df49d17a4125ccb31be395f2343bdae8
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68833553"
---
# <a name="in-development-for-microsoft-intune---august-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 8월

준비 및 계획을 지원하기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 또한,

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 보완적인 Office Message Center 게시물을 게시할 것입니다.
- 미리 보기 또는 일반적으로 사용할 수 있는 기능을 프로덕션 환경에서 시작하면 기능 설명이 이 페이지에서 [새로운 기능 페이지](whats-new.md)로 이동합니다.
- 이 페이지와 [새로운 기능 페이지](whats-new.md)는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [M365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!Note]
> 이러한 항목은 향후 릴리스에서 제공될 Intune 기능에 대한 Microsoft의 현재 기대를 반영합니다. 날짜 및 개별 기능이 변경될 수 있습니다. 개발 중인 모든 항목이 이 페이지에 기능 설명이 있는 것은 아닙니다.

**RSS 피드**: 다음(`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`) URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
#### App management
#### Device configuration
#### Device enrollment
#### Device management
#### Intune apps
#### Monitor and troubleshoot
#### Role-based access control
#### Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>앱 관리

### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144---"></a>장치 등록 취소에서 iOS 앱 제거 동작 제어 <!-- 3504144 -->
관리자는 장치를 사용자 또는 장치 그룹 수준에서 등록 취소 때 장치에서 앱을 제거할지 또는 유지할지를 관리할 수 있습니다. 

### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>비즈니스용 Microsoft Store 앱 범주화 <!-- 3926922 -->
비즈니스 앱에 대 한 Microsoft Store 분류할 수 있습니다. 이렇게 하려면 **Intune**  > **클라이언트** > **앱앱을선택**하 > Microsoft Store 비즈니스 앱 > 앱**을 선택 합니다.**  >  정보**범주.** 드롭다운 메뉴에서 범주를 할당 합니다.
### <a name="configure-app-notification-content-for-organization-accounts----2576686---"></a>조직 계정에 대 한 앱 알림 콘텐츠 구성 <!-- 2576686 -->
Android 및 iOS 장치에서 Intune 앱 보호 정책 (앱)을 사용 하면 조직 계정에 대 한 앱 알림 콘텐츠를 제어할 수 있습니다. 이 기능을 사용 하려면 응용 프로그램에 대 한 지원이 필요 하며, 응용 프로그램을 사용 하도록 설정 된 응용 프로그램에는이 기능을 APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

### <a name="available-google-play-app-reporting-for-android-work-profiles----3041956----"></a>Android 작업 프로필에 사용할 수 있는 Google Play 앱 보고 <!-- 3041956  -->
Android 작업 프로필 디바이스에서 사용할 수 있는 앱 설치의 경우 앱 설치 상태 및 관리형 Google Play 앱의 설치된 버전을 확인할 수 있습니다. 자세한 정보는 [앱 보호 정책 모니터링 방법](app-protection-policies-monitor.md), [Intune으로 Android 작업 프로필 디바이스 관리](android-enterprise-overview.md) 및 [관리형 Google Play 앱 형식](apps-add-android-for-work.md#managed-google-play-app-type)을 참조하세요.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809----"></a>일부 자율 iOS 장치 제한 사항은 iOS 13.0 릴리스와 함께 감독 될 예정입니다. <!-- 4867809  -->
일부 설정은 iOS 13.0 릴리스로 시작 하는 감독 된 장치에 적용 됩니다. 이러한 설정은 다음과 같습니다.

- 앱 스토어, 문서 보기, 게임
  - 앱 스토어
  - 명시적 iTunes, 음악, 포드캐스트 또는 뉴스 콘텐츠
  - Game Center 친구 추가
  - 다중 접속 게임
- 기본 제공 앱
  - 카메라
    - FaceTime
  - Safari
    - 자동 채우기
- 클라우드 및 스토리지
  - iCloud에 백업
  - ICloud 문서 동기화 차단
  - iCloud 키 집합 동기화 차단

IOS 13.0 릴리스 이전에 이러한 설정을 구성 하 고 자율 장치에 할당 한 경우에도 해당 자율 장치에 설정이 적용 됩니다. 장치를 iOS 13.0로 업그레이드 한 후에도 계속 적용 됩니다. 이러한 제한 사항은 백업 및 복원 되는 자율 장치에서 제거 됩니다. 

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md)으로 이동하세요.

적용 대상:  
- iOS 13.0 이상

### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709----"></a>IOS 및 macOS 장치에서 기능을 제한 하는 새 설정 및 기존 설정 변경 <!-- 4867699 4867709  -->
IOS 및 macos를 실행 하는 장치에서 설정을 제한 하는 프로필을 만들 수**있습니다 (** 장치 > **구성**프로필 > **프로필 만들기** >  **플랫폼형식** > 장치제한)에대한**iOS**또는**macos** 다음 기능이 추가됩니다.

- **Macos**장치제한 >  **클라우드및** >  **저장소에서** 새**핸드 오프 설정을사용하여** 사용자가 하나의 macOS 장치에서 작업을 시작 하는 것을 차단 하 고 다른 macOS 또는 iOS 장치에서 작업을 계속 합니다.
  현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](device-restrictions-macos.md)으로 이동하세요.
- IOS **장치제한**에는  > **다음과** 같은 몇 가지 변경 사항이 있습니다.
  - **기본**제공 앱 >  **에서 내 iPhone 찾기 (감독 모드인 경우에만)** : 내 앱 찾기 기능에서이 기능을 차단 하는 새로운 설정입니다. 
  - **기본**제공 앱 >  **에서 내 친구 찾기 (감독 모드인 경우에만)** : 내 앱 찾기 기능에서이 기능을 차단 하는 새로운 설정입니다. 
  - **Wi-fi**상태의 무선 >  **수정 (감독 모드인 경우에만)** : 사용자가 장치에서 wi-fi를 켜거나 끌 수 없도록 하는 새로운 설정입니다.
  - **키보드 및 사전** >  **QuickPath (감독 모드인 경우에만)** : QuickPath 기능을 차단 하는 새로운 설정입니다.
  - **클라우드 및 저장소**: **활동** 연속은**전달으로 이름이 바뀝니다.**

  현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md)으로 이동하세요.

적용 대상:  
- macOS 10.15 이상
- iOS 13 이상

### <a name="control-the-apps-files-documents-and-folders-that-open-when-user-signs-in-to-macos-devices---3914202----"></a>사용자가 macOS 장치에 로그인 할 때 열리는 앱, 파일, 문서 및 폴더를 제어 합니다. <!--3914202  -->
Macos 장치에서 기능을 사용 하도록 설정 하 고 구성할 수 있습니다 **(장치**구성 > **프로필** >  프로 **필**만들기  >  **프로필 형식** 에 대 한 **플랫폼 >** 장치 기능에 대 한 macos입니다. 

사용자가 등록 된 장치에 로그인 할 때 열리는 앱, 파일, 문서 및 폴더를 제어 하기 위한 새로운 로그인 항목 설정이 있습니다. 

현재 설정을 보려면 Intune의 [macOS 디바이스 기능 설정](macos-device-features-settings.md)으로 이동하세요.

적용 대상:  
- macOS

### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946----"></a>다중 앱 모드의 Android Enterprise 전용 장치에 대 한 새로운 기능 <!-- 3755304 3041943 3041946  -->
Android Enterprise 전용 장치의 키오스크 스타일 환경에서 기능과 설정을 제어할 수 있습니다. 이렇게 하려면 장치 구성 **프로필**  > **프로필만들기**  >  Android Enterprise**를 선택**  >  합니다. **플**랫폼 **>** 장치 소유자만, 프로필 형식에 대 한 장치 제한

다음 기능이 추가됩니다.
- **전용 장치** > **다중앱**:**사용자가이동할수** 있도록 장치에서 위로 살짝 밀거나 화면에서 떠 있는 가상홈단추를표시할수있습니다.
- **전용 장치** >  **다중앱**: **손전등액세스** 를 통해 사용자는 손전등를 사용할 수 있습니다. 
- **전용 장치** > **다중앱**:**미디어볼륨** 컨트롤을 사용 하면 사용자가 슬라이더를 사용 하 여 장치의 미디어 볼륨을 제어할 수 있습니다. 
- **전용 장치** > **다중앱**: 화면 보호기를 사용 하도록 설정 하 고, 사용자 지정 이미지를 업로드 하 고, 화면 보호기가 표시 되는 시기를 제어 합니다.

현재 설정 목록을 보려면 Intune에서 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md#dedicated-device-settings)으로 이동합니다.

적용 대상:  
- Android 엔터프라이즈 전용 디바이스

### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215----"></a>Android Enterprise 완전히 관리 되는 장치에 대 한 새 앱 및 구성 프로필 <!-- 3574215  -->
프로필을 사용 하 여 Android Enterprise 완전히 관리 되는 장치에 VPN, 전자 메일 및 Wi-fi 설정을 적용 하는 설정을 구성할 수 있습니다. 다음 작업을 수행할 수 있습니다.
- 앱 프로필을 사용 하 여 Outlook, Gmail 및 9 개의 업무용 메일 설정을 배포 합니다.
- 장치 구성 프로필을 사용 하 여 신뢰할 수 있는 루트 인증서 설정을 배포 합니다.
- 장치 구성 프로필을 사용 하 여 VPN 및 Wi-fi 설정을 배포 합니다.

사용자는 VPN, Wi-fi 및 전자 메일 프로필에 대 한 사용자 이름 및 암호를 사용 하 여 인증 합니다. 현재는 인증서 기반 인증을 사용할 수 없습니다. 

적용 대상:  
- Android Enterprise 완전 관리형

### <a name="support-for-ikev2-vpn-profiles-for-ios----1943438---"></a>iOS용 IKEv2 VPN 프로필 지원 <!-- 1943438 -->
IKEv2 프로토콜을 사용하여 iOS 원시 VPN 클라이언트에 대한 VPN 프로필을 만들 수 있습니다. IKEv2는 **디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **VPN**(프로필 형식) > **설정**의 새 연결 형식입니다.

이 VPN 프로필은 원시 VPN 클라이언트를 구성합니다. 따라서 관리 디바이스에 VPN 클라이언트 앱이 설치되거나 푸시되지 않습니다. 이 기능을 사용하려면 디바이스를 Intune에 등록해야 합니다(MDM 등록).

구성할 수 있는 최신 VPN 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)을 참조하세요.

적용 대상: iOS

<!-- ***********************************************-->
## <a name="device-enrollment"></a>디바이스 등록

### <a name="skip-more-screens-in-setup-assistant---4877451---"></a>설정 도우미에서 더 많은 화면 건너뛰기 <!--4877451 -->
장비 등록 프로그램 프로필을 설정 하 여 다음 설정 도우미 화면을 건너뛸 수 있습니다. 
- 화면 시간
- Touch ID 설정

이렇게 하려면 장치 등록 **Apple등록**  > **등록프로그램** >  **토큰으로이동하>토큰을선택**>  **프로필** **>**  > **설정 도우미 사용자지**정**옆의 프로필 > 속성 편집을 선택 합니다.**
설정 도우미 사용자 지정에 대 한 자세한 내용은 [Apple 등록 프로필 ](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)만들기를 참조 하세요.

### <a name="android-enrollment-device-administrator-support----4869749----"></a>Android 등록 장치 관리자 지원 <!-- 4869749  -->
Android 장치 관리자 등록 옵션이 android**등록 페이지 (Intune**  >  **장치 등록** > **android)에 추가 됩니다. 등록**). Android 장치 관리자는 모든 테 넌 트에 대해 기본적으로 사용 하도록 설정 되어 있습니다.  

### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993----"></a>IOS 장치에 대해 회사 포털 등록 프로세스 개인 정보 화면을 사용자 지정 합니다. <!-- 4394993  -->
Markdown를 사용 하면 iOS 등록 중 최종 사용자에 게 표시 되는 회사 포털 개인 정보 화면을 사용자 지정할 수 있습니다. 특히, 조직에서 볼 수 없거나 장치에서 수행할 수 없는 항목 목록을 사용자 지정할 수 있습니다.

<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리

### <a name="build-number-included-on-android-device-hardware-page----4461910----"></a>Android 장치 하드웨어 페이지에 포함 된 빌드 번호 <!-- 4461910  -->
각 Android 장치에 대 한 하드웨어 페이지의 새 항목에는 장치의 운영 체제 빌드 번호가 포함 됩니다.

### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>자동 장치 정리 시간 제한을 30 일로 구성 <!--4231059  -->
자동 장치 정리 시간 제한은 마지막 로그인 후 30 일 (현재 제한인 90 일 대신)을 30 일로 설정할 수 있습니다. 이렇게 하려면 **Intune** > **장치** >  **설정장치** > **정리 규칙**으로 이동 합니다.

<!-- ***********************************************-->
## <a name="role-based-access-control"></a>역할 기반 액세스 제어

### <a name="default-scope-tag----3702875---"></a>기본 범위 태그 <!-- 3702875 -->
새 기본 제공 기본 범위 태그를 사용할 수 있습니다. 범위 태그를 지 원하는 태그가 지정 되지 않은 모든 Intune 개체는 기본 범위 태그에 자동으로 할당 됩니다. 현재 관리 **환경에서 패리티를 유지 하기 위해 기존 역할 할당에 기본범위태그가추가됩니다.** 관리자가 기본 범위 태그를 가진 Intune 개체를 표시 하지 않도록 하려면 역할 할당에서 기본 범위 태그를 제거 합니다. 이 기능은 System Center Configuration Manager의 보안 범위 기능과 유사 합니다.

<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="import-and-export-security-baselines------3408610------------"></a>보안 기준 가져오기 및 내보내기    <!--3408610          -->  
보안 기준을 내보내고 가져오는 기능을 추가 하는 중입니다. 이 기능을 사용 하면 사용자 지정 항목을 가져와서 Intune 환경 간에 공유할 수 있습니다.

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.




