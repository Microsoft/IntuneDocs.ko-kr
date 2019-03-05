---
title: 사용 사례 시나리오 확인
titlesuffix: Microsoft Intune
description: 이 문서의 정보를 활용하여 Microsoft Intune 클라우드 전용 구현을 위한 Intune 사용 사례 및 하위 사용 사례 시나리오를 확인할 수 있습니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4b3c9af9-78da-44d2-8bd2-3f0f8885952d
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 654b9c373d5abf351dc3156c12b365c1b1fd3423
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57238424"
---
# <a name="identify-mobile-device-management-use-case-scenarios"></a>모바일 디바이스 관리 사용 사례 시나리오 확인

사용 사례 시나리오의 확인은 성공적인 Intune 배포를 위한 계획 프로세스의 중요한 부분입니다. 사용 사례 시나리오는 사용자를 사용자 유형이나 역할 및 사용자 디바이스 소유권(예: 회사 소유 또는 개인 소유)에 따라 관리 가능한 그룹으로 구분할 수 있도록 하므로 유용합니다.

조직이 Intune 사용 사례 시나리오뿐만 아니라 조직 그룹 및 각 사용 사례와 관련된 모바일 디바이스 플랫폼을 확인하는 데에도 도움이 되는 몇 가지 예를 살펴보겠습니다.

## <a name="device-ownership"></a>디바이스 소유권
배포에 대한 주요 사용 사례 시나리오를 확인할 수 있도록 먼저 조직의 Intune 배포 목적과 목표를 참조할 수 있습니다. Intune 배포 계획의 범위 내에서 다음 질문에 대한 대답을 생각해 보세요.

-   회사 소유 디바이스를 지원할 계획인가요?

-   개인 소유 디바이스(BYOD)를 지원할 계획인가요?

이러한 질문은 특정 옵션 중 하나를 선택하는 것이 아닙니다. 즉, 조직의 목적을 충족하기 위해 두 가지 형태의 디바이스 소유권을 모두 지원해야 할 수도 있습니다. 하위 사용 사례를 활용하면 서로 다른 디바이스 관리 정책을 적용해야 하는 경우를 파악할 수 있습니다.

### <a name="user-type-or-device-role"></a>사용자 유형 또는 디바이스 역할

각 사용 사례 시나리오에 하위 사용 사례도 포함되는지를 확인합니다. 예를 들어 조직에서 다음과 같이 사용자 유형 또는 디바이스 역할에 따른 추가 하위 사용 사례가 포함된 회사 사용 사례 시나리오를 지원하기 위한 요구 사항을 확인했을 수 있습니다.

-   정보 근로자

-   임원

-   키오스크

다음은 사용 사례 및 하위 사용 사례 시나리오의 몇 가지 예입니다.

| **사용 사례** | **하위 사용 사례** |
|:---:|:---:|
| 회사 | 정보 근로자 |              
| 회사 | 임원 |           
| 회사 | 키오스크 |
| BYOD | 정보 근로자 |           
| BYOD | 임원 |

[위 표의 템플릿을 다운로드](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)하여 조직의 사용 사례 및 하위 사용 사례 시나리오를 입력할 수 있습니다.

## <a name="organizational-groups-for-your-scenarios"></a>시나리오 관련 조직 그룹

이제 각 사용 사례 및 하위 사용 사례 시나리오와 관련된 조직 그룹을 확인해야 합니다. 예를 들면 다음과 같습니다.

| **사용 사례** | **하위 사용 사례** | **조직 그룹** |
|:---:|:---:|:---:|
| 회사 | 정보 근로자 | HR, 재무 |               
| 회사 | 임원 | HR, 재무 |            
| 회사 | 키오스크 | 소매 |
| BYOD | 정보 근로자 | 마케팅, 영업 |            
| BYOD | 임원 | 마케팅, 영업 |


## <a name="mobile-device-platforms-for-your-scenarios"></a>시나리오의 모바일 디바이스 플랫폼

다음 단계에서는 각 사용 사례 시나리오와 관련된 모바일 디바이스 플랫폼을 확인합니다. 플랫폼이 여러 개일 수도 있습니다.

예를 들어 회사 사용 사례 시나리오가 iOS 및 Android Samsung Knox 디바이스 플랫폼을 지원할 수 있습니다. 그리고 BYOD 정책의 경우 Samsung Knox가 아닌 Android 및 Windows 10 Mobile과 같은 추가 모바일 디바이스 플랫폼 지원을 포함할 수 있습니다. 위의 예를 토대로 하여 각 사용 사례 시나리오와 연결된 모바일 디바이스 플랫폼이 아래에 나와 있습니다.

| **사용 사례** | **하위 사용 사례** | **그룹** | **디바이스 플랫폼** |   
|:---:|:---:|:---:|:---:|
| 회사 | 정보 근로자 | HR, 재무 | iOS |                                                           
| 회사 | 임원 | HR, 재무 | iOS |                                                           
| 회사 | 키오스크 | 소매 | Android |
| BYOD | 정보 근로자 | 마케팅, 영업 | iOS |                                                           
| BYOD | 임원 | 마케팅, 영업 | iOS |

## <a name="next-steps"></a>다음 단계

다음 섹션에서는 [각 사용 사례 시나리오에 대한 Intune 요구 사항을 확인하는 방법](planning-guide-requirements.md)에 대한 지침을 제공합니다.
