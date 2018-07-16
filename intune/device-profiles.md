---
title: Microsoft Intune - Azure의 장치 프로필 | Microsoft Docs
description: 기능, 제한 사항, 이메일, wifi, VPN, 교육, 인증서, Windows 10 업그레이드, BitLocker 및 Windows defender, Windows Information Protection 및 Azure Portal에서 사용자 지정 장치 구성을 포함한 다양한 Microsoft Intune 장치 프로필 개요입니다. 이러한 프로필을 사용하여 회사의 장치와 데이터를 관리하고 보호 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/25/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f241c5bece72b44a6bd3c9047b5997bcd8879ec5
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905192"
---
# <a name="what-are-microsoft-intune-device-profiles"></a>Microsoft Intune 장치 프로필이란?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Microsoft Intune은 조직 내의 다른 장치에서 사용하거나 사용하지 않게 할 수 있는 설정 및 기능을 포함합니다. 이러한 설정 및 기능은 프로필을 사용하여 관리됩니다. 프리필의 예를 들면 다음과 같습니다. 

- 회사 WiFi에 다양한 장치가 액세스하게 하는 WiFi 프로필
- 회사 네트워크 내 VPN 서버에 다양한 장치가 액세스하게 하는 VPN 프로필

이 문서에서는 장치에 대해 만들 수 있는 다양한 프로필에 대해 간략히 설명합니다. 이러한 프로필을 사용하여 장치에서 일부 기능을 방지하거나 허용합니다.

## <a name="before-you-begin"></a>시작하기 전에
사용할 수 있는 기능을 확인하려면 [Azure Portal](https://portal.azure.com)을 연 다음, Intune 리소스를 엽니다. 

**장치 구성**에는 다음 옵션이 포함됩니다.

- **개요**: 사용자 프로필의 상태를 나열하고 사용자 및 장치에 할당한 프로필에 관한 추가 세부 내용을 제공합니다
- **관리**: 장치 프로필을 만들어 프로필 내에서 실행되는 사용자 지정 [PowerShell 스크립트](intune-management-extension.md)를 업로드합니다
- **모니터**: 성공 또는 실패에 대한 프로필 상태를 확인하고 프로필 로그도 봅니다
- **설치**: 인증 기관(SCEP 또는 PFX)를 추가하거나 TEM(Telecom Expense Management)을 프로필에 사용하도록 설정합니다

## <a name="create-the-profile"></a>프로필 만들기

[장치 프로필 만들기](device-profile-create.md)는 프로필을 만드는 단계별 안내를 제공합니다. 

## <a name="device-features---ios-and-macos"></a>장치 기능 - iOS 및 macOS

[장치 기능](device-features-configure.md)을 통해 IOS 및 macOS 장치에서 AirPrint, 알림 및 공유 장치 구성과 같은 기능을 제어합니다.

이 기능은 다음을 지원합니다.
- iOS 
- macOS

## <a name="device-restrictions"></a>장치 제한 사항
[장치 제한](device-restrictions-configure.md)은 장치에서 보안, 하드웨어, 데이터 공유 및 많은 설정을 제어합니다. 예를 들어 iOS 장치의 사용자가 장치 카메라를 사용하지 못하도록 하는 장치 제한 프로필을 만듭니다. 

이 기능은 다음을 지원합니다.

- Android
- iOS
- macOS
- Windows 10
- Windows 10 팀

## <a name="endpoint-protection"></a>Endpoint Protection
[Windows 10에 대한 Endpoint Protection 설정](endpoint-protection-windows-10.md)은 Windows 10 장치에 대한 BitLocker 및 Windows Defender 설정을 구성합니다.

Microsoft Intune에서 WDATP(Windows Defender Advanced Threat Protection)을 온보드하려면 [MDM(모바일 장치 관리) 도구를 사용하여 끝점 구성](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-endpoints-mdm-windows-defender-advanced-threat-protection)을 참조하세요.

이 기능은 다음을 지원합니다.
- Windows 10 이상

## <a name="kiosk"></a>키오스크

[키오스크 설정](kiosk-settings.md) 프로필은 장치에서 하나 또는 여러 앱을 실행하도록 구성합니다. 시작 메뉴와 웹 브라우저를 포함하여 키오스크의 다른 기능을 사용자 지정할 수도 있습니다.

이 기능은 다음을 지원합니다.
- Windows 10 이상

## <a name="email"></a>메일
[이메일 설정](email-settings-configure.md) 프로필은 장치에서 Exchange ActiveSync 이메일 설정을 만들고 할당하고 모니터링합니다. 메일 프로필을 사용하면 일관성이 보장되고, 지원 요청이 감소하며, 최종 사용자가 필요한 설정 없이 자신의 개인 장치에서 회사 메일에 액세스하도록 할 수 있습니다. 

이 기능은 다음을 지원합니다. 

- Android
- iOS
- Windows Phone 8.1
- Windows 10

## <a name="vpn"></a>VPN
[VPN 설정](vpn-settings-configure.md)은 VPN 프로필을 조직 내 사용자와 장치에 할당함으로써 네트워크에 쉽고 안전하게 연결할 수 있습니다. 

VPN(가상 사설망)을 사용하면 사용자가 회사 네트워크에 안전하게 원격으로 액세스할 수 있습니다. 장치에서 VPN 연결 프로필을 사용하여 VPN 서버와의 연결을 시작합니다. 

이 기능은 다음을 지원합니다. 

- Android
- iOS
- macOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="wi-fi"></a>Wi-Fi
[Wi-Fi 설정](wi-fi-settings-configure.md)은 사용자와 장치에 무선 네트워크 설정을 할당합니다. WiFi 프로필을 할당하면 사용자가 Wi-Fi를 직접 구성하지 않고도 회사 WiFi에 액세스할 수 있습니다. 

이 기능은 다음을 지원합니다. 

- Android
- iOS
- macOS
- Windows 8.1(가져오기만 해당)

## <a name="education"></a>교육
[교육 설정 - Windows 10](education-settings-configure.md)은 [Windows Take a Test(Windows 시험 응시) 앱](https://education.microsoft.com/gettrained/win10takeatest)에 대한 옵션을 구성합니다. 이 설정을 구성할 경우 테스트가 완료될 때까지 장치에서 다른 앱을 실행할 수 없습니다.

[교육 설정 - iOS](education-settings-configure-ios-shared.md)는 iOS 교실 앱을 사용하여 학습을 지도하고 교실에서 학생 장치를 제어합니다. 여러 학생이 하나의 장치를 공유할 수 있도록 iPad 장치를 구성할 수 있습니다.

## <a name="edition-upgrade"></a>버전 업그레이드
[Windows 10 버전 업그레이드](edition-upgrade-configure-windows-10.md)는 일부 버전의 Windows 10을 실행하는 장치를 최신 버전으로 자동으로 업그레이드합니다.

이 기능은 다음을 지원합니다. 
- Windows 10 이상

## <a name="update-policies"></a>업데이트 정책
[iOS 업데이트 정책](software-updates-ios.md)은 iOS 장치에 소프트웨어 업데이트를 설치하기 위한 iOS 정책을 만들고 할당하는 방법을 보여 줍니다. 설치 상태를 검토할 수도 있습니다.

이 기능은 다음을 지원합니다.
- iOS

## <a name="certificates"></a>인증서
[인증서](certificates-configure.md)는 장치에 할당하고 Wi-Fi, VPN 및 이메일 프로필을 인증하는 데 사용할 수 있는 신뢰할 만한 SCEP 및 PKCS 인증서를 구성합니다.

이 기능은 다음을 지원합니다. 

- Android
- iOS
- Windows Phone 8.1
- Windows 8.1
- Windows 10

## <a name="windows-information-protection-profile"></a>Windows Information Protection 프로필
[Windows Information Protection](windows-information-protection-configure.md)은 직원 환경을 방해하지 않으면서 데이터 유출로부터 보호하는 데 도움이 됩니다. 또한 직원이 작업에 사용하는 회사 소유 장치 및 개인 장치에서 엔터프라이즈 앱 및 데이터가 실수로 데이터를 누출되지 않게 하는 데도 유용합니다. 작업 환경이나 기타 앱을 변경하지 않고도 가능합니다.

이 기능은 다음을 지원합니다.
- Windows 10 이상

## <a name="custom-profile"></a>사용자 지정 프로필
[사용자 지정 설정](custom-settings-configure.md)은 Intune에 기본 제공되지 않는 장치 설정을 할당하는 기능을 포함합니다. 예를 들어 Android 장치에서 OMA-URI 값을 입력할 수 있습니다. IOS 장치의 경우 Apple Configurator에서 만든 구성 파일을 가져올 수 있습니다. 

이 기능은 다음을 지원합니다.

- Android
- iOS
- macOS
- Windows Phone 8.1

## <a name="manage-and-troubleshoot"></a>관리 및 문제 해결

[프로필을 관리](device-profile-monitor.md)하여 장치 및 할당 된 프로필의 상태를 확인합니다. 또한 충돌을 일으키는 설정과 이러한 설정이 포함된 프로필을 확인하여 충돌을 해결할 수 있습니다. [일반적인 문제 및 해결 방법](device-profile-troubleshoot.md)은 프로필 삭제 시 발생하는 상황, 장치로 보내는 알림의 원인 등 프로필 관련 작업에 도움이 되는 Q&A 목록을 제공합니다.