---
title: Microsoft Intune에서 Google Play 보호 준수 사용
titleSuffix: ''
description: Google Play 보호를 사용하도록 설정하기 위해 Android 디바이스에 대한 준수 정책을 만드는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: E9810BEB-000A-4DFB-B5C7-A22A92082B22
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5963cb7de2994feb41c4679e87970aec4f127de5
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848830"
---
# <a name="how-to-create-a-device-compliance-policy-to-enable-google-play-protect"></a>Google Play 보호를 사용하도록 설정하기 위해 디바이스 준수 정책을 만드는 방법

GPP(Google Play 보호) 준수를 확인하기 위해 Android 플랫폼에 대한 새로운 준수 정책을 만들 수 있습니다.

이러한 설정이 필요한 준수 정책은 Android 사용자 또는 디바이스 그룹을 대상으로 할 수 있습니다. 디바이스에 이러한 설정이 사용하도록 설정되어 있지 않은 경우 해당 디바이스는 준수하지 않는 것입니다.

## <a name="create-a-compliance-policy"></a>규정 준수 정책 만들기

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
2. **관리** 그룹에서 **디바이스 준수**를 선택합니다. 
3. **정책**을 선택하고 **정책 만들기**를 선택합니다.
4. 정책 **이름** 및 **설명**을 입력합니다.
5. 플랫폼으로 **Android**를 선택합니다.
6. **설정** > **장치 상태**를 선택합니다.
7. **Google Play 보호** 설정을 구성합니다.
8. Google Play 보호 설정을 지정했으면 **시스템 보안** 및 **디바이스 속성** 설정을 지정합니다. 작업이 끝나면 **확인**을 선택합니다.

## <a name="configure-the-google-play-protect-settings"></a>Google Play 보호 설정 구성

 - **Google Play 서비스가 구성되었습니다.**  
   Google Play 서비스 앱을 설치하고 사용하도록 설정해야 합니다. Google Play 서비스는 보안 업데이트를 허용하며, 인증된 Google 디바이스의 많은 보안 기능에 대한 기본 수준 종속성입니다.
 - **최신 보안 공급자**  
   최신 보안 공급자가 알려진 취약성으로부터 디바이스를 보호할 수 있도록 합니다.
 - **앱에서 위협 검색**  
   Android **앱 확인** 기능을 사용하도록 설정해야 합니다.
    > [!Note]  
    > 레거시 Android 플랫폼에서 이 기능은 준수 설정입니다. Intune에서는 디바이스 수준에서 이 설정이 사용하도록 설정되어 있는지만 확인할 수 있습니다. Android 회사 프로필이 있는 디바이스에서 이 설정은 구성 정책 설정으로 찾을 수 있습니다. 이를 통해 관리자는 디바이스에 대한 설정을 사용하도록 설정할 수 있습니다.

    엔터프라이즈에서 Android 회사 프로필을 사용하는 경우 등록된 디바이스에 대해 **앱에서 위협 검색**을 사용하도록 설정할 수 있습니다. 디바이스 프로필을 설정하고 시스템 보안 설정이 필요합니다. 자세한 내용은 [Microsoft Intune의 Android 회사 프로필 디바이스 제한 설정](device-restrictions-android-for-work.md)을 참조하세요.

 - **SafetyNet 디바이스 증명**  
   충족해야 하는 SafetyNet 디바이스 증명 무결성 수준을 설정합니다. 수준으로는 **구성되지 않음**, **기본 무결성 검사** 및 **기본 무결성 및 인증 디바이스 검사**가 있습니다.




## <a name="next-steps"></a>다음 단계

Intune 디바이스 준수 정책 작업에 대한 자세한 내용은 [Intune 디바이스 준수 정책 시작](device-compliance-get-started.md)을 참조하세요.
