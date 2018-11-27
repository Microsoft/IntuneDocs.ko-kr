---
title: Microsoft Intune에서 Android 장치에 대한 VPN 설정 구성 - Azure | Microsoft Docs
description: Android 및 Android for Work 디바이스의 VPN 구성 프로필을 만들 때 연결 이름, VPN 서버의 IP 주소 또는 FQDN을 입력하고 VPN 서버를 통한 사용자 인증 방법을 선택한 다음, Citrix, SonicWall, Check Point Capsule, Pulse Secure 및 Microsoft Edge 연결 유형을 선택합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: ac4b7821f132c92b247538e4ea6131f517da7698
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187696"
---
# <a name="configure-vpn-settings-for-devices-running-android-in-intune"></a>Intune에서 Android를 실행하는 장치에 대한 VPN 설정 구성

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 Android를 실행하는 장치에서 VPN 연결을 구성하는 데 사용할 수 있는 Intune 설정을 설명합니다.

다음 플랫폼에 대해 VPN 설정을 구성할 수 있습니다.

- [OWA(Outlook Web Access)](#android-vpn-settings)
- [Android for Work](#android-for-work-vpn-settings)

선택한 설정에 따라 다음 모든 값을 구성할 수 없습니다.

## <a name="android-vpn-settings"></a>Android VPN 설정

- **연결 이름**: 이 연결에 대한 이름을 입력합니다. 최종 사용자는 장치에서 사용 가능한 VPN 연결을 검색할 때 이 이름을 볼 수 있습니다.
- **IP 주소 또는 FQDN**: 장치가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)을 입력합니다. 예를 들어 **192.168.1.1** 또는 **vpn.contoso.com**을 입력합니다.

  - **인증 방법**: 장치가 VPN 서버에 인증하는 방법을 선택합니다. 옵션은 다음과 같습니다.

    - **인증서**: 연결을 인증할 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](certificates-configure.md)에는 인증서 프로필을 만드는 단계가 나열됩니다.
    - **사용자 이름 및 암호**: VPN 서버에 로그인할 때 최종 사용자에게 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.

- **연결 형식**: VPN 연결 형식을 선택합니다. 옵션은 다음과 같습니다.

  - **검사점 캡슐 VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **Citrix**

- **지문**(Check Point Capsule VPN에만 해당): VPN 서버를 신뢰할 수 있는지 확인하려면 **Contoso 지문 코드**와 같은 문자열을 입력합니다. 연결 시 동일한 지문을 가진 서버를 신뢰하도록 지문을 클라이언트에 보낼 수 있습니다. 장치에 지문이 없으면, 사용자에게 지문을 보여주면서 VPN 서버를 신뢰할 것인지 묻는 메시지가 표시됩니다. 사용자는 지문을 수동으로 확인한 후 연결할 신뢰를 선택합니다.
- **Citrix VPN 특성에 대한 키 및 값 쌍을 입력**(Citrix에만 해당): Citrix에서 제공하는 키 및 값 쌍을 입력합니다. 이러한 값은 VPN 연결의 속성을 구성합니다.

## <a name="android-for-work-vpn-settings"></a>Android for Work VPN 설정

- **연결 이름**: 이 연결에 대한 이름을 입력합니다. 최종 사용자는 장치에서 사용 가능한 VPN 연결을 검색할 때 이 이름을 볼 수 있습니다.
- **IP 주소 또는 FQDN**: 장치가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)을 입력합니다. 예를 들어 **192.168.1.1** 또는 **vpn.contoso.com**을 입력합니다.

  - **인증 방법**: 장치가 VPN 서버에 인증하는 방법을 선택합니다. 옵션은 다음과 같습니다.
  
    - **인증서**: 연결을 인증할 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](certificates-configure.md)에는 인증서 프로필을 만드는 단계가 나열됩니다.
    - **사용자 이름 및 암호**: VPN 서버에 로그인할 때 최종 사용자에게 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다.

- **연결 형식**: VPN 연결 형식을 선택합니다. 옵션은 다음과 같습니다.

  - **검사점 캡슐 VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

## <a name="next-steps"></a>다음 단계
[Intune의 VPN 프로필](vpn-settings-configure.md)
