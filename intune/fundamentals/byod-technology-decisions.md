---
title: EMS를 사용한 BYOD에 대한 기술 결정
description: Microsoft Enterprise Mobility + Security를 사용하여 BYOD를 활성화하고 회사 데이터를 보호하기 위한 주요 기술 결정입니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 12/8/2017
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 297926f6-c029-4003-bda4-9ee031d47dda
ms.reviewer: pfetty
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: c1666c55455a630b839f1f007fc93e5a3da20832
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72509123"
---
# <a name="technology-decisions-for-enabling-byod-with-microsoft-enterprise-mobility--security-ems"></a>Microsoft EMS(Enterprise Mobility + Security)를 사용하여 BYOD를 활성화하기 위한 기술 결정

직원이 자신의 디바이스(BYOD)에서 원격으로 작업할 수 있도록 전략을 개발할 때는 BYOD 및 회사 데이터를 보호하는 방법을 활성화하는 시나리오에서 주요 결정을 해야 합니다. 다행히 EMS는 포괄적인 솔루션 집합에 필요한 모든 기능을 제공합니다.  

이 항목에서는 회사 메일에 대한 BYOD 액세스를 활성화하는 간단한 사용 사례를 살펴봅니다. 전체 디바이스를 관리해야 하는지, 아니면 애플리케이션만 관리해야 하는지에 중점을 둡니다. 둘 다 완전히 유효한 선택입니다.

## <a name="assumptions"></a>가정
* Azure Active Directory 및 Microsoft Intune에 대한 기본 지식이 있음
* 메일 계정이 Exchange Online에서 호스트됨

## <a name="common-reasons-to-manage-the-device-mdm"></a>디바이스(MDM)를 관리하는 일반적인 이유
Exchange Online에 [조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal) 정책을 배포하여 사용자가 디바이스를 디바이스 관리에 등록하도록 쉽게 유도할 수 있습니다. 개인 디바이스를 관리하려는 이유는 다음과 같습니다.

**WiFi/VPN** - 사용자가 생산성을 유지하기 위해 회사 연결 프로필이 필요한 경우 매끄럽게 구성할 수 있습니다.

**애플리케이션** - 사용자 디바이스에 앱 집합이 푸시되어야 하는 경우 매끄럽게 제공할 수 있습니다. 여기에는 Mobile Threat Defense 앱과 같이 보안 용도로 필요할 수 있는 애플리케이션이 포함됩니다.

**준수** - 일부 조직은 특정 MDM 컨트롤을 호출하는 규제 정책이나 기타 정책을 준수해야 합니다. 예를 들어 전체 디바이스를 암호화하거나 디바이스에 있는 모든 앱의 보고서를 생성하려면 MDM이 필요합니다.

## <a name="common-reasons-to-only-manage-the-apps-mam"></a>앱(MAM)만 관리하는 일반적인 이유
MDM이 없는 MAM은 BYOD를 지원하는 조직에서 널리 사용됩니다. Exchange Online에 조건부 액세스 정책을 배포하여 Outlook Mobile(MAM 보호 기능 지원)에서 메일에 액세스하도록 사용자를 유도할 수 있습니다. 개인 디바이스의 앱만 관리하려는 이유는 다음과 같습니다.

**사용자 환경** - MDM 등록에는 여러 경고 프롬프트(플랫폼에 의해 적용됨)가 포함되어 있으며, 이로 인해 사용자가 개인 디바이스에서 메일에 액세스하지 않기로 결정할 수 있습니다. MAM은 MAM 보호 기능이 구현되어 있음을 알리기 위해 한 번만 팝업을 사용자에게 표시하므로 방해가 훨씬 더 적습니다.

**준수** - 일부 조직은 개인 디바이스에서 더 적은 관리 기능이 필요한 정책을 준수해야 합니다. 예를 들어 MAM은 디바이스에서 모든 데이터를 제거할 수 있는 MDM과 달리 앱에서만 회사 데이터를 제거할 수 있습니다.

![모바일 디바이스의 디바이스 및 앱 관리를 비교하는 이미지](./media/byod-technology-decisions/byod-app-device-mgmt.png)

[디바이스 관리 및 앱 관리 수명 주기](device-lifecycle.md)에 대해 자세히 알아보세요.

## <a name="mdm-vs-mam-capability-comparison"></a>MDM 및 MAM 기능 비교
이미 언급한 대로 조건부 액세스는 디바이스를 등록하거나 Outlook Mobile 같은 관리형 앱을 사용하도록 사용자를 유도할 수 있습니다. 두 경우 모두, 다음을 비롯한 다른 많은 조건을 적용할 수 있습니다.

* 액세스를 시도 중인 사용자
* 위치를 신뢰할 수 있는지 여부
* 로그인 위험 수준
* 디바이스 플랫폼

여전히 조직에서 특정 위험에 대해 우려하는 경우가 많습니다.  아래 표에는 일반적인 우려 사항과 해당 문제에 대한 MDM 및 MAM 대응이 나와 있습니다.

| 문제   |   MDM  |   MAM  |
|------------|--------|--------|
|권한 없는 데이터 액세스 | 그룹 구성원 필요 | 그룹 구성원 필요 |
|권한 없는 데이터 액세스 | 디바이스 등록 필요 | 보호된 앱 필요 |
|권한 없는 데이터 액세스 | 특정 위치 필요 | 특정 위치 필요 |
| | | |
|손상된 사용자 계정| MFA 필요 | MFA 필요|
|손상된 사용자 계정 | 높은 위험 사용자 차단 | 높은 위험 사용자 차단 |
|손상된 사용자 계정 | 디바이스 PIN | 앱 PIN |
| | | |
| 손상된 디바이스 또는 앱 | 규격 디바이스 필요 | 앱 실행 시 탈옥 확인 |
| 손상된 디바이스 또는 앱 | 디바이스 데이터 암호화 | 앱 데이터 암호화 |
| | | |
|분실 또는 도난당한 디바이스 | 모든 디바이스 데이터 제거 | 모든 앱 데이터 제거|
| | | |
| 우발적인 데이터 공유 또는 비보안 위치에 저장 | 디바이스 데이터 백업 제한 | 잘라내기/복사/붙여넣기 제한|
| 우발적인 데이터 공유 또는 비보안 위치에 저장 | 다른 이름으로 저장 제한 | 다른 이름으로 저장 제한 |
|우발적인 데이터 공유 또는 비보안 위치에 저장 | 인쇄 사용 안 함 | 해당 없음|

## <a name="next-steps"></a>다음 단계
이제 디바이스 관리, 앱 관리 또는 이 둘의 조합에 집중하여 조직에서 BYOD를 활성화할지 여부를 결정해야 합니다. 구현 선택은 사용자 책임이며, Azure AD에서 사용 가능한 ID 및 보안 기능은 관계없이 사용할 수 있습니다.  

Intune [계획 가이드](planning-guide.md)에 따라 다음 수준의 계획을 매핑합니다.
