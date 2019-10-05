---
title: 데이터 웨어하우스 데이터 모델
titleSuffix: Microsoft Intune
description: Microsoft Intune 데이터 웨어하우스 샘플 데이터는 항상 변화하는 모바일 환경에 대한 과거 보기를 제공합니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4D04D3D9-4B6C-41CD-AAF8-466AF8FA6032
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8799734617ed26c25b931284c8c63f0da2e6b951
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71733233"
---
# <a name="microsoft-intune-data-warehouse-data-model"></a>Microsoft Intune 데이터 웨어하우스 데이터 모델

Intune 데이터 웨어하우스 샘플 데이터는 항상 변화하는 모바일 디바이스 환경에 대한 과거 보기를 제공합니다. 보기는 해당 시점의 관련 엔터티로 구성됩니다.

## <a name="entities-entity-sets"></a>엔터티: 엔터티 집합

웨어하우스는 다음과 같은 개략적인 영역으로 데이터를 노출합니다.

- 앱 보호가 설정된 앱 및 사용량
- 등록된 디바이스, 속성 및 인벤토리
- 앱 및 소프트웨어 인벤토리
- 디바이스 구성 및 규정 준수 정책

이러한 영역에는 Intune 환경에 적합한 엔터티가 포함됩니다. 다음 항목의 엔터티 집합에 대한 정보를 찾을 수 있습니다.

- [애플리케이션](../reports-ref-application.md)
- [날짜](reports-ref-date.md)
- [디바이스](reports-ref-devices.md)
- [Intune 관리 확장](reports-ref-intunemanagementextension.md)
- [정책](reports-ref-policy.md)
- [모바일 앱 관리(MAM)](../apps/app-management.md)
- [사용자](reports-ref-user.md)
- [현재 사용자](../reports-ref-current-user.md)
- [사용자 디바이스 연결](reports-ref-user-device.md)

## <a name="relationships-star-schema-model"></a>관계: 별모양 스키마 모델

웨어하우스는 하려는 질문의 유형에 적합한 관계의 엔터티를 구성합니다. 예를 들어, 사내에서 개발된 Android 애플리케이션의 설치 수를 검토할 수 있습니다. 데이터 웨어하우스 구조를 통해 모바일 환경에 대한 정보를 얻을 수 있습니다. 결과적으로 Microsoft Power BI와 같은 분석 도구는 데이터 웨어하우스 데이터 모델을 사용하여 시각화 및 동적 대시보드를 만들 수 있습니다.

엔터티 및 관계는 별모양 스키마 모델을 사용합니다. 별모양 스키마는 시간 차원에서 팩트를 상호 연결합니다. 모델 컨텍스트에서 *팩트*는 디바이스 수, 앱, 개수 또는 등록 시간 같은 정량 측정값을 나타냅니다. 팩트 테이블에는 많은 데이터가 저장됩니다. 데이터가 매우 커질 수 있으므로 일반적으로 정보를 30일로 제한합니다. *차원*은 팩트에 대한 컨텍스트를 제공합니다. 팩트가 무엇이 발생했는지 측정할 경우 차원은 해당 항목이 발생한 대상을 나타냅니다. **User** 테이블과 같은 차원 테이블은 더 작으며, 팩트 테이블의 기간보다 더 길게 데이터를 보존할 수 있습니다. 

별모양 스키마 모델은 유연성과 데이터 분석을 위해 최적화되므로 진화하는 모바일 환경을 이해하는 데 필요한 보고서를 생성할 수 있습니다.

## <a name="time-daily-snapshots"></a>시간: 일일 스냅샷

웨어하우스는 Intune 데이터의 다운스트림입니다. Intune은 자정(UTC)에 일일 스냅샷을 생성하고 웨어하우스에 저장합니다. 저장된 스냅샷의 지속 기간은 팩트 테이블에 따라 다릅니다. 7일, 30일 또는 훨씬 더 오래 저장될 수 있습니다.

## <a name="next-steps"></a>다음 단계

- 데이터 웨어하우스가 Intune에서 사용자의 수명을 추적하는 방법에 대한 자세한 내용은 [Intune 데이터 웨어하우스의 사용자 수명 표시](reports-ref-user-timeline.md)를 참조하세요.
- 데이터 웨어하우스 작업에 대한 자세한 내용은 [첫 번째 데이터 웨어하우스 만들기](https://www.codeproject.com/Articles/652108/Create-First-Data-WareHouse)를 참조하세요.
- Power BI 및 데이터 웨어하우스 작업에 대한 자세한 내용은 [데이터 세트를 가져와서 새 Power BI 보고서 만들기](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/)를 참조하세요. 
