---
title: Microsoft Intune - Azure를 사용하여 iOS 또는 macOS 장치 프로필 만들기 | Microsoft Docs
description: iOS 또는 macOS 장치 프로필을 추가하거나 만든 다음, Microsoft Intune에서 AirPrint, AirPlay, 홈 화면의 레이아웃, 앱 알림, 공유 장치, 단일 로그인 및 웹 콘텐츠 필터 설정에 대한 설정을 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/07/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65457a65504b633018bb61851f16c8c65fa1c806
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185681"
---
# <a name="add-ios-or-macos-device-feature-settings-in-intune"></a>Intune에서 iOS 및 macOS 장치 기능 설정 추가

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

장치 기능을 통해 다음과 같은 iOS 및 macOS에서 설정 및 기능의 범위를 제어할 수 있습니다.

- AirPrint 및 AirPlay 설정
- 홈 화면 레이아웃
- 앱의 알림
- 공유 장치 구성
- Single Sign-On 설정
- 웹 콘텐츠 필터링

이 아티클에서는 iOS 장치 기능 프로필을 구성하는 기본 사항을 보여줍니다. 그런 다음, 장치에 대한 플랫폼 특정 설정을 구성하려면 추가 아티클을 단계별로 실행할 수 있습니다.

## <a name="create-a-device-profile"></a>장치 프로필 만들기

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
3. **장치 구성** > **프로필** > **프로필 만들기**를 선택합니다.
4. 다음 속성을 입력합니다.

   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 설정에 대한 설명을 입력합니다. 선택 사항이지만 입력하는 것이 좋습니다.
   - **플랫폼**: 플랫폼 형식을 선택합니다.
     - **iOS**
     - **macOS**
   - **프로필 형식**: **장치 기능**을 선택합니다.
   - **설정**: 설정은 선택한 플랫폼에 따라 달라집니다. 다음 아티클에서는 각 프로필의 설정에 대해 설명합니다.

     - [iOS 및 MacOS용 AirPrint 설정](air-print-settings-ios-macos.md)
     - [iOS용 AirPlay 설정](airplay-settings-ios.md)
     - [iOS용 홈 화면 레이아웃 설정](home-screen-settings-ios.md)
     - [iOS용 앱 알림 설정](app-notification-settings-ios.md)
     - [iOS용 공유 장치 구성 설정](shared-device-settings-ios.md)
     - [iOS 장치 Single Sign-On용 Intune 구성](sso-ios.md)
     - [iOS 장치용 웹 콘텐츠 필터 설정](web-content-filter-settings-ios.md)

5. 작업이 완료되면 **확인**을 선택한 다음, **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다.

## <a name="next-step"></a>다음 단계

이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.