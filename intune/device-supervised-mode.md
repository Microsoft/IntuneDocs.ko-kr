---
title: Microsoft Intune을 사용하여 iOS 감독 모드 설정
titleSuffix: ''
description: Intune을 사용하여 iOS 감독 모드를 설정하는 방법에 대해 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 8190814-07f0-42d8-9b3a-87c67dd2b7ed
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: c69fa80fb1c1f539252b8e25eb839090b87c97f5
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52190237"
---
# <a name="turn-on-ios-supervised-mode"></a>iOS 감독 모드 설정


[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Apple iOS 감독 모드는 Apple 디바이스를 관리하는 경우 관리자에게 더 많은 옵션을 제공하여 회사에서 소유한 디바이스를 대량으로 배포하는 데 유용합니다. 예를 들어, AirDrop 또는 사용자가 디바이스의 이름을 변경하는 것을 제한하거나 방지할 수 있습니다. 감독 모드가 필요한 설정 목록은 [Intune에서 iOS 디바이스 제한 설정](device-restrictions-ios.md)을 참조하세요.

Intune은 Apple [DEP(디바이스 등록 프로그램)](device-enrollment-program-enroll-ios.md)의 일부로 감독 모드를 지원합니다.

감독이 필요한 Apple 컨트롤의 목록은 Apple의 [페이로드 설정 참조](http://help.apple.com/configurator/mac/2.4/#/cad5370d089)를 참조하세요.

## <a name="turn-on-supervised-mode-during-enrollment"></a>등록 중 감독 모드 설정

Intune에서 [DEP에 Apple 등록 프로필을 만들](https://docs.microsoft.com/intune/device-enrollment-program-enroll-ios#create-an-apple-enrollment-profile) 때 디바이스에 대해 감독 모드를 설정할 수 있습니다. **장치 관리 설정** 아래에서 **감독 됨** 상자를 확인합니다.

## <a name="turn-on-supervised-mode-after-enrollment"></a>등록 후 감독 모드 설정

등록 후 감독 모드를 설정하는 유일한 방법은 iOS 디바이스를 Mac에 연결하고 [Apple Configurator를 사용](apple-configurator-enroll-ios.md)(디바이스가 다시 설정됨)하는 것입니다. 등록 후에는 Intune에서 디바이스를 감독 모드로 구성할 수 없습니다.

## <a name="identify-a-supervised-device"></a>감독된 디바이스 확인

디바이스가 감독되는지 확인하려면 잠금 화면 또는 **About** 페이지를 확인합니다.
- 디바이스 잠금 화면에 **이 iPhone은 "회사 이름"으로 관리됩니다**라는 메시지가 나타납니다.
- 디바이스의 **About** 페이지에 **이 iPhone은 감독됩니다. 회사 이름으로 인터넷 트래픽을 모니터링하고 이 디바이스를 찾을 수 있습니다**라는 메시지가 나타납니다.

## <a name="next-steps"></a>다음 단계

다른 디바이스 관리 옵션은 [Microsoft Intune 디바이스 관리란?](device-management.md)을 참조하세요.
