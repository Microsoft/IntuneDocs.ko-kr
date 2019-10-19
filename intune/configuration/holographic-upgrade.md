---
title: Windows Holographic for Business으로 업그레이드
titleSuffix: Microsoft Intune
description: Windows Holographic을 실행하는 디바이스를 Windows Holographic for Business로 업그레이드하는 방법을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6342ed23f67c37c2f5084e58594294d826a28e40
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72506723"
---
# <a name="upgrade-devices-running-windows-holographic-to-windows-holographic-for-business"></a>Windows Holographic을 실행하는 디바이스를 Windows Holographic for Business로 업그레이드

Microsoft Intune에는 디바이스를 관리하고 보호할 수 있는 많은 설정이 포함되어 있습니다. 이 문서에서는 Windows Holographic 디바이스를 Windows Holographic for Business로 업그레이드하기 위한 설정을 나열하고 설명합니다. 이러한 설정은 Intune에서 디바이스에 푸시되거나 배포되는 업그레이드 구성 프로필에서 생성됩니다.

MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 Windows Holographic 디바이스를 업그레이드합니다. Microsoft HoloLens의 경우 Commercial Suite를 구입하여 업그레이드에 필요한 라이선스를 가져올 수 있습니다. 자세한 내용은 [Windows Holographic for Business 기능 잠금 해제](https://docs.microsoft.com/hololens/hololens1-upgrade-enterprise)를 참조하세요.

이 기능에 대한 자세한 내용은 [Windows 10 버전 업그레이드 또는 S 모드 사용](../edition-upgrade-configure-windows-10.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[디바이스 구성 프로필을 만듭니다](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>버전 업그레이드

- **업그레이드할 버전**: **Windows 10 Holographic for Business**를 선택합니다.
- **라이선스 파일**: 제공된 XML 라이선스 파일을 찾아 선택합니다.

  ![Holographic for Business 라이선스 정보가 포함된 XML 파일 이름 입력](./media/holographic-upgrade/Holographic-edition-upgrade.png)
 
## <a name="next-steps"></a>다음 단계

프로필이 만들어졌지만 아직 아무것도 하지 않습니다. [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](../device-profile-monitor.md)합니다.

[Windows 10 이상](edition-upgrade-windows-settings.md) 디바이스에 대한 버전 업그레이드 프로필을 만들 수도 있습니다.
