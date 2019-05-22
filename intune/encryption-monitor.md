---
title: Microsoft Intune의 암호화 보고서 및 BitLocker 키
titleSuffix: Microsoft Intune
description: Microsoft Intune 포털 내에서 디바이스 암호화 상태 보고서를 살펴보고, BitLocker 복구 키에 액세스할 수 있습니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 52b92483ddafadf460911caaa472825a0bc0a20f
ms.sourcegitcommit: b4483c8476a209de83102e8993d8074dbb323493
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527212"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>BitLocker 및 디바이스 암호화 모니터링  
Azure AD(Azure Active Directory)에서 살펴본 것처럼 Intune은 Windows 10 디바이스의 암호화 상태를 식별하는 중앙 위치를 제공하며, 디바이스에서 BitLocker의 중요 정보에 액세스할 수 있습니다.  

- [암호화 보고서(공개 미리 보기)](#encryption-report)는 디바이스의 암호화 상태 및 준비 상황에 대한 세부 정보를 제공합니다. 보고서 세부 정보를 통해 보호하려는 디바이스의 암호화를 방해하는 문제를 식별할 수 있습니다.  
- Intune 포털 내에서 디바이스의 키 ID나 복구 키 같은 [BitLocker 세부 정보(공개 미리 보기)를 볼 수 있습니다](#bitlocker-recovery-keys).  

## <a name="encryption-report"></a>암호화 보고서
암호화 보고서(공개 미리 보기)를 사용하여 Windows 10 디바이스의 암호화 상태에 대한 세부 정보를 볼 수 있습니다.  

보고서를 찾으려면 [Intune](https://aka.ms/intuneportal)에 로그인하여 **디바이스 구성**으로 이동한 다음, *모니터* 아래에서 **암호화 보고서(미리 보기)** 를 선택합니다.  

### <a name="prerequisites"></a>필수 조건:
암호화 보고서에 표시하려면 디바이스가 Windows 1607 이상 버전을 실행해야 합니다.  

### <a name="report-details"></a>보고서 세부 정보
보고서에는 다음을 포함하여 Windows 10 디바이스의 **디바이스 이름**과 각각에 대한 개략적인 정보가 표시됩니다.  
- **OS 버전** - Windows 버전입니다.  
- **TPM 버전** – 디바이스의 TPM(신뢰할 수 있는 플랫폼 모듈) 버전입니다.  
- **암호화 준비** – BitLocker 암호화를 지원하기 위한 디바이스 준비 상태를 평가합니다. 디바이스를 다음과 같이 식별할 수 있습니다.
  - **준비**: MDM 정책을 사용하여 디바이스를 암호화할 수 있습니다. 이렇게 하려면 디바이스에 TPM이 있어야 하고 다음 Windows 10 버전 및 SKU 요구 사항을 충족해야 합니다.
    - Business, Enterprise, Education 버전 1703 이상
    - Pro 버전 1809 이상  
  
    자세한 내용은 Windows 설명서의 [BitLocker CSP(구성 서비스 공급자)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 참조하세요.  

  - **준비되지 않음**: 디바이스가 완전한 암호화 기능을 갖추고 있진 않지만 여전히 암호화를 지원합니다. 예를 들어 사용자가 수동으로 또는 TMP 없이 암호화를 허용하도록 설정할 수 있는 그룹 정책을 통해 디바이스를 암호화할 수 있습니다.
  - **해당 없음**: 이 디바이스를 분류하는 데 필요한 정보가 충분하지 않습니다.  

- **암호화 상태** – OS 드라이브의 암호화 여부를 나타냅니다.  


### <a name="device-encryption-status"></a>디바이스 암호화 상태
디바이스를 선택하면 Intune은 **디바이스 암호화 상태** 창을 표시합니다.

이 창에는 다음과 같은 세부 정보가 표시됩니다.  
- **디바이스 이름** - 보고 있는 디바이스의 이름입니다.  
- **암호화 준비** – BitLocker 암호화를 지원하기 위한 디바이스 준비 상태를 평가합니다. 디바이스의 암호화 준비 상태가 *준비되지 않음*이라도 TPM이 없으므로 암호화 상태가 *암호화됨*일 수 있습니다. (자세한 내용은 이전 섹션의 암호화 준비를 참조하세요.)
- **암호화 상태** – OS 드라이브의 암호화 여부를 나타냅니다.  
- **프로필** – 이 디바이스에 적용되는 *디바이스 구성* 프로필 목록으로, 다음과 같은 프로필 유형 및 설정을 포함하고 있습니다.  
  - 프로필 유형 = *엔드포인트 보호*  
  - 설정 > Windows 암호화 > 디바이스 암호화 = *필요*  

  프로필 상태 요약에 문제가 있는 것으로 나타나면 이 목록을 사용하여 검토할 개별 정책을 찾을 수 있습니다.  

- **프로파일링 상태 요약** – 이 디바이스에 적용되는 프로필의 요약 정보입니다. 이 요약 정보는 해당하는 모든 프로필 중에서 가장 덜 우호적인 조건을 표시합니다. 예를 들어 한 프로필에서 오류가 발생하면 프로필 상태 요약에 *오류*로 표시됩니다.  
- **상태 세부 정보** – 디바이스의 암호화 상태에 대한 고급 정보입니다. 
  > [!NOTE]  
  > Intune은 *Windows 10 2019년 4월 업데이트* 이상을 실행하는 디바이스의 *상태 세부 정보*만 보여줍니다.
  
  이 필드는 검색할 수 있는 각 해당 오류의 정보를 표시합니다. 이 정보를 사용하여 디바이스가 암호화 준비 상태가 아닌 이유를 이해할 수 있습니다.  

  다음은 Intune이 보고할 수 있는 상태 세부 정보의 예입니다.  

   - BitLocker 정책은 사용자 동의가 있어야만 BitLocker 드라이브 암호화 마법사를 시작하여 OS 볼륨 암호화를 시작할 수 있지만, 사용자가 동의하지 않았습니다.  
   - OS 볼륨의 암호화 방법이 BitLocker 정책과 일치하지 않습니다.  
   - 정책 BitLocker는 OS 볼륨을 보호할 TPM 보호기가 필요하지만, TPM이 사용되고 있지 않습니다.  
   - BitLocker 정책은 OS 볼륨에 대한 TPM 전용 보호기가 필요하지만, TPM 보호가 사용되고 있지 않습니다.  
   - BitLocker 정책은 OS 볼륨에 대한 TPM+PIN 보호가 필요하지만, TPM+PIN 보호기가 사용되고 있지 않습니다.  
   - BitLocker 정책은 OS 볼륨에 대한 TPM+시작 키 보호가 필요하지만, TPM+시작 키 보호기가 사용되고 있지 않습니다.  
   - BitLocker 정책은 OS 볼륨에 대한 TPM+PIN+시작 키 보호가 필요하지만, TPM+PIN+시작 키 보호기가 사용되고 있지 않습니다.  
   - OS 볼륨이 보호되고 있지 않습니다.  
   - 복구 키를 백업하지 못했습니다.  
   - 고정 드라이브가 보호되고 있지 않습니다.  
   - 고정 드라이브의 암호화 방법이 BitLocker 정책과 일치하지 않습니다.  
   - 드라이브를 암호화하려면 BitLocker 정책에 따라 사용자가 관리자로 로그인해야 하거나, 디바이스가 Azure AD에 조인된 경우 AllowStandardUserEncryption 정책을 1로 설정해야 합니다.  
   - WinRE(Windows Recovery Environment)가 구성되지 않았습니다.  
   - TPM이 없어서 레지스트리에서 사용할 수 없거나 OS가가 이동식 드라이브에 있어서 BitLocker에 TPM을 사용할 수 없습니다.  
   - TPM을 BitLocker에 사용할 준비가 되지 않았습니다.  
   - 복구 키 백업에 필요한 네트워크를 사용할 수 없습니다.다.  

## <a name="bitlocker-recovery-keys"></a>BitLocker 복구 키
현재 공개 미리 보기인 Intune은 Intune 포털 내에서 Windows 10 디바이스의 BitLocker 키 ID와 복구 키를 볼 수 있도록 BitLocker의 Azure AD 블레이드에 대한 액세스를 제공합니다.  디바이스에 액세스하려면 디바이스의 키를 Azure AD에 위탁해야 합니다. 
1. [Intune](https://aka.ms/intuneportal)에 로그인하여 **디바이스**로 이동한 다음, *관리* 아래에서 **모든 디바이스**를 선택합니다.
2. 목록에서 디바이스를 선택한 다음, *모니터* 아래에서 **복구 키 – 미리 보기**를 선택합니다.  
  
키를 Azure AD에서 사용할 수 있는 경우 다음 정보를 사용할 수 있습니다.
- BitLocker 키 ID
- BitLocker 복구 키
- 드라이브 유형  

키가 Azure AD에 없는 경우 Intune은 *이 디바이스에 대한 BitLocker 키를 찾을 수 없음* 메시지를 표시합니다.  

BitLocker에 대한 정보는 [BitLocker CSP(구성 서비스 공급자)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)를 사용하여 획득합니다. BitLocker CSP는 Windows 10 버전 1703 이상 및 Windows 10 Pro 1809 이상 버전에서 지원됩니다. 

## <a name="next-steps"></a>다음 단계
Windows 10 디바이스에 대한 [디바이스 규정 준수](compliance-policy-create-windows.md) 정책을 만들어서 BitLocker 및 암호화를 구성합니다.
