---
title: Microsoft Intune 서비스 설명
description: Microsoft Intune은 Windows, iOS, Mac OS X, Android 및 Windows 모바일 디바이스를 관리하는 데 유용한 클라우드 기반 서비스입니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/30/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 40fa5a2e-6c0f-4150-9740-d5ddc0cdbda0
ms.reviewer: cacamp
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b25a72fdc552433886f7eb3349a8f396e2019ea
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041629"
---
# <a name="microsoft-intune-service-description"></a>Microsoft Intune 서비스 설명

Intune은 직원이 회사 데이터를 보호하면서 생산성을 높일 수 있도록 하는 클라우드 기반 엔터프라이즈 이동성 관리(EMM) 서비스입니다. Intune을 사용하면 다음과 같은 작업을 수행할 수 있습니다.
* 직원이 회사 데이터에 액세스하는 데 사용하는 모바일 디바이스를 관리합니다.
* 직원이 사용하는 클라이언트 앱을 관리합니다.
* 직원이 회사 정보에 액세스하여 이를 공유하는 방법을 제어할 수 있게 하여 회사 정보를 보호합니다.
* 디바이스와 앱이 회사 보안 요구 사항을 준수하는지 확인합니다.

Intune은 ID 및 액세스 제어를 위한 Azure AD(Azure Active Directory) 및 데이터 보호를 위한 Azure Information Protection과 긴밀하게 통합됩니다. System Center Configuration Manager와 통합하여 관리 기능을 확장할 수도 있습니다.

Intune을 사용하여 디바이스 및 앱을 관리하고 회사 데이터를 보호하는 방법에 대한 자세한 내용은 [Intune 설명서](https://docs.microsoft.com/intune/)를 참조하세요.

## <a name="30-day-free-trial"></a>30일 평가판
100개의 사용자 라이선스를 포함하는 30일 무료 평가판으로 Intune 사용을 시작할 수 있습니다. 무료 평가판을 시작하려면 [Intune 등록 페이지로 이동하세요](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=40BE278A-DFD1-470a-9EF7-9F2596EA7FF9&dl=INTUNE_A&ali=1#0%20). 조직에서 기업 계약 또는 이와 동등한 볼륨 라이선스 계약을 맺은 경우 Microsoft 담당자에게 문의하여 무료 평가판을 설정하세요.

> [!NOTE]
> 조직에 Microsoft Online Services 회사 또는 학교 계정이 있고 평가 기간이 종료된 후 프로덕션에서 이 Intune 구독을 계속 사용할 수 있는 경우, 해당 페이지에서 **로그인** 옵션을 선택하고 조직의 전역 관리자 계정을 사용하여 인증해야 합니다. 이 작업을 통해 Intune 평가판을 기존 회사 또는 학교 계정에 연결할 수 있습니다.

<!--- For a list of settings that you can set up on mobile devices, see:

-   [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)

-   [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management)

For more about System Center Configuration Manager, see [Documentation  for System Center Configuration Manager](/sccm/index).--->
## <a name="intune-onboarding-benefit"></a>Intune 등록 혜택
Microsoft는 적합한 플랜의 적합한 서비스에 대해 Intune 온보딩 혜택을 제공합니다. 등록 혜택을 이용하면 Microsoft 전문가와 원격으로 함께 작업하여 Intune 환경을 즉시 사용하도록 준비할 수 있습니다. 등록 혜택에 대한 자세한 내용은 [Microsoft Intune 등록 혜택 설명](http://go.microsoft.com/fwlink/?LinkId=619281)을 참조하세요.


## <a name="learn-how-intune-service-updates-affect-you"></a>Intune 서비스 업데이트가 영향을 주는 방식 알아보기

모바일 디바이스 관리 에코시스템은 운영 체제 업데이트 및 모바일 앱 릴리스로 자주 변경되므로, Microsoft는 Intune을 정기적으로 업데이트합니다. 세 가지 방법으로 Intune 서비스 변경 내용을 파악할 수 있습니다.

- [Microsoft Intune의 새로운 기능](whats-new.md). 이 항목은 월별 서비스 업데이트와 함께 업데이트되며 회사 포털 앱 등의 앱이 릴리스되는 경우 매주 업데이트됩니다.

- 중요한 서비스 업데이트는 [Microsoft 365 관리 센터](https://admin.microsoft.com/) 메시지 센터에서도 공지됩니다. 제공된 [Office 365 관리자 모바일 앱](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)을 설치한 경우 모바일 디바이스에서 알림을 받을 수 있습니다. [Office 365 메시지 센터](https://support.office.com/client/results?Shownav=true&ns=O365ENTADMIN&version=15&ver=15&HelpID=O365E_MCManageUpdates)를 사용하는 방법을 자세히 알아봅니다.

    아래에는 그 외의 몇 가지 유용한 정보가 나와 있습니다.

    - Office 365 메시지 센터의 메시지는 특정 대상에게 제공되는 것입니다. 즉, 회사에서 Intune for EDU 서비스를 사용하지 않는 경우에는 Intune for EDU 관련 메시지가 제공되지 않습니다.

    - 메시지에는 만료 기간이 있습니다. 예를 들어 새로운 기능 페이지 링크가 포함된 서비스가 업데이트되었다는 알림은 다음 서비스 업데이트 알림 전에 만료될 가능성이 높습니다. 메시지에 만료 기간이 없으면 더 이상 관련이 없는 많은 게시물이 누적되어 백로그가 커지게 됩니다.

    - Office 365 관리자 모바일 앱에서는 모든 메시지를 검색하여 조직의 동료와 공유하려는 알림을 전달할 수 있습니다.

    - 메시지 센터 기본 설정 편집 아래에 **Intune**용 토글이 포함될 예정이므로, iNTUNE 구독에 대해 게시된 메시지를 확인할 수 있습니다. Office 365용 모바일 디바이스 관리는 Intune이 아닌 다른 서비스이므로 해당 메시지는 Intune과는 관련이 없습니다.

- 또한 다음 두 개의 블로그에서 EMS 메시지 및 Intune 지원 모범 사례가 제공됩니다.

    - [Enterprise Mobility + Security 블로그](https://blogs.technet.microsoft.com/enterprisemobility/)

    - [Intune 지원 블로그](https://blogs.technet.microsoft.com/intunesupport/)

>[!Note]
>[Microsoft 365 관리 센터](https://admin.microsoft.com)에서 Intune 서비스 상태를 모니터링할 수 있습니다. 왼쪽 창에서 **서비스 상태**를 선택합니다. [Office 365 관리자 모바일 앱](https://support.office.com/article/Office-365-Admin-Mobile-App-e16f6421-2a1a-4142-bf9d-9846600a060a)을 사용하여 서비스 상태를 확인할 수도 있습니다.

## <a name="types-of-notices-microsoft-provides-about-the-intune-service"></a>Microsoft가 Intune 서비스에 관하여 제공하는 알림 유형

서비스 변경을 계획하도록 돕기 위해 변경의 영향에 따라 서비스를 변경하기 최소 7-90일 전에 알림이 제공됩니다. 이러한 변경에는 다음과 같은 유형의 변경이 포함될 수 있습니다.

- 기술 지원팀 담당자나 최종 사용자와 공유하려는 최종 사용자 환경 변경 내용. 일반적으로 이러한 변경을 수행하기 7-30일 전에 알림이 제공되며, [Intune 앱 UI의 새로운 기능](whats-new-app-ui.md)에 관련 정보가 문서로 작성됩니다. 철자 오류 수정과 같은 변경의 경우에는 대개 설명서에 관련 정보가 포함되지 않습니다. 그러나 최종 사용자 등록 환경 변경은 UI에서 중요한 변경이므로 Office 365 메시지 센터에 고객 대상 메시지와 Intune 앱 UI의 새로운 기능에 대한 링크가 모두 게시됩니다. 따라서 변경되는 내용 관련 알림을 확인하고 프로덕션 환경에 변경 내용이 실제로 적용되기 전에 최종 사용자 지침을 평가 및 업데이트할 수 있습니다.

- 조치를 취해야 하는 변경인 **변경 계획**의 경우 보통 약 30일 전에 알림이 제공됩니다. Office 365 메시지 센터에서 해당 범주의 이름이 변경 계획이므로 쉽게 확인할 수 있습니다. 또한 프로덕션 환경에 변경 내용을 적용할 정확한 날짜가 결정되면 쉽게 확인 가능한 대기열에 느낌표가 표시된 **조치 기한** 날짜도 제공됩니다.

- 대다수 사용 중단의 경우에는 기본적으로 90일 전에 알림을 제공합니다. 예를 들어 특정 IE 버전을 더 이상 지원하지 않을 예정인 경우에는 90일 전에 알림을 제공하는 것이 목표입니다. 그러나 사용 중단을 다른 회사에서 발표하는 경우에는 상황이 복잡해집니다. 예를 들어 브라우저 업체가 최신 빌드에서 Silverlight를 더 이상 지원하지 않는다는 알림을 제공하는 경우에도 Microsoft는 당사의 90일 전 알림 정책에 따라 해당 브라우저 지원을 중단함을 고객에게 알립니다.

- Intune 서비스 사용 중지 시 12개월 전에 알림을 받을 것입니다.

마지막으로, 드물지만 서비스를 정상 상태로 복구하거나 고객의 의견에 따라 서비스가 중지될 수도 있는 대규모 변경을 수행하기 위해 특정 인시던트 이후에 조치를 취해야 하는 경우에는 고객의 [Office 365 통신 기본 설정](https://support.office.com/article/Change-your-contact-preferences-for-communications-from-Microsoft-6f70de1b-a64d-4498-bfbd-be8c83a9c0fc)이 설정된 방식과 고객이 유효한 전자 메일 주소를 포함했는지 여부(현재 사용 중인 주소를 포함하는 것이 좋음)에 따라 서비스 관리자에게 전자 메일을 전송합니다.  


<!--- ## Choose the management solution that’s right for you
You can set up Intune in several ways to manage and help protect your company's mobile devices and computers (referred to as **devices** in this article).

- **Intune stand-alone configuration.** Use the web-based admin console in Intune to manage devices in your organization. Intune can be used without any on-premises IT infrastructure. If you use Intune with Active Directory Domain Services, you can use domain user accounts that you manage with Domain Services with Intune.

- **Intune with System Center Configuration Manager.** Use the Configuration Manager management console to manage computers and mobile devices in your enterprise. This configuration can help you to manage all your organization’s devices through a single console, the Configuration Manager Admin Console. Configuration Manager supports large numbers of mobile devices, servers, and computers. For more about Configuration Manager, see [Hybrid mobile device management (MDM) with System Center Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management). For more help deciding which approach is right for you, see [Choose between Microsoft Intune standalone and hybrid mobile device management with Configuration Manager](/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).--->

## <a name="language-support"></a>언어 지원
Intune은 다음과 같은 언어를 지원하는 Azure Portal에서 실행됩니다. 중국어(간체), 중국어(번체), 체코어, 네덜란드어, 영어, 독일어, 헝가리어, 이탈리아어, 일본어, 포르투갈어(브라질), 포르투갈어(포르투갈), 러시아어, 스페인어, 영어, 프랑스어, 한국어, 폴란드어, 스웨덴어, 터키어.

Intune 관리 콘솔 및 사용자에 연결하는 모바일 환경에서는 Azure Portal에서 지원하는 모든 언어 외에 덴마크어, 그리스어, 핀란드어, 노르웨이어 및 루마니아어를 지원합니다.

<!--- ## Learn more about Intune
Use these resources to learn more about Intune:

- The [Microsoft Intune Trust Center](https://www.microsoft.com/server-cloud/products/intune-trust-center/) provides information about the security, privacy, and compliance practices of Intune, and it describes some of Intune's certifications.

- [Enrolled device management capabilities of Microsoft Intune](introduction-intune.md)--->
