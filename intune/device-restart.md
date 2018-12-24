---
title: Microsoft Intune을 사용하여 디바이스 다시 시작 - Azure | Microsoft Docs
description: 다시 시작 원격 동작을 사용하는 Azure Portal에서 Microsoft Intune을 사용하여 Windows 및 iOS 디바이스를 다시 시작합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c707e0c4-391a-4bad-9dfd-9a7799c48dd5
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: aa16e180b016ec142ecca5644b7f93fb088d15f5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52184306"
---
# <a name="remotely-restart-devices-with-intune"></a>Intune을 사용하여 원격으로 디바이스 다시 시작


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**다시 시작** 장치 작업을 수행하면 선택한 장치가 다시 시작됩니다. 디바이스 소유자에게 다시 시작이 자동으로 알려지지 않고 작업을 손실할 수 있습니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- Windows - Windows 8.1 이상에서 지원됨
- Windows Phone - Windows Phone 8.1 이상에서 지원됨
- Android 키오스크 디바이스 - 지원됨
- iOS - 지원됨

    > [!Note]  
    > 이 명령은 감독되는 디바이스 및 **디바이스 잠금** 액세스 권한에 필요합니다. 디바이스를 즉시 다시 시작합니다. 암호로 잠긴 iOS 디바이스는 다시 시작한 후에 Wi-Fi 네트워크에 다시 연결되지 않습니다. 디바이스는 다시 시작한 후에 서버와 통신하지 못할 수 있습니다.
- macOS - 지원되지 않음
- Android 및 Android 작업 프로필 디바이스 - 지원되지 않음

## <a name="restart-a-device"></a>디바이스 다시 시작

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치** > **모든 장치**를 선택합니다.
4. 관리하는 디바이스 목록에서 디바이스를 선택하고 **자세히**를 선택한 다음, **다시 시작** 디바이스 원격 작업을 선택합니다.

## <a name="next-steps"></a>다음 단계

- **다시 시작** 장치 작업의 상태를 보려면 **장치** > **장치 작업**을 선택합니다.
