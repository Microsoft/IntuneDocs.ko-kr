---
title: 앱 보호 정책을 사용하는 iOS 앱
titlesuffix: Microsoft Intune
description: 보호 정책이 있는 iOS 앱에서 예상되는 상황을 알아봅니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 586d9440-3813-4dec-b865-8bd319befde0
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e1b2789c8f3b57bbc97e06e8793a96656f74a54d
ms.sourcegitcommit: 2061f7a442efc96c8afd5db764d11531563c7e39
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703284"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

앱 보호 정책이 적용되는 iOS 앱에 대한 사용자 경험을 알아봅니다. 앱 보호 정책은 앱이 회사 컨텍스트에서 사용되는 경우에만 적용됩니다. 예를 들어 회사 계정을 사용하여 앱에 액세스할 때 또는 회사의 OneDrive 위치에 저장된 파일에 액세스할 때입니다.
##  <a name="accessing-apps"></a>앱 액세스

장치가 **Intune에 등록되지 않은** 경우 사용자는 앱을 처음 사용할 때 앱을 다시 시작하도록 요구됩니다.  앱 보호 정책을 앱에 적용할 수 있도록 앱을 다시 시작해야 합니다. 다음 스크린샷은 Skype 앱을 사용하여 이러한 과정을 보여 줍니다.


![PIN 프롬프트를 보여 주는 iOS 장치의 스크린샷](./media/ios-pin-prompt.png)

**Intune에서 관리를 위해 등록**된 장치의 경우 사용자에게 앱이 현재 관리되고 있다는 메시지가 표시됩니다.

![PIN 프롬프트를 포함하는 회사 메시지에 의해 관리되는 iOS 장치를 보여 주는 스크린샷](./media/ios-managed-devices-pin-prompt.png)

##  <a name="using-apps-with-multi-identity-support"></a>다중 ID가 지원되는 앱 사용

사용자가 작업 관련 데이터에 액세스하려고 할 때만 앱 보호 정책이 적용됩니다. 사용자가 개인용 앱에 액세스하려고 하면 다른 동작이 표시될 수 있습니다. 또한 정책은 아직 저장되지 않은 새 콘텐츠에 적용되지 않습니다. 새 콘텐츠는 SharePoint 또는 비즈니스용 OneDrive와 같은 회사 위치에 저장된 후에만 회사 정보로 간주됩니다.

다중 ID를 지원하는 앱에 대해 Intune은 사용자가 작업 데이터에 액세스하는 경우만 앱 보호 정책을 적용합니다.  예를 들어 사용자는 PIN 프롬프트를 얻을 수 있습니다.  **Outlook 앱**에서 사용자가 앱을 시작하는 경우 프롬프트가 표시됩니다. **OneDrive 앱**에서는 사용자가 회사 계정을 입력할 때 프롬프트가 표시됩니다.  Microsoft **Word**, **PowerPoint** 및 **Excel**에서 프롬프트는 사용자가 회사의 OneDrive 문서에 액세스할 때 나타납니다.
##  <a name="managing-user-accounts-on-the-device"></a>장치에서 사용자 계정 관리

Intune은 장치 당 하나의 사용자 계정에 앱 보호 정책을 배포하도록 지원합니다.

* 사용 중인 앱에 따라 두 번째 사용자는 장치에서 차단될 수도 있고 차단되지 않을 수도 있습니다. 그러나 어떤 경우이든 앱 보호 정책을 가져오는 첫 번째 사용자만이 정책에 영향을 받습니다.
  * **Microsoft Word**, **Excel** 및 **PowerPoint**는 추가 사용자 계정에 대 한 액세스를 차단하지 않습니다. 그러나 해당 사용자 계정은 앱 보호 정책의 영향을 받지 않습니다.

  * **OneDrive 및 Outlook 앱**의 경우 회사 계정을 하나만 사용할 수 있습니다.  해당 앱에서는 여러 회사 계정의 추가가 차단됩니다.  그러나 사용자를 장치에서 제거한 다음, 해당 장치에 다른 사용자를 추가할 수 있습니다.

* 앱 보호 정책을 배포하기 전에 장치에는 기존 사용자 계정이 여러 개 있을 수 있습니다. 이 경우 앱 보호 정책이 배포되는 첫 번째 계정은 Intune 앱 보호 정책에서 관리합니다.


Intune에서 여러 사용자 계정을 어떻게 처리하는지 알고 싶으면 다음 예제 시나리오를 읽습니다.

사용자 A는 **회사 X** 및 **회사 Y**에서 일합니다. 사용자 A는 각 회사에 회사 계정을 보유하고 둘 다 Intune을 사용하여 앱 보호 정책을 배포합니다. **회사 X**는 **회사 Y**보다 **먼저** 앱 보호 정책을 배포합니다. **회사 X**와 연결된 계정은 앱 보호 정책을 가져오지만 회사 Y와 관련된 계정이 아닙니다. 회사 Y 사용자 계정이 앱 보호 정책에 의해 관리되게 하려면 사용자 A는 회사 X 사용자 계정을 제거해야 합니다.
### <a name="adding-a-second-account"></a>두 번째 계정 추가

iOS 장치를 사용하는 경우 동일한 장치에 두 번째 회사 계정을 추가하려고 하면 차단 메시지가 표시될 수 있습니다.  계정이 표시되고 제거하려는 계정을 선택할 수 있습니다.

![메시지 및 예 및 아니요 옵션을 차단하는 대화 상자의 스크린 샷](./media/ios-switch-user.PNG)

## <a name="next-steps"></a>다음 단계
[Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](app-protection-enabled-apps-android.md)
### <a name="see-also"></a>참고 항목
[Microsoft Intune으로 앱 보호 정책 만들기 및 배포](app-protection-policies.md)
