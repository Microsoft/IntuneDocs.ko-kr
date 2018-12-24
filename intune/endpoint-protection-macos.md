---
title: Microsoft Intune - Azure의 macOS에서 엔드포인트 보호 추가 | Microsoft Docs
description: MacOS 디바이스에서 게이트키퍼를 사용하여 mac 앱 스토어를 포함해 앱을 설치할 수 있는 위치를 결정합니다. 또한 Microsoft Intune을 사용하여 방화벽이 특정 앱을 허용하도록 구성하거나 사용하도록 설정하고, 특정 앱을 차단하고, 은폐 모드를 사용하고 특정 유형의 들어오는 연결을 차단합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 3/27/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a9828f1b8a24e4f7d871f9e6e6f67e9f6c6fb197
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182774"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Intune에서 macOS 엔드포인트 보호 설정

이 아티클에서는 macOS를 실행하는 디바이스에 대해 구성할 수 있는 엔드포인트 보호 설정을 보여줍니다. 이러한 설정은 이러한 디바이스에서 게이트키퍼 및 방화벽 설정을 포함하며 Microsoft Intune에서 디바이스 프로필을 사용하여 구성할 수 있습니다.

## <a name="gatekeeper"></a>게이트키퍼

- **이러한 위치에서 앱 다운로드 허용**: 앱이 다운로드되는 위치에 따라 앱을 제한합니다. 맬웨어에서 디바이스를 보호하고 신뢰하는 소스로부터만 앱을 허용하기 위함입니다. 허용하는 옵션은 다음과 같습니다. 
  - **Mac 앱 스토어**
  - **Mac 앱 스토어 및 확인된 개발자**
  - **Anywhere**

- **사용자가 게이트키퍼 재정의 가능**: 사용자가 게이트키퍼 설정을 재정의하는 것을 금지하고 앱을 설치하기 위해 컨트롤 클릭을 금지합니다. 사용하도록 설정되면 사용자가 앱을 컨트롤 클릭하여 설치할 수 있습니다.

## <a name="firewall"></a>방화벽

방화벽을 사용하여 포트별이 아닌 응용 프로그램별 연결을 제어합니다. 응용 프로그램별 설정을 사용하면 방화벽 보호의 이점을 더욱 쉽게 얻을 수 있습니다. 또한 합법적인 앱에 대해 열려있는 네트워크 포트를 원하지 않는 앱이 제어하는 것을 방지해줍니다.

- **앱별 연결을 제어하여 무단 네트워크 액세스에서 장치를 보호하기 위해 방화벽을 사용합니다.**
  - **방화벽**: 들어오는 연결을 사용자 환경에서 처리하는 방법을 구성하려면 방화벽을 사용하도록 설정합니다.
  - **들어오는 연결**: DHCP, Bonjour, IPSec 등의 기본 인터넷 서비스에 필요한 연결을 제외하고 들어오는 모든 연결을 차단합니다. 또한 이 기능은 모든 공유 서비스(예: 파일 공유, 화면 공유)를 차단합니다. 공유 서비스를 사용하는 경우 이 설정을 **구성되지 않음**으로 유지합니다.

- **특정 앱에 대한 들어오는 연결 허용 또는 차단**
  - **허용된 앱**: 들어오는 연결을 수신하도록 명시적으로 허용된 앱을 선택합니다.
  - **차단된 앱**: 들어오는 연결을 차단해야 하는 앱을 선택합니다.
  - **은폐 모드**: 컴퓨터가 검색 요청에 응답하지 않게 하려면 은폐 모드를 사용하도록 설정합니다. 디바이스는 권한이 부여된 앱에 대해 들어오는 요청에 계속 응답합니다. ICMP(ping)와 같은 예기치 않은 요청은 무시합니다.
