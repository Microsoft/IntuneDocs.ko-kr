---
title: Microsoft Intune의 BitLocker 정책에 대 한 문제 해결 팁
titleSuffix: Microsoft Intune
description: Intune 정책을 사용 하 여 장치에서 BitLocker 암호화를 사용 하도록 설정 하는 방법과 정책이 장치에 성공적으로 배포 되었는지 확인 하는 방법을 설명 합니다.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 440eb2d457783ac71b905d064a6d83abaa966cfe
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503780"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Microsoft Intune의 BitLocker 정책 문제 해결

이 문서는 Intune 관리자가 Windows 10 장치에서 Intune 정책을 기반으로 BitLocker를 구성 하는 방법을 이해 하는 데 도움이 됩니다. 이 문서에서는 Intune을 사용 하 여 관리 하는 장치에서 BitLocker 설정 문제를 해결 하는 방법에 대 한 지침도 제공 합니다.  

## <a name="understanding-bitlocker"></a>BitLocker 이해

BitLocker 드라이브 암호화는 Microsoft Windows 운영 체제에서 제공 하는 서비스로, 사용자가 하드 드라이브의 데이터를 암호화할 수 있도록 합니다. BitLocker는 운영 체제 드라이브, 이동식 미디어 드라이브 및 고정 데이터 드라이브에 대 한 암호화를 지원 합니다. 또한 BitLocker는 중요 한 데이터의 보호를 강화 하기 위해 256 비트 암호화를 사용할 수 있도록 지원 합니다.  

Microsoft Intune를 사용 하 여 Windows 10 장치에서 BitLocker를 관리 하는 다음과 같은 방법을 사용할 수 있습니다.

- **장치 구성 정책** -일부 기본 제공 정책 옵션은 Intune 관리 콘솔의 **장치 구성**  > **Endpoint Protection**  > **Windows 암호화 정책**에서 사용할 수 있습니다. [Windows 암호화](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)에서 사용 가능한 모든 스위치 및 기능을 찾을 수 있습니다.

- 보안[기준](security-baselines.md) ** -  보안 기준은** Windows 장치를 보호 하는 데 도움이 되는 관련 보안 팀에서 권장 하는 설정 및 기본값의 알려진 그룹입니다. *MDM 보안 기준* 또는 *Microsoft Defender ATP 기준선* 과 같은 다양 한 기준 원본은 서로 다른 설정과 동일한 설정을 관리할 수 있습니다. 장치 구성 정책을 사용 하 여 관리 하는 것과 동일한 설정을 관리할 수도 있습니다. 

Intune 외에도 BitLocker 설정을 그룹 정책 같은 다른 방법으로 관리 하거나 장치 사용자가 수동으로 설정할 수 있습니다.

장치에 설정을 적용 하는 방법에 관계 없이 BitLocker 정책은 [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 를 사용 하 여 장치에서 암호화를 구성 합니다. BitLocker CSP는 Windows에 기본 제공 되며, Intune에서 할당 된 장치에 BitLocker 정책을 배포 하는 경우 정책의 설정이 적용 될 수 있도록 Windows 레지스트리에 적절 한 값을 기록 하는 장치에 대 한 BitLocker CSP입니다.

BitLocker에 대해 자세히 알아보려면 아래 리소스를 참조 하세요.

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 개요 및 요구 사항 FAQ](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

이러한 정책에서 수행 하는 작업 및 작동 방식에 대 한 일반적인 이해를 했으므로 이제 BitLocker 설정이 Windows 클라이언트에 성공적으로 적용 되는지 확인 하는 방법을 살펴보세요.

## <a name="verify-the-source-of-bitlocker-settings"></a>BitLocker 설정의 원본 확인

Windows 10 장치에서 BitLocker 문제를 조사할 때 문제가 Intune 관련 인지 아니면 Windows 관련 인지를 먼저 확인 하는 것이 중요 합니다. 오류가 발생할 수 있는 원인을 알고 나면 올바른 팀에서 문제 해결 노력을 집중 하 고 필요한 경우 올바른 팀에서 지원을 받을 수 있습니다.  

첫 번째 단계로, Intune 정책이 대상 장치에 성공적으로 배포 되었는지 여부를 확인 합니다. 다음 예제에서는 다음과 같이 Windows 암호화 (BitLocker) 설정을 배포 하는 장치 구성 정책이 있습니다. 

![설정을 사용 하는 Windows 암호화 장치 구성 정책](./media/troubleshooting-bitlocker-policies/settings.png)

설정이 대상 장치에 적용 되었는지 확인 하려면 어떻게 해야 하나요? 다음은이 작업을 수행 하는 몇 가지 방법입니다.

### <a name="device-configuration-policy-device-status"></a>장치 구성 정책 장치 상태  

장치 구성 정책을 사용 하 여 BitLocker를 구성 하는 경우 Intune 포털에서 정책의 상태를 확인할 수 있습니다. 포털에서 **장치 구성**  > **프로필** 로 이동 하 > BitLocker 설정을 포함 하는 프로필을 선택한 다음 **장치 상태**를 선택 합니다. 프로필에 할당 된 장치가 나열 되 고 *장치 상태* 열에 장치가 프로필을 성공적으로 배포 했음을 나타냅니다. 

BitLocker 정책을 받는 장치와 완전히 암호화 된 드라이브 사이에 지연이 있을 수 있습니다.  

 
### <a name="use-control-panel-on-the-client"></a>클라이언트에서 제어판 사용  

BitLocker를 사용 하도록 설정 하 고 드라이브를 암호화 한 장치에서는 장치 제어판에서 BitLocker 상태를 볼 수 있습니다. 장치에서 **제어판**  > **시스템 및 보안**  > **BitLocker 드라이브 암호화**를 엽니다. 다음 그림에 표시 된 것 처럼 확인 메시지가 표시 됩니다.  

![BitLocker가 제어판에서 켜 짐](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>명령 프롬프트 사용  

BitLocker를 사용 하도록 설정 되 고 드라이브가 암호화 된 장치에서 관리자 자격 증명을 사용 하 여 명령 프롬프트를 시작 하 고 `manage-bde -status`를 실행 합니다. 결과는 다음과 같습니다.  
status 명령의 ![A 결과 ](./media/troubleshooting-bitlocker-policies/command.png)

예제에서는 
- **BitLocker 보호가** **설정**되어 있습니다.  
- **암호화된 비율**은 **100%** 입니다.  
- **암호화 방법은** **XTS-AES 256**입니다.  

다음 명령을 실행 하 여 **키 보호기** 를 확인할 수도 있습니다.

```cmd
Manage-bde -protectors -get c:
```

또는 PowerShell로 다음을 수행할 수 있습니다.

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>장치 레지스트리 키 구성 검토   

BitLocker 정책이 장치에 성공적으로 배포 되 면 BitLocker 설정의 구성을 검토할 수 있는 장치에서 다음 레지스트리 키를 확인 합니다. *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . 아래 예를 살펴보세요.

![BitLocker 레지스트리 키](./media/troubleshooting-bitlocker-policies/registry.png)

이러한 값은 BitLocker CSP에 의해 구성 됩니다. 키 값이 Intune Windows 암호화 정책의 원본에 지정 된 설정과 일치 하는지 확인 합니다. 이러한 각 설정에 대 한 자세한 내용은 [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 참조 하세요.

> [!NOTE]
> Windows 이벤트 뷰어에는 Bitlocker와 관련 된 다양 한 정보도 포함 되어 있습니다. 여기에 나열할 내용이 너무 많고 **BITLOCKER API** 를 검색 하면 많은 유용한 정보를 얻을 수 있습니다.

### <a name="check-the-mdm-diagnostics-report"></a>MDM 진단 보고서를 확인 합니다.  

BitLocker를 사용 하도록 설정 된 장치에서 대상 장치에서 MDM 진단 보고서를 생성 하 고 보고 BitLocker 정책이 있는지 확인할 수 있습니다. 보고서에서 정책 설정을 볼 수 있는 경우 정책이 성공적으로 배포 되었음을 나타내는 또 다른 표시입니다. Microsoft는 다음 링크에서 비디오를 *사용* 하 여 Windows 장치에서 MDM 진단 보고서를 캡처하는 방법을 설명 합니다. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

MDM 진단 보고서를 분석 하면 먼저 콘텐츠가 약간 혼란 스 러 울 수 있습니다. 다음은 보고서에 있는 항목을 정책의 설정과 상호 연결 하는 방법을 보여 주는 예입니다.

![MDM 진단 보고서 예제](./media/troubleshooting-bitlocker-policies/report.png)

출력 결과에는 BitLocker 정책의 값에 해당 하는 값이 표시 됩니다.

![출력 결과 값을 표시 합니다. ](./media/troubleshooting-bitlocker-policies/output.png)

MDM 진단 출력 결과:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

[BITLOCKER CSP 설명서](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 를 참조 하 여 각 값의 의미를 확인할 수 있습니다. 이 예제에서는 다음 이미지에서 코드 조각이 공유 됩니다.

![값의 목적](./media/troubleshooting-bitlocker-policies/shared-example.png)

 마찬가지로 모든 값을 보고 BitLocker CSP 링크에서 확인할 수 있습니다.

> [!TIP]
> MDM 진단 보고서의 주요 목적은 문제를 해결할 때 Microsoft 지원 지 원하는 것입니다. Intune에 대 한 지원 사례를 열고 문제에 Windows 클라이언트가 포함 된 경우 항상이 보고서를 수집 하 여 지원 요청에 포함 하는 것이 좋습니다.

## <a name="troubleshooting-bitlocker-policy"></a>BitLocker 정책 문제 해결

이제 Intune에서 bitlocker 정책이 성공적으로 배포 되었는지 확인 하는 방법에 대해 잘 알고 있어야 합니다 .이는 WIndows의 BitLocker CSP에 bitlocker를 구성 하는 방법을 설명 하는 것입니다.  

**장치에 도달 하지 못한 정책** : 모든 용량에 Intune 정책이 없는 경우:  
- **장치가 Microsoft Intune에 올바르게 등록 되어 있나요?** 그렇지 않은 경우 정책과 관련 된 모든 문제를 해결 하기 전에 해결 해야 합니다. Windows 등록 문제 해결에 대 한 도움말은 [여기](../enrollment/troubleshoot-windows-enrollment-errors.md)를 참조 하세요.  
- **장치에 활성 네트워크 연결이 있나요?** 장치가 비행기 모드에 있거나 꺼져 있거나, 사용자가 서비스가 없는 위치에 있는 경우에는 네트워크 연결이 복원 될 때까지 정책이 배달 되거나 적용 되지 않습니다.  
- **BitLocker 정책이 올바른 사용자 또는 장치 그룹에 배포 되었습니까?** 올바른 사용자 또는 장치가 대상 그룹의 구성원 인지 확인 합니다.  

**정책이 있지만 일부 설정이 구성 되지 않았습니다** . Intune 정책이 장치에 도달 하면 모든 구성이 설정 되지 않습니다.  
- **전체 정책의 배포가 실패 하거나 적용 되지 않는 특정 설정에만 적용 되나요?** 일부 정책 설정만 적용 되지 않는 시나리오를 발견 한 경우 다음 사항을 확인 하십시오.

  1. 모든 **BitLocker 설정이 모든 Windows 버전에서 지원 되는 것은 아닙니다**.  
  정책은 장치에 단일 단위로 표시 되므로 일부 설정이 적용 되는 경우 정책 자체를 수신 하는 것을 확신할 수 있습니다. 이 시나리오에서는 장치의 Windows 버전이 문제 설정을 지원 하지 않을 수 있습니다. 각 설정에 대 한 버전 요구 사항에 대 한 자세한 내용은 Windows 설명서의 [BITLOCKER CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) 를 참조 하십시오.  

  1. **BitLocker는 모든 하드웨어에서 지원 되지 않습니다**.  
  올바른 버전의 Windows를 사용 하는 경우에도 기본 장치 하드웨어가 BitLocker 암호화에 대 한 요구 사항을 충족 하지 못할 수 있습니다. Windows 설명서의 https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) BitLocker에 대 한 시스템 요구 사항을 확인할 수 있지만 확인 해야 하는 주요 사항은 장치에 호환 되는 TPM 칩 (1.2 이상)과 TCG(신뢰할 수 있는 컴퓨팅 그룹) (TCG) 규격 BIOS 또는 UEFI 펌웨어가 있는지를 확인 하는 것입니다.

**예제 조사** -Windows 10 장치에 BitLocker 정책을 배포 하 고, **장치 암호화** 설정은 포털에서 **오류** 상태를 표시 합니다.

- 이름에서 알 수 있듯이,이 설정을 사용 하면 관리자가 *BitLocker > 장치 암호화*를 사용 하 여 암호화를 설정 하도록 할 수 있습니다. 앞에서 설명한 문제 해결 팁을 사용 하 여 먼저 MDM 진단 보고서를 확인 합니다. 이 보고서는 장치에 올바른 정책이 배포 되었는지 확인 합니다.

  ![보고서가 장치에 올바른 정책을 배포 했는지 확인 합니다.](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- 또한 레지스트리에서 success를 확인 합니다.

  ![RequiredDeviceEncryption 레지스트리 값이 1을 표시 합니다.](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- 그런 다음 PowerShell을 사용 하 여 TPM의 상태를 확인 하 고 장치에서 TPM을 사용할 수 없는 것을 찾습니다.

  ![PowerShell을 사용 하 여 확인 된 TPM 상태](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- BitLocker는 TPM을 사용 하기 때문에 Intune 또는 정책 문제로 인해 BitLocker가 실패 하지 않고 장치 자체에 TPM 칩이 없거나 BIOS에서 TPM이 사용 하지 않도록 설정 되어 있기 때문입니다.

  추가 팁으로 Windows 이벤트 뷰어의 **응용 프로그램 및 서비스 로그**  > **WINDOWS**  > **BitLocker API**에서 동일한 것을 확인할 수 있습니다. **BITLOCKER API** 이벤트 로그에는 TPM을 사용할 수 없음을 의미 하는 이벤트 ID 853이 있습니다.

  ![이벤트 ID 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > 장치에서 **services.msc** 를 실행 하 여 tpm 상태를 확인할 수도 있습니다.



## <a name="summary"></a>요약

Intune의 BitLocker 정책 문제를 해결 하 고 정책이 의도 된 장치에 도달 하는 것을 확인할 수 있으면 문제가 Intune과 직접적으로 관련 되지 않는다고 가정 하는 것이 안전 합니다. 문제는 Windows OS 또는 하드웨어와 관련 된 문제일 가능성이 높습니다. 이 경우 TPM 구성 또는 UEFI, 보안 부팅 등의 다른 영역을 확인 하기 시작 합니다.

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>다음 단계  

BitLocker로 작업할 때 도움이 될 수 있는 추가 리소스는 다음과 같습니다.

- [BitLocker 제품 설명서](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker 시스템 요구 사항](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker 자주 묻는 질문](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [BitLocker CSP 설명서](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows 암호화 정책 설정](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [AAD/MDM을 사용 하 여 하드웨어 독립적 자동 BitLocker 암호화](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [자동 파일럿 장치에서 BitLocker 암호화에 대 한 CSP 정책](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Intune을 사용 하 여 BitLocker 정책 만들기 및 배포 연습](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)