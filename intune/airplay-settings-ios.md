---
title: iOS 디바이스에 대한 Intune AirPlay 설정
titlesuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 AirPlay 호환 디바이스에 iOS 디바이스를 자동으로 연결하는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 712a79fb-14ef-4f6b-aba5-1dfca900afd2
ms.reviewer: karanda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: efeb7895bcd83883e7fcaaca93c3d19d19a0bb5c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184134"
---
# <a name="intune-airplay-settings-for-ios-devices"></a>iOS 디바이스에 대한 Intune AirPlay 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이러한 설정을 사용하여 네트워크에서 AirPlay 호환 디바이스(예: Apple TV)에 관리하는 iOS 디바이스를 연결할 수 있습니다.
이 기능을 사용하여 다음을 수행할 수 있습니다.

- **장치 및 암호 목록 구성** - 사용자가 범위 내에 있는 AirPlay 장치에 자동으로 연결할 수 있습니다. 사용자가 연결할 때 별도로 입력하지 않아도 되도록 AirPlay 디바이스의 이름과 암호를 제공하세요.
- **허용된 대상 구성** - AirPlay 장치 목록을 장치 ID를 기준으로 구성합니다. 최종 사용자는 나열한 디바이스만 보고 연결할 수 있습니다(감독된 디바이스에만 해당).

## <a name="get-started"></a>시작

1. [Azure Portal의 Intune](https://portal.azure.com)에서 [**장치 구성 영역의 장치 기능**으로 이동합니다](device-features-configure.md). 
1. **장치 기능** 창에서 **AirPlay**를 선택합니다.
2. **AirPlay** 창에서 다음 작업 중 하나 또는 모두를 선택합니다.

## <a name="configure-a-device-and-password-list"></a>디바이스 및 암호 목록 구성

1. **암호** 창에서 AirPlay 장치의 **장치 이름** 및 **암호**를 입력합니다(예: **Contoso Apple TV**).
2. 디바이스 세부 정보를 입력한 후 **추가**를 클릭합니다. **장치 이름** 목록에 해당 장치가 표시됩니다.
3. 디바이스를 계속 추가합니다. 작업이 끝나면 **확인**을 선택합니다.


## <a name="configure-allowed-destinations"></a>허용된 대상 구성

1. **허용된 대상(감독 모드에서만 해당)** 창에서 AirPlay 장치의 **장치 ID**를 입력합니다(예: 52:46:CD:51:83:4C).
2. 디바이스 ID를 입력한 후 **추가**를 클릭합니다. **장치 ID** 목록에 해당 ID가 표시됩니다.
3. 디바이스를 계속 추가합니다. 작업이 끝나면 **확인**을 선택합니다.

디바이스 및 암호, 그리고 허용된 대상을 쉼표로 구분된 값(csv) 파일로 가져올 수도 있습니다.


## <a name="next-steps"></a>다음 단계

이제 선택한 그룹에 디바이스 프로필을 할당할 수 있습니다. 자세한 내용은 [디바이스 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.

