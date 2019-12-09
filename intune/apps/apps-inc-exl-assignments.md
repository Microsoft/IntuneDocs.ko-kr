---
title: Microsoft Intune에서 앱 할당 포함 및 제외
titleSuffix: ''
description: Microsoft Intune을 사용하여 앱 할당을 포함하거나 배제하는 방법에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40cbb62a620d6e174ab8acb76798ba53080b78cf
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563972"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Microsoft Intune에서 앱 할당 포함 및 제외

Intune에서 포함 및 제외할 사용자 그룹을 할당하여 앱에 액세스할 수 있는 사용자를 결정할 수 있습니다. 앱에 그룹을 할당하기 전에 앱의 할당 유형을 설정해야 합니다. 할당 유형은 앱을 사용할 수 있게 만들고 필수 사항으로 만들거나 앱을 제거하기도 합니다. 

앱의 사용 가능성을 설정하려면 포함 및 제외 그룹 할당을 조합하여 앱 할당을 사용자 또는 디바이스 그룹에 포함 및 제외합니다. 이 기능은 큰 그룹을 포함시켜 앱을 사용할 수 있게 만든 다음, 작은 그룹을 제외하여 선택한 사용자의 범위를 좁힐 때 유용할 수 있습니다. 더 작은 그룹은 테스트 그룹 또는 경영진 그룹일 수 있습니다. 

모범 사례로, 사용자 그룹에 맞는 앱을 특수하게 만들어 할당하고, 디바이스 그룹에 대해서는 별도로 앱을 만들어 할당합니다. 그룹에 대한 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](~/fundamentals/groups-add.md)을 참조하세요.  

앱 할당을 포함하거나 제외하는 경우 다음과 같은 중요한 시나리오가 적용됩니다.

- 다음과 같이 동일한 그룹 유형 시나리오에서는 제외가 포함보다 우선하게 됩니다.
    - 앱을 할당할 때 사용자 그룹 포함 및 제외
    - 앱을 할당할 때 디바이스 그룹 포함 및 제외

    예를 들어, **모든 회사 사용자** 사용자 그룹에 디바이스 그룹을 할당하지만 **선임 관리 직원** 사용자 그룹의 멤버를 제외하는 경우 **선임 관리 담당자**를 제외한 **모든 회사 사용자**가 할당을 받게 됩니다. 두 그룹이 모두 사용자 그룹이기 때문입니다.
- Intune은 사용자-디바이스 그룹 관계를 평가하지 않습니다. 혼합 그룹에 앱을 할당하는 경우, 결과는 원하는 대로 표시되지 않을 수 있습니다.

    예를 들어 **모든 사용자** 사용자 그룹에 디바이스 그룹을 할당하되 **모든 개인 디바이스** 디바이스 프로필은 제외한다고 가정해 보겠습니다. 이 혼합 그룹 앱 할당에서 **모든 사용자**가 앱을 가져옵니다. 제외는 적용되지 않습니다.

따라서 혼합 그룹에 앱을 할당하지 않는 것이 좋습니다.

> [!NOTE]
> 앱에 대한 그룹 할당을 설정할 때 **해당 사항 없음** 유형은 더 이상 사용되지 않으며 그룹 제외 기능으로 대체되었습니다. 
>
> Intune은 콘솔에서 미리 생성된 **모든 사용자** 및 **모든 디바이스** 그룹을 제공합니다. 그룹에는 편의를 위해 기본 제공 최적화가 포함됩니다. 이들 그룹을 사용하여 직접 만든 “모든 사용자” 또는 “모든 디바이스” 그룹 대신 모든 사용자와 모든 디바이스를 대상으로 지정하는 것이 좋습니다.  
>
> Android 엔터프라이즈는 그룹 포함 및 제외를 지원합니다. Android 엔터프라이즈 앱 할당을 위해 기본 제공된 **모든 사용자** 및 **모든 디바이스** 그룹을 활용할 수 있습니다. 

## <a name="include-and-exclude-groups-when-assigning-apps"></a>앱을 할당할 때 그룹 포함 및 제외 
포함 및 제외 할당을 사용하여 그룹에 앱을 할당하려면:
1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱**을 선택합니다. 추가된 앱 목록이 표시됩니다.
3. 할당하려는 앱을 선택합니다. 대시보드에는 앱에 대한 정보가 표시됩니다. 
4. 메뉴의 **관리** 섹션에서 **할당**을 선택합니다. 

    ![앱을 할당할 때 앱 할당 포함](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)

5. **그룹 추가**를 선택하여 앱이 할당된 사용자 그룹을 추가합니다. 
6. **그룹 추가** 창의 사용 가능한 할당 유형에서 **할당 유형**을 선택합니다.
7. 할당 유형으로 **등록 유무에 상관없이 사용 가능**을 선택합니다.

    ![Intune 앱 할당 - 그룹 추가](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
8. **포함된 그룹**을 선택하여 이 앱을 사용할 수 있도록 하려는 사용자 그룹을 선택합니다.

    > [!NOTE]
    > 그룹을 추가할 때 특정 할당 유형에 이미 다른 그룹이 포함되어 있으면 해당 앱은 다른 포함 할당 유형에 대해 미리 선택되며 수정할 수 없습니다. 사용된 해당 그룹은 포함된 그룹으로 사용할 수 없습니다.

9. **예**를 선택하면 모든 사용자가 이 앱을 사용할 수 있습니다.

    ![Intune 앱 할당 - 그룹 포함](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
10. **확인**을 선택하여 포함할 그룹을 설정합니다.
11. **제외된 그룹**을 선택하여 이 앱을 사용할 수 없도록 하려는 사용자 그룹을 선택합니다. 
12. 제외할 그룹을 선택합니다. 이렇게 하면 해당 그룹에서 이 앱을 사용할 수 없습니다.

    ![Intune 앱 할당 - 그룹 제외](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
13. **선택**을 선택하여 그룹 선택을 완료합니다.
14. **그룹 추가** 창에서 **확인**을 선택합니다. 앱 **할당** 목록이 표시됩니다.
15. **저장**을 클릭하여 앱에 대한 그룹 할당을 활성화합니다.

그룹을 할당할 때 이미 할당된 그룹은 수정할 수 없습니다. 현재 사용할 수 없는 그룹을 선택하려면 먼저 앱의 할당 목록에서 해당 앱을 제거합니다. 

할당을 편집하려면, 앱의 **할당** 목록에서 변경하려는 특정 할당을 포함하는 행을 선택합니다. 또한 행 끝에 있는 줄임표( **...** )를 선택하고 **제거**를 선택하여 할당을 제거할 수 있습니다. **할당** 목록의 보기를 변경하려면 **할당 유형**별 또는 **포함/제외**별로 그룹화합니다.

![Intune 앱 할당 - 완료](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>다음 단계

- 앱에 대한 그룹 할당의 포함 및 제외에 대한 자세한 내용은 [Microsoft Intune 블로그](https://aka.ms/new_app_assignment_process)를 참조하세요.
- [앱 정보 및 할당을 모니터링](apps-monitor.md)하는 방법을 알아보세요.
