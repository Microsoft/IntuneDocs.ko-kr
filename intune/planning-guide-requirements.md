---
title: 사용 사례 시나리오 요구 사항 확인
titleSuffix: Microsoft Intune
description: 이 문서의 정보를 활용하여 Microsoft Intune 클라우드 전용 구현을 위한 Intune 사용 사례 및 하위 사용 사례 시나리오 요구 사항을 확인할 수 있습니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: fd8cb5f7-19f0-4d80-8825-2bafa49624af
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9cb08757732aa5cad08ed0a4b535fb20c0aa1df0
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67528265"
---
# <a name="determine-use-case-scenario-requirements"></a>사용 사례 시나리오 요구 사항 확인

이 섹션에서는 각 사용 사례 시나리오 내에서 각 조직 그룹에 대한 요구 사항을 확인합니다. 이 프로세스를 완료하면 아키텍처, 설계, 온보딩 및 출시와 같은 다른 Intune 배포 계획 영역에 대해 더 적절히 준비할 수 있습니다. 또한 Intune 배포 프로젝트와 관련된 잠재적인 차이 및 과제를 파악할 수도 있습니다.

사용 사례 및 하위 사용 사례 시나리오, 그리고 이와 관련된 조직 그룹과 모바일 디바이스 플랫폼 각각에 대해 다양한 요구 사항 집합이 있을 수 있습니다. 예를 들어 회사 사용 사례 시나리오 요구 사항에 따라 6자로 된 PIN 또는 사용하지 않도록 설정된 클라우드 백업과 같이 보다 제한적인 디바이스 설정 집합을 사용하여 Intune에 디바이스를 등록해야 할 수 있습니다. 반면 BYOD("Bring Your Own Device") 사용 사례 시나리오는 제한 수준이 낮아 4자로 된 PIN과 클라우드 백업 사용이 허용될 수도 있습니다.

회사 사용 사례 시나리오에 대해 다른 요구 사항 집합(예: PIN 설정, Wi-Fi 또는 VPN 프로필, 배포된 앱)이 있는 조직 그룹이 있을 수도 있습니다. 또한 요구 사항이 모바일 디바이스 플랫폼의 기능(예: 지문 판독기, 전자 메일 프로필)에 의해 결정될 수 있습니다.

다음은 조직 사용 사례 요구 사항의 몇 가지 예로, 각 사용 사례 및 하위 사용 사례 시나리오, 조직 그룹 및 모바일 디바이스 플랫폼에 대한 다양한 요구 사항 집합이 나와 있습니다. 아래 표를 사용하여 조직의 사용 사례 요구 사항을 입력할 수도 있습니다.

| **사용 사례** | **하위 사용 사례** | **그룹** | **디바이스 플랫폼** | **요구 사항** |
|:---:|:---:|:---:|:---:|:---:|
| 회사 | 정보 근로자 | HR, 재무 | iOS | 보안 전자 메일, 디바이스 설정, 프로필, 앱 |                                                          
| 회사 | 임원 | HR, 재무 | iOS | 보안 전자 메일, 디바이스 설정, 프로필, 앱 |                                                         
| 회사 | 키오스크 | 소매 | Android | 디바이스 설정, 프로필, 앱 |
| BYOD | 정보 근로자 | 마케팅, 영업 | iOS | 보안 전자 메일, 디바이스 설정, 프로필, 앱 |                                                         
| BYOD | 임원 | 마케팅, 영업 | iOS | 보안 전자 메일, 디바이스 설정, 프로필, 앱 |

[위 표의 템플릿을 다운로드](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0)하여 조직의 사용 사례 및 하위 사용 사례 요구 사항을 입력할 수 있습니다.


## <a name="examples-of-requirements"></a>요구 사항의 예

"요구 사항" 열에 사용할 수 있는 예를 몇 가지 더 들자면 다음과 같습니다.

- **보안 메일**
    - Exchange Online/온-프레미스에 대한 조건부 액세스
    - Outlook 앱 보호 정책

- **디바이스 설정**
    - 4자 또는 6자를 사용하여 PIN 설정
    - 클라우드 백업 제한

- **프로필**
    - Wi-Fi
    - VPN
    - 메일(Windows 10 Mobile)

- **앱**
    - 앱 보호 정책을 사용하는 Office 365
    - 앱 보호 정책을 사용하는 LOB(기간 업무)

## <a name="next-steps"></a>다음 단계

다음 섹션에서는 [Intune 출시 계획 개발 방법](planning-guide-rollout-plan.md)에 대한 지침을 제공합니다.
