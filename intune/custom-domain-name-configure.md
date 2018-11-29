---
title: 사용자 지정 도메인 이름 구성
titlesuffix: Microsoft Intune
description: Microsoft Intune 구독에 사용자 지정 도메인 이름 추가
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2382f36f-13d8-4a32-81ad-6cfa604889c3
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.openlocfilehash: a4227399eb5cf1d2cc2e265215eccb2c05d73ac5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181499"
---
# <a name="configure-a-custom-domain-name"></a>사용자 지정 도메인 이름 구성

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

이 항목에서는 관리자에게 DNS CNAME를 만들어 Microsoft Intune을 사용하는 로그온 환경을 간소화하고 사용자 지정하는 방법을 알려줍니다.

조직에서 Intune과 같은 Microsoft 클라우드 기반 서비스에 등록하면 Azure AD(Active Directory)에 호스트된 초기 도메인 이름(예: **your-domain.onmicrosoft.com**)이 제공됩니다. 이 예제에서 **your-domain**은 등록 시 선택한 도메인 이름입니다. **onmicrosoft.com**은 구독에 추가하는 계정에 할당되는 접미사입니다. 구독을 통해 제공되는 도메인 이름이 아니라 조직의 사용자 지정 도메인에서 Intune에 액세스하도록 구성할 수 있습니다.

사용자 계정을 만들거나 온-프레미스 Active Directory를 동기화하기 전에 .onmicrosoft.com 도메인만 사용할지 아니면 사용자 지정 도메인 이름을 하나 이상 추가할지를 결정하는 것이 좋습니다. 사용자 관리가 간소화되도록 사용자를 추가하기 전에 사용자 지정 도메인을 설정합니다. 이렇게 하면 사용자가 다른 도메인 리소스에 액세스하는 데 사용하는 자격 증명으로 로그인할 수 있습니다.

Microsoft의 클라우드 기반 서비스에 가입한 경우 해당 서비스의 인스턴스는 클라우드 기반 서비스의 ID 및 디렉터리 서비스를 제공하는 Microsoft [Azure AD 테넌트](http://technet.microsoft.com/library/jj573650.aspx#BKMK_WhatIsAnAzureADTenant)가 됩니다. 또한, 조직의 사용자 지정 도메인 이름을 사용하도록 Intune을 구성하는 작업은 다른 Azure AD 테넌트의 경우와 동일하므로 [도메인 추가](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)에 설명된 정보 및 프로시저를 사용할 수 있습니다.

> [!TIP]
> 사용자 지정 도메인에 대해 자세히 알아보려면 [Azure Active Directory에서 사용자 지정 도메인 이름의 개념적 개요](https://azure.microsoft.com/documentation/articles/active-directory-add-domain-concepts/)를 참조하세요.

초기 onmicrosoft.com 도메인 이름을 제거하거나 바꿀 수 없습니다. 비즈니스 ID가 명확히 유지되도록 Intune에서 사용할 사용자 지정 도메인 이름을 추가, 확인 또는 제거할 수 있습니다.

## <a name="to-add-and-verify-your-custom-domain"></a>사용자 지정 도메인을 추가 및 확인하려면

1. [Office 365 관리 포털](https://portal.office.com/Admin/Default.aspx)로 이동한 후 관리자 계정에 로그인합니다.

2. 탐색 창에서 **설치** &gt; **도메인**을 선택합니다.

3. **도메인 추가**를 선택하고 사용자 지정 도메인 이름을 입력합니다. **다음**을 선택합니다.
   ![설정 > 도메인이 선택되고 새 도메인 이름이 추가된 Office 365 관리 센터 스크린샷](./media/domain-custom-add.png)
4. **도메인 확인** 대화 상자가 열리고 DNS 호스팅 공급자에서 TXT 레코드를 만들기 위한 값이 표시됩니다.
    - **GoDaddy 사용자**: Office 365 관리 포털은 사용자를 GoDaddy의 로그인 페이지로 리디렉션합니다. 자격 증명을 입력하고 도메인 변경 권한 계약에 동의하면 TXT 레코드가 자동으로 만들어집니다. 또는 [TXT 레코드를 만들](https://support.office.com/article/Create-DNS-records-at-GoDaddy-for-Office-365-f40a9185-b6d5-4a80-bb31-aa3bb0cab48a) 수도 있습니다.
    - **Register.com 사용자**: [단계별 지침](https://support.office.com/article/Create-DNS-records-at-Register-com-for-Office-365-55bd8c38-3316-48ae-a368-4959b2c1684e#BKMK_verify)에 따라 TXT 레코드를 만듭니다.

사용자 지정 도메인을 추가 및 확인하는 단계는 [Azure Active Directory에서도 수행](https://azure.microsoft.com/documentation/articles/active-directory-add-domain/)할 수 있습니다.

[Office 365의 초기 onmicrosoft.com 도메인 정보](https://support.office.com/article/About-your-initial-onmicrosoft-com-domain-in-Office-365-B9FC3018-8844-43F3-8DB1-1B3A8E9CFD5A)에서 자세한 내용을 확인할 수 있습니다.
