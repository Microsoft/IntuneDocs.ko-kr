---
title: Windows PC에 대한 사용자-장치 연결 관리
description: Intune에서 관리되는 Windows PC에 사용자를 연결하는 방법을 알아봅니다.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 53c99d63-c312-442a-8a71-de1b10fcd39b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 751355c34fc18cd9a1ededd498724d4652fc1368
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31013945"
---
# <a name="manage-user-device-linking-for-windows-pcs"></a>Windows PC에 대한 사용자-장치 연결 관리

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 항목의 정보는 Intune 소프트웨어 클라이언트를 사용하여 PC를 관리하는 Windows 데스크톱에만 적용됩니다. 

소프트웨어를 사용자에게 배포하려면 먼저 사용자를 PC에 연결해야 합니다. 여러 PC에 사용자를 연결할 수 있지만 각 PC는 한 사용자에게만 연결할 수 있습니다. 사용자는 회사 포털을 사용하여 Intune에 등록한 모든 PC에 자동으로 연결됩니다.

사용자를 PC에 연결하려면

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **그룹** &gt; **모든 장치**(또는 사용자에게 연결하려는 PC가 포함된 다른 그룹)를 선택합니다.

2. 사용자를 연결할 PC를 선택한 다음 **사용자 연결**을 선택합니다.

   **사용자 연결** 대화 상자에는 표시 이름과 함께 사용 가능한 사용자, 사용자 ID 및 각 사용자가 현재 연결되어 있는 PC 수의 목록이 표시됩니다. 사용자가 선택한 PC에 이미 연결되어 있는 경우 해당 사용자 이름과 사용자 ID가 **현재 사용자**에 표시됩니다. PC가 어떤 사용자에게도 연결되지 않은 경우 **현재 사용자**에 **사용자 없음**이 표시됩니다.

3. 다음 중 하나를 수행합니다.

   - 현재 사용자(있는 경우)에 연결되어 있는 PC를 그대로 두려면 **취소**를 선택합니다.

   - 현재 사용자에 대한 연결을 제거하려면(있는 경우) <strong>연결 제거** &gt; **확인</strong>을 선택합니다.

   - 새 사용자와 PC를 연결하려면 **모든 사용자** 목록에서 사용자를 선택합니다. 사용자 데이터가 올바른지 확인한 후 **확인**을 선택합니다.

> [!TIP]
> 최종 사용자가 PC에 자신을 연결하는 기능을 제한하려면 **Microsoft Intune 에이전트 설정** 정책에서 **Restrict users' ability to link themselves to PCs**(사용자와 PC를 연결하는 기능 제한) 옵션을 사용하도록 설정합니다.

### <a name="see-also"></a>참고 항목

[Intune 소프트웨어 클라이언트를 사용하는 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)