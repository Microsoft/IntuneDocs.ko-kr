---
title: Microsoft Intune - Azure에서 장치 원격 관리 | Microsoft Docs
description: TeamViewer를 사용하려면 필요한 역할, TeamViewer 커넥터를 설치 하는 방법, Azure Portal에서 Microsoft Intune을 사용하여 장치를 원격으로 관리하는 단계별 지침 보기
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 72cdd888-efca-46e6-b2e7-fb9696bb2fba
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 60d9398b80a30adee194470ac4e5c6c1efc0bd4c
ms.sourcegitcommit: 97b9f966f23895495b4c8a685f1397b78cc01d57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34744638"
---
# <a name="use-teamviewer-to-remotely-administer-intune-devices"></a>TeamViewer를 사용하여 Intune 장치 원격 관리

[TeamViewer](https://www.teamviewer.com)를 사용하여 Intune에서 관리하는 장치를 원격으로 관리할 수 있습니다. TeamViewer는 별도 구입하는 타사 프로그램입니다. 이 항목에서는 Intune에서 TeamViewer를 구성하는 방법과 원격으로 장치를 관리하는 방법을 보여줍니다. 

## <a name="prerequisites"></a>전제 조건

- 지원되는 장치를 사용합니다. Intune에서 관리하는 Android, Windows, iOS 및 macOS 장치는 원격 관리를 지원합니다. TeamViewer는 Windows Holographic(HoloLens), Windows Team(Surface Hub) 또는 Windows 10 S를 지원하지 않을 수 있습니다. 지원 가능성에 대해서는 [TeamViewer](https://www.teamviewer.com)의 모든 업데이트를 참조합니다.

- Azure Portal 내에서 Intune 관리자는 다음 [Intune 역할](role-based-access-control.md)을 해야 합니다.  

    - **원격 지원 업데이트**: 관리자가 TeamViewer 커넥터 설정을 수정할 수 있습니다
    - **원격 지원 요청**: 관리자가 모든 사용자에 대한 새 원격 지원 세션을 시작할 수 있습니다. 이 역할의 사용자는 범위 내의 모든 Intune 역할에 따른 제한을 받지 않습니다. 또한 범위 내에 Intune 역할이 할당된 사용자 또는 장치 그룹은 원격 지원을 요청할 수도 있습니다. 

- 로그인 자격 증명이 있는 [TeamViewer](https://www.teamviewer.com) 계정

TeamViewer를 사용하면 Intune Connector용 TeamViewer가 TeamViewer 세션을 만들고, Active Directory 데이터를 읽고, TeamViewer 계정 액세스 토큰을 저장할 수 있습니다.

## <a name="configure-the-teamviewer-connector"></a>TeamViewer 커넥터 구성

장치에 대한 원격 지원을 제공하려면 먼저 다음 단계에 따라 Intune TeamViewer 커넥터를 구성합니다.

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Microsoft Intune**을 검색합니다.
2. **Microsoft Intune**에서 **장치**를 선택한 다음, **TeamViewer 커넥터**를 선택합니다.
3. **연결**을 선택한 다음, 라이선스에 동의합니다.
4. **권한을 부여하려면 TeamViewer에 로그인합니다**를 선택합니다.
5. TeamViewer 사이트 웹 페이지가 열립니다. TeamViewer 라이선스 자격 증명을 입력하고 **로그인**합니다.

## <a name="remotely-administer-a-device"></a>장치 원격 관리

커넥터를 구성한 후 원격으로 장치를 관리할 준비가 되었습니다. 다음 단계를 따르십시오. 

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Microsoft Intune**을 검색합니다.
2. **Microsoft Intune**에서 **장치**를 선택한 다음, **모든 장치**를 선택합니다.
3. 목록에서 원격으로 관리하려는 장치를 선택합니다. 장치 속성에서 **새 원격 지원 세션**을 선택합니다.
4. Intune이 TeamViewer 서비스에 연결되면 장치에 대한 정보를 확인할 수 있습니다. **연결**하여 원격 세션을 시작합니다.

![TeamViewer를 사용하여 Android 장치 원격 관리 - 예](./media/android-teamviewer.png)

원격 세션을 시작하면 최종 사용자 장치의 회사 포털 앱 아이콘에 알림 플래그가 표시됩니다. 앱을 열 때 알림이 표시됩니다. 그러면 사용자는 원격 지원 요청을 수락할 수 있습니다.

TeamViewer에서 장치 제어를 포함해 장치에서 작업 범위를 완료할 수 있습니다. 수행 가능한 작업에 대한 자세한 내용은 [TeamViewer 지침](https://www.teamviewer.com/support/documents/)을 참조합니다.

작업이 완료되면 TeamViewer 창을 닫습니다.