---
title: iOS용 Microsoft Intune 공유 디바이스 구성 설정
titlesuffix: ''
description: iOS 디바이스 잠금 화면에서 정보를 표시하는 데 사용할 수 있는 Microsoft Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/5/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 638b4b3ebc83917faae0d34ec407b8ad47b4a4fb
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183386"
---
# <a name="shared-device-configuration-settings-to-display-messages-on-the-ios-device-lock-screen"></a>iOS 디바이스 잠금 화면에 메시지를 표시하기 위한 공유 디바이스 구성 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클은 iOS 디바이스 잠금 화면에서 정보를 표시하는 데 사용할 수 있는 Microsoft Intune 설정을 설명합니다.

공유 디바이스 구성 설정을 사용하여 로그인 창 및 잠금 화면에 표시되는 선택적 텍스트를 지정할 수 있습니다. 예를 들어 "분실 시, 돌려주기" 메시지 및 자산 태그를 정보를 입력할 수 있습니다. 

>[!IMPORTANT]
> 이 기능은 iOS 9.3 이상을 실행하는 감독 모드 디바이스에서 지원됩니다.

## <a name="create-shared-device-settings"></a>공유 디바이스 설정 만들기

1. [Azure Portal의 Intune](https://portal.azure.com)에서 [**장치 구성 영역의 장치 기능**으로 이동합니다](device-features-configure.md). 
1. **장치 기능** 창에서 **공유 장치 구성(감독 모드에서만 해당)** 을 선택합니다.
2. **공유 장치 구성(감독 모드에서만 해당)** 창에서 다음 설정을 구성합니다.
    - **자산 태그 정보** - 장치의 자산 태그에 대한 정보를 입력합니다. 예를 들면 **Contoso Corp에서 소유함**입니다. 입력한 정보는 이 프로필을 할당하는 모든 디바이스에 적용됩니다.
    - **잠금 화면 각주** - 장치를 분실했거나 도난당한 경우 장치를 되찾는 데 도움이 되는 정보를 입력합니다. 예를 들어 **발견하는 경우 '번호'로 연락해주세요.** 라고 입력합니다.
3. 작업이 완료되면 **프로필 만들기** 창으로 돌아갈 때까지 **확인**을 선택한 다음, **만들기**를 선택합니다. 


## <a name="next-steps"></a>다음 단계

이제 선택한 그룹에 디바이스 프로필을 할당할 수 있습니다. 자세한 내용은 [디바이스 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.
