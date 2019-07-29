---
title: Microsoft Intune을 사용하여 사용자에게 사용자 지정 알림 보내기
titleSuffix: ''
description: Intune을 사용하여 사용자 지정 푸시 알림을 만들고 iOS 및 Android 디바이스의 사용자에게 보내기
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 7/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1caff820daf2e278c50d154873f569163b264315
ms.sourcegitcommit: c3a4fefbac8ff7badc42b1711b7ed2da81d1ad67
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/22/2019
ms.locfileid: "68378132"
---
# <a name="send-custom-notifications-in-intune"></a>Intune에서 사용자 지정 알림 보내기  

Microsoft Intune를 사용하여 관리형 iOS 및 Android 디바이스의 사용자에게 사용자 지정 알림을 보낼 수 있습니다. 이러한 메시지는 디바이스에 있는 다른 애플리케이션의 알림이 표시되는 것처럼 사용자 디바이스의 회사 포털 앱에서 표준 푸시 알림으로 표시됩니다. Intune 사용자 지정 알림은 Windows 디바이스에서는 지원되지 않습니다.   

사용자 지정 알림 메시지에는 짧은 제목과 500자 이하의 메시지 본문이 포함됩니다. 이러한 메시지는 일반 통신 용도에 맞게 사용자 지정할 수 있습니다.

## <a name="common-scenarios-for-sending-custom-notifications"></a>사용자 지정 알림 보내기의 일반적인 시나리오  

- 사용자 지정 알림을 사용하여 회사 포털에서 사용할 수 있는 새로운 앱에 관해 특정 사용자에게 알립니다.  
- 악천후로 건물 폐쇄와 같은 일정의 변경 사항을 모든 직원에게 알립니다.  

## <a name="considerations-for-using-custom-notifications"></a>사용자 지정 알림 사용에 관한 고려 사항  

**디바이스 구성**:  
- 사용자가 사용자 지정 알림을 받으려면 디바이스에 회사 포털 앱이 설치되어 있어야 합니다. 또한 회사 포털 앱이 푸시 알림을 보내도록 허용하는 권한도 구성했어야 합니다. 회사 포털에서 사용자에게 알림을 허용할지 묻는 메시지를 표시합니다.  
- Android에서는 Google Play 서비스가 필수 종속성입니다.  

**알림 만들기**:  
- 메시지를 작성하려면 **조직**의 **업데이트** 권한을 포함하는 Intune역할이 할당된 계정을 사용합니다. 사용자에게 권한을 할당하려면 [역할 할당](role-based-access-control.md#role-assignments)을 참조하세요.  
- 사용자 지정 알림은 제목 50자와 메시지 500자로 제한됩니다.  
- Intune에서는 보낸 메시지를 저장하지 않습니다. 메시지를 다시 보내려면 해당 메시지를 다시 작성해야 합니다.  
- 시간당 최대 25개의 메시지만 보낼 수 있습니다. 이 제한 사항은 테넌트 수준에 적용됩니다.  
- 각 알림은 최대 25개 그룹을 직접 대상으로 할 수 있습니다. 중첩된 그룹은 이 합계 계산에 포함되지 않습니다.  
- 그룹에는 사용자 또는 디바이스가 포함될 수 있지만 메시지는 사용자에게만 전송되며 사용자가 등록한 각 iOS 또는 Android 디바이스로 전송됩니다.  

**배달**:  
- Intune은 알림을 보낸 후 최대 1시간 안에 배달하려고 합니다.  
- Intune에서 사용자의 회사 포털 앱에 메시지를 보내면, 포털 앱은 푸시 알림을 만듭니다. 사용자가 앱에 로그인하지 않아도 알림이 디바이스에서 푸시됩니다.  
- Intune 및 회사 포털 앱에서는 사용자 지정 알림의 배달은 보장할 수 없습니다. 사용자 지정 알림은 몇 시간의 지연 후에 표시될 수 있으므로 긴급한 메시지에는 가능하면 사용하지 않아야 합니다.  
- Intune의 사용자 지정 알림 메시지는 디바이스에서 표준 푸시 알림으로 표시됩니다. 알림을 받을 때 iOS 디바이스에서 회사 포털 앱이 열리는 경우 알림은 푸시 알림이 아니고 앱에 표시됩니다.  
- 사용자 지정 알림은 iOS 및 Android 디바이스 모두에서 디바이스 설정에 따라 잠금 화면에 표시될 수 있습니다.  
- Android 디바이스에서는 다른 앱이 사용자 지정 알림 데이터에 액세스할 수도 있습니다. 따라서 중요한 통신에는 사용자 지정 알림을 사용하지 마세요.  
- 최근에 등록 취소된 디바이스의 사용자나 그룹에서 제거된 사용자가 이후 해당 그룹에 전송된 사용자 지정 알림을 계속 받을 수 있습니다.  마찬가지로 그룹에 사용자 지정 알림을 보낸 후 그룹에 사용자를 추가하는 경우 새로 추가된 사용자가 이전에 전송된 알림 메시지를 받을 수 있습니다.  

## <a name="send-a-custom-notification"></a>사용자 지정 알림 보내기  

1. 알림을 만들고 보낼 권한이 있는 계정으로 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인하고 **디바이스** > **사용자 지정 알림 보내기**로 이동합니다.  

2. 기본 탭에 다음을 지정하고 **다음**을 선택하여 계속합니다.  
   - **제목** –이 알림의 제목을 지정합니다. 제목은 50자로 제한됩니다.  
   - **본문** – 메시지를 지정합니다. 메시지는 500자로 제한됩니다.

   ![사용자 지정 알림 만들기](./media/custom-notifications/custom-notifications.png)  

3. **할당** 탭에서 이 사용자 지정 알림을 보낼 그룹을 선택하고 다음을 선택하여 계속합니다.  

4. **검토 + 만들기** 탭에서 정보를 검토하고 알림을 보낼 준비가 되면 **만들기**를 선택합니다.  

Intune은 사용자가 만든 메시지를 즉시 처리합니다. 메시지를 보냈다는 확인은 지정 알림이 전송되었음을 확인하는 Intune 알림뿐입니다.  

![보낸 알림 확인](./media/custom-notifications/notification-sent.png)  

Intune은 사용자가 보낸 사용자 지정 알림을 추적하지 않으며 디바이스에서는 디바이스의 알림 센터 외부에서 수신을 기록하지 않습니다.  

## <a name="receive-a-custom-notification"></a>사용자 지정 알림 받기  

디바이스에서 사용자에게 Intune에서 보낸 사용자 지정 알림 메시지가 회사 포털 앱의 표준 푸시 알림으로 표시됩니다. 이러한 알림은 사용자가 디바이스의 다른 앱에서 받는 푸시 알림과 비슷합니다.  

iOS 디바이스에서 알림을 받을 때 회사 포털 앱이 열리는 경우 알림은 푸시 알림이 되지 않고 포털 앱에 표시됩니다.  

알림은 사용자가 해제할 때까지 유지됩니다.  

## <a name="next-steps"></a>다음 단계  
[디바이스 관리](device-management.md)
