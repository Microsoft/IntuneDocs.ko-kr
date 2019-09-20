---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b7b4453d441d2f2367b19a6bf0505dabd8e6e48
ms.sourcegitcommit: 27e63a96d15bc4062af68c2764905631bd928e7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71061675"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. 또한 [중요한 공지](#notices), [과거 릴리스](whats-new-archive.md) 및 [Intune 서비스 업데이트가 릴리스되는 방법](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)에 관한 정보도 찾을 수 있습니다. 

> [!Note]
> 각 [월별 업데이트](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)는 출시에 최대 3일이 걸릴 수 있고 다음 순서로 출시됩니다.
> - 1일: 아시아 태평양(APAC)
> - 2일: 유럽, 중동, 아프리카(EMEA)
> - 3일: 북아메리카
> 
> 일부 기능은 몇 주에 걸쳐 출시될 수 있고 첫 번째 주에는 모든 고객에게 제공되지 않습니다.
>
> [개발 페이지](in-development.md)에서 릴리스의 예정 기능 목록을 확인하세요.

**RSS 피드**: 다음 URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다. `https://docs.microsoft.com/api/search/rss?search=%22What%27s+new+in+microsoft+intune%3F+-+Azure%22&locale=en-us`

<!-- Common categories:  
### App management
### Device configuration
### Device enrollment
### Device management
### Device security
### Intune apps
### Monitor and troubleshoot
### Role-based access control

-->  

<!-- ########################## -->

## <a name="week-of-september-16-2019"></a>2019년 9월 16일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="macos-support-for-web-apps----3174427---"></a>웹 앱에 대한 macOS 지원 <!-- 3174427 -->
웹에서 URL에 바로 가기를 추가할 수 있는 웹 앱을 macOS 회사 포털을 이용해 독에 설치할 수 있습니다. 최종 사용자는 macos 회사 포털에서 웹 앱의 앱 세부정보 페이지로 이동하면 **설치** 작업을 이용할 수 있습니다. **웹 링크** 앱 유형에 대한 자세한 내용은 [Microsoft Intune에 앱 추가](apps-add.md)와 [Microsoft Intune에 웹앱 추가](web-app.md)를 참조하세요.

#### <a name="macos-support-for-vpp-apps----3173501----"></a>VPP 앱에 대한 macOS 지원 <!-- 3173501  -->
Apple Business Manager로 구매한 macOS 앱은 이후 Apple VPP 토큰이 동기화되면 콘솔에 표시됩니다. Intune 콘솔을 이용해 그룹용 디바이스 및 사용자 기반 라이선스를 할당, 취소, 재할당할 수 있습니다. Microsoft Intune을 이용하면 회사에서 사용할 목적으로 구매한 VPP 앱을 다음 기능을 이용해 관리할 수 있습니다.
- 앱 스토어에서 라이선스 정보 보고.
- 사용한 라이선스 수 추적.
- 소유한 양보다 많은 앱 복사본을 설치하지 않도록 도움.

Intune 및 VPP에 대한 자세한 내용은 [Microsoft Intune을 사용하여 대량 구매 앱 및 전자책 관리](vpp-apps.md)를 참조하세요.

## <a name="week-of-september-9-2019"></a>2019년 9월 9일이 있는 주

### <a name="app-management"></a>앱 관리

#### <a name="updates-to-microsoft-intune-app----4997846---"></a>Microsoft Intune 앱 업데이트 <!-- 4997846 -->
Android용 Microsoft Intune 앱이 다음과 같은 향상된 기능으로 업데이트되었습니다.
- 가장 중요한 작업으로 이동할 수 있는 아래쪽 탐색 창을 포함하도록 레이아웃을 업데이트하고 개선했습니다.
- 사용자의 프로필을 표시하는 추가 페이지를 추가했습니다.
- 사용자를 위해 디바이스 설정 업데이트 필요를 알리는 등의 실행 가능한 알림의 표시를 앱에 추가했습니다.
- iOS 및 Android용 회사 포털 앱에 최근 추가된 지원 기능에 따라 앱에 사용자 지정 푸시 알림의 표시를 추가했습니다. 자세한 내용은 [Intune에서 사용자 지정 알림 보내기](custom-notifications.md)를 참조하세요.

#### <a name="for-ios-devices-customize-the-enrollment-process-privacy-screen-of-the-company-portal----4394993---"></a>IOS 디바이스에서 회사 포털의 등록 프로세스 개인 정보 화면을 사용자 지정합니다 <!-- 4394993 -->
Markdown을 이용하면 iOS 등록 과정에서 최종 사용자에게 표시되는 회사 포털의 개인 정보 화면을 사용자 지정할 수 있습니다. 특히 조직이 디바이스에서 볼 수 없거나 해선 안 되는 항목 목록을 사용자 지정할 수 있습니다. 자세한 내용은 [Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md#privacy-statement-customization)을 참조하세요.


## <a name="week-of-september-2-2019"></a>2019년 9월 2일이 있는 주

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="intune-user-interface-update--tenant-status-dashboard-----5273210----"></a>Intune 사용자 인터페이스 업데이트 - 테넌트 상태 대시보드  <!-- 5273210  -->
테넌트 상태 대시보드의 사용자 인터페이스가 Azure 사용자 인터페이스 스타일에 맞게 업데이트되었습니다. 자세한 내용은 [테넌트 상태](tenant-status.md)를 참조하세요.


## <a name="week-of-august-26-2019"></a>2019년 8월 26일 주

### <a name="configure-microsoft-edge-settings-using-administrative-templates-for-windows-10-and-newer----5228061---"></a>Windows 10 이상에 대해 관리 템플릿을 사용하여 Microsoft Edge 설정 구성 <!-- 5228061 -->

Windows 10 이상 디바이스에서는 Intune에서 그룹 정책 설정을 구성하는 관리 템플릿을 만들 수 있습니다. 이 업데이트에서는 Microsoft Edge 버전 77 이상에 적용되는 설정을 구성할 수 있습니다.

관리 템플릿에 대한 자세한 내용은 [Windows 10 템플릿을 사용하여 Intune에서 그룹 정책 설정 구성](administrative-templates-windows.md)을 참조하세요.

적용 대상:

- Windows 10 이상(Windows RS4 이상)

## <a name="week-of-august-12-2019"></a>2019년 8월 12일 주

### <a name="app-management"></a>앱 관리

#### <a name="control-ios-app-uninstall-behavior-at-device-unenrollment----3504144-----"></a>디바이스 등록 취소에서 iOS 앱 제거 동작 제어 <!-- 3504144   -->
관리자는 디바이스가 사용자 또는 디바이스 그룹 수준에서 등록 취소될 때 디바이스에서 앱을 제거할지 유지할지를 관리할 수 있습니다. 

#### <a name="categorize-microsoft-store-for-business-apps----3926922---"></a>비즈니스용 Microsoft Store 앱 범주화 <!-- 3926922 -->
비즈니스용 Microsoft Store 앱을 범주화할 수 있습니다. 이렇게 하려면 **Intune** > **클라이언트 앱** > **앱** > 비즈니스용 Microsoft Store 앱 선택 > **앱 정보** > **범주**를 선택합니다. 드롭다운 메뉴에서 범주를 할당합니다.

#### <a name="customized-notifications-for-microsoft-intune-app-users----4843354----"></a>Microsoft Intune 앱 사용자에 맞게 사용자 지정된 알림 <!-- 4843354  -->
이제 Android용 Microsoft Intune 앱은 사용자 지정 푸시 알림의 표시를 지원하여 iOS 및 Android용 회사 포털 앱에 최근에 추가된 지원에 맞춰 정렬합니다. 자세한 내용은 [Intune에서 사용자 지정 알림 보내기](custom-notifications.md)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="new-features-for-android-enterprise-dedicated-devices-in-multi-app-mode----3755304-3041943-3041946-----"></a>다중 앱 모드에서 Android 엔터프라이즈 전용 디바이스의 새로운 기능 <!-- 3755304 3041943 3041946   -->
Intune에서는 Android 엔터프라이즈 전용 디바이스의 키오스크 스타일 환경에서 기능 및 설정을 제어할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **디바이스 소유자만, 디바이스 제한**(프로필 유형)).

이 업데이트에서는 다음과 같은 기능이 추가됩니다.

- **전용 디바이스** > **다중 앱**: **가상 홈 단추**는 디바이스에서 위로 살짝 밀거나 화면에서 부동 처리하여 표시하면 사용자가 이동할 수 있습니다.
- **전용 디바이스** > **다중 앱**: **손전등 액세스**를 통해 사용자는 손전등을 사용할 수 있습니다. 
- **전용 디바이스** > **다중 앱**: **미디어 볼륨 컨트롤**을 통해 사용자는 슬라이더를 사용하여 디바이스의 미디어 볼륨을 제어할 수 있습니다. 
- **전용 디바이스** > **다중 앱**:  **화면 보호기를 사용**하도록 설정하고, 사용자 지정 이미지를 업로드하고, 화면 보호기 표시 시기를 제어합니다.

현재 설정 목록을 보려면 Intune에서 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md#dedicated-device-settings)으로 이동합니다.

적용 대상:  
- Android 엔터프라이즈 전용 디바이스

#### <a name="new-app-and-configuration-profiles-for-android-enterprise-fully-managed-devices----3574215-3574238-3574235-3574232-----"></a>Android 엔터프라이즈 완전 관리형 디바이스에 대한 새 앱 및 구성 프로필 <!-- 3574215 3574238 3574235 3574232   -->
프로필을 사용하여 Android 엔터프라이즈 디바이스 소유자(완전 관리형) 디바이스에 VPN, 메일 및 Wi-Fi 설정을 적용하는 설정을 구성할 수 있습니다. 이 업데이트에서는 다음을 수행할 수 있습니다.

- [앱 구성 정책](app-configuration-policies-use-android.md)을 사용하여 Outlook, Gmail 및 Nine Work 메일 설정을 배포합니다.
- 디바이스 구성 프로필을 사용하여 [신뢰할 수 있는 루트 인증서 설정](certificates-configure.md)을 배포합니다.
- 디바이스 구성 프로필을 사용하여 [VPN](vpn-settings-android-enterprise.md) 및 [Wi-Fi](wi-fi-settings-android-enterprise.md) 설정을 배포합니다.

> [!IMPORTANT]
> 이 기능을 사용하면 사용자는 VPN, Wi-Fi 및 메일 프로필에 대해 사용자 이름 및 암호를 사용하여 인증합니다. 현재는 인증서 기반 인증을 사용할 수 없습니다. 

적용 대상:  
- Android 엔터프라이즈 디바이스 소유자(완전 관리형)

#### <a name="control-the-apps-files-documents-and-folders-that-open-when-users-sign-in-to-macos-devices---3914202-----"></a>사용자가 macOS 디바이스에 로그인할 때 열리는 앱, 파일, 문서 및 폴더를 제어합니다. <!--3914202   -->
macOS 디바이스에서 기능을 사용하도록 설정하고 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **macOS**(플랫폼) > **디바이스 기능**(프로필 유형)). 

이 업데이트에는 사용자가 등록된 디바이스에 로그인할 때 열리는 앱, 파일, 문서 및 폴더를 제어하는 새 로그인 항목 설정이 있습니다. 

현재 설정을 보려면 Intune의 [macOS 디바이스 기능 설정](macos-device-features-settings.md)으로 이동하세요.

적용 대상:  
- macOS

#### <a name="deadlines-replace-engaged-restart-settings-for-windows-update-rings------4464404----------"></a>최종 기한이 Windows 업데이트 링의 개입형 다시 시작 설정 대체   <!-- 4464404        -->
최신 [Windows 서비스 변경 내용](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1903#servicing)과 맞추기 위해 이제 Intune의 Windows 10 업데이트 링에서 [최종 기한에 대한 설정을 지원](windows-update-settings.md)합니다. ‘최종 기한’은 디바이스에서 기능 및 보안 업데이트를 설치하는 시기를 결정합니다.   Windows 10 1903 이상이 실행되는 디바이스에서 ‘최종 기한’은 ‘개입형 다시 시작’에 대한 구성을 대체합니다.    나중에 ‘최종 기한’은 이전 버전의 Windows 10에서도 ‘개입형 다시 시작’을 대체하게 됩니다.    

‘최종 기한’을 구성하지 않으면 디바이스에서 ‘개입형 다시 시작’ 설정을 계속 사용하지만 향후 업데이트에서 [Intune은 개입형 다시 시작 설정을 더 이상 지원하지 않습니다](whats-new.md#plan-for-change-new-windows-updates-settings-in-intune-).    

모든 Windows 10 디바이스에서 ‘최종 기한’을 사용하도록 계획합니다  . ‘최종 기한’에 대한 설정이 구현되면 ‘개입형 다시 시작’에 대한 Intune 구성을 [구성되지 않음]으로 변경할 수 있습니다.   [구성되지 않음]으로 설정하면 Intune은 디바이스에서 해당 설정 관리를 중지하지만 설정에 대한 마지막 구성을 디바이스에서 제거하지는 않습니다. 따라서 ‘개입형 다시 시작’에 대해 설정된 마지막 구성은 Intune 이외의 다른 방법에 의해 수정될 때까지 디바이스에서 활성화되어 사용 중인 상태로 유지됩니다.  나중에 Windows의 디바이스 버전이 변경되거나 ‘최종 기한’에 대한 Intune 지원이 디바이스 Windows 버전으로 확장되면 디바이스는 이미 구현된 새 설정을 사용하기 시작합니다. 

#### <a name="support-for-multiple-microsoft-intune-certificate-connectors--------4704642--------"></a>여러 Microsoft Intune Certificate Connector에 대한 지원   <!--   4704642      -->
이제 Intune에서 여러 [Microsoft Intune Certificate Connectors for PKCS operations](certficates-pfx-configure.md)(PKCS용 Microsoft Intune Certificate Connector 작업)의 설치 및 사용을 지원합니다. 이러한 변경은 커넥터의 부하 분산 및 고가용성을 지원합니다. 각 커넥터 인스턴스는 Intune의 인증서 요청을 처리할 수 있습니다.  한 커넥터를 사용할 수 없는 경우 다른 커넥터에서 계속 요청을 처리합니다. 

여러 커넥터를 사용하기 위해 최신 버전의 커넥터 소프트웨어로 업그레이드할 필요가 없습니다.  

#### <a name="new-settings-and-changes-to-existing-settings-to-restrict-features-on-ios-and-macos-devices----4867699-4867709-----"></a>iOS 및 macOS 디바이스에서 기능을 제한하는 새 설정 및 기존 설정의 변경 내용 <!-- 4867699 4867709   -->
iOS 및 macOS를 실행하는 디바이스에서 프로필을 만들어 설정을 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 또는 **macOS**(플랫폼 유형) > **디바이스 제한**). 이 업데이트에는 다음 기능이 포함됩니다.

- **macOS** > **디바이스 제한** > **클라우드 및 스토리지**에서 새 **핸드오프** 설정을 사용하여 한 macOS 디바이스에서 사용자의 작업 시작을 차단하고 다른 macOS 또는 iOS 디바이스에서는 계속 작업합니다.

  현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](device-restrictions-macos.md)으로 이동하세요.

- **iOS** > **디바이스 제한**에는 다음과 같은 몇 가지 변경 사항이 있습니다.

  - **기본 제공 앱** > **내 iPhone 찾기(감독 모드인 경우에만)** : 내 앱 찾기 기능에서 이 기능을 차단하는 새로운 설정입니다. 
  - **기본 제공 앱** > **내 친구 찾기(감독 모드인 경우에만)** : 내 앱 찾기 기능에서 이 기능을 차단하는 새로운 설정입니다. 
  - **무선** > **Wi-Fi 상태 수정(감독 모드인 경우에만)** : 사용자가 디바이스에서 Wi-Fi를 켜거나 끌 수 없도록 하는 새로운 설정입니다.
  - **키보드 및 사전** > **QuickPath(감독 모드인 경우에만)** : QuickPath 기능을 차단하는 새로운 설정입니다.
  - **클라우드 및 스토리지**: **활동 연속**은 **핸드오프**로 이름이 바뀌었습니다.

  현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md)으로 이동하세요.

적용 대상:  
- macOS 10.15 이상
- iOS 13 이상

#### <a name="some-unsupervised-ios-device-restrictions-will-become-supervised-only-with-the-ios-130-release----4867809-----"></a>일부 감독되지 않은 iOS 디바이스 제한이 iOS 13.0 릴리스에서 감독 전용이 됨 <!-- 4867809   -->
이 업데이트에서 일부 설정은 iOS 13.0 릴리스를 사용하는 감독 전용 디바이스에 적용됩니다. 이러한 설정이 iOS 13.0 릴리스 이전에 구성되고 감독되지 않은 디바이스에 할당되면 설정은 해당 감독되지 않은 디바이스에 계속 적용됩니다. 또한 디바이스가 iOS 13.0으로 업그레이드된 후에도 계속 적용됩니다. 이러한 제한은 백업되고 복원되는 감독되지 않은 디바이스에서 제거됩니다. 

이러한 설정은 다음과 같습니다.

- 앱 스토어, 문서 보기, 게임
  - 앱 스토어
  - 유해 iTunes, 음악, 팟캐스트 또는 뉴스 콘텐츠
  - Game Center 친구 추가
  - 다중 접속 게임
- 기본 제공 앱
  - 카메라
    - FaceTime
  - Safari
    - 자동 채우기
- 클라우드 및 스토리지
  - iCloud에 백업
  - iCloud 문서 동기화 차단
  - iCloud 키 집합 동기화 차단

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md)으로 이동하세요.

적용 대상:  
- iOS 13.0 이상

#### <a name="improved-device-status-for-macos-filevault-encryption-----4944983-----------"></a>macOS FileVault 암호화에 대한 디바이스 상태 개선  <!-- 4944983         -->
macOS 디바이스에서 FileVault 암호화에 대한 여러 가지 [디바이스 상태 메시지](encryption-monitor.md#device-encryption-status)를 업데이트했습니다.

#### <a name="some-windows-defender-antivirus-scan-settings-in-the-reporting-show-a-failed-status----5119229---"></a>보고의 일부 Windows Defender 바이러스 백신 검사 설정에 실패 상태가 표시됨 <!-- 5119229 -->
Intune에서 Windows Defender 바이러스 백신을 사용하여 Windows 10 디바이스를 검사하는 정책을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **디바이스 제한**(프로필 유형) > **Windows Defender 바이러스 백신**). **매일 빠른 검색을 수행할 시간** 및 **수행할 시스템 검사 유형** 보고에 실제로 성공 상태인 경우에도 실패 상태가 표시됩니다. 

이 업데이트에서 이러한 동작이 수정되었습니다. 따라서 **매일 빠른 검색을 수행할 시간** 및 **수행할 시스템 검사 유형** 설정에는 검사가 성공적으로 완료되면 성공 상태가 표시되고, 설정이 적용되지 않으면 실패 상태가 표시됩니다. 

Windows Defender 바이러스 백신 설정에 대한 자세한 내용은 [Intune을 사용하여 기능을 허용하거나 제한하는 Windows 10 이상 디바이스 설정](device-restrictions-windows-10.md#microsoft-defender-antivirus)을 참조하세요. 

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="default-scope-tags----3702875----"></a>기본 범위 태그 <!-- 3702875  -->
이제 새로운 기본 제공 기본 범위 태그를 사용할 수 있습니다. 범위 태그를 지원하는 태그가 지정되지 않은 모든 Intune 개체는 기본 범위 태그에 자동으로 할당됩니다. 현재 관리자 환경에서 패리티를 유지하기 위해 **기본** 범위 태그는 기존의 모든 역할 할당에 추가됩니다. 관리자가 기본 범위 태그를 사용하여 Intune 개체를 표시하지 않도록 하려면 역할 할당에서 기본 범위 태그를 제거합니다. 이 기능은 System Center Configuration Manager의 보안 범위 기능과 유사합니다. 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

#### <a name="android-enrollment-device-administrator-support----4869749-----"></a>Android 등록 디바이스 관리자 지원 <!-- 4869749   -->
Android 디바이스 관리자 등록 옵션이 Android 등록 페이지(**Intune** > **디바이스 등록** > **Android 등록**)에 추가되었습니다. Android 디바이스 관리자는 모든 테넌트에 대해 기본적으로 사용하도록 설정되어 있습니다.  자세한 내용은 [Android 디바이스 관리자 등록](android-enroll-device-administrator.md)을 참조하세요.

#### <a name="skip-more-screens-in-setup-assistant---4877451----"></a>설정 도우미에서 더 많은 화면 건너뛰기 <!--4877451  -->
다음과 같은 설정 도우미 화면을 건너뛰도록 디바이스 등록 프로그램 프로필을 설정할 수 있습니다.
- iOS의 경우
    - 모양
    - Express 언어
    - 기본 설정 언어
    - 디바이스 간 마이그레이션
- macOS의 경우
    - 화면 시간
    - Touch ID 설정

설정 도우미 사용자 지정에 대한 자세한 내용은 [Create an Apple enrollment profile for iOS](device-enrollment-program-enroll-ios.md#create-an-apple-enrollment-profile)(iOS용 Apple 등록 프로필 만들기) 및 [Create an Apple enrollment profile for macOS](device-enrollment-program-enroll-macos.md#create-an-apple-enrollment-profile)(macOS용 Apple 등록 프로필 만들기)를 참조하세요.

#### <a name="add-a-user-column-to-the-autopilot-device-csv-upload-process----3823054---"></a>Autopilot 디바이스 CSV 업로드 프로세스에 사용자 열 추가 <!-- 3823054 -->
이제 Autopilot 디바이스에 대한 CSV 업로드에 사용자 열을 추가할 수 있습니다. 이렇게 하면 CSV를 가져올 때 사용자를 대량으로 할당할 수 있습니다. 자세한 내용은 [Windows Autopilot을 사용하여 Intune에 Windows 디바이스 등록](enrollment-autopilot.md)을 참조하세요.


### <a name="device-management"></a>디바이스 관리

#### <a name="configure-automatic-device-clean-up-time-limit-down-to-30-days---4231059----"></a>자동 디바이스 정리 시간 제한을 30일로 구성 <!--4231059  -->
자동 디바이스 정리 시간 제한은 마지막 로그인 후 30일(이전에는 90일 제한)로 설정할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스** > **설정디바이스** > **정리 규칙**으로 이동 합니다.

#### <a name="build-number-included-on-android-device-hardware-page----4461910-----"></a>Android 디바이스 하드웨어 페이지에 포함된 빌드 번호 <!-- 4461910   -->
각 Android 디바이스에 대한 하드웨어 페이지의 새 항목에는 디바이스의 운영 체제 빌드 번호가 포함됩니다. 자세한 내용은 [View device details in Intune](device-inventory.md)(Intune에서 디바이스 세부 정보 보기)을 참조하세요.


<!-- ########################## -->

## <a name="week-of-august-5-2019"></a>2019년 8월 5일 주

### <a name="zebra-technologies-is-a-supported-oem-for-oemconfig-on-android-enterprise-devices-----4843713---"></a>Zebra Technologies는 Android 엔터프라이즈 디바이스에서 지원되는 OEMConfig OEM임  <!-- 4843713 -->

Intune에서는 OEMConfig를 사용하여 디바이스 구성 프로필을 만들고, 설정을 Android 엔터프라이즈 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **OEMConfig**(프로필 유형)).

이 업데이트에서 Zebra Technologies는 지원되는 OEMConfig OEM(Original Equipment Manufacturer)입니다. OEMConfig에 대한 자세한 내용은 [Use and manage Android Enterprise devices with OEMConfig](android-oem-configuration-overview.md)(OEMConfig를 사용하여 Android 엔터프라이즈 디바이스 사용 및 관리)를 참조하세요.

적용 대상:  
- Android 엔터프라이즈

<!-- ########################## -->

## <a name="week-of-july-22-2019"></a>2019년 7월 22일 주 

### <a name="app-management"></a>앱 관리

#### <a name="customized-notifications-for-users-and-groups-------16766574------------"></a>사용자 및 그룹을 위한 사용자 지정 알림    <!-- 16766574          -->
Intune으로 관리하는 iOS 및 Android 디바이스를 사용하는 사용자에게 회사 포털 애플리케이션에서 푸시 알림을 보낼 수 있습니다. 모바일 푸시 알림은 무료 텍스트로 원하는 대로 사용자 지정할 수 있으며, 어떤 용도로도 사용할 수 있습니다. 조직의 여러 사용자 그룹을 대상으로 알림을 보낼 수 있습니다. 자세한 내용은 [사용자 지정 알림](custom-notifications.md)을 참조하세요.

#### <a name="googles-device-policy-controller-app----3041950----"></a>Google의 디바이스 정책 컨트롤러 앱 <!-- 3041950  -->
이제 Managed Home Screen 앱에서 Google의 Android 디바이스 정책 앱에 액세스할 수 있습니다. Managed Home Screen 앱은 Intune에 다중 앱 키오스크 모드를 사용하는 AE(Android 엔터프라이즈) 전용 디바이스로 등록된 디바이스에 사용되는 사용자 지정 시작 관리자입니다. Android 디바이스 정책 앱에서 액세스하거나 지원 및 디버깅을 위해 사용자를 Android 디바이스 정책 앱으로 안내할 수 있습니다. 이 시작 기능은 디바이스가 등록되고 Managed Home Screen으로 잠길 때 사용할 수 있습니다. 이 기능을 사용하기 위해 추가 설치가 필요하지 않습니다.

#### <a name="outlook-protection-settings-for-ios-and-android-devices----3212619---"></a>iOS 및 Android 디바이스의 Outlook 보호 설정 <!-- 3212619 -->
이제 디바이스 등록 없이도 간단한 Intune 관리 컨트롤을 사용하여 iOS 및 Android의 Outlook 일반 앱 구성 설정과 데이터 보호 구성 설정을 구성할 수 있습니다. 일반 앱 구성 설정은 관리자가 등록된 디바이스에서 iOS 및 Android용 Outlook을 관리할 때 활성화할 수 있는 설정과 동등한 설정을 제공합니다. Outlook 설정에 대한 자세한 내용은 [iOS 및 Android용 Outlook 앱 구성 설정 배포](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune)를 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910-eeready---idstaged---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 eeready   idstaged -->

Windows 10 다비이스 구성 프로필을 만듭니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼은 **Windows 10** 선택 > **적용 가능성 규칙**). 이 업데이트에서는 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 가능성 규칙을 추가하려면 [적용 가능성 규칙](device-profile-create.md#applicability-rules)을 참조하세요.

적용 대상: Windows 10 이상

#### <a name="use-tokens-to-add-device-specific-information-in-custom-profiles-for-ios-and-macos-devices----3330008----"></a>토큰을 사용하여 iOS 및 macOS 디바이스의 사용자 지정 프로필에 디바이스별 정보 추가 <!-- 3330008  -->
iOS 및 macOS 디바이스에서 사용자 지정 프로필을 사용하여 Intune에서 기본 제공되지 않는 설정 및 기능을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼은 **iOS** 또는 **macOS** 선택 > 프로필 유형은 **사용자 지정** 선택). 이 업데이트에서는 `.mobileconfig` 파일에 토큰을 추가하여 디바이스별 정보를 추가할 수 있습니다. 예를 들어 구성 파일에 `Serial Number: {{serialnumber}}`를 추가하여 디바이스의 일련 번호를 표시할 수 있습니다.

사용자 지정 프로필을 만들려면 [iOS 사용자 지정 설정](custom-settings-ios.md) 또는 [macOS 사용자 지정 설정](custom-settings-macos.md)을 참조하세요.

적용 대상:
- iOS
- macOS

#### <a name="new-configuration-designer-when-creating-an-oemconfig-profile-for-android-enterprise----3712769-----"></a>Android 엔터프라이즈용 OEMConfig 프로필을 만들 때 새로운 구성 디자이너 사용 <!-- 3712769   -->
Intune에서 OEMConfig 앱을 사용하는 디바이스 구성 프로필을 만들 수 있습니다(디바이스 구성 > 프로필 > 프로필 만들기 > 플랫폼은 [Android 엔터프라이즈] 선택 > 프로필은 [OEMConfig] 선택). 이렇게 하면 템플릿 및 변경 가능한 값과 JSON 편집기가 열립니다. 

이 업데이트는 제목, 설명 등과 같은 세부 정보를 앱에 포함하여 표시하는 향상된 사용자 환경을 갖춘 구성 디자이너를 포함합니다. 기존과 같이 JSON 편집기도 사용할 수 있으며, 구성 디자이너에서 수행한 변경 사항이 모두 표시됩니다.

기존 설정을 보려면 [Use and manage Android Enterprise devices with OEMConfig](android-oem-configuration-overview.md)(OEMConfig를 사용하여 Android 엔터프라이즈 디바이스 사용 및 관리)를 참조하세요.

적용 대상: Android Enterprise

#### <a name="updated-ui-for-configuring-windows-hello-----4089576--------------"></a>Windows Hello 구성을 위한 업데이트된 UI  <!-- 4089576            -->
[비즈니스용 Windows Hello를 사용하여 Intune을 구성하는](windows-hello.md) 콘솔이 업데이트되었습니다. 이제 Windows Hello 지원을 활성화하는 콘솔의 동일한 창에서 모든 구성 설정을 이용할 수 있습니다. 


#### <a name="intune-powershell-sdk----4924113---"></a>Intune PowerShell SDK <!-- 4924113 --> 
Microsoft Graph를 통해 Intune API를 지원하는 Intune PowerShell SDK가 버전 6.1907.1.0으로 업데이트되었습니다. Intune PowerShell SDK는 이제 다음을 지원합니다.
- Azure Automation과 작동합니다.
- App-Only Auth 읽기 작업을 지원합니다. 
- 친숙한 짧은 이름(별칭 등)을 지원합니다.
- PowerShell 명명 규칙을 준수합니다. 구체적으로, `Connect-MSGraph` cmdlet의 `PSCredential` 매개 변수 이름이 `Credential`로 변경되었습니다.
- `Invoke-MSGraphRequest` cmdlet을 사용할 때 `Content-Type` 헤더의 값을 수동으로 지정할 수 있습니다.

자세한 내용은 [PowerShell SDK for Microsoft Intune Graph API](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune)(Microsoft Intune Graph API를 위한 PowerShell SDK)를 참조하세요.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="updates-for-enrollment-restrictions-----2871968---"></a>등록 제한 업데이트  <!-- 2871968 -->
Android 엔터프라이즈 회사 프로필이 기본적으로 허용되도록 새로운 테넌트에 대한 등록 제한이 업데이트되었습니다. 이 변경 사항은 기존 테넌트에 영향을 주지 않습니다. Android 엔터프라이즈 회사 프로필을 사용하려면 기존과 같이 [Intune 계정을 관리형 Google Play 계정에 연결](https://docs.microsoft.com/intune/connect-intune-android-enterprise)해야 합니다.

#### <a name="ui-updates-for-apple-enrollment-and-enrollment-restrictions---4089575-4089579----"></a>Apple 등록 및 등록 제한 UI 업데이트 <!--4089575, 4089579  -->
다음 프로세스는 모두 마법사 스타일의 사용자 인터페이스를 사용합니다.
- Apple 디바이스 등록. 자세한 내용은 [Apple 디바이스 등록 프로그램을 통해 iOS 디바이스를 자동으로 등록](device-enrollment-program-enroll-ios.md)을 참조하세요.
- 등록 제한 만들기. 자세한 내용은 [등록 제한 설정](enrollment-restrictions-set.md)을 참조하세요.

#### <a name="handling-pre-configuration-of-corporate-device-identifiers-for-android-q-devices----4711509--idmiss---"></a>Android Q 디바이스의 회사 디바이스 식별자 사전 구성 처리 <!-- 4711509  idmiss -->
Google은 Android Q(v10)에서 레거시 관리형(디바이스 관리자) Android 디바이스의 MDM 에이전트가 디바이스 식별자 정보를 수집하는 기능을 제거할 예정입니다.  Intune에는 IT 관리자가 해당 디바이스를 자동으로 회사 소유로 태그 지정하기 위해 [디바이스 일련 번호 또는 IMEI 목록을 사전 구성](https://docs.microsoft.com/intune/corporate-identifiers-add#identify-corporate-owned-devices-with-imei-or-serial-number)할 수 있도록 지원하는 기능이 있습니다. 디바이스 관리자 관리형 Android Q 디바이스에서는 이 기능이 작동하지 않게 됩니다.  디바이스의 일련 번호와 IMEI 중 어느 것이 업로드되든 관계없이 Intune 등록 중에는 해당 디바이스가 항상 개인용으로 간주됩니다.  등록 후에 소유자를 회사로 수동 전환할 수 있습니다.  이 변경 사항은 새로운 등록에만 영향을 주며, 기존에 등록된 디바이스는 영향을 받지 않습니다.  회사 프로필로 관리되는 Android 디바이스는 이 변경 사항의 영향을 받지 않으며 계속해서 기존과 같이 작동합니다.  이에 더해, 디바이스 관리자로 등록된 Android Q 디바이스는 더 이상 Intune 콘솔에 일련 번호 또는 IMEI를 디바이스 속성으로 보고할 수 없게 됩니다.

#### <a name="icons-have-changed-for-android-enterprise-enrollments-work-profile-dedicated-devices-and-fully-managed-devices----4977730---"></a>Android 엔터프라이즈 등록(회사 프로필, 전용 디바이스 및 완전 관리형 디바이스) 아이콘 변경 <!-- 4977730 -->
Android 엔터프라이즈 등록 프로필 아이콘이 변경되었습니다. 새 아이콘을 보려면 **Intune** > **등록** > **Android 등록**으로 이동한 다음 **등록 프로필** 아래를 보세요.


#### <a name="windows-diagnostic-data-collection-change----4113859---"></a>Windows 진단 데이터 수집 변경 사항 <!-- 4113859 -->
Windows 10 버전 1903 이상을 실행하는 디바이스의 진단 데이터 수집 기본값이 변경되었습니다. Windows 10 1903부터 진단 데이터 수집이 기본적으로 활성화됩니다. Windows 진단 데이터는 Windows 디바이스에서 제공하는 디바이스 관련 및 Windows와 관련 소프트웨어의 성능 관련 중요한 기술 데이터입니다. 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)을 참조하세요. Autopilot 디바이스는 Autopilot 프로필에서 [System/AllowTelemetry](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)가 달리 설정되지 않은 한 “전체” 원격 분석으로 옵트인됩니다.

### <a name="device-management"></a>디바이스 관리

#### <a name="improve-device-location---3855417----"></a>디바이스 위치 개선<!-- 3855417  -->
**디바이스 찾기** 작업을 사용하여 디바이스의 정확한 좌표로 확대할 수 있습니다. 분실한 iOS 디바이스 찾기에 대한 자세한 내용은 [분실한 iOS 디바이스 찾기](device-locate.md)를 참조하세요.


### <a name="device-security"></a>디바이스 보안

#### <a name="advanced-settings-for-windows-defender-firewall--public-preview------1311949-------"></a>Windows Defender 방화벽의 고급 설정(공개 미리 보기)  <!--  1311949     -->  
Intune을 사용하여 디바이스 구성 프로필의 일부로서 Windows 10 엔드포인트 보호를 위해 [사용자 지정 방화벽 규칙을 관리](endpoint-protection-configure.md#add-custom-firewall-rules-for-windows-10-devices)할 수 있습니다. 규칙은 애플리케이션, 네트워크 주소 및 포트에 대한 인바운드 및 아웃바운드 동작을 지정할 수 있습니다. 

#### <a name="updated-ui-for-managing-security-baselines------4091125-------"></a>보안 기준 관리의 업데이트된 UI   <!-- 4091125     -->
Intune 콘솔의 보안 기준 [만들기 및 편집 환경](security-baselines.md#create-the-profile)이 업데이트되었습니다. 변경 사항에는 다음이 포함됩니다.

하나의 블레이드 안에서 단일 블레이드로 압축된 간단한 마법사 스타일 형식. 이 새로운 디자인에서는 IT 전문가가 몇 개의 개별 창을 드릴다운해야 했던 블레이드 확장이 사라졌습니다.  
이제 나중에 돌아가서 기준을 할당하는 대신 만들기 및 편집 환경의 일환으로 할당을 만들 수 있습니다. 새 기준을 만들거나 기존 기준을 편집하기 전에 볼 수 있는 설정 요약도 추가되었습니다. 편집할 때는 현재 편집 중인 속성 범주 내에 설정된 항목 목록의 요약만 표시됩니다.



<!-- ########################## -->

## <a name="week-of-july-15-2019"></a>2019년 7월 15일 주 

### <a name="app-management"></a>앱 관리

#### <a name="managed-home-screen-and-managed-settings-icons----4918107---"></a>Managed Home Screen 및 관리형 설정 아이콘 <!-- 4918107 -->
Managed Home Screen 앱 아이콘과 **관리형 설정** 아이콘이 업데이트되었습니다. Managed Home Screen 앱은 Intune에 AE(Android 엔터프라이즈) 전용 디바이스로 등록되었고 다중 앱 키오스크 모드로 실행되는 디바이스만 사용합니다. Managed Home Screen 앱에 대한 자세한 내용은 [Android 엔터프라이즈에 대해 Microsoft Managed Home Screen 앱 구성](app-configuration-managed-home-screen-app.md)을 참조하세요.

#### <a name="android-device-policy-on-android-enterprise-dedicated-devices----4918136---"></a>Android 엔터프라이즈 전용 디바이스의 Android 디바이스 정책 <!-- 4918136 -->
Managed Home Screen 앱의 디버그 화면에서 Android 디바이스 정책 애플리케이션에 액세스할 수 있습니다. Managed Home Screen 앱은 Intune에 AE(Android 엔터프라이즈) 전용 디바이스로 등록되었고 다중 앱 키오스크 모드로 실행되는 디바이스만 사용합니다. 자세한 내용은 [Android 엔터프라이즈에 대해 Microsoft Managed Home Screen 앱 구성](app-configuration-managed-home-screen-app.md)을 참조하세요.

#### <a name="ios-company-portal-updates----3902931---"></a>iOS 회사 포털 업데이트 <!-- 3902931 -->
기존 “i.manage.microsoft.com” 텍스트가 iOS 앱 관리 프롬프트의 회사 이름으로 대체됩니다. 예를 들어, 사용자가 회사 포털에서 iOS 앱을 설치하려고 시도하거나 사용자가 앱의 관리를 허용할 때 “i.manage.microsoft.com” 대신 회사 이름이 표시됩니다. 이 변경 사항은 향후 며칠에 걸쳐 점진적으로 모든 고객에게 적용될 예정입니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="manage-filevault-for-macos-------3858502--4557986--1210104----"></a>macOS용 FileVault 관리   <!--  3858502 + 4557986 + 1210104  -->
Intune을 사용하여 [macOS 디바이스의 FileVault 키 암호화를 관리](encrypt-devices.md)할 수 있습니다. 디바이스를 암호화하려면 엔드포인트 보호 디바이스 구성 프로필을 사용해야 합니다.

FileVault에 대한 Microsoft의 지원에는 암호화되지 않은 디바이스의 암호화, 디바이스 개인 복구 키의 에스크로, 개인 암호화 키의 자동 또는 수동 회전, 회사 디바이스의 키 검색이 포함됩니다. 최종 사용자는 회사 포털 웹 사이트를 사용하여 암호화된 디바이스의 개인 복구 키를 가져올 수도 있습니다. 

모든 디바이스 암호화 세부 정보를 한곳에서 볼 수 있도록 암호화 보고서에 BitLocker 정보에 더해 [FileVault 정보](encryption-monitor.md)도 표시됩니다. 

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-autopilot-reset-removes-the-devices-primary-user----4156123---"></a>Windows Autopilot 초기화 사용 시 디바이스의 기본 사용자가 제거됨 <!-- 4156123 -->
디바이스에서 Autopilot 초기화를 사용하면 디바이스의 기본 사용자가 제거됩니다. 초기화 후에 로그인하는 사용자가 기본 사용자로 설정됩니다. 이 기능은 향후 며칠에 걸쳐 점진적으로 모든 고객에게 선보일 예정입니다.

## <a name="week-of-july-8-2019"></a>2019년 7월 8일 주

### <a name="new-office-windows-and-onedrive-settings-in-windows-10-administrative-templates----3510695---"></a>Windows 10 관리 템플릿의 새로운 Office, Windows 및 OneDrive 설정 <!-- 3510695 -->

Intune에서 온-프레미스 그룹 정책 관리와 비슷한 관리 템플릿을 만들 수 있습니다(**디바이스 관리** > **프로필** > **프로필 만들기** > 플랫폼은 **Windows 10 이상** 선택 > 프로필 유형은 **관리 템플릿** 선택).

이 업데이트에는 템플릿에 추가할 수 있는 더 많은 Office, Windows 및 OneDrive 설정이 포함됩니다. 새로운 설정을 통해 이제 100% 클라우드 기반인 2500여 개의 설정을 구성할 수 있습니다.

이 기능에 대해 자세히 알아보려면 [Windows 10 템플릿을 사용하여 Intune에서 그룹 정책 설정 구성](administrative-templates-windows.md)을 참조하세요.

적용 대상: Windows 10 이상

## <a name="week-of-july-1-2019"></a>2019년 7월 1일 주 

### <a name="app-management"></a>앱 관리

#### <a name="aad-and-app-on-android-enterprise-devices----3574267---"></a>Android 엔터프라이즈 디바이스의 AAD 및 APP <!-- 3574267 -->
이제 완전 관리형 Android 엔터프라이즈 디바이스를 온보딩할 때 사용자는 새로운 디바이스 또는 초기화된 디바이스의 초기 설정 중에 AAD(Azure Active Directory)에 등록하게 됩니다. 이전에는 완전 관리형 디바이스의 설정이 완료된 후에 사용자가 Microsoft Intune 앱을 수동으로 실행해야 AAD 등록이 시작되었습니다. 이제는 초기 설정 후에 디바이스 홈페이지가 표시되면 디바이스가 등록됩니다.

AAD 업데이트에 더해, 이제 완전 관리형 Android 엔터프라이즈 디바이스에서 Intune APP(앱 보호 정책)가 지원됩니다. 이 기능은 점진적으로 적용될 예정입니다. 자세한 내용은 [Intune을 사용하여 Android 엔터프라이즈 디바이스에 관리형 Google Play 앱 추가](apps-add-android-for-work.md)를 참조하세요.

## <a name="week-of-june-24-2019"></a>2019년 6월 24일 주 

### <a name="app-management"></a>앱 관리

#### <a name="configure-which-browser-is-allowed-to-link-to-organization-data----3145939---"></a>조직 데이터에 연결할 수 있는 브라우저 구성 <!-- 3145939 -->
이제 Android 및 iOS 디바이스의 Intune APP(앱 보호 정책)를 사용하여 Intune Managed Browser 또는 Microsoft Edge뿐 아니라 특정 브라우저로도 조직 웹 링크를 전송할 수 있습니다.  APP에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

#### <a name="all-apps-page-identifies-onlineoffline-microsoft-store-for-business-apps--4089647---"></a>모든 앱 페이지에서 온라인/오프라인 비즈니스용 Microsoft 스토어 앱 식별<!--4089647 -->
이제 **모든 앱** 페이지에 MSFB(비즈니스용 Microsoft 스토어) 앱을 온라인 또는 오프라인 앱으로 식별하기 위한 레이블이 포함됩니다. 각 MSFB 앱에 이제 **Online** 또는 **Offline** 접미사가 포함됩니다. 앱 세부 정보 페이지에는 **라이선스 유형** 및 **디바이스 컨텍스트 설치 지원**(오프라인 라이선스 앱만 해당) 정보가 포함됩니다.

#### <a name="company-portal-app-on-windows-shared-devices---4393553---"></a>Windows 공유 디바이스의 회사 포털 앱 <!--4393553 -->
이제 사용자가 Windows 공유 디바이스에서 회사 포털 앱에 액세스할 수 있습니다. 최종 사용자의 디바이스 타일에 **공유** 레이블이 표시됩니다. 이 변경 사항은 Windows 회사 포털 앱 버전 10.3.45609.0 이상에 적용됩니다.

#### <a name="view-all-installed-apps-from-new-company-portal-web-page----4224326---"></a>새 회사 포털 웹 페이지에서 설치된 모든 앱 보기 <!-- 4224326 -->
회사 포털 앱 사이트의 새 **설치된 앱** 페이지에는 사용자의 디바이스에 설치된 모든 관리형 앱(필수 및 사용 가능)이 나열되어 있습니다. 할당 유형 외에도 사용자는 앱의 게시자, 게시된 날짜 및 현재 설치 상태를 볼 수 있습니다. 사용자가 필요로 하거나 사용할 수 있는 앱을 만들지 않은 경우, 회사 앱이 설치되지 않았다는 메시지가 표시됩니다. 웹에서 새 페이지를 보려면 [회사 포털 웹 사이트](https://portal.manage.microsoft.com)로 이동하여 **설치된 앱**을 클릭합니다.  

#### <a name="new-view-lets-app-users-see-all-managed-apps-installed-on-device----2352913---"></a>새 보기를 통해 앱 사용자가 디바이스에 설치된 관리형 앱을 볼 수 있습니다. <!-- 2352913 -->  
이제 Windows용 회사 포털은 사용자의 디바이스에 설치된 모든 관리형 앱(필수 및 사용 가능)을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수도 있습니다. 사용자가 필요로 하거나 사용할 수 있는 앱을 만들지 않은 경우, 회사 앱이 설치되지 않았다는 메시지가 표시됩니다. 새 보기를 확인하려면 회사 포털 탐색 창으로 이동하여 **앱** > **설치된 앱**을 선택합니다.    

### <a name="device-configuration"></a>디바이스 구성

#### <a name="configure-settings-for-kernel-extensions-on-macos-devices----2043024---"></a>macOS 디바이스에서 커널 확장에 대한 설정 구성 <!-- 2043024 -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택). 이 업데이트는 디바이스에서 커널 확장을 구성하고 사용할 수 있는 새 설정 그룹을 포함합니다. 특정 확장을 추가하거나 특정 파트너 또는 개발자의 모든 확장을 허용할 수 있습니다.

이 기능에 대해 자세히 알아보려면 [커널 확장 개요](kernel-extensions-overview-macos.md) 및 [커널 확장 설정](kernel-extensions-settings-macos.md)을 참조하세요.

적용 대상: macOS 10.13.2 이상

#### <a name="apps-from-the-store-only-setting-for-windows-10-devices-includes-more-configuration-options----2697002---"></a>Windows 10 디바이스에 대한 스토어 앱 전용 설정에 다른 구성 옵션 포함 <!-- 2697002 -->
Windows 디바이스에 대한 디바이스 제한 프로필을 만들 때 **스토어의 앱만** 설정을 사용하여 사용자가 Windows 앱 스토어에서만 앱을 설치하게 할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼용) > **디바이스 제한**(프로필 유형)). 이 업데이트에서는 더 많은 옵션을 지원하도록 이 설정이 확장되었습니다. 

새 설정을 보려면 [기능을 허용하거나 제한하는 Windows 10(이상) 디바이스 설정](device-restrictions-windows-10.md#app-store)으로 이동하세요.

적용 대상: Windows 10 이상

#### <a name="deploy-multiple-zebra-mobility-extensions-device-profiles-to-a-device-same-user-group-or-same-devices-group----4089955---"></a>여러 Zebra 모바일 확장 디바이스 프로필을 디바이스, 동일한 사용자 그룹 또는 동일한 디바이스 그룹에 배포 <!-- 4089955 -->
Intune에서는 디바이스 구성 프로필에서 Zebra MX(모바일 확장)를 사용하여 Intune에서 기본 제공하지 않는 Zebra 디바이스 설정을 사용자 지정할 수 있습니다. 현재는 한 디바이스에 한 프로필을 배포할 수 있습니다. 이 업데이트에서는 다음으로 여러 프로필을 배포할 수 있습니다.
- 동일한 사용자 그룹
- 동일한 디바이스 그룹
- 단일 디바이스

[Microsoft Intune에서 Zebra Mobility Extensions를 사용하여 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)는 Intune에서의 MX 사용 방법을 보여 줍니다.

적용 대상: Android

#### <a name="some-kiosk-settings-on-ios-devices-are-set-using-block-replacing-allow----4404075----"></a>iOS 디바이스에서 일부 키오스크 설정이 “허용”이 아닌 “차단”으로 설정됩니다. <!-- 4404075  -->
iOS 디바이스에서 디바이스 제한 프로필을 만들 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **키오스크**) **자동 잠금**, **벨소리 전환**, **화면 회전**, **화면 일시 중지 단추** 및 **볼륨 단추**를 설정합니다. 

이 업데이트에서는 값이 **차단**(기능 차단) 또는 **구성 안 함**(기능 허용)입니다. 설정을 보려면 [기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md#kiosk-supervised-only)으로 이동하세요. 

적용 대상: iOS

#### <a name="use-face-id-for-password-authentication-on-ios-devices----4490704---"></a>iOS 디바이스에서 암호 인증에 Face ID 사용 <!-- 4490704 -->
iOS 디바이스에 대한 디바이스 제한 프로필을 만들 때 지문을 암호에 사용할 수 있습니다. 이 업데이트에서는 지문 암호 설정에서 안면 인식도 사용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼은 **iOS** 선택 > 프로필 유형은 **디바이스 제한** 선택 > **암호**). 그 결과 다음과 같은 설정이 변경되었습니다.

- **지문 잠금 해제**가 이제 **Touch ID 및 Face ID 잠금 해제**가 됩니다.
- **지문 수정(감독 모드에서만 해당)** 이 이제 **Touch ID 및 Face ID 수정(감독 모드에서만 해당)** 이 됩니다.

Face ID는 iOS 11.0 이상에서 제공됩니다. 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md#password)으로 이동하세요.

적용 대상: iOS

#### <a name="restricting-gaming-and-app-store-features-on-ios-devices-is-now-dependent-on-ratings-region----4593948---"></a>iOS 디바이스에서 게임 및 App Store 기능을 제한할 때 등급 지역에 따라 달라짐 <!-- 4593948 -->
iOS 디바이스에서는 게임, App Store, 문서 보기 관련 기능을 허용하거나 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 형식) > **App Store, 문서 보기, 게임**). 또한 미국처럼 등급 지역을 선택할 수 있습니다. 

이 업데이트에서는 **앱** 기능이 **등급 지역**의 자식 요소가 되며 **등급 지역**에 따라 달라집니다. 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 디바이스 설정](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동하세요.

적용 대상: iOS

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-autopilot-support-for-hybrid-azure-ad-join----4809146--"></a>하이브리드 Azure AD 조인에 대한 Windows Autopilot 지원 <!-- 4809146-->
기존 디바이스에 대한 Windows Autopilot은 이제 기존의 Azure AD 조인 지원에 더해 하이브리드 Azure AD 조인을 지원합니다. 이 변경 사항은 Windows 10 버전 1809 이상 디바이스에 적용됩니다. 자세한 내용은 [기존 디바이스에 대한 Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/existing-devices)을 참조하세요.



### <a name="device-management"></a>디바이스 관리

#### <a name="see-the-security-patch-level-for-android-devices----4461911---"></a>Android 디바이스에 대한 보안 패치 수준 참조 <!-- 4461911 -->
이제 Android 디바이스에 대한 보안 패치 수준을 확인할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스** > **모든 디바이스** > 디바이스 선택 > **하드웨어**를 선택하세요.
패치 수준은 **운영 체제** 섹션에 나열되어 있습니다.

#### <a name="assign-scope-tags-to-all-managed-devices-in-a-security-group----3173810---"></a>보안 그룹의 모든 관리 디바이스에 범위 태그 할당 <!-- 3173810 -->
이제 보안 그룹에 범위 태그를 할당할 수 있으며 이 보안 그룹의 모든 디바이스가 해당 범위 태그에 연결됩니다. 이 그룹의 모든 디바이스에도 해당 범위 태그가 할당됩니다. 이 기능으로 설정된 범위 태그는 현재 디바이스 범위 태그 흐름으로 설정된 범위 태그를 덮어쓰게 됩니다. 자세한 내용은 [분산형 IT에 RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

### <a name="device-security"></a>디바이스 보안

#### <a name="use-keyword-search-with-security-baselines-------"></a>보안 기준에서 키워드 검색 사용 <!--  -->
[보안 기준 프로필](security-baselines.md#create-the-profile)을 만들거나 편집할 때 새로운 *검색* 창에서 키워드를 지정하여 사용 가능한 설정 그룹에서 검색 조건을 포함하는 설정 그룹을 필터링할 수 있습니다. 

#### <a name="the-security-baselines-feature-is-now-generally-available-----3785395---"></a>보안 기준 기능 일반 공급  <!-- 3785395 -->
**보안 기준** 기능의 미리 보기 단계가 종료되어 이제 일반 공급되었습니다.  즉, 이 기능은 프로덕션에서 사용 가능합니다. 단, 개별 기준 템플릿은 아직 미리 보기 상태일 수 있으며, 개별 일정에 따라 평가되어 일반 공급으로 릴리스됩니다.

#### <a name="the-mdm-security-baseline-template-is-now-generally-available------3794072-4217151--3534649---"></a>MDM 보안 기준 템플릿 일반 공급   <!-- 3794072, 4217151,  3534649 -->
MDM 보안 기준 템플릿의 미리 보기 단계가 종료되어 이제 일반 공급되었습니다. 일반 공급 템플릿은 **2019년 5월 MDM 보안 기준**입니다.  이는 미리 보기 버전에서의 업그레이드가 아닌 새 템플릿입니다.  새 템플릿이므로 [여기에 포함된 설정](security-baseline-settings-windows.md)을 검토한 다음 새 프로필을 만들어서 템플릿을 디바이스에 배포해야 합니다. 다른 보안 기준 템플릿은 아직 미리 보기 상태일 수 있습니다. 사용 가능한 기준 목록은 [사용 가능한 보안 기준](security-baselines.md#available-security-baselines)을 참조하세요.  

새 템플릿인 *2019년 5월 MDM 보안 기준* 템플릿은 개발 문서에서 최근 발표된 다음과 같은 두 가지 설정을 포함합니다.  
- 잠금 화면 위: 잠긴 화면에서 음성으로 앱 활성화  
- DeviceGuard: 디바이스의 다음 재부팅 시 VBS(가상화 기반 보안) 사용  

이에 더해, *2019년 5월 MDM 보안 기준*에는 새로 추가된 설정과 제거된 설정이 있으며, 한 가지 설정의 기본값이 변경되었습니다. 미리 보기에서 일반 공급으로의 상세한 변경 사항 목록을 보려면 **새 템플릿의 변경된 내용**을 참조하세요.

#### <a name="security-baseline-versioning-----3194322---"></a>보안 기준 버전 관리  <!-- 3194322 -->
Intune 보안 기준에서는 버전 관리가 지원됩니다. 따라서 각 보안 기준의 새로운 버전이 릴리스되면 처음부터 새 기준을 다시 만들고 배포하지 않고도 기존 보안 기준 프로필이 새 기준 버전을 사용하도록 업데이트할 수 있습니다. 이에 더해, Intune 콘솔에서 해당 기준을 사용하는 개별 프로필의 개수, 프로필이 사용하는 여러 기준 버전의 개수, 특정 보안 기준의 최신 릴리스 날짜 등 각 기준의 정보를 볼 수 있습니다.  자세한 내용은 **보안 기준**을 참조하세요.

#### <a name="the-use-security-keys-for-sign-in-setting-has-moved-----4501151---"></a>로그인 설정의 보안 사용 키가 이동됨  <!-- 4501151 -->
**로그인에 대해 보안 키 사용**이라는 이름의 ID 보호 디바이스 구성 설정이 *비즈니스용 Windows Hello 구성*의 하위 설정에서 최상위 수준 설정으로 이동되었습니다. 따라서 비즈니스용 Windows Hello의 사용을 활성화하지 않아도 언제든지 사용 가능합니다. 자세한 내용은 [ID 보호](identity-protection-windows-settings.md)를 참조하세요.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="new-permissions-for-assigned-group-admins------4504437-----"></a>할당된 그룹 관리자를 위한 새로운 권한   <!-- 4504437   -->
Intune에서 기본 제공되는 학교 관리자 역할이 이제 관리형 앱의 만들기, 읽기, 업데이트, 삭제(CRUD) 권한을 갖습니다. 즉, Intune for Education에서 그룹 관리자로 할당되면 이제 [기존 권한](https://docs.microsoft.com/intune-education/group-admin-delegate#group-admin-permissions)에 더해 iOS MDM Push Certificate, iOS MDM 서버 토큰 및 iOS VPP 토큰을 만들고, 보고, 업데이트하고, 삭제할 수 있습니다. 이러한 작업을 수행하려면 **테넌트 설정** > **iOS 디바이스 관리**로 이동하세요.  

#### <a name="applications-can-use-the-graph-api-to-call-read-operations-without-user-credentials----4655885---"></a>애플리케이션이 Graph API를 사용하여 사용자 자격 증명 없이 읽기 작업을 호출할 수 있음 <!-- 4655885 -->
애플리케이션이 사용자 자격 증명 없이 앱 ID를 통해 Intune Graph API 읽기 작업을 호출할 수 있습니다. Intune에 대해 Microsoft Graph API를 액세스하는 방법에 대한 자세한 내용은 [Working with Intune in Microsoft Graph](https://docs.microsoft.com/graph/api/resources/intune-graph-overview?view=graph-rest-1.0)(Microsoft Graph에서 Intune 사용)를 참조하세요.

#### <a name="apply-scope-tags-to-microsoft-store-for-business-apps----4392555---"></a>비즈니스용 Microsoft 스토어 앱에 범위 태그 적용 <!-- 4392555 -->
이제 비즈니스용 Microsoft 스토어 앱에 범위 태그를 적용할 수 있습니다. 범위 태그에 대한 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](scope-tags.md)을 참조하세요.

## <a name="week-of-june-17-2019"></a>2019년 6월 17일 주 

### <a name="app-management"></a>앱 관리

#### <a name="new-features-in-microsoft-intune-app"></a>Microsoft Intune 앱의 새로운 기능
Android용 Microsoft Intune 앱(미리 보기)에 새로운 기능을 추가했습니다. 이제 완전 관리형 Android 디바이스의 사용자는 다음을 수행할 수 있습니다.  

* Intune 회사 포털 또는 Microsoft Intune 앱을 통해 등록한 디바이스를 보고 관리합니다.    
* 해당 조직에 지원을 문의합니다.    
* Microsoft에 피드백을 보냅니다.    
* 조직에서 설정한 사용 약관을 봅니다.    

## <a name="week-of-june-10-2019"></a>2019년 6월 10일 주 

### <a name="app-management"></a>앱 관리

#### <a name="new-sample-apps-showing-intune-sdk-integration-available-on-github----2653471---"></a>GitHub에서 사용할 수 있는 Intune SDK 통합을 표시하는 새로운 샘플 앱 <!-- 2653471 -->
msintuneappsdk GitHub 계정에서 iOS(Swift), Android, Xamarin.iOS, Xamarin Forms 및 Xamarin.Android용 새 샘플 애플리케이션을 추가했습니다. 이러한 앱은 기존 설명서를 보완하고 Intune 앱 SDK를 사용자 모바일 앱에 통합하는 방법을 보여 주기 위한 것입니다. Intune SDK에 대한 추가 지침이 필요한 앱 개발자는 다음의 연결된 샘플을 참조하세요.
- [Chatr](https://github.com/msintuneappsdk/Chatr-Sample-Intune-iOS-App) - 조정된 인증에 ADAL(Azure Active Directory 인증 라이브러리)을 사용하는 네이티브 iOS(Swift) 인스턴트 메시징 앱입니다.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Android-App) - 조정된 인증에 ADAL을 사용하는 네이티브 Android 할일 목록 앱입니다.
- [Taskr](https://github.com/msintuneappsdk/Taskr-Sample-Intune-Xamarin-Android-Apps) - 조정된 인증에 ADAL을 사용하는 Xamarin.Android 할일 목록 앱입니다. 이 리포지토리에는 Xamarin.Forms 앱도 있습니다.
- [Xamarin.iOS 샘플 앱](https://github.com/msintuneappsdk/sample-intune-xamarin-ios) - 기본 Xamarin.iOS 샘플 앱입니다.

## <a name="week-of-may-27-2019"></a>2019년 5월 27일 주 

### <a name="app-management"></a>앱 관리

#### <a name="reporting-for-potentially-harmful-apps-on-android-devices----4223162---"></a>Android 디바이스에서 잠재적으로 유해한 앱 보고 <!-- 4223162 -->
Intune은 이제 Android 디바이스에서 잠재적으로 유해한 앱에 대한 정보를 제공합니다. 

## <a name="week-of-may-20-2019"></a>2019년 5월 20일 주 

### <a name="app-management"></a>앱 관리

#### <a name="windows-company-portal-app----3316993---"></a>Windows 회사 포털 앱 <!-- 3316993 -->
이제 Windows 회사 포털 앱에 **디바이스**로 레이블이 지정된 새 페이지가 생깁니다. **디바이스** 페이지는 최종 사용자에게 등록된 모든 디바이스를 보여줍니다. 사용자는 버전 10.3.4291.0 이상을 사용할 때 회사 포털에서 이 변경 사항을 볼 수 있습니다. 회사 포털 구성에 대한 정보는 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="autopilot-device-orderid-attribute-name-changed-to-group-tag----4659453---"></a>Autopilot 디바이스 OrderID 특성 이름이 그룹 태그로 변경됨 <!-- 4659453 -->

더 직관적이 되도록 Autopilot 디바이스의 **OrderID** 특성 이름이 **그룹 태그**로 변경되었습니다. CSV를 사용하여 Autopilot 디바이스 정보를 업로드하는 경우 OrderID가 아닌 열 머리글로 그룹 태그를 사용해야 합니다.  

## <a name="week-of-may-13-2019"></a>2019년 5월 13일 주 

### <a name="app-management"></a>앱 관리

#### <a name="intune-policies-update-authentication-method-and-company-portal-app-installation-----1927359----"></a>Intune 정책에서 인증 방법 및 회사 포털 앱 설치를 업데이트함  <!-- 1927359  -->
Apple의 회사 디바이스 등록 방법 중 하나를 통해 설정 도우미에서 이미 등록한 디바이스에서는 최종 사용자가 앱 스토어에서 회사 포털 앱을 수동으로 설치하는 경우 Intune은 더 이상 해당 회사 포털 앱을 지원하지 않습니다. 이 변경은 등록 중에 Apple 설정 도우미로 인증하는 경우에만 적용됩니다. 또한 이 변경은 다음을 통해 등록된 iOS 디바이스에만 영향을 줍니다.  
* Apple Configurator

* Apple Business Manager

* Apple School Manager

* Apple DEP(장비 등록 프로그램)

사용자가 App Store에서 회사 포털 앱을 설치한 다음, 이 앱을 통해 이러한 디바이스를 등록하는 경우 오류가 발생합니다. 이 디바이스는 등록 중에 Intune에서 자동으로 푸시된 경우에만 회사 포털을 사용해야 합니다. Azure Portal에서 Intune의 등록 프로필이 업데이트되므로 디바이스 인증 방법 및 디바이스가 회사 포털 앱을 받는 방법을 지정할 수 있습니다. DEP 디바이스 사용자가 회사 포털을 사용하도록 하려면 등록 프로필에서 기본 설정을 지정해야 합니다. 

또한 iOS 회사 포털 앱에서 **디바이스 식별** 화면이 제거될 예정입니다. 따라서 조건부 액세스를 사용하거나 회사 앱을 배포하려는 관리자는 DEP 등록 프로필을 업데이트해야 합니다. 이 요구 사항은 DEP 등록이 설정 도우미에서 인증된 경우에만 적용됩니다. 이러한 경우 디바이스에 회사 포털을 푸시해야 합니다. 이렇게 하려면 **Intune** > **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰**을 선택하고 토큰 > **프로필**을 선택한 후 프로필 > **속성**을 선택하고 **회사 포털 설치**를 **예**로 설정합니다.

이미 등록된 DEP 디바이스에 회사 포털을 설치하려면 Intune > 클라이언트 앱으로 이동하고 앱 구성 정책을 사용하여 이 앱을 관리형 앱으로 푸시해야 합니다. 

#### <a name="configure-how-end-users-update-a-line-of-business-lob-app-using-an-app-protection-policy----3568384---"></a>최종 사용자가 앱 보호 정책을 사용하여 LOB(기간 업무) 앱을 업데이트하는 방법 구성 <!-- 3568384 -->
이제 최종 사용자가 LOB(기간 업무) 앱의 업데이트된 버전을 다운로드할 수 있는 위치를 구성할 수 있습니다. 최종 사용자는 **최소 앱 버전** 조건부 시작 대화 상자에서 이 기능을 사용할 수 있습니다. 이 대화 상자는 최종 사용자에게 최소 버전의 LOB 앱으로 업데이트할지 묻는 메시지를 표시합니다. LOB APP(앱 보호 정책)의 일부로 이러한 업데이트 세부 정보를 제공해야 합니다. 이 기능은 iOS 및 Android에서 사용할 수 있습니다. iOS에서 이 기능을 사용하려면 앱을 iOS용 Intune SDK v. 10.0.7 이상과 통합(또는 래핑 도구를 사용하여 래핑)해야 합니다. Android에서 이 기능을 사용하려면 최신 회사 포털이 필요합니다. 최종 사용자가 LOB 앱을 업데이트하는 방법을 구성하려면 앱에 관리형 앱 구성 정책과 키 `com.microsoft.intune.myappstore`가 함께 전송되어야 합니다. 전송된 값은 최종 사용자가 앱을 다운로드할 스토어를 정의합니다. 회사 포털을 통해 앱을 배포한 경우 값은 `CompanyPortal`이어야 합니다. 다른 스토어의 경우에는 전체 URL을 입력해야 합니다.

#### <a name="intune-management-extension-powershell-scripts-----3734186----"></a>Intune 관리 확장 PowerShell 스크립트  <!-- 3734186  -->
디바이스에서 사용자의 관리자 권한으로 실행하도록 PowerShell 스크립트를 구성할 수 있습니다. 자세한 내용은 [Intune에서 Windows 10 디바이스에 PowerShell 스크립트 사용](intune-management-extension.md) 및 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

#### <a name="android-enterprise-app-management----4459905---"></a>Android Enterprise 앱 관리 <!-- 4459905 -->
IT 관리자가 Android Enterprise 관리를 보다 쉽게 구성하고 사용하도록 하기 위해 Intune에서는 일반적인 Android Enterprise 관련 앱을 Intune 관리 콘솔에 추가합니다. 다음과 같은 4개의 Android 엔터프라이즈 앱이 있습니다.

- **[Microsoft Intune](https://play.google.com/store/apps/details?id=com.microsoft.intune)** - Android Enterprise완전 관리형 시나리오에 사용합니다.
- **[Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator)** -2단계 인증을 사용하는 경우 계정에 로그인할 수 있도록 지원합니다.
- **[Intune 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)** - APP(앱 보호 정책) 및 Android Enterprise 작업 프로필 시나리오에 사용합니다.
- [관리형 홈 화면](https://play.google.com/store/apps/details?id=com.microsoft.launcher.enterprise) -Android Enterprise 전용/키오스크 시나리오에 사용합니다.

이전에는 IT 관리자가 설치 중에 이러한 앱을 [관리형 Google Play 스토어](https://play.google.com/store/apps)에서 수동으로 찾아서 승인해야 했습니다. 이와 같이 변경되어 이전의 수동 단계가 필요하지 않으므로 고객은 Android Enterprise 관리를 보다 쉽고 빠르게 사용할 수 있습니다.

관리자가 해당 Intune 테넌트를 관리형 Google Play에 먼저 연결하면 해당 Intune 앱 목록에 이러한 4개의 앱이 자동으로 추가됩니다. 자세한 내용은 [Intune 계정을 관리형 Google Play 계정에 연결](connect-intune-android-enterprise.md)을 참조하세요. 이미 해당 테넌트를 연결했거나 Android Enterprise를 이미 사용하고 있는 테넌트의 경우 관리자가 수행해야 할 작업이 없습니다. 이러한 4개 앱은 2019년 5월에 서비스 출시가 완료되면 7일 이내에 자동으로 표시됩니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune-----1533038---"></a>업데이트된 Microsoft Intune용 PFX 인증서 커넥터  <!-- 1533038 -->
기존 PFX 인증서가 계속 재처리되는 문제를 해결하는 [Microsoft Intune용 PFX 인증서 커넥터](certficates-pfx-configure.md#whats-new-for-connectors)에 대한 업데이트를 릴리스했습니다. 이로 인해 커넥터가 새 요청 처리를 중지하게 됩니다.

#### <a name="intune-security-tasks-for-defender-atp-in-public-preview--------3208597---"></a>Defender ATP에 대한 Intune 보안 작업(공개 미리 보기로 제공)     <!-- 3208597 -->
공개 미리 보기에서 Intune을 사용하여 [Microsoft Defender ATP(Advanced Threat Protection)의 보안 작업](atp-manage-vulnerabilities.md)을 관리할 수 있습니다. 이와 같이 ATP와 통합되면 검색부터 문제 완화까지의 기간을 단축하면서 엔드포인트 취약성 및 구성 오류를 검색하고, 우선 순위를 지정하고, 수정할 수 있는 위험 기반 접근 방식이 추가됩니다.

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---idstaged--"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인 <!-- 3617671   idstaged-->
많은 Windows 10 이상 디바이스에는 TPM(신뢰할 수 있는 플랫폼 모듈) 칩셋이 있습니다. 이 업데이트는 디바이스에서 TPM 칩 버전을 확인하는 새 규정 준수 설정을 포함 합니다. 

[Windows 10 이상 규정 준수 정책 설정](compliance-policy-create-windows.md#device-security)에서 이 설정을 설명합니다.

적용 대상: Windows 10 이상

#### <a name="prevent-end-users-from-modifying-their-personal-hotspot-and-disable-siri-server-logging-on-ios-devices----4097904-----"></a>최종 사용자가 개인 핫스폿을 수정하지 못하게 하고 iOS 디바이스에서 Siri 서버 로깅을 사용하지 않음 <!-- 4097904   -->  
iOS 디바이스에서 디바이스 제한 프로필을 만듭니다[**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 사용자가 구성할 수 있는 다음과 같은 새 설정을 포함합니다.

- **기본 제공 앱** Siri용 서버 쪽 로깅 명령
- **무선**: 개인 핫스폿의 사용자 수정(감독 모드에서만 해당)

이러한 설정을 보려면 [iOS용 기본 제공 앱 설정](device-restrictions-ios.md#built-in-apps) 및 [iOS용 무선 설정](device-restrictions-ios.md#wireless)로 이동합니다.

적용 대상: iOS 12.2 이상

#### <a name="new-classroom-app-device-restriction-settings-for-macos-devices----4097905-----"></a>macOS 디바이스에 대한 새로운 강의식 앱 디바이스 제한 설정 <!-- 4097905   --> 
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다[**디바이스 구성** > **프로필** > **프로필 만들기**  >  **macOS**(플랫폼) > **디바이스 제한**(프로필 유형)]. 이 업데이트는 새로운 강의실 앱 설정, 스크린샷을 차단하는 옵션, iCloud 사진 라이브러리를 사용하지 않도록 설정하는 옵션을 포함합니다.

현재 설정을 확인하려면 [Intune을 사용하여 기능을 허용하거나 제한하는 macOS 디바이스 설정](device-restrictions-macos.md)으로 이동하세요.

적용 대상: macOS

#### <a name="the-ios-password-to-access-app-store-setting-is-renamed---4557891----"></a>앱 스토어 설정에 액세스하기 위한 iOS 암호 이름이 바뀜<!-- 4557891  -->
**앱 스토어에 액세스하는 데 사용할 암호** 설정 이름이 **모든 구매에 iTunes Store 암호 필요**(**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS**(플랫폼의 경우) > **디바이스 제한**(프로필 유형의 경우) > **앱 스토어, 문서 보기 및 게임**)로 바뀌었습니다.

사용 가능한 설정을 보려면 [App Store, 문서 보기, 게임 iOS 설정](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동합니다.

적용 대상: iOS

#### <a name="microsoft-defender-advanced-threat-protection--baseline--preview------3754134---"></a>Microsoft Defender Advanced Threat Protection 기준(미리 보기)  <!--  3754134 -->
[Microsoft Defender Advanced Threat Protection](security-baseline-settings-defender-atp.md)의 보안 기준 미리 보기 설정을 추가했습니다. 사용자의 환경이 [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) 사용에 대한 필수 조건을 충족하는 경우 이 기준을 사용할 수 있습니다.

### <a name="device-enrollment"></a>디바이스 등록

#### <a name="windows-enrollment-status-page-esp-is-now-generally-available----3605348---"></a>Windows ESP(등록 상태 페이지)가 일반 공급됨 <!-- 3605348 -->
등록 상태 페이지는 이제 미리 보기가 아닙니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.


#### <a name="intune-user-interface-update---autopilot-enrollment-profile-creation-----4593669---"></a>Intune 사용자 인터페이스 업데이트 - Autopilot 등록 프로필 만들기  <!-- 4593669 -->
Autopilot 등록 프로필을 만들기 위한 사용자 인터페이스가 Azure 사용자 인터페이스 스타일에 맞게 업데이트되었습니다. 자세한 내용은 [Autopilot 등록 프로필 만들기](https://docs.microsoft.com/intune/enrollment-autopilot#create-an-autopilot-deployment-profile)를 참조하세요. 앞으로는 추가 Intune 시나리오가 이 새 UI 스타일으로 업데이트됩니다.

#### <a name="enable-autopilot-reset-for-all-windows-devices----4225665---"></a>모든 Windows 디바이스에 대해 Autopilot 재설정 사용 <!-- 4225665 -->
Autopilot 재설정 기능은 등록 상태 페이지를 사용하도록 구성되지 않은 경우를 비롯한 모든 Windows 디바이스에 작동합니다. 등록 상태 페이지가 초기 디바이스 등록 중에 디바이스에 맞게 구성되지 않았으므로 디바이스는 로그인 후 바로 바탕 화면을 표시합니다. 동기화가 수행되고 Intune에서 준수 상태로 나타날 때까지 최대 8시간이 걸릴 수 있습니다. 자세한 내용은 [원격 Windows Autopilot 재설정으로 디바이스 재설정](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-reset-remote)을 참조하세요.

#### <a name="exact-imei-format-not-required-when-searching-all-devices---30407680---"></a>모든 디바이스를 검색하는 경우 정확한 IMEI 형식이 필요하지 않음 <!--30407680 -->
**모든 디바이스**를 검색할 때 IMEI 번호에 공백을 포함하지 않아도 합니다.

#### <a name="deleting-a-device-in-the-apple-portal-will-be-reflected-in-the-intune-portal---2489996---"></a>Apple 포털에서 디바이스를 삭제하면 Intune 포털에도 반영됩니다. <!--2489996 -->
Apple의 디바이스 등록 프로그램 또는 Apple 비즈니스 관리자 포털에서 디바이스를 삭제하면 다음 동기화 중에 Intune에서도 자동으로 삭제됩니다.

### <a name="the-enrollment-status-page-now-tracks-win32-apps----2714451---"></a>등록 상태 페이지에서 이제 Win32 앱 추적 <!-- 2714451 -->
Windows 10 버전 1903 이상을 실행하는 디바이스에만 해당됩니다. 자세한 내용은 [등록 상태 페이지 설정](windows-enrollment-status.md)을 참조하세요.

### <a name="device-management"></a>디바이스 관리

#### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API를 사용하여 디바이스를 대량으로 다시 설정하고 초기화 <!-- 3295288 -->
이제 Graph API를 사용하여 최대 100대의 디바이스를 대량으로 다시 설정하고 초기화할 수 있습니다.


### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="the-encryption-report-is-out-of-public-preview------4587546--------"></a>암호화 보고서가 공개 미리 보기에서 제외됨   <!-- 4587546      -->
[BitLocker 및 디바이스 암호화 보고서](encryption-monitor.md)는 이제 일반 공급되며, 더 이상 공개 미리 보기에 포함되지 않습니다. 

<!-- ########################## -->

#### <a name="outlook-signature-and-biometric-settings-for--ios-and-android-devices----4050557---"></a>iOS 및 Android 디바이스에 대한 Outlook 서명 및 생체 인식 설정 <!-- 4050557 -->
이제 iOS 및 Android 디바이스의 Outlook에서 기본 서명을 사용하도록 설정할지 여부를 지정할 수 있습니다. 또한 사용자가 iOS에서 Outlook의 생체 인식 설정을 변경할 수 있도록 선택할 수 있습니다.

## <a name="week-of-may-6-2019"></a>2019년 5월 6일 주 

### <a name="device-configuration"></a>디바이스 구성

#### <a name="network-access-control-nac-support-for-f5-access-for-ios-devices----4500808---"></a>iOS 디바이스용 F5 Access에 대한 NAC(네트워크 액세스 제어) 지원 <!-- 4500808 -->

F5는 Intune의 iOS에서 F5 Access를 위한 NAC 기능을 허용하는 BIG-IP 13 업데이트를 릴리스했습니다. 이 기능을 사용하려면

- BIG-IP를 13.1.1.5 새로 고침으로 업데이트합니다. BIG-IP 14는 지원되지 않습니다.
- BIG-IP와 NAC용 Intune을 통합하세요. [개요: 개요: 엔드포인트 관리 시스템을 사용하여 디바이스 상태 검사를 위한 APM 구성](https://techdocs.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html)의 단계.
- Intune의 VPN 프로필에서 **NAC(네트워크 액세스 제어) 사용** 설정을 확인합니다.

사용 가능한 설정을 보려면 [iOS 디바이스에서 VPN 설정 구성](vpn-settings-ios.md)으로 이동합니다.

적용 대상: iOS

#### <a name="updated-pfx-certificate-connector-for-microsoft-intune----doc-vso-1521237----"></a>업데이트된 Microsoft Intune용 PFX 인증서 커넥터 <!-- doc-vso 1521237  -->  
폴링 간격을 5분에서 30초로 낮추는 [Microsoft Intune용 PFX 인증서 커넥터](certficates-pfx-configure.md#whats-new-for-connectors)에 대한 업데이트를 릴리스했습니다.

## <a name="week-of-april-22-2019"></a>2019년 4월 22일 주

### <a name="use-compliance-manager-to-create-assessments-for-microsoft-intune---4404750---"></a>Compliance Manager를 사용하여 Microsoft Intune에 대한 평가 만들기<!-- 4404750 -->

[Compliance Manager](https://servicetrust.microsoft.com/ComplianceManager)(다른 Microsoft 사이트 열기)는 Microsoft Service Trust Portal의 워크플로 기반 위험 평가 도구입니다. 이를 통해 Microsoft 서비스와 관련된 조직의 규정 준수 활동을 추적, 할당 및 확인할 수 있습니다. Office 365, Azure, Dynamics, 전문 서비스 및 Intune을 통해 사용자 고유의 규정 준수 평가를 만들 수 있습니다. Intune에는 FFIEC와 GDPR의 두 가지 평가가 있습니다.

Compliance Manager는 Microsoft에서 관리하는 컨트롤과 조직에서 관리하는 컨트롤을 세분화하여 노력을 집중시키는 데 도움이 됩니다. 평가를 완료한 다음, 해당 평가를 내보내고 인쇄할 수 있습니다.

[FFIEC(연방 금융 기관 심사 위원회)](https://www.microsoft.com/trustcenter/compliance/FFIEC)(다른 Microsoft 사이트 열기) 규정 준수는 FFIEC에서 발표한 온라인 뱅킹 표준 세트입니다. 이는 Intune을 사용하는 금융 기관에 대해 가장 많이 요청되는 평가입니다. Intune에서 퍼블릭 클라우드 워크로드와 관련된 FFIEC 사이버 보안 지침을 충족시키는 방법을 해석합니다. Intune의 FFIEC 평가는 Compliance Manager의 두 번째 FFIEC 평가입니다.

다음 예에서는 FFIEC 컨트롤에 대한 분석을 볼 수 있습니다. Microsoft에서 64개의 컨트롤을 담당하며, 사용자는 나머지 12개의 컨트롤을 담당하고 있습니다.

![FFIEC에 대한 Intune 평가 샘플 참조(고객 작업 및 Microsoft 작업 포함)](./media/intune-ffiec-assessment-status.png)

[GDPR(일반 데이터 보호 규정)](https://www.microsoft.com/trustcenter/privacy/gdpr/gdpr-overview)(다른 Microsoft 사이트 열기)은 개인과 해당 데이터의 권한을 보호하는 데 도움이 되는 EU(유럽 연합) 법률입니다. GDPR은 개인 정보 보호 규정을 준수하도록 지원하기 위해 가장 많이 요청되는 평가입니다. 

다음 예에서는 GDPR 컨트롤에 대한 분석을 볼 수 있습니다. Microsoft에서 49개의 컨트롤을 담당하며, 사용자는 나머지 66개의 컨트롤을 담당하고 있습니다.

![GDPR에 대한 Intune 평가 샘플 참조(고객 작업 및 Microsoft 작업 포함)](./media/intune-assessment-status.png)

## <a name="week-of-april-15-2019"></a>2019년 4월 15일 주

### <a name="app-management"></a>앱 관리

#### <a name="openssl-encryption-for-android-app-protection-policies----3747362---"></a>Android 앱 보호 정책에 대한 OpenSSL 암호화 <!-- 3747362 -->
Android 디바이스의 Intune APP(앱 보호 정책)는 이제 FIPS 140-2 준수 OpenSSL 암호화 라이브러리를 사용합니다. 자세한 내용은 [Microsoft Intune의 Android 앱 보호 정책 설정](app-protection-policy-settings-android.md)의 [암호화](app-protection-policy-settings-android.md#encryption) 섹션을 참조하세요.

#### <a name="enable-win32-app-dependencies----2617348----"></a>Win32 앱 종속성 사용 <!-- 2617348  -->
관리자는 Win32 앱을 설치하기 전에 다른 앱이 종속성으로 설치되도록 요구할 수 있습니다. 특히 디바이스는 Win32 앱을 설치하기 전에 종속 앱을 설치해야 합니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 **앱 추가** 블레이드를 표시합니다. **앱 유형**으로 **Windows 앱(Win32)** 을 선택합니다. 앱이 추가되면 **종속성**을 선택하여 Win32 앱을 설치하기 전에 설치해야 하는 종속 앱을 추가할 수 있습니다. 자세한 내용은 [Intune 독립 실행형 - Win32 앱 관리](apps-win32-app-management.md)를 참조하세요. 

#### <a name="app-version-installation-information-for-microsoft-store-for-business-apps----3537391-----"></a>비즈니스용 Microsoft Store 앱에 대한 앱 버전 설치 정보 <!-- 3537391   -->
앱 설치 보고서에는 비즈니스용 Microsoft Store 앱에 대한 앱 버전 정보가 포함되어 있습니다. Intune에서 **클라이언트 앱** > **앱**을 차례로 선택합니다. **비즈니스용 Microsoft Store 앱**을 선택한 다음, **모니터** 섹션 아래에서 **디바이스 설치 상태**를 선택합니다.

#### <a name="additions-to-win32-apps-requirement-rules----3676883-----"></a>Win32 앱 요구 사항 규칙 추가 <!-- 3676883   -->
PowerShell 스크립트, 레지스트리 값 및 파일 시스템 정보를 기반으로 하여 요구 사항 규칙을 만들 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. 그런 다음, **앱 추가** 블레이드에서 **앱 유형**으로 **Windows 앱(Win32)** 을 선택합니다.  **요구 사항** > **추가**를 차례로 선택하여 추가 요구 사항 규칙을 구성합니다. 그런 다음, **요구 사항 유형**으로 **파일 형식**, **레지스트리** 또는 **스크립트**를 선택합니다. 자세한 내용은 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

#### <a name="configure-your-win32-apps-to-be-installed-on-intune-enrolled-azure-ad-joined-devices----3695227----"></a>Intune에 등록된 Azure AD 조인 디바이스에 설치되도록 Win32 앱 구성 <!-- 3695227  -->
Intune에 등록된 Azure AD 조인 디바이스에 설치할 Win32 앱을 할당할 수 있습니다. Intune의 Win32 앱에 대한 자세한 내용은 [Win32 앱 관리](apps-win32-app-management.md)를 참조하세요.

#### <a name="device-overview-shows-primary-user---3794259----"></a>디바이스 개요에 기본 사용자가 표시됨 <!--3794259  -->
디바이스 개요 페이지에는 UDA(사용자 디바이스 선호도) 사용자라고도 하는 기본 사용자가 표시됩니다. 디바이스에 대한 기본 사용자를 보려면 **Intune** > **디바이스** > **모든 디바이스**를 차례로 선택한 다음, 디바이스를 선택합니다. 기본 사용자가 **개요**페이지의 위쪽에 표시됩니다.

#### <a name="additional-managed-google-play-app-reporting-for-android-enterprise-work-profile-devices----4105925----"></a>관리형 Google Play 앱에서 Android Enterprise 작업 프로필 디바이스에 대한 추가 보고 <!-- 4105925  -->
Android Enterprise 작업 프로필 디바이스에 배포된 관리형 Google Play 앱의 경우 디바이스에 설치된 앱의 특정 버전 번호를 볼 수 있습니다. 이는 필수 앱에만 적용됩니다.  

#### <a name="ios-third-party-keyboards----4111843-----"></a>iOS 타사 키보드 <!-- 4111843   -->
**타사 키보드** 설정에 대한 Intune APP(앱 보호 정책) 지원은 iOS 플랫폼 변경으로 인해 종료되었습니다. Intune Admin Console에서 이 설정을 구성할 수 없으며 Intune App SDK의 클라이언트에 적용할 수 없습니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="set-login-settings-and-control-restart-options-on-macos-devices----1210083----"></a>macOS 디바이스에서 로그인 설정 지정 및 다시 시작 옵션 제어 <!-- 1210083  -->
macOS 디바이스에서 디바이스 구성 프로필을 만들 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** 선택 > 프로필 유형에 대해 **디바이스 기능** 선택). 이 업데이트에는 사용자 지정 배너 표시, 사용자 로그인 방법 선택, 전원 설정 표시 또는 숨기기 등과 같은 새 로그인 창 설정이 포함되어 있습니다.

이러한 설정을 보려면 [macOS 디바이스 기능 설정](macos-device-features-settings.md)으로 이동하세요.

#### <a name="configure-wifi-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode---3041940----"></a>다중 앱 키오스크 모드로 실행되는 Android Enterprise 디바이스 소유자 전용 디바이스에서 WiFi 구성 <!--3041940  -->
다중 앱 키오스크 모드에서 전용 디바이스로 실행 중일 때 Android Enterprise, 디바이스 소유자에서 설정을 사용하도록 설정할 수 있습니다. 이 업데이트에서는 사용자가 WiFi 네트워크를 구성하고 연결할 수 있도록 설정할 수 있습니다(**Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자만, 디바이스 제한** > **전용 디바이스** > **키오스크 모드**: **다중 앱** > **WiFi 구성**). 

구성할 수 있는 모든 설정을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상: 다중 앱 키오스크 모드로 실행되는 Android Enterprise 전용 디바이스


#### <a name="configure-bluetooth-and-pairing-on-android-enterprise-device-owner-dedicated-devices-running-in-multi-app-kiosk-mode----3041941----"></a>다중 앱 키오스크 모드로 실행되는 Android Enterprise 디바이스 소유자 전용 디바이스에서 Bluetooth 및 페어링 구성 <!-- 3041941  -->
다중 앱 키오스크 모드에서 전용 디바이스로 실행 중일 때 Android Enterprise, 디바이스 소유자에서 설정을 사용하도록 설정할 수 있습니다. 이 업데이트에서는 최종 사용자가 Bluetooth를 사용하도록 설정하고 Bluetooth를 통해 디바이스를 페어링하도록 허용할 수 있습니다(**Intune** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자만, 디바이스 제한** > **전용 디바이스** > **키오스크 모드**: **다중 앱** > **Bluetooth 구성**). 

구성할 수 있는 모든 설정을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상: 다중 앱 키오스크 모드로 실행되는 Android Enterprise 전용 디바이스

#### <a name="create-and-use-oemconfig-device-configuration-profiles-in-intune----3305883----"></a>Intune에서 OEMConfig 디바이스 구성 프로필 만들기 및 사용 <!-- 3305883  -->
이 업데이트에서 Intune은 OEMConfig를 사용하여 Android Enterprise 디바이스를 구성할 수 있도록 지원합니다. 특히 OEMConfig를 사용하여 디바이스 구성 프로필을 만들고, 설정을 Android Enterprise 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise**).

OEM 지원은 현재 OEM별로 제공됩니다. OEMConfig 앱 목록에서 원하는 OEMConfig 앱을 사용할 수 없는 경우 `IntuneOEMConfig@microsoft.com`에 문의하세요.

이 기능에 대한 자세한 내용을 알아보려면 [Microsoft Intune에서 OEMConfig를 사용하여 Android Enterprise 디바이스 사용 및 관리](android-oem-configuration-overview.md)로 이동하세요.

적용 대상: Android 엔터프라이즈

#### <a name="windows-update-notifications-----3316758-3316782----"></a>Windows 업데이트 알림  <!-- 3316758, 3316782  -->
Intune 콘솔에서 관리할 수 있는 두 가지 *사용자 환경 설정*이 Windows 업데이트 링 구성에 추가되었습니다. 이제 다음을 수행할 수 있습니다.
- 사용자의 [Windows 업데이트 검사](windows-update-settings.md)를 차단하거나 허용합니다.
- 사용자에게 표시되는 [Windows 업데이트 알림 수준](windows-update-settings.md)을 관리합니다.

#### <a name="new-device-restriction-settings-for-android-enterprise-device-owner----3574254----"></a>Android Enterprise 디바이스 소유자용 새 디바이스 제한 설정 <!-- 3574254  -->
Android Enterprise 디바이스에서 디바이스 제한 프로필을 만들어 기능을 허용하거나 제한하고, 암호 규칙을 설정하는 등의 작업을 수행할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** 선택 > 프로필 유형에 대해 **디바이스 소유자만 > 디바이스 제한** 선택). 

이 업데이트에는 새 암호 설정, Google Play 스토어에서의 완전 관리형 디바이스용 앱에 대한 전체 액세스 허용 등이 포함되어 있습니다. 현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다. 

적용 대상: Android Enterprise 완전 관리형 디바이스

#### <a name="check-for-a-tpm-chipset-in-a-windows-10-device-compliance-policy----3617671---"></a>Windows 10 디바이스 준수 정책에서 TPM 칩셋 확인 <!-- 3617671 -->

이 기능은 지연되고 있으며 나중에 출시될 예정입니다.

#### <a name="updated-ui-changes-for-microsoft-edge-browser-on-windows-10-and-later-devices----3775833-----"></a>Windows 10 이상 디바이스의 Microsoft Edge 브라우저에서 변경되어 업데이트된 UI <!-- 3775833   -->
디바이스 구성 프로필을 만들 때 Windows 10 이상 디바이스에서 Microsoft Edge 기능을 허용하거나 제한할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Windows 10 이상** > 프로필 유형에 대해 **디바이스 제한** > **Microsoft Edge 브라우저**). 이 업데이트에서는 Microsoft Edge 설정을 더 자세히 설명하여 더 쉽게 이해할 수 있습니다. 

이러한 기능을 확인하려면 [Microsoft Edge 브라우저 디바이스 제한 설정](device-restrictions-windows-10.md#microsoft-edge-browser)으로 이동하세요.

적용 대상: Windows 10 이상

#### <a name="expanded-support-for-android-enterprise-fully-managed-devices--preview-------3903241-3903244-3903246-----"></a>Android Enterprise 완전 관리형 디바이스에 대한 지원 확장(미리 보기)  <!--   3903241, 3903244, 3903246   -->
아직 공개 미리 보기에서 Android Enterprise 완전 관리형 디바이스([2019년 1월에 처음 발표](whats-new.md#week-of-january-14-2019))에 대한 지원이 다음과 같이 확장되었습니다. 

- 완전 관리형 전용 디바이스에서 [준수 정책](compliance-policy-create-android-for-work.md)을 만들어 암호 규칙 및 운영 체제 요구 사항을 포함할 수 있습니다(**디바이스 준수** > **정책** > **정책 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자**). 

  전용 디바이스의 경우 디바이스가 **비준수**로 표시될 수 있습니다. 조건부 액세스는 전용 디바이스에서 사용할 수 없습니다. 할당된 정책을 준수하는 전용 디바이스를 가져오는 모든 태스크 또는 작업을 수행해야 합니다.

- [조건부 액세스](conditional-access.md) - Android에 적용되는 조건부 액세스 정책은 Android Enterprise 완전 관리형 디바이스에도 적용됩니다. 이제 사용자는 **Microsoft Intune 앱**을 사용하여 완전 관리형 디바이스를 Azure Active Directory에 등록할 수 있습니다. 그런 다음, 규정 준수 문제를 확인하고 해결하여 조직 리소스에 액세스합니다.

- 새 최종 사용자 앱(Microsoft Intune 앱) - **Microsoft Intune**이라는 새로운 Android 완전 관리형 디바이스용 최종 사용자 앱이 있습니다. 이 새 앱은 최신의 간단한 앱이며 기능적으로 회사 포털 앱과 비슷하지만 완전 관리형 디바이스를 제공합니다. 자세한 내용은 [Google Play의 Microsoft Intune 앱](https://play.google.com/store/apps/details?id=com.microsoft.intune)을 참조하세요.

Android 완전 관리형 디바이스를 설정하려면 **디바이스 등록** > **Android 등록** > **회사 소유의 완전 관리형 사용자 디바이스**로 이동합니다. 완전 관리형 Android 디바이스에 대한 지원은 미리 보기로 남아 있으며, 일부 Intune 기능이 완벽하게 작동하지 않을 수 있습니다.  

이 미리 보기에 대한 자세한 내용은 [Microsoft Intune - Android Enterprise 완전 관리형 디바이스 미리 보기 2](https://aka.ms/preview2_AE_fullymanaged) 블로그를 참조하세요.


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="configure-profile-to-skip-some-screens-during-setup-assistant----2276470----"></a>설정 도우미 수행 중에 일부 화면을 건너뛰도록 프로필 구성 <!-- 2276470  -->
macOS 등록 프로필을 만드는 경우 사용자가 설정 도우미를 수행할 때 다음 화면 중 하나를 건너뛰도록 구성할 수 있습니다.
- 모양
- 표시 색상
- iCloudStorage 새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다.  사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.
자세한 내용은 [Apple School Manager 또는 장비 등록 프로그램을 통해 자동으로 macOS 디바이스 등록](device-enrollment-program-enroll-macos.md)을 참조하세요.

#### <a name="bulk-device-naming-when-enrolling-corporate-ios-devices--3566569----"></a>회사 iOS 디바이스를 등록할 때 대량으로 디바이스 이름 지정<!--3566569  -->
Apple의 회사 등록 방법(DEP/ABM/ASM) 중 하나를 사용할 때 들어오는 iOS 디바이스의 이름을 자동으로 지정하도록 디바이스 이름 형식을 설정할 수 있습니다. 디바이스 유형과 일련 번호가 포함된 형식을 템플릿에 지정할 수 있습니다. 이렇게 하려면 **Intune** > **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > **토큰 선택** >**프로필 만들기** > **디바이스 명명 형식**을 차례로 선택합니다. 기존 프로필을 편집할 수 있지만 새로 동기화된 디바이스에만 이름이 적용됩니다.

#### <a name="updated-default-timeout-message-on-enrollment-status-page----3959331---"></a>등록 상태 페이지에서 기본 시간 제한 메시지가 업데이트됨 <!-- 3959331 -->
ESP(등록 상태 페이지)가 ESP 프로필에 지정된 시간 제한 값을 초과할 때 사용자에게 표시되는 기본 시간 제한 메시지가 업데이트되었습니다. 새 기본 메시지는 사용자에게 표시되어 ESP 배포를 통해 수행할 다음 작업을 이해하는 데 도움이 됩니다.  

### <a name="device-management"></a>디바이스 관리

#### <a name="retire-noncompliant-devices-----1827291-----"></a>비준수 디바이스 사용 중지  <!-- 1827291   -->
이 기능은 지연되고 있으며 향후 릴리스에서 제공될 예정입니다.


### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="intune-data-warehouse-v10-changes-reflecting-back-to-beta----4403765---"></a>Intune 데이터 웨어하우스 V1.0에서 베타 버전을 다시 반영하도록 변경됨 <!-- 4403765 -->
V1.0은 1808에 처음 도입되었을 때 베타 API와 상당한 차이가 있었습니다. 이러한 변경 내용은 1903에서 베타 API 버전으로 다시 반영됩니다. 베타 API 버전을 사용하는 중요한 보고서가 있으면 변경 내용을 위반하지 않도록 해당 보고서를 V1.0으로 전환하는 것이 좋습니다. 자세한 내용은 [Intune 데이터 웨어하우스 API에 대한 변경 로그](reports-changelog.md#1903-part-2)를 참조하세요.

#### <a name="monitor-security-baseline-status-public-preview----3082047---"></a>보안 기준 모니터링 상태(공개 미리 보기) <!-- 3082047 --> 
보안 기준 모니터링에 [범주별 보기](security-baselines-monitor.md#per-category-view)가 추가되었습니다. (보안 기준은 미리 보기로 남아 있습니다.) 범주별 보기는 해당 범주의 각 상태 그룹에 속하는 디바이스의 비율과 함께 기준의 각 범주를 표시합니다. 이제 개별 범주와 일치하지 않거나, 잘못 구성되었거나, 적용되지 않는 디바이스의 수를 확인할 수 있습니다.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-apple-vpp-tokens---2371886----"></a>Apple VPP 토큰에 대한 범위 태그 <!--2371886  -->
이제 범위 태그는 Apple VPP 토큰에 추가할 수 있습니다. 동일한 범위 태그가 할당된 사용자만 해당 태그를 사용하여 Apple VPP 토큰에 액세스할 수 있습니다. 이 토큰을 사용하여 구입한 VPP 앱 및 eBook은 해당 범위 태그를 상속합니다. 범위 태그에 대한 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.







## <a name="week-of-april-1-2019"></a>2019년 4월 1일 주

### <a name="device-configuration"></a>디바이스 구성

#### <a name="updated-certificate-connectors-----icm-113304612---"></a>업데이트된 인증서 커넥터  <!-- ICM 113304612 -->
[Intune 인증서 커넥터와 Microsoft Intune용 PFX 인증서 커넥터](certficates-pfx-configure.md#whats-new-for-connectors) 모두에 대한 업데이트가 릴리스되었습니다. 새 릴리스에서는 몇 가지 알려진 문제를 해결합니다.  

### <a name="app-management"></a>앱 관리

#### <a name="user-experience-update-for-the-company-portal-app-for-ios----2536024---"></a>iOS용 회사 포털 앱의 사용자 환경 업데이트 <!-- 2536024 -->
iOS 디바이스용 회사 포털 앱의 홈페이지가 다시 디자인되었습니다. 이 변경을 통해 홈페이지에서 iOS UI 패턴을 더 잘 따르고 앱과 eBook에 대한 향상된 검색 기능도 제공합니다.

#### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>iOS 12 디바이스 사용자에 대한 회사 포털 등록 변경 <!--3448635 -->  
iOS용 회사 포털 등록 화면 및 단계가 Apple iOS 12.2에서 릴리스된 MDM 등록 변경 내용에 맞게 업데이트되었습니다. 업데이트된 워크플로는 사용자에게 다음 작업을 요청합니다.  

* Safari가 회사 포털 앱으로 돌아가기 전에 회사 포털 웹 사이트를 열어서 관리 프로필을 다운로드하도록 허용합니다.  
* 설정 앱을 열고 관리 프로필을 해당 디바이스에 설치합니다.
* 회사 포털 앱으로 돌아가서 등록을 완료합니다.  

업데이트된 등록 단계 및 화면은 [Intune에서 iOS 디바이스 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-ios)을 참조하세요.  

## <a name="week-of-march-25-2019"></a>2019년 3월 25일 주

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

### <a name="support-for-the-power-bi-compliance-app-from-the-data-warehouse-blade-in-microsoft-intune----4260871---"></a>Microsoft Intune의 데이터 웨어하우스 블레이드에서 Power BI 준수 앱 지원 <!-- 4260871 -->
이전에는 **Intune 데이터 웨어하우스** 블레이드의 **Power BI 파일 다운로드** 링크에서 Intune 데이터 웨어하우스 보고서(.pbix 파일)를 다운로드했습니다. 이 보고서는 Power BI 준수 앱으로 대체되었습니다. Power BI 준수 앱에는 특별한 로드 또는 설정이 필요하지 않습니다. Power BI Online 포털에서 직접 열리며, 특별히 자격 증명에 따라 Intune 테넌트에 대한 데이터를 표시합니다. Intune에서 Intune 블레이드의 오른쪽에 있는 **Intune 데이터 웨어하우스 설정** 링크를 선택합니다. 그런 다음, **Power BI 앱 다운로드**를 클릭합니다. 자세한 내용은 [Power BI를 통해 데이터 웨어하우스에 연결](reports-proc-get-a-link-powerbi.md)을 참조하세요.

## <a name="week-of-march-18-2019"></a>2019년 3월 18일 주

### <a name="app-management"></a>앱 관리

#### <a name="deploy-microsoft-visio-and-microsoft-project----3725386----"></a>Microsoft Visio 및 Microsoft 프로젝트 배포 <!-- 3725386  -->
해당 앱에 대한 라이선스가 있는 경우 이제 Microsoft Intune을 사용하여 Microsoft Visio Pro for Office 365 및 Microsoft Project Online 데스크톱 클라이언트를 독립 앱으로 Windows 10 디바이스에 배포할 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 차례로 선택하여 **앱 추가** 블레이드를 표시합니다. **앱 추가** 블레이드에서 **앱 유형**으로 **Windows 10**을 선택합니다. 그런 다음, **앱 제품군 구성**을 선택하여 설치할 앱을 선택합니다. Windows 10 디바이스용 Office 365 앱에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](apps-add-office365.md)을 참조하세요.

#### <a name="microsoft-visio-pro-for-office-365-product-name-change----3593653----"></a>Microsoft Visio Pro for Office 365 제품 이름 변경 <!-- 3593653  -->
이제 **Microsoft Visio Pro for Office 365**는 **Microsoft Visio Online 플랜 2**로 알려집니다.  Microsoft Visio에 대한 자세한 내용은 [Visio Online 플랜 2](https://products.office.com/visio/visio-online-plan-2)를 참조하세요. Windows 10 디바이스용 Office 365 앱에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](apps-add-office365.md)을 참조하세요.

#### <a name="intune-app-protection-policy-app-character-limit-setting----3291302----"></a>Intune APP(앱 보호 정책) 문자 제한 설정 <!-- 3291302  -->
Intune 관리자는 Intune APP의 **다른 앱에서 잘라내기, 복사 및 붙여넣기 제한** 정책 설정에 대한 예외를 지정할 수 있습니다.  관리자는 관리형 앱에서 잘라내거나 복사할 수 있는 문자 수를 지정할 수 있습니다. 이 설정을 사용하면 "다른 앱에서 잘라내기, 복사 및 붙여넣기 제한" 설정에 관계없이 지정된 문자 수를 모든 앱에 공유할 수 있습니다. Android용 Intune 회사 포털 앱 버전에는 5.0.4364.0 버전 이상이 필요합니다. 자세한 내용은 [iOS 데이터 보호](app-protection-policy-settings-ios.md#data-protection), [Android 데이터 보호](app-protection-policy-settings-android.md#data-protection) 및 [클라이언트 앱 보호 로그 검토](app-protection-policy-settings-log.md#app-protection-policy-settings)를 참조하세요.

#### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477-----"></a>Office ProPlus용 ODT(Office 배포 도구) XML 배포 <!-- 3192477   -->
Intune 관리 콘솔에서 Office Pro Plus 인스턴스를 만들 때 ODT(Office 배포 도구) XML을 제공할 수 있습니다. 이렇게 하면 기존 Intune UI 옵션이 사용자의 요구 사항을 충족시키지 못하는 경우 사용자 지정 가능성이 향상됩니다. 자세한 내용은 [Microsoft Intune을 사용하여 Office 365 앱을 Windows 10 디바이스에 할당](https://docs.microsoft.com/intune/apps-add-office365) 및 [Office 배포 도구에 대한 구성 옵션](https://docs.microsoft.com/DeployOffice/configuration-options-for-the-office-2016-deployment-tool)을 참조하세요.

#### <a name="app-icons-will-now-be-displayed-with-an-automatically-generated-background----1429026----"></a>앱 아이콘이 자동으로 생성된 배경에 표시됨 <!-- 1429026  -->
이제 Windows 회사 포털 앱에서 앱 아이콘이 아이콘의 기준 색(감지 가능한 경우)에 따라 자동으로 생성된 배경에 표시됩니다. 해당되는 경우 이 배경은 이전에 앱 타일에 표시된 회색 테두리를 대체합니다. 이 변경은 10.3.3451.0 이후 버전의 회사 포털에서 사용자에게 표시됩니다.

#### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523-----"></a>Windows 대량 등록 후 회사 포털 앱을 사용하여 사용 가능한 앱 설치 <!-- 2751523   -->
[Windows 대량 등록](windows-bulk-enroll.md)(프로비저닝 패키지)을 사용하여 Intune에 등록한 Windows 디바이스는 회사 포털 앱을 사용하여 사용 가능한 앱을 설치할 수 있습니다. 회사 포털 앱에 대한 자세한 내용은 [수동으로 Windows 10 회사 포털 추가](store-apps-company-portal-app.md) 및 [Microsoft Intune 회사 포털 앱을 구성하는 방법](company-portal-app.md)을 참조하세요.

#### <a name="the-microsoft-teams-app-can-be-selected-as-part-of-the-office-app-suite----3828932----"></a>Microsoft Teams 앱을 Office 앱 제품군의 일부로 선택할 수 있음 <!-- 3828932  -->
Microsoft Teams 앱은 Office Pro Plus 앱 제품군 설치의 일부로 포함하거나 제외할 수 있습니다. 이 기능은 Office Pro Plus 빌드 번호 16.0.11328.20116 이상에서 작동합니다. 설치를 완료하려면 사용자가 로그아웃한 다음, 디바이스에 로그인해야 합니다. Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **Office 365 제품군** 앱 유형 중 하나를 선택한 다음, **앱 제품군 구성**을 선택합니다.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="automatically-start-an-app-when-running-multiple-apps-in-kiosk-mode-on-windows-10-and-later-devices----2351390---"></a>Windows 10 이상 디바이스에서 여러 앱을 키오스크 모드로 실행할 때 자동으로 앱 시작 <!-- 2351390 -->

Windows 10 이상 디바이스에서는 디바이스를 키오스크 모드로 실행하고 여러 앱을 실행할 수 있습니다. 이 업데이트에는 **자동 시작** 설정이 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Windows 10 이상** > 프로필 유형에 대해 **키오스크** > **다중 앱 키오스크**). 사용자가 디바이스에 로그인할 때 앱을 자동으로 시작하려면 이 설정을 사용합니다.

모든 키오스크 설정에 대한 목록과 설명을 보려면 [Intune에서 키오스크로 실행하는 Windows 10 이상 디바이스 설정](kiosk-settings-windows.md)을 참조하세요.

적용 대상: Windows 10 이상

#### <a name="operational-logs-also-show-details-on-non-compliant-devices----4063755----"></a>작업 로그에는 비준수 디바이스에 대한 세부 정보도 표시됨 <!-- 4063755  -->
Intune 로그를 Azure 모니터 기능으로 라우팅할 때 작동 로그를 라우팅할 수도 있습니다. 이 업데이트에서 작업 로그는 비준수 디바이스에 대한 정보도 제공합니다. 

이 기능에 대한 자세한 내용은 [Intune에서 스토리지, 이벤트 허브 또는 로그 분석에 로그 데이터 전송](review-logs-using-azure-monitor.md)을 참조하세요.

#### <a name="route-logs-to-azure-monitor-in-more-intune-workloads----3804627---"></a>더 많은 Intune 워크로드에서 로그를 Azure Monitor로 라우팅 <!-- 3804627 -->
Intune에서 Azure Monitor의 감사 및 작업 로그를 이벤트 허브, 스토리지 및 로그 분석으로 라우팅할 수 있습니다(**Intune** > **모니터링** > **진단 설정**). 이 업데이트에서 이러한 로그는 규정 준수, 구성, 클라이언트 앱 등을 포함한 Intune 워크로드에서 라우팅할 수 있습니다. 

로그를 Azure Monitor로 라우팅하는 방법에 대한 자세한 내용은 [Intune에서 스토리지, 이벤트 허브 또는 로그 분석에 로그 데이터 전송](review-logs-using-azure-monitor.md)을 참조하세요.

#### <a name="create-and-use-mobility-extensions-on-android-zebra-devices-in-intune----3305880-----"></a>Intune의 Android Zebra 디바이스에서 이동성 확장 만들기 및 사용 <!-- 3305880   -->
이 업데이트에서 Intune은 Android Zebra 디바이스 구성을 지원합니다. 특히 디바이스 구성 프로필을 만들고 StageNow에서 생성된 MX(Mobility Extensions) 프로필을 사용하여 설정을 Android Zebra 디바이스에 적용할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android** > 프로필 유형에 대해 **MX 프로필(Zebra만)** ).

이 기능에 대한 자세한 내용은 [Intune에서 이동성 확장을 통해 Zebra 디바이스 사용 및 관리](android-zebra-mx-overview.md)를 참조하세요.

적용 대상: Android

### <a name="device-management"></a>디바이스 관리

#### <a name="encryption-report-for-windows-10-devices-in-public-preview---2351538---"></a>Windows 10 디바이스에 대한 암호화 보고서(공개 미리 보기)<!-- 2351538 -->  
새 [암호화 보고서(미리 보기)](encryption-monitor.md)를 사용하여 Windows 10 디바이스에 대한 암호화 상태에 대한 세부 정보를 확인합니다. 사용 가능한 세부 정보에는 디바이스 TPM 버전, 암호화 준비 상태 및 상태, 오류 보고 등이 포함됩니다.  

#### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-in-public-preview----2351547-----"></a>Intune 포털에서 BitLocker 복구 키 액세스(공개 미리 보기) <!-- 2351547   -->  
이제 Intune을 사용하여 Azure Active Directory에서 BitLocker 키 ID 및 BitLocker 복구 키에 대한 [세부 정보를 볼 수 있습니다](encryption-monitor.md).

#### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS 및 Android 디바이스의 Intune 시나리오에 대한 Microsoft Edge 지원 <!-- 3411007 -->
Microsoft Edge는 최종 사용자 환경에 향상된 기능을 추가하여 Intune Managed Browser와 동일한 모든 관리 시나리오를 모두 지원합니다. Intune 정책에 따라 사용하도록 설정된 Microsoft Edge 엔터프라이즈 기능에는 이중 ID, 앱 보호 정책 통합, Azure 애플리케이션 프록시 통합, 관리형 즐겨찾기 및 홈페이지 바로 가기가 포함됩니다. 자세한 내용은 [Microsoft Edge 지원](app-configuration-managed-browser.md#microsoft-edge-support)을 참조하세요.

#### <a name="exchange-onlineintune-connector-deprecate-support-for-eas-only-devices---3105122----"></a>Exchange Online/Intune Connector에서 EAS 전용 디바이스에 대한 지원 중단 <!--3105122  -->
Intune 콘솔은 Intune Connector를 사용하는 Exchange Online에 연결된 EAS 전용 디바이스를 보고 관리하는 기능을 더 이상 지원하지 않습니다. 대신 다음 옵션을 사용할 수 있습니다.
- MDM(모바일 디바이스 관리)에 디바이스 등록
- Intune 앱 보호 정책을 사용하여 디바이스 관리
- [Exchange Online의 클라이언트 및 모바일](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/clients-and-mobile-in-exchange-online)에서 설명한 대로 Exchange 제어 사용

### <a name="search-the-all-devices-page-for-an-exact-device-by-using-name---4254930---"></a>[name]을 사용하여 모든 디바이스 페이지에서 정확한 디바이스 검색 <!--4254930 -->
이제 정확한 디바이스 이름을 검색할 수 있습니다. **Intune** > **디바이스** > **모든 디바이스**로 차례로 이동하고, 정확히 일치하는 항목을 검색하기 위해 검색 상자에서 디바이스 이름을 {}로 묶습니다. 예를 들어 **{Device12345}** 입니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202----"></a>테넌트 상태 페이지에서 추가 커넥터 지원 <!-- 3617202  -->
이제 [테넌트 상태 페이지](tenant-status.md)에서 *Windows Defender ATP(Advanced Threat Protection)* 및 다른 Mobile Threat Defense 커넥터를 포함한 추가 커넥터에 대한 상태 정보가 표시됩니다.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917----"></a>Intune 읽기 전용 액세스 권한을 몇 가지 Azure Active Directory 역할에 부여 <!-- 3637917  -->
Intune 읽기 전용 액세스 권한이 부여된 Azure AD 역할은 다음과 같습니다. Azure AD 역할에 부여된 권한은 Intune RBAC(역할 기반 액세스 제어)에 부여된 권한보다 우선합니다.

Intune 감사 데이터에 대한 읽기 전용 액세스:

- 규정 준수 관리자
- 준수 데이터 관리자

모든 Intune 데이터에 대한 읽기 전용 액세스:

- 보안 관리자
- 보안 운영자
- 보안 Reader

자세한 내용은 [역할 기반 액세스 제어](role-based-access-control.md)를 참조하세요.

#### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430-----"></a>iOS 앱 프로비저닝 프로필에 대한 범위 태그 <!--2934430   -->
범위 태그를 iOS 앱 프로비저닝 프로필에 추가하여 해당 범위 태그도 할당된 역할이 있는 사용자만 iOS 앱 프로비저닝 프로필에 액세스할 수 있습니다. 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

#### <a name="scope-tags-for-app-configuration-policies---2371891-----"></a>앱 구성 정책에 대한 범위 태그 <!--2371891   -->
범위 태그를 앱 구성 정책에 추가하여 해당 범위 태그도 할당된 역할이 있는 사용자만 앱 구성 정책에 액세스할 수 있습니다. 앱 구성 정책은 동일한 범위 태그가 할당된 앱만 대상으로 지정하거나 연결할 수 있습니다. 자세한 내용은 [RBAC 및 범위 태그 사용](scope-tags.md)을 참조하세요.

### <a name="microsoft-edge-support-for-intune-scenarios-on-ios-and-android-devices----3411007---"></a>iOS 및 Android 디바이스의 Intune 시나리오에 대한 Microsoft Edge 지원 <!-- 3411007 -->
Microsoft Edge는 최종 사용자 환경에 향상된 기능을 추가하여 Intune Managed Browser와 동일한 모든 관리 시나리오를 모두 지원합니다. Intune 정책에 따라 사용하도록 설정된 Microsoft Edge 엔터프라이즈 기능에는 이중 ID, 앱 보호 정책 통합, Azure 애플리케이션 프록시 통합, 관리형 즐겨찾기 및 홈페이지 바로 가기가 포함됩니다. 자세한 내용은 [Microsoft Edge 지원](app-configuration-managed-browser.md#microsoft-edge-support)을 참조하세요.

## <a name="week-of-february-25-2019"></a>2019년 2월 25일 주

### <a name="device-configuration"></a>디바이스 구성

#### <a name="intune-powershell-module----951068----"></a>Intune PowerShell 모듈 <!-- 951068  -->
Microsoft Graph를 통해 Intune API를 지원하는 Intune PowerShell 모듈은 이제 [Microsoft PowerShell 갤러리](https://www.powershellgallery.com/packages/Microsoft.Graph.Intune/6.1902.1.10)에서 사용할 수 있습니다.

- [이 모듈을 사용하는 방법에 대한 세부 정보](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/README.md)
- [이 모듈을 사용하는 시나리오 예제](https://github.com/Microsoft/Intune-PowerShell-SDK/blob/master/Samples/README.md)

#### <a name="improved-support-for-delivery-optimization----3183757----"></a>향상된 전송 최적화 지원  <!--3183757  -->
Intune에서 전송 최적화 구성 지원이 확장되었습니다. 이제 확장된 [전송 최적화 설정](delivery-optimization-settings.md) 목록을 구성하여 Intune 콘솔에서 직접 대상을 디바이스로 지정할 수 있습니다.


## <a name="week-of-february-18-2019"></a>2019년 2월 18일 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-will-leverage-google-play-protect-apis-on-android-devices----2577355-----"></a>Intune은 Android 디바이스에서 Google Play 보호 API를 활용함 <!-- 2577355   -->
일부 IT 관리자는 최종 사용자가 휴대폰의 루팅 또는 탈옥(jailbreaking)을 종료할 수 있는 BYOD 환경에 직면합니다. 때로는 악의가 없는 이 동작은 결국 최종 사용자 디바이스에서 조직의 데이터를 보호하기 위해 설정된 여러 Intune 정책을 무시하게 됩니다. 따라서 Intune은 등록 및 등록되지 않은 디바이스에 대한 루팅 및 탈옥 검색을 제공합니다. 이 릴리스에서 Intune은 Google Play 보호 API를 활용하여 등록되지 않은 디바이스에 대한 기존 루트 검색 검사를 추가합니다. Google은 발생하는 루트 검색 검사 전체를 공유하지 않는 반면, Intune에서는 이러한 API가 디바이스 사용자 지정을 비롯해 이전 디바이스에 최신 OS 업데이트를 가져오는 등의 갖가지 이유로 자신의 디바이스를 루팅한 사용자를 검색하기를 기대합니다. 이러한 사용자는 회사 데이터에 액세스하지 못하도록 차단되거나, 회사 계정이 앱을 사용하도록 설정된 해당 정책에서 초기화될 수 있습니다. 추가 값의 경우 IT 관리자는 Intune 앱 보호 블레이드 내에 여러 보고 업데이트를 보유하고 있습니다. "플래그가 지정된 사용자" 보고서에는 Google Play 보호의 SafetyNet API 검색을 통해 검색된 사용자가 표시되며, "잠재적으로 위험한 앱" 보고서에는 Google의 Verify Apps API 검색을 통해 검색된 앱이 표시됩니다. 이 기능은 Android에서 사용할 수 있습니다.

#### <a name="win32-app-information-available-in-troubleshooting-blade----2617342-----"></a>문제 해결 블레이드에서 사용할 수 있는 Win32 앱 정보 <!-- 2617342   -->
이제 Intune 앱 **문제 해결** 블레이드에서 Win32 앱 설치에 대한 오류 로그 파일을 수집할 수 있습니다. 앱 설치 문제 해결에 대한 자세한 내용은 [앱 설치 문제 해결](troubleshoot-app-install.md) 및 [Win32 앱 문제 해결](apps-win32-app-management.md#troubleshoot-win32-app-issues)을 참조하세요.

#### <a name="app-status-details-for-ios-apps----3761235-----"></a>iOS 앱에 대한 앱 상태 세부 정보 <!-- 3761235   -->
다음과 관련된 새로운 앱 설치 오류 메시지가 있습니다.
- 공유 iPad에 설치하는 경우 VPP 앱의 오류
- 앱 스토어를 사용하지 않도록 설정하는 경우의 오류
- 앱용 VPP 라이선스를 찾지 못하는 오류
- MDM 공급 기업을 통해 시스템 앱을 설치하지 못하는 오류
- 디바이스가 분실 모드 또는 키오스크 모드에 있는 경우 앱을 설치하지 못하는 오류
- 사용자가 앱 스토어에 로그인하지 않은 경우 앱을 설치하지 못하는 오류

Intune에서 **클라이언트 앱** > **앱** > "애플리케이션 이름" > **디바이스 설치 상태**를 선택합니다. 새 오류 메시지는 **상태 세부 정보** 열에서 사용할 수 있습니다.

#### <a name="new-app-categories-screen-in-the-company-portal-app-for-windows-10---3834780----"></a>Windows 10용 회사 포털 앱의 새 앱 범주 화면<!-- 3834780  -->
Windows 10용 회사 포털의 앱 찾아보기 및 선택 환경을 개선하기 위해 **앱 범주**라는 새 화면이 추가되었습니다. 이제 앱이 **추천**, **교육용**, **생산성** 등의 범주에 따라 정렬되어 사용자에게 표시됩니다. 이 변경은 회사 포털 버전 10.3.3451.0 이상에서 나타납니다. 새 화면을 보려면 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)을 참조하세요. 회사 포털의 앱에 대한 자세한 내용은 [디바이스에 앱 설치 및 공유](/intune-user-help/install-apps-cpapp-windows)를 참조하세요.  

#### <a name="power-bi-compliance-app----1455231-doc-work-item---"></a>Power BI 준수 앱 <!-- 1455231 doc-work-item -->
[Intune 준수(데이터 웨어하우스)](https://aka.ms/intune/datawarehouseapi/getpowerbiapp) 앱을 사용하여 Power BI Online에서 Intune 데이터 웨어하우스에 액세스합니다. 이제 이 Power BI 앱을 사용하면 설정할 필요 없이 웹 브라우저를 떠나지 않고도 미리 만들어진 보고서에 액세스하고 공유할 수 있습니다. 자세한 내용은 [변경 로그 - Power BI 준수 앱](reports-changelog.md#power-bi-compliance-app)을 참조하세요.


### <a name="device-configuration"></a>디바이스 구성

#### <a name="powershell-scripts-can-run-in-a-64-bit-host-on-64-bit-devices----1862675-----"></a>PowerShell 스크립트가 64비트 디바이스의 64비트 호스트에서 실행될 수 있음 <!-- 1862675   -->
디바이스 구성 프로필에 PowerShell 스크립트를 추가한 경우 해당 스크립트는 항상 32비트, 심지어 64비트 운영 체제에서도 실행됩니다. 이 업데이트를 사용하여 관리자는 64비트 디바이스의 64비트 PowerShell 호스트에서 스크립트를 실행할 수 있습니다(**디바이스 구성** > **PowerShell 스크립트** > **추가** > **구성** > **64비트 PowerShell 호스트에서에서 스크립트 실행**).

PowerShell을 사용하는 방법에 대한 자세한 내용은 [Intune의 PowerShell 스크립트](intune-management-extension.md)를 참조하세요.

적용 대상: Windows 10 이상

#### <a name="macos-users-are-prompted-to-update-their-password----1873216---"></a>macOS 사용자에게 암호를 업데이트하라는 메시지가 표시됨 <!-- 1873216 -->
Intune에서 **ChangeAtNextAuth** 설정을 macOS 디바이스에 적용하고 있습니다. 이 설정은 규정 준수 암호 정책 또는 디바이스 제한 암호 프로필이 있는 최종 사용자 및 디바이스에 영향을 줍니다. 최종 사용자에게 암호를 업데이트하라는 메시지가 표시됩니다. 사용자가 디바이스에 로그인하는 것처럼 인증이 필요한 작업을 처음 실행할 때마다 이 프롬프트가 발생합니다. 또한 키 집합 액세스 요청처럼 관리 권한이 필요한 작업을 수행할 때 해당 암호를 업데이트하라는 메시지가 사용자에게 표시될 수 있습니다. 

관리자가 새 암호 또는 기존 암호 정책을 변경하면 최종 사용자에게 자신의 암호를 업데이트하라는 메시지가 다시 표시됩니다.

적용 대상:  
macOS

#### <a name="assign-scep-certificates-to-a-userless-macos-device-------2340521------"></a>SCEP 인증서를 사용자가 없는 macOS 디바이스에 할당    <!-- 2340521    -->
디바이스 특성을 사용하는 SCEP(단순 인증서 등록 프로토콜) 인증서를 사용자 선호도가 없는 디바이스를 포함한 macOS 디바이스에 할당하고, 인증서 프로필을 Wi-Fi 또는 VPN 프로필에 연결할 수 있습니다. 이렇게 하면 Windows, iOS 및 Android를 실행하는 [사용자 선호도가 있거나 없는 디바이스에 SCEP 인증서를 이미 할당](certificates-profile-scep.md)해야 하는 지원이 확장됩니다.  이 업데이트에는 macOS에 대한 SCEP 인증서 프로필을 구성할 때 *디바이스*라는 인증서 종류를 선택하는 옵션이 추가되었습니다.

적용 대상: 
- macOS

#### <a name="intune-conditional-access-ui-update------2432313-----"></a>Intune 조건부 액세스 UI 업데이트   <!-- 2432313   -->
Intune 콘솔에서 조건부 액세스 UI가 향상되었습니다. 확인할 수 있습니다.
- Intune ‘조건부 액세스 블레이드가 Azure Active Directory의 블레이드로 대체되었습니다.  이렇게 하면 Intune 콘솔 내에서 Azure AD 기술로 유지되는 [조건부 액세스](conditional-access.md)에 대한 전체 설정 및 구성에 액세스할 수 있습니다. 
- *온-프레미스 액세스* 블레이드의 이름이 *Exchange 액세스*로 변경되고, 이름이 변경된 이 블레이드에 *Exchange 서비스 커넥터* 설정이 재배치되었습니다.  이 변경은 [Exchange 온라인 및 온-프레미스와 관련된 세부 정보를 구성하고 모니터링](exchange-connector-install.md)하는 위치에서 통합됩니다.  

#### <a name="kiosk-browser-and-microsoft-edge-browser-apps-can-run-on-windows-10-devices-in-kiosk-mode----2935135-----"></a>키오스크 브라우저 및 Microsoft Edge 브라우저 앱은 Windows 10 디바이스에서 키오스크 모드로 실행될 수 있음 <!-- 2935135   -->
Windows 10 디바이스를 키오스크 모드에서 사용하여 하나 또는 여러 앱을 실행할 수 있습니다. 이 업데이트에는 다음을 포함하여 키오스크 모드에서 브라우저 앱 사용에 대한 몇 가지 변경 사항이 포함됩니다.

- Microsoft Edge 브라우저 또는 키오스크 브라우저를 추가하여 키오스크 디바이스에서 앱으로 실행합니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **Windows 10 이상** > 프로필 유형에 대한 **키오스크**).
- 다음을 포함하여 새로운 기능과 설정은 허용하거나 제한하는 데 사용할 수 있습니다(**디바이스 구성** > **프로필** > **새 프로필** > 플랫폼에 대해 **Windows 10 이상** > 프로필 유형에 대해 **디바이스 제한**).

- Microsoft Edge 브라우저:
  - Microsoft Edge 키오스크 모드 사용
  - 유휴 시간 후 브라우저 새로 고침

- 즐겨찾기 및 검색:
  - 검색 엔진 변경 허용

이러한 설정 목록은 다음을 참조하세요.

- [키오스크로 실행되는 Windows 10 이상 디바이스 설정](kiosk-settings-windows.md)
- [Microsoft Edge 브라우저 디바이스 제한](device-restrictions-windows-10.md#microsoft-edge-browser)
- [즐겨찾기 및 검색 디바이스 제한](device-restrictions-windows-10.md##favorites-and-search)

적용 대상: Windows 10 이상

#### <a name="new-device-restriction-settings-for-ios-and-macos-devices----3448774-----"></a>iOS 및 macOS 디바이스에 대한 새 디바이스 제한 설정 <!-- 3448774   -->
iOS 및 macOS를 실행하는 디바이스에서 일부 설정 및 기능을 제한할 수 있습니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** 또는 **macOS** > 프로필 유형에 대한 **디바이스 제한**). 이 업데이트에는 화면 시간 설정, eSIM 설정 및 셀룰러 계획 변경 등을 포함하여 iOS 디바이스에서 제어할 수 있는 더 많은 기능과 설정이 추가되었습니다. 또한 사용자의 소프트웨어 업데이트 표시를 지연시키고 macOS 디바이스의 콘텐츠 캐싱을 차단합니다. 

제한할 수 있는 기능 및 설정을 확인하려면 다음을 참조하세요.

- [iOS 디바이스 제한 설정](device-restrictions-ios.md)
- [macOS 디바이스 제한 설정](device-restrictions-macos.md)

적용 대상:

- iOS
- macOS

#### <a name="kiosk-devices-are-now-called-dedicated-devices-on-android-enterprise-devices----3598402-----"></a>"키오스크" 디바이스는 이제 Android Enterprise 디바이스에서 "전용 디바이스"라고 함 <!-- 3598402   -->
Android 용어에 맞게 **키오스크**가 Android Enterprise 디바이스에 대한 **전용 디바이스**로 변경되었습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise > **디바이스 소유자만** > **디바이스 제한** > **전용 디바이스**).

사용 가능한 설정을 확인하려면 [기능을 허용하거나 제한하는 디바이스 설정](device-restrictions-android-for-work.md#dedicated-device-settings)으로 이동하세요.

적용 대상:  
Android Enterprise

#### <a name="safari-and-delaying-user-software-update-visibility-ios-settings-are-moving-in-the-intune-ui----3640850-3803313-----"></a>Safari 및 사용자 소프트웨어 업데이트 표시 지연 iOS 설정이 Intune UI에서 이동 중 <!-- 3640850, 3803313   -->
iOS 디바이스의 경우 Safari 설정을 설정하고 소프트웨어 업데이트를 구성할 수 있습니다. 이 업데이트에서 이러한 설정은 다음과 같이 Intune UI의 다른 파트로 이동합니다.

- Safari 설정은 **Safari**(**디바이스 구성** > **프로필** > **새 프로필** > 플랫폼에 대해 **iOS** > 프로필 유형에 대해 **디바이스 제한**)에서 **[기본 제공 앱](device-restrictions-ios.md#built-in-apps)** 으로 이동합니다.
- **감독되는 iOS 디바이스에 대한 사용자 소프트웨어 업데이트 표시 지연** 설정(**소프트웨어 업데이트** > **iOS용 정책 업데이트**)은 **디바이스 제한** >  **[일반](device-restrictions-ios.md#general)** 으로 이동합니다.  기존 정책에 미치는 영향에 대한 자세한 내용은 [iOS 소프트웨어 업데이트](software-updates-ios.md#configure-the-policy)를 참조하세요. 

설정 목록은 다음을 참조하세요.

- [iOS 디바이스 제한](device-restrictions-ios.md) 
- [iOS 소프트웨어 업데이트](software-updates-ios.md)

이 기능은 다음에 적용됩니다. 

- iOS

#### <a name="enabling-restrictions-in-the-device-settings-is-renamed-to-screen-time-on-ios-devices----3699164-----"></a>디바이스 설정에서 제한을 사용하도록 설정하면 iOS 디바이스에서 화면 시간으로 이름이 바뀜 <!-- 3699164   -->
감독되는 iOS 디바이스의 **디바이스 설정에서 제한의 활성화**를 구성할 수 있습니다(플랫폼에 대한 **디바이스 구성** > **프로필** > **새 프로필** > **iOS** > 프로필 유형에 대한 **디바이스 제한** > **일반**). 이 업데이트에서 이 설정은 **화면 시간(감독 모드인 경우에만)** 으로 이름이 바뀝니다. 

동작은 동일합니다. 특히: 

- iOS 11.4.1 이하: **차단**은 최종 사용자가 디바이스 설정에서 자신만의 제한을 설정하지 못하도록 방지합니다. 
- iOS 12.0 이상: **차단**은 최종 사용자가 디바이스 설정에서 콘텐츠 및 개인정보처리 제한 사항을 비롯해 자신만의 **화면 시간**을 설정하지 못하도록 방지합니다. iOS 12.0로 업그레이드된 디바이스에는 디바이스 설정의 제한 탭이 더 이상 표시되지 않습니다. 이러한 설정은 **화면 시간**에 있습니다. 

설정 목록은 [iOS 디바이스 제한](device-restrictions-ios.md#general)을 참조하세요.

적용 대상: 
- iOS


### <a name="device-management"></a>디바이스 관리

#### <a name="rename-an-enrolled-windows-device----1911112----"></a>등록된 Windows 디바이스 이름 바꾸기 <!-- 1911112  -->
이제 등록된 Windows 10 디바이스(RS4 이상)의 이름을 바꿀 수 있습니다. 이름을 바꾸려면 **Intune** > **디바이스** > **모든 디바이스** > 디바이스 선택 > **디바이스 이름 바꾸기**를 선택합니다. 이 기능은 현재 하이브리드 Azure AD Windows 디바이스의 이름 바꾸기를 지원하지 않습니다.

#### <a name="auto-assign-scope-tags-to-resources-created-by-an-admin-with-that-scope----3173823----"></a>해당 범위를 사용하여 관리자가 만든 리소스에 범위 태그 자동 할당 <!-- 3173823  -->
관리자가 리소스를 만드는 경우 관리자에게 할당된 모든 범위 태그는 새 리소스에 자동으로 할당됩니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="failed-enrollment-report-moves-to-the-device-enrollment-blade----3560202----"></a>실패한 등록 보고서가 디바이스 등록 블레이드로 이동 <!-- 3560202  -->
**실패한 등록** 보고서는 **디바이스 등록** 블레이드의 **모니터링** 섹션으로 이동되었습니다. 두 개의 열(등록 방법 및 OS 버전)이 새로 추가되었습니다.

#### <a name="company-portal-abandonment-report-renamed-to-incomplete-user-enrollments---3815076-eemiss---"></a>회사 포털 중단 보고서 이름이 사용자 등록 미완료로 변경됨 <!--3815076 eemiss -->
**회사 포털 중단** 보고서의 이름이 **사용자 등록 미완료**로 변경되었습니다.


<!-- ########################## -->
## <a name="week-of-february-4-2019"></a>2019년 2월 4일 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-macos-company-portal-dark-mode----3300524----"></a>Intune macOS 회사 포털 어둠 모드 <!-- 3300524  -->
Intune macOS 회사 포털은 이제 macOS용 어두운 모드를 지원합니다. macOS 10.14 이상 디바이스에서 어두운 모드를 활성화하면 회사 포털은 해당 모드를 리플렉션하는 색으로 모양을 조정합니다.

<!-- ########################## -->
## <a name="week-of-january-21-2019"></a>2019년 1월 21일 주

### <a name="app-management"></a>앱 관리

#### <a name="toast-notifications-for-win32-apps----3136566-----"></a>Win32 앱에 대한 알림 메시지 <!-- 3136566   -->
앱 할당마다 최종 사용자 토스트 알림을 표시하지 않을 수 있습니다. Intune에서 **클라이언트 앱** > **앱** > 앱 선택 > **할당** > **포함 그룹**을 선택합니다. 

#### <a name="intune-app-protection-policies-ui-update----3251427----"></a>Intune 앱 보호 정책 UI 업데이트 <!-- 3251427  -->
각각 더 쉽게 이해할 수 있도록 Intune 앱 보호 설정 및 단추의 레이블을 변경했습니다. 일부 변경 내용은 다음과 같습니다.  
- 컨트롤은 **예** / **아니요** 컨트롤에서 기본 **차단** / **허용** 및 **사용 안 함** / **사용** 컨트롤로 변경됩니다. 레이블도 업데이트됩니다.  
- 설정이 다시 포맷되므로 설정과 레이블이 컨트롤에 나란히 있어 더 효율적으로 검색할 수 있습니다.   

기본 설정과 설정 수는 동일하게 유지되지만, 이 변경으로 인해 사용자가 선택한 앱 보호 정책을 적용하기 위해 설정을 더 쉽게 이해, 검색 및 활용할 수 있습니다. 자세한 내용은 [iOS 설정](app-protection-policy-settings-ios.md) 및 [Android 설정](app-protection-policy-settings-android.md)을 참조하세요.

### <a name="additional-settings-for-outlook----3301182----"></a>Outlook에 대한 추가 설정 <!-- 3301182  -->
이제 Intune을 사용하여 Android 및 iOS용 Outlook에 대한 다음과 같은 설정을 추가로 구성할 수 있습니다.

- iOS 및 Android의 Outlook에서 사용할 회사 또는 학교 계정만 허용
- Office 365 및 하이브리드 최신 인증 온-프레미스 계정에 대한 최신 인증 배포
- 기본 인증을 선택한 경우 이메일 프로필의 사용자 이름 필드에 대한 `SAMAccountName` 사용
- 저장할 연락처 허용
- 외부 받는 사람 MailTips 구성
- **중요 받은 편지함** 구성
- iOS용 Outlook에 액세스하려면 생체 인식 필요
- 외부 이미지 차단

> [!NOTE]
> 회사 ID에 대한 액세스를 관리하기 위해 Intune 앱 보호 정책을 사용하는 경우 **생체 인식 필요**를 사용하지 않도록 설정하는 것이 좋습니다. 자세한 내용은 [iOS 액세스 요구 사항](app-protection-policy-settings-ios.md#access-requirements) 및 [Android 액세스 설정](app-protection-policy-settings-android.md#access-requirements)에 **액세스하려면 회사 자격 증명 필요**를 참조하세요.

자세한 내용은 [Microsoft Outlook 구성 설정](app-configuration-policies-outlook.md)을 참조하세요.

#### <a name="delete-android-enterprise-apps----1352553---"></a>Android Enterprise 앱 삭제 <!-- 1352553 -->
Microsoft Intune에서 관리되는 Google Play 앱을 삭제할 수 있습니다. 관리되는 Google Play 앱을 삭제하려면 Azure Portal에서 Microsoft Intune을 열고 **클라이언트 앱** > **앱**을 선택합니다. 앱 목록에서 관리되는 Google Play 앱의 오른쪽에 있는 줄임표(...)를 선택한 다음, 표시된 목록에서 **삭제**를 선택합니다. 앱 목록에서 관리되는 Google Play 앱을 삭제하면 관리되는 Google Play 앱이 자동으로 승인되지 않습니다.

#### <a name="managed-google-play-app-type----1352580---"></a>관리되는 Google Play 앱 유형 <!-- 1352580 -->
**관리되는 Google Play** 앱 형식을 사용하면 [관리되는 Google Play 앱](https://play.google.com/work/search?q=microsoft&c=apps)을 Intune에 추가할 수 있습니다. Intune 관리자는 이제 Intune 내에서 승인된 관리되는 Google Play 앱을 찾고, 검색하고, 승인하며, 동기화하고 할당할 수 있습니다.  더 이상 관리되는 Google Play 콘솔을 개별적으로 찾아보지 않아도 되며 더 이상 재인증할 필요가 없습니다.  Intune에서 **클라이언트 앱** > **앱** > **추가**를 선택합니다. **앱 유형** 목록에서 앱 유형으로 **관리되는 Google Play**를 선택합니다.

### <a name="default-android-pin-keyboard----3802457---"></a>기본 Android PIN 키보드 <!-- 3802457 -->
'숫자' PIN 형식을 사용하여 Android 디바이스에서 Intune APP(앱 보호 정책) PIN을 설정한 최종 사용자에게는 이제 이전에 설계된 고정 Android 키보드 UI 대신 기본 Android 키보드가 표시됩니다. '숫자' 및/또는 '암호' PIN 형식 모두에 대해 iOS 및 Android 디바이스 모두에서 기본 키보드를 사용하는 경우 일치하도록 이렇게 변경되었습니다. Android에서 APP PIN과 같은 최종 사용자 액세스 설정에 대한 자세한 내용은 [Android 액세스 요구 사항](app-protection-policy-settings-android.md#access-requirements)을 참조하세요.

### <a name="device-configuration"></a>디바이스 구성

#### <a name="use-microsoft-recommended-settings-with-security-baselines-public-preview----2055484-----"></a>보안 기준에 Microsoft 추천 설정 사용(공개 미리 보기) <!-- 2055484   -->

Intune은 Windows Defender ATP 및 Office 365 ATP를 비롯하여 보안에 중점을 둔 다른 서비스와 통합됩니다. 고객은 Microsoft 365 서비스에서 공통 전략 및 조화로운 엔드투엔드 보안 워크플로 집합을 요청하고 있습니다. 우리의 목표는 보안 작업 및 공통 관리자 작업을 연결하는 솔루션을 빌드하기 위한 전략을 조정하는 것입니다. Intune에서는 Microsoft 권장 “보안 기준” 집합(**Intune** > **보안 기준**)을 게시하여 이 목표를 달성하고자 합니다.  관리자는 이러한 기준에서 직접 보안 정책을 만든 다음, 이를 사용자에게 배포할 수 있습니다. 또한 조직의 요구 사항을 충족하도록 최선의 권장 사항을 사용자 지정할 수도 있습니다. Intune은 디바이스가 이러한 기준을 계속 준수하는지 확인하고 준수하지 않는 디바이스나 사용자에 대해 관리자에게 알립니다.

이 기능은 공개 미리 보기이므로 이제 만든 모든 프로필이 일반 공급(GA)되는 보안 기준 템플릿으로 이동하지 않습니다. 프로덕션 환경에서 이러한 미리 보기 템플릿을 사용하려고 하지 말아야 합니다.

보안 기준에 대해 자세히 알아보려면 [Intune에서 Windows 10 보안 기준 만들기](security-baselines-monitor.md)를 참조하세요.

이 기능은 다음에 적용됩니다. Windows 10 이상

#### <a name="non-administrators-can-enable-bitlocker-on-windows-10-devices-joined-to-azure-ad---2147379-----"></a>관리자가 아닌 사용자는 Azure AD에 조인된 Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 수 있음<!-- 2147379   -->
Windows 10 디바이스에서 BitLocker를 사용하도록 설정할 때(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상**(플랫폼) > **Endpoint Protection**(프로필 유형) > **Windows 암호화**) BitLocker 설정을 추가합니다. 

이 업데이트에는 표준 사용자(관리자가 아닌 사용자)가 암호화를 사용하도록 설정하게 허용하는 새 BitLocker 설정이 포함됩니다. 

설정을 보려면 [Windows 10용 엔드포인트 보호 설정](endpoint-protection-windows-10.md#windows-encryption)으로 이동합니다.

#### <a name="check-for-configuration-manager-compliance----2192052--eepublished----"></a>Configuration Manager 준수 확인 <!-- 2192052  eepublished  -->
이 업데이트에는 새 System Center Configuration Manager 준수 설정(**디바이스 준수** > **정책** > **정책 만들기** > **Windows 10 이상** > **Configuration Manager 준수**)이 포함됩니다. Configuration Manager는 Intune 준수에 신호를 보냅니다. 이 설정을 사용하여 모든 Configuration Manager 신호에 “준수”를 반환하도록 요구할 수 있습니다.

예를 들어 모든 소프트웨어 업데이트를 디바이스에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 디바이스의 프로그램이 알 수 없는 상태인 경우 디바이스는 Intune에서 비준수가 됩니다.

[Configuration Manager 준수](compliance-policy-create-windows.md#configuration-manager-compliance)에 이 설정이 설명되어 있습니다.

적용 대상: Windows 10 이상

#### <a name="customize-wallpaper-on-supervised-ios-devices-using-a-device-configuration-profile----2809324-----"></a>디바이스 구성 프로필을 사용하여 감독되는 iOS 디바이스에서 배경 화면 사용자 지정 <!-- 2809324   -->
iOS 디바이스에 대한 디바이스 구성 프로필을 만드는 경우 일부 기능(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대한 **iOS** > 프로필 유형에 대한 **디바이스 기능**)을 사용자 지정할 수 있습니다. 이 업데이트에는 관리자가 홈 화면 또는 잠금 화면에 .png, .jpg 또는 .jpeg 이미지를 사용하도록 허용하는 새 **배경 무늬** 설정이 포함됩니다. 이러한 배경 무늬 설정은 감독되는 디바이스에만 적용됩니다. 

이러한 설정의 목록은 [iOS 디바이스 기능 설정](ios-device-features-settings.md)을 참조하세요.

#### <a name="windows-10-kiosk-is-generally-available----3594661----"></a>Windows 10 키오스크가 일반 공급됨 <!-- 3594661  -->
이 업데이트에서 Windows 10 이상 디바이스의 키오스크 기능이 일반 공급(GA)됩니다. 추가 및 구성할 수 있는 모든 설정을 보려면 [Windows 10(및 이상)에 대한 키오스크 설정](kiosk-settings.md)을 참조하세요.

#### <a name="contact-sharing-via-bluetooth-is-removed-in-device-restrictions--device-owner-for-android-enterprise----3598396-----"></a>Bluetooth를 통한 연락처 공유가 디바이스 제한 > Android Enterprise에 대한 디바이스 소유자에서 제거됨 <!-- 3598396   -->
Android Enterprise 디바이스용 디바이스 제한 프로필을 만들 때 **Bluetooth를 통한 연락처 공유** 설정이 있습니다. 이 업데이트에서 **Bluetooth를 통한 연락처 공유** 설정이 제거됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼용 **Android Enterprise** > **디바이스 제한 사항 > 프로필 유형에 대한 디바이스 소유자** > **일반**). 

**Bluetooth를 통한 연락처 공유** 설정은 Android Enterprise 디바이스 소유자 관리에 대해 지원되지 않습니다. 따라서 이 설정을 제거하면 사용자 환경에서 이 설정을 활성화하고 구성하더라도 디비이스나 테넌트에 영향을 주지 않습니다.

현재 설정 목록을 보려면 [기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](device-restrictions-android-for-work.md)으로 이동합니다.

적용 대상: Android Enterprise 디바이스 소유자

### <a name="device-management"></a>디바이스 관리

#### <a name="selective-wipe-support-for-wip-without-enrollment-devices----1434452---"></a>등록 디바이스 없이 WIP에 대한 선택적 초기화 지원 <!-- 1434452 -->
등록 없이 Windows 정보 보호(WIP-WE) 를 사용하면 고객은 전체 MDM 등록할 필요 없이 Windows 10 디바이스에서 회사 데이터를 보호할 수 있습니다. 문서가 WIP-WE 정책으로 보호되면 Intune 관리자는 보호되는 데이터를 선택적으로 초기화할 수 있습니다. 사용자 및 디바이스를 선택하고 초기화 요청을 보내면 WIP-WE 정책을 통해 보호된 모든 데이터를 사용할 수 없게 됩니다. Azure Portal의 Intune에서 **모바일 앱** > **앱 선택적 초기화**를 선택합니다.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="new-operational-logs-and-ability-to-send-logs-to-azure-monitor-services----3762211----"></a>새 작업 로그 및 Azure Monitor 서비스에 로그 보내기 기능 <!-- 3762211  -->
Intune에는 변경 사항이 발생할 때 이벤트를 추적하는 기본 제공 감사 로깅 기능이 있습니다. 이 업데이트에는 다음을 비롯한 새 로깅 기능이 포함됩니다. 
- 성공 및 실패한 시도를 포함한 등록된 사용자 및 디바이스의 세부 정보를 표시하는 작업 로그(미리 보기).
- 감사 로그 및 작업 로그를 스토리지 계정, Event Hubs 및 Log Analytics를 비롯한 Azure Monitor에 보낼 수 있습니다. 이러한 서비스를 통해 Splunk 및 QRadar와 같은 분석을 저장하고 사용하며 로깅 데이터의 시각화를 가져올 수 있습니다.

[Intune에서 스토리지, Event Hubs 또는 Log Analytics에 로그 데이터 전송](review-logs-using-azure-monitor.md)에 이 기능에 대한 자세한 정보가 나와 있습니다.

### <a name="skip-more-setup-assistant-screens-on-an-ios-dep-device----2687509----"></a>iOS DEP 디바이스에서 더 많은 설정 도우미 화면 건너뛰기 <!-- 2687509  -->
현재 건너뛸 수 있는 화면 외에도 사용자가 디바이스를 등록할 때 설정 도우미에서 다음 화면을 건너뛰도록 iOS DEP 디바이스를 설정할 수 있습니다. 표시음, 개인 정보, Android 마이그레이션, 홈 단추, iMessage 및 FaceTime, 온보딩, 마이그레이션 보기, 모양, 화면 시간, 소프트웨어 업데이트, SIM 설치.
건너뛸 화면을 선택하려면 **디바이스 등록** > **Apple 등록** > **등록 프로그램 토큰** > 토큰 선택 > **프로필** > 프로필 선택 > **속성** > **설정 도우미 사용자 지정** > 건너뛸 화면의 **숨기기** 선택 > **확인**으로 이동합니다.
새 프로필을 만들거나 프로필을 편집하는 경우 선택한 건너뛰기 화면이 Apple MDM 서버와 동기화되어야 합니다. 사용자는 프로필 변경 내용을 선택하는 데 지연이 발생하지 않도록 디바이스의 수동 동기화를 발행할 수 있습니다.

#### <a name="android-enterprise-app-we-app-deployment----1171203---"></a>Android 엔터프라이즈 APP-WE 앱 배포 <!-- 1171203 -->
등록되지 않은 APP-WE(등록이 없는 앱 보호 정책) 배포 시나리오에 있는 Android 디바이스의 경우 관리형 Google Play를 사용하여 스토어 앱 및 LOB 앱을 사용자에게 배포할 수 있습니다. 특히 최종 사용자에게 알 수 없는 소스에서 설치를 허용하여 해당 디바이스의 보안 상태를 느슨하게 하도록 더 이상 요구하지 않는 앱 카탈로그 및 설치 환경을 제공할 수 있습니다. 또한 이 배포 시나리오는 향상된 최종 사용자 환경을 제공합니다.

<!-- ########################## -->
## <a name="week-of-january-14-2019"></a>2019년 1월 14일의 주

### <a name="preview-of-support-for-android-corporate-owned-fully-managed-devices----1574342----"></a>Android 회사 소유의 완전 관리형 디바이스 지원에 대한 미리 보기 <!-- 1574342  -->
Intune은 이제 디바이스가 IT 부서에서 긴밀하게 관리되고 개별 사용자와 관련된 회사 소유 "디바이스 소유자" 시나리오인 완전 관리형 Android 디바이스를 지원합니다. 이를 통해 관리자는 전체 디바이스를 관리하고, 확장된 범위의 정책 제어를 회사 프로필에 사용할 수 없게 할 수 있고 사용자가 관리형 Google Play의 앱만 설치하도록 제한합니다. 자세한 내용은 [Android 완전 관리형 디바이스의 Intune 등록 설정](android-fully-managed-enroll.md) 및 [전용 디바이스 또는 완전 관리형 디바이스 등록](android-dedicated-devices-fully-managed-enroll.md)을 참조하세요.  이 기능은 미리 보기에 있습니다. 인증서, 규정 준수 및 조건부 액세스와 같은 일부 Intune 기능은 현재 Android 완전 관리형 사용자 디바이스에서 사용할 수 없습니다.

<!-- ########################## -->
## <a name="week-of-january-7-2019"></a>2019년 1월 7일의 주

### <a name="app-management"></a>앱 관리

#### <a name="intune-app-pin----2298397---"></a>Intune 앱 PIN <!-- 2298397 -->
IT 관리자는 이제 최종 사용자의 Intune 앱 PIN을 변경해야 할 때까지 최종 사용자가 대기할 수 있는 기간(일)을 구성할 수 있습니다. 새 설정은 *다음 일마다 PIN 다시 설정*이며 Azure Portal에서 **Intune** > **클라이언트 앱** > **앱 보호 정책** > **정책 만들기** > **설정** > **액세스 요구 사항**을 선택하여 사용할 수 있습니다. [iOS](app-protection-policy-settings-ios.md) 및 [Android](app-protection-policy-settings-android.md) 디바이스에서 사용 가능하며, 이 기능은 양의 정수 값을 지원합니다.


#### <a name="intune-device-reporting-fields----2748738---"></a>Intune 디바이스 보고 필드 <!-- 2748738 -->
Intune은 앱 등록 ID, Android 제조업체, 모델 및 보안 패치 버전을 포함한 추가 디바이스 보고 필드와 iOS 모델을 제공합니다. Intune에서 이러한 필드를 사용하려면 **클라이언트 앱** > **앱 보호 상태**를 선택하고 **앱 보호 보고서: iOS, Android**를 선택합니다. 또한 이러한 매개 변수를 사용하여 디바이스 제조업체(Android)의 **허용** 목록, 디바이스 모델(Android 및 iOS)의 **허용** 목록 및 최소 Android 보안 패치 버전 설정을 구성할 수 있습니다. 


### <a name="device-configuration"></a>디바이스 구성

#### <a name="administrative-templates-are-in-public-preview-and-moved-to-their-own-configuration-profile----3322847---"></a>관리 템플릿은 공개 미리 보기로 있으며 자체 구성 프로필로 이동됨 <!-- 3322847 -->

Intune의 관리 템플릿(**디바이스 구성** > **관리 템플릿**)은 현재 공개 미리 보기로 있습니다. 이 업데이트 포함:

- 관리 템플릿에는 Intune에서 관리할 수 있는 약 300개 설정이 포함됩니다. 이전에는 이러한 설정이 그룹 정책 편집기에만 있었습니다.
- 관리 템플릿은 공개 미리 보기로 제공됩니다.
- 관리 템플릿은 **디바이스 구성** > **관리 템플릿**에서 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10 이상** 선택, **프로필 유형**에서 **관리 템플릿** 선택으로 이동됩니다.
- 보고가 사용하도록 설정됩니다.

이 기능에 대해 자세히 알아보려면 [그룹 정책 설정을 구성하기 위한 Windows 10 템플릿](administrative-templates-windows.md)으로 이동합니다.

적용 대상: Windows 10 이상

#### <a name="use-smime-to-encrypt-and-sign-multiple-devices-for-a-user-----1333642---"></a>S/MIME를 사용하여 사용자에 대한 여러 디바이스 암호화 및 서명  <!-- 1333642 -->
이 업데이트에는 가져온 새 인증서 프로필을 사용하는 S/MIME 이메일 암호화가 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** &gt; 플랫폼 선택 &gt; **PKCS 가져온 인증서** 프로필 유형). Intune에서 PFX 형식의 인증서를 가져올 수 있습니다. 그런 다음, Intune은 단일 사용자에 의해 등록된 여러 디바이스에 이러한 동일한 인증서를 제공할 수 있습니다. 다음도 포함되어 있습니다.
- 네이티브 iOS 이메일 프로필은 PFX 형식의 가져온 인증서를 사용하는 S/MIME 암호화 활성화를 지원합니다.
- Windows Phone 10 디바이스의 네이티브 메일 앱은 S/MIME 인증서를 자동으로 사용합니다.
- 여러 플랫폼에서 프라이빗 인증서를 제공할 수 있습니다. 하지만 모든 이메일 앱이 S/MIME를 지원하지는 않습니다.
- 다른 플랫폼에서 S/MIME를 활성화하도록 메일 앱을 수동으로 구성해야 할 수 있습니다.  
- S/MIME 암호화를 지원하는 이메일 앱은 해당 게시자의 인증서 저장소에서 읽기와 같은 MDM에서 지원할 수 없는 방식으로 S/MIME 이메일 암호화에 대한 인증서 가져오기를 처리할 수 있습니다.
이 기능에 대한 자세한 내용은 [이메일 서명 및 암호화를 위한 S/MIME 개요](certificates-s-mime-encryption-sign.md)를 참조하세요.
지원 됩니다. Windows, Windows Phone 10, macOS, iOS, Android

#### <a name="new-options-to-automatically-connect-and-persist-rules-when-using-dns-settings-on-windows-10-and-later-devices----1333665-2999078---"></a>Windows 10 이상 디바이스에서 DNS 설정을 사용할 때 자동으로 규칙을 연결하고 유지하는 새 옵션 <!-- 1333665, 2999078 -->
Windows 10 이상 디바이스에서는 contoso.com과 같은 도메인 확인을 위한 DNS 서버 목록을 포함하는 VPN 구성 프로필을 만들 수 있습니다. 이 업데이트에는 이름 확인(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **Windows 10 이상** 선택 > 프로필 유형에서 **VPN** 선택 > **DNS 설정** >**추가**)에 대한 새 설정이 포함됩니다. 
- **자동으로 연결**: **사용하도록 설정**한 경우 디바이스가 입력한 도메인(예: contoso.com)에 연결되면 디바이스가 자동으로 VPN에 연결됩니다.
- **영구**: 기본적으로 모든 NRPT(이름 확인 정책 테이블) 규칙은 디바이스가 이 VPN 프로필을 사용하여 연결되어 있는 한 활성 상태입니다. NRPT 규칙에서 이 설정이 **사용하도록 설정**되면 VPN 연결이 끊어지더라도 디바이스에서 규칙이 활성 상태로 유지됩니다. 규칙은 VPN 프로필이 제거되거나 PowerShell을 통해 규칙을 수동으로 제거할 때까지 유지됩니다.
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에서는 설정을 설명합니다. 

#### <a name="use-trusted-network-detection-for-vpn-profiles-on-windows-10-devices----1500165---"></a>Windows 10 디바이스의 VPN 프로필에 신뢰할 수 있는 네트워크 검색 사용 <!-- 1500165 -->
신뢰할 수 있는 네트워크 검색을 사용하는 경우 사용자가 이미 신뢰할 수 있는 네트워크에 있을 때 VPN 프로필에서 자동으로 VPN에 연결되지 않도록 할 수 있습니다. 이 업데이트를 사용하여 DNS 접미사를 추가하여 Windows 10 이상을 실행하는 디바이스에서 신뢰할 수 있는 네트워크 검색을 사용하도록 설정할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼의 **Windows 10 이상** > 프로필 유형의 **VPN**).
[Windows 10 VPN 설정](vpn-settings-windows-10.md)에는 현재 VPN 설정이 나열됩니다.

#### <a name="manage-windows-holographic-for-business-devices-used-by-multiple-users----1907917-1063203---"></a>여러 사용자가 사용하는 Windows Holographic for Business 디바이스 관리 <!-- 1907917, 1063203 -->
현재는 사용자 지정 OMA-URI 설정을 사용하여 Windows 10 및 Windows Holographic for Business 디바이스에서 공유 PC 설정을 구성할 수 있습니다. 이 업데이트를 사용하여 새 프로필을 추가하여 공유 디바이스 설정을 구성합니다(**디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10 이상** > **공유 다중 사용자 디바이스**).
이 기능에 대해 자세히 알아보려면 [공유 디바이스를 관리하기 위한 Intune 설정](shared-user-device-settings.md)으로 이동합니다.
적용 대상: Windows 10 이상, Windows Holographic for Business

#### <a name="new-windows-10-update-settings---2626030--2512994----"></a>새 Windows 10 업데이트 설정 <!--2626030  2512994  -->
[Windows 10 업데이트 링](windows-update-for-business-configure.md)의 경우 다음을 구성할 수 있습니다.
- **자동 업데이트 동작** - 새 옵션 사용, *2018년 10월 업데이트*를 실행 중인 머신의 Windows 10 머신에서 원래 자동 업데이트 설정을 복원하도록 *기본값으로 다시 설정*
- **사용자가 Windows 업데이트를 일시 중지하는 것을 차단** - 사용자가 머신의 *설정*에서 업데이트 설치를 일시 중지하는 기능을 차단 또는 허용할 수 있는 새 소프트웨어 업데이트 설정 구성 

#### <a name="ios-email-profiles-can-use-smime-signing-and-encryption----2662949---"></a>iOS 이메일 프로필에서 S/MIME 서명 및 암호화를 사용할 수 있음 <!-- 2662949 -->
다양한 설정을 포함하는 이메일 프로필을 만들 수 있습니다. 이 업데이트에는 iOS 디바이스에서 이메일 통신 서명 및 암호화에 사용할 수 있는 S/MIME 설정이 포함됩니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **이메일**).
[iOS 이메일 구성 설정](email-settings-ios.md)에는 설정이 나열됩니다.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition---2727036---"></a>일부 BitLocker 설정에서 Windows 10 Pro 버전을 지원함<!-- 2727036 -->
BitLocker를 포함하여 Windows 10 디바이스에서 엔드포인트 보호 설정을 설정하는 구성 프로필을 만들 수 있습니다. 이 업데이트는 일부 BitLocker 설정에 대한 Windows 10 Professional Edition 지원을 추가합니다. 이러한 보호 설정을 보려면 [Windows 10용 엔드포인트 보호 설정](endpoint-protection-windows-10.md#windows-encryption)으로 이동합니다.

#### <a name="shared-device-configuration-is-renamed-to-lock-screen-message-for-ios-devices-in-the-azure-portal---2809362---"></a>공유 디바이스 구성의 이름이 Azure Portal에서 iOS 디바이스에 대한 잠금 화면 메시지로 변경됨<!-- 2809362 -->
iOS 디바이스용 구성 프로필을 만들 경우 **공유 디바이스 구성** 설정을 추가하여 잠금 화면에 특정 텍스트를 표시할 수 있습니다. 이 업데이트에는 다음 변경 내용이 포함됩니다. 
- Azure Portal의 **공유 디바이스 구성** 설정은 “잠금 화면 메시지(감독 모드인 경우에만)”으로 이름이 바뀝니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에서 **iOS** 선택 > 프로필 유형에서 **디바이스 기능** 선택 > **잠금 화면 메시지**).
- 잠금 화면 메시지를 추가하면 일련 번호, 디바이스 이름 또는 또 다른 디바이스별 값을 **자산 태그 정보** 및 **잠금 화면 각주**의 변수로 삽입할 수 있습니다. 예를 들어 중괄호를 사용하여 `Device name: {{devicename}}` 또는 `Serial number is {{serialnumber}}`를 입력할 수 있습니다. [iOS 토큰](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 사용 가능한 토큰이 나열됩니다.
[잠금 화면에 메시지를 표시하기 위한 설정](shared-device-settings-ios.md)에는 설정이 나열됩니다.

#### <a name="new-app-store-doc-viewing-gaming-device-restriction-settings-added-to-ios-devices----2827760--"></a>iOS 디바이스에 앱 스토어, 문서 보기, 게임 디바이스 제한 설정이 새로 추가됨 <!-- 2827760-->
**디바이스 구성** > **프로필** > **프로필 만들기** > **iOS** 플랫폼에 대해 > **디바이스 제한** 프로필 유형에 대해 > **앱 스토어, 문서 보기, 게임**에서 다음 설정이 추가되었습니다. 관리되는 앱이 관리되지 않는 연락처 계정에 연락처를 쓸 수 있도록 허용. 관리되지 않는 앱이 관리되는 연락처 계정에서 연락처를 읽을 수 있도록 허용. 이러한 설정을 보려면 [iOS 디바이스 제한 사항](device-restrictions-ios.md#app-store-doc-viewing-gaming)으로 이동합니다.

#### <a name="new-notification-hints-and-keyguard-settings-to-android-enterprise-device-owner-devices----3201839-3201843---"></a>Android Enterprise 디바이스 소유자 디바이스에 대한 새로운 알림, 힌트 및 keyguard 설정 <!-- 3201839 3201843 -->
이 업데이트에는 디바이스 소유자로 실행할 경우 Android 엔터프라이즈 디바이스의 여러 가지 새로운 기능이 포함됩니다. 이러한 기능을 사용하려면 **디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Android 엔터프라이즈** 선택 > **프로필 유형**에서 **디바이스 소유자만** 선택 > **디바이스 제한 사항**으로 이동합니다.

새로운 기능은 다음과 같습니다. 

- 들어오는 호출, 시스템 경고, 시스템 오류 등을 포함하여 시스템 알림이 표시되지 않도록 설정
- 처음 열린 앱에 대한 시작 자습서 및 힌트 건너뛰기 제안
- 카메라, 알림, 지문 잠금 해제 등의 고급 Keyguard 설정을 사용하지 않도록 설정


설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

#### <a name="android-enterprise-device-owner-devices-can-use-always-on-vpn-connections----3202194---"></a>Android Enterprise 디바이스 소유자 디바이스에서 Always On VPN 연결을 사용할 수 있음 <!-- 3202194 -->
이 업데이트에서는 Android 엔터프라이즈 디바이스 소유자 디바이스에서 Always on VPN 연결을 사용할 수 있습니다. 상시 VPN 연결은 계속 연결된 상태로 유지되거나 사용자가 디바이스를 잠금 해제한 경우, 디바이스가 다시 시작된 경우 또는 무선 네트워크가 변경된 경우 바로 다시 연결됩니다. 또한 VPN 연결이 활성화될 때까지 모든 네트워크 트래픽을 차단하는 “잠금” 모드로 연결 상태를 전환할 수도 있습니다.
**디바이스 구성** > **프로필** > **프로필 만들기** > **Android 엔터프라이즈**(플랫폼) > **디바이스 제한 사항**(디바이스 소유자만) > **연결** 설정에서 Always-on VPN을 사용하도록 설정할 수 있습니다. 설정을 보려면 [Android 엔터프라이즈 디바이스 제한 사항 설정](device-restrictions-android-for-work.md)으로 이동합니다.

#### <a name="new-setting-to-end-processes-in-task-manager-on-windows-10-devices----3285177---"></a>Windows 10 디바이스의 작업 관리자에서 프로세스를 종료하는 새로운 설정 <!-- 3285177 --> 
이 업데이트에는 Windows 10 디바이스의 작업 관리자를 사용하여 프로세스를 종료하는 새로운 설정이 포함됩니다. 디바이스 구성 프로필(**디바이스 구성** > **프로필** > **프로필 만들기** > **플랫폼**에서 **Windows 10** 선택 > **프로필 유형**에서 **디바이스 제한 사항** 선택 > **일반** 설정)을 사용하여 이 설정을 허용하거나 차단하도록 선택합니다.
이러한 설정을 보려면 [Windows 10 디바이스 제한 사항 설정](device-restrictions-windows-10.md)으로 이동합니다.
적용 대상: Windows 10 이상


### <a name="device-enrollment"></a>디바이스 등록

#### <a name="more-detailed-enrollment-restriction-failure-messaging----3111564---"></a>자세한 등록 제한 오류 메시징 <!-- 3111564 -->
등록 제한 사항이 충족되지 않으면 더 자세한 오류 메시지가 제공됩니다. 이러한 메시지를 보려면 **Intune** > **문제 해결**로 이동하고 등록 실패 테이블을 확인합니다. 자세한 내용은 [등록 실패 목록](help-desk-operators.md#enrollment-failure-reference)을 참조하세요.

### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="tenant-status-dashboard-----1124854---"></a>테넌트 상태 대시보드  <!-- 1124854 -->
새 [테넌트 상태 페이지](tenant-status.md)는 테넌트에 대한 상태와 관련된 세부 정보를 볼 수 있는 단일 위치를 제공합니다.  대시보드는 4개 영역으로 구분됩니다.
- **테넌트 세부 정보** - 테넌트 이름 및 위치, MDM 권한, 테넌트에 등록된 총 디바이스 수, 라이선스 수를 포함하는 정보를 포함합니다. 이 섹션은 테넌트에 대한 현재 서비스 릴리스도 나열합니다.
- **커넥터 상태** - 사용자가 구성한 사용 가능한 커넥터에 대한 정보를 표시하고 아직 활성화하지 않은 항목도 나열할 수 있습니다.  
   각 커넥터의 현재 상태에 따라 정상, 경고 또는 비정상으로 플래그가 지정됩니다. 커넥터를 선택하여 세부 정보를 드릴스루하고 보거나 추가 정보를 구성합니다.
- **Intune Service Health** - 테넌트의 활성 인시던트 또는 중단 상태에 대한 세부 정보를 표시합니다. 이 섹션의 정보는 Office Message Center에서 직접 검색됩니다.
- **Intune 뉴스** - 테넌트에 대한 활성 메시지를 표시합니다. 메시지는 테넌트에서 최신 Intune 기능을 받는 경우 알림과 같은 항목을 포함합니다.  이 섹션의 정보는 Office Message Center에서 직접 검색됩니다.

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10----1488939--"></a>Windows 10용 회사 포털의 새로운 도움말 및 지원 환경 <!-- 1488939-->
새 회사 포털 도움말 및 지원 페이지는 사용자가 문제를 해결하고 앱 및 액세스 문제에 대한 도움을 요청하는 데 도움이 됩니다. 새 페이지에서 오류 및 진단 로그 세부 정보에 대한 이메일을 보내고 해당 조직의 기술 지원팀 세부 정보를 찾을 수 있습니다. 또한 관련 Intune 설명서에 대한 링크를 사용하여 FAQ 섹션을 찾을 수도 있습니다. 

#### <a name="new-help-and-support-experience-for-intune------3307080---"></a>Intune에 대한 새로운 도움말 및 지원 환경   <!-- #3307080 -->
다음 며칠 동안 새 도움말 및 지원 환경을 모든 테넌트에게 롤아웃합니다. 이 새로운 환경은 Intune에 대해 사용할 수 있으며 [Azure Portal](https://portal.azure.com/)에서 Intune 블레이드를 사용하는 경우에 액세스할 수 있습니다.
새 환경을 사용하면 문제를 사용자 고유의 언어로 설명하고, 문제 해결 인사이트와 웹 기반 수정 콘텐츠를 받을 수 있습니다. 이러한 솔루션은 사용자 문의에 따라 구동되는 규칙 기반 기계 학습 알고리즘을 통해 제공됩니다. 문제별 지침 외에도 새 사례 만들기 워크플로를 사용하여 이메일 또는 전화를 통해 지원 사례를 엽니다. 이 새로운 환경은 도움말 및 지원을 열 때 제공되는 콘솔의 영역에 따라 미리 선택된 옵션의 정적 집합에 대한 이전의 도움말 및 지원 환경을 대체합니다. 자세한 내용은 [Microsoft Intune에 대한 지원을 받는 방법](get-support.md)을 참조하세요.

### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="scope-tags-for-apps----1081941---"></a>앱에 대한 범위 태그 <!-- 1081941 -->
범위 태그를 만들어 역할 및 앱에 대한 액세스를 제한할 수 있습니다. 해당 범위 태그가 할당된 역할이 있는 사용자만 앱에 액세스할 수 있도록 앱에 범위 태그를 추가할 수 있습니다. 현재는 관리되는 Google Play에서 Intune에 추가된 앱 또는 Apple VPP(Volume Purchase Program)를 통해 구매한 앱에는 범위 태그를 할당할 수 없습니다(향후 지원될 예정임). 자세한 내용은 [범위 태그를 사용하여 정책 필터링](scope-tags.md)을 참조하세요.

## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]
