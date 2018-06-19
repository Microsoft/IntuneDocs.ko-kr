---
title: Dynamics CRM Online 보호
description: 조건부 액세스로 Dynamics CRM Online을 보호하고 액세스를 제어합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 01/03/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f1c4522b-5a34-4f5a-89d2-7809c4352af7
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2f720c8a6613884397111c2a421fa1cfdc0eb53
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021798"
---
# <a name="protect-access-to-dynamics-crm-online-with-intune"></a>Intune을 사용하여 Dynamics CRM Online에 대한 액세스 보호

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune 조건부 액세스를 사용하여 iOS 및 Android 장치에서 Microsoft Dynamics CRM Online에 대한 액세스를 제어할 수 있습니다.  Intune 조건부 액세스에는 두 구성 요소가 포함되어 있습니다.
* [장치 준수 정책](introduction-to-device-compliance-policies-in-microsoft-intune.md) - 장치가 규격으로 간주되기 위해 준수해야 하는 정책입니다.
* [조건부 액세스 정책](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) - 여기서 장치가 서비스에 액세스하기 위해 충족해야 하는 조건을 지정합니다.

조건부 액세스가 어떻게 작동하는지에 대한 자세한 내용은 [메일 및 0365 및 기타 서비스에 대한 액세스 보호](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) 문서를 읽어보세요.

> [!IMPORTANT]
> 조건부 액세스를 배포하려면 Intune 및 Azure Active Directory Premium에 대한 구독이 있어야 하고, 사용자는 두 제품의 라이선스를 취득해야 합니다. **EMS(Enterprise Mobility + Security) 구독**에는 Intune 구독과 Azure Active Directory Premium 구독이 모두 포함되어 있습니다. 자세한 내용은 [Enterprise Mobility 가격 책정 페이지](https://www.microsoft.com/cloud-platform/enterprise-mobility-pricing)를 참조하세요. EMS 구독이 없는 경우에는 Azure Active Directory Premium에 대한 구독을 가져올 수 있습니다. [Azure Active Directory 가격 책정 페이지](https://azure.microsoft.com/pricing/details/active-directory/)를 참조하세요.

대상 사용자가 장치에서 Dynamics CRM 앱을 사용하려고 시도하는 경우 다음 평가가 발생합니다.

![장치에서 서비스에 대한 액세스가 허용 또는 차단되는지 여부를 결정하는 데 사용되는 결정 지점을 보여 주는 다이어그램](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Dynamics CRM Online에 액세스해야 하는 장치는 다음과 같아야 합니다.
* **Android** 또는 **iOS** 장치여야 합니다.
* Intune에 **등록**되어 있어야 합니다.
* 배포된 Intune 규정 준수 정책을 **준수**해야 합니다.

장치 상태는 지정한 조건에 따라 액세스를 부여하거나 차단하는 Azure Active Directory에 저장됩니다.

조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.
* 장치를 Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우, 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.
* 장치가 규정을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Microsoft Intune 웹 포털 또는 회사 포털 앱과 문제의 해결 방법을 알려 주는 메시지가 표시됩니다.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Dynamics CRM Online에 대한 조건부 액세스 구성  
### <a name="step-1-configure-active-directory-security-groups"></a>1단계: Active Directory 보안 그룹 구성

시작하기 전에 조건부 액세스 정책에 대한 Azure Active Directory 보안 그룹을 구성합니다. **Office 365 관리 센터**에서 이러한 그룹을 구성할 수 있습니다. 이러한 그룹을 사용하여 사용자를 대상으로 지정하거나 정책에서 사용자를 제외합니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 장치가 규정을 준수해야 리소스에 액세스할 수 있습니다.

Dynamics CRM 정책에 사용할 두 가지 그룹 유형을 지정할 수 있습니다.
* **대상이 지정된 그룹**. 정책이 적용되는 사용자 그룹을 포함합니다.
* **제외된 그룹**. 정책에서 제외되는 사용자 그룹을 포함합니다.

사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2단계: 규정 준수 정책 구성 및 배포
규정 준수 정책을 [만들어](create-a-device-compliance-policy-in-microsoft-intune.md) 이 정책의 영향을 받는 모든 장치에 [배포](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)합니다. 대상 그룹의 사용자가 사용하는 모든 장치가 여기에 해당됩니다.

> [!NOTE]
> 규정 준수 정책을 Intune 그룹에 배포하는 동안 Azure Active Directory 보안 그룹을 조건부 액세스 정책의 대상으로 합니다.

> [!IMPORTANT]
> 규정 준수 정책을 배포하지 않은 경우 장치는 준수하는 것으로 간주됩니다.

준비가 되었으면 3단계를 계속합니다.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>3단계: Dynamics CRM 정책 구성
다음으로 관리되고 규정을 준수하는 장치만 Dynamics CRM에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure Active Directory에 저장됩니다.

1. Intune 관리 콘솔에서 **정책 > 조건부 액세스 > Dynamics CRM Online 정책**을 선택합니다.

   ![Dynamics CRM Online 조건부 액세스 정책 페이지의 스크린샷](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2. **조건부 액세스 정책 사용**을 선택합니다.
3. **응용 프로그램 액세스**에서 다음 플랫폼에 조건부 액세스 정책을 적용하도록 선택할 수 있습니다.
   * **iOS**
   * **OWA(Outlook Web Access)**
4. **대상 그룹**에서 **수정**을 선택하여 정책을 적용할 Azure Active Directory 보안 그룹을 선택합니다. 모든 사용자 또는 선택한 사용자 그룹을 대상으로 지정할 수 있습니다.
5. **제외된 그룹**에서 필요에 따라 **수정**을 선택하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.
6. 작업이 끝나면 **저장**을 선택합니다.

이제 Dynamics CRM에 대한 조건부 액세스가 구성되었습니다. 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>준수 및 조건부 액세스 정책 모니터링

**그룹** 작업 영역에서 장치의 조건부 액세스 상태를 볼 수 있습니다.

모든 모바일 장치 그룹을 선택하고 **장치** 탭에서 다음 **필터**중 하나를 선택합니다.
* **AAD에 등록되지 않은 장치**. 이러한 장치는 Dynamics CRM에서 차단됩니다.
* **규격이 아닌 장치**. 이러한 장치는 Dynamics CRM에서 차단됩니다.
* **AAD 및 규격에 등록된 장치**. 이러한 장치는 Dynamics CRM에 액세스할 수 있습니다.

##  <a name="next-steps"></a>다음 단계
* [Exchange Online에 액세스 보호](restrict-access-to-exchange-online-with-microsoft-intune.md)

* [Exchange 온-프레미스에 대한 액세스 보호](restrict-access-to-exchange-onpremises-with-microsoft-intune.md)
* [SharePoint Online에 대한 액세스 보호](restrict-access-to-sharepoint-online-with-microsoft-intune.md)

* [비즈니스용 Skype Online에 대한 액세스 보호](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)
