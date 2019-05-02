---
title: Microsoft Intune의 Windows 10 교육 설정 - Azure | Microsoft Docs
description: Microsoft Intune에서 Windows 8.1 및 Windows Phone 8.1 장치에 대 한 준수를 설정 하는 경우 사용할 수는 모든 설정의 목록을 참조 하세요. 데이터 저장소에서 암호화를 사용 하는 최소 및 최대 운영 체제에서 암호 제한 설정 및 길이 규정 준수에 대 한 확인 합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ed863378616f8001beab89177c642404287e7d3
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59424956"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>규격 또는 비규격 Intune을 사용 하 여 장치 됨으로 표시 하려면 Windows 8.1 설정

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

이 문서에서는 나열 하 고 Intune에서 Windows 8.1 장치에서 구성할 수 있습니다 다른 규정 준수 설정에 설명 합니다. 모바일 장치 관리 (MDM) 솔루션의 일부로,이 설정을 사용 하 여 이러한 단순 암호 차단, 최소 및 최대 OS 버전을 설정 합니다.

이 기능은 다음에 적용됩니다.

- Windows Phone 8.1
- Windows 8.1 이상

Intune 관리자로 서 이러한 규정 준수 설정을 통해 조직 리소스를 보호 하기 위해 사용 합니다. 준수 정책 및 모든 필수 조건에 대한 자세한 내용은 [디바이스 준수 시작](device-compliance-get-started.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[규정 준수 정책 만들기](create-compliance-policy.md#create-the-policy) 에 대 한 **플랫폼**를 선택 **Windows Phone 8.1** 하거나 **Windows 8.1 이상**합니다.

## <a name="device-properties"></a>디바이스 속성

- **필요한 최소 OS**: 최소 허용 버전을 입력 합니다. 디바이스가 OS 최소 버전 요구 사항을 충족하지 못하면 비규격 디바이스로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 해당 디바이스를 업그레이드한 후 회사 리소스에 액세스할 수 있습니다.
- **허용 된 최대 OS 버전**: 최대 허용 버전을 입력 합니다. 디바이스가 규칙에 입력된 버전보다 최신 OS 버전을 사용하는 경우 회사 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 사용자에게 표시됩니다. 디바이스는 OS 버전을 허용하는 규칙을 변경하기 전까지 조직의 리소스에 액세스할 수 없습니다.

Windows 8.1 PC는 **3** 버전을 반환합니다. Windows에 대한 OS 버전 규칙이 Windows 8.1로 설정된 경우 디바이스에 Windows 8.1이 있어도 디바이스가 호환되지 않는 것으로 보고됩니다.

## <a name="system-security"></a>시스템 보안

### <a name="password"></a>암호

- **모바일 디바이스의 잠금을 해제하는 데 암호 필요**: **필요**로 설정하면 사용자가 암호를 입력해야 디바이스에 액세스할 수 있습니다.
- **단순 암호**: **차단**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 단순 암호를 만들 수 없습니다. **구성되지 않음**으로 설정하면 사용자가 **1234** 또는 **1111** 같은 암호를 만들 수 있습니다.
- **최소 암호 길이**: 암호에 포함해야 하는 최소 자릿수 또는 문자 수를 입력합니다.

  Windows를 실행하고 Microsoft 계정으로 액세스하는 디바이스에서는 다음과 같은 경우 준수 정책이 올바르게 평가하지 못합니다.
  - 최소 암호 길이가 8자를 초과하는 경우
  - 또는 최소 문자 집합 수가 3개 이상인 경우

- **암호 유형**: 암호에 **숫자**만 사용해야 하는지 또는 숫자와 기타 문자(**영숫자**)를 함께 사용해야 하는지 선택합니다.
  
  - **암호에 포함해야 하는 영숫자가 아닌 문자 수**: **필수 암호 유형**이 **영숫자**로 설정된 경우 이 설정은 암호에 포함해야 하는 최소 문자 집합 수를 지정합니다. 4가지 문자 집합은 다음과 같습니다.
    - 소문자
    - 대문자
    - 기호
    - 숫자

    더 큰 값을 설정하면 사용자는 더욱 복잡한 암호를 만들어야 합니다. Microsoft 계정으로 액세스하는 디바이스에서는 다음과 같은 경우 준수 정책이 올바르게 평가되지 않습니다.

    - 최소 암호 길이가 8자를 초과하는 경우
    - 또는 최소 문자 집합 수가 3개 이상인 경우

- **암호를 요구하기 전까지 최대 비활성 시간(분)**: 사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.
- **암호 만료(일)**: 암호가 만료되기 전에 새로 만들어야 하는 일수를 선택합니다.
- **재사용을 방지하기 위한 이전 암호 수**: 사용할 수 없는 이전에 사용된 암호 수를 입력합니다.

### <a name="encryption"></a>암호화

- **모바일 장치 암호화 필요**: **필요**로 설정하면 장치가 데이터 스토리지 리소스에 연결하기 위해 암호화되어야 합니다.

**확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

## <a name="next-steps"></a>다음 단계

- [비규격 장치에 대 한 작업 추가](actions-for-noncompliance.md) 하 고 [필터 정책에 대 한 범위 태그를 사용 하 여](scope-tags.md)입니다.
- [규정 준수 정책을 모니터링](compliance-policy-monitor.md)합니다.
- 참조 된 [준수 정책 설정은 Windows 10 이상용](compliance-policy-create-windows.md) 장치입니다.