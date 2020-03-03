---
title: Intune 사용자에게 역할 할당
description: Microsoft Intune에서 사용자에게 기본 제공 또는 사용자 지정 역할을 할당하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19fff092f7eccfc6de2a027c7834c52698176cbf
ms.sourcegitcommit: 5881979c45fc973cba382413eaa193d369b8dcf6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/24/2020
ms.locfileid: "77569169"
---
# <a name="assign-a-role-to-an-intune-user"></a>Intune 사용자에게 역할 할당

Intune 사용자에게 [기본 제공](role-based-access-control.md#built-in-roles) 또는 [사용자 지정](create-custom-role.md) 역할을 할당할 수 있습니다.

역할을 만들거나 편집하거나 할당하려면 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.
- **전역 관리자**
- **Intune 서비스 관리자**

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **테넌트 관리** > **역할** > **모든 역할**을 선택합니다.

2. **Intune 역할 - 모든 역할** 블레이드에서 할당할 기본 제공 역할 > **할당** > **할당**을 선택합니다.

5. **기본 사항** 페이지에서 **할당 이름** 및 선택적 **할당 설명**을 입력하고 **다음**을 선택합니다.

6. **관리 그룹** 페이지에서 권한을 부여할 사용자가 포함된 그룹을 선택합니다. **다음**을 선택합니다.

7. **범위(그룹)** 페이지에서 위의 구성원이 관리할 수 있는 사용자/디바이스를 포함하는 그룹을 선택합니다. **다음**을 선택합니다.

8. **범위(태그)** 페이지에서 이 역할 할당을 적용할 태그를 선택합니다. **다음**을 선택합니다.

9. **검토 + 만들기** 페이지에서 완료되면 **만들기**를 선택합니다. 새 할당이 할당 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계
- [Intune에서 역할 기반 액세스 제어에 대해 자세히 알아보기](role-based-access-control.md)
- [사용자 지정 역할 만들기](create-custom-role.md)


