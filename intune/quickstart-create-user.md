---
title: 빠른 시작 - Intune에서 사용자 만들기
description: 빠른 시작 - Intune에서 사용자를 만듭니다.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 6a1d591e635dccd99551d9b8d40e099724a85d77
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581677"
---
# <a name="quickstart-create-a-user-and-assign-a-license-to-it"></a>빠른 시작: 사용자를 만들고 라이선스 할당

이 빠른 시작에서는 사용자를 만들고 라이선스를 할당합니다. Intune을 사용할 때 회사 데이터에 액세스할 수 있게 만들고 싶은 각 사용자가 사용자 계정을 갖고 있어야 합니다. 그 후 Intune 관리자는 이러한 사용자를 구성하여 액세스 제어를 관리할 수 있습니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.

## <a name="create-a-user"></a>사용자 만들기

사람들이 Intune 장치 관리에 등록하려면 사용자 계정이 있어야 합니다.

1. Intune에서 **사용자** > **모든 사용자** > **새 사용자**를 선택합니다.
![브라우저](media/quickstart-create-user/create-user.png)
2. **이름** 상자에 *Dewey Kellum*을 입력합니다.
3. **사용자 이름** 상자에 *Dewey@contoso.onmicrosoft.com*을 입력합니다.
4. **그룹** > **모든 사용자** > **선택**을 누릅니다.
5. **암호 표시**를 선택하고, 테스트 장치에 로그인할 수 있도록 자동으로 생성된 암호를 기록해 둡니다.
6. **만들기**를 선택합니다.

## <a name="assign-a-license-to-the-user"></a>사용자에게 라이선스 할당

사용자를 만든 후에는 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)을 사용하여 해당 사용자에게 Intune 라이선스를 할당해야 합니다. 라이선스를 할당하지 않으면 사용자가 장치를 Intune에 등록할 수 없습니다. 

1. Intune에 로그인하는 데 사용한 것과 동일한 자격 증명으로 [Office 365 포털](http://go.microsoft.com/fwlink/p/?LinkId=698854)에 로그인합니다.
2. **사용자** > **활성 사용자**를 선택하고 방금 만든 사용자를 선택합니다.
3. **위치** 아래에서 사용자의 위치를 선택합니다.
3. **제품 라이선스**를 선택하고 **Enterprise Mobility + Security E3**(또는 Intune을 포함하는 다른 라이선스)를 **켜기**로 설정합니다.
   > [!NOTE]
   > 그러면 라이선스 중 하나가 이 사용자에 사용됩니다. 라이브 환경을 사용하는 경우 나중에 실제 사용자에게 다시 할당하기 위해 이 라이선스 사용을 해제할 수 있습니다.
5. **저장**을 선택합니다.

## <a name="clean-up-resources"></a>리소스 정리

이 사용자가 더 이상 필요 없으면 **사용자** > **모든 사용자**를 선택하고 목록에서 사용자를 선택한 다음, **사용자 삭제** > **예**를 선택하여 삭제할 수 있습니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 사용자를 만들고 라이선스를 할당했습니다. 이제 해당 사용자를 그룹에 할당할 수 있습니다.

> [!div class="nextstepaction"]
> [그룹 만들기](quickstart-create-group.md)
