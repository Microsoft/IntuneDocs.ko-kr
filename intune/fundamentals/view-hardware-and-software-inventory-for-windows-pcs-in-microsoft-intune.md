---
title: Windows PC에 대한 하드웨어 및 소프트웨어 인벤토리 보기
titleSuffix: Microsoft Intune
description: Intune 소프트웨어 클라이언트를 사용하여 PC로 관리하는 Windows 데스크톱에 대한 하드웨어 및 소프트웨어 정보를 확인하는 방법입니다.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 06/26/2019
ms.topic: archived
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 3c10f4c9-520b-4864-92fc-a45a9f640ad4
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1ea74904657ec5457454e4371fb956648c74c422
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504802"
---
# <a name="view-hardware-and-software-inventory-for-windows-pcs"></a>Windows PC에 대한 하드웨어 및 소프트웨어 인벤토리 보기

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

> [!NOTE]
> 이 항목의 정보는 Intune 소프트웨어 클라이언트를 사용하여 PC를 관리하는 Windows 데스크톱에만 적용됩니다. 모바일 장치로 등록 된 Windows Pc의 인벤토리를 보려는 경우 [Intune에서 장치 세부 정보 보기](../remote-actions/device-inventory.md)를 참조 하세요.

Intune은 Intune 소프트웨어 클라이언트를 사용하여 PC로 관리하는 데스크톱의 하드웨어 및 소프트웨어에 대한 자세한 정보를 수집합니다. 다음 절차의 정보를 통해 다음을 만드는 방법에 대해 알아볼 수 있습니다.

- 관리하는 PC의 하드웨어 성능에 대한 정보를 표시하는 보고서

- 각 PC에 설치된 소프트웨어를 표시하는 보고서

- 보고서의 현재 데이터를 확인하기 위해 PC 인벤토리를 새로 고치는 방법

## <a name="to-display-information-about-pcs-you-manage"></a>관리하는 PC에 대한 정보를 표시하려면

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **보고서** &gt; **컴퓨터 인벤토리 보고서**를 선택합니다.

2. **새 보고서 만들기** 페이지에서 기본값을 그대로 사용하거나 보고서에서 반환할 결과를 필터링하도록 값을 사용자 지정합니다. 예를 들어 Windows 8.1을 실행하는 PC만 보고서에 표시되도록 선택할 수 있습니다.

3. **컴퓨터 인벤토리 보고서**를 새 창으로 열려면 **보고서 보기**를 선택합니다.

    **이름**, **섀시 종류** 또는 **제조업체**와 같은 각 열 제목을 선택하여 보고서를 열별로 정렬할 수 있습니다.

## <a name="to-display-software-installed-on-pcs-you-manage"></a>관리하는 PC에 설치된 소프트웨어를 표시하려면

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **보고서** &gt; **검색된 소프트웨어 보고서**를 선택합니다.

2. **새 보고서 만들기** 페이지에서 기본값을 그대로 사용하거나 보고서에서 반환할 결과를 필터링하도록 값을 사용자 지정합니다. 예를 들어 Microsoft에서 게시한 소프트웨어만 보고서에 표시되도록 선택할 수 있습니다.

3. **검색된 소프트웨어 보고서**를 새 창으로 열려면 **보고서 보기**를 선택합니다.

    **이름**, **게시자** 또는 **범주**와 같은 각 열 제목을 선택하여 보고서를 열별로 정렬할 수 있습니다. 목록 항목 옆에 있는 방향 화살표를 선택해서 목록에서 업데이트를 확장하여 세부 정보(예: 설치되어 있는 PC)를 표시할 수 있습니다.

## <a name="to-refresh-computer-inventory-to-ensure-it-is-current"></a>현재 컴퓨터 인벤토리를 확인하기 위해 새로 고치려면

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **그룹**&gt;**모든 디바이스**(또는 인벤토리를 새로 고치려는 PC가 포함된 다른 그룹)를 선택합니다.

2. PC를 선택하거나, **Ctrl** 키를 누른 상태에서 여러 PC를 선택합니다.

3. 작업 표시줄에서 **원격 작업** &gt; **인벤토리 새로 고침**을 선택합니다.

4. 작업 상태를 확인하려면 페이지의 오른쪽 아래 모서리에 있는 **원격 작업**을 선택합니다.

    **작업 상태** 대화 상자에는 현재 원격 작업, 작업 상태, 디바이스 이름 및 보고된 모든 오류 목록이 표시되고, 문제 해결 정보 링크도 제공됩니다.

## <a name="see-also"></a>참고 항목

[Intune 소프트웨어 클라이언트를 사용하는 일반 Windows PC 관리 작업](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)
