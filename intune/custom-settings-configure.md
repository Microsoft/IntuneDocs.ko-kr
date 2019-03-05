---
title: Microsoft Intune - Azur에서 사용자 지정 디바이스 설정 사용 | Microsoft Docs
description: Microsoft Intune을 사용하여 Windows Phone, Windows 8.1, Windows 10 이상, Android, Android 엔터프라이즈, macOS 및 iOS 디바이스에 대한 사용자 지정 설정을 사용할 프로필 추가 또는 만들기
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9556d8d348de7ffe79e4907fe6a1dae99dc50bee
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57229958"
---
# <a name="create-a-profile-with-custom-settings-in-intune"></a>Intune에서 사용자 지정 설정을 사용하여 프로필 만들기

## <a name="what-are-custom-profiles"></a>사용자 지정 프로필이란

Microsoft Intune에는 디바이스의 여러 기능을 제어하는 많은 기본 제공 설정이 있습니다. 사용자 지정 프로필을 만들 수도 있습니다. 사용자 지정 프로필은 Intune에 기본 제공되지 않은 디바이스 설정 및 기능을 사용하려는 경우 유용합니다. 이러한 프로필에는 조직에서 디바이스를 제어하기 위한 기능과 설정이 있습니다. 예를 들어, 모든 iOS 디바이스에 동일한 기능을 설정하는 사용자 지정 프로필을 만들 수 있습니다.

구성 프로필에 대한 자세한 내용은 [Microsoft Intune 디바이스 프로필이란?](device-profiles.md)을 참조하세요. 

이 문서에는 Android, Android 엔터프라이즈, iOS, macOS 및 Windows에 대한 사용자 지정 프로필을 만드는 데 필요한 링크가 있습니다.

## <a name="available-platforms"></a>사용 가능한 플랫폼

사용자 지정 설정은 플랫폼마다 다르게 구성됩니다. 예를 들어 Android 및 Windows 디바이스에서 기능을 제어하려면 OMA-URI(Open Mobile Alliance Uniform Resource Identifier) 값을 입력할 수 있습니다. Apple 디바이스의 경우 [Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) 또는 [Apple Profile Manager](https://support.apple.com/profile-manager)를 사용하여 만든 파일을 가져올 수 있습니다.

사용자 지정 프로필은 기본 제공 프로필과 유사하게 만들어지며 다음 플랫폼에서 사용할 수 있습니다.

- [OWA(Outlook Web Access)](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)

## <a name="next-steps"></a>다음 단계

플랫폼을 선택하고 다음을 시작합니다.

- [OWA(Outlook Web Access)](custom-settings-android.md)
- [Android Enterprise](custom-settings-android-for-work.md)
- [iOS](custom-settings-ios.md)
- [macOS](custom-settings-macos.md)
- [Windows 10](custom-settings-windows-10.md)
- [Windows Holographic for Business](custom-settings-windows-holographic.md)
- [Windows Phone 8.1](custom-settings-windows-phone-8-1.md)
