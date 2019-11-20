---
title: 조건부 액세스 시나리오
titleSuffix: Microsoft Intune
description: Intune 조건부 액세스를 디바이스 및 앱 기반 조건부 액세스에 일반적으로 사용하는 방법에 대해 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9795ca8a585fd926cc269d493760b37aa7666eb
ms.sourcegitcommit: f46df983b66845bea24a90aaa2ac6cace16b9b0b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051966"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Intune에서 조건부 액세스를 사용하는 일반적인 방법이란?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Intune을 사용하는 조건부 액세스에는 디바이스 기반 조건부 액세스 및 앱 기반 조건부와 같은 두 가지 방법이 있습니다. 조직에서 조건부 액세스 규정 준수를 추진하는 관련 규정 준수 정책을 구성해야 합니다. 일반적으로 조건부 액세스를 사용하여 Exchange에 대한 액세스를 허용하거나 차단하는 작업, 네트워크에 대한 액세스를 제어하는 작업 또는 Mobile Threat Defense 솔루션과 통합하는 작업 등을 수행합니다.
 
이 문서에 있는 정보는 Intune 모바일 *디바이스* 규정 준수 기능 및 Intune 모바일 *애플리케이션* 관리(MAM) 기능 사용 방법의 이해에 도움이 됩니다. 

> [!NOTE]
> 조건부 액세스는 Azure Active Directory Premium 라이선스에 포함된 Azure Active Directory 기능입니다. Intune은 솔루션에 모바일 디바이스 호환성과 모바일 앱 관리 기능을 추가하여 이 기능을 향상합니다. *Intune*에서 액세스되는 조건부 액세스 노드는 *Azure AD*에서 액세스한 것과 동일한 노드입니다.  

## <a name="device-based-conditional-access"></a>디바이스 기반 조건부 액세스

Intune과 Azure Active Directory는 연동되어 준수 상태의 관리 디바이스만 전자 메일, Office 365 서비스, SaaS(Software as a Service) 앱 및 [온-프레미스 앱](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started)에 액세스할 수 있습니다. 또한 Azure Active Directory에서 도메인에 가입된 컴퓨터 또는 Intune에 등록된 모바일 디바이스에서만 Office 365 서비스에 액세스할 수 있도록 하는 정책을 설정할 수도 있습니다.

Intune은 디바이스의 준수 상태를 평가하는 디바이스 준수 정책 기능을 제공합니다. 준수 상태는 Azure Active Directory에 보고되며, Azure Active Directory는 사용자가 회사 리소스에 액세스하려고 하면 Azure Active Directory에서 작성된 조건부 액세스 정책을 적용하는 데 이 상태를 사용합니다.

Exchange Online 및 기타 Office 365 제품용 디바이스 기반 조건부 액세스 정책이 [Azure Portal](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune)을 통해 구성됩니다.  

- [Azure Active Directory의 조건부 액세스를 사용하여 관리 디바이스 필요](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)에 대해 자세히 알아봅니다.

- [Intune 디바이스 준수](device-compliance-get-started.md)에 대해 자세히 확인해 보세요.

- [Azure Active Directory의 조건부 액세스를 사용하여 지원되는 브라우저](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers)에 대해 자세히 알아봅니다.

> [!NOTE]
> Android 디바이스에서 SharePoint Online에 대한 디바이스 기반 액세스 또는 Exchange Online에 대한 브라우저 기반 액세스를 사용하도록 설정하는 경우 사용자는 다음과 같이 등록된 디바이스에서 **브라우저 액세스 사용** 옵션을 사용해야 합니다.
> 1. **회사 포털 앱**을 시작합니다.
> 2. 세 개의 점(...) 또는 하드웨어 메뉴 단추에서 **설정** 페이지로 이동합니다.
> 3. **브라우저 액세스 사용** 단추를 누릅니다. 
> 4. Chrome 브라우저에서, Office 365에서 로그아웃하고 Chrome을 다시 시작합니다.

### <a name="conditional-access-based-on-network-access-control"></a>네트워크 액세스 제어 기준 조건부 액세스

Intune은 Cisco ISE, Aruba Clear Pass, Citrix NetScaler 등의 파트너 제품과 통합되어 Intune 등록 및 디바이스 준수 상태에 따른 액세스 제어 기능을 제공합니다.

사용 중인 디바이스가 관리되는지 여부와 Intune 디바이스 준수 정책을 준수하는지 여부에 따라 사용자가 회사 Wi-Fi 또는 VPN 리소스에 대한 액세스가 허용되거나 거부될 수 있습니다.

- 자세한 내용은 [Intune과 NAC 통합](network-access-control-integrate.md)을 참조하세요.

### <a name="conditional-access-based-on-device-risk"></a>디바이스 위험 기준 조건부 액세스

Intune은 보안 솔루션을 제공하는 Mobile Threat Defense 공급업체와의 제휴를 통해 모바일 디바이스에서 맬웨어, 트로이 목마 및 기타 위협을 검색합니다.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Intune과 Mobile Threat Defense 통합의 작동 방식

모바일 디바이스에 Mobile Threat Defense 에이전트가 설치되어 있으면 해당 에이전트는 모바일 디바이스 자체에서 위협이 발견되었는지를 보고하는 준수 상태 메시지를 Intune으로 다시 보냅니다.

Intune과 Mobile Threat Defense 통합은 디바이스 위험 기반 조건부 액세스를 결정할 때 중요한 요인으로 작용합니다.

- [Intune Mobile Threat Defense](mobile-threat-defense.md)에 대해 자세히 알아보세요.

### <a name="conditional-access-for-windows-pcs"></a>Windows PC에 대한 조건부 액세스

PC에 대한 조건부 액세스는 모바일 디바이스에 사용할 수 있는 것과 유사한 기능을 제공합니다. 이 항목에서는 Intune으로 PC를 관리할 때 조건부 액세스를 사용할 수 있는 방식을 설명합니다.

#### <a name="corporate-owned"></a>회사 소유

- **온-프레미스 AD 도메인 가입:** 기존에 자사에서 AD 그룹 정책 또는 System Center Configuration Manager로 PC를 관리하는 방식에 어느 정도 익숙한 조직에서 흔히 사용되는 옵션입니다.

- **Azure AD 도메인 가입 및 Intune 관리:** 이 시나리오는 클라우드 우선(즉, 온-프레미스 인프라 사용을 줄이기 위해 클라우드 서비스를 주로 사용함) 또는 클라우드 전용(온-프레미스 인프라 없음)을 사용하려는 조직을 위한 것입니다. Azure AD 조인은 하이브리드 환경에서 정상적으로 작동하여 클라우드 및 온-프레미스 앱과 리소스에 모두 액세스할 수 있도록 합니다. 디바이스가 Azure AD에 조인되고 Intune에 등록되면 회사 리소스에 액세스할 때 조건부 액세스 조건으로 사용할 수 있습니다.

- **AD 도메인 가입 및 System Center Configuration Manager:** 현재 분기를 기준으로 할 때 System Center Configuration Manager는 도메인에 가입된 PC 이외에 다음과 같은 특정 준수 기준도 평가할 수 있는 조건부 액세스 기능을 제공합니다.

  - PC의 암호화 여부

  - 맬웨어 방지 설치 여부 PC가 최신 상태인지 여부

  - 디바이스가 탈옥 또는 루팅되었는지 여부

#### <a name="bring-your-own-device-byod"></a>BYOD(Bring Your Own Device)

- **작업 공간 연결 및 Intune 관리:** 이 경우 사용자는 개인 디바이스에 연결하여 회사 리소스 및 서비스에 액세스할 수 있습니다. 작업 공간 연결을 사용하여 디바이스를 Intune MDM에 등록하면 디바이스 수준 정책을 수신할 수 있습니다. 이러한 방식은 조건부 액세스 기준을 평가할 수 있는 다른 옵션입니다.

[Azure Active Directory의 디바이스 관리](https://docs.microsoft.com/azure/active-directory/devices/overview)에 대해 자세히 알아봅니다.

## <a name="app-based-conditional-access"></a>앱 기반 조건부 액세스

Intune 및 Azure Active Directory는 연동되어 관리되는 앱만 회사 전자 메일 또는 기타 Office 365 서비스에 액세스할 수 있도록 합니다.

- [Intune을 사용하는 앱 기반 조건부 액세스](app-based-conditional-access-intune.md)에 대해 자세히 알아보세요.

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Exchange 온-프레미스에 대한 Intune 조건부 액세스

조건부 액세스를 사용하면 디바이스 준수 정책 및 등록 상태를 기반으로 **Exchange 온-프레미스**에 대한 액세스를 허용하거나 차단할 수 있습니다. 조건부 액세스를 디바이스 준수 정책과 함께 사용하면 준수 디바이스에서만 Exchange 온-프레미스에 액세스할 수 있습니다.

다음과 같은 보다 자세한 제어를 위해 조건부 액세스에서 고급 설정을 구성할 수 있습니다.

- 특정 플랫폼 허용 또는 차단

- Intune에서 관리하지 않는 디바이스 즉시 차단

디바이스 준수 및 조건부 액세스 정책을 적용하면 Exchange 온-프레미스에 액세스하는 데 사용되는 모든 디바이스에서 준수를 확인합니다.

디바이스가 설정된 조건을 충족하지 않는 경우 최종 사용자에게 디바이스를 등록하고 비규격의 원인이 되는 문제를 해결하는 과정이 안내됩니다.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Exchange 온-프레미스에 대한 조건부 액세스의 작동 방식

Exchange 온-프레미스에 대한 조건부 액세스는 Azure 조건부 액세스 기반 정책과 다르게 작동합니다. Exchange server와 직접 상호 작용하려면 Intune Exchange 온-프레미스 커넥터를 설치합니다. Intune Exchange 커넥터는 Exchange 서버에 있는 모든 EAS(Exchange Active Sync) 레코드를 끌어옵니다. 그러면 Intune에서 이러한 EAS 레코드를 가져와 Intune 디바이스 레코드에 매핑할 수 있습니다. 이러한 레코드는 Intune에 의해 등록 및 인식되는 디바이스입니다. 이 프로세스는 전자 메일 액세스를 허용하거나 차단합니다.

EAS 레코드가 신규 항목이어서 Intune이 인식할 수 없는 경우 Intune은 Exchange 서버에서 메일 액세스를 차단하도록 하는 cmdlet(“커맨드렛”으로 발음됨)을 실행합니다. 이 프로세스의 작동 방식에 대한 자세한 내용이 다음에 나와 있습니다.

![CA를 사용하는 Exchange 온-프레미스 순서도](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. 사용자가 Exchange 온-프레미스 2010 SP1 이상에서 호스트되는 회사 메일에 액세스하려고 합니다.

2. 디바이스가 Intune을 통해 관리되지 않는 경우 메일 액세스가 차단됩니다. Intune에서 EAS 클라이언트에 차단 알림을 보냅니다.

3. EAS는 차단 알림을 수신하면 디바이스를 격리로 이동한 후 사용자가 디바이스를 등록할 수 있도록 링크가 포함된 수정 단계를 제공하는 격리 메일을 전송합니다.

4. 디바이스가 Intune을 통해 관리되도록 하려면 가장 먼저 수행해야 하는 단계인 작업 공간 연결 프로세스가 진행됩니다.

5. 디바이스가 Intune에 등록됩니다.

6. Intune이 EAS 레코드를 디바이스 레코드에 매핑하고 디바이스 준수 상태를 저장합니다.

7. Azure AD 디바이스 등록 프로세스를 통해 EAS 클라이언트 ID가 등록됩니다. 그러면 Intune 디바이스 레코드와 EAS 클라이언트 ID 간의 관계가 작성됩니다.

8. Azure AD 디바이스 등록에서 디바이스 상태 정보가 저장됩니다.

9. 사용자가 조건부 액세스 정책을 충족하는 경우 Intune에서 Intune Exchange 커넥터를 통해 사서함 동기화를 허용하는 cmdlet을 실행합니다.

10. 사용자가 전자 메일에 액세스할 수 있도록 Exchange 서버가 EAS 클라이언트에 알림을 전송합니다.


#### <a name="whats-the-intune-role"></a>Intune 역할이란?

Intune은 디바이스 상태를 평가하고 관리합니다.

#### <a name="whats-the-exchange-server-role"></a>Exchange 서버 역할이란?

Exchange 서버는 디바이스를 해당 격리로 이동하는 API 및 인프라를 제공합니다.

> [!IMPORTANT]
> 디바이스를 사용하는 사용자에게 준수 프로필 및 Intune 라이선스가 할당되어 있어야 디바이스에 대한 준수 여부가 평가될 수 있습니다. 사용자에게 규정 준수 정책이 배포되지 않은 경우 디바이스는 준수하는 것으로 간주되며 액세스 제한이 적용되지 않습니다.

## <a name="next-steps"></a>다음 단계

[Azure Active Directory에서 조건부 액세스를 구성하는 방법](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[앱 기반 조건부 액세스 정책 설정](app-based-conditional-access-intune-create.md)

[Intune과 함께 온-프레미스 Exchange 커넥터를 설치하는 방법](exchange-connector-install.md)

[Exchange 온-프레미스에 대한 조건부 액세스 정책을 만드는 방법](conditional-access-exchange-create.md)
