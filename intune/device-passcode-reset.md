---
title: Microsoft Intune-Azure에서 장치 암호 다시 설정 | Micrososft Docs
description: Intune에서 관리하거나 모니터링하는 장치에서 암호 제거 작업을 사용하여 암호를 제거하거나 다시 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/29/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 47181d19-4049-4c7a-a8de-422206c4027e
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 81330083830eb2e3e1fe3e36217d403a77094a65
ms.sourcegitcommit: 8be5f29107d882c3ecf3dc0ce718a2423f91ce9a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/27/2018
ms.locfileid: "36964728"
---
# <a name="reset-or-remove-a-device-passcode-in-intune"></a>Intune에서 장치 암호 다시 설정 또는 제거

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

장치에 새 암호를 만들려면 **암호 제거** 작업을 사용합니다.

## <a name="supported-platforms"></a>지원되는 플랫폼

- 작업 프로필에 등록된 Android 장치 버전 8.0 이상
- 버전 6.0 이하의 Android 장치
- iOS 
     
## <a name="unsupported-platforms"></a>지원되지 않는 플랫폼

- 작업 프로필에 등록된 Android 장치 버전 7.0 이하
- 버전 7.0 이상의 Android 장치
- macOS
- Windows

## <a name="reset-a-passcode"></a>암호 재설정

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
3. **장치**를 선택한 다음, **모든 장치**를 선택합니다.
4. 관리하는 장치 목록에서 장치를 선택하고 **자세히...** 를 선택합니다. 그런 다음, **암호 제거** 장치 원격 작업을 선택합니다.

## <a name="resetting-android-for-work-passcodes"></a>Android for Work 암호 다시 설정

지원되는 Android for Work 장치는 최종 사용자에 대한 관리되는 새 프로필 잠금 해제 암호 또는 관리되는 프로필 질문을 수신합니다. 작업 프로필이 있는 Android 8.0 이상 장치의 경우 등록 완료된 후 즉시 재설정 암호 토큰을 활성화하려면 최종 사용자에게 알림이 제공됩니다. 작업 프로필 암호가 필요하고 설정된 경우 알림이 표시됩니다. 암호를 입력하면 알림은 해제됩니다.

## <a name="resetting-ios-passcodes"></a>iOS 암호 다시 설정

iOS 장치에서 암호가 제거됩니다. 준수 정책이 설정된 암호가 있는 경우 장치의 설정에서 새 암호를 설정하라는 메시지가 사용자에게 나타납니다. 

## <a name="next-steps"></a>다음 단계

방금 수행한 작업의 상태를 확인하려면 **장치**에서 **장치 작업**을 선택합니다.
