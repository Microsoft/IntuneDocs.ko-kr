---
title: Microsoft Intune-Azure에서 분실 iOS 디바이스 찾기 | Micrososft Docs
description: Microsoft Intune에서 디바이스 찾기 기능을 사용하여 분실하거나 도난당한 iOS 디바이스를 찾습니다. 디바이스 찾기 작업을 사용하는 경우 보안 및 개인 정보 취급 방침에 대한 세부 정보를 가져옵니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 08/24/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 3e544286-12ad-4a3a-86f8-d2cf16940b1f
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1128daf5f3a0cbc969bcae2ce060cd05ea29af84
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232117"
---
# <a name="locate-lost-or-stolen-ios-devices-with-intune"></a>Intune을 사용하여 분실했거나 도난당한 iOS 디바이스 찾기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

맵에서 분실하거나 도난당한 iOS 디바이스의 위치를 가져오려면 **디바이스 찾기** 작업을 사용합니다. 디바이스는 감독 모드 상태여야 합니다. 이 작업을 사용하기 전에 디바이스가 [분실 모드](device-lost-mode.md) 상태인지 확인합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- iOS 9.3 이상

다음 시스템에서는 이 기능이 지원되지 않습니다. 
- Windows
- Windows Phone
- macOS
- Android

## <a name="locate-a-lost-or-stolen-device"></a>분실되거나 도난당한 디바이스 찾기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **디바이스**를 선택한 다음, **모든 디바이스**를 선택합니다.
4. 관리하는 디바이스 목록에서 iOS 디바이스를 선택하고 **자세히...** 를 선택합니다. 그런 다음, **디바이스 찾기** 원격 작업을 선택합니다.
5. 디바이스를 찾으면 해당 위치가 **디바이스 찾기**에 표시됩니다.
    ![Azure에서 Intune을 사용하여 디바이스 찾기 스크린샷](./media/locate-device.png)

>[!NOTE]
>개인 정보 보호 차원에서 맵을 확대할 수 있는 거리가 반경 300미터로 제한됩니다.

## <a name="activate-lost-mode-sound-alert-on-an-ios-device"></a>iOS 디바이스에서 분실 모드 알림음 활성화

누군가 iOS 9.3 이상의 디바이스를 분실하는 경우 관리자는 디바이스를 원격으로 트리거하여 사용자가 찾을 수 있도록 알림음을 재생할 수 있습니다. 디바이스가 [분실 모드](device-lost-mode.md)에 있어야 합니다.

[Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스** > **모든 디바이스** &gt; iOS 디바이스 &gt; **개요** > **기타** > **분실 모드 소리 재생(감독 모드인 경우에만)** 을 선택합니다.

사용자가 디바이스에서 소리를 사용하지 않도록 설정하거나 디바이스가 분실 모드에서 제거될 때까지 소리가 계속 재생됩니다.


## <a name="security-and-privacy-information-for-lost-mode-and-locate-device-actions"></a>분실 모드의 보안 및 개인 정보와 디바이스 찾기 작업
- 이 작업을 켤 때까지 디바이스 위치 정보는 Intune에 전송되지 않습니다.
- 디바이스 찾기 작업을 사용하는 경우 Graph API를 사용하여 디바이스의 위도/경도 좌표를 검색할 수 있습니다.
- 데이터는 24시간 동안 저장되었다가 제거됩니다. 위치 데이터를 수동으로 제거할 수 없습니다.
- 위치 데이터는 저장된 동안 및 전송되는 동안 모두 암호화됩니다.
- 분실 모드를 구성할 때 잠금 화면에 표시되는 메시지를 사용자 지정할 수 있습니다. 이 메시지에서 디바이스를 찾는 사용자를 돕기 위해 분실된 디바이스를 반환하는 특정 세부 정보를 포함해야 합니다.

## <a name="next-steps"></a>다음 단계

디바이스 찾기를 설정한 상태를 보려면 **디바이스**를 열고 **디바이스 작업**을 선택합니다.
