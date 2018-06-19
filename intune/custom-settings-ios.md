---
title: iOS를 실행하는 장치에 대한 Microsoft Intune 사용자 지정 설정
titleSuffix: ''
description: Microsoft Intune의 iOS 사용자 지정 프로필에서 사용할 수 있는 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e0ae4e757264465043ee6992033710c5a81d7157
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31831303"
---
# <a name="microsoft-intune-custom-device-settings-for-devices-running-ios"></a>iOS를 실행하는 장치에 대한 Microsoft Intune 사용자 지정 장치 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[Apple Configurator 도구](https://itunes.apple.com/app/apple-configurator-2/id1037126344?mt=12)를 사용하여 만든 설정을 Microsoft Intune iOS 사용자 지정 프로필을 사용하여 iOS 장치에 할당할 수 있습니다. 이 도구를 사용하면 이러한 장치의 작업을 제어하는 많은 설정을 만들어 구성 프로필에 내보낼 수 있습니다. 그런 다음 이 구성 프로필을 Intune iOS 사용자 지정 프로필로 가져와서 조직의 사용자와 장치에 설정을 할당할 수 있습니다.

이 기능을 사용하면 다른 Intune 프로필 유형으로 구성할 수 없는 iOS 설정을 할당할 수 있습니다.


1. [Microsoft Intune에서 사용자 지정 장치 설정을 구성하는 방법](custom-settings-configure.md)의 지침을 사용하여 시작합니다.
2. **사용자 지정 구성 프로필** 창에서 다음의 설정 각각을 구성합니다.

- **사용자 지정 구성 프로필 이름** - 장치 및 Intune 상태에 표시되는 정책의 이름을 입력합니다.
- **구성 프로필 파일** - Apple Configurator를 사용하여 만든 구성 프로필을 찾아 봅니다.
Apple Configurator 도구에서 내보내는 설정이 iOS 사용자 지정 정책을 할당하는 장치에 있는 iOS의 버전과 호환되는지 확인합니다. 호환되지 않는 설정을 해결하는 방법에 대한 정보를 보려면 [Apple 개발자](https://developer.apple.com/) 웹 사이트에서 **구성 프로필 참조** 및 **모바일 장치 관리 프로토콜 참조**를 검색하세요.

가져온 파일은 창의 **파일 내용** 영역에 표시됩니다.
