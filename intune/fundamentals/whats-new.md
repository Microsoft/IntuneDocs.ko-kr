---
title: Microsoft Intune의 새로운 기능 - Azure | Microsoft Docs
titleSuffix: ''
description: Intune Azure 포털의 새로운 기능 알아보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 791ed23f-bd13-4ef0-a3dd-cd2d7332c5cc
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7018e2ab4290219c752f44b4b391822438461e8e
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415076"
---
# <a name="whats-new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

매주 Microsoft Intune에 추가되는 새로운 기능에 대해 알아봅니다. 또한 [중요한 공지](#notices), [과거 릴리스](whats-new-archive.md) 및 [Intune 서비스 업데이트가 릴리스되는 방법](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)에 관한 정보도 찾을 수 있습니다. 

> [!Note]
> 각 [월별 업데이트](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Microsoft-Intune-Service-Updates/ba-p/358728)는 출시에 최대 3일이 걸릴 수 있고 다음 순서로 출시됩니다.
>
> - 1일: 아시아 태평양(APAC)
> - 2일: 유럽, 중동, 아프리카(EMEA)
> - 3일: 북아메리카
> - 4일 이후: Intune for Government
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
## <a name="week-of-february-10-2020"></a>2020년 2월 10일이 포함된 주

### <a name="windows-7-ends-extended-support---3042987--"></a>Windows 7 확장 지원 종료 <!--3042987-->
Windows 7은 2020년 1월 14일부로 확장 지원이 종료되었습니다. Intune은 Windows 7 동시 실행 디바이스를 지원하지 않습니다. PC 보호에 유용한 기술 지원과 자동 업데이트를 더 이상 사용할 수 없습니다. Windows 10으로 업그레이드해야 합니다. 자세한 내용은 [변경 계획 블로그 게시물](https://aka.ms/Windows7_Intune)을 참조하세요.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="microsoft-edge-version-77-and-later-on-windows-10-devices---5843584---"></a>Windows 10 디바이스에서 Microsoft Edge 버전 77 이상<!-- 5843584 -->
이제 Intune은 Windows 10 디바이스에서 Microsoft Edge 버전 77 이상 제거를 지원합니다. 자세한 내용은 [Microsoft Intune에 Microsoft Edge for Windows 10 추가](~/apps/apps-windows-edge.md)를 참조하세요.

#### <a name="screen-removed-from-company-portal-android-work-profile-enrollment--6103987---"></a>회사 포털에서 화면이 제거됨, Android 회사 프로필 등록<!--6103987 -->
사용자 환경을 간소화하기 위해 **다음 단계** 화면이 회사 포털의 Android 회사 프로필 등록 흐름에서 제거되었습니다. [Android 회사 프로필에 등록](/intune-user-help/enroll-device-android-work-profile)으로 이동하여 업데이트된 Android 회사 프로필 등록 흐름을 확인합니다.  

#### <a name="company-portal-app-improved-performance---6178652---"></a>회사 포털 앱 향상된 성능<!-- 6178652 -->
Surface Pro X와 같이 ARM64 프로세서를 사용하는 디바이스의 향상된 성능을 지원하도록 회사 포털 앱이 업데이트되었습니다. 이전에는 에뮬레이트된 ARM32 모드에서 회사 포털이 작동했습니다. 이제 버전 10.4.7080.0 이상의 회사 포털 앱은 기본적으로 ARM64에 대해 컴파일됩니다. 회사 포털 앱에 대한 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](~/apps/company-portal-app.md)을 참조하세요.

<!-- ########################## -->
## <a name="week-of-january-27-2020"></a>2020년 1월 27일이 포함된 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="intune-support-for-additional-microsoft-edge-version-77-deployment-channel-for-macos---5983950----"></a>macOS용 추가 Microsoft Edge 버전 77 배포 채널에 대한 Intune 지원<!-- 5983950  -->
이제 Microsoft Intune은 macOS용 Microsoft Edge 앱을 위한 **안정적인** 추가 배포 채널을 지원합니다. **안정** 채널은 엔터프라이즈 환경에서 Microsoft Edge를 광범위하게 배포할 때 권장되는 채널입니다. 6주마다 업데이트되는 각 릴리스는 **Beta** 채널의 향상된 기능을 통합합니다. **안정** 채널과 **Beta** 채널 외에도 Intune은 **Dev** 채널을 지원합니다. 공개 미리 보기는 macOS용 Microsoft Edge 버전 77 이상을 위한 안정 채널과 Dev 채널을 제공합니다. 브라우저의 자동 업데이트가 기본적으로 켜져 있습니다. 자세한 내용은 [Microsoft Intune을 사용하여 macOS 디바이스에 Microsoft Edge 추가](~/apps/apps-edge-macos.md)를 참조하세요.

#### <a name="retirement-of-intune-managed-browser--5728447---"></a>Intune Managed Browser 사용 중지<!--5728447 -->
Intune Managed Browser가 사용 중지됩니다. 보호된 Intune 브라우저 환경에서 Microsoft Edge를 사용하세요. 자세한 내용은 아래 [알림](~/fundamentals/whats-new.md#notices) 섹션의 ‘[조치 취하기: 보호된 Intune 브라우저 환경에서 Microsoft Edge 사용](~/fundamentals/whats-new.md#take-action-use-microsoft-edge-for-your-protected-intune-browser-experience)’ 항목을 참조하세요.

<!-- ########################## -->
## <a name="week-of-january-20-2020-2001-service-release"></a>2020년 1월 20일이 포함된 주(2001 서비스 릴리스)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="user-experience-change-when-adding-apps-to-intune---4705829-----"></a>Intune에 앱 추가 시 사용자 환경 변경<!-- 4705829   -->
Intune을 통해 앱을 추가할 때 새로운 사용자 환경이 표시됩니다. 이 환경은 이전에 사용했던 것과 동일한 설정 및 세부 정보를 제공하지만 새로운 환경에서는 앱을 Intune에 추가하기 전에 마법사와 비슷한 프로세스를 따릅니다. 이 새로운 환경에서는 앱 추가 전에 검토 페이지도 제공합니다. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **모든 앱** > **추가**를 선택합니다. 자세한 내용은 [Microsoft Intune에 앱 추가](~/apps/apps-add.md)를 참조하세요.

#### <a name="require-win32-apps-to-restart----5622282-----"></a>Win32 앱을 다시 시작해야 함 <!-- 5622282   -->
Win32 앱이 설치된 후 다시 시작하도록 지정할 수 있습니다. 또한 다시 시작해야 할 때까지의 시간(유예 기간)을 선택할 수 있습니다.

#### <a name="user-experience-change-when-configuring-apps-in-intune---4207990-----"></a>Intune에서 앱 구성 시 사용자 환경 변경<!-- 4207990   -->
Intune에서 앱 구성 정책을 만들 때 새로운 사용자 환경이 표시됩니다. 이 환경은 이전에 사용했던 것과 동일한 설정 및 세부 정보를 제공하지만 새로운 환경에서는 정책을 Intune에 추가하기 전에 마법사와 비슷한 프로세스를 따릅니다. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **앱 구성 정책** > **추가**를 선택합니다. 자세한 내용은 [Microsoft Intune용 앱 구성 정책](~/apps/app-configuration-policies-overview.md)을 참조하세요. 

#### <a name="intune-support-for-additional-microsoft-edge-for-windows-10-deployment-channel---5861774---"></a>Windows 10용 Microsoft Edge 추가 배포 채널에 대한 Intune 지원<!-- 5861774 -->
이제 Microsoft Intune은 Windows 10용 Microsoft Edge(버전 77 이상) 앱을 위한 **안정적인** 추가 배포 채널을 지원합니다. **안정** 채널은 엔터프라이즈 환경에서 Windows 10용 Microsoft Edge를 광범위하게 배포할 때 권장되는 채널입니다. 6주마다 업데이트되는 각 릴리스는 **Beta** 채널의 향상된 기능을 통합합니다. **안정** 채널과 **Beta** 채널 외에도 Intune은 **Dev** 채널을 지원합니다. 자세한 내용은 [Windows 10용 Microsoft Edge - 앱 설정 구성](~/apps/apps-windows-edge.md#configure-app-settings)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>디바이스 구성

#### <a name="improved-user-interface-experience-when-configuring-exchange-activesync-on-premises-connector-ui---5695492-----"></a>Exchange ActiveSync 온-프레미스 커넥터 UI 구성 시 향상된 사용자 인터페이스 환경<!-- 5695492   -->
[Exchange ActiveSync 온-프레미스 커넥터 UI 구성](../protect/exchange-connector-install.md)을 위한 환경이 업데이트되었습니다. 업데이트된 환경에서는 단일 창을 사용하여 온-프레미스 커넥터의 세부 정보를 구성, 편집, 요약합니다. 

#### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-----"></a>Android Enterprise 회사 프로필의 Wi-Fi 프로필에 자동 프록시 설정 추가<!-- 4490822   -->
Android Enterprise 회사 프로필 디바이스에서 Wi-Fi 프로필을 만들 수 있습니다. Wi-Fi Enterprise 유형을 선택하면 Wi-Fi 네트워크에서 사용되는 EAP(확장할 수 있는 인증 프로토콜) 유형을 입력할 수도 있습니다.

이제 Enterprise 유형을 선택하면 `proxy.contoso.com`과 같은 프록시 서버 URL을 비롯한 자동 프록시 설정을 입력할 수도 있습니다.

구성할 수 있는 현재 Wi-Fi 설정을 보려면 [Microsoft Intune에서 Android Enterprise 및 Android 키오스크를 실행하는 디바이스의 Wi-Fi 설정 추가](../configuration/wi-fi-settings-android-enterprise.md)로 이동합니다.

적용 대상:
- Android Enterprise 회사 프로필

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-enrollment"></a>디바이스 등록

#### <a name="block-android-enrollments-by-device-manufacturer--5197392----"></a>디바이스 제조업체별 Android 등록 차단<!--5197392  -->
디바이스의 제조업체를 기준으로 디바이스 등록을 차단할 수 있습니다. Android 디바이스 관리자 및 Android Enterprise 회사 프로필 디바이스에 적용됩니다. 등록 제한을 보려면 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431) > **디바이스** > **등록 제한**으로 이동합니다.

#### <a name="improvements-to-the-iosipados-create-enrollment-type-profile-ui---6055005---"></a>iOS/iPadOS 등록 유형 프로필 만들기 UI의 향상된 기능<!-- 6055005 -->
iOS/iPadOS 사용자 등록의 경우 **등록 유형 프로필 만들기** **설정** 페이지가 간소화되어 동일한 기능을 유지하면서 **등록 유형** 선택 프로세스가 향상되었습니다. 새 UI를 보려면 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431) > **디바이스** > **iOS** > **iOS 등록** > **등록 유형** > **프로필 만들기** > **설정** 페이지로 이동합니다. 자세한 내용은 [Intune에서 사용자 등록 프로필 만들기](../enrollment/ios-user-enrollment.md#create-a-user-enrollment-profile-in-intune)를 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="new-information-in-device-details---4471759-5604099----"></a>디바이스 세부 정보의 새로운 정보<!-- 4471759 5604099  -->
이제 디바이스의 **개요** 페이지에 다음 정보가 제공됩니다.
- 메모리 용량(디바이스의 실제 메모리 양)
- 스토리지 용량(디바이스의 실제 스토리지 양) 
- CPU 아키텍처


#### <a name="ios-bypass-activation-lock-remote-action-renamed-to-disable-activation-lock---5904591----"></a>iOS 활성화 잠금 무시 원격 작업의 이름이 활성화 잠금 사용 안 함으로 변경됨 <!--5904591  -->
**활성화 잠금 무시** 원격 작업의 이름이 **활성화 잠금 사용 안 함**으로 변경되었습니다. 자세한 내용은 [Intune에서 iOS 활성화 잠금 사용 안 함](../remote-actions/device-activation-lock-bypass.md)을 참조하세요.

#### <a name="windows-10-feature-update-deployment-support-for-autopilot-devices---5948137-----"></a>Autopilot 디바이스에 대한 Windows 10 기능 업데이트 배포 지원<!-- 5948137   -->
이제 Intune에서 [Windows 10 기능 업데이트 배포](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)를 사용하여 Autopilot 등록 디바이스를 대상으로 지정할 수 있습니다.

Windows 10 기능 업데이트 정책은 Autopilot OOBE(첫 실행 경험) 중에 적용될 수 없으며, 디바이스가 프로비저닝을 완료한 후(일반적으로 하루) 첫 번째 Windows 업데이트 검사 시에만 적용됩니다.


<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="windows-autopilot-deployment-reports-preview----3856172-----"></a>Windows AutoPilot 배포 보고서(미리 보기) <!-- 3856172   -->
새 보고서는 Windows Autopilot을 통해 배포된 각 디바이스에 대해 자세히 설명합니다. 자세한 내용은 [Autopilot 배포 보고서](../enrollment/enrollment-autopilot.md#autopilot-deployments-report)를 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-----"></a>새로운 Intune 기본 제공 역할 엔드포인트 보안 관리자<!--4253397   -->
새로운 Intune 기본 제공 역할인 엔드포인트 보안 관리자를 사용할 수 있습니다. 이 새로운 역할은 관리자에게 Intune의 엔드포인트 관리자 노드에 대한 모든 권한을 부여하고 다른 영역에 대한 읽기 전용 액세스를 제공합니다. 이 역할은 Azure AD의 "보안 관리자" 역할을 확장한 것입니다. 현재 역할이 전역 관리자인 경우 변경이 필요하지 않습니다. 엔드포인트 보안 관리자가 제공하는 세부 역할을 사용하려면 해당 역할이 제공된 뒤 해당 역할을 할당하세요. 기본 제공 역할에 대한 자세한 내용은 [역할 기반 액세스 제어](role-based-access-control.md)를 참조하세요.

<!-- ########################## -->
## <a name="week-of-january-6-2020"></a>2020년 1월 6일이 포함된 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="smime-support-for-microsoft-outlook-for-ios---2669398---"></a>iOS용 Microsoft Outlook의 S/MIME 지원<!-- 2669398 -->
Intune은 iOS 디바이스에서 iOS용 Outlook과 함께 사용할 수 있는 S/MIME 서명 및 암호화 인증서 배달을 지원합니다. 자세한 내용은 [iOS 및 Android용 Outlook의 민감도 레이블 지정 및 보호](https://aka.ms/omsmime)를 참조하세요.

#### <a name="cache-win32-app-content-using-microsoft-connected-cache-server---6030314---"></a>Microsoft Connected 캐시 서버를 사용 중인 캐시 Win32 앱 콘텐츠<!-- 6030314 -->
Intune Win32 앱 콘텐츠를 캐시하기 위해 Configuration Manager 배포 지점에 Microsoft Connected 캐시 서버를 설치할 수 있습니다. 자세한 내용은 [Configuration Manager의 Microsoft Connected Cache-Intune Win32 앱 지원](https://docs.microsoft.com/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="windows-10-administrative-templates-admx-profiles-now-support-scope-tags---5137390---"></a>현재 범위 태그를 지원 중인 Windows 10 관리 템플릿(ADMX) 프로필 <!--5137390 -->
이제는 관리 템플릿 프로필(ADMX)에 범위 태그를 할당할 수 있습니다. 이 작업을 위해서는 **Intune** > **디바이스** > **구성 프로필** > 목록에서 관리 템플릿 프로필 선택 > **속성** > **범위 태그** 순서로 이동합니다. 범위 태그에 대한 자세한 내용은 [다른 개체로 범위 태그 할당](../fundamentals/scope-tags.md#assign-scope-tags-to-other-objects)을 참조하세요.

<!-- ########################## -->
## <a name="week-of-december-30-2019"></a>2019년 12월 30일이 포함된 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="retrieve-personal-recovery-key-from-mem-encrypted-macos-devices---4851745---"></a>MEM 암호화된 macOS 디바이스에서 개인 복구 키 검색<!-- 4851745 -->
최종 사용자는 iOS 회사 포털 앱을 사용하여 개인 복구 키(FileVault 키)를 검색할 수 있습니다. 개인 복구 키를 포함한 디바이스는 Intune에 등록하고 Intune을 통한 FileVault로 암호화해야 합니다. iOS 회사 포털 앱을 사용하면 최종 사용자는 **복구 키 가져오기**를 클릭해 암호화된 macOS 디바이스에서 개인 복구 키를 검색할 수 있습니다. Intune에서 **디바이스** > *암호화되어 등록된 macOS 디바이스* > **복구 키 가져오기**를 선택하여 복구 키를 검색할 수도 있습니다. FileVault에 대한 자세한 내용은 [macOS용 FileVault 암호화](~/protect/encrypt-devices.md#filevault-encryption-for-macos)를 참조하세요.

#### <a name="ios-and-ipados-user-licensed-vpp-apps---5619268---"></a>iOS 및 iPadOS 사용자에게 사용이 허가된 VPP 앱<!-- 5619268 -->
사용자가 등록한 iOS 및 iPadOS 디바이스의 경우 최종 사용자에게는 디바이스에서 사용이 허가된 신규 생성 VPP 앱 배포를 이용할 수 있다는 메시지가 더 이상 표시되지 않습니다. 그러나 회사 포털에서는 최종 사용자가 사용자에게 사용이 허가된 모든 VPP 앱을 계속 볼 수 있습니다. VPP 앱에 대한 자세한 내용은 [Microsoft Intune을 사용하여 Apple Volume Purchase Program을 통해 구매한 iOS 및 macOS 앱을 관리하는 방법](~/apps/vpp-apps-ios.md)을 참조하세요.

<!-- ########################## -->
## <a name="week-of-december-23-2019"></a>2019년 12월 23일이 포함된 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="notice---windows-10-1703-rs2-will-be-moving-out-of-support----5026679---"></a>알림 - Windows 10 1703(RS2)의 지원 종료 <!-- 5026679 -->
2018년 10월 9일부터 Microsoft 플랫폼의 Home, Pro, Pro for Workstations 에디션용 Windows 10 1703(RS2)의 지원이 중단되었습니다. Windows 10 Enterprise 및 Education 에디션의 경우 2019년 10월 8일부터 Windows 10 1703(RS2)의 지원이 중단되었습니다. 2019년 12월 26일부터 Windows 회사 포털 애플리케이션을 최소 Windows 10 1709(RS3)으로 업데이트할 예정입니다. 1709 이전 버전으로 실행되는 컴퓨터는 Microsoft Store에서 업데이트된 버전의 애플리케이션을 받을 수 없습니다. 이 변경 사항은 메시지 센터를 통해 Windows 10의 이전 버전을 사용하는 사용자에게 전달되었습니다. 자세한 내용은 [Windows 수명 주기 팩트 시트](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)를 참조하세요.

<!-- ########################## -->

## <a name="week-of-december-16-2019"></a>2019년 12월 16일이 포함된 주

### <a name="device-configuration"></a>디바이스 구성

#### <a name="updates-to-administrative-templates-for-windows-10-devices----5941568---"></a>Windows 10 디바이스용 관리 템플릿 업데이트 <!-- 5941568 -->

Microsoft Intune의 ADMX 템플릿을 사용해 Microsoft Edge, Office, Windows의 설정을 제어하고 관리할 수 있습니다. Intune의 관리 템플릿에 다음과 같은 정책 설정이 업데이트되었습니다.

- Microsoft Edge 버전 78 및 79 지원 추가
- [관리 템플릿 파일(ADMX/ADML) 및 Office 365 ProPlus, Office 2019, Office 2016용 Office 사용자 지정 도구](https://www.microsoft.com/download/details.aspx?id=49030)에 2019년 11월 11일의 ADMX 파일 포함

Intune의 ADMX 템플릿에 대한 자세한 내용은 [Windows 10 템플릿을 사용해 Microsoft Intune의 그룹 정책 설정 구성하기](../configuration/administrative-templates-windows.md)를 참조하세요.

적용 대상:

- Windows 10 이상

## <a name="week-of-december-9-2019-1912-service-release"></a>2019년 12월 9일이 포함된 주(1912 서비스 릴리스)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="migrating-to-microsoft-edge-for-managed-browsing-scenarios---5173762---"></a>관리되는 검색 시나리오를 위해 Microsoft Edge로 마이그레이션<!-- 5173762 -->
Intune Managed Browser가 점차 사용 중지되는 상황에서 사용자를 Edge로 이동하는 데 필요한 단계를 간소화하기 위해 앱 보호 정책을 변경했습니다. 앱 보호 정책 설정 **다른 앱을 사용한 웹 콘텐츠 전송 제한**에 대한 옵션을 다음 중 하나로 업데이트했습니다.

- 모든 앱
- Intune Managed Browser
- Microsoft Edge
- 관리되지 않는 브라우저 

**Microsoft Edge**를 선택하면 관리되는 검색 시나리오에 Microsoft Edge가 필요하다는 액세스 조건 메시지가 최종 사용자에게 표시됩니다. 해당 AAD 계정으로 Microsoft Edge를 다운로드하여 로그인하라는 메시지가 표시됩니다(아직 수행하지 않은 경우).  이는 애플리케이션 구성 설정을 사용하여 MAM 지원 앱을 대상으로 `com.microsoft.intune.useEdge`를 **True**로 설정하는 것과 동일합니다. **정책 관리 브라우저** 설정을 사용하는 기존 앱 보호 정책에 이제 **Intune Managed Browser**가 선택되었으며 작동에는 변화가 없습니다. 즉, **useEdge** 앱 구성 설정을 **True**로 설정한 경우 사용자에 게 Microsoft Edge를 사용하라는 메시지가 표시됩니다. 관리되는 검색 시나리오를 활용하는 모든 고객은 **다른 앱을 사용한 웹 콘텐츠 전송 제한**을 포함해 앱 보호 정책을 업데이트하여 연결을 시작하는 앱에 관계없이 사용자가 Microsoft Edge로 전환하기 위한 적절한 지침을 확인하는 것이 좋습니다. 

#### <a name="configure-app-notification-content-for-organization-accounts---2576686----"></a>조직 계정용 앱 알림 콘텐츠 구성<!-- 2576686  -->
Android 및 iOS 디바이스의 Intune 앱 보호 정책(APP)으로 조직 계정용 앱 알림 콘텐츠를 제어할 수 있습니다. 옵션(허용, 조직 데이터 차단, 차단)을 선택해 선택한 앱에서 조직 계정이 표시되는 알림 방식을 지정할 수 있습니다. 이 기능을 사용하려면 애플리케이션에서 지원이 필요하며, APP을 사용하는 모든 애플리케이션에서 사용 가능하지 않을 수 있습니다. iOS 버전 4.15.0 이상을 지원하는 Outlook 및 Android 4.83.0 이상을 지원하는 Outlook은 이 설정을 지원합니다. 콘솔에서도 이 설정을 사용할 수 있지만 해당 기능은 2019년 12월 16일부터 실제 사용이 가능합니다. APP에 대한 자세한 내용은 [앱 보호 정책이란?](../apps/app-protection-policy.md)을 참조하세요.

#### <a name="microsoft-app-icons-update--4677605----"></a>Microsoft 앱 아이콘 업데이트<!--4677605  -->
앱 보호 정책 및 앱 구성 정책을 위한 앱 대상 창 내 Microsoft 앱용 아이콘이 업데이트되었습니다.

#### <a name="require-use-of-approved-keyboards-on-android--4761794----"></a>Android에서 승인된 키보드 필수 사용<!--4761794  -->
앱 보호 정책의 일환으로 [**승인된 키보드**](../apps/app-protection-policy-settings-android.md#data-protection)의 설정을 지정하여 관리되는 Android 앱에서 사용할 수 있는 Android 키보드를 관리할 수 있습니다. 사용자가 관리되는 앱을 열었을 때 사전에 앱에서 승인된 키보드가 없는 경우, 기존에 디바이스에 설치된 승인된 키보드 중 하나로 변경하도록 합니다. 필요한 경우 승인된 키보드의 Google Play 스토어 다운로드 링크를 표시하여 이를 설치하고 설정하도록 합니다. 사용 중인 키보드가 승인된 키보드가 아닐 경우 사용자는 관리되는 앱의 텍스트 필드만 편집이 가능합니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>디바이스 구성

#### <a name="updated-single-sign-on-experience-for-apps-and-websites-on-your-ios-ipados-and-macos-devices---4999578----"></a>iOS, iPadOS, macOS 디바이스의 앱 및 웹 사이트에서 업데이트된 Single Sign-On 환경<!-- 4999578  -->
Intune에 iOS, iPadOS, macOS 디바이스용 Single Sign-On(SSO) 설정이 더 추가되었습니다. 이제 ID 공급자 또는 조직이 작성한 리디렉션 SSO 앱 확장을 구성할 수 있습니다. 이 설정을 사용하면 OAuth나 SAML2와 같이 현대적인 인증 방식을 사용하는 앱이나 웹 사이트에서 더욱 매끄러운 Single Sign-On 환경을 구성할 수 있습니다. 

이 새 설정은 SSO 앱 확장 및 Apple 내장 Kerberos 확장의 기존 설정을 보강합니다(**디바이스** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼 유형: **iOS/iPadOS** 또는 **macOS** > 프로필 유형: **디바이스 기능**). 

구성할 수 있는 SSO 앱 확장 설정의 전체 범위를 확인하려면 [iOS의 SSO](../configuration/ios-device-features-settings.md#single-sign-on-app-extension) 및 [macOS의 SSO](../configuration/macos-device-features-settings.md#single-sign-on-app-extension)로 이동하세요.

적용 대상:

- iOS/iPadOS
- macOS

#### <a name="we-have-updated-two-device-restriction-settings-for-ios-and-ipados-devices-to-correct-their-behavior---5701352------"></a>디바이스의 동작 수정을 위해 iOS 및 iPadOS용 디바이스 제한 설정 두 가지를 업데이트했습니다<!-- 5701352    -->
iOS 디바이스의 경우 디바이스 제한 프로필을 생성해 **무선 PKI 업데이트를 허용**하고 **USB 제한 모드를 차단**할 수 있습니다(**디바이스** > **디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼: **iOS/iPadOS** > 프로필 유형: **디바이스 제한**). 이번 릴리스에서 다음 설정에 대한 UI 설정과 설명의 오류가 수정되었습니다. 이번 릴리스에서 이 설정 동작은 다음과 같습니다.

**무선 PKI 업데이트 차단**: **차단**하면 디바이스가 컴퓨터에 연결될 때까지 사용자의 소프트웨어 업데이트 수신을 차단합니다. **구성 안 함**(기본): 컴퓨터와 연결하지 않고도 디바이스의 소프트웨어 업데이트 수신을 허용합니다.
- 이전까지 이 설정 구성은 다음과 같았습니다. **허용**하면 사용자가 컴퓨터에 디바이스를 연결하지 않아도 소프트웨어 업데이트를 수신합니다.
**디바이스가 잠겨 있는 동안 USB 액세서리 허용**: **허용**하면 USB 액세서리가 1시간 이상 잠겨 있는 디바이스와 데이터를 교환할 수 있습니다. **구성되지 않음**(기본)은 디바이스의 USB 제한 모드 업데이트를 하지 않으며, 디바이스가 1시간 이상 잠겨 있는 경우 USB 액세서리의 데이터 전송이 차단됩니다.
- 이전까지 이 설정 구성은 다음과 같았습니다. **차단**을 선택하면 감독 모드 디바이스에서 USB 제한 모드를 사용하지 않습니다.

구성할 수 있는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 및 iPadOS 디바이스 설정](../configuration/device-restrictions-ios.md)을 참조하세요.

이 기능은 다음에 적용됩니다.

- OS/iPadOS

#### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>macOS 디바이스의 유선 네트워크 디바이스 구성 프로필<!-- 3508686  -->
   > [!NOTE]
   > 이 기능은 지연되었지만 곧 릴리스될 예정입니다.

#### <a name="block-users-from-configuring-certificate-credentials-in-the-managed-keystore-on-android-enterprise-device-owner-devices---3311998---"></a>Android 엔터프라이즈 디바이스 소유자 디바이스의 관리되는 키 저장소에서 사용자의 인증서 자격 증명 구성 차단<!-- 3311998 -->
Android 엔터프라이즈 디바이스 소유자 디바이스의 관리되는 키 저장소에서 사용자가 인증서 자격 증명을 구성하지 못하도록 새 설정을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼: **Android 엔터프라이즈** > **디바이스 소유자만 > 프로필 유형: 디바이스 제한** > **사용자 및 계정**).

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="protected-wipe-action-now-available--51150000---"></a>보호되는 초기화 동작 사용<!--51150000 -->
디바이스의 보호되는 초기화를 수행하는 초기화 디바이스 동작을 사용하는 옵션을 선택할 수 있습니다. 보호되는 초기화는 기본 초기화와 동일하지만 디바이스 종료가 불가능하다는 점에서 차이가 있습니다. 보호되는 초기화는 성공할 때까지 디바이스 재설정을 계속 시도합니다. 일부 구성에서 이 작업을 수행하면 디바이스를 다시 부팅할 수 없는 상태로 남을 수 있습니다. 자세한 내용은 [디바이스 사용 중지 및 초기화](../remote-actions/devices-wipe.md)를 참조하세요.

#### <a name="device-ethernet-mac-address-added-to-devices-overview-page--5562275---"></a>디바이스 개요 페이지에 디바이스 이더넷 MAC 주소 추가<!--5562275 -->
디바이스 세부 페이지(**디바이스** > **모든 디바이스** > 디바이스 선택 > **개요**)에서 디바이스의 이더넷 MAC 주소를 확인할 수 있습니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>디바이스 보안

#### <a name="improved-experience-on-a-shared-device-when-device-based-conditional-access-policies-are-enabled---1734096----"></a>디바이스 기반 조건부 액세스 정책을 사용할 경우 공유 디바이스의 환경 개선<!-- 1734096  -->
정책을 적용할 때 사용자의 최신 규정 준수 평가를 확인해 디바이스 기반 조건부 액세스 정책 대상인 여러 사용자의 공유 디바이스 환경을 개선했습니다. 자세한 내용은 다음 개요 문서를 참조하세요.
- [조건부 액세스에 대한 Azure 개요](https://docs.microsoft.com/azure/active-directory/conditional-access/overview)
- [Intune 디바이스 규정 준수 개요](../protect/device-compliance-get-started.md)

#### <a name="use-pkcs-certificate-profiles-to-provision-devices-with-certificates---2317124-2317130-2317139-2340517-2340528-2340529----"></a>인증서로 디바이스를 프로비전할 때 PKCS 인증서 프로필 사용<!-- 2317124, 2317130, 2317139, 2340517, 2340528, 2340529  -->
이제 Wi-Fi나 VPN에서 PKCS 인증서 프로필과 연결된 경우 PKCS 인증서 프로필을 사용해 Android for Work, iOS, Windows를 실행하는 *디바이스*에 인증서를 발행할 수 있습니다. 이전까지 이 세 플랫폼은 사용자 기반 인증서만 지원했으며 디바이스 기반 지원은 macOS에만 제한되었습니다.

> [!NOTE]
> PKCS 인증서 프로필은 Wi-Fi 프로필로 지원되지 않습니다. 그 대신 [EAP 유형](../configuration/wi-fi-settings-windows.md#enterprise-profile)을 사용할 때 SCEP 인증서 프로필을 사용합니다.

디바이스 기반 인증서를 사용하려면 지원되는 플랫폼에서 [PKCS 인증서 프로필을 만들 때](../protect/certficates-pfx-configure.md#create-a-pkcs-certificate-profile) **설정**을 선택합니다. 이제 디바이스 또는 사용자 옵션을 지원하는 **인증 유형** 설정을 확인할 수 있습니다.



<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="centralized-audit-logs--5603185-5697164---"></a>중앙화된 감사 로그<!--5603185, 5697164 -->
새롭게 중앙화된 감사 로그는 모든 범위의 감사 로그를 한 페이지에 수집합니다. 이제 로그를 필터링하여 찾는 데이터를 확인할 수 있습니다. 감사 로그를 보려면 **테넌트 관리** > **감사 로그**로 이동합니다. 

#### <a name="scope-tag-information-included-in-audit-log-activity-details--5763534---"></a>감사 로그 활동 세부 사항에 범위 태그 정보 포함<!--5763534 -->
감사 로그 활동 세부 사항이 이제 범위 태그 정보를 포함합니다(범위 태그를 지원하는 Intune 개체용). 감사 로그에 대한 자세한 내용은 [감사 로그를 사용하여 이벤트 추적 및 모니터링](monitor-audit-logs.md)을 참조하세요.


<!-- ########################## -->
## <a name="week-of-december-2-2019"></a>2019년 12월 2일 주

#### <a name="new-microsoft-endpoint-configuration-manager-co-management-licensing--5027281--"></a>새 Microsoft Endpoint Configuration Manager 공동 관리 라이선스<!--5027281-->
Software Assurance가 있는 Configuration Manager 고객은 공동 관리를 위해 추가 Intune 라이선스를 구매할 필요 없이 Windows 10 PC용 Intune 공동 관리가 가능합니다. 고객은 이제 Windows 10 공동 관리를 위해 최종 사용자에게 개별 Intune/EMS 라이선스를 할당할 필요가 없습니다.
- Configuration Manager에서 관리되고 공동 관리에 등록된 디바이스는 Intune 독립 실행형 MDM 관리 PC와 거의 동일한 권한을 가집니다. 그러나 다시 설정한 후에는 Autopilot을 사용하여 다시 프로비전할 수 없습니다.
- 다른 수단을 사용하여 Intune에 등록된 Windows 10 디바이스에는 전체 Intune 라이선스가 필요합니다.
- 다른 플랫폼의 디바이스에는 여전히 전체 Intune 라이선스가 필요합니다.

자세한 내용은 [라이선스 사용 약관](https://www.microsoft.com/en-us/Licensing/product-licensing/products)을 참조하세요.


<!-- ########################## -->
## <a name="week-of-november-18-2019-1911-service-release"></a>2019년 11월 18일 주(1911 서비스 릴리스)

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리

#### <a name="ui-update-when-selectively-wiping-app-data---4102028---"></a>앱 데이터를 선택적으로 초기화하는 경우의 UI 업데이트<!-- 4102028 -->
Intune에서 앱 데이터를 선택적으로 초기화하는 UI가 업데이트되었습니다. UI 변경 사항에는 다음이 포함됩니다.
- 하나의 창 내에 압축된 마법사 스타일 형식을 사용하여 간소화된 환경
- 할당을 포함하는 만들기 흐름에 대한 업데이트
- 속성을 볼 때, 새 정책을 만들기 전에 또는 속성을 편집할 때 설정된 모든 항목의 요약된 페이지 또한 속성을 편집할 때 요약에는 편집 중인 속성 범주의 항목 목록만 표시됩니다.

자세한 내용은 [Intune 관리 앱에서 회사 데이터만 초기화하는 방법](~/apps/apps-selective-wipe.md)을 참조하세요.

#### <a name="ios-and-ipados-third-party-keyboard-support---4922950---"></a>iOS 및 iPadOS 타사 키보드 지원<!-- 4922950 -->
2019년 3월에는 iOS 앱 보호 정책 설정 "타사 키보드"의 지원이 제거된다는 소식을 발표했습니다. 이 기능은 iOS 및 iPadOS가 모두 지원되는 Intune으로 전환될 예정입니다. 이 설정을 사용하려면 새 또는 기존 iOS/iPadOS 앱 보호 정책의 **데이터 보호** 탭으로 이동한 후 **데이터 전송** 아래의 **타사 키보드** 설정을 찾습니다.

이 정책 설정의 동작은 이전 구현과 약간 다릅니다. 이 설정이 **차단**으로 구성된 앱 보호 정책의 대상으로 지정된 SDK 버전 12.0.16 이상을 사용하는 다중 ID 앱에서 최종 사용자는 조직 및 개인 계정 모두에서 타사 키보드를 옵트인(opt in)할 수 없습니다. SDK 버전 12.0.12 이하 버전을 사용하는 앱은 블로그 게시물 제목, [알려진 문제: 타사 키보드가 개인 계정의 iOS에서 차단되지 않습니다](https://aka.ms/3rdparty_iOS_Intune)에 설명된 동작을 계속 발생합니다.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-configuration"></a>디바이스 구성

#### <a name="target-macos-user-groups-to-require-jamf-management---4061739----"></a>Jamf 관리가 필요한 macOS 사용자 그룹을 대상으로 지정합니다.<!-- 4061739  --> 
[macOS 디바이스를 Jamf로 관리](../protect/conditional-access-integrate-jamf.md)할 특정 사용자 그룹을 대상으로 지정할 수 있습니다. 이렇게 하면 다른 디바이스가 Intune에서 관리되는 동안 macOS 디바이스 하위 세트에 Jamf 준수 통합을 적용할 수 있습니다. Jamf 통합을 이미 사용하고 있는 경우 모든 사용자는 기본적으로 통합의 대상이 됩니다.

#### <a name="new-exchange-activesync-settings-when-creating-an-email-device-configuration-profile-on-ios-devices---4892824-----"></a>iOS 디바이스에서 메일 디바이스 구성 프로필을 만들 경우 새로운 Exchange ActiveSync 설정<!-- 4892824   --> 
iOS/iPadOS 디바이스의 디바이스 구성 프로필에서 메일 연결을 구성할 수 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해  > **iOS/iPadOS** 선택 > 프로필 유형에 대해 **메일** 선택). 

다음을 포함하는 새 Exchange ActiveSync 설정을 사용할 수 있습니다.
- **동기화할 Exchange 데이터**: 일정, 연락처, 미리 알림, 메모 및 메일에 대해 동기화(또는 동기화를 차단)할 Exchange 서비스를 선택합니다.
- **사용자가 동기화 설정을 변경할 수 있도록 허용**: 사용자가 디바이스에서 이러한 서비스에 대한 동기화 설정을 변경할 수 있도록 허용(또는 차단)합니다.  

이러한 설정에 대한 자세한 내용은 [Intune에서 iOS 디바이스에 대한 메일 프로필 설정](../configuration/email-settings-ios.md)으로 이동합니다. 

적용 대상:

- iOS 13.0 이상
- iPadOS 13.0 이상

#### <a name="prevent-users-from-adding-personal-google-accounts-to-android-enterprise-fully-managed-and-dedicated-devices---5353228-----"></a>사용자가 Android Enterprise 완전 관리형 및 전용 디바이스에 개인 Google 계정을 추가하지 못하도록 차단<!-- 5353228   -->
Android Enterprise 완전 관리형 및 전용 디바이스에는 사용자가 개인 Google 계정을 만들 수 없도록 하는 새로운 설정이 있습니다(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **Android Enterprise** > 프로필 유형에 대해 **디바이스 소유자만 > 디바이스 제한** > **사용자 및 계정 설정** > **개인 Google 계정**).

구성할 수 있는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 Android Enterprise 디바이스 설정](../configuration/device-restrictions-android-for-work.md)으로 이동하세요.

적용 대상:

- Android Enterprise 완전 관리형 디바이스
- Android 엔터프라이즈 전용 디바이스

#### <a name="server-side-logging-for-siri-commands-setting-is-removed-in-iosipados-device-restrictions-profile----5468501-----"></a>Siri용 서버 쪽 로깅 명령 설정이 iOS/iPadOS 디바이스 제한 프로필에서 제거됨 <!-- 5468501   -->
iOS 및 iPadOS 디바이스에서 **Siri용 서버 쪽 로깅 명령** 설정이 Microsoft Endpoint Manager 관리자 콘솔(**디바이스 구성** > **프로필** > **프로필 만들기** > 플랫폼에 대해 **iOS/iPadOS** > 프로필 유형에 대해 **디바이스 제한** > **기본 제공 앱**)에서 제거됩니다. 

이 설정은 디바이스에 영향을 주지 않습니다. 기존 프로필에서 설정을 제거하려면 프로필을 열고 원하는 대로 변경한 다음, 프로필을 저장합니다. 프로필이 업데이트되고 설정이 디바이스에서 삭제됩니다.

구성할 수 있는 모든 설정을 보려면 [Intune을 사용하여 기능을 허용하거나 제한하는 iOS 및 iPadOS 디바이스 설정](../configuration/device-restrictions-ios.md)을 참조하세요.

적용 대상:

- iOS/iPadOS

#### <a name="windows-10-feature-updates-public-preview---2384877---"></a>Windows 10 기능 업데이트(공개 미리 보기)<!-- 2384877 -->
이제 Windows 10 디바이스에 [Windows 10 기능 업데이트](../protect/windows-update-for-business-configure.md#windows-10-feature-updates)를 배포할 수 있습니다. Windows 10 기능 업데이트는 디바이스에 설치하고 유지할 Windows 10 버전을 설정하는 새로운 소프트웨어 업데이트 정책입니다. 기존 Windows 10 업데이트 링과 함께 이 새로운 정책 유형을 사용할 수 있습니다.

Windows 10 기능 업데이트 정책이 적용되는 디바이스는 지정된 버전의 Windows를 설치하고 정책이 편집 또는 제거될 때까지 해당 버전으로 유지됩니다. 이후 버전의 Windows를 실행하는 디바이스는 현재 버전으로 유지됩니다. 특정 버전의 Windows로 유지되는 디바이스는 Windows 10 업데이트 링에서 해당 버전에 대한 품질 및 보안 업데이트를 계속 설치할 수 있습니다.

이번 주에 이 새로운 유형의 정책이 테넌트로 롤아웃되기 시작합니다. 테넌트에서 이 새로운 정책을 아직 사용할 수 없는 경우 곧 제공될 예정입니다.

#### <a name="add-and-change-key-information-in-plist-files-for-macos-applications---4736278---"></a>macOS 애플리케이션용 plist 파일에서 키 정보 추가 및 변경<!-- 4736278 -->
macOS 디바이스에서 이제 앱 또는 디바이스에 연결된 속성 목록 파일(.plist)을 업로드하는 디바이스 구성 프로필을 만들 수 있습니다(**디바이스** > **구성 프로필** > **프로필 만들기** > 플랫폼에 대해 **macOS** > 프로필 유형에 대해 **기본 설정 파일**).

일부 앱에서만 관리형 기본 설정을 지원하며, 이러한 앱에서 모든 설정을 관리할 수 있는 것은 아닙니다. 사용자 채널 설정이 아니라 디바이스 채널 설정을 구성하는 속성 목록 파일을 업로드해야 합니다.

이 기능에 대한 자세한 내용은 [Microsoft Intune을 사용하여 macOS 디바이스에 속성 목록 파일 추가](../configuration/preference-file-settings-macos.md)를 참조하세요.

적용 대상:

- 10.7 이상 버전을 실행하는 macOS 디바이스

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-management"></a>디바이스 관리

#### <a name="edit-device-name-value-for-autopilot-devices---2640074---"></a>Autopilot 디바이스에 대한 디바이스 이름 값 편집<!-- 2640074 -->
Azure AD 조인 Autopilot 디바이스에 대한 디바이스 이름 값을 편집할 수 있습니다.  자세한 내용은 [Autopilot 디바이스 특성 편집](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)을 참조하세요.

#### <a name="edit-group-tag-value-for-autopilot-devices---4816775-----"></a>Autopilot 디바이스에 대한 그룹 태그 값 편집<!-- 4816775   -->
Autopilot 디바이스에 대한 그룹 태그 값을 편집할 수 있습니다. 자세한 내용은 [Autopilot 디바이스 특성 편집](../enrollment/enrollment-autopilot.md#edit-autopilot-device-attributes)을 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="monitor-and-troubleshoot"></a>모니터링 및 문제 해결

#### <a name="updated-support-experience---5012398---"></a>업데이트된 지원 환경<!-- 5012398 -->

오늘부터 [Intune에 대한 도움말 및 지원 받기](get-support.md)를 위한 업데이트되고 간소화된 콘솔 내 환경이 테넌트에 롤아웃됩니다. 이 새로운 환경을 아직 사용할 수 없는 경우 곧 제공될 예정입니다.

콘솔 내의 일반 문제 검색과 피드백, 그리고 고객 지원팀 연락에 이용하는 워크플로도 개선되었습니다. 지원 문제를 열 때 언제 콜백이나 이메일 회신을 받게 될지에 대한 예상 정보가 실시간으로 표시되며 프리미어 및 통합 지원 고객은 문제의 심각도를 간편히 지정해 지원을 더 신속히 받을 수 있습니다.

#### <a name="improved-intune-reporting-experience-public-preview----3791418---"></a>향상된 Intune 보고 환경(퍼블릭 미리 보기) <!-- 3791418 -->
이제 Intune은 새로운 보고서 유형, 더 나은 보고서 구성, 더 집중된 보기, 향상 된 보고서 기능, 좀 더 일관되고 시기 적절한 데이터를 포함하는 향상된 보고 환경을 제공합니다. 새 보고서 유형은 다음에 주안점을 둡니다.
- **작동** - 음수(-) 상태 포커스가 있는 새 레코드를 제공합니다. 
- **조직** - 전반적인 상태에 대한 광범위한 요약을 제공합니다.
- **기록** - 일정 시간 동안의 패턴 및 추세를 제공합니다.
- **전문가** - 원시 데이터를 사용하여 고유한 사용자 지정 보고서를 만들 수 있습니다.

새 보고서의 첫 번째 세트는 디바이스 준수에 주안점을 둡니다. 자세한 내용은 [블로그 - Microsoft Intune 보고 프레임워크](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Reporting-Framework-Coming-to-Intune/ba-p/1009553) 및 [Intune 보고서](~/fundamentals/reports.md)를 참조하세요.

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="role-based-access-control"></a>역할 기반 액세스 제어

#### <a name="duplicate-custom-or-built-in-roles----1081938-----"></a>중복된 사용자 지정 또는 기본 제공 역할 <!-- 1081938   -->
이제 기본 제공 및 사용자 지정 역할을 복사할 수 있습니다. 자세한 내용은 [역할 복사](../fundamentals/create-custom-role.md#copy-a-role)를 참조하세요.

#### <a name="new-permissions-for-school-administrator-role----5621805----"></a>학교 관리자 역할에 대한 새 권한 <!-- 5621805  -->  
2개의 새 사용 권한인 **프로필 할당** 및 **디바이스 동기화**가 학교 관리자 역할 > **권한** > **등록 프로그램**에 추가되었습니다. 프로필 동기화 권한을 통해 관리자는 Windows Autopilot 디바이스를 동기화할 수 있습니다. 프로필 할당 권한을 통해 사용자가 시작한 Apple 등록 프로필을 삭제할 수 있습니다. 또한 Autopilot 디바이스 할당 및 Autopilot 배포 프로필 할당을 관리할 수 있는 권한도 부여됩니다. 모든 학교 관리자/그룹 관리자 권한 목록은 [그룹 관리자 할당](https://docs.microsoft.com/intune-education/group-admin-delegate)을 참조하세요. 

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="security"></a>보안

#### <a name="bitlocker-key-rotation---2564951----"></a>BitLocker 키 순환<!-- 2564951  -->
Intune 디바이스 작업을 사용하여 Windows 버전 1909 이상을 실행하는 관리 디바이스에 대한 [BitLocker 복구 키를 원격으로 순환](../protect/encrypt-devices.md#rotate-bitlocker-recovery-keys)할 수 있습니다. 복구 키를 순환할 수 있으려면 복구 키 순환을 지원하도록 디바이스를 구성해야 합니다.  

#### <a name="updates-to-dedicated-device-enrollment-to-support-scep-device-certificate-deployment----5198878----"></a>SCEP 디바이스 인증서 배포를 지원하도록 전용 디바이스 등록 업데이트 <!-- 5198878  -->
이제 Intune은 Wi-Fi 프로필에 대한 인증서 기반 액세스를 위해 Android Enterprise 전용 디바이스에 SCEP 디바이스 인증서를 배포하도록 지원합니다. 배포가 작동하려면 디바이스에 Microsoft Intune 앱이 있어야 합니다. 따라서 Android Enterprise 전용 디바이스의 등록 환경이 업데이트되었습니다. 새 등록은 동일하게 시작되지만(QR, NFC, Zero-touch 또는 디바이스 식별자 사용), 이제 사용자에게 Intune 앱을 설치하도록 요구하는 단계가 제공됩니다. 기존 디바이스에서 롤링을 기준으로 앱을 자동으로 설치하기 시작합니다.

#### <a name="intune-audit-logs-for-business-to-business-collaboration--5670211---"></a>기업 간 공동 작업을 위한 Intune 감사 로그<!--5670211 -->
B2B(기업 간) 공동 작업을 사용하여 회사의 애플리케이션과 서비스를 다른 조직의 게스트 사용자와 안전하게 공유하면서 자체 회사 데이터에 대한 제어를 유지할 수 있습니다. 이제 Intune에서 B2B 게스트 사용자에 대한 감사 로그를 지원합니다. 예를 들어, 게스트 사용자가 변경을 수행하는 경우 Intune에서 감사 로그를 통해이 데이터를 캡처할 수 있습니다. 자세한 내용은 [Azure Active Directory B2B의 게스트 사용자 액세스란?](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b)을 참조하세요.


<!-- ########################## -->
## <a name="week-of-november-11-2019"></a>2019년 11월 11일 주  

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="app-management"></a>앱 관리  

#### <a name="improved-macos-enrollment-experience-in-company-portal----5074349----"></a>회사 포털의 개선된 macOS 등록 환경 <!-- 5074349  -->  
macOS용 회사 포털 등록 환경은 iOS용 회사 포털 등록 환경과 보다 긴밀하게 정렬된 더 간단한 등록 프로세스를 제공합니다. 이제 디바이스 사용자에게 다음과 같은 이점이 제공됩니다.  

* 보다 간소화된 사용자 인터페이스.  
* 향상된 등록 확인 목록.  
* 보다 명확하게 설명된 디바이스 등록 방법.  
* 개선된 문제 해결 옵션.  

#### <a name="web-apps-launched-from-the-windows-company-portal-app---5030972---"></a>Windows 회사 포털 앱에서 시작된 웹앱<!-- 5030972 -->
이제 최종 사용자가 Windows 회사 포털 앱에서 직접 웹앱을 시작할 수 있습니다. 최종 사용자는 웹앱을 선택한 다음 **브라우저에서 열기** 옵션을 선택할 수 있습니다. 게시된 웹 URL이 웹 브라우저에서 직접 열립니다. 이 기능은 다음 주에 출시될 예정입니다. 웹앱에 대한 자세한 내용은 [Microsoft Intune에 웹앱 추가](~/apps/web-app.md)를 참조하세요.  


#### <a name="new-assignment-type-column-in-company-portal-for-windows-10----5459950----"></a>Windows 10용 회사 포털의 새 할당 유형 열 <!-- 5459950  -->
회사 포털 > **설치된 앱** > **할당 유형** 열의 이름이 **조직에서 요구**로 변경되었습니다.  이 열 아래에 **예** 또는 **아니요** 값이 표시되어 조직에서 해당 앱을 필수 또는 선택 사항으로 지정했는지 나타냅니다. 이러한 변경 사항은 디바이스 사용자가 사용 가능한 앱 개념을 혼동하기 때문에 적용된 것입니다. 최종 사용자는 [디바이스에 앱 설치 및 공유](/intune-user-help/install-apps-cpapp-windows)에서 회사 포털에서 앱을 설치하는 자세한 내용을 확인할 수 있습니다. 최종 사용자를 위해 회사 포털 앱을 구성하는 자세한 내용은 [Microsoft Intune 회사 포털 앱을 구성하는 방법](~/apps/company-portal-app.md)을 참조하세요.  

<!-- ########################## -->
## <a name="week-of-november-4-2019"></a>2019년 11월 4일 주

<!-- vvvvvvvvvvvvvvvvvvvvvv -->
### <a name="device-security"></a>디바이스 보안

#### <a name="security-baselines-are-supported-on-microsoft-azure-government---4062552---"></a>보안 기준은 Microsoft Azure Government에서 지원됩니다.<!-- 4062552 -->

*Microsoft Azure Government*에서 호스트되는 Intune 인스턴스는 이제 [보안 기준](../protect/security-baselines.md)을 사용하여 사용자와 디바이스를 보호하는 데 도움이 될 수 있습니다.

## <a name="whats-new-archive"></a>새로운 기능 아카이브
이전 달의 경우 [새로운 아카이브 기능](whats-new-archive.md)를 참조하세요.

## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]
