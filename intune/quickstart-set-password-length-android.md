---
title: 빠른 시작 - Android 장치에 필요한 암호 길이 설정
titlesuffix: Microsoft Intune
description: 이 빠른 시작에서는 Microsoft Intune을 사용하여 Android 장치에 필요한 암호의 길이 설정합니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/17/2018
ms.topic: quickstart
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 81b4fa08-5333-4c54-9f49-8db5f6984ed2
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f925df731c3ddd45b13d976b0686d76d941c71e6
ms.sourcegitcommit: 2e88ec7a412a2db35034d30a70d20a5014ddddee
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49395298"
---
# <a name="quickstart-set-a-required-password-length-for-android-devices"></a>빠른 시작: Android 장치에 필요한 암호 길이 설정

이 빠른 시작에서는 Microsoft Intune을 사용하여 Android 장치의 정보에 대한 액세스 권한이 부여되기 전에 인력 중 Android 사용자에게 특정 길이의 암호를 입력하도록 요구합니다. 

> [!IMPORTANT]
> 암호 설정 이외에 인력을 보호하기 위한 다른 시스템 보안 설정도 고려해야 합니다. 자세한 내용은 [시스템 보안 설정](compliance-policy-create-android-for-work.md#system-security-settings)을 참조하세요.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. Azure Portal에서 **모든 서비스** > **Intune**을 선택하여 Intune을 찾습니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.

## <a name="create-a-device-compliance-policy"></a>장치 준수 정책 만들기
1. **Microsoft Intune** 블레이드를 연 후 **장치 준수** > **정책** > **정책 만들기**를 선택합니다.
2. **Android 준수**를 **이름**으로 추가합니다. 또한 **설명**을 추가합니다.
3. **플랫폼**에서 **Android**를 선택합니다. 
4. **설정** > **시스템 보안**을 선택하여 Android **시스템 보안**  블레이드를 표시합니다.
5. **암호** 섹션에서 **모바일 장치의 잠금을 해제하는 데 암호 필요** 옆에 있는 **필요**를 클릭합니다.
6. **최소 암호 길이** 옆에 **6**을 입력합니다.  

    ![Microsoft Intune에서 그룹 만들기 스크린샷](./media/quickstart-set-password-length-android-01.png)

7. 작업이 완료되면 **확인**을 클릭하여 **시스템 보안** 블레이드를 닫습니다. 
8. **확인**을 클릭하여 **Android 준수 정책** 블레이드를 닫습니다. 
9. **만들기**를 클릭하여 정책을 만듭니다.

정책을 성공적으로 만들었으면 **장치 준수 - 정책** 목록에 정책이 표시됩니다. 

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Intune을 사용하여 최소 6자 길이의 암호를 요구하는 인력의 Android 장치에 대한 준수 정책을 만들었습니다.

> [!div class="nextstepaction"]
> [자동 등록 설정](quickstart-setup-auto-enrollment.md)
