---
title: Intune에서 디바이스를 그룹으로 분류
titleSuffix: Microsoft Intune
description: 디바이스를 보다 쉽게 관리하도록 그룹으로 분류하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 02/22/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 7b668c37-40b9-4c69-8334-5d8344e78c24
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: a7bb551784af2f61b61cfc57b968e32ab4db2f7e
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55848052"
---
# <a name="categorize-devices-into-groups"></a>디바이스를 그룹으로 분류

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

디바이스를 보다 쉽게 관리하기 위해 Microsoft Intune 디바이스 범주를 사용하여 정의된 범주에 따라 자동으로 디바이스를 그룹에 추가할 수 있습니다.

디바이스 범주에는 다음 워크플로가 사용됩니다.
1. 사용자가 자신의 디바이스를 등록할 때 선택할 수 있는 범주를 만듭니다.
2. iOS 및 Android 디바이스의 사용자는 디바이스를 등록할 경우 구성된 범주 목록에서 범주를 선택해야 합니다. Windows 디바이스에 범주를 할당하려면 사용자는 회사 포털 웹 사이트를 사용해야 합니다.
3. 그런 다음 이러한 그룹에 정책 및 앱을 배포할 수 있습니다.

원하는 모든 디바이스 범주를 만들 수 있습니다. 예를 들면 다음과 같습니다.
- POS 디바이스
- 데모 디바이스
- 판매
- 계정
- Manager

## <a name="how-to-configure-device-categories"></a>디바이스 범주를 구성하는 방법

### <a name="step-1-create-device-categories-on-the-intune-blade-of-the-azure-portal"></a>1단계: Azure Portal의 Intune 블레이드에서 디바이스 범주 만들기
1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스 등록**을 선택합니다.
2. **디바이스 등록** 블레이드에서 **디바이스 범주**를 선택합니다.
3. **디바이스 범주** 페이지에서 **만들기**를 선택하여 새 범주를 추가합니다.
4. **디바이스 범주 만들기** 블레이드에서 새 범주의 **이름** 및 선택적 **설명**을 입력합니다.
5. 작업이 완료되면 **만들기**를 선택합니다. 범주 목록에서 새 범주를 확인할 수 있습니다.

2단계에서 Azure AD(Azure Active Directory) 보안 그룹을 만들 때 디바이스 범주 이름을 사용합니다.

### <a name="step-2-create-azure-active-directory-security-groups"></a>2단계: Azure Active Directory 보안 그룹 만들기
이 단계에서는 디바이스 범주 및 디바이스 범주 이름에 따라 Azure Portal에서 동적 그룹을 만듭니다.

계속하려면 Azure AD 설명서에서 [특성을 사용하여 고급 규칙 만들기](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/#using-attributes-to-create-rules-for-device-objects)를 참조하세요.

이 섹션의 정보를 통해 **deviceCategory** 특성을 사용하는 고급 규칙이 있는 디바이스 그룹을 만듭니다. 예를 들면 **device.deviceCategory-eq** "*Azure Portal에서 가져온 디바이스 범주 이름*"입니다.

디바이스 그룹을 구성하고 사용자가 해당 디바이스를 등록한 후에는 구성한 범주의 목록으로 표시됩니다. 범주를 선택하고 등록을 완료한 후에 이 디바이스는 선택한 범주에 해당하는 Active Directory 보안 그룹에 추가됩니다.

### <a name="view-the-categories-of-devices-that-you-manage"></a>관리하는 디바이스의 범주 보기

1.  [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스**를 선택합니다.

2.  **관리** 아래에서 **모든 디바이스**를 선택합니다.

3.  디바이스 목록에서 **디바이스 범주** 열을 확인합니다.

**디바이스 범주** 열이 표시되지 않는 경우 **열**을 선택합니다. 목록에서 **디바이스 범주**를 선택한 다음, **적용**을 선택합니다.

### <a name="change-the-category-of-a-device"></a>디바이스의 범주 변경

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **디바이스**를 선택합니다.
2. **관리** 섹션 아래 **디바이스** 블레이드에서 **모든 디바이스**를 선택합니다.
3. 디바이스 목록에서 원하는 디바이스를 선택합니다. **관리** 섹션 아래의 디바이스 속성 블레이드에서 **속성**을 선택합니다.
4. 다음 블레이드에서 선택한 디바이스의 **디바이스 범주**를 이전에 구성한 범주 이름으로 변경할 수 있습니다.

## <a name="after-you-configure-device-groups"></a>디바이스 그룹 구성 후

iOS 및 Android 디바이스의 사용자는 해당 디바이스를 등록할 경우 구성된 범주 목록에서 범주를 선택해야 합니다. 범주를 선택하고 등록을 완료한 후에 이 디바이스는 선택한 범주에 해당하는 Intune 디바이스 그룹 또는 Active Directory 보안 그룹에 추가됩니다.

Windows 사용자는 회사 포털 웹 사이트를 사용해 범주를 선택해야 합니다.

사용자는 플랫폼과 관계없이 디바이스를 등록한 후 언제든지 toportal.manage.microsoft.com으로 이동할 수 있습니다. 사용자가 회사 포털 웹 사이트에 액세스하여 **내 디바이스**로 이동하게 합니다. 사용자는 페이지에 나열되어 있는 등록된 디바이스를 선택하고 범주를 선택할 수 있습니다.

범주를 선택하고 나면 작성한 해당 그룹에 디바이스가 자동으로 추가됩니다. 범주를 구성하기 전에 디바이스가 이미 등록돼 있는 경우 회사 포털 웹 사이트에서 디바이스에 대한 알림을 사용자에게 표시합니다. 이렇게 하면 사용자는 다음에 iOS 또는 Android에서 회사 포털 앱에 액세스할 때 범주를 선택할 수 있습니다.

## <a name="further-information"></a>추가 정보
- Azure Portal에서 디바이스 범주를 편집할 수 있지만, 해당 범주를 참조하는 모든 Azure AD 보안 그룹을 수동으로 업데이트해야 합니다.

- 범주를 삭제하면 해당 범주에 할당된 디바이스의 범주 이름이 **할당되지 않음**으로 표시됩니다.
