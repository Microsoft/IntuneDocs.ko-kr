---
title: Microsoft Intune VPN 프로필에 대한 사용자 지정 구성
description: 사용자 지정 구성을 사용하여 Intune에서 VPN 프로필을 만듭니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4c0bd439-3b58-420b-9a9a-282886986786
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 512bd38802dbb97a74d3d19d74a7d5086784d327
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018756"
---
# <a name="custom-configurations-for-microsoft-intune-vpn-profiles"></a>Microsoft Intune VPN 프로필에 대한 사용자 지정 구성

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="create-a-custom-configuration"></a>사용자 지정 구성 만들기
사용자 지정 구성 정책을 사용하여 다음에 대한 VPN 프로필을 만들 수 있습니다.

* Android 4 이상을 실행하는 장치
* Android for Work 장치
* Windows 8.1 이상을 실행하는 등록된 장치
* Windows Phone 8.1 이상을 실행하는 장치
* Windows 10 데스크톱 이상을 실행하는 등록된 장치
* Windows 10 Mobile을 실행하는 장치

표준 Intune VPN 정책에 사용하려는 설정이 없는 경우 이 유형의 정책이 유용할 수 있습니다.

## <a name="to-create-a-custom-configuration-policy"></a>사용자 지정 구성 정책을 만들려면

1. [Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **정책 추가** > *플랫폼 확장* > **사용자 지정 구성** > **정책 만들기**를 선택합니다.
2. 정책의 이름을 입력합니다.
3. 지정하려는 각 URI 설정에 대해 **추가**를 선택하고 요청된 정보를 제공합니다. 아래 예를 살펴보세요.

   ![VPN 프로필 사용자 지정 구성 대화 상자](./media/Intune_Add_VPN_URI.png)

4. URI 설정을 모두 입력한 후에 **정책 저장**을 선택한 다음 정책을 배포합니다.

그런 다음 일반적인 방식으로 [정책을 배포](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#deploy-a-configuration-policy)합니다.

## <a name="example-uri-settings"></a>URI 설정 예

이러한 설정은 Contoso라는 가상의 회사에서 VPN에 대한 사용자 지정 구성을 만드는 데 사용할 수 있습니다.
사용할 수 있는 모든 설정이 대한 자세한 내용은 [VPNv2 CSP](https://msdn.microsoft.com/library/windows/hardware/dn914776.aspx)를 참조하세요.

**네이티브 Contoso VPN(IKEv2):**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Servers

**vpn.contoso.com**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/NativeProtocolType

**Ikev2<br />** ./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/RoutingPolicyType

**SplitTunnel**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/UserMethod

**Eap**<br />
./Vendor/MSFT/VPNv2/ContosoVPN/NativeProfile/Authentication/Eap/Configuration
``` xml
<EapHostConfig xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
   <EapMethod>
      <Type xmlns="http://www.microsoft.com/provisioning/EapCommon">13</Type>
      <VendorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorId>
      <VendorType xmlns="http://www.microsoft.com/provisioning/EapCommon">0</VendorType>
      <AuthorId xmlns="http://www.microsoft.com/provisioning/EapCommon">0</AuthorId>
   </EapMethod>
   <Config xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
      <Eap xmlns="http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1">
         <Type>13</Type>
         <EapType xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1">
            <CredentialsSource>
               <CertificateStore>
                  <SimpleCertSelection>true</SimpleCertSelection>
               </CertificateStore>
            </CredentialsSource>
            <ServerValidation>
               <DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation>
               <ServerNames></ServerNames>
            </ServerValidation>
            <DifferentUsername>false</DifferentUsername>
            <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </PerformServerValidation>
            <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
               false
            </AcceptServerName>
         </EapType>
      </Eap>
   </Config>
</EapHostConfig>
```
**./Vendor/MSFT/VPNv2/ContosoVPN/ByPassForLocal**<br />
True

**./Vendor/MSFT/VPNv2/ContosoVPN/RememberCredentials**<br />
1

**./Vendor/MSFT/VPNv2/ContosoVPN/DomainNameInformationList/1/DomainName**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/DnsSuffix**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/TrustedNetworkDetection**<br />
Corp.Contoso.com

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/Address**<br />
10.0.0.0

**./Vendor/MSFT/VPNv2/ContosoVPN/RouteList/1/PrefixSize**<br />
8

**./Vendor/MSFT/VPNv2/ContosoVPN/AlwaysOn**<br />
true

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/0/App/Id**<br />
%PROGRAMFILES%\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/1/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/AppTriggerList/2/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/0/App/Id**<br />
%PROGRAMFILES% (x86)\Internet Explorer\iexplore.exe

**./Vendor/MSFT/VPNv2/ContosoVPN/TrafficFilterList/1/App/Id**<br />
Microsoft.MicrosoftEdge_8wekyb3d8bbwe

이러한 설정을 어떻게 사용해야 할지에 대한 질문 또는 수행 작업에 대한 자세한 내용을 확인하려면 고객은 [CSP(구성 서비스 공급자) 설명서](https://msdn.microsoft.com/library/windows/hardware/dn914776(v=vs.85).aspx)를 참조해야 합니다.

## <a name="uri-settings-for-android-per-app-vpn-on-pulsesecure"></a>PulseSecure에서 Android 앱별 VPN에 대한 URI 설정
### <a name="custom-uri-for-package-list"></a>패키지 목록에 대한 사용자 지정 URI
-  데이터 형식 = 문자열
-  OMA-URI = ./Vendor/MSFT/VPN/Profile/Name/PackageList
-  값 = 구분 기호로 구분된 패키지 목록.
   - 구분 기호: 세미콜론(;), 콜론(:), 쉼표(,), 파이프(|)

예:
- com.android.chrome
- com.android.chrome;com.android.browser

### <a name="custom-uri-for-mode-optional"></a>모드에 대한 사용자 지정 URI(선택 사항)
- 데이터 형식 = 문자열
- OMA-URI = ./Vendor/MSFT/VPN/Profile/NAME/Mode

> 참고
> - 사용자 지정 프로필에 할당한 동일한 *이름* 사용
> - 가능한 값: *전역*, *화이트 리스트*, *블랙 리스트*
> - PackageList를 제공하지 않는 경우 *전역*에 대한 기본값(시스템 차원의 프로필이 있는 이전 버전과 호환성)
> - PackageList에서 제공하는 경우 *화이트 리스트*에 대한 기본값


### <a name="see-also"></a>참고 항목
[Microsoft Intune에서 VPN 연결](vpn-connections-in-microsoft-intune.md)
