---
title: REST 클라이언트를 사용하여 데이터 웨어하우스 API에서 데이터 가져오기
titlesuffix: Microsoft Intune
description: RESTful API를 사용하여 Intune 데이터 웨어하우스에서 데이터를 검색합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/13/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: D6D15039-4036-446C-A58F-A5E18175720A
ms.reviewer: aanavath
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2a79bac39e6d5529196d63394d86922a6d57bda5
ms.sourcegitcommit: bea4a81d262607c6e9dd1e26f5cd1a2faf7d051b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45602217"
---
# <a name="get-data-from-the-intune-data-warehouse-api-with-a-rest-client"></a>REST 클라이언트를 사용하여 Intune 데이터 웨어하우스 API에서 데이터 가져오기

RESTful 엔드포인트를 통해 Intune 데이터 웨어하우스 데이터 모델에 액세스할 수 있습니다. 데이터에 대한 액세스 권한을 얻으려면 클라이언트가 OAuth 2.0을 사용하여 Microsoft Azure AD(Azure Active Directory)에 대한 권한을 부여해야 합니다. 액세스할 수 있게 하려면 먼저 Azure에서 네이티브 앱을 설정하고 Microsoft Intune API에 권한을 부여합니다. 로컬 클라이언트가 권한을 부여받은 다음 클라이언트는 네이티브 앱을 통해 데이터 웨어하우스 엔드포인트와 통신할 수 있습니다.

데이터 웨어하우스 API에서 데이터를 가져오도록 클라이언트를 설정하는 단계에서는 다음과 같이 해야 합니다.

1. Azure에서 클라이언트 앱을 네이티브 앱으로 만들기
3. 클라이언트 앱에 Microsoft Intune API에 대한 액세스 권한 부여
3. 데이터를 가져올 로컬 REST 클라이언트 만들기

다음 단계를 사용하여 REST 클라이언트로 API에 권한을 부여하고 액세스하는 방법을 알아봅니다. 먼저 Postman을 사용하여 일반 REST 클라이언트를 사용하는 방법을 살펴봅니다. Postman은 REST 클라이언트 문제를 해결하고 API와 작동하는 REST 클라이언트를 개발하는 데 일반적으로 사용되는 도구입니다. Postman에 대한 자세한 내용은 [Postman](https://www.getpostman.com) 사이트를 참조하세요. 그런 다음 C# 코드 샘플을 살펴봅니다. 이 샘플은 클라이언트에 권한을 부여하고 API에서 데이터를 가져오는 예제를 제공합니다.

## <a name="create-a-client-app-as-a-native-app-in-azure"></a>Azure에서 클라이언트 앱을 네이티브 앱으로 만들기

Azure에서 네이티브 앱을 만듭니다. 이 네이티브 앱은 클라이언트 앱입니다. 로컬 컴퓨터에서 실행되는 클라이언트는 로컬 클라이언트가 자격 증명을 요청할 때 Intune 데이터 웨어하우스 API를 참조합니다.

1. 테넌트의 Azure Portal에 로그인합니다. **Azure Active Directory** > **앱 등록**을 선택하여 **앱 등록** 창을 엽니다.
2. **새 앱 등록**을 선택합니다.
3. 앱 세부 정보를 입력합니다.
    1.  **이름**에 이름을 입력합니다(예: Intune Data Warehouse Client).
    2.  **응용 프로그램 종류**로 **네이티브**를 선택합니다.
    3.  **로그온 URL**의 URL을 입력합니다. 로그온 URL은 구체적인 시나리오에 따라 달라지지만, Postman을 사용하려는 경우 `https://www.getpostman.com/oauth2/callback`을 입력합니다. Azure AD에 인증할 때 클라이언트 인증 단계에 콜백을 사용합니다.
4.  **만들기**를 선택합니다.

     ![Intune 데이터 웨어하우스 API](./media/reports-get_rest_data_client_overview.png)

5. 이 앱의 **응용 프로그램 ID**를 기록해 둡니다. 다음 섹션에서 이 ID를 사용합니다.

## <a name="grant-the-client-app-access-to-the-microsoft-intune-api"></a>클라이언트 앱에 Microsoft Intune API에 대한 액세스 권한 부여

이제 Azure에 정의된 앱이 있습니다. 네이티브 앱에서 Microsoft Intune API에 대한 액세스 권한을 부여합니다.

1.  네이티브 앱을 선택합니다. **Intune 데이터 웨어하우스 클라이언트**와 같은 앱 이름이 지정되었습니다.
2.  **설정** 창에서 **필요한 권한** 선택
3.  **필요한 권한** 창에서 **추가**를 선택합니다.
4.  **API 선택**을 선택합니다.
5.  웹앱 이름을 검색합니다. 웹앱 이름은 **Microsoft Intune API**로 지정되었습니다.
6.  목록에서 해당 앱을 선택합니다.
7.  **선택**을 선택합니다.
8.  **위임된 권한** 상자를 선택하여 **Get data warehouse information from Microsoft Intune**(Microsoft Intune에서 데이터 웨어하우스 정보 가져오기)을 추가합니다.

    ![액세스 사용 - Microsot Intune API](./media/reports-get_rest_data_client_access.png)

9.  **선택**을 선택합니다.
10.  **완료**를 선택합니다.
11.  필요에 따라 필요한 권한 창에서 **사용 권한 부여**를 선택합니다. 그러면 현재 디렉터리의 모든 계정에 액세스 권한이 부여됩니다. 따라서 테넌트의 모든 사용자에게 동의 대화 상자가 나타나지 않습니다. 자세한 내용은 [Azure Active Directory와 응용 프로그램 통합](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications)을 참조하세요.
12.  **예**를 선택합니다.

## <a name="get-data-from-the-microsoft-intune-api-with-postman"></a>Postman을 사용하여 Microsoft Intune API에서 데이터 가져오기

Postman과 같은 제네릭 REST 클라이언트를 사용하여 Intune 데이터 웨어하우스 API와 작동할 수 있습니다. Postman은 기본 OData 데이터 모델인 API의 기능에 대한 정보를 제공하고 API 리소스에 대한 연결 문제를 해결할 수 있습니다. 이 섹션에서는 로컬 클라이언트에 대한 Auth2.0 토큰 생성에 관한 정보를 찾을 수 있습니다. 클라이언트는 Azure AD를 인증하고 API 리소스에 액세스하기 위한 토큰이 필요합니다.

### <a name="information-you-will-need-to-make-the-call"></a>호출하는 데 필요한 정보

Postman을 사용하여 REST 호출을 수행하려면 다음 정보가 필요합니다.

| 특성        | 설명                                                                                                                                                                          | 예제                                                                                       |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| 콜백 URL     | 앱 설정 페이지에서 이를 콜백 URL로 설정합니다.                                                                                                                              | https://www.getpostman.com/oauth2/callback                                                    |
| 토큰 이름       | Azure 앱에 자격 증명을 전달하는 데 사용되는 문자열입니다. 이 프로세스에서는 데이터 웨어하우스 API를 호출할 수 있도록 토큰을 생성합니다.                          | 전달자                                                                                        |
| 인증 URL         | 인증하는 데 사용되는 URL입니다. | https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/ |
| 액세스 토큰 URL | 토큰을 부여하는 데 사용되는 URL입니다.                                                                                                                                              | https://login.microsoftonline.com/common/oauth2/token |
| 클라이언트 ID        | Azure에서 네이티브 앱을 만들 때 이 ID를 만들고 기록했습니다.                                                                                               | 4184c61a-e324-4f51-83d7-022b6a81b991                                                          |
| 범위(선택 사항) | 비어 있음                                                                                                                                                                               | 필드를 비워 둘 수 있습니다.                                                                     |
| 권한 부여 유형       | 토큰은 인증 코드입니다.                                                                                                                                                  | 인증 코드                                                                            |

### <a name="odata-endpoint"></a>OData 엔드포인트

엔드포인트도 필요합니다. 데이터 웨어하우스 엔드포인트를 가져오려면 사용자 지정 피드 URL이 필요합니다. 데이터 웨어하우스 창에서 OData 엔드포인트를 가져올 수 있습니다.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **기타 작업**에서 **Intune 데이터 웨어하우스 설정**을 선택합니다.
4. **타사 보고 서비스 사용** 아래에서 사용자 지정 피드 URL을 복사합니다. 다음과 유사합니다. `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta`

엔드포인트는 다음과 같은 형식입니다. `https://fef.{yourtenant}.manage.microsoft.com/ReportingService/DataWarehouseFEService/{entity}?api-version={verson-number}`.

예를 들어 **dates** 엔터티는 다음과 같습니다. `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`

자세한 내용은 [Intune 데이터 웨어하우스 API 엔드포인트](reports-api-url.md)를 참조하세요.

### <a name="make-the-rest-call"></a>REST 호출하기

Postman에 대한 새 액세스 토큰을 가져오려면 Azure AD 권한 부여 URL, 클라이언트 ID 및 클라이언트 암호를 추가해야 합니다. Postman이 자격 증명을 입력할 권한 부여 페이지를 로드합니다.

#### <a name="add-the-information-used-to-request-the-token"></a>토큰을 요청하는 데 사용되는 정보 추가

1.  아직 설치하지 않은 경우 Postman을 다운로드합니다. Postman을 다운로드하려면 [www.getpostman](https://www.getpostman.com)을 참조하세요.
2.  Postman을 엽니다. HTTP 작업 **GET**을 선택합니다.
3.  엔드포인트 URL을 주소에 붙여넣습니다. 다음과 유사합니다.  

    `https://fef.tenant.manage.microsoft.com/ReportingService/DataWarehouseFEService/dates?api-version=beta`
4.  **Authorization**(권한 부여) 탭을 선택하고 **Type**(형식) 목록에서 **OAuth 2.0**을 선택합니다.
5.  **Get New Access Token**(새 액세스 토큰 가져오기)을 선택합니다.
6.  Azure에서 이미 앱에 콜백 URL을 추가했는지 확인합니다. 콜백 URL은 `https://www.getpostman.com/oauth2/callback`입니다.
7.  **Token Name**(토큰 이름)에 Bearer를 입력합니다.
8.  **Auth URL**(인증 URL)을 추가합니다. 다음과 유사합니다.  

    `https://login.microsoftonline.com/common/oauth2/authorize?resource=https://api.manage.microsoft.com/`
9.  **Access Token URL**(액세스 토큰 URL)을 추가합니다. 다음과 유사합니다.  

     `https://login.microsoftonline.com/common/oauth2/token`

10. Azure에서 만들고 이름을 `Intune Data Warehouse Client`로 지정한 네이티브 앱에서 **Client ID**(클라이언트 ID)를 추가합니다. 다음과 유사합니다.  

     `88C8527B-59CB-4679-A9C8-324941748BB4`

11. **Authorization Code**(인증 코드) 및 [Request access token locally]\(로컬로 액세스 토큰 요청)를 선택합니다.

12. **Request Token**(토큰 요청)을 선택합니다.

    ![토큰에 대한 정보](./media/reports-postman_getnewtoken.png)

13. Active AD 권한 부여 페이지에서 자격 증명을 입력합니다. Postman의 토큰 목록에 이제 `Bearer`라는 토큰이 들어 있습니다.
14. **Use Token**(토큰 사용)을 선택합니다. 헤더 목록에는 권한 부여의 새 키 값과 `Bearer <your-authorization-token>` 값이 포함되어 있습니다.

#### <a name="send-the-call-to-the-endpoint-using-postman"></a>Postman을 사용하여 엔드포인트로 호출 보내기

1.  **보내기**를 선택합니다.
2.  반환 데이터는 Postman 응답 본문에 표시됩니다.

    ![Postman 200OK](./media/reports-postman_200OK.png)

## <a name="create-a-rest-client-c-to-get-data-from-the-intune-data-warehouse"></a>Intune 데이터 웨어하우스에서 데이터를 가져오기 위한 REST 클라이언트(C#) 만들기

다음 샘플은 간단한 REST 클라이언트를 포함합니다. 코드는 .NET 라이브러리의 **httpClient** 클래스를 사용합니다. 클라이언트는 Azure AD에 대한 자격 증명을 얻은 후 데이터 웨어하우스 API에서 dates 엔터티를 검색하기 위한 GET REST 호출을 생성합니다.

> [!Note]  
> [GitHub의 샘플](https://github.com/Microsoft/Intune-Data-Warehouse/blob/master/Samples/CSharp/Program.cs)인 다음 코드에 액세스할 수 있습니다. 샘플에 대한 최신 변경 내용 및 업데이트는 GitHub 리포지토리를 참조하세요.

1. **Microsoft Visual Studio**를 엽니다.
2. **파일** > **새 프로젝트**를 선택합니다. **Visual C#** 을 확장하고 **콘솔 앱(.Net Framework)** 을 선택합니다.
3. 프로젝트 이름을 ` IntuneDataWarehouseSamples`로 지정하고 프로젝트를 저장할 위치로 이동한 다음 **확인**을 선택합니다.
4. 솔루션 탐색기에서 솔루션의 이름을 마우스 오른쪽 단추로 클릭한 다음 **솔루션용 NuGet 패키지 관리**를 선택합니다. **찾아보기**를 클릭한 다음 검색 상자에서 `Microsoft.IdentityModel.Clients.ActiveDirectory`를 선택합니다.
5. 패키지를 선택하고 솔루션 패키지 관리에서 **IntuneDataWarehouseSamples** 프로젝트를 선택한 다음 **설치**를 선택합니다.
6. **동의함**을 선택하여 NuGet 패키지 라이선스에 동의합니다.
7. 솔루션 탐색기에서 `Program.cs`를 엽니다.

    ![Visual Studio의 프로젝트](./media/reports-get_rest_data_in.png)

8. Program.cs의 코드를 다음 코드로 바꿉니다.  
   ```csharp
   namespace IntuneDataWarehouseSamples
   {
   using System;
   using System.Net.Http;
   using System.Net.Http.Headers;
   using Microsoft.IdentityModel.Clients.ActiveDirectory;

   class Program
   {
    static void Main(string[] args)
   {
   /**
   * TODO: Replace the below values with your own.
   * emailAddress - The email address of the user that you will authenticate as.
   *
   * password  - The password for the above email address.
   *    This is inline only for simplicity in this sample. We do not
   *    recommend storing passwords in plaintext.
   *
   * applicationId - The application ID of the native app that was created in AAD.
   *
   * warehouseUrl   - The data warehouse URL for your tenant. This can be found in
   *      the Azure portal.
   *
   * collectionName - The name of the warehouse entity collection you would like to
   *      access.
   */
   var emailAddress = "intuneadmin@yourcompany.com";
   var password = "password_of(intuneadmin@yourcompany.com)";
   var applicationId = "<Application ID>";
   var warehouseUrl = "https://fef.{yourinfo}.manage.microsoft.com/ReportingService/DataWarehouseFEService?api-version=beta";
   var collectionName = "dates";

   var adalContext = new AuthenticationContext("https://login.windows.net/common/oauth2/token");
   AuthenticationResult authResult = adalContext.AcquireTokenAsync(
   resource: "https://api.manage.microsoft.com/",
   clientId: applicationId,
   userCredential: new UserPasswordCredential(emailAddress, password)).Result;

   var httpClient = new HttpClient();
   httpClient.DefaultRequestHeaders.Authorization = new AuthenticationHeaderValue("Bearer", authResult.AccessToken);

   var uriBuilder = new UriBuilder(warehouseUrl);
   uriBuilder.Path += "/" + collectionName;

   HttpResponseMessage response = httpClient.GetAsync(uriBuilder.Uri).Result;

   Console.Write(response.Content.ReadAsStringAsync().Result);
   Console.ReadKey();
   }
   }
   ```

9. 코드 샘플의 `TODO`를 업데이트합니다.
10. **Ctrl + F5**를 눌러 디버그 모드에서 Intune.DataWarehouseAPIClient 클라이언트를 빌드하고 실행합니다.

    ![JSON 형식으로 검색된 날짜 엔터티](./media/reports-get_rest_data_output.png)

11. 콘솔 출력을 검토합니다. 출력에는 Intune 테넌트의 **dates** 엔터티에서 끌어온 JSON 형식의 데이터가 포함되어 있습니다.

## <a name="next-steps"></a>다음 단계

[Intune 데이터 웨어하우스 API 사용](reports-api-url.md)에서 권한 부여, API URL 구조 및 OData 엔드포인트에 대한 자세한 내용을 확인할 수 있습니다.

Intune 데이터 웨어하우스 데이터 모델을 참조하여 API에 포함된 데이터 엔터티를 찾을 수도 있습니다. 자세한 내용은 [Intune 데이터 웨어하우스 API 데이터 모델](reports-ref-data-model.md)을 참조하세요.
