---
title: Microsoft Intune에서 미리 공유한 키를 사용하여 WiFi 프로필 만들기 - Azure | Microsoft Docs
description: 사용자 지정 프로필을 사용하여 미리 공유한 키로 Wi-Fi 프로필을 만들고, Microsoft Intune에서 Android, Windows 및 EAP 기반 Wi-Ri 프로필에 대한 샘플 XML 코드를 가져옵니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c6fd72a6-7dc8-48fc-9df1-db5627a51597
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f7f888a5a384503393c086a27d1c2ce6410357fd
ms.sourcegitcommit: 1a7f04c80548e035be82308d2618492f6542d3c0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73755031"
---
# <a name="use-a-custom-device-profile-to-create-a-wifi-profile-with-a-pre-shared-key-in-intune"></a>Intune에서 사용자 지정 디바이스 프로필을 사용하여 미리 공유한 키로 WiFi 프로필 만들기

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

일반적으로 PSK(미리 공유한 키)를 사용하여 WiFi 네트워크 또는 무선 LAN에서 사용자를 인증합니다. Intune에서 미리 공유한 키를 사용하여 Wi-Fi 프로필을 만들 수 있습니다. 프로필을 만들려면 Intune 내에서 **사용자 지정 디바이스 프로필** 기능을 사용합니다. 이 아티클에는 EAP 기반 Wi-Fi 프로필을 만드는 방법에 대한 예제가 포함됩니다.

이 기능은 다음을 지원합니다.

- Android
- Windows
- EAP 기반 Wi-Fi

> [!IMPORTANT]
> - Windows 10에서 미리 공유한 키를 사용하면 Intune에서 나타나는 업데이트 관리 오류가 발생합니다. 이런 경우 Wi-Fi 프로필은 디바이스에 제대로 할당되고 프로필은 예상대로 작동합니다.
> - 미리 공유한 키를 포함하는 Wi-Fi 프로필을 내보내는 경우 파일이 보호되도록 합니다. 키가 일반 텍스트인 경우 키를 보호하는 것은 사용자의 책임입니다.

## <a name="before-you-begin"></a>시작하기 전에

- 나중에 이 아티클에서 설명한 대로 해당 네트워크에 연결된 컴퓨터에서 코드를 쉽게 복사할 수 있습니다.
- 더 많은 OMA-URI 설정을 추가하여 여러 네트워크와 키를 추가할 수 있습니다.
- iOS의 경우 Mac 스테이션의 Apple Configurator를 사용하여 프로필을 설정합니다.
- PSK는 64자리 16진수 문자열 또는 인쇄 가능한 8~63자의 ASCII 문자를 요구합니다. 별표(*) 등의 일부 문자는 지원되지 않습니다.

## <a name="create-a-custom-profile"></a>사용자 지정 프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 정책에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 예를 들어 **Android 디바이스에 대한 사용자 지정 OMA-URI Wi-Fi 프로필 설정**이 적절한 정책 이름일 수 있습니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 플랫폼을 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **설정**에서 **추가**를 선택합니다. 다음 속성의 새 OMA-URI 설정을 입력합니다.

    1. **이름**: OMA-URI 설정의 이름을 입력합니다.
    2. **설명**: OMA-URI 설정에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    3. **OMA URI** 다음 옵션 중 하나를 입력합니다.

        - **Android의 경우**: `./Vendor/MSFT/WiFi/Profile/SSID/Settings`
        - **Windows의 경우**: `./Vendor/MSFT/WiFi/Profile/SSID/WlanXml`

        > [!NOTE]
        > 시작 부분에 점 문자를 포함해야 합니다.

        SSID는 정책을 만들고 있는 SSID입니다. 예를 들어 Wi-Fi 이름이 `Hotspot-1`인 경우 `./Vendor/MSFT/WiFi/Profile/Hotspot-1/Settings`을 입력합니다.

    4. **데이터 형식**: **문자열**을 선택합니다.

    5. **값**: XML 코드를 붙여 넣습니다. 이 문서의 [예제](#android-or-windows-wi-fi-profile-example)를 참조하세요. 네트워크 설정에 맞게 각 값을 업데이트합니다. 코드의 주석 섹션에는 일부 포인터가 포함됩니다.

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 프로필 목록에 표시됩니다. 그런 다음, 사용자 그룹에 [이 프로필을 할당](../device-profile-assign.md)합니다. 이 정책은 사용자 그룹에만 할당할 수 있습니다.

다음에 각 디바이스가 체크인되면 정책이 적용되고 해당 디바이스에 Wi-Fi 프로필이 만들어집니다. 디바이스는 네트워크에 자동으로 연결될 수 있습니다.

## <a name="android-or-windows-wi-fi-profile-example"></a>Android 또는 Windows Wi-Fi 프로필 예제

다음 예제에는 Android 또는 Windows Wi-Fi 프로필의 XML 코드가 포함됩니다. 이 예제는 적절한 형식을 표시하고 자세한 내용을 제공하기 위해 제공된 것입니다. 이는 예시일 뿐이며, 사용자 환경에 대한 권장 구성으로 제공된 것은 아닙니다.

### <a name="what-you-need-to-know"></a>기억해야 하는 사항

- `<protected>false</protected>`는 **false**로 설정해야 합니다. **true**로 설정하면 디바이스가 암호화된 암호를 요구한 다음, 암호를 해독하려 할 수 있습니다. 이로 인해 연결에 실패할 수 있습니다.

- `<hex>53534944</hex>`는 `<name><SSID of wifi profile></name>`의 16진수 값으로 설정해야 합니다. Windows 10 디바이스는 잘못된 `x87D1FDE8 Remediation failed` 오류를 반환할 수 있지만, 디바이스에는 계속 프로필이 포함됩니다.

- XML에는 `&`(앰퍼샌드)와 같은 특수 문자가 있습니다. 특수 문자를 사용하면 XML이 예상대로 작동하지 않을 수 있습니다. 

### <a name="example"></a>예제

``` xml
<!--
<hex>53534944</hex> = The hexadecimal value of <name><SSID of wifi profile></name>
<Name of wifi profile> = Name of profile shown to users. It could be <name>Your Company's Network</name>.
<SSID of wifi profile> = Plain text of SSID. Does not need to be escaped. It could be <name>Your Company's Network</name>.
<nonBroadcast><true/false></nonBroadcast>
<Type of authentication> = Type of authentication used by the network, such as WPA2PSK.
<Type of encryption> = Type of encryption used by the network, such as AES.
<protected>false</protected> do not change this value, as true could cause device to expect an encrypted password and then try to decrypt it, which may result in a failed connection.
<password> = Plain text of the password to connect to the network
-->

<WLANProfile
xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
  <name><Name of wifi profile></name>
  <SSIDConfig>
    <SSID>
      <hex>53534944</hex>
 <name><SSID of wifi profile></name>
    </SSID>
    <nonBroadcast>false</nonBroadcast>
  </SSIDConfig>
  <connectionType>ESS</connectionType>
  <connectionMode>auto</connectionMode>
  <autoSwitch>false</autoSwitch>
  <MSM>
    <security>
      <authEncryption>
        <authentication><Type of authentication></authentication>
        <encryption><Type of encryption></encryption>
        <useOneX>false</useOneX>
      </authEncryption>
      <sharedKey>
        <keyType>passPhrase</keyType>
        <protected>false</protected>
        <keyMaterial>password</keyMaterial>
      </sharedKey>
      <keyIndex>0</keyIndex>
    </security>
  </MSM>
</WLANProfile>
```

### <a name="eap-based-wi-fi-profile-example"></a>EAP 기반 Wi-Fi 프로필 예제
다음 예제에는 EAP 기반 Wi-Fi 프로필의 XML 코드가 포함됩니다. 이 예제는 적절한 형식을 표시하고 자세한 내용을 제공하기 위해 제공된 것입니다. 이는 예시일 뿐이며, 사용자 환경에 대한 권장 구성으로 제공된 것은 아닙니다.


```xml
    <WLANProfile xmlns="http://www.microsoft.com/networking/WLAN/profile/v1">
      <name>testcert</name>
      <SSIDConfig>
        <SSID>
          <hex>7465737463657274</hex>
          <name>testcert</name>
        </SSID>
        <nonBroadcast>true</nonBroadcast>
      </SSIDConfig>
      <connectionType>ESS</connectionType>
      <connectionMode>auto</connectionMode>
      <autoSwitch>false</autoSwitch>
      <MSM>
        <security>
          <authEncryption>
            <authentication>WPA2</authentication>
            <encryption>AES</encryption>
            <useOneX>true</useOneX>
            <FIPSMode     xmlns="http://www.microsoft.com/networking/WLAN/profile/v2">false</FIPSMode>
          </authEncryption>
          <PMKCacheMode>disabled</PMKCacheMode>
          <OneX xmlns="http://www.microsoft.com/networking/OneX/v1">
            <cacheUserData>false</cacheUserData>
            <authMode>user</authMode>
            <EAPConfig>
              <EapHostConfig     xmlns="http://www.microsoft.com/provisioning/EapHostConfig">
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
                      <PerformServerValidation xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</PerformServerValidation>
                      <AcceptServerName xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">false</AcceptServerName>
                      <TLSExtensions xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2">
                        <FilteringInfo xmlns="http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3">
                          <AllPurposeEnabled>true</AllPurposeEnabled>
                          <CAHashList Enabled="true">
                            <IssuerHash>75 f5 06 9c a4 12 0e 9b db bc a1 d9 9d d0 f0 75 fa 3b b8 78 </IssuerHash>
                          </CAHashList>
                          <EKUMapping>
                            <EKUMap>
                              <EKUName>Client Authentication</EKUName>
                              <EKUOID>1.3.6.1.5.5.7.3.2</EKUOID>
                            </EKUMap>
                          </EKUMapping>
                          <ClientAuthEKUList Enabled="true"/>
                          <AnyPurposeEKUList Enabled="false">
                            <EKUMapInList>
                              <EKUName>Client Authentication</EKUName>
                            </EKUMapInList>
                          </AnyPurposeEKUList>
                        </FilteringInfo>
                      </TLSExtensions>
                    </EapType>
                  </Eap>
                </Config>
              </EapHostConfig>
            </EAPConfig>
          </OneX>
        </security>
      </MSM>
    </WLANProfile>
```

## <a name="create-the-xml-file-from-an-existing-wi-fi-connection"></a>기존 Wi-Fi 연결에서 XML 파일 만들기

기존 Wi-Fi 연결에서 XML 파일을 만들 수도 있습니다. Windows 컴퓨터에서 다음 단계를 사용합니다.

1. 내보낸 Wi-Fi 프로필에 대한 로컬 폴더를 만듭니다(예: c:\WiFi).
2. 관리자 권한으로 명령 프롬프트를 엽니다(`cmd` > **관리자로 실행**을 마우스 오른쪽 단추로 클릭합니다).
3. `netsh wlan show profiles`를 실행합니다. 모든 프로필의 이름이 나열됩니다.
4. `netsh wlan export profile name="YourProfileName" folder=c:\Wifi`를 실행합니다. 이 명령은 c:\Wifi.에 `Wi-Fi-YourProfileName.xml`이라는 파일을 만듭니다.

    - 미리 공유한 키를 포함하는 Wi-Fi 프로필을 내보내는 경우 명령에 `key=clear`를 추가해야 합니다.
  
        `netsh wlan export profile name="YourProfileName" key=clear folder=c:\Wifi`

        `key=clear`는 프로필을 성공적으로 사용하는 데 필요한 일반 텍스트로 키를 내보냅니다.

XML 파일을 만든 후에는 XML 구문을 복사하여 OMA-URI 설정 > **데이터 형식**에 붙여넣습니다. [사용자 지정 프로필 만들기](#create-a-custom-profile)(이 문서에서)는 단계를 나열합니다.

> [!TIP]
> `\ProgramData\Microsoft\Wlansvc\Profiles\Interfaces\{guid}`에는 XML 형식의 모든 프로필도 포함됩니다.

## <a name="best-practices"></a>최선의 구현 방법

- PSK를 사용하여 Wi-Fi 프로필을 배포하기 전에 디바이스를 엔드포인트에 직접 연결할 수 있는지 확인합니다.

- 키(암호)를 회전하는 경우 가동 중지 시간을 예상하고 배포를 계획합니다. 근무 외 시간에 새 Wi-Fi 프로필을 푸시하는 것이 좋습니다. 연결에 영향을 받을 만한 사용자에게 경고를 하는 것도 좋습니다.

- 원활한 전환을 구현하려면 최종 사용자의 디바이스에서 인터넷에 연결하는 대안을 마련해야 합니다. 예를 들어, 최종 사용자가 게스트 WiFi(또는 다른 WiFi 네트워크)로 다시 전환할 수 있거나 셀룰러 연결을 통해 Intune과 통신할 수 있습니다. 추가 연결을 사용하면 디바이스에서 회사 Wi-Fi 프로필이 업데이트될 때 사용자가 정책 업데이트를 받을 수 있습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.
