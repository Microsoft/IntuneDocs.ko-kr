---
title: Active Directory용 Intune Connector의 프록시 설정 구성
description: 기존 온-프레미스 프록시 서버와 함께 작동하도록 Active Directory용 Intune Connector를 구성하는 방법을 설명합니다.
keywords: ''
author: master11218
ms.author: erikje
manager: dougeby
ms.date: 4/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: tanvira
ms.suite: ems
search.appverid: ''
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3a1af2e7c8aff281e04e92344b3e2c762bb23e0a
ms.sourcegitcommit: ce518a5dfe62c546a77f32ef372f36efbaad473f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2019
ms.locfileid: "74465753"
---
# <a name="work-with-existing-on-premises-proxy-servers"></a>기존 온-프레미스 프록시 서버 작업

이 문서에서는 아웃바운드 프록시 서버와 함께 작동하도록 Active Directory용 Intune Connector를 구성하는 방법을 설명합니다. 이 문서는 네트워크 환경에 기존 프록시가 있는 고객을 위해 작성되었습니다.

커넥터의 작동 방식에 대한 자세한 내용은 [Azure AD 애플리케이션 프록시 커넥터의 이해](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-connectors)를 참조하세요.

## <a name="bypass-outbound-proxies"></a>아웃바운드 프록시 바이패스

커넥터에는 아웃바운드 요청을 수행하는 기본 OS 구성 요소가 있습니다. 이러한 구성 요소는 자동으로 WPAD(웹 프록시 자동 검색)를 사용하여 네트워크의 프록시 서버를 찾으려고 시도합니다.

OS 구성 요소는 wpad.domainsuffix에 대한 DNS 조회를 수행하여 프록시 서버를 찾으려고 시도합니다. 조회를 통해 DNS가 확인되면 wpad.dat의 IP 주소에 대한 HTTP 요청이 만들어집니다. 이 요청은 해당 환경의 프록시 구성 스크립트가 됩니다. 커넥터는 이 스크립트를 사용하여 아웃바운드 프록시 서버를 선택합니다. 그러나 프록시에 필요한 추가 구성 설정 때문에 커넥터 트래픽이 여전히 통과하지 못할 수 있습니다.

온-프레미스 프록시를 바이패스하여 Azure 서비스에 직접 연결하도록 커넥터를 구성할 수 있습니다. 네트워크 정책에서 허용한다면 이 방법을 사용하는 것이 좋습니다. 유지 관리할 구성이 하나 줄어들기 때문입니다.

커넥터에 아웃바운드 프록시를 사용하지 않도록 설정하려면 이 코드 샘플에 표시된 섹션의 :\Program Files\Microsoft Intune\ODJConnector\ODJConnectorUI\ODJConnectorUI.exe.config 파일을 편집하고 프록시 주소 및 프록시 포트를 추가합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup> 
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

Connector Updater 서비스도 프록시를 바이패스하게 하려면 C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config 파일을 비슷하게 변경합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>  
        <defaultProxy>   
            <proxy proxyaddress="<PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>   
        </defaultProxy>  
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

기본 .config 파일로 되돌려야 할 경우를 대비하여 원래 파일의 복사본을 만들어 두어야 합니다.

구성 파일을 수정한 후에는 Intune Connector 서비스를 다시 시작해야 합니다. 

1. **services.msc**를 엽니다.
2. **Intune ODJConnector 서비스**를 찾아서 선택합니다.
3. **다시 시작**을 선택합니다.

![서비스 다시 시작의 스크린샷](./media/autopilot-hybrid-connector-proxy/service-restart.png)


## <a name="next-steps"></a>다음 단계

[디바이스 관리](../remote-actions/device-management.md)
