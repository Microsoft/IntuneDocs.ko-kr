---
title: 빠른 시작 - 사용자 관리를 위한 그룹 만들기
titleSuffix: Microsoft Intune
description: 이 빠른 시작에서는 Microsoft Intune을 사용하여 기존 사용자를 기반으로 그룹을 만듭니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/24/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 723f4b4e-3090-4811-84ff-6af652abea5a
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a8a444f886a5b754fd6ba3763e183db0fe95d5f
ms.sourcegitcommit: d2ac912b834c4840de9cc92ba1815b6ecfbfb52b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68482979"
---
# <a name="quickstart-create-a-group-to-manage-users"></a>빠른 시작: 사용자 관리를 위한 그룹 만들기

이 빠른 시작에서는 Intune을 사용하여 기존 사용자를 기반으로 그룹을 만듭니다. 그룹은 사용자를 관리하고 회사 리소스에 직원의 액세스를 제어하는 데 사용됩니다. 이러한 리소스는 회사 인트라넷의 일부일 수도 있고 SharePoint 사이트, SaaS 앱, 웹앱 등의 외부 리소스일 수도 있습니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

>[!NOTE]
>Intune은 편의를 위해 콘솔에서 미리 만든 **모든 사용자** 및 **모든 디바이스** 그룹에 기본 최적화 기능을 제공합니다.

## <a name="prerequisites"></a>전제 조건

- 이 빠른 시작을 완료하려면 [사용자를 만들어야 합니다](quickstart-create-user.md).

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune 포털](https://aka.ms/intuneportal)에 [글로벌 관리자 또는 Intune 서비스 관리자](users-add.md#types-of-administrators)로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="create-a-group"></a>그룹 만들기

이 빠른 시작 시리즈에서 나중에 사용될 그룹을 만듭니다. 그룹 만들기:

1. **Microsoft Intune** 창을 연 후에는 **그룹** > **새 그룹**을 선택합니다.
2. **그룹 형식** 드롭다운 상자에서 **보안**을 선택합니다.
3. **그룹 이름** 필드에서 새 그룹의 이름(예: **Contoso 테스터**)을 입력합니다.
4. 그룹 **설명**을 추가합니다.
5. **멤버 자격 형식**을 **할당됨**으로 설정합니다. 
6. **멤버**를 클릭하고 목록에서 그룹에 하나 이상의 멤버를 선택합니다.

    ![Microsoft Intune에서 그룹 만들기 스크린샷](./media/quickstart-use-groups-01.png)

7. **선택** > **만들기**를 클릭합니다.

그룹을 성공적으로 만들었으면 **모든 그룹** 목록에 표시됩니다. 

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Intune을 사용하여 기존 사용자를 기반으로 그룹을 만들었습니다. Intune에 그룹을 추가하는 방법에 대한 자세한 내용은 [사용자 및 디바이스를 구성하는 그룹 추가](groups-add.md)를 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: Windows 10 디바이스에 대한 자동 등록 설정](quickstart-setup-auto-enrollment.md)
