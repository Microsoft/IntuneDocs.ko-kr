---
title: Intune에서 최신 인증을 사용하지 않는 앱 차단
titleSuffix: Microsoft Intune
description: 최신 인증(ADAL)을 사용하지 않는 앱 차단에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 73db3070-d033-40fb-a8f1-58b9d198021e
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 354109cc4d84e34eebd5df6df86919f386e143f6
ms.sourcegitcommit: 9f99b4a7f20ab4175d6fa5735d9f4fd6a03e0d3a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40251797"
---
# <a name="block-apps-that-do-not-use-modern-authentication-adal"></a>최신 인증(ADAL)을 사용하지 않는 앱 차단

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

앱 보호 정책을 사용하는 앱 조건부 액세스의 경우 응용 프로그램에서 OAuth2 구현인 [최신 인증](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)을 사용해야 합니다. 최신 Office 모바일 및 데스크톱 응용 프로그램은 최신 인증을 사용하지만 기본 인증 및 양식 기반 인증과 같은 다른 인증 방법을 사용하는 타사 앱이나 이전 Office 앱도 있습니다.

이러한 앱에 대한 액세스를 차단하려면 다음을 권장합니다.

* 최신 인증 이외의 인증 프로토콜을 차단하도록 ADFS 클레임 규칙을 설정해야 합니다. 자세한 지침은 시나리오 3 - [브라우저 기반 응용 프로그램을 제외한 모든 O365 액세스 차단](https://technet.microsoft.com/library/dn592182.aspx)에서 제공됩니다.
* **Exchange 및 SharePoint Online**의 경우 Azure Active Directory 조건부 액세스를 사용하고 SharePoint Online의 경우 PowerShell commandlet Set-SPOTenant를 사용합니다. 자세한 내용은 [Azure Active Directory 조건부 액세스를 위해 SharePoint Online 및 Exchange Online 설정](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication#legacy-authentication-protocols)을 참조하세요.


>[!IMPORTANT]
>앱 기반 CA는 Azure AD(Azure Active Directory) 인증서 기반 인증으로 사용할 수 없습니다. 한 번에 하나만 구성할 수 있습니다.

### <a name="see-also"></a>참고 항목
[Intune을 사용하는 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)
