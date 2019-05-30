---
title: Microsoft Intune의 Windows 10을 위한 배달 최적화 설정 - Azure | Microsoft Docs
description: Intune으로 관리하는 Windows 10 디바이스에서 전송 최적화를 사용하는 방법을 구성합니다. Intune에서 디바이스 구성 프로필을 만들어 인터넷을 통해 업데이트를 설치합니다. 또한 기존 업데이트 링을 배달 최적화 프로필로 바꾸는 방법을 참조하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: d927c886bbb3f82c18d5873a86fc427d00d96337
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66042628"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune의 전송 최적화 설정

Intune이 있으면 Windows 10 디바이스에 전송 최적화 설정을 사용하여 디바이스로 애플리케이션 및 업데이트를 다운로드할 때 대역폭 소비를 줄일 수 있습니다. 전송 최적화는 디바이스 구성 프로필의 일부로 구성됩니다.  

이 문서에서는 디바이스 구성 프로필의 일부로 전송 최적화 설정을 구성 는 방법을 설명합니다. 프로필을 만든 후에는 해당 프로필을 Windows 10 디바이스에 할당 또는 배포합니다. 

Intune에서 지원하는 전송 최적화 설정 목록은 [Intune의 전송 최적화 설정](delivery-optimization-settings.md)을 참조하세요.  

Windows 10의 전송 최적화에 대한 자세한 내용은 Windows 설명서의 [전송 최적화 업데이트](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)를 참조하세요.  


> [!NOTE]
> **소프트웨어 업데이트 - Windows 10 업데이트 링**은 **배달 최적화** 설정으로 대체됩니다. 기존 업데이트 링은 **배달 최적화** 설정을 사용하도록 변경할 수 있습니다. [기존 업데이트 링을 전송 최적화로 이동](#move-existing-update-rings-to-delivery-optimization)(본 문서의 내용) 
## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링하고 **Intune**을 선택합니다.

2. **디바이스 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.

3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 플랫폼 선택:  

        - **Windows 10 이상**

    - **프로필 유형**: **배달 최적화**를 선택합니다.
    - **설정**: 업데이트 및 앱을 다운로드하려는 방식을 정의하는 설정을 구성합니다. 사용 가능한 설정에 대한 내용은 [Intune의 전송 최적화 설정](delivery-optimization-settings.md)을 참조하세요.

4. 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고 [상태를 모니터링](device-profile-monitor.md)합니다.

## <a name="move-existing-update-rings-to-delivery-optimization"></a>기존 업데이트 링을 배달 최적화로 이동

**전송 최적화** 설정은 **소프트웨어 업데이트 - Windows 10 업데이트 링**을 대체합니다. 기존 업데이트 링은 **배달 최적화** 설정을 사용하도록 쉽게 변경할 수 있습니다. 전송 최적화 프로필을 만들 때 동일한 설정을 유지하려면 동일한 *전송 최적화 다운로드 모드*를 사용한 다음, 이미 사용 중인 설정과 똑같이 설정하면 됩니다. 하지만 전송 최적화 프로필로 관리할 수 있는 추가 설정을 최대한 활용하도록 전송 최적화 설정을 다시 구성할 수도 있습니다.

1. 배달 최적화 구성 프로필을 만듭니다.

    1. Intune에서 **디바이스 구성** > **프로필** > **프로필 만들기**를 선택합니다.
    2. 다음 속성을 입력합니다.

        - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
        - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
        - **플랫폼**: **Windows 10 이상**을 선택합니다.
        - **프로필 유형**: **배달 최적화**를 선택합니다.
        - **설정**: **전송 최적화 다운로드 모드**의 경우 디바이스에 적용되는 설정을 변경하려는 의도가 아닌 한 기존 소프트웨어 업데이트 링에 사용되는 모드와 동일한 모드를 선택합니다. 옵션은 다음과 같습니다.
            - **구성되지 않음**
            - **HTTP만, 피어링 없음**
            - **동일한 NAT 뒤에서 피어링과 혼합 된 HTTP**
            - **비공개 그룹 간의 피어링과 혼합된 HTTP**
            - **인터넷 피어링과 혼합된 HTTP**
            - **피어링이 없는 단순 다운로드 모드**
            - **바이패스 모드**
    3. 관리하려는 모든 추가 설정을 구성합니다.
1. 이 새 프로필을 기존 소프트웨어 업데이트 링과 동일한 디바이스 및 사용자에게 할당합니다. [프로필 할당](device-profile-assign.md)에 단계가 나열됩니다.

3. 기존 소프트웨어 링을 구성 해제합니다.
    1. Intune에서 **소프트웨어 업데이트** > Windows 10 업데이트 링으로 이동합니다.
    2. 목록에서 업데이트 링을 선택합니다.
    3. 설정에서 **배달 최적화 다운로드 모드**를 **구성되지 않음**으로 설정합니다.
    4. **확인** > 을 선택하여 변경 내용을 **저장**합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.  
Intune의 [전송 최적화 설정](delivery-optimization-settings.md)을 살펴봅니다.
