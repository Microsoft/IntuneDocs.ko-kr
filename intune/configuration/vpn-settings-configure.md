---
title: Microsoft Intune에서 디바이스에 VPN 설정 추가 - Azure | Microsoft Docs
description: Android, Android 엔터프라이즈, iOS, macOS 및 Windows 디바이스의 경우 기본 제공 설정을 사용하여 Microsoft Intune에서 VPN(가상 사설망) 연결을 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59a1b5679b81a8de90e39d6ec13bbe87dac90947
ms.sourcegitcommit: a7c35efb31c4efd816bd4aba29240013965aee92
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "73984179"
---
# <a name="create-vpn-profiles-to-connect-to-vpn-servers-in-intune"></a>Intune에서 VPN 서버에 연결할 VPN 프로필 생성

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

VPN(가상 사설망)을 사용하면 사용자가 조직 네트워크에 안전하게 원격으로 액세스할 수 있습니다. 디바이스에서 VPN 연결 프로필을 사용하여 VPN 서버와의 연결을 시작합니다. Microsoft Intune의 **VPN 프로필**은 조직의 사용자 및 디바이스에 VPN 설정을 할당하여 조직 네트워크에 쉽고 안전하게 연결할 수 있습니다.

예를 들어 조직 네트워크에서 파일 공유에 연결하는 데 필요한 설정을 사용하여 모든 iOS 디바이스를 구성하려고 할 수 있습니다. 이러한 설정이 포함된 VPN 프로필을 만듭니다. 그런 다음, iOS 디바이스를 사용하는 모든 사용자에게 이 프로필을 할당합니다. 사용자에게는 지원되는 네트워크 목록에서 VPN 연결이 표시되어 최소한의 노력으로 연결할 수 있습니다.

> [!NOTE]
> [Intune 사용자 지정 구성 정책](custom-settings-configure.md)을 사용하여 다음 플랫폼에 대한 VPN 프로필을 만들 수 있습니다.
>
> * Android 4 이상
> * Windows 8.1 이상을 실행하는 등록된 디바이스
> * Windows Phone 8.1 이상
> * Windows 10 데스크톱 이상을 실행하는 등록된 디바이스
> * Windows 10 Mobile
> * Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 연결 형식

다음의 연결 유형을 사용하여 VPN 프로필을 만들 수 있습니다.

|연결 형식|플랫폼|
|-|-|
|자동|Windows 10|
|검사점 캡슐 VPN|- Android<br/>- Android 엔터프라이즈 회사 프로필<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Cisco AnyConnect|- Android<br/>- Android 엔터프라이즈 회사 프로필<br/>- Android 엔터프라이즈 디바이스 소유자(완전 관리형)<br/>- iOS<br/>- macOS|
|Cisco(IPsec)|iOS|
|Citrix SSO|- Android<br/>- Android 엔터프라이즈 회사 프로필: [앱 구성 정책](../apps/app-configuration-policies-use-android.md) 사용<br/>- Android 엔터프라이즈 디바이스 소유자(완전 관리형) [앱 구성 정책](../apps/app-configuration-policies-use-android.md) 사용<br/>- iOS<br/>- Windows 10|
|사용자 지정 VPN|- iOS<br/>- macOS|
|F5 Access|- Android<br/>- Android 엔터프라이즈 회사 프로필<br/>- Android 엔터프라이즈 디바이스 소유자(완전 관리형)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|IKEv2| - iOS<br/>- Windows 10|
|L2TP|Windows 10|
|Palo Alto Networks GlobalProtect|- Android 엔터프라이즈 회사 프로필: [앱 구성 정책](../apps/app-configuration-policies-use-android.md) 사용<br/>- iOS<br/>- Windows 10|
|PPTP|Windows 10|
|Pulse Secure|- Android<br/>- Android 엔터프라이즈 회사 프로필<br/>- Android 엔터프라이즈 디바이스 소유자(완전 관리형)<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|SonicWall Mobile Connect|- Android<br/>- Android 엔터프라이즈 회사 프로필<br/>- iOS<br/>- macOS<br/>- Windows 10<br/>- Windows 8.1<br/>- Windows Phone 8.1|
|Zscaler|- Android 엔터프라이즈 회사 프로필: [앱 구성 정책](../apps/app-configuration-policies-use-android.md) 사용<br/>- iOS|

> [!IMPORTANT]
> 디바이스에 할당된 VPN 프로필을 사용하려면 프로필에 적용 가능한 VPN 앱을 설치해야 합니다. [Microsoft Intune의 앱 관리란?](../apps/app-management.md) 아티클의 정보를 참조하여 Intune을 사용해 앱을 할당할 수 있습니다.  

[사용자 지정 설정을 사용하여 프로필 만들기](custom-settings-configure.md)에서 URI 설정을 사용하여 사용자 지정 VPN 프로필을 만드는 방법을 알아봅니다.

## <a name="create-a-device-profile"></a>디바이스 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 프로필 이름을 지정합니다. 예를 들어 **전체 회사에 대한 VPN 프로필**은 좋은 프로필 이름입니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 디바이스 플랫폼을 선택합니다. 옵션은 다음과 같습니다.

      - **OWA(Outlook Web Access)**
      - **Android 엔터프라이즈** > **디바이스 소유자만**
      - **Android 엔터프라이즈** > **작업 프로필만**
      - **iOS/iPadOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 이상**
      - **Windows 10 이상**

    - **프로필 유형**: **VPN**을 선택합니다.

4. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 각 플랫폼에 대한 자세한 설정을 보려면 다음 문서로 이동하세요.

    - [Android 설정](vpn-settings-android.md)
    - [Android Enterprise 설정](vpn-settings-android-enterprise.md)
    - [iOS/iPadOS 설정](vpn-settings-ios.md)
    - [macOS 설정](vpn-settings-macos.md)
    - [Windows Phone 8.1 설정](vpn-settings-windows-phone-8-1.md)
    - [Windows 8.1 설정](vpn-settings-windows-8-1.md)
    - [Windows 10 설정](vpn-settings-windows-10.md)(Windows Holographic for Business 포함)

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다. 이 프로필을 그룹에 할당하려면 [디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="secure-your-vpn-profiles"></a>VPN 프로필 보호

VPN 프로필에서는 다른 제조업체의 다양한 연결 형식과 프로토콜을 사용할 수 있습니다. 이러한 연결은 일반적으로 다음 방법을 사용하여 보안이 유지됩니다.

### <a name="certificates"></a>인증서

VPN 프로필을 만들 때 이전에 Intune에서 만든 SCEP 또는 PKCS 인증서 프로필을 선택합니다. 이 프로필은 ID 인증서라고 합니다. 사용자 디바이스를 연결하기 위해 만든 신뢰할 수 있는 인증서 프로필(또는 *루트 인증서*)에 대해 인증하는 데 사용됩니다. 신뢰할 수 있는 인증서는 VPN 연결을 인증하는 컴퓨터(대개 VPN 서버)에 할당됩니다.

Intune에서 인증서 프로필을 만들고 사용하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 인증서를 구성하는 방법](../protect/certificates-configure.md)을 참조하세요.

### <a name="user-name-and-password"></a>사용자 이름 및 암호

사용자는 사용자 이름과 암호를 제공하여 VPN 서버에 인증합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성되면 아직 아무 작업도 수행하지 않습니다. 다음으로, 일부 디바이스에 [프로필을 할당](device-profile-assign.md)합니다.

[Android](android-pulse-secure-per-app-vpn.md) 및 [iOS](vpn-setting-configure-per-app.md)디바이스에서 앱별 VPN을 만들고 사용할 수도 있습니다.
