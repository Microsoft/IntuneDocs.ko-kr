---
title: Microsoft Intune을 사용하는 조건부 액세스
titlesuffix: ''
description: Intune 조건부 액세스를 장치 및 앱 기반 조건부 액세스에 일반적으로 사용하는 방법에 대해 알아봅니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: 59cba4ead614fe0b5deac535efb9bcb303d5810d
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253612"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Intune에서 조건부 액세스를 사용하는 일반적인 방법이란?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune을 사용하는 조건부 액세스에는 장치 기반 조건부 액세스 및 앱 기반 조건부와 같은 두 가지 방법이 있습니다. 조직에서 조건부 액세스 규정 준수를 추진하는 관련 규정 준수 정책을 구성해야 합니다. 일반적으로 조건부 액세스를 사용하여 Exchange 온-프레미스에 대한 액세스를 허용하거나 차단하는 작업, 네트워크에 대한 액세스를 제어하는 작업 또는 Mobile Threat Defense 솔루션과 통합하는 작업 등을 수행합니다.

아래 정보는 Intune 모바일 *장치* 규정 준수 기능 및 Intune 모바일 *응용 프로그램* 관리(MAM) 기능 사용 방법의 이해에 도움이 됩니다. 

> [!NOTE]
> 조건부 액세스는 Azure Active Directory Premium 라이선스에 포함된 Azure Active Directory 기능입니다. Intune은 솔루션에 모바일 장치 호환성과 모바일 앱 관리 기능을 추가하여 이 기능을 향상합니다.

## <a name="device-based-conditional-access"></a>장치 기반 조건부 액세스

Intune과 Azure Active Directory는 연동되어 준수 상태의 관리 장치만 전자 메일, Office 365 서비스, SaaS(Software as a Service) 앱 및 [온-프레미스 앱](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)에 액세스할 수 있도록 합니다. 또한 Azure Active Directory에서 도메인에 가입된 컴퓨터 또는 Intune에 등록된 모바일 장치에서만 Office 365 서비스에 액세스할 수 있도록 하는 정책을 설정할 수도 있습니다.

Intune은 장치의 준수 상태를 평가하는 장치 준수 정책 기능을 제공합니다. 준수 상태는 Azure Active Directory에 보고되며, Azure Active Directory는 사용자가 회사 리소스에 액세스하려고 하면 Azure Active Directory에서 작성된 조건부 액세스 정책을 적용하는 데 이 상태를 사용합니다.

Exchange Online 및 기타 Office 365 제품용 장치 기반 조건부 액세스 정책이 [Azure Portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)을 통해 구성됩니다.

-   [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)에 대해 자세히 알아보세요.

-   [Intune 장치 준수](device-compliance.md)에 대해 자세히 확인해 보세요.

-   [Intune에서 조건부 액세스를 사용하여 전자 메일, Office 365 및 기타 서비스 보호](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune)에 대해 자세히 알아보세요.

### <a name="conditional-access-for-exchange-on-premises"></a>Exchange 온-프레미스에 대한 조건부 액세스

조건부 액세스를 사용하면 장치 준수 정책 및 등록 상태를 기반으로 **Exchange 온-프레미스**에 대한 액세스를 허용하거나 차단할 수 있습니다. 조건부 액세스를 장치 준수 정책과 함께 사용하면 준수 장치에서만 Exchange 온-프레미스에 액세스할 수 있습니다.

다음과 같은 보다 자세한 제어를 위해 조건부 액세스에서 고급 설정을 구성할 수 있습니다.

-   특정 플랫폼 허용 또는 차단

-   Intune에서 관리하지 않는 장치 즉시 차단

장치 준수 및 조건부 액세스 정책을 적용하면 Exchange 온-프레미스에 액세스하는 데 사용되는 모든 장치에서 준수를 확인합니다.

장치가 설정된 조건을 충족하지 않는 경우 최종 사용자에게 장치를 등록하고 비규격의 원인이 되는 문제를 해결하는 과정이 안내됩니다.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange 온-프레미스에 대한 조건부 액세스의 작동 방식

Intune Exchange 커넥터는 Exchange 서버에 있는 모든 EAS(Exchange Active Sync) 레코드를 끌어옵니다. 그러면 Intune에서 이러한 EAS 레코드를 가져와 Intune 장치 레코드에 매핑할 수 있습니다. 이러한 레코드는 Intune에 의해 등록 및 인식되는 장치입니다. 이 프로세스는 전자 메일 액세스를 허용하거나 차단합니다.

EAS 레코드가 신규 항목이어서 Intune이 인식할 수 없는 경우 Intune은 전자 메일 액세스를 차단하는 commandlet을 실행합니다. 이 프로세스의 작동 방식에 대한 자세한 내용이 아래에 나와 있습니다.

![CA를 사용하는 Exchange 온-프레미스 순서도](./media/ca-intune-common-ways-1.png)

1.  사용자가 Exchange 온-프레미스 2010 SP1 이상에서 호스트되는 회사 메일에 액세스하려고 합니다.

2.  Intune을 통해 관리되지 않는 장치의 경우 메일 액세스가 차단됩니다. Intune에서 EAS 클라이언트에 차단 알림을 보냅니다.

3.  EAS는 차단 알림을 수신하면 장치를 격리로 이동한 다음 사용자가 장치를 등록할 수 있도록 링크가 포함된 수정 단계를 제공하는 격리 메일을 전송합니다.

4.  장치가 Intune을 통해 관리되도록 하려면 가장 먼저 수행해야 하는 단계인 작업 공간 연결 프로세스가 진행됩니다.

5.  장치가 Intune에 등록됩니다.

6.  Intune이 EAS 레코드를 장치 레코드에 매핑하고 장치 준수 상태를 저장합니다.

7.  Azure AD 장치 등록 프로세스를 통해 EAS 클라이언트 ID가 등록됩니다. 그러면 Intune 장치 레코드와 EAS 클라이언트 ID 간의 관계가 작성됩니다.

8.  Azure AD 장치 등록에서 장치 상태 정보가 저장됩니다.

9.  사용자가 조건부 액세스 정책을 충족하는 경우 Intune에서 Intune Exchange 커넥터를 통해 사서함 동기화를 허용하는 commandlet을 실행합니다.

10. 사용자가 전자 메일에 액세스할 수 있도록 Exchange 서버가 EAS 클라이언트에 알림을 전송합니다.

#### <a name="whats-the-intune-role"></a>Intune 역할이란?

Intune은 장치 상태를 평가하고 관리합니다.

#### <a name="whats-the-exchange-server-role"></a>Exchange 서버 역할이란?

Exchange 서버는 장치를 해당 격리로 이동하는 API 및 인프라를 제공합니다.

> [!IMPORTANT]
> 장치를 사용하는 사용자에게 준수 프로필이 할당되어 있어야 장치에 대한 준수 여부가 평가됩니다. 사용자에게 규정 준수 정책이 배포되지 않은 경우 장치는 준수하는 것으로 간주되며 액세스 제한이 적용되지 않습니다.

### <a name="conditional-access-based-on-network-access-control"></a>네트워크 액세스 제어 기준 조건부 액세스

Intune은 Cisco ISE, Aruba Clear Pass, Citrix NetScaler 등의 파트너 제품과 통합되어 Intune 등록 및 장치 준수 상태에 따른 액세스 제어 기능을 제공합니다.

장치가 관리되는지 여부와 Intune 장치 준수 정책을 준수하는지 여부에 따라 사용자가 회사 Wi-Fi 또는 VPN 리소스에 액세스할 때 액세스가 허용되거나 거부될 수 있습니다.

-   자세한 내용은 [Intune과 NAC 통합](network-access-control-integrate.md)을 참조하세요.

### <a name="conditional-access-based-on-device-risk"></a>장치 위험 기준 조건부 액세스

Intune은 보안 솔루션을 제공하는 Mobile Threat Defense 공급업체와의 제휴를 통해 모바일 장치에서 맬웨어, 트로이 목마 및 기타 위협을 검색합니다.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune과 Mobile Threat Defense 통합의 작동 방식

모바일 장치에 Mobile Threat Defense 에이전트가 설치되어 있으면 해당 에이전트는 모바일 장치 자체에서 위협이 발견되었는지를 보고하는 준수 상태 메시지를 Intune으로 다시 보낼 수 있습니다.

Intune과 Mobile Threat Defense 통합은 장치 위험 기반 조건부 액세스를 결정할 때 중요한 요인으로 작용합니다.

-   [Intune Mobile Threat Defense](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense)에 대해 자세히 알아보세요.

### <a name="conditional-access-for-windows-pcs"></a>Windows PC에 대한 조건부 액세스

PC에 대한 조건부 액세스는 모바일 장치에 사용할 수 있는 것과 유사한 기능을 제공합니다. 이 항목에서는 Intune으로 PC를 관리할 때 조건부 액세스를 사용할 수 있는 방식을 설명합니다.

#### <a name="corporate-owned"></a>회사 소유

-   **온-프레미스 AD 도메인 가입:** 기존에 자사에서 AD 그룹 정책 및/또는 System Center Configuration Manager로 PC를 관리하는 방식에 어느 정도 익숙한 조직에서 흔히 사용되는 옵션입니다.

-   **Azure Active Directory 도메인 가입 및 Intune 관리:** 이 시나리오는 대개 장치가 회사 네트워크에 거의 연결되지 않는 CYOD(Choose Your Own Device) 및 로밍 노트북 시나리오에서 사용됩니다. 이 경우 장치는 Azure AD에 가입한 다음 Intune에 등록되므로 온-프레미스 AD 및 도메인 컨트롤러에 종속되지 않습니다. 회사 리소스에 액세스할 때는 이 시나리오를 조건부 액세스 기준으로 사용할 수 있습니다.

-   **AD 도메인 가입 및 System Center Configuration Manager:** 현재 분기를 기준으로 할 때 System Center Configuration Manager는 도메인에 가입된 PC 이외에 다음과 같은 특정 준수 기준도 평가할 수 있는 조건부 액세스 기능을 제공합니다.

    -   PC의 암호화 여부

    -   맬웨어 설치 여부 PC가 최신 상태인지 여부

    -   장치가 탈옥 또는 루팅되었는지 여부

#### <a name="bring-your-own-device-byod"></a>BYOD(Bring Your Own Device)

-   **작업 공간 연결 및 Intune 관리:** 이 경우 사용자는 개인 장치에 연결하여 회사 리소스 및 서비스에 액세스할 수 있습니다. 작업 공간 연결을 사용하여 장치를 Intune에 등록하면 장치 수준 정책을 수신할 수 있습니다. 이러한 방식은 조건부 액세스 기준을 평가할 수 있는 또 다른 옵션이기도 합니다.

## <a name="app-based-conditional-access"></a>앱 기반 조건부 액세스

Intune 및 Azure Active Directory는 연동되어 관리되는 앱만 회사 전자 메일 또는 기타 Office 365 서비스에 액세스할 수 있도록 합니다.

-   [Intune을 사용하는 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)에 대해 자세히 알아보세요.

## <a name="next-steps"></a>다음 단계

[Azure Active Directory에서 조건부 액세스를 구성하는 방법](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Intune과 함께 온-프레미스 Exchange 커넥터를 설치하는 방법](https://docs.microsoft.com/intune/exchange-connector-install)

[Exchange 온-프레미스에 대한 조건부 액세스 정책을 만드는 방법](conditional-access-exchange-create.md)
