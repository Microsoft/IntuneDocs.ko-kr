---
title: Microsoft Intune에서 VPN 디바이스 프로필 만들기 - Azure | Microsoft Docs
description: iOS 디바이스의 경우 VPN(가상 사설망) 연결 형식을 보고, Azure Portal에서 VPN 디바이스 프로필을 만들고, Microsoft Intune에서 인증서 또는 사용자 이름과 암호를 사용하여 VPN 프로필을 보호 하는 옵션을 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cd605542a0711e27f87d68af51662fd318f3250e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184882"
---
# <a name="create-vpn-profiles-in-intune"></a>Intune에서 VPN 프로필 만들기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

VPN(가상 사설망)을 사용하면 사용자가 회사 네트워크에 안전하게 원격으로 액세스할 수 있습니다. 디바이스는 VPN 연결 프로필을 사용하여 VPN 서버와의 연결을 시작합니다. Microsoft Intune의 **VPN 프로필**을 사용하여 조직의 사용자 및 디바이스에 VPN 설정을 할당하면 네트워크에 쉽고 안전하게 연결할 수 있습니다.

예를 들어 기업 네트워크에서 파일 공유에 연결하는 데 필요한 설정을 사용하여 모든 iOS 디바이스를 프로비전하려고 할 수 있습니다. 기업 네트워크에 연결하는 설정을 포함하는 VPN 프로필을 만듭니다. 그런 다음, iOS 디바이스를 사용하는 모든 사용자에게 이 프로필을 할당합니다. 사용자에게는 지원되는 네트워크 목록에서 VPN 연결이 표시되어 최소한의 노력으로 연결할 수 있습니다.

Intune 사용자 지정 구성 정책을 사용하여 다음 플랫폼에 대한 VPN 프로필을 만들 수 있습니다.

* Android 4 이상
* Windows 8.1 이상을 실행하는 등록된 디바이스
* Windows Phone 8.1 이상
* Windows 10 데스크톱 이상을 실행하는 등록된 디바이스
* Windows 10 Mobile
* Windows Holographic for Business

## <a name="vpn-connection-types"></a>VPN 연결 형식

다음의 연결 유형을 사용하여 VPN 프로필을 만들 수 있습니다.

|연결 형식|Android<br>Android 회사 프로필|iOS|macOS|Windows Phone 8.1|Windows 8.1|Windows 10|
|-|-|-|-|-|-|-|
|자동|아니요|아니요|아니요|아니요|아니요|예|
|검사점 캡슐 VPN|예|예|예|예|예|예|
|Cisco AnyConnect|예|예|예|아니요|아니요|아니요|
|SonicWall Mobile Connect|예|예|예|예|예|예|
|F5 Edge Client|예|예|예|예|예|예|
|Palo Alto Networks GlobalProtect|아니요|예|아니요|아니요|아니요|예|
|Pulse Secure|예|예|예|예|예|예|
|Cisco(IPsec)|아니요|예|아니요|아니요|아니요|아니요|
|Citrix|예(Android에만 해당)|예|아니요|아니요|아니요|예|
|IKEv2|아니요|아니요|아니요|아니요|아니요|예|
|L2TP|아니요|아니요|아니요|아니요|아니요|예|
|PPTP|아니요|아니요|아니요|아니요|아니요|예|
|Zscaler|아니요|예|아니요|아니요|아니요|아니요|
|사용자 지정 VPN|아니요|예|예|아니요|아니요|아니요|

> [!IMPORTANT]
> 디바이스에 할당된 VPN 프로필을 사용하려면 프로필에 적용 가능한 VPN 앱을 설치해야 합니다. [Microsoft Intune의 앱 관리란?](app-management.md) 아티클의 정보를 참조하여 Intune을 사용해 앱을 할당할 수 있습니다.  

[사용자 지정 설정을 사용하여 프로필 만들기](custom-settings-configure.md)에서 URI 설정을 사용하여 사용자 지정 VPN 프로필을 만드는 방법을 알아봅니다.

## <a name="create-a-device-profile-containing-vpn-settings"></a>VPN 설정을 포함하는 디바이스 프로필 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
4. VPN 프로필의 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 VPN 설정을 적용할 장치 플랫폼을 선택합니다. 현재 VPN 디바이스 설정에 대해 다음 플랫폼 중 하나를 선택할 수 있습니다.
   - **OWA(Outlook Web Access)**
   - **Android 엔터프라이즈**
   - **iOS**
   - **macOS**
   - **Windows Phone 8.1**
   - **Windows 8.1 이상**
   - **Windows 10 이상**
6. **프로필** 유형 드롭다운 목록에서 선택 **VPN**을 선택합니다.
7. 선택한 플랫폼에 따라 구성할 수 있는 설정이 다릅니다. 각 플랫폼에 대한 자세한 설정을 보려면 다음 항목 중 하나로 이동하세요.
   - [Android 및 Android 회사 프로필 설정](vpn-settings-android.md)
   - [iOS 설정](vpn-settings-ios.md)
   - [macOS 설정](vpn-settings-macos.md)
   - [Windows Phone 8.1 설정](vpn-settings-windows-phone-8-1.md)
   - [Windows 8.1 설정](vpn-settings-windows-8-1.md)
   - [Windows 10 설정](vpn-settings-windows-10.md)(Windows Holographic for Business 포함)
8. 작업이 완료되면 프로필을 **만듭니다**.

프로필이 만들어지고 프로필 목록에 표시됩니다. 이 프로필을 그룹에 할당하려면 [디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.

## <a name="methods-of-securing-vpn-profiles"></a>VPN 프로필을 보호하는 방법

VPN 프로필에서는 다른 제조업체의 다양한 연결 형식과 프로토콜을 사용할 수 있습니다. 이러한 연결은 일반적으로 다음의 두 가지 방법 중 하나를 사용하여 보안이 유지됩니다.

### <a name="certificates"></a>인증서

VPN 프로필을 만들 때 이전에 Intune에서 만든 SCEP 또는 PKCS 인증서 프로필을 선택합니다. 이 프로필은 ID 인증서라고 합니다. 사용자 디바이스를 연결하기 위해 만든 신뢰할 수 있는 인증서 프로필(또는 *루트 인증서*)에 대해 인증하는 데 사용됩니다. 신뢰할 수 있는 인증서는 VPN 연결을 인증하는 컴퓨터(대개 VPN 서버)에 할당됩니다.

Intune에서 인증서 프로필을 만들고 사용하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 인증서를 구성하는 방법](certificates-configure.md)을 참조하세요.

### <a name="user-name-and-password"></a>사용자 이름 및 암호

사용자는 사용자 이름과 암호를 제공하여 VPN 서버에 인증합니다.
