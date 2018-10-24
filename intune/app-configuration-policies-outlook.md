---
title: Microsoft Intune의 iOS 및 Android 장치에 대한 Outlook 설정
description: iOS 및 Android 장치에서 실행되는 Microsoft Outlook 설정을 설정하기 위한 구성 정책을 만듭니다.
keywords: ''
author: Erikre
ms.author: erikre
ms.reviewer: smithre4
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 24ed1a895dd3e4cad6111b40913b43fa9c6a3cec
ms.sourcegitcommit: 11bd3dbbc9dd762df7c6d20143f2171799712547
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2018
ms.locfileid: "48903525"
---
# <a name="microsoft-outlook-configuration-settings"></a>Microsoft Outlook 구성 설정 

iOS 및 Android 장치에서 실행되는 Microsoft Outlook 설정을 설정하기 위한 구성 정책을 사용합니다. 

관리되는 iOS 장치용 앱 구성 정책을 만들려면 [관리되는 iOS 장치용 앱 구성 정책 추가](app-configuration-policies-use-ios.md)를 참조하세요. 관리되는 Android 장치용 앱 구성 정책을 만들려면 [관리되는 Android 장치용 앱 구성 정책 추가](app-configuration-policies-use-android.md)를 참조하세요. 

## <a name="configuration-settings"></a>구성 설정

Intune에서 구성 정책을 추가할 때 Microsoft Outlook을 구성하도록 특정 설정을 설정할 수 있습니다. **구성 설정** 창에서 메일 계정 구성을 설정할 수 있습니다.

### <a name="basic-authentication-email-account-settings"></a>기본 인증 메일 계정 설정
iOS 및 Android용 Outlook은 ActiveSync 프로토콜을 이용한 기본 인증을 사용하는 온-프레미스 사용자에게 계정 구성을 "푸시"할 수 있는 기능을 Exchange 관리자에게 제공합니다. 자세한 내용은 [기본 인증을 사용하여 iOS 및 Android용 Outlook의 계정 설정](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/account-setup)을 참조하세요. 계정 설정 구성을 사용하려면 다음 설정을 구성할 수 있습니다.

- **메일 서버**: 온-프레미스 Exchange 서버(예: mail.contoso.com)의 호스트 이름을 입력합니다.
- **메일 계정 이름**: 메일 계정의 표시 이름을 입력합니다. 이 이름은 해당 장치에서 사용자에게 표시됩니다.
- **AAD의 사용자 이름 특성**: 이 이름은 Intune이 Azure AD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 프로필에서 사용되는 사용자 이름을 동적으로 생성합니다. 다음과 같은 선택 사항이 있습니다.
  - **사용자 계정 이름**: `user1` 또는 `user1@contoso.com`과 같은 이름을 가져옵니다.
  - **기본 SMTP 주소**: `user1@contoso.com`과 같은 이메일 주소 형식의 이름을 가져옵니다.
- **AAD의 이메일 주소 특성**: 사용자의 이메일 주소가 생성되는 방식을 선택합니다. **사용자 계정 이름**(`user1@contoso.com` 또는 `user1`)을 선택하여 전체 계정 이름을 이메일 주소로 사용하거나, **기본 SMTP 주소**(`user1@contoso.com`)를 사용하여 Exchange에 로그인합니다. 권장 사항은 **기본 SMTP 주소**를 선택하는 것입니다.
- **계정 도메인**: (선택 사항) 계정의 도메인입니다.

## <a name="next-steps"></a>다음 단계
[Intune에서 이메일 설정 구성](email-settings-configure.md)

