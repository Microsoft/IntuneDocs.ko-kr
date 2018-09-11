---
title: Microsoft Intune에서 iOS 장치에 대한 VPN 설정 - Azure | Microsoft Docs
description: 기본 설정에서 연결 세부 정보, 인증 방법 및 분할 터널링을 비롯하여 식별자를 포함하는 사용자 지정 VPN 설정, Safari URL을 포함하는 앱당 VPN 설정, SSID 또는 DNS 검색 도메인을 포함하는 주문형 VPN 및 iOS를 실행하는 장치의 Microsoft Intune에서 구성 스크립트, IP 또는 FQDN 주소 및 TCP 포트를 포함하는 프록시 설정 등 지원되는 VPN(가상 사설망) 구성 설정을 봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 8/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: deb6a230573ff20237e6eee386052baba472832a
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43313873"
---
# <a name="configure-vpn-settings-in-microsoft-intune-for-devices-running-ios"></a>iOS를 실행하는 장치용 Microsoft Intune에서 VPN 설정 구성

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 iOS를 실행하는 장치에서 VPN 연결을 구성하는 데 사용할 수 있는 Intune 설정을 설명합니다.

선택한 설정에 따라 다음 목록의 일부 값을 구성할 수 없습니다.

## <a name="base-vpn-settings"></a>기본 VPN 설정
아래 목록에서 표시되는 실제 설정은 선택하는 VPN 연결 형식에 따라 결정됩니다.  
- **연결 이름**: 최종 사용자가 장치에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **사용자 지정 도메인 이름**(Zscaler에만 해당): 사용자가 속하는 도메인을 사용하여 Zscaler 앱의 로그인 필드를 미리 채웁니다. 예를 들어 사용자 이름이 **Joe@contoso.net**인 경우 도메인이 **contoso.net**은 앱이 열릴 때 필드에 정적으로 표시됩니다. 도메인 이름을 입력하지 않으면 Azure Active Directory에서 UPN의 도메인 부분이 사용됩니다.
- **IP 주소 또는 FQDN**: 장치가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)입니다. 예를 들어 **192.168.1.1** 또는 **vpn.contoso.com**을 입력합니다. 
- **조직의 클라우드 이름**(Zscaler에만 해당): 조직이 프로비전되는 클라우드의 이름을 입력합니다. 이름을 찾으려면 Zscaler에 로그인하는 데 사용하는 URL을 확인합니다.  
- **인증 방법**: 장치가 VPN 서버에 인증하는 방법을 선택합니다. 
  - **인증서**: **인증 인증서** 아래에서 연결을 인증하기 위해 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](certificates-configure.md)에서는 인증서 프로필에 대한 몇 가지 지침을 제공합니다.
  - **사용자 이름 및 암호**: 최종 사용자는 VPN 서버에 로그인하기 위해 사용자 이름 및 암호를 입력해야 합니다.  

    > [!NOTE]
    > 사용자 이름과 암호를 Cisco IPsec VPN에 대한 인증 방법으로 사용하는 경우 사용자 지정 Apple Configurator 프로필을 통해 SharedSecret을 전달해야 합니다.
  
- **연결 형식**: 다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.
  - **검사점 캡슐 VPN**
  - **Cisco Legacy AnyConnect**: [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 앱 버전 4.0.5x 이전에 적용할 수 있습니다.
  - **Cisco AnyConnect**: [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 앱 버전 4.0.7x 이상에 적용할 수 있습니다.
  - **SonicWall Mobile Connect**
  - **F5 Access Legacy**: F5 Access 앱 버전 2.1 이전에 적용할 수 있습니다.
  - **F5 Access**: F5 Access 앱 버전 3.0 이상에 적용할 수 있습니다.
  - **Palo Alto Networks GlobalProtect(Legacy)**: Palo Alto Networks GlobalProtect 앱 버전 4.1 이전에 적용할 수 있습니다.
  - **Palo Alto Networks GlobalProtect**: Palo Alto Networks GlobalProtect 앱 버전 5.0 이상에 적용할 수 있습니다.
  - **Pulse Secure**
  - **Cisco(IPSec)**
  - **Citrix VPN**
  - **Citrix SSO**
  - **Zscaler**: Azure Active Directory 계정과 ZPA(Zscaler Private Access)를 통합해야 합니다. 자세한 단계는 [Zscaler 설명서](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad#Azure_UserSSO)를 참조하세요. 
  - **사용자 지정 VPN**    

    > [!NOTE]
    > Cisco, Citrix, F5 및 Palo Alto는 해당 레거시 클라이언트가 iOS 12의 향후 릴리스에서 작동하지 않을 예정임을 발표했습니다. 가능한 한 빨리 새 앱으로 마이그레이션해야 합니다. 자세한 내용은 [Microsoft Intune 지원 팀 블로그](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)를 참조하세요.

* **제외된 URL**(Zscaler에만 해당): Zscaler VPN에 연결되면 Zscaler 클라우드 외부에서 나열된 URL에 액세스할 수 있습니다. 

- **분할 터널링**: 장치에서 트래픽에 따라 사용할 연결을 결정할 수 있도록 **사용** 또는 **사용 안 함**으로 설정합니다. 예를 들어 호텔에 있는 사용자는 VPN 연결을 사용하여 작업 파일에 액세스하지만, 일반적인 웹 검색에는 호텔의 표준 네트워크를 사용합니다.   

## <a name="custom-vpn-settings"></a>사용자 지정 VPN 설정

**사용자 지정 VPN**을 연결 형식으로 선택한 경우 다음과 같은 설정을 구성합니다. 이러한 설정은 Zscaler 및 Citrix 연결에 대해서도 표시됩니다.

- **VPN 식별자**: 사용 중인 VPN 앱의 식별자이며, VPN 공급자에서 제공합니다.
- **조직의 사용자 지정 VPN 특성에 대한 키/값 쌍 입력**: VPN 연결을 사용자 지정하는 **키** 및 **값**을 추가하거나 가져옵니다. 이러한 값은 일반적으로 VPN 공급자가 제공합니다.

## <a name="automatic-vpn-settings"></a>자동 VPN 설정

- **앱별 VPN**: 이 옵션을 사용하면 앱별 VPN을 사용하도록 설정하여 특정 앱을 열 때 VPN 연결을 자동으로 트리거할 수 있습니다. 이 옵션을 선택하는 것 외에도 이 VPN 프로필과 앱을 연결해야 합니다. 자세한 내용은 [iOS용 앱별 VPN을 설정하기 위한 지침](vpn-setting-configure-per-app.md)을 참조하세요. 
  - **공급자 유형** 설정은 Pulse Secure 및 사용자 지정 VPN에 대해서만 사용 가능합니다.
  - Pulse Secure 또는 사용자 지정 VPN과 함께 iOS **앱당 VPN** 프로필을 사용할 때 앱 계층 터널링(app-proxy) 또는 패킷 수준 터널링(packet-tunnel)을 사용할 수 있습니다. **ProviderType** 값을 앱 계층 터널링에 대해 **앱 프록시** 또는 패널 계층 터널링에 대해 **패킷 터널**로 설정합니다. 사용할 값을 잘 모를 경우 VPN 공급자의 설명서를 참조하세요. 
  - **이 VPN을 트리거하는 Safari URL**: 하나 이상의 웹 사이트 URL을 추가하도록 선택합니다. 장치에서 Safari 브라우저를 사용하여 이러한 URL을 방문할 때 VPN 연결이 자동으로 설정됩니다.

- **주문형 VPN**: VPN 연결이 시작되는 시기를 제어하는 조건부 규칙을 구성합니다. 예를 들어 장치가 회사 Wi-Fi 네트워크에 연결되지 않은 경우에만 VPN 연결이 사용되는 조건을 만듭니다. 또는 장치에서 지정한 DNS 검색 도메인에 액세스할 수 없는 경우 VPN 연결이 시작되지 않는 조건을 만듭니다.

  - **SSID 또는 DNS 검색 도메인**: 이 조건에서 무선 네트워크 **SSID** 또는 **DNS 검색 도메인**을 사용할지를 선택합니다. 하나 이상의 SSID 또는 검색 도메인을 구성하려면 **추가**를 선택합니다.
  - **URL 문자열 프로브:**: 선택 사항입니다. 규칙이 테스트로 사용하는 URL을 입력합니다. 이 프로필이 설치된 장치가 리디렉션 없이 이 URL에 액세스할 수 있는 경우 VPN 연결이 시작되고 장치가 대상 URL에 연결됩니다. 사용자에게 URL 문자열 프로브 사이트가 표시되지 않습니다. URL 문자열 프로브 예제는 VPN을 연결하기 전에 장치 준수를 확인하는 감사 웹 서버의 주소입니다. 또는 VPN을 통해 장치를 대상 URL에 연결하기 전에 URL에서 VPN이 사이트에 연결할 수 있는지 테스트할 수도 있습니다.
  - **도메인 작업**: 다음 항목 중 하나를 선택합니다.
    - 필요한 경우 연결
    - 연결 안 함
  - **작업**: 다음 항목 중 하나를 선택합니다.
    - 연결
    - 연결 평가
    - 무시
    - 연결 끊기

## <a name="proxy-settings"></a>프록시 설정
프록시를 사용하는 경우 다음 설정을 구성합니다. 프록시 설정은 Zscaler VPN 연결에 사용할 수 없습니다.  

- **자동 구성 스크립트**: 파일을 사용하여 프록시 서버를 구성합니다. 구성 파일이 포함된 **프록시 서버 URL**(예: **http://proxy.contoso.com**)을 입력합니다.
- **주소**: 프록시 서버의 정규화된 호스트 이름 IP 주소를 입력합니다.
- **포트 번호**: 프록시 서버와 연결된 포트 번호 입력

## <a name="next-step"></a>다음 단계
[Intune에서 VPN 프로필 만들기](vpn-settings-configure.md)  
