---
title: 앱 보호 정책 배포 및 타이밍의 이해
titleSuffix: Microsoft Intune
description: 다양한 앱 보호 정책 배포 시기를 살펴보면서 언제 최종 사용자 디바이스에 변경 내용을 표시해야 하는지 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ec111319-7e02-434f-946b-88647726bf1a
ms.reviewer: joglocke
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7460d5ccf046b25510d798c3a7ed4aa9ecd87a8a
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72499171"
---
# <a name="understand-app-protection-policy-delivery-timing"></a>앱 보호 정책 배포 타이밍의 이해

다양한 앱 보호 정책 배포 시기를 살펴보면서 언제 최종 사용자 디바이스에 변경 내용을 표시해야 하는지 알아봅니다.

## <a name="delivery-timing-summary"></a>배포 타이밍 요약

애플리케이션 보호 정책 배포는 사용자의 라이선스 상태 및 Intune 서비스 등록에 따라 달라집니다.  

|    사용자 상태    |    앱 보호 동작     |    재시도 간격(참고 확인)    |    이유는 무엇입니까?    |
|-----------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
|    테넌트가 온보딩되지 않음    |    다음 재시도 시간까지 기다리세요.  앱 보호가 사용자에 대해 활성 상태가 아닙니다.    |    24시간    |    Intune에 대한 테넌트를 설정하지 않았을 때 발생합니다.    |
|    사용자의 제품의 사용이 허가되지 않음     |    다음 재시도 시간까지 기다리세요.  앱 보호가 사용자에 대해 활성 상태가 아닙니다.     |    12시간 - 하지만 Android 디바이스의 경우 Intune APP SDK 버전 5.6.0 이상이 있어야만 이 간격이 적용됩니다. 그렇지 않은 Andriod 디바이스의 재시도 간격은 24시간입니다.   |    사용자에게 Intune 사용을 허가하지 않은 경우에 발생합니다.    |
|    사용자에게 앱 보호 정책이 할당되지 않음    |    다음 재시도 시간까지 기다리세요.  앱 보호가 사용자에 대해 활성 상태가 아닙니다.    |    12시간        |    사용자에게 앱 설정을 할당하지 않은 경우에 발생합니다.    |
|    사용자가 Intune MAM에 성공적으로 등록    |    앱 보호는 정책 설정에 따라 적용됩니다.    업데이트는 재시도 간격에 따라 발생합니다.    |    Intune 서비스는 사용자 부하에 따라 정의됩니다.    일반적으로 30분입니다.     |    사용자가 MAM 구성용 Intune 서비스에 성공적으로 등록했을 때 발생합니다.    |

> [!NOTE]
> 활성 앱 사용이 발생해야만, 다시 말해서 앱이 시작되고 사용 중이어야만 재시도 간격이 적용될 수도 있습니다.  재시도 간격이 24시간이고 사용자가 앱이 시작되기를 48시간 동안 기다리는 경우 애플리케이션 보호 클라이언트는 48시간에 재시도합니다.

## <a name="handling-network-connectivity-issues"></a>네트워크 연결 문제 처리

네트워크 연결 문제로 인해 사용자 등록이 실패하면 가속화된 재시도 간격이 사용됩니다.  간격이 60분에 도달하거나 연결이 만들어질 때까지 애플리케이션 보호 클라이언트의 재시도 간격이 점점 길어집니다.  그러면 클라이언트는 연결이 만들어질 때까지 60분 간격으로 재시도합니다. 그 후 클라이언트는 사용자 상태에 따라 표준 재시도 간격으로 돌아갑니다.

## <a name="next-steps"></a>다음 단계

[Intune에 디바이스를 등록할 수 있도록 사용자에게 라이선스 할당](../fundamentals/licenses-assign.md)

