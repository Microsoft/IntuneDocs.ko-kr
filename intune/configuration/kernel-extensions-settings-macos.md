---
title: Microsoft Intune의 macOS 커널 확장 설정-Azure | Microsoft Docs
titleSuffix: ''
description: MacOS 장치에서 커널 확장을 사용 하도록 설정을 추가, 구성 또는 만듭니다. 또한 사용자가 승인 된 확장을 재정의 하거나, 팀 식별자에서 모든 확장을 허용 하거나, Microsoft Intune에서 특정 확장 또는 앱을 허용할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/10/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1306bfea1880061980413d283943e6521c1ac213
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71734494"
---
# <a name="macos-device-settings-to-configure-and-use-kernel-extensions-in-intune"></a>Intune에서 커널 확장을 구성 및 사용 하는 macOS 장치 설정

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

이 문서에서는 macOS 디바이스에서 제어할 수 있는 다양한 커널 확장 설정을 나열하고 설명합니다. MDM (모바일 장치 관리) 솔루션의 일부로, 이러한 설정을 사용 하 여 장치에서 커널 확장을 추가 하 고 관리 합니다.

Intune의 커널 확장 및 모든 필수 구성 요소에 대 한 자세한 내용은 [macOS 커널 확장 추가](../kernel-extensions-overview-macos.md)를 참조 하세요.

이러한 설정은 Intune에서 디바이스 구성 프로필에 추가된 다음, macOS 디바이스에 할당되거나 배포됩니다.

## <a name="before-you-begin"></a>시작하기 전에

[장치 커널 확장 구성 프로필을 만듭니다](../kernel-extensions-overview-macos.md).

> [!NOTE]
> 이러한 설정은 다른 등록 유형에 적용 됩니다. 다양 한 등록 유형에 대 한 자세한 내용은 [Macos 등록](../macos-enroll.md)을 참조 하세요.

## <a name="kernel-extensions"></a>커널 확장

### <a name="settings-apply-to-user-approved-automated-device-enrollment"></a>설정 적용 대상: 사용자 승인 됨, 자동 장치 등록

- **사용자 재정의 허용**: **허용** 을 설정 하면 사용자가 구성 프로필에 포함 되지 않은 커널 확장을 승인할 수 있습니다. **구성 되지 않음** (기본값)은 사용자가 구성 프로필에 포함 되지 않은 확장을 허용 하지 않도록 합니다. 즉, 구성 프로필에 포함 된 확장명만 허용 됩니다.

  이 기능에 대 한 자세한 내용은 [사용자 승인 커널 확장 로드](https://developer.apple.com/library/archive/technotes/tn2459/_index.html) (Apple 웹 사이트 열기)를 참조 하세요.

- **허용 된 팀 식별자**: 하나 이상의 팀 id를 허용 하려면이 설정을 사용 합니다. 입력 한 팀 Id로 서명 된 모든 커널 확장은 허용 되 고 신뢰할 수 있습니다. 즉,이 옵션을 사용 하 여 같은 팀 ID 내에 있는 모든 커널 확장을 허용할 수 있습니다 .이는 특정 개발자나 파트너가 될 수 있습니다.

  로드 하려는 유효한 서명 된 커널 확장의 팀 식별자를 **추가** 합니다. 팀 식별자를 여러 개 추가할 수 있습니다. 팀 식별자에는 영숫자 (문자와 숫자)와 10 자가 있어야 합니다. 예를 들어 다음과 같이 입력합니다. `ABCDE12345`

  팀 식별자를 추가한 후에는 삭제할 수도 있습니다.

  [팀 ID](https://help.apple.com/developer-account/#/dev55c3c710c) (Apple의 웹 사이트 열기)를 찾아 자세한 정보를 찾습니다.

- **허용 되는 커널 확장**: 특정 커널 확장을 허용 하려면이 설정을 사용 합니다. 입력 한 커널 확장만 허용 되거나 신뢰할 수 있습니다. 

  로드 하려는 커널 확장의 번들 식별자 및 팀 식별자를 **추가** 합니다. 서명 되지 않은 레거시 커널 확장의 경우 빈 팀 식별자를 사용 합니다. 커널 확장을 여러 개 추가할 수 있습니다. 팀 식별자에는 영숫자 (문자와 숫자)와 10 자가 있어야 합니다. 예를 들어 **번들 ID**에 `com.contoso.appname.macos`을 입력 하 고 **팀 식별자**로 `ABCDE12345`를 입력 합니다.

  > [!TIP]
  > MacOS 장치에서 커널 확장 (Kext)의 번들 ID를 가져오려면 다음을 수행할 수 있습니다.
  >
  > 1. 터미널에서 `kextstat | grep -v com.apple`을 실행 하 고 출력을 확인 합니다. 원하는 소프트웨어 또는 Kext를 설치 합니다. @No__t-0을 다시 실행 하 고 변경 내용을 확인 합니다.
  >
  >    터미널에서 `kextstat`은 OS의 커널 확장을 모두 나열 합니다. 
  >
  > 2. 장치에서 Kext에 대 한 정보 속성 목록 파일 (info.plist)을 엽니다. 번들 ID가 표시 됩니다. 각 Kext에는 내에 저장 된 info.plist 파일이 있습니다. 

> [!NOTE]
> 팀 식별자 및 커널 확장을 추가할 필요가 없습니다. 하나 또는 다른을 구성할 수 있습니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](../device-profile-assign.md)하고, 해당 [상태를 모니터링](../device-profile-monitor.md)합니다.
