---
title: Microsoft Intune에서 Windows 10 가상 머신 사용
titleSuffix: ''
description: Microsoft Intune에서 Windows 10 가상 머신을 사용하기 위한 지침
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: dougeby
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 486ca7eae1b1e8b016f44c735ec04a23145421a8
ms.sourcegitcommit: e1ff157f692983b49bdd6e20cc9d0f93c3b3733c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124982"
---
# <a name="using-windows-10-virtual-machines-with-intune"></a>Intune에서 Windows 10 가상 머신 사용

Intune은 특정 제한 사항에 따라 Windows 10 Enterprise를 실행하는 가상 머신을 관리할 수 있도록 지원합니다. Intune 관리는 동일한 가상 머신의 Windows Virtual Desktop 관리에 의존하거나 영향을 주지 않습니다.

Intune을 사용하여 Windows 10 VM을 관리하는 경우 다음 사항을 염두에 두세요.

## <a name="enrollment"></a>등록
- 주문형 세션 호스트 가상 머신은 Intune으로 관리하지 않는 것이 좋습니다. 각 VM은 만들 때 등록해야 합니다. 또한 정기적으로 VM을 삭제하면 분리된 디바이스 레코드를 [정리](../remote-actions/devices-wipe.md#automatically-delete-devices-with-cleanup-rules)할 때까지 Intune에 남아 있게 됩니다. 
- Windows Autopilot 자체 배포 및 화이트 글러브 배포 유형은 TPM(신뢰할 수 있는 플랫폼 모듈)이 필요하기 때문에 지원되지 않습니다. 
- RDP를 사용해야만 액세스할 수 있는 VM(예: Azure에서 호스트되는 VM)에서는 OOBE(첫 실행 경험) 등록이 지원되지 않습니다. 이러한 제한 사항은 다음을 의미합니다.
    - Windows Autopilot 및 상업적 OOBE가 지원되지 않습니다.
    - 디바이스 컨텍스트 정책에 대한 등록 상태 페이지 옵션이 지원되지 않습니다.

## <a name="configuration"></a>구성
Intune은 다음을 비롯한 신뢰할 수 있는 플랫폼 모듈 또는 하드웨어 관리를 활용하는 구성을 지원하지 않습니다.
- [BitLocker 설정](../configuration/device-profiles.md#endpoint-protection)
- [디바이스 펌웨어 구성 인터페이스 설정](../configuration/device-profiles.md#device-firmware-configuration-interface)

## <a name="reporting"></a>보고
Intune은 가상 머신을 자동으로 검색하고 **디바이스** > **모든 디바이스**에서 “가상 머신"으로 보고합니다. 디바이스를 선택하고 **개요** > **모델** 필드를 선택합니다. 

할당되지 않은 가상 머신은 [Intune 서비스로 체크 인](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)할 수 없으므로 비규격 디바이스 보고서에 포함될 수 있습니다.

## <a name="retirement"></a>사용 중지
RDP 액세스 권한만 있는 경우 [초기화 작업](../remote-actions/devices-wipe.md#wipe)을 사용하지 마세요. 초기화 작업을 수행하면 가상 머신의 RDP 설정이 삭제되므로 다시 연결되지 않습니다.


