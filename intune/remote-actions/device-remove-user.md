---
title: Microsoft Intune을 사용하여 iOS 디바이스에서 사용자 제거
titleSuffix: ''
description: Intune을 사용하여 공유 iOS 디바이스에서 사용자를 제거하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 2ea5941c-a69b-4e1c-b42c-a1fc0c3a7de7
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 772cdbe203b0489a9b2312a1cc10ea1b3182b35d
ms.sourcegitcommit: 28622c5455adfbce25a404de4d0437fa2b5370be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713165"
---
# <a name="remove-a-user-from-a-shared-ios-device"></a>공유 iOS 디바이스에서 사용자 제거


[!INCLUDE [azure_portal](../includes/azure_portal.md)]

**사용자 제거** 작업은 공유 iPad 디바이스의 로컬 캐시에서 선택한 사용자를 삭제합니다. iPad 디바이스는 [iOS 교육 프로필](../fundamentals/education-settings-configure-ios.md)을 사용하여 iOS 클래스룸 앱을 관리하도록 설정되어야 합니다. 

## <a name="supported-platforms"></a>지원되는 플랫폼

- Windows - 지원되지 않음
- Windows Phone - 지원되지 않음
- iOS - iOS 9.3 및 이상에서 지원됨(공유 iPad 디바이스만 해당)
- macOS - 지원되지 않음
- Android - 지원되지 않음

## <a name="remove-a-user"></a>사용자 제거

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스** > **모든 디바이스**를 선택합니다.
3. 관리하는 디바이스 목록에서 iOS 디바이스를 선택합니다.
4. 디바이스에 대한 창에서 **사용자**를 선택합니다.
5. 목록에서 제거할 사용자를 마우스 오른쪽 단추로 클릭한 다음, **사용자 제거**를 선택합니다.

## <a name="next-steps"></a>다음 단계

- **사용자 제거** 작업의 상태를 보려면 **디바이스** > **디바이스 작업**을 선택합니다.
