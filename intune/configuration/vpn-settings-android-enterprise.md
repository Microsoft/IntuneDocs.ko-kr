---
title: Microsoft Intune에서 Android Enterprise에 대한 VPN 설정 사용 - Azure | Microsoft Docs
description: Microsoft Intune의 Android 엔터프라이즈 장치에서 VPN 연결을 만드는 모든 설정을 참조 하세요. VPN 서버의 연결 이름, IP 주소 또는 FQDN을 입력 하 고, 사용자가 인증 하는 방법을 선택 하 고, Citrix, SonicWall, Check Point 캡슐 및 Pulse Secure 연결 형식을 선택 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/06/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 647e8869caf24638f6809479274dbf7a7b967b9e
ms.sourcegitcommit: f5108039f0ade52e95ea3ac1da1aa16d02224af3
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/09/2019
ms.locfileid: "74946634"
---
# <a name="android-enterprise-device-settings-to-configure-vpn-in-intune"></a>Intune에서 VPN을 구성 하는 Android 엔터프라이즈 장치 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 문서에서는 Android Enterprise 디바이스에서 제어할 수 있는 다양한 VPN 연결 설정을 나열하고 설명합니다. MDM (모바일 장치 관리) 솔루션의 일부로, 이러한 설정을 사용 하 여 VPN 연결을 만들고, VPN에서 인증 하는 방법, VPN 서버 유형 등을 선택 합니다.

Intune 관리자는 VPN 설정을 만들어 Android Enterprise 디바이스에 할당할 수 있습니다. 

Intune의 VPN 프로필에 대 한 자세한 내용은 [vpn 프로필](vpn-settings-configure.md)을 참조 하세요.

> [!NOTE]
> Always on VPN을 구성 하려면 VPN 프로필을 만들고 Always on VPN 설정을 구성 하 여 [장치 제한](device-restrictions-android-for-work.md#connectivity) 프로필을 만들어야 합니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만들고](vpn-settings-configure.md#create-a-device-profile), **Android Enterprise**를 선택합니다.

## <a name="device-owner-only"></a>디바이스 소유자만

- **연결 이름**: 이 연결에 대한 이름을 입력합니다. 최종 사용자는 디바이스에서 사용 가능한 VPN 연결을 검색할 때 이 이름을 볼 수 있습니다. 예를 들어 다음과 같이 입력합니다. `Contoso VPN`
- **IP 주소 또는 FQDN**: 디바이스가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)을 입력합니다. 예를 들어 **192.168.1.1** 또는 **vpn.contoso.com**을 입력합니다.

  - **인증 방법**: 디바이스가 VPN 서버에 인증하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  
    - **인증서**: 연결을 인증할 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](../protect/certificates-configure.md)에는 인증서 프로필을 만드는 단계가 나열됩니다.
    - **사용자 이름 및 암호**: VPN 서버에 로그인할 때 최종 사용자에게 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.

- **연결 형식**: VPN 연결 형식을 선택합니다. 옵션은 다음과 같습니다.

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**

## <a name="work-profile-only"></a>작업 프로필만

- **연결 이름**: 이 연결에 대한 이름을 입력합니다. 최종 사용자는 디바이스에서 사용 가능한 VPN 연결을 검색할 때 이 이름을 볼 수 있습니다. 예를 들어 다음과 같이 입력합니다. `Contoso VPN`
- **IP 주소 또는 FQDN**: 디바이스가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)을 입력합니다. 예를 들어 **192.168.1.1** 또는 **vpn.contoso.com**을 입력합니다.

  - **인증 방법**: 디바이스가 VPN 서버에 인증하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  
    - **인증서**: 연결을 인증할 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](../protect/certificates-configure.md)에는 인증서 프로필을 만드는 단계가 나열됩니다.
    - **사용자 이름 및 암호**: VPN 서버에 로그인할 때 최종 사용자에게 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.

- **연결 형식**: VPN 연결 형식을 선택합니다. 옵션은 다음과 같습니다.

  - **Cisco AnyConnect**
  - **F5 Access**
  - **Pulse Secure**
  - **SonicWall Mobile Connect**
  - **검사점 캡슐 VPN**

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md), [macos](vpn-settings-macos.md), [Windows 10 이상](vpn-settings-windows-10.md), [Windows 8.1](vpn-settings-windows-8-1.md)및 [Windows Phone 8.1](vpn-settings-windows-phone-8-1.md) 장치에 대 한 VPN 프로필을 만들 수도 있습니다.
