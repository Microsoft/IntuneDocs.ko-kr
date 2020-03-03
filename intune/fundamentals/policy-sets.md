---
title: 정책 세트
titleSuffix: Microsoft Intune
description: 정책 세트를 사용하여 Microsoft Intune에서 관리 개체 컬렉션을 그룹화합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 12/19/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: craigma
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 48bfe727615f5165fc70ed2e08f98f01203dc895
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514832"
---
# <a name="use-policy-sets-to-group-collections-of-management-objects"></a>정책 세트를 사용하여 관리 개체 컬렉션 그룹화

정책 세트를 사용하면 단일 개념 단위로 식별, 대상 지정 및 모니터링해야 하는 기존 관리 엔터티에 대한 참조 번들을 만들 수 있습니다. 정책 세트는 사용자가 만든 앱, 정책 및 기타 관리 개체의 할당 가능한 컬렉션입니다. 정책 세트를 만들면 한 번에 여러 다른 개체를 선택하고 한 위치에서 할당할 수 있습니다. 조직이 변경되면 정책 세트를 다시 방문하여 해당 개체 및 할당을 추가하거나 제거할 수 있습니다. 정책 세트를 사용하여 단일 패키지의 앱, 정책 및 VPN과 같은 기존 개체를 연결하고 할당할 수 있습니다. 

> [!IMPORTANT]
> 정책 세트에 관련된 알려진 문제 목록은 [정책 세트 알려진 문제](~/fundamentals/policy-sets.md#policy-sets-known-issues)를 참조하세요.

정책 세트는 기존 개념 또는 개체를 대체하지 않습니다. 개별 개체를 계속 할당할 수 있으며 정책 세트의 일부로 개별 개체를 참조할 수도 있습니다. 따라서 해당 개별 개체의 모든 변경 내용이 정책 세트에 반영됩니다. 

정책 세트를 사용하여 다음을 수행할 수 있습니다.

- 할당해야 하는 개체를 함께 그룹화
- 모든 관리형 디바이스에서 조직의 최소 구성 요구 사항 할당
- 모든 사용자에게 일반적으로 사용되거나 관련된 앱 할당

정책 세트에 다음 관리 개체를 포함할 수 있습니다.
- 앱
- 앱 구성 정책
- 앱 보호 정책
- 디바이스 구성 프로필
- 디바이스 준수 정책
- 디바이스 유형 제한
- Windows AutoPilot 배포 프로필
- 등록 상태 페이지

정책 세트를 만들 때 단일 할당 단위를 만들고 여러 개체 간 연결을 관리합니다. 정책 세트는 외부 개체에 대한 참조가 됩니다. 포함된 개체의 모든 변경 내용이 정책 세트에도 영향을 줍니다. 정책 세트를 만든 후 해당 개체 및 할당을 반복적으로 보고 편집할 수 있습니다. 

> [!NOTE]
> 정책 세트는 Windows, Android, macOS 및 iOS/iPadOS 설정을 지원하며 플랫폼 간에 할당될 수 있습니다.

## <a name="how-to-create-a-policy-set"></a>정책 세트를 만드는 방법

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **정책 세트** > **정책 세트** > **만들기**를 선택합니다.
3. **기본 사항** 페이지에서 다음 값을 추가합니다.
    - **정책 세트 이름** - 이 정책 세트의 이름을 제공합니다.
    - **설명** - 필요에 따라 정책 세트에 대한 설명을 제공합니다.
   <p>
   <img alt="Create policy set - Basics" src="~/fundamentals/media/policy-sets/policy-sets-01.png">

4. **다음: 애플리케이션 관리**를 클릭합니다.<br>
   **애플리케이션 관리** 페이지에서 필요에 따라 [앱](~/apps/apps-add.md), [앱 구성 정책](~/apps/app-configuration-policies-overview.md) 및 [앱 보호 정책](~/apps/app-protection-policy.md)을 정책 세트에 추가할 수 있습니다. 앱 관리에 대한 자세한 내용은 [Microsoft Intune 앱 관리란?](~/apps/app-management.md)을 참조하세요. 
5. **다음: 장치 관리**를 클릭합니다.<br>
   **장치 관리** 페이지에서는 [디바이스 구성 프로필](~/configuration/device-profiles.md) 및 [디바이스 준수 정책](~/protect/device-compliance-get-started.md)과 같은 장치 관리 개체를 정책 세트에 추가할 수 있습니다. 다른 정책, 인증서 및 보안 기준 프로필과 같은 관련된 모든 개체를 포함해야 합니다.
6. **다음: 디바이스 등록**을 클릭합니다.<br>
   **디바이스 등록** 페이지에서는 [디바이스 유형 제한](~/enrollment/enrollment-restrictions-set.md), [Windows Autopilot 배포 프로필](~/enrollment/enrollment-autopilot.md) 및 [등록 상태 페이지 프로필](~/enrollment/windows-enrollment-status.md)과 같은 디바이스 등록 개체를 정책 세트에 추가할 수 있습니다.
7. **다음: 할당**을 클릭합니다.<br>
   **할당** 페이지에서는 사용자 및 디바이스에 정책 세트를 할당할 수 있습니다. Intune에서 디바이스를 관리하는지 여부와 관계없이 디바이스에 정책 세트를 할당할 수 있다는 점에 유의해야 합니다.
8. **다음: 검토 + 만들기**를 클릭하여 프로필에 대해 입력한 값을 검토합니다.
9. 작업이 완료되면 **만들기**를 클릭하여 Intune에서 정책 세트를 만듭니다. 

## <a name="policy-sets-known-issues"></a>정책 세트 알려진 문제

1910의 새로운 기능은 정책 세트에는 다음과 같은 알려진 문제가 있습니다.

- 정책 세트를 만들 때 범위가 지정된 관리자가 범위 태그를 선택하지 않고 정책 세트를 만들려고 하면 **검토 + 만들기** 페이지에 도달할 때 유효성 검사에 실패하며 상태 표시줄에 오류가 표시됩니다. 관리자는 프로세스의 다른 페이지로 전환한 후 **검토 + 만들기** 페이지로 돌아가야 합니다. 이렇게 하면 **만들기** 옵션을 사용할 수 있습니다.  
 
- 현재 정책 세트에서 지원되는 앱 유형은 다음과 같습니다.
    - iOS/iPadOS 스토어 앱
    - iOS/iPadOS 기간 업무 앱
    - 관리형 iOS/iPadOS 기간 업무 앱
    - Android 스토어 앱
    - Android 기간 업무 앱
    - 관리형 Android 기간 업무 앱
    - Office 365 ProPlus 제품군(Windows 10)
    - 웹 링크
    - 기본 제공 iOS/iPadOS 앱
    - 기본 제공 Android 앱

- **모든 사용자**의 정책 세트 할당을 **Autopilot 프로필**로 설정할 수는 없습니다.

- 정책 세트에는 다음과 같은 등록 제한 및 ESP(등록 상태 페이지) 문제가 있습니다.
    - 제한 및 ESP는 가상 그룹 할당을 지원하지 않습니다.
    - 제한 및 ESP는 제외 그룹 할당을 지원하지 않습니다. 
    - 제한 및 ESP는 우선 순위 기반 충돌 해결을 사용합니다. 제한 및 ESP가 우선 순위가 더 높은 제한 및 ESP의 대상으로 지정되는 경우에는 나머지 정책 세트 페이로드와 동일한 사용자에게 제한 및 ESP가 적용되지 않을 수 있습니다.
    - 기본 제한 및 ESP는 정책 세트에 추가될 수 없습니다.

- 정책 세트를 지원하는 MAM 정책 유형은 다음과 같습니다. 
    - MAM WIP(Windows) MDM 대상 관리형 앱 보호 
    - MAM iOS/iPadOS 대상 관리형 앱 보호
    - MAM Android 대상 관리형 앱 보호
    - MAM iOS/iPadOS 대상 관리형 앱 구성
    - MAM Android 대상 관리형 앱 구성

- 정책 세트를 지원하지 않는 MAM 정책 유형은 다음과 같습니다. 
    - MAM WIP(Windows) 대상 관리형 앱 보호

- MAM은 정책 세트 할당을 다음 정책 유형의 직접 할당으로 처리합니다.
    - MAM iOS/iPadOS 대상 관리형 앱 보호
    - MAM Android 대상 관리형 앱 보호
    - MAM iOS/iPadOS 대상 관리형 앱 구성
    - MAM Android 대상 관리형 앱 구성

    그룹에 배포된 정책 세트에 정책이 추가되면 그룹은 “정책 세트를 통해 할당됨”이 아니라 워크로드에서 직접 할당됨으로 표시됩니다. 이로 인해 MAM은 정책 세트에서 들어오는 그룹 할당 삭제를 처리하지 않습니다.

- MAM은 모든 정책 유형의 **모든 사용자** 및 **모든 디바이스** 가상 그룹에 대한 배포를 지원하지 않습니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune에 디바이스 등록](~/enrollment/index.yml)