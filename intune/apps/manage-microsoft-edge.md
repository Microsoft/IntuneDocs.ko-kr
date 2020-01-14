---
title: Intune을 사용하여 iOS 및 Android용 Microsoft Edge 관리
titleSuffix: ''
description: Microsoft Edge와 함께 Intune 앱 보호 정책을 사용하여 항상 보호 기능을 갖춘 회사 웹 사이트에 액세스합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3fb2f050-ec94-42ab-be05-c3d4101148bb
ms.reviewer: ilwu
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 304a6a60ea8dbfa98e62eb8e52a69e14af795746
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75548006"
---
# <a name="manage-web-access-by-using-microsoft-edge-with-microsoft-intune"></a>Microsoft Intune과 함께 Microsoft Edge를 사용하여 웹 액세스 관리

Microsoft Edge와 함께 Intune 앱 보호 정책을 사용하면 항상 보호 기능을 갖춘 회사 웹 사이트에 액세스할 수 있습니다. Intune 정책을 통해 다음 Microsoft Edge 엔터프라이즈 기능으 사용할 수 있습니다.

- **이중 ID.** 사용자는 검색을 위해 회사 계정뿐 아니라 개인 계정을 추가할 수 있습니다. Office 365 및 Outlook의 아키텍처 및 환경과 비슷한 두 ID는 완전히 분리됩니다. Intune 관리자는 회사 계정 내에서 보호된 검색 환경을 위해 원하는 정책을 설정할 수 있습니다.
- **Intune 앱 보호 정책 통합.** Microsoft Edge는 Intune SDK와 통합되므로 앱 보호 정책을 대상으로 지정하여 데이터 손실을 방지할 수 있습니다. 이러한 기능에는 잘라내기, 복사 및 붙여넣기 제어, 화면 캡처 방지, 사용자가 선택한 링크가 다른 관리형 앱에서만 열리도록 하는 기능이 포함됩니다.
- **Azure 애플리케이션 프록시 통합.** SaaS(Software as a Service) 앱 및 웹앱의 액세스를 제어할 수 있습니다. 따라서 최종 사용자가 회사 네트워크에서 연결하든지, 인터넷에서 연결하든지 관계없이 브라우저 기반 앱이 보안 Microsoft Edge 브라우저에서만 실행되도록 할 수 있습니다.
- **애플리케이션 구성.** 애플리케이션 구성 설정을 활용하여 조직의 보안 상태를 강화하고 최종 사용자가 사용하기 쉬운 기능을 구성할 수 있습니다. 예를 들어 책갈피, 홈페이지 바로 가기, 허용/차단된 사이트, Azure Active Directory(Azure AD) 애플리케이션 프록시 등을 정의할 수 있습니다.

Microsoft Edge에 대한 Microsoft Intune 보호 정책을 통해 조직의 데이터 및 리소스를 보호할 수 있습니다. 이러한 정책을 Microsoft Edge와 함께 사용하면 회사의 리소스는 기본적으로 설치된 앱 내에서는 물론 웹 브라우저를 통해 액세스할 때도 보호됩니다.

## <a name="getting-started"></a>시작하기

최종 사용자는 조직에서 사용할 수 있도록 공개 앱 스토어에서 Microsoft Edge를 다운로드할 수 있습니다. 브라우저 정책에 관한 운영 체제 요구 사항은 다음과 같습니다.
- Android 4 이상
- iOS 8.0 이상

## <a name="application-protection-policies-for-microsoft-edge"></a>Microsoft Edge에 대한 애플리케이션 보호 정책

Microsoft Edge는 Intune SDK와 통합되어 있으므로 둘 다에 애플리케이션 보호 정책을 적용할 수 있습니다.

이러한 설정을 적용할 수 있는 장치는 다음과 같습니다.
- Intune에 등록된 디바이스
- 다른 모바일 디바이스 관리 제품에 등록된 디바이스
- 관리되지 않는 디바이스

Microsoft Edge가 Intune 정책을 대상으로 지정하지 않은 경우, 사용자가 이를 사용하여 Office 앱과 같은 다른 Intune 관리 애플리케이션의 데이터에 액세스할 수 없습니다. 

## <a name="conditional-access-for-microsoft-edge"></a>Microsoft Edge용 조건부 액세스

Azure AD 조건부 액세스를 사용하여 Microsoft Edge를 통해서만 회사 콘텐츠에 액세스하도록 사용자를 리디렉션할 수 있습니다. 이렇게 하면 Azure AD 연결 웹앱의 모바일 브라우저 액세스가 정책에 따라 보호되는 Microsoft Edge로 제한됩니다. 그러면 Safari 또는 Chrome과 같은 다른 보호되지 않는 브라우저에서의 액세스를 차단합니다. 조건부 액세스를 Exchange Online 및 SharePoint Online과 같은 Azure 리소스, Microsoft 365 관리 센터 및 [Azure AD 애플리케이션 프록시](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)를 통해 외부 사용자에게 노출한 온-프레미스 사이트에도 적용될 수 있습니다.

iOS 및 Android에서 Microsoft Edge를 사용하도록 Azure AD 연결 웹앱을 제한하려면
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. Intune 노드에서 **조건부 액세스** > **새 정책**을 선택합니다.
3. 창의 **액세스 제어** 섹션에서 **권한 부여**를 선택합니다.
4. **승인된 클라이언트 앱 필요**를 선택합니다.
5. **권한 부여** 창에서 **선택**을 선택합니다. 이 정책은 Intune Managed Browser 앱에만 액세스할 수 있도록 하려는 클라우드 앱에 할당되어야 합니다.

    ![조건부 액세스 정책 - 권한 부여의 스크린샷](./media/manage-microsoft-edge/manage-microsoft-edge-01.png)

6. 할당 섹션에서 **조건** > **앱**을 선택합니다. **앱** 창이 표시됩니다.
7. **구성** 아래에서 **예**를 선택하여 특정 클라이언트 앱에 정책을 적용합니다.
8. **브라우저**가 클라이언트 앱으로 선택되었는지 확인하세요.

    ![조건부 액세스 정책 - 클라이언트 앱 선택의 스크린샷](./media/manage-microsoft-edge/manage-microsoft-edge-02.png)

    > [!NOTE]
    > 이러한 클라우드 애플리케이션에 액세스할 수 있는 네이티브 앱(비 브라우저 앱)을 제한하려는 경우 **모바일 앱 및 데스크톱 클라이언트**를 선택할 수도 있습니다.

9. **할당** 섹션에서 **사용자 및 그룹**을 선택한 다음, 이 정책을 할당하려는 사용자 또는 그룹을 선택합니다.

10. **할당** 섹션에서 **클라우드 앱**을 선택하여 이 정책으로 보호할 앱을 선택합니다.

위의 정책이 구성되면 사용자는 Microsoft Edge를 사용하여 이 정책으로 보호한 Azure AD 연결 웹앱에 액세스해야 합니다. 사용자가 이 시나리오에서 비관리형 브라우저를 사용하려고 하면 Microsoft Edge를 사용해야 한다는 메시지가 표시됩니다.

> [!TIP]
> 조건부 액세스는 Azure AD 기술입니다. Intune에서 액세스하는 조건부 액세스 노드는 Azure AD에서 액세스한 것과 동일한 노드입니다.

## <a name="single-sign-on-to-azure-ad-connected-web-apps-in-policy-protected-browsers"></a>정책으로 보호되는 브라우저에서 Azure AD 연결 웹앱에 Single Sign-On

iOS 및 Android의 Microsoft Edge는 Azure AD에 연결된 모든 웹앱(SaaS 및 온-프레미스)에 SSO(Single Sign-On)를 활용할 수 있습니다. SSO를 사용하면 사용자가 자격 증명을 다시 입력하지 않고도 Microsoft Edge를 통해 Azure AD 연결 웹앱에 액세스할 수 있습니다.

SSO를 사용하려면 iOS 디바이스용 Microsoft Authenticator 앱 또는 Android의 Intune 회사 포털 중 하나에서 디바이스를 등록해야 합니다. 사용자가 이 둘 중 하나를 가지고 있으면 정책으로 보호되는 브라우저에서 Azure AD 연결 웹앱으로 이동할 때 해당 디바이스를 등록하라는 메시지가 표시됩니다. (이는 디바이스가 아직 등록되지 않은 경우에만 해당됩니다.) 디바이스가 Intune에서 관리되는 사용자의 계정으로 등록되면 해당 계정은 Azure AD 연결 웹앱에서 SSO를 사용하도록 설정됩니다.

> [!NOTE]
> 디바이스 등록은 Azure AD 서비스를 사용하는 간단한 체크 인입니다. 전체 디바이스를 등록할 필요가 없고 디바이스에 대한 추가 권한을 IT에 부여하지 않습니다.

## <a name="create-a-protected-browser-app-configuration"></a>보호된 브라우저 앱 구성 만들기

Microsoft Edge의 앱 구성을 만들려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **앱 구성 정책** > **추가**를 선택합니다.
3. **구성 정책 추가** 창에서 앱 구성 설정에 대한 **이름** 및 **설명**(선택 사항)을 입력합니다.
4. **디바이스 등록** 유형에 **관리되는 앱**를 선택합니다.
5. **필수 앱 선택**을 선택하고 **대상 앱** 창에서 iOS나 Android 중 하나 또는 둘 다에 대해 **Managed Browser** 또는 **Edge**를 선택합니다.
6. **확인**을 선택하여 **구성 정책 추가** 창으로 돌아옵니다.
7. **구성 설정**을 선택합니다. **구성** 창에서 키와 값 쌍을 정의하여 Microsoft Edge에 대한 구성을 제공합니다. 이 문서의 뒷부분에 나오는 섹션에서 정의할 수 있는 다양한 키와 값 쌍에 대해 알아보세요.

    > [!NOTE]
    > Microsoft Edge는 Managed Browser와 동일한 키와 값 쌍을 사용합니다. Android에서 앱 구성 정책을 적용하려면 Microsoft Edge를 앱 보호 정책 대상으로 지정해야 합니다.

8. 작업이 완료되면 **확인**을 선택합니다.
9. **구성 정책 추가** 창에서 **추가**를 선택합니다.<br>
    새 구성이 생성되어 **앱 구성** 창에 표시됩니다.

## <a name="assign-the-configuration-settings-you-created"></a>작성한 구성 설정을 할당합니다. 

Azure AD의 사용자 그룹에 설정을 할당합니다. 해당 사용자가 대상이 지정된 보호되는 브라우저 앱을 설치한 경우에는 지정한 설정을 통해 앱이 관리됩니다.

1. Intune 모바일 애플리케이션 관리 대시보드의 **앱** 창에서 **앱 구성 정책**을 선택합니다.
2. 앱 구성 목록에서 할당하려는 구성을 선택합니다.
3. 다음 창에서 **할당**을 선택합니다.
4. **할당** 창에서 앱 구성을 할당할 Azure AD 그룹을 선택하고 **확인**을 선택합니다.

## <a name="direct-users-to-microsoft-edge-instead-of-the-intune-managed-browser"></a>Intune Managed Browser 대신 Microsoft Edge로 사용자 연결 

Intune Managed Browser와 Microsoft Edge 모두 정책으로 보호되는 브라우저로 사용할 수 있습니다. 사용자에게 올바른 브라우저 앱을 사용하도록 지시하려면 다음 구성 설정으로 모든 Intune 관리 앱(예: Outlook, OneDrive 및 SharePoint)을 대상으로 지정합니다.

|    Key    |    값    |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.useEdge`    |    값 `true`는 사용자에게 Microsoft Edge를 다운로드하고 사용하도록 지시합니다.<br>값 `false`를 사용하면 사용자가 Intune Managed Browser를 사용할 수 있습니다.    |

이 앱 구성 값을 설정하지 **않은** 경우 다음 논리는 회사 링크를 여는 데 사용되는 브라우저를 정의합니다.

Android:
- 사용자가 Intune Managed Browser와 Microsoft Edge를 둘 다 해당 디바이스에 있는 경우에는 Intune Managed Browser가 실행됩니다. 
- 디바이스에 Microsoft Edge만 다운로드되고 Intune 정책을 대상으로 하는 경우 Microsoft Edge가 실행됩니다.
- 디바이스에 Managed Browser만 있고 Intune 정책의 대상으로 지정된 경우 Managed Browser가 실행됩니다.

iOS, iOS용 Intune SDK v. 9.0.9+를 통합한 앱:
- Managed Browser와 Microsoft Edge가 모두 디바이스에 있는 경우 Intune Managed Browser가 실행됩니다.  
- 디바이스에 Microsoft Edge만 있고 Intune 정책의 대상으로 지정된 경우 Microsoft Edge가 실행됩니다.
- 디바이스에 Managed Browser만 있고 Intune 정책의 대상으로 지정된 경우 Managed Browser가 실행됩니다.

## <a name="configure-application-proxy-settings-for-microsoft-edge"></a>Microsoft Edge의 애플리케이션 프록시 설정 구성

Microsoft Edge와 [Azure AD 애플리케이션 프록시](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)를 함께 사용하여 사용자가 모바일 디바이스의 인트라넷 사이트에 액세스하도록 할 수 있습니다. 

다음은 Azure AD 애플리케이션 프록시를 사용하도록 설정한 시나리오의 몇 가지 예입니다. 

- 사용자가 Intune을 통해 보호되는 Outlook 모바일 앱을 사용 중입니다. 그런 다음, 메일의 인트라넷 사이트에 대한 링크를 클릭하면 Microsoft Edge는 이 인트라넷 사이트가 애플리케이션 프록시를 통해 사용자에게 노출되었음을 인식합니다. 사용자는 인트라넷 사이트에 연결하기 전에 적용 가능한 다단계 인증 및 조건부 액세스를 사용하여 인증하도록 애플리케이션 프록시를 통해 자동으로 라우팅됩니다. 이제 사용자는 자신의 모바일 디바이스에서도 내부 사이트에 액세스할 수 있으며 Outlook의 링크는 올바로 작동합니다.
- 사용자가 iOS 또는 Android 디바이스에서 Microsoft Edge를 엽니다. Microsoft Edge가 Intune으로 보호되고 애플리케이션 프록시가 사용하도록 설정된 경우 사용자는 사용하던 내부 URL을 통해 인트라넷 사이트로 이동할 수 있습니다. Microsoft Edge는 이 인트라넷 사이트가 애플리케이션 프록시를 통해 사용자에게 공개되었음을 인식합니다. 사용자는 애플리케이션 프록시를 통해 자동으로 라우팅되어 인트라넷 사이트에 연결하기 전에 인증됩니다. 

### <a name="before-you-start"></a>시작하기 전에

- Azure AD 애플리케이션 프록시를 통해 내부 애플리케이션을 설정합니다.
  - 애플리케이션 프록시를 구성하고 애플리케이션을 게시하려면 [설정 설명서](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)를 참조하세요.
- Microsoft Edge 앱에 [Intune 앱 보호 정책](app-protection-policy.md)이 할당되어 있어야 합니다.

> [!NOTE]
> 업데이트된 애플리케이션 프록시 리디렉션 데이터는 Managed Browser 및 Microsoft Edge에 적용되는 데 최대 24시간이 걸릴 수 있습니다.

#### <a name="step-1-enable-automatic-redirection-to-microsoft-edge-from-outlook"></a>1단계: Outlook에서 Microsoft Edge로 자동 리디렉션 사용 설정
**정책 관리형 브라우저와 웹 콘텐츠 공유** 설정을 사용하도록 설정하는 앱 보호 정책으로 Outlook을 구성합니다.

![앱 보호 정책 - 정책 관리형 브라우저와 웹 콘텐츠 공유의 스크린샷](./media/manage-microsoft-edge/manage-microsoft-edge-03.png)

#### <a name="step-2-set-the-app-configuration-setting-to-enable-app-proxy"></a>2단계: 앱 프록시를 사용하도록 앱 구성 설정을 설정
Microsoft Edge에 대한 애플리케이션 프록시를 사용하도록 설정하려면 다음 키/값 쌍을 사용하여 Microsoft Edge를 대상으로 지정합니다.

|    Key    |    값    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.AppProxyRedirection    |    true    |

온-프레미스 웹앱에 원활하고 보호된 액세스로 Microsoft Edge 및 Azure AD 애플리케이션 프록시를 함께 사용하는 방법에 대한 자세한 내용은 [연계를 통해 성능 향상: 사용자 액세스를 개선하려는 Intune 및 Azure Active Directory 팀](https://cloudblogs.microsoft.com/enterprisemobility/2017/07/06/better-together-intune-and-azure-active-directory-team-up-to-improve-user-access)을 참조하세요. 이 블로그 게시물은 Intune Managed Browser를 참조하지만 콘텐츠는 Microsoft Edge에도 적용됩니다.

## <a name="configure-a-homepage-shortcut-for-microsoft-edge"></a>Microsoft Edge에 대한 홈페이지 바로 가기 구성

이 설정을 사용하면 Microsoft Edge에 대한 홈페이지 바로 가기를 구성할 수 있습니다. Microsoft Edge에서 새 탭을 열면 구성한 홈페이지 바로 가기가 검색 창 아래에 첫 번째 아이콘으로 나타납니다. 사용자는 관리형 컨텍스트에서 이 바로 가기를 편집하거나 삭제할 수 없습니다. 홈페이지 바로 가기에는 구분을 위해 조직 이름이 표시됩니다. 

다음 키/값 쌍을 사용하여 홈페이지 바로 가기를 구성합니다.

|    Key    |    값    |
|-------------------------------------------------------------------|-------------|
|    com.microsoft.intune.mam.managedbrowser.homepage   |    유효한 URL을 지정합니다. 잘못된 URL은 보안 조치로 차단됩니다.<br>**예:**  <`https://www.bing.com`>

## <a name="configure-your-organizations-logo-and-brand-color-for-new-tab-pages-in-microsoft-edge"></a>Microsoft Edge의 새 탭 페이지에 대해 조직의 로고 및 브랜드 색 구성

이러한 설정을 사용하면 Microsoft Edge의 새 탭 페이지를 사용자 지정하여 조직의 로고 및 브랜드 색을 페이지 배경으로 표시할 수 있습니다.

조직의 로고 및 색을 업로드하려면 먼저 다음 단계를 완료하세요.
- Azure Portal 내에서 [Intune] -> [클라이언트 앱] -> [회사 포털 브랜딩] -> [회사 아이덴티티 브랜딩]으로 이동합니다.
- 브랜드 로고를 설정하려면 “표시”에서 “회사 로고만”을 선택합니다. 투명한 배경 로고가 권장됩니다. 
- 브랜드의 배경색을 설정하려면 “표시”에서 “테마 색”을 선택합니다. Microsoft Edge는 새 탭 페이지에서 색의 더 밝은 음영을 적용하여 페이지의 가독성이 향상되도록 합니다. 

다음으로, 다음 키/값 쌍을 사용하여 조직 브랜딩을 Microsoft Edge로 끌어옵니다.

|    Key    |    값    |
|--------------------------------------------------------------------|------------|
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandLogo    |    True    |
|    com.microsoft.intune.mam.managedbrowser.NewTabPage.BrandColor    |    True    |

## <a name="display-relevant-industry-news-on-new-tab-pages"></a>새 탭 페이지에서 관련 분야 뉴스 표시

Microsoft Edge 모바일 내 새 탭 페이지에 조직과 관련된 산업 분야 뉴스를 표시하도록 환경을 구성할 수 있습니다. 이 기능을 사용하면 Microsoft Edge 모바일은 조직의 도메인 이름을 사용해 웹에서 조직, 조직의 분야, 경쟁자의 뉴스를 수집하므로 사용자는 Microsoft Edge의 중앙화된 새 탭 페이지에서 모든 관련 외부 뉴스를 검색할 수 있습니다. 관련 뉴스는 표시되지 않는 것이 기본 설정이며 조직에서 이를 사용하도록 설정할 수 있습니다. 

|    Key    |    값    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    'com.microsoft.intune.SohwIndustryNews'    |    **True**를 선택하면 Microsoft Edge 모바일 새 탭 페이지에서 관련 업계 뉴스를 표시합니다.<p>**False**(기본값)를 선택하면 새 탭 페이지에서 관련 업계 뉴스를 숨깁니다.    |

## <a name="configure-managed-bookmarks-for-microsoft-edge"></a>Microsoft Edge에 대한 관리형 책갈피 구성

액세스의 편의성을 위해 Microsoft Edge를 사용할 때 사용자가 사용할 책갈피를 구성할 수 있습니다. 

다음은 몇 가지 세부 정보입니다.

- 이 책갈피는 사용자가 Microsoft Edge의 [회사 모드](https://docs.microsoft.com/intune/apps/app-configuration-managed-browser#how-to-configure-bookmarks-for-a-protected-browser)를 사용할 때만 나타납니다. 
- 이 책갈피는 사용자가 삭제하거나 수정할 수 없습니다.
- 이 책갈피는 목록 맨 위에 표시됩니다. 사용자가 만드는 모든 책갈피는 이 책갈피 아래에 표시됩니다.
- 애플리케이션 프록시 리디렉션을 사용한 경우 내부 또는 외부 URL 중 하나를 사용하여 애플리케이션 프록시 웹앱을 추가할 수 있습니다.

관리 책갈피를 구성하려면 다음 키/값 쌍을 사용합니다.

|    Key    |    값    |
|---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.bookmarks    |    이 구성에 대한 값은 책갈피 목록입니다. 각 책갈피는 책갈피 제목과 책갈피 URL로 이루어져 있습니다. 제목과 URL을 `|` 문자로 구분합니다.      예제:<br>`Microsoft Bing|https://www.bing.com`<br>여러 책갈피를 구성하려면 각 쌍을 이중 문자 `||`로 구분합니다.<p>예제:<br>`Microsoft Bing|https://www.bing.com||Contoso|https://www.contoso.com`    |

## <a name="display-myapps-within-microsoft-edge-bookmarks"></a>Microsoft Edge 책갈피 내에 MyApps 표시

기본적으로 사용자에게 Microsoft Edge 책갈피 폴더 내에 구성된 MyApps 사이트가 표시됩니다. 폴더에는 조직의 이름으로 레이블이 지정됩니다.

|    Key    |    값    |
|------------------------------------------------------|----------------------------------------------------------------------------------------------------------------|
|    com.microsoft.intune.mam.managedbrowser.MyApps    |    **True**는 Microsoft Edge 책갈피 내에 MyApps를 표시합니다.<p>**False**는 Microsoft Edge 내에서 MyApps를 숨깁니다.    |

## <a name="specify-allowed-or-blocked-sites-list-for-microsoft-edge"></a>Microsoft Edge에 대해 허용되거나 차단된 사이트 목록 지정
앱 구성을 사용하여 사용자가 작업 프로필을 사용할 때 액세스할 수 있는 사이트를 정의할 수 있습니다. 허용 목록을 사용하면 사용자는 명시적으로 나열한 사이트에만 액세스할 수 있습니다. 차단된 목록을 사용하면 사용자는 명시적으로 차단된 사이트를 제외한 모든 사이트에 액세스할 수 있습니다. 허용 목록이나 차단된 목록 중 하나만 적용해야 하며, 둘 다 적용해서는 안됩니다. 둘 다를 적용하면 허용된 목록이 적용됩니다.  

Microsoft Edge에 대해 허용되거나 차단된 사이트 목록을 구성하려면 다음 키/값 쌍을 사용합니다. 

|    Key    |    값    |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    다음 중에서 선택합니다.<p>1. 허용되는 URL을 지정합니다(이러한 URL만 허용되며 다른 사이트에 액세스할 수 없음).<br>`com.microsoft.intune.mam.managedbrowser.AllowListURLs`<p>2. 차단되는 URL을 지정합니다(다른 모든 사이트는 액세스할 수 있음).<br>`com.microsoft.intune.mam.managedbrowser.BlockListURLs`    |    키에 해당하는 값은 URL 목록입니다. 허용하거나 차단할 모든 URL을 파이프 `|` 문자로 구분된 단일 값으로 입력합니다.<br>**예:**<br>`URL1|URL2|URL3`<br>`http://.contoso.com/|https://.bing.com/|https://expenses.contoso.com`  |

### <a name="url-formats-for-allowed-and-blocked-site-list"></a>허용되거나 차단된 사이트 목록의 URL 형식 
다양한 URL 형식을 사용하여 허용/차단된 사이트 목록을 작성할 수 있습니다. 이러한 허용되는 패턴은 다음 표에 자세히 설명되어 있습니다. 시작하기 전에 다음과 같은 몇 가지 참고 사항이 있습니다. 
- URL을 목록에 입력할 때 모든 URL의 앞에 **http** 또는 **https** 를 덧붙여야 합니다.
- 다음과 같이 허용되는 패턴 목록의 규칙에 따라 와일드카드 기호(\*)를 사용할 수 있습니다.
- 와일드카드는 호스트 이름의 전체 구성 요소(마침표로 구분됨) 또는 경로의 전체 부분(슬래시로 구분됨)만 일치할 수 있습니다. 예를 들어 `http://*contoso.com`은 지원되지 **않습니다**.
- 주소에 포트 번호를 지정할 수 있습니다. 포트 번호를 지정하지 않으면 다음 값이 사용됩니다.
  - http의 경우 포트 80
  - https의 경우 포트 443
- 포트 번호에 대한 와일드카드 사용은 지원되지 **않습니다**. 예를 들어 `http://www.contoso.com:*` 및 `http://www.contoso.com:*/`은 지원되지 않습니다. 

    |    URL    |    세부 정보    |    일치하는 항목    |    일치하지 않는 항목    |
    |-------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------|
    |    `http://www.contoso.com`    |    단일 페이지와 일치    |    `www.contoso.com`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`contoso.com/`    |
    |    `http://contoso.com`    |    단일 페이지와 일치    |    `contoso.com/`    |    `host.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com`    |
    |    `http://www.contoso.com/*;`   |    `www.contoso.com`으로 시작하는 모든 URL과 일치    |    `www.contoso.com`<br>`www.contoso.com/images`<br>`www.contoso.com/videos/tvshows`    |    `host.contoso.com`<br>`host.contoso.com/images`    |
    |    `http://*.contoso.com/*`    |    `contoso.com` 아래의 모든 하위 도메인과 일치    |    `developer.contoso.com/resources`<br>`news.contoso.com/images`<br>`news.contoso.com/videos`    |    `contoso.host.com`
    |    `http://*contoso.com/*`    |    `contoso.com/`으로 끝나는 모든 하위 도메인과 일치    |    `http://news-contoso.com`<br>`http://news-contoso.com.com/daily`    |    `http://news-contoso.host.com`    |
    `http://www.contoso.com/images`    |    단일 폴더와 일치    |    `www.contoso.com/images`    |    `www.contoso.com/images/dogs`    |
    |    `http://www.contoso.com:80`    |    포트 번호를 사용하여 단일 페이지와 일치    |    `http://www.contoso.com:80`    |         |
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
  - `https://*contoso.com`
  - `http://www.contoso.com:*`
  - `http://www.contoso.com: /*`

## <a name="transition-users-to-their-personal-context-when-trying-to-access-a-blocked-site"></a>차단된 사이트에 액세스하려고 할 때 사용자의 개인 컨텍스트로 전환

Microsoft Edge에 기본 제공된 이중 ID 모델을 사용하면 Intune Managed Browser보다 더 유연한 환경을 최종 사용자에게 제공할 수 있습니다. 사용자가 Microsoft Edge에서 차단된 사이트에 연결하는 경우 회사 컨텍스트가 아니라 프라이빗 컨텍스트에서 링크를 열라는 메시지를 사용자에게 표시할 수 있습니다. 이렇게 하면 사용자도 보호하고 회사 리소스를 안전하게 유지할 수 있습니다. 예를 들어 사용자가 Outlook 통해 뉴스 기사의 링크를 받는 경우 프라이빗 컨텍스트 또는 InPrivate 탭에서 링크를 열 수 있습니다. 회사 컨텍스트에서는 뉴스 웹 사이트를 허용하지 않습니다. 기본적으로 이러한 전환이 허용됩니다.

이러한 소프트 전환을 허용할지 여부를 구성하려면 다음 키/값 쌍을 사용합니다.

|    Key    |    값    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.openInPrivateIfBlock'    |    **True**를 선택하면 InPrivate 브라우징에서 직접 제한된 링크를 엽니다.<p>**False**(기본)를 선택하면 사용자가 제한된 링크를 열 때 InPrivate 브라우징 또는 관리 서비스 계정(MSA)를 선택하도록 합니다.    |

## <a name="open-restricted-links-directly-in-inprivate-tab-pages"></a>InPrivate 탭 페이지에서 직접 제한된 링크 열기

제한된 링크를 InPrivate 브라우징에서 직접 열도록 구성하면 사용자가 더욱 원활한 브라우징 환경을 갖게 됩니다. 이렇게 하면 사용자가 사이트를 볼 때 개인 컨텍스트로 전환하는 단계가 필요하지 않습니다. InPrivate 브라우징은 관리되지 않는 것으로 간주되므로 사용자가 InPrivate 브라우징 모드를 사용할 때는 액세스할 수 없습니다. 

|    Key    |    값    |
|----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `com.microsoft.intune.mam.managedbrowser.AllowTransitionOnBlock`    |    **True**이면 Microsoft Edge에서 사용자를 프라이빗 컨텍스트로 전환하여 차단된 사이트를 열 수 있습니다.<p>**차단**이면 Microsoft Edge에서 사용자를 전환할 수 없습니다. 사용자에게는 액세스하려는 사이트가 차단되었다는 메시지만 표시됩니다.    |


## <a name="use-microsoft-edge-on-ios-to-access-managed-app-logs"></a>iOS에서 Microsoft Edge를 사용하여 관리형 앱 로그에 액세스 

iOS 디바이스에 Microsoft Edge가 설치된 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있습니다. 관리되는 iOS 앱의 문제를 해결하기 위해 로그를 보낼 수 있습니다. 방법은 다음과 같습니다.
1. iOS 디바이스에서 Microsoft Edge를 엽니다.
2. 주소 상자에 `about:intunehelp`를 입력합니다. 
3. Microsoft Edge가 문제 해결 모드를 시작합니다.

앱 로그에 저장된 설정 목록은 [Managed Browser에서 앱 보호 로그 검토](app-protection-policy-settings-log.md)를 참조하세요.

Android 디바이스의 로그를 보는 방법을 확인하려면 [이메일을 통해 IT 관리자에게 로그 보내기](https://docs.microsoft.com/intune-user-help/send-logs-to-your-it-admin-by-email-android)를 참조하세요. 

## <a name="security-and-privacy-for-microsoft-edge"></a>Microsoft Edge에 대한 보안 및 개인 정보

Microsoft Edge의 추가 보안 및 개인 정보 고려 사항은 다음과 같습니다.

- Microsoft Edge는 사용자가 해당 디바이스의 기본 브라우저에서 지정한 설정에 액세스할 수 없어 이러한 설정을 사용하지 않습니다.
- Microsoft Edge와 연결된 앱 보호 정책에서 **액세스용 단순 PIN 필요** 또는 **액세스용 회사 자격 증명 필요** 옵션을 구성할 수 있습니다. 사용자가 인증 페이지의 도움말 링크를 선택하면 정책의 차단된 목록에 추가되었는지와 관계없이 모든 인트라넷 사이트든 검색할 수 있습니다.
- Microsoft Edge는 직접 액세스하는 사이트에 대한 액세스만 차단할 수 있습니다. 사용자가 중간 서비스(변환 서비스 등)를 사용하여 사이트에 액세스하는 경우 액세스를 차단하지 않습니다.
- 인증 및 Intune 문서에 대한 액세스를 허용하기 위해 허용 또는 차단 목록 설정에서 * **.microsoft.com**이 제외됩니다. 항상 허용됩니다.
- 사용자는 데이터 수집을 해제할 수 있습니다. Microsoft는 Microsoft 제품 및 서비스를 개선하기 위해 Managed Browser의 성능 및 사용에 대한 익명의 데이터를 자동으로 수집합니다. 사용자는 디바이스에서 **사용량 현황 데이터** 설정을 사용하여 데이터의 수집을 해제할 수 있습니다. 이 데이터의 수집은 제어할 수 없습니다. iOS 디바이스에서 만료되거나 신뢰할 수 없는 인증서가 있는 웹 사이트를 사용자가 방문하면 해당 웹 사이트를 열 수 없습니다.

## <a name="next-steps"></a>다음 단계

- [앱 보호 정책이란?](app-protection-policy.md) 
