---
title: 비즈니스용 Microsoft 스토어에서 앱 관리
titlesuffix: Microsoft Intune
description: 비즈니스용 Microsoft Store에서 Intune에 앱을 동기화한 다음, 해당 앱을 할당하고 추적하는 방법을 알아봅니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2ed5d3f0-2749-45cd-b6bf-fd8c7c08bc1b
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c30d20592a95f7894bb040f9e8fe5a2e3ddd0166
ms.sourcegitcommit: 1134ecd733356277b40eb1c7f2b318b36d387e00
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50915753"
---
# <a name="how-to-manage-apps-you-purchased-from-the-microsoft-store-for-business-with-microsoft-intune"></a>Microsoft Intune을 사용하여 비즈니스용 Microsoft 스토어에서 구입한 앱을 관리하는 방법

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

[비즈니스용 Microsoft 스토어](https://www.microsoft.com/business-store)는 개별적으로 또는 대량으로 조직에 대한 앱을 찾고 구입할 수 있는 위치를 제공합니다. 스토어를 Microsoft Intune에 연결하여 Azure Portal에서 대량 구매 앱을 관리할 수 있습니다. 예를 들면 다음과 같습니다.
* Intune을 사용하여 저장소에서 구입한 앱 목록을 동기화할 수 있습니다.
* 동기화되는 앱은 Intune 관리 콘솔에 나타납니다. 이러한 앱을 다른 앱처럼 할당할 수 있습니다.
* Intune 관리 콘솔에서 사용 가능한 라이선스 수 및 사용되는 라이선스 수를 추적할 수 있습니다.
* Intune은 사용 가능한 라이선스가 부족한 경우에 앱의 할당 및 설치를 차단합니다.
* 비즈니스용 Microsoft Store에서 관리하는 앱은 사용자가 회사를 떠나거나 관리자가 사용자 및 사용자 장치를 제거하면 라이선스를 자동으로 해지합니다.

## <a name="before-you-start"></a>시작하기 전에

비즈니스용 Microsoft 스토어에서 앱 동기화 및 할당을 시작하기 전에 다음 정보를 검토합니다.

- Intune을 조직에 대한 모바일 장치 관리 기관으로 구성합니다.
- 비즈니스용 Microsoft 스토어에서 계정을 등록해야 합니다.
- Microsoft 비즈니스 스토어 계정을 Intune과 연결한 후에는 나중에 다른 계정으로 변경할 수 없습니다.
- 스토어에서 구입한 앱을 Intune에 수동으로 추가하거나 Intune에서 삭제할 수 없습니다. 비즈니스용 Microsoft 스토어와만 동기화할 수 있습니다.
- 비즈니스용 Microsoft 스토어에서 구매한 온라인 및 오프라인 사용이 허가된 앱은 Intune Portal에 동기화됩니다. 그런 다음 이러한 앱을 장치 그룹 또는 사용자 그룹에 배포할 수 있습니다. 
- 온라인 앱 설치는 스토어에서 관리합니다.
- 무료 오프라인 앱도 Intune에 동기화할 수 있습니다. 이런 앱은 스토어가 아닌 Intune을 통해 설치됩니다.
- 이 기능을 사용하려면 장치가 Active Directory Domain Services에 가입하거나 작업 공간에 연결되어 있어야 합니다.
- 등록된 장치가 1511 릴리스의 Windows 10 이상을 사용 중이어야 합니다.

또한 비즈니스용 Microsoft 스토어에서 동기화된 오프 라인 사용이 허가된 앱 및 관련 집합은 이제 UI에서 단일 앱 항목으로 통합되게 됩니다. 개별 패키지에서의 모든 배포 세부 정보는 단일 항목으로 마이그레이션됩니다. Azure Portal에서 관련 집합을 보려면 **클라이언트 앱** 블레이드에서 **앱 라이선스**를 선택합니다.

## <a name="associate-your-microsoft-store-for-business-account-with-intune"></a>비즈니스용 Microsoft 스토어 계정을 Intune에 연결
Intune 콘솔에서 동기화를 사용하기 전에 관리 도구로 Intune을 사용하도록 스토어 계정을 구성해야 합니다.
1. Intune에 로그인하는 데 사용하는 동일한 테넌트 계정을 사용하여 업무용 스토어에 로그인해야 합니다.
2. 업무용 스토어에서 **설정** > **관리 도구**를 선택합니다.
3. 관리 도구 페이지에서 **관리 도구 추가**를 선택하고 **Microsoft Intune**을 선택합니다.

> [!NOTE]
> 이전에는 앱을 할당하는 하나의 관리 도구만 비즈니스용 Microsoft 스토어에 연결할 수 있었습니다. 이제 Intune 및 Configuration Manager와 같은 여러 관리 도구를 스토어에 연결할 수 있습니다.

이제 계속하고 Intune 콘솔에서 동기화를 설정할 수 있습니다.

## <a name="configure-synchronization"></a>동기화 구성

1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스** > **Intune**을 선택합니다. Intune은 **모니터링 + 관리** 섹션에 있습니다.
3. **Intune** 창에서 **클라이언트 앱**을 선택합니다.
1. **클라이언트 앱** 창에서 **설치** > **비즈니스용 Microsoft Store**를 선택합니다.
2. **사용**을 클릭합니다.
3. 아직 수행하지 않은 경우에는 링크를 클릭하여 비즈니스용 Microsoft 스토어에 등록하고 이전에 설명된 대로 계정을 연결합니다.
5. **언어** 드롭다운 목록에서 비즈니스용 Microsoft Store의 앱이 Azure Portal에 표시되는 언어를 선택합니다. 표시되는 언어에 관계없이 사용 가능한 경우 최종 사용자의 언어로 설치됩니다.
6. **동기화**를 클릭하여 Microsoft 스토어에서 구입한 앱을 Intune으로 가져옵니다.

## <a name="synchronize-apps"></a>앱 동기화

1. **클라이언트 앱** 워크로드에서 **설치** > **비즈니스용 Microsoft Store**를 선택합니다.
2. **동기화**를 클릭하여 Microsoft 스토어에서 구입한 앱을 Intune으로 가져옵니다.

## <a name="assign-apps"></a>앱 할당

다른 Intune 앱을 할당하는 방법과 마찬가지로 스토어에서 앱을 할당합니다. 자세한 내용은 [Microsoft intune을 사용하여 그룹에 앱을 할당하는 방법](apps-deploy.md)을 참조하세요. 그러나 **모든 앱** 페이지에서 앱을 할당하는 대신 **사용이 허가된 앱** 페이지에서 앱을 할당합니다.

오프라인 앱은 사용자 그룹, 장치 그룹 또는 사용자와 장치를 포함하는 그룹을 대상으로 할 수 있습니다.
장치의 특정 사용자 또는 장치의 모든 사용자에 대해 오프라인 앱을 설치할 수 있습니다. 


비즈니스용 Microsoft 스토어를 할당할 때 앱을 설치하는 각 사용자에서 라이선스가 사용됩니다. 할당된 앱에 사용 가능한 라이선스를 모두 사용한 경우에는 복사본을 더 이상 할당할 수 없습니다. 다음 작업 중 하나를 수행합니다.
* 일부 장치에서 앱을 제거합니다.
* 충분한 라이선스를 보유한 사용자만 대상으로 하도록 현재 할당 범위를 줄입니다.
* 비즈니스용 Microsoft 스토어에서 더 많은 앱 사본을 구입합니다.

## <a name="remove-apps"></a>앱 제거

비즈니스용 Microsoft Store에서 동기화된 앱을 제거하려면 비즈니스용 Microsoft Store에 로그인하여 앱을 반환해야 합니다.

![앱 세부 정보 제거의 스크린샷](./media/microsoft-store-for-business-01.png)

> [!NOTE]
> 개인 스토어에서 앱의 가시성을 제거해도 Intune에서 동기화되지 않습니다. 앱을 반환해야 합니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Intune을 사용하여 대량 구매 앱 및 전자책 관리](vpp-apps.md)