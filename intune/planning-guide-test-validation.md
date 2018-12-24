---
title: Intune 테스트 및 유효성 검사
titlesuffix: Microsoft Intune
description: 사용자 환경에서 Intune 클라우드 전용 솔루션의 테스트 및 유효성 검사 방법.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4f82ee0c-4bd6-4623-9b10-9249d316ccf5
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: ba214e059e9a5ddb17a8b1344d4d30ab1d7b40fa
ms.sourcegitcommit: 5058dbfb0e224207dd4e7ca49712c6ad3434c83c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2018
ms.locfileid: "53112462"
---
# <a name="intune-testing-and-validation"></a>Intune 테스트 및 유효성 검사

Microsoft Intune 구현을 테스트할 때 기능 유효성 검사 및 사용 사례 유효성 검사를 고려 합니다. 기능 유효성 검사는 각 구성 요소 및 구성이 올바르게 작동하는지 확인하는 테스트로 구성됩니다. 사용 사례 유효성 검사는 일련의 작업이 연관된 시나리오가 예상 대로 작동하는지 확인하는 테스트가 포함됩니다. 

지원 설명서를 만들도록 테스트 단계에 IT 지원 및 지원 센터 직원을 포함하는 것이 좋습니다. 그러면 IT 지원 및 지원 센터 직원의 제품 지원이 편리해집니다. 구성 요소 또는 시나리오가 사용 사례에 따라 작동하지 않을 경우 필요한 변경 내용을 문서화하고 변경을 수행한 이유를 포함해야 합니다.

## <a name="before-you-begin"></a>시작하기 전에

다음을 문서화하는 것이 좋습니다.

-   **테스트 기준**: 비교 측정할 벤치마크를 확인합니다.

-   **설계 구성 요소**: 하나 이상의 테스트 기준에 존재해야 합니다.

요구 사항 또는 시나리오에 맞는 설계 구성 요소가 하나 이상의 테스트 기준에 존재하지 않는 경우 설계 구성 요소가 필요한지 여부를 고려해야 합니다. 또한 다음 항목이 있는지 확인해야 합니다.

-   **계정:** 모든 사용 사례 시나리오를 테스트하려면 EMS 및 Office 365에 대한 라이선스가 있는 테스트 계정이어야 합니다.

-   **디바이스:** 공장 기본값으로 초기화하거나 다시 설정할 수 있는 테스트 디바이스입니다.

-   **통합 구성 요소:** 필요한 경우 모든 통합 구성 요소(Certificate Connector, Hosted Exchange용 Intune Service To Service Connector 및 Intune On-Premises Exchange Connector)를 설치하고 구성해야 합니다.

예측하지 못한 문제를 해결하기 위해 설계를 변경해야 할 수 있습니다. 또한 모든 설계 변경 내용은 각 변경에 대한 이유와 함께 완벽하게 문서화해야 합니다. 다음은 어떤 변경이 일어날 수 있는지를 보여 주는 예입니다.

<blockquote>NDES(네트워크 디바이스 등록 서비스)의 요구 사항을 충족하지 못한다는 사실을 알게 될 수 있습니다. 그리고 NDES 구현 없이 동일한 요구 사항을 충족하는 루트 CA를 사용하여 VPN 및 Wi-Fi 프로필을 구성할 수도 있음을 알게 됩니다.</blockquote>

테스트 및 유효성 검사 프로세스 중 기술 지침 또는 특수한 문제 해결이 필요한 과제 또는 문제에 직면할 수 있습니다. 이 경우 Microsoft 지원 채널을 통해 지원을 요청하는 것이 좋습니다.

-   [Microsoft Intune에 대한 관리 지원을 받는 방법](get-support.md)

-   [Microsoft Intune의 담당자 전화 지원](get-support.md)

## <a name="functional-validation-testing"></a>기능 유효성 검사 테스트

기능 유효성 검사는 각 구성 요소 및 구성이 올바르게 작동하는지 확인하는 테스트로 구성됩니다. 유효성 검사 테스트의 예는 아래 표에 나와 있습니다.

![섹션 9 표 1](./media/section-9-image-1-table.PNG)

## <a name="use-case-validation-testing"></a>사용 사례 유효성 검사 테스트

시나리오가 완전하며 작동하는지 확인하려면 사용 사례 유효성 검사 테스트를 수행합니다. 두 가지 유형 즉, IT 관리자 및 최종 사용자의 사용 사례 시나리오가 있습니다.

### <a name="it-admin"></a>IT 관리자

디바이스에서 수행되거나 사용자가 수행한 관리 작업이 올바르게 작동하는지 확인하려면 IT 관리자 유효성 검사 테스트를 수행합니다. 다음은 IT 관리자 종단 간 유효성 검사 시나리오의 예입니다.

![섹션 9 표 2](./media/section-9-image-2-table.PNG)

### <a name="end-user"></a>최종 사용자

최종 사용자 환경이 예상대로 작동하며 모든 사용자 통신에 제대로 표시되는지 확인하려면 최종 사용자 유효성 검사 테스트를 수행합니다. 최종 사용자 환경이 올바른지 유효성을 검사하는 것이 중요합니다. 유효성 검사에 실패하면 채택 비율은 낮아지고 지원 센터 호출은 많아질 수 있습니다.

![섹션 9 표 3](./media/section-9-image-3-table.PNG)

## <a name="next-steps"></a>다음 단계

Intune 기능 및 사용자 사례 시나리오를 테스트하고 그 유효성을 검사했으므로 이제 [Intune 프로덕션 출시](planning-guide-rollout-plan.md)에 대한 준비가 되었습니다.

계획 템플릿 및 정보를 자세히 보려면 [추가 리소스](planning-guide-resources.md)를 참조하세요.
