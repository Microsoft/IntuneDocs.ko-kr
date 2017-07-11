---
title: "그룹에 앱을 할당하는 방법 | Microsoft 문서"
titleSuffix: Intune Azure preview
description: "Intune Azure 미리 보기: Intune에 앱을 추가한 후 사용자 또는 장치 그룹에 할당할 수 있습니다."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc349e22-9e1c-42ba-9e70-fb2ef980ef7a
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 1246ef539c044b894b4e4a93f449e60e6462600a
ms.contentlocale: ko-kr
ms.lasthandoff: 05/23/2017

---

# <a name="how-to-assign-apps-to-groups-with-microsoft-intune"></a>Microsoft intune을 사용하여 그룹에 앱을 할당하는 방법

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Intune에 앱을 추가한 후 사용자 및 장치로 가져올 수 있습니다. 해당 앱을 할당하면 됩니다.

Intune에서 관리되는지 여부에 상관없이 장치에 앱을 할당할 수 있습니다. 다음 표를 사용하면 사용자 및 장치에 앱을 할당하는 다양한 옵션을 쉽게 이해할 수 있습니다.

||||
|-|-|-|-|
|&nbsp;|Intune에 등록된 장치|Intune에 등록되지 않은 장치|
|사용자에게 할당|예|예|
|장치에 할당|예|아니요|
|래핑된 앱 또는 Intune SDK 통합 앱(앱 보호 정책용) 할당|예|예|
|사용 가능으로 앱 할당|예|예|
|필수로 앱 할당|예|아니요|
|앱 제거|예|아니요|
|최종 사용자가 회사 포털 앱에서 사용 가능한 앱 설치|예|아니요|
|최종 사용자가 웹 기반 회사 포털에서 사용 가능한 앱 설치|예|예|

> [!NOTE]
> 현재 Intune에 등록되지 않은 장치에 iOS 및 Android 앱(기간 업무 및 스토어 구매 모두)을 할당할 수 있습니다.

## <a name="changes-to-how-you-assign-apps-to-groups-in-the-intune-preview"></a>Intune 미리 보기에서 그룹에 앱을 할당하는 방법에 대한 변경 내용

Intune Azure 미리 보기에서는 더 이상 Intune 그룹을 사용하여 앱을 할당하지 않습니다. 이제 Azure AD(Azure Active Directory) 보안 그룹을 사용합니다. 이 때문에 Intune 자식 그룹에 앱을 할당한 경우 특히 앱 할당의 작동 방식에 대한 일부 변경 내용을 알아야 합니다.
가장 중요한 사항은 Azure AD에 자식 그룹의 개념이 없다는 것입니다. 그러나 일부 그룹에 동일한 멤버가 포함될 수 있습니다. 이 경우 클래식 Intune과 Intune Azure 미리 보기 간의 동작이 서로 다릅니다. 다음 표에서는 이 동작을 보여 줍니다.

||||||
|-|-|-|-|-|
|**Intune 클래식(테넌트 마이그레이션 전)**|-|**Intune Azure(테넌트 마이그레이션이 완료된 후)**|-|**추가 정보**|
|**부모 그룹 할당 의도**|**자식 그룹 할당 의도**|**이전 부모 및 자식 그룹의 공통 멤버에 대한 할당 의도**|**상위 그룹의 멤버에 대한 할당 의도 작업**|-|
|사용 가능|필수|필수 및 사용 가능|사용 가능|필수 및 사용 가능은 필요에 따라 할당되는 앱을 회사 포털 앱에서도 볼 수 있음을 의미합니다.
|해당 없음|사용 가능|해당 없음|해당 없음|해결 방법: Intune 부모 그룹에서 '적용할 수 없음' 할당 의도를 제거합니다.
|필수|사용 가능|필수 및 사용 가능|필수|-|
|필수 및 사용 가능<sup>1</sup>|사용 가능|필수 및 사용 가능|필수 및 사용 가능|-|
|필수|해당 없음|필수|필수|-|
|필수 및 사용 가능|해당 없음|필수 및 사용 가능|필수 및 사용 가능|-|
|필수|제거|필수|필수|-|
|필수 및 사용 가능|제거|필수 및 사용 가능|필수 및 사용 가능|-|
<sup>1</sup> 관리 되는 iOS 스토어 앱의 경우에만 이러한 앱을 Intune에 추가하고 필수로 할당할 때 필수 및 사용 가능 의도로 자동으로 생성됩니다.

다음 작업을 수행하여 할당 충돌을 방지할 수 있습니다.

1.    이전에 관련 Intune 부모 및 자식 그룹에 앱을 할당한 경우 테넌트 마이그레이션이 시작되기 전에 이러한 할당을 제거하는 것이 좋습니다.
2.    부모 그룹에서 자식 그룹을 제거하고 이전 자식 그룹의 멤버를 포함하는 새 그룹을 만듭니다. 그런 다음 이 그룹에 대한 새로운 앱 할당을 만들 수 있습니다.
참고: 이전 부모 그룹이 "모든 사용자"인 경우 자식 그룹의 멤버를 포함하지 않는 새 동적 그룹을 만들어야 합니다.
사용자 및 장치 그룹의 경우 [Azure Portal](https://portal.azure.com/)에서 그룹을 변경해야 합니다. [클래식 Azure Portal](https://manage.windowsazure.com/)에서는 사용자 그룹만 변경할 수 있습니다.


## <a name="how-to-assign-an-app"></a>앱을 할당하는 방법

1. Azure 포털에 로그인합니다.
2. **추가 서비스** > **모니터링 + 관리** > **Intune**을 선택합니다.
3. **Intune** 블레이드에서 **Mobile Apps**를 선택합니다.
1. **모바일 앱** 워크로드에서 **관리** > **앱**을 선택합니다.
2. 앱 목록 블레이드에서 할당할 앱을 클릭합니다.
3. <*앱 이름*> - **개요** 블레이드에서 **관리** > **할당**을 선택합니다.
4. **그룹 선택**을 선택하고 **그룹 선택** 블레이드에서 앱을 할당할 Azure AD 그룹을 선택합니다.
5. 선택한 각 앱에 대해 **할당 유형**을 선택합니다.
    - **사용 가능** - 사용자가 회사 포털 앱 또는 웹 사이트에서 앱을 설치합니다.
    - **해당 사항 없음** - 앱이 설치되거나 회사 포털에 표시되지 않습니다.
    - **필수** - 앱이 선택한 그룹의 장치에 설치됩니다.
    - **제거** - 앱이 선택한 그룹의 장치에서 제거됩니다.
    - **등록없이 사용 가능** - 이 앱을 Intune에 등록되지 않은 장치의 사용자 그룹에 할당합니다. 도움말은 위 표를 참조하세요.
6. 작업이 끝나면 **저장**을 선택합니다.

이제 선택한 그룹에 앱이 할당됩니다.

앱 할당을 모니터링하는 데 유용한 정보는 [앱을 모니터링하는 방법](apps-monitor.md)을 참조하세요.
