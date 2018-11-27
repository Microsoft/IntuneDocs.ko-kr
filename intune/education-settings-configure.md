---
title: Windows 10용 Intune 교육 설정 구성
titleSuffix: Microsoft Intune
description: 관리하는 장치에서 Intune을 사용하여 Windows 10 교육 설정을 구성하는 방법을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 6f4de4bd-3dde-4a8d-8e22-46c5d06c3eea
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 120aca8dae457748fea322ce164aa663ffa7e748
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187381"
---
# <a name="how-to-configure-windows-10-education-settings-in-microsoft-intune"></a>Microsoft Intune에서 Windows 10 교육 설정을 구성하는 방법

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

교육 프로필을 사용하면 계정 세부 정보 및 테스트 URL을 포함하여 Windows 시험 응시(Windows Take a Test) 앱을 구성하는 세부 정보를 지정할 수 있습니다. 이 설정을 구성할 경우 지정한 테스트와 함께 시험 응시(Take a Test) 앱이 열립니다. 테스트가 완료될 때까지 장치에서 다른 앱을 실행할 수 없습니다.

테스트 앱 사용에 대한 세부 정보는 [Windows 10에서 테스트 수행](https://docs.microsoft.com/education/windows/take-tests-in-windows-10)을 참조하세요.

## <a name="create-a-device-profile-containing-education-profile-settings"></a>교육 프로필 설정을 포함하는 장치 프로필 만들기

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **장치 구성**을 선택합니다.
2. **관리** 섹션 아래의 **장치 구성** 창에서 **프로필**을 선택합니다.
3. 프로필 창에서 **프로필 만들기**를 선택합니다.
4. **프로필 만들기** 창에서 장치 제한 프로필에 대한 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 **Windows 10 이상**을 선택합니다.
6. **프로필 유형** 드롭다운 목록에서 선택 **교육 프로필**을 선택합니다. 
7. **설정 > 구성**을 선택한 다음, **시험 응시** 창에서 다음을 구성합니다.
    - **계정 유형** - 드롭 다운 필드에서 계정 유형을 선택합니다.
    - **계정 사용자 이름** - 시험 응시에 사용한 계정의 사용자 이름을 입력합니다. 이름은 도메인 계정, AAD(Azure Active Directory) 계정 또는 로컬 컴퓨터 계정일 수 있습니다.
    - **평가 URL** - 사용자가 수행해야 할 테스트의 URL을 제공합니다. 자세한 내용은 시험 응시 설명서를 참조하세요.
    - **화면 모니터링** - 사용자가 테스트를 수행하는 동안 화면 활동을 모니터링할 수 있는지 여부를 지정합니다.
    - **텍스트 제안** - 사용자가 테스트를 수행하는 동안 텍스트 제안을 허용하거나 차단합니다.
8. 작업이 완료되면 **프로필 만들기** 창으로 돌아가서 **만들기**를 누릅니다.

프로필이 만들어지고 프로필 목록 창에 표시됩니다.

## <a name="next-steps"></a>다음 단계

계속해서 이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.



