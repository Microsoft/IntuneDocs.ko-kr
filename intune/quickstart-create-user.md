---
title: 빠른 시작 - Intune에서 사용자 만들기
description: 빠른 시작 - Intune에서 사용자를 만듭니다.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 10/30/2018
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.openlocfilehash: b5653c67766a3312cf7ce2872e8b0cd4301b0e8b
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52189498"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>빠른 시작: 사용자를 만들고 라이선스 할당

이 빠른 시작에서는 사용자를 만든 다음, 해당 사용자에게 라이선스를 할당합니다. Intune을 사용할 때 회사 데이터에 액세스할 수 있게 만들고 싶은 각 사용자가 사용자 계정을 갖고 있어야 합니다. 이후에 Intune 관리자는 액세스 제어를 관리하도록 이러한 사용자를 구성할 수 있습니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 [글로벌 관리자 또는 Intune 서비스 관리자](users-add.md#types-of-administrators)로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-a-user"></a>사용자 만들기

Intune 장치 관리에 등록하려면 사용자 계정이 있어야 합니다.

1. Intune에서 **사용자** > **모든 사용자** > **새 사용자**를 선택합니다.
![브라우저](media/quickstart-create-user/create-user.png)
2. **이름** 상자에 *Dewey Kellum*과 같은 이름을 입력합니다.
3. **사용자 이름** 상자에 Dewey@contoso.onmicrosoft.com과 같은 사용자 식별자를 입력합니다.

    > [!NOTE]
    > 사용자 지정 도메인 이름을 구성하지 않은 경우 Intune 구독(또는 [평가판](free-trial-sign-up.md#sign-up-for-a-microsoft-intune-free-trial))을 만드는 데 사용한 확인된 도메인 이름을 사용합니다. 

4. **암호 표시**를 선택하고, 테스트 장치에 로그인할 수 있도록 자동으로 생성된 암호를 기록해 둡니다.
5. **만들기**를 선택합니다.

## <a name="assign-a-license-to-the-user"></a>사용자에게 라이선스 할당

사용자를 만든 후에는 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)을 사용하여 해당 사용자에게 Intune 라이선스를 할당해야 합니다. 라이선스를 할당하지 않으면 사용자가 디바이스를 Intune에 등록할 수 없습니다. 

1. Intune에 로그인하는 데 사용한 것과 동일한 자격 증명으로 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)에 로그인합니다.
2. **사용자** > **활성 사용자**를 선택하고 방금 만든 사용자를 선택합니다.
3. **제품 라이선스** 옆에 있는 **편집**을 선택합니다.
4. **위치** 아래에서 사용자의 위치를 선택합니다.
5. Intune 라이선스(또는 Intune을 포함하는 다른 라이선스) 옆에 있는 **켜기**를 클릭합니다. 표시된 [제품 이름](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference)**은 Azure 관리에서 서비스 계획으로 사용됩니다. 

   > [!NOTE]
   > 이 설정은 이 사용자의 라이선스 중 하나를 사용합니다. 평가판 환경을 사용하는 경우 나중에 라이브 환경에서 실제 사용자에게 이 라이선스를 다시 할당합니다.
6. **저장** > **닫기**를 선택합니다.

이제 새롭게 활성화된 Intune 사용자가 **Intune** 라이선스를 사용하고 있다고 표시됩니다.

## <a name="clean-up-resources"></a>리소스 정리

이 사용자가 더 이상 필요하지 않으면 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)로 이동하여 사용자를 삭제하고, **사용자** > **활성 사용자** > *목록에서 사용자 선택* > **사용자 삭제** > **사용자 삭제** > **변경 내용 확인** > **닫기**를 선택할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 사용자를 만들고 해당 사용자에게 라이선스를 할당했습니다. Intune에 사용자를 추가하는 방법에 대한 자세한 내용은 [사용자 추가 및 Intune에 관리 권한 부여](users-add.md)를 참조하세요.

Intune 빠른 시작 시리즈를 계속하려면 아래의 다음 빠른 시작 단계를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: 사용자 관리를 위한 그룹 만들기](quickstart-create-group.md)
