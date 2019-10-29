---
title: Microsoft Intune의 Windows 8.1 규정 준수 설정 - Azure | Microsoft Docs
description: Microsoft Intune에서 Windows 8.1 및 Windows Phone 8.1 디바이스에 대한 규정 준수를 설정할 때 사용할 수 있는 모든 설정 목록을 참조하세요. 최소 및 최대 운영 체제에 대한 규정 준수 여부, 암호 제한 및 길이 설정, 데이터 스토리지에 대한 암호화 설정 등을 확인합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3e074d922078a9772ca67a6ebd99948bc3e64601
ms.sourcegitcommit: 25acfc88b366d2da71c37d354a0238e4f1168325
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72813220"
---
# <a name="windows-81-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Intune을 사용하여 디바이스를 규격 또는 비규격으로 표시하는 Windows 8.1 설정

이 문서에서는 Intune의 Windows 8.1 디바이스에서 구성할 수 있는 다양한 규정 준수 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이 설정을 사용하여 간단한 암호를 차단하고 최소 및 최대 OS 버전을 설정하는 등의 작업을 수행합니다.

이 기능은 다음에 적용됩니다.

- Windows Phone 8.1
- Windows 8.1 이상

Intune 관리자는 이러한 규정 준수 설정을 통해 조직 리소스를 보호할 수 있습니다. 규정 준수 정책 및 정책 수행에 대한 자세한 내용은 [디바이스 규정 준수 시작](device-compliance-get-started.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[규정 준수 정책 만들기](create-compliance-policy.md#create-the-policy) **플랫폼**의 경우 **Windows Phone 8.1** 또는 **Windows 8.1 이상**을 선택합니다.

## <a name="device-properties"></a>디바이스 속성

### <a name="operating-system-version"></a>운영 체제 버전

**Windows Phone 8.1 이상**
- **모바일 장치에 대 한 최소 OS 버전**:  
  허용 되는 최소 버전을 입력 합니다. 디바이스가 OS 최소 버전 요구 사항을 충족하지 못하면 비규격 디바이스로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 디바이스 사용자는 해당 디바이스를 업그레이드한 후 회사 리소스에 액세스할 수 있습니다.

- **모바일 장치에 대 한 최대 OS 버전**:  
  허용 되는 최대 버전을 입력 합니다. 디바이스가 규칙에 입력된 버전보다 최신 OS 버전을 사용하는 경우 조직 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 디바이스 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 디바이스는 조직 리소스에 액세스할 수 없습니다.

**Windows 8.1 이상**
- **최소 OS 버전**:  
  허용 되는 최소 버전을 입력 합니다. 디바이스가 OS 최소 버전 요구 사항을 충족하지 못하면 비규격 디바이스로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 디바이스 사용자는 해당 디바이스를 업그레이드한 후 회사 리소스에 액세스할 수 있습니다.

- **최대 OS 버전**:  
  허용 되는 최대 버전을 입력 합니다. 디바이스가 규칙에 입력된 버전보다 최신 OS 버전을 사용하는 경우 조직 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 디바이스 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 디바이스는 조직 리소스에 액세스할 수 없습니다.

Windows 8.1 PC는 **3** 버전을 반환합니다. OS 버전 규칙이 Windows용 Windows 8.1로 설정된 경우 디바이스에 Windows 8.1이 있어도 디바이스가 비규격으로 보고됩니다.

## <a name="system-security"></a>시스템 보안

### <a name="password"></a>암호

- **모바일 디바이스의 잠금을 해제하는 데 암호 필요**:  
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **필요** - 사용자는 암호를 입력해야 자신의 디바이스에 액세스할 수 있습니다.

- **단순 암호**:  
  - **구성 되지 않음** (*기본값*)-사용자가 **1234** 또는 **1111**와 같은 단순한 암호를 만들 수 있습니다.
  - **차단** - 사용자가 **1234** 또는 **1111** 같은 단순한 암호를 만들 수 없습니다.  

- **최소 암호 길이**:  
  암호에 포함해야 하는 최소 자릿수 또는 문자 수를 입력합니다.

  Windows를 실행 하 고 Microsoft 계정를 사용 하 여 액세스 하는 장치의 경우 다음 조건 중 하나를 충족 하는 경우 준수 정책이 올바르게 평가 되지 않습니다.  
  - 최소 암호 길이가 8자를 초과함
  - 최소 문자 집합 수가 3개 이상임

- **암호 형식**:  
  암호에 **숫자**만 사용해야 하는지 또는 숫자와 기타 문자(**영숫자**)를 함께 사용해야 하는지 선택합니다.

  *영숫자*로 설정 된 경우 다음 설정을 사용할 수 있습니다.  

  - **암호에 포함해야 하는 영숫자가 아닌 문자 수**:  
    *암호 형식이* **영숫자**로 설정 된 경우 암호에 포함 해야 하는 최소 문자 집합 수를 지정 합니다. 옵션에는 **0** ~ **4** 개의 집합이 포함 되며 기본값은 **1**입니다.
    
    4가지 문자 집합은 다음과 같습니다.
    - 소문자
    - 대문자
    - 기호
    - 숫자

    더 큰 값을 설정하면 사용자는 더욱 복잡한 암호를 만들어야 합니다. Microsoft 계정를 사용 하 여 액세스 하는 장치의 경우 다음 조건 중 하나를 충족 하는 경우 준수 정책이 올바르게 평가 되지 않습니다.

    - 최소 암호 길이가 8자를 초과함
    - 최소 문자 집합 수가 3개 이상임

- **암호를 요구하기 전까지 최대 비활성 시간(분)** :  
  사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.

- **암호 만료(일)** :  
  암호가 만료되기 전에 사용자가 새로 만들어야 하는 일수를 선택합니다.

- **재사용을 방지하기 위한 이전 암호 수**:  
  사용할 수 없는, 이전에 사용된 암호 수를 입력합니다.

### <a name="encryption"></a>암호화

- **디바이스에 있는 데이터 스토리지의 암호화**:  
  - **구성되지 않음**(*기본값*)
  - **필요** - 디바이스의 데이터 스토리지를 암호화하려면 *필요*를 사용합니다.


<!-- not on phone   
- **Require encryption on mobile device**: **Require** the device to be encrypted to connect to data storage resources.
--> 

## <a name="next-steps"></a>다음 단계

- [비규격 디바이스에 대한 작업 추가](actions-for-noncompliance.md) 및 [범위 태그를 사용하여 정책 필터링](../fundamentals/scope-tags.md).
- [규정 준수 정책 모니터링](compliance-policy-monitor.md).
- [Windows 10 이상용 규정 준수 정책 설정](compliance-policy-create-windows.md) 디바이스를 참조하세요.