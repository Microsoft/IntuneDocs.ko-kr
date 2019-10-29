---
title: Microsoft Intune에서 Android 디바이스 규정 준수 설정 - Azure | Microsoft Docs
description: Microsoft Intune에서 Android 디바이스의 규정 준수를 설정할 때 사용할 수 있는 모든 설정 목록을 참조하세요. 암호 규칙 설정, 최소 또는 최대 운영 체제 버전 선택, 특정 앱 제한, 암호 재사용 방지 등.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/21/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: efff117ca79e4fa9a00fd8d9a4be792e246f1a86
ms.sourcegitcommit: 3ace4cba6e2f6fefa9120be3807387a49b200c9b
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810168"
---
# <a name="android-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Intune을 사용하여 디바이스를 규격 또는 비규격으로 표시하는 Android 설정

이 문서에서는 Intune의 Android 디바이스에서 구성할 수 있는 다양한 규정 준수 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 루팅된(무단 해제) 디바이스를 비규격으로 표시하고, 허용되는 위협 수준을 설정하고, Google Play Protect를 사용하도록 설정하는 등의 작업을 수행합니다.

이 기능은 다음에 적용됩니다.

- Android 디바이스 관리자

Intune 관리자는 이러한 규정 준수 설정을 통해 조직 리소스를 보호할 수 있습니다. 규정 준수 정책 및 정책 수행에 대한 자세한 내용은 [디바이스 규정 준수 시작](device-compliance-get-started.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[규정 준수 정책 만들기](create-compliance-policy.md#create-the-policy) **플랫폼**에서 **Android 장치 관리자**를 선택 합니다.

## <a name="device-health"></a>디바이스 상태

- **루팅된 디바이스**: 
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **차단** - 루팅된(무단 해제된) 디바이스를 비규격으로 표시합니다. 

- **디바이스를 디바이스 위협 수준 이하로 유지**:  
  연결 된 모바일 위협 방어 서비스에서 위험 평가를 규정 준수에 대 한 조건으로 사용 하려면이 설정을 사용 합니다. 
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다. 
  - **보안** - 이 옵션은 디바이스가 어떠한 위협에도 노출되지 않았으므로 가장 안전합니다. 위협 수준이 있는 디바이스가 검색되면 규정 비준수로 평가됩니다.
  - **낮음** - 낮은 수준의 위협만 있는 경우 디바이스가 규격으로 평가됩니다. 더 높은 수준의 위협이 발생하면 디바이스는 규정 비준수 상태가 됩니다.
  - **보통** - 디바이스의 기존 위협이 낮음 또는 보통 수준인 경우 디바이스가 규격으로 평가됩니다. 디바이스에 높은 수준의 위협이 있는 것으로 검색되면 규정 비준수로 결정됩니다.
  - **높음** - 이 옵션은 최소 보안이며 모든 위협 수준을 허용합니다. 이 수준은 이 솔루션을 보고 용도로만 사용하는 경우에 유용할 수 있습니다.

### <a name="google-play-protect"></a>Google Play 보호

- **Google Play 서비스가 구성됨**:  
  Google Play 서비스는 보안 업데이트를 허용하며, 인증된 Google 디바이스의 많은 보안 기능에 대한 기본 수준 종속성입니다.
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.  
  - **필요** - Google Play 서비스 앱이 설치되어 사용할 수 있어야 합니다.  

- **최신 보안 공급자**: 
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.  
  - **필요** - 최신 보안 공급자가 알려진 취약성으로부터 디바이스를 보호할 수 있도록 합니다. 

- **앱에서 위협 검색**:  
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.  
  - **필요** - Android **앱 확인** 기능을 사용하도록 설정해야 합니다.  
  > [!NOTE]
  > 레거시 Android 플랫폼에서 이 기능은 준수 설정입니다. Intune에서는 디바이스 수준에서 이 설정이 사용하도록 설정되어 있는지만 확인할 수 있습니다.

- **SafetyNet 디바이스 증명**:  
  충족해야 하는 [SafetyNet 증명](https://developer.android.com/training/safetynet/attestation.html) 수준을 입력합니다. 옵션은 다음과 같습니다.
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **기본 무결성 확인**
  - **기본 무결성 및 인증된 디바이스 확인**

> [!NOTE]
> 앱 보호 정책을 사용하여 Google Play Protect 설정을 구성하려면 Android에서 [Intune 앱 보호 정책 설정](../apps/app-protection-policy-settings-android.md#conditional-launch)을 참조하세요.

## <a name="device-properties"></a>디바이스 속성

### <a name="operating-system-version"></a>운영 체제 버전 

- **최소 OS 버전**:  
  디바이스가 OS 최소 버전 요구 사항을 충족하지 못하면 비규격 디바이스로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 해당 디바이스를 업그레이드한 후 회사 리소스에 액세스할 수 있습니다.

   *기본적으로 버전은 구성 되어 있지*않습니다.

- **최대 OS 버전**:  
  디바이스가 규칙에 지정된 버전보다 최신 OS 버전을 사용하는 경우 회사 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 이 디바이스는 회사 리소스에 액세스할 수 없습니다.

  *기본적으로 버전은 구성 되어 있지*않습니다.

## <a name="system-security"></a>시스템 보안

### <a name="password"></a>암호
<!-- - **Minimum password length**: Enter the minimum number of digits or characters that the user's password must have.   


- **Maximum minutes of inactivity before password is required**: Enter the idle time before the user must reenter their password. When you choose **Not configured** (default), this setting isn't evaluated for compliance or non-compliance.

- **Password expiration (days)**: Select the number of days before the password expires and the user must create a new password.

- **Number of previous passwords to prevent reuse**: Enter the number of recent passwords that can't be reused. Use this setting to restrict the user from creating previously used passwords.

-->

- **모바일 디바이스의 잠금을 해제하는 데 암호 필요**: 
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **필요** - 사용자는 암호를 입력해야 자신의 디바이스에 액세스할 수 있습니다.  

- **필수 암호 유형**:  
  암호에 숫자만 사용해야 하는지 또는 숫자와 기타 문자를 함께 사용해야 하는지 선택합니다. 옵션은 다음과 같습니다.
  - **장치 기본값** -암호 준수를 평가 하려면 **장치 기본값**이외의 암호 강도를 선택 해야 합니다.
  - **낮은 보안 생체 인식**
  - **최소 숫자** 
  - **복합 숫자** - `1111` 또는 `1234`와 같이 반복 또는 연속된 숫자는 허용되지 않습니다.
  - **최소 알파벳** 
  - **최소 영숫자**
  - **기호가 포함된 최소 영숫자**


### <a name="encryption"></a>암호화

- **디바이스에 있는 데이터 스토리지의 암호화**:  
  *Android 4.0 이상 또는 KNOX 4.0 이상에서 지원 됩니다.*  
  <br>
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다. 
  - 장치에서 데이터 저장소를 암호화 **해야** 합니다. **모바일 디바이스의 잠금을 해제하는 데 암호 필요** 설정을 선택하면 디바이스가 암호화됩니다.  

### <a name="device-security"></a>디바이스 보안

- **알 수 없는 출처의 앱 차단**:  
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **보안 > 알 수 없는 소스** 를 사용 하는 **블록** 장치-Android 4.x를 통해 android 4.0에서 지원 *. Android 8.0 이상에서는 지원되지 않음*).  

  앱을 테스트용으로 로드하려면 알 수 없는 소스를 허용해야 합니다. Android 앱을 테스트용으로 로드하는 경우가 아니면 이 기능을 **차단**으로 설정하여 이 준수 정책을 사용하도록 설정합니다. 

  > [!IMPORTANT]
  > 앱을 테스트용으로 로드하려면 **알 수 없는 소스의 앱 차단** 설정을 사용하도록 설정해야 합니다. 디바이스에서 Android 앱을 테스트용으로 로드하지 않는 경우에만 이 준수 정책을 적용합니다.

- **회사 포털 앱 런타임 무결성**:  
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.  
  - **필요** - *필요*를 선택하여 회사 포털 앱이 다음 요구 사항을 모두 충족하는지 확인합니다.
    - 기본 런타임 환경이 설치되어 있습니다.
    - 적절하게 서명되었습니다.
    - 디버그 모드가 아닙니다.
    - 알려진 원본에서 설치되었습니다.

- **장치에서 USB 디버깅 차단** *(Android 4.2 이상)* :  
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **차단** - 디바이스에서 USB 디버깅 기능을 사용할 수 없도록 방지합니다.  

- **최소 보안 패치 수준** *(Android 6.0 이상)* :  
  디바이스에서 사용할 수 있는 가장 오래된 보안 패치 수준을 선택합니다. 최소한 이 패치 수준이 아닌 디바이스는 비규격입니다. `YYYY-MM-DD` 형식으로 날짜를 입력해야 합니다.

  *기본적으로 날짜는 구성 되지 않습니다*.

- **제한된 앱**:  
  제한되어야 하는 앱에 대해 **앱 이름** 및 **앱 번들 ID**를 입력한 다음 **추가**를 선택합니다. 하나 이상의 제한된 앱이 설치된 디바이스는 비규격으로 표시됩니다.

## <a name="next-steps"></a>다음 단계

- [비규격 디바이스에 대한 작업 추가](actions-for-noncompliance.md) 및 [범위 태그를 사용하여 정책 필터링](../fundamentals/scope-tags.md).
- [규정 준수 정책 모니터링](compliance-policy-monitor.md).
- [Android Enterprise용 규정 준수 정책 설정](compliance-policy-create-android-for-work.md) 디바이스를 참조하세요.
