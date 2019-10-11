---
title: Microsoft Intune-Azure를 사용하여 디바이스 관리 | Micrososft Docs
description: 디바이스 목록을 csv 형식으로 내보내는 것을 포함하여 Microsoft intune으로 관리하는 디바이스를 검토하고, Azure Active Directory-조인된 디바이스를 보고, 디바이스에서 동작의 변경 로그를 검토하고, IT 관리자가 원격으로 Android 디바이스의 문제를 해결할 수 있게 TeamViewer 커넥터를 사용하고 디바이스에서 실행할 수 있는 모든 작업을 봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/19/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d2412418-d91a-4767-a3d6-bc88bb29caa2
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: cd1d99e0c3853a7bf607dd2f64046c503068566d
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71728626"
---
# <a name="what-is-microsoft-intune-device-management"></a>Microsoft Intune 디바이스 관리란?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

IT 관리자의 경우 관리되는 디바이스가 위험으로부터 해당 데이터를 보호하는 동안 사용자가 해당 작업을 수행해야 하는 리소스를 제공하도록 해야 합니다.

**디바이스** 워크로드는 관리하는 디바이스에 대한 정보를 제공하고, 이러한 디바이스에 대해 원격 작업을 수행할 수 있도록 합니다.

## <a name="get-to-your-devices"></a>디바이스로 가져오기

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
3. **디바이스**를 선택합니다. 이 보기는 개별 디바이스에 대한 자세한 정보 및 다음을 포함해 이 정보로 할 수 있는 작업을 표시합니다.

   - **개요**는 등록된 디바이스에 대한 시각적 스냅샷을 표시하고 또한 얼마나 많은 디바이스가 Android, iOS 등을 포함한 다른 플랫폼을 사용하는지를 표시합니다.
   - **모든 디바이스** - 관리하는 등록된 디바이스의 목록을 표시합니다.

     **내보내기** 기능을 사용하여 10,000개(Internet Explorer) 또는 30,000개(Microsoft Edge, Chrome)씩 늘어나도록 모든 디바이스의 .csv 목록을 만듭니다.

     하드웨어 세부 정보, 설치된 앱, 해당 준수 정책 상태 등을 포함해 [해당 디바이스에 대한 추가 세부 정보 보기](device-inventory.md)하려면 모든 디바이스를 선택합니다.

   - **Azure AD 디바이스**는 Azure AD(Active Directory)로 등록되거나 조인된 디바이스 목록을 표시합니다. [Azure AD 디바이스 관리](https://docs.microsoft.com/azure/active-directory/device-management-introduction)에 대해 자세히 알아봅니다.
   - **디바이스 작업**은 작업, 해당 상태, 작업을 시작한 사용자 및 시간을 비롯한 다른 디바이스에서 실행된 원격 작업의 기록을 포함합니다.

     ![디바이스 작업 모니터링 스크린샷](./media/device-management/monitor-device-actions.png)

   - **감사 로그**는 Intune에서 변경을 생성하는 활동 레코드입니다. [감사 로그](../fundamentals/monitor-audit-logs.md)는 자세한 세부 정보를 제공합니다.
   - **TeamViewer 커넥터**는 Intune에서 관리되는 Android 디바이스의 사용자가 IT 관리자의 원격 지원을 받을 수 있는 서비스입니다. [TeamViewer](teamviewer-support.md)에 대해 자세히 알아봅니다.
   - **도움말 및 지원**은 문제 해결 팁, 지원 요청 또는 Intune 상태 확인에 대한 바로 가기를 제공합니다.

## <a name="available-device-actions"></a>사용 가능한 디바이스 작업
사용 가능한 작업은 디바이스 플랫폼 및 디바이스 구성에 따라 다릅니다.

- [디바이스 인벤토리 보기](device-inventory.md)
- 다음의 원격 디바이스 작업을 실행합니다.
  - [사용 중지](devices-wipe.md#retire)
  - [초기화](devices-wipe.md#wipe)
  - [원격 잠금](device-remote-lock.md)
  - [암호 초기화](device-passcode-reset.md)
  - [활성화 잠금 무시](device-activation-lock-bypass.md)(iOS만 해당)
  - [새로 시작](device-fresh-start.md)(Windows만 해당)
  - [분실 모드](device-lost-mode.md)(iOS만 해당)
  - [디바이스 찾기](device-locate.md)(iOS만 해당)
  - [다시 시작](device-restart.md)(Windows만 해당)
  - [Windows 10 PIN 재설정](device-windows-pin-reset.md)
  - [Android 원격 제어](teamviewer-support.md)
  - [디바이스 동기화](device-sync.md)
  - [사용자 지정 알림 보내기](custom-notifications.md#send-a-custom-notification-to-a-single-device)(Android, iOS)

## <a name="next-steps"></a>다음 단계

- 특정 디바이스에 대한 자세한 정보를 보려면 **모든 디바이스**에서 디바이스를 선택 합니다.
- **디바이스 작업**을 선택하여 관리하는 디바이스에서 수행된 작업의 상태를 확인합니다.
