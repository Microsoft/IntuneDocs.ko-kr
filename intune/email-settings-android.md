---
title: Microsoft Intune에서 Android 및 Android 회사 프로필 장치에 대한 이메일 설정 - Azure | Microsoft Docs
description: Exchange 서버를 사용하는 장치 구성 이메일 프로필을 만들고 Azure Active Directory에서 특성을 검색합니다. 또한 SSL 또는 SMIME을 활성화하고, 인증서 또는 사용자 이름/암호를 인증하고, Microsoft Intune을 사용하여 Android 및 Android 회사 프로필 장치에서 이메일 및 일정을 동기화할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: b8ab8dfadb113d81922119a54aefcac43d15b5a1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52187432"
---
# <a name="email-profile-settings-for-devices-running-android-and-android-enterprise---intune"></a>Android 및 Android Enterprise를 실행하는 장치에 대해 이메일 프로필 설정 - Intune

이메일 프로필 설정을 사용하여 Android를 실행하는 장치를 구성합니다.

Intune 관리자는 다음 Android 장치에 대해 이메일 설정을 만들고 할당할 수 있습니다.

- Android Samsung Knox Standard
- Android Enterprise

## <a name="android-samsung-knox"></a>Android(Samsung Knox)

- **이메일 서버**: Exchange 서버의 호스트 이름을 입력합니다.
- **계정 이름**: 이메일 계정의 표시 이름을 입력합니다. 이 이름은 해당 장치에서 사용자에게 표시됩니다.
- **AAD의 사용자 이름 특성**: 이 이름은 Intune이 AAD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 프로필에서 사용되는 사용자 이름을 동적으로 생성합니다. 옵션은 다음과 같습니다.
  - **사용자 계정 이름**: `user1` 또는 `user1@contoso.com`과 같은 이름을 가져옵니다.
  - **사용자 이름**: `user1`과 같은 이름만 가져옵니다.
  - **sAM 계정 이름**: `domain\user1`과 같은 도메인이 필요합니다. sAM 계정 이름은 Android 장치에서만 사용할 수 있습니다. Android Enterprise는 지원되지 않습니다.

    또한 다음을 입력합니다.  
    - **사용자 도메인 이름 원본**: **AAD**(Azure Active Directory) 또는 **사용자 지정**을 선택합니다.

      **AAD**에서 특성을 가져오도록 선택할 때 다음을 입력합니다.
      - **AAD의 사용자 도메인 이름 특성**: 사용자의 **전체 도메인 이름** 또는 **NetBIOS 이름** 특성을 가져오도록 선택

      **사용자 지정** 특성을 사용하도록 선택할 때 다음을 입력합니다.
      - **사용할 사용자 지정 도메인 이름**: Intune이 도메인 이름(예: `contoso.com` 또는 `contoso`)에 사용하는 값을 입력합니다.

- **AAD의 이메일 주소 특성**: 사용자의 이메일 주소가 생성되는 방식을 선택합니다. **사용자 계정 이름**(`user1@contoso.com` 또는 `user1`)을 선택하여 전체 계정 이름을 이메일 주소로 사용하거나, **기본 SMTP 주소**(`user1@contoso.com`)를 사용하여 Exchange에 로그인합니다.

- **인증 방법**: 이메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서** 중 하나를 선택합니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.

### <a name="security-settings"></a>보안 설정

- **SSL**: 이메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **S/MIME**: S/MIME 암호화를 사용하여 보내는 이메일을 전송합니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.

### <a name="synchronization-settings"></a>동기화 설정

- **동기화할 이메일 양**: 동기화할 이메일의 일 수를 선택하거나, **무제한**을 선택하여 사용 가능한 모든 이메일을 동기화합니다.
- **동기화 일정**: Exchange 서버의 데이터를 동기화하는 장치의 일정을 선택합니다. 데이터가 도착하는 즉시 동기화하는 **메시지가 도착할 때**를 선택하거나 장치의 사용자가 동기화를 시작해야 하는 **수동**을 선택할 수도 있습니다.

### <a name="content-sync-settings"></a>콘텐츠 동기화 설정

- **동기화할 콘텐츠 형식**: 장치에 동기화할 콘텐츠 형식을 선택합니다.
  - **연락처**
  - **일정**
  - **태스크**

## <a name="android-enterprise"></a>Android Enterprise

- **이메일 앱**: **Gmail** 또는 **Nine Work**를 선택합니다.
- **이메일 서버** - Exchange 서버의 호스트 이름입니다.
- **AAD의 사용자 이름 특성**: 이 이름은 해당 이메일 프로필에 대해 사용자 이름을 생성하는 데 사용되는 AD(Active Directory) 또는 Azure AD의 특성입니다. user1@contoso.com와 같은 **기본 SMTP 주소** 또는 user1, user1@contoso.com와 같은 **사용자 계정 이름**을 선택합니다.
- **AAD의 이메일 주소 특성**: 각 장치에서 사용자의 이메일 주소가 생성되는 방식을 선택합니다. 전체 사용자 이름을 전자 메일 주소 또는 **사용자 이름**으로 사용하려면 **사용자 계정 이름**을 선택합니다.
- **인증 방법**: 이메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서** 중 하나를 선택합니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.
- **SSL**: 이메일을 전송하거나 수신할 때와 Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **동기화할 이메일 양**: 동기화할 이메일의 일 수를 선택하거나, **무제한**을 선택하여 사용 가능한 모든 이메일을 동기화합니다.
- **동기화할 콘텐츠 형식**(Nine Work에만 해당): 장치에 동기화할 콘텐츠 형식을 선택합니다.
  - **연락처**
  - **일정**
  - **태스크**

## <a name="next-steps"></a>다음 단계
[Intune에서 이메일 설정 구성](email-settings-configure.md)
