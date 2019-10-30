---
title: Intune을 사용하여 MTD(Mobile Threat Defense) 앱 보호 정책 만들기
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 MTD(Mobile Threat Defense) 앱 보호 정책 만들기
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 15d986bc5017a44571c6194f9c6b53167b671349
ms.sourcegitcommit: 06a1fe83fd95c9773c011690e8520733e1c031e3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72794422"
---
# <a name="create-mobile-threat-defense-app-protection-policy-with-intune"></a>Intune을 사용하여 Mobile Threat Defense 앱 보호 정책 만들기

> [!NOTE] 
> 이 문서는 이 문서는 앱 보호 정책을 지원하는 모든 MTD(Mobile Threat Defense) 파트너에게 적용됩니다. Better Mobile(Android), Zimperium(iOS), Lookout for Work(Android/iOS).

Intune 및 MTD를 사용하면 위협을 검색하고 모바일 디바이스의 위험을 평가할 수 있습니다. 위험을 평가하는 Intune 앱 보호 정책을 만들어 디바이스가 회사 데이터에 대한 액세스를 허용하는지 확인할 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

MTD 설치의 일부로 MTD 파트너 콘솔에서 다양한 위협을 높음, 보통 및 낮음으로 분류하는 정책을 만들었습니다. 이제 Intune 앱 보호 정책에서 Mobile Threat Defense 수준을 설정해야 합니다.

MTD를 사용한 앱 보호 정책에 대한 필수 구성 요소:

- Intune과 MTD 통합 설정 이 통합이 없으면 MTD 앱 보호 정책이 적용되지 않습니다.

## <a name="to-create-an-mtd-app-protection-policy"></a>MTD 앱 보호 정책을 만들려면

1. [Azure Portal](https://portal.azure.com/)로 이동한 다음 Intune 자격 증명을 사용하여 로그인합니다.

2. **Azure 대시보드**의 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune**을 선택합니다. **Intune 대시보드**가 열립니다.

4. **Intune 대시보드**에서 **클라이언트 앱**을 선택한 다음, **관리** 섹션에서 **앱 보호 정책**을 선택합니다.

5. **정책 만들기**를 선택하고, **이름**, **설명**을 입력한 다음, **플랫폼**을 선택합니다. 

6. **조건부 시작** 창의 **디바이스 조건** 테이블에서 **허용된 최대 디바이스 위협 수준** 아래 드롭다운 목록에서 모바일 위협 수준을 선택합니다.

    a.  **보안**: 이 수준이 가장 안전합니다. 디바이스가 어떠한 위협에도 노출되지 않았으며 회사 리소스에 계속 액세스할 수 있습니다. 어떠한 위협이든 확인되는 디바이스는 비규격으로 평가됩니다.

    b.  **낮음**: 낮은 수준의 위협만 있는 디바이스는 규격 디바이스입니다. 더 높은 수준의 위협이 발생하면 디바이스는 규정 비준수 상태가 됩니다.

    c.  **보통**: 낮음 또는 보통 수준의 위협이 있는 디바이스는 규격 디바이스입니다. 높은 수준의 위협이 검색되는 경우 해당 디바이스는 비규격으로 간주됩니다.

    d.  **높음**: 보안이 가장 취약한 수준입니다. 이 수준은 모든 위협 수준을 허용하며 보고용으로만 Mobile Threat Defense를 사용합니다. 디바이스에 MTD 앱이 이 설정으로 활성화되어 있어야 합니다.

7. **저장**을 두 번 클릭하고 **만들기**를 선택합니다.

## <a name="to-assign-an-mtd-app-protection-policy"></a>MTD 앱 보호 정책을 할당하려면

사용자에게 디바이스 준수 정책을 할당하려면 이전에 구성한 정책을 선택합니다. 기존 정책은 **디바이스 준수 – 정책** 창에서 확인할 수 있습니다.

1. 사용자에게 할당할 정책을 선택한 다음 **할당**을 선택합니다. 이 작업은 **Azure Active Directory 보안 그룹**을 선택하고 이를 정책에 할당할 수 있는 창을 엽니다.

2. **포함할 그룹 선택**을 선택하여 Azure AD 보안 그룹을 표시하는 창을 엽니다. **선택**을 선택하면 정책이 사용자에게 배포됩니다.

> [!NOTE] 
> 사용자에게 정책을 적용했습니다. 정책의 대상이 되는 사용자가 사용하는 디바이스는 Intune 앱 보호를 통해 대상 앱의 회사 데이터에 액세스할 수 있는지 평가됩니다.

## <a name="next-steps"></a>다음 단계  

- Microsoft Intune의 [Mobile Threat Defense](~/protect/mobile-threat-defense.md)에 대해 자세히 알아봅니다.
