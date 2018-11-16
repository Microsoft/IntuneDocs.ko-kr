---
title: Microsoft Intune에서 iOS 장치에 대한 이메일 설정 - Azure | Microsoft Docs
description: Exchange 서버를 사용하여 장치 구성 이메일 프로필을 만들고 Azure Active Directory에서 특성을 검색합니다. 또한 SSL을 활성화하고, 인증서 또는 사용자 이름/암호를 인증하고, Microsoft Intune을 사용하여 iOS 장치에서 이메일을 동기화할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a6fd10ab6a1e9dd7249e2ae1d4bf558d190276ed
ms.sourcegitcommit: b0ee8626191961dc07f9f7f9d8e6a5fb09c63350
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51505881"
---
# <a name="email-profile-settings-for-ios-devices---intune"></a>iOS 장치에 대한 이메일 프로필 설정 - Intune

이메일 프로필 설정을 사용하여 iOS를 실행하는 장치를 구성합니다.

> [!IMPORTANT]
> 이 문서에서 설명하는 S/MIME 기능에 몇 가지 개선 사항을 적용하고 있습니다. 그 결과 Intune에서 S/MIME 기능이 일시적으로 제거되었습니다. 이 기능이 릴리스되면 본 메모를 제거하겠습니다.

## <a name="email-settings"></a>전자 메일 설정

- **이메일 서버**: Exchange 서버의 호스트 이름을 입력합니다.
- **계정 이름**: 이메일 계정의 표시 이름을 입력합니다. 이 이름은 해당 장치에서 사용자에게 표시됩니다.
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

- **S/MIME**: S/MIME 서명을 사용하여 보내는 이메일을 전송하기 위해 **S/MIME를 사용하도록 설정**합니다. 사용하도록 설정하면 암호화된 이메일을 수신할 수 있는 수신인에게 이메일을 암호화하고 보낸 사람으로부터 받은 이메일의 암호를 해독할 수 있습니다.
  - **인증서**를 선택한 경우 기존 PKCS 인증서 프로필을 선택하여 Exchange 연결을 인증 및/또는 이메일 교환을 암호화합니다.
- **동기화할 이메일 양**: 동기화할 이메일의 일 수를 선택합니다. 또는 **무제한**을 선택하여 사용 가능한 모든 이메일을 동기화합니다.
- **다른 이메일 계정으로 메시지 이동 허용**: **사용 설정**하면 사용자가 디바이스에 구성한 여러 계정 간에 이메일 메시지를 이동할 수 있습니다.
- **타사 애플리케이션에서 보내는 이메일 허용**: **사용 설정**하면 사용자는 이 프로필을 이메일 보내기의 기본 계정으로 선택할 수 있습니다. 타사 애플리케이션이 이메일에 파일을 첨부하는 것과 같이 기본 이메일 앱에서 이메일을 열 수 있습니다.
- **최근 사용된 이메일 주소 동기화**: **사용 설정**하면 사용자는 장치에서 최근에 사용한 이메일 주소 목록을 서버와 동기화할 수 있습니다.

## <a name="next-steps"></a>다음 단계
[Intune에서 이메일 설정 구성](email-settings-configure.md)
