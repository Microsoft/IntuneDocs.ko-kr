---
title: Android를 실행하는 장치에 대한 Microsoft Intune VPN 설정
titlesuffix: ''
description: Android를 실행하는 장치에서 VPN 연결을 구성하는 데 사용할 수 있는 Intune 설정을 알아봅니다
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f52c43f8918589c1b66034ad68908f4d5ddba6d
ms.sourcegitcommit: 98b444468df3fb2a6e8977ce5eb9d238610d4398
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/07/2018
ms.locfileid: "37905124"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-android"></a>Android를 실행하는 장치용 Microsoft Intune에서 VPN 설정 구성 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 Android를 실행하는 장치에서 VPN 연결을 구성하는 데 사용할 수 있는 Intune 설정을 설명합니다.


다음 플랫폼에 대해 VPN 설정을 구성할 수 있습니다.

- [OWA(Outlook Web Access)](#android-vpn-settings)
- [Android 회사 프로필 장치](#android-for-work-vpn-settings)

선택한 설정에 따라 다음 모든 값을 구성할 수 없습니다.

## <a name="android-vpn-settings"></a>Android VPN 설정
**연결 이름** - 이 연결에 대한 이름을 입력합니다. 최종 사용자가 장치에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **IP 주소 또는 FQDN** - 장치가 연결되는 VPN 서버의 IP 주소 또는 정규화된 도메인 이름을 입력합니다. 예: **192.168.1.1**, **vpn.contoso.com**.
- **인증 방법** - 장치에서 VPN 서버에 인증하는 방법을 선택합니다.
    - **인증서** - 이전에 연결을 인증하기 위해 만든 SCEP 또는 PKCS 인증서 프로필을 선택합니다. 인증서 프로필에 대한 자세한 내용은 [인증서를 구성하는 방법](certificates-configure.md)을 참조하세요.
    - **사용자 이름 및 암호** - 최종 사용자는 VPN 서버에 로그인하기 위해 사용자 이름 및 암호를 제공해야 합니다.
- **연결 형식** - 다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.
    - **검사점 캡슐 VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**
    - **Citrix**

- **지문**(검사점 캡슐 VPN에만 해당) - 신뢰할 수 있는 VPN 서버를 확인하는 데 사용할 문자열(예: 'Contoso 지문 코드')을 지정합니다. 연결 시 동일한 지문을 제시하는 서버가 신뢰할 수 있는지 알 수 있도록 클라이언트에 지문을 보낼 수 있습니다. 장치에 지문이 아직 없으면 사용자에게 지문을 보여주면서 연결하려는 VPN 서버를 신뢰할 것인지 묻는 메시지가 표시됩니다. 사용자는 지문을 수동으로 확인한 후 연결 신뢰를 선택합니다.
- **Citrix VPN 특성에 대한 키 및 값 쌍을 입력합니다**(Citrix에만 해당) - Citrix에서 제공한 키 및 값 쌍을 입력하여 VPN 연결의 속성을 구성합니다.

## <a name="android-work-profile-device-vpn-settings"></a>Android 회사 프로필 장치 VPN 설정

**연결 이름** - 이 연결에 대한 이름을 입력합니다. 최종 사용자가 장치에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **IP 주소 또는 FQDN** - 장치가 연결되는 VPN 서버의 IP 주소 또는 정규화된 도메인 이름을 입력합니다. 예: **192.168.1.1**, **vpn.contoso.com**.
- **인증 방법** - 장치에서 VPN 서버에 인증하는 방법을 선택합니다.
    - **인증서** - 이전에 연결을 인증하기 위해 만든 SCEP 또는 PKCS 인증서 프로필을 선택합니다. 인증서 프로필에 대한 자세한 내용은 [인증서를 구성하는 방법](certificates-configure.md)을 참조하세요.
    - **사용자 이름 및 암호** - 최종 사용자는 VPN 서버에 로그인하기 위해 사용자 이름 및 암호를 제공해야 합니다.
- **연결 형식** - 다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.
    - **검사점 캡슐 VPN**
    - **Cisco AnyConnect**
    - **SonicWall Mobile Connect**
    - **F5 Edge Client**
    - **Pulse Secure**

