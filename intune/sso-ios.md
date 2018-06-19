---
title: iOS 장치 Single Sign-On용 Microsoft Intune 구성
titlesuffix: ''
description: iOS 장치 Single Sign-On용 Microsoft Intune을 구성하는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 010ed8511b042d6f764ba947f616d76521588f42
ms.sourcegitcommit: 91802e78cd5014d20a828ca25a54a381d452f0f8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/16/2018
ms.locfileid: "34216261"
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>iOS 장치 Single Sign-On용 Microsoft Intune 구성

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

대부분의 LOB(기간 업무) 앱이 보안을 지원하려면 일부 수준의 사용자 인증이 필요합니다. 대부분의 경우 사용자가 동일한 자격 정보를 여러 번 입력해야 하며 사용자에게 번거로울 수 있습니다. 사용자 경험을 향상하기 위해 개발자는 Single Sign-On을 사용하는 앱을 만들어 사용자가 자격 증명을 제공해야 하는 횟수를 줄일 수 있습니다.

iOS 장치 Single Sign-On을 활용하려면 다음 조건이 있어야 합니다.

- iOS 장치의 Single Sign-On 페이로드에서 사용자 자격 증명 저장소를 찾도록 코딩된 앱입니다.
- iOS 장치 Single Sign-On용으로 구성된 Intune입니다.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>iOS 장치 Single Sign-On용 Intune을 구성하려면


1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **장치 구성**을 선택합니다.
4. **관리** 섹션 아래의 **장치 구성** 창에서 **프로필**을 선택합니다.
5. 프로필 창에서 **프로필 만들기**를 선택합니다.
6. 이름과 설명을 입력하고 다음 설정을 구성합니다.
   - **플랫폼**: **iOS**를 선택합니다.
   - **프로필 유형**: **장치 기능**을 선택합니다.
7. **장치 기능** 창에서 **Single Sign-On**을 선택합니다.

   ![Single Sign-On 창](./media/sso-blade.png)

8. 다음 요약표를 사용하여 **Single Sign-On** 창의 필드를 채울 수 있습니다. 자세한 내용은 표 뒤에 있는 섹션을 참조하세요.

   |필드  |참고|
   |---------|---------|
   |**AAD의 사용자 이름 특성**|Intune이 AAD에서 각 사용자에 대해 확인하고 장치에 설치되는 XML 페이로드를 생성하기 전에 해당 필드(예: UPN)를 채우는 특성입니다.|
   |**영역**|URL의 도메인 부분입니다.|
   |**Single Sign-On을 사용할 URL 접두사**|사용자 Single Sign-On 인증이 필요한 조직의 모든 URL입니다.|
   |**Single Sign-On을 사용할 앱**|Single Sign-On 페이로드를 사용하는 최종 사용자 장치의 앱입니다.|
   |**자격 증명 갱신 인증서**|인증에 인증서를 사용하는 경우 인증 인증서로 사용자에게 배포되는 SCEP 또는 PFX 인증서를 선택합니다.|

다음 섹션에서는 각 Single Sign-On 필드에 대한 자세한 정보를 제공합니다.

### <a name="username-attribute-from-aad-and-realm"></a>AAD 및 영역의 사용자 이름 특성

- 이 필드에 대해 **사용자 계정 이름**을 선택하면 다음과 같은 방식으로 구문 분석됩니다.

   ![사용자 이름 특성](media/User-name-attribute.png)

   **영역** 텍스트 상자에 입력한 텍스트로 영역을 덮어쓸 수도 있습니다.

   예를 들어 Contoso에 유럽, 아시아, 북아메리카와 같은 여러 하위 영역이 있을 수 있습니다. 아시아의 사용자가 SSO 페이로드를 사용하도록 할 수 있으며, 앱에 *username@asia.contoso.com* 형식의 UPN이 필요합니다. 이 경우 **사용자 계정 이름**을 선택하면 기본적으로 각 사용자의 영역이 AAD에서 검색되며, 단순히 *contoso.com*일 수 있습니다. 따라서 특히 아시아의 사용자에 대해 이 페이로드를 만들고 영역을 *asia.contoso.com* 값으로 덮어쓸 수 있습니다. 이제 최종 사용자의 UPN은 *username@contoso.com*이 아니라 *username@asia.contoso.com*이 됩니다.

- **장치 ID**를 선택하면 Intune에서 Intune 장치 ID가 자동으로 선택됩니다.

   기본적으로 앱은 장치 ID만 사용해야 합니다. 그러나 앱이 장치 ID 외에 영역을 사용하는 경우 **영역** 텍스트 상자에 영역을 입력할 수 있습니다.

   > [!NOTE]
   > 기본적으로 장치 ID를 사용하는 경우 영역을 비워 둡니다.

### <a name="url-prefixes-that-will-use-single-sign-on"></a>Single Sign-On을 사용할 URL 접두사

사용자 인증이 필요한, 조직에 있는 모든 URL을 여기에 입력합니다.

예를 들어 사용자가 이러한 사이트에 연결하는 경우 iOS 장치는 Single Sign-On 자격 증명을 사용하며, 사용자가 추가 자격 증명을 입력하지 않아도 됩니다. 그러나 다단계 인증을 사용하는 경우 사용자가 두 번째 인증을 입력해야 합니다.

> [!NOTE]
> 이러한 URL은 올바른 형식의 FQDN이어야 합니다. Apple에서는 `http://<yourURL.domain>` 형식의 FQDN이어야 합니다.

URL 일치 패턴은 `http://` 또는 `https://`로 시작해야 합니다. 단순 문자열 일치가 수행되므로 URL 접두사 `http://www.contoso.com/`은 `http://www.contoso.com:80/`과 일치하지 않습니다. 그러나 iOS 9.0 이상에서는 단일 와일드카드 \*를 사용하여 일치하는 모든 값을 지정할 수 있습니다. 예를 들어 `http://*.contoso.com/`은 `http://store.contoso.com/` 및 `http://www.contoso.com` 둘 다와 일치합니다.
`http://.com` 및 `https://.com` 패턴은 각각 모든 HTTP 및 HTTPS URL과 일치합니다.

### <a name="apps-that-will-use-single-sign-on"></a>Single Sign-On을 사용할 앱

Single Sign-On 페이로드를 사용할 수 있는 최종 사용자 장치의 앱을 나타냅니다.

`AppIdentifierMatches` 배열에는 앱 번들 ID와 일치하는 문자열이 포함되어야 합니다. 이러한 문자열은 정확히 일치하는 항목(예: `com.contoso.myapp`)이거나, \* 와일드카드 문자를 사용하여 번들 ID의 접두사 일치를 지정할 수 있습니다. 와일드카드 문자는 마침표 문자(.) 뒤에 표시되어야 하며, 문자열의 끝에 한 번만 나타날 수 있습니다(예: `com.contoso.*`). 와일드카드가 포함되면 번들 ID가 접두사로 시작하는 모든 앱에 계정에 대한 액세스 권한이 부여됩니다.

**앱 이름** 필드는 사용자가 번들 ID를 쉽게 식별할 수 있는 친숙한 이름을 추가하는 데 사용됩니다.

### <a name="credential-renewal-certificate"></a>자격 증명 갱신 인증서

인증서(암호 아님)를 사용하여 최종 사용자를 인증하는 경우 이 필드를 사용하여 사용자에게 인증 인증서로 배포되는 SCEP 또는 PFX 인증서를 선택합니다. 일반적으로 VPN, Wi-Fi, 이메일 등의 다른 프로필에 대해 사용자에게 배포되는 것과 동일한 인증서입니다.

## <a name="next-steps"></a>다음 단계

장치 기능 구성에 대한 자세한 내용은 [Microsoft Intune에서 장치 기능 설정을 구성하는 방법](device-features-configure.md)을 참조하세요.
