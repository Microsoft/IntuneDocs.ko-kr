---
title: Microsoft Intune - Azure에서 장치 프로필 만들기 | Microsoft Docs
description: 플랫폼 형식 선택과 Azure Portal 내에서 설정 구성을 비롯하여 Microsoft Intune에서 장치 프로필을 추가하거나 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d98aceff-eb35-4e3e-8e40-5f300e7335cc
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3f62e306574606ffa1eb1e6f242c3cb30b1a9c1b
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744655"
---
# <a name="create-a-device-profile-in-microsoft-intune"></a>Microsoft Intune에서 장치 프로필 만들기

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

## <a name="create-the-profile"></a>프로필 만들기
1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Microsoft Intune**을 검색합니다.

2. **Microsoft Intune**에서 **장치 구성**를 선택한 다음, **프로필**을 선택합니다. 그런 다음, **프로필 만들기**를 선택합니다.

3. 다음 속성을 입력합니다.

   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 설정에 대한 설명을 입력합니다. 선택 사항이지만 입력하는 것이 좋습니다.
   - **플랫폼**: 플랫폼 형식을 선택 합니다.  

       - **OWA(Outlook Web Access)**
       - **Android for Work**
       - **Android**
       - **macOS**
       - **Windows Phone 8.1**
       - **Windows 8.1 이상**
       - **Windows 10 이상**

   - **프로필 유형** - 만들려는 유형을 선택합니다. 목록은 선택한 플랫폼에 따라 달라집니다.
   - **설정** - 다음 항목에서는 각 프로필 유형의 설정에 대해 설명합니다.

       -  [장치 기능](device-features-configure.md)
       -  [장치 제한 사항](device-restrictions-configure.md)
       -  [엔드포인트 보호](endpoint-protection-configure.md)
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
