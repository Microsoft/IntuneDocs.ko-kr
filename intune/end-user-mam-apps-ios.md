---
title: 앱 보호 정책을 사용하는 iOS 앱
description: 이 항목에서는 앱 보호 정책을 통해 iOS 앱이 관리될 때 예상되는 결과를 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bc4ceb6fe8c96a80310ceb58e13850c65b676d0c
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52182384"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

 이 항목에서는 앱 보호 정책이 적용되는 앱을 사용하는 경우의 사용자 환경을 설명합니다. 앱 보호 정책은 사용자가 회사 계정을 사용하여 앱에 액세스하거나 회사의 비즈니스용 OneDrive 위치에 저장된 파일에 액세스하는 경우처럼 앱이 업무용으로 사용될 때만 적용됩니다.

##  <a name="access-apps"></a>앱 액세스

장치가 **Intune에 등록되지 않은** 경우 사용자가 앱을 처음 사용할 때 앱을 다시 시작하라는 메시지가 표시됩니다. 앱 보호 정책을 앱에 적용할 수 있도록 앱을 다시 시작해야 합니다.

<!--- The following screenshot from the Skype app illustrates this restart request: --->


<!---  ![Screenshot of the iOS device showing PIN prompt](../media/appmanagement/iOS_AppPINPrompt.png) --->

**Intune에서 관리를 위해 등록**된 장치의 경우 사용자에게 앱이 현재 관리되고 있다는 메시지가 표시됩니다.

##  <a name="use-apps-with-multi-identity-support"></a>다중 ID가 지원되는 앱 사용

다중 ID를 지원하는 앱을 사용하면 앱이 회사 컨텍스트에서 사용되는 경우 앱 보호 정책이 적용되는 동안 다른 계정(회사 및 개인)을 사용하여 동일한 앱에 액세스할 수 있습니다.  

예를 들어 사용자가 업무 데이터에 액세스하면 PIN 프롬프트가 표시됩니다. **Outlook 앱**에서는 사용자가 앱을 시작할 때 PIN을 입력하라는 메시지가 표시됩니다. **OneDrive 앱**에서는 사용자가 회사 계정을 입력할 때 PIN을 입력하라는 메시지가 표시됩니다.  Microsoft **Word**, **PowerPoint** 및 **Excel**의 경우에는 사용자가 회사의 비즈니스용 OneDrive 위치에 저장된 문서에 액세스할 때 PIN을 입력하라는 메시지가 표시됩니다.

- Intune을 통해 [앱 보호 및 다중 ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)를 지원하는 앱에 대해 자세히 알아봅니다.

앱 보호 정책은 앱을 업무용으로 사용할 때만 적용됩니다. 즉, 앱을 업무용으로 사용하는지 아니면 개인용으로 사용하는지에 따라 작동 방식이 달라질 수 있습니다.

##  <a name="manage-user-accounts-on-the-device"></a>장치에서 사용자 계정 관리

다중 ID 응용 프로그램에서 사용자는 계정을 여러 개 추가할 수 있습니다.  Intune 앱은 하나의 관리 계정만을 지원합니다.  Intune 앱은 관리되지 않는 계정 수를 제한하지 않습니다.

응용 프로그램에 관리 계정이 있는 경우:
*   사용자가 두 번째 관리 계정을 추가하려고 시도한다면 어떤 관리 계정을 사용할 것인지 선택하라는 메시지가 표시됩니다.  다른 계정은 제거됩니다.
*   IT 관리자가 두 번째 기존 계정에 정책을 추가한다면 어떤 관리 계정을 사용할 것인지 선택하라는 메시지가 표시됩니다.  다른 계정은 제거됩니다.

여러 사용자 계정이 처리되는 방법을 더욱 상세하게 파악하려면 다음 예제 시나리오를 확인하세요.

사용자 A는 **회사 X** 및 **회사 Y**에서 일합니다. 사용자 A는 각 회사에 회사 계정을 보유하고 둘 다 Intune을 사용하여 앱 보호 정책을 배포합니다. **회사 X**는 **회사 Y**보다 **먼저** 앱 보호 정책을 배포합니다. **회사 X**와 연결된 계정은 앱 보호 정책을 먼저 가져옵니다. 회사 Y와 연결된 사용자 계정을 앱 보호 정책으로 관리하려는 경우에는 회사 X와 연결된 사용자 계정을 제거하고 회사 Y와 연결된 사용자 계정을 추가해야 합니다.

### <a name="add-a-second-account"></a>두 번째 계정 추가

iOS 장치를 사용하는 경우 해당 장치에 두 번째 회사 계정을 추가하려고 하면 차단 메시지가 표시될 수 있습니다. 이 경우 계정이 표시되면 제거할 계정을 선택할 수 있습니다.

## <a name="next-steps"></a>다음 단계
[Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](end-user-mam-apps-android.md)
