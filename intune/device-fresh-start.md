---
title: Microsoft Intune-Azure를 사용한 Windows 10 장치 다시 설정 | Microsoft Docs
description: Microsoft Intune을 사용하여 Windows 10 PC에서 앱을 제거하기 위해 새로 시작을 사용합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5aa5cfa3-c483-4099-b40f-578ff8dca425
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 5658bf2e1ee250ef9fd405b3f7ec1772b166f338
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31020999"
---
# <a name="use-fresh-start-to-reset-windows-10-devices-with-intune"></a>Intune을 통해 새로 시작 기능을 사용하여 Windows 10 장치 다시 설정


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

**새로 시작** 장치 작업은 크리에이터스 업데이트를 실행하는 Windows 10 PC에 설치된 모든 앱을 제거합니다. 그런 다음, PC를 최신 버전의 Windows로 자동으로 업데이트합니다.

이 작업을 통해 새로운 PC에서 일반적으로 설치된 사전 설치된(OEM) 앱을 제거할 수 있습니다. 사용자의 홈 폴더의 콘텐츠를 유지하고 앱 및 설정을 제거하려면 `if user data is retained` 설정을 사용합니다.

> [!IMPORTANT]
> 새로 시작은 Intune에서 장치 등록을 취소하지만 장치가 Azure Active Directory에 계속 가입됩니다.

## <a name="use-fresh-start"></a>새로 시작 사용

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치**를 선택한 다음, **모든 장치**를 선택합니다.
4. 관리하는 장치 목록에서 Windows 10 데스크톱 장치를 선택한 다음, **새로 시작**을 선택합니다.

## <a name="next-steps"></a>다음 단계

이 작업의 상태를 보려면 **장치 작업**(**Microsoft Intune** > **장치**)을 선택합니다.