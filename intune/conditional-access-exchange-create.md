---
title: Exchange 조건부 액세스 정책 만들기
titlesuffix: Microsoft Intune
description: Intune에서 Exchange 온-프레미스 레거시 Exchange Online Dedicated의 조건부 액세스를 구성합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 127dafcb-3f30-4745-a561-f62c9f095907
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d44b7483d65eeb7b2a39783fb113c444184db4f3
ms.sourcegitcommit: fffa64f28278573dc83a846b647315def2108781
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48232225"
---
# <a name="create-a-conditional-access-policy-for-exchange-on-premises-and-legacy-exchange-online-dedicated"></a>Exchange 온-프레미스 및 레거시 Exchange Online Dedicated에 대한 조건부 액세스 정책 만들기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클은 장치 준수를 기반으로 Exchange 온-프레미스에 대한 조건부 액세스를 구성하는 방법을 설명합니다.

Exchange Online Dedicated 환경이 있고 신규 또는 기존 구성 상태인지를 확인해야 하는 경우 계정 관리자에게 문의하세요. Exchange 온-프레미스 또는 레거시 Exchange Online Dedicated 환경에 대한 메일 액세스를 제어하려면 Intune에서 Exchange 온-프레미스에 대한 조건부 액세스를 구성합니다.

## <a name="before-you-begin"></a>시작하기 전에

조건부 액세스를 구성하기 전에 다음을 확인합니다.

- Exchange 버전은 **Exchange 2010 SP1 이상**이어야 합니다. Exchange Server CAS(클라이언트 액세스 서버) 배열이 지원됩니다.

- Intune을 온-프레미스 Exchange에 연결하는 [Exchange Active Sync 온-프레미스 Exchange 커넥터](exchange-connector-install.md)를 사용해야 합니다.

    >[!IMPORTANT]
    >온-프레미스 Exchange 커넥터는 Intune 테넌트별로 다르며 다른 테넌트에서는 사용할 수 없습니다. 이제 Intune은 구독당 여러 온-프레미스 Exchange Connector를 지원합니다. 둘 이상의 온-프레미스 Exchange 조직이 있는 경우 각 Exchange 조직에 대해 별도의 커넥터를 설정할 수 있습니다.

- 컴퓨터에서 Exchange Server와 통신할 수 있는 한 해당되는 모든 컴퓨터에 온-프레미스 Exchange 조직에 대한 커넥터를 설치할 수 있습니다.

- 이 커넥터는 **Exchange CAS 환경**을 지원합니다. 원할 경우 Exchange CAS 서버에 직접 커넥터를 설치하는 것도 기술적으로 가능하지만 서버의 부하가 증가하므로 권장되지 않습니다. 커넥터를 구성할 때는 커넥터가 Exchange CAS 서버 중 하나와 통신하도록 설정해야 합니다.

- **Exchange ActiveSync**는 인증서 기반 인증 또는 사용자 자격 증명 항목으로 구성되어야 합니다.

- 조건부 액세스 정책이 구성되고 사용자를 대상으로 지정한 경우 사용자가 자신의 전자 메일에 연결하기 전에 사용하는 **장치**는 다음과 같아야 합니다.
    - Intune에 **등록**되어 있거나 도메인에 가입된 PC여야 합니다.
    - **Azure Active Directory에 등록**되어야 합니다. 또한 클라이언트 Exchange ActiveSync ID가 Azure Active Directory에 등록되어 있어야 합니다.
<br></br>
- Azure AD DRS(Device Registration Service)는 Intune 및 Office 365 고객에 대해 자동으로 활성화됩니다. ADFS 장치 등록 서비스를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 장치가 표시되지 않습니다. **Windows PC 및 Windows Phone 장치에는 적용되지 않습니다**.

- 해당 장치에 배포된 장치 준수 정책을 **준수**해야 합니다.

- 장치가 조건부 액세스 설정을 충족하지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.
    - 장치를 Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우, 회사 포털 앱을 설치하고 장치를 등록하며 메일을 활성화하는 방법에 대한 지침이 포함된 메시지가 표시됩니다. 이 프로세스는 또한 장치의 Exchange ActiveSync ID를 Azure Active Directory의 장치 레코드와 연결합니다.
    - 장치가 정책을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Intune 웹 포털 또는 회사 포털 앱과 문제를 해결하는 방법을 알려주는 메시지가 표시됩니다.

### <a name="support-for-mobile-devices"></a>모바일 장치에 대한 지원

- Windows Phone 8.1 이상
- iOS의 기본 메일 앱
- EAS 메일 클라이언트(예: Android 4 이상의 Gmail).
- EAS 메일 클라이언트 **Android 회사 프로필 장치:** **회사 프로필**의 **Gmail** 및 **Nine Work for Android Enterprise**만 Android 회사 프로필에 대해 지원됩니다. 조건부 액세스가 Android 회사 프로필에서 작동하려면 Gmail 또는 Nine Work for Android Enterprise 앱에 대한 이메일 프로필을 배포하며, 이러한 앱을 필수 설치로 배포해야 합니다.

> [!NOTE]
> Android 및 iOS용 Microsoft Outlook 앱은 지원되지 않습니다. 

### <a name="support-for-pcs"></a>PC 지원

Windows 8.1 이상에 설치된 기본 **메일** 응용 프로그램(Intune에 등록된 경우)


## <a name="configure-exchange-on-premises-access"></a>Exchange 온-프레미스 액세스 구성

1. [Azure Portal](https://portal.azure.com/)로 이동한 다음 Intune 자격 증명을 사용하여 로그인합니다.

1. 정상적으로 로그인되면 **Azure 대시보드**가 표시됩니다.

1. 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

1. **Intune**을 선택하면 **Intune 대시보드**가 표시됩니다.

1. **온-프레미스 액세스**를 선택합니다. **온-프레미스 액세스** 창에 조건부 액세스 정책의 상태 및 그 영향을 받는 장치가 표시됩니다.

1. **관리** 아래에서 **Exchange 온-프레미스 액세스**를 선택합니다.

1. **Exchange 온-프레미스 액세스** 창에서 **예**를 선택하여 Exchange 온-프레미스 액세스 제어를 사용하도록 설정합니다.

    > [!NOTE]
    > Exchange Active Sync 온-프레미스 커넥터를 구성하지 않은 경우 이 옵션은 사용할 수 없습니다.  Exchange 온-프레미스에 대한 조건부 액세스를 사용하도록 설정하기 전에 먼저 하나 이상의 커넥터를 설치하고 구성해야 합니다. 자세한 내용은 [Intune 온-프레미스 Exchange Connector 설치](exchange-connector-install.md)를 참조하세요.

1. **할당** 아래에서 **그룹 포함됨**을 선택합니다.  조건부 액세스를 적용해야 하는 보안 사용자 그룹을 사용합니다. 이 작업은 사용자가 Intune에 장치를 등록하고 준수 프로필을 준수하도록 요구합니다.

1. 특정 사용자 그룹을 제외하려면 **그룹 제외됨**을 선택하고 장치 등록 및 준수 대상에서 제외할 사용자 그룹을 선택하면 됩니다.

1. **설정** 아래에서 **사용자 알림**을 선택하여 기본 메일 메시지를 수정합니다. 이 메시지는 해당 장치가 준수되지 않으며 Exchange 온-프레미스에 액세스하려는 사용자에게 전송됩니다. 메시지 템플릿에는 마크업 언어가 사용됩니다.  입력할 때 메시지 모양에 대한 미리 보기도 표시될 수 있습니다.
    > [!TIP]
    > 마크업 언어에 대한 자세한 내용은 이 Wikipedia [문서](https://en.wikipedia.org/wiki/Markup_language)를 참조하세요.

1. **고급 Exchange Active Sync 액세스 설정** 창에서 다음 두 단계에 설명된 대로 Intune을 통해 관리되지 않는 장치의 액세스에 대한 전역 기본 규칙 및 플랫폼 수준 규칙을 설정합니다.

1. 조건부 액세스 또는 다른 규칙의 영향을 받지 않는 장치의 경우 Exchange에 대한 액세스를 허용하거나 차단하도록 선택할 수 있습니다.

   - 액세스를 허용하도록 설정하면 모든 장치에서 Exchange 온-프레미스에 즉시 액세스할 수 있습니다.  **그룹 포함됨**의 사용자에게 속한 장치는 이후에 준수 정책을 준수하지 않거나 Intune에 등록되지 않은 것으로 평가되는 경우 차단됩니다.
   - 액세스를 차단하도록 설정하면 모든 장치에서 초기에 Exchange 온-프레미스에 대한 액세스가 즉시 차단됩니다.  **그룹 포함됨**의 사용자에게 속한 장치는 Intune에 등록되고 준수하는 것으로 평가되는 경우 액세스 권한이 부여됩니다. Samsung Knox Standard를 실행하지 않는 Android 장치는 이 설정을 지원하지 않으므로 항상 차단됩니다.

1. **장치 플랫폼 예외** 아래에서 **추가**를 선택하여 플랫폼을 지정합니다. **관리되지 않는 장치 액세스** 설정이 **차단됨**으로 설정된 경우 등록 및 호환되는 장치는 차단에 대한 플랫폼 예외가 있는 경우에도 허용됩니다. **확인**을 선택하여 설정을 저장합니다.

1. **온-프레미스** 창에서 **저장**을 클릭하여 조건부 액세스 정책을 저장합니다.

## <a name="create-azure-ad-conditional-access-policies-in-intune"></a>Intune에서 Azure AD 조건부 액세스 정책 만들기

Intune 1704 릴리스부터는 관리자가 Intune Azure Portal에서 Azure AD 조건부 액세스 정책을 만들 수 있습니다. 이렇게 하면 Azure 워크로드와 Intune 워크로드 간을 전환하지 않아도 됩니다.

> [!IMPORTANT]
> Intune Azure Portal에서 Azure AD 조건부 액세스 정책을 만들려면 Azure AD Premium 라이선스가 있어야 합니다.

### <a name="to-create-azure-ad-conditional-access-policy"></a>Azure AD 조건부 액세스 정책을 만들려면

1. **Intune 대시보드**에서 **조건부 액세스**를 선택합니다.

2. **정책** 창에서 **새 정책**을 선택하여 새 Azure AD 조건부 액세스 정책을 만듭니다.

## <a name="see-also"></a>참고 항목

[Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access)
