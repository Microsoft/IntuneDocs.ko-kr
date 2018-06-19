---
title: 장치 준수 정책
description: 이 항목에서는 장치 준수 정책의 개념과 작동 원리를 설명합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 0775107a-6662-41c8-9404-be14bbb599f3
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c9c93d29ddee6d01e057c01a44c81950b857213
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31031756"
---
# <a name="device-compliance-policies-in-microsoft-intune"></a>Microsoft Intune의 장치 준수 정책

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="what-is-a-compliance-policy"></a>준수 정책이란?
회사 데이터를 보호하는 데 도움이 되려면 회사 앱 및 데이터에 액세스하는 데 사용되는 장치가 특정 규칙을 준수하는지 확인해야 합니다. 이러한 규칙에는 장치에 액세스하는 데 PIN을 사용하고 장치에 저장된 데이터를 암호화하는 규칙이 포함됩니다. 이러한 규칙의 집합을 준수 정책이라고 합니다.

## <a name="how-should-i-use-compliance-policies"></a>준수 정책은 어떻게 사용해야 합니까?
준수 정책을 조건부 액세스 정책과 함께 사용하여 준수 정책 규칙을 준수하는 장치만 메일과 기타 서비스에 액세스할 수 있도록 허용할 수 있습니다. 두 정책을 함께 사용할 수 있는 방법을 알아보려면 [Microsoft Intune을 사용한 메일, O365 및 기타 서비스에 대한 액세스 제한](restrict-access-to-email-and-o365-services-with-microsoft-intune.md) 문서를 참조하세요.

또한 준수 정책을 조건부 액세스와 독립적으로 사용할 수 있습니다. 준수 정책을 독립적으로 사용하는 경우 대상 장치는 평가되고 준수 상태와 함께 보고됩니다. 예를 들어 암호화되지 않는 장치의 수 또는 탈옥 또는 루팅된 장치에 대해 보고할 수 있습니다. 그러나 준수 정책을 독립적으로 사용하는 경우 회사 리소스에 대한 액세스 제한이 없습니다.

사용자에게 준수 정책을 배포합니다. 준수 정책을 사용자에게 배포하면 사용자 장치의 준수가 확인됩니다.
정책이 배포된 후 모바일 장치가 정책을 수신하기까지 걸리는 시간에 대해 알아보려면 [장치의 설정 및 기능 관리](/intune-classic/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies#frequently-asked-questions-about-intune-policies)를 참조하세요.

다음 표에는 준수 정책이 지원하는 장치 유형이 나와 있습니다. 또한 준수 정책을 조건부 액세스 정책과 함께 사용할 경우 비준수 설정을 관리하는 방법을 설명합니다.

-----------------------------

|정책 설정| Windows 8.1 이상| Windows Phone 8.1 이상| iOS 8.0 이상|Android 4.0 이상<br/>Samsung Knox Standard 4.0 이상|
|-----|----|----|----|----|
|**PIN 또는 암호 구성** |재구성됨|재구성됨|재구성됨|격리됨|
|**장치 암호화**|해당 없음|재구성됨|재구성됨(PIN 설정)|격리됨|
|**탈옥 또는 루팅된 장치**|해당 없음|해당 없음|격리됨(설정 아님)|격리됨(설정 아님)|
|**전자 메일 프로필**|해당 없음|해당 없음|격리됨|해당 없음|
|**최소 OS 버전**|격리됨|격리됨|격리됨|격리됨|
|**최대 OS 버전**|격리됨|격리됨|격리됨|격리됨|
|**Windows 상태 증명**|격리됨: Windows 10 및 Windows 10 Mobile<br /><br />해당 없음: Windows 8.1|해당 없음|해당 없음|해당 없음|

------------------------------

**재구성됨** = 장치 운영 체제에서 준수를 적용하도록 요구합니다. (예를 들어 사용자에게 PIN을 설정하도록 강제합니다.)

**격리됨** = 장치 운영 체제에서 준수를 적용하도록 요구하지 않습니다. (예를 들어, Android 장치에서 사용자에게 장치를 암호화하도록 강제하지 않습니다.) 장치가 호환되지 않으면 다음 작업이 수행됩니다.

-   조건부 액세스 정책이 사용자에게 적용될 경우 장치가 차단됩니다.

-   회사 포털은 모든 준수 문제에 대해 사용자에게 알립니다.

## <a name="next-steps"></a>다음 단계
[장치 준수 정책 만들기](create-a-device-compliance-policy-in-microsoft-intune.md)

[장치 준수 정책 배포 및 모니터링](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### <a name="see-also"></a>참고 항목
[메일 및 O365 서비스에 대한 액세스 제한](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)
