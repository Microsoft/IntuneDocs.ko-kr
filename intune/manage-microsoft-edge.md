---
title: Microsoft Intune과 함께 Microsoft Edge를 사용하여 웹 액세스 관리
titleSuffix: ''
description: Microsoft Edge와 함께 Intune 앱 보호 정책을 사용하여 항상 보호 기능을 갖춘 회사 웹 사이트에 액세스합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 06/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1a255391a2cf27a764da6122031fd0c9cbb64cf
ms.sourcegitcommit: cb76efd3db60a422a65478ebce83d3aea7b5eeed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66751361"
---
# <a name="manage-web-access-using-microsoft-edge-with-microsoft-intune"></a>Microsoft Intune과 함께 Microsoft Edge를 사용하여 웹 액세스 관리

Microsoft Edge와 함께 Intune 앱 보호 정책을 사용하면 항상 보호 기능을 갖춘 회사 웹 사이트에 액세스할 수 있습니다. Intune 정책을 통해 사용할 수 있는 다음 Microsoft Edge 엔터프라이즈 기능이 제공됩니다. 이 엔터프라이즈 기능에는 다음이 포함됩니다.

1.  **이중 ID** - 사용자는 검색을 위해 회사 계정뿐 아니라 개인 계정을 추가할 수 있습니다. Office 365 및 Outlook의 아키텍처 및 환경과 비슷한 두 ID는 완전히 분리됩니다. Intune 관리자는 회사 계정 내에서 보호된 검색 환경에 대해 원하는 정책을 설정할 수 있습니다.
2.  **Intune 앱 보호 정책 통합** – Microsoft Edge는 Intune SDK와 통합되므로 앱 보호 정책을 대상으로 지정하여 데이터 손실 보호를 보장할 수 있습니다. 이러한 기능에는 잘라내기, 복사 및 붙여넣기 제어, 화면 캡처 방지, 사용자가 선택한 링크가 다른 관리 앱에서만 열리도록 하는 기능이 포함됩니다.
3.  **Azure 애플리케이션 프록시 통합** - SaaS 앱 및 웹앱에 대한 액세스를 제어할 수 있으므로, 최종 사용자가 회사 네트워크에서 연결하든지, 인터넷에서 연결하든지 관계없이 브라우저 기반 앱이 Microsoft Edge 브라우저에서만 실행되도록 할 수 있습니다.
4.  **애플리케이션 구성** - 애플리케이션 구성 설정을 활용하여 조직의 보안 태세를 강화하고 최종 사용자가 사용하기 쉬운 기능을 구성할 수 있습니다. 예를 들어 책갈피, 홈 페이지 바로 가기, 허용/차단된 사이트, Azure 애플리케이션 프록시 등을 정의할 수 있습니다.
Microsoft Edge에 대한 Microsoft Intune 보호 정책을 통해 조직의 데이터 및 리소스를 보호할 수 있습니다. 이러한 정책을 Microsoft Edge와 함께 사용하면 회사의 리소스는 기본적으로 설치된 앱 내에서는 물론 웹 브라우저를 통해 액세스할 때도 보호됩니다.

## <a name="getting-started"></a>시작하기

최종 사용자는 조직에서 사용할 수 있도록 공개 앱 스토어에서 Microsoft Edge를 다운로드할 수 있습니다. 브라우저 정책에 대한 운영 체제 요구 사항:
- Android 4 이상
- iOS 8.0 이상

## <a name="application-protection-policies-for-microsoft-edge"></a>Microsoft Edge에 대한 애플리케이션 보호 정책

Microsoft Edge는 Intune SDK와 통합되어 있으므로 다음과 같은 애플리케이션 보호 정책을 적용할 수 있습니다.
- 잘라내기, 복사 및 붙여넣기 사용 제어
- 화면 캡처 방지
- 회사 링크가 관리되는 앱 및 브라우저 내에서만 열리는지 확인

자세한 내용은 [앱 보호 정책이란?]을 참조하세요.
이러한 설정을 적용할 수 있는 장치는 다음과 같습니다.
- Intune에 등록된 디바이스
- 다른 MDM 제품에 등록된 장치
- 관리되지 않는 디바이스

Microsoft Edge가 Intune 정책을 대상으로 지정하지 않은 경우, 사용자가 이를 사용하여 Office 앱과 같은 다른 Intune 관리 애플리케이션의 데이터에 액세스할 수 없습니다. 

## <a name="conditional-access-for-microsoft-edge"></a>Microsoft Edge용 조건부 액세스

Azure AD 조건부 액세스를 사용하여 Microsoft Edge를 통해서만 회사 콘텐츠에 액세스하도록 사용자를 리디렉션할 수 있습니다. 이렇게 하면 Azure AD 연결 웹앱에 대한 모바일 브라우저 액세스가 정책에 따라 보호되는 Microsoft Edge로 제한됩니다. 그러면 Safari 또는 Chrome과 같은 다른 보호되지 않는 브라우저에서 액세스를 차단합니다. 조건부 액세스는 Exchange Online 및 SharePoint Online과 같은 Azure 리소스, Microsoft 365 관리 센터 및 [Azure AD 애플리케이션 프록시](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)를 통해 외부 사용자에게 노출한 온-프레미스 사이트에도 적용될 수 있습니다.

iOS 및 Android에서 Microsoft Edge를 사용하도록 Azure AD 연결 웹앱을 제한하려면 다음 단계를 따릅니다.
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. Intune 노드에서 **조건부 액세스** > **새 정책**을 선택합니다.
3. 다음으로 블레이드의 **액세스 제어** 섹션에서 **권한 부여**를 선택합니다.
4. **승인된 클라이언트 앱 필요**를 클릭합니다.
5. **권한 부여** 블레이드에서 **선택**을 클릭합니다. 이 정책은 Intune Managed Browser 앱에만 액세스할 수 있도록 하려는 클라우드 앱에 할당되어야 합니다.

    ![조건부 액세스 정책 - 권한 부여](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. 할당 섹션에서 조건 > 클라이언트 앱을 선택합니다. 클라이언트 앱 블레이드가 표시됩니다.
7. 구성 아래에서 [예]를 클릭하여 특정 클라이언트 앱에 정책을 적용합니다.
8. 브라우저가 클라이언트 앱으로 선택되었는지 확인하세요.

    ![조건부 액세스 정책 - 클라이언트 앱 선택](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > 이러한 클라우드 애플리케이션에 액세스할 수 있는 네이티브 앱(비 브라우저 앱)을 제한하려는 경우 **모바일 앱 및 데스크톱 클라이언트**를 선택할 수도 있습니다.

9. **할당** 섹션에서 **사용자 및 그룹**을 선택한 다음, 이 정책을 할당하려는 사용자 또는 그룹을 선택합니다.

    > [!NOTE]
    > 사용자는 또한 앱 구성 정책을 받으려면 Intune 앱 보호 정책을 사용해야 합니다. Intune 앱 보호 정책에 대한 자세한 내용은 [앱 보호 정책이란?](app-protection-policy.md)을 참조하세요.

10. **할당** 섹션에서 **클라우드 앱**을 선택하여 이 정책으로 보호할 앱을 선택합니다.

위의 정책이 구성되면 사용자는 Microsoft Edge를 사용하여 이 정책으로 보호한 Azure AD 연결 웹앱에 액세스해야 합니다. 사용자가 이 시나리오에서 관리되지 않는 브라우저를 사용하려고 하면 Microsoft Edge를 사용해야 한다는 메시지가 표시됩니다.

> [!TIP]
> 조건부 액세스는 Azure AD(Azure Active Directory) 기술입니다. Intune에서 액세스하는 조건부 액세스 노드는 Azure AD에서 액세스한 것과 동일한 노드입니다.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>정책으로 보호되는 브라우저에서 Azure AD 연결 웹앱에 Single Sign-On

iOS 및 Android의 Microsoft Edge는 Azure AD에 연결된 모든 웹앱(SaaS 및 온-프레미스)에 SSO를 활용할 수 있습니다. SSO를 사용하면 사용자가 자격 증명을 다시 입력하지 않고도 Microsoft Edge를 통해 Azure AD 연결 웹앱에 액세스할 수 있습니다.

SSO를 사용하려면 iOS 디바이스용 Microsoft Authenticator 앱 또는 Android의 Intune 회사 포털 중 하나에서 디바이스를 등록해야 합니다. 사용자가 Authenticator 앱 또는 Intune 회사 포털을 가지고 있을 때 디바이스가 아직 등록되지 않은 경우, 정책으로 보호되는 브라우저에서 Azure AD 연결 웹앱으로 이동할 때 해당 디바이스를 등록하라는 메시지가 표시됩니다. 디바이스가 Intune에서 관리되는 사용자의 계정으로 등록되면 해당 계정은 Azure AD 연결 웹앱에서 SSO를 사용하도록 설정합니다.

> [!NOTE]
> 디바이스 등록은 Azure AD 서비스를 사용하는 간단한 체크 인입니다. 전체 디바이스를 등록할 필요가 없고 디바이스에 대한 추가 권한을 부여하지 않습니다.

## <a name="create-a-protected-browser-app-configuration"></a>보호된 브라우저 앱 구성 만들기

앱 구성을 적용하려면 사용자의 보호되는 브라우저 또는 디바이스의 다른 앱이 [Intune 앱 보호 정책](app-protection-policy.md)을 통해 이미 관리되고 있어야 합니다.

다음 단계는 보호된 브라우저 앱 구성을 만드는 데 사용됩니다.

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **클라이언트 앱** > **앱 구성 정책** > **추가**를 선택합니다.
3. **구성 정책 추가** 블레이드에서 앱 구성 설정에 대한 **이름** 및 **설명**(선택 사항)을 입력합니다.
4. **디바이스 등록** 유형에 **관리되는 앱**를 선택합니다.
5. **필수 앱 선택**을 선택하고 **대상 앱** 블레이드에서 iOS나 Android 중 하나 또는 둘 다에 대해 **Managed Browser** 및/또는 **Edge**를 선택합니다.
6. **확인**을 선택하여 **구성 정책 추가** 블레이드로 돌아옵니다.
7. **구성 설정**을 선택합니다. **구성** 블레이드에서 키와 값 쌍을 정의하여 Microsoft Edge에 대한 구성을 제공합니다. 이 문서의 뒷부분에 나오는 섹션에서 정의할 수 있는 다양한 키와 값 쌍에 대해 알아보세요.

    > [!NOTE]
    > Microsoft Edge는 Managed Browser와 동일한 키와 값 쌍을 사용합니다. 

8.  작업이 끝나면 **확인**을 클릭합니다.
9.  **구성 정책 추가** 블레이드에서 **추가**를 선택합니다.<br>
    새 구성이 생성되어 **앱 구성** 블레이드에 표시됩니다.

## <a name="assign-the-configuration-settings-you-created"></a>작성한 구성 설정을 할당합니다. 

Azure AD 사용자 그룹에 설정을 할당합니다. 해당 사용자가 대상이 지정된 보호되는 브라우저 앱을 설치한 경우에는 지정한 설정을 통해 앱이 관리됩니다.

1. Intune 모바일 애플리케이션 관리 대시보드의 **클라이언트 앱** 블레이드에서 **앱 구성 정책**을 선택합니다.
2. 앱 구성 목록에서 할당하려는 구성을 선택합니다.
3. 다음 블레이드에서 **할당**을 선택합니다.
4. **할당** 블레이드에서 앱 구성을 할당할 Azure AD 그룹을 선택하고 **확인**을 선택합니다.

## <a name="how-to-configure-application-proxy-settings-for-protected-browsers"></a>보호되는 브라우저에 대한 애플리케이션 프록시 설정을 구성하는 방법

Microsoft Edge와 [Azure AD 애플리케이션 프록시](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)를 함께 사용하여 사용자가 모바일 디바이스의 인트라넷 사이트에 액세스할 수 있습니다. 

다음은 AD 애플리케이션 프록시를 사용하도록 설정한 시나리오의 몇 가지 예입니다. 

- 사용자가 Intune을 통해 보호되는 Outlook 모바일 앱을 사용 중입니다. 그런 다음, 이메일의 인트라넷 사이트에 대한 링크를 클릭하면 Microsoft Edge는 이 인트라넷 사이트가 애플리케이션 프록시를 통해 사용자에게 노출되었음을 인식합니다. 사용자는 인트라넷 사이트에 연결하기 전에 적용 가능한 다단계 인증 및 조건부 액세스를 사용하여 인증하도록 애플리케이션 프록시를 통해 자동으로 라우팅됩니다. 이제 사용자는 자신의 모바일 디바이스에서도 내부 사이트에 액세스할 수 있으며 Outlook의 링크는 예상대로 작동합니다.
- 사용자가 iOS 또는 Android 디바이스에서 Microsoft Edge를 엽니다. Microsoft Edge가 Intune으로 보호되고 애플리케이션 프록시가 활성화된 경우 사용자는 사용하는 내부 URL을 통해 인트라넷 사이트로 이동할 수 있습니다. Microsoft Edge는 이 인트라넷 사이트가 애플리케이션 프록시를 통해 사용자에게 노출되었고 사용자가 자동으로 애플리케이션 프록시를 통해 라우팅되어 인트라넷 사이트에 도달하기 전에 인증된다는 것을 인식합니다. 

### <a name="before-you-start"></a>시작하기 전에

- Azure AD 애플리케이션 프록시를 통해 내부 애플리케이션을 설정합니다.
    - 애플리케이션 프록시를 구성하고 애플리케이션을 게시하려면 [설정 설명서](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)를 참조하세요.
- Microsoft Edge 앱에 [Intune 앱 보호 정책](app-protection-policy.md)이 할당되어 있어야 합니다.

> [!NOTE]
> 업데이트된 애플리케이션 프록시 리디렉션 데이터는 Managed Browser 및 Microsoft Edge에 적용되는 데 최대 24시간이 걸릴 수 있습니다.

#### <a name="step-1-enable-automatic-redirection-to-a-protected-browser-from-outlook"></a>1단계: Outlook에서 보호되는 브라우저로 자동 리디렉션 사용 설정
**정책 관리형 브라우저와 웹 콘텐츠 공유** 설정을 사용하도록 설정하는 앱 보호 정책으로 Outlook이 구성되어 있어야 합니다.

![앱 보호 정책 - 정책 관리형 브라우저와 웹 콘텐츠 공유](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>2단계: 앱 프록시를 사용하도록 앱 구성 설정을 설정
Microsoft Edge에 대한 애플리케이션 프록시를 사용하도록 설정하려면 아래 키/값 쌍을 사용하여 Microsoft Edge를 대상으로 지정합니다.

|    Key    |    값    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

온-프레미스 웹앱에 원활한(및 보호된) 액세스와 함께 Microsoft Edge 및 Azure AD 애플리케이션 프록시를 사용하는 방법에 대한 자세한 내용은 Enterprise Mobility + Security 블로그 게시물 [연계를 통해 성능 향상: 사용자 액세스를 개선하려는 Intune 및 Azure Active Directory 팀](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access)을 참조하세요. 이 블로그 게시물은 Intune Managed Browser를 참조하지만 콘텐츠는 Microsoft Edge에도 적용됩니다.

## <a name="how-to-configure-a-homepage-shortcut-for-microsoft-edge"></a>Microsoft Edge에 대한 홈페이지 바로 가기를 구성하는 방법

이 설정을 사용하면 Microsoft Edge에 대한 홈페이지 바로 가기를 구성할 수 있습니다.  Microsoft Edge에서 새 탭을 열면 구성한 홈페이지 바로 가기가 검색 창 아래에 첫 번째 아이콘으로 나타납니다. 사용자는 관리 컨텍스트에서 이 바로 가기를 편집하거나 삭제할 수 없습니다. 홈페이지 바로 가기에는 구분을 위해 조직 이름이 표시됩니다. 

아래 키/값 쌍을 사용하여 홈페이지 바로 가기를 구성합니다.

|    Key    |    값    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    유효한 URL을 지정합니다. 잘못된 URL은 보안 조치로 차단됩니다.<br>**예:** `<https://www.bing.com`>
    |

## <a name="how-to-configure-managed-bookmarks-for-microsoft-edge"></a>Microsoft Edge에 대한 관리 책갈피를 구성하는 방법

액세스의 편의성을 위해 Microsoft Edge를 사용할 때 사용자가 사용할 책갈피를 구성할 수 있습니다. 다음은 몇 가지 세부 정보입니다.

- 이 책갈피는 사용자가 Microsoft Edge의 회사 모드를 사용할 때만 나타납니다. 
- 이 책갈피는 사용자가 삭제하거나 수정할 수 없습니다.
- 이 책갈피는 목록 맨 위에 표시됩니다. 사용자가 만드는 모든 책갈피는 이 책갈피 아래에 표시됩니다.
- 앱 프록시 리디렉션을 사용한 경우 내부 또는 외부 URL 중 하나를 사용하여 앱 프록시 웹앱을 추가할 수 있습니다.

관리 책갈피를 구성하려면 다음 키/값 쌍을 사용합니다.

|    Key    |    값    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    이 구성에 대한 값은 책갈피 목록입니다. 각 책갈피는 책갈피 제목과 책갈피 URL로 이루어져 있습니다. 제목과 URL을 `|` 문자로 구분합니다.      **예:**<br>`Microsoft Bing|https://www.bing.com`<p>여러 책갈피를 구성하려면 각 쌍을 이중 문자 `||`로 구분합니다.<p>**예:**<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="how-to-display-myapps-within-microsoft-edge-bookmarks"></a>Microsoft Edge 책갈피 내에 MyApps를 표시하는 방법

기본적으로 사용자에게 Microsoft Edge 책갈피 폴더 내에 구성된 MyApps 사이트가 표시됩니다. 폴더에는 조직의 이름으로 레이블이 지정됩니다.

|    Key    |    값    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True**는 Microsoft Edge 책갈피 내에 MyApps를 표시합니다.<p>**False**는 Microsoft Edge 내에서 MyApps를 숨깁니다.    |

## <a name="how-to-specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Microsoft Edge에 대해 허용되거나 차단된 사이트 목록을 지정하는 방법
앱 구성을 사용하여 사용자가 작업 프로필을 사용할 때 액세스할 수 있는 사이트를 정의할 수 있습니다. 허용 목록을 사용하면 사용자는 명시적으로 나열한 사이트에만 액세스할 수 있습니다. 차단된 목록을 사용하면 사용자는 명시적으로 차단된 사이트를 제외한 모든 사이트에 액세스할 수 있습니다. 허용 목록이나 차단 목록 중 하나만 적용해야 하며, 둘 다 적용해서는 안됩니다. 둘 다를 디바이스에 대상으로 하면 허용된 목록이 적용됩니다.  

아래의 키/값 쌍을 사용하여 Microsoft Edge에 대해 허용되거나 차단된 사이트 목록을 구성할 수 있습니다. 올바른 URL 형식에 대한 자세한 내용을 보려면 계속 읽어보세요. 

|    Key    |    값    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    다음 중에서 선택합니다.<p>1. 허용되는 URL을 지정합니다(이러한 URL만 허용되며 다른 사이트에 액세스할 수 없음).<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. 차단되는 URL을 지정합니다(다른 모든 사이트는 액세스할 수 있음).<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    키에 해당하는 값은 URL 목록입니다. 허용하거나 차단할 모든 URL을 파이프 `|` 문자로 구분된 단일 값으로 입력합니다.<p>**예:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>허용되거나 차단된 사이트 목록의 URL 형식 
다양한 URL 형식을 사용하여 허용/차단된 사이트 목록을 작성할 수 있습니다. 이러한 허용되는 패턴은 아래 표에 자세히 설명되어 있습니다. 시작하기 전에 다음과 같은 몇 가지 참고 사항이 있습니다. 
- URL을 목록에 입력할 때 모든 URL의 앞에 **http** 또는 **https** 를 덧붙여야 합니다.
- 다음과 같이 허용되는 패턴 목록의 규칙에 따라 와일드카드 기호(*)를 사용할 수 있습니다.
- 주소에 포트 번호를 지정할 수 있습니다. 포트 번호를 지정하지 않으면 다음 값이 사용됩니다.
    - http의 경우 포트 80
    - https의 경우 포트 443
- 포트 번호에 대한 와일드카드 사용은 지원되지 **않습니다**. 예를 들어 `http://www.contoso.com:*` 및 `http://www.contoso.com:*/`은 지원되지 않습니다.

    |    URL    |    세부 정보    |    일치하는 항목    |    일치하지 않는 항목    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    단일 페이지와 일치    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    단일 페이지와 일치    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/&#42;`   |    `www.contoso.com`으로 시작하는 모든 URL과 일치    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    `contoso.com` 아래의 모든 하위 도메인과 일치    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`    |
    |    `http://www.contoso.com/images`    |    단일 폴더와 일치    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    포트 번호를 사용하여 단일 페이지와 일치    |    http://www.contoso.com:80    |         |
    |    `https://www.contoso.com`    |    안전한 단일 페이지와 일치    |    `https://www.contoso.com`    |    `http://www.contoso.com`    |
    |    `http://www.contoso.com/images/*`    |    단일 폴더 및 모든 하위 폴더와 일치    |    `www.contoso.com/images/dogs`<br>`www.contoso.com/images/cats`    |    `www.contoso.com/videos`    |
  
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
  
## <a name="defining-behavior-when-users-try-to-access-a-blocked-site"></a>사용자가 차단된 사이트에 액세스하려고 할 때 동작 정의

Microsoft Edge에 기본 제공된 이중 ID 모델을 사용하면 Intune Managed Browser에서는 불가능했던 최종 사용자에게 보다 유연한 환경을 제공할 수 있습니다. 사용자가 Microsoft Edge에서 차단된 사이트에 방문하면 회사 리소스를 안전하게 유지하면서 작업 컨텍스트 대신 해당 개인 컨텍스트에서 링크를 열라는 메시지를 표시할 수 있습니다. 예를 들어 사용자가 Outlook을 통해 뉴스 기사에 대한 링크를 보내면 개인 컨텍스트에서 또는 뉴스 웹 사이트를 허용하지 않는 작업 컨텍스트 대신 개인 컨텍스트 또는 InPrivate 탭에서 링크를 열 수 있습니다. 기본적으로 이러한 전환이 허용됩니다.

이러한 소프트 전환이 허용되는지 여부를 구성하려면 아래 키/값 쌍을 사용합니다.

|    Key    |    값    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True**이면 Microsoft Edge에서 사용자를 개인 컨텍스트로 전환하여 차단된 사이트를 열 수 있습니다.<p>**블록**은 Microsoft Edge가 사용자를 전환하는 것을 방지하며 사용자에게는 액세스하려는 사이트가 차단되었다는 메시지 표시됩니다.    |

## <a name="directing-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Intune Managed Browser 대신 Microsoft Edge로 사용자 연결 

Intune Managed Browser와 Microsoft Edge는 이제 정책으로 보호되는 브라우저로 사용할 수 있습니다. 사용자에게 올바른 브라우저 앱을 사용하도록 지시하려면 다음 구성 설정으로 모든 Intune 관리 앱(예: Outlook 및 OneDrive)을 대상으로 지정합니다.

|    Key    |    값    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    값 `true`는 사용자에게 Microsoft Edge를 사용하도록 지시합니다.<p>값 `false`는 사용자에게 Intune Managed Browser를 사용하도록 지시합니다.    |

이 앱 구성 값을 설정하지 않은 경우 다음 논리는 회사 링크를 여는 데 사용되는 브라우저를 정의합니다.

Android:
- 사용자가 Intune Managed Browser와 Microsoft Edge를 둘 다 해당 디바이스에 다운로드한 경우에는 Intune Managed Browser가 실행됩니다. 
- 디바이스에 Microsoft Edge만 다운로드되고 Intune 정책을 대상으로 하는 경우 Microsoft Edge가 열립니다.
- 디바이스에 Managed Browser만 있고 Intune 정책을 대상으로 하는 경우 Managed Browser가 열립니다.

iOS, iOS용 Intune SDK v. 9.0.9+를 통합한 앱:
- Managed Browser와 Microsoft Edge가 모두 디바이스에 있는 경우 Intune Managed Browser가 실행됩니다.  
- 디바이스에 Microsoft Edge만 있고 Intune 정책의 대상으로 지정된 경우 Microsoft Edge가 실행됩니다.
- 디바이스에 Managed Browser만 있고 정책의 Intune 대상으로 지정된 경우 Managed Browser.

## <a name="using-microsoft-edge-on-ios-to-access-managed-app-logs"></a>iOS에서 Microsoft Edge를 사용하여 관리 앱 로그에 액세스 

iOS 디바이스에 Microsoft Edge가 설치된 최종 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있습니다. 관리되는 iOS 앱의 문제를 해결하기 위해 로그를 보낼 수 있습니다.
1. iOS 디바이스에서 Microsoft Edge를 엽니다.
2. 주소 상자에 `about:intunehelp`를 입력합니다. 
3. 문제 해결 모드는 Microsoft Edge 내에서 시작됩니다.

앱 로그에 저장된 설정 목록은 [Managed Browser에서 앱 보호 로그 검토](app-protection-policy-settings-log.md)를 참조하세요.

Android 디바이스의 로그를 보는 방법을 확인하려면 [이메일을 통해 IT 관리자에게 로그 보내기](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)를 참조하세요. 

## <a name="security-and-privacy-for-microsoft-edge"></a>Microsoft Edge에 대한 보안 및 개인 정보

Microsoft Edge에 대한 추가 보안 및 개인 정보 고려 사항:

- Microsoft Edge는 이러한 설정에 액세스할 수 없기 때문에 사용자가 해당 디바이스의 기본 브라우저에 대해 설정한 설정을 사용하지 않습니다.
- Microsoft Edge와 연결된 앱 보호 정책에서 **액세스용 단순 PIN 필요** 또는 **액세스용 회사 자격 증명 필요** 옵션을 구성하고 사용자가 인증 페이지에서 도움말 링크를 선택하는 경우에는, 정책의 차단 목록에 추가되었는지와 상관없이 모든 인터넷 사이트를 탐색할 수 있습니다.
- Microsoft Edge는 직접 액세스하는 사이트에 대한 액세스만 차단할 수 있습니다. 중간 서비스(변환 서비스 등)를 사용하여 사이트에 액세스하는 경우 액세스를 차단하지 않습니다.
- 인증 및 Intune 문서에 대한 액세스를 허용하기 위해 허용 또는 차단 목록 설정에서 * **.microsoft.com**이 제외됩니다. 이 값은 항상 허용됩니다.
사용량 데이터 끄기: Microsoft는 Microsoft 제품 및 서비스를 개선하기 위해 Managed Browser의 성능 및 사용에 대한 익명의 데이터를 자동으로 수집합니다. 사용자는 디바이스에서 **사용 데이터** 설정을 사용하여 데이터의 수집을 해제할 수 있습니다. 이 데이터의 수집은 제어할 수 없습니다. iOS 디바이스에서 만료되거나 신뢰할 수 없는 인증서가 있는 웹 사이트를 사용자가 방문하면 해당 웹 사이트를 열 수 없습니다.

## <a name="next-steps"></a>다음 단계

- [앱 보호 정책이란?](app-protection-policy.md) 
