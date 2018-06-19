---
title: 사용자 및 장치 그룹 계획
description: 조직의 요구에 맞게 그룹을 계획합니다.
keywords: ''
author: sanchusa
manager: angrobe
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f11bb256-1094-4f7e-b826-1314c57f3356
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: lpatha
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 679399f306f3837a010cc01799c7567c1e5b5b39
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025317"
---
# <a name="plan-your-user-and-device-groups"></a>사용자 및 장치 그룹 계획

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune의 그룹을 통해 장치 및 사용자를 매우 유연하게 관리할 수 있습니다. 다음 사항에 따라 조직의 요구에 맞도록 그룹을 설정할 수 있습니다.

- 지리적 위치
- department
- 하드웨어 특성
- 운영 체제
- 장치가 사용자 소유인지 또는 회사 소유인지 여부


## <a name="how-intune-groups-work"></a>Intune 그룹의 작업 방법


Intune 관리 콘솔에 있는 **그룹** 노드의 기본 보기는 다음과 같습니다.

![Intune 콘솔에 있는 그룹 노드에 대한 기본 보기의 스크린샷](../media/Intune_Planning_Groups_Default_small.png)

정책이 그룹에 배포되므로 그룹 계층 구조는 디자인 시 주요 고려 사항 중 하나입니다. 그룹을 만든 후에는 해당 그룹의 상위 그룹을 변경할 수 없음을 알고 있어야 합니다. 그룹을 디자인하는 방법은 Intune 서비스 사용을 시작하는 순간부터 중요합니다. 여기서는 조직의 요구에 따라 그룹 계층 구조를 디자인하기 위한 몇 가지 권장 방법을 설명합니다.

## <a name="group-membership-rules"></a>그룹 구성원 자격 규칙

- 그룹에는 사용자 또는 장치 중 하나만 포함할 수 있으며 이 둘을 동시에 포함할 수는 없습니다.

    * **장치 그룹**. 여기에는 컴퓨터와 모바일 장치가 모두 포함됩니다. 그룹에 컴퓨터를 추가하려면 먼저 컴퓨터를 등록해야 합니다. 그룹에 모바일 장치를 추가하려면 먼저 모바일 장치를 지원하도록 환경을 구성해야 하고, Exchange ActiveSync에서 장치를 검색하거나 등록해야 합니다.

    * **사용자 그룹**. 그룹에는 보안 그룹의 사용자가 있을 수 있습니다. 보안 그룹은 Active Directory 인스턴스와 동기화합니다. Active Directory와 동기화하지 않는 경우 이러한 그룹을 수동으로 만들 수 있습니다.

- 하나의 장치 또는 사용자가 둘 이상의 그룹에 속할 수도 있습니다.

- 그룹에서 다음 구성원 규칙에 따라 구성원을 포함하거나 제외할 수 있습니다.

    * **구성원 자격 기준**. Intune에서 구성원을 포함하거나 제외하기 위해 실행하는 동적 규칙입니다. 이러한 기준은 로컬 Active Directory의 로컬 인스턴스와 동기화되는 보안 그룹 및 기타 정보를 사용합니다. 보안 그룹 또는 데이터가 변경되면 Active Directory와 동기화할 때 그룹 구성원이 달라질 수 있습니다.

    * **직접 멤버 관리 규칙**. 구성원을 명시적으로 추가하거나 제외하는 정적 규칙입니다. 구성원 목록은 정적입니다.

-   사용자 또는 컴퓨터를 포함하는 사용자 그룹이나 장치 그룹을 만들 경우 AD DS(Active Directory 도메인 서비스)는 필요하지 않습니다. 하지만 모바일 장치를 포함하는 장치 그룹의 경우 모바일 장치를 지원하도록 환경을 구성해야 합니다.

    또한 장치를 검색하여 Intune에 추가해야 합니다.

## <a name="group-relationship-rules"></a>그룹 관계 규칙

- 사용자가 만드는 모든 그룹에는 상위그룹이 있어야 합니다. 그룹이 만든 후에는 해당 그룹의 상위 그룹을 변경할 수 없습니다.

- 하위 그룹에 사용자 또는 장치를 추가할 경우:

    * 하위 그룹은 항상 상위 그룹의 일부입니다.

    * 하위 그룹에 추가하는 새 구성원은 자동으로 해당 그룹의 상위 그룹에 추가됩니다.

    * 구성원이 상위 그룹에서 제외되면 하위 그룹에 해당 구성원을 추가할 수 없습니다.

- 상위 그룹의 구성원이 하위 그룹의 사용 가능한 구성원을 정의합니다.

- 상위 그룹을 삭제하면 하위 그룹도 모두 삭제됩니다.

- 콘텐츠 및 정책을 하위 그룹에는 배포하지 않고 상위 그룹에만 배포할 수 있습니다.

- 특정 사용자 또는 장치가 상위 그룹의 구성원이 아닌 경우에는 하위 그룹에 해당 사용자 또는 장치를 추가할 수 있습니다. 이렇게 하면 새 하위 그룹 구성원이 상위 그룹에 추가됩니다.

    그러나 구성원이 상위 그룹에서 제외되는 경우 구성원은 하위 그룹에 추가할 수 없습니다.

- 그룹 구성원은 재귀적입니다. 예를 들면 다음과 같습니다.

    * **박단** 은 **노트북 사용자** 보안 그룹이라는 한 그룹에만 속한 구성원입니다.

    * **노트북 사용자** 그룹은 **승인된 사용자** 보안 그룹의 구성원입니다.

    * Intune에서 **승인된 사용자** 그룹의 구성원이 포함된 동적 구성원 쿼리를 사용하는 그룹을 만듭니다. 그 결과 Intune 사용자 그룹에 **Pat**이 포함됩니다.

> [!TIP]
> 그룹을 만들 때 정책을 적용하는 방법을 생각해야 합니다. 예를 들어 조직에 장치 운영 체제와 관련된 정책이나, Active Directory에 이미 정의된 조직 단위 또는 다른 역할과 관련된 정책이 있을 수 있습니다. 일부 관리자들은 iOS, Android 및 Windows 전용 장치 그룹을 만드는 것이 유용하다고 생각합니다. 이 작업에는 조직 역할 각각에 대해 사용자 그룹을 추가하는 것도 포함됩니다.

<!--- should we just link to a policies topic at this point and remove this? Ask Rob
 You'll probably want to create a default policy that applies to all groups and devices, to establish the basic compliance requirements of your organization. Then, you create more specific policies for the broadest categories of users and devices, for example, email policies for each of the device operating systems.

 Be careful when you name your policies, so that you can easily identify them later. For example, a good, descriptive policy name is **WP Email Policy for Entire Company**.

 Each time you create a restrictive policy, you'll want to communicate it to your users. After you create the more general groups and policies, pay attention to how you create smaller groups so that you can reduce unnecessary communication.--->

## <a name="built-in-groups"></a>기본 제공 그룹
Intune은 편집하거나 삭제할 수 없는 9개의 기본 제공 그룹을 제공합니다.<!--maybe a screen shot would be best?-->

-   **모든 사용자**
    -   그룹 해제된 사용자
-   **모든 장치**
    -   모든 컴퓨터
    -   모든 모바일 장치
        -   모든 직접 관리 장치
        -   모든 Exchange ActiveSync 관리 장치
    -   모든 회사 소유 장치
    -   그룹 해제된 장치

> [!NOTE]
> 명심할 사항: *단순하게 유지*. 다음 섹션에서 설명하는 것과 같은 특정 요구 사항이 조직에 없는 경우 간단하게 유지하고 기본 그룹 구조 및 정책을 사용해야 합니다. 이렇게 하면 장기적인 서비스 관리에 도움이 됩니다. 사용자를 일관되게 관리할 때 유지 관리는 보다 쉬워 집니다. 그룹별로 거의 차별화하지 않음으로써 유지 관리할 정책 수가 줄어 듭니다.


### <a name="all-users-and-devices-in-your-organization"></a>조직의 모든 사용자 및 장치
조직의 모든 사용자 및 장치에 상위 그룹을 정의합니다. 모두에 적용되는 정책이 있을 수 있습니다. 이 목적을 위해 Intune의 기본 **모든 사용자** 및 **모든 장치** 그룹을 사용할 수 있습니다. 본인의 고유 장치(BYOD)에 대한 그룹 및 회사 소유(CO) 장치에 대한 그룹과 같은 구체적인 사항별로 장치를 체계화하는 하위 그룹은 **모든 사용자** 및 **모든 장치** 상위 그룹의 하위 그룹일 수 있습니다.

## <a name="customize-groups-for-your-organization"></a>조직을 위해 그룹 사용자 지정

### <a name="byod-and-corporate-owned-devices"></a>BYOD 및 회사 소유 장치
조직이 직원이 본인의 장치를 사용하도록 허용하거나, 회사 소유 장치를 제공하거나, 둘의 조합을 적용한 경우 그러한 두 범주의 장치에 별도의 정책을 적용하는 것이 좋습니다.

BYOD 또는 혼합의 경우에 로컬 개인 정보 보호 규정을 침해하지 않는 정책을 계획해야 합니다. 자신의 장치를 가져오는 모든 사용자에 대한 부모 그룹을 만듭니다. 이 그룹을 사용하여 이 범주의 모든 사용자에 해당하는 정책을 적용할 수 있습니다.

![BYOD 상위 그룹 만들기](../media/Intune_Planning_Groups_BYOD_small.png)

마찬가지로 조직의 CO 장치 사용자에 대한 그룹을 만들 수 있습니다.

![BYOD 및 CO 장치에 대한 형제 사용자 그룹](../media/Intune_Planning_Groups_BYOD_Hierachy_View_small.png)

<!---START HERE--->

### <a name="groups-for-geographic-regions"></a>지역에 대한 그룹
조직에 특정 지역에 대한 정책이 필요한 경우 지리적 영역에 따라 그룹을 만들 수 있습니다. Active Directory 인스턴스에서 이미 만들었을 수 있는 지역 그룹을 기반으로 하고 이를 Azure Active Directory 서비스와 동기화할 수 있습니다. 또한 Azure Active Directory에서 지역 그룹을 직접 만들 수도 있습니다.

다음 스크린샷은 온-프레미스 Active Directory에서 동기화된 그룹을 기반으로 Intune 그룹을 만드는 방법을 보여 줍니다. 이 예제에서는 **미국 사용자 그룹**이라는 Active Directory 보안 그룹이 있다고 가정합니다.

먼저 일반 정보를 제공합니다.

![그룹 편집 영역의 스크린샷](../media/Intune_Planning_Groups_AD_General_small.png)

**구성원 자격 조건**에서 Active Directory와 동기화된 **미국 사용자 그룹**을 구성원 자격 규칙에 사용할 보안 그룹으로 선택합니다.

![그룹 편집 대화 상자의 스크린샷](../media/Intune_Planning_Groups_AD_Criteria_small.png)

항목을 검토한 다음 **마침**을 선택하여 그룹을 만듭니다.

![그룹 편집 대화 상자의 스크린샷](../media/Intune_Planning_Groups_AD_Summary_small.png)

이 예제에서는 중동 및 아시아에 대한 **MEA**라는 그룹도 만들었습니다.

> [!NOTE]
> 그룹 구성원 자격이 보안 그룹 구성원 자격에 따라 채워지지 않는 경우 그룹 구성원에게 Intune 라이선스를 할당했는지 확인합니다.

### <a name="groups-for-specific-hardware"></a>특정 하드웨어에 대한 그룹
조직이 특정 하드웨어 유형에 적용되는 정책을 요구하는 경우 이 요구 사항을 기반으로 그룹을 만들 수 있습니다. Active Directory의 온-프레미스 인스턴스에서 이미 만든 특정 그룹에 대한 정책을 기반으로 하고 이를 Azure Active Directory와 동기화할 수 있습니다. 또한 Azure Active Directory에서 그룹을 직접 만들 수도 있습니다. 이 예제에서는 **미국 사용자 그룹**을 **노트북 사용자** 그룹의 상위 그룹으로 사용합니다.

![보안 그룹 대화 상자 선택](../media/Intune_Planning_Groups_Laptop_small.png)

이제 그룹 계층은 다음 스크린샷과 비슷하게 보일 것입니다. Intune 그룹 **노트북 사용자** 내에 구성원이 표시됩니다. 이제 이 그룹에 적용된 모든 정책이 미국 지역의 BYOD 노트북 사용자에게 적용됩니다.

![노트북 사용자 그룹의 표시](../media/Intune_Planning_Groups_Laptop_Hierarchy_small.png)

### <a name="groups-for-specific-operating-systems"></a>특정 운영 체제에 대한 그룹
조직이 Android, iOS 또는 Windows와 같은 특정 운영 체제에 적용되는 정책을 요구하는 경우 이 요구 사항을 기반으로 그룹을 만들 수 있습니다. 앞의 예와 같이 Active Directory의 온-프레미스 인스턴스에서 이미 만든 OS 고유 그룹에 대한 정책을 기반으로 하고 이를 Azure Active Directory와 동기화할 수 있습니다. 또한 Azure Active Directory 인스턴스에서 그룹을 직접 만들 수도 있습니다.

이전 예제에 나오는 방법을 동일하게 사용하여 특정 운영 체제 플랫폼을 사용하는 <!--devices?--> 사용자를 기반으로 그룹을 만들 수 있습니다.

> [!NOTE]
> 사용자가 여러 모바일 플랫폼 또는 운영 체제를 사용하며 사용자를 Android 사용자, iOS 사용자 또는 Windows 사용자로 분류하는 자동화된 방식이 없는 경우 장치 수준에서 정책을 적용하는 것이 좋습니다. 이렇게 하면 운영 체제와 관련된 정책을 훨씬 유연하게 적용할 수 있습니다.
>
> 장치의 운영 체제를 기반으로 그룹을 동적으로 프로비전할 수 없습니다. 대신 Active Directory 또는 Azure Active Directory 보안 그룹을 사용하여 작업을 수행해 보세요.

![노트북 사용자 그룹](../media/Intune_Planning_Groups_OS_Hierachy_small.png)

모든 사용자 그룹이 조직 요구 사항에 따라 채워진 후 그룹 계층 구조는 다음과 같아야 합니다.

![그룹 계층 보기](../media/Intune_Planning_Groups_Midpoint_Hierachy_small.png)

이 계층 구조를 사용하여 조직의 정책을 적용할 수 있습니다.

### <a name="device-groups"></a>장치 그룹
다음와 같이 BYOD 시나리오에 대해 모든 직원 소유 장치를 포함하는 광범위한 그룹으로 시작하여 장치에 대한 유사한 그룹을 만들 수도 있습니다.

![그룹 만들기 대화 상자](../media/Intune_Planning_Groups_Device_General_small.png)

그룹에 모든 BYO 장치가 포함되도록 **모든 장치(컴퓨터 및 모바일)** 을 선택해야 합니다.

![구성원 자격 기준 정의 페이지](../media/Intune_Planning_Groups_Device_Criteria_small.png)

항목을 검토한 다음 **마침**을 선택하여 BYOD 그룹을 만듭니다.

![그룹 만들기 대화 상자](../media/Intune_Planning_Groups_Device_Summary_small.png)

장치 그룹 계층 구조가 사용자 그룹 계층 구조와 비슷해질 때까지 계속해서 장치 그룹을 만듭니다. Intune 콘솔의 그룹 노드가 다음과 같이 표시됩니다.

![Intune 그룹 계층 보기](../media/Intune_Groups_Hierarchy_Final_Small.png)

## <a name="group-hierarchies-and-naming-conventions"></a>그룹 계층 구조 및 명명 규칙
정책 관리가 용이하도록 각 정책의 이름을 용도, 플랫폼 및 적용하는 범위에 따라 지정하는 것이 좋습니다. 정책 적용을 준비할 때 만든 그룹 구조를 따르는 명명 표준을 사용하세요.

예를 들어 미국 지역 수준에서 모든 회사, Android, 모바일 장치에 적용되는 Android 정책의 경우 정책 이름을 **CO_US_Mob_Android_General**로 지정할 수 있습니다.

![Android에 대한 정책 만들기](../media/Intune_planning_policy_android_small.png)

이러한 방식으로 정책 이름을 지정하면 아래와 같이 정책과, **정책**에서 의도한 사용 및 범위를 빠르게 식별할 수 있습니다.

![Intune 정책 목록](../media/Intune_planning_policy_view_small.png)

## <a name="next-steps"></a>다음 단계
[그룹 만들기](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)
