---
title: Microsoft Intune에서 Windows 10 디바이스에 대한 이메일 설정 - Azure | Microsoft Docs
description: Exchange 서버를 사용하여 디바이스 구성 이메일 프로필을 만들고 Azure Active Directory에서 특성을 검색합니다. 또한 SSL을 사용하도록 설정하고 Microsoft Intune을 사용하여 Windows 10 디바이스에서 이메일 및 일정을 동기화할 수도 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/29/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e2b3708b6b0c75a1384a7cdbdb524dff3f0627d
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565437"
---
# <a name="email-profile-settings-for-devices-running-windows-10---intune"></a>Windows 10을 실행하는 디바이스의 이메일 설정 - Intune

이메일 프로필 설정을 사용하여 Windows 10을 실행하는 디바이스에서 메일 앱을 구성합니다.

- **이메일 서버**: Exchange 서버의 호스트 이름을 입력합니다.
- **계정 이름**: 이메일 계정의 표시 이름을 입력합니다. 이 이름은 해당 디바이스에서 사용자에게 표시됩니다.
- **AAD의 사용자 이름 특성**: 이 이름은 Intune이 AAD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 프로필에서 사용되는 사용자 이름을 동적으로 생성합니다. 옵션은 다음과 같습니다.
  - **사용자 계정 이름**: `user1` 또는 `user1@contoso.com`과 같은 이름을 가져옵니다.
  - **기본 SMTP 주소**: `user1@contoso.com`과 같은 이메일 주소 형식의 이름을 가져옵니다.
  - **sAM 계정 이름**: `domain\user1`과 같은 도메인이 필요합니다.

    또한 다음을 입력합니다.  
    - **사용자 도메인 이름 원본**: **AAD**(Azure Active Directory) 또는 **사용자 지정**을 선택합니다.

      **AAD**에서 특성을 가져오도록 선택할 때 다음을 입력합니다.
      - **AAD의 사용자 도메인 이름 특성**: 사용자의 **전체 도메인 이름** 또는 **NetBIOS 이름** 특성을 가져오도록 선택

      **사용자 지정** 특성을 사용하도록 선택할 때 다음을 입력합니다.
      - **사용할 사용자 지정 도메인 이름**: Intune이 도메인 이름(예: `contoso.com` 또는 `contoso`)에 사용하는 값을 입력합니다.

- **AAD의 이메일 주소 특성**: 사용자의 이메일 주소가 생성되는 방식을 선택합니다. **사용자 계정 이름**(`user1@contoso.com` 또는 `user1`)을 선택하여 전체 계정 이름을 이메일 주소로 사용하거나, **기본 SMTP 주소**(`user1@contoso.com`)를 사용하여 Exchange에 로그인합니다.

## <a name="security-settings"></a>보안 설정

- **SSL**: 이메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.

## <a name="synchronization-settings"></a>동기화 설정

- **동기화할 이메일 양**: 동기화할 이메일의 일 수를 선택합니다. 또는 **무제한**을 선택하여 사용 가능한 모든 이메일을 동기화합니다.
- **동기화 일정**: Exchange 서버에서 데이터를 동기화할 디바이스의 일정을 선택합니다. 데이터가 도착하는 즉시 동기화하는 **메시지가 도착할 때**를 선택하거나 또는 디바이스의 사용자가 동기화를 시작해야 하는 **수동**을 선택할 수도 있습니다.

## <a name="content-sync-settings"></a>콘텐츠 동기화 설정

- **동기화할 콘텐츠 형식**: 디바이스에 동기화할 콘텐츠 형식을 선택합니다.
  - **연락처**
  - **일정**
  - **태스크**

## <a name="next-steps"></a>다음 단계
[Intune에서 이메일 설정 구성](email-settings-configure.md)
