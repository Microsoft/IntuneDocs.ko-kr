---
title: Microsoft Intune에서 iOS 디바이스에 대한 VPN 설정 구성 - Azure | Microsoft Docs
description: 기본 설정에서 연결 세부 정보, 인증 방법 및 분할 터널링을 비롯하여 식별자를 포함하는 사용자 지정 VPN 설정, Safari URL을 포함하는 앱당 VPN 설정, SSID 또는 DNS 검색 도메인을 포함하는 주문형 VPN 및 iOS를 실행하는 디바이스의 Microsoft Intune에서 구성 스크립트, IP 또는 FQDN 주소 및 TCP 포트를 포함하는 프록시 설정 등 VPN(가상 프라이빗 네트워크) 구성 설정을 사용하는 VPN 구성 프로필을 추가하거나 만듭니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 274b5a8d45f9fb525010e4d225172a6a1ce22275
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734156"
---
# <a name="add-vpn-settings-on-ios-devices-in-microsoft-intune"></a>Microsoft Intune의 iOS 디바이스에 대한 VPN 설정 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune에는 iOS 디바이스에 배포할 수 있는 여러 VPN 설정이 포함됩니다. 조직의 네트워크에 VPN 연결을 만들고 구성하는 데 이러한 설정이 사용됩니다. 이 문서에서는 이러한 설정을 설명합니다. 일부 설정은 Citrix, Zscaler 등과 같은 일부 VPN 클라이언트에 대해서만 지원됩니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](vpn-settings-configure.md).

> [!NOTE]
> 이러한 설정은 모든 등록 형식에 사용할 수 있습니다. 등록 유형에 대 한 자세한 내용은 [iOS 등록](../enrollment/ios-enroll.md)을 참조 하세요.

## <a name="connection-type"></a>연결 형식

다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.

- **검사점 캡슐 VPN**
- **Cisco Legacy AnyConnect**: [Cisco Legacy AnyConnect](https://itunes.apple.com/app/cisco-legacy-anyconnect/id392790924) 앱 버전 4.0.5x 이전에 적용할 수 있습니다.
- **Cisco AnyConnect**: [Cisco AnyConnect](https://itunes.apple.com/app/cisco-anyconnect/id1135064690) 앱 버전 4.0.7x 이상에 적용할 수 있습니다.
- **SonicWall Mobile Connect**
- **F5 Access Legacy**: F5 Access 앱 버전 2.1 이전에 적용할 수 있습니다.
- **F5 Access**: F5 Access 앱 버전 3.0 이상에 적용할 수 있습니다.
- **Palo Alto Networks GlobalProtect(Legacy)** : Palo Alto Networks GlobalProtect 앱 버전 4.1 이전에 적용할 수 있습니다.
- **Palo Alto Networks GlobalProtect**: Palo Alto Networks GlobalProtect 앱 버전 5.0 이상에 적용할 수 있습니다.
- **Pulse Secure**
- **Cisco(IPSec)**
- **Citrix VPN**
- **Citrix SSO**
- **Zscaler**: 조건부 액세스를 사용하거나 사용자가 Zscaler 로그인 화면을 무시하도록 허용하려면 ZPA(Zscaler Private Access)를 Azure AD 계정과 통합해야 합니다. 자세한 단계는 [Zscaler 설명서](https://help.zscaler.com/zpa/configuration-example-microsoft-azure-ad)를 참조하세요. 
- **Ikev2**: [ikev2 설정](#ikev2-settings) (이 문서의)에서는 속성에 대해 설명 합니다.
- **사용자 지정 VPN**

> [!NOTE]
> Cisco, Citrix, F5 및 Palo Alto는 해당 레거시 클라이언트가 iOS 12에서 작동하지 않는다고 발표했습니다. 가능한 한 빨리 새 앱으로 마이그레이션해야 합니다. 자세한 내용은 [Microsoft Intune 지원 팀 블로그](https://go.microsoft.com/fwlink/?linkid=2013806&clcid=0x409)를 참조하세요.

## <a name="base-vpn-settings"></a>기본 VPN 설정

다음 목록에 표시된 설정은 선택한 VPN 연결 형식에 의해 결정됩니다.  

- **연결 이름**: 최종 사용자가 디바이스에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **사용자 지정 도메인 이름**(Zscaler에만 해당): 사용자가 속하는 도메인을 사용하여 Zscaler 앱의 로그인 필드를 미리 채웁니다. 예를 들어 사용자 이름이 `Joe@contoso.net`인 경우 도메인 `contoso.net`은 앱이 열릴 때 필드에 정적으로 표시됩니다. 도메인 이름을 입력하지 않으면 Azure AD(Active Directory)에서 UPN의 도메인 부분이 사용됩니다.
- **IP 주소 또는 FQDN**: 디바이스가 연결되는 VPN 서버의 IP 주소 또는 FQDN(정규화된 도메인 이름)입니다. 예를 들어 `192.168.1.1` 또는 `vpn.contoso.com`을 입력합니다.
- **조직의 클라우드 이름**(Zscaler에만 해당): 조직이 프로비전되는 클라우드 이름을 입력합니다. Zscaler에 로그인하는 데 사용하는 URL에는 이름이 포함됩니다.  
- **인증 방법**: 디바이스가 VPN 서버에 인증하는 방법을 선택합니다. 
  - **인증서**: **인증 인증서** 아래에서 연결을 인증하기 위해 기존 SCEP 또는 PKCS 인증서 프로필을 선택합니다. [인증서 구성](../protect/certificates-configure.md)에서는 인증서 프로필에 대한 몇 가지 지침을 제공합니다.
  - **사용자 이름 및 암호**: 최종 사용자는 VPN 서버에 로그인하기 위해 사용자 이름 및 암호를 입력해야 합니다.  

    > [!NOTE]
    > 사용자 이름과 암호를 Cisco IPsec VPN에 대한 인증 방법으로 사용하는 경우 사용자 지정 Apple Configurator 프로필을 통해 SharedSecret을 전달해야 합니다.

- **제외된 URL**(Zscaler에만 해당): Zscaler VPN에 연결되면 Zscaler 클라우드 외부에서 나열된 URL에 액세스할 수 있습니다. 

- **분할 터널링**: 디바이스에서 트래픽에 따라 사용할 연결을 결정할 수 있도록 **사용** 또는 **사용 안 함**으로 설정합니다. 예를 들어 호텔에 있는 사용자는 VPN 연결을 사용하여 작업 파일에 액세스하지만, 일반적인 웹 검색에는 호텔의 표준 네트워크를 사용합니다.

- **VPN 식별자**(사용자 지정 VPN, Zscaler 및 Citrix): 사용 중인 VPN 앱의 식별자이며, VPN 공급자에서 제공합니다.
  - **조직의 사용자 지정 VPN 특성에 대한 키/값 쌍 입력**: VPN 연결을 사용자 지정하는 **키** 및 **값**을 추가하거나 가져옵니다. 이러한 값은 일반적으로 VPN 공급자가 제공합니다.

- **NAC(네트워크 액세스 제어) 사용**(Citrix SSO, F5 Access): **동의**를 선택하는 경우 디바이스 ID가 VPN 프로필에 포함됩니다. 이 ID는 VPN에 대한 인증으로 네트워크 액세스를 허용하거나 차단하는 데 사용할 수 있습니다.

  **F5 Access를 사용하는 경우** 다음을 확인합니다.

  - F5 BIG-IP 13.1.1.5를 사용하고 있는지 확인합니다. BIG-IP 14는 지원되지 않습니다.
  - BIG-IP와 NAC용 Intune을 통합하세요. [개요: 엔드포인트 관리 시스템을 사용하여 디바이스 상태 검사를 위한 APM 구성](https://support.f5.com/kb/en-us/products/big-ip_apm/manuals/product/apm-client-configuration-7-1-6/6.html#guid-0bd12e12-8107-40ec-979d-c44779a8cc89) F5 가이드를 참조하세요.
  - VPN 프로필에서 NAC를 사용하도록 설정합니다.

  **게이트웨이에서 Citrix SSO를 사용하는 경우** 다음을 확인하세요.

  - Citrix Gateway 12.0.59 이상을 사용 중인지 확인합니다.
  - 사용자가 디바이스에 Citrix SSO 1.1.6 이상을 설치했는지 확인합니다.
  - Citrix 게이트웨이와 NAC용 Intune을 통합하세요. [Microsoft Intune/Enterprise Mobility Suite와 NetScaler 통합(LDAP+OTP 시나리오)](https://www.citrix.com/content/dam/citrix/en_us/documents/guide/integrating-microsoft-intune-enterprise-mobility-suite-with-netscaler.pdf) Citrix 배포 가이드를 참조하세요.
  - VPN 프로필에서 NAC를 사용하도록 설정합니다.

  **중요한 세부 정보**:  

  - NAC를 사용하도록 설정하는 경우 VPN의 연결이 24시간마다 끊어졌습니다. VPN을 즉시 다시 연결할 수 있습니다.
  - 디바이스 ID는 프로필의 일부이지만 Intune에는 표시되지 않습니다. 이 ID는 Microsoft에서 저장되거나 공유되지 않습니다.

  디바이스 ID가 VPN 파트너에 의해 지원되면 Citrix SSO와 같은 VPN 클라이언트가 ID를 가져올 수 있습니다. 그런 다음, Intune을 쿼리하여 디바이스가 등록되었는지 확인하고 VPN 프로필이 정책을 준수하는지 여부를 확인합니다.

  - 이 설정을 제거하려면 프로필을 다시 만들고 **동의함**을 선택하지 않습니다. 그런 다음, 프로필을 다시 할당합니다.

## <a name="ikev2-settings"></a>IKEv2 설정

이러한 설정은 **연결 유형** > **IKEv2**를 선택 하는 경우에 적용 됩니다.

- **원격 식별자**: IKEv2 서버의 네트워크 IP 주소, Fqdn, userfqdn 또는 ASN1DN을 입력 합니다. 예를 들어 `10.0.0.3` 또는 `vpn.contoso.com`을 입력합니다. 일반적으로 [**연결 이름과**](#base-vpn-settings) 같은 값을 입력 합니다 (이 문서 참조). 그러나 IKEv2 서버 설정에 따라 달라 집니다.

- **클라이언트 인증 유형**: VPN 클라이언트가 vpn에 인증 하는 방법을 선택 합니다. 옵션은 다음과 같습니다.
  - **사용자 인증** (기본값): VPN에 대 한 사용자 자격 증명을 인증 합니다.
  - **컴퓨터 인증**: 장치 자격 증명이 VPN에 인증 합니다.

- **인증 방법**: 서버에 보낼 클라이언트 자격 증명 유형을 선택 합니다. 옵션은 다음과 같습니다.
  - **인증서**: 기존 인증서 프로필을 사용 하 여 VPN에 인증 합니다. 이 인증서 프로필이 사용자 또는 장치에 이미 할당 되어 있어야 합니다. 그렇지 않으면 VPN 연결에 실패 합니다.
    - **인증서 유형**: 인증서에서 사용 하는 암호화 유형을 선택 합니다. 이 유형의 인증서를 허용 하도록 VPN 서버가 구성 되어 있어야 합니다. 옵션은 다음과 같습니다.
      - **RSA** (기본값)
      - **ECDSA256**
      - **ECDSA384**
      - **ECDSA521**

  - 사용자 **이름 및 암호** (사용자 인증에만 해당): 사용자가 VPN에 연결할 때 사용자 이름과 암호를 입력 하 라는 메시지가 표시 됩니다.
  - **공유 암호** (컴퓨터 인증만): VPN 서버에 보낼 공유 암호를 입력할 수 있습니다.
    - **공유 암호**: psk (미리 공유한 키) 라고도 하는 공유 암호를 입력 합니다. 값이 VPN 서버에 구성 된 공유 암호와 일치 하는지 확인 합니다.

- **서버 인증서 발급자 일반 이름**: vpn 서버에서 vpn 클라이언트에 인증할 수 있도록 허용 합니다. 장치의 VPN 클라이언트에 전송 되는 VPN 서버 인증서의 인증서 발급자 CN (일반 이름)을 입력 합니다. CN 값이 VPN 서버의 구성과 일치 하는지 확인할 수 있습니다. 그렇지 않으면 VPN 연결에 실패 합니다.
- **서버 인증서 일반 이름**: 인증서 자체에 대 한 CN을 입력 합니다. 비워 두면 원격 식별자 값이 사용 됩니다.

- **배달 되지 않은 피어 검색 율**: vpn 터널이 활성 상태 인지 여부를 vpn 클라이언트에서 확인 하는 빈도를 선택 합니다. 옵션은 다음과 같습니다.
  - **구성 되지 않음**: iOS 시스템 기본값을 사용 합니다 .이 기본값은 **미디어**를 선택 하는 것과 동일할 수 있습니다.
  - **없음**: 배달 되지 않은 피어 검색을 사용 하지 않도록 설정 합니다.
  - **낮음**: 30 분 마다 keepalive 메시지를 보냅니다.
  - **보통** (기본값): 10 분 마다 keepalive 메시지를 보냅니다.
  - **High**: 60 초 마다 keepalive 메시지를 보냅니다.

- **Tls 버전 범위 최소**: 사용할 최소 TLS 버전을 입력 합니다. @No__t-0, `1.1` 또는 `1.2`를 입력 합니다. 이 값을 비워 두면 기본값 `1.0`이 사용 됩니다.
- **Tls 버전 범위 최대**: 사용할 최대 tls 버전을 입력 합니다. @No__t-0, `1.1` 또는 `1.2`를 입력 합니다. 이 값을 비워 두면 기본값 `1.2`이 사용 됩니다.
- **완벽 한 전달 보안**: **사용** 을 선택 하 여 PFS (완벽 한 전달 보안)를 설정 합니다. PFS는 세션 키가 손상 된 경우의 영향을 줄이는 IP 보안 기능입니다. **Disable** (기본값)은 PFS를 사용 하지 않습니다.
- **인증서 해지 확인**: **사용** 을 선택 하 여 VPN 연결이 성공 하도록 허용 하기 전에 인증서가 해지 되지 않았는지 확인 합니다. 이 확인은 가장 좋은 방법입니다. 인증서가 해지 되었는지 여부를 확인 하기 전에 VPN 서버가 시간 초과 되 면 액세스 권한이 부여 됩니다. **사용 안 함** (기본값)은 해지 된 인증서를 확인 하지 않습니다.

- **보안 연결 매개 변수 구성**: **구성 되지 않음** (기본값)은 iOS 시스템 기본값을 사용 합니다. **사용** 을 선택 하 여 VPN 서버와의 보안 연결을 만들 때 사용 되는 매개 변수를 입력 합니다.
  - **암호화 알고리즘**: 원하는 알고리즘을 선택 합니다.
    - DES
    - 3DES
    - AES-128
    - AES-256 (기본값)
    - AES-128-GCM
    - AES-256-GCM
  - **무결성 알고리즘**: 원하는 알고리즘을 선택 합니다.
    - SHA1-96
    - SHA1-160
    - SHA2-256 (기본값)
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman 그룹**: 원하는 그룹을 선택 합니다. 기본값은 그룹 `2`입니다.
  - **수명** (분): 키를 회전할 때까지 보안 연결이 활성 상태로 유지 되는 기간을 선택 합니다. @No__t-0과 `1440` 사이의 전체 값 (1440 분은 24 시간)을 입력 합니다. 기본값은 `1440`입니다.

- **자식 보안 연결에 대 한 별도의 매개 변수 집합 구성**: iOS를 사용 하면 IKE 연결 및 자식 연결에 대 한 별도의 매개 변수를 구성할 수 있습니다. 

  **구성 되지 않음** (기본값)은 이전 **보안 연결 매개 변수 구성** 설정에 입력 한 값을 사용 합니다. **사용** 을 선택 하 여 VPN 서버와의 *자식* 보안 연결을 만들 때 사용 되는 매개 변수를 입력 합니다.
  - **암호화 알고리즘**: 원하는 알고리즘을 선택 합니다.
    - DES
    - 3DES
    - AES-128
    - AES-256 (기본값)
    - AES-128-GCM
    - AES-256-GCM
  - **무결성 알고리즘**: 원하는 알고리즘을 선택 합니다.
    - SHA1-96
    - SHA1-160
    - SHA2-256 (기본값)
    - SHA2-384
    - SHA2-512
  - **Diffie-hellman 그룹**: 원하는 그룹을 선택 합니다. 기본값은 그룹 `2`입니다.
  - **수명** (분): 키를 회전할 때까지 보안 연결이 활성 상태로 유지 되는 기간을 선택 합니다. @No__t-0과 `1440` 사이의 전체 값 (1440 분은 24 시간)을 입력 합니다. 기본값은 `1440`입니다.

## <a name="automatic-vpn-settings"></a>자동 VPN 설정

- **앱당 VPN**: 앱당 VPN을 사용하도록 설정합니다. VPN 연결이 특정 앱을 열 때 자동으로 트리거될 수 있습니다. 이 VPN 프로필을 사용하여 앱을 연결할 수도 있습니다. 자세한 내용은 [iOS용 앱당 VPN을 설정하기 위한 지침](vpn-setting-configure-per-app.md)을 참조하세요.
  - **공급자 형식**: Pulse Secure 및 사용자 지정 VPN에 대해서만 지원됩니다.
  - Pulse Secure 또는 사용자 지정 VPN과 함께 iOS **앱당 VPN** 프로필을 사용하면 앱 계층 터널링(app-proxy) 또는 패킷 수준 터널링(packet-tunnel)을 선택합니다. **ProviderType** 값은 앱 계층 터널링의 경우 **app-proxy**로 설정하고, 패킷 계층 터널링의 경우 **packet-tunnel**로 설정합니다. 사용할 값을 모르는 경우 VPN 공급자의 설명서를 확인하세요.
  - **이 VPN을 트리거하는 Safari URL**: 하나 이상의 웹 사이트 URL을 추가합니다. 디바이스에서 Safari 브라우저를 사용하여 이러한 URL을 방문할 때 VPN 연결이 자동으로 설정됩니다.

- **주문형 VPN**: VPN 연결이 시작되는 시기를 제어하는 조건부 규칙을 구성합니다. 예를 들어 디바이스가 회사 Wi-Fi 네트워크에 연결되지 않은 경우에만 VPN 연결이 사용되는 조건을 만듭니다. 또는 조건을 만듭니다. 예를 들어 사용자가 입력한 DNS 검색 도메인에 디바이스가 액세스할 수 없는 경우 VPN 연결이 시작되지 않습니다.

  - **SSID 또는 DNS 검색 도메인**: 이 조건에서 무선 네트워크 **SSID** 또는 **DNS 검색 도메인**을 사용할지를 선택합니다. 하나 이상의 SSID 또는 검색 도메인을 구성하려면 **추가**를 선택합니다.
  - **URL 문자열 프로브:** : 선택 사항입니다. 규칙이 테스트로 사용하는 URL을 입력합니다. 이 프로필을 포함한 디바이스에서 리디렉션 없이 이 URL에 액세스하는 경우 VPN 연결이 시작됩니다. 또한 디바이스가 대상 URL에 연결됩니다. 사용자에게 URL 문자열 프로브 사이트가 표시되지 않습니다. URL 문자열 프로브 예제는 VPN을 연결하기 전에 디바이스 준수를 확인하는 감사 웹 서버의 주소입니다. 또는 VPN을 통해 디바이스를 대상 URL에 연결하기 전에 URL에서 VPN이 사이트에 연결할 수 있는지 테스트할 수도 있습니다.
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

- **자동 구성 스크립트**: 파일을 사용하여 프록시 서버를 구성합니다. 구성 파일이 포함된 **프록시 서버 URL**(예: `http://proxy.contoso.com`)을 입력합니다.
- **주소**: 프록시 서버의 정규화된 호스트 이름 IP 주소를 입력합니다.
- **포트 번호**: 프록시 서버와 연결된 포트 번호 입력

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Android](vpn-settings-android.md), [android Enterprise](vpn-settings-android-enterprise.md), [macos](vpn-settings-macos.md)및 [Windows 10](vpn-settings-windows-10.md) 장치에서 VPN 설정을 구성 합니다.
