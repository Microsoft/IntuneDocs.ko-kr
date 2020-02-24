---
title: 정책에 따라 보호되는 브라우저로 회사 웹 액세스 관리
titleSuffix: Microsoft Intune
description: Intune에서 할당한 정책에 따라 보호되는 브라우저를 사용하여 회사 웹 검색 및 웹 데이터 전송을 관리합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1feca24f-9212-4d5d-afa9-7c171c5e8525
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure, seoapril2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: c7c47a829f8f609528f45b30d0dd9bf56d9d8eb9
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77414897"
---
# <a name="manage-web-access-using-a-microsoft-intune-policy-protected-browser"></a>Microsoft Intune 정책에 따라 보호되는 브라우저를 사용하여 웹 액세스 관리

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune 정책(Microsoft Edge 또는 Intune Managed Browser)으로 보호되는 브라우저를 사용하여 회사 웹 사이트에 항상 안전하게 액세스할 수 있습니다.  Intune으로 구성된 경우 보호되는 브라우저에서 다음을 활용할 수 있습니다.

- 애플리케이션 보호 정책
- 조건부 액세스
- Single Sign-On
- 애플리케이션 구성 설정
- Azure 애플리케이션 프록시 통합

> [!IMPORTANT]
> Intune Managed Browser가 사용 중지됩니다. 보호된 Intune 브라우저 환경에서 Microsoft Edge를 사용하세요. 

## <a name="microsoft-edge-support"></a>Microsoft Edge 지원

iOS/iPadOS 및 Android 디바이스의 엔터프라이즈 시나리오에서 Microsoft Edge를 사용할 수 있습니다. Microsoft Edge는 최종 사용자 환경에 향상된 기능을 추가하여 Intune Managed Browser와 동일한 모든 관리 시나리오를 모두 지원합니다. Intune 정책을 통해 사용할 수 있는 Microsoft Edge 엔터프라이즈 기능은 다음과 같습니다.

- **이중 ID** - 사용자는 검색을 위해 회사 계정뿐 아니라 개인 계정을 추가할 수 있습니다. Office 365 및 Outlook의 아키텍처 및 환경과 비슷한 두 ID는 완전히 분리됩니다. Intune 관리자는 회사 계정 내에서 보호된 검색 환경에 대해 원하는 정책을 설정할 수 있습니다. 
- **Intune 앱 보호 정책 통합** - 관리자는 이제 잘라내기, 복사 및 붙여넣기 제어, 화면 캡처 방지, 사용자가 선택한 링크가 다른 관리형 앱에서만 열리도록 하는 기능을 포함하여 앱 보호 정책의 대상을 Microsoft Edge로 지정할 수 있습니다.
- **Azure 애플리케이션 프록시 통합** - 관리자는 SaaS 앱 및 웹앱에 대한 액세스를 제어할 수 있으므로, 최종 사용자가 회사 네트워크에서 연결하든지, 인터넷에서 연결하든지 관계없이 브라우저 기반 앱이 Microsoft Edge 브라우저에서만 실행되도록 할 수 있습니다. 
- **즐겨찾기 및 홈페이지 바로 가기 관리** - 간편한 액세스를 위해 관리자는 최종 사용자가 회사 컨텍스트에 있을 경우 즐겨찾기 아래에 URL이 표시되도록 설정할 수 있습니다. 관리자는 회사 사용자가 Microsoft Edge에서 새 페이지 또는 새 탭을 열 때 기본 바로 가기로 표시될 홈페이지 바로 가기를 설정할 수 있습니다.

Microsoft Edge에 대한 Microsoft Intune 보호 정책을 통해 조직의 데이터 및 리소스를 보호할 수 있습니다. Intune으로 보호되는 Microsoft Edge를 사용하면 회사의 리소스는 기본적으로 설치된 앱 내에서는 물론 웹 브라우저를 통해 액세스할 때도 보호됩니다.

## <a name="getting-started"></a>시작하기

Microsoft Edge 및 Intune Managed Browser는 공개 앱 스토어에서 다운로드하여 조직에서 사용할 수 있는 웹 브라우저 앱입니다. 

브라우저 정책에 대한 운영 체제 요구 사항:
- Android 4 이상
- iOS/iPadOS 8.0 이상

Android 및 iOS/iPadOS 이전 버전에서도 계속 Managed Browser를 사용할 수는 있지만 새로운 버전의 앱을 설치할 수 없고 모든 기능을 액세스하지 못할 수 있습니다. 이러한 디바이스를 지원되는 운영 체제 버전으로 업데이트하는 것이 좋습니다.

>[!NOTE]
>Managed Browser는 SSLv3(Secure Sockets Layer 버전 3) 암호화 프로토콜을 지원하지 않습니다.


## <a name="application-protection-policies-for-protected-browsers"></a>보호되는 브라우저에 대한 애플리케이션 보호 정책

Microsoft Edge와 Managed Browser에는 Intune SDK가 통합되어 있으므로 다음을 비롯한 앱 보호 정책을 적용할 수도 있습니다.
- 잘라내기, 복사 및 붙여넣기 사용 제어
- 화면 캡처 방지
- 회사 링크가 관리되는 앱 및 브라우저 내에서만 열리는지 확인

자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

이러한 설정을 적용할 수 있는 장치는 다음과 같습니다.

- Intune에 등록된 디바이스
- 다른 MDM 제품에 등록된 장치
- 관리되지 않는 디바이스

>[!NOTE]
>사용자가 앱 스토어에서 Managed Browser를 설치했는데 Intune에서 Managed Browser를 관리하지 않는 경우에는 Managed Browser를 기본 웹 브라우저로 사용할 수 있습니다. 이 경우 Microsoft MyApps 사이트를 통해 Single Sign-On이 지원됩니다. 사용자는 MyApps 사이트로 직접 이동되며, 여기서 프로비저닝된 모든 SaaS 애플리케이션을 확인할 수 있습니다.
Managed Browser 또는 Microsoft Edge는 Intune에서 관리되지 않는 동시에 다른 Intune 관리 애플리케이션의 데이터에 액세스할 수 없습니다. 


## <a name="conditional-access-for-protected-browsers"></a>보호된 브라우저에 대한 조건부 액세스

Managed Browser는 조건부 액세스에 승인된 클라이언트 앱입니다. 즉, 사용자가 Managed Browser만 사용할 수 있는 Azure AD 연결 웹앱에 대한 모바일 브라우저 액세스를 제한할 수 있습니다. 그러면 Chrome 또는 Safari와 같은 다른 보호되지 않는 브라우저에서 액세스를 차단합니다. 이 보호는 Exchange Online 및 SharePoint Online과 같은 Azure 리소스, Microsoft 365 관리 센터 및 [Azure AD 애플리케이션 프록시](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)를 통해 외부 사용자에게 노출한 온-프레미스 사이트에도 적용될 수 있습니다. 

Azure AD 연결 웹앱이 모바일 플랫폼에서 Intune Managed Browser를 사용하도록 제한하려면 승인된 클라이언트 애플리케이션을 필요로 하는 조건부 액세스 정책을 만들 수 있습니다. 

> [!TIP]  
> 조건부 액세스는 Azure AD(Azure Active Directory) 기술입니다. *Intune*에서 액세스되는 조건부 액세스 노드는 *Azure AD*에서 액세스한 것과 동일한 노드입니다.  

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **조건부 액세스** > **새 정책**을 선택합니다.
3. 정책 **이름**을 추가합니다. 
4. **할당** 섹션에서 **조건** > **클라이언트 앱**을 선택합니다. **클라이언트 앱** 창이 표시됩니다.
5. **구성** 아래에서 **예**를 클릭하여 특정 클라이언트 앱에 정책을 적용합니다.
6. **브라우저**가 클라이언트 앱으로 선택되었는지 확인하세요.

    ![Azure AD - Managed Browser - 클라이언트 앱 선택](./media/app-configuration-managed-browser/managed-browser-conditional-access-02.png)

    > [!NOTE]
    > 이러한 클라우드 애플리케이션에 액세스할 수 있는 네이티브 앱(비 브라우저 앱)을 제한하려는 경우 **모바일 앱 및 데스크톱 클라이언트**를 선택할 수도 있습니다.

7. **완료** > **완료**를 클릭합니다.
8. **할당** 섹션에서 **사용자 및 그룹**을 선택한 다음, 이 정책을 할당하려는 사용자 또는 그룹을 선택합니다. **완료**를 클릭하여 창을 닫습니다.
9. **할당** 섹션에서 **클라우드 앱 또는 작업**을 선택하여 이 정책으로 보호할 앱을 선택합니다. **완료**를 클릭하여 창을 닫습니다.
10. 창의 **액세스 제어** 섹션에서 **권한 부여**를 선택합니다. 
11. **액세스 권한 부여**를 클릭하고 **승인된 클라이언트 앱 필요**를 클릭합니다. 
12. **권한 부여** 창에서 **선택**을 클릭합니다. 이 정책은 Intune Managed Browser 앱에만 액세스할 수 있도록 하려는 클라우드 앱에 할당되어야 합니다.

    ![Azure AD - Managed Browser 조건부 액세스 정책](./media/app-configuration-managed-browser/managed-browser-conditional-access-01.png)



위의 정책이 구성되면 사용자는 Intune Managed Browser를 사용하도록 강제하여 이 정책으로 보호한 Azure AD 연결 웹앱에 액세스할 수 있습니다. 사용자가 이 시나리오에서 관리되지 않는 브라우저를 사용하는 경우 Intune Managed Browser를 대신 사용해야 한다는 알림이 표시됩니다.

관리되는 브라우저는 클래식 조건부 액세스 정책을 지원하지 않습니다. 자세한 내용은 [Azure Portal에서 클래식 정책을 마이그레이션](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-migration)을 참조하세요.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>정책으로 보호되는 브라우저에서 Azure AD 연결 웹앱에 Single Sign-On

iOS/iPadOS 및 Android의 Microsoft Edge 및 Intune Managed Browser는 Azure AD에 연결된 모든 웹앱(SaaS 및 온-프레미스)에 SSO를 활용할 수도 있습니다. Microsoft Authenticator 앱이 iOS/iPadOS 또는 Android의 Intune 회사 포털 앱에 표시되는 경우, 정책으로 보호되는 브라우저의 사용자는 자격 증명을 다시 입력하지 않고도 Azure AD 연결 웹앱에 액세스할 수 있습니다.

SSO는 디바이스를 iOS/iPadOS 또는 Android의 Intune 회사 포털에 있는 Microsoft Authenticator 앱에 등록하는 작업이 필요합니다. 해당 디바이스가 다른 애플리케이션에 등록되어 있지 않은 경우 Authenticator 앱 또는 Intune 회사 포털을 사용하는 사용자가 정책으로 보호되는 브라우저에서 Azure AD 연결 웹앱으로 이동할 때 해당 디바이스를 등록하라는 메시지가 표시됩니다. 디바이스가 Intune에서 관리되는 계정으로 등록되면 해당 계정은 Azure AD 연결 웹앱에서 SSO를 사용하도록 설정합니다. 

> [!NOTE]
> 디바이스 등록은 Azure AD 서비스를 사용하는 간단한 체크 인입니다. 전체 디바이스를 등록할 필요가 없고 디바이스에 대한 추가 권한을 부여하지 않습니다.

## <a name="create-a-protected-browser-app-configuration"></a>보호된 브라우저 앱 구성 만들기

>[!IMPORTANT]
>앱 구성을 적용하려면 사용자의 보호되는 브라우저 또는 디바이스의 다른 앱이 [Intune 앱 보호 정책]( ../app-protection-policy.md)을 통해 이미 관리되고 있어야 합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **앱 구성 정책** > **추가** > **관리형 앱**을 선택합니다.
3. **구성 정책 추가** 창의 **앱 구성 정책 만들기** 창에서 앱 구성 설정에 대한 **이름** and optional **설명**(선택 사항)을 입력합니다.
4. **퍼블릭 앱 선택**을 선택하고 iOS/iPadOS, Android 또는 둘 다에 대해 **Managed Browser** 및/또는 **Edge**를 선택합니다.
5. **선택**을 클릭하여 **앱 구성 정책 만들기** 창으로 돌아갑니다.
6. **다음**을 클릭하여 **설정** 페이지를 표시합니다.
7. **설정** 페이지에서 앱용 구성을 제공할 키 및 값 쌍을 정의합니다. 이 문서의 뒷부분에 나오는 섹션에서 정의할 수 있는 다양한 키와 값 쌍에 대해 알아보세요.
8. **다음**을 클릭하여 **할당** 페이지를 표시한 후 **포함할 그룹 선택** 및/또는 **제외할 그룹 선택**을 클릭합니다.
9. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다.
10. 앱 구성 정책을 검토한 후 **만들기**를 클릭합니다.

새 구성이 생성되어 **앱 구성** 창에 표시됩니다.


## <a name="assign-the-configuration-settings-you-created"></a>작성한 구성 설정을 할당합니다.

Azure AD 사용자 그룹에 설정을 할당합니다. 해당 사용자가 대상이 지정된 보호되는 브라우저 앱을 설치한 경우에는 지정한 설정을 통해 앱이 관리됩니다.

1. Intune 모바일 애플리케이션 관리 대시보드의 **앱** 창에서 **앱 구성 정책**을 선택합니다.
2. 앱 구성 목록에서 할당하려는 구성을 선택합니다.
3. 다음 창에서 **할당**을 선택합니다.
4. **할당** 창에서 앱 구성을 할당할 Azure AD 그룹을 선택하고 **확인**을 선택합니다.

## <a name="how-to-set-microsoft-edge-as-the-protected-browser-for-your-organization"></a>Microsoft Edge를 조직의 보호되는 브라우저로 설정하는 방법

이 설정을 사용하면 Microsoft Edge와 Intune Managed Browser 모두 앱 보호 정책을 사용하여 대상 지정된다고 가정할 때 사용자가 Microsoft Edge 또는 Intune Managed Browser로 리디렉션됩니다. **이 애플리케이션 구성 정책 설정은 웹 링크가 열리는 Intune 관리 앱을 대상으로 해야 합니다.** 

이 설정이 "True"로 설정된 경우:

- 사용자는 이 설정을 사용하여 대상 지정된 Intune 관리 앱에서 링크를 열 때 Microsoft Edge로 리디렉션됩니다. 
- 앱이 아직 없는 사용자의 경우 Intune Managed Browser를 다운로드했는지 여부에 관계없이 스토어에서 Microsoft Edge를 다운로드하라는 메시지가 표시됩니다.

이 설정이 "False"로 설정된 경우:

- 사용자가 Managed Browser와 Microsoft Edge를 **모두** 다운로드한 경우 Managed Browser가 시작됩니다. 
- 사용자가 Managed Browser **또는** Microsoft Edge 중 **하나**를 다운로드한 경우 해당 브라우저 앱이 시작됩니다. 
- 사용자가 어느 브라우저 앱도 다운로드하지 않은 경우 Managed Browser를 다운로드하라는 메시지가 표시됩니다.

위 절차를 사용하여 Microsoft Edge 앱 구성을 만듭니다. **구성** 창에서 **구성 설정**을 선택할 때 다음 키-값 쌍을 제공합니다(9단계).

| Key                              |  값   |
|----------------------------------|----------|
| **com.microsoft.intune.useEdge** | **true** |

> [!NOTE]
> Microsoft Edge와 앱 구성에서 지정한 연결 앱을 관리하는 앱 보호 정책에서 다음 데이터 보호 정책 설정이 설정되어 있는지 확인합니다.
> - 다른 앱에 조직 데이터 보내기: **정책 관리 앱**
> - 다른 앱을 사용하여 웹 콘텐츠 전송 제한: **정책 관리 브라우저**

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>보호되는 브라우저에 대한 애플리케이션 프록시 설정을 구성하는 방법

Microsoft Edge 및 Intune Managed Browser와 [Azure AD 애플리케이션 프록시]( https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)를 함께 사용하면 iOS/iPadOS 및 Android 디바이스 사용자에 대해 다음과 같은 시나리오를 지원할 수 있습니다.

- 사용자가 Microsoft Outlook 앱을 다운로드하고 로그인합니다. Intune 앱 보호 정책이 자동으로 적용됩니다. 저장된 데이터를 암호화하고 사용자가 디바이스에서 관리되지 않는 앱 또는 위치로 회사 파일을 전송할 수 없도록 차단합니다. 그런 다음 사용자가 Outlook에서 인트라넷 사이트에 대한 링크를 클릭할 때 해당 링크가 다른 브라우저 대신 보호되는 브라우저 애플리케이션에서 열리도록 지정할 수 있습니다. 보호되는 브라우저는 이 인트라넷 사이트가 애플리케이션 프록시를 통해 사용자에게 공개된 것을 인식합니다. 사용자는 인트라넷 사이트에 연결하기 전에 적용 가능한 다단계 인증 및 조건부 액세스를 사용하여 인증하도록 애플리케이션 프록시를 통해 자동으로 라우팅됩니다. 이전에는 사용자가 원격으로 작업하는 동안 찾을 수 없었던 이 사이트에 이제 액세스할 수 있으며 Outlook의 링크가 예상대로 작동합니다.
- 원격 사용자가 보호되는 브라우저 애플리케이션을 열고 내부 URL을 사용하여 인트라넷 사이트로 이동합니다. 보호되는 브라우저는 이 인트라넷 사이트가 애플리케이션 프록시를 통해 사용자에게 공개된 것을 인식합니다. 사용자는 인트라넷 사이트에 연결하기 전에 적용 가능한 다단계 인증 및 조건부 액세스를 사용하여 인증하도록 애플리케이션 프록시를 통해 자동으로 라우팅됩니다. 이전에는 사용자가 원격으로 작업하는 동안 찾을 수 없었던 이 사이트에 이제 액세스할 수 있습니다.

### <a name="before-you-start"></a>시작하기 전에

- Azure AD 애플리케이션 프록시를 통해 내부 애플리케이션을 설정합니다.
  - 애플리케이션 프록시를 구성하고 애플리케이션을 게시하려면 [설정 설명서](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)를 참조하세요. 
  - 리디렉션이 발생할 엔터프라이즈 애플리케이션에 [사용자가 할당](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy-add-on-premises-application#add-a-user-for-testing)되어야 합니다. 애플리케이션이 사전 인증을 위한 통과 모드로 설정되어 있고 애플리케이션 프록시 설정에서 사용자 할당 요구 사항이 해제되어 있는 경우에도 이 작업을 수행해야 합니다.
- 최소 버전 1.2.0의 Managed Browser 앱을 사용해야 합니다.
- Managed Browser 또는 Microsoft Edge 앱의 사용자에게는 [Intune 앱 보호 정책](app-protection-policy.md)이 앱에 할당되어 있습니다.

    > [!NOTE]
    > 업데이트된 애플리케이션 프록시 리디렉션 데이터는 Managed Browser 및 Microsoft Edge에 적용되는 데 최대 24시간이 걸릴 수 있습니다.


#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>1단계: Outlook에서 보호되는 브라우저로 자동 리디렉션 사용 설정
**Managed Browser에서 표시할 수 있는 웹 콘텐츠 제한** 설정을 사용하도록 설정하는 앱 보호 정책으로 Outlook이 구성되어 있어야 합니다.

#### <a name="step-2-assign-an-app-configuration-policy-assigned-for-the-protected-browser"></a>2단계: 보호되는 브라우저에 할당되는 앱 구성 정책 할당
이 절차에서는 앱 프록시 리디렉션을 사용하도록 Managed Browser 또는 Microsoft Edge 앱을 구성합니다. 

정책의 구성 설정에서 **Edge** 탭을 열고 애플리케이션 리디렉션 값에 대해 **사용**을 선택합니다. 이 설정을 사용하도록 설정하면 사용자는 회사 링크와 Azure 애플리케이션 프록시를 통해 게시된 온-프레미스 웹앱에 액세스할 수 있습니다.

온-프레미스 웹앱에 원활한(및 보호된) 액세스와 함께 Managed Browser, Microsoft Edge 및 Azure AD 애플리케이션 프록시를 사용하는 방법에 대한 자세한 내용은 Enterprise Mobility + Security 블로그 게시물 [연계를 통해 성능 향상: 사용자 액세스를 개선하려는 Intune 및 Azure Active Directory 팀](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access)을 참조하세요.

## <a name="how-to-configure-the-homepage-for-a-protected-browser"></a>보호된 브라우저에 대해 홈페이지를 구성하는 방법

이 설정을 사용하면 보호되는 브라우저를 시작하거나 새 탭을 만들 때 사용자에게 표시되는 홈페이지를 구성할 수 있습니다. 
- 이 설정은 Managed Browser에서 웹 페이지를 표시합니다.  Edge는 홈페이지 바로 가기를 표시합니다.
- 홈페이지 바로 가기 아이콘은 검색 컨트롤 아래에 아이콘으로 나타납니다.  편집하거나 삭제할 수 없습니다.
- 홈페이지 바로 가기에는 구분을 위해 조직 이름이 표시됩니다.  항상 첫 번째 아이콘으로 표시됩니다.

Microsoft Edge 또는 Managed Browser 앱 구성을 만드는 절차를 수행할 때 다음 키와 값 쌍을 제공합니다.

|                                Key                                |                                                           값                                                            |
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.homepage</strong> | 유효한 URL을 지정합니다. 잘못된 URL은 보안 조치로 차단됩니다.<br>예: `https://www.bing.com` |

## <a name="how-to-configure-bookmarks-for-a-protected-browser"></a>보호된 브라우저에 대해 책갈피를 구성하는 방법

이 설정을 사용하면 Microsoft Edge 또는 Managed Browser의 사용자에게 제공되는 책갈피 집합을 구성할 수 있습니다.

- 이 책갈피는 사용자가 삭제하거나 수정할 수 없습니다.
- 이 책갈피는 목록 맨 위에 표시됩니다. 사용자가 만드는 모든 책갈피는 이 책갈피 아래에 표시됩니다.
- 앱 프록시 리디렉션을 사용한 경우 내부 또는 외부 URL 중 하나를 사용하여 앱 프록시 웹앱을 추가할 수 있습니다.

Microsoft Edge 또는 Managed Browser 앱 구성을 만드는 절차를 수행할 때 다음 키와 값 쌍을 제공합니다.

|                                Key                                 |                                                                                                                                                                                                                                                         값                                                                                                                                                                                                                                                          |
|--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <strong>com.microsoft.intune.mam.managedbrowser.bookmarks</strong> | 이 구성에 대한 값은 책갈피 목록입니다. 각 책갈피는 책갈피 제목과 책갈피 URL로 이루어져 있습니다. 제목과 URL을 <strong>&#124;</strong> 문자로 구분합니다.<br><br>예제:<br> <code>Microsoft Bing&#124;https://www.bing.com</code><br><br>여러 책갈피를 구성하려면 각 쌍을 이중 문자 <strong>&#124;&#124;</strong>로 구분합니다.<br><br>예제:<br> <code>Bing&#124;https://www.bing.com&#124;&#124;Contoso&#124;https://www.contoso.com</code> |

## <a name="how-to-specify-allowed-and-blocked-urls-for-a-protected-browser"></a>보호되는 브라우저에 대해 허용 URL 및 차단 URL을 지정하는 방법

Microsoft Edge 또는 Managed Browser 앱 구성을 만드는 절차를 수행할 때 다음 키와 값 쌍을 제공합니다.

|Key|값|
|-|-|
|다음 중에서 선택합니다.<br><ul><li>허용되는 URL을 지정합니다(이러한 URL만 허용되며 다른 사이트에 액세스할 수 없음).<br> **com.microsoft.intune.mam.managedbrowser.AllowListURLs**<br><br></li><li>차단되는 URL을 지정합니다(다른 모든 사이트는 액세스할 수 있음).<br>**com.microsoft.intune.mam.managedbrowser.BlockListURLs**</li></ul>|키에 해당하는 값은 URL 목록입니다. 허용하거나 차단할 모든 URL을 파이프 **&#124;** 문자로 구분된 단일 값으로 입력합니다.<br><br>예:<br><br><code>URL1&#124;URL2&#124;URL3</code><br><code>http://*.contoso.com/*&#124;https://*.bing.com/*&#124;https://expenses.contoso.com</code>|

>[!IMPORTANT]
>두 키를 모두 지정하지 마세요. 두 키가 동일한 사용자를 대상으로 하는 경우 가장 제한적인 옵션인 허용 키가 사용됩니다.
>그리고 회사 웹 사이트 등의 중요한 페이지는 차단하지 않아야 합니다.

### <a name="url-format-for-allowed-and-blocked-urls"></a>허용 및 차단 URL에 대한 URL 형식
다음 정보를 사용하여 허용 및 차단 목록에 URL을 지정할 때 사용할 수 있는 형식 및 와일드카드에 대해 알아볼 수 있습니다.

- 다음과 같이 허용되는 패턴 목록의 규칙에 따라 와일드카드 기호( **&#42;** )를 사용할 수 있습니다.

- URL을 목록에 입력할 때 모든 URL의 앞에 **http** 또는 **https** 를 덧붙여야 합니다.

- 주소에 포트 번호를 지정할 수 있습니다. 포트 번호를 지정하지 않으면 다음 값이 사용됩니다.

  - http의 경우 포트 80

  - https의 경우 포트 443

  포트 번호에 대한 와일드 카드 사용은 지원되지 않습니다. 예를 들어 `http://www.contoso.com:;` 및 `http://www.contoso.com: /;`은 지원되지 않습니다.

- 다음 표를 사용하여 URL을 지정할 때 사용할 수 있는 패턴에 대해 알아볼 수 있습니다.

|                  URL                  |                     세부 정보                      |                                                일치하는 항목                                                |                                일치하지 않는 항목                                 |
|---------------------------------------|--------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
|        `http://www.contoso.com`         |              단일 페이지와 일치               |                                            `www.contoso.com`                                            |  `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`contoso.com`/   |
|          `http://contoso.com`           |              단일 페이지와 일치               |                                             `contoso.com/`                                              | `host.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com` |
|    `http://www.contoso.com/&#42;`     | `www.contoso.com`으로 시작하는 모든 URL과 일치 |      `www.contoso.com`<br /><br />`www.contoso.com/images`<br /><br />`www.contoso.com/videos/tvshows`      |              `host.contoso.com`<br /><br />`host.contoso.com/images`              |
|    `http://*.contoso.com/*`     |     contoso.com 아래의 모든 하위 도메인과 일치     | `developer.contoso.com/resources`<br /><br />`news.contoso.com/images`<br /><br />`news.contoso.com/videos` |                               `contoso.host.com`                                |
|     `http://www.contoso.com/images`     |             단일 폴더와 일치              |                                        `www.contoso.com/images`                                         |                          `www.contoso.com/images/dogs`                          |
|       `http://www.contoso.com:80`       |  포트 번호를 사용하여 단일 페이지와 일치   |                                       `http://www.contoso.com:80`                                       |                                                                               |
|        `https://www.contoso.com`        |          안전한 단일 페이지와 일치           |                                        `https://www.contoso.com`                                        |                            `http://www.contoso.com`                             |
| `http://www.contoso.com/images/&#42;` |    단일 폴더 및 모든 하위 폴더와 일치    |                  `www.contoso.com/images/dogs`<br /><br />`www.contoso.com/images/cats`                   |                            `www.contoso.com/videos`                             |

- 다음은 지정할 수 없는 몇몇 입력의 예입니다.

  - `*.com`

  - `*.contoso/*`

  - `www.contoso.com/*images`

  - `www.contoso.com/*images*pigs`

  - `www.contoso.com/page*`

  - IP 주소

  - `https://*`

  - `http://*`

  - `http://www.contoso.com:*`

  - `http://www.contoso.com: /*`
  
## <a name="soft-transitions-from-work-to-personal-accounts"></a>회사 계정에서 개인 계정으로 부드럽게 전환

Microsoft Edge 모바일 엔터프라이즈 환경의 초석은 이중 ID 모델입니다. 즉, Microsoft Edge에서는 회사 ID와 개인 ID를 모두 지원합니다. Office 365 및 Outlook 앱에서처럼 이 이중 ID 모델을 통해 최종 사용자는 탐색이 필요할 때 항상 Microsoft Edge를 사용하고 관리자가 정의한 콘텐츠 정책에 따라 쉽게 두 환경 사이를 이동할 수 있습니다. 개인 컨텍스트에서의 탐색은 영향을 받지 않으며 회사 정보는 Microsoft Edge 내의 회사 컨텍스트 내로 완전히 제한됩니다. 

이 모델의 이점 중 하나는 조직에서 허용하지 않는 사이트에 대한 링크(예: 신문 기사 등)를 열려고 하는 사용자는 회사 컨텍스트와 완전히 분리된 자신의 개인 컨텍스트에서 이 작업을 수행할 수 있다는 점입니다. 이러한 부드러운 전환은 기본적으로 사용하도록 설정되어 있습니다. 

Microsoft Edge 또는 Managed Browser 앱 구성을 만드는 절차를 수행할 때 다음 키와 값 쌍을 제공합니다.

| Key                                                                | 값                                                 |
|--------------------------------------------------------------------|-------------------------------------------------------|
| **com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock** | **False**는 이러한 부드러운 전환이 이루어지는 것을 차단합니다. |

## <a name="how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios"></a>iOS에서 Managed Browser를 사용하여 관리되는 앱 로그에 액세스하는 방법

iOS/iPadOS 디바이스에 Managed Browser가 설치된 최종 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있습니다. 관리되는 iOS/iPadOS 앱의 문제를 해결하기 위해 로그를 보낼 수 있습니다.

1. iOS/iPadOS **설정**을 엽니다.
2. 관리되는 **브라우저** 애플리케이션 설정을 엽니다.
3. **Intune 진단 사용**을 토글하여 브라우저를 문제 해결 모드에 설정합니다.
4. 관리되는 **브라우저**를 엽니다. **Intune 앱 상태 보기**를 클릭하여 개별 애플리케이션 정책 설정을 봅니다.
5. **시작** 및 **로그 공유** 또는 **Microsoft에 로그 보내기**를 눌러서 문제 해결 IT 관리자나 Microsoft에 보냅니다.

앱 내에서 문제 해결 모드로 브라우저를 열 수도 있습니다.

1. Managed Browser를 엽니다.
2. 주소 상자에 `about:intunehelp`를 입력합니다.
브라우저가 문제 해결 모드를 시작합니다.

앱 로그에 저장된 설정 목록은 [Managed Browser에서 앱 보호 로그 검토](app-protection-policy-settings-log.md)를 참조하세요.

## <a name="security-and-privacy-for-the-managed-browser"></a>Managed Browser에 대한 보안 및 개인 정보

- Managed Browser에서는 사용자가 자신의 디바이스에서 기본 제공 브라우저에 대해 구성하는 설정을 사용하지 않습니다. Managed Browser는 이러한 설정에 액세스할 수 없습니다.

- Managed Browser와 연결된 앱 보호 정책에서 **액세스용 단순 PIN 필요** 또는 **액세스용 회사 자격 증명 필요** 옵션을 구성하고 사용자가 인증 페이지에서 도움말 링크를 선택하는 경우에는, 정책의 차단 목록에 추가되었는지와 상관없이 모든 인터넷 사이트를 탐색할 수 있습니다.

- Managed Browser는 직접 액세스하는 사이트에 대한 액세스만 차단할 수 있습니다. 중간 서비스(변환 서비스 등)를 사용하여 사이트에 액세스하는 경우 액세스를 차단하지 않습니다.

- 인증 및 Intune 문서에 대한 액세스를 허용하기 위해 허용 또는 차단 목록 설정에서 **&#42;.microsoft.com**이 제외됩니다. 이 값은 항상 허용됩니다.

### <a name="turn-off-usage-data"></a>사용량 현황 데이터 해제
Microsoft는 Microsoft 제품 및 서비스를 개선하기 위해 Managed Browser의 성능 및 사용에 대한 익명의 데이터를 자동으로 수집합니다. 사용자는 디바이스에서 **사용량 현황 데이터** 설정을 사용하여 데이터의 수집을 해제할 수 있습니다. 이 데이터의 수집은 제어할 수 없습니다.

- iOS/iPadOS 디바이스에서 만료되거나 신뢰할 수 없는 인증서가 있는 웹 사이트를 사용자가 방문하면 해당 웹 사이트를 열 수 없습니다.

## <a name="next-steps"></a>다음 단계

- [앱 보호 정책이란?](app-protection-policy.md) 
