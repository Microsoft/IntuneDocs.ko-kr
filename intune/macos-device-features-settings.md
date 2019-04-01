---
title: Microsoft Intune의 macOS 디바이스 기능 설정 | Microsoft Docs
description: Microsoft Intune에서 AirPrint용 macOS 디바이스를 구성하는 모든 설정을 참조하세요. 또한 네트워크에 있는 AirPrint 서버의 IP 주소, 경로 및 포트 설정을 가져오려 단계를 참조하세요. 디바이스 구성 프로필의 이 설정을 사용하여 네트워크의 AirPrint 서버를 사용하도록 macOS 디바이스를 구성합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: ''
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4973dc5038ecfe9a8e909df1a1db3feceb30979b
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565335"
---
# <a name="macos-device-feature-settings-in-intune"></a>Intune에서 macOS 디바이스 기능 설정

Intune에는 macOS 사용자가 네트워크의 AirPrint 프린터로 인쇄할 수 있 수 있는 몇 가지 기본 제공 설정이 포함되어 있습니다. 이 문서에서는 이러한 설정을 나열하고 각 설정이 수행하는 작업을 설명합니다. 터미널 앱(에뮬레이터)을 사용하여 AirPrint 프린터의 IP 주소, 경로 및 포트를 가져오는 단계도 나열합니다.

## <a name="before-you-begin"></a>시작하기 전에

[macOS 디바이스 구성 프로필을 만듭니다](device-features-configure.md).

## <a name="airprint-settings"></a>AirPrint 설정

1. **설정**에서 **AirPrint**를 선택합니다. AirPrint 서버의 다음 속성을 입력합니다.

    - **IP 주소**: 프린터의 IPv4 또는 IPv6 주소를 입력합니다. 호스트 이름을 사용하여 프린터를 식별하는 경우 터미널 앱에서 프린터를 ping하여 IP 주소를 가져올 수 있습니다. [IP 주소 및 경로 가져오기](#get-the-ip-address-and-path)(이 문서)에서 자세한 정보를 제공합니다.
    - **경로**: 프린터의 경로를 입력합니다. 네트워크의 프린터에 대한 경로는 일반적으로 `ipp/print`입니다. [IP 주소 및 경로 가져오기](#get-the-ip-address-and-path)(이 문서)에서 자세한 정보를 제공합니다.
    - **포트**: AirPrint 대상의 수신 대기 포트를 입력합니다. 이 속성을 비워두면 AirPrint는 기본 포트를 사용합니다. iOS 11.0 이상에서 사용할 수 있습니다.
    - **TLS**: TLS(전송 계층 보안)를 사용하여 AirPrint 연결을 보호하려면 **사용**을 선택합니다. iOS 11.0 이상에서 사용할 수 있습니다.

2. **추가**를 선택합니다. AirPrint 서버가 목록에 추가됩니다. 많은 AirPrint 서버를 추가할 수 있습니다.

    AirPrint 프린터 목록을 포함하는 쉼표로 구분된 파일(.csv)을 **가져오기**할 수도 있습니다. 또한 Intune에서 AirPrint 프린터를 추가한 후에 이 목록을 **내보내기**할 수 있습니다.

3. 완료되면 **확인**을 선택하여 목록을 저장합니다.

## <a name="get-the-ip-address-and-path"></a>IP 주소 및 경로 가져오기

AirPrinter 서버를 추가하려면 프린터의 IP 주소, 리소스 경로 및 포트가 필요합니다. 다음 단계에서는 이 정보를 가져오는 방법을 보여줍니다.

1. AirPrint 프린터와 동일한 로컬 네트워크(서브넷)에 연결된 Mac에서 **터미널**을 엽니다(**/Applications/Utilities**에서).
2. 터미널 앱에서 `ippfind`를 입력하고 enter를 선택합니다.

    프린터 정보를 기록합니다. 예를 들어 `ipp://myprinter.local.:631/ipp/port1`과 유사한 항목을 반환할 수 있습니다. 첫 번째 부분은 프린터의 이름입니다. 마지막 부분(`ipp/port1`)은 리소스 경로입니다.

3. 터미널에서 `ping myprinter.local`을 입력하고 enter를 선택합니다.

   IP 주소를 기록합니다. 예를 들어 `PING myprinter.local (10.50.25.21)`과 유사한 항목을 반환할 수 있습니다.

4. IP 주소 및 리소스 경로 값을 사용합니다. 이 예제에서 IP 주소는 `10.50.25.21`이고, 리소스 경로는 `/ipp/port1`입니다.

## <a name="next-steps"></a>다음 단계

- [iOS](ios-device-features-settings.md) 디바이스에 대한 모든 설정을 봅니다.
- 이 프로필을 그룹에 할당합니다. [디바이스 프로필 할당](device-profile-assign.md)을 참조하세요.
