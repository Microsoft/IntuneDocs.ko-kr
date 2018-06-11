---
title: Microsoft Intune에서 장치 프로필 확인 - Azure | Microsoft Docs
description: Microsoft Intune에서 장치 구성 프로필 세부 정보를 보고 관리하며, 프로필에 할당된 장치 수의 그래픽 차트를 보고, 프로필이 할당되거나 배포된 장치를 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9deaed87-fb4b-4689-ba88-067bc61686d7
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: bffb6832200379fca0221d8718afdebe06163980
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744791"
---
# <a name="monitor-device-profiles-in-microsoft-intune"></a>Microsoft Intune에서 장치 프로필 모니터링

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Intune에는 장치 구성 프로필을 모니터링하고 관리하는 데 도움이 되는 Azure Portal의 일부 기능이 포함되어 있습니다. 예를 들어, 프로필의 상태를 확인하고, 할당된 장치를 확인하고, 프로필 속성을 업데이트할 수 있습니다.

## <a name="view-existing-profiles"></a>기존 프로필 보기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성** > **프로필**을 선택합니다.

모든 기존 프로필이 나열되고 이러한 프로필은 플랫폼 정보 및 프로필이 장치에 할당되었는지 여부 등의 세부 정보를 포함합니다.

## <a name="view-details-on-a-profile"></a>프로필에 대한 세부 정보 보기

장치 프로필을 만든 후 Intune에서 그래픽 차트를 제공합니다. 이러한 차트에는 프로필이 장치에 성공적으로 할당되어 있는 상태 또는 프로필에 충돌이 표시되는지 여부 등의 프로필 상태가 표시됩니다.

1. 기존 프로필을 선택합니다. 예를 들어, macOS 프로필을 선택합니다.
2. **개요** 탭을 선택합니다.

    위쪽 그래픽 차트에는 특정 장치 프로필에 할당된 장치 수가 표시됩니다. 예를 들어, 구성 장치 프로필이 macOS 장치에 적용되는 경우 차트는 macOS 장치의 개수가 나열됩니다.

    또한 동일한 장치 프로필이 할당된 기타 플랫폼의 장치 수도 표시됩니다. 예를 들어, macOS 이외의 장치 수가 표시됩니다.

    ![장치 프로필에 할당된 장치 수 보기](./media/device-configuration-profile-graphical-chart.png)

    아래쪽 그래픽 차트에는 특정 장치 프로필에 할당된 사용자 수가 표시됩니다. 예를 들어 구성 장치 프로필이 macOS 사용자에게 적용되는 경우 차트에는 macOS 사용자 수가 나열됩니다.

3. 위쪽 그래픽 차트에서 원을 선택합니다. **장치 상태**가 열립니다.

    프로필에 할당된 장치가 나열되고 프로필이 성공적으로 배포되었는지 여부가 표시됩니다. 또한 특정 플랫폼(예: macOS)이 있는 장치만 나열됩니다.

    **장치 상태** 세부 정보를 닫습니다.

4. 아래쪽 그래픽 차트에서 원을 선택합니다. **사용자 상태**가 열립니다. 

    프로필에 할당된 사용자가 나열되고 프로필이 성공적으로 배포되었는지 여부가 표시됩니다. 또한 특정 플랫폼(예: macOS)이 있는 사용자만 나열됩니다.

    **사용자 상태** 세부 정보를 닫습니다.

5. **프로필** 목록으로 돌아가서 특정 프로필을 선택합니다. 또한 다음과 같은 기존 속성을 변경할 수도 있습니다.
  - **속성**: 이름을 변경하거나 기존 설정을 업데이트합니다.
  - **할당**: 정책을 적용해야 하는 장치를 포함하거나 제외합니다. **선택된 그룹**을 선택하여 특정 그룹을 선택합니다.
  - **장치 상태**: 프로필에 할당된 장치가 나열되고 프로필이 성공적으로 배포되었는지 여부가 표시됩니다. 특정 장치를 선택하여 설치된 앱을 비롯한 더 많은 세부 정보를 얻을 수 있습니다.
  - **사용자 상태**: 이 프로필의 영향을 받는 장치를 가진 사용자 이름 및 프로필이 성공적으로 배포되었는지 여부를 나열합니다. 특정 사용자를 선택하여 더 많은 세부 정보를 얻을 수 있습니다.
  - **설정별 상태**: 프로필 내의 개별 설정을 표시하여 출력을 필터링하고 설정이 성공적으로 적용되었는지 여부를 표시합니다.

## <a name="next-steps"></a>다음 단계
[사용자 및 장치 프로필 할당](device-profile-assign.md)  
[일반적인 문제와 장치 프로필을 사용한 해결](device-profile-troubleshoot.md)