---
title: Azure Active Directory Single Sign-On을 사용하도록 Skycure 구성
description: Azure Active Directory SSO(Single Sign-On)을 사용하도록 Skycure 구성
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/16/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 34d5d359-5c7c-4225-a205-8ce890b6f890
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f7f83e87ed3e625775aa41295cab122653ec160c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31015220"
---
# <a name="configure-skycure-to-use-azure-active-directory-single-sign-on-sso"></a>Azure Active Directory SSO(Single Sign-On)을 사용하도록 Skycure 구성

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Azure AD SSO는 Skycure와 Intune을 통합하는 경우 사용됩니다. 주요 이점은 다음과 같습니다.

-   **관리자**는 Microsoft 포털(Intune, Azure) 및 Skycure 관리 콘솔에서 로그인 및 로그아웃할 때마다 자격 증명을 다시 입력하지 않고도 동일한 자격 증명을 사용할 수 있습니다.

-   **최종 사용자**는 Skycure 앱에서 로그인 및 로그아웃할 때마다 자격 증명을 다시 입력하지 않고도 동일한 Azure AD 자격 증명을 사용할 수 있습니다.

다음은 Skycure와 Azure Active Directory SSO(Single Sign-On)를 통합하는 단계입니다.

## <a name="to-retrieve-the-azure-active-directory-tenant-id"></a>Azure Active Directory 테넌트 ID를 검색하려면

Azure AD 테넌트 ID를 검색해야 합니다.

1.  [Azure Portal](https://portal.azure.com/)로 이동한 다음 자격 증명을 사용하여 로그인합니다.

2.  **대시보드**가 나타나면 **Azure Active Directory**를 선택합니다.

![Azure AD 대시보드](../media/mtp/skycure-sso-1.png)

1.  **Azure Active Directory** 블레이드가 열리면 **속성**을 선택합니다.

![Azure AD 속성 블레이드](../media/mtp/skycure-sso-2.png)

1.  **Azure Active Directory 속성** 블레이드의 **테넌트 디렉터리 ID**에서 **복사 아이콘**을 클릭합니다.

> 나중에 사용할 수 있도록 복사된 디렉터리 ID 값을 텍스트 파일에 붙여넣습니다. 디렉터리 ID 값은 Skycure 및 Intune 통합 프로세스의 뒷부분에 필요합니다.

![Azure AD 대시보드](../media/mtp/skycure-sso-3.png)

## <a name="allow-skycure-to-communicate-with-azure-active-directory"></a>Skycure가 Azure Active Directory와 통신하도록 허용

1.  브라우저에서 아래 URL을 입력합니다. **DIRECTORY_ID** 대신, 텍스트 파일에 복사해 놓은 Azure Active Directory 테넌트 ID를 입력합니다.

        https://login.microsoftonline.com/<DIRECTORY_ID>/oauth2/authorize?client_id=28fd67fdb1794629a8b0dad420b697c7&prompt=admin_consent&redirect_uri=https%3A%2F%2Fmc.skycure.com%2Fapi%2Fexternal%2Fmdm%2Faad_app_consent%2Fmanagement_callback&response_type=code

2.  Azure Active Directory 자격 증명을 사용하여 로그인해야 합니다. 계속하려면 **허용**을 클릭합니다.

![Azure AD Dlogin 페이지](../media/mtp/skycure-sso-4.png)

## <a name="create-an-azure-ad-security-group-for-skycure-optional"></a>Skycure용 Azure AD 보안 그룹 만들기(선택 사항)

Skycure를 실행하는 사용자(예: Skycure 사용자)를 포함하는 전용 사용자 그룹을 만들 수 있습니다. 이 작업은 보고서를 통해 Skycure 활동을 분석하는 경우 유용할 수 있습니다.

-   [그룹을 만들고 Azure AD에서 구성원을 추가하는 방법](https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal)을 자세히 알아보세요.

> [!NOTE] 
> 또한 기존 Azure AD 보안 그룹을 사용할 수 있습니다.

## <a name="configure-the-azure-ad-account-to-integrate-intune-with-skycure"></a>Skycure와 Intune이 통합되도록 Azure AD 계정 구성

1.  [Skycure 관리 콘솔](https://aad.skycure.com/)에서 텍스트 파일에 저장해 놓은 Azure Active Directory 테넌트 ID를 입력합니다.

![Skycure 관리 콘솔 Azure AD 테넌트 ID 필드](../media/mtp/skycure-sso-5.png)

> [!IMPORTANT] 
> Skycure에서 Azure AD 테넌트 ID가 있는지 Azure AD에 쿼리하여 유효성을 검사합니다. Skycure에서 해당 ID를 찾고 나면 관리자는 그 다음 단계인 기본 설정을 계속할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Skycure iOS 앱 구성 정책 다운로드](/intune-classic/deploy-use/download-skycure-ios-app-configuration-policy)
