---
title: Microsoft Intune의 Android 이메일 설정 - Azure | Microsoft Docs
description: Exchange 서버를 사용하는 디바이스 구성 메일 프로필을 만들고 Azure Active Directory에서 특성을 검색합니다. SSL 또는 SMIME을 사용하도록 설정하고, 인증서 또는 사용자 이름/암호를 인증하고, Microsoft Intune을 사용하여 Android 및 Android Samsung Knox 디바이스에서 이메일 및 일정을 동기화합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/15/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 53f1c95fdbdd9d779fb339e4820a3e7000573e60
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57236929"
---
# <a name="android-device-settings-to-configure-email-authentication-and-synchronization-in-intune"></a>Intune에서 이메일, 인증 및 동기화를 구성하기 위한 Android 디바이스 설정

이 문서에서는 Intune의 Android Samsung Knox 디바이스에서 제어할 수 있는 다양한 이메일 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 메일 서버를 구성하고, SSL을 사용하여 메일을 암호화하는 등의 작업을 수행합니다.

Intune 관리자는 Android Samsung Knox Standard 디바이스에 이메일 설정을 만들고 할당할 수 있습니다.

Intune의 이메일 프로필에 대한 자세한 내용은 [이메일 설정 구성](email-settings-configure.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](email-settings-configure.md#create-a-device-profile).

## <a name="android-samsung-knox"></a>Android(Samsung Knox)

- **메일 서버**: Exchange 서버의 호스트 이름을 입력합니다. 예를 들어 다음과 같이 입력합니다. `outlook.office365.com`
- **계정 이름**: 메일 계정의 표시 이름을 입력합니다. 이 이름은 해당 디바이스에서 사용자에게 표시됩니다.
- **AAD의 사용자 이름 특성**: 이 이름은 Intune이 Azure AD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 프로필에서 사용되는 사용자 이름을 동적으로 생성합니다. 옵션은 다음과 같습니다.
  - **사용자 계정 이름**: 이름(예: `user1` 또는 `user1@contoso.com`)을 가져옵니다.
  - **사용자 이름**: `user1`과 같은 이름만 가져옵니다.
  - **sAM 계정 이름**: `domain\user1`과 같은 도메인이 필요합니다. sAM 계정 이름은 Android 디바이스에서만 사용됩니다.

    또한 다음을 입력합니다.  
    - **사용자 도메인 이름 원본**: **AAD**(Azure Active Directory) 또는 **사용자 지정**을 선택합니다.

      **AAD**에서 특성을 가져오도록 선택할 때 다음을 입력합니다.
      - **AAD의 사용자 도메인 이름 특성**: 사용자의 **전체 도메인 이름** 또는 **NetBIOS 이름** 특성을 가져오도록 선택

      **사용자 지정** 특성을 사용하도록 선택할 때 다음을 입력합니다.
      - **사용할 사용자 지정 도메인 이름**: Intune이 도메인 이름(예: `contoso.com` 또는 `contoso`)에 사용하는 값을 입력합니다.

- **AAD의 메일 주소 특성**: 이 이름은 Intune이 Azure AD에서 가져오는 이메일 특성입니다. Intune은 이 프로필에서 사용되는 이메일 주소를 동적으로 생성합니다. 옵션은 다음과 같습니다.
  - **사용자 계정 이름**:  `user1@contoso.com` 또는 `user1`과 같은 전체 사용자 계정 이름을 이메일 주소로 사용합니다.
  - **기본 SMTP 주소**: `user1@contoso.com`과 같은 기본 SMTP 주소를 사용하여 Exchange에 로그인합니다.

- **인증 방법**: 전자 메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서**중 하나를 선택합니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.

### <a name="security-settings"></a>보안 설정

- **SSL**: 전자 메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **S/MIME**: S/MIME 암호화를 사용하여 발신 전자 메일을 전송합니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.

### <a name="synchronization-settings"></a>동기화 설정

- **동기화할 메일 양**: 동기화할 메일의 일 수 또는 **무제한**을 선택하여 사용 가능한 모든 메일을 동기화합니다.
- **동기화 일정**: Exchange 서버의 데이터를 동기화하는 디바이스의 일정을 선택합니다. 데이터가 도착하는 즉시 동기화하는 **메시지가 도착할 때**를 선택하거나 디바이스의 사용자가 동기화를 시작해야 하는 **수동**을 선택할 수도 있습니다.

### <a name="content-sync-settings"></a>콘텐츠 동기화 설정

- **동기화할 콘텐츠 형식**: 디바이스에서 동기화할 콘텐츠 형식을 선택합니다. **구성되지 않음**을 선택하면 이 설정이 비활성화합니다. **구성되지 않음**으로 설정할 때 최종 사용자가 디바이스에서 동기화를 활성화하면 정책이 강화됨에 따라 디바이스가 Intune과 동기화될 때 동기화가 비활성화됩니다. 

  다음 콘텐츠를 동기화할 수 있습니다.  
  - **연락처**: 최종 사용자가 연락처를 해당 디바이스에 동기화할 수 있도록 하려면 **사용**을 선택합니다.
  - **일정**: 최종 사용자가 일정을 해당 디바이스에 동기화할 수 있도록 하려면 **사용**을 선택합니다.
  - **작업**: 최종 사용자가 모든 작업을 해당 디바이스에 동기화할 수 있도록 하려면 **사용**을 선택합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[Android Enterprise - 회사 프로필](email-settings-android-enterprise.md), [iOS](email-settings-ios.md), [Windows 10 이상](email-settings-windows-10.md) 및 [Windows Phone 8.1](email-settings-windows-phone-8-1.md)에 대한 이메일 프로필을 만들 수도 있습니다.
