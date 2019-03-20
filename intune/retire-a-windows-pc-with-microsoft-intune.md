---
title: Windows PC 사용 중지
titlesuffix: Microsoft Intune
description: Intune에서 관리되는 Windows PC를 사용 중지하는 방법을 알아봅니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: archived
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0bafdfd4d688ccbbd547c41e0495af19f0b691e4
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57461110"
---
# <a name="retire-a-windows-pc"></a>Windows PC 사용 중지

[!INCLUDE [classic-portal](includes/classic-portal.md)]

데스크톱에서 Intune 소프트웨어 클라이언트를 실행하여 PC로 관리하는 데스크톱 사용을 중지하려면 다음 단계를 따르세요. PC를 사용 중지하면 Intune 관리에서 PC가 제거됩니다. Intune에서 PC를 초기화하여 원래 공장 설정으로 되돌릴 수 없습니다.

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **그룹**&gt;**모든 디바이스**(또는 사용 중지하려는 PC가 포함된 다른 그룹)를 선택합니다.

2.  사용 중지하려는 디바이스를 선택한 후 **사용 중지/초기화**를 선택합니다.

PC를 Intune에 다시 등록하려면 [Microsoft Intune을 사용하여 Windows PC 클라이언트 설치](install-the-windows-pc-client-with-microsoft-intune.md)의 지침을 사용하여 PC에 소프트웨어 클라이언트를 다시 설치합니다.

PC에서 Intune에 연결할 수 없는 경우 **대시보드** 작업 영역에 메시지가 표시됩니다.

PC 사용 중지하는 경우:

-   PC가 Intune 관리 및 인벤토리에서 제거되며, PC와 연결된 라이선스를 다시 사용할 수 있습니다. 사용 중지/초기화는 Intune 소프트웨어 클라이언트를 제거하지만, PC에서 앱 또는 데이터는 제거하지 않습니다. 이처럼 PC를 사용 중지해도 PC에서 전체 초기화는 수행되지 않습니다.

-   또한 해당 상태가 Intune 콘솔에 더 이상 표시되지 않습니다.

-   Intune이 PC에서 소프트웨어 클라이언트를 제거합니다. PC가 Intune 서비스에 연결되어 있지 않은 경우 다음번에 서비스에 연결할 때 소프트웨어 클라이언트가 제거됩니다.

-   Microsoft Intune Endpoint Protection이 PC에서 제거됩니다. PC에 다른 엔드포인트 앱이 설치되어 있지만 사용되지 않도록 설정된 경우, Microsoft Intune Endpoint Protection을 제거하면 이 애플리케이션이 다시 사용되도록 설정되어 PC가 보호될 수 있습니다.

-   PC에서 정책을 제거하면 해당 정책으로 설정된 값이 변경됩니다.

-   PC는 Intune 서비스로부터 소프트웨어 업데이트나 맬웨어 정의 업데이트를 더 이상 받지 않습니다.

-   구성 방법에 따라 사용 중지된 PC도 Windows Server Update Services, Windows 업데이트 또는 Microsoft 업데이트를 사용하여 업데이트를 수신할 수 있습니다.

    > [!IMPORTANT]
    > GPO(그룹 정책 개체)를 사용하여 클라이언트 소프트웨어를 설치한 경우 해당 클라이언트 소프트웨어를 제거하려면 먼저 해당 GPO(그룹 정책 개체)를 제거해야 소프트웨어가 다시 설치되는 것을 방지할 수 있습니다.

    Endpoint Protection 클라이언트를 제거하지 못한 경우 자세한 내용은 [Endpoint Protection 문제 해결](/intune/troubleshoot-endpoint-protection-in-microsoft-intune)을 참조하세요.

### <a name="see-also"></a>참고 항목

[Intune 소프트웨어 클라이언트를 사용하는 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
