---
title: Microsoft Intune이란?
description: Microsoft Intune이 어떻게 Enterprise Mobility + Security 솔루션의 MDM(모바일 디바이스 관리) 및 MAM(모바일 앱 관리) 구성 요소가 되며 회사 데이터를 보호하는 데 도움이 되는지 알아봅니다.
keywords: Intune이란
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/20/2019
ms.topic: overview
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: e0ba46314a7c44e8db89d11a2866c86375a4cdfd
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726182"
---
# <a name="what-is-microsoft-intune"></a>Microsoft Intune이란?

Microsoft Intune은 회사 데이터를 보호하면서 직원이 생산성을 높일 수 있도록 하는 EMM(엔터프라이즈 이동성 관리) 공간의 클라우드 기반 서비스입니다. 다른 Azure 서비스와 비슷하게 Azure Portal에서 Microsoft Intune을 사용할 수 있습니다. Intune을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

- 직원이 회사 데이터에 액세스하는 데 사용하는 모바일 디바이스 및 PC를 관리합니다.
- 직원이 사용하는 모바일 앱을 관리합니다.
- 직원이 회사 정보에 액세스하여 이를 공유하는 방법을 제어할 수 있게 하여 회사 정보를 보호합니다.
- 디바이스와 앱이 회사 보안 요구 사항을 준수하는지 확인합니다.

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune에서 해결할 수 있는 일반적인 비즈니스 문제

- [모바일 디바이스에서 액세스할 수 있도록 온-프레미스 메일 및 데이터 보호](common-scenarios.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
- [모바일 디바이스에서 안전하게 액세스할 수 있도록 Office 365 메일 및 데이터 보호](common-scenarios.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
- [직원에게 회사 소유의 휴대폰 발급](common-scenarios.md#issue-corporate-owned-phones-to-your-employees)
- [모든 직원에게 BYOD(Bring Your Own Device) 또는 개인 디바이스 프로그램 제공](common-scenarios.md#offer-a-bring-your-own-device-program-to-all-employees)
- [직원이 관리되지 않는 공용 키오스크에서 Office 365에 안전하게 액세스하도록 지원](common-scenarios.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
- [작업자에게 사용이 제한된 공유 태블릿 발급](common-scenarios.md#issue-limited-use-shared-tablets-to-your-employees)

## <a name="how-does-intune-work"></a>Intune은 어떻게 작동하나요?

Intune은 모바일 디바이스 및 앱을 관리하는 Microsoft EMS(Enterprise Mobility + Security)의 구성 요소입니다. Intune은 ID 및 액세스 제어를 위한 Azure AD(Azure Active Directory) 및 데이터 보호를 위한 Azure Information Protection과 같은 다른 EMS 구성 요소와 긴밀하게 통합됩니다. Intune과 Office 365를 함께 사용하면 조직의 정보를 보호하면서 직원이 사용하는 모든 디바이스에서 생산성을 높이도록 할 수 있습니다.

![Intune 아키텍처의 이미지](./media/what-is-intune/intunearch_sm.png)

Intune 아키텍처 다이어그램의 [확대 버전](./media/intunearchitecture.svg)을 보세요.

Intune 및 EMS 데이터 보호의 디바이스 및 앱 관리 기능을 어떻게 사용할지는 [해결하려는 비즈니스 문제](#common-business-problems-that-intune-helps-solve)에 따라 달라집니다. 예를 들면 다음과 같습니다.
* 소매점에서 교대로 근무하는 직원들이 공유할 단일 사용 디바이스 풀을 만드는 경우 디바이스 관리를 많이 활용할 수 있습니다.
* 직원이 자신의 개인 디바이스를 사용하여 회사 데이터에 액세스할 수 있도록 허용하는 경우(BYOD)에 앱 관리 및 데이터 보호를 이용할 수 있습니다.  
* 정보 작업자에게 회사 전화기를 발급하는 경우에는 모든 기술을 이용합니다.

## <a name="intune-device-management-explained"></a>Intune 디바이스 관리 설명
Intune 디바이스 관리는 모바일 운영 체제에서 사용할 수 있는 프로토콜 또는 API를 사용하여 작동합니다. 여기에는 다음과 같은 작업이 포함됩니다.
* IT 부서에서 회사 서비스에 액세스하는 디바이스의 인벤토리를 보유할 수 있도록 디바이스를 관리에 등록
* 회사 보안 및 상태 표준을 준수하도록 디바이스 구성
* 회사 서비스에 액세스하기 위한 인증서 및 Wi-Fi/VPN 프로필 제공
* 디바이스의 회사 표준 규정 준수에 대한 보고 및 측정
* 관리되는 디바이스에서 회사 데이터 제거  

**회사 데이터에 대한 액세스 제어**가 디바이스 관리 기능이라고 생각하는 경우가 종종 있습니다. 하지만 이것은 모바일 운영 체제가 제공하는 기능이 아니라 ID 공급자가 제공하는 기능입니다. Microsoft의 ID 공급자는 ID 및 액세스 관리 시스템인 Azure AD(Active Directory)입니다.  

Intune은 Azure AD와 통합되어 광범위한 액세스 제어 시나리오를 사용합니다. 예를 들어 모바일 디바이스가 Exchange와 같은 회사 서비스에 액세스하려면 Intune에서 정의한 회사 표준을 준수하도록 요구할 수 있습니다. 마찬가지로, 특정 모바일 앱 집합에서만 특정 회사 서비스를 사용하도록 제한할 수 있습니다. 예를 들어 Exchange Online에는 Outlook 또는 Outlook Mobile에서만 액세스하도록 제한할 수 있습니다.

## <a name="intune-app-management-explained"></a>Intune 앱 관리 설명
앱 관리에 대해 논의할 때는 다음에 대해 이야기합니다.
* 직원에게 모바일 앱 할당
* 앱이 실행될 때 사용되는 표준 설정으로 앱 구성
* 모바일 앱에서 회사 데이터를 사용 및 공유하는 방법 제어
* 모바일 앱에서 회사 데이터 제거   
* 앱 업데이트
* 모바일 앱 인벤토리 보고
* 모바일 앱 사용 현황 추적

MAM(모바일 앱 관리)이라는 용어는 이러한 작업을 개별적으로 의미하거나 특정 작업 조합을 의미하는 데 사용되기도 했습니다. 특히, 사용자들은 앱 구성의 개념을 모바일 앱 내에서 회사 데이터를 보호하는 개념과 결합하여 사용하는 것이 일반적입니다. 이는 일부 모바일 앱이 데이터 보안 기능을 구성할 수 있도록 하는 설정을 노출하기 때문입니다.

앱 구성 및 Intune에 대해 논의할 때는 특히 [iOS의 관리되는 앱 구성](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)과 같은 기술을 의미하는 것입니다.

Intune을 EMS의 다른 서비스와 함께 사용하면 모바일 운영 체제와 모바일 앱이 앱 구성을 통해 제공하는 기능 외에도 조직 모바일 앱 보안을 제공할 수 있습니다. EMS를 사용하여 관리되는 앱에서는 다음과 같이 보다 광범위한 일련의 모바일 앱 및 데이터 보호 기능에 액세스할 수 있습니다.

* [Single sign-on](https://docs.microsoft.com/azure/active-directory/active-directory-appssoaccess-whatis)  
* [다단계 인증](https://docs.microsoft.com/azure/active-directory/authentication/multi-factor-authentication)
* [앱의 조건부 액세스 - 모바일 앱에 회사 데이터가 포함된 경우 액세스 허용](../protect/app-based-conditional-access-intune.md)
* [동일한 앱 내의 개인 데이터에서 회사 데이터 격리](../apps/app-protection-policy.md)
* [앱 보호 정책(PIN, 암호화, 다른 이름으로 저장, 클립보드 등)](../apps/app-protection-policies.md)
* [모바일 앱에서 회사 데이터 초기화](../apps/apps-selective-wipe.md)
* [권한 관리 지원](https://docs.microsoft.com/information-protection/understand-explore/what-is-azure-rms)

![앱 관리 데이터 보안 수준을 보여 주는 이미지](./media/what-is-intune/managing-mobile-apps.png)

### <a name="intune-app-security"></a>Intune 앱 보안
앱 보안 제공은 앱 관리의 일부이며, Intune에서의 모바일 앱 보안은 다음을 의미합니다.
* 기업 IT 인식에서 개인 정보 격리 유지
* 복사, 잘라내기/붙여넣기, 보기 등 사용자가 회사 정보로 수행할 수 있는 작업 제한
* 모바일 앱에서 회사 데이터 제거(선택적 초기화 또는 회사 초기화라고도 함)

Intune은 **앱 보호 정책** 기능을 통해 모바일 앱 보안을 제공합니다. 앱 보호 정책은 Azure AD ID를 사용하여 개인 데이터에서 회사 데이터를 분리합니다. 회사 자격 증명을 사용하여 액세스되는 데이터에는 회사의 추가 보호가 제공됩니다.

예를 들어 사용자가 회사 자격 증명을 사용하여 자신의 디바이스에 로그온할 때 해당 회사 ID를 사용하면 개인 ID에 대해 거부되는 데이터에 액세스할 수 있습니다. 해당 회사 데이터가 사용되면 앱 보호 정책에서 데이터의 저장 및 공유 방법을 제어합니다. 사용자가 자신의 개인 ID를 사용하여 디바이스에 로그온할 때 액세스되는 데이터에 동일한 보호가 적용되지 않습니다. 이러한 방식으로 IT는 회사 데이터를 제어하는 반면 최종 사용자는 개인 데이터에 대한 제어 및 개인 정보 취급 방침을 유지 관리합니다.

## <a name="emm-with-and-without-device-enrollment"></a>디바이스 등록을 사용하거나 사용하지 않는 EMM
대부분의 엔터프라이즈 이동성 관리 솔루션은 기본 모바일 디바이스 및 모바일 앱 기술을 지원합니다. 이것은 일반적으로 조직의 MDM(모바일 디바이스 관리) 솔루션에 등록되는 디바이스와 연결됩니다. Intune은 이러한 시나리오를 지원하며 여러 가지 "등록 없는" 시나리오를 지원합니다.  

"등록 없는" 시나리오를 채택하는 범위는 조직마다 다릅니다. 일부 조직은 이를 표준화합니다. 개인 태블릿 같은 보조 디바이스를 허용하는 조직도 있습니다. 그렇지 않은 조직은 이를 전혀 지원하지 않습니다. 조직에서 모든 직원 디바이스를 MDM에 등록해야 하는 이 마지막 경우에도, 조직은 일반적으로 계약자, 공급업체 및 특정한 예외가 있는 디바이스에 대해 "등록 없는" 시나리오를 지원합니다.

등록된 디바이스에서도 Intune의 "등록 없는" 기술을 사용할 수 있습니다. 예를 들어 MDM에 등록된 디바이스에는 모바일 운영 체제에서 제공하는 “여는 위치” 보호 기능이 있을 수 있습니다. "여는 위치" 보호는 두 개의 앱(예: Outlook과 Word)이 모두 MDM 공급자에 의해 관리되지 않으면 하나의 앱에서 열린 문서를 다른 앱에서 열지 못하도록 제한하는 Apple iOS의 기능입니다. 또한 IT는 앱 보호 정책을 EMS가 관리하는 모바일 앱에 적용하여 다른 이름으로 저장을 제어하거나 다단계 인증을 제공합니다.

등록되거나 등록되지 않은 모바일 디바이스 및 앱에 대한 조직의 입장과는 상관없이 Intune에는 EMS의 일부로서 직원들의 생산성을 향상하면서 회사 데이터를 보호하도록 지원하는 도구가 있습니다.

## <a name="microsoft-intune-in-the-azure-portal"></a>Azure Portal의 Microsoft Intune

[Azure portal](https://portal.azure.com)은 Microsoft Intune 서비스를 찾을 수 있는 곳입니다.

Azure Portal에서 Microsoft Intune 환경의 주요 특징은 다음과 같습니다.

- 모든 EMS(Enterprise Mobility + Security) 구성 요소에 대한 통합 콘솔
- 웹 표준을 기반으로 하는 HTML 기반 콘솔
- 많은 작업을 자동화하는 Microsoft Graph API 지원
- 모든 Azure 애플리케이션에서 호환성을 제공하는 Azure AD(Active Directory) 그룹
- 대부분의 최신 웹 브라우저 지원

사용자 포털 환경을 사용자 지정하는 빠른 가이드는 [Azure Portal에서 Intune 시작](tutorial-walkthrough-intune-portal.md)을 참조하세요.

> [!NOTE]
> 이전 버전의 Microsoft Intune을 사용한 경우 다음 정보가 유용할 수 있습니다.
> * [Azure에서 내 기능은 어디에 있나요?](../ui-changes.md)는 Azure로 이동을 통해 변경된 특정 워크플로 및 UI를 보여 주는 참조입니다.
> * [Azure Portal의 Intune 클래식 그룹](groups-get-started.md)에서는 그룹 관리를 위해 Azure Active Directory 보안 그룹으로 이동하는 의미를 설명합니다.

### <a name="before-you-start"></a>시작하기 전에

Azure Portal에서 Intune을 사용하려면 Intune 관리 및 테넌트 계정이 있어야 합니다. 계정이 아직 없는 경우 [계정에 등록](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20)하세요.

### <a name="supported-web-browsers-for-the-azure-portal"></a>Azure Portal에 대해 지원되는 웹 브라우저

Azure Portal은 대부분의 최신 PC, Mac 및 태블릿에서 실행됩니다. 휴대폰은 지원되지 않습니다.
현재 지원되는 브라우저는 다음과 같습니다.

- Microsoft Edge(최신 버전)
- Microsoft Internet Explorer 11
- Safari(최신 버전, Mac만)
- Chrome(최신 버전)
- Firefox(최신 버전)

지원되는 브라우저에 대한 최신 정보는 [Azure Portal](https://docs.microsoft.com/azure/azure-preview-portal-supported-browsers-devices)을 참조하세요.

## <a name="next-steps"></a>다음 단계
* [Intune을 사용하는 일반적인 방법](common-scenarios.md)의 일부 읽기
* [Intune의 30일 평가판으로](free-trial-sign-up.md) 제품에 대해 알아보기
* Intune의 [기술 요구 사항 및 기능](supported-devices-browsers.md)에 대해 자세히 알아보기
