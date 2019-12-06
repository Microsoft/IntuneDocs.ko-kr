---
title: Microsoft Intune에 Android Enterprise 시스템 앱 추가
titleSuffix: ''
description: Microsoft Intune에 Android Enterprise 시스템 앱을 추가하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
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
ms.openlocfilehash: d45455a97f8016527dce49839b5493f16b173d43
ms.sourcegitcommit: 73b362173929f59e9df57e54e76d19834f155433
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74563653"
---
# <a name="add-android-enterprise-system-apps-to-microsoft-intune"></a>Microsoft Intune에 Android Enterprise 시스템 앱 추가

앱은 디바이스 또는 사용자 그룹에 할당하기 전에 먼저 앱을 Microsoft Intune에 추가해야 합니다. Android Enterprise 디바이스에서 시스템 앱이 지원됩니다. [Android Enterprise 전용 디바이스](../enrollment/android-kiosk-enroll.md) 또는 [완전 관리형 디바이스](../enrollment/android-fully-managed-enroll.md)용 시스템 앱을 사용하도록 설정할 수 있습니다.

## <a name="add-the-app"></a>앱 추가

다음을 수행하여 Azure Portal에서 Android Enterprise 시스템 앱을 Intune에 추가할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **앱** > **모든 앱** > **추가**를 선택합니다.
3. **앱 추가** 창의 사용할 수 있는 **기타** 유형 아래에서 **Android Enterprise 시스템 앱**을 선택합니다.
4. 앱 정보를 구성하려면 **구성**을 선택하고 다음 정보를 제공합니다.
    - **앱 이름**: 앱의 이름을 입력합니다.
    - **게시자**: 앱 게시자의 이름을 입력합니다.  
    - **패키지 이름**: 패키지 이름을 입력합니다. Intune에서 패키지 이름이 유효한지 확인합니다.
5. **확인**을 선택합니다.
6. **추가**를 선택합니다.

> [!NOTE]
> 활성화/비활성화하려는 앱의 패키지 이름을 찾으려면 디바이스 OEM과 협력해야 합니다.

만든 앱이 앱 목록에 표시되며, 여기서 이 앱을 선택한 그룹에 할당할 수 있습니다. 

Android Enterprise 시스템 앱은 이미 플랫폼에 포함된 앱을 사용하거나 사용하지 않도록 설정합니다. 앱을 사용하도록 설정하려면 시스템 앱을 **필수**로 할당합니다. 앱을 사용하지 않도록 설정하려면 시스템 앱을 **제거**로 할당합니다. 시스템 앱은 사용자에게 사용 가능으로 할당할 수 없습니다.


## <a name="next-steps"></a>다음 단계

- [그룹에 앱 할당](apps-deploy.md)
