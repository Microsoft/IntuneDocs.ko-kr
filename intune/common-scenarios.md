---
title: Microsoft Intune을 사용하는 일반적인 방법
description: Microsoft Intune에서 쉽게 관리할 수 있는 가장 일반적인 여섯 가지 작업에 대해 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 05/30/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f37d4ff-b5a7-4a89-8884-a6184908b09c
ms.reviewer: dougeby
ms.suite: ems
ms.custom: intune-classic; get-started
ms.openlocfilehash: fd7b5328c163c978d91cb67af7d3142624996ab8
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253581"
---
# <a name="common-ways-to-use-microsoft-intune"></a>Microsoft Intune을 사용하는 일반적인 방법

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

이 구현 작업을 시작하기 전에 회사의 엔터프라이즈 이동성 이해 관계자와 비즈니스 목표를 서로 조율하는 것이 중요합니다.  Enterprise Mobility를 처음으로 사용하든, 다른 제품에서 마이그레이션하든 관계없이 이 사전 조율을 수행해야 합니다.  

엔터프라이즈 이동성과 관련된 요구 사항은 동적으로 진화하며, 이러한 요구를 처리하는 Microsoft의 접근 방식은 시장의 다른 솔루션들과 다른 경우가 있습니다. 비즈니스 목표를 조율하는 가장 좋은 방법은 직원, 파트너 및 IT 부서에 사용하려는 시나리오의 측면에서 목표를 표현하는 것입니다.  

아래에서는 Intune에 따른 가장 일반적인 여섯 가지 시나리오 및 각 항목을 계획하고 배포하는 방법에 대한 자세한 정보의 링크를 간단히 소개합니다.

>[!NOTE]
>Microsoft IT에서 Intune을 사용하여 회사 데이터 보안을 유지하면서 Microsoft 직원이 모바일 장치에서 회사 리소스에 액세스할 수 있는 방법이 궁금한가요? [이 기술 사례 연구를 참고하여](https://www.microsoft.com/itshowcase/Article/Content/588) Microsoft IT에서 Intune 및 다른 서비스를 사용하여 ID, 장치, 앱 및 데이터를 관리하는 방법을 자세히 확인할 수 있습니다.  

>[!IMPORTANT]
>최근 iOS 장치에 있었던 "Trident" 맬웨어 공격을 감안하여 모바일 장치가 최신 상태인지 확인하려고 합니다. 그래서 [Microsoft Intune을 사용하여 모바일 장치가 최신 상태로 유지](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/)라는 블로그 글을 게시했습니다. 이 게시물은 Intune이 사용자 장치를 안전하고 최신 상태로 유지하도록 도와주는 다양한 방법에 대한 정보를 제공합니다.

## <a name="protecting-your-on-premises-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>온-프레미스 메일 및 데이터를 보호하여 모바일 장치에서 안전하게 액세스할 수 있도록 합니다.
대부분의 엔터프라이즈 이동성 전략은 인터넷에 연결된 모바일 장치를 사용하는 직원이 메일에 대한 보안 액세스를 사용하는 계획으로 시작됩니다. 대부분의 조직에는 해당 회사 네트워크에 호스팅되는 온-프레미스 데이터 및 Microsoft Exchange와 같은 응용 프로그램 서버가 있습니다.


Intune 및 Microsoft EMS(Enterprise Mobility + Security)는 장치가 Intune을 통해 등록될 때까지 어떤 모바일 앱도 전자 메일에 액세스할 수 없도록 하는 고유한 통합형 Exchange Server용 [조건부 액세스 솔루션](conditional-access.md)([클래식 포털](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune))을 제공합니다. 회사 네트워크의 경계에 또 다른 게이트웨이 컴퓨터를 배포하지 않고도 이 모든 작업을 수행할 수 있습니다.

또한 Intune에서는 기간 업무 앱 서버와 같은 온-프레미스 데이터에 대한 보안 액세스가 필요한 모바일 앱에 대한 액세스를 지원합니다. 일반적으로는 경계의 표준 VPN 게이트웨이 또는 프록시(예: Microsoft Azure Active Directory 응용 프로그램 프록시)와 함께 [Intune 관리 인증서](certificates-configure.md)([클래식 포털](/intune-classic/deploy-use/secure-resource-access-with-certificate-profiles))를 사용하여 액세스를 제어하는 방식으로 이 작업을 수행합니다. 

이러한 경우에 회사 데이터에 액세스하는 유일한 방법은 관리에 장치를 등록하는 것입니다. 일단 장치를 등록하면 관리 시스템이 장치를 정책과 호환되도록 해야 회사 데이터에 액세스할 수 있습니다. 또한 Intune의 [앱 줄 바꿈 도구 및 앱 SDK](apps-prepare-mobile-application-management.md)를 사용하면 액세스한 데이터를 기간 업무 앱 내에서 유지할 수 있으므로, 소비자 앱 또는 서비스에 회사 데이터를 전달할 수 없습니다.

<!-- Learn more about how to plan and deploy Intune to help secure on-premises email and data. -->


## <a name="protecting-your-office-365-email-and-data-so-it-can-be-safely-accessed-by-mobile-devices"></a>Office 365 메일 및 데이터를 보호하여 모바일 장치에서 안전하게 액세스할 수 있도록 합니다.
Office 365(전자 메일, 문서, 인스턴트 메시지, 연락처)에서 회사 데이터를 보호하는 작업은 사용자에도 쉽고 원활합니다.


Intune 및 Microsoft Enterprise Mobility + Security는 사용자, 앱 또는 장치가 회사의 규정 준수 요구 사항([다단계 인증 수행](/intune-classic/deploy-use/multi-factor-authentication-azure-active-directory), Intune을 사용하여 등록, 관리되는 앱 사용, 지원되는 OS 버전, 장치 PIN, 사용자 위험 프로필 저하 등)을 충족하지 않는 경우 Office 365 데이터를 액세스할 수 없도록 하는 고유하고 통합된 조건부 액세스 솔루션을 제공합니다.


해당 앱 스토어의 Office 모바일 앱은 Intune을 통해 구성할 수 있는 데이터 제약 정책으로 수행할 준비가 되어 있습니다. 이를 통해 IT 부서에서 관리하지 않는 앱(예: 기본 메일 앱) 및 저장소 위치(예: Dropbox)에서 데이터를 공유하지 못하도록 할 수 있습니다. 이 기능은 모두 Office 365 및 EMS에 빌드됩니다. 이 값을 가져오기 위해 추가 인프라를 배포할 필요가 없습니다.

일반적인 Office 365 배포 방법은 장치가 회사 앱/인증서/Wi-Fi/VPN 구성을 사용하여 완전히 설정되어야 하는 경우 관리에 해당 장치를 등록하는 것으로, 회사 소유 장치에 대한 일반적인 시나리오입니다.  


그러나 사용자가 회사 메일 및 문서에만 액세스하면 된다면(대개 개인 소유 장치를 사용하는 경우) [앱 보호 정책](app-protection-policies.md)([클래식 포털](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune))을 적용한 Office 모바일 앱을 사용하도록 하고 장치 등록 과정은 모두 건너뛸 수 있습니다.  



어느 방법을 사용하더라도 Office 365 데이터는 정의한 정책에 의해 보호됩니다.

<!-- Learn more about how to plan and deploy Intune to help secure Office 365 email and data. -->


## <a name="offer-a-bring-your-own-device-program-to-all-employees"></a>BYOD(Bring your own device) 프로그램을 모든 직원에게 제공합니다.
BYOD는 하드웨어 비용 절감 또는 직원에 대한 모바일 생산성 선택 항목을 증가하는 수단으로 조직 사이에 널리 사용되고 있습니다. 요즘 모든 사람들이 개인 전화를 갖고 있으므로 하나 더 갖고 다니더라도 좋을 것입니다. 가장 큰 문제는 직원이 관리에 자신의 개인 장치를 등록하도록 유도하는 것입니다. IT 부서가 자신의 장치를 사용하여 무엇을 보고 수행하는지 우려하기 때문입니다.  

장치 등록 옵션을 사용할 수 없는 경우 Intune에서는 [회사 데이터를 포함하는 앱만 관리](app-protection-policies.md)([클래식 포털](/intune-classic/deploy-use/protect-apps-and-data-with-microsoft-intune))하는 대체 BYOD 접근 방식을 제공합니다. Intune은 의심스러운 앱이 회사 및 개인 데이터에 액세스하더라도 Office 모바일 앱의 경우와 마찬가지로 회사 데이터를 보호합니다.  

관리자는 사용자가 Office 모바일 앱에서 Office 365에 액세스하도록 요구하고 보호되는(암호화, PIN으로 보호 등의 방법으로) 데이터를 보관하는 정책을 사용하여 앱을 구성할 수 있습니다. 이러한 앱 보호 정책은 관리되지 않는 앱 및 저장소 위치 즉, 해당 앱의 내부 또는 외부에서의 데이터 손실을 방지합니다. 예를 들어 정책은 Outlook Mobile 내에서 두 프로필을 구성하더라도 사용자가 회사 메일 프로필에서 고객 메일 프로필에 텍스트를 복사하지 않도록 방지합니다. 다른 서비스 및 BYOD 사용자에게 필요한 응용 프로그램에 비슷한 구성을 배포할 수 있습니다.

<!-- Learn more about how to plan and deploy Intune to support BYOD.-->

## <a name="issue-corporate-owned-phones-to-your-employees"></a>직원에게 회사 소유의 휴대폰 발급
오늘날에는 대부분의 직원들이 모바일 방식으로 업무를 수행하므로, 모바일 장치에서 생산성을 높여야 경쟁력도 높일 수 있습니다. 이러한 직원은 어디에서 언제든지 모든 회사 앱 및 데이터에 원활하게 액세스할 수 있어야 합니다. 회사 데이터가 안전하고 관리 비용은 적어야 합니다.  

Intune은 Apple 장치 등록 프로그램 및 Samsung Knox 모바일 보안 플랫폼을 포함하여 현재 시판 중인 주요 회사 장치 관리 플랫폼과 통합되는 [대량 프로비전 및 관리 솔루션](device-enrollment.md)([클래식 포털](/intune-classic/deploy-use/manage-corporate-owned-devices))을 제공합니다. Intune을 사용하여 장치 구성을 중앙 집중적으로 제작하면 고도로 자동화할 수 있는 회사 장치를 프로비전할 수 있습니다.  

열려 있지 않은 iPhone 상자를 직원에게 전달한다고 상상해 보세요. 직원은 iPhone을 켜고 자신을 인증해야 하는 회사 브랜드 설치 흐름을 진행합니다. [보안 정책](device-profiles.md)([클래식 포털](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies))을 통해 IPhone을 원활하게 구성할 수 있습니다.

그러면 직원은 Intune 회사 포털 앱을 시작하여 사용할 수 있는 선택적 회사 앱에 액세스합니다.

<!-- Learn more about how to plan and deploy Intune to support corporate owned devices. -->

## <a name="issue-limited-use-shared-tablets-to-your-employees"></a>직원에게 사용이 제한된 공유 태블릿 발급
직원들은 모바일 기술을 점점 더 많이 사용하고 있습니다. 예를 들어 이제 공유 태블릿은 소매 대리점 직원에게 일상적으로 사용됩니다.  판매를 처리하거나 즉시 인벤토리를 확인하는 경우 태블릿은 고객 상호 작용에 큰 도움이 됩니다.

이 경우에 사용자 경험의 단순함이 중요합니다. 따라서 태블릿은 일반적으로 직원이 상호 작용할 수 있는 유일한 것이 단일 기간 업무 앱인 경우와 같이 사용이 제한된 모드에서 직원에게 제공됩니다. Intune을 사용하면 이 사용이 제한된 모드에서 실행되도록 구성할 수 있는 이러한 공유 [iOS 및 Android](device-profiles.md)([클래식 포털](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)) 장치를 대량으로 프로비저닝하고 보호하고 중앙에서 관리할 수 있습니다.

<!-- Learn more about how to plan and deploy Intune to support shared tablets. -->

## <a name="enable-your-employees-to-securely-access-office-365-from-an-unmanaged-public-kiosk"></a>직원이 관리되지 않는 공용 키오스크에서 Office 365에 안전하게 액세스하도록 할 수 있습니다.
직원이 무역 박람회 및 호텔 로비에 있는 공용 컴퓨터 등 관리할 수 없는 장치, 앱 또는 브라우저를 사용해야 하는 경우도 있습니다.

이 경우에 직원이 회사 전자 메일에 액세스할 수 있어야 하나요? Intune 및 Microsoft Enterprise Mobility + Security를 사용하면 [조직에서 관리하는 장치에 대한 전자 메일 액세스를 제한](conditional-access.md)([클래식 포털](/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune))할 수 있으므로, 직원에게 이러한 방식의 회사 전자 메일 액세스를 허용할 필요가 없습니다. 이렇게 하면 강력하게 인증된 직원이 실수로 신뢰할 수 없는 컴퓨터에 회사 데이터를 남기지 않게 됩니다.
