---
title: 회사 포털 웹 사이트에서 암호를 재설정하는 방법 | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 06/23/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 4fa3255b-9d1e-42d5-bd8b-70963dcf2d86
searchScope:
- User help
ROBOTS: ''
ms.reviewer: jieyang
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 45b087b9617b783517f8296f1726891392764d5f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31019333"
---
# <a name="how-to-reset-your-device-passcode-from-the-company-portal-website"></a>회사 포털 웹 사이트에서 장치 암호를 재설정하는 방법

Intune에서 등록한 장치의 장치 PIN 또는 암호를 분실할 경우 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)를 사용하여 암호를 재설정할 수 있습니다. 회사 포털 웹 사이트에서 Intune에 등록한 컴퓨터 및 장치를 관리하고 회사 포털 앱을 사용할 때 수행할 수 있는 동일한 작업을 대부분 수행할 수 있습니다.

> [!NOTE]
> 회사에 등록된 장치를 사용하는 경우 회사 포털 웹 사이트에 암호 재설정 단추가 표시되지 않을 수도 있습니다. 그렇지 않으면 회사 지원팀에 암호를 재설정하도록 요청해야 합니다.

암호를 재설정하려면

1. [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)에서 __메뉴__ 단추 ![세 개의 가로 막대가 병렬로 누적된 메뉴 단추의 작은 이미지](/intune/media/CP_hamburger_menu.png)를 탭한 다음 __내 장치__를 선택합니다.

2. __내 장치__ 페이지에서 암호를 다시 설정할 장치의 이름을 선택합니다.

   ![목록에 없는 장치를 등록하거나 식별되지 않은 장치를 식별하라는 배너 프롬프트 위에 몇 개의 식별되지 않은 장치가 표시된 내 장치 페이지의 스크린샷](./media/macOS_enroll_002_tap_here_banner.png)

3. 장치가 팝업 창에서 열립니다. **암호 다시 설정** 단추를 선택합니다.

   ![이름 바꾸기, 제거, 장치 다시 설정, 암호 다시 설정, 원격 잠금 등 회사 포털 웹 사이트에서 선택한 장치에 대한 모든 옵션 ](./media/iwp-screen-with-all-options.png)

4. 암호를 다시 설정할 것인지 확인하고 그 후에 장치에서 로그아웃됨을 확인하는 배너가 표시됩니다. 다시 로그인하기 전에 5분 정도 기다려야 합니다.

   ![장치 암호 다시 설정 및 사용자가 로그아웃되는 방식에 대한 경고가 포함된 암호 다시 설정 배너 사용자 입력 단추는 로그아웃 및 취소입니다.](./media/iwp-reset-passcode-popup.png)

5. **로그아웃**을 선택하면 장치에서 암호가 제거됨을 알려주는 최종 메시지가 수신됩니다. 장치를 갖고 있지 않으면 장치에 대한 물리적 액세스 권한이 있는 누구든지 대부분의 정보(개인 또는 회사)에 액세스할 수 있으므로 암호를 제거하지 마세요. 

   ![장치 암호 다시 설정 및 암호가 장치에서 제거되는 방식에 대한 경고가 포함된 두 번째 암호 다시 설정 배너 또한 장치 설정으로 이동하여 새 암호를 설정하는 방법을 알려줍니다.](./media/iwp-reset-passcode-2nd-popup.png)

   장치에 따라 암호 유형이 서로 다릅니다.

   **Android**: 기존 암호를 제거하고 문자와 숫자를 사용하여 임시 암호를 만듭니다. 
  
   > [!NOTE]
   > Android 7.0 이상에서는 장치의 암호를 재설정할 수 없습니다. 암호를 잊은 경우 이러한 장치를 공장 설정으로 초기화해야 합니다.

   **iOS**: 기존 암호를 제거하고 임시 암호를 만들지 않습니다. 장치를 열거나 구매를 위해 Touch ID 지문 스캐너를 사용하는 경우 암호를 다시 설정해야 합니다.

   **Windows 10 Mobile**: 기존 암호를 제거하고 문자와 숫자를 모두 사용하여 임시 암호를 만듭니다. 로그인하는 데 Windows Hello의 얼굴 인식을 사용 중인 경우 해당 기능은 계속 지원됩니다.
    
   **Windows Phone 8.1**: 기존 암호를 제거하고 숫자를 사용하여 임시 암호를 만듭니다.

   Android 및 Windows 장치의 경우 **장치 세부 정보**에 임시 암호가 표시됩니다. 

6. 장치의 잠금을 해제한 후 장치 **설정**으로 이동하여 새 암호를 설정하거나 임시 암호를 변경합니다.

암호가 재설정되었는지 확인하는 알림을 보려면 회사 포털 웹 사이트의 오른쪽 맨 위에 있는 알림 플래그를 클릭합니다.

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. 연락처 정보는 [회사 포털 웹 사이트](https://portal.manage.microsoft.com#HelpDeskDialog)를 참조하세요.
