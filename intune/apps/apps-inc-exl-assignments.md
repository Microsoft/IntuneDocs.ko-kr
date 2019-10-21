---
title: Microsoft Intune에서 앱 할당 포함 및 제외
titleSuffix: ''
description: Microsoft Intune을 사용하여 앱 할당을 포함하거나 배제하는 방법에 대해 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: c59f6df5-3317-4dff-8f19-fdeec33faedf
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c743b25ce2823c952b1e4b8ab764a48488c0ca5d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71725103"
---
# <a name="include-and-exclude-app-assignments-in-microsoft-intune"></a>Microsoft Intune에서 앱 할당 포함 및 제외

Intune에서 포함 및 제외할 사용자 그룹을 할당하여 앱에 액세스할 수 있는 사용자를 결정할 수 있습니다. 앱에 그룹을 할당하기 전에 앱의 할당 유형을 설정해야 합니다. 할당 유형은 앱을 사용할 수 있게 만들고 필수 사항으로 만들거나 앱을 제거하기도 합니다. 

앱의 사용 가능성을 설정하려면 포함 및 제외 그룹 할당을 조합하여 앱 할당을 사용자 또는 디바이스 그룹에 포함 및 제외합니다. 이 기능은 큰 그룹을 포함시켜 앱을 사용할 수 있게 만든 다음, 작은 그룹을 제외하여 선택한 사용자의 범위를 좁힐 때 유용할 수 있습니다. 더 작은 그룹은 테스트 그룹 또는 경영진 그룹일 수 있습니다. 

앱 할당에서 그룹을 제외하는 경우 사용자 그룹만 또는 디바이스 그룹만 제외해야 합니다. 사용자 그룹과 디바이스 그룹을 섞어서 제외하면 안 됩니다. 

Intune은 그룹을 제외할 때 사용자와 디바이스 간의 연결을 고려하지 않습니다. 디바이스 그룹을 제외하고 사용자 그룹을 포함하면 필요한 결과를 얻을 가능성이 적습니다. 포함이 제외보다 우선 적용됩니다. 예를 들어, iOS 앱의 대상을 **모든 사용자**로 지정하고 **모든 iPad**를 제외하면 iPad를 사용하는 모든 사용자가 앱을 계속 얻을 수 있습니다. 그러나 iOS 앱의 대상을 **모든 디바이스**로 지정하고 **모든 iPad**를 제외하면 배포가 성공적으로 수행됩니다.  

> [!NOTE]
> 앱에 대한 그룹 할당을 설정할 때 **해당 사항 없음** 유형은 더 이상 사용되지 않으며 그룹 제외 기능으로 대체되었습니다. 
>
> Intune은 콘솔에서 미리 생성된 **모든 사용자** 및 **모든 디바이스** 그룹을 제공합니다. 그룹에는 편의를 위해 기본 제공 최적화가 포함됩니다. 이들 그룹을 사용하여 직접 만든 “모든 사용자” 또는 “모든 디바이스” 그룹 대신 모든 사용자와 모든 디바이스를 대상으로 지정하는 것이 좋습니다.  
>
> Android 엔터프라이즈는 그룹 포함 및 제외를 지원합니다. Android 엔터프라이즈 앱 할당을 위해 기본 제공된 **모든 사용자** 및 **모든 디바이스** 그룹을 활용할 수 있습니다. 


## <a name="include-and-exclude-groups-when-assigning-apps"></a>앱을 할당할 때 그룹 포함 및 제외 
포함 및 제외 할당을 사용하여 그룹에 앱을 할당하려면:
1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
4. **클라이언트 앱** 창에서 **앱**을 선택합니다. 추가된 앱 목록이 표시됩니다.
5. 할당하려는 앱을 선택합니다. 대시보드에는 앱에 대한 정보가 표시됩니다. 
6. 메뉴의 **관리** 섹션에서 **할당**을 선택합니다. 

    ![앱을 할당할 때 앱 할당 포함](./media/apps-inc-exl-assignments/apps-inc-exl-01.png)
7. **그룹 추가**를 선택하여 앱이 할당된 사용자 그룹을 추가합니다. 
8. **그룹 추가** 창의 사용 가능한 할당 유형에서 **할당 유형**을 선택합니다.
9. 할당 유형으로 **등록 유무에 상관없이 사용 가능**을 선택합니다.

    ![Intune 앱 할당 - 그룹 추가](./media/apps-inc-exl-assignments/apps-inc-exl-02.png)
10. **포함된 그룹**을 선택하여 이 앱을 사용할 수 있도록 하려는 사용자 그룹을 선택합니다.

    > [!NOTE]
    > 그룹을 추가할 때 특정 할당 유형에 이미 다른 그룹이 포함되어 있으면 해당 앱은 다른 포함 할당 유형에 대해 미리 선택되며 수정할 수 없습니다. 사용된 해당 그룹은 포함된 그룹으로 사용할 수 없습니다.

11. **예**를 선택하면 모든 사용자가 이 앱을 사용할 수 있습니다.

    ![Intune 앱 할당 - 그룹 포함](./media/apps-inc-exl-assignments/apps-inc-exl-03.png)
12. **확인**을 선택하여 포함할 그룹을 설정합니다.
13. **제외된 그룹**을 선택하여 이 앱을 사용할 수 없도록 하려는 사용자 그룹을 선택합니다. 
14. 제외할 그룹을 선택합니다. 이렇게 하면 해당 그룹에서 이 앱을 사용할 수 없습니다.

    ![Intune 앱 할당 - 그룹 제외](./media/apps-inc-exl-assignments/apps-inc-exl-04.png)
15. **선택**을 선택하여 그룹 선택을 완료합니다.
16. **그룹 추가** 창에서 **확인**을 선택합니다. 앱 **할당** 목록이 표시됩니다.
17. **저장**을 클릭하여 앱에 대한 그룹 할당을 활성화합니다.

그룹을 할당할 때 이미 할당된 그룹은 수정할 수 없습니다. 현재 사용할 수 없는 그룹을 선택하려면 먼저 앱의 할당 목록에서 해당 앱을 제거합니다. 

할당을 편집하려면, 앱의 **할당** 목록에서 변경하려는 특정 할당을 포함하는 행을 선택합니다. 또한 행 끝에 있는 줄임표( **...** )를 선택하고 **제거**를 선택하여 할당을 제거할 수 있습니다. **할당** 목록의 보기를 변경하려면 **할당 유형**별 또는 **포함/제외**별로 그룹화합니다.

![Intune 앱 할당 - 완료](./media/apps-inc-exl-assignments/apps-inc-exl-05.png)

## <a name="next-steps"></a>다음 단계

- 앱에 대한 그룹 할당의 포함 및 제외에 대한 자세한 내용은 [Microsoft Intune 블로그](https://aka.ms/new_app_assignment_process)를 참조하세요.
- [앱 정보 및 할당을 모니터링](apps-monitor.md)하는 방법을 알아보세요.