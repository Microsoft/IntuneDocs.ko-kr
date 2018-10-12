---
title: Microsoft Intune을 사용하여 Windows 장치에 대한 등록 설정
titlesuffix: ''
description: Windows 장치에 대한 등록을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f94dbc2e-a855-487e-af6e-8d08fabe6c3d
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 31c3e7b6d255cd99efee134f0276fd4d15dab6b9
ms.sourcegitcommit: 2795255e89cbe97d0b17383d446cca57c7335016
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47403564"
---
# <a name="set-up-enrollment-for-windows-devices"></a>Windows 장치에 대한 등록 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서는 IT 관리자가 사용자를 위해 Windows 등록을 간소화하는 데 도움이 됩니다. [Intune을 설정](setup-steps.md)한 후에는 사용자가 회사 또는 학교 계정으로 [로그인](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)하여 Windows 장치를 등록합니다.  

Intune 관리자는 다음과 같은 방식으로 등록을 간소화할 수 있습니다.
- [자동 등록 사용](#enable-windows-10-automatic-enrollment)(Azure AD Premium 필요)
- [CNAME 등록](#simplify-windows-enrollment-without-azure-ad-premium)
- [대량 등록 사용](windows-bulk-enroll.md)(Azure AD Premium 및 Windows 구성 디자이너 필요)

다음의 두 가지 요소로 Windows 장치를 간편하게 등록하는 방법을 결정합니다.

- **Azure Active Directory Premium을 사용하나요?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)은 Enterprise Mobility + Security 및 기타 라이선싱 계획에 포함되어 있습니다.
- **사용자가 등록할 Windows 클라이언트 버전은 무엇인가요?** <br>Windows 10 장치는 회사 또는 학교 계정을 추가하여 자동으로 등록할 수 있습니다. 이전 버전은 회사 포털 앱을 사용하여 등록해야 합니다.

||**Azure AD Premium**|**기타 AD** |
|----------|---------------|---------------|  
|**Windows 10**|[자동 등록](#enable-windows-10-automatic-enrollment) |[사용자 등록](#enable-windows-enrollment-without-azure-ad-premium)|
|**이전 버전의 Windows**|[사용자 등록](#enable-windows-enrollment-without-azure-ad-premium)|[사용자 등록](#enable-windows-enrollment-without-azure-ad-premium)|

자동 등록을 사용할 수 있는 조직에서는 Windows 구성 디자이너 앱을 사용하여 [장치 대량 등록](windows-bulk-enroll.md)을 구성할 수도 있습니다.

## <a name="multi-user-support"></a>다중 사용자 지원

Intune에서는 Windows 10 크리에이터스 업데이트를 실행하고 Azure Active Directory 도메인에 조인된 장치에 대한 다중 관리를 지원합니다. 표준 사용자가 Azure AD 자격 증명으로 로그인하는 경우 해당 사용자 이름에 할당된 앱과 정책을 받게 됩니다. 현재 사용자는 앱 설치와 같은 셀프 서비스에 대해 회사 포털을 사용할 수 없습니다.

[!INCLUDE [AAD-enrollment](./includes/win10-automatic-enrollment-aad.md)]

## <a name="simplify-windows-enrollment-without-azure-ad-premium"></a>Azure AD Premium을 사용하지 않고 Windows 등록 간소화
등록을 간소화하려면 등록 요청을 Intune 서버에 리디렉션하는 DNS(도메인 이름 서버) 별칭(CNAME 레코드 형식)을 만듭니다. 그렇지 않으면, Intune에 연결하려는 사용자가 등록하는 동안 Intune 서버 이름을 입력해야 합니다.

**1단계: CNAME 만들기**(선택 사항)<br>
회사의 도메인에 대한 CNAME DNS 리소스 레코드를 만듭니다. 예를 들어, 회사의 웹 사이트가 contoso.com인 경우 DNS에 EnterpriseEnrollment.contoso.com을 enterpriseenrollment-s.manage.microsoft.com으로 리디렉션하는 CNAME을 만듭니다.

CNAME DNS 항목을 만드는 것은 선택 사항이지만 CNAME 레코드를 사용하면 사용자가 보다 쉽게 등록할 수 있습니다. 등록 CNAME 레코드가 없으면 사용자에게 MDM 서버 이름인 enrollment.manage.microsoft.com을 수동으로 입력하라는 메시지가 표시됩니다.

|유형|호스트 이름|지시 대상|TTL|
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1시간|
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|1시간|

회사에서 두 개 이상의 UPN 접미사를 사용하는 경우 각 도메인 이름에 대해 하나씩 CNAME을 만들고 EnterpriseEnrollment-s.manage.microsoft.com에 각각을 가리켜야 합니다. 예를 들어 Contoso의 사용자는 해당 이메일/UPN으로 다음 형식을 사용합니다.

- name@contoso.com
- name@us.contoso.com
- name@eu.constoso.com\

Contoso DNS 관리자는 다음 CNAME을 만들어야 합니다.

|유형|호스트 이름|지시 대상|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1시간|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1시간|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1시간|

`EnterpriseEnrollment-s.manage.microsoft.com` – 메일의 도메인 이름에서 도메인을 인식하여 Intune 서비스로 리디렉션을 지원합니다.

DNS 레코드 변경 내용이 전파되는 데는 최대 72시간이 걸릴 수 있습니다. DNS 레코드가 전파될 때까지 Intune에서 DNS 변경 내용을 확인할 수 없습니다.

**2단계: CNAME 확인**(선택 사항)<br>
1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **CNAME 유효성 검사**를 선택합니다.
2. **도메인** 상자에서 회사 웹 사이트를 입력한 다음, **테스트**를 선택합니다.

## <a name="tell-users-how-to-enroll-windows-devices"></a>사용자에게 Windows 장치를 등록하는 방법 안내
사용자에게 Windows 장치를 등록하는 방법과 장치가 관리될 때 발생할 수 있는 상황에 대해 알려주어야 합니다.

> [!NOTE]
> 최종 사용자는 특정 버전의 Windows용으로 할당된 Windows 앱을 보려면 Microsoft Edge를 통해 회사 포털 웹 사이트에 액세스해야 합니다. Google Chrome, Mozilla Firefox 및 Internet Explorer를 비롯한 다른 브라우저는 이런 유형의 필터링을 지원하지 않습니다.

최종 사용자 등록 지침은 [Intune에서 Windows 장치 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-windows)을 참조하세요. 사용자에게 [IT 관리자가 장치에서 볼 수 있는 정보](https://docs.microsoft.com/intune-user-help/what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows)를 검토하도록 지시할 수도 있습니다.

>[!IMPORTANT]
> 자동 MDM 등록을 사용하지 않지만 Windows 10 장치가 Azure AD에 가입된 경우 등록한 후에 두 레코드가 Intune 콘솔에 표시됩니다. Azure AD 가입 장치를 가진 사용자가 동일한 계정을 사용하여 **계정** > **회사 또는 학교에 액세스** 및 **연결**로 이동하는지 확인하여 중지할 수 있습니다. 

최종 사용자 작업에 대한 자세한 내용은 [Microsoft Intune에서 최종 사용자 환경 관련 리소스](end-user-educate.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [Azure에서 Intune을 사용하여 Windows 장치를 관리할 때 고려 사항](/intune-classic/deploy-use/intune-on-azure)
