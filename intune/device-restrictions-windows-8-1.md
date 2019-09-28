---
title: Windows 8.1을 실행하는 디바이스에 대한 Microsoft Intune 디바이스 제한 설정
titleSuffix: ''
description: Windows 8.1을 실행하는 디바이스에서 디바이스 설정 및 기능을 제어하는 데 사용할 수 있는 Intune 설정을 알아봅니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/6/2018
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: afe87d5de385fbf159b7195c22da4be866b87d93
ms.sourcegitcommit: 7315fe72b7e55c5dcffc6d87f185f3c2cded9028
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "71302333"
---
# <a name="microsoft-intune-windows-81-and-later-device-restriction-settings"></a>Microsoft Intune Windows 8.1 이상 디바이스 제한 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 아티클에서는 Windows 8.1 이상을 실행하는 디바이스에 대해 구성할 수 있는 Microsoft Intune 디바이스 제한 설정을 보여줍니다.


## <a name="general"></a>일반

- **진단 데이터 제출** - 디바이스에서 Microsoft에 진단 정보를 제출할 수 있습니다.
- **방화벽** - Windows 방화벽이 켜져 있어야 합니다.
- **사용자 계정 컨트롤** - 디바이스에 UAC(사용자 계정 컨트롤)를 사용해야 합니다.

## <a name="password"></a>암호
- **필수 암호 유형** - 최종 사용자에게 디바이스에 액세스하려면 암호를 입력하도록 요구합니다.
- **최소 암호 길이** - 암호에 대한 최소 문자 길이를 구성합니다.
- **디바이스를 초기화하기 전 로그인 오류 발생 횟수** - 이 횟수만큼 로그인에 실패하면 디바이스를 초기화합니다.
- **화면이 잠기기 전까지 최대 비활성 시간(분)** - 잠금을 해제하기 위해 암호가 필요하게 되기까지 디바이스가 유휴 상태여야 하는 시간(분)을 지정합니다.
- **암호 만료(일)** - 디바이스 암호를 변경해야 할 때까지의 기간(일)을 지정합니다.
- **이전 암호 다시 사용 방지** - 사용자가 이전에 사용한 암호를 구성할 수 있을지 여부를 지정합니다.
- **사진 암호 및 PIN** - 사진 암호 및 PIN을 사용하도록 설정합니다. 그림 암호를 허용하면, 그림에 제스처를 사용하여 로그인할 수 있습니다. PIN을 허용하면, 4자리 코드를 사용하여 빠르게 로그인할 수 있습니다.
- **암호화** - 디바이스의 파일을 암호화해야 합니다.<br>Windows 8.1을 실행하는 디바이스에 암호화를 적용하려면 각 디바이스에 [Windows용 December 2014 MDM 클라이언트 업데이트](https://support.microsoft.com/kb/3013816) 를 설치해야 합니다.
Windows 8.1 디바이스에 대해 이 설정을 사용하려면 디바이스의 모든 사용자가 Microsoft 계정을 가지고 있어야 합니다.
암호화가 작동하려면 디바이스가 [Microsoft InstantGo](https://blogs.windows.com/windowsexperience/2014/06/19/instantgo-a-better-way-to-sleep/#IBHULcTfI4PokO8X.97) 하드웨어 인증 요구 사항을 만족해야 합니다.
디바이스에 암호화를 적용하는 경우, 복구 키는 자신의 OneDrive 계정에서 액세스한 Microsoft 계정에서만 액세스할 수 있습니다. 사용자를 대신하여 이 키를 복구할 수 없습니다. 



## <a name="browser"></a>브라우저
- **자동 채우기** - 사용자가 브라우저에서 자동 완성 설정을 변경할 수 있습니다.
- **사기 경고** - 사기성일 수 있는 웹 사이트 경고를 사용하거나 사용하지 않도록 설정합니다.
- **SmartScreen** - 사기성일 수 있는 웹 사이트 경고를 사용하거나 사용하지 않도록 설정합니다.
- **JavaScript** - 브라우저에서 Java 스크립트와 같은 스크립트를 실행할 수 있습니다.
- **팝업** - 브라우저 팝업 차단을 사용하거나 사용하지 않도록 설정합니다.
- **Do Not Track 헤더 보내기** - Internet Explorer에서 방문한 사이트에 Do Not Track 헤더를 보냅니다.
- **플러그 인** - 사용자가 Internet Explorer에 플러그 인을 추가할 수 있습니다.
- **인트라넷 사이트에서 한 단어 입력** - 한 단어를 사용하여 Internet Explorer를 ‘Bing’ 등과 같은 웹 사이트로 디렉션할 수 있습니다.
- **인트라넷 사이트 자동 검색** - Internet Explorer에서 인트라넷 사이트의 보안을 구성하도록 돕습니다.
- **인터넷 보안 수준** - 인터넷 사이트에 대한 Internet Explorer 보안 수준을 설정합니다.
- **인트라넷 보안 수준** - 인트라넷 사이트에 대한 Internet Explorer 보안 수준을 설정합니다.
- **신뢰할 수 있는 사이트 보안 수준** - 신뢰할 수 있는 사이트 영역에 대한 보안 수준을 구성합니다.
- **제한된 사이트에 대한 높은 수준의 보안** - 제한된 사이트 영역에 대한 보안 수준을 구성합니다.
- **엔터프라이즈 모드 메뉴 액세스** - 사용자가 Internet Explorer에서 엔터프라이즈 모드 메뉴에 액세스하도록 허용합니다.
이 설정을 선택하면 사용자가 엔터프라이즈 모드 액세스를 켜 놓은 웹 사이트를 보여주는 보고서에 대한 URL을 포함하는 **로깅 보고서 위치**를 지정할 수 있습니다.
- **엔터프라이즈 모드 사이트 목록 위치** – 엔터프라이즈 모드가 활성화된 경우 이 모드를 사용하는 웹 사이트 목록의 위치를 지정합니다.

## <a name="cellular"></a>셀룰러
- **데이터 로밍** - 디바이스가 셀룰러 네트워크에 있을 때 데이터 로밍을 사용하도록 설정합니다.

## <a name="cloud-and-storage"></a>클라우드 및 스토리지
- **작업 폴더 URL** - 문서를 디바이스 간에 동기화될 수 있도록 작업 폴더의 URL을 설정합니다.
- **Microsoft 계정이 없는 Windows Mail 앱 액세스** - Microsoft 계정 없이 Windows Mail 애플리케이션에 대한 액세스를 사용하도록 설정합니다.
