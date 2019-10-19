---
title: Microsoft Intune - Azure에서 Windows 10을 위한 디바이스 제한 설정 | Microsoft Docs
description: Windows 10 이상 디바이스의 디바이스 제한 사항을 만들기 위한 모든 설정 및 관련 설명 목록을 확인합니다. 구성 프로필에 있는 이러한 설정을 사용하여 스크린샷, 암호 요구 사항, 키오스크 설정, 스토어의 앱, Microsoft Edge 브라우저, Windows defender, 클라우드 액세스, 시작 메뉴 및 Microsoft Intune의 기타 기능을 제어합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 164c34f4a46ca11e2788b72dee70bdd40c25e7f3
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72493899"
---
# <a name="windows-10-and-newer-device-settings-to-allow-or-restrict-features-using-intune"></a>Intune을 사용하여 기능을 허용하거나 제한하는 Windows 10 이상 디바이스 설정

이 문서에서는 Windows 10 이상 디바이스에서 제어할 수 있는 다양한 설정을 모두 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로 이러한 설정을 사용하여 기능을 허용하거나 사용하지 않도록 설정하고, 암호 규칙을 설정하고, 잠금 화면을 사용자 지정하며, Microsoft Defender를 사용합니다.

이러한 설정은 Intune에서 디바이스 구성 프로필에 추가된 다음, Windows 10 디바이스에 할당 또는 배포됩니다.

> [!Note]
> 모든 Windows 버전에서 모든 옵션을 사용할 수 있는 것은 아닙니다. 지원되는 버전을 보려면 [정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)(다른 Microsoft 웹 사이트 열기)를 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](device-restrictions-configure.md#create-the-profile).

## <a name="app-store"></a>앱 스토어

다음 설정에서는 [ApplicationManagement 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **앱 스토어**(모바일 전용): **구성되지 않음**(기본값)을 사용하면 최종 사용자가 모바일 디바이스의 앱 스토어에 액세스할 수 있습니다. **차단**은 앱 스토어를 사용하지 못하도록 차단합니다.
- **스토어에서 앱 자동 업데이트**: **구성되지 않음**(기본값)을 사용하면 Microsoft Store에서 설치된 앱을 자동으로 업데이트할 수 있습니다. **차단**은 업데이트가 자동으로 설치되지 않도록 차단합니다.
- **신뢰할 수 있는 앱 설치**: 비 Microsoft Store 앱을 설치할 수 있는 경우(사이드로드라고도 함) 이 설정을 선택합니다. 사이드로드는 Microsoft Store에서 인증하지 않은 앱을 설치한 다음, 실행하거나 테스트합니다. 예를 들어 회사 내부에만 있는 앱입니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): OS 기본값을 사용합니다.
  - **차단**: 사이드로드를 차단합니다. 비 Microsoft Store 앱을 설치할 수 없습니다.
  - **허용**: 사이드로드를 허용합니다. 비 Microsoft Store 앱을 설치할 수 있습니다.
- **개발자 잠금 해제**: Windows 개발자 설정을 허용합니다(예: 최종 사용자가 사이드로드된 앱을 수정할 수 있도록 허용). 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): OS 기본값을 사용합니다.
  - **차단**: 개발자 모드 및 앱 사이드로드를 차단합니다.
  - **허용**: 개발자 모드 및 앱 사이드로드를 허용합니다.

  [디바이스를 개발에 사용할 수 있도록 설정](https://docs.microsoft.com/windows/uwp/get-started/enable-your-device-for-development)에는 이 기능에 대한 자세한 정보가 있습니다.

- **공유 사용자 앱 데이터**: **허용**을 선택하면 동일한 디바이스의 다른 사용자와 해당 앱의 다른 인스턴스 간에 애플리케이션 데이터를 공유할 수 있습니다. **구성되지 않음**(기본값)은 동일한 앱의 다른 사용자 및 다른 인스턴스와 데이터를 공유하지 못하도록 차단합니다.
- **프라이빗 스토어만 사용**: **허용**을 사용하면 소매 카탈로그를 포함하여 프라이빗 스토어에서만 앱을 다운로드할 수 있고 퍼블릭 스토어에서는 다운로드할 수 없습니다. **구성되지 않음**(기본값)을 사용하면 프라이빗 스토어와 퍼블릿 스토어에서 앱을 다운로드할 수 있습니다.
- **스토어에서 시작된 앱 시작**: **차단**은 디바이스에 미리 설치되어 있거나 Microsoft Store에서 다운로드한 앱을 모두 사용하지 않도록 설정합니다. **구성되지 않음**(기본값)을 사용하면 이러한 앱을 열 수 있습니다.
- **시스템 볼륨에 앱 데이터 설치**: **차단**은 앱에서 데이터를 디바이스의 시스템 볼륨에 저장하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 앱에서 데이터를 시스템 디스크 볼륨에 저장할 수 있습니다.
- **시스템 드라이브에 앱 설치**: **차단**은 앱이 디바이스의 시스템 드라이브에 설치되지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 앱을 시스템 드라이브에 설치할 수 있습니다.
- **게임 DVR**(데스크톱에만 해당): **차단**은 Windows 게임 녹화 및 방송을 사용하지 않도록 설정합니다. **구성되지 않음**(기본값)을 사용하면 게임을 녹화하고 브로드캐스트할 수 있습니다.
- **스토어 에서만 앱**:이 설정은 사용자가 Microsoft Store 이외의 위치에서 앱을 설치할 때 사용자 환경을 결정 합니다. 옵션은 다음과 같습니다.

  - **구성 되지 않음** (기본값): 최종 사용자가 다른 정책 설정에 정의 된 앱을 포함 하 여 Microsoft Store 이외의 위치에서 앱을 설치할 수 있습니다.  
  - **Anywhere**: 앱 권장 사항을 해제 하 고 사용자가 모든 위치에서 앱을 설치할 수 있도록 합니다.  
  - **저장소 전용**: 최종 사용자가 Microsoft Store 에서만 앱을 설치 하도록 합니다.
  - **권장 사항**: Microsoft Store에서 사용할 수 있는 웹에서 앱을 설치 하는 경우 사용자에 게 스토어에서 다운로드 하는 것을 제안 하는 메시지가 표시 됩니다.  
  - **스토어 선호**: Microsoft Store 이외의 위치에서 앱을 설치할 때 사용자에 게 경고 합니다.

  [SmartScreen/EnableAppInstallControl CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen#smartscreen-enableappinstallcontrol)

- **설치에 대한 사용자 정의 컨트롤**: **구성되지 않음**(기본값)으로 설정하면 Windows Installer에서 사용자가 파일을 설치할 디렉터리 입력 등 일반적으로 시스템 관리자용으로 예약된 설치 옵션을 변경하지 못하도록 합니다. **차단**: 사용자가 이러한 설치 옵션을 변경하는 것을 허용하며, 일부 Windows Installer 보안 기능이 무시됩니다.

  [ApplicationManagement/MSIAllowUserControlOverInstall CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msiallowusercontroloverinstall)

- **높은 권한으로 앱 설치**: **구성되지 않음**(기본값)으로 설정하면 시스템에서 시스템 관리자가 배포하거나 제공하지 않은 프로그램을 설치할 때 현재 사용자의 권한을 적용합니다. **차단**: Windows Installer가 시스템에 프로그램을 설치할 때 높은 권한을 사용하도록 지시합니다. 이러한 권한은 모든 프로그램으로 확장됩니다.

  [ApplicationManagement/MSIAlwaysInstallWithElevatedPrivileges CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-msialwaysinstallwithelevatedprivileges)

- **시작 앱**: 사용자가 디바이스에 로그인한 후 열리는 앱 목록을 입력합니다. Windows 애플리케이션의 세미콜론으로 구분된 PFN(패키지 패밀리 이름) 목록을 사용해야 합니다. 이 정책을 사용하려면 Windows 앱의 매니페스트가 시작 작업을 사용해야 합니다.

  [ApplicationManagement/LaunchAppAfterLogOn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-launchappafterlogon)

## <a name="cellular-and-connectivity"></a>셀룰러 및 연결

다음 설정에서는 [연결 정책](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-connectivity) 및 [Wi-Fi 정책](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi) CSP를 사용하며, 지원되는 Windows 버전도 나열합니다.

- [Wi-Fi 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wifi)

- **셀룰러 데이터 채널**: 최종 사용자가 셀룰러 네트워크에 연결할 때 웹 검색과 같은 데이터를 사용할 수 있는지 여부를 선택합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 셀룰러 데이터 채널이 허용될 수 있는 OS 기본값을 사용합니다. 이 옵션은 최종 사용자가 해제할 수 있습니다.
  - **차단**: 셀룰러 데이터 채널을 허용하지 않습니다. 이 옵션은 최종 사용자가 설정할 수 있습니다.
  - **허용(편집할 수 없음)** : 셀룰러 데이터 채널을 허용합니다. 이 옵션은 최종 사용자가 해제할 수 없습니다.

- **데이터 로밍**: **차단**은 디바이스의 셀룰러 데이터를 로밍하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 데이터에 액세스할 때 네트워크 간 로밍을 허용합니다.
- **셀룰러 네트워크를 통한 VPN**: **차단**은 셀룰러 네트워크에 연결될 때 디바이스에서 VPN 연결에 액세스하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 VPN에서 셀룰러를 포함한 모든 연결을 사용할 수 있습니다.
- **셀룰러 네트워크를 통한 VPN 로밍**: **차단**은 셀룰러 네트워크에서 로밍할 때 디바이스에서 VPN 연결에 액세스하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 로밍할 때 VPN 연결을 허용합니다.
- **연결된 디바이스 서비스**: **차단**은 CDP(연결된 디바이스 플랫폼) 구성 요소를 사용하지 않도록 설정합니다. CDP는 원격 앱 시작, 원격 메시징, 원격 앱 세션 및 기타 디바이스 간 환경을 지원하기 위해 Bluetooth/LAN 또는 클라우드를 통해 다른 디바이스(Bluetooth/LAN 또는 클라우드를 통해)를 검색하고 연결하도록 설정합니다. **구성되지 않음**(기본값)은 다른 Bluetooth 디바이스에 대한 검색 및 연결을 사용하도록 설정하는 연결된 디바이스 서비스를 허용합니다.
- **NFC**: **차단**은 NFC(근거리 통신) 기능을 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 디바이스에서 NFC 기능을 사용하도록 설정하고 구성할 수 있습니다.
- **Wi-Fi**: **차단**은 사용자가 디바이스에서 Wi-Fi 연결을 설정, 구성 및 사용하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 Wi-Fi 연결을 허용합니다.
- **자동으로 Wi-Fi 핫스팟에 연결**: **차단**은 디바이스에서 Wi-Fi 핫스팟에 자동으로 연결하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 디바이스에서 사용 가능한 Wi-Fi 핫스팟에 자동으로 연결하고, 연결에 대한 모든 사용 약관에 자동으로 동의할 수 있습니다.
- **수동 Wi-Fi 구성**: **차단**은 디바이스에서 MDM 서버에 설치된 네트워크 외부의 Wi-Fi에 연결하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 최종 사용자가 자신의 Wi-Fi 연결 네트워크 SSID를 추가하고 구성할 수 있습니다.
- **Wi-Fi 검색 간격**: 디바이스가 Wi-Fi 네트워크를 검색하는 빈도를 입력합니다. 1(빈도 가장 높음)에서 500(빈도 가장 낮음) 사이의 값을 입력합니다. 기본값은 `0`(영)입니다.

### <a name="bluetooth"></a>Bluetooth

다음 설정에서는 [Bluetooth 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **Bluetooth**: **차단**은 사용자가 Bluetooth 사용을 설정하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 디바이스에서 Bluetooth를 허용합니다.
- **Bluetooth 검색 기능**: **차단**은 다른 Bluetooth 지원 디바이스에서 디바이스를 검색하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 헤드셋과 같은 다른 Bluetooth 지원 디바이스에서 디바이스를 검색할 수 있습니다.
- **Bluetooth 사전 페어링**: **차단**은 특정 Bluetooth 디바이스에서 호스트 디바이스와 자동으로 페어링하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 호스트 디바이스와 자동으로 페어링할 수 있습니다.
- **Bluetooth 광고**: **차단**은 디바이스에서 Bluetooth 광고를 보내지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 디바이스에서 Bluetooth 광고를 보낼 수 있습니다.
- **Bluetooth 허용 서비스**: 허용되는 Bluetooth 서비스 및 프로필 목록을 16진수 문자열(예: `{782AFCFC-7CAA-436C-8BF0-78CD0FFBD4AF}`)로 **추가**합니다.

  [ServicesAllowedList 사용 가이드](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-bluetooth#servicesallowedlist-usage-guide)에는 서비스 목록에 대한 자세한 정보가 있습니다.

## <a name="cloud-and-storage"></a>클라우드 및 스토리지

다음 설정에서는 [계정 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-accounts)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **Microsoft 계정**: **차단**은 최종 사용자가 Microsoft 계정을 디바이스와 연결하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 Microsoft 계정을 추가하고 사용할 수 있습니다.
- **타사 계정**: **차단**은 최종 사용자가 사용자 인터페이스를 사용하여 타사 계정을 추가하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 Microsoft 계정과 연결되지 않은 이메일 계정을 추가할 수 있습니다.
- **Microsoft 계정의 설정 동기화**: **구성되지 않음**(기본값)을 사용하면 Microsoft 계정과 연결된 디바이스 및 앱 설정을 디바이스 간에 동기화할 수 있습니다. **차단**은 이 동기화를 차단합니다.
- **Microsoft 계정 로그인 도우미**: **구성되지 않음**(기본값)으로 설정하면 최종 사용자가 **Microsoft 계정 로그인 도우미**(wlidsvc) 서비스를 시작하고 중지할 수 있습니다. 사용자는 이 운영 체제 서비스를 통해 Microsoft 계정에 로그인할 수 있습니다. **사용 안 함**은 최종 사용자가 Microsoft 로그인 도우미 서비스(wlidsvc)를 제어하지 못하도록 차단합니다.

## <a name="cloud-printer"></a>클라우드 프린터

다음 설정에서는 [EnterpriseCloudPrint 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-enterprisecloudprint)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **프린터 검색 URL**: 클라우드 프린터 검색을 위한 URL을 입력합니다. 예를 들어 다음과 같이 입력합니다. `https://cloudprinterdiscovery.contoso.com`
- **프린터 액세스 인증 기관 URL**: 인증 엔드포인트 URL을 입력하여 OAuth 토큰을 가져옵니다. 예를 들어 다음과 같이 입력합니다. `https://azuretenant.contoso.com/adfs`
- **Azure 네이티브 클라이언트 앱 GUID**: OAuthAuthority에서 OAuth 토큰을 가져오도록 허용되는 클라이언트 애플리케이션의 GUID를 입력합니다. 예를 들어 다음과 같이 입력합니다. `E1CF1107-FF90-4228-93BF-26052DD2C714`
- **인쇄 서비스 리소스 URI**: Azure Portal에 구성된 인쇄 서비스의 OAuth 리소스 URI를 입력합니다. 예를 들어 다음과 같이 입력합니다. `http://MicrosoftEnterpriseCloudPrint/CloudPrint`
- **쿼리할 최대 프린터 수**: 쿼리하려는 최대 프린터 수를 입력합니다. 기본값은 `20`입니다.
- **프린터 검색 서비스 리소스 URI**: Azure Portal에 구성된 프린터 검색 서비스의 OAuth 리소스 URI를 입력합니다. 예를 들어 다음과 같이 입력합니다. `http://MopriaDiscoveryService/CloudPrint`

> [!TIP]
> [Windows Server 하이브리드 클라우드 인쇄](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-overview)를 설정하면 이러한 설정을 구성한 다음, Windows 디바이스에 배포할 수 있습니다.

## <a name="control-panel-and-settings"></a>제어판 및 설정

- **설정 앱**: **차단**은 최종 사용자가 Windows 설정 앱에 액세스하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 디바이스에서 설정 앱을 열 수 있습니다.
  - **시스템**: **차단**은 설정 앱의 시스템 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
    - **전원 및 절전 모드 설정 수정**(데스크톱 전용): **차단**은 최종 사용자가 디바이스의 전원 및 절전 모드 설정을 변경하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 전원 및 절전 모드 설정을 변경할 수 있습니다.
  - **디바이스**: **차단**은 디바이스에 있는 설정 앱의 [디바이스] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **네트워크 인터넷**: **차단**은 디바이스에 있는 설정 앱의 [네트워크 및 인터넷] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **맞춤 설정**: **차단**은 디바이스에 있는 설정 앱의 [맞춤 설정] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **앱**: **차단**은 디바이스에 있는 설정 앱의 [앱] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **계정**: **차단**은 디바이스에 있는 설정 앱의 계정 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **시간 및 언어**: **차단**은 디바이스에 있는 설정 앱의 시간 및 언어 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
    - **시스템 시간 수정**: **차단**은 최종 사용자가 디바이스의 날짜 및 시간 설정을 변경하지 못하도록 차단합니다. **구성되지 않음**을 사용하면 사용자가 이러한 설정을 변경할 수 있습니다.
    - **지역 설정 수정**(데스크톱 전용): **차단**은 최종 사용자가 디바이스의 지역 설정을 변경하지 못하도록 차단합니다. **구성되지 않음**을 사용하면 사용자가 이러한 설정을 변경할 수 있습니다.
    - **언어 설정 수정(데스크톱 전용)** : **차단**은 사용자가 디바이스의 언어 설정을 변경하지 못하도록 차단합니다. **구성되지 않음**을 사용하면 사용자가 이러한 설정을 변경할 수 있습니다.

      [Settings 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-settings)

  - **게임**: **차단**은 디바이스에 있는 설정 앱의 [게임] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **접근성**: **차단**은 디바이스에 있는 설정 앱의 [접근성] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **개인 정보**: **차단**은 디바이스에 있는 설정 앱의 [개인 정보] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.
  - **업데이트 및 보안**: **차단**은 디바이스에 있는 설정 앱의 [업데이트 및 보안] 영역에 대한 액세스를 차단합니다. **구성되지 않음**(기본값)은 액세스를 허용합니다.

## <a name="display"></a>표시

다음 설정에서는 [표시 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-display)를 사용하며, 지원되는 Windows 버전도 나열합니다.

GDI DPI 크기 조정은 DPI를 인식하지 않는 애플리케이션에서 DPI를 모니터별로 인식하도록 설정합니다.

- **앱용 GDI 조정 켜기**: GDI DPI 크기 조정을 설정하려는 레거시 앱을 **추가**합니다. 예를 들어 `filename.exe` 또는 `%ProgramFiles%\Path\Filename.exe`을 입력합니다.

  GDI DPI 크기 조정이 목록의 모든 레거시 애플리케이션에 대해 설정됩니다.

- **앱용 GDI 조정 끄기**: GDI DPI 크기 조정을 해제하려는 레거시 앱을 **추가**합니다. 예를 들어 `filename.exe` 또는 `%ProgramFiles%\Path\Filename.exe`을 입력합니다.

  GDI DPI 크기 조정이 목록의 모든 레거시 애플리케이션에 대해 해제됩니다.

또한 앱 목록이 있는 .csv 파일을 **가져올** 수도 있습니다.

## <a name="general"></a>일반

다음 설정에서는 [환경 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)를 사용하며, 지원되는 Windows 버전도 나열합니다. 

- **화면 캡처**(모바일 전용): **차단**은 최종 사용자가 디바이스에서 스크린샷을 가져오지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **복사 및 붙여넣기(모바일 전용)** : **차단**은 최종 사용자가 디바이스의 앱 간에 복사 및 붙여넣기를 사용하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **수동 등록 취소**: **차단**은 최종 사용자가 디바이스의 작업 영역 제어판을 사용하여 작업 영역 계정을 삭제하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.

  이 정책 설정은 컴퓨터가 Azure AD에 조인되어 있고 자동 등록이 활성화된 경우에는 적용되지 않습니다.

- **수동 루트 인증서 설치**(모바일 전용): **차단**은 최종 사용자가 루트 인증서 및 중간 CAP 인증서를 수동으로 설치하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **카메라**: **차단**은 최종 사용자가 디바이스에서 카메라를 사용하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **OneDrive 파일 동기화**: **차단**은 최종 사용자가 파일을 디바이스에서 OneDrive로 동기화하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **이동식 스토리지**: **차단**은 최종 사용자가 디바이스에서 SD 카드와 같은 외부 스토리지 디바이스를 사용하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **지리적 위치**: **차단**은 최종 사용자가 디바이스에서 위치 서비스를 설정하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **인터넷 공유**: **차단**은 디바이스의 인터넷 연결 공유를 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **휴대폰 초기화**: **차단**은 최종 사용자가 디바이스에서 삭제하거나 공장 초기화를 수행하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **USB 연결**: **차단**은 디바이스의 USB 연결을 통해 외부 스토리지 디바이스에 액세스하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다. USB 충전은 이 설정의 영향을 받지 않습니다.
- **AntiTheft 모드**(모바일 전용): **차단**은 최종 사용자가 디바이스에서 AntiTheft 모드 기본 설정을 선택하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **Cortana**: **차단**은 디바이스에서 Cortana 음성 도우미를 사용하지 않도록 설정합니다. Cortana가 해제되어 있는 경우에도 사용자가 디바이스에서 항목을 검색하여 찾을 수 있습니다. **구성되지 않음**(기본값)은 Cortana를 허용합니다.
- **음성 녹음**(모바일 전용): **차단**은 최종 사용자가 디바이스에서 디바이스 음성 녹음기를 사용하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 앱에 대한 음성 녹음을 허용합니다.
- **디바이스 이름 수정**(모바일 전용): **차단**은 최종 사용자가 디바이스 이름을 변경하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **프로비저닝 패키지 추가**: **차단**은 디바이스에 프로비저닝 패키지를 설치하는 런타임 구성 에이전트를 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **프로비저닝 패키지 제거**: **차단**은 디바이스에서 프로비저닝 패키지를 제거하는 런타임 구성 에이전트를 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **디바이스 검색**: **차단**은 다른 디바이스에서 디바이스를 검색하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **작업 전환기**(모바일 전용): **차단**은 디바이스의 작업 전환을 차단합니다. **구성되지 않음**(기본값)은 이 기능을 허용합니다.
- **SIM 카드 오류 대화 상자**(모바일 전용): **차단**은 SIM 카드가 검색되지 않으면 오류 메시지를 디바이스에 표시하지 않도록 차단합니다. **구성되지 않음**(기본값)을 오류 메시지를 표시합니다.
- **잉크 작업 영역**: 사용자가 잉크 작업 영역에 액세스할 수 있는지 여부와 액세스하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 잉크 작업 영역을 설정합니다. 그러면 사용자가 잠금 화면 위에서 이 작업 영역을 사용할 수 있습니다.
  - **잠금 화면에서 사용할 수 없습니다**: 잉크 작업 영역을 사용하도록 설정하지만 이 기능이 켜집니다. 이 경우 사용자가 잠금 화면 위에서 이 작업 영역에 액세스할 수 없습니다.
  - **사용 안 함**: 잉크 작업 영역에 대한 액세스를 사용하지 않도록 설정합니다. 이 기능이 해제됐습니다.

  [WindowsInkWorkspace 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsinkworkspace)

- **자동 재배포**: **허용**을 선택하면 관리 권한이 있는 사용자가 디바이스 잠금 화면에서 **Ctrl+Win+R**을 사용하여 모든 사용자 데이터 및 설정을 삭제할 수 있습니다. 디바이스가 자동으로 다시 구성되고 관리에 다시 등록됩니다. **구성되지 않음**(기본값)으로 설정하면 이 기능을 차단합니다.
- **디바이스 설정 중 사용자가 네트워크에 연결해야 함**: **필요**를 선택하면 Windows 설치 중에 네트워크 페이지를 통과하기 전에 디바이스에서 네트워크에 연결할 수 있습니다. **구성되지 않음**(기본값)을 사용하면 네트워크에 연결되어 있지 않더라도 사용자가 네트워크 페이지를 통과할 수 있습니다.

  이 설정은 다음에 디바이스를 초기화하거나 재설정할 때 적용됩니다. 다른 Intune 구성과 마찬가지로, 구성 설정을 수신하려면 디바이스를 Intune에서 등록하고 관리해야 합니다. 그러나 등록하고 정책을 수신한 다음, 디바이스를 다시 설정하면 다음 Windows 설치 중에 설정이 적용됩니다.

- **직접 메모리 액세스**: **차단**을 선택하면 사용자가 Windows에 로그인할 때까지 모든 핫 플러그형 PCI 다운스트림 포트에 대한 DMA(직접 메모리 액세스)가 차단됩니다. **사용**(기본값)으로 설정하면, 사용자가 로그인되지 않은 경우에도 DMA에 액세스할 수 있습니다.

  CSP: [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess)

- **작업 관리자에서 프로세스 종료**: 이 설정은 관리자가 아닌 사용자가 작업 관리자를 사용하여 작업을 종료할 수 있는지 여부를 결정합니다. **차단**을 선택하면 표준 사용자(비관리자)가 작업 관리자를 사용하여 디바이스에서 프로세스 또는 작업을 종료하지 못합니다. **구성되지 않음**(기본값)은 표준 사용자가 작업 관리자를 사용하여 프로세스 또는 작업을 종료할 수 있도록 허용합니다.

## <a name="locked-screen-experience"></a>잠긴 화면 환경

- **알림 센터 알림(모바일 전용)** : **차단**은 알림 센터 알림을 디바이스 잠금 화면에 표시하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 알림을 잠금 화면에 표시할 앱을 선택할 수 있습니다.

  [AboveLock/AllowActionCenterNotifications CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowactioncenternotifications)

- **잠긴 화면 그림 URL(데스크톱 전용)** : Windows 잠금 화면 배경으로 사용되는 JPG, JPEG 또는 PNG 형식의 그림에 대한 URL을 입력합니다. 예를 들어 다음과 같이 입력합니다. `https://contoso.com/image.png` 이 설정은 이미지를 잠그고 나중에 변경할 수 없습니다.
- **사용자 구성 가능 화면 시간 제한(모바일 전용)** : **허용**을 사용하면 화면 시간 제한을 구성할 수 있습니다. **구성되지 않음**(기본값)은 사용자에게 이 옵션을 제공하지 않습니다.

  [DeviceLock/AllowScreenTimeoutWhileLockedUserConfig CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowscreentimeoutwhilelockeduserconfig)

- **잠긴 화면 위 Cortana**(데스크톱 전용): **차단**은 디바이스가 잠금 화면으로 있을 때 사용자가 Cortana와 상호 작용하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 Cortana와의 상호 작용을 허용합니다.

  [AboveLock/AllowCortanaAboveLock CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowcortanaabovelock)

- **잠긴 화면 위 알림**: **차단**은 알림 메시지를 디바이스 잠금 화면에 표시하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이러한 알림을 허용합니다.

  [AboveLock/AllowToasts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-abovelock#abovelock-allowtoasts)

- **화면 시간 제한(모바일 전용)** : 화면 잠금에서 화면 해제까지의 기간(분)을 설정합니다. 지원되는 값은 11-1800입니다. 예를 들어 이 시간 제한을 5분으로 설정하려면 `300`을 입력합니다.

  [DeviceLock/ScreenTimeoutWhileLocked CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-screentimeoutwhilelocked)

## <a name="messaging"></a>메시징

다음 설정에서는 [메시징 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-messaging)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **메시지 동기화(모바일 전용)** : **차단**은 문자 메시지를 백업 및 복원하지 않고 Windows 디바이스 간에 메시지를 동기화하지 않도록 설정합니다. 사용하지 않도록 설정되면 정보가 조직에서 제어하지 않는 서버에 저장되지 않습니다. **구성되지 않음**(기본값)을 사용하면 사용자가 이러한 설정을 변경하고 해당 메시지를 동기화할 수 있습니다.
- **MMS(모바일 전용)** : **차단**은 디바이스에서 MMS 보내기 및 받기 기능을 사용하지 않도록 설정합니다. 기업의 경우 이 정책을 사용하여 감사 또는 관리 요구 사항의 일부로 디바이스에서 MMS를 사용하지 않도록 설정합니다. **구성되지 않음**(기본값)을 사용하면 MMS를 보내고 받을 수 있습니다.
- **RCS(모바일 전용)** : **차단**은 디바이스에서 RCS(Rich Communication Services) 보내기 및 받기 기능을 사용하지 않도록 설정합니다. 기업의 경우 이 정책을 사용하여 감사 또는 관리 요구 사항의 일부로 디바이스에서 RCS를 사용하지 않도록 설정합니다. **구성되지 않음**(기본값)을 사용하면 RCS를 보내고 받을 수 있습니다.

## <a name="microsoft-edge-browser"></a>Microsoft Edge 브라우저

다음 설정에서는 [브라우저 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser)를 사용하며, 지원되는 Windows 버전도 나열합니다.

### <a name="use-microsoft-edge-kiosk-mode"></a>Microsoft Edge 키오스크 모드 사용

사용 가능한 설정은 선택한 항목에 따라 변경됩니다. 옵션은 다음과 같습니다.

- **아니요**(기본값): Microsoft Edge가 키오스크 모드에서 실행되고 있지 않습니다. 모든 Microsoft Edge 설정을 변경하고 구성할 수 있습니다.
- **디지털/대화형 신호(단일 앱 키오스크)** : Windows 10 단일 앱 키오스크에서만 사용할 수 있도록 디지털/대화형 신호 Microsoft Edge 키오스크 모드에 적용할 수 있는 Microsoft Edge 설정을 필터링합니다. URL 전체 화면을 열고 해당 웹 사이트에 콘텐츠만 표시하려면 이 설정을 선택합니다. [디지털 서명 설정](https://docs.microsoft.com/windows/configuration/setup-digital-signage)은 이 기능에 대한 자세한 정보를 제공합니다.
- **InPrivate Public 검색(단일 앱 키오스크)** : Windows 10 단일 앱 키오스크에서 사용할 수 있도록 InPrivate Public Browsing Microsoft Edge 키오스크 모드에 적용할 수 있는 Microsoft Edge 설정을 필터링합니다. Microsoft Edge의 다중 탭 버전을 실행합니다.
- **일반 모드(다중 앱 키오스크)** : 일반 Microsoft Edge 키오스크 모드에 적용할 수 있는 Microsoft Edge 설정을 필터링합니다. 모든 검색 기능을 사용하여 Microsoft Edge의 전체 버전을 실행합니다.
- **공용 검색(다중 앱 키오스크)** : Windows 10 다중 앱 키오스크에서 공용 검색에 적용할 수 있는 Microsoft Edge 설정을 필터링합니다.  Microsoft Edge InPrivate의 다중 탭 버전을 실행합니다.

> [!TIP]
> 이러한 옵션의 기능에 대한 자세한 내용은 [Microsoft Edge 키오스크 모드 구성 유형](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-configuration-types)을 참조하세요.

이 디바이스 제한 프로필은 [Windows 키오스크 설정](kiosk-settings-windows.md)을 사용하여 생성한 키오스크 프로필과 직접 연관이 됩니다. 요약:

1. [Windows 키오스크 설정](kiosk-settings-windows.md)을 만들어 디바이스를 키오스크 모드로 실행합니다. Microsoft Edge를 애플리케이션으로 선택하고 키오스크 프로필에서 Microsoft Edge 키오스크 모드를 설정합니다.
2. 이 문서에서 설명하는 디바이스 제한 프로필을 만들고 Microsoft Edge에서 허용되는 특정 기능 및 설정을 구성합니다. 키오스크 프로필에서 선택한 것과 동일한 Microsoft Edge 키오스크 모드 유형을 선택해야 합니다([Windows 키오스크 설정](kiosk-settings-windows.md)). 

    [지원되는 키오스크 모드 설정](https://docs.microsoft.com/microsoft-edge/deploy/microsoft-edge-kiosk-mode-deploy#supported-policies-for-kiosk-mode)은 유용한 리소스입니다.

> [!IMPORTANT] 
> 이 Microsoft Edge 프로필을 키오스크 프로필과 동일한 디바이스에 할당해야 합니다([Windows 키오스크 설정](kiosk-settings-windows.md)).

CSP: [ConfigureKioskMode](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configurekioskmode)

### <a name="start-experience"></a>시작 환경

- **다음에서 Microsoft Edge 시작**: Microsoft Edge가 시작될 때 열리는 페이지를 선택합니다. 옵션은 다음과 같습니다.
  - **시작 페이지 사용자 지정**: 시작 페이지(예: `http://www.contoso.com`)를 입력합니다. Microsoft Edge에서 사용자가 입력한 시작 페이지를 로드합니다.
  - **새 탭 페이지**: Microsoft Edge에서 **새 탭 URL** 설정에 입력된 내용을 로드합니다.
  - **마지막 세션의 페이지**: Microsoft Edge에서 마지막 세션 페이지를 로드합니다.
  - **로컬 앱 설정의 시작 페이지**: Microsoft Edge가 OS에서 정의한 기본 시작 페이지로 시작합니다.

- **사용자가 시작 페이지를 변경할 수 있도록 허용**: **예**(기본값)를 사용하면 사용자가 시작 페이지를 변경할 수 있습니다. 관리자는 `EdgeHomepageUrls`를 사용하여 Microsoft Edge를 열 때 사용자에게 기본적으로 표시되는 시작 페이지를 입력할 수 있습니다. **아니요**는 사용자가 시작 페이지를 변경하지 못하도록 차단합니다.
- **새 탭 페이지에서 웹 콘텐츠 허용**: **예**(기본값)로 설정하면 Microsoft Edge에서 **새 탭 URL** 설정에 입력된 URL을 엽니다. **새 탭 URL** 설정이 비어 있으면 Microsoft Edge에서 Microsoft Edge 설정에 나열된 새 탭 페이지를 엽니다. 이 설정은 사용자가 변경할 수 있습니다. **아니요**로 설정하면 Microsoft Edge에서 빈 페이지가 있는 새 탭을 엽니다. 이 설정은 사용자가 변경할 수 없습니다.
- **새 탭 URL**: 새 탭 페이지에서 열 URL을 입력합니다. 예를 들어 `https://www.bing.com` 또는 `https://www.contoso.com`을 입력합니다.

- **홈 단추**: 홈 단추가 선택되면 수행할 작업을 선택합니다. 옵션은 다음과 같습니다.
  - **시작 페이지**: **다음으로 Microsoft Edge 시작** 설정에서 선택한 옵션을 엽니다.
  - **새 탭 페이지**: **새 탭 URL** 설정에 입력한 URL을 엽니다.
  - **홈 단추 URL**: 열 URL을 입력합니다. 예를 들어 `https://www.bing.com` 또는 `https://www.contoso.com`을 입력합니다.
  - **홈 단추 숨기기**: 홈 단추를 숨깁니다.
- **사용자가 홈 단추를 변경할 수 있도록 허용**: **예**를 사용하면 사용자가 홈 단추를 변경할 수 있습니다. 사용자의 변경 내용이 홈 단추의 모든 관리자 설정을 재정의합니다. **아니요**(기본값)는 관리자가 홈 단추를 구성한 방법을 사용자가 변경하지 못하도록 차단합니다.
- **첫 번째 실행 경험 페이지 표시(모바일 전용)** : **예**(기본값)는 처음 사용하는 Microsoft Edge에 대한 소개 페이지를 표시합니다. **아니요**는 Microsoft Edge를 처음 실행할 때 소개 페이지를 표시하지 못하도록 차단합니다. 이 기능을 사용하면 무배출(zero emission) 구성에 등록된 조직과 같은 기업에서 이 페이지를 차단할 수 있습니다.
- **첫 실행 경험 URL 목록 위치**(Windows 10 Mobile 전용): 첫 번째 실행 페이지 URL이 포함된 XML 파일을 가리키는 URL을 입력합니다. 예를 들어 다음과 같이 입력합니다. `https://www.contoso.com/sites.xml`

- **유휴 시간 후 브라우저 새로 고침**: 브라우저를 새로 고칠 때까지 0-1440분 사이의 유휴 시간(분)을 입력합니다. 기본값은 `5`분입니다. `0`(영)으로 설정하면 유휴 상태 후 브라우저가 새로 고쳐지지 않습니다.

  이 설정은 [InPrivate Public 검색(단일 앱 키오스크)](#use-microsoft-edge-kiosk-mode)에서 실행되는 경우에만 사용할 수 있습니다.

- **팝업 허용**(데스크톱 전용): **예**(기본값)는 웹 브라우저의 팝업을 허용합니다. **아니요**는 브라우저의 팝업 창을 차단합니다.
- **Internet Explorer에 인트라넷 트래픽 보내기**(데스크톱 전용): **예**를 사용하면 사용자가 Microsoft Edge 대신 Internet Explorer에서 인트라넷 웹 사이트를 열 수 있습니다. 이 설정은 이전 버전과의 호환성을 위한 것입니다. **아니요**(기본값)를 사용하면 사용자가 Microsoft Edge를 사용할 수 있습니다.
- **엔터프라이즈 모드 사이트 목록 위치**(데스크톱 전용): 엔터프라이즈 모드에서 열리는 웹 사이트의 목록이 포함된 XML 파일을 가리키는 URL을 입력합니다. 사용자가 이 정보를 변경할 수 없습니다. 예를 들어 다음과 같이 입력합니다. `https://www.contoso.com/sites.xml`
- **Internet Explorer에서 사이트를 열 때 메시지**: 이 설정을 사용하여 Internet Explorer 11에서 사이트가 열리기 전에 알림을 표시하도록 Microsoft Edge를 구성합니다. 옵션은 다음과 같습니다.
  - **메시지를 다시 표시 안 함** : 메시지를 표시하지 않을 수 있는 OS 기본 동작을 사용합니다.
  - **Internet Explorer 11에서 사이트가 열렸다는 메시지 표시**: IE에서 사이트를 열 때 메시지를 표시합니다. 사이트가 IE에서 열립니다. 
  - **Microsoft Edge에서 사이트를 열기 위한 옵션과 함께 메시지 표시**: Microsoft Edge에서 사이트를 열 때 메시지를 표시합니다. 메시지에는 **Keep going in Microsoft Edge**(Microsoft Edge에서 계속) 링크가 포함되므로 사용자가 IE 대신 Microsoft Edge를 선택할 수 있습니다.

  > [!IMPORTANT]
  > 이 설정을 사용하려면 **엔터프라이즈 모드 사이트 목록 위치** 설정, **Internet Explorer에 인트라넷 트래픽 보내기** 설정 또는 두 설정을 모두 사용해야 합니다.

- **Microsoft 호환성 목록 허용**: **예**(기본값)는 Microsoft 호환성 목록을 사용할 수 있도록 허용합니다. **아니요**는 Microsoft Edge에서 Microsoft 호환성 목록을 사용하지 못하도록 차단합니다. Microsoft에서 제공하는 이 목록은 Microsoft Edge에서 알려진 호환성 문제가 있는 사이트를 표시하는 데 유용합니다.
- **시작 페이지 및 새 탭 페이지 미리 로드**: **예**(기본값)는 이러한 페이지를 미리 로드할 수 있는 OS 기본 동작을 사용합니다. 미리 로드하면 Microsoft Edge를 시작하고 새 탭을 로드하는 시간이 최소화됩니다. **아니요**는 Microsoft Edge에서 가 시작 페이지 및 새 탭 페이지를 미리 로드하지 못하도록 차단합니다.
- **시작 페이지 및 새 탭 페이지 사전 시작**: **예**(기본값)는 이러한 페이지를 미리 시작할 수 있는 OS 기본 동작을 사용합니다. 사전 실행하면 Microsoft Edge 성능이 향상될 수 있고 Microsoft Edge를 시작하는 데 필요한 시간이 최소화됩니다. **아니요**는 Microsoft Edge에서 시작 페이지 및 새 탭 페이지를 사전 시작하지 못하도록 차단합니다.

### <a name="favorites-and-search"></a>즐겨찾기 및 검색

- **즐겨찾기 모음 표시**: Microsoft Edge 페이지에서 즐겨찾기 모음에 수행할 작업을 선택합니다. 옵션은 다음과 같습니다.
  - **시작 및 새 탭 페이지에서**: Microsoft Edge 시작 시 및 모든 탭 페이지에서 즐겨찾기 모음을 표시합니다. 이 설정은 최종 사용자가 변경할 수 있습니다.
  - **표시**: 모든 페이지에서 즐겨찾기 모음을 표시합니다. 이 설정은 최종 사용자가 변경할 수 없습니다.
  - **숨김**: 모든 페이지에서 즐겨찾기 모음을 숨깁니다. 이 설정은 최종 사용자가 변경할 수 없습니다.
- **즐겨찾기 변경 허용**: **예**(기본값)는 사용자가 목록을 변경할 수 있도록 허용하는 OS 기본값을 사용합니다. **아니요**는 최종 사용자가 즐겨찾기 목록을 추가, 가져오기, 정렬 또는 편집하지 못하도록 차단합니다.
  - **즐겨찾기 목록**: 즐겨찾기 파일에 URL 목록을 추가합니다. 예를 들어 `http://contoso.com/favorites.html`을 추가합니다.
- **Microsoft 브라우저 간 즐겨찾기 동기화(데스크톱 전용)** : **예**는 Windows에서 Internet Explorer와 Microsoft Edge 간에 즐겨찾기를 동기화하도록 강제로 적용합니다. 즐겨찾기에 대한 추가, 삭제, 수정 및 순서 변경이 브라우저 간에 공유됩니다.  **아니요**(기본값)는 사용자에게 브라우저 간에 즐겨찾기를 동기화하기 위한 선택 항목을 제공할 수 있는 OS 기본값을 사용합니다.
- **기본 검색 엔진**: 디바이스의 기본 검색 엔진을 선택합니다. 최종 사용자는 언제든지 이 값을 변경할 수 있습니다. 옵션은 다음과 같습니다.
  - 클라이언트 Microsoft Edge 설정의 검색 엔진
  - Bing
  - Google
  - Yahoo
  - 사용자 지정 값: **OpenSearch Xml URL**에서 XML 파일이 포함된 HTTPS URL(최소한 검색 엔진에 대한 약식 이름과 URL 포함)을 입력합니다. 예를 들어 다음과 같이 입력합니다. `https://www.contoso.com/opensearch.xml`
- **검색 제안 표시**: **예**(기본값)를 사용하면 주소 표시줄에 검색 구를 입력할 때 검색 엔진에서 사이트를 제안할 수 있습니다. **아니요**는 이 기능을 차단합니다.
- **검색 엔진 변경 허용**: **예**(기본값)를 통해 사용자는 새 검색 엔진을 추가하거나 Microsoft Edge에서 기본 검색 엔진을 변경할 수 있습니다. 사용자가 검색 엔진을 사용자 지정하지 못하도록 하려면 **아니요**를 선택합니다.

  이 설정은 [일반 모드(다중 앱 키오스크)](#use-microsoft-edge-kiosk-mode)에서 실행 중인 때에만 사용할 수 있습니다.

### <a name="privacy-and-security"></a>개인 정보 보호 및 보안

- **InPrivate 브라우징 허용**: **예**(기본값)를 사용하면 Microsoft Edge에서 InPrivate 브라우징을 허용합니다. 모든 InPrivate 탭이 닫히면 Microsoft Edge에서 디바이스의 검색 데이터를 삭제합니다. **아니요**는 최종 사용자가 InPrivate 브라우징 세션을 열지 못하도록 차단합니다.
- **검색 기록 저장**: **예**(기본값)를 사용하면 Microsoft Edge에서 검색 기록을 저장할 수 있습니다. **아니요**는 검색 기록을 저장하지 못하도록 차단합니다.
- **종료 시 검색 데이터 지우기(데스크톱 전용)** : **예**는 사용자가 Microsoft Edge를 종료할 때 기록 및 검색 데이터를 지웁니다. **아니요**는 검색 데이터를 캐시할 수 있는 OS 기본값을 사용합니다.
- **사용자의 디바이스 간 브라우저 설정 동기화**: 디바이스 간 브라우저 설정을 동기화할 방법을 선택합니다. 옵션은 다음과 같습니다.
  - **허용**: 사용자의 디바이스 간에 Microsoft Edge 브라우저 설정을 동기화할 수 있습니다.
  - **사용자 재정의 차단 및 사용**: 사용자의 디바이스 간에 Microsoft Edge 브라우저 설정 동기화를 차단합니다. 사용자가 이 설정을 재정의할 수 있습니다.
  - **차단**: 사용자 디바이스 간의 Microsoft Edge 브라우저 설정 동기화를 차단합니다. 사용자가 이 설정을 재정의할 수 없습니다.

"사용자 재정의 차단 및 사용"을 선택하면 사용자가 관리자 지정을 재정의할 수 있습니다.

- **암호 관리자 허용**: **예**(기본값)를 사용하면 Microsoft Edge에서 암호 관리자를 자동으로 사용할 수 있으므로 사용자가 디바이스에서 암호를 저장하고 관리할 수 있습니다. **아니요**는 Microsoft Edge에서 암호 관리자를 사용하지 못하도록 차단합니다.
- **쿠키**: 웹 브라우저에서 쿠키 처리 방법을 선택합니다. 옵션은 다음과 같습니다.
  - **허용**: 쿠키가 디바이스에 저장됩니다.
  - **모든 쿠키 차단**: 쿠키가 디바이스에 저장되지 않습니다.
  - **타사 쿠키만 차단**: 타사 또는 파트너 쿠키가 디바이스에 저장되지 않습니다.
- **양식 자동 채우기 허용**: **예**(기본값)를 사용하면 브라우저에서 자동 완성 설정을 변경하고 양식 필드를 자동으로 채울 수 있습니다. **아니요**는 Microsoft Edge에서 자동 채우기 기능을 사용하지 않도록 설정합니다.
- **Do Not Track 헤더 보내기**: **예**는 추적 정보를 요청하는 웹 사이트에 Do Not Track 헤더를 보냅니다(추천). **아니요**는 웹 사이트에서 사용자를 추적할 수 있는 헤더를 보내지 않습니다. 이 설정은 사용자가 구성할 수 있습니다.
- **WebRTC localhost IP 주소 표시**: **예**를 사용하면 이 프로토콜을 사용하여 전화를 걸 때 사용자의 localhost IP 주소를 표시할 수 있습니다. **아니요**는 사용자의 localhost IP 주소를 표시하지 못하도록 차단합니다. 
- **라이브 타일 데이터 수집 허용**: **예**(기본값)를 사용하면 Microsoft Edge에서 시작 메뉴에 고정된 라이브 타일로부터 정보를 수집할 수 있습니다. **아니요**는 사용자에게 제한된 환경을 제공할 수 있는 이 정보를 수집하지 못하도록 차단합니다.
- **사용자가 인증서 오류를 재정의할 수 있음**: **예**(기본값)를 사용하면 사용자가 SSL/TLS(Secure Sockets Layer/Transport Layer Security) 오류가 있는 웹 사이트에 액세스할 수 있습니다. **아니요**(보안 향상을 위해 추천됨)는 사용자가 SSL 또는 TLS 오류가 있는 웹 사이트에 액세스하지 못하도록 차단합니다.

### <a name="additional"></a>추가 정보

- **Microsoft Edge 브라우저 허용**(모바일 전용): **예**(기본값)를 사용하면 모바일 디바이스에서 Microsoft Edge 웹 브라우저를 사용할 수 있습니다. **아니요**는 디바이스에서 Microsoft Edge를 사용하지 못하도록 차단합니다. **아니요**를 선택하는 경우 다른 개별 설정은 데스크톱에만 적용됩니다.
- **주소 표시줄 드롭다운 허용**: **예**(기본값)를 사용하면 Microsoft Edge에서 제안 목록이 있는 주소 표시줄 드롭다운을 표시할 수 있습니다. **아니요**는 입력 시 Microsoft Edge에서 드롭다운 목록에 제안 목록을 표시하지 못하도록 차단합니다. **아니요**로 설정하면 다음을 수행합니다.
  - Microsoft Edge와 Microsoft 서비스 간의 네트워크 대역폭을 최소화하는 데 도움이 됩니다.
  - Microsoft Edge> 설정에서 **입력할 때 검색 및 사이트 제안 표시**를 사용하지 않도록 설정합니다.
- **전체 화면 모드 허용**: **예**(기본값)를 사용하면 Microsoft Edge에서 웹 콘텐츠만 표시하고 Microsoft Edge UI를 숨기는 전체 화면 모드를 사용할 수 있습니다. **아니요**는 Microsoft Edge에서 전체 화면 모드를 차단합니다.
- **플래그 페이지 정보 허용**: **예**(기본값)는 `about:flags` 페이지에 액세스하도록 허용할 수 있는 OS 기본값을 사용합니다. `about:flags` 페이지를 사용하면 사용자가 개발자 설정을 변경하고 실험 기능을 사용하도록 설정할 수 있습니다. **아니요**는 최종 사용자가 Microsoft Edge에서 `about:flags` 페이지에 액세스하지 못하도록 차단합니다.
- **개발자 도구 허용**: **예**(기본값)를 사용하면 사용자가 기본적으로 F12 개발자 도구를 사용하여 웹 페이지를 작성하고 디버그할 수 있습니다. **아니요**는 최종 사용자가 F12 개발자 도구를 사용하지 못하도록 차단합니다.
- **JavaScript 허용**: **예**(기본값)를 사용하면 Javascript와 같은 스크립트를 Microsoft Edge 브라우저에서 실행할 수 있습니다. **아니요**는 브라우저에서 Java 스크립트를 실행하지 못하도록 차단합니다.
- **사용자가 확장을 설치할 수 있음**: **예**(기본값)를 사용하면 최종 사용자가 디바이스에 Microsoft Edge 확장을 설치할 수 있습니다. **아니요**는 설치를 차단합니다.
- **개발자 확장 사이드로드 허용**: **예**(기본값)는 사이드로드를 허용할 수 있는 OS 기본값을 사용합니다. 사이드로드는 확인되지 않은 확장을 설치하고 실행합니다. **아니요**는 Microsoft Edge에서 **확장 로드** 기능을 사용하여 사이드로드하지 못하도록 차단합니다. PowerShell과 같은 다른 방법을 사용하여 확장을 사이드로드하는 것은 방지하지 않습니다.
- **필요한 확장**: Microsoft Edge에서 최종 사용자가 끌 수 없는 확장을 선택합니다. 패키지 패밀리 이름을 입력하고 **추가**를 선택합니다. [PFN(패키지 패밀리 이름) 찾기](https://docs.microsoft.com/sccm/protect/deploy-use/find-a-pfn-for-per-app-vpn)는 몇 가지 지침을 제공합니다.

  패키지 패밀리 이름을 포함하는 CSV 파일을 **가져올** 수도 있습니다. 또는 입력한 패키지 패밀리 이름을 **내보냅니다**.

## <a name="network-proxy"></a>네트워크 프록시

다음 설정에서는 [NetworkProxy 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/networkproxy-csp)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **자동으로 프록시 설정 검색**: **차단**은 디바이스에서 PAC(프록시 자동 구성) 스크립트를 자동으로 검색하지 않도록 설정합니다. **구성되지 않음**(기본값)은 이 기능을 사용하도록 설정합니다. 사용하도록 설정되면 디바이스에서 PAC 스크립트 경로를 찾으려고 합니다.
- **프록시 스크립트 사용**: **허용**을 선택하면 프록시 서버를 구성할 PAC 스크립트의 경로를 입력할 수 있습니다. **구성되지 않음**(기본값)을 사용하면 PAC 스크립트의 URL을 입력할 수 없습니다.
  - **설정 스크립트 주소 URL**: 프록시 서버를 구성하는 데 사용할 PAC 스크립트의 URL을 입력합니다.
- **수동 프록시 서버 사용**: **허용**을 선택하면 프록시 서버의 이름 또는 IP 주소와 TCP 포트 번호를 수동으로 입력할 수 있습니다. **구성되지 않음**(기본값)을 사용하면 프록시 서버의 세부 정보를 수동으로 입력할 수 없습니다.
  - **주소**: 프록시 서버의 이름 또는 IP 주소를 입력합니다.
  - **포트 번호**: 프록시 서버의 포트 번호를 입력합니다.
  - **프록시 예외**: 프록시 서버를 사용하지 말아야 하는 URL을 입력합니다. 각각 구분을 위해 세미콜론을 사용하세요.
  - **로컬 주소에 프록시 서버 사용 안 함**: **구성되지 않음**(기본값)은 프록시 서버를 인트라넷의 로컬 주소에 사용하지 못하도록 차단합니다. **허용**은 프록시 서버를 로컬 주소에 사용합니다.

## <a name="password"></a>암호

다음 설정에서는 [DeviceLock 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **암호**: **필요**를 선택하면 최종 사용자에게 디바이스에 액세스하기 위해 암호를 입력해야 합니다. **구성되지 않음**(기본값)을 사용하면 암호 없이 디바이스에 액세스할 수 있습니다. 로컬 계정에만 적용 됩니다. 도메인 계정 암호는 AD (Active Directory) 및 Azure AD에 의해 구성 된 상태로 유지 됩니다.

  - **필수 암호 유형**: 암호 유형을 선택합니다. 옵션은 다음과 같습니다.
    - **구성되지 않음**: 숫자와 문자가 포함될 수 있는 임호입니다.
    - **숫자**: 숫자로만 구성된 암호여야 합니다.
    - **영숫자**: 암호가 숫자와 문자가 혼합된 암호여야 합니다.
  - **최소 암호 길이**: 필요한 최소 숫자 또는 문자 수(4-16)를 입력합니다. 예를 들어 암호 길이에 6자 이상의 문자가 필요하면 `6`을 입력합니다.
  
    > [!IMPORTANT]
    > Windows 데스크톱에서 암호 요구 사항이 변경되면 사용자가 다음에 로그인할 때 영향을 받습니다. 디바이스가 유휴 상태에서 활성 상태로 변하기 때문입니다. 요구 사항을 충족하는 암호를 사용하는 사용자에게도 암호를 변경하라는 메시지가 표시됩니다.
    
  - **디바이스를 초기화하기 전 로그인 오류 발생 횟수**: 디바이스를 초기화하기 전에 허용되는 인증 실패 횟수를 11 이내로 입력합니다. 입력 하는 유효한 숫자는 버전에 따라 다릅니다. [Devicelock/MAXDEVICEPASSWORDFAILEDATTEMPTS CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts) 는 지원 되는 값을 나열 합니다. `0`(0)은 디바이스 초기화 기능을 사용하지 않도록 설정할 수 있습니다.

    이 설정은 버전에 따라 다른 영향도 줍니다. 이 설정에 대한 관련 세부 정보는 [DeviceLock/MaxDevicePasswordFailedAttempts CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-maxdevicepasswordfailedattempts)를 참조하세요.

  - **화면이 잠기기 전까지 최대 비활성 시간(분)** : 화면이 잠기기 전에 디바이스가 유휴 상태여야 하는 기간을 입력합니다.
  - **암호 만료(일)** : 디바이스 암호를 변경해야 하는 만료 시간(1-365일)을 입력합니다. 예를 들어 암호가 90일 후에 만료되도록 하려면 `90`을 입력합니다.
  - **이전 암호 다시 사용 안 함**: 이전에 사용하여 다시 사용할 수 없는 암호의 수(1-24)를 입력합니다. 예를 들어 사용자가 새 암호를 현재 암호 또는 이전 4개의 암호 중 하나로 설정할 수 없도록 하려면 `5`를 입력합니다.
  - **디바이스가 유휴 상태에서 되돌아올 때 암호 요구**(Mobile 및 Holographic): **필요**를 선택하면 사용자가 암호를 입력하여 유휴 상태 이후의 디바이스 잠금을 해제할 수 있습니다. **구성되지 않음**(기본값)은 디바이스가 유휴 상태에서 다시 시작될 때 PIN 또는 암호를 요구하지 않습니다.
  - **단순 암호**: **차단**으로 설정하면 사용자가 `1234` 또는 `1111`과 같은 단순 암호를 만들 수 없습니다. **구성되지 않음**(기본값)으로 설정하면 사용자가 `1234` 또는 `1111`과 같은 암호를 만들 수 있습니다. 또한 이 설정은 Windows 사진 암호의 사용을 허용하거나 차단합니다.
- **AADJ 중 자동 암호화**: **블록**은 Azure AD가 조인된 디바이스가 처음 사용할 준비가 되었을 때 자동 BitLocker 디바이스 암호화를 방지합니다. **구성되지 않음**(기본값)을 통해 암호화를 사용하도록 설정할 수 있는 운영 체제 기본값을 사용합니다. [BitLocker 디바이스 암호화](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10#bitlocker-device-encryption)에 대한 추가 정보.

  [Security/PreventAutomaticDeviceEncryptionForAzureADJoinedDevices CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-security#security-preventautomaticdeviceencryptionforazureadjoineddevices)

- **FIPS(Federal Information Processing Standard) 정책**: **허용**을 선택하면 암호화, 해시 및 서명에 대한 미국 정부 표준인 FIPS(Federal Information Processing Standard) 정책을 사용합니다. **구성되지 않음**(기본값)을 통해 FIPS를 사용하지 않는 운영 체제 기본값을 사용합니다.

  [Cryptography/AllowFipsAlgorithmPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-cryptography#cryptography-allowfipsalgorithmpolicy)

- **Windows Hello 디바이스 인증**: **허용**을 선택하면 사용자가 전화, 적합성 대역 또는 IoT 디바이스와 같은 Windows Hello 포함 디바이스를 사용하여 Windows 10 컴퓨터에 로그인할 수 있습니다. **구성되지 않음**(기본값)을 통해 운영 체제 기본값을 사용하므로 Windows Hello 포함 디바이스가 Windows에서 인증됩니다.

  [Authentication/AllowSecondaryAuthenticationDevice CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-allowsecondaryauthenticationdevice)

- **웹 로그인**: SAML(Security Assertion Markup Language)과 같은 비 ADFS(Active Directory Federation Services) 페더레이션 공급자에 대한 Windows 로그인 지원을 사용하도록 설정합니다. SAML은 웹 브라우저에 SSO(Single Sign-On) 환경을 제공하는 보안 토큰을 사용합니다. 옵션은 다음과 같습니다.

  - **구성되지 않음**(기본값): 디바이스의 운영 체제 기본값을 사용합니다.
  - **사용 가능**: 웹 자격 증명 공급자가 로그인할 수 있습니다.
  - **사용 안 함**: 웹 자격 증명 공급자가 로그인할 수 없습니다.

  [Authentication/EnableWebSignIn CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-enablewebsignin)

- **기본 Azure AD 테넌트 도메인**: Azure AD 조직에 기존 도메인 이름을 입력합니다. 이 도메인의 사용자가 로그인할 때 도메인 이름을 입력할 필요가 없습니다. 예를 들어 다음과 같이 입력합니다. `contoso.com` `contoso.com` 도메인의 사용자는 `abby@contoso.com` 대신 `abby`와 같은 사용자 이름을 사용하여 로그인할 수 있습니다.

  [Authentication/PreferredAadTenantDomainName CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-authentication#authentication-preferredaadtenantdomainname)

## <a name="per-app-privacy-exceptions"></a>앱별 개인 정보 예외

"기본 개인 정보"에 정의된 것과 다른 개인 정보 동작이 필요한 앱을 추가할 수 있습니다.

- **패키지 이름**: 앱 패키지 패밀리 이름입니다.
- **앱 이름**: 앱 이름입니다.

### <a name="exceptions"></a>예외

- **계정 정보**: 이 앱에서 사용자 이름, 사진 및 기타 연락처 정보에 액세스할 수 있는지 여부를 정의합니다.
- **백그라운드 앱**: 이 앱을 백그라운드에서 실행할 수 있는지 여부를 정의합니다.
- **일정**: 이 앱에서 일정에 액세스할 수 있는지 여부를 정의합니다.
- **통화 기록**: 이 앱에서 내 통화 기록에 액세스할 수 있는지 여부를 정의합니다.
- **카메라**: 이 앱에서 카메라에 액세스할 수 있는지 여부를 정의합니다.
- **연락처**: 이 앱에서 연락처에 액세스할 수 있는지 여부를 정의합니다.
- **메일**: 이 앱에서 메일에 액세스하고 메일을 보낼 수 있는지 여부를 정의합니다.
- **위치**: 이 앱에서 위치 정보에 액세스할 수 있는지 여부를 정의합니다.
- **메시지**: 이 앱에서 문자 메시지 또는 MMS 메시지를 읽거나 보낼 수 있는지 여부를 정의합니다.
- **마이크**: 이 앱에서 마이크를 사용할 수 있는지 여부를 정의합니다.
- **동작**: 이 앱에서 디바이스 동작 정보에 액세스할 수 있는지 여부를 정의합니다.
- **알림**: 이 앱에서 알림에 액세스할 수 있는지 여부를 정의합니다.
- **전화**: 이 앱에서 전화에 액세스할 수 있는지 여부를 정의합니다.
- **송수신 디바이스**: 일부 앱은 디바이스의 송수신 디바이스(예: Bluetooth)를 사용하여 데이터를 보내고 받으며 이러한 송수신 디바이스를 켜거나 꺼야 합니다. 이 앱에서 이러한 송수신 장치를 제어할 수 있는지 여부를 정의합니다.
- **작업**: 이 앱에서 작업에 액세스할 수 있는지 여부를 정의합니다.
- **신뢰할 수 있는 디바이스**: 이 앱에서 신뢰할 수 있는 디바이스를 사용할 수 있는지 여부를 선택합니다. 신뢰할 수 있는 디바이스는 이미 연결된 하드웨어 또는 디바이스와 함께 제공되는 하드웨어입니다. 예를 들어 TV, 프로젝터 등을 신뢰할 수 있는 디바이스로 사용합니다.
- **피드백 및 진단**: 이 앱에서 진단 정보에 액세스할 수 있는지 여부를 정의합니다.
- **디바이스와 동기화**: 이 앱에서 디바이스와 명시적으로 페어링되지 않은 무선 디바이스와 정보를 자동으로 공유 및 동기화할 수 있는지 여부를 선택합니다.

## <a name="personalization"></a>Personalization

다음 설정에서는 [맞춤 설정 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/personalization-csp)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **바탕 화면 배경 그림 URL(바탕 화면만 해당)** : Windows 바탕 화면 배경으로 사용하려는 .jpg, .jpeg 또는 .png 형식의 그림에 대한 URL을 입력합니다. 사용자는 그림을 변경할 수 없습니다. 예를 들어 다음과 같이 입력합니다. `https://contoso.com/logo.png`

## <a name="printer"></a>프린터

- **프린터**: 추가된 로컬 프린터 목록입니다.
- **기본 프린터**: 기본 프린터를 설정합니다.
- **새 프린터 추가에 대한 사용자 액세스**: 로컬 프린터 사용을 허용하거나 차단합니다.

## <a name="privacy"></a>개인 정보 취급 방침

다음 설정에서는 [개인 정보 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **입력 개인 설정**: **차단**은 음성을 받아쓰기에 사용하지 못하도록 차단하고, Microsoft 클라우드 기반 음성 인식을 사용하는 Cortana 및 다른 앱과도 대화하지 못하도록 차단합니다. 그러면 이 기능을 사용하지 않도록 지정되고 사용자가 설정을 사용하여 온라인 음성 인식을 사용할 수 없습니다. **구성되지 않음**(기본값)을 사용하면 사용자가 이 기능을 선택할 수 있습니다. 이러한 서비스를 허용하면 Microsoft에서 서비스를 향상시키기 위해 음성 데이터를 수집할 수 있습니다.
- **페어링 및 개인 정보 보호 사용자 동의 프롬프트의 자동 수락**: **허용**을 선택하면 Windows에서 앱을 실행할 때 페어링 및 개인 정보 보호 동의 메시지를 자동으로 수락할 수 있습니다. **구성되지 않음**(기본값)은 앱을 열 때 페어링 및 개인 정보 사용자 동의 창을 자동으로 수락하지 못하도록 차단합니다.
- **사용자 작업 게시**: **차단**은 작업 피드에서 최근에 사용한 리소스의 공유 환경 및 검색을 차단합니다. **구성되지 않음**(기본값)은 이 기능을 사용하여 앱에서 최종 사용자 작업을 게시할 수 있도록 설정합니다.
- **로컬 작업 전용**: **차단**을 선택하면 로컬 작업만 기반으로 작업 전환기에서 최근에 사용한 리소스의 공유 경험 및 검색이 제한됩니다. **구성되지 않음**(기본값)은 이 기능을 사용하도록 설정합니다.

디바이스의 모든 앱이 액세스할 수 있는 정보를 구성할 수 있습니다. **앱별 개인 정보 예외**를 사용하여 앱별 예외를 정의할 수 있습니다.

### <a name="exceptions"></a>예외

- **계정 정보**: 이 앱에서 사용자 이름, 사진 및 기타 연락처 정보에 액세스할 수 있는지 여부를 정의합니다.
- **백그라운드 앱**: 이 앱을 백그라운드에서 실행할 수 있는지 여부를 정의합니다.
- **일정**: 이 앱에서 일정에 액세스할 수 있는지 여부를 정의합니다.
- **통화 기록**: 이 앱에서 내 통화 기록에 액세스할 수 있는지 여부를 정의합니다.
- **카메라**: 이 앱에서 카메라에 액세스할 수 있는지 여부를 정의합니다.
- **연락처**: 이 앱에서 연락처에 액세스할 수 있는지 여부를 정의합니다.
- **메일**: 이 앱에서 메일에 액세스하고 메일을 보낼 수 있는지 여부를 정의합니다.
- **위치**: 이 앱에서 위치 정보에 액세스할 수 있는지 여부를 정의합니다.
- **메시지**: 이 앱에서 문자 메시지 또는 MMS 메시지를 읽거나 보낼 수 있는지 여부를 정의합니다.
- **마이크**: 이 앱에서 마이크를 사용할 수 있는지 여부를 정의합니다.
- **동작**: 이 앱에서 디바이스 동작 정보에 액세스할 수 있는지 여부를 정의합니다.
- **알림**: 이 앱에서 알림에 액세스할 수 있는지 여부를 정의합니다.
- **전화**: 이 앱에서 전화에 액세스할 수 있는지 여부를 정의합니다.
- **송수신 디바이스**: 일부 앱은 디바이스의 송수신 디바이스(예: Bluetooth)를 사용하여 데이터를 보내고 받으며 이러한 송수신 디바이스를 켜거나 꺼야 합니다. 이 앱에서 이러한 송수신 장치를 제어할 수 있는지 여부를 정의합니다.
- **작업**: 이 앱에서 작업에 액세스할 수 있는지 여부를 정의합니다.
- **신뢰할 수 있는 디바이스**: 이 앱에서 신뢰할 수 있는 디바이스를 사용할 수 있는지 여부를 선택합니다. 신뢰할 수 있는 디바이스는 이미 연결된 하드웨어 또는 디바이스와 함께 제공되는 하드웨어입니다. 예를 들어 TV, 프로젝터 등을 신뢰할 수 있는 디바이스로 사용합니다.
- **피드백 및 진단**: 이 앱에서 진단 정보에 액세스할 수 있는지 여부를 선택합니다.
- **디바이스와 동기화** - 이 앱에서 이 PC, 태블릿 또는 휴대폰과 명시적으로 페어링되지 않은 무선 디바이스와 정보를 자동으로 공유 및 동기화할 수 있는지 여부를 정의합니다.

## <a name="projection"></a>프로젝션

다음 설정에서는 [WirelessDisplay 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-wirelessdisplay)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **무선 디스플레이 수신기의 사용자 입력**: **차단**은 무선 디스플레이 수신기에서 사용자 입력을 차단합니다. **구성되지 않음**(기본값)을 사용하면 키보드, 마우스, 펜 및 터치식 입력을 무선 디스플레이에서 원본 디바이스로 다시 보낼 수 있습니다.
- **이 PC로 프로젝션**: **차단**은 다른 디바이스에서 프로젝션할 디바이스를 찾지 못하도록 방지합니다. **구성되지 않음**(기본값)을 사용하면 디바이스를 검색할 수 있으며 디바이스의 잠금 화면 위에 프로젝션할 수 있습니다.
- **페어링 시 PIN 필요**: **필요**를 선택하면 프로젝션 디바이스에 연결할 때 항상 PIN을 입력하라는 메시지를 표시할 수 있습니다. **구성되지 않음**(기본값)은 디바이스를 프로젝션 디바이스에 페어링하기 위해 PIN을 요구하지 않습니다.

## <a name="reporting-and-telemetry"></a>모니터링 및 원격 분석

- **사용량 현황 데이터 공유**: 전송되는 진단 데이터 수준을 선택합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**: 데이터가 공유되지 않습니다.
  - **보안**: 연결된 사용자 환경 및 원격 분석 구성 요소 설정, 악성 소프트웨어 제거 도구 및 Windows Defender에 대한 데이터를 포함하여 Windows 보안을 더욱 강화하는 데 필요한 정보입니다.
  - **기본**: 품질 관련 데이터, 앱 호환성, 앱 사용량 데이터 및 보안 수준 데이터를 포함한 기본 디바이스 정보입니다.
  - **고급**: Windows, Windows Server, System Center 및 앱을 사용하는 방법, 성능, 고급 안정성 데이터 및 기본 및 보안 수준 모두의 데이터를 포함한 추가 인사이트입니다.
  - **전체**: 보안, 기본 및 고급 수준의 데이터를 포함하여 문제를 식별하고 해결하는 데 필요한 모든 데이터입니다.

  [System/AllowTelemetry CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

- **Microsoft 365 분석으로 Microsoft Edge 검색 데이터 보내기**: 이 기능을 사용하려면 **사용량 현황 데이터 공유** 설정을 **고급** 또는 **전체**로 설정합니다. 이 기능은 Microsoft Edge에서 구성된 상업용 ID가 있는 엔터프라이즈 디바이스에 대해 Microsoft 365 분석에 보내는 데이터를 제어합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**: OS 기본값을 사용하므로 검색 기록 데이터를 보낼 수 없습니다.
  - **인트라넷 데이터만 보내기**: 관리자가 인트라넷 데이터 기록을 보낼 수 있습니다.
  - **인터넷 데이터만 보내기**: 관리자가 인터넷 데이터 기록을 보낼 수 있습니다.
  - **인트라넷 및 인터넷 데이터 보내기**: 관리자가 인트라넷 및 인터넷 데이터 기록을 보낼 수 있습니다.

  [Browser/ConfigureTelemetryForMicrosoft365Analytics CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-configuretelemetryformicrosoft365analytics)

- **원격 분석 프록시 서버**: SSL(Secure Sockets Layer) 연결을 사용하여 연결된 사용자 환경 및 원격 분석 요청을 전달할 프록시 서버의 FQDN(정규화된 도메인 이름) 또는 IP 주소를 입력합니다. 이 설정의 형식은 *server*:*port*입니다. 명명된 프록시가 실패할 경우 또는 이 정책을 사용하도록 설정할 때 프록시를 입력하지 않은 경우 연결된 사용자 환경 및 원격 분석 데이터가 전송되지 않고 로컬 디바이스에 남아 있습니다.

  형식 예:

  ```
  IPv4: 192.246.246.106:100
  IPv6: [2001:4898:4010:4013:95c1:a8b2:953c:c633]:100
  FQDN: www.contoso.com:345
  ```

  [System/TelemetryProxy CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-system#system-telemetryproxy)

**확인**을 선택하여 변경 내용을 저장합니다.

## <a name="search"></a>검색

다음 설정에서는 [검색 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-search)를 사용하며, 지원되는 Windows 버전도 나열합니다. 

- **안전 검색(모바일 전용)** : Cortana가 검색 결과에서 성인 콘텐츠를 필터링하는 방법을 제어합니다. 옵션은 다음과 같습니다.
  - **사용자 정의**: 최종 사용자가 자신의 설정을 선택할 수 있습니다.
  - **고급**: 성인 콘텐츠에 대한 최고 수준의 필터링입니다.
  - **보통**: 성인 콘텐츠에 대한 중간 수준의 필터링입니다. 유효한 검색 결과는 필터링되지 않습니다.
- **검색에 웹 결과 표시**: **차단**으로 설정하면 사용자가 검색할 수 없으며 웹 결과가 Search에 표시되지 않습니다. **구성되지 않음**(기본값)을 사용하면 사용자가 웹을 검색할 수 있으며 결과가 디바이스에 표시됩니다.

## <a name="start"></a>시작

다음 설정에서는 [시작 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start)를 사용하며, 지원되는 Windows 버전도 나열합니다.  

- **시작 메뉴 레이아웃**: 기본 시작 레이아웃을 재정의하고 데스크톱 디바이스의 시작 메뉴를 사용자 지정합니다. 앱이 나열된 순서 등을 포함하여 사용자 지정이 포함된 XML 파일을 업로드합니다. 개발자가 입력한 시작 메뉴 레이아웃은 사용자가 변경할 수 없습니다.
- **시작 메뉴의 타일에 웹 사이트 고정**: 데스크톱 디바이스용 Windows 시작 메뉴에 링크로 표시되는 Microsoft Edge에서 이미지를 가져옵니다.
- **작업 표시줄에서 앱 고정 해제**: **차단**은 사용자가 작업 표시줄에서 앱 고정을 해제하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 작업 표시줄에서 앱 고정을 해제할 수 있습니다.
- **빠른 사용자 전환**: **차단**은 로그오프하지 않고 동시에 로그온한 사용자 간의 전환을 차단합니다. **구성되지 않음**(기본값)은 사용자 타일에서 **사용자 전환**을 표시합니다.
- **가장 많이 사용한 앱**: **차단**은 시작 메뉴에서 가장 많이 사용한 앱을 표시하지 않도록 숨깁니다. 또한 설정 앱에서 해당 토글을 비활성화합니다. **구성되지 않음**(기본값)은 가장 많이 사용한 앱을 표시합니다.
- **최근 추가된 앱**: **차단**은 시작 메뉴에서 최근에 추가한 앱을 표시하지 않도록 숨깁니다. 또한 설정 앱에서 해당 토글을 비활성화합니다. **구성되지 않음**(기본값)은 시작 메뉴에서 최근에 추가한 앱을 표시합니다.
- **시작 화면 모드**: 시작 화면이 표시되는 방법을 선택합니다. 옵션은 다음과 같습니다.
  - **사용자 정의**: 시작 크기를 강제로 적용하지 않습니다. 사용자가 크기를 설정할 수 있습니다.
  - **전체 화면**: 전체 화면 크기를 강제로 적용합니다.
  - **전체 화면 아님**: 전체 화면이 아닌 시작 크기를 강제로 적용합니다.
- **점프 목록의 최근에 연 항목**: **차단**은 시작 메뉴 및 작업 표시줄에서 최근 점프 목록을 표시하지 않도록 숨깁니다. 또한 설정 앱에서 해당 토글을 비활성화합니다. **구성되지 않음**(기본값)은 점프 목록에서 최근에 연 항목을 표시합니다.
- **앱 목록**: 모든 앱 목록을 표시하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  - **사용자 정의**: 설정을 강제로 적용하지 않습니다. 사용자가 디바이스에서 앱 목록을 표시하는 방법을 선택합니다.
  - **축소**: 모든 앱 목록을 숨깁니다.
  - **설정 앱 축소 및 사용 안 함**: 모든 앱 목록을 숨기고, 설정 앱에서 **시작 메뉴에서 앱 목록 표시**를 사용하지 않도록 설정합니다.
  - **설정 앱 제거 및 사용 안 함**: 모든 앱 목록을 숨기고, 모든 앱 단추를 제거한 다음, 설정 앱에서 **시작 메뉴에서 앱 목록 표시**를 사용하지 않도록 설정합니다.
- **전원 단추**: **차단**은 시작 메뉴에서 전원 단추를 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 전원 단추를 표시합니다.
- **사용자 타일**: **차단**은 사용자 타일이 시작 메뉴에 표시되지 않도록 숨깁니다. **구성되지 않음**(기본값)은 사용자 타일을 표시하고 다음 설정도 설정합니다.
  - **잠금**: **차단**은 시작 메뉴의 사용자 타일에서 **잠금** 옵션을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 **잠금** 옵션을 표시합니다.
  - **로그아웃**: **차단**은 시작 메뉴의 사용자 타일에서 **로그아웃** 옵션을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 **로그아웃** 옵션을 표시합니다.
- **종료**: **차단**은 시작 메뉴의 전원 단추에서 **업데이트 및 종료** 및 **종료** 옵션을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 이러한 옵션을 표시합니다.
- **절전 모드**: **차단**은 시작 메뉴의 전원 단추에서 **절전 모드** 옵션을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 이 옵션을 표시합니다.
- **최대 절전 모드**: **차단**은 시작 메뉴의 전원 단추에서 **최대 절전 모드** 옵션을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 이 옵션을 표시합니다.
- **계정 전환**: **차단**은 시작 메뉴의 사용자 타일에서 **계정 전환**을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 이 옵션을 표시합니다.
- **다시 시작 옵션**: **차단**은 시작 메뉴의 전원 단추에서 **업데이트 및 다시 시작** 및 **다시 시작** 옵션을 표시하지 않도록 숨깁니다. **구성되지 않음**(기본값)은 이러한 옵션을 표시합니다.
- **시작 메뉴의 문서**: Windows 시작 메뉴에서 문서 폴더를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 다운로드**: Windows 시작 메뉴에서 다운로드 폴더를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 파일 탐색기**: Windows 시작 메뉴에서 파일 탐색기를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 홈 그룹**: Windows 시작 메뉴에서 홈 그룹 바로 가기를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 음악**: Windows 시작 메뉴에서 음악 폴더를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 네트워크**: Windows 시작 메뉴에서 네트워크를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 개인 폴더**: Windows 시작 메뉴에서 개인 폴더를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 그림**: Windows 시작 메뉴에서 그림 폴더를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 설정**: Windows 시작 메뉴에서 설정 바로 가기를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
- **시작 메뉴의 비디오**: Windows 시작 메뉴에서 비디오 폴더를 숨기거나 표시합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): 설정을 강제로 적용하지 않습니다. 사용자가 바로 가기를 표시하거나 숨기도록 선택합니다.
  - **숨기기**: 바로 가기를 숨기고 설정 앱에서 설정을 사용하지 않도록 설정합니다.
  - **표시**: 바로 가기를 표시하고 설정 앱에서 설정을 사용하지 않도록 설정합니다.

## <a name="windows-defender-smart-screen"></a>Windows Defender Smart Screen

- **Microsoft Edge용 SmartScreen**: **필요**는 Windows Defender SmartScreen을 해제하고, 사용자가 이를 설정하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 SmartScreen을 설정합니다. 사용자를 잠재적인 위협으로부터 보호하고 사용자가 이를 해제하지 못하도록 차단합니다.

  Microsoft Edge는 Windows Defender SmartScreen(설정됨)을 사용하여 잠재적 피싱 사기 및 악성 소프트웨어로부터 사용자를 보호합니다.

  [Browser/AllowSmartScreen CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

- **악성 사이트 액세스**: **차단**은 사용자가 Windows Defender SmartScreen 필터 경고를 무시하지 못하도록 차단하고, 사이트로도 이동하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 경고를 무시하고 사이트를 계속 사용할 수 있습니다.

  [Browser/PreventSmartScreenPromptOverride CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride)

- **확인되지 않은 파일 다운로드**: **차단**은 사용자가 Windows Defender SmartScreen 필터 경고를 무시하지 못하도록, 확인되지 않은 파일도 다운로드하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자가 경고를 무시하고 확인되지 않은 파일을 계속 다운로드할 수 있습니다.

  [Browser/PreventSmartScreenPromptOverrideForFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles)

## <a name="windows-spotlight"></a>Windows 추천

다음 설정에서는 [환경 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-experience)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **Windows 추천**: **차단**은 잠금 화면, Windows 팁, Microsoft 소비자 기능 및 기타 관련 기능의 Windows 추천을 해제합니다. 디바이스의 네트워크 트래픽을 최소화하려면 이 기능을 **차단**으로 설정합니다. **구성되지 않음**(기본값)은 Windows 추천 기능을 허용하며 최종 사용자가 제어할 수 있습니다. 사용하도록 설정하면 다음 설정도 허용하거나 차단할 수 있습니다.

  - **잠금 화면에서 Windows 추천**: **차단**은 Windows 추천을 통해 정보를 디바이스 잠금 화면에 표시하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 이 기능을 사용하도록 설정합니다.
  - **Windows 추천에서의 타사 제안**: **차단**은 Windows 추천을 통해 Microsoft에서 게시하지 않은 콘텐츠를 제안하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 Windows 추천 기능에서 타사 소프트웨어 게시자에 의한 앱 및 콘텐츠 제안(예: 잠금 화면 추천, 시작 메뉴에 제안된 앱 및 Windows 팁)을 허용합니다.
  - **소비자 기능**: **차단**은 일반적으로 소비자만을 대상으로 하는 환경(예: 시작 제안, 구성원 자격 알림, 사후 OOBE(out of box experience) 앱 설치 및 리디렉션 타일)을 해제합니다. **구성되지 않음**(기본값)은 이러한 기능을 허용합니다.
  - **Windows 팁**: **차단**은 팝업 Windows 팁을 사용하지 않도록 설정합니다. **구성되지 않음**(기본값)을 사용하면 Windows 팁을 표시할 수 있습니다.
  - **알림 센터의 Windows 추천**: **차단**은 알림 센터에서 Windows 추천 알림을 표시하지 못하도록 차단합니다. **구성되지 않음**(기본값)은 Windows에서 사용자의 생산성을 향상시키는 데 도움이 되는 앱 또는 기능을 제안하는 알림을 알림 센터에 표시할 수 있습니다.
  - **Windows 추천 맞춤 설정**: **차단**은 Windows에서 진단 데이터를 사용하여 사용자에 맞춘 사용자 지정 환경을 제공하지 못하도록 차단합니다. **구성되지 않음**(기본값)을 사용하면 사용자 요구 사항에 맞게 Windows를 조정할 수 있도록 Microsoft에서 진단 데이터를 사용하여 맞춤형 추천, 팁 및 제안을 제공할 수 있습니다.
  - **Windows 시작 환경**: **차단**은 Windows 추천의 Windows 시작 환경 기능을 해제합니다. Windows 및 해당 앱에 대한 업데이트와 변경 내용이 있으면 Windows 시작 환경이 표시되지 않습니다. **구성되지 않음**(기본값)은 사용자에게 새롭거나 업데이트된 기능에 대한 정보를 표시하는 Windows 시작 환경을 허용합니다.

## <a name="microsoft-defender-antivirus"></a>Microsoft Defender 바이러스 백신

다음 설정에서는 [Defender 정책 CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)를 사용하며, 지원되는 Windows 버전도 나열합니다.

- **실시간 모니터링**: **사용**하면 맬웨어, 스파이웨어 및 기타 사용자 동의 없이 설치된 소프트웨어에 대한 실시간 검사를 켭니다. 이 옵션은 사용자가 해제할 수 없습니다. 

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는이 기능을 설정 하 고 사용자가 변경할 수 있도록 허용 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

- **동작 모니터링**: **사용**하면 동작 모니터링을 켜고 Defender에서 디바이스의 의심스러운 활동에 대해 알려진 특정 패턴을 확인합니다. 사용자는 동작 모니터링을 해제할 수 없습니다. 

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는 동작 모니터링을 켜고 사용자가 변경할 수 있도록 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowBehaviorMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring)

- **NIS(네트워크 검사 시스템)** : NIS를 통해 네트워크 기반 취약성 공격으로부터 디바이스를 보호할 수 있습니다. Microsoft Endpoint Protection Center에서 알려진 취약성의 서명을 사용하여 악성 트래픽을 검색하고 차단합니다.

  **사용을 설정 하면** 네트워크 보호 및 네트워크 차단이 사용 됩니다. 이 옵션은 사용자가 해제할 수 없습니다. 사용 하도록 설정 하면 사용자가 알려진 취약점에 대 한 연결을 차단 합니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는 NIS를 켜고 사용자가 변경할 수 있도록 허용 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/EnableNetworkProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)

- **모든 다운로드 검색**: **사용** 을 설정 하 고, Defender는 인터넷에서 다운로드 한 모든 파일을 검색 합니다. 사용자가이 설정을 해제할 수 없습니다. 

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는이 설정을 켜고 사용자가 변경할 수 있도록 허용 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowIOAVProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection)

- **Microsoft 웹 브라우저에 로드된 스크립트 검색**: **사용**하면 Defender가 Internet Explorer에 사용되는 스크립트를 검색하도록 허용합니다. 사용자가이 설정을 해제할 수 없습니다. 

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는이 설정을 켜고 사용자가 변경할 수 있도록 허용 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowScriptScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning)

- **Defender에 대한 최종 사용자 액세스**: **차단**하면 최종 사용자에게 Microsoft Defender 사용자 인터페이스를 표시하지 않도록 숨깁니다. Microsoft Defender 알림도 모두 표시되지 않습니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 차단 하 고 **구성 되지 않음**으로 다시 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는 Microsoft Defender UI에 대 한 사용자 액세스를 허용 하 고 사용자가 변경할 수 있도록 허용 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  이 설정이 변경되면 다음에 최종 사용자 PC를 다시 시작할 때 적용됩니다.

  [Defender/AllowUserUIAccess CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess)

- **보안 인텔리전스 업데이트 간격 (시간)** : Defender에서 새 보안 인텔리전스를 확인 하는 간격 (0-24)을 입력 합니다. 옵션은 다음과 같습니다.

  - **구성 되지 않음** (기본값): 8 시간 마다 업데이트를 확인 합니다.
  - **확인 안 함**: Defender에서 새 보안 인텔리전스 업데이트를 확인 하지 않습니다.
  - **1-24**: `1`은 매 시간마다 검사하고, `2`는 2시간마다 검사하고, `24`는 매일 검사하는 등등입니다.
  
  [Defender/서명 Updateinterval CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval)
  
- **파일 및 프로그램 활동 모니터링**: Defender가 디바이스의 파일 및 프로그램 활동을 모니터링하도록 허용합니다. 옵션은 다음과 같습니다.

  - **구성 되지 않음** (기본값): 모든 파일을 모니터링 합니다.
  - **모니터링 사용 안 함**
  - **모든 파일 모니터링**
  - **들어오는 파일만 모니터링**
  - **나가는 파일만 모니터링**

  [Defender/RealTimeScanDirection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-realtimescandirection)

- **다음 기간(일) 후 격리된 맬웨어 삭제**: 이전에 영향을 받은 디바이스를 수동으로 확인할 수 있도록 입력한 기간(일) 동안 확인된 맬웨어를 계속 추적합니다. 기간(일)을 `0`으로 설정하면, 맬웨어가 격리 폴더에 유지되며 자동으로 제거되지 않습니다. `90`으로 설정하면 격리 항목을 90일 동안 시스템에 저장한 다음, 제거합니다.

  [Defender/DaysToRetainCleanedMalware CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware)

- **검색하는 동안 CPU 사용 제한**: 검사에 사용할 수 있는 CPU의 양을 `0`에서 `100` 사이로 제한할 수 있습니다.
- **보관 파일 검색**: **활성화** 는 Zip 또는 Cab 파일과 같은 보관 파일을 검색 하도록 Defender를 설정 합니다. 사용자가이 설정을 해제할 수 없습니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는이 검색을 설정 하 고 사용자가 변경할 수 있도록 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowArchiveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning)

- **받는 메일 메시지 검사**: **사용**은 Defender에서 디바이스에 도착하는 이메일 메시지를 검사할 수 있도록 허용합니다. 사용 하도록 설정 하면 엔진은 사서함 및 메일 파일을 구문 분석 하 여 메일 본문 및 첨부 파일을 분석 합니다. .Pst (Outlook), .dbx, mbx, MIME (Outlook Express) 및 BinHex (Mac) 형식을 검사할 수 있습니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는이 검색을 해제 하 고 사용자가 변경할 수 있도록 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowEmailScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning)

- **전체 검색 중 이동식 드라이브 검색**: **사용을 설정** 하면 전체 검색을 수행 하는 동안 Defender 이동식 드라이브 검색을 사용 합니다. 사용자가이 설정을 해제할 수 없습니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로, OS는 Defender가 USB 스틱 같은 이동식 드라이브를 검색 하 고 사용자가이 설정을 변경할 수 있도록 허용 합니다.

  빠른 검색 중에는 이동식 드라이브를 계속 검색할 수 있습니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowFullScanRemovableDriveScanning CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning)

- **전체 검사 중 매핑된 네트워크 드라이브 검사**: **사용**하면 Defender에서 매핑된 네트워크 드라이브의 파일을 검사할 수 있습니다. 드라이브의 파일이 읽기 전용이면, Defender가 파일에서 발견한 맬웨어를 제거할 수 없습니다. 사용자가이 설정을 해제할 수 없습니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는이 기능을 설정 하 고 사용자가 변경할 수 있도록 허용 합니다.

  빠른 검색을 수행 하는 동안 매핑된 네트워크 드라이브를 계속 검색할 수 있습니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowFullScanOnMappedNetworkDrives CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives)

- **네트워크 폴더에서 열린 파일 검색**: **사용** 은 Defender에서 네트워크 폴더 또는 공유 네트워크 드라이브 (예: UNC 경로에서 액세스 한 파일)에서 연 파일을 검색 합니다. 사용자가이 설정을 해제할 수 없습니다. 드라이브의 파일이 읽기 전용이면, Defender가 파일에서 발견한 맬웨어를 제거할 수 없습니다.

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는 네트워크 폴더에서 열린 파일을 검색 하 여 사용자가 변경할 수 있도록 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowScanningNetworkFiles CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles)

- **클라우드 보호**: **사용**하면 Microsoft 활성 보호 서비스에서 사용자가 관리하는 디바이스의 맬웨어 활동에 대한 정보를 받을 수 있습니다. 사용자가 이 설정을 변경할 수 없습니다. 

  **구성 되지 않음** (기본값)으로 설정 되 면 Intune은이 설정을 건드리지 않습니다. 설정을 사용 하도록 설정 하 고 다시 **구성 되지 않음**으로 변경 하는 경우 Intune은 이전에 구성 된 상태에서 설정을 그대로 둡니다. 기본적으로 OS는 Microsoft 활성 보호 서비스에서 정보를 받을 수 있도록 하 고 사용자가이 설정을 변경할 수 있도록 허용 합니다.

  Intune은이 기능을 해제 하지 않습니다. 사용 하지 않도록 설정 하려면 사용자 지정 URI를 사용 합니다.

  [Defender/AllowCloudProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection)

- **샘플을 제출하기 전에 사용자에게 확인**: 추가 분석이 필요할 수도 있는 악의적 파일을 Microsoft에 자동으로 전송할지 여부를 제어합니다. 옵션은 다음과 같습니다.

  - **구성 되지 않음** (기본값): 안전 샘플을 자동으로 보냅니다.
  - **항상 확인**
  - **개인 데이터를 보내기 전에 확인**
  - **데이터를 보내지 않음**
  - **확인하지 않고 모든 데이터 보내기**: 데이터를 자동으로 보냅니다.

  [Defender/SubmitSamplesConsent CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent)

- **매일 빠른 검색을 수행하는 시간**: 매일 빠른 검색을 실행할 시간을 선택합니다. **구성되지 않음**을 사용하면 매일 검색을 실행하지 않습니다. 추가 사용자 지정을 하려는 경우 **수행할 시스템 검색 유형** 설정을 구성합니다.

  [Defender/ScheduleQuickScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime)

- **수행할 시스템 검색 유형**: 검색 수준과 검색을 실행하는 날짜 및 시간을 포함한 시스템 검색을 예약합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**: 디바이스에서 시스템 검색을 예약하지 않습니다. 최종 사용자는 디바이스에서 필요에 따라 또는 원하는 검색을 수동으로 실행할 수 있습니다.
  - **사용 안 함**: 디바이스에서 시스템 검색을 비활성화합니다. 디바이스를 검색하는 파트너 바이러스 백신 솔루션을 사용하는 경우 이 옵션을 선택합니다.
  - **빠른 검사**: 레지스트리 키 및 알려진 Windows 시작 폴더처럼 맬웨어가 있을 수 있는 일반적인 위치를 찾습니다.
    - **예약일**: 검사를 실행할 날짜를 선택합니다.
    - **예약 시간**: 검사를 실행할 시간을 선택합니다.
  - **전체 검사**: 맬웨어가 있을 수 있는 일반적인 위치를 찾고 디바이스의 모든 파일과 폴더를 검사합니다.
    - **예약일**: 검사를 실행할 날짜를 선택합니다.
    - **예약 시간**: 검사를 실행할 시간을 선택합니다.

  > [!TIP]
  > 이 설정은 **매일 빠른 검사를 수행하는 시간** 설정과 충돌할 수 있습니다. 권장 구성 저장:  
  >
  > - 매일 빠른 검색을 예약 하 고 매주 전체 검색을 예약 하려면 다음을 수행 합니다.
  >   1. **매일 빠른 검색 설정을 수행할 시간** 을 구성 합니다.
  >   2. 전체 검색을 수행 하기 위해 **수행할 시스템 검색 유형을** 구성 합니다.
  > 
  > - 매일 빠른 검색을 한 번만 수행 하려면 (전체 검색 안 함), **매일 빠른 검색을 수행** 하거나 **수행할 시스템 검색 유형을**설정: 시간 중 하나를 사용 합니다. 예를 들어 매주 화요일 오전 6시에 빠른 검색을 실행하려면 **수행할 시스템 검색 유형** 설정을 구성합니다.
  > 
  > - **매일 빠른 검색을 수행하는 시간** 설정과 **빠른 검색**으로 설정된 **수행할 시스템 검색 유형**을 동시에 구성하지 마세요. 이러한 설정이 충돌할 수 있으며 검색이 실행되지 않을 수 있습니다.

  [Defender/ScanParameter CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter)  
  [Defender/ScheduleScanDay CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday)  
  [Defender/ScheduleScanTime CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime)

- **사용자 동의 없이 설치된 애플리케이션 검색**: Windows에서 사용자 동의 없이 설치된 애플리케이션을 검색하는 경우의 보호 수준을 선택합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(기본값): Windows Defender의 사용자 동의 없이 설치된 애플리케이션 보호를 사용하지 않도록 설정합니다.
  - **차단**: Windows Defender에서 사용자 동의 없이 설치된 애플리케이션을 검색하고 검색된 항목을 차단합니다. 이러한 항목은 다른 위협과 함께 기록에 표시됩니다.
  - **감사**: Windows Defender에서 사용자 동의 없이 설치된 애플리케이션을 검색하지만 아무런 조치도 수행하지 않습니다. Windows Defender에서 조치를 취할 애플리케이션에 대한 정보를 검토할 수 있습니다. 예를 들어 Windows Defender에서 만든 이벤트를 이벤트 뷰어에서 검색합니다.

  사용자 동의 없이 설치된 앱에 대한 자세한 내용은 [사용자 동의 없이 설치된 애플리케이션 검색 및 차단](https://docs.microsoft.com/windows/threat-protection/windows-defender-antivirus/detect-block-potentially-unwanted-apps-windows-defender-antivirus)을 참조하세요.

  [Defender/PUAProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection)

- **검색 된 맬웨어 위협에 대 한 작업**: 맬웨어 스레드를 처리 하는 방법을 선택 합니다. **구성 되지 않음** (기본값) Microsoft Defender에서 가장 적합 한 옵션을 선택할 수 있습니다. **사용**으로 설정한 경우 감지된 각 위협 수준(낮음, 보통, 높음 및 심각)에 대해 Defender에서 수행할 작업을 선택합니다. 옵션은 다음과 같습니다.
  
  - **정리**
  - **격리**
  - **제거**
  - **허용**
  - **사용자 정의**
  - **차단**

  작업을 수행할 수 없는 경우, Windows Defender는 위협 요소를 재구성 하는 데 가장 적합 한 옵션을 선택 합니다. 

  [Defender/ThreatSeverityDefaultAction CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-threatseveritydefaultaction)

### <a name="windows-defender-antivirus-exclusions"></a>Windows Defender 바이러스 백신 제외

- **검색 및 실시간 보호에서 제외할 파일 및 폴더**: 제외 목록에 **C:\Path** 또는 **%ProgramFiles%\Path\filename.exe** 같은 파일과 폴더를 하나 이상 추가합니다. 이러한 파일과 폴더는 실시간 또는 예약된 검색에 포함되지 않습니다.
- **검색 및 실시간 보호에서 제외할 파일 확장명**: 제외 목록에 **jpg** 또는 **txt**와 같은 하나 이상의 파일 확장명을 추가합니다. 이러한 확장명의 파일은 실시간 또는 예약된 검색에 포함되지 않습니다.
- **검색 및 실시간 보호에서 제외할 프로세스**: 제외 목록에 **.exe**, **.com** 또는 **.scr** 형식의 프로세스를 하나 이상 추가합니다. 이러한 프로세스는 실시간 검색 또는 예약된 검색에 포함되지 않습니다.

## <a name="next-steps"></a>다음 단계

각 설정에 대한 추가 기술 세부 정보 및 지원되는 Windows 버전은 [Windows 10 정책 CSP 참조](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider)를 참조하세요.
