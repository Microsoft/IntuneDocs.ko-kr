---
title: Microsoft Defender Advanced Threat Protection에 대한 Intune 보안 기준 설정
titleSuffix: Microsoft Intune
description: Microsoft Defender Advanced Threat Protection 관리를 위해 Intune에서 지원하는 보안 기준 설정
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/25/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: karthib
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a2cb5d7375ae5b76a24861872d4abf786f199dfd
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72508996"
---
# <a name="microsoft-defender-advanced-threat-protection-baseline-settings-for-intune"></a>Intune에 대한 Microsoft Defender Advanced Threat Protection 기준 설정

Microsoft Intune에서 지원하는 Microsoft Defender Advanced Threat Protection(이전 Windows Defender Advanced Threat Protection) 기준 설정을 봅니다. ATP(Advanced Threat Protection) 기준 기본값은 ATP에 대한 권장 구성을 나타내며, 다른 보안 기준의 기준 기본값과 일치하지 않을 수 있습니다.  

사용자의 환경이 [Microsoft Defender Advanced Threat Protection](advanced-threat-protection.md#prerequisites) 사용에 대한 필수 조건을 충족하는 경우 Microsoft Defender Advanced Threat Protection 기준을 사용할 수 있습니다. 

이 기준은 물리적 장치에 최적화 되어 있으며, 현재 Vm (가상 머신) 또는 VDI 끝점에서 사용 하지 않는 것이 좋습니다. 특정 기준 설정은 가상화된 환경의 원격 대화형 세션에 영향을 줄 수 있습니다. 자세한 내용은 Windows 문서에서 [Increase compliance to the Microsoft Defender ATP security baseline](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-machines-security-baseline)(Microsoft Defender ATP 보안 기준의 준수 강화)을 참조하세요.


> [!NOTE]  
> ATP 기준 설정은 **미리 보기**로 제공됩니다. 미리 보기 상태에서 사용 가능한 설정 목록 및 이 콘텐츠가 해당 설정을 제공하는 순서는 포털에서 사용 가능한 항목과 일치하지 않을 수 있습니다.  
>
> 기준 설정이 미리 보기가 아닌 경우 이 콘텐츠는 Intune에서 지원하는 현재 보안 기준 설정 목록을 반영하도록 업데이트됩니다.

## <a name="application-guard"></a>Application Guard  
자세한 내용은 Windows 설명서의 [WindowsDefenderApplicationGuard CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsdefenderapplicationguard-csp)를 참조하세요.  

Microsoft Edge를 사용하는 동안 Microsoft Defender Application Guard는 조직에서 신뢰하지 않는 사이트로부터 환경을 보호합니다. 사용자가 격리된 네트워크 경계에 나열되지 않은 사이트를 방문하면 해당 사이트가 Hyper-V 가상화된 브라우징 세션에서 열립니다. 신뢰할 수 있는 사이트는 네트워크 경계로 정의됩니다.  

- **Application Guard** - *Settings/AllowWindowsDefenderApplicationGuard*  
  예를 선택하여 이 기능을 켜면 Hyper-V 가상화된 브라우징 컨테이너에서 신뢰할 수 없는 사이트가 열립니다.  ‘구성되지 않음’으로 설정하면 모든 사이트(신뢰할 수 있는 사이트 및 신뢰할 수 없는 사이트)가 디바이스에서는 열리고 가상화된 컨테이너에서는 열리지 않습니다.   

  **기본값**: 예
 
  - **엔터프라이즈 사이트의 외부 콘텐츠** - *Settings/BlockNonEnterpriseContent*  
    ‘예’를 선택하여 승인되지 않은 웹 사이트의 콘텐츠가 로드되지 않도록 차단합니다.  ‘구성되지 않음’으로 설정하면 엔터프라이즈가 아닌 사이트가 디바이스에서 열릴 수 있습니다.  
 
    **기본값**: 예

  - **클립보드 동작** - *Settings/ClipboardSettings*  
    로컬 PC와 Application Guard 가상 브라우저 간에 허용되는 복사 및 붙여넣기 작업을 선택합니다.  다음 옵션을 사용할 수 있습니다.
    - ‘구성되지 않음’   
    - ‘둘 다 차단’ - PC와 가상 브라우저 간에 데이터를 전송할 수 없습니다.   
    - ‘호스트-컨테이너 차단’ - PC에서 가상 브라우저로 데이터를 전송할 수 없습니다. 
    - ‘컨테이너-호스트 차단’ - 가상 브라우저에서 호스트 PC로 데이터를 전송할 수 없습니다. 
    - ‘차단 안 함’ - 콘텐츠가 차단되지 않습니다.   

    **기본값**: 둘 다 차단  

- **Windows 네트워크 격리 정책 – 엔터프라이즈 네트워크 도메인 이름**  
  자세한 내용은 Windows 설명서의 [Policy CSP - NetworkIsolation](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-networkisolation)(정책 CSP - NetworkIsolation)을 참조하세요.
  
  Application Guard가 엔터프라이즈 사이트로 처리하는 클라우드에서 호스트되는 도메인, IP 주소 범위 및 네트워크 경계의 목록을 지정합니다.  

  **기본값**: securitycenter.windows.com

## <a name="application-reputation"></a>애플리케이션 안전도  

자세한 내용은 Windows 문서의 [정책 CSP - SmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-smartscreen)을 참조하세요.

- **확인되지 않은 파일의 차단 실행**  
    사용자가 확인되지 않은 파일을 실행하는 것을 차단합니다. ‘구성되지 않음’으로 설정하면 직원은 SmartScreen 경고를 무시하고 악성 파일을 실행할 수 있습니다.  ‘예’로 설정하면 직원은 SmartScreen 경고를 무시하고 악성 파일을 실행할 수 없습니다.   
  
    **기본값**: 예

- **앱 및 파일용 SmartScreen 필요**  
  Windows용 SmartScreen을 사용하도록 설정하려면 ‘예’로 설정합니다.   

  **기본값**: 예

## <a name="attack-surface-reduction"></a>공격 노출 영역 축소  

- **Office 앱이 자식 프로세스 유형을 시작**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - ‘차단’으로 설정하면 Office 앱이 자식 프로세스를 만들 수 없습니다.  Office 앱에는 Word, Excel, PowerPoint, OneNote 및 Access가 포함됩니다. 자식 프로세스 만들기는 일반적인 맬웨어 동작으로, 특히 Office 앱을 사용하여 악성 실행 파일을 시작하거나 다운로드하려고 시도하는 매크로 기반 공격에 적용됩니다.  

  **기본값**: 차단

- **스크립트에서 다운로드된 페이로드 실행 유형**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – 다운로드하거나 설치를 시도하는 사용자 동의 없이 설치된 애플리케이션의 검색 수준을 지정합니다.  

  **기본값**: 차단 

- **자격 증명 도용 방지 유형**  
  [Credential Guard를 사용하여 파생된 도메인 자격 증명을 보호](https://docs.microsoft.com/windows/security/identity-protection/credential-guard/credential-guard)하려면 ‘사용’으로 설정합니다.  Windows Defender Credential Guard는 가상화 기반 보안을 사용하여 권한 있는 시스템 소프트웨어만 액세스할 수 있도록 비밀을 격리합니다. 이러한 암호에 대한 무단 액세스는 Pass-the-Hash 또는 Pass-The-Ticket과 같은 자격 증명 도난 공격을 초래할 수 있습니다. Windows Defender Credential Guard는 NTLM 암호 해시, Kerberos 티켓 부여 티켓 및 애플리케이션에서 도메인 자격 증명으로 저장된 자격 증명을 보호하여 이러한 공격을 방지합니다.  

  **기본값**: 사용

- **이메일 콘텐츠 실행 유형**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - ‘차단’으로 설정하면 이 규칙은 다음 파일 형식이 Microsoft Outlook 또는 웹 메일(예: Gmail.com 또는 Outlook.com) 중 하나에 표시된 메일에서 실행되거나 시작되지 않도록 차단합니다.   

  - 실행 파일(예: .exe, .dll 또는 .scr)  
  - 스크립트 파일(예: PowerShell.ps, VisualBasic.vbs 또는 JavaScript.js 파일)  
  - 스크립트 보관 파일  

  **기본값**: 차단

- **자식 프로세스에서 Adobe Reader 시작**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - Adobe Reader가 자식 프로세스를 만들지 못하도록 차단하려면 이 규칙을 ‘사용’으로 설정합니다.  소셜 엔지니어링이나 악용을 통해 맬웨어가 추가 페이로드를 다운로드 및 시작하고 Adobe Reader를 중단합니다.  

  **기본값**: 사용

- **스크립트에서 난독 처리된 매크로 코드 유형**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - 맬웨어 및 기타 위협은 일부 스크립트 파일에서 해당 악성 코드를 난독 처리하거나 숨길 수 있습니다. 이 규칙은 난독 처리된 것으로 보이는 스크립트가 실행되는 것을 방지합니다.  
    
  **기본값**: 차단

- **신뢰할 수 없는 USB 프로세스 유형**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) – ‘차단’으로 설정하면 USB 이동식 드라이브 및 SD 카드에서 서명되지 않은 실행 파일이나 신뢰할 수 없는 실행 파일을 실행할 수 없습니다. 

  실행 파일은 다음과 같습니다.
  - 실행 파일(예: .exe, .dll 또는 .scr)
  - 스크립트 파일(예: PowerShell.ps, VisualBasic.vbs 또는 JavaScript.js 파일)  

  **기본값**: 차단

- **Office 앱 및 기타 프로세스 삽입 유형**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - ‘차단’으로 설정하면 Word, Excel, PowerPoint 및 OneNote를 포함한 Office 앱이 다른 프로세스에 코드를 삽입할 수 없습니다.  코드 삽입은 일반적으로 바이러스 백신 검사 엔진으로부터 활동을 숨기려는 악성 코드를 실행하는 맬웨어에서 사용됩니다.  

  **기본값**: 차단

- **Office 매크로 코드에서 Win32 가져오기 유형**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - ‘차단’으로 설정하면 이 규칙은 Win32 DLL을 가져올 수 있는 매크로 코드를 포함하는 Office 파일을 차단하려 합니다.  Office 파일에는 Word, Excel, PowerPoint 및 OneNote가 포함됩니다. 맬웨어는 Office 파일의 매크로 코드를 사용하여 Win32 DLL을 가져오고 로드할 수 있으며, 이 Win32 DLL은 이후 API를 호출하여 시스템 전체에 추가 감염을 일으키는 데 사용됩니다.  

  **기본값**: 차단

- **자식 프로세스에서 Office 통신 앱 시작**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - ‘사용’으로 설정하면 이 규칙은 Outlook이 자식 프로세스를 만들지 못하도록 차단합니다.  이 규칙은 자식 프로세스 만들기를 차단하여 소셜 엔지니어링 공격으로부터 보호하고 익스플로잇 코드가 Outlook에서 취약성을 악용하지 못하도록 차단합니다.  

  **기본값**: 사용

- **Office 앱 실행 파일 콘텐츠 생성 또는 시작 유형**  
  [공격 표면 감소 규칙](/windows/security/threat-protection/microsoft-defender-atp/attack-surface-reduction#attack-surface-reduction-rules) - ‘차단’으로 설정하면 Office 앱이 실행 가능한 콘텐츠를 만들 수 없습니다.  Office 앱에는 Word, Excel, PowerPoint, OneNote 및 Access가 포함됩니다.  

  이 규칙의 대상은 실행 파일을 만들거나 시작하는 의심스러운 악성 추가 기능 및 스크립트(확장)에서 사용되는 일반적인 동작입니다. 일반적인 맬웨어 기술입니다. 확장은 Office 앱에서 사용되는 것을 차단합니다. 일반적으로 이 확장은 Windows Scripting Host(.wsh 파일)를 사용하여 특정 작업을 자동화하는 스크립트를 실행하거나 사용자가 만든 추가 기능을 제공합니다.

  **기본값**: 차단

## <a name="bitlocker"></a>BitLocker  

자세한 내용은 Windows 설명서의 [BitLocker Group Policy settings](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-group-policy-settings)(BitLocker 그룹 정책 설정)를 참조하세요.  

- **디바이스 암호화**  
  ‘예’를 선택하여 BitLocker 디바이스 암호화를 사용하도록 설정합니다.  디바이스 하드웨어 및 Windows 버전에 따라 디바이스에 타사 암호화가 없는지 확인하는 메시지가 디바이스 사용자에게 표시될 수 있습니다. 타사 암호화가 활성화된 동안 Windows 암호화를 켜면 디바이스가 불안정하게 렌더링됩니다.  

   **기본값**: 예

- **BitLocker 이동식 드라이브 정책**  
  이 정책의 값은 BitLocker가 이동식 드라이브의 암호화에 사용하는 암호화 수준을 결정합니다. 기업은 보안 향상을 위해 암호화 수준을 제어합니다(AES-256이 AES-128보다 강력함). 예를 선택하여 이 설정을 사용하도록 설정하면 고정 데이터 드라이브, 운영 체제 드라이브 및 이동식 데이터 드라이브에 대한 암호화 알고리즘 및 키 암호 수준을 개별적으로 구성할 수 있습니다.  고정 및 운영 체제 드라이브의 경우 XTS-AES 알고리즘을 사용하는 것이 좋습니다. 이동식 드라이브의 경우 해당 드라이브가 Windows 10 버전 1511 이상을 실행하지 않는 다른 디바이스에서 사용될 경우 AES-CBC 128비트 또는 AES-CBC 256비트를 사용해야 합니다. 암호화 메서드를 변경해도 드라이브가 이미 암호화된 경우 또는 암호화가 진행 중인 경우에는 영향이 없습니다. 이러한 경우 이 정책을 무시합니다. 

  BitLocker 이동식 드라이브의 경우 다음 설정을 구성합니다.

  - **쓰기 액세스에 암호화 필요**  
    **기본값**: 예

  - **암호화 메서드**  
    **기본값**: AES 128비트 CBC

- **BitLocker 고정 드라이브 정책**  
  이 정책의 값은 BitLocker가 고정 드라이브의 암호화에 사용하는 암호화 수준을 결정합니다. 기업은 보안 향상을 위해 암호화 수준을 제어할 수 있습니다(AES-256이 AES-128보다 강력함). 이 설정을 사용하도록 설정하면 고정 데이터 드라이브, 운영 체제 드라이브 및 이동식 데이터 드라이브에 대한 암호화 알고리즘 및 키 암호 수준을 개별적으로 구성할 수 있습니다. 고정 및 운영 체제 드라이브의 경우 XTS-AES 알고리즘을 사용하는 것이 좋습니다. 이동식 드라이브의 경우 해당 드라이브가 Windows 10 버전 1511 이상을 실행하지 않는 다른 디바이스에서 사용될 경우 AES-CBC 128비트 또는 AES-CBC 256비트를 사용해야 합니다. 암호화 메서드를 변경해도 드라이브가 이미 암호화된 경우 또는 암호화가 진행 중인 경우에는 영향이 없습니다. 이러한 경우 이 정책을 무시합니다.

  BitLocker 고정 드라이브의 경우 다음 설정을 구성합니다.

  - **쓰기 액세스에 암호화 필요**  
    **기본값**: 예

  - **암호화 메서드**  
    **기본값**: AES 128비트 XTS

- **BitLocker 시스템 드라이브 정책**  
  이 정책의 값은 BitLocker가 시스템 드라이브의 암호화에 사용하는 암호화 수준을 결정합니다. 기업은 보안 향상을 위해 암호화 수준을 제어하려고 할 수 있습니다(AES-256이 AES-128보다 강력함). 이 설정을 사용하도록 설정하면 고정 데이터 드라이브, 운영 체제 드라이브 및 이동식 데이터 드라이브에 대한 암호화 알고리즘 및 키 암호 수준을 개별적으로 구성할 수 있습니다. 고정 및 운영 체제 드라이브의 경우 XTS-AES 알고리즘을 사용하는 것이 좋습니다. 이동식 드라이브의 경우 해당 드라이브가 Windows 10 버전 1511 이상을 실행하지 않는 다른 디바이스에서 사용될 경우 AES-CBC 128비트 또는 AES-CBC 256비트를 사용해야 합니다. 암호화 메서드를 변경해도 드라이브가 이미 암호화된 경우 또는 암호화가 진행 중인 경우에는 영향이 없습니다. 이러한 경우 이 정책을 무시합니다.  

  BitLocker 시스템 드라이브의 경우 다음 설정을 구성합니다.  

  - **암호화 메서드**  
    **기본값**: AES 128비트 XTS

## <a name="device-control"></a>디바이스 제어  

- **전체 검색 중 이동식 드라이브 검색**  
  [Defender/AllowFullScanRemovableDriveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanremovabledrivescanning) - ‘예’로 설정하면 Defender는 전체 검사 중에 이동식 드라이브(예: 플래시 드라이브)에서 악의적이고 원하지 않는 소프트웨어를 검사합니다.  Defender 바이러스 백신은 USB 디바이스에 있는 파일이 실행되기 전에 USB 디바이스에서 모든 파일을 검사합니다.

  이 목록의 관련 설정: *Defender/AllowFullScanOnMappedNetworkDrives*  

  **기본값**: 예

- **커널 DMA 보호와 호환되지 않는 외부 디바이스 열거**  
   [Policy CSP - DmaGuard](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dmaguard#dmaguard-deviceenumerationpolicy)(정책 CSP - DmaGuard)에서 *DmaGuard/DeviceEnumerationPolicy*를 참조하세요.

  이 정책은 외부 DMA 지원 디바이스에 대한 추가 보안을 제공합니다. 이 정책을 통해 DMA 디바이스 메모리 격리 및 샌드박스와 호환되지 않는 외부 DMA 지원 디바이스의 열거를 더 세부적으로 제어할 수 있습니다.

  이 정책은 커널 DMA 보호가 지원되고 시스템 펌웨어를 통해 사용하도록 설정되는 경우에만 적용됩니다. 커널 DMA 보호는 정책 또는 디바이스 사용자가 제어할 수 없는 플랫폼 기능입니다. 이 기능은 제조 시 시스템에서 지원되어야 합니다. 

  시스템에서 커널 DMA 보호를 지원하는지 확인하려면 시스템에서 MSINFO32.exe를 실행하고 요약 페이지에서 ‘커널 DMA 보호’ 필드를 검토합니다.   

  다음 옵션을 사용할 수 있습니다. 
  - ‘디바이스 기본값’ - 로그인 또는 화면 잠금 해제 이후에 DMA 다시 매핑 호환 드라이버를 사용하는 디바이스가 언제든지 열거될 수 있습니다.  DMA 다시 매핑 비호환 드라이버를 사용하는 디바이스는 사용자가 화면을 잠금 해제한 후에만 열거됩니다.
  - ‘모두 허용’ - 모든 외부 DMA 지원 PCIe 디바이스가 언제든지 열거됩니다. 
  - ‘모두 차단’ - DMA 다시 매핑 호환 드라이버를 사용하는 디바이스가 언제든지 열거될 수 있습니다.  DMA 다시 매핑 비호환 드라이버를 사용하는 디바이스가 언제든지 DMA를 시작하고 수행할 수 없습니다.

  **기본값**: 디바이스 기본값

- **디바이스 식별자로 하드웨어 디바이스 설치**  
  [DeviceInstallation/PreventInstallationOfMatchingDeviceIDs](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-preventinstallationofmatchingdeviceids) - 이 정책 설정을 사용하여 Windows를 설치하지 못하게 막는 플러그 앤 플레이 하드웨어 ID 목록 및 디바이스의 호환되는 ID 목록을 지정합니다. 이 정책 설정은 Windows에서 디바이스를 설치하도록 허용하는 기타 모든 정책 설정에 우선합니다. 이 정책 설정을 사용하도록 설정하면(‘하드웨어 디바이스 설치 차단’으로 설정) 만든 목록에 표시되는 하드웨어 ID 또는 호환되는 ID의 디바이스를 Windows에서 설치하지 못하게 막습니다.  원격 데스크톱 서버에서 이 정책 설정을 사용하도록 설정하면 이 정책은 원격 데스크톱 클라이언트에서 원격 데스크톱 서버로 지정된 디바이스의 리디렉션에 영향을 줍니다. 이 정책 설정을 사용하지 않도록 설정하거나 구성하지 않으면(‘하드웨어 디바이스 설치 허용’으로 설정) 기타 정책 설정에서 허용되거나 방지된 대로 디바이스를 설치하고 업데이트할 수 있습니다.   

  **기본**: 하드웨어 디바이스 설치 차단  

  ‘하드웨어 디바이스 설치 차단’을 선택하는 경우 사용할 수 있는 설정은 다음과 같습니다. 
  - **일치하는 하드웨어 디바이스 제거**  
    이 설정은 *디바이스 식별자에 의한 하드웨어 디바이스 설치*가 *하드웨어 디바이스 설치 차단*으로 설정된 경우에만 사용할 수 있습니다.  

    **기본**: *기본 구성 없음*

  - **차단된 하드웨어 디바이스 식별자**  
    이 설정은 *디바이스 식별자에 의한 하드웨어 디바이스 설치*가 *하드웨어 디바이스 설치 차단*으로 설정된 경우에만 사용할 수 있습니다. 이 설정을 구성하려면 옵션을 확장하고, **+ 추가**를 선택한 다음, 차단할 하드웨어 디바이스 식별자를 지정합니다.  

    **기본값**: ‘디바이스가 차단되지 않음’   

- **직접 메모리 액세스 차단**  
  [DataProtection/AllowDirectMemoryAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-dataprotection#dataprotection-allowdirectmemoryaccess) - 이 정책 설정을 사용하여 사용자가 Windows에 로그인할 때까지 디바이스에서 모든 핫 플러그형 PCI 다운스트림 포트에 대한 DMA(직접 메모리 액세스)를 차단합니다. 사용자가 로그인하면 Windows는 호스트 플러그 PCI 포트에 연결된 PCI 디바이스를 열거합니다. 사용자가 머신을 잠글 때마다 DMA는 사용자가 다시 로그인할 때까지 자식 디바이스가 없는 핫플러그 PCI 포트에서 차단됩니다. 머신을 잠그지 않은 경우 이미 열거된 디바이스는 분리될 때까지 계속 기능합니다. 

  이 정책 설정은 BitLocker 또는 디바이스 암호화를 사용하는 경우에만 적용됩니다.  

  **기본값**: 예


- **설치 클래스에 의한 하드웨어 디바이스 설치**  
  [DeviceInstallation/AllowInstallationOfMatchingDeviceSetupClasses](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-deviceinstallation#deviceinstallation-allowinstallationofmatchingdevicesetupclasses) - 이 정책 설정을 사용하면 Windows를 설치하지 못하게 막는 디바이스 드라이버에 대한 디바이스 설치 클래스 GUID(글로벌 고유 식별자)의 목록을 지정할 수 있습니다. 이 정책 설정은 Windows에서 디바이스를 설치하도록 허용하는 기타 모든 정책 설정에 우선합니다. 이 정책 설정을 사용하도록 설정하면(‘하드웨어 디바이스 설치 차단’으로 설정) Windows에서는 만든 목록에 표시되는 디바이스 설치 클래스 GUID의 디바이스 드라이버를 설치하거나 업데이트하지 못하게 방지합니다.  원격 데스크톱 서버에서 이 정책 설정을 사용하도록 설정하면 정책 설정은 원격 데스크톱 클라이언트에서 원격 데스크톱 서버로 지정된 디바이스의 리디렉션에 영향을 줍니다. 이 정책 설정을 사용하지 않도록 설정하거나 구성하지 않으면(‘하드웨어 디바이스 설치 허용’으로 설정) 기타 정책 설정에서 허용되거나 방지된 대로 Windows에서 디바이스를 설치하고 업데이트할 수 있습니다.   

  **기본**: 하드웨어 디바이스 설치 차단

  ‘하드웨어 디바이스 설치 차단’을 선택하는 경우 사용할 수 있는 설정은 다음과 같습니다.   

  - **일치하는 하드웨어 디바이스 제거**  
    이 설정은 *설치 클래스에 의한 하드웨어 디바이스 설치*가 *하드웨어 디바이스 설치 차단*으로 설정된 경우에만 사용할 수 있습니다.  
 
    **기본**: *기본 구성 없음*  

  - **차단된 하드웨어 디바이스 식별자**  
    이 설정은 [설치 클래스에 의한 하드웨어 디바이스 설치]가 [하드웨어 디바이스 설치 차단]으로 설정된 경우에만 사용할 수 있습니다. 이 설정을 구성하려면 옵션을 확장하고, **+ 추가**를 선택한 다음, 차단할 하드웨어 디바이스 식별자를 지정합니다.  
 
    **기본값**: ‘디바이스가 차단되지 않음’ 

## <a name="endpoint-detection-and-response"></a>엔드포인트 검색 및 응답  
자세한 내용은 Windows 설명서의 [WindowsAdvancedThreatProtection CSP](https://docs.microsoft.com/windows/client-management/mdm/windowsadvancedthreatprotection-csp)를 참조하세요.  

- **원격 분석 보고 주기 단축** - *Configuration/TelemetryReportingFrequency*  

  Microsoft Defender Advanced Threat Protection 원격 분석 보고 주기를 단축합니다.  

  **기본값**: 예

- **모든 파일에 대해 샘플 공유** - *Configuration/SampleSharing*  

  Microsoft Defender Advanced Threat Protection 샘플 공유 구성 매개 변수를 반환하거나 설정합니다.  

  **기본값**: 예

## <a name="exploit-protection"></a>Exploit Protection  

- **악용 방지 XML**  
  자세한 내용은 Windows 설명서의 [Import, export, and deploy exploit protection configurations](/windows/security/threat-protection/microsoft-defender-atp/import-export-exploit-protection-emet-xml)(악용 방지 구성 가져오기, 내보내기 및 배포)를 참조하세요.  

  IT 관리자가 원하는 시스템 및 애플리케이션 마이그레이션 옵션을 나타내는 구성을 조직의 모든 디바이스에 내보낼 수 있도록 설정합니다. 구성은 XML로 표시됩니다. 

  악용 방지를 적용하면 악용을 통한 맬웨어 유포 및 감염으로부터 디바이스를 보호하는 데 도움이 됩니다. Windows 보안 앱 및 PowerShell을 사용하여 완화 세트(일명 구성)를 만듭니다. 그런 다음, 이 구성을 XML 파일로 내보내서 여러 머신이 동일한 완화 설정 세트를 갖도록 공유할 수 있습니다.
 
  또한 기존 EMET 구성 XML 파일을 악용 방지 구성 XML로 변환하고 가져올 수 있습니다.

- **재정의 차단**  
  [WindowsDefenderSecurityCenter/DisallowExploitProtectionOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-windowsdefendersecuritycenter#windowsdefendersecuritycenter-disallowexploitprotectionoverride) – 사용자가 Windows Defender Security Center에서 악용 방지 설정 영역을 변경하지 못하도록 차단하려면 ‘예’로 설정합니다.  이 설정을 사용하지 않도록 설정하거나 구성하지 않은 경우 로컬 사용자는 악용 방지 설정 영역을 변경할 수 있습니다.  
  **기본값**: 예  

- **제어된 폴더 액세스**  
  [Defender/ControlledFolderAccessAllowedApplications](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessallowedapplications) 및 [Defender/ControlledFolderAccessProtectedFolders](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-controlledfolderaccessprotectedfolders)를 참조하세요. 
  
   인증되지 않은 앱이 파일 및 폴더를 무단으로 변경할 수 없도록 보호합니다.

  **기본값**: 감사 모드

## <a name="web--network-protection"></a>웹 및 네트워크 보호  

- **네트워크 보호 유형**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) - 이 정책을 사용하면 Windows Defender Exploit Guard에서 네트워크 보호를 켜거나 끌 수 있습니다. 네트워크 보호는 모든 앱을 사용하는 직원이 인터넷에서 피싱 사기, 악용 호스팅 사이트 및 악성 콘텐츠에 액세스하지 못하도록 보호하는 Windows Defender Exploit Guard의 기능입니다. 이 기능에는 타사 브라우저의 위험한 사이트 연결을 방지하는 것이 포함됩니다.  

  ‘사용’ 또는 ‘감사 모드’로 설정하면 사용자가 네트워크 보호를 끌 수 없으며 Windows Defender Security Center를 사용하여 연결 시도 정보를 볼 수 있습니다.    
 
  - ‘사용’으로 설정하면 사용자와 앱이 위험한 도메인에 연결하지 못하도록 차단됩니다.   
  - ‘감사 모드’로 설정하면 사용자와 앱이 위험한 도메인에 연결하지 못하도록 차단되지 않습니다.   

  ‘사용자 정의’로 설정하면 사용자와 앱이 위험한 도메인에 연결하지 못하도록 차단되지 않고 Windows Defender Security Center에서 연결 정보를 사용할 수 없습니다.   

  **기본값**: 감사 모드

- **Microsoft Edge용 SmartScreen 필요**  
  [Browser/AllowSmartScreen](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen) - Microsoft Edge에서는 Windows Defender SmartScreen(켜짐)을 사용하여 기본적으로 잠재적 피싱 사기 및 악성 소프트웨어로부터 사용자를 보호합니다. 기본적으로 이 정책은 사용하도록 설정되고(‘예’로 설정), 사용하도록 설정되면 사용자가 Windows Defender SmartScreen을 끄지 못하도록 차단됩니다.   디바이스에 대한 실제 정책이 [구성되지 않음]으로 설정되면 사용자가 Windows Defender SmartScreen을 켤 수 있으므로 디바이스가 보호되지 않습니다.  

  **기본값**: 예
  
- **악성 사이트 액세스 차단**  
  [Browser/PreventSmartScreenPromptOverride](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride) - 기본적으로 Microsoft Edge를 사용하면 사용자는 잠재적 악성 사이트에 대한 Windows Defender SmartScreen 경고를 무시하고 계속 사이트를 탐색할 수 있습니다. 이 정책을 사용하도록 설정하면(‘예’로 설정) Microsoft Edge에서는 사용자가 경고를 무시하지 못하고 계속 사이트를 탐색하지 못하도록 차단합니다.   

  **기본값**: 예

- **확인되지 않은 파일 다운로드 차단**  
  [Browser/PreventSmartScreenPromptOverrideForFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles) - 기본적으로 Microsoft Edge를 사용하면 사용자는 잠재적 악성 파일에 대한 Windows Defender SmartScreen 경고를 무시하고 확인되지 않은 파일의 다운로드를 계속할 수 있습니다. 이 정책을 사용하도록 설정하면(‘예’로 설정) 사용자는 경고를 무시하지 못하도록 차단되고 확인되지 않은 파일을 다운로드할 수 없습니다.   

  **기본값**: 예

## <a name="windows-defender-anti-virus----settings-review-pending-for-this-section"></a>Windows Defender 바이러스 백신    [이 섹션에 대한 설정 검토 보류 중]

자세한 내용은 Windows 설명서의 [정책 CSP - Defender](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender)를 참조하세요.

- **Microsoft 웹 브라우저에 로드된 스크립트 검사**  
  [Defender/AllowScriptScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscriptscanning) – Windows Defender 스크립트 검사 기능을 허용하려면 ‘예’로 설정합니다.   

  **기본값**: 예

- **들어오는 메일 메시지 검사**  
  [Defender/AllowEmailScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowemailscanning) – Windows Defender가 메일을 검사하도록 허용하려면 ‘예’로 설정합니다.   

  **기본값**: 예

- **Defender 샘플 제출 동의 형식**  
  [Defender/SubmitSamplesConsent](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent) - 데이터를 전송하려면 Windows Defender의 사용자 동의 수준을 확인합니다. 필요한 동의가 이미 부여된 경우 Windows Defender에서는 해당 동의를 제출합니다. 그렇지 않은 경우(및 사용자가 요청을 지정하지 않은 경우) 데이터를 전송하기 전에 UI가 시작되어 사용자 동의를 요청합니다(‘클라우드 제공 보호’가 ‘예’로 설정된 경우).    

  **기본**: 자동으로 안전 샘플 보내기

- **NIS(네트워크 검사 시스템)**  
  [Defender/EnableNetworkProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection) - NIS(네트워크 검사 시스템)에서 서명으로 검색된 악성 트래픽을 차단합니다.  
 
  **기본값**: 예

- **서명 업데이트 주기(시간)**  
  [Defender/SignatureUpdateInterval](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-signatureupdateinterval) – 디바이스가 새 Defender 서명 업데이트를 확인하는 빈도를 시간 단위로 지정합니다.  
 
  **기본값**: 4

- **예약된 검사에 대해 낮은 CPU 우선 순위 구성**  
  [Defender/EnableLowCPUPriority](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-enablelowcpupriority) – ‘예’로 설정하면 검사의 CPU 우선 순위가 낮음으로 설정됩니다.  *구성되지 않음*으로 설정하면 예약된 검사의 CPU 우선 순위가 변경되지 않습니다.  

    **기본값**: 예

- **Defender 액세스 시 보호 차단**  
  [Defender/AllowOnAccessProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowonaccessprotection) – ‘예’로 설정하면 Windows Defender 액세스 시 보호가 사용하도록 설정됩니다.   

  **기본값**: 예

- **수행할 시스템 검사 유형**  
  [Defender/ScanParameter](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-scanparameter) - Defender 검사 유형입니다.  

  **기본값**: 빠른 검색

- **모든 다운로드 검색**  
  [Defender/AllowIOAVProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowioavprotection) - ‘예’로 설정하면 Defender는 모든 다운로드된 파일과 첨부 파일을 검사합니다.   

  **기본값**: 예

- **격리된 맬웨어 삭제까지 남은 일 수**  
  [Defender/DaysToRetainCleanedMalware](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-daystoretaincleanedmalware) - 자동으로 삭제되기 전에 시스템에서 격리 항목을 유지할 기간(일)을 지정합니다. 0으로 설정하면 격리된 항목이 자동으로 삭제되지 않습니다.  

  **기본값**: 0

- **예약된 검사 시작 시간**  
  [Defender/ScheduleScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescantime) – Defender가 디바이스를 검사할 하루 중 시간을 예약합니다. 
  
  이 목록의 관련 옵션: *Defender/ScheduleScanDay*   

  **기본값**: 오전 2시

- **클라우드 제공 보호**  
  [Defender/AllowCloudProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowcloudprotection) – ‘예’로 설정하면 Windows Defender가 발견한 문제에 대한 정보를 Microsoft에 보냅니다.  Microsoft에서는 해당 정보를 분석하고, 사용자 및 기타 고객에게 영향을 미치는 문제에 대해 자세히 알아본 다음, 향상된 솔루션을 제공합니다.

  이 정책을 ‘예’로 설정하면 ‘Defender 샘플 전송 동의 유형’을 사용하여 사용자에게 디바이스에서 정보를 보내는 작업을 제어할 권한을 제공할 수 있습니다.    

  **기본값**: 예

- **잠재적으로 필요 없는 Defender 앱 작업**  
  [Defender/PUAProtection](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-puaprotection) – Windows Defender 바이러스 백신은 PUA(‘사용자 동의 없이 설치된 애플리케이션’)를 식별하고 PUA가 네트워크의 엔드포인트에서 다운로드 및 설치되지 않도록 차단할 수 있습니다.  
 
  - ‘차단’으로 설정하면 Windows Defender는 PUA를 차단하고 다른 위협과 함께 기록에 나열합니다. 
  - ‘감사’로 설정하면 Windows Defender는 PUA를 검색하지만 차단하지는 않습니다.  Windows Defender가 작업을 수행하는 대상 애플리케이션에 대한 정보를 찾으려면 이벤트 뷰어에서 Windows Defender에서 생성된 이벤트를 검색합니다.  
  - ‘디바이스 기본값’으로 설정하면 PUA 보호가 꺼집니다.   
 
  **기본값**: 차단

- **Defender 클라우드 제한 시간 연장**  
  [Defender/CloudExtendedTimeout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudextendedtimeout) - Windows Defender 바이러스 백신이 클라우드의 결과를 기다리는 동안 파일을 차단해야 하는 최대 추가 시간을 지정합니다. Windows Defender가 대기하는 기본 시간은 10초입니다. 여기에서 지정하는 추가 시간(최대 50초)은 기본 10초에 추가됩니다. 대부분의 경우 검사에는 최댓값보다 적은 시간이 걸립니다. 시간을 확장하면 클라우드가 의심스러운 파일을 철저하게 조사할 수 있습니다.  

  기본적으로 연장된 시간 값은 0(사용 안 함)입니다. Intune에서는 이 설정을 사용하도록 설정하고 추가로 적어도 20초를 지정하도록 권장합니다.  
 
  **기본값**: 0

- **보관 파일 검색**  
  [Defender/AllowArchiveScanning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowarchivescanning) – Windows Defender가 보관 파일을 검사하게 하려면 ‘예’로 설정합니다.   

  **기본값**: 예

- **Defender 시스템 검사 일정**  
  [Defender/ScheduleScanDay](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulescanday) - Defender가 디바이스를 검사하는 일정입니다. 
 
  이 목록의 관련 옵션: *Defender/ScheduleScanTime*

  **기본값**: 사용자 정의

- **동작 모니터링**  
  [Defender/AllowBehaviorMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowbehaviormonitoring) – Windows Defender 동작 모니터링 기능을 켜려면 ‘예’로 설정합니다.  Windows 10에 포함된 Windows Defender 동작 모니터링 센서는 운영 체제에서 동작 신호를 수집하고 처리하며, 이 센서 데이터를 Microsoft Defender ATP의 격리된 프라이빗 클라우드 인스턴스로 보냅니다.  

  **기본값**: 예

- **네트워크 폴더에서 열린 파일 검색**  
  [Defender/AllowScanningNetworkFiles](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowscanningnetworkfiles) – Windows Defender가 네트워크에 있는 파일을 검사하게 하려면 ‘예’로 설정합니다.  사용자는 읽기 전용 파일에서 검색된 맬웨어를 제거할 수 없습니다.  

  **기본값**: 예

- **Defender 클라우드 차단 수준**  
  [Defender/CloudBlockLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel) – 이 정책을 사용하여 적극적인 Windows Defender 바이러스 백신이 의심스러운 파일을 차단 및 검사하는 방법을 결정합니다. 다음 옵션을 사용할 수 있습니다.

  - 높음 - 클라이언트 성능을 최적화하는 동안 적극적으로 알 수 없는 파일을 차단합니다(거짓 긍정의 가능성 큼).
  - 높음 + - 적극적으로 알 수 없는 파일을 차단하고 추가 보호 수단을 적용합니다(클라이언트 성능에 영향을 줄 수 있음).
  - 허용 오차 제로 - 알 수 없는 실행 파일을 모두 차단합니다.

  **기본값**: 구성되지 않음

- **실시간 모니터링**  
  [Defender/AllowRealtimeMonitoring](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowrealtimemonitoring) – Windows Defender 실시간 모니터링을 허용하려면 ‘예’로 설정합니다.   

  **기본값**: 예

- **검색하는 동안 CPU 사용 제한**  
  [Defender/AvgCPULoadFactor](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-avgcpuloadfactor) – Windows Defender가 검사하는 동안 사용할 수 있는 최대 평균 CPU 사용률을 지정합니다.  

  **기본값**: 50

- **전체 검색 중 매핑된 네트워크 드라이브 검색**  
  [Defender/AllowFullScanOnMappedNetworkDrives](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowfullscanonmappednetworkdrives) – Windows Defender가 네트워크에 있는 파일을 검사하게 하려면 ‘예’로 설정합니다.  사용자는 읽기 전용 파일에서 검색된 맬웨어를 제거할 수 없습니다.

  이 목록의 관련 설정: *Defender/AllowScanningNetworkFiles*

  **기본값**: 예

- **Defender에 대한 최종 사용자 액세스 차단**  
  [Defender/AllowUserUIAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-allowuseruiaccess) – 디바이스에서 최종 사용자가 Windows Defender UI에 액세스하지 못하게 차단하려면 ‘예’로 설정합니다.   

  **기본값**: 예

- **빠른 검사 시작 시간**  
  [Defender/ScheduleQuickScanTime](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-schedulequickscantime) - Defender가 빠른 검사를 실행할 하루 중 시간을 예약합니다.  

  **기본값**: 오전 2시

## <a name="windows-defender-firewall"></a>Windows Defender 방화벽
자세한 내용은 Windows 설명서의 [Firewall CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp)(방화벽 CSP)를 참조하세요.

- **삭제 전 보안 연결 유휴 시간** - *MdmStore/Global/SaIdleTime*   
  이 시간(초) 동안 네트워크 트래픽이 확인되지 않으면 보안 연결이 삭제됩니다.  
  **기본값**: 300

- **파일 전송 프로토콜** - *MdmStore/Global/DisableStatefulFtp*   
  상태 저장 FTP(파일 전송 프로토콜)를 차단합니다.  
  **기본값**: 예

- **패킷 큐** - *MdmStore/Global/EnablePacketQueue*    
  IPsec 터널 게이트웨이 시나리오의 암호화된 수신 및 일반 텍스트 전달에 대해 수신 쪽 소프트웨어의 크기 조정이 활성화되는 방법을 지정합니다. 이렇게 하면 패킷 순서가 유지됩니다.  
  **기본값**: 디바이스 기본값

- **방화벽 프로필 도메인** - *FirewallRules/FirewallRuleName/Profiles*  
  규칙이 속한 프로필을 도메인, 프라이빗, 공용 중에서 지정합니다. 이 값은 도메인에 연결된 네트워크의 프로필을 나타냅니다.  

  사용 가능한 설정:  
  - **멀티캐스트 브로드캐스트에 대한 유니캐스트 응답 필요**  
    **기본값**: 예

  - **그룹 정책의 권한 있는 애플리케이션 규칙 병합됨**  
    **기본값**: 예

  - **인바운드 알림 차단됨**  
    **기본값**: 예

  - **그룹 정책의 전역 포트 규칙 병합됨**  
    **기본값**: 예

  - **은폐 모드 차단됨**  
    **기본값**: 예

  - **방화벽 사용**  
    **기본값**: 허용됨

  - **그룹 정책의 연결 보안 규칙 병합 안 됨**  
    **기본값**: 예

  - **그룹 정책의 정책 규칙 병합 안 됨**  
    **기본값**: 예

- **공용 방화벽 프로필** - *FirewallRules/FirewallRuleName/Profiles*  
  규칙이 속한 프로필을 도메인, 프라이빗, 공용 중에서 지정합니다. 이 값은 공용 네트워크의 프로필을 나타냅니다. 이 네트워크는 서버 호스트에서 관리자가 공용으로 분류합니다. 호스트가 네트워크에 처음 연결할 때 분류가 수행됩니다. 일반적으로 이 네트워크는 공항, 커피숍 및 네트워크의 피어나 네트워크 관리자를 신뢰할 수 없는 기타 공공 장소에 있습니다.  

  사용 가능한 설정:

  - **인바운드 연결 차단됨**  
    **기본값**: 예 

  - **멀티캐스트 브로드캐스트에 대한 유니캐스트 응답 필요**  
    **기본값**: 예  

  - **은폐 모드 필요**  
    **기본값**: 예 
 
  - **아웃바운드 연결 필요**  
    **기본값**: 예  

  - **그룹 정책의 권한 있는 애플리케이션 규칙 병합됨**  
    **기본값**: 예  

  - **인바운드 알림 차단됨**  
    **기본값**: 예  

  - **그룹 정책의 전역 포트 규칙 병합됨**  
    **기본값**: 예

  - **은폐 모드 차단됨**  
    **기본값**: 예

  - **방화벽 사용**  
    **기본값**: 허용됨  

  - **그룹 정책의 연결 보안 규칙 병합 안 됨**  
    **기본값**: 예  

  - **들어오는 트래픽 필요**  
    **기본값**: 예

  - **그룹 정책의 정책 규칙 병합 안 됨**  
    **기본값**: 예  

- **프라이빗 방화벽 프로필** - *FirewallRules/FirewallRuleName/Profiles*  
  규칙이 속한 프로필을 도메인, 프라이빗, 공용 중에서 지정합니다. 이 값은 프라이빗 네트워크의 프로필을 나타냅니다.  

  사용 가능한 설정: 

  - **인바운드 연결 차단됨**  
    **기본값**: 예

  - **멀티캐스트 브로드캐스트에 대한 유니캐스트 응답 필요**  
    **기본값**: 예

  - **은폐 모드 필요**  
    **기본값**: 예

  - **아웃바운드 연결 필요**  
    **기본값**: 예

  - **인바운드 알림 차단됨**  
    **기본값**: 예

  - **그룹 정책의 전역 포트 규칙 병합됨**  
    **기본값**: 예

  - **은폐 모드 차단됨**  
    **기본값**: 예  

  - **방화벽 사용**  
    **기본값**: 허용됨

  - **그룹 정책의 권한 있는 애플리케이션 규칙 병합 안 됨**  
    **기본값**: 예

  - **그룹 정책의 연결 보안 규칙 병합 안 됨**  
    **기본값**: 예

  - **들어오는 트래픽 필요**  
    **기본값**: 예

  - **그룹 정책의 정책 규칙 병합 안 됨**  
    **기본값**: 예  

- **방화벽 사전 공유 키 인코딩 방법**  
  **기본값**: UTF8

- **인증서 해지 목록 확인**  
  **기본값**: 디바이스 기본값

## <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello  

자세한 내용은 Windows 설명서의 [PassportForWork CSP](https://docs.microsoft.com/windows/client-management/mdm/passportforwork-csp)를 참조하세요.

- **비즈니스용 Windows Hello 구성** - *TenantId/Policies/UsePassportForWork*    
  비즈니스용 Windows Hello는 암호, 스마트 카드 및 가상 스마트 카드를 대체하여 Windows에 로그인할 수 있는 대체 방법입니다.  

  - *예*로 설정 되 면이 정책을 사용 하도록 설정 하 고 장치에서 비즈니스용 Windows Hello를 프로 비전 합니다.  
  - *구성 되지 않음*으로 설정 된 경우 기준은 장치의 정책 설정에 영향을 주지 않습니다. 즉, 장치에서 비즈니스용 Windows Hello를 사용 하지 않도록 설정한 경우 사용 하지 않도록 설정 된 상태로 유지 됩니다. 사용 하도록 설정 된 경우 사용 하도록 설정 된 상태로 유지 됩니다. 

  이 기준선을 통해 비즈니스용 Windows Hello를 사용 하지 않도록 설정할 수 없습니다. [Windows 등록](windows-hello.md)을 구성 하거나 [id 보호](identity-protection-configure.md)를 위한 장치 구성 프로필의 일부로 비즈니스용 windows Hello를 사용 하지 않도록 설정할 수 있습니다.  

비즈니스용 Windows Hello는 암호, 스마트 카드 및 가상 스마트 카드를 대체하여 Windows에 로그인할 수 있는 대체 방법입니다.  

  이 정책 설정을 구성하지 않거나 사용하도록 설정하면 디바이스가 비즈니스용 Windows Hello를 프로비저닝합니다. 이 정책 설정을 사용하지 않도록 설정하면 디바이스가 사용자를 위해 비즈니스용 Windows Hello를 프로비저닝하지 않습니다.

  Intune에서는 Windows Hello를 사용하지 않도록 설정할 수 없습니다. 대신 비즈니스용 Windows Hello를 사용하도록 정책을 구성하거나(예), 직접 Windows Hello를 구성하지 않을 수 있습니다(구성되지 않음). 구성되지 않음으로 설정하면 디바이스가 다른 정책을 통해 구성을 받을 수 있으므로 이 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.  

  **기본값**: 예  

- **PIN에 소문자 필요** - *TenantId/Policies/PINComplexity/LowercaseLetters*  
  **기본값**: 허용됨  

- **PIN에 특수 문자 필요** - *TenantId/Policies/PINComplexity/SpecialCharacters*  
  **기본값**: 허용됨  

- **PIN에 대문자 필요** - *TenantId/Policies/PINComplexity/UppercaseLetters*   
  **기본값**: 허용됨  

