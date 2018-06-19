---
title: Microsoft Intune에서 그룹 만들기
titleSuffix: ''
description: 사용자가 액세스할 수 있는 정책 및 앱을 더 쉽게 관리할 수 있도록 사용자를 그룹으로 구성합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/26/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 39a93fb5-d318-4997-a409-b64549a00e7a
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d039cfe5509990ff15fe8a1cb476ad44037d60df
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31021016"
---
# <a name="create-a-group-to-manage-your-users-and-data-access"></a>사용자 및 데이터 액세스를 관리하는 그룹 만들기

그룹은 사용자를 관리하고 회사 리소스에 직원의 액세스를 제어하는 데 사용됩니다. 이러한 리소스는 디렉터리의 일부이거나 SaaS 앱 또는 SharePoint 사이트와 같은 외부 리소스일 수 있습니다.

Microsoft Intune은 Azure AD(Azure Active Directory)를 사용하여 회사 리소스에 대한 액세스를 관리합니다. 이 액세스는 디렉터리의 역할을 사용하여 제어됩니다. 그런 다음 Intune은 모바일 장치에 대해 이 액세스를 관리하여 해당 그룹의 구성원이 리소스에 액세스할 수 있도록 합니다.

## <a name="how-do-i-create-a-group"></a>그룹을 만들려면 어떻게 하나요?

1. [Azure 포털](https://portal.azure.com)에 로그인합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Microsoft Intune** 창을 열면 **그룹**을 선택합니다.
4. **사용자 및 그룹 - 모든 그룹** 창에서 **새 그룹** 명령을 선택합니다.
5. **그룹** 창에서 **그룹 형식**을 선택합니다.
5. 그룹의 **이름**과 **설명**을 추가합니다.
6. **멤버 자격 유형**을 **할당됨**으로 설정합니다. 테스트 그룹에 대해 **Office 기능 사용**을 설정하지 마세요.
7. 그룹의 **멤버**를 선택합니다.
7. **만들기**를 클릭합니다.

그룹을 성공적으로 만들었으면 **모든 그룹** 목록에 표시됩니다. 목록에 표시되지 않는 경우 다른 그룹을 만들어 보세요.

## <a name="next-steps"></a>다음 단계

[정책 시작](get-started-policies.md) - 사용자가 장치에서 권한이 없는 작업을 수행하지 않도록 하는 정책을 만듭니다.

## <a name="learn-more"></a>자세한 정보

* [Intune에서 그룹을 사용하여 등록 제한 설정](groups-add.md)
* [Azure Active Directory의 그룹을 사용하여 회사 리소스에 대한 액세스 관리](https://docs.microsoft.com/azure/active-directory/active-directory-manage-groups)
