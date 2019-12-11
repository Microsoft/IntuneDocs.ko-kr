---
title: Microsoft Intune에서 MDM 정책을 사용하여 Windows BIOS 기능 업데이트 - Azure | Microsoft Docs
description: DFCI(디바이스 펌웨어 구성 인터페이스) 프로필을 추가하여 Microsoft Intune에서 Windows 10 디바이스의 CPU, 기본 제공 하드웨어 및 부팅 옵션과 같은 UEFI 설정을 관리합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 38f02d694f1935e4732805f3ae7c66fd9718057a
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74059600"
---
# <a name="use-device-firmware-configuration-interface-profiles-on-windows-devices-in-microsoft-intune-public-preview"></a>Microsoft Intune에서 Windows 디바이스에 디바이스 펌웨어 구성 인터페이스 프로필 사용(공개 미리 보기)

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Intune을 사용하여 Autopilot 디바이스를 관리하는 경우 DFCI(디바이스 펌웨어 구성 인터페이스)를 사용하여 등록된 후 UEFI(BIOS) 설정을 관리할 수 있습니다. 이점, 시나리오 및 필수 구성 요소에 대한 개요는 [DFCI 개요](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Dfci_Feature/)를 참조하세요.

DFCI를 사용하면 [Windows를 통해 Intune에서 UEFI(Unified Extensible Firmware Interface)로 관리 명령을 전달](https://docs.microsoft.com/windows/client-management/mdm/uefi-csp)할 수 있습니다.

Intune에서 이 기능을 사용하여 BIOS 설정을 제어합니다. 일반적으로 펌웨어는 악의적인 공격에 보다 탄력적입니다. 펌웨어는 최종 사용자의 BIOS 제어를 제한하며, 이는 손상된 상황에 적합합니다.

예를 들어 보안 환경에서 Windows 10 디바이스를 사용하고 카메라를 사용하지 않도록 설정하려고 합니다. 펌웨어 계층에서 카메라를 사용하지 않도록 설정할 수 있으므로 최종 사용자가 수행하는 작업은 중요하지 않습니다. OS를 다시 설치하거나 컴퓨터를 초기화하면 카메라가 다시 켜지지 않습니다. 또 다른 예제에서는 사용자가 다른 OS 또는 동일한 보안 기능이 없는 이전 버전의 Windows를 부팅하지 못하도록 부팅 옵션을 잠급니다.

이전 Windows 버전을 다시 설치하거나, 별도의 OS를 설치하거나, 하드 드라이브를 포맷하면 DFCI 관리를 재정의할 수 없습니다. 이 기능을 사용하면 맬웨어가 높은 권한의 OS 프로세스를 포함하여 OS 프로세스와 통신할 수 없습니다. DFCI의 신뢰 체인은 공개 키 암호화를 사용하며 로컬 UEFI(BIOS) 암호 보안에 의존하지 않습니다. 이 보안 계층은 로컬 사용자가 디바이스의 UEFI(BIOS) 메뉴에서 관리형 설정에 액세스하지 못하도록 합니다.

이 기능은 다음에 적용됩니다.

- 지원되는 UEFI의 Windows 10 RS5(1809) 이상

## <a name="before-you-begin"></a>시작하기 전에

- 디바이스 제조업체는 제조 프로세스에서 UEFI 펌웨어에 또는 설치하는 펌웨어 업데이트로 DFCI를 추가해야 합니다. 디바이스 공급업체와 협력하여 [DFCI를 지원하는 공급업체](https://microsoft.github.io/mu/dyn/mu_plus/DfciPkg/Docs/Scenarios/DfciScenarios/#oems-that-support-dfci) 또는 DFCI를 사용하는 데 필요한 펌웨어 버전을 확인합니다.

- 디바이스는 [Microsoft CSP(클라우드 솔루션 공급자) 파트너](https://partner.microsoft.com/cloud-solution-provider)가 Windows Autopilot에 등록하거나 OEM이 직접 등록해야 합니다. 

  [csv 파일에서 가져온](../enrollment/enrollment-autopilot.md#add-devices) Autopilot에 수동으로 등록된 디바이스는 DFCI를 사용할 수 없습니다. 기본적으로 DFCI 관리를 사용하려면 OEM 또는 Windows Autopilot에 대한 Microsoft CSP 파트너 등록을 통해 디바이스의 상용 구매에 대한 외부 증명이 필요합니다.

  디바이스가 등록되면 Windows Autopilot 디바이스 목록에 일련 번호가 표시됩니다.

  모든 요구 사항을 포함하여 Autopilot에 대한 자세한 내용은 [Windows Autopilot을 사용하여 Intune에 Windows 디바이스 등록](../enrollment/enrollment-autopilot.md)을 참조하세요.

## <a name="create-your-azure-ad-security-groups"></a>Azure AD 보안 그룹 만들기

Autopilot 배포 프로필은 Azure AD 보안 그룹에 할당됩니다. DFCI 지원 디바이스를 포함하는 그룹을 만들어야 합니다. DFCI 디바이스의 경우 대부분의 조직에서는 사용자 그룹 대신 디바이스 그룹을 만들 수 있습니다. 다음과 같은 시나리오를 가정해 보겠습니다.

- HR(인사 관리)에는 다양한 Windows 디바이스가 있습니다. 보안상의 이유로 이 그룹의 모든 사용자가 디바이스에서 카메라를 사용할 수 없도록 합니다. 이 시나리오에서는 디바이스 유형과 관계없이 HR 그룹의 사용자에게 정책이 적용되도록 HR 보안 사용자 그룹을 만들 수 있습니다.
- 제조 공간에는 10개의 디바이스가 있습니다. 모든 디바이스에서 USB 디바이스를 통해 디바이스를 부팅하지 못하도록 합니다. 이 시나리오에서는 보안 디바이스 그룹을 만들고 이 10개의 디바이스를 그룹에 추가할 수 있습니다.

Intune에서 그룹을 만드는 방법에 대한 자세한 내용은 [사용자 및 디바이스를 구성하는 그룹 추가](../fundamentals/groups-add.md)를 참조하세요.

## <a name="create-the-profiles"></a>프로필 만들기

DFCI를 사용하려면 다음 프로필을 만들고 그룹에 할당합니다.

### <a name="create-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 만들기

이 프로필은 새 디바이스를 설정하고 미리 구성합니다. [Autopilot 배포 프로필](../enrollment/enrollment-autopilot.md#create-an-autopilot-deployment-profile)에는 프로필을 만드는 단계가 나와 있습니다.

### <a name="create-an-enrollment-state-page-profile"></a>등록 상태 페이지 프로필 만들기

이 프로필을 사용하면 디바이스가 Windows 설치 중에 DFCI에 대해 확인되고 사용하도록 설정됩니다. 모든 앱과 프로필이 설치될 때까지 이 프로필을 사용하여 디바이스 사용을 차단하는 것이 좋습니다. [등록 상태 페이지 프로필](../enrollment/windows-enrollment-status.md)에는 프로필을 만드는 단계가 나와 있습니다.

### <a name="create-the-dfci-profile"></a>DFCI 프로필 만들기

이 프로필에는 사용자가 구성하는 DFCI 설정이 포함됩니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 프로필에 대한 설명이 포함된 이름을 입력합니다. 나중에 쉽게 식별할 수 있도록 정책 이름을 지정합니다. 예를 들어 좋은 프로필 이름은 **Windows: Windows 디바이스에서 DFCI 설정 구성**입니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: **Windows 10 이상**을 선택합니다.
    - **프로필 유형**: **디바이스 펌웨어 구성 인터페이스**를 선택합니다.

4. 설정을 구성합니다.

    - **로컬 사용자가 UEFI(BIOS) 설정을 변경하도록 허용**: 옵션은 다음과 같습니다.
      - **구성되지 않은 설정만**: 로컬 사용자는 Intune에 의해 **사용** 또는 **사용 안 함**으로 명시적으로 설정된 설정을 ‘제외한’ 모든 설정을 변경할 수 있습니다. 
      - **없음**: 로컬 사용자는 DFCI 프로필에 표시되지 않는 설정을 포함하여 모든 UEFI(BIOS) 설정을 변경할 수 없습니다.

    - **CPU 및 IO 가상화**: 옵션은 다음과 같습니다.
        - **구성되지 않음** Intune은 이 기능을 변경하지 않으며 모든 설정을 그대로 유지합니다.
        - **사용**: BIOS는 OS에서 사용할 플랫폼의 CPU 및 IO 가상화 기능을 사용하도록 설정합니다. Windows 가상화 기반 보안 및 Device Guard 기술을 켭니다.
        - **사용 안 함**: BIOS는 플랫폼 CPU 및 IO 가상화 기능을 사용하지 않도록 설정하고 사용되지 않도록 차단합니다.
    - **카메라**: 옵션은 다음과 같습니다.
        - **구성되지 않음** Intune은 이 기능을 변경하지 않으며 모든 설정을 그대로 유지합니다.
        - **사용**: UEFI(BIOS)에서 직접 관리되는 모든 기본 제공 카메라를 사용할 수 있습니다. USB 카메라와 같은 주변 디바이스는 영향을 받지 않습니다.
        - **사용 안 함**: UEFI(BIOS)에서 직접 관리되는 모든 기본 제공 카메라를 사용할 수 없습니다. USB 카메라와 같은 주변 디바이스는 영향을 받지 않습니다.
    - **마이크 및 스피커**:  옵션은 다음과 같습니다.
        - **구성되지 않음** Intune은 이 기능을 변경하지 않으며 모든 설정을 그대로 유지합니다.
        - **사용**: UEFI(BIOS)에서 직접 관리되는 모든 기본 제공 마이크 및 스피커를 사용할 수 있습니다. USB 디바이스와 같은 주변 디바이스는 영향을 받지 않습니다.
        - **사용 안 함**: UEFI(BIOS)에서 직접 관리되는 모든 기본 제공 마이크 및 스피커를 사용할 수 없습니다. USB 디바이스와 같은 주변 디바이스는 영향을 받지 않습니다.
    - **라디오(Bluetooth, Wi-Fi, NFC 등)** : 옵션은 다음과 같습니다.
        - **구성되지 않음** Intune은 이 기능을 변경하지 않으며 모든 설정을 그대로 유지합니다.
        - **사용**: UEFI(BIOS)에서 직접 관리되는 모든 기본 제공 라디오를 사용할 수 있습니다. USB 디바이스와 같은 주변 디바이스는 영향을 받지 않습니다.
        - **사용 안 함**: UEFI(BIOS)에서 직접 관리되는 모든 기본 제공 라디오를 사용할 수 없습니다. USB 디바이스와 같은 주변 디바이스는 영향을 받지 않습니다.

        > [!WARNING]
        > **라디오** 설정을 사용하지 않도록 설정하는 경우에는 디바이스에 유선 네트워크 연결이 필요합니다. 그러지 않으면 디바이스를 관리할 수 없습니다.

    - **외부 미디어(USB, SD)에서 부팅**: 옵션은 다음과 같습니다.
        - **구성되지 않음** Intune은 이 기능을 변경하지 않으며 모든 설정을 그대로 유지합니다.
        - **사용**: UEFI(BIOS)가 하드 드라이브 이외 스토리지에서 부팅하도록 허용합니다.
        - **사용 안 함**: UEFI(BIOS)가 하드 드라이브 이외 스토리지에서 부팅하도록 허용하지 않습니다.
    - **네트워크 어댑터에서 부팅**:  옵션은 다음과 같습니다.
        - **구성되지 않음** Intune은 이 기능을 변경하지 않으며 모든 설정을 그대로 유지합니다.
        - **사용**: UEFI(BIOS)가 기본 제공 네트워크 인터페이스에서 부팅하도록 허용합니다.
        - **사용 안 함**: UEFI(BIOS)가 기본 제공 네트워크 인터페이스에서 부팅하도록 허용하지 않습니다.

5. 작업이 완료되면 **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 프로필이 만들어지고 목록에 표시됩니다.

## <a name="assign-the-profiles-and-reboot"></a>프로필을 할당하고 다시 부팅

프로필이 생성된 후에는 [프로필을 할당할 수 있습니다](../configuration/device-profile-assign.md). DFCI 디바이스를 포함하는 Azure AD 보안 그룹에 프로필을 할당해야 합니다.

디바이스에서 Windows Autopilot을 실행하면 등록 상태 페이지에서 DFCI가 강제로 다시 부팅될 수 있습니다. 이 첫 번째 다시 부팅에서 UEFI가 Intune에 등록됩니다. 

디바이스가 등록되었는지 확인하려면 디바이스를 다시 부팅해야 하지만 필수는 아닙니다. 디바이스 제조업체의 지침을 사용하여 UEFI 메뉴를 열고 UEFI가 이제 관리되고 있는지 확인합니다.

다음번에 디바이스가 Intune과 동기화될 때 Windows는 DFCI 설정을 수신합니다. 디바이스를 다시 부팅합니다. UEFI가 Windows에서 DFCI 설정을 받으려면 이 세 번째 다시 부팅이 필요합니다.

## <a name="update-existing-dfci-settings"></a>기존 DFCI 설정 업데이트

사용 중인 디바이스에서 기존 DFCI 설정을 변경하려면 다음을 수행하면 됩니다. 기존 DFCI 프로필에서 설정을 변경하고 변경 내용을 저장합니다. 프로필이 이미 할당되어 있으므로 다음과 같은 경우 새 DFCI 설정이 적용됩니다.

1. 디바이스가 Intune 서비스에 체크 인하여 프로필 업데이트를 검토합니다. 체크 인은 다양한 시간에 발생합니다. 자세한 내용은 [디바이스가 정책, 프로필 또는 앱 업데이트를 가져오는 경우](../configuration/device-profile-troubleshoot.md#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned)를 참조하세요.

2. 새 설정을 적용하려면 디바이스를 [원격으로](../remote-actions/device-restart.md) 또는 로컬로 다시 부팅합니다.

[체크 인하도록 디바이스에 신호를 보낼](../remote-actions/device-sync.md) 수도 있습니다. 동기화에 성공한 후 [다시 부팅하도록 신호를 보냅니다](../remote-actions/device-restart.md).

>[!NOTE]
> DFCI 프로필을 삭제하거나 프로필에 할당된 그룹에서 디바이스를 제거해도 DFCI 설정이 제거되거나 UEFI(BIOS) 메뉴가 다시 사용하도록 설정되지 않습니다. DFCI 사용을 중지하려면 기존 DFCI 프로필을 업데이트합니다. 단계에 대한 자세한 내용은 이 문서에서 [디바이스 사용 중지](#retire)를 참조하세요.

## <a name="reuse-retire-or-recover-the-device"></a>디바이스 재사용, 사용 중지 또는 복구

### <a name="reuse"></a>재사용

Windows를 초기화하여 디바이스 용도를 변경하려면  [디바이스를 초기화](../remote-actions/devices-wipe.md)합니다. Autopilot 디바이스 레코드를 제거하지 **마세요**.

디바이스를 초기화한 후 새 DFCI 및 Autopilot 프로필이 할당된 그룹으로 디바이스를 이동합니다. Windows 설치를 다시 실행하려면 디바이스를 다시 부팅해야 합니다.

### <a name="retire"></a>사용 중지

디바이스를 사용 중지하고 관리에서 해제할 준비가 되면 DFCI 프로필을 종료 상태에서 원하는 UEFI(BIOS) 설정으로 업데이트합니다. 일반적으로 모든 설정을 사용하도록 설정하려고 합니다. 예를 들면 다음과 같습니다.

1. DFCI 프로필을 엽니다(**디바이스** > **구성 프로필**).
2. **로컬 사용자가 UEFI(BIOS) 설정을 변경하도록 허용**을 **구성되지 않은 설정만**으로 변경합니다.
3. 다른 모든 설정을 **구성되지 않음**으로 설정합니다.
4. 설정을 저장합니다.

이 단계에서는 디바이스의 UEFI(BIOS) 메뉴 잠금을 해제합니다. 값은 프로필과 동일하게 유지되며(**사용** 또는 **사용 안 함**) 다시 기본 OS 값으로 설정되지 않습니다.

이제 디바이스를 초기화할 준비가 되었습니다. 디바이스가 초기화된 후에는 Autopilot 레코드를 삭제합니다. 레코드를 삭제하면 다시 부팅될 때 디바이스가 자동으로 다시 등록되지 않습니다.

### <a name="recover"></a>복구

디바이스를 초기화하고 UEFI(BIOS) 메뉴의 잠금을 해제하기 전에 Autopilot 레코드를 삭제하면 메뉴는 잠긴 상태로 유지됩니다. Intune은 프로필 업데이트를 보내 잠금을 해제할 수 없습니다.

디바이스를 잠금 해제하려면 UEFI(BIOS) 메뉴를 열고 네트워크에서 관리를 새로 고칩니다. 복구 기능으로는 메뉴가 잠금 해제되지만 모든 UEFI(BIOS) 설정이 이전 Intune DFCI 프로필의 값으로 설정됩니다.

## <a name="end-user-impact"></a>최종 사용자 영향

DFCI 정책이 적용되면 UEFI(BIOS) 메뉴가 암호로 보호된 경우에도 로컬 사용자는 DFCI에 의해 구성된 설정을 변경할 수 없습니다. 구성하는 설정에 따라 최종 사용자에게 하드웨어 구성 요소를 찾을 수 없거나 진단할 수 없다는 오류가 표시될 수 있습니다. 사용하지 않도록 설정한 옵션을 설명하는 설명서를 최종 사용자에게 제공해야 합니다.  

## <a name="next-steps"></a>다음 단계

프로필이 할당된 후 [상태를 모니터링합니다](../device-profile-monitor.md).
