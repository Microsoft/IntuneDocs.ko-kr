---
title: 전원 최적화에서 메일 액세스 방지 | Microsoft Docs
description: Android에서 메일을 받을 수 있도록 전원 최적화를 해제하는 방법을 알아봅니다.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 07/07/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ad713f18-40a9-421f-aa2b-f8c21028d57c
searchScope:
- User help
ROBOTS: ''
ms.reviewer: maxles
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 98b8d4636b3f402b2b7246311e8027722fa01953
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55838122"
---
# <a name="outlook-wont-sync-managed-email-when-battery-optimization-for-android-is-turned-on"></a>Android의 경우 배터리 최적화가 설정되어 있으면 Outlook에서 관리되는 메일을 동기화하지 않습니다.

> [!IMPORTANT]
> 이 문제를 여기서 설명하는 이유는 이 문제에 대해 받은 고객 보고서 수가 증가했기 때문입니다. 다음 단계를 수행한 후에도 이 문제가 계속되면 [회사 지원팀](https://go.microsoft.com/fwlink/?linkid=2010980)에 추가 지원을 문의하세요.

Intune에서 디바이스를 등록하면 회사 리소스에 액세스할 수 있습니다. 가장 일반적인 리소스 중 하나는 메일 액세스입니다. Android 디바이스에 배터리 최적화가 설정되어 있으면 Outlook을 통해 메일에 액세스하는 경우 문제가 발생하는 것을 확인할 수 있었습니다. 배터리 최적화는 가능한 한 오랫동안 디바이스 전원이 유지되도록 자동으로 설정될 수 있습니다. 배터리 최적화는 자동 메일 다운로드를 중지하려고 하므로 전원 유지에 부분적으로 도움이 될 수 있습니다.

Microsoft Intune 팀은 이 문제를 해결하기 위해 적극적으로 노력하고 있습니다. 디바이스가 절전 모드로 전환되는 것을 방지하는 한 가지 방법은 배터리 충전이 30%가 넘는 수준으로 유지되도록 하는 것입니다. 절전 모드로 전환되는 경우 문제가 발생하지 않도록 하려면 배터리 최적화 및 절전 설정의 영향을 받는 앱 목록에서 회사 포털 및 Outlook을 제거해야 합니다.

많은 제조업체에서 많은 Android 디바이스를 만들고 있습니다. 따라서 모든 디바이스에 대해 수행되어야 할 정확한 단계를 설명할 수는 없습니다. 이 작업은 장치의 시스템 설정에서 수행해야 할 수도 있고 특정 제조업체별 설정에서 수행해야 할 수도 있습니다. Android 디바이스에서 이 문제를 해결하는 방법에 대한 몇 가지 일반적인 예를 제공해 드립니다.

## <a name="unmodified-android-devices"></a>수정되지 않은 Android 디바이스

많은 제조업체에서 Android 디바이스에 대한 수정을 추가합니다. 이를 통해 테마 및 알림과 같이 디바이스와 상호 작용하는 방식이 변경될 수 있습니다. Google은 일반적으로 전화에 대해 이러한 유형의 수정을 하지 않습니다. 예를 들어 Android 7.0 이상을 사용하는 Google Pixel 디바이스에서는 다음 단계에 따라 배터리 최적화에서 이들 앱을 제거합니다.

1. **설정**을 엽니다.
2. **배터리** > **자세히** > **배터리 최적화**를 탭합니다.
3. 그런 다음, 아래쪽 화살표를 탭하고 **최적화하지 않음**을 탭합니다.
4. 회사 포털 및 Outlook 앱을 선택하고 배터리 최적화를 해제합니다.

## <a name="samsung-devices"></a>Samsung 디바이스

Android 7.0 이상을 사용하는 Samsung 디바이스 등 다른 유형의 Android 디바이스에서는 Outlook 및 회사 포털 앱을 배터리 최적화에서 제거하기 위해 다른 단계를 따라야 합니다.

1. **설정**을 엽니다.
2. **메뉴(...)** > **특별 액세스** > **배터리 사용 최적화**를 탭합니다.
3. 드롭다운 목록에서 **모든 앱**을 선택합니다.
4. 회사 포털 및 Outlook 앱 옆에 있는 토글을 **해제**하여 배터리 최적화를 해제합니다.

또한 하위 버전의 Android가 포함된 Samsung 디바이스를 사용하는 경우 다음 단계에 따라 절전 모드에서 이러한 앱을 제거해야 합니다.

1. **설정**을 엽니다.
2. **디바이스 유지 관리** > **배터리** > **모니터링되지 않는 앱**을 탭합니다.
3. **앱 추가**를 탭합니다.
4. 회사 포털 및 Outlook 앱을 선택하고 **완료**를 탭합니다.

## <a name="oneplus-devices"></a>OnePlus 디바이스

이러한 설정을 찾는 또 다른 방법은 시스템 설정에서 검색하는 방법입니다. 예를 들어 Android 7.1.1을 사용하는 OnePlus 3에서는 다음 단계를 따릅니다. 

1. **시스템 설정**을 엽니다. 
2. **검색** 단추를 탭합니다. 화면 오른쪽 위에 돋보기처럼 표시됩니다. 
3. 검색에 **배터리 최적화**를 입력한 다음, 표시되는 **설정** 화면에서 **배터리 최적화** 옵션을 선택합니다. 
4. **배터리** > **배터리 최적화**를 탭합니다.
5. 회사 포털 및 Outlook 앱을 선택하고 **최적화하지 않음**을 선택합니다. **완료**를 탭합니다.

<!--On a OnePlus 5 device with Android 7.1.1, you would follow these steps to remove these apps from battery optimization:
1. Open **Settings**.
2. Tap **Battery** > **Battery optimization**.
3. Select the Company Portal and Outlook apps, then select **Don’t optimize**. Tap **Done**.-->

여전히 도움이 필요하세요? 회사 지원 부서에 문의하세요. IT 관리자의 연락처 정보는 [회사 포털 웹 사이트](https://go.microsoft.com/fwlink/?linkid=2010980)를 참조하세요.
