---
title: iOS 장치에 대한 Microsoft Intune 메일 설정
titleSuffix: ''
description: iOS를 실행하는 장치에서 이메일 설정을 구성하는 데 사용할 수 있는 Microsoft Intune 설정에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 5/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: fe791dce88878fdbde7c62e59452a53ac08ef06b
ms.sourcegitcommit: af0cc27b05bf0743f7d0970f5f3822f0aab346af
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190488"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-ios"></a>iOS를 실행하는 장치용 Microsoft Intune에서 이메일 프로필 설정 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 iOS를 실행하는 장치에 대해 구성할 수 있는 이메일 프로필 설정을 보여줍니다.

## <a name="email-settings"></a>전자 메일 설정

- **메일 서버** - Exchange Server의 호스트 이름입니다.
- **계정 이름** - 장치에서 사용자에게 표시되는 전자 메일 계정의 표시 이름입니다.
- **AAD의 사용자 이름 특성** - 이것은 이메일 프로필에 대한 사용자 이름을 생성하는 데 사용되는 Active Directory(AD) 또는 Azure AD의 특성입니다. **user1@contoso.com**와 같은 **기본 SMTP 주소** 또는 **user1**, **user1@contoso.com**와 같은 **사용자 계정 이름**을 선택합니다.
- **AAD의 메일 주소 특성** - 각 장치에서 사용자의 메일 주소가 생성되는 방식을 선택합니다. **기본 SMTP 주소**를 선택하여 Exchange에 로그인하는 기본 SMTP 주소를 사용하거나 **사용자 계정 이름**을 사용하여 메일 주소와 전체 사용자 이름을 사용합니다.
- **인증 방법** - 메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서** 중 하나를 선택합니다. **참고**: Azure Multi-factor Authentication은 지원되지 않습니다.
    - **인증서**를 선택한 경우 Exchange 연결을 인증하는 데 사용할 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.
- **SSL** - 메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **S/MIME** - S/MIME 서명을 사용하여 보내는 메일을 전송합니다.
    - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 PKCS 인증서 프로필을 선택합니다.
- **동기화할 메일 양** - 동기화할 메일의 일 수를 선택하거나, **무제한**을 선택하여 사용 가능한 모든 메일을 동기화합니다.
- **다른 메일 계정으로 메시지를 이동할 수 있음** - 사용자가 자신의 장치에 구성한 여러 계정 간에 메일 메시지를 이동할 수 있도록 허용합니다.
- **타사 응용 프로그램에서 메일을 전송할 수 있음** - 사용자는 이 프로필을 메일을 보내기 위한 기본 계정으로 선택하고, 타사에서는 네이티브 메일 앱의 메일을 열고 메일에 파일을 첨부할 수 있게 됩니다.
- **최근 사용된 메일 주소 동기화** - 이 기능을 통해 사용자는 장치에서 최근에 사용한 메일 주소 목록을 서버와 동기화할 수 있습니다.
