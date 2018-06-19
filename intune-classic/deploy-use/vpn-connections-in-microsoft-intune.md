---
title: VPN 연결
description: VPN 프로필을 사용하여 조직의 사용자 및 장치에 VPN 설정을 배포합니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: angrobe
ms.date: 05/15/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: abc57093-7351-408f-9f41-a30877f96f73
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 104bab7575a683d0cbe6e553c54f42dd3a88e133
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31030108"
---
# <a name="vpn-connections-in-microsoft-intune"></a>Microsoft Intune에서 VPN 연결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

VPN(가상 사설망)을 사용하면 사용자가 회사 네트워크에 안전하게 원격으로 액세스할 수 있습니다. 장치는 *VPN 연결 프로필*을 사용하여 VPN 서버와의 연결을 시작합니다. Microsoft Intune의 *VPN 프로필*을 사용하여 조직의 사용자 및 장치에 VPN 설정을 배포하면 네트워크에 쉽고 안전하게 연결할 수 있습니다.

예를 들어 기업 네트워크에서 파일 공유에 연결하는 데 필요한 설정을 사용하여 모든 iOS 장치를 프로비전하려고 할 수 있습니다. 회사 네트워크에 연결하는 데 필요한 설정이 포함된 VPN 프로필을 만들어 iOS 장치를 이용하는 모든 사용자에게 배포합니다. 사용자에게 이용 가능한 네트워크 목록에 대한 VPN 연결이 표시되어 최소한의 노력으로 연결할 수 있습니다.

VPN 프로필을 사용하여 다음의 장치 유형을 구성할 수 있습니다.

* Android 4 이상을 실행하는 장치
* Android for Work 장치
* iOS 8.0 이상을 실행하는 장치
* Mac OS X 10.9 이상을 실행하는 장치
* Windows 8.1 이상을 실행하는 등록된 장치
* Windows Phone 8.1 이상을 실행하는 장치
* Windows 10 Desktop 및 Mobile을 실행하는 장치

VPN 프로필 구성 옵션은 선택하는 장치 유형에 따라 다릅니다.

## <a name="vpn-connection-types"></a>VPN 연결 형식

Intune에서는 다음의 연결 유형을 사용하는 VPN 프로필 만들기를 지원합니다.


연결 형식 |iOS 및 Mac OS X  |Android 및 Android for Work|Windows 8.1|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop 및 Mobile |
----------------|------------------|-------|-----------|----------|--------------|-----------------|----------------------|
Cisco AnyConnect|예 |예   |아니요    |아니요  |아니요    | 예(OMA-URI, Mobile만)|     
Cisco(IPsec)|예 |예   |아니요  |아니요  |아니요 | 아니요|
Citrix|예 |예(Android에만 해당)   |아니요  |아니요  |아니요 | 아니요|
Pulse Secure|예  |예 |예   |예  |예| 예|        
F5 Edge Client|예 |예 |예 |예  |   예 |  예|   
SonicWall Mobile Connect|예 |예 |예 |예 |예 |예|         
CheckPoint Mobile VPN|예 |예 |예 |예|예|예|
Microsoft SSL(SSTP)|아니요 |아니요 |아니요 |아니요|아니요|VPNv1 OMA-URI*|
Microsoft 자동|아니요 |아니요 |아니요 |아니요|예(OMA-URI)|예|
IKEv2|iOS 사용자 지정 프로필|아니요 |아니요 |아니요|예(OMA-URI)|예|
PPTP|iOS 사용자 지정 프로필|아니요 |아니요 |아니요|아니요|예|
L2TP|iOS 사용자 지정 프로필|아니요 |아니요 |아니요|예(OMA-URI)|예|

\* Windows 10에 사용할 수 있는 추가 설정이 없습니다.

> [!IMPORTANT]
> 장치에 배포된 VPN 프로필을 사용하려면 프로필에 적용 가능한 VPN 앱을 설치해야 합니다. [Microsoft Intune에서 앱 배포](deploy-apps-in-microsoft-intune.md) 항목의 정보를 참조하여 Intune을 사용해 해당 앱을 배포할 수 있습니다.  

 URI 설정을 사용하여 사용자 지정 VPN 프로필을 만드는 방법에 대해 알아보려면 [VPN 프로필에 대한 사용자 지정 구성](create-custom-vpn-profiles.md)을 참조하세요.     

## <a name="methods-of-securing-vpn-profiles"></a>VPN 프로필을 보호하는 방법

VPN 프로필에서는 다른 제조업체의 다양한 연결 형식과 프로토콜을 사용할 수 있습니다. 이러한 연결은 일반적으로 다음의 두 가지 방법 중 하나를 사용하여 보안이 유지됩니다.

### <a name="certificates"></a>인증서

VPN 프로필을 만들 때 이전에 Intune에서 만든 SCEP 또는 .PFX 인증서 프로필을 선택합니다. ID 인증서라고 합니다. 사용자 장치의 연결 허용을 설정하기 위해 만든 신뢰할 수 있는 인증서 프로필(또는 *루트 인증서*)에 대해 인증하는 데 사용됩니다. 신뢰할 수 있는 인증서는 VPN 연결을 인증하는 컴퓨터(대개 VPN 서버)에 배포됩니다.

Intune에서 인증서 프로필을 만들고 사용하는 방법에 대한 자세한 내용은 [인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요.

### <a name="user-name-and-password"></a>사용자 이름 및 암호

사용자는 사용자 이름과 암호를 제공하여 VPN 서버에 인증합니다.

## <a name="create-a-vpn-profile"></a>VPN 프로필 만들기

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **정책 추가**를 선택합니다.
2. 관련 장치 종류를 확장하여 새 정책에 대한 템플릿을 선택한 다음 해당 장치에 대한 VPN 프로필을 선택합니다.
    * **VPN 프로필(Android 4 이상)**
    * **VPN 프로필(Android for Work)**
    * **VPN 프로필(iOS 8.0 이상)**
    * **VPN 프로필(Mac OS X 10.9 이상)**
    * **VPN 프로필(Windows 8.1 이상)**
    * **VPN 프로필(Windows Phone 8.1 이상)**
    * **VPN 프로필(Windows 10 Desktop 및 Mobile 이상)**

   사용자 지정 VPN 프로필 정책만 만들고 배포할 수 있습니다. 권장 설정은 사용할 수 없습니다.

> [!Note]
> Android for Work 장치용 VPN 프로필에서는 장치의 업무용 프로필에 설치된 앱만 VPN 연결을 사용하도록 설정합니다.
>
> 일부 VPN 연결 유형은Android for Work 장치에 대해 앱당 VPN을 지원하고, Intune을 통해 배포된 앱에서 앱당 VPN을 사용하도록 설정할 수 있도록 합니다.  

3. 다음 테이블을 사용하여 VPN 프로필 설정을 쉽게 구성할 수 있습니다.

|                                                    설정 이름                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                  추가 정보                                                                                                                                                                                                                                                                                                                                                                                                                   |
|---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                <strong>Name</strong>                                                |                                                                                                                                                                                                                                                                                                                                                                               Intune 콘솔에서 쉽게 식별할 수 있도록 VPN 프로필에 대한 고유한 이름을 입력합니다.                                                                                                                                                                                                                                                                                                                                                                                |
|                                            <strong>설명</strong>                                             |                                                                                                                                                                                                                                                                                                                                                             VPN 프로필의 개요에 대한 설명과 찾을 때 도움이 되는 기타 관련 정보를 제공합니다.                                                                                                                                                                                                                                                                                                                                                             |
|                              <strong>VPN 연결 이름(사용자에게 표시)</strong>                              |                                                                                                                                                                                                                                                                                                                                                         VPN 프로필의 이름을 지정합니다. 사용자는 장치의 사용 가능한 VPN 연결 목록에서 이 이름을 볼 수 있습니다.                                                                                                                                                                                                                                                                                                                                                         |
|                                          <strong>연결 형식</strong>                                           |                                                                                                                                                                                                                                                     VPN 프로필에서 사용할 연결 형식으로 다음 중 하나를 선택합니다. <strong>Cisco AnyConnect</strong>(Windows 8.1 또는 Windows Phone 8.1에 대해 사용할 수 없음), <strong>Pulse Secure</strong>, <strong>Citrix</strong>, <strong>F5 Edge Client</strong>, <strong>SonicWall Mobile Connect</strong>, <strong>CheckPoint Mobile VPN</strong>.                                                                                                                                                                                                                                                     |
|                                       <strong>VPN 서버 설명</strong>                                       |                                                                                                                                                                                                                                                                               장치가 연결될 VPN 서버에 대한 설명을 지정합니다. 예: <strong>Contoso VPN 서버</strong>. 연결 형식이 <strong>F5 Edge Client</strong>인 경우 <strong>서버 목록</strong> 필드를 사용하여 서버 설명 및 IP 주소 목록을 지정합니다.                                                                                                                                                                                                                                                                               |
|                                     <strong>서버 IP 주소 또는 FQDN</strong>                                      |                                                                                                                                                                                                                                                 장치를 연결할 VPN 서버의 정규화된 도메인 이름 또는 IP 주소를 입력합니다. 예: <strong>192.168.1.1</strong>, <strong>vpn.contoso.com</strong>.  연결 형식이 <strong>F5 Edge Client</strong>인 경우 <strong>서버 목록</strong> 필드를 사용하여 서버 설명 및 IP 주소 목록을 지정합니다.                                                                                                                                                                                                                                                 |
|                                            <strong>서버 목록</strong>                                             |                                                                                                                                                                                                                                                                                           <strong>추가</strong>를 선택하여 VPN 연결에 사용할 새 VPN 서버를 추가합니다. 또한 연결에 대한 기본 서버를 지정할 수도 있습니다. 연결 형식이 <strong>F5 Edge Client</strong>인 경우에만 이 옵션이 표시됩니다.                                                                                                                                                                                                                                                                                            |
|                        <strong>VPN 연결을 통해 모든 네트워크 트래픽 보내기</strong>                         |                                                                                                                                                                                                                                이 옵션을 선택하는 경우 모든 네트워크 트래픽이 VPN 연결을 통해 보내집니다. 이 옵션을 선택하지 않으면 클라이언트에서 타사 VPN 서버에 연결할 때 분할 터널링용 라우트를 동적으로 협상합니다. 회사 네트워크에 대한 연결만 VPN 터널을 통해 보내집니다. VPN 터널링은 인터넷에 있는 리소스에 연결할 경우에는 사용되지 않습니다.                                                                                                                                                                                                                                |
|                                       <strong>인증 방법</strong>                                        |                                                                                                                                                                                                                                                         VPN 연결에서 사용되는 인증 방법(<strong>인증서</strong> 또는 <strong>사용자 이름 및 암호</strong>)을 선택합니다. (연결 형식이 Cisco AnyConnect인 경우에는 <strong>사용자 이름 및 암호</strong>를 사용할 수 없습니다.) Windows 8.1의 경우 <strong>인증 방법</strong> 옵션을 사용할 수 없습니다.                                                                                                                                                                                                                                                         |
|                            <strong>로그온 할 때마다 사용자 자격 증명 기억</strong>                             |                                                                                                                                                                                                                                                                                                                                          연결을 설정할 때마다 사용자가 자격 증명을 입력하지 않아도 되도록 사용자 자격 증명을 저장하려면 이 옵션을 선택합니다.                                                                                                                                                                                                                                                                                                                                           |
|            <strong>클라이언트 인증을 위해 클라이언트 인증서 선택(ID 인증서)</strong>            |                                                                                                                                                                                                                     이전에 만든 클라이언트 SCEP 인증서를 선택합니다. VPN 연결을 인증하는 데 사용됩니다. Intune에서 인증서 프로필을 사용하는 방법에 대한 자세한 내용은 [인증서 프로필을 통해 리소스 액세스 보안](secure-resource-access-with-certificate-profiles.md)을 참조하세요. 인증 방법이 <strong>인증서</strong>인 경우에만 이 옵션이 표시됩니다.                                                                                                                                                                                                                      |
|                                                <strong>역할</strong>                                                |                                                                                                                                                                                                                                                                          이 연결에 대한 액세스 권한이 있는 사용자 역할의 이름을 지정합니다. 사용자 역할은 개인 설정과 옵션을 정의하고, 특정 액세스 기능을 사용 또는 사용하지 않도록 설정합니다. 연결 형식이 <strong>Pulse Secure</strong> 또는 <strong>Citrix</strong>인 경우에만 이 옵션이 표시됩니다.                                                                                                                                                                                                                                                                           |
|                                               <strong>영역</strong>                                                |                                                                                                                                                                                                                                                                   사용하려는 인증 영역의 이름을 지정합니다. 인증 영역은 Pulse Secure 또는 Citrix 연결 형식에서 사용하는 인증 리소스 그룹입니다. 연결 형식이 <strong>Pulse Secure</strong> 또는 <strong>Citrix</strong>인 경우에만 이 옵션이 표시됩니다.                                                                                                                                                                                                                                                                    |
|                                       <strong>로그인 그룹 또는 도메인</strong>                                        |                                                                                                                                                                                                                                                                                                                                   연결하려는 로그인 그룹 또는 도메인의 이름을 지정합니다. 연결 형식이 <strong>SonicWall Mobile Connect</strong>인 경우에만 이 옵션이 표시됩니다.                                                                                                                                                                                                                                                                                                                                   |
|                                            <strong>지문</strong>                                             |                                                                                                                 신뢰할 수 있는 VPN 서버를 확인하는 데 사용할 문자열(예: 'Contoso 지문 코드')을 지정합니다. 연결 시 동일한 지문을 제시하는 서버가 신뢰할 수 있는지 알 수 있도록 클라이언트에 지문을 보낼 수 있습니다. 장치에 지문이 아직 없으면, 사용자에게 지문을 보여주면서 연결하려는 VPN 서버를 신뢰할 것인지 묻는 메시지가 표시됩니다. 사용자는 지문을 수동으로 확인한 후 연결할 <strong>신뢰</strong>를 선택합니다. 연결 형식이 <strong>CheckPoint Mobile VPN</strong>인 경우에만 이 옵션이 표시됩니다.                                                                                                                 |
|                                            <strong>앱별 VPN</strong>                                             |                                                                                                                                                                                                                                                         앱이 실행될 때 연결이 열리도록 이 VPN 연결을 iOS 또는 Mac OS X 앱과 연결하려면 이 옵션을 선택합니다. 소프트웨어를 배포할 때 VPN 프로필을 앱과 연결할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 앱 배포](deploy-apps-in-microsoft-intune.md) 항목을 참조하세요.                                                                                                                                                                                                                                                         |
|                                           <strong>요청 시 VPN</strong>                                            |                                                                                                                                                                                                                                                                                                                                    iOS 8.0 이상 장치에 대해 필요 시 VPN을 설정할 수 있습니다. 이를 설정하는 방법에 대한 지침은 [iOS 장치에 대한 필요 시 VPN](#on-demand-vpn-for-ios-devices)에 제공됩니다.                                                                                                                                                                                                                                                                                                                                    |
|    <strong>프록시 설정 자동 검색</strong>(iOS, Mac OS X, Windows 8.1 및 Windows Phone 8.1에만 해당)    |                                                                                                                                                                                                                                                                                                                    VPN 서버에 연결을 위한 프록시 서버가 필요한 경우 장치가 연결 설정을 자동으로 검색할지 여부를 지정합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.                                                                                                                                                                                                                                                                                                                    |
|    <strong>자동 구성 스크립트 사용</strong>(iOS, Mac OS X, Windows 8.1 및 Windows Phone 8.1에만 해당)     |                                                                                                                                                                                                                                                                                VPN 서버에 연결을 위한 프록시 서버가 필요한 경우 설정을 정의하기 위해 자동 구성 스크립트를 사용할지 여부를 지정한 다음 설정이 포함된 파일에 대한 URL을 지정합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.                                                                                                                                                                                                                                                                                 |
|             <strong>프록시 서버 사용</strong>(iOS, Mac OS X, Windows 8.1 및 Windows Phone 8.1에만 해당)              |                                                                                                                                                                                                                                                                                                                  VPN 서버에 연결을 위한 프록시 서버가 필요한 경우 이 옵션을 선택한 다음 프록시 서버의 주소 및 포트 번호를 지정합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.                                                                                                                                                                                                                                                                                                                  |
| <strong>로컬 주소에 대해 프록시 설정 사용 안 함</strong>(iOS, Mac OS X, Windows 8.1 및 Windows Phone 8.1에만 해당) |                                                                                                                                                                                                                                                                                                           VPN 서버에 연결을 위한 프록시 서버가 필요한 경우 지정하는 로컬 주소에 대해 프록시 서버를 사용하지 않으려면 이 옵션을 선택합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.                                                                                                                                                                                                                                                                                                           |
|                <strong>사용자 지정 XML</strong>(Windows 8.1 이상 및 Windows Phone 8.1 이상에만 해당)                 | VPN 연결을 구성하는 사용자 지정 XML 명령을 지정합니다. <strong>Pulse Secure</strong>의 예: &lt;pulse-schema&gt;&lt;isSingleSignOnCredential&gt;true&lt;/isSingleSignOnCredential&gt;&lt;/pulse-schema&gt;. <strong>CheckPoint Mobile VPN</strong>의 예: &lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true"  debug="3" /&gt;. <strong>SonicWall Mobile Connect</strong>의 예: &lt;MobileConnect&gt;&lt;Compression&gt;false&lt;/Compression&gt;&lt;debugLogging&gt;True&lt;/debugLogging&gt;&lt;packetCapture&gt;False&lt;/packetCapture&gt;&lt;/MobileConnect&gt;. <strong>F5 Edge Client</strong>의 예: &lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;. 사용자 지정 XML 명령을 작성하는 방법에 대한 자세한 내용은 각 제조업체의 VPN 설명서를 참조하세요. |
|                          <strong>DNS 접미사 검색 목록</strong>(Windows Phone 8.1에만 해당)                           |                                                                                                                                                                                        각 줄에 하나의 DNS 접미사를 지정합니다. 지정하는 각 DNS 접미사는 짧은 이름을 사용하여 웹 사이트에 연결할 때 검색됩니다. 예를 들어 DNS 접미사 <strong>domain1.contoso.com</strong> 및 <strong>domain2.contoso.com</strong>을 지정하고, URL <strong><http://mywebsite></strong>로 이동하고, <strong><http://mywebsite.domain1.contoso.com></strong> 및 <strong><http://mywebsite.domain2.contoso.com></strong>이라는 URL을 검색합니다.                                                                                                                                                                                        |
|            <strong>회사 Wi-Fi 네트워크에 연결된 경우 VPN 사용 안 함</strong>(Windows Phone 8.1에만 해당)             |                                                                                                                                                                                                                                                                                                                                                          장치가 회사 Wi-Fi 네트워크에 연결된 경우 VPN 연결을 사용하지 않도록 지정하려면 이 옵션을 선택합니다.                                                                                                                                                                                                                                                                                                                                                          |
|              <strong>가정용 Wi-Fi 네트워크에 연결된 경우 VPN 사용 안 함</strong>(Windows Phone 8.1에만 해당)              |                                                                                                                                                                                                                                                                                                                                                            장치가 가정용 Wi-Fi 네트워크에 연결된 경우 VPN 연결을 사용하지 않도록 지정하려면 이 옵션을 선택합니다.                                                                                                                                                                                                                                                                                                                                                             |

Windows 10 Desktop 및 Mobile 장치에는 다음과 같은 추가 설정을 사용할 수 있습니다.


|              설정 이름              |                                                                                                                                                                     추가 정보                                                                                                                                                                     |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>네트워크 트래픽 규칙</strong> | VPN 연결을 위해 사용할 프로토콜, 로컬/원격 포트와 주소 범위를 선택합니다. 네트워크 트래픽 규칙을 만들지 않으면 모든 프로토콜, 포트 및 주소 범위를 사용할 수 있습니다. 규칙을 만들고 나면 해당 규칙에 지정하는 프로토콜, 포트 및 주소 범위만 VPN 연결에 사용됩니다. |
|        <strong>경로</strong>         |                                                                                                                                                     VPN 연결을 사용할 경로를 선택합니다.                                                                                                                                                     |
|      <strong>DNS 서버</strong>      |                                                                                                                                연결이 설정된 후 VPN 연결에 사용할 DNS 서버를 선택합니다.                                                                                                                                 |
|    <strong>연결된 앱</strong>    |                                                           자동으로 VPN 연결을 사용하는 앱 목록을 제공합니다. 앱의 유형에 따라 앱 식별자가 결정됩니다. 유니버설 앱의 경우 패키지 패밀리 이름을 제공합니다. 데스크톱 앱의 경우에는 앱의 파일 경로를 제공합니다.                                                           |

> [!IMPORTANT]
> 앱별 VPN의 구성에서 사용하기 위해 컴파일하는 앱의 모든 목록을 보호하는 것이 좋습니다. 권한이 없는 사용자가 목록을 수정한 경우 해당 목록을 앱별 VPN 앱 목록으로 가져오는 경우 액세스 권한이 부여되면 안 되는 앱에 VPN 액세스 권한을 잠재적으로 부여하게 됩니다. 앱 목록을 보호할 수 있는 한 가지 방법은 ACL(액세스 제어 목록)을 사용하는 것입니다.

회사 경계 설정을 사용할 수 있는 경우의 예로, 원격 데스크톱에 대해서만 VPN을 사용하려는 경우를 들 수 있습니다. 이렇게 하려면 외부 포트 3996에서 프로토콜 27에 대한 트래픽을 허용하는 네트워크 트래픽 규칙을 만듭니다. 그러면 다른 트래픽은 VPN을 사용하지 않습니다.

분할 터널링의 트래픽을 처리하는 방법을 정의할 수 없는 VPN 연결 형식을 사용할 때 회사 경계에서 경로를 정의하면 유용합니다. 이 경우에는 **경로**를 사용하여 VPN을 사용할 경로를 나열합니다.

사용자 지정 OMA-URI 설정을 만들어 Windows 10 장치의 VPN 사용을 특정 앱으로 제한할 수 있습니다.

새 정책이 **정책** 작업 영역의 **구성 정책** 노드에 표시됩니다.

### <a name="on-demand-vpn-for-ios-devices"></a>iOS 장치에 대한 필요 시 VPN
iOS 8.0 이상 장치에 대해 필요 시 VPN을 구성할 수 있습니다.

> [!NOTE]
>  
> 앱당 VPN과 필요 시 VPN을 동일한 정책에 사용할 수 없습니다.

1. 정책 구성 페이지에서 **이 VPN 연결에 대한 주문형 규칙**을 찾습니다. 열의 레이블은 규칙에서 확인하는 조건인 **일치**와 조건이 일치할 경우 정책에서 트리거하는 작업인 **작업**입니다.
2. **추가**를 선택하여 규칙을 만듭니다. 규칙에서 설정할 수 있는 일치 유형은 두 가지입니다. 규칙당 이러한 유형 중 하나만 구성할 수 있습니다.
   - **SSID** - 무선 네트워크를 나타냅니다.
   - **DNS 검색 도메인** - 정규화된 도메인 이름(예: *team. corp.contoso.com*)을 사용하거나 도메인(예: *contoso.com*)을 사용할 수 있습니다(* *.contoso.com*을 사용하는 것과 동일).
3. 선택 사항: 규칙에서 테스트로 사용하는 URL인 URL 문자열 프로브를 제공합니다. 이 프로필이 설치된 장치에서 리디렉션 없이 이 URL에 액세스할 수 있는 경우 VPN이 설정되고 장치가 대상 URL에 연결됩니다. 사용자에게 URL 문자열 프로브 사이트가 표시되지 않습니다. URL 문자열 프로브의 예는 VPN을 연결하기 전에 장치 준수를 확인하는 감사 웹 서버의 주소입니다. 또한 VPN 통해 장치를 대상 URL에 연결하기 전에 URL에서 VPN이 사이트에 연결할 수 있는지 테스트할 수도 있습니다.
4. 다음 작업 중 하나를 선택합니다.
   - **연결**
   - **연결 평가** - 세 가지 설정이 있습니다. **도메인 작업** - **필요한 경우 연결** 또는 **연결 안 함**을 선택합니다. b. **쉼표로 구분된 도메인 목록** - **도메인 작업**을 **필요한 경우 연결**로 선택한 경우에만 이 설정을 구성합니다. c. **필요한 URL 문자열 프로브** - HTTP 또는 HTTPS(기본 설정) URL(예: *https://vpntestprobe.contoso.com*). 규칙에서는 이 주소에서 받은 응답이 있는지 확인합니다. 응답이 없고 **도메인 작업**이 **필요한 경우 연결**이면 VPN이 트리거됩니다.
      
     > [!TIP]
     >
     >예를 들어 회사 네트워크의 일부 사이트에 직접 또는 VPN 회사 네트워크 연결이 필요하지만 다른 사이트에는 필요하지 않은 경우 이 작업을 사용할 수 있습니다. **DNS 검색 도메인 목록**에 *corp.contoso.com*을 나열하는 경우 **필요한 경우 연결**을 선택한 다음 해당 네트워크 내에서 VPN이 필요할 수 있는 특정 사이트(예: *sharepoint.corp.contoso.com*)를 나열할 수 있습니다. 그러면 규칙에서 *vpntestprobe.contoso.com*에 연결할 수 있는지 확인합니다. 연결할 수 없으면 sharepoint 사이트에 대해 VPN이 트리거됩니다.
   - **무시** - 이 작업을 선택해도 VPN 연결에는 아무 변화가 없습니다. VPN이 연결되면 연결된 채로 두고 연결되지 않으면 연결하지 마세요. 예를 들어 모든 내부 회사 웹 사이트에 대해 VPN을 연결하는 규칙이 있을 수 있지만 장치가 실제로 기업 네트워크에 연결된 경우에만 이러한 내부 사이트 중 하나에 액세스할 수 있도록 하고 싶을 수도 있습니다. 이 경우 해당하는 하나의 사이트에 대해 무시 규칙을 만들 수 있습니다.
   - **연결 끊기** - 조건이 일치하면 장치와 VPN 연결을 끊습니다. 예를 들어 **SSID** 필드에 회사 무선 네트워크를 나열하고 장치가 이러한 네트워크 중 하나에 연결하는 경우 장치와 VPN 연결을 끊는 규칙을 만들 수 있습니다.

도메인 특정 규칙은 전체 도메인 규칙보다 먼저 평가됩니다.


## <a name="deploy-the-policy"></a>정책 배포

1.  **정책** 작업 영역에서 배포할 정책을 선택한 다음 **배포 관리**를 선택합니다.

2.  **배포 관리** 대화 상자에서

    -   정책을 배포하려면 정책을 배포하려는 그룹을 하나 이상 선택하고 **추가** &gt; **확인**을 선택합니다.

    -   정책을 배포하지 않고 대화 상자를 닫으려면 **취소**를 선택합니다.


배포 후 사용자는 장치의 VPN 연결 목록에서 지정된 VPN 연결 이름을 볼 수 있습니다.

**정책** 작업 영역의 **개요** 페이지에 있는 상태 요약 및 경고는 주의가 필요한 정책 문제를 식별합니다. 또한 상태 요약은 대시보드 작업 영역에 표시됩니다.
