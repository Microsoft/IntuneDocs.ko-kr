---
title: Microsoft Intune의 Windows 10을 위한 배달 최적화 설정 - Azure | Microsoft Docs
description: Intune으로 관리하는 Windows 10 디바이스에서 전송 최적화를 사용하는 방법을 구성합니다. Intune에서 디바이스 구성 프로필을 만들어 인터넷을 통해 업데이트를 설치합니다. 또한 기존 업데이트 링을 배달 최적화 프로필로 바꾸는 방법을 참조하세요.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/10/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: kerimh
ms.openlocfilehash: 9fb4aab6b02c6ad6a5d2f18ca9d15beafc12d58a
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124812"
---
# <a name="delivery-optimization-settings-in-microsoft-intune"></a>Microsoft Intune의 전송 최적화 설정

Intune이 있으면 Windows 10 디바이스에 전송 최적화 설정을 사용하여 디바이스로 애플리케이션 및 업데이트를 다운로드할 때 대역폭 소비를 줄일 수 있습니다. 디바이스 구성 프로필의 일부로 전송 최적화를 설정할 수 있습니다.  

이 문서에서는 디바이스 구성 프로필의 일부로 전송 최적화 설정을 구성 는 방법을 설명합니다. 프로필을 만든 후에는 해당 프로필을 Windows 10 디바이스에 할당 또는 배포합니다. 

Intune에서 지원하는 전송 최적화 설정 목록을 보려면 [Intune의 전송 최적화 설정](../delivery-optimization-settings.md)을 참조하세요.  

Windows 10의 전송 최적화에 대한 자세한 내용은 Windows 설명서의 [전송 최적화 업데이트](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)를 참조하세요.  

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.

3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **배달 최적화**를 선택합니다.

4. **설정** > **구성**을 선택하고 업데이트 및 앱을 다운로드하려는 방식을 정의합니다. 사용 가능한 설정에 대한 내용은 [Intune의 전송 최적화 설정](../delivery-optimization-settings.md)을 참조하세요.

5. 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시됩니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고 [상태를 모니터링](device-profile-monitor.md)합니다.

<!-- ## Move existing update rings to delivery optimization

**Delivery optimization** settings replace **Software updates – Windows 10 Update Rings**. Your existing update rings can be easily changed to use the **Delivery optimization** settings. To maintain the same settings when you create a delivery optimization profile, use the same *Delivery optimization download mode* and then set the same settings as you already use. However, you can choose to reconfigure delivery optimization settings to take advantage of the full range of addition settings that the Delivery Optimization profile can manage. 
-->

## <a name="remove-delivery-optimization-from-windows-10-update-rings"></a>Windows 10 업데이트 링에서 전송 최적화 제거

전송 최적화는 이전에 소프트웨어 업데이트 링의 일부로 구성되었습니다. 2019 년 2월부터 전송 최적화 설정이 전송 최적화 장치 구성 프로필의 일부로 구성되어 디바이스에 소프트웨어 업데이트 전송 이상의 영향을 주는 추가 설정이 포함됩니다. 아직 하지 않았다면 전송 최적화 설정을 ‘구성되지 않음’으로 설정하여 업데이트 링에서 제거한 후 전송 최적화 프로필을 사용하여 사용 가능한 옵션을 더 광범위하게 관리할 수 있습니다. 

1. 전송 최적화 디바이스 구성 프로필 만들기:

    1. Microsoft Endpoint Manager 관리 센터에서 **디바이스** > **구성 프로필** > **프로필 만들기**를 선택합니다.
    2. 다음 속성을 입력합니다.

        - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
        - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
        - **플랫폼**: **Windows 10 이상**을 선택합니다.
        - **프로필 유형**: **배달 최적화**를 선택합니다.
        - **설정**: **전송 최적화 다운로드 모드**의 경우 디바이스에 적용되는 설정을 변경하려는 의도가 아닌 한 기존 소프트웨어 업데이트 링에 사용되는 모드와 동일한 모드를 선택합니다. 옵션은 다음과 같습니다.
            - **구성되지 않음**
            - **HTTP만, 피어링 없음**
            - **동일한 NAT 뒤에서 피어링과 혼합 된 HTTP**
            - **프라이빗 그룹 간의 피어링과 혼합된 HTTP**
            - **인터넷 피어링과 혼합된 HTTP**
            - **피어링이 없는 단순 다운로드 모드**
            - **바이패스 모드**
    3. 관리하려는 모든 추가 설정을 구성합니다.

2. 이 새 프로필을 기존 소프트웨어 업데이트 링과 동일한 디바이스 및 사용자에게 할당합니다. [프로필 할당](device-profile-assign.md)에 단계가 나열됩니다.

3. 기존 소프트웨어 링을 구성 해제합니다.
    1. Microsoft Endpoint Manager 관리 센터에서 **소프트웨어 업데이트** > Windows 10 업데이트 링으로 이동합니다.
    2. 목록에서 업데이트 링을 선택합니다.
    3. 설정에서 **배달 최적화 다운로드 모드**를 **구성되지 않음**으로 설정합니다.
    4. **확인** > 을 선택하여 변경 내용을 **저장**합니다.

## <a name="next-steps"></a>다음 단계

[프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.  
Intune의 [전송 최적화 설정](../delivery-optimization-settings.md)을 살펴봅니다.
