---
title: Intune에서 데이터 스토리지 및 처리
description: Intune에서 개인 데이터를 저장하고 처리하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: edb07842-6a16-482e-8c1d-541a29e169a8
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b2947969c1c07d595a0a5baa48be11ba7a941424
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71726884"
---
# <a name="data-storage-and-processing-in-intune"></a>Intune에서 데이터 스토리지 및 처리

Intune에서 [데이터를 수집](privacy-data-collect.md)한 후에는 아래와 같이 해당 데이터의 스토리지 및 처리가 진행됩니다.

## <a name="storing-personal-data"></a>개인 데이터 저장

수집되는 모든 비 원격 분석 데이터는 Intune 서비스를 통해 처리되며 다음 스토리지 위치 중 하나 이상에 저장됩니다. 

- SQLAzure 
- 신뢰할 수 있는 컬렉션(서비스 패브릭)  
- Azure 스토리지 

안정적인 서비스를 모니터링하고 제공하는 데 중요한 원격 측정(서비스 로그, 성능 로그, 오류 등)은 Microsoft의 원격 분석 데이터 저장소로 전송됩니다.

### <a name="storage-locations"></a>스토리지 위치

Microsoft는 전 세계 여러 지역에서 Intune 서비스를 제공하고 운영합니다. Intune은 관리자가 선택한 고객 데이터 스토리지 위치를 우선합니다.

자세한 내용은 [데이터 위치](https://www.microsoft.com/trust-center/privacy/data-location)를 참조하세요.

### <a name="personal-data-retention"></a>개인 데이터 보존

일반적으로 개인 데이터는 Intune 관리 대상에서 제외된 후 30일까지 Intune에 보존됩니다.

Intune 사용 데이터의 일부로 수집되는 원격 측정 데이터는 최대 30일 동안 보존됩니다.

감사 로그는 최대 1년 동안 보존됩니다.

## <a name="processing-personal-data"></a>개인 데이터 처리

Intune은 ISO 인증 시스템을 통해 개인 데이터를 처리합니다. 자세한 내용은 [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp)을 참조하세요.

### <a name="profiling-and-marketing"></a>프로파일링 및 마케팅

Microsoft Intune은 프로파일링 또는 마케팅 목적으로 서비스를 제공하는 과정에서 수집되는 개인 데이터를 사용하지 않습니다. 

### <a name="restrict-processing-of-personal-data"></a>개인 데이터 처리 제한

사용자의 개인 데이터 처리를 제한하기 위해 다음 방법으로 사용자 계정을 삭제할 수 있습니다.
1. 다음을 포함한 사용자 개인 데이터의 전자 사본 내보내기
    - 계정
    - 서비스 데이터
    - 연결된 로그
2. Intune에서 사용자의 계정 및 관련 데이터를 삭제합니다.

## <a name="next-steps"></a>다음 단계

Intune의 개인 데이터 [저장 및 공유](privacy-data-secure-share.md) 방법에 대해 자세히 알아봅니다. 
