---
title: Microsoft Intune을 사용하여 MTD 디바이스 준수 정책 만들기
titleSuffix: Microsoft Intune
description: MTD 파트너 위협 수준을 사용하는 Intune 디바이스 준수 정책을 만들어서 모바일 디바이스가 회사 리소스에 액세스할 수 있는지 확인합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5d12254f-ffab-4792-b19c-ab37f5e02f35
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2315136fe277f06f6dbb11c13139a9dc193ce6f7
ms.sourcegitcommit: bccfbf1e3bdc31382189fc4489d337d1a554e6a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67549363"
---
# <a name="create-mobile-threat-defense-mtd-device-compliance-policy-with-intune"></a>Intune을 사용하여 MTD(Mobile Threat Defense) 디바이스 준수 정책 만들기

> [!NOTE] 
> 이 정보는 모든 Mobile Threat Defense 파트너에게 적용됩니다.

Intune 및 MTD를 사용하면 위협을 검색하고 모바일 디바이스의 위험을 평가할 수 있습니다. 위험을 평가하는 Intune 디바이스 준수 정책 규칙을 만들어 디바이스가 정책을 준수하는지 여부를 확인할 수 있습니다. 그런 다음 [조건부 액세스 정책](create-conditional-access-intune.md)을 사용하여 디바이스 준수 여부에 따라 서비스 액세스를 차단할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

MTD 설치의 일부로 MTD 파트너 콘솔에서 다양한 위협을 높음, 보통 및 낮음으로 분류하는 정책을 만들었습니다. 이제 Intune 디바이스 준수 정책에서 Mobile Threat Defense 수준을 설정해야 합니다.

MTD를 사용한 디바이스 준수 정책에 대한 필수 조건:

- Intune과 MTD 통합 설정

## <a name="to-create-an-mtd-device-compliance-policy"></a>MTD 디바이스 준수 정책을 만들려면

1. [Azure Portal](https://portal.azure.com/)로 이동한 다음 Intune 자격 증명을 사용하여 로그인합니다.

2. **Azure 대시보드**의 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune**을 선택합니다. **Intune 대시보드**가 열립니다.

4. **Intune 대시보드**에서 **디바이스 준수**를 선택한 다음 **관리** 섹션에서 **정책**을 선택합니다.

5. **정책 만들기**를 선택하고 디바이스 준수 **이름**, **설명**을 입력한 다음 **플랫폼**을 선택하고 **설정** 섹션에서 **구성**을 선택합니다.

6. **준수 정책** 창에서 **디바이스 상태**를 선택합니다.

7. **디바이스 상태** 창의 **디바이스가 디바이스 위협 수준 이하여야 함** 아래에 있는 드롭다운 목록에서 Mobile Threat Level을 선택합니다.

    a.  **보안**: 이 수준이 가장 안전합니다. 디바이스가 어떠한 위협에도 노출되지 않았으며 회사 리소스에 계속 액세스할 수 있습니다. 어떠한 위협이든 확인되는 디바이스는 비규격으로 평가됩니다.

    b.  **낮음**: 낮은 수준의 위협만 있는 디바이스는 규격 디바이스입니다. 더 높은 수준의 위협이 발생하면 디바이스는 규정 비준수 상태가 됩니다.

    c.  **보통**: 낮음 또는 보통 수준의 위협이 있는 디바이스는 규격 디바이스입니다. 높은 수준의 위협이 검색되는 경우 해당 디바이스는 비규격으로 간주됩니다.

    d.  **높음**: 보안이 가장 취약한 수준입니다. 이 수준은 모든 위협 수준을 허용하며 보고용으로만 Mobile Threat Defense를 사용합니다. 디바이스에 MTD 앱이 이 설정으로 활성화되어 있어야 합니다.

8. **확인**을 두 번 클릭하고 **만들기**를 선택합니다.

> [!IMPORTANT]
> Office 365 또는 기타 서비스용으로 조건부 액세스 정책을 만드는 경우 디바이스 준수 평가가 수행되며, 디바이스에서 위협이 해결될 때까지 회사 리소스에 대한 비규격 디바이스의 액세스가 차단됩니다.

## <a name="to-assign-an-mtd-device-compliance-policy"></a>MTD 디바이스 준수 정책을 할당하려면

사용자에게 디바이스 준수 정책을 할당하려면 이전에 구성한 정책을 선택합니다. 기존 정책은 **디바이스 준수 – 정책** 창에서 확인할 수 있습니다.

1. 사용자에게 할당할 정책을 선택한 다음 **할당**을 선택합니다. 이 작업은 **Azure Active Directory 보안 그룹**을 선택하고 이를 정책에 할당할 수 있는 창을 엽니다.

2. **포함할 그룹 선택**을 선택하여 Azure AD 보안 그룹을 표시하는 창을 엽니다.  **선택**을 선택하면 정책이 사용자에게 배포됩니다.

    > [!NOTE] 
    > 사용자에게 정책을 적용했습니다. 정책의 대상이 되는 사용자가 사용하는 디바이스에 대한 규정 준수 여부가 평가됩니다.

## <a name="next-steps"></a>다음 단계

- [Intune에서 MTD 사용](mtd-connector-enable.md)
