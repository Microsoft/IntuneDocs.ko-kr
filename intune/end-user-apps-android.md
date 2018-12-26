---
title: Android 사용자가 앱을 얻는 방법
description: 최종 사용자에게 Android 앱을 제공하기 위한 방법
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 08/21/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: 5f8263f06fe33537a74a6d1889b02b89ee6a825f
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183403"
---
# <a name="how-your-android-users-get-their-apps"></a>Android 사용자가 앱을 얻는 방법

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

이 정보를 사용하여 최종 사용자가 Microsoft Intune을 통해 배포하는 Android 앱을 얻는 방법과 위치를 이해합니다. 해당 정보는 네이티브 Android 디바이스와 Samsung Knox Standard 디바이스 등 디바이스 유형에 따라 다를 수 있습니다.

## <a name="native-non-samsung-knox-standard-android-devices"></a>네이티브(비 Samsung Knox 표준) Android 디바이스

| 앱 유형 | LOB(기간 업무) 앱 | Play 스토어 앱  |
| ------------- |-------------| -----|
| 사용 가능한 앱      | 회사 포털에서 **설치**를 누릅니다. 설치를 시작하려면 누르라는 알림이 나타납니다. 설치가 정상적으로 수행되면 알림이 사라집니다. | 사용자가 회사 포털에서 앱을 누르면 설치를 시작할 수 있는 Play 스토어의 앱 페이지로 이동됩니다.|
| Required apps      | 사용자에 앱을 설치해야 함을 나타내는 알림이 표시되며 이 알림은 해제할 수 없습니다. 설치를 시작하려면 알림을 누릅니다. 설치가 정상적으로 수행되면 알림이 사라집니다.    | 사용자에 앱을 설치해야 함을 나타내는 알림이 표시되며 이 알림은 해제할 수 없습니다. 알림을 누르며 설치를 시작할 수 있는 Play 스토어의 앱 페이지로 이동됩니다. 설치가 정상적으로 수행되면 알림이 사라집니다. |

[LOB 앱](lob-apps-android.md)을 설치하려면 최종 사용자가 알 수 없는 출처에서의 설치를 허용해야 합니다. 이러한 문제는 일반적으로 다음의 두 위치에서 발생합니다.

* **Android 7.1.2 이하**: **설정** > **보안** > **출처를 알 수 없는 앱**
* **Android 8.0 이상**: **설정** > **앱 및 알림** > **특수 앱 액세스** > **Install unknown apps**(알 수 없는 앱 설치) > **회사 포털** > **Allow from this source**(이 출처의 앱 허용)

이 문제가 발생하면 회사 포털 앱에서 최종 사용자에게 알리고 직접 적절한 설정을 안내합니다. 


## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox Standard Android 디바이스

| 앱 유형 | LOB(기간 업무) 앱 | Play 스토어 앱  |
| ------------- |-------------| -----|
| 사용 가능한 앱      | 회사 포털에서 **설치**를 누릅니다. 추가 사용자 작업 없이도 앱이 설치됩니다. | 사용자가 회사 포털에서 앱을 누르면 설치를 시작할 수 있는 Play 스토어의 앱 페이지로 이동됩니다.|
| Required apps      | 추가 사용자 작업 없이도 앱이 설치됩니다.    | 사용자에 앱을 설치해야 함을 나타내는 알림이 표시되며 이 알림은 해제할 수 없습니다. 알림을 누르며 설치를 시작할 수 있는 Play 스토어의 앱 페이지로 이동됩니다. 설치가 정상적으로 수행되면 알림이 사라집니다. |

아래와 같이 앱은 관리되거나 관리되지 않을 수 있습니다. 앱을 관리되는 앱으로 만드는 프로세스는 모든 종류의 Android 디바이스에 대해 동일합니다.

**관리되는 앱** - 정책을 통해 관리할 수 있는 앱입니다. Intune에서 "래핑"되거나 Intune 앱 SDK를 사용하여 빌드됩니다. 이러한 앱은 Intune에서 관리할 수 있고, 애플리케이션 정책을 적용할 수 있습니다.

**관리되지 않는 앱** - 정책을 통해 관리할 수 없는 앱입니다. Intune에서 래핑되지 않았거나 Intune 앱 SDK를 통합하지 않습니다. Application policies cannot be applied to these apps.

### <a name="see-also"></a>참고 항목
[Microsoft Intune을 사용하여 앱 추가](apps-add.md)

[iOS 사용자가 앱을 얻는 방법](end-user-apps-ios.md)

[Windows 사용자가 앱을 얻는 방법](end-user-apps-windows.md)
