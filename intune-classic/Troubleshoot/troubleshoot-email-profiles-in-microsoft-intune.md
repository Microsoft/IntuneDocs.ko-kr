---
title: 메일 프로필 문제 해결
description: 전자 메일 프로필 문제와 이 문제를 해결하는 방법입니다.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f5c944ea-32a6-48af-bb57-16d5f1f3c588
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e001d1df510ac249687be9f5690c16f0a738c3e2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31013741"
---
# <a name="troubleshoot-email-profiles-in-microsoft-intune"></a>Microsoft Intune에서 전자 메일 프로필 문제 해결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

여기에서는 일부 메일 프로필 문제와 이 문제를 해결하는 방법을 제공합니다.

이 정보로 문제가 해결되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)을 참조하여 도움을 얻을 수 있는 다른 방법을 찾아보세요.


## <a name="unable-to-send-images-from--email-account"></a>전자 메일 계정에서 이미지를 보낼 수 없습니다.
자동으로 구성된 전자 메일 계정의 사용자는 자신의 장치에서 그림이나 이미지를 보낼 수 없습니다.
**Allow e-mail to be sent from third-party applications**(타사 응용 프로그램에서 전자 메일을 보내도록 허용) 옵션이 활성화되지 않은 경우에 이런 일이 발생합니다.

### <a name="intune-solution"></a>Intune 솔루션

1.  Microsoft Intune 관리 콘솔을 열고 **정책** 작업 &gt; **구성 정책**을 선택합니다.

2.  메일 프로필을 선택하고 **편집**을 선택합니다.

3.  **Allow e-mail to be sent from third-party applications**(타사 응용 프로그램에서 전자 메일을 보내도록 허용)을 선택합니다.

### <a name="configuration-manager-integrated-with-intune-solution"></a>Intune 솔루션과 통합된 Configuration Manager

1.  Configuration Manager 콘솔 &gt;**자산 및 호환성**을 엽니다.

2.  **개요**  -&gt; **준수 설정**  -&gt; **회사 리소스 액세스**를 확장하고 **메일 프로필**을 선택합니다.

3.  전자 메일 프로필을 마우스 오른쪽 단추로 클릭하고 **속성**을 엽니다.

4.  **동기화 설정** 탭에서 **타사 응용 프로그램에서 전자 메일을 보내도록 허용**을 선택합니다.


## <a name="device-already-has-an-email-profile-installed"></a>장치에 메일 프로필이 이미 설치되어 있음

사용자가 Intune에서 프로필을 프로비전하기 전에 이미 메일 프로필을 설치한 경우에 Intune 메일 프로필 배포 결과는 장치 플랫폼에 따라 달라집니다.

-**iOS**: Intune에서는 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. 사용자가 만든 중복 메일 프로필에서는 Intune 관리자가 만든 프로필 배포가 차단됩니다. iOS 사용자는 일반적으로 메일 프로필을 만든 후에 등록을 하므로 이것은 일반적인 문제입니다. 회사 포털에서는 수동으로 구성된 메일 프로필 때문에 규정에 맞지 않음을 사용자에게 알리며, 프로필을 제거하라는 메시지를 표시합니다. 사용자는 Intune 프로필을 배포할 수 있도록 메일 프로필을 제거해야 합니다. 이 문제를 방지하려면 메일 프로필을 설치하기 전에 먼저 등록하고 Intune의 프로필 배포를 허용하라고 안내합니다.

-**Windows**: Intune에서는 호스트 이름 및 메일 주소를 기반으로 기존에 중복된 메일 프로필을 검색합니다. Intune은 사용자가 만든 기존 메일 프로필을 덮어씁니다.

-**Samsung KNOX Standard**: Intune에서는 메일 주소를 기반으로 중복된 메일 계정을 식별하고 Intune 프로필로 덮어씁니다. 사용자가 해당 계정을 구성하더라도 Intune 프로필에서 다시 덮어씁니다. 이렇게 하면 계정 구성이 덮어쓰기되는 사용자는 혼동될 수 있습니다.

Samsung KNOX에서는 프로필 식별에 호스트 이름을 사용하지 않으므로 여러 호스트에서 동일한 메일 주소로 배포할 메일 프로필을 여러 개 만들지 않는 것이 좋습니다. 이렇게 하면 각각 덮어쓰게 됩니다.

## <a name="error--0x87d1fde8-for-knox-standard-device"></a>KNOX Standard 장치에 대한 오류 0x87D1FDE8
**문제**: 다양한 Android 장치에 대한 삼성 KNOX Standard용 Exchange Active Sync 메일 프로필을 만들고 배포한 후 장치의 속성 &gt; 정책 탭에 **0x87D1FDE8** 또는 **조정 실패**라는 오류가 보고됩니다.

삼성 KNOX 및 소스 정책에 대한 EAS 프로필 구성을 확인하세요. Samsung KNOX 동기화 옵션은 더 이상 지원되지 않으며, 해당 옵션은 프로필에서 선택하면 안 됩니다. 장치가 최대 24시간까지 정책을 처리하기에 충분한 시간을 갖도록 합니다.

## <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라 Microsoft 지원에 문의하세요.
