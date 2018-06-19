---
title: Windows Holographic에서 Windows Holographic for Business로 업그레이드
titleSuffix: Microsoft Intune
description: Windows Holographic을 실행하는 장치를 Windows Holographic for Business로 업그레이드하는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 08763aa527f24ff7b357603be5e3bd4da5083b45
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31830436"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Windows Holographic을 실행하는 장치를 Windows Holographic for Business로 업그레이드


Microsoft Intune으로 Windows Holographic를 실행하는 장치를 관리하려면 Windows Holographic에서 Windows Holographic for Business로 장치를 업그레이드해야 합니다. 업그레이드 작업을 수행하여 버전 업그레이드 프로필을 만들 수 있습니다. Microsoft HoloLens의 경우 Commercial Suite를 구입하여 업그레이드에 필요한 라이선스를 얻을 수 있습니다. 자세한 내용은 [Windows Holographic for Business 기능 잠금 해제](https://docs.microsoft.com/en-us/hololens/hololens-upgrade-enterprise)를 참조하세요.

## <a name="to-set-up-an-edition-upgrade-device-configuration-profile"></a>버전 업그레이드 장치 구성 프로파일을 설정하려면

1. [Azure Portal](https://portal.azure.com)에 관리자 계정으로 로그인합니다.


2.  **장치 구성**, **프로필**을 클릭한 다음, **+ 프로필 만들기**를 클릭합니다.

    ![프로필 만들기](media/Holographic-create-profile.png)

3.  **프로필 만들기** 창에서 프로필의 이름을 입력하고 플랫폼에 대해 **Windows 10 이상**을 선택하고 프로필 유형에 대해 **버전 업그레이드**를 선택합니다. **설정 구성**을 클릭합니다.

5. **버전 업그레이드** 창의 **업그레이드할 버전**에서 **Windows 10 Holographic for Business**을 선택합니다. **라이선스 파일**에서, 제공된 XML 라이선스 파일을 찾아 선택합니다.

    ![XML 파일 이름 입력](media/Holographic-edition-upgrade.png)
 
5.  **확인**을 클릭한 다음, **만들기**를 클릭하여 프로필을 만듭니다.


## <a name="deploy-the-edition-upgrade-policy"></a>버전 업그레이드 정책 배포

그 다음, 선택한 그룹 또는 장치에 버전 업그레이드 프로필을 할당합니다.

1. 이전 단계에서 만든 프로필에서 **할당**을 클릭합니다.

2. **할당** 페이지에서, 정책으로 포함 및 제외하려는 사용자 그룹 및 장치를 선택합니다.

![그룹 포함 및 제외](media/Holographic-groups.PNG)

이러한 사용자 또는 장치가 Intune에 등록되면 버전 업그레이드 프로필이 적용됩니다. 

## <a name="next-steps"></a>다음 단계

그룹에 대한 자세한 내용은 [그룹 시작하기](get-started-groups.md)를 참조하세요.


