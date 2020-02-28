---
title: Microsoft Intune에서 macOS 디바이스에 대한 VPN 설정 구성 - Azure | Microsoft Docs
description: 연결 세부 정보, 분할 터널링, 사용자 지정 VPN 설정(식별자 포함), 키/값 쌍, 구성 스크립트를 사용하는 프록시 설정, IP 또는 FQDN 주소 그리고 macOS를 실행하는 디바이스에서 Microsoft Intune의 TCP 포트를 포함해 VPN(가상 사설망) 구성 프로필을 추가하거나 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b20a7eca6f71d46380f9fcdb1674226cc54a104f
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510782"
---
# <a name="add-vpn-settings-on-macos-devices-in-microsoft-intune"></a>Microsoft Intune의 macOS 디바이스에 대한 VPN 설정 추가



이 아티클에서는 macOS를 실행하는 디바이스에서 VPN 연결을 구성하는 데 사용할 수 있는 Intune 설정을 설명합니다.

선택한 설정에 따라 다음 목록의 일부 값을 구성할 수 없습니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](vpn-settings-configure.md).

> [!NOTE]
> 이러한 설정은 모든 등록 유형에 사용할 수 있습니다. 등록 유형에 대한 자세한 내용은 [macOS 등록](../enrollment/macos-enroll.md)을 참조하세요.

## <a name="base-vpn-settings"></a>기본 VPN 설정

**연결 이름**: 이 연결의 이름을 입력합니다. 최종 사용자가 디바이스에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **IP 주소 또는 FQDN**: 디바이스를 연결할 VPN 서버의 정규화된 도메인 이름 또는 IP 주소를 입력합니다. 예: **192.168.1.1**, **vpn.contoso.com**.
- **인증 방법**: 디바이스가 VPN 서버에 인증하는 방법을 선택합니다.
  - **인증서**: **인증 인증서** 아래에서 이전에 연결을 인증하기 위해 만든 SCEP 또는 PKCS 인증서 프로필을 선택합니다. 인증서 프로필에 대한 자세한 내용은 [인증서를 구성하는 방법](../protect/certificates-configure.md)을 참조하세요.
  - **사용자 이름 및 암호**: 최종 사용자는 VPN 서버에 로그인하기 위해 사용자 이름 및 암호를 제공해야 합니다.
- **연결 형식**: 다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.
  - **검사점 캡슐 VPN**
  - **Cisco AnyConnect**
  - **SonicWall Mobile Connect**
  - **F5 Edge Client**
  - **Pulse Secure**
  - **사용자 지정 VPN**
- **분할 터널링**: 디바이스에서 트래픽에 따라 사용할 연결을 결정할 수 있도록 하는 이 옵션을 **사용** 또는 **사용 안 함**으로 설정합니다. 예를 들어 호텔에 있는 사용자는 VPN 연결을 사용하여 작업 파일에 액세스하지만, 일반적인 웹 검색에는 호텔의 표준 네트워크를 사용합니다.

<!--- **Per-app VPN** - Select this option if you want to associate this VPN connection with an iOS/iPadOS or macOS app so that the connection will be opened when the app is run. You can associate the VPN profile with an app when you assign the software. For more information, see [How to assign and monitor apps](../apps/apps-deploy.md). --->

## <a name="custom-vpn-settings"></a>사용자 지정 VPN 설정

**사용자 지정 VPN**을 선택한 경우 다음 추가 설정을 구성합니다.

- **VPN 식별자**: 사용 중인 VPN 앱에 대한 식별자를 입력합니다. 이 식별자는 VPN 공급자가 제공합니다.
- **사용자 지정 VPN 특성에 대한 키 및 값 쌍 입력**: VPN 연결을 사용자 지정하는 **키** 및 **값**을 추가하거나 가져옵니다. 이러한 값은 일반적으로 VPN 공급자가 제공합니다.

## <a name="proxy-settings"></a>프록시 설정

- **자동 구성 스크립트**: 파일을 사용하여 프록시 서버를 구성합니다. 구성 파일을 포함하는 **프록시 서버 URL**을 입력합니다. 예를 들어 다음과 같이 입력합니다. `http://proxy.contoso.com`
- **주소**: 프록시 서버 주소를 IP 주소로 입력합니다.
- **포트 번호**: 프록시 서버와 연결된 포트 번호를 입력합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Android](vpn-settings-android.md), [Android Enterprise](vpn-settings-android-enterprise.md), [iOS/iPadOS](vpn-settings-ios.md) 및 [Windows 10](vpn-settings-windows-10.md) 디바이스에서 VPN 설정을 구성합니다.
