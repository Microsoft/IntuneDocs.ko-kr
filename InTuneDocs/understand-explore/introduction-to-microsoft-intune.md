---
title: "Microsoft Intune이란? | Microsoft 문서"
description: "Intune이 어떻게 Enterprise Mobility + Security 솔루션의 모바일 장치 관리 구성 요소가 되며 회사 데이터를 보호하는 데 도움이 되는지 알아봅니다."
keywords: "Intune이란"
author: Lindavr
ms.author: lindavr
manager: angrobe
ms.date: 11/15/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d0057f1e3d2ead729c2143587571fa4b16a3dd2f
ms.openlocfilehash: 9b4eed086853c0feeb8266a8087a275f2b70e40f


---

# <a name="what-is-intune"></a>Intune이란?

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Intune은 직원이 회사 데이터를 보호하면서 생산성을 높일 수 있도록 하는 클라우드 기반 엔터프라이즈 이동성 관리(EMM) 서비스입니다. Intune을 사용하면 다음과 같은 작업을 수행할 수 있습니다.
* 직원이 회사 데이터에 액세스하는 데 사용하는 모바일 장치를 관리합니다.
* 직원이 사용하는 모바일 앱을 관리합니다.
* 직원이 회사 정보에 액세스하여 이를 공유하는 방법을 제어할 수 있게 하여 회사 정보를 보호합니다.
* 장치와 앱이 회사 보안 요구 사항을 준수하는지 확인합니다.

Intune은 ID 및 액세스 제어를 위한 Azure AD(Azure Active Directory) 및 데이터 보호를 위한 Azure RMS(Azure Rights Management)와 긴밀하게 통합됩니다. 이것은 Microsoft EMS(Enterprise Mobility + Security)의 *관리 암(arm)*이며, Office 365는 Microsoft의 이동성 솔루션의 *생산성 암(arm)*입니다.  

Office 365 및 EMS를 함께 사용하여 조직의 정보를 보호하면서 직원이 사용하는 모든 장치에서 생산성을 높일 수 있습니다. EMS와 함께 사용하는 Office 365는 생산성, ID, 액세스 제어, 관리 및 데이터 보호를 모두 포함하는 엔터프라이즈 이동성을 위한 완전한 통합 제품군입니다. 조직의 Mobility 솔루션을 배포하고 운영하는 효과적인 방법을 제공합니다.

## <a name="how-does-intune-work"></a>Intune은 어떻게 작동하나요?
Intune은 모바일 장치 관리(MDM) 및 모바일 앱 관리(MAM)를 제공합니다. Intune의 MDM 및 MAM 기능은 데이터 보호 및 규정 준수 시나리오로 구성된 EMS 모음에 사용됩니다.  

Intune 및 EMS 데이터 보호의 MDM/MAM 기능을 어떻게 사용할지는 [해결하려는 비즈니스 문제](#common-business-problems-that-intune-helps-solve)에 따라 달라집니다. 예를 들면 다음과 같습니다.
* 소매점에서 교대로 근무하는 직원들이 공유할 단일 사용 장치 풀을 만드는 경우 MDM을 활용할 수 있습니다.
* 직원이 자신의 개인 장치를 사용하여 회사 데이터(BYOD)에 액세스할 수 있도록 허용하는 경우에 MAM 및 데이터 보호를 이용할 수 있습니다.  
* 정보 작업자에게 회사 전화기를 발급하는 경우에는 이 두 기술 모두를 이용합니다.

## <a name="intune-mobile-device-management-mdm-explained"></a>Intune MDM(모바일 장치 관리) 설명
MDM은 모바일 운영 체제에서 사용할 수 있는 프로토콜 또는 API를 사용하여 작동합니다. 여기에는 다음과 같은 작업이 포함됩니다.
* IT 팀에서 회사 서비스에 액세스하는 장치의 인벤토리를 관리할 수 있도록 장치를 관리에 등록
* 회사 보안 및 상태 표준을 준수하도록 장치 구성
* 회사 서비스에 액세스하기 위한 인증서 및 Wi-Fi/VPN 프로필 제공
* 장치의 회사 표준 규정 준수에 대한 보고 및 측정
* 관리되는 장치에서 회사 데이터 제거  

**회사 데이터에 대한 액세스 제어**가 MDM 기능이라고 생각하는 경우가 종종 있습니다. 하지만 이것은 모바일 운영 체제가 제공하는 기능이 아니라 ID 공급자가 제공하는 기능입니다. Microsoft의 ID 공급자는 ID 및 액세스 관리 시스템인 Azure AD(Active Directory)입니다.  

Intune은 Azure AD와 통합되어 광범위한 액세스 제어 시나리오를 사용합니다. 예를 들어 모바일 장치가 Exchange와 같은 회사 서비스에 액세스하려면 Intune에 정의된 회사 표준을 준수하도록 요구할 수 있습니다. 마찬가지로, 특정 모바일 앱 집합에서만 특정 회사 서비스를 사용하도록 제한할 수 있습니다. 예를 들어 Exchange Online에는 Outlook 또는 Outlook Mobile에서만 액세스하도록 제한할 수 있습니다.

## <a name="intune-mobile-app-management-mam-explained"></a>Intune 모바일 앱 관리(MAM) 설명
Microsoft가 MAM에 대해 말할 때는 IT 전문가들이 Microsoft 솔루션을 통해 모바일 앱을 사용하여 다음과 같은 작업을 할 수 있음을 의미하는 것입니다.
* 직원들에게 모바일 앱 게시
* 앱 구성
* 모바일 앱에서 회사 데이터를 사용 및 공유하는 방법 제어
* 모바일 앱에서 회사 데이터 제거   
* 모바일 앱 업데이트
* 모바일 앱 인벤토리 보고
* 모바일 앱 사용 현황 추적

MAM은 이러한 작업을 개별적으로 의미하거나 작업들의 특정한 조합을 의미하는 데 사용되기도 했습니다. 특히 사용자들은 앱 구성의 개념(즉, [iOS에서 관리되는 앱 구성](https://developer.apple.com/library/content/samplecode/sc2279/Introduction/Intro.html)과 같은 기술의 사용)을 모바일 앱 내에서 회사 데이터를 보호한다는 개념과 혼합하여 사용하는 것이 일반적입니다. 이는 일부 모바일 앱이 데이터 보안 기능을 구성할 수 있도록 하는 설정을 노출하기 때문입니다.

그것은 데이터 보호를 위한 운영 체제 기능(예를 들어 Windows 10의 Windows 정보 보호와 같은 MDM 기능)과 더불어 모바일 장치에 다양한 데이터 보호 기능을 제공합니다.

Intune을 EMS의 다른 서비스와 함께 사용하면 모바일 운영 체제와 모바일 앱이 앱 구성을 통해 제공하는 기능 외에도 조직 모바일 앱 보안을 제공할 수 있습니다. EMS를 사용하여 관리되는 앱에서는 다음과 같이 보다 광범위한 모바일 앱 및 데이터 보호 기능 집합에 액세스할 수 있습니다.

* [Single sign-on](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-appssoaccess-whatis)  
*   [다단계 인증](https://docs.microsoft.com/en-us/multi-factor-authentication/multi-factor-authentication)
* [앱의 조건부 액세스(모바일 앱에 회사 데이터가 포함된 경우 액세스 허용)](https://docs.microsoft.com/en-us/intune/deploy-use/allow-policy-managed-apps-access-to-o365)
* [동일한 앱 내의 개인 데이터에서 회사 데이터 격리](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [앱 보호 정책(PIN, 암호화, 다른 이름으로 저장, 클립보드 등)](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [모바일 앱에서 회사 데이터 초기화](https://docs.microsoft.com/en-us/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune)
* [권한 관리 지원](https://docs.microsoft.com/en-us/information-protection/understand-explore/what-is-azure-rms)

![앱 관리 데이터 보안 수준을 보여 주는 이미지](./media/managing-mobile-apps.png)

### <a name="intune-mobile-app-security"></a>Intune 모바일 앱 보안
앱 보안 제공은 MAM의 일부이며, Intune에서의 모바일 앱 보안은 다음을 의미합니다.
* 기업 IT 인식에서 개인 정보 격리 유지
* 복사, 잘라내기/붙여넣기, 보기 등 사용자가 회사 정보로 수행할 수 있는 작업 제한
* 모바일 앱에서 회사 데이터 제거(선택적 초기화 또는 회사 초기화라고도 함)

Intune이 모바일 앱 보안을 제공하는 한 가지 방법은 **앱 보호 정책** 기능을 통해서입니다. 앱 보호 정책은 Azure AD ID를 사용하여 개인 데이터에서 회사 데이터를 분리합니다. 회사 자격 증명을 사용하여 액세스하는 데이터에는 회사의 추가 보호가 제공됩니다.

사용자가 회사 자격 증명을 사용하여 자신의 장치에 로그온할 때 자신의 회사 ID를 사용하면 개인 ID에 대해서는 거부되는 데이터에 액세스할 수 있습니다. 회사 데이터를 사용할 때와 같이 Intune은 다른 EMS 기술과 함께 데이터 저장 및 공유 방식을 제어합니다. 사용자가 자신의 개인 ID를 사용하여 자신의 장치에 로그온하여 액세스하는 데이터에는 그러한 보호가 적용되지 않습니다. 이러한 방식으로 IT는 회사 데이터를 제어하고 최종 사용자는 개인 데이터에 대한 제어 및 개인 정보 취급 방침을 유지 관리합니다.

## <a name="emm-with-and-without-device-enrollment"></a>장치 등록을 사용하거나 사용하지 않는 EMM
대부분의 엔터프라이즈 이동성 관리 솔루션은 기본 모바일 장치 및 모바일 앱 기술을 지원합니다. 이것은 일반적으로 조직의 MDM 솔루션에 등록되는 장치와 연결됩니다. Intune은 이러한 시나리오를 지원하며 여러 가지 "등록 없는" 시나리오를 지원합니다.  

"등록 없는" 시나리오를 채택하는 범위는 조직마다 다릅니다. 일부 조직은 이를 표준화합니다. 개인 태블릿 같은 보조 장치를 허용하는 조직도 있습니다. 그렇지 않은 조직은 이를 전혀 지원하지 않습니다. 모든 직원 장치를 MDM에 등록해야 하는 마지막 경우에도, 조직은 대개 계약자, 공급업체 및 특정한 예외가 있는 장치에 대해 “등록 없는” 시나리오를 지원합니다.

등록된 장치에서도 Intune의 "등록 없는" 기술을 사용할 수 있습니다. 예를 들어 MDM에 등록된 장치에는 모바일 운영 체제에서 제공하는 열기 보호 기능이 있을 수 있습니다. 열기 보호는 두 개의 앱(예: Outlook과 Word)이 모두 MDM 공급자에 의해 관리되는 경우 하나의 앱에서 열린 문서를 다른 앱에서 열지 못하도록 제한하는 iOS 기능입니다. 또한 IT는 앱 보호 정책을 EMS가 관리하는 모바일 앱에 적용하여 다른 이름으로 저장을 제어하거나 다단계 인증을 제공합니다.

등록되거나 등록되지 않은 모바일 장치 및 앱에 대한 조직의 입장과는 상관없이 Intune에는 EMS의 일부로서 직원들의 생산성을 향상하면서 회사 데이터를 보호하도록 지원하는 도구가 있습니다.

## <a name="common-business-problems-that-intune-helps-solve"></a>Intune에서 해결할 수 있는 일반적인 비즈니스 문제
다음 비즈니스 문제 목록은 Microsoft가 제공할 수 있는 솔루션에 대한 자세한 정보와 연결되어 있습니다. 마지막 항목만 솔루션의 일부로 MDM 등록이 필요합니다.

* [모바일 장치에서 액세스할 수 있도록 온-프레미스 메일 및 데이터 보호](common-ways-to-use-intune.md#protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [모바일 장치에서 안전하게 액세스할 수 있도록 Office 365 메일 및 데이터 보호](common-ways-to-use-intune.md#protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices)
* [직원에게 회사 소유의 휴대폰 발급](common-ways-to-use-intune.md#issue-corporate-owned-phones-to-your-information-workers)
* [모든 직원에게 BYOD(Bring Your Own Device) 또는 개인 장치 프로그램 제공](common-ways-to-use-intune.md#offer-a-bring-your-own-device-program-to-all-employees)
* [직원이 관리되지 않는 공용 키오스크에서 Office 365에 안전하게 액세스하도록 지원](common-ways-to-use-intune.md#enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk)
* [작업자에게 사용이 제한된 공유 태블릿 발급](common-ways-to-use-intune.md#issue-limited-use-shared-tablets-to-your-task-workers)

### <a name="next-steps"></a>다음 단계
* [Intune을 사용하는 일반적인 방법](common-ways-to-use-intune.md)의 일부 읽기
* [Intune의 30일 평가판으로](get-started-with-a-30-day-trial-of-microsoft-intune.md) 제품에 대해 알아보기
* Intune의 [기술 요구 사항 및 기능](/intune/get-started/what-to-know-before-you-start-microsoft-intune)에 대해 자세히 알아보기



<!--HONumber=Jan17_HO2-->

