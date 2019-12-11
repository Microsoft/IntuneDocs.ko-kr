---
title: Windows Phone 8.1에 대한 Microsoft Intune 이메일 설정
titleSuffix: ''
description: Windows Phone 8.1을 실행하는 디바이스에서 이메일 연결을 구성하는 데 사용할 수 있는 Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 455d69328f8b70b1de73067c6290b6955df1e710
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72506755"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-windows-phone-81"></a>Windows Phone 8.1을 실행하는 디바이스용 Microsoft Intune에서 이메일 프로필 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 아티클에서는 Windows Phone 8.1을 실행하는 디바이스에 대해 구성할 수 있는 이메일 프로필 설정을 보여줍니다.


- **Windows Phone 8.1에만 모든 설정 적용** - Intune 클래식 포털에서 구성할 수 있는 설정입니다. Azure Portal에서는 이 설정을 변경할 수 없습니다. **구성됨**으로 설정된 경우 모든 설정이 Windows Phone 8.1 디바이스에만 적용됩니다. **구성되지 않음**으로 설정한 경우 Windows 10 Mobile 디바이스에도 이러한 설정이 적용됩니다.
- **메일 서버** - Exchange Server의 호스트 이름입니다.
- **계정 이름** - 디바이스에서 사용자에게 표시되는 전자 메일 계정의 표시 이름입니다.
- **AAD의 사용자 이름 특성** - 이것은 이메일 프로필에 대한 사용자 이름을 생성하는 데 사용되는 Active Directory(AD) 또는 Azure AD의 특성입니다. **user1@contoso.com** 와 같은 **기본 SMTP 주소** 또는 **user1**, **user1@contoso.com** 와 같은 **사용자 계정 이름**을 선택합니다.
- **AAD의 메일 주소 특성** - 각 디바이스에서 사용자의 메일 주소가 생성되는 방식을 선택합니다. **기본 SMTP 주소**를 선택하여 Exchange에 로그인하는 기본 SMTP 주소를 사용하거나 **사용자 계정 이름**을 사용하여 메일 주소와 전체 사용자 이름을 사용합니다.


## <a name="security-settings"></a>보안 설정

- **SSL** - 메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.



## <a name="synchronization-settings"></a>동기화 설정

- **동기화할 메일 양** - 동기화할 메일의 일 수를 선택하거나, **무제한**을 선택하여 사용 가능한 모든 메일을 동기화합니다.
- **동기화 일정** - 디바이스가 Exchange 서버의 데이터를 동기화하는 일정을 선택합니다. 데이터가 도착하는 즉시 동기화하는 **메시지가 도착할 때**를 선택하거나 또는 디바이스의 사용자가 동기화를 시작해야 하는 **수동**을 선택할 수도 있습니다.

## <a name="content-sync-settings"></a>콘텐츠 동기화 설정

- **동기화할 콘텐츠 형식** - 디바이스에 동기화할 콘텐츠 형식을 선택합니다.
  - **연락처**
  - **일정**
  - **태스크**
