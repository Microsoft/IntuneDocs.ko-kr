---
title: Microsoft Intune이란? - Azure | Microsoft Docs
description: Microsoft Intune이 어떻게 Enterprise Mobility + Security 솔루션의 MDM(모바일 디바이스 관리) 및 MAM(모바일 앱 관리) 구성 요소가 되며 회사 데이터를 보호하는 데 도움이 되는지 알아봅니다.
keywords: Intune이란
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3c03c67a99b78804c999250f8d1148a4b3d1d97
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504756"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune은 디바이스에 대한 MDM 및 MAM 공급자입니다.

Microsoft Intune은 MDM(모바일 장치 관리) 및 MAM(모바일 응용 프로그램 관리)에 중점을 둔 클라우드 기반 서비스입니다. Intune은 Microsoft의 [Enterprise Mobility + Security(EMS) 제품군](https://www.microsoft.com/microsoft-365/enterprise-mobility-security)에 포함되어 있으므로 사용자는 조직 데이터를 보호하면서 생산성을 높일 수 있습니다. 액세스 권한이 있는 사용자 및 액세스 권한이 있는 사용자를 제어하기 위해 Microsoft 365 및 Azure AD(Azure Active Directory)를 비롯한 다른 서비스와 통합되며, 데이터 보호를 위해 Azure Information Protection과 통합됩니다. Intune과 Microsoft 365를 함께 사용하면 조직의 정보를 보호하면서 직원이 사용하는 모든 디바이스에서 생산성을 높이도록 할 수 있습니다.

![Intune 아키텍처의 이미지](./media/what-is-intune/intunearch_sm.png)

Intune 아키텍처 다이어그램의 [확대 버전](./media/what-is-intune/intunearchitecture.svg)을 보세요.

Intune을 사용하면 다음과 같은 작업을 수행할 수 있습니다.

- Intune을 사용하는 100% 클라우드를 선택하거나 Configuration Manager 및 Intune을 사용하는 [공동 관리](https://docs.microsoft.com/sccm/comanage/overview)를 선택합니다.
- 개인 또는 조직이 소유한 디바이스에서 데이터 및 네트워크에 액세스할 수 있도록 규칙을 설정하고 설정을 구성합니다.
- 디바이스(온-프레미스 및 모바일)에 앱을 배포하고 인증합니다.
- 사용자가 정보에 액세스하고 공유하는 방법을 제어하여 회사 정보를 보호합니다.
- 디바이스와 앱이 보안 요구 사항을 준수하는지 확인합니다.

## <a name="manage-devices"></a>디바이스 관리

Intune에서는 사용자에게 적합한 방법을 사용하여 디바이스를 관리할 수 있습니다. 조직 소유 디바이스의 경우 설정, 기능, 보안 등 디바이스에 대한 완전한 제어를 원할 수 있습니다. 이 방법에서는 디바이스 및 해당 사용자가 Intune에 "등록"됩니다. 등록된 디바이스는 Intune에서 구성된 정책을 통해 규칙 및 설정을 수신합니다. 예를 들어 암호 및 PIN 요구 사항을 설정하고, VPN 연결을 만들고, 위협 방지를 설정하는 등의 작업을 수행할 수 있습니다.

개인 디바이스 또는 BYOD(Bring Your Own Device)의 경우 사용자가 조직 관리자에게 모든 권한을 부여하기를 원치 않을 수 있습니다. 이 방법에서는 사용자에게 옵션을 제공합니다. 예를 들어 사용자가 조직 리소스에 대한 모든 액세스 권한을 원할 경우 디바이스를 [등록](../enrollment/device-enrollment.md)합니다. 또는, 이러한 사용자가 전자 메일 또는 Microsoft Teams에만 액세스하려는 경우 MFA(다단계 인증)를 요구하는 앱 보호 정책을 사용하여 이러한 앱을 사용합니다.

Intune에서 디바이스를 등록하고 관리하는 경우 관리자는 다음과 같은 작업을 수행할 수 있습니다.

- 등록된 디바이스를 확인하고 조직 리소스에 액세스하는 디바이스의 인벤토리를 가져옵니다.
- 보안 및 상태 표준을 충족하도록 디바이스를 구성합니다. 예를 들어 탈옥 디바이스를 차단하려는 경우가 있습니다.
- 사용자가 Wi-Fi 네트워크에 쉽게 액세스하거나 VPN을 사용하여 네트워크에 연결할 수 있도록 디바이스에 인증서를 푸시합니다.
- 사용자 및 디바이스에 대한 규정 준수 보고서를 확인합니다.
- 디바이스를 분실했거나, 도난당했거나, 더 이상 사용하지 않는 경우 조직 데이터를 제거합니다.

**온라인 리소스**:

- [디바이스 등록이란?](../enrollment/device-enrollment.md)

- [디바이스 프로필을 사용하여 디바이스에서 기능 및 설정 적용](../configuration/device-profiles.md)

- [Microsoft Intune으로 디바이스 보호](../protect/device-protect.md)

## <a name="manage-apps"></a>앱 관리

Intune의 MAM(모바일 응용 프로그램 관리)은 사용자 지정 앱 및 스토어 앱을 포함하여 애플리케이션 수준에서 조직 데이터를 보호하도록 설계되었습니다. 앱 관리는 조직 소유 디바이스 및 개인 디바이스에서 사용할 수 있습니다.

앱이 Intune에서 관리되는 경우 관리자는 다음과 같은 작업을 수행할 수 있습니다.

- 특정 그룹의 사용자, 특정 그룹의 디바이스 등을 포함하여 사용자 그룹 및 디바이스에 모바일 앱을 추가하고 할당합니다.
- 특정 설정을 사용하여 시작 또는 실행하도록 앱을 구성하고 디바이스에 이미 있는 기존 앱을 업데이트합니다.
- 사용되는 앱에 대한 보고서를 확인하고 사용 현황을 추적합니다.
- 앱에서 조직 데이터만 제거하여 선택적 초기화를 수행합니다.

Intune이 모바일 앱 보안을 제공하는 한 가지 방법은 **[앱 보호 정책](../apps/app-protection-policy.md)** 을 통해서입니다. 앱 보호 정책:

- Azure AD ID를 사용하여 조직 데이터와 개인 데이터를 격리합니다. 따라서 개인 정보는 조직의 IT 인식에서 격리됩니다. 조직 자격 증명을 사용하여 액세스하는 데이터에는 추가 보안 보호가 제공됩니다.
- 복사 및 붙여넣기, 저장, 보기와 같이 사용자가 수행할 수 있는 작업을 제한하여 개인 디바이스에 대한 액세스를 보호합니다.
- Intune에 등록되었거나, 다른 MDM 서비스에 등록되어 있거나, MDM 서비스에 등록되지 않은 디바이스에서 만들고 배포할 수 있습니다. 등록된 디바이스에서 앱 보호 정책은 보호 계층을 추가할 수 있습니다.

예를 들어 사용자가 조직 자격 증명을 사용하여 디바이스에 로그인합니다. 조직 ID를 사용하면 개인 ID에서 거부된 데이터에 액세스할 수 있습니다. 해당 조직 데이터가 사용되면 앱 보호 정책에서 데이터가 저장 및 공유되는 방법을 제어합니다. 사용자가 개인 ID를 사용하여 로그인하면 동일한 보호는 적용되지 않습니다. 이러한 방식으로 IT는 조직 데이터를 제어하는 반면 최종 사용자는 개인 데이터에 대한 제어 및 개인 정보 취급 방침을 유지 관리합니다.

그리고, Intune을 EMS의 다른 서비스와 함께 사용할 수 있습니다. 이 기능은 운영 체제 및 앱에 포함된 것 이상으로 조직 모바일 앱 보안을 제공합니다. EMS를 사용하여 관리되는 앱은 보다 광범위한 일련의 모바일 앱 및 데이터 보호 기능에 액세스할 수 있습니다.

![앱 관리 데이터 보안 수준을 보여 주는 이미지](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>규정 준수 및 조건부 액세스

Intune은 Azure AD와 통합되어 광범위한 액세스 제어 시나리오를 사용합니다. 예를 들어 전자 메일 또는 SharePoint와 같은 네트워크 리소스에 액세스하려면 모바일 디바이스가 Intune에 정의된 조직 표준을 준수해야 합니다. 마찬가지로 특정 모바일 앱 집합에만 사용할 수 있도록 서비스를 잠글 수 있습니다. 예를 들어 Exchange Online은 Outlook 또는 Outlook Mobile에서만 액세스할 수 있도록 제한할 수 있습니다.

**온라인 리소스**:

- [조직의 리소스 액세스를 허용하도록 디바이스에서 규칙을 설정](../protect/device-compliance-get-started.md)

- [Intune에서 조건부 액세스를 사용하는 일반적인 방법](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Intune을 받는 방법

Intune은 다음과 같이 제공됩니다.

- 독립형 [Azure 서비스](https://go.microsoft.com/fwlink/?linkid=2090973)로
- [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) 및 [Microsoft 365 정부](https://www.microsoft.com/microsoft-365/government)에 포함하여
- 일부 제한된 Intune 기능으로 구성된 [Office 365에서 모바일 장치 관리](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22)로

Intune은 [정부](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description), [교육](https://www.microsoft.com/en-us/education/intune), [키오스크 또는 전용 장치](../configuration/kiosk-settings.md)(제조 및 소매용)를 비롯한 여러 섹터에서 사용됩니다.

## <a name="next-steps"></a>다음 단계

- [Intune에서 해결하는 일반적인 비즈니스 문제](https://docs.microsoft.com/intune/common-scenarios)를 읽습니다.
- [Intune 30일 평가판](free-trial-sign-up.md)을 사용하여 시작합니다.
- [Intune으로 마이그레이션](migration-guide.md)을 계획합니다.
- 무료 평가판 또는 구독을 사용하여 [빠른 시작: iOS용 이메일 디바이스 프로필 만들기](../configuration/quickstart-email-profile.md)의 단계에 따라 iOS 디바이스의 테스트 디바이스 프로필을 만듭니다.
