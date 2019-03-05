---
title: Windows PC 원격 지원 요청 및 제공
titlesuffix: Microsoft Intune
description: PC로 관리되는 Windows 데스크톱에 대한 원격 지원에 필요한 최종 사용자와 IT 관리자 단계 및 PC를 원격으로 시작하기 위한 단계를 설명합니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 01/01/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c2654491-5144-408a-a45a-644eb91ac1bb
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3ef4b8dd30d1b20465ca041ad5b1c412fb9b71be
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57237676"
---
# <a name="request-and-provide-remote-assistance-for-windows-pcs"></a>Windows PC 원격 지원 요청 및 제공

[!INCLUDE [classic-portal](includes/classic-portal.md)]

이 항목의 정보는 Intune 소프트웨어 클라이언트를 사용하여 PC를 관리하는 Windows 데스크톱에만 적용됩니다.

Intune은 [TeamViewer](https://www.teamviewer.com) 소프트웨어(별매)를 사용하여 Intune 소프트웨어 클라이언트를 실행하는 사용자에게 원격 지원을 제공하도록 지원할 수 있습니다. 사용자가 Microsoft Intune Center의 도움을 요청하는 경우 이를 안내하는 알림이 표시되므로 해당 요청을 수신한 후 지원을 제공할 수 있습니다. 이 기능은 Intune에서 기존의 Windows 원격 지원 기능을 대체합니다.


## <a name="before-you-start"></a>시작하기 전에

원격 지원을 설정하고 원격 지원 요청에 응답하려면 먼저, 다음과 같은 선행 조건을 충족했는지 확인합니다.

- TeamViewer 웹 사이트에 로그인하기 위한 [TeamViewer 계정을 등록](https://login.teamviewer.com/LogOn#register)해야 합니다.
- 관리하려는 Windows PC를 [Windows 소프트웨어 클라이언트에서 관리](manage-windows-pcs-with-microsoft-intune.md)해야 합니다.
- Intune에서 지원하는 모든 Windows PC 운영 체제를 관리할 수 있어야 합니다.

## <a name="configure-the-teamviewer-connector"></a>TeamViewer 커넥터 구성

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **관리자**를 선택합니다.
2. **관리자** 작업 영역에서 **TeamViewer**를 선택합니다.
3. **TeamViewer** 페이지의 **TeamViewer 커넥터**에서 **사용**을 선택합니다.
4. **TeamViewer 사용** 대화 상자에서 사용 조건을 확인한 후 **동의**합니다. TeamViewer 라이선스가 아직 없는 경우 **TeamViewer 라이선스 구입**을 선택합니다.
5. TeamViewer 브라우저 창이 열리면 TeamViewer 자격 증명을 사용하여 사이트에 로그인합니다.
6. TeamViewer 사이트에서 옵션을 읽은 후 동의하여 Intune에서 TeamViewer에 연결하도록 합니다.
7. Intune 콘솔에서 **TeamViewer 커넥터** 항목이 **사용**으로 표시되는지 확인합니다.


## <a name="open-a-remote-assistance-request-end-user"></a>원격 지원 요청 열기(최종 사용자)

1. 클라이언트 Windows PC에서 **Microsoft Intune Center**를 엽니다.
2. **원격 지원** 아래에서 **원격 지원 요청**을 선택합니다.
3. 요청을 승인하면(아래 참조) 클라이언트에서 TeamViewer가 열립니다. 사용자는 웹 브라우저에서 TeamViewer 애플리케이션을 열려고 한다는 사실을 나타내는 메시지에 동의해야 합니다.
4. PC를 제어하도록 허용할지 묻는 메시지가 사용자에게 표시됩니다. 계속하려면 이 메시지에 동의해야 합니다.
5. 원격 지원 세션 중 연결되어 있음을 보여 주는 창이 사용자에게 표시됩니다. 사용자가 이 창을 닫으면 원격 세션이 종료됩니다.

## <a name="respond-to-a-remote-assistance-request"></a>원격 지원 요청에 응답

1. 사용자가 원격 지원 요청을 제출하는 경우 **경고** 작업 영역의 **모니터링** > **원격 지원**에서 해당 요청을 확인할 수 있습니다. 예를 들면 다음과 같습니다.
   > ![원격 지원 요청 스크린샷](/intune/media/team-viewer.png)

<br>요청에 대해 4시간 이상 동안 답변하지 않으면 해당 요청이 제거됩니다.
2. 요청을 수락하려면 **요청을 승인하고 원격 지원을 시작합니다.** 를 선택합니다.
3. **새 원격 지원 요청이 보류 중입니다.** 대화 상자에서 **원격 지원 요청 수락**을 선택합니다. 아직 설치되어 있지 않은 경우 TeamViewer가 PC에 필요한 모든 앱을 설치합니다.
4. 그런 다음, TeamViewer가 최종 사용자에게 PC 제어를 허용하려는지 묻는 알림을 표시합니다. 사용자가 그 요청을 수락하면 TeamViewer 창이 열리며, PC를 제어할 수 있게 됩니다.

원격 지원 세션에서 작업하는 동안, 사용 가능한 모든 TeamViewer 명령을 사용하여 원격 PC를 제어할 수 있습니다. 이러한 명령의 도움말을 보려면 TeamViewer 웹 사이트에서 [원격 제어 매뉴얼](http://www.teamviewer.com/en/support/documents/)을 다운로드하세요.

## <a name="close-the-remote-assistance-session"></a>원격 지원 세션 닫기

**TeamViewer** 창의 **작업** 메뉴에서 **세션 끝내기**를 선택합니다.

## <a name="remotely-restart-a-windows-pc"></a>원격으로 Windows PC 다시 시작
사용자의 문제 해결을 도와줄 때 사용자의 PC를 원격으로 다시 시작해야 하는 경우가 종종 있을 수 있습니다. Windows PC를 원격으로 다시 시작하려면 다음 단계를 사용합니다.

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **그룹**&gt;**모든 디바이스**(또는 다시 시작하려는 PC가 포함된 다른 그룹)를 선택합니다.

2.  PC를 하나 이상 선택한 다음 **원격 작업** &gt; **컴퓨터 다시 시작**을 선택합니다.

3.  작업 상태를 확인하려면 페이지의 오른쪽 아래 모서리에 있는 **원격 작업**을 선택합니다.

4.  **작업 상태** 대화 상자에서 현재 원격 작업, 작업 상태, 디바이스 이름 및 보고된 모든 오류를 검토할 수 있습니다.

### <a name="see-also"></a>참고 항목

[Intune 소프트웨어 클라이언트를 사용하는 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
