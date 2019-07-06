---
title: IntuneManagementExtension 엔터티
titleSuffix: Microsoft Intune
description: Intune 데이터 웨어하우스 API에서 엔터티 컬렉션의 IntuneManagementExtension 엔터티 범주에 대한 참조 항목입니다.
keywords: Intune 데이터 웨어하우스
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 73DF3B90-6D52-4EF6-AFFD-1873A18C7421
ms.reviewer: dariusz
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 571080f3d25753fdc423c45100b06377ecd426b5
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549192"
---
# <a name="reference-for-intune-management-extension"></a>Intune 관리 확장에 대한 참조

**IntuneManagementExtension** 범주는 다음과 같은 정보를 추적하는 모바일 디바이스에 대한 엔터티를 포함합니다.

  - IntuneManagementExtension의 버전
  - IntuneManagementExtension의 설치 상태

## <a name="intunemanagementextensionversion"></a>IntuneManagementExtensionVersion

**IntuneManagementExtensionVersion** 엔터티는 IntuneManagementExtension에 사용되는 모든 버전을 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| ExtensionVersionKey |IntuneManagementExtension 버전의 고유 식별자입니다. | 1 |
| ExtensionVersion |4 자리 버전 번호입니다. |1.0.2.0 |

## <a name="intunemanagementextensionhealthstate"></a>IntuneManagementExtensionHealthState

**IntuneManagementExtensionHealthState**는 IntuneManagementExtension의 가능한 상태를 모두 나열합니다.

| 속성  | 설명 | 예제 |
|---------|------------|--------|
| ExtensionStateKey |상태의 고유 식별자입니다. | 2 |
| ExtensionState |IntuneManagementExtension의 상태입니다. | 정상 |

## <a name="intunemanagementextension"></a>IntuneManagementExtension

**IntuneManagementExtension**은 일별 각 Windows 10 디바이스의 IntuneManagementExtension 상태를 나열합니다.
데이터는 최근 60일 동안 보존됩니다. 


|      속성       |                         설명                         | 예제 |
|---------------------|-------------------------------------------------------------|---------|
|       DateKey       |               날짜의 고유 식별자입니다.                |   123   |
|      TenantKey      |              테넌트의 고유 식별자입니다.               |   456   |
|      DeviceKey      |              디바이스의 고유 식별자입니다.               |   789   |
| ExtensionVersionKey | IntuneManagementExtension 버전의 고유 식별자입니다. |    1    |
|  ExtensionStateKey  |             상태의 고유 식별자입니다.              |    2    |

