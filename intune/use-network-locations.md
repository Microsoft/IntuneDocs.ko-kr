---
title: Microsoft Intune에서 네트워크 위치별로 Android 디바이스 바인딩 - Azure | Microsoft Docs
description: Android 디바이스용 Microsoft Intune에서 네트워크 위치를 만들거나 구성합니다. 디바이스의 네트워크 위치를 기반으로 하여 디바이스를 비준수로 표시할 수 있습니다. 디바이스가 네트워크 위치 외부로 나가면 회사 리소스에 대한 액세스를 차단할 수 있습니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: ddc58aed6e7a1efaecd8b7e7cf51a39e43d14e58
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66044336"
---
# <a name="use-locations-network-fence-in-intune"></a>Intune에서 위치(네트워크 펜스) 사용

디바이스가 위치를 벗어나면 회사 네트워크에 대한 액세스를 차단할 수 있습니다. Intune의 **위치** 기능에서 이 기능을 제공합니다. 

네트워크 펜싱이라고도 하는 네트워크 위치 기반 준수 정책을 만들 수 있습니다. 정책을 준수하려면 디바이스가 회사 네트워크에 연결되어 있어야 합니다. 이 정책은 조건부 액세스 정책과 함께 사용할 수 있으므로 디바이스가 회사 네트워크에 연결되어 있는 *경우에만* 회사 리소스에 액세스할 수 있습니다. 디바이스가 회사 네트워크에 연결되어 있지 않으면 디바이스가 준수되지 않으며 회사 리소스에 대한 액세스가 손실됩니다.

다음과 같은 경우를 고려할 수 있습니다.

제조 시설에서 일부 직원은 Android 디바이스를 사용합니다. 직원이 시설 또는 공장의 외부에서 Android 디바이스를 사용합니다. 무단 액세스를 방지하기 위해 다음을 수행할 수 있습니다.

1. **제조 현장**이라고 하는 IPv4 범위가 있는 위치를 만듭니다.
2. 이러한 디바이스를 회사 네트워크에 연결해야 하는 준수 정책을 만들고 이 정책을 할당합니다.
3. 디바이스가 제조 공장의 외부로 나가면 디바이스가 비준수 디바이스로 간주되어 회사 리소스에 액세스할 수 없게 됩니다.

또한 [비준수에 대한 작업](#configure-the-actions-for-noncompliance)을 추가할 수 있습니다. 디바이스가 온-프레미스 및 네트워크 위치에 다시 들어오면 회사 리소스에 다시 액세스할 수 있습니다.

## <a name="prerequisites"></a>전제 조건

위치 기반 준수 정책을 만들려면 다음을 수행합니다.

- 네트워크 위치를 디바이스에서 연결하는 게이트웨이 서버, DHCP 서버 및/또는 DNS 서버에 대한 IPV4 네트워크 범위로 만듭니다.
- 이러한 위치를 사용하는 준수 정책을 만들고, 디바이스가 더 이상 네트워크 위치에 연결되지 않을 때 수행할 작업을 정의합니다.
- 업데이트된 회사 포털 앱이 있는 Android 디바이스 6.0 이상

## <a name="create-a-location"></a>위치 만들기

1. Intune에서 **디바이스 준수** > **위치** > **만들기**를 차례로 선택합니다.

2. 다음 속성을 입력합니다.  

   - 필수 사항입니다. 위치에 대한 **이름**을 입력합니다(예: **제조 현장** 또는 **건물 44 보안**).
   - 선택 사항입니다. CIDR(Classless Interdomain Routing) 표기법을 사용하여 **IPv4 범위**를 입력합니다(예: `aaa.bbb.ccc.ddd/n`).
   - 선택 사항입니다. **IPv4 게이트웨이** 주소를 입력합니다(예: `aaa.bbb.ccc.ddd`).
   - 선택 사항입니다. **IPv4 DHCP 서버** 주소를 입력합니다(예: `aaa.bbb.ccc.ddd`).
   - 선택 사항입니다. **IPv4 DNS 서버** 주소 목록을 입력합니다. 이 설정은 **하위 집합 일치**를 사용합니다. 디바이스의 IPv4 DNS 서버가 정의된 값의 하위 집합인 경우 디바이스는 펜스 내(IN the fence)로 간주됩니다. 주소를 줄당 하나씩 입력해야 합니다. 예를 들어 다음과 같습니다.  
     `aaa.bbb.ccc.ddd`  
     `aaa.bbb.ccc.ddd`
   - 선택 사항입니다. **DNS 접미사** 목록을 입력합니다. 이 설정은 **하위 집합 일치**를 사용합니다. 디바이스의 DNS 접미사가 정의된 값의 하위 집합인 경우 디바이스는 펜스 내로 간주됩니다. 도메인 이름을 줄당 하나씩 입력해야 합니다. 예를 들어 다음과 같습니다.  
     `contoso.com`  
     `contoso.org`

3. 변경 내용을 **저장**합니다.

## <a name="create-the-location-compliance-policy"></a>위치 준수 정책 만들기

준수 정책을 만드는 경우 **플랫폼**에 대해 **Android**를 선택합니다. **위치**에서 추가한 네트워크 위치 중 하나 이상을 선택할 수 있습니다. 이러한 위치는 디바이스에 대해 만드는 네트워크 펜스에 속합니다.

[네트워크 위치 기반 준수 정책 만들기](compliance-policy-create-android.md#locations)에서 몇 가지 지침을 제공하고 있습니다.

## <a name="configure-the-actions-for-noncompliance"></a>비준수에 대한 작업 구성

준수 정책이 만들어지면 비준수에 대한 기본 작업이 해당 디바이스에 적용됩니다. 더 많은 작업을 추가할 수 있습니다. 예를 들어 디바이스에서 더 이상 위치를 준수하지 않는 경우 사용자에게 이메일을 보내는 작업을 추가합니다.

[비준수를 위한 작업 추가](actions-for-noncompliance.md)에서 몇 가지 지침을 제공하고 있습니다.

## <a name="company-portal-app"></a>회사 포털 앱

디바이스가 사용자의 위치에 연결되면 회사 포털 앱에서 해당 디바이스가 준수로 표시됩니다. 디바이스가 사용자의 위치 중 하나에 연결되어 있지 않으면 해당 디바이스가 비준수로 표시됩니다.

## <a name="next-steps"></a>다음 단계
[디바이스 준수 정책 모니터링](compliance-policy-monitor.md)  
[준수 정책 시작](device-compliance-get-started.md)
