---
title: Microsoft 365에서 디바이스 관리
description: Microsoft 365 Enterprise는 Microsoft Intune을 포함하고 있습니다. Intune이 조직에 모바일 디바이스 관리 및 모바일 애플리케이션 관리를 제공하는 방법을 참조하세요. 일반적인 시나리오를 읽고 Intune을 사용하여 사용자 환경에 Microsoft 365를 배포합니다.
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/14/2019
ms.topic: conceptual
audience: ITPro
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.technology: ''
ms.custom: intune
ms.assetid: 0649d310-43a7-4b01-85d2-da255d03e1da
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfa7e34d19465eb43b5eb9cd68b7513545938fa8
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504782"
---
# <a name="device-management-overview"></a>디바이스 관리 개요

모든 관리자의 주요 작업은 조직의 리소스와 데이터를 안전하게 보호하는 것입니다. 이 작업이 *디바이스 관리*입니다. 사용자는 개인 파일을 열고 공유하고, 웹 사이트를 방문하고, 앱과 게임을 설치하는 많은 디바이스를 보유하고 있습니다. 이러한 사용자는 직원이자 학생이기도 합니다. 이메일, OneNote 등의 회사 및 학교 리소스에 액세스하는 데 자신의 디바이스를 사용하고자 합니다.

디바이스 관리는 조직에서 다양한 디바이스로부터 리소스 및 데이터를 보호할 수 있게 해줍니다.

조직은 디바이스 관리 공급자를 사용하여 승인된 사람과 디바이스만이 조직 소유의 정보에 액세스할 수 있도록 관리할 수 있습니다. 마찬가지로, 디바이스 사용자는 자신의 디바이스가 조직의 보안 요구 사항을 충족한다는 사실을 알고 있기 때문에 안심하고 휴대폰으로 회사 데이터에 액세스할 수 있습니다. 조직의 입장에서 **리소스를 보호하려면 어떻게 해야 하나요?** 라는 질문을 할 수 있습니다.

답은 [Microsoft Intune](what-is-intune.md)입니다. Intune은 MDM(모바일 디바이스 관리) 및 MAM(모바일 애플리케이션 관리)을 제공합니다. MAM 또는 MDM 솔루션의 핵심 작업은 다음과 같습니다.

- 다양한 모바일 환경을 지원하고 iOS, Android, Windows 및 macOS 디바이스를 안전하게 관리합니다.
- 디바이스와 앱이 조직의 보안 요구 사항을 준수하는지 확인합니다.
- 조직 소유 디바이스와 개인 디바이스에서 조직 데이터를 안전하게 보호하는 정책을 만듭니다.
- 통합된 단일 모바일 솔루션을 사용하여 이러한 정책을 적용하고 디바이스, 앱, 사용자 및 그룹 관리를 도와줍니다.
- 직원이 회사 정보에 액세스하여 데이터를 공유하는 방법을 제어할 수 있게 하여 회사 정보를 보호합니다.

Intune은 Microsoft Azure, Microsoft 365에 포함되어 있으며 Azure Active Directory(Azure AD)와 통합됩니다. Azure AD는 누가 무엇에 액세스할 수 있는지를 제어합니다.

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft를 비롯한 여러 조직에서는 사용자가 회사 소유 디바이스 및 개인용 모바일 디바이스로 액세스하는 회사 데이터를 안전하게 보호하기 위해 Intune을 사용합니다. Intune에는 데이터 액세스를 보호하고 모니터링하는 데 도움이 되는 디바이스 및 앱 구성 정책, 소프트웨어 업데이트 정책 및 설치 상태(차트, 테이블 및 보고서)가 포함되어 있습니다.

사람들이 서로 다른 플랫폼을 사용하는 여러 디바이스를 보유하고 있는 것을 흔히 볼 수 있습니다. 예를 들어 한 직원이 회사 업무에는 Surface Pro를 사용하고 개인 생활에서는 Android 모바일 디바이스를 사용할 수 있습니다. 사람들이 이처럼 여러 디바이스에서 Microsoft Outlook이나 SharePoint 같은 조직 리소스에 액세스하는 것도 매우 흔한 일입니다.

Intune을 사용하면 사용자별로 여러 디바이스를 관리하고 iOS, macOS, Android 및 Windows를 포함하여 각 디바이스에서 실행되는 여러 플랫폼을 관리할 수 있습니다. Intune은 디바이스 플랫폼별로 정책 및 설정을 구분합니다. 따라서 특정 플랫폼의 디바이스를 쉽게 관리하고 볼 수 있습니다.

**[일반적인 시나리오](common-scenarios.md)** 는 모바일 디바이스를 사용할 때 자주 발생하는 문제를 Intune이 어떻게 해결하는지 볼 수 있는 유용한 리소스입니다. 다음과 같은 시나리오를 찾을 수 있습니다.  

- 온-프레미스 Exchange를 사용하여 이메일 보호
- Office 365에 안전하게 액세스
- 개인용 디바이스를 사용하여 조직 리소스에 액세스

Intune에 대 한 자세한 내용은 [Intune 이란?](what-is-intune.md)을 참조 하세요.

## <a name="integration-with-secure-and-protect-services"></a>안전하게 보호되는 서비스와 통합

모든 디바이스 관리 솔루션의 핵심 작업은 보안 및 보호를 제공하는 것입니다. Intune은 다른 서비스와 통합하여 이 핵심 작업을 처리합니다. 예를 들면 다음과 같습니다.

- **Microsoft 365**는 일반적인 IT 작업을 간소화하는 핵심 구성 요소입니다. Microsoft 365 관리 센터에서 사용자를 만들고 그룹을 관리합니다. Intune, Azure AD 등과 같은 다른 서비스에도 액세스할 수 있습니다.

  예를 들어 Microsoft 365에서 iOS 디바이스 그룹을 만듭니다. 그런 다음, Intune을 사용하여 앱 스토어 액세스, iCloud에 백업, Apple 웹 필터 사용 등과 같은 iOS 기능에 집중하는 정책을 iOS 디바이스 그룹에 푸시합니다.

- **Windows Defender**는 Windows 10 디바이스를 보호하는 여러 보안 기능을 갖추고 있습니다. 예를 들어 Intune 및 Windows Defender를 함께 사용하여 다음을 수행할 수 있습니다.

  - [Windows Defender SmartScreen](../protect/endpoint-protection-windows-10.md)으로 모바일 디바이스의 파일 및 앱에서 의심스러운 활동을 검색합니다.
  - [Microsoft Defender ATP(Advanced Threat Protection)](../protect/advanced-threat-protection.md)를 사용하여 모바일 디바이스의 보안 위반을 방지합니다. 또한 사용자를 회사 리소스에서 차단하여 보안 위반의 영향을 제한하는 데 도움이 됩니다.

- **조건부 액세스**는 Azure Active Directory의 기능이며 Intune과 원활하게 통합됩니다. [조건부 액세스](../protect/conditional-access.md)를 사용하여 규정을 준수하는 디바이스만 이메일, SharePoint 및 기타 앱에 액세스할 수 있는지 확인합니다.

## <a name="choose-the-device-management-solution-thats-right-for-you"></a>상황에 맞는 디바이스 관리 솔루션 선택

디바이스를 관리하는 몇 가지 방법이 있습니다. 첫 번째 Intune에 기본 제공되는 기능을 사용하여 디바이스의 다양한 측면을 관리할 수 있습니다. 이 접근 방식을 **MDM(모바일 디바이스 관리)** 이라고 합니다. 사용자는 자신의 디바이스를 "등록"하고 인증서를 사용하여 Intune과 통신합니다. IT 관리자는 디바이스에 앱을 푸시하고, 디바이스를 특정 운영 체제로 제한하고, 개인용 디바이스를 차단하는 등의 조치를 취할 수 있습니다. 또한 디바이스를 분실하거나 도난당할 경우 디바이스의 모든 데이터를 제거할 수 있습니다.

두 번째 방법으로, 디바이스에서 앱을 관리합니다. 이 접근 방법을 **MAM(모바일 애플리케이션 관리)** 이라고 합니다. 사용자는 자신의 개인용 디바이스로 조직 리소스에 액세스할 수 있습니다. 사용자가 이메일, SharePoint 등의 앱을 열 때 추가로 인증을 해야 합니다. 디바이스를 분실하거나 도난당할 경우 디바이스의 모든 데이터를 제거할 수 있습니다.

[MDM 및 MAM](byod-technology-decisions.md)을 조합해서 사용할 수도 있습니다.

Intune을 설정할 때 오직 Azure Portal에서만 디바이스를 관리하도록 선택할 수도 있고, Intune과 Microsoft 365를 함께 사용하여 디바이스를 관리하도록 선택할 수도 있습니다. [Azure Portal에서 모바일 디바이스 관리를 Intune으로 마이그레이션](https://www.microsoft.com/itshowcase/Article/Content/1042/Migrating-mobile-device-management-to-Intune-in-the-Azure-portal)하는 것은 Microsoft IT 사례 연구입니다. 이 사례 연구에서는 Microsoft IT가 최신 디바이스 관리 방식을 선택하고 학습된 교훈을 읽는 방법을 확인합니다.

## <a name="simplify-it-tasks-using-the-device-management-admin-center"></a>디바이스 관리의 관리 센터를 사용하여 IT 작업 간소화

[디바이스 관리의 관리 센터](https://devicemanagement.microsoft.com/)는 모바일 디바이스에 대한 작업을 관리하고 완료할 수 있는 원스톱 샵입니다. 이 작업 영역에는 Intune 및 Azure Active Directory를 비롯한 디바이스와 클라이언트 앱 관리에 사용되는 서비스가 포함되어 있습니다.

장치 관리 관리 센터에서 다음을 수행할 수 있습니다.

- [디바이스 등록](../enrollment/device-enrollment.md)
- [디바이스 준수 설정](../protect/device-compliance-get-started.md)
- [디바이스 관리](../remote-actions/device-management.md)
- [앱 관리](../apps/app-management.md)  
- [iOS 전자책](../apps/vpp-ebooks-ios.md)  
- [Exchange On-premises Connector 설치](../protect/exchange-connector-install.md)  
- [역할 관리](role-based-access-control.md)  
- 소프트웨어 업데이트 관리
  - [Windows 10 업데이트 관리](../protect/windows-update-for-business-configure.md)  
  - [iOS 업데이트 관리](../protect/software-updates-ios.md)  
- [Azure Active Directory](https://docs.microsoft.com/azure/active-directory)  
- [사용자 관리](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory)
- [그룹 및 멤버 관리](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-manage-groups)
- [문제 해결](help-desk-operators.md)

## <a name="next-steps"></a>다음 단계

MDM 또는 MAM 솔루션을 시작할 준비가 완료되면 Intune을 설정하고, 디바이스를 등록하고, 정책 만들기를 시작하는 여러 단계를 수행합니다. [Microsoft 365용 모바일 디바이스 관리](https://docs.microsoft.com/microsoft-365/enterprise/mobility-infrastructure)도 유용한 리소스입니다.
