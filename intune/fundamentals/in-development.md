---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/07/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.assetid: 25b3c26e-cf4e-4152-8306-bf4be4af2ad1
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 01ea2f75d166e5cc6aef4b890dba5722a74c1f61
ms.sourcegitcommit: 8f56220e7cafc5bc43135940575a9acb5afde730
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827822"
---
# <a name="in-development-for-microsoft-intune---january-2020"></a>개발 중인 Microsoft Intune 기능 - 2020년 1월

준비 및 계획을 돕기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 이 페이지의 정보 외에도: 

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 Office 메시지 센터에 보완 게시물을 게시할 것입니다.
- 기능이 프로덕션 환경에 들어가면 미리 보기 인지, 일반 공급 인지에 관계 없이 기능 설명이이 페이지에서 [새로운](whats-new.md)기능으로 이동 됩니다.
- 이 페이지와 [새로운 기능](whats-new.md) 페이지는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [Microsoft 365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!NOTE]
> 이 페이지에는 향후 릴리스에서 제공 되는 Intune 기능에 대 한 현재 기대치가 반영 됩니다. 날짜 및 개별 기능이 변경될 수 있습니다. 이 페이지는 개발의 모든 기능을 설명 하지는 않습니다.

**RSS 피드**: URL `https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`를 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->

<!-- Common categories:  
## App management
## Device configuration
## Device enrollment
## Device management
## Intune apps
## Monitor and troubleshoot
## Role-based access control
## Security

-->
 
<!-- ***********************************************-->
## <a name="app-management"></a>앱 관리

### <a name="display-notifications-for-the-company-portal-app-on-windows---1808082----"></a>Windows에서 회사 포털 앱에 대 한 알림 표시<!-- 1808082  -->
응용 프로그램이 닫힌 경우에도 사용자에 게 알림 메시지를 표시 하도록 Windows 장치의 회사 포털 앱을 업데이트 합니다. 업데이트는 설치 상태를 완료 하거나 실패 한 경우에만 사용 가능한 앱에 대 한 알림을 표시 합니다. 회사 포털 앱은 필요한 응용 프로그램에 대 한 알림을 표시 하지 않습니다. 

### <a name="display-installation-status-messages-for-the-company-portal-app---2514416----"></a>회사 포털 앱에 대 한 설치 상태 메시지 표시<!-- 2514416  -->
회사 포털 앱은 최종 사용자에 게 추가 앱 설치 상태 메시지를 표시 합니다. 새 Win32 종속성 기능에는 다음과 같은 조건이 적용 됩니다.
- 앱을 설치하지 못했습니다. 관리자가 정의한 종속성이 충족 되지 않았습니다.

### <a name="retarget-web-clips-to-microsoft-edge-on-ios-devices---5455276-idready---"></a>IOS 장치에서 Microsoft Edge로 웹 클립의 대상을 변경 합니다.<!-- 5455276 idready -->
IOS 장치에서 고정 된 웹 앱 역할을 하는 웹 클립은 업데이트 해야 합니다. 보호 된 브라우저에서 열어야 하는 경우 새로 배포 된 웹 클립이 Intune Managed Browser 대신 Microsoft Edge에서 열립니다. Managed Browser 아닌 Microsoft Edge에서 열 수 있도록 기존 웹 클립의 대상을 변경 해야 합니다. 

### <a name="user-experience-change-when-adding-apps-to-intune---4705829-idready---"></a>Intune에 앱을 추가할 때 사용자 환경 변경<!-- 4705829 idready -->
Intune을 통해 앱을 추가할 때 새로운 사용자 환경이 표시 됩니다. 이 환경은 이전에 사용한 것과 동일한 설정 및 세부 정보를 제공 하지만, Intune에 앱을 추가 하기 전에 마법사와 유사한 프로세스를 따릅니다. 이 새로운 환경에서는 앱을 추가 하기 전에 검토 페이지도 제공 합니다. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **앱** > **모든 앱** > **추가**를 선택합니다. 자세한 내용은 [Microsoft Intune에 앱 추가](~/apps/apps-add.md)를 참조하세요.

#### <a name="require-win32-apps-to-restart----3136567--"></a>Win32 앱을 다시 시작 해야 함 <!-- 3136567-->
성공적으로 설치한 후에는 Win32 앱을 다시 시작 해야 할 수 있습니다. 또한 다시 시작이 발생 하기 전 까지의 시간 (유예 기간)을 선택할 수 있습니다.

<!-- ***********************************************-->
## <a name="device-configuration"></a>디바이스 구성

### <a name="add-automatic-proxy-settings-to-wi-fi-profiles-for-android-enterprise-work-profiles---4490822-idready---"></a>Android Enterprise 회사 프로필에 대 한 Wi-fi 프로필에 자동 프록시 설정 추가<!-- 4490822 idready -->
Android Enterprise Work Profile 장치에서 Wi-fi 프로필을 만들 수 있습니다. Wi-fi 엔터프라이즈 유형을 선택 하는 경우 Wi-fi 네트워크에서 사용 되는 EAP (확장할 수 있는 인증 프로토콜) 유형을 입력할 수도 있습니다.

이후 업데이트에서 엔터프라이즈 유형을 선택 하면 `proxy.contoso.com`와 같은 프록시 서버 URL을 포함 하는 자동 프록시 설정을 입력할 수 있습니다.

구성할 수 있는 현재 Wi-fi 설정을 보려면 [Microsoft Intune에서 Android Enterprise 및 android 키오스크를 실행 하는 장치에 대 한 wi-fi 설정 추가](../configuration/wi-fi-settings-android-enterprise.md)로 이동 합니다.

적용 대상:
- Android Enterprise 회사 프로필

### <a name="wired-network-device-configuration-profiles-for-macos-devices---3508686----"></a>MacOS 장치에 대 한 유선 네트워크 장치 구성 프로필<!-- 3508686  -->
유선 네트워크 (**장치 구성** ** >  > 프로필** 을 구성 하는 새로운 macos 장치 구성 프로필을 사용 하 여 프로필 유형에 대 한 플랫폼 > **유선 네트워크** 에 대 한 프로필 > **macos** **만들기** 이 기능을 사용 하 여 유선 네트워크를 관리 하 고 이러한 유선 네트워크를 macOS 장치에 배포 하는 802.1 x 프로필을 만듭니다.

적용 대상:
- macOS

### <a name="vpn-profiles-with-ikev2-vpn-connections-can-use-always-on-with-ios-devices----1947932-idready---"></a>IKEv2 VPN 연결을 사용 하는 VPN 프로필은 iOS 장치에서 always on을 사용할 수 있습니다. <!-- 1947932 idready -->
IOS 장치에서 IKEv2 연결을 사용 하는 VPN 프로필 **을 만들 수** 있습니다 (**장치 구성** > **프로필 >  > 프로필** 유형으로 **ios/iPadOS** for platform > **VPN** ). 이후 업데이트에서는 IKEv2를 사용 하 여 always on을 구성할 수 있습니다. 구성 된 경우 IKEv2 VPN 프로필은 자동으로 연결 되며 VPN에 연결 된 상태를 유지 합니다 (또는 빠르게 다시 연결). 네트워크 간에 이동 하거나 장치를 다시 시작 하는 경우에도 연결 된 상태를 유지 합니다.

IOS에서 항상 VPN은 IKEv2 프로필로 제한 됩니다.

구성할 수 있는 최신 IKEv2 설정은 [Microsoft Intune의 iOS 디바이스에서 VPN 설정 추가](../configuration/vpn-settings-ios.md#ikev2-settings)를 참조하세요.

적용 대상:
- iOS

### <a name="improved-user-interface-experience-when-creating-configuration-profiles-on-ios-and-macos-devices---5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984-idready---"></a>IOS 및 macOS 장치에서 구성 프로필을 만들 때 향상 된 사용자 인터페이스 환경<!-- 5569008-5569039-5569057-5569110-5569116-5569131-5569139-5569153-5859984 idready -->
IOS 또는 macOS 장치에 대 한 프로필을 만들면 Endpoint Management 관리 센터의 환경이 업데이트 됩니다. 이러한 변경으로 장치 **구성 프로필 (** **장치** > **구성 프로필** >  > **iOS** 또는 **macos 플랫폼용 os** )에 영향을 줍니다.

- 사용자 지정: iOS, macOS
- 장치 기능: iOS, macOS
- 디바이스 제한: iOS, macOS
- Endpoint Protection: macOS
- 확장: macOS
- 기본 설정 파일: macOS

### <a name="improved-user-interface-experience-when-creating-oemconfig-configuration-profiles-on-android-enterprise-devices---5568645-idready----"></a>Android 엔터프라이즈 장치에서 OEMConfig 구성 프로필을 만들 때 향상 된 사용자 인터페이스 환경<!-- 5568645 idready  -->
Android Enterprise 장치에 대 한 OEMConfig 프로필을 만들거나 편집할 때 Endpoint Management 관리 센터의 환경이 업데이트 됩니다. 업데이트 된 환경에서는 한 번에 구성한 설정의 요약 정보를 제공 합니다. 이와 같이 변경 하면 OEMConfig 장치 구성 프로필 (**장치** > **구성** 프로필 **만들기** > 프로필 > **Android Enterprise** for platform > **oemconfig** )에 영향을 줍니다.

이 기능은 다음에 적용됩니다.
- Android Enterprise 

<!-- ***********************************************-->
## <a name="device-enrollment"></a>디바이스 등록

### <a name="block-android-enrollments-by-device-manufacturer--5197392-idready--"></a>장치 제조업체에서 Android 등록 차단<!--5197392 idready-->
장치의 제조업체에 따라 장치의 등록을 차단할 수 있습니다. 이는 Android 장치 관리자 및 Android Enterprise work profile 장치에 적용 됩니다. 등록 제한을 보려면 [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)> **장치** > **등록 제한**으로 이동 합니다.



<!-- ***********************************************-->
## <a name="device-management"></a>디바이스 관리


### <a name="new-information-in-device-details---4471759-5604099----"></a>장치 세부 정보의 새 정보<!-- 4471759 5604099  -->
다음 정보가 장치에 대 한 **개요** 페이지에 추가 됩니다.
- 메모리 용량 (장치의 실제 메모리 양)
- 저장소 용량 (장치의 실제 저장소 크기) 
- CPU 프로세서 종류와 속도
- RAM 및 프로세서 데이터

<!-- ***********************************************-->
<!--## Intune apps-->
 

<!-- ***********************************************-->

<!--
## Monitoring and troubleshooting
-->


<!-- ***********************************************-->
## <a name="role-based-access-control"></a>역할 기반 액세스 제어

### <a name="new-intune-built-in-role-endpoint-security-manager--4253397-idready--"></a>새 Intune 기본 제공 역할 끝점 보안 관리자<!--4253397 idready-->
새 Intune 기본 제공 역할 (끝점 보안 관리자)을 사용할 수 있습니다. 이 새로운 역할은 관리자에 게 Intune의 끝점 관리자 노드에 대 한 모든 권한을 부여 하 고 다른 영역에 대 한 준비 된 전용 액세스를 제공 합니다. 이 역할은 Azure AD에서 "보안 관리자" 역할을 확장 한 것입니다. 현재 전역 관리자 역할이 역할 인 경우에는 변경 사항이 필요 하지 않습니다. 역할을 사용 하 고 Endpoint Security Manager에서 제공 하는 세분성을 원하는 경우 해당 역할을 사용할 수 있는 경우 할당 합니다. 기본 제공 역할에 대 한 자세한 내용은 [역할 기반 액세스 제어](role-based-access-control.md)를 참조 하세요.

### <a name="intune-roles-user-interface-changes-coming--5801612-idready--"></a>Intune 역할 사용자 인터페이스 변경 예정<!--5801612 idready-->
[Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431) 에 대 한 사용자 인터페이스 > **테 넌 트 관리** > **역할** 은 보다 사용자에 게 친숙 하 고 직관적인 디자인으로 변경 됩니다. 이 환경에서는 지금 사용 하는 것과 동일한 설정 및 세부 정보를 제공 하지만, 새 환경에서는 마법사와 같은 프로세스를 사용 합니다.


<!-- ***********************************************-->
## <a name="security"></a>보안

### <a name="derived-credentials-support-on-android-cobo-devices--4839592--"></a>Android COBO 장치에서 파생 된 자격 증명 지원<!--4839592-->
Android Enterprise 완전히 관리 되는 장치에서 파생 자격 증명을 사용할 수 있습니다. Entrust Datacard, 중재 및 DISA Purebred에 대 한 파생 자격 증명을 검색 하기 위한 지원이 포함 됩니다. 앱 인증, Wi-fi, VPN 또는 S/MIME 서명 및/또는 암호화를 지 원하는 앱에 대해 파생 된 자격 증명을 사용할 수 있습니다. 

<!-- ***********************************************-->
## <a name="notices"></a>알림

[!INCLUDE [Intune notices](../includes/intune-notices.md)]

## <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


