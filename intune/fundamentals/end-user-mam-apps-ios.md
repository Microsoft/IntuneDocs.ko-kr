---
title: 앱 보호 정책을 사용하는 iOS 앱
description: 이 항목에서는 앱 보호 정책을 통해 iOS 앱이 관리될 때 예상되는 결과를 설명합니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: b57e6525-b57c-4cb4-a84c-9f70ba1e8e19
ms.reviewer: andcerat
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 165ce160339647e396b9cfc3a8374f21c77665f8
ms.sourcegitcommit: f9dc50642efa8656054ef67f9335b9b46b655f93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/02/2020
ms.locfileid: "75606624"
---
# <a name="what-to-expect-when-your-ios-app-is-managed-by-app-protection-policies"></a>iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황

Intune 앱 보호 정책은 직장이나 학교에서 사용하는 앱에 적용됩니다. 직원이나 학생이 개인 컨텍스트에서 앱을 사용할 경우에도 환경에 차이가 발생하지 않는다는 의미입니다. 그러나 직장이나 학교 컨텍스트에서 계정 선택, 업데이트 설정, 지원 문의 등이 표시될 수 있습니다. 이 문서에서는 Intune 보호 앱을 액세스하고 사용할 때 사용자의 환경에 대해 안내합니다.  

## <a name="access-apps"></a>앱 액세스

디바이스가 **Intune에 등록되지 않은** 경우 사용자가 앱을 처음 사용할 때 앱을 다시 시작하라는 메시지가 표시됩니다. 앱 보호 정책을 앱에 적용할 수 있도록 앱을 다시 시작해야 합니다.

<!--- The following screenshot from the Skype app illustrates this restart request: --->

<!---  ![Screenshot of the iOS device showing PIN prompt](./media/end-user-mam-apps-ios/iOS_AppPINPrompt.png) --->

**Intune에서 관리를 위해 등록**된 디바이스의 경우 사용자에게 앱이 현재 관리되고 있다는 메시지가 표시됩니다.

## <a name="use-apps-with-multi-identity-support"></a>다중 ID가 지원되는 앱 사용

다중 ID를 지원하는 앱은 동일한 앱에 액세스할 때 직장 및 개인 계정을 별도로 사용하도록 합니다. 디바이스 PIN 입력 등의 앱 보호 정책은 사용자가 앱을 직장 및 학교 컨텍스트에서 액세스할 때 활성화됩니다.   

사용자의 정책 구성에 따라 앱 사용 시 PIN 표시가 다르게 나타날 수 있습니다.  예를 들면 다음과 같은 정책을 구성할 수 있습니다.       
* Microsoft Outlook에서는 앱을 실행할 때 PIN을 입력하도록 합니다. 
* OneDrive에서는 사용자가 직장 계정에 로그인할 때 PIN을 입력하도록 합니다.  
* Microsoft Word, PowerPoint, Excel은 비즈니스용 OneDrive 위치에 저장된 문서에 액세스할 때 PIN을 입력하도록 표시합니다.  

- Intune을 통해 [앱 보호 및 다중 ID](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)를 지원하는 앱에 대해 자세히 알아봅니다.  

## <a name="manage-user-accounts-on-the-device"></a>디바이스에서 사용자 계정 관리  

Intune 앱 보호 정책은 사용자가 앱마다 일 또는 학교 관리 계정을 하나씩 두도록 제한합니다. 앱 보호 정책은 사용자가 추가할 수 있는 비관리 계정의 수를 제한하지 않습니다.   

- 사용자가 두 번째 관리 계정을 추가하려고 시도한다면 어떤 관리 계정을 사용할 것인지 선택하라는 메시지가 표시됩니다. 사용자가 두 번째 계정을 추가할 경우 첫 번째 계정은 삭제됩니다.
- 사용자 계정에 또 다른 보호 정책을 추가할 경우 사용자가 어떤 관리 계정을 사용할지 선택하도록 합니다. 다른 계정은 제거됩니다. 

동일한 사용자라면 관리 계정 간 전환 또는 선택 옵션이 표시되지 않습니다. 다음 디바이스에서는 이런 옵션을 사용할 수 없습니다.
* Intune 관리 디바이스  
* 타사 모빌리티 관리 솔루션으로 관리되고 IntuneMAMUPN 설정으로 구성된 디바이스 

다음 예제 시나리오에서 여러 사용자 계정이 처리되는 방법을 설명합니다.  

사용자 A는 **회사 X** 및 **회사 Y**에서 일합니다. 사용자 A는 각 회사에 회사 계정을 보유하고 둘 다 Intune을 사용하여 앱 보호 정책을 배포합니다. **회사 X**는 **회사 Y**보다 **먼저** 앱 보호 정책을 배포합니다. **회사 X**와 연결된 계정은 앱 보호 정책을 먼저 가져옵니다. 회사 Y와 연결된 사용자 계정을 앱 보호 정책으로 관리하려는 경우에는 회사 X와 연결된 사용자 계정을 제거하고 회사 Y와 연결된 사용자 계정을 추가해야 합니다.  

## <a name="next-steps"></a>다음 단계

[Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](end-user-mam-apps-android.md)
