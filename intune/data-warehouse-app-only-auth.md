---
title: Intune 데이터 웨어하우스 애플리케이션 전용 인증
titleSuffix: Microsoft Intune
description: 이 항목에서는 Microsoft Intune 데이터 웨어하우스 애플리케이션 전용 인증에 대해 설명합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 04/09/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d7166563-6bb5-4624-b8c8-6b300a997c3a
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30d7b2acb6acf48699df92075349b06e5ad9e742
ms.sourcegitcommit: 617bd653c34c1e6a4e2ad61811c5912f8dab775c
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 04/10/2019
ms.locfileid: "59476513"
---
# <a name="intune-data-warehouse-application-only-authentication"></a>Intune 데이터 웨어하우스 애플리케이션 전용 인증

Azure AD(Azure Active Directory)를 사용하여 애플리케이션을 설정하고 Intune 데이터 웨어하우스에 인증할 수 있습니다. 이 프로세스는 애플리케이션이 사용자 자격 증명에 액세스할 수 없어야 하는 웹 사이트, 앱, 백그라운드 프로세스에 유용합니다. 다음 단계에 따라 OAuth 2.0을 사용하여 Azure AD에 애플리케이션을 인증합니다.

## <a name="authorization"></a>권한 부여

Azure AD(Azure Active Directory)는 OAuth 2.0을 사용하여 Azure AD 테넌트의 웹 애플리케이션과 웹 API에 액세스할 권한을 부여할 수 있게 합니다. 이 가이드에서는 C#을 사용하여 애플리케이션을 인증하는 방법을 보여 줍니다. OAuth 2.0 권한 부여 코드 흐름은 OAuth 2.0 사양의 섹션 4.1에 설명되어 있습니다. 자세한 내용은 [OAuth 2.0 및 Azure Active Directory를 사용하여 웹 애플리케이션에 대한 액세스 권한 부여](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)에서 참조하세요.


## <a name="azure-keyvault"></a>Azure KeyVault

다음 프로세스에서는 개인 메서드를 사용하여 앱 키를 처리하고 변환합니다. 이 개인 메서드의 이름은 SecureString입니다. 또는 Azure KeyVault를 사용하여 앱 키를 저장할 수도 있습니다. 자세한 내용은 [Key Vault](https://azure.microsoft.com/services/key-vault/)를 참조하세요.

## <a name="create-a-web-app"></a>웹앱 만들기

이 섹션에서는 Intune에서 가리키려는 웹앱에 대한 세부 정보를 제공합니다. 웹앱은 클라이언트-서버 애플리케이션입니다. 서버는 UI, 콘텐츠 및 기능을 포함하는 웹앱을 제공합니다. 이 앱 유형은 웹에서 별도로 유지 관리됩니다. Intune을 사용하여 웹앱에 Intune 액세스 권한을 부여합니다. 데이터 흐름은 웹앱에서 시작됩니다. 

1.  [Azure 포털](https://portal.azure.com)에 로그인합니다.
2.  Azure Portal의 위쪽에 있는 **리소스, 서비스, 문서 검색** 필드를 사용하여 **Azure Active Directory**를 검색합니다.
3.  드롭다운 메뉴에서 **서비스** 아래의 **Azure Active Directory**를 선택합니다.
4.  **앱 등록**을 선택합니다.
5.  **새 애플리케이션 등록**을 클릭하여 **만들기** 블레이드를 표시합니다.
6.  **만들기** 블레이드에서 다음과 같은 앱 정보를 추가합니다.

    - 앱 이름(예: *Intune App-Only Auth*).
    - **애플리케이션 유형**. 웹 애플리케이션, Web API 또는 둘 다를 나타내는 앱을 추가하려면 **웹앱/API**를 선택합니다.
    - 애플리케이션의 **로그온 URL**. 인증 프로세스 중에 사용자가 자동으로 이동되는 위치입니다. 사용자는 여기서 신원을 증명해야 합니다. 자세한 내용은 [Azure Active Directory를 사용하는 애플리케이션 액세스 및 Single Sign-On이란 무엇인가요?](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)를 참조하세요.

7.  **만들기** 블레이드의 맨 아래에서 **만들기**를 클릭합니다.

    >[!NOTE] 
    > **등록된 앱** 블레이드에서 나중에 사용할 **애플리케이션 ID**를 복사합니다.

## <a name="create-a-key"></a>키 만들기

이 섹션에서는 Azure AD가 앱에 대한 키 값을 생성합니다.

1.  **앱 등록** 블레이드에서 새로 만든 앱을 선택하여 앱 블레이드를 표시합니다.
2.  블레이드 위쪽에 있는 **설정**을 선택하여 **설정 블레이드**를 표시합니다.
3.  **설정** 블레이드에서 **키**를 선택합니다.
4.  키 **설명**, **만료** 기간, 키 **값**을 추가합니다.
5.  **저장**을 클릭하여 애플리케이션의 키를 저장하고 업데이트합니다.
6.  생성된 키 값(base64로 인코드됨)을 복사해야 합니다.

    >[!NOTE] 
    > **키** 블레이드를 나가면 키 값이 사라집니다. 나중에 이 블레이드에서 키를 검색할 수 없습니다. 나중에 사용하려면 키를 복사합니다.

## <a name="grant-application-permissions"></a>애플리케이션 사용 권한 부여

이 섹션에서는 애플리케이션에 대한 사용 권한을 부여합니다.

1.  **설정** 블레이드에서 **필요한 권한**을 선택합니다.
2.  **추가**를 클릭합니다.
3.  **API 추가**를 선택하여 **API 선택** 블레이드를 표시합니다.
4.  **Microsoft Intune API(MicrosoftIntuneAPI)** 를 선택하고 **API 선택** 블레이드에서 **선택**을 클릭합니다. **사용 권한 선택** 단계가 선택되고 **액세스 사용** 블레이드가 표시됩니다.
5.  **애플리케이션 사용 권한** 섹션에서 **Microsoft Intune에서 데이터 웨어하우스 정보 가져오기** 옵션을 선택합니다.
6.  **액세스 사용** 블레이드에서 **선택**을 클릭합니다.
7.  **API 액세스 추가** 블레이드에서 **완료**를 클릭합니다.
8.  **필요한 사용 권한** 블레이드에서 **사용 권한 부여**를 클릭하고 이 애플리케이션의 기존 사용 권한을 모두 업데이트하라는 메시지가 표시되면 **예**를 클릭합니다.

## <a name="generate-token"></a>토큰 생성

Visual Studio를 사용하여 .NET Framework를 지원하고 C#을 코딩 언어로 사용하는 콘솔 앱(.NET Framework) 프로젝트를 만듭니다.

1.  **파일** > **새로 만들기** > **프로젝트**를 선택하여 **새 프로젝트** 대화 상자를 표시합니다.
2.  왼쪽에서 **Visual C#** 을 선택하여 모든 .NET Framework 프로젝트를 표시합니다.
3.  **콘솔 앱(.NET Framework)** 을 선택하고 앱 이름을 추가한 다음 **확인**을 클릭하여 앱을 만듭니다.
4.  **솔루션 탐색기**에서 **Program.cs**를 선택하여 코드를 표시합니다.
5.  팝업 메뉴에서 **추가** > **새 항목**을 선택합니다. **새 항목 추가** 대화 상자가 표시됩니다.
6.  왼쪽의 **Visual C#** 에서 **코드**를 선택합니다.
7.  **클래스**를 선택하고 클래스 이름을 *IntuneDataWarehouseClass.cs*로 변경한 다음 **추가**를 클릭합니다.
8.  <code>Main</code> 메서드 안에 다음 코드를 추가합니다.

    ``` csharp
         var applicationId = ConfigurationManager.AppSettings["appId"].ToString();
         SecureString applicationSecret = ConvertToSecureStr(ConfigurationManager.AppSettings["appKey"].ToString()); // Load as SecureString from configuration file or secret store (i.e. Azure KeyVault)
         var tenantDomain = ConfigurationManager.AppSettings["tenantDomain"].ToString();
         var adalContext = new AuthenticationContext($"https://login.windows.net/" + tenantDomain + "/oauth2/token");
    
         AuthenticationResult authResult = adalContext.AcquireTokenAsync(
             resource: "https://api.manage.microsoft.com/",
             clientCredential: new ClientCredential(
                 applicationId,
                 new SecureClientSecret(applicationSecret))).Result;
    ``` 

9. 코드 파일의 맨 위에 다음 코드를 추가하여 네임스페이스를 추가합니다.

    ``` csharp
     using System.Security;
     using Microsoft.IdentityModel.Clients.ActiveDirectory;
     using System.Configuration;
    ``` 

10. <code>Main</code> 메서드 뒤에 다음 개인 메서드를 추가하여 앱 키를 처리하고 변환합니다.

    ``` csharp
    private static SecureString ConvertToSecureStr(string appkey)
    {
        if (appkey == null)
            throw new ArgumentNullException("AppKey must not be null.");
    
        var secureAppKey = new SecureString();
    
        foreach (char c in appkey)
            secureAppKey.AppendChar(c);
    
        secureAppKey.MakeReadOnly();
        return secureAppKey;
    }
    ```

11. **솔루션 탐색기**에서 **참조**를 마우스 오른쪽 단추로 클릭한 다음 **NuGet 패키지 관리**를 선택합니다.
12. *Microsoft.IdentityModel.Clients.ActiveDirectory*를 검색하고 관련 Microsoft NuGet 패키지를 설치합니다.
13. **솔루션 탐색기**에서 *App.config* 파일을 선택하고 엽니다.
14. xml이 다음과 같이 표시되도록 <code>appSettings</code> 섹션을 추가합니다.

    ``` xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup> 
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1" />
        </startup>
        <appSettings>
          <add key="appId" value="App ID created from 'Create a Web App' procedure"/>
          <add key="appKey" value="Key created from 'Create a key' procedure" />
          <add key="tenantDomain" value="contoso.onmicrosoft.com"/>
        </appSettings>
    </configuration>
    ``` 

15. <code>appId</code>, <code>appKey</code> 및 <code>tenantDomain</code> 값을 고유한 앱 관련 값과 일치하도록 업데이트합니다.
16. 앱을 빌드합니다.

    >[!NOTE] 
    > 추가 구현 코드를 보려면 [Intune-Data-Warehouse 코드 예제](https://github.com/Microsoft/Intune-Data-Warehouse/tree/master/Samples/CSharp )를 참조하세요.

## <a name="next-steps"></a>다음 단계
[Azure Key Vault란?](https://docs.microsoft.com/azure/key-vault/key-vault-whatis)을 검토하여 Azure Key Vault에 대해 자세히 알아보세요.

