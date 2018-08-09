---
title: Microsoft Intune에서 등록 제한 설정
titlesuffix: ''
description: Intune에서 플랫폼별로 등록을 제한하고 장치 등록 제한을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9691982c-1a03-4ac1-b7c5-73087be8c5f2
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 2900f7c211a675a20300a2e212b0d57bad3a597a
ms.sourcegitcommit: 32a4b1eb6bf20da7262f27276f8e94e435803386
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39501152"
---
# <a name="set-enrollment-restrictions"></a>등록 제한 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune 관리자는 Intune을 사용하여 관리에 등록할 수 있는 장치의 수와 유형을 정의하는 등록 제한을 만들고 관리할 수 있습니다. 다수의 제한을 만들어서 다른 사용자 그룹에 적용할 수 있습니다. 다양한 제한 사항에 대한 [우선 순위](#change-enrollment-restriction-priority)를 설정할 수 있습니다.

>[!NOTE]
>등록 제한은 보안 기능이 아닙니다. 손상된 장치는 해당 문자를 잘못 표시할 수 있습니다. 이러한 제한은 무해한 사용자를 위한 최선의 장벽입니다.

>[!NOTE]
>이 아티클에서 언급된 그룹 할당 등록 제한 및 우선 순위 기능은 Intune 고객 기반에 롤아웃되고 있습니다. 이 롤아웃이 완료될 때까지 그룹 및 우선 순위 기능에 액세스하지 못할 수 있습니다.

만들 수 있는 등록 제한 사항은 다음과 같습니다.

- 등록된 장치의 최대 수
- 등록할 수 있는 장치 플랫폼:
  - Android:
  - Android 회사 프로필
  - iOS
  - macOS
  - 지원합니다.
- iOS, Android, Android 회사 프로필 및 Windows용 플랫폼 운영 체제 버전입니다. (Windows 10 버전만을 사용할 수 있습니다. Windows 8.1을 허용하는 경우 이 항목을 비워둡니다.)
  - 최소 버전
  - 최대 버전
- 개인 소유 장치 제한(iOS, Android, Android 회사 프로필, macOS만 해당).

## <a name="default-restrictions"></a>기본 제한 사항

기본 제한 사항은 장치 유형 및 장치 개수 등록 제한 모두에 자동으로 제공됩니다. 기본값에 대한 옵션을 변경할 수 있습니다. 기본 제한 사항은 모든 사용자 등록과 사용자가 없는 등록에 적용됩니다. 우선 순위가 더 높은 새로운 제한 사항을 만들어서 이러한 기본값을 재정의할 수 있습니다.

## <a name="create-a-restriction"></a>제한 사항 만들기

1. Azure Portal에 로그인합니다.
2. **추가 서비스**를 선택하고 **Intune**을 검색한 다음, **Intune**을 선택합니다.
3. **장치 등록** > **등록 제한**을 선택합니다.
4. **제한 만들기**를 선택합니다.
5. 제한의 이름과 설명을 입력합니다.
6. **제한 유형**을 선택한 다음, **만들기**를 선택합니다.
7. 장치 개수 제한은 **장치 제한**을 선택하여 사용자가 등록할 수 있는 장치의 최대 수를 설정합니다.
8. 장치 유형 제한은 **플랫폼** 및 **플랫폼 구성**을 선택하여 다양한 플랫폼 및 버전을 허용하거나 차단합니다.
9. **할당** > **+ 그룹 선택**을 선택합니다.
10. **그룹 선택**에서 그룹을 하나 이상 선택한 다음, **선택**을 선택합니다. 제한은 할당된 그룹에만 적용됩니다. 제한을 하나 이상의 그룹에 할당하지 않으면 아무런 효과가 없습니다.
11. **저장**을 선택합니다.
12. 새로운 제한은 기본값 바로 위의 우선 순위로 만들어집니다. [우선 순위는 변경](#change-enrollment-restriction-priority)할 수 있습니다.

## <a name="set-device-type-restrictions"></a>장치 유형 제한 설정

장치 유형 제한에 대한 설정은 다음 단계를 수행하여 변경할 수 있습니다.

1. Azure Portal에 로그인합니다.
2. **추가 서비스**를 선택하고 **Intune**을 검색한 다음, **Intune**을 선택합니다.
3. **장치 등록** > **등록 제한**을 선택합니다.
4. **장치 유형 제한**에서 설정하려는 제한을 선택합니다.
5. 제한 이름(기본 제한의 **모든 사용자**)에서 **플랫폼**을 선택합니다. 각 플랫폼 목록에 대해 **허용** 또는 **차단**을 선택합니다.
6. **저장**을 선택합니다.
7. 제한 이름(기본 제한의 **모든 사용자**)에서 **플랫폼 구성**을 선택합니다. 그럼 다음, 나열된 플랫폼에 대한 최소 및 최대 **버전**을 선택합니다. 지원되는 버전 형식은 다음과 같습니다.
    - Android 회사 프로필은 major.minor.rev.build를 지원합니다.
    - iOS는 major.minor.rev를 지원합니다.
    - Windows는 Windows 10용 major.minor.rev.build만 지원합니다.
  운영 체제 버전은 장비 등록 프로그램, Apple School Manager 또는 Apple Configurator 앱에 등록되는 Apple 장치에 적용되지 않습니다.
8. 나열된 각 플랫폼에서 **개인적으로 소유한**장치를 **허용**할지 **차단**할지 지정합니다.
    ![개인적으로 소유한 설정이 구성된 기본 장치 플랫폼 구성이 표시되는 장치 제한 작업 영역](media/device-restrictions-platform-configurations.png)
9. **저장**을 선택합니다.


>[!NOTE]
>- 개인적으로 소유한 Android 장치의 등록을 차단하는 경우에도 개인적으로 소유한 Android 회사 프로필 장치는 계속 등록할 수 있습니다.
>- 기본적으로 Android 회사 프로필 장치 설정은 Android 장치에 대한 설정과 동일합니다. Android 회사 프로필 설정을 변경하면 달라집니다.
>- 개인적인 Android 회사 프로필 등록을 차단하는 경우 회사 Android 장치만 Android 회사 프로필로 등록할 수 있습니다.

## <a name="set-device-limit-restrictions"></a>장치 개수 제한

장치 개수 제한에 대한 설정은 다음 단계를 수행하여 변경할 수 있습니다.

1. Azure Portal에 로그인합니다.
2. **추가 서비스**를 선택하고 **Intune**을 검색한 다음, **Intune**을 선택합니다.
3. **장치 등록** > **등록 제한**을 선택합니다.
4. **장치 개수 제한**에서 설정하려는 제한을 선택합니다.
5. **장치 제한**을 선택한 다음, 드롭다운 목록에서 사용자가 등록할 수 있는 장치의 최대 수를 선택합니다.
    ![장치 개수 제한이 있는 장치 개수 제한 블레이드](./media/device-restrictions-limit.png)
6. **저장**을 선택합니다.


등록된 장치 수가 한도에 다다랐을 때 사용자에게 알림이 표시됩니다. 예를 들어, iOS에서는 다음과 같습니다.

![iOS 장치 제한 알림](./media/enrollment-restrictions-ios-set-limit-notification.png)

## <a name="change-enrollment-restriction-priority"></a>등록 제한 우선 순위 변경

우선 순위는 사용자가 제한이 할당된 여러 그룹에 있는 경우에 사용됩니다. 사용자에게는 자신이 속한 그룹에 할당된 우선 순위가 가장 높은 제한만 적용됩니다. 예를 들어 Joe는 우선 순위가 5인 제한에 할당된 A 그룹과 우선 순위가 2인 제한에 할당된 B 그룹에도 속합니다. Joe에게는 우선 순위가 2인 제한만 적용됩니다.

제한을 만들면 기본값 바로 위 목록에 추가됩니다.

장치 등록에는 장치 유형 및 장치 개수 제한에 대한 기본 제한이 포함됩니다. 이러한 두 가지 제한은 우선 순위가 더 높은 제한으로 재정의된 경우가 아니면 모든 사용자에게 적용됩니다.

기본값 이외의 제한은 우선 순위를 변경할 수 있습니다.

1. Azure Portal에 로그인합니다.
2. **추가 서비스**를 선택하고 **Intune**을 검색한 다음, **Intune**을 선택합니다.
3. **장치 등록** > **등록 제한**을 선택합니다.
4. 우선 순위 목록의 제한을 마우스로 가리킵니다.
5. 세로 점 세 개를 사용하여 목록의 원하는 위치로 우선 순위를 끕니다.
