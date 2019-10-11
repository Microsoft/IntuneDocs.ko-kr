---
title: Microsoft Intune의 디바이스 기능 및 설정 | Microsoft Docs
description: 다양한 Microsoft Intune 디바이스 프로필의 개요입니다. 기능, 제한 사항, 메일, wifi, VPN, 교육, 인증서, Windows 10 업그레이드, BitLocker 및 Windows defender, Windows Information Protection, 관리 템플릿 및 Azure Portal에서 사용자 지정 디바이스 구성 설정에 대한 정보를 확인합니다. 이러한 프로필을 사용하여 회사의 디바이스와 데이터를 관리하고 보호합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3afdb365d0ed88a58028287cc7010bb334e9001e
ms.sourcegitcommit: fca2670142c083d7562c0a36547a6a451863e315
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72036439"
---
# <a name="apply-features-and-settings-on-your-devices-using-device-profiles-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 프로필을 사용하여 디바이스에서 기능 및 설정 적용

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune은 조직 내의 다른 디바이스에서 사용하거나 사용하지 않게 할 수 있는 설정 및 기능을 포함합니다. 이러한 설정 및 기능을 "구성 프로필"에 추가합니다. iOS, Android 및 Windows를 포함하여 다양한 디바이스 및 플랫폼에 대한 프로필을 만들 수 있습니다. 그런 다음, Intune을 사용하여 디바이스에 프로필을 적용 또는 “할당”합니다.

MDM(모바일 디바이스 관리) 솔루션의 일부로 이 구성 프로필을 사용하여 다른 작업을 완료합니다. 프리필의 예를 들면 다음과 같습니다.

- Windows 10 디바이스에서 프로필 템플릿을 사용하여 Internet Explorer의 ActiveX 컨트롤을 차단합니다.
- iOS 및 macOS 디바이스에서 사용자가 조직의 AirPrint 프린터를 사용하게 할 수 있습니다.
- 디바이스에서 bluetooth에 대한 액세스를 허용하거나 방지합니다.
- 회사 네트워크에 다양한 디바이스가 액세스하게 하는 WiFi 또는 VPN 프로필을 만듭니다.
- 소프트웨어 업데이트가 설치된 경우를 포함하여 해당 업데이트를 관리합니다.
- 하나의 앱 또는 여러 앱을 실행할 수 있는 전용 키오스크 디바이스인 Android 디바이스를 실행합니다.

이 문서에서는 만들 수 있는 다양한 프로필 유형에 대해 간략히 설명합니다. 이러한 프로필을 사용하여 디바이스에서 일부 기능을 방지하거나 허용합니다.

## <a name="administrative-templates"></a>관리 템플릿

[관리 템플릿](administrative-templates-windows.md)에는 Internet Explorer, OneDrive, 원격 데스크톱, Word, Excel 및 기타 Office 프로그램에 대해 구성할 수 있는 수백 가지 설정이 포함됩니다.

이 템플릿을 통해 관리자는 그룹 정책과 유사한 설정을 간단하게 볼 수 있지만 해당 템플릿은 100% 클라우드 기반입니다.

이 기능은 다음을 지원합니다.

- Windows 10 이상

## <a name="certificates"></a>인증서

[인증서](../protect/certificates-configure.md)는 디바이스에 할당된 신뢰할 수 있는 SCEP 및 PKCS 인증서를 구성합니다. 이 인증서는 WiFi, VPN 및 메일 프로필을 인증합니다.

이 기능은 다음을 지원합니다. 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 이상

## <a name="custom-profile"></a>사용자 지정 프로필

[사용자 지정 설정](../custom-settings-configure.md)을 사용하면 관리자가 Intune에 기본 제공되지 않는 디바이스 설정을 할당할 수 있습니다. Android 디바이스에서는 OMA-URI 값을 입력할 수 있습니다. IOS 디바이스의 경우 Apple Configurator에서 만든 구성 파일을 가져올 수 있습니다.

이 기능은 다음을 지원합니다.

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1

## <a name="delivery-optimization"></a>배달 최적화

[배달 최적화](../delivery-optimization-windows.md)는 소프트웨어 업데이트를 배달하기 위한 향상된 환경을 제공합니다. 이러한 설정은 **소프트웨어 업데이트** > **Windows 10 업데이트 링** 설정을 대체합니다.

이러한 설정을 사용하여 조직의 디바이스에 소프트웨어 업데이트를 다운로드하는 방법을 제어할 수 있습니다. 예를 들어 사용자가 자신만의 업데이트를 가져오거나 디바이스 프로필에서 배달 최적화 클라우드 서비스를 사용하여 업데이트를 가져오도록 설정할 수 있습니다.

이 기능은 다음을 지원합니다.

- Windows 10 이상

## <a name="device-features"></a>디바이스 기능

[디바이스 기능](../device-features-configure.md)을 통해 iOS 및 macOS 디바이스에서 AirPrint, 알림 및 잠금 화면 메시지와 같은 기능을 제어합니다.

이 기능은 다음을 지원합니다.

- iOS/iPadOS
- macOS

## <a name="device-restrictions"></a>디바이스 제한 사항

[디바이스 제한](device-restrictions-configure.md)은 디바이스에서 보안, 하드웨어, 데이터 공유 및 많은 설정을 제어합니다. 예를 들어 iOS 디바이스의 사용자가 디바이스 카메라를 사용하지 못하도록 하는 디바이스 제한 프로필을 만듭니다. 

이 기능은 다음을 지원합니다.

- Android
- Android 엔터프라이즈
- iOS/iPadOS
- macOS
- Windows 10 이상
- Windows 10 팀

## <a name="edition-upgrade"></a>버전 업그레이드

[Windows 10 버전 업그레이드](edition-upgrade-configure-windows-10.md)는 일부 버전의 Windows 10을 실행하는 디바이스를 최신 버전으로 자동으로 업그레이드합니다.

이 기능은 다음을 지원합니다.

- Windows 10 이상

## <a name="education"></a>교육

[교육 설정 - Windows 10](education-settings-configure.md)은 [Windows Take a Test(Windows 시험 응시) 앱](https://education.microsoft.com/gettrained/win10takeatest)에 대한 옵션을 구성합니다. 이 설정을 구성할 경우 테스트가 완료될 때까지 디바이스에서 다른 앱을 실행할 수 없습니다.

[교육 설정 - iOS](../fundamentals/education-settings-configure-ios-shared.md)는 iOS 교실 앱을 사용하여 학습을 지도하고 교실에서 학생 디바이스를 제어합니다. 여러 학생이 하나의 디바이스를 공유할 수 있도록 iPad 디바이스를 구성할 수 있습니다.

## <a name="email"></a>메일

[메일 설정](email-settings-configure.md)은 디바이스에서 Exchange ActiveSync 메일 설정을 만들고 할당하고 모니터링합니다. 메일 프로필을 사용하면 일관성이 제공되고, 지원 요청이 감소하며, 최종 사용자가 필요한 설정 없이 자신의 개인 디바이스에서 회사 메일에 액세스하도록 할 수 있습니다. 

이 기능은 다음을 지원합니다. 

- Android
- Android Enterprise
- iOS/iPadOS
- Windows Phone 8.1
- Windows 10 이상

## <a name="endpoint-protection"></a>Endpoint Protection

[Windows 10에 대한 Endpoint Protection 설정](../protect/endpoint-protection-windows-10.md)은 Windows 10 디바이스에 대한 BitLocker 및 Windows Defender 설정을 구성합니다.

Microsoft Intune에서 WDATP(Microsoft Defender Advanced Threat Protection)를 온보드하려면 [MDM(모바일 디바이스 관리) 도구를 사용하여 엔드포인트 구성](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints-mdm)을 참조하세요.

이 기능은 다음을 지원합니다.

- Windows 10 이상

## <a name="esim-cellular---public-preview"></a>eSIM 셀룰러 - 공개 미리 보기

[eSIM 셀룰러 프로필](esim-device-configuration.md)을 사용하여 관리자가 인터넷 및 데이터 액세스용 관리 디바이스에서 셀룰러 데이터 계획을 구성할 수 있습니다. 이용 중인 통신사로부터 활성화 코드를 받아 Intune을 사용하여 가져온 후에 eSIM 지원 디바이스에 할당합니다.

이 기능은 다음을 지원합니다.

- Windows 10 Fall Creators Update 이상

## <a name="extensions"></a>확장

[커널 확장](kernel-extensions-overview-macos.md)을 사용하면 관리자가 macOS 디바이스의 커널 수준에서 기능 또는 프로그램을 추가할 수 있습니다. 특정 개발자나 파트너의 모든 확장을 신뢰하거나 특정 커널 확장을 허용하도록 이러한 설정을 구성합니다.

이 기능은 다음을 지원합니다.

- macOS

## <a name="identity-protection"></a>ID 보호

[ID 보호](../protect/identity-protection-configure.md)는 Windows 10 및 Windows 10 모바일 디바이스에서 비즈니스용 Windows Hello 환경을 제어합니다. 사용자 및 디바이스가 비즈니스용 Windows Hello를 사용할 수 있도록 하고, 디바이스 PIN 및 제스처에 대한 요구 사항을 지정하도록 이러한 설정을 구성합니다.  

이 기능은 다음을 지원합니다.  

- Windows 10 이상
- Windows Holographic for Business  

## <a name="kiosk"></a>키오스크

[키오스크 설정](kiosk-settings.md) 프로필은 디바이스에서 하나 이상의 앱을 실행하도록 구성합니다. 시작 메뉴와 웹 브라우저를 포함하여 키오스크의 다른 기능을 사용자 지정할 수도 있습니다.

이 기능은 다음을 지원합니다.

- Windows 10 이상

키오스크 설정은 [Android](device-restrictions-android.md#kiosk), [Android 엔터프라이즈](device-restrictions-android-for-work.md#dedicated-device-settings) 및 [iOS](device-restrictions-ios.md#kiosk)의 디바이스 제한 사항으로도 사용할 수 있습니다.

## <a name="oemconfig"></a>OEMConfig

[OEMConfig](android-oem-configuration-overview.md)는 OEM(원래 장비 제조업체) 및 EMM(Enterprise Mobility Management)이 Android Enterprise 디바이스에서 표준화된 방식으로 OEM 전용 기능을 빌드하고 지원할 수 있게 허용하는 표준입니다. OEM은 OEMConfig를 사용하여, OEM 전용 관리 기능을 정의하는 스키마를 만들어 Google Play에 업로드된 앱에 포함시킵니다. Intune은 앱에서 스키마를 읽고 Intune 관리자가 스키마의 설정을 구성하도록 허용합니다.

이 기능은 다음을 지원합니다.

- Android Enterprise(OEMConfig)

## <a name="powershell-scripts"></a>PowerShell 스크립트

[Windows 10 디바이스의 PowerShell 스크립트](../apps/intune-management-extension.md)에서는 Intune 관리 확장을 사용하여 Intune에서 PowerShell 스크립트를 업로드한 후 디바이스에서 이 스크립트를 실행합니다. 또한 확장을 사용하는 데 필요한 것, 이것을 Intune에 추가하는 방법, 기타 중요 정보를 확인하세요.


이 기능은 다음을 지원합니다.

- Windows 10 이상
- Windows Holographic for Business

## <a name="shared-multi-user-device"></a>다중 사용자 디바이스 공유

[Windows 10](shared-user-device-settings-windows.md) 및 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md)에는 공유 디바이스 또는 공유 PC라고도 하는 여러 사용자가 포함된 디바이스를 관리하는 설정이 포함됩니다. 사용자가 디바이스에 로그인하는 경우 사용자가 절전 모드 옵션을 변경하거나 디바이스에 파일을 저장할 수 있는지를 선택합니다. 또 다른 예로, 공간을 절약하기 위해 Windows HoloLens 디바이스에서 비활성 자격 증명을 삭제하는 프로필을 만들 수 있습니다.

이러한 다중 사용자 공유 디바이스 설정을 사용하면 관리자가 일부 디바이스 기능을 제어하고 Intune을 통해 이러한 공유 디바이스를 관리할 수 있습니다.

이 기능은 다음을 지원합니다.

- Windows 10 이상
- Windows Holographic for Business

## <a name="update-policies"></a>업데이트 정책

[iOS 업데이트 정책](../software-updates-ios.md)은 iOS 디바이스에 소프트웨어 업데이트를 설치하기 위한 iOS 정책을 만들고 할당하는 방법을 보여 줍니다. 설치 상태를 검토할 수도 있습니다.

Windows 디바이스의 업데이트 정책은 [배달 최적화](../delivery-optimization-windows.md)를 참조하세요. 

이 기능은 다음을 지원합니다.

- iOS/iPadOS

## <a name="vpn"></a>VPN

[VPN 설정](vpn-settings-configure.md)은 VPN 프로필을 조직 내 사용자와 디바이스에 할당함으로써 네트워크에 쉽고 안전하게 연결할 수 있습니다. 

VPN(가상 프라이빗 네트워크)을 사용하면 사용자가 회사 네트워크에 안전하게 원격으로 액세스할 수 있습니다. 디바이스에서 VPN 연결 프로필을 사용하여 VPN 서버와의 연결을 시작합니다. 

이 기능은 다음을 지원합니다. 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10 이상

## <a name="wi-fi"></a>Wi-Fi

[Wi-Fi 설정](wi-fi-settings-configure.md)은 사용자와 디바이스에 무선 네트워크 설정을 할당합니다. WiFi 프로필을 할당하면 사용자가 Wi-Fi를 직접 구성하지 않고도 회사 WiFi에 액세스할 수 있습니다. 

이 기능은 다음을 지원합니다. 

- Android
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1(가져오기만 해당)
- Windows 10 이상

## <a name="windows-information-protection-profile"></a>Windows Information Protection 프로필

[Windows Information Protection](../protect/windows-information-protection-configure.md)은 직원 환경을 방해하지 않으면서 데이터 유출로부터 보호하는 데 도움이 됩니다. 또한 직원이 작업에 사용하는 회사 소유 디바이스 및 개인 디바이스에서 엔터프라이즈 앱 및 데이터가 실수로 데이터를 누출되지 않게 하는 데도 유용합니다. Windows Information Protection을 사용하면 운영 환경이나 기타 앱을 변경할 필요가 없습니다.

이 기능은 다음을 지원합니다.

- Windows 10 이상

## <a name="zebra-mobility-extensions-mx"></a>Zebra MX(Mobility Extensions)

[Zebra MX(Mobility Extensions)](android-zebra-mx-overview.md)를 통해 관리자는 Intune에서 Zebra 디바이스를 사용 및 관리할 수 있습니다. 사용자 설정을 사용하여 StageNow 프로필을 만든 후 Intune을 사용하여 Zebra 디바이스에 이 프로필을 할당 및 배포합니다. [StageNow 로그 및 일반적인 문제](android-zebra-mx-logs-troubleshoot.md)는 프로필 문제를 해결하고 StageNow 사용 시 발생할 수 있는 몇 가지 문제를 확인하는 좋은 리소스입니다.

이 기능은 다음을 지원합니다.

- Android(이동성 확장)

## <a name="manage-and-troubleshoot"></a>관리 및 문제 해결

[프로필을 관리](../device-profile-monitor.md)하여 디바이스 및 할당 된 프로필의 상태를 확인합니다. 또한 충돌을 일으키는 설정과 이 설정이 포함된 프로필을 확인하여 충돌을 해결할 수 있습니다. [일반적인 문제 및 해결 방법](device-profile-troubleshoot.md)은 관리자가 프로필 작업을 수행하는 데 도움이 됩니다. 이 문서는 프로필 삭제 시 발생하는 상황, 디바이스로 보내는 알림의 원인 등을 설명합니다.

## <a name="next-steps"></a>다음 단계

플랫폼을 선택하고 시작합니다.
