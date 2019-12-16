---
title: Microsoft Intune - Azure에서 디바이스 원격 관리 | Microsoft Docs
description: TeamViewer를 사용하려면 필요한 역할, TeamViewer 커넥터를 설치 하는 방법, Azure Portal에서 Microsoft Intune을 사용하여 디바이스를 원격으로 관리하는 단계별 지침 보기
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: remote-actions
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0372c9629e111c460b095d8c0236305866da42e3
ms.sourcegitcommit: ec69e7ccc6e6183862a48c1b03ca6a3bf573f354
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74907205"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>TeamViewer를 사용하여 Intune 디바이스 원격 관리

[TeamViewer](https://www.teamviewer.com)를 사용하여 Intune에서 관리하는 디바이스를 원격으로 관리할 수 있습니다. TeamViewer는 별도 구입하는 타사 프로그램입니다. 이 항목에서는 Intune에서 TeamViewer를 구성하는 방법과 원격으로 디바이스를 관리하는 방법을 보여줍니다. 

## <a name="prerequisites"></a>전제 조건

- 지원되는 디바이스를 사용합니다. Intune에서 관리하는 Android 디바이스 관리자, Android 회사 프로필, Windows, iOS 및 macOS 디바이스는 원격 관리를 지원합니다. TeamViewer는 Windows Holographic(HoloLens), Windows Team(Surface Hub) 또는 Windows 10 S를 지원하지 않을 수 있습니다. 지원 가능성에 대해서는 [TeamViewer](https://www.teamviewer.com)의 모든 업데이트를 참조합니다.

> [!NOTE]
> Android 전용 및 완전 관리형은 지원되지 않습니다.

- Azure Portal 내에서 Intune 관리자는 다음 [Intune 역할](../fundamentals/role-based-access-control.md)을 해야 합니다.  

  - **원격 지원 업데이트**: 관리자가 TeamViewer 커넥터 설정을 수정할 수 있습니다
  - **원격 지원 요청**: 관리자가 모든 사용자에 대한 새 원격 지원 세션을 시작할 수 있습니다. 이 역할의 사용자는 범위 내의 모든 Intune 역할에 따른 제한을 받지 않습니다. 또한 범위 내에 Intune 역할이 할당된 사용자 또는 디바이스 그룹은 원격 지원을 요청할 수도 있습니다. 

- 로그인 자격 증명이 있는 [TeamViewer](https://www.teamviewer.com) 계정. 일부 TeamViewer 라이선스만 Intune과의 통합을 지원할 수 있습니다. 특정 TeamViewer 요구 사항은 [TeamViewer 통합 파트너: Microsoft Intune](https://www.teamviewer.com/integrations/microsoft-intune/)을 참조하세요.

TeamViewer를 사용하면 Intune Connector용 TeamViewer가 TeamViewer 세션을 만들고, Active Directory 데이터를 읽고, TeamViewer 계정 액세스 토큰을 저장할 수 있습니다.

## <a name="configure-the-teamviewer-connector"></a>TeamViewer 커넥터 구성

디바이스에 대한 원격 지원을 제공하려면 먼저 다음 단계에 따라 Intune TeamViewer 커넥터를 구성합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **테넌트 관리** > **커넥터 및 토큰** > **TeamViewer 커넥터**를 선택합니다.
3. **연결**을 선택한 다음, 라이선스에 동의합니다.
4. **권한을 부여하려면 TeamViewer에 로그인합니다**를 선택합니다.
5. TeamViewer 사이트 웹 페이지가 열립니다. TeamViewer 라이선스 자격 증명을 입력하고 **로그인**합니다.

## <a name="remotely-administer-a-device"></a>디바이스 원격 관리

커넥터를 구성한 후 원격으로 디바이스를 관리할 준비가 되었습니다. 다음 단계를 따르십시오. 

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 다음을 수행합니다.
2. **디바이스**를 선택한 다음, **모든 디바이스**를 선택합니다.
3. 목록에서 원격으로 관리하려는 디바이스를 선택하고 **...**  > **새 원격 지원 세션**을 선택합니다.
4. Intune이 TeamViewer 서비스에 연결되면 디바이스에 대한 정보를 확인할 수 있습니다. **연결**하여 원격 세션을 시작합니다.

![TeamViewer를 사용하여 Android 디바이스 원격 관리 - 예](./media/teamviewer-support/android-teamviewer.png)

원격 세션을 시작하면 사용자는 디바이스의 회사 포털 앱 아이콘에 알림 플래그를 볼 수 있습니다. 앱이 열릴 때 알림도 표시됩니다. 그러면 사용자는 원격 지원 요청을 수락할 수 있습니다.

> [!NOTE]
> DEM 및 WCD와 같은 "사용자 없는" 메서드를 사용하여 등록된 Windows 디바이스는 회사 포털 앱에 TeamViewer 알림을 표시하지 않습니다. 이러한 시나리오에서는 TeamViewer 포털을 사용하여 세션을 생성하는 것이 좋습니다.

TeamViewer에서 디바이스 제어를 포함해 디바이스에서 작업 범위를 완료할 수 있습니다. 수행 가능한 작업에 대한 자세한 내용은 [TeamViewer 지침](https://www.teamviewer.com/support/documents/)을 참조합니다.

작업이 완료되면 TeamViewer 창을 닫습니다.
