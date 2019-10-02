---
title: Intune 모바일 디바이스 관리 마이그레이션 가이드
titleSuffix: Microsoft Intune
description: 이 가이드에서는 타사 MDM 공급자에서 Microsoft Intune으로 마이그레이션하는 과정과 관련된 다양한 세부 정보를 단계적으로 안내합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dcfc21f9-1bcd-4371-a46d-f2e18154ec50
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3341ac7bfb4e145d050440f78fc65faee1c1325f
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727469"
---
# <a name="intune-migration-guide"></a>Intune 마이그레이션 가이드

![Microsoft Intune MDM 마이그레이션 가이드 아트](./media/migration-guide/MDM-migration-guide-art.PNG)

Microsoft Intune으로의 성공적인 마이그레이션은 현재 MDM(모바일 디바이스 관리) 환경, 비즈니스 목표 및 기술 요구 사항을 고려하는 견고한 계획에서 시작합니다. 또한 마이그레이션 계획을 지원하고 협력해 줄 주요 관련자가 포함되어야 합니다.

이 가이드에서는 타사 MDM 공급자에서 Intune으로 마이그레이션하는 과정과 관련된 다양한 세부 정보를 단계적으로 안내합니다.

## <a name="whats-included-in-this-guide"></a>이 가이드의 내용

이 가이드에서는 마이그레이션을 두 단계로 나누며, 이 두 단계 모두 Intune MDM으로 마이그레이션하는 전체 프로세스를 단계별로 수행하는 데 도움이 되는 작업, 전략 및 기술적 지침을 포함하고 있습니다.

- [1단계: 모바일 디바이스 관리를 위한 Intune 준비](migration-guide-prepare.md)

  - [MDM 마이그레이션 요구 사항 평가](migration-guide-prepare.md#assess-mdm-requirements)

  - [기본 설정](migration-guide-setup.md)

  - [디바이스 및 앱 관리 정책 구성](migration-guide-configure-policies.md)

  - [앱 보호 정책 구성](../apps/app-protection-policies.md)

  - [특별 마이그레이션 고려 사항](migration-guide-considerations.md)

- [2단계: 마이그레이션 캠페인](migration-guide-campaign.md)

  - [통신 계획](migration-guide-communication-plan.md)

  - [조건부 액세스로 최종 사용자 도입 촉진](migration-guide-drive-adoption.md)

  - [일반적인 마이그레이션 주기](migration-guide-cycle.md)
    - [마이그레이션 모니터링](migration-guide-cycle.md#monitoring-migration)
    - [마이그레이션 후](migration-guide-cycle.md#post-migration)

## <a name="assumptions"></a>가정

- PoC(개념 증명) 환경에서 Intune을 이미 평가했으며 이를 조직의 MDM 솔루션으로 사용하기로 했습니다.

- Intune 및 해당 기능을 이미 잘 알고 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

새 Intune 배포는 이전 MDM 배포와 다를 수 있습니다. 기존의 MDM 서비스와 달리 Intune은 ID 기반의 액세스 제어에 중점을 두므로 조직의 네트워크 경계 외부에 있는 모바일 디바이스에서의 회사 데이터 액세스를 제어하는 데 네트워크 프록시 어플라이언스가 필요하지 않습니다. Microsoft는 Enterprise Client + Security 기능으로 통칭되는, 긴밀하게 통합된 클라우드 서비스 제품군을 통해 클라우드 자체 내에서 데이터 보안 서비스 솔루션을 제공합니다.

- [Intune을 사용하는 일반적인 방법](common-scenarios.md)을 읽어봅니다.

## <a name="next-steps"></a>다음 단계

[1단계: 모바일 디바이스 관리를 위한 Intune 준비](migration-guide-prepare.md)
