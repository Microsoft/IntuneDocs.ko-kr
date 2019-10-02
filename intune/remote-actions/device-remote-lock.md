---
title: Microsoft Intune-Azure를 사용하여 디바이스 잠금 | Micrososft Docs
description: Microsoft Intune에서 원격 잠금 작업을 사용하여 PIN 또는 암호로 보호되는 디바이스를 잠급니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/07/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b67f285-229d-4a0f-ae34-0402a20b4518
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8637e5333ae96fcaf69cb772bcce23193f85ae50
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728561"
---
# <a name="remotely-lock-devices-with-intune"></a>Intune을 사용하여 디바이스 원격 잠금

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**원격 잠금** 디바이스 작업을 수행하면 디바이스가 잠깁니다. 디바이스의 잠금을 해제하려면 디바이스 소유자가 암호를 입력해야 합니다. PIN 또는 암호 설정이 있는 디바이스를 원격으로 잠글 수 있습니다. PIN 또는 암호가 없는 디바이스를 원격으로 잠글 수 없습니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

**원격 잠금**은 다음 플랫폼에서 지원됩니다.

- Android
- Android 엔터프라이즈 키오스크 디바이스
- Android 엔터프라이즈 회사 프로필 디바이스
- iOS
- macOS
- Windows 10 Mobile
- Windows Phone 8.1 이상

**원격 잠금**은 다음에 지원되지 않습니다.
- Windows 10 Desktop

> [!NOTE]
> macOS 디바이스의 경우 6자리 복구 PIN을 설정합니다. 디바이스가 잠기면 **디바이스 개요**에는 다른 디바이스 작업이 전송될 때까지 PIN이 표시됩니다.

## <a name="remote-lock-a-device"></a>디바이스 원격 잠금

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **디바이스** > **모든 디바이스**를 선택합니다.
4. 디바이스 목록에서 디바이스를 선택한 다음, **원격 잠금** 작업을 선택합니다.

## <a name="next-steps"></a>다음 단계

- 이 작업의 상태를 보려면 **Microsoft Intune** > **디바이스** > **디바이스 작업**을 선택합니다. 
- 디바이스를 관리할 수 있는 추가 작업은 [사용 가능한 작업](device-management.md)을 참조하세요.
