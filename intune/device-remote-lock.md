---
title: Microsoft Intune-Azure를 사용하여 장치 잠금 | Micrososft Docs
description: Microsoft Intune에서 원격 잠금 작업을 사용하여 PIN 또는 암호로 보호되는 장치를 잠급니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 45ab6434245c0dd412b2e9d23e394f72871a459a
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31829767"
---
# <a name="remotely-lock-devices-with-intune"></a>Intune을 사용하여 장치 원격 잠금

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**원격 잠금** 장치 작업을 수행하면 장치가 잠깁니다. 장치의 잠금을 해제하려면 장치 소유자가 암호를 입력해야 합니다. PIN 또는 암호 설정이 있는 장치를 원격으로 잠글 수 있습니다. PIN 또는 암호가 없는 장치를 원격으로 잠글 수 없습니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

**원격 잠금**은 다음 플랫폼에서 지원됩니다.

- Android
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 이상

**원격 잠금**은 다음에 지원되지 *않습니다*.
- Windows 10 Desktop

> [!NOTE]
> macOS 장치의 경우 6자리 복구 PIN을 설정합니다. 장치가 잠기면 **장치 개요**에는 다른 장치 작업이 전송될 때까지 PIN이 표시됩니다.

## <a name="remote-lock-a-device"></a>장치 원격 잠금

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
3. **장치** > **모든 장치**를 선택합니다.
4. 장치 목록에서 장치를 선택한 다음, **원격 잠금** 작업을 선택합니다.

## <a name="next-steps"></a>다음 단계

- 이 작업의 상태를 보려면 **Microsoft Intune** > **장치** > **장치 작업**을 선택합니다. 
- 장치를 관리할 수 있는 추가 작업은 [사용 가능한 작업](device-management.md)을 참조하세요.
