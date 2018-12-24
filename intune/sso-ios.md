---
title: Microsoft Intune에서 iOS 디바이스용 Single Sign-On 추가 - Azure | Microsoft Docs
description: Microsoft Intune에서 조직의 리소스 및 데이터에 대한 인증을 위해 iOS 디바이스가 암호 대신 SSO(Single Sign-On)를 사용하도록 만들거나 구성하거나 허용하거나 사용하도록 설정합니다. SSO를 사용하려면 디바이스 구성 프로필을 만들고 UPN, 디바이스 ID, 응용 프로그램 및 인증서를 입력하여 사용자와 디바이스를 인증합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c4d19807ecfcc33b957d5f6582f095427dbf978e
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190203"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Microsoft Intune에서 Single Sign-On iOS 디바이스 사용

대부분의 LOB(기간 업무) 앱이 보안을 지원하려면 일부 수준의 사용자 인증이 필요합니다. 대부분의 경우 이 인증은 사용자가 동일한 자격 증명을 여러 번 입력해야 하므로 번거롭습니다. 사용자 경험을 향상하기 위해 개발자는 SSO(Single Sign-On)을 사용하는 앱을 만들어 사용자가 자격 증명을 입력해야 하는 횟수를 줄일 수 있습니다.

이 문서에서는 Microsoft Intune에서 디바이스 구성 프로필을 사용하여 iOS 디바이스에 대한 Single Sign-On을 설정하는 방법을 설명합니다.

## <a name="before-you-begin"></a>시작하기 전에

iOS 디바이스의 Single Sign-On 페이로드에서 사용자 자격 증명 저장소를 찾도록 코딩된 앱이 있습니다.

## <a name="create-the-sso-profile"></a>SSO 프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: `ios sso profile` 등의 프로필의 이름을 입력합니다.
    - **설명**: 목록에서 프로필을 쉽게 찾을 수 있도록 주요 용어와 함께 설명을 입력합니다.
    - **플랫폼**: **iOS**를 선택합니다.
    - **프로필 유형**: **장치 기능**을 선택합니다.

4. **Single Sign On**을 선택합니다.

    ![Single Sign-On 창](./media/sso-blade.png)

5. 다음 설정을 입력합니다. 

    - **AAD의 사용자 이름 특성**: Intune은 Azure AD에서 각 사용자에 대해 이 특성을 찾습니다. 그런 다음, Intune이 디바이스에 설치되는 XML 페이로드를 생성하기 전에 해당 필드(예: UPN)를 채웁니다. 옵션은 다음과 같습니다.
    
        - **사용자 계정 이름**: UPN은 다음과 같은 방법으로 구문 분석을 합니다.

            ![사용자 이름 특성](media/User-name-attribute.png)

            **영역** 텍스트 상자에 입력한 텍스트로 영역을 덮어쓸 수도 있습니다.

            예를 들어 Contoso에 유럽, 아시아, 북아메리카와 같은 여러 하위 영역이 있을 수 있습니다. 아시아의 사용자가 SSO 페이로드를 사용하도록 할 수 있으며, 앱에 `username@asia.contoso.com` 형식의 UPN이 필요합니다. 이 경우 **사용자 계정 이름**을 선택하면 기본적으로 각 사용자의 영역이 Azure AD에서 검색되며, 단순히 *contoso.com*일 수 있습니다. 따라서 특히 아시아의 사용자에 대해 이 페이로드를 만들고 영역을 *asia.contoso.com* 값으로 덮어쓸 수 있습니다. 이제 최종 사용자의 UPN은 username@contoso.com 대신 username@asia.contoso.com이 됩니다.

        - **Intune 장치 ID**: Intune은 Intune 장치 ID를 자동으로 선택합니다. 

            기본적으로 앱은 디바이스 ID만 사용해야 합니다. 그러나 앱이 영역 *및* 디바이스 ID를 사용하는 경우 **영역** 텍스트 상자에 영역을 입력할 수 있습니다.

            > [!NOTE]
            > 기본적으로 디바이스 ID를 사용하는 경우 영역을 비워 둡니다.

    - **영역**: URL의 도메인 부분입니다.
    
    - **Single Sign-On을 사용할 URL 접두사**: 사용자 Single Sign-On 인증이 필요한 조직의 모든 URL을 **추가**합니다. 

        예를 들어 사용자가 이러한 사이트에 연결하는 경우 iOS 디바이스는 Single Sign-On 자격 증명을 사용합니다. 사용자는 추가 자격 증명을 입력할 필요가 없습니다. 그러나 다단계 인증을 사용하는 경우 사용자가 두 번째 인증을 입력해야 합니다.

        > [!NOTE]
        > 이러한 URL은 올바른 형식의 FQDN이어야 합니다. Apple은 URL이 `http://<yourURL.domain>` 형식이어야 합니다.

        URL 일치 패턴은 `http://` 또는 `https://`로 시작해야 합니다. 단순 문자열 일치가 수행되므로 URL 접두사 `http://www.contoso.com/`은 `http://www.contoso.com:80/`과 일치하지 않습니다. 그러나 iOS 10.0 이상에서는 단일 와일드카드 \*를 사용하여 일치하는 모든 값을 입력할 수 있습니다. 예를 들어 `http://*.contoso.com/`은 `http://store.contoso.com/` 및 `http://www.contoso.com` 둘 다와 일치합니다.

        `http://.com` 및 `https://.com` 패턴은 각각 모든 HTTP 및 HTTPS URL과 일치합니다.
    
    - **Single Sign-On을 사용할 앱**: Single Sign-On을 사용할 수 있는 최종 사용자 장치에서 앱을 **추가**합니다. 

        `AppIdentifierMatches` 배열에는 앱 번들 ID와 일치하는 문자열이 포함되어야 합니다. 이러한 문자열은 정확히 일치하는 항목(예: `com.contoso.myapp`)이거나, \* 와일드카드 문자를 사용하여 번들 ID의 접두사 일치를 입력할 수 있습니다. 와일드카드 문자는 마침표 문자(.) 뒤에 표시되어야 하며, 문자열의 끝에 한 번만 나타날 수 있습니다(예: `com.contoso.*`). 와일드카드가 포함되면 번들 ID가 접두사로 시작하는 모든 앱에 계정에 대한 액세스 권한이 부여됩니다.

        **앱 이름**을 사용하여 번들 ID를 식별할 수 있도록 친숙한 이름을 입력합니다.
    
    - **자격 증명 갱신 인증서**: 인증에 인증서를 사용하는 경우(암호 아님) 인증 인증서로 사용자에게 배포되는 SCEP 또는 PFX 인증서를 선택합니다. 일반적으로 VPN, Wi-Fi, 이메일 등의 다른 프로필에 대해 사용자에게 배포되는 것과 동일한 인증서입니다.

6. **확인** > **확인** > **만들기**를 차례로 선택하여 변경 내용을 저장하고 프로필을 만듭니다. 만들어지면 **디바이스 구성 - 프로필** 목록에 나타납니다. 

## <a name="next-steps"></a>다음 단계

디바이스 기능 구성에 대한 자세한 내용은 [Microsoft Intune에서 디바이스 기능 설정을 구성하는 방법](device-features-configure.md)을 참조하세요.

iOS 장치에 [이 프로필을 할당합니다](device-profile-assign.md).
