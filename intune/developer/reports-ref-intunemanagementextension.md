---
title: IntuneManagementExtension 엔터티
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 IntuneManagementExtension 엔터티 범주에 대한 참조 항목입니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: ae99e747f9c0540418c15f24fbe0c27c585f869c
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72490310"
---
# <a name="reference-for-intune-management-extensions"></a>Intune 관리 확장에 대한 참조

**intuneManagementExtensions** 범주는 다음과 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

- IntuneManagementExtension의 버전
- IntuneManagementExtension의 설치 상태

## <a name="intunemanagementextensionversions"></a>intuneManagementExtensionVersions

**intuneManagementExtensionVersion** 엔터티는 intuneManagementExtensions에서 사용하는 모든 버전을 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| extensionVersionKey |intuneManagementExtensions 버전의 고유 식별자입니다. | 1 |
| extensionVersion |4 자리 버전 번호입니다. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstates"></a>intuneManagementExtensionHealthStates

**intuneManagementExtensionHealthState**는 intuneManagementExtensions의 가능한 상태를 모두 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| extensionStateKey |상태의 고유 식별자입니다. | 2 |
| extensionState |IntuneManagementExtension의 상태입니다. | 정상 |

## <a name="intunemanagementextensions"></a>intuneManagementExtensions

**intuneManagementExtension**은 각 Windows 10 디바이스의 IntuneManagementExtensions 상태를 일별로 나열합니다.
데이터는 최근 60일 동안 보존됩니다. 


|      속성       |                         설명                         | 예제 |
|---------------------|-------------------------------------------------------------|---------|
|       dateKey       |               날짜의 고유 식별자입니다.                |   123   |
|      tenantKey      |              테넌트의 고유 식별자입니다.               |   456   |
|      deviceKey      |              디바이스의 고유 식별자입니다.               |   789   |
| extensionVersionKey | intuneManagementExtension 버전의 고유 식별자입니다. |    1    |
|  extensionStateKey  |             상태의 고유 식별자입니다.              |    2    |

