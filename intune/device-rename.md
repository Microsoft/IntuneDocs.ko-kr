---
title: Microsoft Intune을 사용하여 Windows 디바이스 이름 바꾸기 - Azure | Microsoft Docs
description: Microsoft Intune을 사용하여 Windows 디바이스 이름을 바꿉니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8dfdc3641d583fc045346034ee8543feff1e7cbf
ms.sourcegitcommit: 1144247aa7f042eb1b99d8fd8dd17b909eae38c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2019
ms.locfileid: "59567103"
---
# <a name="rename-a-windows-device-in-intune"></a>Intune에서 Windows 디바이스 이름 바꾸기


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**디바이스 이름 바꾸기** 작업을 통해 Intune에 등록된 회사 소유 Windows 디바이스의 이름을 바꿀 수 있습니다. 디바이스 이름은 Intune 및 디바이스에서 변경됩니다. 

이 기능은 현재 하이브리드 Azure AD Windows 디바이스의 이름 바꾸기를 지원하지 않습니다.

## <a name="rename-a-device"></a>디바이스 이름 바꾸기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **디바이스** > **모든 디바이스**를 선택한 후 Windows 디바이스 > **기타** > **디바이스 이름 바꾸기**를 선택합니다.
4. **디바이스 이름 바꾸기** 블레이드에서 텍스트 상자에 새 이름을 입력합니다. 문자, 숫자 및 하이픈을 사용할 수 있습니다. 이름은 하나 이상의 문자 또는 하이픈을 포함해야 합니다.
5. 이름을 바꾼 후 디바이스를 다시 시작하려면 **이름을 바꾼 후 다시 시작** 옆에 있는 **예**를 선택합니다.
6. **이름 바꾸기**를 선택합니다.



## <a name="next-steps"></a>다음 단계

디바이스 **이름 바꾸기** 작업의 상태를 확인하려면 디바이스의 **개요** 페이지를 확인합니다.
