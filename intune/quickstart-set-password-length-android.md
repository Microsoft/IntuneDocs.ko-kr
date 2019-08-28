---
title: 빠른 시작 - Android 디바이스에 대한 암호 규정 준수 정책
titleSuffix: Microsoft Intune
description: 이 빠른 시작에서는 Microsoft Intune을 사용하여 Android 디바이스에 필요한 암호의 길이를 설정합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 08/23/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 30c4d5976b7f743a12a9691878e2b7031e373b1d
ms.sourcegitcommit: c8cb314256c4896e838918f015ffaefb8f00ace5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2019
ms.locfileid: "70001841"
---
# <a name="quickstart-create-a-password-compliance-policy-for-android-devices"></a>빠른 시작: Android 디바이스에 대한 암호 규정 준수 정책 만들기

이 빠른 시작에서는 Microsoft Intune을 사용하여 Android 디바이스의 정보에 대한 액세스 권한이 부여되기 전에 인력 중 Android 사용자에게 특정 길이의 암호를 입력하도록 요구합니다. 

Intune 디바이스 준수 정책은 디바이스가 준수하는 것으로 간주되기 위해 충족해야 하는 규칙과 설정을 지정합니다. 준수 정책을 조건부 액세스와 함께 사용하여 회사 리소스에 대한 액세스를 허용하거나 차단할 수 있습니다. 디바이스 보고서를 가져오 고 비준수에 대해 조치를 할 수 있습니다.

> [!IMPORTANT]
> 암호 설정 이외에 인력을 보호하기 위한 다른 시스템 보안 설정도 고려해야 합니다. 자세한 내용은 [시스템 보안 설정](compliance-policy-create-android-for-work.md)을 참조하세요.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. 

## <a name="create-a-device-compliance-policy"></a>디바이스 준수 정책 만들기

이 빠른 시작에서는 Microsoft Intune을 사용하여 Android 디바이스의 정보에 대한 액세스 권한이 부여되기 전에 업무용 Android 사용자에게 특정 길이의 암호를 입력하도록 요구합니다.

1. Intune에서 **디바이스 준수** > **정책** > **정책 만들기**를 선택합니다.
2. **Android 준수**를 **이름**으로 추가합니다. 또한 **설명**을 추가합니다.
3. **플랫폼**에서 **Android**를 선택합니다. 
4. **설정** > **시스템 보안**을 선택하여 Android **시스템 보안**  블레이드를 표시합니다.
5. **모바일 디바이스의 잠금을 해제하는 데 암호 요구** 옆에 있는 **필요**를 클릭합니다.
6. **필수 암호 유형** 옆의 **최소 숫자**를 선택합니다.
7. **최소 암호 길이** 옆에 있는 **6**을 입력합니다. 

    ![Microsoft Intune에서 그룹 만들기 스크린샷](media/quickstart-set-password-length-android/quickstart-set-password-length-android-01.png)

7. 완료되면 **확인** > **확인** > **만들기**를 클릭하여 정책을 만듭니다.

정책을 성공적으로 만들었으면 해당 정책은 디바이스 준수 정책 목록에 나타납니다. 

## <a name="clean-up-resources"></a>리소스 정리

정책이 더 이상 필요 없으면 정책을 삭제합니다. 이렇게 하려면 준수 정책을 선택하고 **삭제**를 클릭합니다.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Intune을 사용하여 최소 6자 길이의 암호를 요구하는 업무용 Android 디바이스 사용자에 대한 준수 정책을 만들었습니다. 준수 정책 만들기에 대한 자세한 내용은 [Intune에서 디바이스 준수 정책 시작](device-compliance-get-started.md)을 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: 비규격 디바이스로 알림 보내기](quickstart-send-notification.md)
