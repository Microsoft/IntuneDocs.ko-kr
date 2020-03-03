---
title: Android 사용자가 앱을 얻는 방법
description: 최종 사용자에게 Android 앱을 제공하기 위한 방법
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 09/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f33d1684-b1b5-44f7-9aac-c6d5186a5d7c
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 231b30e93a3e56811e1569c32cc1286e02320f0d
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514407"
---
# <a name="how-your-android-users-get-their-apps"></a>Android 사용자가 앱을 얻는 방법

이 문서를 참조하여 최종 사용자가 Microsoft Intune을 통해 배포하는 Android 앱을 얻는 방법과 위치를 이해할 수 있습니다. 해당 정보는 네이티브 Android 디바이스와 Samsung Knox Standard 디바이스 등 디바이스 유형에 따라 다를 수 있습니다.

## <a name="native-non-samsung-knox-standard-android-devices"></a>네이티브(비 Samsung Knox 표준) Android 디바이스

| 앱 유형 | LOB(기간 업무) 앱 | Play 스토어 앱  |
| ------------- |-------------| -----|
| 사용 가능한 앱      | 회사 포털에서 **설치**를 누릅니다. 설치를 시작하려면 누르라는 알림이 나타납니다. 설치가 정상적으로 수행되면 알림이 사라집니다. | 사용자가 회사 포털에서 앱을 누르면 Play 스토어의 앱 페이지로 이동됩니다. 여기에서 설치를 시작합니다.|
| Required apps      | 사용자에 앱을 설치해야 함을 나타내는 알림이 표시되며 이 알림은 해제할 수 없습니다. 설치를 시작하려면 알림을 누릅니다. 설치가 정상적으로 수행되면 알림이 사라집니다.    | 사용자에 앱을 설치해야 함을 나타내는 알림이 표시되며 이 알림은 해제할 수 없습니다. 알림을 누르며 Play 스토어의 앱 페이지로 이동됩니다. 여기에서 설치를 시작합니다. 설치가 정상적으로 수행되면 알림이 사라집니다. |

[LOB 앱](../apps/lob-apps-android.md)을 설치하려면 최종 사용자가 알 수 없는 출처에서의 설치를 허용해야 합니다. 이러한 설정은 일반적으로 다음의 두 위치에서 발생합니다.

* **Android 7.1.2 이하**: **설정** > **보안** > **출처를 알 수 없는 앱**
* **Android 8.0 이상**: **설정** > **앱 및 알림** > **특수 앱 액세스** > **Install unknown apps**(알 수 없는 앱 설치) > **회사 포털** > **Allow from this source**(이 출처의 앱 허용)

이 문제가 발생하면 회사 포털 앱에서 최종 사용자에게 알리고 직접 적절한 설정을 안내합니다. 

## <a name="samsung-knox-standard-android-devices"></a>Samsung Knox Standard Android 디바이스

| 앱 유형 | LOB(기간 업무) 앱 | Play 스토어 앱  |
| ------------- |-------------| -----|
| 사용 가능한 앱      | 회사 포털에서 **설치**를 누릅니다. 추가 사용자 작업 없이도 앱이 설치됩니다. | 사용자가 회사 포털에서 앱을 누르면 Play 스토어의 앱 페이지로 이동됩니다. 여기에서 설치를 시작합니다.|
| Required apps      | 추가 사용자 작업 없이도 앱이 설치됩니다.    | 사용자에 앱을 설치해야 함을 나타내는 알림이 표시되며 이 알림은 해제할 수 없습니다. 알림을 누르며 Play 스토어의 앱 페이지로 이동됩니다. 여기에서 설치를 시작합니다. 설치가 정상적으로 수행되면 알림이 사라집니다. |

아래와 같이 앱은 관리되거나 관리되지 않을 수 있습니다. 앱을 관리되는 앱으로 만드는 프로세스는 모든 종류의 Android 디바이스에 대해 동일합니다.

**관리되는 앱** - 이러한 앱은 정책을 통해 관리할 수 있습니다. Intune에서 "래핑"되거나 Intune 앱 SDK를 사용하여 빌드됩니다. 이러한 앱은 Intune에서 관리할 수 있고, 애플리케이션 정책을 적용할 수 있습니다.

**관리되지 않는 앱** - 이러한 앱은 정책을 통해 관리할 수 없습니다. Intune에서 래핑되지 않았거나 Intune 앱 SDK를 통합하지 않습니다. 애플리케이션 정책을 이러한 앱에 적용할 수 없습니다.

## <a name="zebra-devices-with-zebra-mobility-extensions"></a>Zebra Mobility Extensions를 사용하는 Zebra 디바이스

Intune은 Zebra MX(Mobility Extensions) 도구 키트를 사용하여 디바이스 관리자가 관리하는 Zebra 디바이스에 앱을 자동으로 설치합니다. 이 기능을 사용하여 사용자 개입 없이 Zebra 디바이스에서 앱을 배포 및 업데이트할 수 있습니다. 디바이스 MX 버전이 4.2 이상이면 앱이 자동으로 설치되지 않습니다. 자세한 내용은 Zebra의 웹 사이트에서 [전체 MX 기능 매트릭스](http://techdocs.zebra.com/mx/compatibility/)를 참조하세요.

Zebra 디바이스 배포된 LOB 앱은 디바이스의 퍼블릭 위치에서 설치해야 합니다. .apk 앱 패키지는 디바이스의 퍼블릭 스토리지에 대해서도 액세스 권한이 있는 다른 앱 및 서비스에서 액세스할 수 있습니다. 일반적으로 이러한 액세스는 앱 다운로드를 완료하는 시점과 설치를 시작하는 시점 사이의 짧은 기간 동안 허용됩니다. 이러한 기간에는 타이밍 공격을 받기 쉽습니다. 예를 들어, 이 기간 동안 .apk 패키지를 변경할 수 있습니다. Intune은 .apk가 퍼블릭 스토리지에서 보내는 시간을 최소화하고 서명되지 않은 앱의 설치를 허용하지 않습니다. 보안 위험을 최소화하기 위해 업로드하는 .apk 파일에 중요한 정보가 포함되지 않도록 해야 합니다.

## <a name="see-also"></a>참고 항목

[Microsoft Intune을 사용하여 앱 추가](../apps/apps-add.md)

[iOS/iPadOS 사용자가 앱을 얻는 방법](end-user-apps-ios.md)

[Windows 사용자가 앱을 얻는 방법](end-user-apps-windows.md)
