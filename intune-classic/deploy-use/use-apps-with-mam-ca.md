---
title: MAM CA가 있는 앱 사용
description: O365 서비스에 액세스할 수 있는 앱을 제어하도록 MAM CA에서 지원하는 방식을 이해합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2f313fcbfa26c8f82708f8f830404da97a3eca25
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31018484"
---
# <a name="what-to-expect-when-using-an-app-with-app-based-ca"></a>앱 기반 CA가 적용된 앱을 사용할 경우 어떤가요?

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

앱 기반 CA는 장치에 존재해야 하는 Broker 앱을 통해 승인된 응용 프로그램 ID를 확인합니다.
*  **iOS**에서는 **Azure Authenticator 앱**이 Broker 앱입니다.
* **Android**에서는 **Intune 회사 포털 앱**이 Broker 앱입니다. 

OneDrive 또는 Outlook과 같이 앱 기반 CA에서 지원되는 앱에 처음으로 로그인하는 최종 사용자에게는 Broker 앱을 설치하고 Azure AD에 장치를 등록하라는 메시지가 표시됩니다. Azure AD(이전의 Workplace Join)의 장치 등록에서 토큰을 발행한 장치 레코드와 인증서가 만들어집니다.  **MDM 등록**과 동일하지는 **않습니다**. 적용되는 관리 프로필 또는 정책이 없으며 장치에 앱에서 가져온 앱 인벤토리가 없습니다.  Broker 앱을 설치하고 장치를 등록하는 프로세스는 관리되는 앱을 처음 사용할 때만 실행됩니다.

다음은 장치에서 직접 파생된 속성 목록입니다.

* alternativeSecurityIds(Azure Active Directory 인증서 지문 및 공개 키 해시)
* deviceOSType
* deviceOSVersion
* displayName

> [!NOTE]
> Android 장치:
>   * 장치에 회사 포털 앱 설치는 필수 사항이지만 최종 사용자는 앱에 로그인하지 않아도 됩니다.
>   * 장치 등록은 OneDrive 또는 Outlook 앱을 통해 수행해야 합니다.

## <a name="to-remove-a-device-from-azure-ad-registration"></a>Azure AD 등록에서 장치 제거.
일반적으로 IT 관리자가 Azure AD 관리 콘솔을 통해 장치 등록을 제거할 수도 있고  장치 자체에서 최종 사용자가 제거할 수도 있습니다.

* **Azure AD 관리 콘솔**: Azure AD 관리 콘솔**에서 제거하려는 장치를 삭제합니다.
* **iOS 장치**: Azure Authenticator 앱을 열고 계정을 왼쪽으로 살짝 민 다음 등록 취소를 선택합니다.  
* **Android 장치**: 회사 포털 앱을 제거하거나 **시스템 설정**에서 계정을 제거합니다.

## <a name="app-based-ca-with-device-based-ca"></a>앱 기반 CA 및 장치 기반 CA  

[장치 규정 준수를 기반으로 하는 조건부 액세스](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)(<strong>장치 CA</strong>)를 [Intune 관리자 콘솔](https://manage.microsoft.com) 또는 [Azure AD Premium 관리 콘솔](https://manage.windowsazure.com)에 구성할 수 있습니다. 장치 CA를 사용하려면 사용자는 Intune 장치 규정 준수 정책을 준수하는 Intune 관리 장치 또는 도메인에 가입된 PC를 통해서만 Exchange Online에 연결해야 합니다.  사용자가 앱 기반 CA와 장치 CA 정책 모두를 대상으로 하는 보안 그룹 하나 이상에 속해 있는 경우 사용자는 두 가지 요구 사항 중 하나를 충족해야 합니다.
* 서비스에 액세스하는 데 사용되는 앱이 
* 에서 지원되는 모바일 앱이고 앱이 실행 중인 장치에 **iOS Authenticator(iOS 장치용)**, 또는 **회사 포털 앱(Android 장치용)** 이 설치되어 있어야 합니다.
* 서비스에 액세스하는 데 사용하는 장치가 **Intune에서 관리되고 Intune 장치 규정 준수 정책을 준수하거나**, 장치가 **도메인에 가입된 PC**입니다.  이에 대해 설명하는 몇 가지 예는 다음과 같습니다.
  * 사용자가 **네이티브 iOS 메일 앱**에서 연결할 경우 네이티브 메일 앱은 앱 기반 CA에서 지원되지 않으므로 사용자가 **관리되고 규정을 준수하는 장치**에 있어야 합니다.
  * 사용자가 **Windows 가정용 PC**에서 연결할 경우 **장치 CA 정책**이 적용되어 사용자가 도메인에 가입된 PC를 사용해야 합니다.

## <a name="next-steps"></a>다음 단계
[MAM 앱에 대한 Exchange Online 정책 만들기](mam-ca-for-exchange-online.md)

[최신 인증이 없는 앱 차단](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>참고 항목

[앱 보호 정책을 사용하여 앱 데이터 보호](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)
