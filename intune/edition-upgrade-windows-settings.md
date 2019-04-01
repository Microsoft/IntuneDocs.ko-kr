---
title: Microsoft Intune의 Windows 10 업그레이드 및 S 모드 설정 - Azure | Microsoft Docs
description: 모든 설정 목록 및 디바이스에서 Windows 10 버전을 업그레이드하거나 Microsoft Intune에서 디바이스 구성 프로필을 사용하여 디바이스에서 S 모드를 사용하도록 설정할 때 수행할 작업을 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c2a8c234c305744c48785763c87913c2635276ad
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57565607"
---
# <a name="windows-10-and-newer-device-settings-to-upgrade-editions-or-enable-s-mode-in-intune"></a>Intune에서 버전을 업그레이드 하거나 S 모드를 사용하도록 Windows 10(이상) 디바이스 설정

Microsoft Intune에는 디바이스를 관리하고 보호할 수 있는 많은 설정이 포함되어 있습니다. 이 문서에서는 Windows 10 디바이스에서 버전을 업그레이드하거나 S 모드를 활성화하기 위한 설정을 나열하고 설명합니다. 이러한 설정은 Intune에서 디바이스에 푸시되거나 배포되는 업그레이드 구성 프로필에서 생성됩니다.

MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 Windows 10 디바이스의 버전 및 S 모드 옵션을 제어합니다.

이 기능에 대한 자세한 내용은 [Windows 10 버전 업그레이드 또는 S 모드 사용](edition-upgrade-configure-windows-10.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[프로필을 만듭니다](edition-upgrade-configure-windows-10.md#create-the-profile).

## <a name="edition-upgrade"></a>버전 업그레이드

- **업그레이드할 대상 버전**: 업그레이드하려는 Windows 10 버전을 선택합니다. 이 정책의 대상 디바이스가 선택한 버전으로 업그레이드됩니다.
- **제품 키**: Microsoft에서 받은 제품 키를 입력합니다. 제품 키를 사용하여 정책이 만들어진 경우 이 키는 업데이트할 수 없으며 보안상의 이유로 숨겨져 있습니다. 제품 키를 변경하려면 전체 키를 다시 입력합니다.
- **라이선스 파일**: **Windows 10 Holographic for Business** 또는 **Windows 10 Mobile 버전**의 경우 **찾아보기**를 선택하여 Microsoft에서 받은 라이선스 파일을 선택합니다. 이 라이선스 파일에는 디바이스를 업그레이드하려는 버전에 대한 라이선스 정보가 포함되어 있습니다.

## <a name="mode-switch"></a>모드 스위치

- **구성 없음**: S 모드 디바이스는 S 모드로 유지됩니다. 최종 사용자는 S 모드로부터 디바이스를 전환할 수 있습니다.
- **S 모드로 유지**: 최종 사용자가 S 모드에서 디바이스를 전환할 수 없도록 설정합니다.
- **전환**: S 모드로부터 디바이스를 전환합니다.

## <a name="next-steps"></a>다음 단계

프로필이 만들어졌지만 아직 아무것도 하지 않습니다. [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Windows Holographic for Business](holographic-upgrade.md) 디바이스에 대한 버전 업그레이드 프로필을 만들 수도 있습니다.
