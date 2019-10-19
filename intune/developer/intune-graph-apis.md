---
title: Azure AD를 사용하여 Microsoft Graph의 Intune API에 액세스하는 방법
titleSuffix: Microsoft Intune
description: 앱에서 Azure AD를 통해 Microsoft Graph의 Intune API에 액세스하는 데 필요한 단계를 설명합니다.
keywords: intune graphapi c# powershell 권한 역할
author: dougeby
manager: dougeby
ms.author: dougeby
ms.date: 03/08/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 79A67342-C06D-4D20-A447-678A6CB8D70A
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a5381d139247424d976b6b510d62681f623203a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490514"
---
# <a name="how-to-use-azure-ad-to-access-the-intune-apis-in-microsoft-graph"></a>Azure AD를 사용하여 Microsoft Graph의 Intune API에 액세스하는 방법

이제 [Microsoft Graph API](https://developer.microsoft.com/graph/)는 특정 API 및 권한 역할을 통해 Microsoft Intune을 지원합니다.  Microsoft Graph API는 Azure AD(Azure Active Directory)를 사용하여 인증 및 액세스 제어를 수행합니다.  
Microsoft Graph에서 Intune API에 액세스하려면 다음 항목이 필요합니다.

- 다음 권한/권한 범위가 있는 애플리케이션 ID:

  - Azure AD 및 Microsoft Graph API를 호출할 수 있는 권한
  - 특정 애플리케이션 작업과 관련된 권한 범위

- 다음 권한이 있는 사용자 자격 증명:

  - 애플리케이션과 연결된 Azure AD 테넌트 액세스 권한
  - 애플리케이션 권한 범위를 지원하는 데 필요한 역할 권한

- 최종 사용자가 Azure 테넌트에 대해 애플리케이션 작업을 수행할 권한을 앱에 부여

이 문서의 내용은 다음과 같습니다.

- Microsoft Graph API 및 관련 권한 역할에 대한 액세스 권한으로 애플리케이션을 등록하는 방법을 보여 줍니다.

- Intune API 권한 역할에 대해 설명합니다.

- C# 및 PowerShell에 대한 Intune API 인증 예제를 제공합니다.

- 여러 테넌트를 지원하는 방법을 설명합니다.

자세한 내용은 다음을 참조하세요.

- [OAuth 2.0 및 Azure Active Directory를 사용하여 웹 애플리케이션에 대한 액세스 권한 부여](https://docs.microsoft.com/azure/active-directory/develop/active-directory-protocols-oauth-code)
- [Azure AD 인증 시작](https://www.visualstudio.com/docs/integrate/get-started/auth/oauth)
- [Azure Active Directory와 애플리케이션 통합](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)
- [OAuth 2.0 이해](https://oauth.net/2/)

## <a name="register-apps-to-use-the-microsoft-graph-api"></a>Microsoft Graph API를 사용할 앱 등록

Microsoft Graph API를 사용할 앱을 등록하려면 다음을 수행합니다.

1. 관리 자격 증명을 사용 하 여 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) 에 로그인 합니다.

    해당하는 경우 다음 계정을 사용할 수 있습니다.
    - 테넌트 관리자 계정
    - **사용자가 애플리케이션을 등록할 수 있음** 설정이 활성화된 테넌트 사용자 계정

2. 메뉴에서 **Azure Active Directory** &gt; **앱 등록**을 선택합니다.

    <img src="../media/azure-ad-app-reg.png" width="157" height="170" alt="The App registrations menu command" />

3. **새 애플리케이션 등록**을 선택하여 새 애플리케이션을 만들거나 기존 애플리케이션을 선택합니다.  기존 애플리케이션을 선택하는 경우 다음 단계는 건너뛰세요.

4. **만들기** 블레이드에서 다음을 지정합니다.

    1. 사용자가 로그인할 때 표시되는 애플리케이션의 **이름**

    2. **애플리케이션 유형** 및 **리디렉션 URI** 값

        이러한 정보는 요구 사항에 따라 달라집니다. 예를 들어 ADAL(Azure AD [인증 라이브러리](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries))을 사용하는 경우에는 **애플리케이션 유형**를 `Native`로, **리디렉션 URI**를 `urn:ietf:wg:oauth:2.0:oob`로 설정합니다.

        <img src="../media/azure-ad-app-new.png" width="209" height="140" alt="New app properties and values" />

        자세한 내용을 알아보려면 [Azure AD의 인증 시나리오](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios)를 참조하세요.

5. 애플리케이션 블레이드에서 다음을 수행합니다.

    1. **애플리케이션 ID** 값을 적어 둡니다.

    2. **설정** &gt; **API 액세스** &gt; **필요한 권한**을 선택합니다.

    <img src="../media/azure-ad-req-perm.png" width="483" height="186" alt="The Required permissions setting" />

6. **필요한 권한** 블레이드에서 **추가** &gt; **API 액세스 추가** &gt; **API 선택**을 선택합니다.

    <img src="../media/azure-ad-add-graph.png" width="436" height="140" alt="The Microsoft Graph setting" />

7. **API 선택** 블레이드에서 **Microsoft Graph** &gt; **선택**을 선택합니다.  **액세스 사용** 블레이드가 열리고 애플리케이션에 사용할 수 있는 권한 범위가 나열됩니다.

    <img src="../media/azure-ad-perm-scopes.png" width="489" height="248" alt="Intune Graph API permission scopes" />

    관련 이름 왼쪽에 확인 표시를 하여 앱에 필요한 역할을 선택합니다.  특정 Intune 권한 범위에 대해 자세히 알아보려면 [Intune 권한 범위](#intune-permission-scopes)를 참조하세요.  다른 Graph API 권한 범위에 대해 자세히 알아보려면 [Microsoft Graph 권한 참조](https://developer.microsoft.com/graph/docs/concepts/permissions_reference)를 참조하세요.

    최상의 결과를 얻으려면 애플리케이션을 구현하는 데 필요한 가장 적은 수의 역할을 선택합니다.

    작업이 완료되면 **선택**, **완료**를 선택하여 변경 내용을 저장합니다.

이 시점에서 다음을 수행할 수도 있습니다.

- 자격 증명을 제공하지 않고 앱을 사용할 수 있도록 모든 테넌트 계정에 대해 권한을 부여하도록 선택합니다.  

    이렇게 하려면 **권한 부여**를 선택하고 확인 메시지를 수락합니다.

    애플리케이션을 처음으로 실행하면 선택한 역할을 수행하기 위한 권한을 앱에 부여하라는 메시지가 표시됩니다.

    <img src="../media/azure-ad-grant-perm.png" width="351" height="162" alt="The Grant permissions button" />

- 테넌트 외부 사용자가 앱을 사용할 수 있도록 설정합니다.  일반적으로는 여러 테넌트/조직을 지원하는 파트너만 이 작업을 수행하면 됩니다.  

    확인 방법은 다음과 같습니다.

  1. 애플리케이션 블레이드에서 **매니페스트**를 선택합니다. 그러면 **매니페스트 편집** 블레이드가 열립니다.

     <img src="../media/azure-ad-edit-mft.png" width="295" height="114" alt="The Edit manifest blade" />

  2. `availableToOtherTenants` 설정의 값을 `true`로 변경합니다.

  3. 변경 내용을 저장합니다.

## <a name="intune-permission-scopes"></a>Intune 권한 범위

Azure AD 및 Microsoft Graph는 권한 범위를 사용하여 회사 리소스에 대한 액세스를 제어합니다.  

_OAuth 범위_라고도 하는 권한 범위는 특정 Intune 엔터티 및 해당 속성에 대한 액세스를 제어합니다. 이 섹션에서는 Intune API 기능의 권한 범위를 요약하고 있습니다.

자세한 내용은 다음 항목을 참조하세요.
- [Azure AD 인증](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-pass-through-authentication)
- [애플리케이션 권한 범위](https://docs.microsoft.com/azure/active-directory/develop/active-directory-v2-scopes)

Microsoft Graph에 권한을 부여하는 경우 다음 범위를 지정하여 Intune 기능에 대한 액세스를 제어할 수 있습니다. 아래 표에는 Intune API 권한 범위가 요약되어 있습니다.  첫 번째 열에는 Azure Portal에 표시되는 기능의 이름이 표시되어 있고 두 번째 열에는 권한 범위 이름이 나와 있습니다.

_액세스 사용_ 설정 | 범위 이름
:--|:--
__Microsoft Intune 디바이스에서 사용자에게 영향을 주는 원격 작업 수행__ | [DeviceManagementManagedDevices.PrivilegedOperations.All](#mgd-po)
__Microsoft Intune 디바이스 읽기 및 쓰기__ | [DeviceManagementManagedDevices.ReadWrite.All](#mgd-rw)
__Microsoft Intune 디바이스 읽기__ | [DeviceManagementManagedDevices.Read.All](#mgd-ro)
__Microsoft Intune RBAC 설정 읽기 및 쓰기__ | [DeviceManagementRBAC.ReadWrite.All](#rac-rw)
__Microsoft Intune RBAC 설정 읽기__ | DeviceManagementRBAC.Read.All
__Microsoft Intune 앱 읽기 및 쓰기__ | [DeviceManagementApps.ReadWrite.All](#app-rw)
__Microsoft Intune 앱 읽기__ | [DeviceManagementApps.Read.All](#app-ro)
__Microsoft Intune 디바이스 구성 및 정책 읽기 및 쓰기__ | DeviceManagementConfiguration.ReadWrite.All
__Microsoft Intune 디바이스 구성 및 정책 읽기__ | [DeviceManagementConfiguration.Read.All](#cfg-ro)
__Microsoft Intune 구성 읽기 및 쓰기__ | [DeviceManagementServiceConfig.ReadWrite.All](#svc-rw)
__Microsoft Intune 구성 읽기__ | DeviceManagementServiceConfig.Read.All

표에는 Azure Portal에 표시되는 설정이 나와 있습니다. 다음 섹션에서는 범위를 사전순으로 설명합니다.

현재 모든 Intune 권한 범위에는 관리자 권한이 필요합니다.  즉, Intune API 리소스에 액세스하는 앱 또는 스크립트를 실행할 때 해당 자격 증명이 필요합니다.

### <a name="app-ro"></a>DeviceManagementApps.Read.All

- **액세스 사용** 설정: __Microsoft Intune 앱 읽기__

- 다음 엔터티 속성과 상태에 대한 읽기 권한을 허용합니다.
  - 클라이언트 앱
  - 모바일 앱 범주
  - 앱 보호 정책
  - 앱 구성

### <a name="app-rw"></a>DeviceManagementApps.ReadWrite.All

- **액세스 사용** 설정: __Microsoft Intune 앱 읽기 및 쓰기__

- __DeviceManagementApps.Read.All__과 같은 작업을 허용합니다.

- 다음 엔터티의 변경도 허용합니다.

  - 클라이언트 앱
  - 모바일 앱 범주
  - 앱 보호 정책
  - 앱 구성

### <a name="cfg-ro"></a>DeviceManagementConfiguration.Read.All

- **액세스 사용** 설정: __Microsoft Intune 디바이스 구성 및 정책 읽기__

- 다음 엔터티 속성과 상태에 대한 읽기 권한을 허용합니다.
  - 디바이스 구성
  - 디바이스 준수 정책
  - 알림 메시지

### <a name="cfg-ra"></a>DeviceManagementConfiguration.ReadWrite.All

- **액세스 사용** 설정: __Microsoft Intune 디바이스 구성 및 정책 읽기 및 쓰기__

- __DeviceManagementConfiguration.Read.All__과 같은 작업을 허용합니다.

- 앱은 다음 엔터티 만들기/할당/삭제/변경도 수행할 수 있습니다.
  - 디바이스 구성
  - 디바이스 준수 정책
  - 알림 메시지

### <a name="mgd-po"></a>DeviceManagementManagedDevices.PrivilegedOperations.All

- **액세스 사용** 설정: __Microsoft Intune 디바이스에서 사용자에게 영향을 주는 원격 작업 수행__

- 관리 디바이스에서 다음과 같은 원격 작업을 허용합니다.
  - 사용 중지
  - 초기화
  - 암호 초기화/복구
  - 원격 잠금
  - 분실 모드 사용/사용 안 함
  - PC 정리
  - 다시 부팅
  - 공유 디바이스에서 사용자 삭제

### <a name="mgd-ro"></a>DeviceManagementManagedDevices.Read.All

- **액세스 사용** 설정: __Microsoft Intune 디바이스 읽기__

- 다음 엔터티 속성과 상태에 대한 읽기 권한을 허용합니다.
  - 관리 디바이스
  - 디바이스 범주
  - 검색된 앱
  - 원격 작업
  - 맬웨어 정보

### <a name="mgd-rw"></a>DeviceManagementManagedDevices.ReadWrite.All

- **액세스 사용** 설정: __Microsoft Intune 디바이스 읽기 및 쓰기__

- __DeviceManagementManagedDevices.Read.All__과 같은 작업을 허용합니다.

- 앱은 다음 엔터티 만들기/삭제/변경도 수행할 수 있습니다.
  - 관리 디바이스
  - 디바이스 범주

- 다음과 같은 원격 작업도 허용됩니다.
  - 디바이스 찾기
  - 활성화 잠금 무시
  - 원격 지원 요청

### <a name="rac-ro"></a>DeviceManagementRBAC.Read.All

- **액세스 사용** 설정: __Microsoft Intune RBAC 설정 읽기__

- 다음 엔터티 속성과 상태에 대한 읽기 권한을 허용합니다.
  - 역할 할당
  - 역할 정의
  - 리소스 작업

### <a name="rac-rw"></a>DeviceManagementRBAC.ReadWrite.All

- **액세스 사용** 설정: __Microsoft Intune RBAC 설정 읽기 및 쓰기__

- __DeviceManagementRBAC.Read.All__과 같은 작업을 허용합니다.

- 앱은 다음 엔터티 만들기/할당/삭제/변경도 수행할 수 있습니다.
  - 역할 할당
  - 역할 정의

### <a name="svc-ro"></a>DeviceManagementServiceConfig.Read.All

- **액세스 사용** 설정: __Microsoft Intune 구성 읽기__

- 다음 엔터티 속성과 상태에 대한 읽기 권한을 허용합니다.
  - 디바이스 등록
  - Apple Push Notification Certificate
  - Apple 장비 등록 프로그램
  - Apple Volume Purchase Program
  - Exchange Connector
  - 사용 약관
  - 통신 비용 관리
  - 클라우드 PKI
  - 브랜딩
  - Mobile Threat Defense

### <a name="svc-rw"></a>DeviceManagementServiceConfig.ReadWrite.All

- **액세스 사용** 설정: __Microsoft Intune 구성 읽기 및 쓰기__

- DeviceManagementServiceConfig.Read.All_과 같은 작업을 허용합니다.

- 앱은 다음 Intune 기능을 구성할 수도 있습니다.
  - 디바이스 등록
  - Apple Push Notification Certificate
  - Apple 장비 등록 프로그램
  - Apple Volume Purchase Program
  - Exchange Connector
  - 사용 약관
  - 통신 비용 관리
  - 클라우드 PKI
  - 브랜딩
  - Mobile Threat Defense

## <a name="azure-ad-authentication-examples"></a>Azure AD 인증 예제

이 섹션에서는 C# 및 PowerShell 프로젝트에 Azure AD를 통합하는 방법을 보여 줍니다.

앞에서 설명한 것처럼 각 예제에서는 최소한 `DeviceManagementManagedDevices.Read.All` 권한 범위가 있는 애플리케이션 ID를 지정해야 합니다.

각 예제를 테스트할 때는 다음과 같은 HTTP 상태 403(Forbidden) 오류가 표시될 수 있습니다.

``` javascript
{
  "error": {
    "code": "Forbidden",
    "message": "Application is not authorized to perform this operation - Operation ID " +
       "(for customer support): 00000000-0000-0000-0000-000000000000 - " +
       "Activity ID: cc7fa3b3-bb25-420b-bfb2-1498e598ba43 - " +
       "Url: https://example.manage.microsoft.com/" +
       "Service/Resource/RESTendpoint?" +
       "api-version=2017-03-06 - CustomApiErrorPhrase: ",
    "innerError": {
      "request-id": "00000000-0000-0000-0000-000000000000",
      "date": "1980-01-0112:00:00"
    }
  }
}
```

이러한 오류가 발생하면 다음 사항을 확인하세요.

- 애플리케이션 ID를 Microsoft Graph API 및 `DeviceManagementManagedDevices.Read.All` 권한 범위를 사용하도록 권한이 부여된 ID로 업데이트했습니다.

- 테넌트 자격 증명이 관리 기능을 지원합니다.

- 코드가 표시된 샘플과 비슷합니다.


### <a name="authenticate-azure-ad-in-c"></a>C에서 Azure AD 인증\#

이 예제에서는 C#을 사용하여 Intune 계정과 연결된 디바이스 목록을 검색하는 방법을 보여 줍니다.

1. Visual Studio를 시작한 다음 새 Visual C# 콘솔 앱(.NET Framework) 프로젝트를 만듭니다.

2. 프로젝트의 이름을 입력하고 필요에 따라 다른 세부 정보를 입력합니다.

    <img src="../media/aad-auth-cpp-new-console.png" width="624" height="433" alt="Creating a C# console app project in Visual Studio"  />

3. 솔루션 탐색기를 사용하여 프로젝트에 Microsoft ADAL NuGet 패키지를 추가합니다.

    1. 솔루션 탐색기를 마우스 오른쪽 단추로 클릭합니다.
    2. **NuGet 패키지 관리...** &gt; **찾아보기**를 선택합니다.
    3. `Microsoft.IdentityModel.Clients.ActiveDirectory`를 선택하고 **설치**를 선택합니다.

    <img src="../media/aad-auth-cpp-install-package.png" width="624" height="458" alt="Selecting the Azure AD identity model module" />

4. **Program.cs** 맨 위에 다음 문을 추가합니다.

    ``` csharp
    using Microsoft.IdentityModel.Clients.ActiveDirectory;</p>
    using System.Net.Http;
    ```

5. 권한 부여 헤더를 만드는 메서드를 추가합니다.

    ``` csharp
    private static async Task<string> GetAuthorizationHeader()
    {
        string applicationId = "<Your Application ID>";
        string authority = "https://login.microsoftonline.com/common/";
        Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
        AuthenticationContext context = new AuthenticationContext(authority);
        AuthenticationResult result = await context.AcquireTokenAsync(
            "https://graph.microsoft.com",
            applicationId, redirectUri,
            new PlatformParameters(PromptBehavior.Auto));
        return result.CreateAuthorizationHeader();
    ```

    `application_ID`의 값은 앞에서 설명한 것처럼 최소한 `DeviceManagementManagedDevices.Read.All` 권한 범위가 부여된 ID와 일치하도록 변경해야 합니다.

6. 디바이스 목록을 검색하는 메서드를 추가합니다.

    ``` csharp
    private static async Task<string> GetMyManagedDevices()
    {
        string authHeader = await GetAuthorizationHeader();
        HttpClient graphClient = new HttpClient();
        graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
        return await graphClient.GetStringAsync(
            "https://graph.microsoft.com/beta/me/managedDevices");
    }
    ```

7. **Main**을 업데이트하여 **GetMyManagedDevices**를 호출합니다.

    ``` csharp
    string devices = GetMyManagedDevices().GetAwaiter().GetResult();
    Console.WriteLine(devices);
    ```

8. 프로그램을 컴파일하고 실행합니다.  

프로그램을 처음 실행하면 두 개의 프롬프트가 표시됩니다.  첫 번째 프롬프트는 자격 증명을 요청하고, 두 번째 프롬프트는 `managedDevices` 요청에 대한 권한을 부여합니다.  

참조할 수 있는 컴파일된 프로그램은 다음과 같습니다.

``` csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using System;
using System.Net.Http;
using System.Threading.Tasks;

namespace IntuneGraphExample
{
    class Program
    {
        static void Main(string[] args)
        {
            string devices = GetMyManagedDevices().GetAwaiter().GetResult();
            Console.WriteLine(devices);
        }

        private static async Task<string> GetAuthorizationHeader()
        {
            string applicationId = "<Your Application ID>";
            string authority = "https://login.microsoftonline.com/common/";
            Uri redirectUri = new Uri("urn:ietf:wg:oauth:2.0:oob");
            AuthenticationContext context = new AuthenticationContext(authority);
            AuthenticationResult result = await context.AcquireTokenAsync("https://graph.microsoft.com", applicationId, redirectUri, new PlatformParameters(PromptBehavior.Auto));
            return result.CreateAuthorizationHeader();
        }

        private static async Task<string> GetMyManagedDevices()
        {
            string authHeader = await GetAuthorizationHeader();
            HttpClient graphClient = new HttpClient();
            graphClient.DefaultRequestHeaders.Add("Authorization", authHeader);
            return await graphClient.GetStringAsync("https://graph.microsoft.com/beta/me/managedDevices");
        }
    }
}
```

### <a name="authenticate-azure-ad-powershell"></a>Azure AD 인증(PowerShell)

다음 PowerShell 스크립트는 인증을 위해 Azure AD PowerShell 모듈을 사용합니다.  자세한 내용을 알아보려면 [Azure Active Directory PowerShell 버전 2](https://docs.microsoft.com/powershell/azure/install-adv2?view=azureadps-2.0) 및 [Intune PowerShell 예제](https://github.com/microsoftgraph/powershell-intune-samples)를 참조하세요.

이 예제에서는 유효한 애플리케이션 ID와 일치하도록 `$clientID`의 값을 업데이트합니다.

``` powershell
function Get-AuthToken {
    [cmdletbinding()]
    param
    (
        [Parameter(Mandatory = $true)]
        $User
    )

    $userUpn = New-Object "System.Net.Mail.MailAddress" -ArgumentList $User
    $tenant = $userUpn.Host

    Write-Host "Checking for AzureAD module..."

    $AadModule = Get-Module -Name "AzureAD" -ListAvailable
    if ($AadModule -eq $null) {
        Write-Host "AzureAD PowerShell module not found, looking for AzureADPreview"
        $AadModule = Get-Module -Name "AzureADPreview" -ListAvailable
    }

    if ($AadModule -eq $null) {
        write-host
        write-host "AzureAD Powershell module not installed..." -f Red
        write-host "Install by running 'Install-Module AzureAD' or 'Install-Module AzureADPreview' from an elevated PowerShell prompt" -f Yellow
        write-host "Script can't continue..." -f Red
        write-host
        exit
    }

    # Getting path to ActiveDirectory Assemblies
    # If the module count is greater than 1 find the latest version

    if ($AadModule.count -gt 1) {
        $Latest_Version = ($AadModule | select version | Sort-Object)[-1]
        $aadModule = $AadModule | ? { $_.version -eq $Latest_Version.version }
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    else {
        $adal = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.dll"
        $adalforms = Join-Path $AadModule.ModuleBase "Microsoft.IdentityModel.Clients.ActiveDirectory.Platform.dll"
    }

    [System.Reflection.Assembly]::LoadFrom($adal) | Out-Null
    [System.Reflection.Assembly]::LoadFrom($adalforms) | Out-Null

    $clientId = "<Your Application ID>"
    $redirectUri = "urn:ietf:wg:oauth:2.0:oob"
    $resourceAppIdURI = "https://graph.microsoft.com"
    $authority = "https://login.microsoftonline.com/$Tenant"

    try {
        $authContext = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext" -ArgumentList $authority
        # https://msdn.microsoft.com/library/azure/microsoft.identitymodel.clients.activedirectory.promptbehavior.aspx
        # Change the prompt behaviour to force credentials each time: Auto, Always, Never, RefreshSession
        $platformParameters = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.PlatformParameters" -ArgumentList "Auto"
        $userId = New-Object "Microsoft.IdentityModel.Clients.ActiveDirectory.UserIdentifier" -ArgumentList ($User, "OptionalDisplayableId")
        $authResult = $authContext.AcquireTokenAsync($resourceAppIdURI, $clientId, $redirectUri, $platformParameters, $userId).Result
        # If the accesstoken is valid then create the authentication header
        if ($authResult.AccessToken) {
            # Creating header for Authorization token
            $authHeader = @{
                'Content-Type' = 'application/json'
                'Authorization' = "Bearer " + $authResult.AccessToken
                'ExpiresOn' = $authResult.ExpiresOn
            }
            return $authHeader
        }
        else {
            Write-Host
            Write-Host "Authorization Access Token is null, please re-run authentication..." -ForegroundColor Red
            Write-Host
            break
        }
    }
    catch {
        write-host $_.Exception.Message -f Red
        write-host $_.Exception.ItemName -f Red
        write-host
        break
    }   
}

$authToken = Get-AuthToken -User "<Your AAD Username>"

try {
    $uri = "https://graph.microsoft.com/beta/me/managedDevices"
    Write-Verbose $uri
    (Invoke-RestMethod -Uri $uri –Headers $authToken –Method Get).Value
}
catch {
    $ex = $_.Exception
    $errorResponse = $ex.Response.GetResponseStream()
    $reader = New-Object System.IO.StreamReader($errorResponse)
    $reader.BaseStream.Position = 0
    $reader.DiscardBufferedData()
    $responseBody = $reader.ReadToEnd();
    Write-Host "Response content:`n$responseBody" -f Red
    Write-Error "Request to $Uri failed with HTTP Status $($ex.Response.StatusCode) $($ex.Response.StatusDescription)"
    write-host
    break
}
```

## <a name="support-multiple-tenants-and-partners"></a>여러 테넌트 및 파트너 지원

조직에서 자체 Azure AD 테넌트가 있는 조직을 지원하는 경우에는 클라이언트가 개별 테넌트에서 애플리케이션을 사용하도록 허용할 수 있습니다.

확인 방법은 다음과 같습니다.

1. 클라이언트 계정이 대상 Azure AD 테넌트에 있는지 확인합니다.

2. 테넌트 계정이 사용자의 애플리케이션 등록을 허용하는지 확인합니다(**사용자 설정** 참조).

3. 각 테넌트 간의 관계를 설정합니다.  

    이렇게 하려면 다음 중 하나를 수행합니다.

    a. [Microsoft 파트너 센터](https://partnercenter.microsoft.com/)를 사용하여 클라이언트 및 전자 메일 주소로 관계를 정의합니다.

    b. 테넌트의 게스트로 포함할 사용자를 초대합니다.

테넌트의 게스트로 포함할 사용자를 초대하려면 다음을 수행합니다.

1. **빠른 태스크** 패널에서 **게스트 사용자 추가**를 선택합니다.

    <img src="../media/azure-ad-add-guest.png" width="448" height="138" alt="Use Quick Tasks to add a guest user" />

2. 클라이언트의 전자 메일 주소를 입력하고 필요에 따라 초대를 위한 개인 설정 메시지를 추가합니다.

    <img src="../media/azure-ad-guest-invite.png" width="203" height="106" alt="Inviting an external user as a guest" />

3. **초대**를 선택합니다.

그러면 해당 사용자에게 초대가 전송됩니다.

   <img src="../media/aad-multiple-tenant-invitation.png" width="624" height="523" alt="A sample guest invitation" />

   사용자가 **시작** 링크를 선택하여 초대를 수락해야 합니다.

관계가 설정되거나 초대가 수락되면 사용자 계정을 **디렉터리 역할**에 추가합니다.

필요에 따라 사용자를 다른 역할에 추가하세요. 예를 들어 Intune 설정을 구성할 수 있도록 하려는 사용자는 **전역 관리자** 또는 **Intune 서비스 관리자**로 지정해야 합니다.

또한 다음 작업도 수행합니다.

- 을 사용하여 사용자 계정에 Intune https://admin.microsoft.com 라이선스를 할당합니다.

- 애플리케이션 코드를 업데이트하여 자체 도메인이 아닌 클라이언트의 Azure AD 테넌트 도메인에 인증합니다.

    예를 들어 자체 테넌트 도메인은 `contosopartner.onmicrosoft.com`이고 클라이언트의 테넌트 도메인은 `northwind.onmicrosoft.com`인 경우 클라이언트의 테넌트에 인증하도록 코드를 업데이트합니다.

    위의 예제를 기준으로 C# 애플리케이션에서 코드를 업데이트하려면 다음 `authority` 변수의 값을 위에서 아래로 변경합니다.

    ``` csharp
    string authority = "https://login.microsoftonline.com/common/";
    ```

    을

    ``` csharp
    string authority = "https://login.microsoftonline.com/northwind.onmicrosoft.com/";
    ```
