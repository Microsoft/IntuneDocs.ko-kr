---
title: Microsoft Intune의 BitLocker 정책에 대한 문제 해결 팁
titleSuffix: Microsoft Intune
description: Intune 정책을 사용하여 디바이스에서 BitLocker 암호화를 사용하도록 설정하는 방법과 정책이 디바이스에 성공적으로 배포되었는지 확인하는 방법을 설명합니다.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556502"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Microsoft Intune의 BitLocker 정책 문제 해결

이 문서를 참조하여 Intune 관리자는 Windows 10 디바이스에서 Intune 정책을 기반으로 BitLocker를 구성하는 방법을 이해할 수 있습니다. 이 문서에서는 Intune을 사용하여 관리하는 디바이스에서 BitLocker 설정 문제를 해결하는 방법에 대해서도 지침을 제공합니다.  

## <a name="understanding-bitlocker"></a>BitLocker 이해

BitLocker 드라이브 암호화는 Microsoft Windows 운영 체제에서 제공하는 서비스로, 사용자가 하드 드라이브의 데이터를 암호화할 수 있게 합니다. BitLocker는 운영 체제 드라이브, 이동식 미디어 드라이브 및 고정 데이터 드라이브에 대한 암호화를 지원합니다. 또한 BitLocker는 중요한 데이터의 보호를 강화하기 위해 256비트 암호화를 사용하도록 지원합니다.  

Microsoft Intune을 사용하여 다음과 같은 방법으로 Windows 10 디바이스에서 BitLocker를 관리할 수 있습니다.

- **디바이스 구성 정책** - 엔드포인트 보호를 관리하는 디바이스 구성 프로필을 만들 때 Intune에서 특정 기본 제공 정책 옵션을 사용할 수 있습니다. 이러한 옵션을 찾으려면 [엔드포인트 보호를 위한 디바이스 프로필을 만든](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings) 후에 *플랫폼*으로 **Windows 10 이상**을 선택한 다음 *설정*으로 **Windows 암호화** 범주를 선택합니다. 

   사용할 수 있는 옵션 및 기능에 대한 자세한 내용은 [Windows 암호화](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)를 참조하세요.

- **보안 기준** - [보안 기준](security-baselines.md)은 관련 보안 팀에서 권장하는 알려진 설정 및 기본값 그룹으로, Windows 디바이스 보안을 지원합니다. *MDM 보안 기준* 또는 *Microsoft Defender ATP 기준*과 같은 다양한 기준 원본은 서로 다른 설정뿐 아니라 동일한 설정도 관리할 수 있습니다. 디바이스 구성 정책을 사용하여 관리하는 것과 동일한 설정을 관리할 수도 있습니다. 

Intune 외에도 Modern Standby 및 HSTI 규격인 하드웨어의 경우, 이러한 기능 중 하나를 사용하면 사용자가 디바이스를 Azure AD에 조인할 때마다 BitLocker 디바이스 암호화가 자동으로 설정됩니다. Azure AD는 복구 키도 백업되는 포털을 제공하므로 사용자는 필요 시 셀프 서비스를 위한 자체 복구 키를 검색할 수 있습니다.

BitLocker 설정을 그룹 정책 같은 다른 방법으로 관리하거나 디바이스 사용자가 수동으로 설정할 수도 있습니다.

디바이스에 설정을 적용하는 방법과 관계없이 BitLocker 정책은 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 사용하여 디바이스에서 암호화를 구성합니다. BitLocker CSP는 Windows에 기본적으로 제공되며 Intune에서 할당된 디바이스에 BitLocker 정책을 배포하는 경우 정책의 설정이 적용될 수 있도록 Windows 레지스트리에 적절한 값을 기록하는 디바이스에 대한 BitLocker CSP입니다.

BitLocker에 대해 자세히 알아보려면 다음 리소스를 참조하세요.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 개요 및 요구 사항 FAQ](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

이러한 정책이 수행하는 작업 및 작동하는 방식에 대해 전반적으로 이해했으므로 이제 BitLocker 설정이 Windows 클라이언트에 성공적으로 적용되는지 확인할 수 있는 방법을 알아보세요.

## <a name="verify-the-source-of-bitlocker-settings"></a>BitLocker 설정의 원본 확인

Windows 10 디바이스에서 BitLocker 문제를 조사할 때 문제가 Intune 관련인지 아니면 Windows 관련인지를 먼저 확인하는 것이 중요합니다. 오류가 발생할 수 있는 원인을 알고 나면 문제 해결 노력을 올바른 위치에 집중할 수 있으며 필요한 경우 올바른 팀의 지원을 받을 수 있습니다.  

첫 번째 단계로, Intune 정책이 대상 디바이스에 성공적으로 배포되었는지 여부를 확인합니다. 다음 예제에는 다음과 같이 Windows 암호화(BitLocker) 설정을 배포하는 디바이스 구성 정책이 있습니다.

![설정을 사용한 Windows 암호화 디바이스 구성 정책](./media/troubleshooting-bitlocker-policies/settings.png)

설정이 대상 디바이스에 적용되었는지 확인하려면 어떻게 하나요? 다음과 같은 몇 가지 방법이 있습니다.

### <a name="device-configuration-policy-device-status"></a>디바이스 구성 정책 디바이스 상태  

디바이스 구성 정책을 사용하여 BitLocker를 구성할 때 Intune 포털에서 정책의 상태를 확인할 수 있습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.

2. **디바이스** > **구성 프로필**을 선택하고 BitLocker 설정을 포함하는 프로필을 선택합니다.

3. 보려는 프로필을 선택한 후 **디바이스 상태**를 선택합니다. 프로필에 할당된 디바이스가 나열되고 *디바이스 상태* 열에 디바이스가 프로필을 성공적으로 배포했음을 나타냅니다.

BitLocker 정책을 수신하는 디바이스와 완전히 암호화되는 드라이브 사이에 지연이 있을 수 있습니다.  

### <a name="use-control-panel-on-the-client"></a>클라이언트에서 제어판 사용  

BitLocker를 사용하도록 설정하고 드라이브를 암호화한 디바이스에서는 디바이스 제어판에서 BitLocker 상태를 볼 수 있습니다. 디바이스에서 **제어판** > **시스템 및 보안** > **BitLocker 드라이브 암호화**를 엽니다. 다음 이미지처럼 확인 메시지가 표시됩니다.  

![BitLocker가 제어판에서 켜짐](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>명령 프롬프트 사용  

BitLocker를 사용하도록 설정하고 드라이브를 암호화한 디바이스에서 관리자 자격 증명을 사용하여 명령 프롬프트를 시작하고 `manage-bde -status`를 실행합니다. 결과는 다음과 같습니다.  
![status 명령의 결과](./media/troubleshooting-bitlocker-policies/command.png)

예제에서는

- **BitLocker 보호**가 **설정**되어 있습니다.
- **암호화된 비율**은 **100%** 입니다.
- **암호화 방법**은 **XTS-AES 256**입니다.

다음 명령을 실행하여 **키 보호기**를 확인할 수도 있습니다.

```cmd
Manage-bde -protectors -get c:
```

또는 PowerShell로 다음을 수행할 수 있습니다.

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>디바이스 레지스트리 키 구성 검토

BitLocker 정책이 디바이스에 성공적으로 배포되면 디바이스에서 다음 레지스트리 키를 확인하여 BitLocker 설정의 구성을 검토할 수 있습니다.  *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. 아래 예를 살펴보세요.

![BitLocker 레지스트리 키](./media/troubleshooting-bitlocker-policies/registry.png)

이러한 값은 BitLocker CSP에 의해 구성됩니다. 키 값이 Intune Windows 암호화 정책의 원본에 지정된 설정과 일치하는지 확인합니다. 이러한 각 설정에 대한 자세한 내용은 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 참조하세요.

> [!NOTE]
> Windows 이벤트 뷰어에는 Bitlocker와 관련된 다양한 정보도 포함되어 있습니다. 나열할 내용이 너무 많지만, **Bitlocker API**를 검색하면 많은 유용한 정보를 얻을 수 있습니다.

### <a name="check-the-mdm-diagnostics-report"></a>MDM 진단 보고서 확인

BitLocker를 사용하도록 설정한 디바이스에서는 대상 디바이스에서 MDM 진단 보고서를 생성 및 확인하여 BitLocker 정책이 있는지 확인할 수 있습니다. 보고서에서 정책 설정을 볼 수 있다면 정책이 성공적으로 배포되었음을 나타내는 다른 표시입니다. 다음 링크 *Microsoft 도움말* 비디오에서는 Windows 디바이스에서 MDM 진단 보고서를 캡처하는 방법을 설명합니다.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

MDM 진단 보고서를 분석하면 처음에 내용이 약간 혼란스러울 수 있습니다. 다음은 보고서에 있는 항목을 정책의 설정과 상호 연결하는 방법을 보여 주는 예입니다.

![MDM 진단 보고서 예제](./media/troubleshooting-bitlocker-policies/report.png)

출력 결과에는 BitLocker 정책의 값에 해당하는 값이 표시됩니다.

![출력 결과에 값 표시 ](./media/troubleshooting-bitlocker-policies/output.png)

MDM 진단 출력 결과:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

[BitLocker CSP 설명서](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 참조하여 각 값의 의미를 확인할 수 있습니다. 이 예제에서는 다음 이미지에서 코드 조각이 공유됩니다.

![값의 목적](./media/troubleshooting-bitlocker-policies/shared-example.png)

마찬가지로 모든 값을 보고 BitLocker CSP 링크에서 확인할 수 있습니다.

> [!TIP]
> MDM 진단 보고서의 주요 목적은 문제를 해결할 때 Microsoft 지원에 도움을 주는 것입니다. Intune에 대한 지원 사례를 여는 경우 문제가 Windows 클라이언트 관련이면 항상 이 보고서를 수집하고 지원 요청에 포함하는 것이 좋습니다.

## <a name="troubleshooting-bitlocker-policy"></a>BitLocker 정책 문제 해결

이제 BitLocker 정책이 Intune에 의해 성공적으로 배포되어 BitLocker의 구성이 Windows의 BitLocker CSP에 전달되었는지 확인하는 방법을 잘 알게 되었습니다.

**정책이 디바이스에 도달하지 못함** - 용량에 Intune 정책이 없는 경우:

- **디바이스가 Microsoft Intune에 제대로 등록되어 있습니까?** 등록되어 있지 않다면 정책과 관련된 문제를 해결하기 전에 등록 문제를 해결해야 합니다. Windows 등록 문제 해결에 대한 도움말은 [여기](../enrollment/troubleshoot-windows-enrollment-errors.md)를 참조하세요.

- **디바이스에 활성 네트워크 연결이 있습니까?** 디바이스가 비행기 모드이거나, 꺼져 있거나, 서비스가 제공되지 않는 위치에 사용자 디바이스가 있는 경우에는 네트워크 연결이 복원될 때까지 정책이 제공 또는 적용되지 않습니다.

- **BitLocker 정책이 올바른 사용자 또는 디바이스 그룹에 배포되었나요?** 올바른 사용자 또는 디바이스가 대상 그룹의 구성원인지 확인합니다.

**정책이 있지만 일부 설정만 구성됨** - Intune 정책이 디바이스에 도달했지만 일부 구성만 설정된 경우:

- **전체 정책이 배포되지 못하나요 아니면 특정 설정만 적용되지 않나요?** 일부 정책 설정만 적용되지 않는 시나리오가 발생한 경우 다음 고려 사항을 확인하세요.

  1. **일부 BitLocker 설정이 일부 Windows 버전에서만 지원됨**.
     정책은 단일 단위인 디바이스에 적용되므로, 일부 설정이 적용되고 다른 설정은 적용되지 않는 경우 정책 자체가 수신되었다고 확신할 수 있습니다. 이 경우 디바이스의 Windows 버전이 문제가 되는 설정을 지원하지 않을 수 있습니다. 각 설정에 대한 버전 요구 사항을 자세히 알아보려면 Windows 설명서의 [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 참조하세요.

  2. **BitLocker가 일부 하드웨어에서만 지원됨**.
     올바른 버전의 Windows를 사용하는 경우에도 기본 디바이스 하드웨어가 BitLocker 암호화를 위한 요구 사항을 충족하지 못할 수 있습니다. Windows 설명서에서 [BitLocker의 시스템 요구 사항](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)을 확인할 수 있지만 확인해야 할 주요 사항은 that the 디바이스에 호환되는 TPM 칩(1.2 이상)과 TCG(신뢰할 수 있는 컴퓨팅 그룹) 규격 BIOS 또는 UEFI 펌웨어가 있는지 확인하는 것입니다.
     
**Bitlocker 암호화가 자동으로 수행되지 않습니다** - "다른 디스크 암호화에 대한 경고" 설정이 차단으로 설정되고 암호화 마법사가 계속 다음과 같이 표시되는 Endpoint Protection 정책을 구성했습니다.

- **Windows 버전에서 자동 암호화를 지원하는지 확인** 이를 위해서는 최소한 버전 1803이 필요합니다. 사용자가 디바이스의 관리자가 아닌 경우, 최소 버전 1809가 필요합니다. 또한 버전 1809는 Modern Standby를 지원하지 않는 디바이스에 대한 지원을 추가했습니다.

**Bitlocker로 암호화된 디바이스가 Intune 준수 정책에 맞지 않는 것으로 나타남** -BitLocker 암호화가 완료되지 않을 때 이러한 문제가 발생합니다. 디스크 크기, 파일 수, BitLocker 설정 등의 제반 요인에 따라 BitLocker 암호화는 시간이 오래 걸릴 수 있습니다. 암호화가 완료되면 디바이스는 준수 상태로 표시됩니다. Windows 업데이트를 최근에 설치한 직후에도 디바이스가 일시적으로 비준수 상태를 보일 수 있습니다.

**정책이 256 비트를 지정할 때 디바이스는 128비트 알고리즘을 사용하여 암호화됩니다.** -- 기본적으로 Windows 10은 XTS-AES 128비트 암호화로 드라이브를 암호화합니다. [Autopilot 진행 중 BitLocker에 대한 256비트 암호화를 설정](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#)하려면 이 가이드를 참조하세요.


**조사 예제**

- Windows 10 디바이스에 BitLocker 정책을 배포하면 포털에서 **디바이스 암호화** 설정에 **오류** 상태가 표시됩니다.

- 이름에서 알 수 있듯이, 이 설정을 사용하면 관리자가 *BitLocker > 디바이스 암호화*를 사용하여 암호화를 켜도록 요구할 수 있습니다. 앞에서 설명한 문제 해결 팁을 사용하여 먼저 MDM 진단 보고서를 확인합니다. 이 보고서는 디바이스에 올바른 정책이 배포되었는지 확인합니다.

  ![보고서에서 디바이스에 올바른 정책이 배포되었는지 확인](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- 레지스트리에서 성공 여부도 확인합니다.

  ![RequiredDeviceEncryption 레지스트리 값이 1로 표시됨](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 그런 다음 PowerShell을 사용하여 TPM의 상태를 확인하고 이 TPM을 디바이스에서 사용할 수 없는지 확인합니다.

  ![PowerShell을 사용하여 확인된 TPM 상태](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- BitLocker는 TPM을 사용하기 때문에 Intune이나 정책의 문제로 인해서가 아니라 디바이스 자체에 TPM 칩이 없거나 BIOS에서 TPM이 사용하지 않도록 설정되어 있기 때문에 BitLocker가 실패한다고 판단할 수 있습니다.

  추가 팁으로, Windows 이벤트 뷰어의 **애플리케이션 및 서비스 로그** > **Microsoft** > **Windows** > **BitLocker API**에서도 동일한 내용을 확인할 수 있습니다. **BitLocker API** 이벤트 로그에서 TPM을 사용할 수 없음을 의미하는 이벤트 ID 853을 확인할 수 있습니다.

  ![이벤트 ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > 디바이스에서 **tpm.msc**를 실행하여 TPM 상태를 확인할 수도 있습니다.

## <a name="summary"></a>요약

Intune에서 BitLocker 정책 문제를 해결하고 정책이 의도된 디바이스에 도달하는 것을 확인할 수 있으면 문제가 Intune과 직접적인 관련이 없다고 가정해도 됩니다. 문제는 Windows OS 또는 하드웨어와 관련이 있을 가능성이 높습니다. 이 경우 TPM 구성이나 UEFI 및 보안 부팅 같은 다른 영역을 확인하기 시작합니다.

## <a name="next-steps"></a>다음 단계  

BitLocker로 작업할 때 도움이 될 수 있는 추가 리소스는 다음과 같습니다.

- [BitLocker 제품 설명서](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 시스템 요구 사항](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker 자주 묻는 질문](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP 설명서](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows 암호화 정책 설정](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [AAD/MDM을 사용하여 하드웨어에 무관한 자동 BitLocker 암호화](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Auto-Pilot 디바이스에서 BitLocker 암호화에 대한 CSP 정책](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Intune을 사용하여 BitLocker 정책 만들기 및 배포 연습](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
