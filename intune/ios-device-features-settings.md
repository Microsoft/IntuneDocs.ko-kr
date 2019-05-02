---
title: Microsoft Intune의 iOS 디바이스 기능 설정 - Azure | Microsoft Docs
description: Microsoft Intune에서 AirPrint, 홈 화면의 레이아웃, 앱 알림, 공유 디바이스, Single Sign-On 및 웹 콘텐츠 필터 설정에 대한 iOS 디바이스를 구성하는 모든 설정을 확인합니다. 디바이스 구성 프로필에서 이러한 설정을 확인하여 조직에서 이러한 서로 다른 Apple 기능을 사용하도록 iOS 디바이스를 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2a94be7ebc369005f92809d57c8e55076972df3
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799268"
---
# <a name="ios-device-settings-to-use-common-ios-features-in-intune"></a>Intune에서 iOS의 일반적인 기능을 사용 하는 iOS 장치 설정

Intune은 iOS 사용자가 해당 디바이스의 다른 Apple 기능을 사용하도록 허용하는 몇 가지 기본 제공 설정을 포함합니다. 예를 들어 관리자는 iOS 사용자가 AirPrint 프린터를 사용하고, 홈 화면의 도킹 및 페이지에 앱 및 폴더를 추가하고, 앱 알림을 표시하고, 잠금 화면에서 자산 태그 정보를 표시하고, Single Sign-On 인증을 사용하고, 인증서를 사용하여 사용자를 인증하는 방법을 제어할 수 있습니다.

모바일 장치 관리 (MDM) 솔루션의 일부분으로 iOS 장치를 제어 하려면 이러한 기능을 사용 합니다.

이 문서에서는 이러한 설정을 나열하고, 각 설정이 수행하는 작업을 설명합니다.

## <a name="before-you-begin"></a>시작하기 전에

[iOS 디바이스 구성 프로필을 만듭니다](device-features-configure.md#create-a-device-profile).

## <a name="airprint-settings"></a>AirPrint 설정

이 기능을 통해 iOS 사용자는 알려진 AirPrint 프린터로 인쇄할 수 있습니다.

1. **설정**에서 **AirPrint**를 선택합니다. AirPrint 서버의 다음 속성을 입력합니다.

    - **IP 주소**: 프린터의 IPv4 또는 IPv6 주소를 입력합니다. 호스트 이름을 사용하여 프린터를 식별하는 경우 터미널에서 프린터를 ping하여 IP 주소를 가져올 수 있습니다. IP 주소 및 경로 가져오기(이 문서)에서 자세한 정보를 제공합니다.
    - **경로**: 네트워크의 프린터에 대한 경로는 일반적으로 `ipp/print`입니다. IP 주소 및 경로 가져오기(이 문서)에서 자세한 정보를 제공합니다.
    - **포트**: AirPrint 대상의 수신 대기 포트를 입력합니다. 이 속성을 비워두면 AirPrint는 기본 포트를 사용합니다. iOS 11.0 이상에서 사용할 수 있습니다.
    - **TLS**: TLS(전송 계층 보안)를 사용하여 AirPrint 연결을 보호하려면 **사용**을 선택합니다. iOS 11.0 이상에서 사용할 수 있습니다.

2. **추가**를 선택합니다. AirPrint 서버가 목록에 추가됩니다. 많은 AirPrint 서버를 추가할 수 있습니다.

    이 정보를 사용하여 쉼표로 구분된 파일(.csv)을 **가져올** 수도 있습니다. 목록을 만든 후 AirPrint 서버의 목록을 **내보낼** 수도 있습니다.

3. 완료되면 **확인**을 선택하여 목록을 저장합니다.

AirPrinter 서버를 추가하려면 프린터의 IP 주소, 리소스 경로 및 포트가 필요합니다. 다음 단계에서는 이 정보를 가져오는 방법을 보여줍니다.

1. AirPrint 프린터와 동일한 로컬 네트워크(서브넷)에 연결된 Mac에서 **터미널**을 엽니다(**/Applications/Utilities**).
2. 터미널에서 `ippfind`를 입력하고 enter를 선택합니다.

    프린터 정보를 기록합니다. 예를 들어 `ipp://myprinter.local.:631/ipp/port1`과 유사한 항목을 반환할 수 있습니다. 첫 번째 부분은 프린터의 이름입니다. 마지막 부분(`ipp/port1`)은 리소스 경로입니다.

3. 터미널에서 `ping myprinter.local`을 입력하고 enter를 선택합니다.

   IP 주소를 기록합니다. 예를 들어 `PING myprinter.local (10.50.25.21)`과 유사한 항목을 반환할 수 있습니다.

4. IP 주소 및 리소스 경로 값을 사용합니다. 이 예제에서 IP 주소는 `10.50.25.21`이고, 리소스 경로는 `/ipp/port1`입니다.

## <a name="home-screen-layout-settings"></a>홈 화면 레이아웃 설정

이러한 설정은 iOS 디바이스의 도킹 및 홈 화면에서 앱 레이아웃 및 폴더를 구성합니다. 이 기능을 사용하려면 iOS 디바이스는 감독 모드에 있어야 하며 iOS 9.3 이상을 실행해야 합니다.

### <a name="dock"></a>도킹

**도킹** 설정을 사용하여 iOS 화면의 도킹에 최대 6개의 항목 또는 폴더를 추가합니다. 많은 디바이스는 적은 수의 항목을 지원합니다. 예를 들어 iPhone 디바이스는 최대 4개의 항목을 지원합니다. 이 경우 추가하는 처음 4개 항목만 디바이스에 표시됩니다.

1. **설정**에서 **홈 화면 레이아웃(감독 모드에서만 해당)** > **도킹** > **추가**를 선택합니다. 디바이스 도킹에 최대 **6**개의 항목(결합된 앱 및 폴더)을 추가할 수 있습니다.
2. **형식**에서 **앱** 또는 **폴더**를 추가하도록 선택합니다.

    - **앱 추가**: 이 옵션을 선택하여 화면의 도킹에 앱을 추가합니다. 입력:

      - **앱 이름**: 앱의 이름을 입력 합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. iOS 디바이스에 표시되지 *않습니다*.
      - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS 앱에 대한 번들 ID](#bundle-ids-for-built-in-ios-apps)(이 문서에서)를 참조하세요.

      **확인**을 선택하여 변경 내용을 저장합니다.

    - **폴더 추가**: 이 옵션을 선택하여 화면의 도킹에 폴더를 추가합니다. 

      폴더에서 페이지에 추가하는 앱은 목록과 동일한 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 다른 페이지로 이동합니다.

      1. **폴더 이름**을 입력합니다. 이 이름은 해당 디바이스에서 사용자에게 표시됩니다.
      2. **추가**를 선택하고, 다음 속성을 입력합니다.

          - **페이지 이름을**: 페이지에 대 한 이름을 입력 합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. iOS 디바이스에 표시되지 *않습니다*.
          - **앱 이름**: 앱의 이름을 입력 합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. iOS 디바이스에 표시되지 *않습니다*.
          - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS 앱에 대한 번들 ID](#bundle-ids-for-built-in-ios-apps)(이 문서에서)를 참조하세요.

      3. **추가**를 선택합니다. 디바이스 도킹에 최대 **20**개의 페이지를 추가할 수 있습니다.
      4. **확인**을 선택하여 변경 내용을 저장합니다.

> [!NOTE]
> 도킹 설정을 사용 하 여 아이콘을 추가 하면 홈 화면 및 페이지에 있는 아이콘 잠겨 있으며 이동할 수 없습니다. 이 iOS 및 Apple MDM 정책을 사용 하 여 설계 수 있습니다.

#### <a name="example"></a>예제

다음 예제에서 도킹 화면은 Safari, Mail 및 Stocks 앱만 표시합니다. 해당 속성을 표시하도록 Mail 앱이 선택되었습니다.

![샘플 iOS Dock 설정](./media/FfFiUcP.png)

iPhone에 정책을 할당할 때 도킹은 다음 이미지와 유사합니다.

![iPhone의 샘플 iOS 레이아웃 Dock](./media/bAgCe8F.png)

### <a name="pages"></a>페이지

홈 화면에 표시할 페이지와 각 페이지에 표시할 앱을 추가합니다. 페이지에 추가하는 앱은 목록과 동일한 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 다른 페이지로 이동합니다.

> [!TIP]
> 홈 화면과 페이지 목록의 항목을 다시 정렬하기 위해 항목을 끌어서 놓을 수 있습니다.

1. **설정**에서 **홈 화면 레이아웃(감독 모드에서만 해당)** > **페이지** > **추가**를 선택합니다. 디바이스에 최대 **40**개의 페이지를 추가할 수 있습니다.
2. **페이지 이름**을 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용되며, iOS 디바이스에는 표시되지 *않습니다*. 

    **추가**를 선택합니다. 디바이스에 최대 **60**개의 항목(결합된 앱 및 폴더)을 추가할 수 있습니다.

3. **형식**에서 **앱** 또는 **폴더**를 추가하도록 선택합니다.

    - **앱 추가**: 이 옵션을 선택하여 화면의 페이지에 앱을 추가합니다. 입력:

      - **앱 이름**: 앱의 이름을 입력 합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. iOS 디바이스에 표시되지 *않습니다*.
      - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS 앱에 대한 번들 ID](#bundle-ids-for-built-in-ios-apps)(이 문서에서)를 참조하세요.

      **확인**을 선택하여 변경 내용을 저장합니다.

    - **폴더 추가**: 이 옵션을 선택하여 화면의 도킹에 폴더를 추가합니다. 

      폴더에서 페이지에 추가하는 앱은 목록과 동일한 순서대로 왼쪽에서 오른쪽으로 정렬됩니다. 한 페이지에 들어가는 개수보다 많은 앱을 추가할 경우 앱이 다른 페이지로 이동합니다.

      1. **폴더 이름**을 입력합니다. 이 이름은 해당 디바이스에서 사용자에게 표시됩니다.
      2. **추가**를 선택하고, 다음 속성을 입력합니다.

          - **페이지 이름을**: 페이지에 대 한 이름을 입력 합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. iOS 디바이스에 표시되지 *않습니다*.
          - **앱 이름**: 앱의 이름을 입력 합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. iOS 디바이스에 표시되지 *않습니다*.
          - **앱 번들 ID**: 앱의 번들 ID를 입력합니다. 일부 예제는 [기본 제공 iOS 앱에 대한 번들 ID](#bundle-ids-for-built-in-ios-apps)(이 문서에서)를 참조하세요.

      3. **추가**를 선택합니다.
      4. **확인**을 선택하여 변경 내용을 저장합니다.

#### <a name="example"></a>예제

다음 예제에서 **Contoso**라는 새 페이지가 추가됩니다. 페이지는 친구 찾기와 설정 앱을 표시합니다. 해당 속성을 표시하도록 설정 앱이 선택되었습니다.

![iOS 홈 화면 설정 예제](./media/Jc2OxyX.png)

iPhone에 정책을 할당할 때 페이지는 다음 이미지와 유사합니다.

![수정된 홈 화면을 사용하는 iOS 디바이스](./media/Bd37PHa.png)

## <a name="app-notifications-settings"></a>앱 알림 설정

iOS 디바이스에 설치된 앱에서 알림을 전송하는 방식을 선택합니다. 이 설정은 iOS 9.3 이상을 실행하는 감독 모드 디바이스를 지원합니다.

1. **설정**에서 **앱 알림(감독 모드에서만 해당)** > **추가**를 선택합니다.

    ![Intune의 iOS 프로필에서 앱 알림 추가](./media/ios-macos-app-notifications.png)

2. 다음 속성을 입력합니다.

    - **앱 번들 ID**: 추가할 앱의 **앱 번들 ID**를 입력합니다. 일부 예제는 [기본 제공 iOS 앱에 대한 번들 ID](#bundle-ids-for-built-in-ios-apps)(이 문서에서)를 참조하세요.
    - **앱 이름**: 추가할 앱 이름을 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. 디바이스에 표시되지 *않습니다*.
    - **게시자**: 추가하는 앱의 게시자를 입력합니다. 이 이름은 Azure Portal에서 참조용으로 사용됩니다. 디바이스에 표시되지 *않습니다*.
    - **알림** - 앱에서 디바이스에 알림을 보내는 작업을 **사용하도록 설정**하거나, **사용하지 않도록 설정**합니다.
       - **알림 센터에 표시** - **사용하도록 설정**하면 앱이 디바이스 알림 센터에 알림을 표시할 수 있습니다. **사용하지 않도록 설정**은 앱이 알림 센터에서 알림을 표시하지 못하도록 방지합니다.
       - **잠금 화면에 표시**: 디바이스 잠금 화면의 앱에서 알림을 보려면 **사용**을 선택합니다. **사용하지 않도록 설정**은 앱이 잠금 화면에 알림을 표시하지 못하도록 방지합니다.
       - **경고 유형**: 디바이스가 잠금 해제되면 알림이 표시되는 방식을 선택합니다. 옵션은 다음과 같습니다.
         - **없음**: 알림이 표시되지 않습니다.
         - **배너**: 배너는 알림과 함께 간단하게 표시됩니다.
         - **모달**: 알림이 표시되면 사용자는 디바이스를 계속 사용하기 전에 수동으로 알림을 해제해야 합니다.
       - **앱 아이콘 배지**: 선택 **사용** 를 앱 아이콘 배지를 추가 합니다. 배지는 앱이 알림을 전송했음을 의미합니다.
       - **소리**: 알림이 전달될 때 소리를 재생하려면 **사용**을 선택합니다.

3. **확인**을 선택하여 변경 내용을 저장합니다. 원하는 앱을 계속해서 추가합니다. 완료되면 **확인**을 선택합니다.

## <a name="lock-screen-message-settings"></a>잠금 화면 메시지 설정

이러한 설정을 사용하여 로그인 창 및 잠금 화면에 사용자 지정 메시지 또는 텍스트를 표시합니다. 예를 들어 "분실 시, 돌려주기..." 메시지 및 자산 태그를 정보를 입력할 수 있습니다. 

이 기능은 다음을 실행하는 감독 디바이스를 지원합니다.

- iOS 9.3 이상

1. **설정**에서 **잠금 화면 메시지(감독 모드 전용)** 를 선택합니다.
2. 다음 설정을 입력합니다.

    - **자산 태그 정보**: 디바이스의 자산 태그에 대한 정보를 입력합니다. 예를 들어 `Owned by Contoso Corp` 또는 `Serial Number: {{serialnumber}}`을 입력합니다. 

      입력한 텍스트는 디바이스의 로그인 창 및 잠금 화면에 표시됩니다.

    - **잠금 화면 각주**: 디바이스를 분실했거나 도난당한 경우 디바이스를 되찾는 데 도움이 되는 정보를 입력합니다. 원하는 텍스트를 입력할 수 있습니다. 예를 들어 `If found, call Contoso at ...`와 같이 입력합니다.

    디바이스 토큰은 디바이스별 정보를 이러한 필드에 추가하는 데도 사용할 수 있습니다. 예를 들어 일련 번호를 표시하려면 `Serial Number: {{serialnumber}}`를 입력합니다. 잠금 화면에서 텍스트는 `Serial Number 123456789ABC`와 비슷하게 표시됩니다. 변수를 입력할 때 `{{ }}` 중괄호를 사용해야 합니다. [앱 구성 토큰](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 변수 목록이 포함됩니다. `deviceName` 또는 기타 디바이스 관련 값을 사용할 수도 있습니다.

    > [!NOTE]
    > UI에서 변수 유효성이 검사되지 않습니다. 따라서, 잘못된 입력으로 저장된 프로필을 볼 수 있습니다. 예를 들어 `{{devicename}}` 대신 `{{Devicename}}`을 입력하면 디바이스 고유의 이름 대신 리터럴 문자열이 표시될 수 있습니다.

3. 완료되면 **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="single-sign-on-settings"></a>Single Sign-On 설정

대부분의 LOB(기간 업무) 앱이 보안을 지원하려면 일부 수준의 사용자 인증이 필요합니다. 대부분의 경우 인증은 사용자가 동일한 자격 증명을 반복적으로 입력해야 하므로 사용자에게 번거롭습니다. 사용자 환경을 개선하기 위해 개발자는 SSO(Single Sign-On)를 사용하는 앱을 만들 수 있습니다. Single Sign-On을 사용하면 사용자가 자격 증명을 입력해야 하는 횟수를 줄입니다.

Single Sign-On을 사용하려면 다음이 있어야 합니다.

- 디바이스의 Single Sign-On에서 사용자 자격 증명 저장소를 찾도록 코딩된 앱
- iOS 디바이스 Single Sign-On용으로 구성된 Intune입니다.

1. **설정**에서 **Single Sign-On**을 선택합니다.

   ![Single Sign-On 창](./media/sso-blade.png)

2. 다음 설정을 입력합니다.

    - **AAD의 사용자 이름 특성**: Intune은 Azure AD에서 각 사용자에 대해 이 특성을 찾습니다. 그런 다음, Intune이 디바이스에 설치되는 XML을 생성하기 전에 해당 필드(예: UPN)를 채웁니다. 옵션은 다음과 같습니다.

      - **사용자 계정 이름**: UPN은 다음과 같은 방법으로 구문 분석을 합니다.

        ![사용자 이름 특성](media/User-name-attribute.png)

        **영역** 텍스트 상자에 입력한 텍스트로 영역을 덮어쓸 수도 있습니다.

        예를 들어 Contoso는 유럽, 아시아 및 북아메리카를 포함하는 여러 지역이 있습니다. Contoso는 아시아 사용자가 SSO를 사용하길 원하며, 앱은 `username@asia.contoso.com` 형식의 UPN이 필요합니다. **사용자 계정 이름**을 선택하면 각 사용자의 영역이 Azure AD에서 검색되며, `contoso.com`입니다. 따라서 아시아 사용자의 경우 **사용자 계정 이름**을 선택하고, `asia.contoso.com`을 입력합니다. 최종 사용자의 UPN은 `username@contoso.com` 대신 `username@asia.contoso.com`이 됩니다.

      - **Intune 디바이스 ID**: Intune은 Intune 디바이스 ID를 자동으로 선택합니다.

        기본적으로 앱은 디바이스 ID만 사용해야 합니다. 그러나 앱이 영역 및 디바이스 ID를 사용하는 경우 영역 텍스트 상자에 영역을 입력할 수 있습니다.

        > [!NOTE]
        > 기본적으로 디바이스 ID를 사용하는 경우 영역을 비워 둡니다.

      - **Azure AD 디바이스 ID**

    - **영역**: URL의 도메인 부분을 입력합니다. 예를 들어 다음과 같이 입력합니다. `contoso.com`
    - **Single Sign-On을 사용할 URL 접두사**: 사용자 Single Sign-On 인증이 필요한 조직의 모든 URL을 **추가**합니다.

        예를 들어 사용자가 이러한 사이트에 연결하는 경우 iOS 디바이스는 Single Sign-On 자격 증명을 사용합니다. 사용자는 추가 자격 증명을 입력할 필요가 없습니다. 다단계 인증이 활성화된 경우 사용자는 두 번째 인증을 입력해야 합니다.

        > [!NOTE]
        > 이러한 URL은 올바른 형식의 FQDN이어야 합니다. Apple에서는 `http://<yourURL.domain>` 형식의 FQDN이어야 합니다.

        URL 일치 패턴은 `http://` 또는 `https://`로 시작해야 합니다. 단순 문자열 일치가 수행되므로 `http://www.contoso.com/` URL 접두사는 `http://www.contoso.com:80/`과 일치하지 않습니다. iOS 10.0 이상에서는 단일 와일드카드 \*를 사용하여 일치하는 모든 값을 입력할 수 있습니다. 예를 들어 `http://*.contoso.com/`은 `http://store.contoso.com/` 및 `http://www.contoso.com` 둘 다와 일치합니다.

        `http://.com` 및 `https://.com` 패턴은 각각 모든 HTTP 및 HTTPS URL과 일치합니다.

    - **Single Sign-On을 사용할 앱**: Single Sign-On을 사용할 수 있는 최종 사용자 디바이스에서 앱을 **추가**합니다.

        `AppIdentifierMatches` 배열에는 앱 번들 ID와 일치하는 문자열이 포함되어야 합니다. 이러한 문자열은 정확히 일치하는 항목(예: `com.contoso.myapp`)이거나, \* 와일드카드 문자를 사용하여 번들 ID의 접두사 일치를 입력할 수 있습니다. 와일드카드 문자는 마침표 문자(.) 뒤에 표시되어야 하며, 문자열의 끝에 한 번만 나타날 수 있습니다(예: `com.contoso.*`). 와일드카드가 포함되면 번들 ID가 접두사로 시작하는 모든 앱에 계정에 대한 액세스 권한이 부여됩니다.

        **앱 이름**을 사용하여 번들 ID를 식별할 수 있도록 친숙한 이름을 입력합니다.

    - **자격 증명 갱신 인증서**: 인증에 인증서를 사용하는 경우(암호 아님) 인증 인증서로 기존 SCEP 또는 PFX 인증서를 선택합니다. 일반적으로 이 인증서는 VPN, Wi-Fi, 이메일 등의 다른 프로필에 대해 사용자에게 배포되는 것과 동일한 인증서입니다.

3. 완료되면 **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="web-content-filter-settings"></a>웹 콘텐츠 필터 설정

이러한 설정은 iOS 디바이스에서 브라우저 URL 액세스를 제어합니다.

1. **설정**에서 **웹 콘텐츠 필터(감독 모드에서만 해당)** 를 선택합니다.
2. **필터 형식**을 선택합니다. 옵션은 다음과 같습니다.

    - **URL 구성**: 불경한 언어 및 성적으로 노골적인 언어를 포함하는 성인 용어를 검색하는 Apple의 기본 제공 웹 필터를 사용합니다. 이 기능은 로드되는 각 웹 페이지를 평가하고, 부적절한 콘텐츠를 식별하고 차단합니다. 또한 필터로 검사하지 않으려는 URL을 추가할 수도 있습니다. 또는 Apple의 필터 설정에 관계없이 특정 URL을 차단합니다.

      - **Url 허용**: **추가** 허용 하려는 Url입니다. 이러한 URL은 Apple 웹 필터를 무시합니다.

        > [!NOTE]
        > 입력하는 URL은 Apple 웹 필터에서 평가하지 않으려는 URL입니다. 이러한 URL은 허용되는 웹 사이트 목록이 아닙니다. 허용되는 웹 사이트 목록을 만들려면 **필터 형식**을 **특정 웹 사이트만**으로 설정합니다.

        **확인**을 선택하여 변경 내용을 저장합니다.

      - **URL 차단**: Apple 웹 필터 설정에 관계없이 열기를 중지하려는 URL을 **추가**합니다.

        **확인**을 선택하여 변경 내용을 저장합니다.

    - **특정 웹 사이트만**(Safari 웹 브라우저만 해당): 이러한 URL은 Safari 브라우저의 책갈피에 추가됩니다. 사용자는 이 사이트**만** 방문이 허용됩니다. 다른 사이트를 열 수 없습니다. 사용자가 액세스할 수 있는 URL의 정확한 목록을 알고 있는 경우에만 이 옵션을 사용합니다.

      - **URL**: 허용하려는 웹 사이트의 URL을 입력합니다. 예를 들어 다음과 같이 입력합니다. `https://www.contoso.com`
      - **책갈피 경로**: 책갈피를 저장할 경로를 입력 합니다. 예를 들어 다음과 같이 입력합니다. `/Contoso/Business Apps` 경로를 추가하지 않으면 디바이스의 기본 책갈피 폴더에 책갈피가 추가됩니다.
      - **제목**: 책갈피에 대한 설명이 포함된 제목을 입력합니다.

      URL을 입력하지 않는 경우 최종 사용자는 `microsoft.com`, `microsoft.net` 및 `apple.com`을 제외한 웹 사이트에 액세스할 수 없습니다. 이러한 URL은 Intune에서 자동으로 허용됩니다.

      **확인**을 선택하여 변경 내용을 저장합니다.

## <a name="wallpaper-settings"></a>배경 무늬 설정

감독되는 iOS 디바이스에 사용자 지정 .png, .jpg 또는 .jpeg 이미지를 추가합니다. 예를 들어 잠금 화면에 회사 로고를 사용합니다.

이미지가 없는 프로필을 기존 이미지가 있는 디바이스에 할당하면 예기치 않은 동작이 발생할 수 있습니다. 예를 들어 이미지가 없는 프로필을 만듭니다. 이 프로필이 이미지가 이미 있는 디바이스에 할당됩니다. 이 시나리오에서는 이미지가 디바이스 기본값으로 변경되거나 원래 이미지가 디바이스에 남아있을 수 있습니다. 이런 동작은 Apple의 MDM 플랫폼에 의해 제어되고 제한됩니다.

- **표시 위치를 바탕 화면**: 이미지를 표시 하려면 장치에서 위치를 선택 합니다. 옵션은 다음과 같습니다.
  - **구성 되지 않은**: 사용자 지정 이미지를 장치에 추가 되지 않습니다. 디바이스는 운영 체제 기본값을 사용합니다.
  - **잠금 화면**: 잠금 화면에 이미지를 추가 합니다.
  - **홈 화면**: 홈 화면에 이미지를 추가 합니다.
  - **잠금 화면 및 홈 화면**: 잠금 화면 및 홈 화면에서 동일한 이미지를 사용 합니다.
- **배경 무늬 이미지**: 사용하려는 기존 .png, .jpg 또는 .jpeg 이미지를 업로드합니다. 파일 크기는 750KB 미만이어야 합니다. 추가한 이미지를 **제거**할 수도 있습니다.

> [!TIP]
> 잠금 화면 및 홈 화면에 다른 이미지를 표시하려면 잠금 화면 이미지를 사용하여 프로필을 만듭니다. 홈 화면 이미지를 사용하여 다른 프로필을 만듭니다. iOS 사용자 또는 디바이스 그룹에 두 프로필을 할당합니다.

## <a name="bundle-ids-for-built-in-ios-apps"></a>기본 제공 iOS 앱에 대한 번들 ID

다음 목록에서는 몇 가지 일반적인 기본 제공 iOS 앱의 번들 ID를 보여줍니다. 다른 앱의 번들 ID를 찾으려면 소프트웨어 공급업체에 문의하세요.

| 번들 ID                   | 앱 이름     | 게시자 |
|-----------------------------|--------------|-----------|
| com.apple.AppStore          | 앱 스토어    | Apple     |
| com.apple.calculator        | 계산기   | Apple     |
| com.apple.mobilecal         | 일정     | Apple     |
| com.apple.camera            | 카메라       | Apple     |
| com.apple.mobiletimer       | 시계        | Apple     |
| com.apple.compass           | 나침반      | Apple     |
| com.apple.MobileAddressBook | 연락처     | Apple     |
| com.apple.facetime          | FaceTime     | Apple     |
| com.apple.DocumentsApp      | 파일        | Apple     |
| com.apple.mobileme.fmf1     | 친구 찾기 | Apple     |
| com.apple.mobileme.fmip1    | 나의 iPhone 찾기  | Apple     |
| com.apple.gamecenter        | 게임 센터  | Apple     |
| com.apple.mobilegarageband  | GarageBand   | Apple     |
| com.apple.Health            | 상태       | Apple     |
| com.apple.Home              | 홈         | Apple     |
| com.apple.iBooks            | iBooks       | Apple     |
| com.apple.iMovie            | iMovie       | Apple     |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore       | iTunes Store | Apple     |
| com.apple.itunesu           | iTunes U     | Apple     |
| com.apple.Keynote           | 키노트      | Apple     |
| com.apple.mobilemail        | Mail         | Apple     |
| com.apple.Maps              | 맵         | Apple     |
| com.apple.MobileSMS         | 메시지     | Apple     |
| com.apple.Music             | 음악        | Apple     |
| com.apple.news              | 뉴스         | Apple     |
| com.apple.mobilenotes       | 참고        | Apple     |
| com.apple.Numbers           | 숫자      | Apple     |
| com.apple.Pages             | 페이지        | Apple     |
| com.apple.Photo-Booth       | Photo Booth  | Apple     |
| com.apple.mobileslideshow   | 사진       | Apple     |
| com.apple.podcasts          | Podcasts     | Apple     |
| com.apple.reminders         | 미리 알림    | Apple     |
| com.apple.mobilesafari      | Safari       | Apple     |
| com.apple.Preferences       | 설정     | Apple     |
| com.apple.SiriViewService   | Siri         | Apple     |
| com.apple.stocks            | 주식       | Apple     |
| com.apple.tips              | 팁         | Apple     |
| com.apple.TV                | TV           | Apple     |
| com.apple.videos            | 동영상       | Apple     |
| com.apple.VoiceMemos        | 음성 메모   | Apple     |
| com.apple.Passbook          | Wallet       | Apple     |
| com.apple.Bridge            | 보기        | Apple     |
| com.apple.weather           | 날씨      | Apple     |

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.

[macOS](macos-device-features-settings.md) 디바이스에 대한 디바이스 기능 프로필을 만들 수도 있습니다.
