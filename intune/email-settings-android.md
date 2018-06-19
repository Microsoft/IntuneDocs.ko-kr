---
title: Android 및 Android for Work를 실행하는 장치에 대해 Microsoft Intune 이메일 설정
titleSuffix: ''
description: Android 및 Android for Work를 실행하는 장치에서 이메일 설정을 구성하는 데 사용할 수 있는 Microsoft Intune 설정에 대해 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d492e107fffe730d36c662b9187fc9c6faced907
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31832753"
---
# <a name="email-profile-settings-in-microsoft-intune-for-devices-running-android-and-android-for-work"></a>Android 및 Android for Work를 실행하는 장치에 대해 Microsoft Intune에서 이메일 프로필 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 Android를 실행하는 장치에 대해 구성할 수 있는 이메일 프로필 설정을 보여줍니다.

Intune 관리자는 다음 Android 장치에 대해 이메일 설정을 만들고 할당할 수 있습니다.
- [Android Samsung Knox Standard](#android-samsung-knox-standard-email-settings)
- [Android for Work](#android-for-work-email-settings)

## <a name="android-samsung-knox-standard-email-settings"></a>Android Samsung Knox Standard 메일 설정
- **메일 서버** - Exchange Server의 호스트 이름입니다.
- **계정 이름** - 장치에서 사용자에게 표시되는 전자 메일 계정의 표시 이름입니다.
- **AAD의 사용자 이름 특성** - 이 이름은 해당 전자 메일 프로필에 대해 사용자 이름을 생성하는 데 사용되는 AD(Active Directory) 또는 Azure AD의 특성입니다. user1@contoso.com와 같은 **기본 SMTP 주소** 또는 user1, user1@contoso.com와 같은 **사용자 계정 이름**을 선택합니다.
- **AAD의 메일 주소 특성** - 각 장치에서 사용자의 메일 주소가 생성되는 방식을 선택합니다. **기본 SMTP 주소**를 선택하여 Exchange에 로그인하는 기본 SMTP 주소를 사용하거나 **사용자 계정 이름**을 사용하여 전체 사용자 이름을 전자 메일 주소로 사용합니다.
- **인증 방법** - 메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서** 중 하나를 선택합니다.
    - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.

### <a name="security-settings"></a>보안 설정

- **SSL** - 메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **S/MIME** - S/MIME 암호화를 사용하여 보내는 메일을 전송합니다.
    - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.

### <a name="synchronization-settings"></a>동기화 설정

- **동기화할 메일 양** - 동기화할 메일의 일 수를 선택하거나, **무제한**을 선택하여 사용 가능한 모든 메일을 동기화합니다.
- **동기화 일정** - 장치가 Exchange 서버의 데이터를 동기화하는 일정을 선택합니다. 데이터가 도착하는 즉시 동기화하는 **메시지가 도착할 때**를 선택하거나 장치의 사용자가 동기화를 시작해야 하는 **수동**을 선택할 수도 있습니다.

### <a name="content-sync-settings"></a>콘텐츠 동기화 설정

- **동기화할 콘텐츠 형식** - 장치에 동기화할 콘텐츠 형식을 선택합니다.
    - **연락처**
    - **일정**
    - **태스크**

## <a name="android-for-work-email-settings"></a>Android for Work 전자 메일 설정

- **전자 메일 앱** - **Gmail** 또는 **Nine Work**를 선택합니다.
- **메일 서버** - Exchange Server의 호스트 이름입니다.
- **AAD의 사용자 이름 특성** - 이 이름은 해당 이메일 프로필에 대해 사용자 이름을 생성하는 데 사용되는 AD(Active Directory) 또는 Azure AD의 특성입니다. user1@contoso.com와 같은 **기본 SMTP 주소** 또는 user1, user1@contoso.com와 같은 **사용자 계정 이름**을 선택합니다.
- **AAD의 메일 주소 특성** - 각 장치에서 사용자의 메일 주소가 생성되는 방식을 선택합니다. 전체 사용자 이름을 전자 메일 주소 또는 **사용자 이름**으로 사용하려면 **사용자 계정 이름**을 선택합니다.
- **인증 방법** - 메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서** 중 하나를 선택합니다.
    - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.
- **SSL** - 메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **동기화할 메일 양** - 동기화할 메일의 일 수를 선택하거나, **무제한**을 선택하여 사용 가능한 모든 메일을 동기화합니다.
- **동기화할 콘텐츠 형식**(Nine Work에만 해당) - 장치에 동기화할 콘텐츠 형식을 선택합니다.
    - **연락처**
    - **일정**
    - **태스크**
