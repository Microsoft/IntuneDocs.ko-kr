---
title: Microsoft Intune에서 디바이스 프로필 할당
description: Azure Portal을 사용하여 사용자 및 디바이스에 디바이스 프로필 및 정책을 할당합니다. Microsoft Intune에서 프로필 할당으로부터 그룹을 제외하는 방법에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f6f5414d-0e41-42fc-b6cf-e7ad76e1e06d
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f489f4d53fde988dd9ce8c7c4cc61cbded701fc4
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55841218"
---
# <a name="assign-user-and-device-profiles-in-microsoft-intune"></a>Microsoft Intune에서 사용자 및 디바이스 프로필 할당

프로필을 만든 후에 Azure AD(Azure Active Directory) 그룹에 해당 프로필을 할당할 수 있습니다.

## <a name="assign-a-device-profile"></a>디바이스 프로필 할당

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Microsoft Intune**을 검색합니다.
2. **Microsoft Intune**에서 **디바이스 구성**를 선택한 다음, **프로필**을 선택합니다.
3. 프로필 목록에서 할당할 프로필을 선택한 다음, **할당**을 선택합니다.
4. 그룹을 **포함**하거나 **제외**하기로 선택한 다음, 그룹을 선택합니다.  

    ![프로필 할당에서 그룹 제외 또는 포함하는 옵션 스크린샷](./media/group-include-exclude.png)

5. 그룹을 선택하면 Azure AD 그룹을 선택합니다. 여러 그룹을 선택하려면 **Ctrl** 키를 누르고 있습니다.
6. 작업이 완료되면 **저장**을 선택합니다.

## <a name="exclude-groups-from-a-profile-assignment"></a>프로필 할당에서 그룹 제외

Intune 디바이스 구성 프로필을 통해 정책 할당에서 그룹을 제외할 수 있습니다. 예를 들어 **모든 회사 사용자** 그룹에 디바이스 프로필을 할당하되 **Senior Management Staff** 그룹의 구성원을 모두 제외할 수 있습니다.

할당에서 그룹을 제외하는 경우 사용자만 제외하거나 디바이스 그룹만(그룹의 혼합 아님)만 제외하면 Intune은 사용자-디바이스 관계를 고려하지 않습니다. 디바이스 그룹을 제외하고 사용자 그룹을 포함하면 기대한 결과를 만들 수 없습니다. 그룹을 섞어서 사용하거나 다른 충돌이 있는 경우 포함이 제외보다 우선 적용됩니다.

예를 들어 키오스크 디바이스를 제외한 조직의 모든 디바이스에 디바이스 프로필을 할당하려고 합니다. **모든 사용자** 그룹을 포함하되 **모든 디바이스** 그룹을 제외합니다. 이 경우 사용자 디바이스가 **모든 디바이스** 그룹에 속하는 경우에도 모든 사용자와 해당 디바이스에 정책이 적용됩니다.

제외는 그룹의 직접 구성원만 해당하며 사용자와 연결된 디바이스는 포함하지 않습니다. 그러나 사용자가 없는 디바이스는 정책을 얻지 못합니다. 이는 이러한 디바이스가 **모든 사용자** 그룹과 아무 관계도 없기 때문에 발생합니다.

**모든 디바이스**를 포함하고 **모든 사용자**를 제외하면 모든 디바이스에 정책이 적용됩니다. 이 시나리오의 의도는 연결된 사용자가 있는 디바이스를 이 정책에서 제외하기 위한 것입니다. 하지만 제외는 직접적인 그룹 구성원만 비교하기 때문에 디바이스는 제외하지 않습니다.

## <a name="next-steps"></a>다음 단계
디바이스 프로필 할당을 모니터링하는 데 지침은 [디바이스 프로필을 모니터링하는 방법](device-profile-monitor.md)을 참조하세요.
