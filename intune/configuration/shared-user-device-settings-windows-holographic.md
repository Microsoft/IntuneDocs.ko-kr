---
title: Windows Holographic Business 공유 디바이스 설정 - Microsoft Intune - Azure | Microsoft Docs
description: Microsoft Intune에서 여러 사용자에 의해 공유되거나 사용되는 디바이스를 구성하도록 Windows Holographic for Business를 추가하고 사용합니다. 계정 관리 설정의 목록 및 Microsoft HoloLens를 비롯한 디바이스에서의 용도를 확인합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9c89712539d4e5bd78cc317af2af396f8ca7006
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72492226"
---
# <a name="windows-holographic-for-business-settings-to-manage-shared-devices-using-intune"></a>Intune을 사용하여 공유 디바이스를 관리하는 Windows Holographic for Business 설정

Microsoft HoloLens와 같은 Windows Holographic for Business 디바이스를 여러 사용자가 사용할 수 있습니다. 다중 사용자가 있는 디바이스는 공유 디바이스라고 하며 MDM(모바일 디바이스 관리) 솔루션의 일부입니다.

Microsoft Intune을 사용하여 사용자는 게스트 계정으로 이러한 공유 디바이스에 로그인할 수 있습니다. 디바이스를 사용하므로 사용자는 허용하는 기능에 대한 액세스만을 얻습니다.

이 문서에서는 Windows Holographic for Business 디바이스 구성 프로필에서 사용하는 설정을 나열하고 설명합니다. 프로필이 Intune에서 생성될 때 조직의 디바이스 그룹에 프로필을 배포하거나 할당합니다. 또한 혼합된 디바이스 유형과 OS 버전을 사용하여 디바이스 그룹에 이 프로필을 할당할 수도 있습니다.

Intune의 이 기능에 대한 자세한 내용은 [공유 PC 또는 다중 사용자 디바이스에서 액세스, 계정 및 전원 기능 제어](shared-user-device-settings.md)를 참조하세요. Windows CSP에 대한 자세한 내용은 [AccountManagement CSP](https://docs.microsoft.com/windows/client-management/mdm/accountmanagement-csp)를 참조하세요.

## <a name="before-your-begin"></a>시작하기 전에

[프로필을 만듭니다](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>다중 사용자 디바이스 공유 설정

> [!NOTE]
> Microsoft HoloLens를 포함하여 Windows Holographic for Business를 실행하는 디바이스에서만 **계정 관리** 설정을 지원합니다. **공유 PC 모드**를 포함하여 Intune에 표시된 다른 설정을 구성하는 경우 이러한 디바이스에 영향을 주지 않습니다.

- **계정 관리**: **사용**으로 설정하여 게스트가 만든 로컬 계정과 AD 및 Azure AD의 계정을 자동으로 삭제합니다. 사용자가 디바이스에서 로그아웃하거나 시스템 유지 관리가 실행될 때 이러한 계정이 삭제됩니다. 활성화되는 경우 다음도 설정합니다.
  - **계정 삭제**: 계정 삭제 시기 선택: **스토리지 공간 임계값 도달 시**, **스토리지 공간 임계값 및 비활성 임계값 도달 시** 또는 **로그아웃 후 즉시**. 또한 다음을 입력합니다.
    - **임계값(%) 삭제 시작**: 디스크 공간의 백분율(0-100)을 입력합니다. 총 디스크/스토리지 공간이 입력한 값 아래로 떨어지는 경우 캐시된 계정이 삭제됩니다. 지속적으로 계정을 삭제하여 디스크 공간을 확보합니다. 활성화되지 않은 가장 긴 계정은 먼저 삭제됩니다.
    - **임계값(%) 삭제 중지**: 디스크 공간의 백분율(0-100)을 입력합니다. 총 디스크/스토리지 공간이 입력한 값을 충족하는 경우 삭제가 중지됩니다.

  **사용하지 않음**으로 설정하여 게스트가 만든 로컬, AD 및 Azure AD 계정을 유지합니다.

  > [!NOTE]
  > Microsoft HoloLens 디바이스에서만 **계정 관리** 설정을 지원합니다.

## <a name="next-steps"></a>다음 단계

- [프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
- [Windows 10 이상](shared-user-device-settings-windows.md)에 대한 설정을 확인합니다.
