---
title: Microsoft Intune - Azure에서 디바이스 프로필 만들기 | Microsoft Docs
description: 플랫폼 형식 선택과 Azure Portal 내에서 설정 구성을 비롯하여 Microsoft Intune에서 디바이스 프로필을 추가하거나 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: befffd3f3ae43531d8a5f541e6f7cd4e43f4a2b0
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55845793"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune에서 디바이스 프로필 만들기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링하고 **Intune**을 선택합니다.

2. **디바이스 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.

3. 다음 속성을 입력합니다.

   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
   - **플랫폼**: 플랫폼 형식을 선택합니다.  

       - **OWA(Outlook Web Access)**
       - **Android 엔터프라이즈**
       - **iOS**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 이상**
       - **Windows 10 이상**

   - **프로필 유형**: 만들려는 유형을 선택합니다. 목록은 선택한 플랫폼에 따라 달라집니다.
   - **설정**: 다음 아티클에서는 각 프로필의 설정에 대해 설명합니다.

       -  [디바이스 기능](device-features-configure.md)
       -  [디바이스 제한 사항](device-restrictions-configure.md)
       -  [엔드포인트 보호](endpoint-protection-configure.md)
       -  [ID 보호](identity-protection-configure.md)  
       -  [키오스크](kiosk-settings.md)
       -  [전자 메일](email-settings-configure.md)
       -  [VPN](vpn-settings-configure.md)
       -  [Wi-Fi](wi-fi-settings-configure.md)
       -  [Windows 10](education-settings-configure.md) 및 [iOS](wi-fi-settings-ios.md) 교육
       -  [Windows 10 버전 업그레이드](edition-upgrade-configure-windows-10.md)
       -  [iOS 업데이트 정책](software-updates-ios.md)
       -  [인증서](certificates-configure.md)
       -  [Windows Information Protection](windows-information-protection-configure.md)
       -  [사용자 지정](custom-settings-configure.md)

     ![프로필 만들기 스크린샷](./media/create-device-profile.png)

4. 완료된 경우 **만들기**를 선택합니다.

프로필이 만들어지고 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계
[프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
