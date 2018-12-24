---
title: Microsoft Intune에서 iOS 디바이스에 사용자 지정 설정 추가 - Azure | Microsoft Docs
titleSuffix: ''
description: Apple Configurator 또는 Apple Profile Manager 도구에서 iOS 설정을 내보낸 다음, 이 설정을 Microsoft Intune으로 가져옵니다. 이 설정은 iOS 디바이스에서 사용자 지정 설정과 기능을 만들고 사용하고 제어할 수 있습니다. 그런 다음, 이 사용자 지정 프로필을 조직의 iOS 장비에 할당하거나 배포하여 기준 또는 표준을 만들 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 4c65b381afaad4b3ba65fa3d8eb49ba8f52b95d1
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183352"
---
# <a name="use-custom-settings-for-ios-devices-in-microsoft-intune"></a>Microsoft Intune의 iOS 디바이스에 대한 사용자 지정 설정

Microsoft Intune을 사용하면 "사용자 지정 프로필"을 사용하여 iOS 디바이스에 대한 사용자 지정 설정을 추가하거나 만들 수 있습니다. 사용자 지정 프로필은 Intune의 기능입니다. Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 추가하도록 설계되었습니다.

iOS 디바이스를 사용하는 경우 사용자 지정을 Intune으로 가져오는 방법은 두 가지가 있습니다.

- [Apple Configurator](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)
- [Apple Profile Manager](https://support.apple.com/profile-manager)

이 도구를 사용하여 설정을 구성 프로필로 내보낼 수 있습니다. Intune에서 이 파일을 가져온 다음, iOS 사용자 및 디바이스에 프로필을 할당합니다. 할당되면, 설정이 배포되며 조직의 iOS에 대한 기준 또는 표준도 만듭니다.

이 문서는 iOS 디바이스의 사용자 지정 프로필을 만드는 방법을 보여줍니다. 또한 Apple Configurator 및 Apple Profile Manager 사용에 대한 지침을 제공합니다.

## <a name="before-you-begin"></a>시작하기 전에

- **Apple Configurator**를 사용하여 구성 프로필을 만들 때, 내보내는 설정이 사용 중인 장치의 iOS 버전과 호환되는지 확인합니다. 호환되지 않는 설정 해결에 대한 정보를 보려면 [Apple 개발자](https://developer.apple.com/) 웹 사이트에서 **구성 프로필 참조** 및 **모바일 디바이스 관리 프로토콜 참조**를 검색하세요.

- **Apple Profile Manager**를 사용하는 경우 다음을 확인해야 합니다.

  - Profile Manager에서 [모바일 디바이스 관리](https://help.apple.com/serverapp/mac/5.7/#/apd05B9B761-D390-4A75-9251-E9AD29A61D0C)를 사용합니다.
  - Profile Manager에서 [iOS 디바이스](https://help.apple.com/profilemanager/mac/5.7/#/pm9onzap1984)를 추가합니다.
  - Profile Manager에서 장치를 추가한 후 **라이브러리에서** > **장치** >장치 선택 > **설정**으로 이동합니다. 디바이스에 대한 일반 설정을 입력합니다.

    이 파일을 다운로드하고 저장합니다. Intune 프로필에서 이 파일을 입력합니다.

  - Apple Profile Manager에서 내보내는 설정이 사용 중인 디바이스의 iOS 버전과 호환되는지 확인합니다. 호환되지 않는 설정 해결에 대한 정보를 보려면 [Apple 개발자](https://developer.apple.com/) 웹 사이트에서 **구성 프로필 참조** 및 **모바일 디바이스 관리 프로토콜 참조**를 검색하세요.

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
3. 다음 설정을 입력합니다.

    - **이름**: `ios custom profile` 등의 프로필의 이름을 입력합니다.
    - **설명**: 설정에 대한 설명을 입력합니다.
    - **플랫폼**: **iOS**를 선택합니다.
    - **프로필 유형**: **사용자 지정**을 선택합니다.

4. **사용자 지정 구성**에서 다음 설정을 입력합니다.

    - **사용자 지정 구성 프로필 이름**: 정책의 이름을 입력합니다. 이 이름은 디바이스 및 Intune 상태에서 표시됩니다.
    - **구성 프로필 파일** - Apple Configurator 또는 Apple Profile Manager를 사용하여 만든 구성 프로필을 찾아봅니다. 가져온 파일은 **파일 내용** 영역에 표시됩니다.

5. **확인** > **만들기**를 선택하여 Intune 프로필을 만듭니다. 완료되면 프로필이 **디바이스 구성 - 프로필** 목록에 나타납니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어지지만 아직 아무것도 하지 않습니다. 그런 다음, [프로필을 할당합니다](device-profile-assign.md).

[macOS 장치에서 프로필을 만드는](custom-settings-macos.md) 방법을 참조하세요. 