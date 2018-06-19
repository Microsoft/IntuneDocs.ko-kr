---
title: 관리자 역할에 대한 콘솔 보기 사용자 지정
description: 이 항목에서는 Intune 관리 콘솔 보기를 필터링하여 관리자만 해당 역할에 필요한 항목을 확인하도록 할 수 있습니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 12/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e0783eaa-67dc-410e-9e80-4d3aa72f36d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: bdc248689f586a44f4c84568b9d9f9c1fa3e059a
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31013639"
---
# <a name="customize-intune-console-views-according-to-admin-roles"></a>관리자 역할에 따라 Intune 콘솔 보기 사용자 지정

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune 관리 콘솔 보기를 필터링하여 관리자만 해당 역할에서 참조해야 하는 항목을 확인하도록 할 수 있습니다. 예를 들어, 맬웨어 정의 업데이트 또는 장치에 대한 암호 재설정을 관리 콘솔 운영자에게만 허용할 수 있습니다. 특정 사용자에게 할당하는 사전 설정된 **명칭**을 사용하여 수행할 수 있습니다. 이러한 사용자가 관리 콘솔에 액세스하는 경우 자신의 명칭에 해당하는 항목만 볼 수 있습니다.

## <a name="to-create-a-custom-view"></a>사용자 지정 보기를 만들려면

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **관리**&gt; **서비스 관리자**를 선택합니다.

2. 서비스 관리자의 목록에서 명칭을 변경할 사용자를 선택한 다음 **액세스 관리**를 선택합니다.

3. **액세스 관리** 대화 상자에서 선택한 사용자에게 제공할 액세스 수준을 선택합니다. 다음 중 하나를 선택할 수 있습니다.

   -   **모든 권한**
   -   **읽기 전용 권한**
   -   **기술 지원팀 - 그룹 노드**

   전체 액세스 및 읽기 전용 액세스는 설명이 따로 필요하지 않습니다. <!--- **Helpdesk - Groups Node** allows users to choose from one of the following designations that provide custom levels of access to the Intune admin console:--->

   **기술 지원팀-그룹 노드**는 관리자가 다음과 같은 작업에서 확인하고 수행하는 내용을 제한합니다.

   -   사용자 및 장치 목록을 확인합니다. 관리자는 필터를 사용하여 보기를 수정할 수 없습니다. 그러나 그룹 필터링을 사용하여 관리자가 볼 수 있는 내용을 수정할 수 있습니다. 자세한 내용은 [Microsoft Intune에서 그룹을 사용하여 사용자 및 장치 관리](use-groups-to-manage-users-and-devices-with-microsoft-intune.md)를 참조하세요.

   -   사용자 및 장치 목록을 인쇄합니다.

   -   사용자 및 장치 목록을 내보냅니다.

   -   사용자 또는 장치의 속성을 봅니다.

   -   다음과 같은 원격 작업을 수행합니다.

       -   전체 맬웨어 검색 실행

       -   빠른 맬웨어 검색 실행

       -   컴퓨터 다시 시작

       -   맬웨어 정의 업데이트

       -   정책 새로 고치기

       -   인벤토리 새로 고치기

       -   장치 원격 잠금

       -   암호 재설정

다음에 구성한 관리자가 Intune 관리 콘솔을 여는 경우 지정된 액세스 수준이 부여됩니다.
