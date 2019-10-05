---
title: Microsoft Intune에서 iOS 디바이스의 메일 설정 구성 - Azure | Microsoft Docs
description: Exchange 서버 사용 및 Azure Active Directory에서 특성 가져오기를 비롯한 Microsoft Intune에서 iOS 디바이스에 추가하고 구성할 수 있는 모든 이메일 설정 목록을 확인합니다. 또한 SSL을 활성화하고, 인증서 또는 사용자 이름/암호를 인증하고, Microsoft Intune에서 디바이스 구성 프로필을 사용하여 iOS 디바이스에서 이메일을 동기화할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/05/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3bd91891fa6da770404dc0af6d59016aeefe30b3
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734598"
---
# <a name="add-e-mail-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune에서 iOS 디바이스의 메일 설정 추가

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Microsoft Intune에서 이메일 서버에 연결하기 위한 이메일을 만들고 구성하고, 사용자가 인증하는 방법을 선택하고, 암호화를 위한 S/MIME를 사용하는 등을 할 수 있습니다.

이 문서에서는 iOS를 실행하는 디바이스에 사용할 수 있는 모든 이메일 설정을 나열하고 설명합니다. 이러한 이메일 설정을 iOS 디바이스에 푸시하거나 배포하려면 디바이스 구성 프로필을 만들 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](../email-settings-configure.md).

> [!NOTE]
> 이러한 설정은 모든 등록 형식에 사용할 수 있습니다. 등록 유형에 대 한 자세한 내용은 [iOS 등록](../ios-enroll.md)을 참조 하세요.

## <a name="email-settings"></a>전자 메일 설정

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

- **AAD의 이메일 주소 특성**: 사용자의 이메일 주소가 생성되는 방식을 선택합니다. 전체 사용자 이름을 이메일 주소로 사용하려면 **사용자 계정 이름**(`user1@contoso.com` 또는 `user1`)을 선택합니다. 기본 SMTP 주소를 사용하여 Exchange에 로그인하려면 **기본 SMTP 주소**(`user1@contoso.com`)를 선택합니다.
- **인증 방법**: 이메일 프로필에서 사용되는 인증 방법으로 **사용자 이름 및 암호** 또는 **인증서** 중 하나를 선택합니다. Azure 다단계 인증은 지원되지 않습니다.
  - **인증서**를 선택한 경우 Exchange 연결을 인증하는 데 사용할 이전에 만든 클라이언트 SCEP 또는 PKCS 인증서 프로필을 선택합니다.
- **SSL**: **사용 가능**에서는 이메일을 보내고, 이메일을 받고, Exchange Server와 통신할 때 SSL(Secure Sockets Layer) 통신을 사용합니다.
- **OAuth**: **사용 가능**에서는 이메일을 보내고, 이메일을 받고, Exchange와 통신할 때 OAuth(Open Authorization) 통신을 사용합니다. OAuth 서버에서 인증서 인증을 사용하는 경우 **인증서**를 **인증 방법**으로 선택하고 프로필에 인증서를 포함합니다. 그렇지 않으면 **사용자 이름 및 암호**를 **인증 방법**으로 선택합니다. OAuth를 사용할 때 다음 사항을 확인합니다.

  - 이 프로필을 사용자에게 지정하기 전에 이메일 솔루션이 OAuth를 지원하는지 확인합니다. Office 365 Exchange 온라인은 OAuth를 지원합니다. 온-프레미스 Exchange 및 기타 파트너 또는 타사 솔루션은 OAuth를 지원하지 않을 수 있습니다. 온-프레미스 Exchange 최신 인증용으로 구성할 수 있습니다([Exchange 온-프레미스용 하이브리드 최신 인증 발표](https://blogs.technet.microsoft.com/exchange/2017/12/06/announcing-hybrid-modern-authentication-for-exchange-on-premises/) 블로그 게시물 참조).

    이메일 프로필에서 Oauth를 사용하고 이메일 서비스가 이를 지원하지 않는 경우 **암호 다시 입력** 옵션이 해제된 것으로 나타납니다. 예를 들어 사용자가 Apple의 디바이스 설정에서 **암호 다시 입력**을 선택하면 아무 일도 발생하지 않습니다.

  - OAuth를 사용하도록 설정하면 최종 사용자는 MFA(다단계 인증)를 지원하는 다른 "최신 인증" 이메일 로그인 환경을 갖게 됩니다. 

  - 일부 조직에서는 [셀프 서비스 애플리케이션 액세스](https://docs.microsoft.com/azure/active-directory/manage-apps/manage-self-service-access)를 수행하는 최종 사용자의 기능을 비활성화합니다. 이 시나리오에서는 관리자가 "iOS 계정" 엔터프라이즈 앱을 만들고 사용자에게 Azure AD의 앱에 대한 액세스 권한을 부여할 때까지 최신 인증 로그인이 실패할 수 있습니다.

    기본 작업은 **비즈니스 승인 없이** [애플리케이션 액세스 패널](https://docs.microsoft.com/azure/active-directory/user-help/active-directory-saas-access-panel-introduction) **앱 추가** 기능을 사용하여 애플리케이션을 추가하는 것입니다. 자세한 내용은 [애플리케이션에 사용자 할당](https://docs.microsoft.com/azure/active-directory/manage-apps/ways-users-get-assigned-to-applications)을 참조하세요.

  > [!NOTE]
  > OAuth를 사용하도록 설정하면 다음과 같은 상황이 발생합니다.  
  > 1. 이미 대상으로 지정된 디바이스에 새 프로필이 발행됩니다.
  > 2. 최종 사용자에게 자격 증명을 다시 입력하라는 메시지가 표시됩니다.

- **S/MIME**: 사용자가 iOS 네이티브 메일 애플리케이션에서 이메일에 서명 및/또는 암호화할 수 있게 하려면 **S/MIME을 사용**합니다. 

  이메일 메시지를 통해 S/MIME를 사용하는 경우 보낸 사람의 신뢰성 및 메시지의 무결성 및 기밀성을 확인합니다.

  - **S/MIME 서명 사용**: **사용**을 선택하여 사용자가 입력한 계정에 보내는 이메일에 디지털 서명을 할 수 있게 합니다. 서명을 사용하면 메시지를 수신하는 사용자가 보낸 사람으로 가장하는 누군가가 아닌, 특정 보낸 사람에게서 온 메시지임을 확신하는 데 도움이 됩니다. **사용 안 함**은 사용자가 메시지에 디지털 서명을 하도록 허용하지 않습니다.
    - **사용자가 설정을 변경하도록 허용**: **사용**을 선택하여 사용자가 S/MIME 서명 동작을 변경할 수 있게 합니다. **사용 안함**을 통해 구성한 S/MIME 서명 설정을 변경하는 것을 방지합니다. iOS 12 이상에서 사용할 수 있습니다.

  - **S/MIME 서명 인증서**: 이메일 메시지 서명에 사용되는 기존 PKCS 또는 SCEP 인증서 프로필을 선택합니다.
    - **사용자가 설정을 변경하도록 허용**: **사용**을 선택하여 사용자가 서명 인증서를 변경할 수 있게 합니다. **사용 안 함**을 통해 사용자가 서명 인증서를 변경하는 것을 방지하고 구성한 인증서를 사용자가 강제로 사용하도록 합니다. iOS 12 이상에서 사용할 수 있습니다.

  - **기본적으로 암호화**: **사용**은 기본 동작으로 모든 메시지를 암호화합니다. **사용 안 함**은 기본 동작으로 모든 메시지를 암호화하지 않습니다.
    - **사용자가 설정을 변경하도록 허용**: **사용**을 선택하여 사용자가 기본 암호화 동작을 변경할 수 있게 합니다. **사용 안 함**을 통해 사용자가 암호화 기본 동작을 변경하는 것을 방지하고 구성한 설정을 사용자가 강제로 사용하도록 합니다. iOS 12 이상에서 사용할 수 있습니다.

  - **메시지당 암호화 적용**: 메시지당 암호화를 통해 사용자가 발송되기 전에 서명된 이메일을 선택할 수 있습니다. **사용**을 선택하면 새 이메일을 만들 때 메시지당 암호화 옵션이 표시됩니다. 그런 다음, 사용자는 메시지당 암호화의 옵트인 또는 옵트아웃을 선택할 수 있습니다. **사용 안 함**을 사용하면 메시지당 암호화 옵션이 표시되는 것을 방지합니다.

    **기본적으로 암호화** 설정이 사용되도록 설정된 경우 메시지당 암호화를 사용하면 사용자는 메시지당 암호화를 옵트아웃할 수 있습니다. **기본적으로 암호화** 설정이 사용되지 않도록 설정된 경우 메시지당 암호화를 사용하면 사용자는 메시지당 암호화를 옵트인할 수 있습니다.

  - **S/MIME 암호화 인증서**: 이메일 메시지 암호화에 사용되는 기존 PKCS 또는 SCEP 인증서 프로필을 선택합니다.
    - **사용자가 설정을 변경하도록 허용**: **사용**을 선택하여 사용자가 암호화 인증서를 변경할 수 있게 합니다. **사용 안 함**을 통해 사용자가 암호화 인증서를 변경하는 것을 방지하고 구성한 인증서를 사용자가 강제로 사용하도록 합니다. iOS 12 이상에서 사용할 수 있습니다.
- **동기화할 이메일 양**: 동기화할 이메일의 일 수를 선택합니다. 또는 **무제한**을 선택하여 사용 가능한 모든 이메일을 동기화합니다.
- **다른 이메일 계정으로 메시지 이동 허용**: **사용 설정**하면 사용자가 디바이스에 구성한 여러 계정 간에 이메일 메시지를 이동할 수 있습니다.
- **타사 애플리케이션에서 보내는 이메일 허용**: **사용 설정**하면 사용자는 이 프로필을 이메일 보내기의 기본 계정으로 선택할 수 있습니다. 타사 애플리케이션이 이메일에 파일을 첨부하는 것과 같이 기본 이메일 앱에서 이메일을 열 수 있습니다.
- **최근 사용된 이메일 주소 동기화**: **사용 설정**하면 사용자는 디바이스에서 최근에 사용한 이메일 주소 목록을 서버와 동기화할 수 있습니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](../device-profile-assign.md)하고, [해당 상태를 모니터링](../device-profile-monitor.md)합니다.

[Android](../email-settings-android.md), [android Enterprise](../email-settings-android-enterprise.md), [Windows 10](email-settings-windows-10.md)및 [Windows Phone 8.1](email-settings-windows-phone-8-1.md) 장치에서 전자 메일 설정을 구성 합니다.
