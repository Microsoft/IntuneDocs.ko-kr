---
title: macOS 장치 지우기
titleSuffix: Microsoft Intune
description: macOS 장치에서 운영 체제를 비롯한 모든 데이터를 지우는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/31/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ab396092-907a-44b7-a157-aabee62176a9
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d99bef78d635f98f9c888d8096247f314ade6a52
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020931"
---
# <a name="erase-all-data-from-a-macos-device"></a>macOS 장치에서 모든 데이터 지우기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

운영 체제를 포함하여 macOS 장치에서 모든 데이터를 지울 수 있습니다. Intune 관리에서 장치도 제거됩니다. 최종 사용자에게 아무런 경고도 표시되지 않습니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치** > **모든 장치** 선택하고 > 지우려는 장치를 선택합니다.
![스크린샷](./media/device-erase/choosedevice.png)
2. **자세히** > **지우기**를 클릭하고 >**복구 PIN**에 6자리 숫자를 제공합니다. 이것은 사용자가 운영 체제를 장치에 재설치할 수 있도록 사용자에게 제공해야 하는 PIN입니다. 지우기 작업이 완료된 후에는 이 PIN이 보이지 않기 때문에 기록해두어야 합니다.
![스크린샷](./media/device-erase/providepin.png)
3. **확인**을 클릭하여 장치를 지웁니다.
