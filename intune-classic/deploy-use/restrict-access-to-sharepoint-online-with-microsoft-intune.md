---
title: SharePoint Online 보호
description: 조건부 액세스를 사용하여 SharePoint Online의 회사 데이터를 보호하고 해당 데이터에 대한 액세스를 제어하는 방법을 설명합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b088e5a0-fd4a-4fe7-aa49-cb9c8cfb1585
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2b7285c272efac8eab406393b0b896795fa5d8ed
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31027979"
---
# <a name="protect-access-to-sharepoint-online-with-microsoft-intune"></a>Microsoft Intune을 사용하여 SharePoint Online에 대한 액세스 보호

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune 조건부 액세스를 사용하여 SharePoint Online에 있는 파일에 대한 액세스를 제어합니다.
조건부 액세스에는 두 구성 요소가 포함되어 있습니다.
- 장치가 규격으로 간주되기 위해 준수해야 하는 정책인 장치 준수 정책.
- 장치가 서비스에 액세스하기 위해 충족해야 하는 조건을 지정하는 조건부 액세스 정책.
조건부 액세스의 작동 방식에 대한 자세한 내용을 확인하려면 [메일, O365 및 기타 서비스에 대한 액세스 보호](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) 항목을 읽어보세요.

준수 및 조건부 액세스 정책은 사용자에게 배포합니다. 이를 통해 사용자가 서비스에 액세스하는 데 사용하는 모든 장치의 정책 준수 여부를 확인합니다.

사용자가 자신의 장치에 있는 OneDrive 등의 지원되는 앱을 사용하여 파일에 연결하려고 하면 다음 평가 작업이 수행됩니다.

![장치에서 SharePoint에 대한 액세스가 허용되는지 아니면 차단되는지를 결정하는 결정 지점을 보여 주는 다이어그램](../media/ConditionalAccess8-6.png)


SharePoint Online에 대한 조건부 액세스 정책을 구성하기 **전에** 다음을 수행해야 합니다.
- **SharePoint Online 구독**이 있어야 하며 사용자는 SharePoint Online의 라이선스를 취득해야 합니다.
- **Enterprise Mobility + Security(EMS) 구독** 또는 **Azure AD(Azure Active Directory) Premium 구독**이 있어야 하며 사용자는 EMS 또는 Azure AD의 라이선스를 취득해야 합니다. 자세한 내용은 [Enterprise Mobility 가격 책정 페이지](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) 또는 [Azure Active Directory 가격 책정 페이지](https://azure.microsoft.com/pricing/details/active-directory/)를 참조하세요.


  필수 파일에 연결하려면 장치가 다음 조건을 충족해야 합니다.
-   Intune에 **등록**되어 있거나 도메인에 가입된 PC여야 합니다.

-   Azure Active Directory에 **등록**되어 있어야 합니다. Intune에 장치를 등록하면 이 등록이 자동으로 수행됩니다.


-   배포된 Intune 규정 준수 정책을 **준수**해야 합니다.

Azure Active Directory에 저장되는 장치 상태는 지정한 조건에 따라 파일에 대한 액세스 권한을 부여하거나 차단합니다.

조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.

-   장치를 Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.

-   장치가 규정을 준수하지 않으면 Intune 회사 포털 웹 사이트를 안내하는 메시지가 표시됩니다. 해당 웹 사이트에서 사용자는 문제에 관한 정보와 이를 해결하는 방법을 확인할 수 있습니다.

**외부 공유에는 조건부 액세스가 적용되지 않습니다**. 테넌트 또는 사이트 모음에서의 외부 공유를 방지하는 방법을 알아보려면 [SharePoint Online 환경에 대한 외부 공유 관리](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85)를 참조하세요.

>[!NOTE]
>SharePoint Online에 대해 조건부 액세스를 사용하도록 설정하는 경우 [Remove-SPOTenantSyncClientRestriction](https://technet.microsoft.com/library/dn917451.aspx) 항목에 설명된 대로 목록의 도메인을 사용하지 않도록 설정하는 것이 좋습니다.  

## <a name="support-for-mobile-devices"></a>모바일 장치에 대한 지원
지원되는 운영 체제는 다음과 같습니다.
- iOS 8.0 이상
- Android 4.0 이상, Samsung Knox Standard 4.0 이상
- Windows Phone 8.1 이상

**iOS** 및 **Android** 장치가 브라우저에서 액세스하는 경우 SharePoint Online 액세스를 보호할 수 있습니다. 규격 장치의 지원되는 브라우저에서만 액세스가 허용됩니다.
* Safari(iOS)
* Chrome(Android)
* Intune Managed Browser(iOS 및 Android 5.0 이상)

**지원되지 않는 브라우저는 차단됩니다**.

## <a name="support-for-pcs"></a>PC 지원
지원되는 운영 체제는 다음과 같습니다.
- Windows 8.1 이상(PC가 Intune에 등록된 경우)
- Windows 7.0, Windows 8.1 또는 Windows 10(PC가 도메인에 가입된 경우)
  > [!NOTE]
  >Windows 10 PC에 조건부 액세스를 사용하려면 해당 PC를 Windows 10 1주년 업데이트로 업데이트해야 합니다.

  - 도메인에 가입된 PC의 경우 Azure Active Directory에 [자동으로 등록](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/)하도록 설정해야 합니다. Intune 및 Office 365 고객의 경우에는 Azure AD Device Registration Service가 자동으로 활성화됩니다. ADFS Device Registration Service를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 장치가 표시되지 않습니다.

  - 정책이 도메인 가입을 요구하도록 설정되어 있지만 PC가 도메인에 가입되지 않은 경우 IT 관리자에게 문의하라는 메시지가 표시됩니다.

  - 정책이 도메인 가입 또는 규정 준수를 요구하도록 설정되어 있는 경우 PC가 요구 사항을 충족하지 않으면 회사 포털 앱을 설치하고 등록하는 방법에 대한 지침이 포함된 메시지가 표시됩니다.
    >[!NOTE]
    >Intune 컴퓨터 클라이언트를 실행 중인 PC에서는 조건부 액세스가 지원되지 않습니다.

[Office 365 최신 인증을 사용](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)하도록 설정해야 하며 최신 Office 업데이트를 모두 설치해야 합니다.

최신 인증을 사용하는 경우 Office 2013 Windows 클라이언트에 ADAL(Active Directory Authentication Library) 기반 로그인 기능이 제공되며, **다단계 인증** 및 **인증서 기반 인증**과 같은 더욱 효율적인 보안 기능을 사용할 수 있습니다.


## <a name="configure-conditional-access-for-sharepoint-online"></a>SharePoint Online에 대한 조건부 액세스 구성

### <a name="step-1-configure-active-directory-security-groups"></a>1단계: Active Directory 보안 그룹 구성
시작하기 전에 조건부 액세스 정책에 대한 Azure Active Directory 보안 그룹을 구성합니다. **Office 365 관리 센터**또는 **Intune 계정 포털**에서 이러한 그룹을 구성할 수 있습니다. 이러한 그룹을 사용하여 사용자를 대상으로 지정하거나 정책에서 사용자를 제외합니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 장치가 규정을 준수해야 리소스에 액세스할 수 있습니다.

SharePoint Online 정책에 두 그룹 유형을 지정할 수 있습니다.

-   **대상 그룹**: 정책이 적용되는 사용자 그룹을 포함합니다.

-   **제외된 그룹**: 정책에서 제외되는 사용자 그룹을 포함합니다.

사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2단계: 규정 준수 정책 구성 및 배포
아직 수행하지 않은 경우 준수 정책을 만들어 SharePoint Online 정책의 대상이 될 사용자에게 배포합니다.

> [!NOTE]
> 규정 준수 정책을 Intune 그룹에 배포하는 동안 Azure Active Directory 보안 그룹을 조건부 액세스 정책의 대상으로 합니다.

준수 정책을 구성하는 방법에 대한 자세한 내용은 [준수 정책 만들기](create-a-device-compliance-policy-in-microsoft-intune.md)를 참조하세요.

> [!IMPORTANT]
> 준수 정책을 배포하지 않은 경우 장치는 규정을 준수하는 것으로 간주됩니다.

준비가 되었으면 **3단계**를 계속합니다.

### <a name="step-3-configure-the-sharepoint-online-policy"></a>3단계: SharePoint Online 정책 구성
다음으로 관리되고 규정을 준수하는 장치만 SharePoint Online에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure Active Directory에 저장됩니다.

#### <a name="bkmk_spopolicy"></a>

>[!NOTE]
> Azure AD 관리 콘솔에서 Intune 장치용 조건부 액세스 정책을 만들 수도 있습니다. Azure AD에서는 이 정책을 **장치 기반 조건부 액세스 정책**이라고 합니다. 또한 다단계 인증 등의 다른 조건부 액세스 정책을 만들 수도 있습니다. Azure AD에서 지원하는 Salesforce, Box 등의 타사 엔터프라이즈 앱에 대한 조건부 액세스 정책을 설정할 수도 있습니다. 자세한 내용은 [Azure Active Directory 연결 응용 프로그램에 대한 액세스 제어를 위해 Azure Active Directory 장치 기반 조건부 액세스 정책을 설정하는 방법](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/)을 참조하세요.


1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **조건부 액세스** > **SharePoint Online 정책**을 선택합니다.
   ![SharePoint Online 정책 페이지의 스크린샷](../media/mdm-ca-spo-policy-configuration.png)

2. **SharePoint Online에 대한 조건적 액세스 정책 사용**을 선택합니다.

3. **응용 프로그램 액세스**에서 다음 플랫폼에 조건부 액세스 정책을 적용하도록 선택할 수 있습니다.

   - **모든 플랫폼**

     이 경우 **SharePoint Online**에 액세스하는 데 사용되는 모든 장치가 Intune에 등록되고 정책을 준수해야 합니다. **최신 인증**을 사용하는 모든 클라이언트 응용 프로그램에는 조건부 액세스 정책이 적용됩니다. 플랫폼이 현재 Intune에서 지원되지 않는 경우 **SharePoint Online**에 대한 액세스는 차단됩니다.

     **모든 플랫폼** 옵션을 선택하면 클라이언트 응용 프로그램에서 보고하는 플랫폼에 관계없이, Azure Active Directory가 모든 인증 요청에 이 정책을 적용합니다. 다음을 제외한 모든 플랫폼은 등록되어 있어야 하며 정책을 준수해야 합니다.
     *   Windows 장치: 등록되어 있고 정책을 준수해야 하거나, 온-프레미스 Active Directory를 통해 도메인에 가입되어 있거나, 두 조건을 모두 충족해야 합니다.
     * 지원되지 않는 플랫폼(예: Mac). 그러나 이러한 플랫폼에서 제공하는 최신 인증을 사용하는 앱은 계속 차단됩니다.

   - **특정 플랫폼**

      지정한 장치 플랫폼에서 최신 인증을 사용하는 모든 클라이언트 앱에 조건부 액세스 정책이 적용됩니다.

     Windows PC의 경우 해당 PC가 도메인에 가입되어 있거나 Intune에 등록되어 있고 정책을 준수해야 합니다. 다음 요구 사항을 설정할 수 있습니다.

     -   **장치가 도메인에 가입되어 있거나 규정을 준수해야 합니다.** PC가 도메인에 가입되어 있거나 Intune에 설정된 정책을 준수해야 하도록 지정하려는 경우 이 옵션을 선택합니다. PC가 이러한 요구 사항을 하나라도 충족하지 않을 경우 Intune에 장치를 등록하라는 메시지가 표시됩니다.

     -   **장치가 규정을 준수해야 합니다.** PC가 Intune에 등록되어 있고 규정을 준수해야 하는 경우 이 옵션을 선택합니다. PC가 등록되지 않은 경우 등록 방법에 대한 지침이 포함된 메시지가 표시됩니다.

4. SharePoint Online 및 비즈니스용 OneDrive에 대한 **브라우저 액세스**에서, 지원되는 브라우저인 Safari(iOS) 및 Chrome(Android)을 통해서만 Exchange Online에 대한 액세스를 허용하도록 선택할 수 있습니다. 다른 브라우저에서의 액세스는 차단됩니다. OneDrive에 대한 응용 프로그램 액세스에 선택한 것과 동일한 플랫폼 제한 사항이 여기에도 적용됩니다.

   **Android** 장치에서는, 사용자가 브라우저 액세스를 사용하도록 설정해야 합니다. 이렇게 하려면 사용자가 등록된 장치에서 다음과 같이 **브라우저 액세스 사용** 옵션을 선택해야 합니다.
   1.    **회사 포털** 앱을 엽니다.
   2.    줄임표(...) 또는 하드웨어 메뉴 단추에서 **설정** 페이지로 이동합니다.
   3.    **브라우저 액세스 사용** 단추를 누릅니다.
   4.    Chrome 브라우저에서, Office 365에서 로그아웃하고 Chrome을 다시 시작합니다.

   **iOS** 및 **Android** 플랫폼에서, 서비스에 액세스하는 데 사용되는 장치를 식별하기 위해 Azure Active Directory는 TLS(전송 계층 보안) 인증서를 장치에 발급합니다. 아래 스크린샷에 나와 있는 것처럼 장치에서 사용자에게 인증서를 선택하라는 메시지와 함께 인증서를 표시합니다. 사용자는 이 인증서를 선택해야 브라우저를 사용할 수 있습니다.

   **iOS**

   ![iPad의 인증서 관련 메시지 스크린샷](../media/mdm-browser-ca-ios-cert-prompt.png)

   **OWA(Outlook Web Access)**

   ![Android 장치의 인증서 관련 메시지 스크린샷](../media/mdm-browser-ca-android-cert-prompt.png)
5. **대상 그룹**에서 **수정**을 선택하여 정책이 적용되는 Azure Active Directory 보안 그룹을 선택합니다. 모든 사용자 또는 선택한 사용자 그룹을 대상으로 지정할 수 있습니다.

6. **제외된 그룹**에서 필요에 따라 **수정**을 선택하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.

7. 작업이 완료되면 **저장**을 선택합니다.

조건부 액세스 정책은 배포하지 않아도 즉시 적용됩니다.

### <a name="step-4-monitor-the-compliance-and-conditional-access-policies"></a>4단계: 규정 준수 및 조건부 액세스 정책 모니터링
**그룹** 작업 영역에서 장치의 상태를 볼 수 있습니다.

아무 모바일 장치 그룹이나 선택합니다. 그런 다음 **장치** 탭에서 다음 **필터**중 하나를 선택합니다.

-   **AAD에 등록되지 않은 장치**. 이러한 장치는 SharePoint Online에서 차단됩니다.

-   **규격이 아닌 장치**. 이러한 장치는 SharePoint Online에서 차단됩니다.

-   **AAD 및 규격에 등록된 장치**. 이러한 장치는 SharePoint Online에 액세스할 수 있습니다.

### <a name="see-also"></a>참고 항목
[Microsoft Intune을 사용한 메일 및 O365 서비스 액세스 보호](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
