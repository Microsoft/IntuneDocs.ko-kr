---
title: Microsoft Intune에 Android Enterprise 시스템 앱 추가
titleSuffix: ''
description: Microsoft Intune에 Android Enterprise 시스템 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: priyar
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 613369070d847265f371a7b228a2b6d81bf813fe
ms.sourcegitcommit: 139853f8d6ea61786da7056cfb9024a6459abd70
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/26/2020
ms.locfileid: "76755258"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Microsoft Intune에 Android Enterprise 시스템 앱 추가

앱은 디바이스 또는 사용자 그룹에 할당하기 전에 먼저 앱을 Microsoft Intune에 추가해야 합니다. Android Enterprise 디바이스에서 시스템 앱이 지원됩니다. [Android Enterprise 전용 디바이스](../enrollment/android-kiosk-enroll.md) 또는 [완전 관리형 디바이스](../enrollment/android-fully-managed-enroll.md)용 시스템 앱을 사용하도록 설정할 수 있습니다.

## <a name="add-the-app"></a>앱 추가

다음을 수행하여 Azure Portal에서 Android Enterprise 시스템 앱을 Intune에 추가할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 유형 선택** 창의 사용 가능한 **기타** 유형 아래에서 **Android Enterprise 시스템 앱**을 선택합니다.
4. **선택**을 클릭합니다. **앱 추가** 단계가 표시됩니다.
**앱 정보** 페이지에서 앱 세부 정보를 추가합니다.
    - **앱 이름**: 앱의 이름을 입력합니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.  
    - **패키지 이름**: 패키지 이름을 입력합니다. Intune에서 패키지 이름이 유효한지 확인합니다.
5. **다음**을 클릭하여 **범위 태그** 페이지를 표시합니다.
8. **범위 태그 선택**을 클릭하여 앱의 범위 태그를 선택적으로 추가합니다. 자세한 내용은 [분산형 IT에 RBAC(역할 기반 액세스 제어) 및 범위 태그 사용](~/fundamentals/scope-tags.md)을 참조하세요.
9. **다음**을 클릭하여 **할당** 페이지를 표시합니다.
10. 앱의 그룹 할당을 선택합니다. 자세한 내용은 [그룹을 추가하여 사용자 및 디바이스 구성](~/fundamentals/groups-add.md)을 참조하세요. 
11. **다음**를 클릭하여 **검토 + 만들기** 페이지를 표시합니다. 앱에 대해 입력한 값과 설정을 검토합니다.
12. 완료되면 **만들기**를 클릭하여 Intune에 앱을 추가합니다.

만든 앱의 **개요 블레이드**가 표시됩니다.

> [!NOTE]
> 활성화/비활성화하려는 앱의 패키지 이름을 찾으려면 디바이스 OEM과 협력해야 합니다.

만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다. 

Android Enterprise 시스템 앱은 이미 플랫폼에 포함된 앱을 사용하거나 사용하지 않도록 설정합니다. 앱을 사용하도록 설정하려면 시스템 앱을 **필수**로 할당합니다. 앱을 사용하지 않도록 설정하려면 시스템 앱을 **제거**로 할당합니다. 시스템 앱은 사용자에게 사용 가능으로 할당할 수 없습니다.


## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)
