---
title: Microsoft Intune의 Windows 10을 위한 배달 최적화 설정 - Azure | Microsoft Docs
description: Windows 10 이상 디바이스에서 사용 가능한 배달 최적화 클라우드 서비스를 사용하여 소프트웨어 업데이트가 디바이스에 배달되는 방법을 구성합니다. Intune에서 디바이스 구성 프로필을 만들어 인터넷을 통해 업데이트를 설치합니다. 또한 기존 업데이트 링을 배달 최적화 프로필로 바꾸는 방법을 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1b83a380620704e9e3f616cee77b33d577c86c0d
ms.sourcegitcommit: 88f760abcea7348a0c6d00b533b54a6ff68d3985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2018
ms.locfileid: "52977272"
---
# <a name="windows-10-and-newer-delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune에서 Windows 10 이상 배달 최적화 설정

이 문서에서는 Windows 10 디바이스에 대해 구성할 수 있는 모든 배달 최적화 설정을 나열하고 설명합니다. 이러한 설정은 디바이스 구성 프로필에 추가된 후 Microsoft Intune을 사용하여 디바이스에 할당 또는 배포됩니다. 

[배달 최적화 업데이트](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)는 Windows 10의 배달 최적화를 자세히 알아볼 수 있는 훌륭한 리소스입니다.

## <a name="settings"></a>설정

**배달 최적화 다운로드 모드**: 업데이트가 디바이스에 배달되는 방법을 선택합니다. 옵션은 다음과 같습니다.

- **구성되지 않음** 최종 사용자는 OS에서 제공되는 **Windows 업데이트** 또는 **배달 최적화** 설정을 사용할 수 있는 고유한 방법으로 해당 디바이스를 업데이트합니다.
- **HTTP만, 피어링 없음**: 인터넷에서만 업데이트를 가져옵니다. 네트워크(피어링 또는 피어 투 피어라고 함)의 다른 컴퓨터에서 업데이트를 가져오지 마세요.
- **비공개 그룹에서 피어링과 혼합된 동일한 NAT HTTP 뒤의 피어링과 혼합된 HTTP**: 인터넷 및 네트워크의 다른 컴퓨터에서 업데이트를 가져옵니다. 동일한 Active Directory 사이트(있는 경우) 또는 동일한 도메인의 디바이스에서 피어링이 발생합니다. 이 옵션을 선택하면 피어링이 NAT(Network Address Translation) IP 주소를 교차합니다.
- **인터넷 피어링과 혼합된 HTTP**: 인터넷 및 네트워크의 다른 컴퓨터에서 업데이트를 가져옵니다.
- **피어링이 없는 단순 다운로드 모드**: Microsoft와 같은 업데이트 소유자로부터 직접 인터넷에서 업데이트를 가져옵니다. 배달 최적화 클라우드 서비스에는 연결하지 않습니다.
- **바이패스 모드**: BITS(Background Intelligent Transfer Service)를 사용하여 업데이트를 가져옵니다. 배달 최적화를 사용하지 마세요.

## <a name="move-from-existing-update-rings-to-delivery-optimization"></a>기존 업데이트 링에서 배달 최적화로 이동

**소프트웨어 업데이트 - Windows 10 업데이트 링**은 **배달 최적화** 설정으로 대체됩니다. 기존 업데이트 링은 **배달 최적화** 설정을 사용하도록 쉽게 변경할 수 있습니다. 단계:

1. 배달 최적화 구성 프로필을 만듭니다.

    1. Intune에서 **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
    2. 프로필에 대한 **이름**과 **설명**을 입력합니다.
    3. **플랫폼**에서 **Windows 10 이상**을 선택합니다. **프로필 유형**에서 **배달 최적화**를 선택합니다.
    4. **설정**을 선택합니다. **배달 최적화 다운로드 모드**에서 기존 소프트웨어 업데이트 링에 사용된 것과 동일한 모드를 선택합니다. 옵션은 다음과 같습니다.
        - **구성되지 않음**
        - **HTTP만, 피어링 없음**
        - **비공개 그룹에서 피어링과 혼합된 동일한 NAT HTTP 뒤의 피어링과 혼합된 HTTP**
        - **인터넷 피어링과 혼합된 HTTP**
        - **피어링이 없는 단순 다운로드 모드**
        - **바이패스 모드**

2. 이 새 프로필을 기존 소프트웨어 업데이트 링과 동일한 디바이스 및 사용자에게 할당합니다. [프로필 할당](device-profile-assign.md)에 단계가 나열됩니다.

3. 기존 소프트웨어 링을 구성 해제합니다.
    1. Intune에서 **소프트웨어 업데이트** > Windows 10 업데이트 링으로 이동합니다.
    2. 목록에서 업데이트 링을 선택합니다.
    3. 설정에서 **배달 최적화 다운로드 모드**를 **구성되지 않음**으로 설정합니다.
    4. **확인** > 을 선택하여 변경 내용을 **저장**합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.
