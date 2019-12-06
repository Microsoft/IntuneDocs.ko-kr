---
title: Microsoft Intune을 사용하여 MTD 디바이스 준수 정책 만들기
titleSuffix: Microsoft Intune
description: MTD 파트너 위협 수준을 사용하는 Intune 디바이스 준수 정책을 만들어서 모바일 디바이스가 회사 리소스에 액세스할 수 있는지 확인합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 504c77fb56918cf97312e70f50b38356f9f7efef
ms.sourcegitcommit: a7b479c84b3af5b85528db676594bdb3a1ff6ec6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74409691"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Intune을 사용하여 MTD(Mobile Threat Defense) 디바이스 준수 정책 만들기

Intune 및 MTD를 사용하면 위협을 검색하고 모바일 디바이스의 위험을 평가할 수 있습니다. 위험을 평가하는 Intune 디바이스 준수 정책 규칙을 만들어 디바이스가 정책을 준수하는지 여부를 확인할 수 있습니다. 그런 다음 [조건부 액세스 정책](create-conditional-access-intune.md)을 사용하여 디바이스 준수 여부에 따라 서비스 액세스를 차단할 수 있습니다.

> [!NOTE]
> 이 정보는 모든 Mobile Threat Defense 파트너에게 적용됩니다.

## <a name="before-you-begin"></a>시작하기 전에

MTD 설치의 일부로 MTD 파트너 콘솔에서 다양한 위협을 높음, 보통 및 낮음으로 분류하는 정책을 만들었습니다. 이제 Intune 디바이스 준수 정책에서 Mobile Threat Defense 수준을 설정해야 합니다.

MTD를 사용한 디바이스 준수 정책에 대한 필수 조건:

- Intune과 MTD 통합 설정

## <a name="to-create-an-mtd-device-compliance-policy"></a>MTD 디바이스 준수 정책을 만들려면

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **준수 정책** > **정책 만들기**를 선택합니다.

3. 디바이스 준수 정책 **이름**, **설명**을 지정하고, **플랫폼**을 선택한 후 **설정** 섹션 아래에서 **구성**을 선택합니다.

4. **준수 정책** 창에서 **디바이스 상태**를 선택합니다.

5. **디바이스 상태** 창의 **디바이스가 디바이스 위협 수준 이하여야 함** 아래에 있는 드롭다운 목록에서 Mobile Threat Level을 선택합니다.

   - **보안**: 이 수준이 가장 안전합니다. 디바이스가 어떠한 위협에도 노출되지 않았으며 회사 리소스에 계속 액세스할 수 있습니다. 어떠한 위협이든 확인되는 디바이스는 비규격으로 평가됩니다.

   - **낮음**: 낮은 수준의 위협만 있는 디바이스는 규격 디바이스입니다. 더 높은 수준의 위협이 발생하면 디바이스는 규정 비준수 상태가 됩니다.

   - **보통**: 낮음 또는 보통 수준의 위협이 있는 디바이스는 규격 디바이스입니다. 높은 수준의 위협이 검색되는 경우 해당 디바이스는 비규격으로 간주됩니다.

   - **높음**: 보안이 가장 취약한 수준입니다. 이 수준은 모든 위협 수준을 허용하며 보고용으로만 Mobile Threat Defense를 사용합니다. 디바이스에 MTD 앱이 이 설정으로 활성화되어 있어야 합니다.

6. **확인**를 두 번 선택한 다음, **만들기**를 선택하여 정책을 만듭니다.

> [!IMPORTANT]
> Office 365 또는 기타 서비스용으로 조건부 액세스 정책을 만드는 경우 디바이스 준수 평가가 수행되며, 디바이스에서 위협이 해결될 때까지 회사 리소스에 대한 비규격 디바이스의 액세스가 차단됩니다.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>MTD 디바이스 준수 정책을 할당하려면

사용자에게 디바이스 준수 정책을 할당하려면 다음을 수행합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **준수 정책**을 선택합니다.

3. 사용자에게 할당 하려는 정책을 선택하고 **할당**을 선택합니다. 사용할 수 있는 옵션을 사용하여 이 정책을 수신할 그룹을 *포함* 및 *제외*합니다.  

4. 저장을 선택하여 할당을 완료합니다. 할당을 저장하면 해당 정책이 선택한 사용자에게 배포되고 해당 디바이스의 규정 준수 여부가 평가됩니다.

## <a name="next-steps"></a>다음 단계

[Intune에서 MTD 사용](mtd-connector-enable.md)
