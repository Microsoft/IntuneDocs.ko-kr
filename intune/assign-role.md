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
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: pjain
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0539e4d12173ba2c7ba8d3af3364daf69ddbbf34
ms.sourcegitcommit: 74911a263944f2dbd9b754415ccda6c68dae0759
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71071543"
---
# <a name="assign-a-role-to-an-intune-user"></a>Intune 사용자에게 역할 할당

Intune 사용자에게 [기본 제공](role-based-access-control.md#built-in-roles) 또는 [사용자 지정](create-custom-role.md) 역할을 할당할 수 있습니다.

역할을 만들거나 편집하거나 할당하려면 계정에 Azure AD의 다음 사용 권한 중 하나가 있어야 합니다.
- **전역 관리자**
- **Intune 서비스 관리자**

각 기본 제공 역할에 대한 사용 권한의 전체 목록은 [Intune RBAC 테이블](https://gallery.technet.microsoft.com/Intune-RBAC-table-2e3c9a1a)을 참조하세요.

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.

2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.

3. **Intune** 블레이드에서 **역할** > **모든 역할**을 선택합니다.

4. **Intune 역할 - 모든 역할** 블레이드에서 할당할 기본 제공 역할을 선택합니다.

5. <역할 이름> - **개요** 블레이드에서 **관리** > **할당**을 선택합니다. 

6. 사용자 지정 역할 블레이드에서 **할당**을 선택합니다.

7. **역할 할당** 블레이드에서 할당에 대한 **할당 이름** 및 선택적 **할당 설명**을 입력합니다.

8. **구성원(그룹)** 의 경우, 사용 권한을 부여할 사용자가 포함된 그룹을 선택합니다.

9. **범위(그룹)** 의 경우, 위의 구성원이 관리할 수 있는 사용자/디바이스를 포함하는 그룹을 선택합니다.

10. **범위(태그)** 의 경우, 이 역할 할당을 적용할 태그를 선택합니다.

11. 작업이 완료되면 **확인**을 선택합니다. 새 할당이 할당 목록에 표시됩니다.


## <a name="next-steps"></a>다음 단계
- [Intune에서 역할 기반 액세스 제어에 대해 자세히 알아보기](role-based-access-control.md)
- [사용자 지정 역할 만들기](create-custom-role.md)
