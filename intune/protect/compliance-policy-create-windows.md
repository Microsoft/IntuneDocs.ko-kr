---
title: Microsoft Intune의 Windows 10 규정 준수 설정 - Azure | Microsoft Docs
description: Microsoft Intune에서 Windows 10, Windows Holographic 및 Surface Hub 디바이스에 대한 규정 준수를 설정할 때 사용할 수 있는 모든 설정 목록을 참조하세요. 최소 및 최대 운영 체제에 대한 규정 준수 여부, 암호 제한 및 길이 설정, 파트너 AV(바이러스 백신) 솔루션 검사, 데이터 스토리지에 대한 암호화 설정 등을 확인합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 12/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ca5d475f92cbe3298689273dcdf0da1644078b2
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547034"
---
# <a name="windows-10-and-later-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Intune을 사용하여 디바이스를 규격 또는 비규격으로 표시하는 Windows 10 이상 설정

이 문서에서는 Intune의 Windows 10 이상 디바이스에서 구성할 수 있는 다양한 규정 준수 설정을 나열하고 설명합니다. MDM(모바일 디바이스 관리) 솔루션의 일부로, 이러한 설정을 사용하여 BitLocker를 요구하고, 최소 및 최대 운영 체제를 설정하고, Microsoft Defender ATP(Advanced Threat Protection)를 사용하여 위험 수준을 설정하는 등의 작업을 수행합니다.

이 기능은 다음에 적용됩니다.

- Windows 10 이상
- Windows Holographic for Business
- Surface Hub

Intune 관리자는 이러한 규정 준수 설정을 통해 조직 리소스를 보호할 수 있습니다. 규정 준수 정책 및 정책 수행에 대한 자세한 내용은 [디바이스 규정 준수 시작](device-compliance-get-started.md)을 참조하세요.

## <a name="before-you-begin"></a>시작하기 전에

[규정 준수 정책 만들기](create-compliance-policy.md#create-the-policy) **플랫폼**에 대해 **Windows 10 이상**을 선택합니다.

## <a name="device-health"></a>디바이스 상태

### <a name="windows-health-attestation-service-evaluation-rules"></a>Windows 상태 증명 서비스 평가 규칙

- **BitLocker 필요**:  
   Windows BitLocker 드라이브 암호화는 Windows 운영 체제 볼륨에 저장된 모든 데이터를 암호화합니다. BitLocker는 TPM (신뢰할 수 있는 플랫폼 모듈)을 사용 하 여 Windows 운영 체제 및 사용자 데이터를 보호 합니다. 따라서 컴퓨터를 방치하거나 분실하거나 도난당하더라도 변조를 방지할 수 있습니다. 컴퓨터에 호환 가능한 TPM이 장착된 경우 BitLocker는 TPM을 사용하여 데이터를 보호하는 암호화 키를 잠급니다. 따라서 TPM에서 컴퓨터의 상태를 확인할 때까지 키에 액세스할 수 없습니다.  

   - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
   - **필요** - 디바이스가 꺼져 있거나 최대 절전 모드일 때 드라이브에 저장된 데이터를 무단 액세스로부터 보호할 수 있습니다.  


- **디바이스에서 보안 부팅을 사용하도록 설정해야 합니다**.  
    - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
    - **필요** -시스템이 공장에서 신뢰할 수 있는 상태로 강제로 부팅 됩니다. 머신을 부팅하는 데 사용되는 핵심 구성 요소에는 디바이스를 제조한 조직에서 신뢰할 수 있는 올바른 암호화 서명이 있어야 합니다. UEFI 펌웨어에서 컴퓨터가 시작되도록 허용하기 전에 서명을 확인합니다. 해당 서명을 손상시키는 파일이 손상된 경우 시스템이 부팅되지 않습니다.

  > [!NOTE]
  > **디바이스에서 보안 부팅을 활성화해야 하는** 설정은 일부 TPM 1.2 및 2.0 디바이스에서 지원됩니다. TPM 2.0 이상을 지원하지 않는 디바이스의 경우 Intune의 정책 상태가 **호환되지 않음**으로 표시됩니다. 지원되는 버전에 대한 자세한 내용은 [디바이스 상태 증명](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-overview#device-health-attestation)을 참조하세요.

- **코드 무결성 필요**:  
  코드 무결성은 메모리에 로드될 때마다 드라이버 또는 시스템 파일의 무결성을 확인하는 기능입니다.
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  -  **필요** - 서명되지 않은 드라이버 또는 시스템 파일이 커널로 로드되고 있는지 여부를 검색하는 코드 무결성이 필요합니다. 또한 시스템 파일이 악성 소프트웨어에 의해 변경되었는지 아니면 관리자 권한을 가진 사용자 계정으로 실행되었는지 여부를 검색합니다.

추가 리소스:

- 상태 증명 서비스의 작동 방식에 대 한 자세한 내용은 [상태 증명 CSP](https://docs.microsoft.com/windows/client-management/mdm/healthattestation-csp)를 참조 하세요.
- [지원 팁: Intune 규정 준수 정책의 일부로 디바이스 상태 증명 설정 사용](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Using-Device-Health-Attestation-Settings-as-Part-of/ba-p/282643)

## <a name="device-properties"></a>디바이스 속성

### <a name="operating-system-version"></a>운영 체제 버전

- **최소 OS 버전**:  
  허용되는 최소 버전을 **주 버전.부 버전.빌드.CU 번호** 형식으로 입력합니다. 올바른 값을 얻으려면 명령 프롬프트를 열고 `ver`을 입력합니다. `ver` 명령은 버전을 다음 형식으로 반환합니다.

  `Microsoft Windows [Version 10.0.17134.1]`

  입력하는 OS 버전보다 이전 버전이 디바이스에 있으면 호환되지 않는 것으로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 디바이스를 업그레이드하도록 선택할 수 있습니다. 업그레이드 후 회사 리소스에 액세스할 수 있습니다.

- **최대 OS 버전**:  
  허용되는 최대 버전을 **주 버전.부 버전.빌드.수정 번호** 형식으로 입력합니다. 올바른 값을 얻으려면 명령 프롬프트를 열고 `ver`을 입력합니다. `ver` 명령은 버전을 다음 형식으로 반환합니다.

  `Microsoft Windows [Version 10.0.17134.1]`

  디바이스가 입력된 버전보다 최신 OS 버전을 사용하는 경우 조직 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 최종 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 디바이스는 조직 리소스에 액세스할 수 없습니다.

- **모바일 디바이스에 필요한 최소 OS**:  
  허용되는 최소 버전을 주 버전.부 버전.빌드 번호 형식으로 입력합니다.

  입력하는 OS 버전보다 이전 버전이 디바이스에 있으면 호환되지 않는 것으로 보고됩니다. 업그레이드 방법에 대한 정보를 제공하는 링크가 표시됩니다. 최종 사용자는 디바이스를 업그레이드하도록 선택할 수 있습니다. 업그레이드 후 회사 리소스에 액세스할 수 있습니다.

- **모바일 디바이스에 필요한 최대 OS**:  
  허용되는 최대 버전을 주 버전.부 버전.빌드 번호로 입력합니다.

  디바이스가 입력된 버전보다 최신 OS 버전을 사용하는 경우 조직 리소스에 대한 액세스가 차단됩니다. IT 관리자에게 문의하라는 메시지가 최종 사용자에게 표시됩니다. OS 버전을 허용하도록 규칙이 변경될 때까지 디바이스는 조직 리소스에 액세스할 수 없습니다.

- **유효한 운영 체제 빌드**:  
  최소 버전과 최대 버전을 포함하여 허용되는 운영 체제 버전의 범위를 입력합니다. 이러한 허용되는 OS 빌드 번호의 CSV(쉼표로 구분된 값) 파일 목록을 **내보낼** 수도 있습니다.

## <a name="configuration-manager-compliance"></a>Configuration Manager 준수

Windows 10 이상을 실행하는 공동 관리 디바이스에만 적용됩니다. Intune 전용 디바이스는 사용할 수 없음 상태를 반환합니다.

- **Configuration Manager에서 장치 준수 필요**:  
  - **구성되지 않음**(*기본값*) - Intune은 규정 준수에 대한 Configuration Manager 설정을 확인하지 않습니다.
  - **필요** - Configuration Manager의 모든 설정(구성 항목)을 준수해야 합니다.  

    예를 들어 모든 소프트웨어 업데이트를 디바이스에 설치해야 합니다. Configuration Manager에서 이 요구 사항의 상태는 “설치됨”입니다. 디바이스의 프로그램이 알 수 없는 상태에 있는 경우 디바이스는 Intune에서 비준수가 됩니다.

## <a name="system-security"></a>시스템 보안

### <a name="password"></a>암호

- **모바일 디바이스의 잠금을 해제하는 데 암호 필요**:  
  - **구성되지 않음**(*기본값*) - 이 설정은 규정 준수 또는 비준수에 대해 평가되지 않습니다.
  - **필요** - 사용자는 암호를 입력해야 자신의 디바이스에 액세스할 수 있습니다. 

- **단순 암호**:  
  - **구성 되지 않음** (*기본값*)-사용자가 **1234** 또는 **1111**와 같은 단순한 암호를 만들 수 있습니다.
  - **차단** - 사용자가 **1234** 또는 **1111** 같은 단순한 암호를 만들 수 없습니다.

- **암호 형식**:  
  필요한 암호 또는 PIN의 유형을 선택합니다. 옵션은 다음과 같습니다.
  - **장치 기본값** (*기본값*)-암호, 숫자 pin 또는 영숫자 pin 필요
  - **숫자** -암호 또는 숫자 PIN 필요
  - **영숫자** -암호 또는 영숫자 PIN을 요구 합니다.  
  
  *영숫자*로 설정 된 경우 다음 설정을 사용할 수 있습니다.  
  - **암호 복잡도**:  
    옵션은 다음과 같습니다. 
    - **숫자 및 소문자 필요** (*기본값*)
    - **숫자, 소문자 및 대문자 필요**
    - **숫자, 소문자, 대문자 및 특수 문자 필요**

    > [!TIP]
    > 영숫자 암호 정책은 복잡할 수 있습니다. 관리자가 Csp를 읽고 자세한 내용을 확인 하는 것이 좋습니다.
    >
    > - [DeviceLock/AlphanumericDevicePasswordRequired CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-alphanumericdevicepasswordrequired)
    > - [DeviceLock/MinDevicePasswordComplexCharacters CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-devicelock#devicelock-mindevicepasswordcomplexcharacters)

- **최소 암호 길이**:  
  암호에 포함해야 하는 최소 자릿수 또는 문자 수를 입력합니다.

- **암호를 요구하기 전까지 최대 비활성 시간(분)** :  
  사용자가 해당 시간 내에 자신의 암호를 다시 입력해야 하는 유휴 시간을 입력합니다.

- **암호 만료(일)** :  
  암호가 만료되기 전에 새로 만들어야 하는 일수(1~730)를 입력합니다.

- **재사용을 방지하기 위한 이전 암호 수**:  
  사용할 수 없는, 이전에 사용된 암호 수를 입력합니다.

- **디바이스가 유휴 상태에서 되돌아오는 경우 암호 필요(모바일 및 홀로그램)** :  
  - **구성되지 않음**(*기본값*)
  - **필요** - 디바이스가 유휴 상태에서 되돌아올 때마다 디바이스 사용자가 암호를 입력해야 합니다.

  > [!IMPORTANT]
  > Windows 데스크톱에서 암호 요구 사항이 변경되면 사용자가 다음에 로그인할 때 영향을 받습니다. 디바이스가 유휴 상태에서 활성 상태로 변하기 때문입니다. 요구 사항을 충족하는 암호를 사용하는 사용자에게도 암호를 변경하라는 메시지가 표시됩니다.

### <a name="encryption"></a>암호화

- **디바이스에 있는 데이터 스토리지의 암호화**:  
  이 설정은 장치의 모든 드라이브에 적용 됩니다.
  - **구성되지 않음**(*기본값*)
  - **필요** - 디바이스의 데이터 스토리지를 암호화하려면 *필요*를 사용합니다.

  > [!NOTE]
  > **디바이스에서 데이터 스토리지 암호화** 설정은 일반적으로 디바이스가 암호화되었는지 확인합니다. 보다 강력한 암호화 설정을 위해 **BitLocker 필요**를 사용하는 것이 좋습니다. 그러면 Windows 디바이스 상태 증명을 활용하여 TPM 수준에서 Bitlocker 상태의 유효성을 검사합니다.

### <a name="device-security"></a>디바이스 보안  

- **방화벽**:  
  - **구성 되지 않음** (*기본값*)-Intune은 Microsoft Defender 방화벽을 제어 하거나 기존 설정을 변경 하지 않습니다.
  - Microsoft Defender 방화벽을 **사용 하도록 설정** 하 고 사용자가 끄지 못하도록 합니다.  

  [방화벽 CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)

  > [!NOTE]
  > 다시 부팅 한 후 장치를 즉시 동기화 하거나 즉시 절전 모드에서 절전 모드를 해제 하는 경우이 설정이 **오류로**보고 될 수 있습니다. 이 시나리오는 전체 장치 준수 상태에 영향을 주지 않을 수 있습니다. 준수 상태를 다시 평가 하려면 장치를 수동으로 [동기화](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows)합니다.

- **TPM(신뢰할 수 있는 플랫폼 모듈)** :  
  - **구성 되지 않음** (*기본값*)-INTUNE이 장치에서 TPM 칩 버전을 확인 하지 않습니다.
  - **필수** -INTUNE에서 TPM 칩 버전이 준수 하는지 확인 합니다. TPM 칩 버전이 **0** 보다 큰 경우 장치는 규정을 준수 합니다. 장치에 TPM 버전이 없는 경우 장치는 정책을 준수 하지 않습니다.  

  [DeviceStatus CSP-DeviceStatus/TPM/사양 버전 노드](https://docs.microsoft.com/windows/client-management/mdm/devicestatus-csp)
  
- **바이러스 백신**:  
  - **구성되지 않음**(*기본값*) - Intune은 디바이스에 설치된 바이러스 백신 솔루션을 확인하지 않습니다. 
  - **필요** - Symantec 및 Microsoft Defender와 같은 [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)에 등록된 바이러스 백신 솔루션을 사용하여 규정 준수를 확인합니다.

- **스파이웨어 방지**:  
  - **구성되지 않음**(*기본값*) - Intune은 디바이스에 설치된 스파이웨어 방지 솔루션을 확인하지 않습니다.
  - **필요** - Symantec 및 Microsoft Defender와 같은 [Windows Security Center](https://blogs.windows.com/windowsexperience/2017/01/23/introducing-windows-defender-security-center/)에 등록된 스파이웨어 방지 솔루션을 사용하여 규정 준수를 확인합니다.  

### <a name="defender"></a>Defender

*Windows 10 Desktop에서 지원 되는 호환성 설정은 다음과 같습니다.*

- **Microsoft Defender 맬웨어 방지 프로그램**:  
  - **구성 되지 않음** (*기본값*)-Intune은 서비스를 제어 하거나 기존 설정을 변경 하지 않습니다.
  - Microsoft Defender 맬웨어 방지 서비스를 **사용 하도록 설정** 하 고 사용자가 끄지 못하도록 합니다.

- **Microsoft Defender 맬웨어 방지 최소 버전**:  
  Microsoft Defender 맬웨어 방지 서비스의 최소 허용 버전을 입력 합니다. 예를 들어 다음과 같이 입력합니다. `4.11.0.0` 비워 두면 모든 버전의 Microsoft Defender 맬웨어 방지 서비스를 사용할 수 있습니다.  

  *기본적으로 버전은 구성 되어 있지*않습니다.

- **Microsoft Defender 맬웨어 방지 보안 인텔리전스 최신 상태**:  
  장치에서 Windows 보안 바이러스 및 위협 방지 업데이트를 제어 합니다.
  - **구성 되지 않음** (*기본값*)-Intune에서 요구 사항을 적용 하지 않습니다.
  - -Force를 **요구** 하면 Microsoft Defender 보안 인텔리전스를 최신 상태로 유지 합니다.

  [Defender/Health/SignatureOutOfDate CSP](https://docs.microsoft.com/windows/client-management/mdm/defender-csp)
  
  자세한 내용은 [Microsoft Defender 바이러스 백신 및 기타 microsoft 맬웨어 방지 프로그램에 대 한 보안 인텔리전스 업데이트](https://www.microsoft.com/en-us/wdsi/defenderupdates)를 참조 하세요.

- **실시간 보호**:  
  - **구성 되지 않음** (*기본값*)-Intune은이 기능을 제어 하거나 기존 설정을 변경 하지 않습니다.
  - **요구** -맬웨어, 스파이웨어 및 기타 사용자 동의 없이 설치 된 소프트웨어를 검색 하는 실시간 보호를 설정 합니다.  

  [Defender/AllowRealtimeMonitoring CSP](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring)

## <a name="microsoft-defender-atp"></a>Microsoft Defender ATP

### <a name="microsoft-defender-advanced-threat-protection-rules"></a>Microsoft Defender Advanced Threat Protection 규칙

- **디바이스를 머신 위험 점수 이하로 유지**:  
  이 설정을 사용하여 위협 방지 서비스에서 준수 조건에 따라 위험 평가를 수행합니다. 허용된 최대 위협 수준을 선택합니다.
  - **구성되지 않음**(*기본값*)  
  - **지우기** - 디바이스에 어떤 위협도 없으므로 이 옵션이 가장 안전합니다. 수준에 관계없이 위협이 발견된 디바이스는 비규격으로 평가됩니다.
  - **낮음** - 낮은 수준의 위협만 있는 경우 디바이스가 규격으로 평가됩니다. 더 높은 수준의 위협이 확인되는 디바이스는 비규격 상태로 설정됩니다.
  - **보통** - 디바이스의 기존 위협이 낮음 또는 보통 수준인 경우 디바이스가 규격으로 평가됩니다. 디바이스에 높은 수준의 위협이 있는 것으로 검색되면 비규격으로 결정됩니다.
  - **높음** - 이 옵션은 최소 보안이며 모든 위협 수준을 허용합니다. 이 수준은 이 솔루션을 보고 용도로만 사용하는 경우에 유용할 수 있습니다.
  
  방어 위협 서비스로 Microsoft Defender ATP(Advanced Threat Protection)를 설정하려면[조건부 액세스로 Microsoft Defender ATP 사용](advanced-threat-protection.md)을 참조하세요.


## <a name="windows-holographic-for-business"></a>Windows Holographic for Business

Windows Holographic for Business는 **Windows 10 이상** 플랫폼을 사용합니다. Windows Holographic for Business는 다음과 같은 설정을 지원합니다.

- **시스템 보안** > **암호화** > **디바이스의 데이터 스토리지 암호화**.

Microsoft HoloLens에서 디바이스 암호화를 확인하려면 [디바이스 암호화 확인](https://docs.microsoft.com/hololens/hololens-encryption#verify-device-encryption)을 참조하세요.

## <a name="surface-hub"></a>Surface Hub

Surface Hub는 **Windows 10 이상** 플랫폼을 사용합니다. Surface Hub는 준수 및 조건부 액세스 둘 다에서 지원됩니다. Surface Hub에서 이러한 기능을 사용하려면 Intune에서 [Windows 10 자동 등록을 사용하도록 설정](../enrollment/windows-enroll.md)하고(Azure AD(Azure Active Directory) 필요), 디바이스 그룹으로 Surface Hub 디바이스를 대상으로 지정하는 것이 좋습니다. 규정 준수 및 조건부 액세스가 작동하려면 Surface Hub가 Azure AD에 연결되어야 합니다.

지침은 [Windows 디바이스에 대한 등록 설정](../enrollment/windows-enroll.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

- [비규격 디바이스에 대한 작업 추가](actions-for-noncompliance.md) 및 [범위 태그를 사용하여 정책 필터링](../fundamentals/scope-tags.md).
- [규정 준수 정책 모니터링](compliance-policy-monitor.md).
- [Windows 8.1용 규정 준수 정책 설정](compliance-policy-create-windows-8-1.md) 디바이스를 참조하세요.
