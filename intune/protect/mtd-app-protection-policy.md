---
title: Intune을 사용하여 MTD(Mobile Threat Defense) 앱 보호 정책 만들기
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 MTD(Mobile Threat Defense) 앱 보호 정책 만들기
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7279921719677fce0845517aefc5958f57ce13cb
ms.sourcegitcommit: 32391f74241ee3289a76ccd5319fe700b800d427
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2020
ms.locfileid: "77075708"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Intune을 사용하여 Mobile Threat Defense 앱 보호 정책 만들기

Intune 및 MTD(Mobile Threat Defense)를 사용하면 위협을 검색하고 모바일 디바이스의 위험을 평가할 수 있습니다. 위험을 평가하는 Intune 앱 보호 정책을 만들어 디바이스가 회사 데이터에 대한 액세스를 허용하는지 확인할 수 있습니다.


> [!NOTE]
> 이 문서는 앱 보호 정책을 지원하는 모든 Mobile Threat Defense 파트너에게 적용됩니다.
>
> - Better Mobile(Android)
> - Zimperium(Android, iOS)
> - Lookout for Work (Android, iOS).

## <a name="before-you-begin"></a>시작하기 전에

MTD 설치의 일부로 MTD 파트너 콘솔에서 다양한 위협을 높음, 보통 및 낮음으로 분류하는 정책을 만들었습니다. 이제 Intune 앱 보호 정책에서 Mobile Threat Defense 수준을 설정해야 합니다.

MTD를 사용한 앱 보호 정책에 대한 필수 구성 요소:

- Intune과 MTD 통합 설정 이 통합이 없으면 MTD 앱 보호 정책이 적용되지 않습니다.

## <a name="to-create-an-mtd-app-protection-policy"></a>MTD 앱 보호 정책을 만들려면

[iOS/iPadOS 또는 Android용 애플리케이션 보호 정책 만들기](../apps/app-protection-policies.md#app-protection-policies-for-iosipados-and-android-apps) 절차를 사용하고 *앱*, *조건부 시작* 및 *할당* 페이지에 대한 다음 정보를 사용합니다.

- **앱**: 앱 보호 정책의 대상으로 지정하려는 앱을 선택합니다. 이 기능 집합의 경우 선택한 모바일 위협 방어 공급업체의 디바이스 위험 평가에 따라 이러한 앱이 차단되거나 선택적으로 초기화됩니다. 
- **조건부 시작**:  *디바이스 조건* 아래에서 드롭다운 상자를 사용하여 **허용되는 최대 장치 위협 수준**을 선택합니다.

  위협 수준 **값** 옵션:

  - **보안**: 이 수준이 가장 안전합니다. 디바이스가 어떠한 위협에도 노출되지 않았으며 회사 리소스에 계속 액세스할 수 있습니다. 어떠한 위협이든 확인되는 디바이스는 비규격으로 평가됩니다.
  - **낮음**: 낮은 수준의 위협만 있는 디바이스는 규격 디바이스입니다. 더 높은 수준의 위협이 발생하면 디바이스는 규정 비준수 상태가 됩니다.
  - **중간**: 낮음 또는 보통 수준의 위협이 있는 디바이스는 규격 디바이스입니다. 높은 수준의 위협이 검색되는 경우 해당 디바이스는 비규격으로 간주됩니다.
  - **높음**: 보안이 가장 취약한 수준입니다. 이 수준은 모든 위협 수준을 허용하며 보고용으로만 Mobile Threat Defense를 사용합니다. 디바이스에 MTD 앱이 이 설정으로 활성화되어 있어야 합니다.

  **작업** 옵션:

  - **액세스 차단**
  - **데이터 초기화**

- **할당**: 사용자 그룹에 정책을 할당합니다.  그룹의 구성원이 사용하는 디바이스는 Intune 앱 보호를 통해 대상 앱의 회사 데이터에 액세스할 수 있는지 평가됩니다.


## <a name="next-steps"></a>다음 단계  

- Microsoft Intune의 [Mobile Threat Defense](~/protect/mobile-threat-defense.md)에 대해 자세히 알아봅니다.
