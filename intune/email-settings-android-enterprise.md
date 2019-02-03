---
title: Microsoft Intune의 Android Enterprise 이메일 설정 - Azure | Microsoft Docs
description: Exchange 서버를 사용하는 디바이스 구성 이메일 프로필을 만들고 Azure Active Directory에서 특성을 검색합니다. SSL 또는 SMIME을 사용하도록 설정하고, 인증서 또는 사용자 이름/암호를 인증하고, Microsoft Intune을 사용하여 Android 회사 프로필 디바이스에서 이메일 및 일정을 동기화합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.openlocfilehash: ff2732bb68d7e3f2199f392275d476374ee0c10c
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54832593"
---
# <a name="android-enterprise-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune에서 이메일, 인증 및 동기화를 구성하기 위한 Android Enterprise 디바이스 설정

이 문서에서는 Android Enterprise 디바이스에서 제어할 수 있는 다양한 이메일 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 메일 서버를 구성하고, SSL을 사용하여 메일을 암호화하는 등의 작업을 수행합니다.

Intune 관리자는 회사 프로필의 Android Enterprise 디바이스에 이메일 설정을 만들고 할당할 수 있습니다.

Intune의 이메일 프로필에 대한 자세한 내용은 [이메일 설정 구성](email-settings-configure.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만들고](email-settings-configure.md#create-a-device-profile), 회사 프로필을 선택합니다.

## <a name="android-enterprise"></a>Android Enterprise

- **메일 앱**: **Gmail** 또는 **Nine Work**를 선택합니다.
- **메일 서버**: Exchange 서버의 호스트 이름입니다. 예를 들어 다음과 같이 입력합니다. `outlook.office365.com`
- **AAD의 사용자 이름 특성**: 이 이름은 Intune이 Azure AD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 프로필에서 사용되는 사용자 이름을 동적으로 생성합니다. 옵션은 다음과 같습니다.

  - **사용자 계정 이름**: 이름(예: `user1` 또는 `user1@contoso.com`)을 가져옵니다.
  - **사용자 이름**: `user1`과 같은 이름만 가져옵니다.

- **AAD의 메일 주소 특성**: 이 이름은 Intune이 Azure AD에서 가져오는 이메일 특성입니다. Intune은 이 프로필에서 사용되는 이메일 주소를 동적으로 생성합니다. 옵션은 다음과 같습니다.
  - **사용자 계정 이름**:  `user1@contoso.com` 또는 `user1`과 같은 전체 사용자 계정 이름을 이메일 주소로 사용합니다.
  - **기본 SMTP 주소**: `user1@contoso.com`과 같은 기본 SMTP 주소를 사용하여 Exchange에 로그인합니다.

- **인증 방법**: 이메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서**를 선택합니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.
- **SSL**: 이메일을 보내고, 이메일을 받고, Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용하려면 **사용**을 선택합니다.
- **동기화할 메일 양**: 동기화할 이메일 시간을 선택합니다. 또는 **무제한**을 선택하여 사용 가능한 모든 이메일을 동기화합니다.
- **동기화할 콘텐츠 형식**(Nine Work만 해당): 디바이스에서 동기화할 데이터를 선택합니다. 옵션은 다음과 같습니다.
  - **연락처**: 최종 사용자가 연락처를 해당 디바이스에 동기화할 수 있도록 하려면 **사용**을 선택합니다.
  - **일정**: 최종 사용자가 일정을 해당 디바이스에 동기화할 수 있도록 하려면 **사용**을 선택합니다.
  - **작업**: 최종 사용자가 모든 작업을 해당 디바이스에 동기화할 수 있도록 하려면 **사용**을 선택합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android Samsung Knox](email-settings-android.md), [iOS](email-settings-ios.md), [Windows 10 이상](email-settings-windows-10.md) 및 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 디바이스용 이메일 프로필을 만들 수도 있습니다.