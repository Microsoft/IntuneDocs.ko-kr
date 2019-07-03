---
title: 빠른 시작 - iOS에 대한 이메일 디바이스 프로필 만들기
titleSuffix: Microsoft Intune
description: iOS 디바이스가 회사 이메일에 안전하게 연결할 수 있도록 Microsoft Intune을 사용하여 이메일 디바이스 프로필을 만드는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/26/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbd8d81dfab46a1e752084aab75fbcf0d8104187
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044285"
---
# <a name="quickstart-create-an-email-device-profile-for-ios"></a>빠른 시작: iOS용 이메일 디바이스 프로필 만들기

이 빠른 시작에서는 iOS 디바이스에 대한 이메일 디바이스 프로필을 만드는 방법을 알아봅니다. 이 프로필은 회사 이메일에 연결하기 위해 iOS 디바이스의 기본 제공 이메일 앱에 필요한 설정을 지정합니다. 이메일 디바이스 프로필을 사용하면 디바이스 설정을 표준화할 수 있으며, 최종 사용자가 설정 작업을 수행할 필요 없이 자신의 개인용 디바이스에서 회사 이메일에 액세스할 수 있습니다. 메일을 더욱 안전하게 보호하려면 메일 프로필을 사용하여 디바이스가 규정을 준수하는지 확인한 다음, 규정을 준수하는 디바이스만 메일에 액세스할 수 있도록 조건부 액세스를 설정하면 됩니다. 이메일 프로필에 대한 자세한 내용은 [Microsoft Intune에서 이메일 설정을 구성하는 방법](email-settings-configure.md)을 참조하세요.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-an-ios-email-profile"></a>iOS 이메일 프로필 만들기
1. Intune에서 **디바이스 구성**을 선택하고 **프로필**을 선택합니다.
2. **프로필 만들기**를 선택합니다.
   
   ![iOS에 대한 이메일 프로필 만들기](media/quickstart-email-profile/ios-create-profile.png)

3. **이름** 아래에 새 프로필에 대해 설명하는 이름을 입력합니다. 이 예에서는 **iOS에서 회사 이메일 요구**를 입력합니다.
4. 다음 프로필 정보를 입력합니다.
   - **설명**에 **iOS 디바이스에 회사 이메일을 사용하도록 요구**를 입력합니다.
   - **플랫폼**에서 **iOS**를 선택합니다.
   - **프로필 유형**으로 **이메일**을 선택합니다.
    
     ![iOS에서 사용할 이메일 프로필 만들기](media/quickstart-email-profile/ios-email-profile-name.png)

5. **설정**을 선택하고 다음 설정을 입력합니다(그 외의 설정은 기본값 유지).
   - **메일 서버**: 이 빠른 시작에서는 **outlook.office365.com**을 입력합니다. 이 설정은 iOS 메일 앱이 이메일에 연결하는 데 사용할 이메일 서버의 Exchange 위치(URL)를 지정합니다.
   - **계정 이름**: **회사 이메일**을 입력합니다.
   - **AAD의 사용자 이름 특성**: 이 이름은 Intune이 Azure AD(Azure Active Directory)에서 가져오는 특성입니다. Intune은 이 이름을 사용하여 이 프로필의 사용자 이름을 동적으로 생성합니다. 이 빠른 시작에서는 **사용자 계정 이름**을 프로필의 사용자 이름으로 사용할 것입니다(예: user1@contoso.com).
   - **AAD의 메일 주소 특성**: 이 설정은 Exchange에 로그인하는 데 사용되는 Azure AD의 이메일 주소입니다. 이 빠른 시작에서는 **사용자 계정 이름**을 선택합니다.
   - **인증 방법**: 이 빠른 시작에서는 **사용자 이름 및 암호**를 선택합니다. (Intune에 대한 인증서를 이미 설정한 경우 **인증서**를 선택해도 됩니다.)
    
     ![iOS 사용에 대한 이메일 프로필 만들기](media/quickstart-email-profile/ios-email-profile.png)

6. **확인**을 선택합니다.
7. **만들기**를 선택합니다. 프로필 목록에 새 프로필이 나타나고 대시보드가 표시되므로 프로필이 iOS 디바이스 및 iOS 사용자에게 어떻게 할당되었는지 모니터링할 수 있습니다.
8. **할당**을 선택합니다.
9. **포함** 탭을 선택하고 **모든 사용자 및 모든 장치**를 선택합니다. 
10. **저장**을 선택합니다.

## <a name="clean-up-resources"></a>리소스 정리
여기서 만든 프로필을 다른 자습서 또는 테스트에 더 이상 사용하지 않으려는 경우 지금 삭제할 수 있습니다.
1. Intune에서 **디바이스 구성**을 선택하고 **프로필**을 선택합니다.
2. 여기서 만든 테스트 프로필 **iOS에서 회사 이메일 요구**를 선택합니다.
3. 프로필 옆에서 줄임표( **...** )를 선택하고 **삭제**를 선택합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 iOS 디바이스에 대한 이메일 프로필을 만들었습니다. 이제 이 프로필을 사용하여 프로필과 일치하지 않는 iOS 디바이스를 비준수로 표시하는 준수 정책을 만들어서 iOS 디바이스의 규정 준수 여부를 확인할 수 있습니다. 보다 강력한 보호를 원하는 경우 비준수 iOS 디바이스의 메일 액세스를 차단하는 조건부 액세스 정책을 만들면 됩니다. 디바이스 준수 정책에 대한 자세한 내용은 [Intune에서 디바이스 준수 정책 시작](device-compliance-get-started.md)을 참조하세요.

> [!div class="nextstepaction"]
> [자습서: 관리 디바이스에서 Exchange Online 이메일 보호](tutorial-protect-email-on-enrolled-devices.md)
