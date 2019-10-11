---
title: Intune을 사용하는 앱 기반 조건부 액세스
titleSuffix: Microsoft Intune
description: Intune을 사용하는 앱 기반 조건부 액세스 작동 방식에 대해 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/11/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b399fba0-5dd4-4777-bc9b-856af038ec41
ms.reviewer: chrisgre
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 46ff51c872c2e8c87d044bde3c262203d5f55e8e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71723062"
---
# <a name="app-based-conditional-access-with-intune"></a>Intune을 사용하는 앱 기반 조건부 액세스

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

[Intune 앱 보호 정책](../apps/app-protection-policy.md)을 사용하면 Intune에 등록된 디바이스에서 회사 데이터를 보호하는 데 도움이 됩니다. Intune에서 관리를 위해 등록되지 않은 직원 소유 디바이스에서 앱 보호 정책을 사용할 수도 있습니다. 이 경우 회사에서 디바이스를 관리하지 않더라도 여전히 회사 데이터와 리소스가 보호되고 있음을 확인해야 합니다.

앱 기반 조건부 액세스 및 클라이언트 앱 관리는 Intune 앱 보호 정책을 지원하는 클라이언트 앱만 Exchange Online 및 기타 Office 365 서비스에 액세스할 수 있도록 함으로써 보안 계층을 추가합니다.

> [!NOTE]
> 관리되는 앱은 앱 보호 정책이 적용되어 있으며 Intune을 통해 관리할 수 있는 앱입니다.

Microsoft Outlook 앱만 Exchange Online에 액세스할 수 있도록 하려는 경우 iOS 및 Android에서 기본 제공 메일 앱을 차단할 수 있습니다. 또한 Intune 앱 보호 정책이 적용되지 않은 앱은 SharePoint Online에 액세스하지 못하도록 차단할 수 있습니다.

## <a name="prerequisites"></a>전제 조건
앱 기반 조건부 액세스 정책을 만들려면 다음 항목을 준비해야 합니다.

- **EMS(Enterprise Mobility + Security)** 또는 **Azure AD(Active Directory) Premium 구독**
- 사용자에게 EMS 또는 Azure AD 라이선스가 있어야 합니다.

자세한 내용은 [Enterprise Mobility 가격 책정](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing) 또는 [Azure Active Directory 가격 책정](https://azure.microsoft.com/pricing/details/active-directory/)을 참조하세요.

## <a name="supported-apps"></a>지원되는 앱

앱 기반 조건부 액세스를 지원하는 앱 목록은 [Azure Active Directory 조건부 액세스 기술 참조 문서](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-technical-reference)에서 확인할 수 있습니다.

앱 기반 조건부 액세스에서는 [LOB(기간 업무) 앱도 지원](app-modern-authentication-block.md)하지만, 이러한 앱은 [Office 365 최신 인증](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)을 사용해야 합니다. 

## <a name="how-app-based-conditional-access-works"></a>앱 기반 조건부 액세스의 작동 방식

이 예에서는 관리자가 앱 보호 정책을 Outlook 앱에 적용한 다음, 회사 이메일에 액세스할 때 사용할 수 있는 승인된 앱 목록에 Outlook 앱을 추가하는 조건부 액세스 규칙을 적용합니다.

> [!NOTE]
> 아래의 순서도 구조는 다른 관리되는 앱에도 사용할 수 있습니다.

![순서도에 예시된 앱 기반 조건부 액세스 프로세스](./media/app-based-conditional-access-intune/ca-intune-common-ways-3.png)

1. 사용자가 Outlook 앱에서 Azure AD에 인증을 시도합니다.

2. 사용자가 처음으로 인증을 시도할 때 앱 스토어로 리디렉션되며, 브로커 앱을 설치하라는 메시지가 표시됩니다. 브로커 앱은 iOS의 경우 Microsoft Authenticator, Android 디바이스의 경우 Microsoft 회사 포털일 수 있습니다.

   사용자가 기본 전자 메일 앱을 사용하려고 하면 앱 스토어로 리디렉션되며, Outlook 앱을 설치해야 합니다.

3. 디바이스에 브로커 앱이 설치됩니다.

4. 브로커 앱에서 Azure AD 등록 프로세스를 시작하며, 이 프로세스에서 Azure AD에 디바이스 레코드를 만듭니다. 이 프로세스는 MDM(모바일 디바이스 관리) 등록 프로세스와는 다르지만 조건부 액세스 정책을 디바이스에 적용하려면 이 레코드가 필요합니다.

5. 브로커 앱이 앱의 ID를 확인합니다. 앱이 사용자가 사용할 수 있도록 권한이 부여된 앱인지 브로커 앱이 유효성을 검사할 수 있는 보안 계층이 있습니다.

6. 브로커 앱은 사용자 인증 프로세스의 일환으로 Azure AD에 앱 클라이언트 ID를 보내서 해당 앱이 정책으로 승인된 목록에 있는지를 확인합니다.

7. Azure AD에서 사용자가 인증을 하고 정책으로 승인된 목록을 기반으로 앱을 사용하도록 허용합니다. 앱이 목록에 없으면 Azure AD는 앱 액세스를 거부합니다.

8. Outlook 앱이 Outlook 클라우드 서비스와 통신을 하여 Exchange Online과의 통신을 시작합니다.

9. Outlook 클라우드 서비스는 Azure AD와 통신을 하여 사용자에 대한 Exchange Online 서비스 액세스 토큰을 검색합니다.

10. Outlook 앱이 Exchange Online과 통신을 하여 사용자의 회사 전자 메일을 검색합니다.

11. 회사 전자 메일이 사용자의 사서함에 배달됩니다.

## <a name="next-steps"></a>다음 단계
[앱 기반 조건부 액세스 정책 만들기](app-based-conditional-access-intune-create.md)

[최신 인증이 없는 앱 차단](app-modern-authentication-block.md)
