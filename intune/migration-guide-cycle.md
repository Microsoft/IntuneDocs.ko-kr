---
title: 일반적인 Intune 마이그레이션 주기 작동 방식
titleSuffix: Microsoft Intune
description: 이 아티클에서는 Microsoft Intune 마이그레이션 주기 작동 방식에 대해 설명하고 고객이 마이그레이션 주기를 처리하는 방법에 대한 예제를 제공합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3688b724-9521-4210-bf4d-bcf47d8d4ca0
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87e5ac06e93027b577d42b27e7d15b9b18e11020
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67046355"
---
# <a name="typical-migration-cycle"></a>일반적인 마이그레이션 주기

조직에서는 일반적으로 IT 부서의 사용자 하위 집합을 대상으로, 소규모 파일럿을 통해 Intune 마이그레이션을 시작합니다. 또한 조직은 변경에 대한 그룹의 열의, 사용자 수, 복잡성, 요구 사항, 위치 및 비즈니스 위험 등의 요인에 대해 논의하여 마이그레이션 기간 결정 과정을 지원해야 할 수 있습니다.

다음은 대상 그룹을 예약하는 방법에 대한 예입니다.

  | **마이그레이션 대상 그룹** | **기간 1** | **기간 2** | **기간 3** | **기간 4** | **...**
|:---:|:---:|:---:|:---:|:---:|:---:|
| 제한된 파일럿 IT 조직(사용자 50명) | 계획 발표 | 등록 지시 | 마감일 지정 | 조건부 액세스 적용 |  |                                                        
| 확장된 파일럿 IT 조직(사용자 200명) |  | 계획 발표 | 등록 지시 | 마감일 지정 | 조건부 액세스 적용 |
| 마이그레이션 1단계 기술에 정통한 사용자(2,000명) |  |  | 계획 발표 | 등록 지시 | 마감일 지정 |
| 마이그레이션 2단계 미국 동부 |  |  |  | 계획 발표 | 등록 지시 |
| 모든 지역 |  |  |  |  | 계획 발표 |

## <a name="customer-migration-case-study"></a>고객 마이그레이션 사례 연구

### <a name="adatum-corporation"></a>Adatum Corporation

[how Adatum Corporation went through the process of migration from a third-party MDM provider to Intune](https://gallery.technet.microsoft.com/Intune-migration-guide-893a95e3?redir=0)(Adatum Corporation이 타사 MDM 공급자에서 Intune으로 마이그레이션 프로세스를 수행한 방법)을 확인해 보세요.

## <a name="monitoring-migration"></a>마이그레이션 모니터링

Intune에서는 마이그레이션을 모니터링할 수 있는 여러 방법을 제공합니다.

* Intune 사용자 그룹 뷰

* 기본 제공 보고서 집합

* 콘솔 내 경고

다음을 수행할 수 있도록 각 단계 후 얼마나 많은 사용자가 디바이스를 등록했는지 추적합니다.

-   통신 계획의 효율성 평가

-   조건부 액세스 적용의 영향 예측


## <a name="post-migration"></a>마이그레이션 후

Intune으로 마이그레이션한 후 이전 MDM 공급자를 사용 중지하고 서비스 구독을 취소합니다. 또한 MDM 공급자의 지침에 따라 불필요한 인프라 요구 사항을 제거합니다.
