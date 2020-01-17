---
title: Microsoft Intune에서 Windows 8.1 디바이스에 대한 VPN 설정 구성 - Azure | Microsoft Docs
description: Vpn (가상 사설망) 구성 설정을 사용 하 여 VPN 구성 프로필을 추가 하거나 만듭니다. 여기에는 연결 세부 정보를 비롯 하 여 IP 또는 FQDN 주소를 포함 하는 프록시 설정과 Windows 8.1를 실행 하는 장치에 Microsoft Intune TCP 포트가 포함 됩니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9f9a1399d5474d79ac8fd48a8aa3a844f20eb640
ms.sourcegitcommit: e166b9746fcf0e710e93ad012d2f52e2d3ed2644
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207046"
---
# <a name="add-vpn-settings-on-windows-81-devices-in-microsoft-intune"></a>Microsoft Intune의 Windows 8.1 디바이스에 대한 VPN 설정 추가



이 아티클에서는 Windows 8.1을 실행하는 디바이스에서 VPN 연결을 구성하는 데 사용할 수 있는 Intune 설정을 설명합니다.

선택한 설정에 따라 다음 목록의 일부 값을 구성할 수 없습니다.

## <a name="base-vpn-settings"></a>기본 VPN 설정

- **Windows 8.1에만 모든 설정 적용**: Intune 클래식 포털에서이 설정을 구성 합니다. Microsoft Endpoint Manager 관리 센터에서이 설정은 변경할 수 없습니다. **구성됨**으로 설정한 경우 모든 설정이 Windows 8.1 디바이스에만 적용됩니다. **구성되지 않음**으로 설정한 경우 Windows 10 디바이스에도 이러한 설정이 적용됩니다.
- **연결 이름**: 이 연결의 이름을 입력합니다. 사용자가 디바이스에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **서버**: 디바이스를 연결할 VPN 서버를 한 대 이상 추가합니다.
  - **추가**: 다음 정보를 지정할 수 있는 **행 추가** 페이지를 엽니다.
    - **설명**: 서버의 설명이 포함된 이름(예: **Contoso VPN 서버**)을 지정합니다.
    - **IP 주소 또는 FQDN**: 디바이스를 연결할 VPN 서버의 정규화된 도메인 이름 또는 IP 주소를 입력합니다. 예: **192.168.1.1**, **vpn.contoso.com**.
    - **기본 서버**: 이 서버를 디바이스에서 연결을 설정하는 데 사용할 기본 서버로 사용합니다. 기본적으로 하나의 서버만 설정해야 합니다.
  - **가져오기**: 설명, IP 주소 또는 FQDN, 기본 서버 형식의 서버 목록을 포함하는 쉼표로 구분된 파일로 이동합니다. **확인**을 선택하여 이러한 서버를 **서버** 목록으로 가져옵니다.
  - **내보내기**: 서버 목록을 쉼표로 구분된 값(csv) 파일로 내보냅니다.

- **연결 형식**: 다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.
  - **검사점 캡슐 VPN**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**

<!--- **Fingerprint** (Check Point Capsule VPN only): Specify a string (for example, "Contoso Fingerprint Code") that will be used to verify that the VPN server can be trusted. A fingerprint can be sent to the client so it knows to trust any server that presents the same fingerprint when connecting. If the device doesn’t already have the fingerprint, it will prompt the user to trust the VPN server that they are connecting to while showing the fingerprint. (The user manually verifies the fingerprint and chooses **trust** to connect.) --->

- **로그인 그룹 또는 도메인**(SonicWall Mobile Connect에만 해당): 연결하려는 로그인 그룹 또는 도메인의 이름을 지정합니다.

- **역할**(Pulse Secure에만 해당): 이 연결에 대한 액세스 권한이 있는 사용자 역할의 이름을 지정합니다. 사용자 역할은 개인 설정과 옵션을 정의하고, 특정 액세스 기능을 사용 또는 사용하지 않도록 설정합니다.

- **영역**(Pulse Secure에만 해당): 사용하려는 인증 영역의 이름을 지정합니다. 인증 영역은 Pulse Secure 연결 형식에서 사용하는 인증 리소스 그룹입니다.

- **사용자 지정 XML**: VPN 연결을 구성하는 모든 사용자 지정 XML 명령을 지정합니다.

  **Pulse Secure 예제**:

  ```xml
  <pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
  ```

  **CheckPoint Mobile VPN 예제**:

  ```xml
  <CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
  ```

  **SonicWall Mobile Connect 예제**:

  ```xml
  <MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
  ```

  **F5 Edge Client 예제**:

  ```xml
  <f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
  ```

  사용자 지정 XML 명령을 작성하는 방법에 대한 자세한 내용은 제조업체의 VPN 설명서를 참조하세요.

## <a name="proxy-settings"></a>프록시 설정

- **자동으로 프록시 설정 검색**: VPN 서버에 연결을 위한 프록시 서버가 필요한 경우 디바이스가 연결 설정을 자동으로 검색할지 여부를 지정합니다.
- **자동 구성 스크립트**: 파일을 사용하여 프록시 서버를 구성합니다. 구성 파일을 포함하는 **프록시 서버 URL**을 입력합니다. 예를 들어 다음과 같이 입력합니다. `http://proxy.contoso.com`
- **프록시 서버 사용**: 프록시 서버 설정을 수동으로 입력하려는 경우 이 옵션을 선택합니다.
  - **주소**: 프록시 서버 주소를 IP 주소로 입력합니다.
  - **포트 번호**: 프록시 서버와 연결된 포트 번호를 입력합니다.
- **로컬 주소에 프록시 서버 사용 안 함**: VPN 서버에 연결을 위한 프록시 서버가 필요하며 입력하는 로컬 주소에 대해 프록시 서버를 사용하지 않으려면 이 옵션을 선택합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Android](vpn-settings-android.md), [android Enterprise](vpn-settings-android-enterprise.md), [macos](vpn-settings-macos.md)및 [Windows 10](vpn-settings-windows-10.md) 장치에서 VPN 설정을 구성 합니다.
