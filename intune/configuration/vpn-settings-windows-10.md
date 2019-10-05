---
title: Microsoft Intune의 Windows 10 VPN 설정 - Azure | Microsoft Docs
description: 트래픽 규칙, 조건부 액세스, Windows 10에 대한 DNS 및 프록시 설정, Windows Holographic for Business 디바이스를 포함해 Microsoft Intune에서 사용할 수 있는 모든 VPN 설정, 사용 목적 및 수행 작업에 대해 읽고 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.reviewer: tycast
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5d5bd16964162bd30e1c246215ce5fafd23df5dd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734130"
---
# <a name="windows-10-and-windows-holographic-device-settings-to-add-vpn-connections-using-intune"></a>Intune을 사용하여 VPN 연결을 추가하기 위한 Windows 10 및 Windows Holographic 디바이스 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune을 사용하여 디바이스에 대한 VPN 연결을 추가하고 구성할 수 있습니다. 이 문서에서는 VPN(가상 프라이빗 네트워크)을 만들 때 일반적으로 사용되는 설정 및 기능을 나열하고 설명합니다. 이러한 VPN 설정 및 기능은 푸시되거나 디바이스에 배포되는 Intune에서 디바이스 구성 프로필에 사용됩니다.

MDM(모바일 디바이스 관리) 솔루션의 일부로 이러한 설정을 사용하여 VPN 공급 기업 사용, Always On 사용하도록 설정, DNS 사용, 프록시 추가 등을 비롯한 기능을 사용하거나 사용하지 않도록 설정합니다.

이러한 설정은 다음을 실행하는 디바이스에 적용됩니다.

- Windows 10
- Windows Holographic for Business

선택하는 설정에 따라 일부 값은 구성할 수 없습니다.

## <a name="before-you-begin"></a>시작하기 전에

[VPN 디바이스 구성 프로필을 만듭니다](vpn-settings-configure.md).

## <a name="base-vpn-settings"></a>기본 VPN 설정

- **연결 이름**: 이 연결에 대한 이름을 입력합니다. 최종 사용자가 디바이스에서 사용 가능한 VPN 연결 목록을 찾아볼 때 이 이름이 표시됩니다.
- **서버**: 디바이스를 연결할 한 대 이상의 VPN 서버를 추가합니다. 서버를 추가할 때 다음 정보를 입력합니다.
  - **설명**: 서버의 설명이 포함된 이름(예: **Contoso VPN 서버**) 입력
  - **IP 주소 또는 FQDN**: 디바이스가 연결되는 VPN 서버(예: **192.168.1.1** 또는 **vpn.contoso.com**)의 IP 주소 또는 FQDN(정규화된 도메인 이름) 입력
  - **기본 서버**: 이 서버를 디바이스에서 연결을 설정하는 데 사용할 기본 서버로 사용합니다. 기본적으로 하나의 서버만 설정합니다.
  - **가져오기**: 설명, IP 주소 또는 FQDN, 기본 서버 형식의 서버 목록을 포함하는 쉼표로 구분된 파일로 이동합니다. **확인**을 선택하여 이러한 서버를 **서버** 목록으로 가져옵니다.
  - **내보내기**: 서버 목록을 쉼표로 구분된 값(csv) 파일로 내보내기

- **내부 DNS를 사용하여 IP 주소 등록**: 내부 DNS를 사용하여 VPN 인터페이스에 할당된 IP 주소를 동적으로 등록하도록 Windows 10 VPN 프로필을 구성하려면 **사용**을 선택합니다. IP 주소를 동적으로 등록하지 않으려면 **사용 안 함**을 선택합니다.

- **연결 형식**: 다음 공급업체 목록에서 VPN 연결 형식을 선택합니다.

  - **Pulse Secure**
  - **F5 Edge Client**
  - **SonicWall Mobile Connect**
  - **검사점 캡슐 VPN**
  - **Citrix**
  - **Palo Alto Networks GlobalProtect**
  - **자동**
  - **IKEv2**
  - **L2TP**
  - **PPTP**

  VPN 연결 형식을 선택하면 다음 설정을 요청하는 메시지가 표시될 수도 있습니다.  
  - **Always On**: 다음과 같은 이벤트가 발생할 경우 VPN 연결에 자동으로 연결하려면 **사용**을 선택합니다. 
    - 자신의 디바이스에 사용자가 로그인하는 경우
    - 디바이스의 네트워크가 변경되는 경우
    - 디바이스의 화면이 꺼졌다가 다시 켜지는 경우 

  - **인증 방법**: 사용자가 VPN 서버에 인증하도록 할 방법을 선택합니다. **인증서**를 사용하면 무인 환경, 주문형 VPN, 앱별 VPN 등의 향상된 기능이 제공됩니다.
  - **로그온 시 자격 증명 기억**: 인증 자격 증명을 캐시하려면 선택합니다.
  - **사용자 지정 XML**: VPN 연결을 구성하는 사용자 지정 XML 명령을 입력합니다.
  - **EAP XML**: VPN 연결을 구성하는 EAP XML 명령을 입력합니다.

### <a name="pulse-secure-example"></a>Pulse Secure의 예

```
<pulse-schema><isSingleSignOnCredential>true</isSingleSignOnCredential></pulse-schema>
```

### <a name="f5-edge-client-example"></a>F5 Edge Client의 예

```
<f5-vpn-conf><single-sign-on-credential /></f5-vpn-conf>
```

### <a name="sonicwall-mobile-connect-example"></a>SonicWALL Mobile Connect의 예
**로그인 그룹 또는 도메인**: VPN 프로필에 이 속성을 설정할 수 없습니다. 대신, Mobile Connect는 사용자 이름 및 도메인을 `username@domain` 또는 `DOMAIN\username` 형식으로 입력할 경우 이 값을 구문 분석합니다.

예:

```
<MobileConnect><Compression>false</Compression><debugLogging>True</debugLogging><packetCapture>False</packetCapture></MobileConnect>
```

### <a name="checkpoint-mobile-vpn-example"></a>CheckPoint Mobile VPN의 예

```
<CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" />
```

### <a name="writing-custom-xml"></a>사용자 지정 XML 작성
사용자 지정 XML 명령을 작성하는 방법에 대한 자세한 내용은 각 제조업체의 VPN 설명서를 참조하세요.

사용자 지정 EAP XML을 만드는 방법에 대한 자세한 내용은 [EAP 구성](https://docs.microsoft.com/windows/client-management/mdm/eap-configuration)을 참조하세요.

## <a name="apps-and-traffic-rules"></a>앱 및 트래픽 규칙

- **이 VPN에 WIP 또는 앱 연결**: 일부 앱에서 이 VPN 연결을 사용하게 하려면 이 설정을 사용하도록 설정합니다. 옵션은 다음과 같습니다.

  - **이 연결에 WIP를 연결**: **이 연결에 대한 WIP 도메인**을 입력합니다.
  - **이 연결을 사용하여 앱 연결**: **이러한 앱에 대한 VPN 연결을 제한**한 다음, **연결된 앱**을 추가할 수 있습니다. 입력한 앱에서 자동으로 VPN 연결을 사용합니다. 앱의 유형에 따라 앱 식별자가 결정됩니다. 유니버설 앱의 경우 패키지 패밀리 이름을 입력합니다. 데스크톱 앱의 경우에는 앱의 파일 경로를 입력합니다.
  >[!IMPORTANT]
  >앱당 VPN에 대해 만든 모든 앱 목록을 보호하는 것이 좋습니다. 권한이 없는 사용자가 이 목록을 변경한 경우 해당 목록을 앱별 VPN 앱 목록으로 가져오는 경우 액세스 권한이 부여되면 안 되는 앱에 VPN 액세스 권한을 잠재적으로 부여하게 됩니다. 앱 목록을 보호할 수 있는 한 가지 방법은 ACL(액세스 제어 목록)을 사용하는 것입니다.

- **이 VPN 연결에 대한 네트워크 트래픽 규칙**: VPN 연결을 위해 사용할 프로토콜, 로컬 및 원격 포트와 주소 범위를 선택합니다. 네트워크 트래픽 규칙을 만들지 않으면 모든 프로토콜, 포트 및 주소 범위를 사용할 수 있습니다. 규칙을 만들고 나면 해당 규칙에 입력하는 프로토콜, 포트 및 주소 범위만 VPN 연결에 사용됩니다.

## <a name="conditional-access"></a>조건부 액세스

- **이 VPN 연결에 대한 조건부 액세스**: 클라이언트에서 디바이스 준수 흐름이 가능하게 합니다. 사용하도록 설정하면, VPN 클라이언트가 인증에 사용할 인증서를 가져오기 위해 Azure AD(Active Directory)와 통신합니다. 인증서 인증을 사용하려면 VPN을 설정해야 하고, VPN 서버가 Azure AD에서 반환된 서버를 신뢰해야 합니다.

- **대체 인증서를 사용한 SSO(Single Sign-On)** : 디바이스 준수에 대해 Kerberos 인증을 위한 VPN 인증 인증서와 다른 인증서를 사용합니다. 다음 설정으로 인증서를 입력합니다.

  - **이름**: EKU(확장된 키 사용)의 이름
  - **개체 식별자**: EKU의 개체 식별자
  - **발급자 해시**: SSO 인증서의 지문

## <a name="dns-settings"></a>DNS 설정

- **DNS 접미사 검색 목록**: **DNS 접미사**에서 DNS 접미사를 입력하고 **Add**를 입력합니다. 많은 접미사를 추가할 수 있습니다.

  DNS 접미사를 사용하는 경우 FQDN(정규화된 도메인 이름) 대신 짧은 이름을 사용해 네트워크 리소스를 검색할 수 있습니다. 짧은 이름을 사용하여 검색하는 경우 접미사는 DNS 서버에서 자동으로 결정됩니다. 예를 들어 `utah.contoso.com`은 DNS 접미사 목록에 있습니다. `DEV-comp`을 ping합니다. 이 시나리오에서는 `DEV-comp.utah.contoso.com`으로 확인됩니다.

  DNS 접미사는 나열된 순서로 확인되며 이 순서는 변경 가능합니다. 예를 들어, `colorado.contoso.com` 및 `utah.contoso.com`은 DNS 접미사 목록에 있으며 둘 다 `DEV-comp`이라는 리소스를 포함합니다. `colorado.contoso.com`은 목록의 맨 처음에 나오므로 `DEV-comp.colorado.contoso.com`으로 확인됩니다.
  
  순서를 변경하려면 DNS 접미사 왼쪽의 점을 클릭하고 해당 접미사를 맨 위로 끕니다.

  ![세 개의 점을 선택하고 클릭한 후 끌어 dns 접미사 이동](./media/vpn-settings-windows-10/vpn-settings-windows10-move-dns-suffix.png)

- **Nrpt (이름 확인 정책 테이블) 규칙**: nrpt (이름 확인 정책 테이블) 규칙은 VPN에 연결 된 경우 DNS에서 이름을 확인 하는 방법을 정의 합니다. VPN 연결이 설정된 후 VPN 연결에서 사용할 DNS 서버를 선택합니다.

  입력하는 도메인을 확인하려면 도메인, DNS 서버, 프록시 및 기타 세부 정보를 포함하는 테이블에 규칙을 추가할 수 있습니다. VPN 연결은 사용자가 입력할 도메인을 연결할 때 이러한 규칙을 사용합니다.

  새 규칙을 추가하려면 **추가**를 선택합니다. 각 서버에 대해 다음을 입력합니다.

  - **도메인**: 규칙을 적용하려면 FQDN(정규화된 도메인 이름) 또는 DNS 접미사를 입력합니다. 또한 DNS 접미사의 시작 부분에 마침표(.)를 입력할 수도 있습니다. 예를 들어 `contoso.com` 또는 `.allcontososubdomains.com`을 입력합니다.
  - **DNS 서버**: IP 주소 또는 도메인을 확인하는 DNS 서버를 입력합니다. 예를 들어 `10.0.0.3` 또는 `vpn.contoso.com`을 입력합니다.
  - **프록시**: 도메인을 확인하는 웹 프록시 서버를 입력합니다. 예를 들어 다음과 같이 입력합니다. `http://proxy.com`
  - **자동으로 연결**: **사용**으로 설정하면 디바이스가 입력한 도메인(예: `contoso.com`)에 연결되면 디바이스가 자동으로 VPN에 연결됩니다. **구성되지 않음**(기본값)으로 설정된 경우 디바이스에서 VPN에 자동으로 연결되지 않습니다.
  - **영구**: **사용**으로 설정된 경우 규칙이 디바이스에서 수동으로 제거될 때까지 심지어 VPN 연결이 끊긴 후에도 규칙은 NRPT(이름 확인 정책 테이블)에 유지됩니다. **구성되지 않음**(기본값)으로 설정된 경우 VPN 연결이 끊길 때 VPN 프로필의 NRPT 규칙이 디바이스에서 제거됩니다.

## <a name="proxy-settings"></a>프록시 설정

- **자동 구성 스크립트**: 파일을 사용하여 프록시 서버를 구성합니다. 구성 파일을 포함하는 `http://proxy.contoso.com`과 같은 **프록시 서버 URL**을 입력합니다.
- **주소**: 프록시 서버 주소 입력(예: IP 주소 또는 `vpn.contoso.com`)
- **포트 번호**: 프록시 서버에서 사용하는 TCP 포트 번호 입력
- **로컬 주소에 프록시 서버 사용 안 함**: 로컬 주소에 프록시 서버를 사용하지 않으려면 [사용]을 선택합니다. 이 설정은 VPN 서버에서 연결에 프록시 서버가 필요한 경우, 적용됩니다.

## <a name="split-tunneling"></a>분할 터널링

- **분할 터널링**: 디바이스에서 트래픽에 따라 사용할 연결을 결정할 수 있도록 **사용** 또는 **사용 안 함**으로 설정합니다. 예를 들어 호텔에 있는 사용자는 VPN 연결을 사용하여 작업 파일에 액세스하지만, 일반적인 웹 검색에는 호텔의 표준 네트워크를 사용합니다.
- **이 VPN 연결에 대한 분할 터널링 경로**: 타사 VPN 공급자에 대한 선택적 경로를 추가합니다. 대상 접두사 및 각 연결의 접두사 크기를 입력합니다.

## <a name="trusted-network-detection"></a>신뢰할 수 있는 네트워크 검색

**신뢰할 수 있는 네트워크 DNS 접미사**: 사용자가 이미 신뢰할 수 있는 네트워크에 연결된 경우 디바이스가 자동으로 다른 VPN 연결에 연결하지 못하게 방지할 수 있습니다.

**DNS 접미사**에 신뢰할 수 있는 DNS 접미사(예: contoso.com)을 입력하고 **추가**를 선택합니다. 원하는 만큼 많은 접미사를 추가할 수 있습니다.

사용자가 목록의 DNS 접미사에 연결된 경우 사용자는 자동으로 다른 VPN 연결에 연결되지 않습니다. 사용자는 입력하는 신뢰할 수 있는 DNS 접미사 목록을 계속 사용합니다. 자동 트리거로 설정된 경우에도 신뢰할 수 있는 네트워크를 여전히 사용합니다.

예를 들어 사용자가 이미 신뢰할 수 있는 DNS 접미사에 연결된 경우에는 다음의 자동 트리거를 무시합니다. 특히 목록의 DNS 접미사는 다음을 포함하여 기타 모든 연결 자동 트리거를 취소합니다.

- Always On
- 앱 기반 트리거
- DNS 자동 트리거

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 그럼 다음, [프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Android](vpn-settings-android.md), [iOS](vpn-settings-ios.md) 및 [macOS](vpn-settings-macos.md) 디바이스에서 VPN 설정을 구성합니다.
