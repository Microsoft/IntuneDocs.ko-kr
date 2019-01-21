---
title: Microsoft Intune을 사용하여 iOS 디바이스에서 잠금 화면 사용자 지정 - Azure | Microsoft Docs
titlesuffix: ''
description: iOS용 공유 디바이스 구성 설정을 사용하여 iOS 디바이스 잠금 화면에 정보를 표시하는 데 사용할 수 있는 Microsoft Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/12/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9f4d75d795421c761398f349c324b498fd21ca01
ms.sourcegitcommit: 4a7421470569ce4efe848633bd36d5946f44fc8d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2019
ms.locfileid: "54203079"
---
# <a name="add-custom-messages-to-lock-screen-and-login-window-on-ios-devices-using-microsoft-intune"></a>Microsoft Intune을 사용하여 iOS 디바이스에서 잠금 화면 및 로그인 창에 사용자 지정 메시지 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서에서는 iOS 디바이스 잠금 화면 및 로그인 창에 정보를 표시하는 데 사용할 수 있는 Microsoft Intune 설정을 설명합니다. 

이러한 설정을 사용하여 로그인 창 및 잠금 화면에 사용자 지정 메시지 또는 텍스트를 표시합니다. 예를 들어 "분실 시, 돌려주기..." 메시지 및 자산 태그를 정보를 입력할 수 있습니다.

이 설정은 iOS 9.3 이상을 실행하는 감독 모드 디바이스를 지원합니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링하고 **Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 프로필에 대한 **이름**과 **설명**을 입력합니다.
4. **플랫폼**에서 **iOS**를 선택합니다. **프로필 형식**에서 **디바이스 기능**을 선택합니다.
5. **설정**에서 **잠금 화면 메시지(감독 모드 전용)** 를 선택합니다. 다음 설정을 구성합니다.

    - **자산 태그 정보**: 디바이스의 자산 태그에 대한 정보를 입력합니다. 예를 들어 다음과 같이 입력합니다. `123xyz`

        입력한 텍스트는 디바이스의 로그인 창 및 잠금 화면에 표시됩니다.

    - **잠금 화면 각주**: 디바이스를 분실했거나 도난당한 경우 디바이스를 되찾는 데 도움이 되는 정보를 입력합니다. 필드에 원하는 모든 텍스트를 입력할 수 있습니다. 예를 들어 `If found, call Contoso at ...`와 같이 입력합니다.

    디바이스 토큰은 디바이스별 정보를 이러한 필드에 추가하는 데도 사용할 수 있습니다. 예를 들어 일련 번호를 표시하려면 `Serial Number: {{serialnumber}}`를 입력합니다. 잠금 화면에서 텍스트는 `Serial Number 123456789ABC`와 비슷하게 표시됩니다. 변수를 입력할 때 `{{ }}` 중괄호를 사용해야 합니다. [앱 구성 토큰](app-configuration-policies-use-ios.md#tokens-used-in-the-property-list)에는 사용할 수 있는 변수 목록이 포함됩니다. `deviceName` 또는 기타 디바이스 관련 값을 사용할 수도 있습니다.

6. 완료되면 **확인** > **확인** > **만들기**를 선택합니다. 프로필이 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.
