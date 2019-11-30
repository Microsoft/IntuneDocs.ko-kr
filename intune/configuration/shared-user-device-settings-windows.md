---
title: Windows 10 공유 디바이스 설정 - Microsoft Intune - Azure | Microsoft Docs
description: Microsoft Intune에서 여러 사용자에 의해 공유되거나 사용되는 디바이스를 구성하도록 Windows 10을 추가하고 사용합니다. 모든 설정의 목록 및 Microsoft Surface를 비롯한 디바이스에서의 용도를 확인합니다. 게스트 계정 제어, 계정 관리 및 비활성 계정 삭제, 로컬 스토리지에 저장 허용 또는 금지, 전원 설정 및 절전 모드 옵션, 업데이트가 설치되는 시기 선택 및 디바이스 구성 프로필의 교육 환경에서 디바이스 사용
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/01/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0e59a4ba7a929df448eddaf36038c2d6deaa0a7a
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547926"
---
# <a name="windows-10-and-later-settings-to-manage-shared-devices-using-intune"></a>Intune을 사용하여 공유 디바이스를 관리하기 위한 Windows 10 이상 설정

Microsoft Surface와 같은 Windows 10 이상 디바이스를 다수의 사용자가 사용할 수 있습니다. 다중 사용자가 있는 디바이스는 공유 디바이스라고 하며 MDM(모바일 디바이스 관리) 솔루션의 일부입니다.

Microsoft Intune을 사용하여 최종 사용자는 게스트 계정으로 이러한 공유 디바이스에 로그인할 수 있습니다. 디바이스를 사용하므로 사용자는 허용하는 기능에 대한 액세스만을 얻습니다. Intune 관리자로서 공유 Windows 10 디바이스에 대한 액세스를 구성하고, 계정이 삭제되는 시기를 선택하고, 전원 관리 설정을 제어하는 등의 작업을 수행합니다.

이 문서에서는 Windows 10(이상) 디바이스 구성 프로필에서 사용하는 설정을 나열하고 설명합니다. 프로필이 Intune에서 생성될 때 조직의 디바이스 그룹에 프로필을 배포하거나 할당합니다. 또한 혼합된 디바이스 유형과 OS 버전을 사용하여 디바이스 그룹에 이 프로필을 할당할 수도 있습니다.

Intune의 이 기능에 대한 자세한 내용은 [공유 PC 또는 다중 사용자 디바이스에서 액세스, 계정 및 전원 기능 제어](shared-user-device-settings.md)를 참조하세요. Windows CSP에 대한 자세한 내용은 [SharedPC CSP](https://docs.microsoft.com/windows/client-management/mdm/sharedpc-csp)를 참조하세요.

## <a name="before-your-begin"></a>시작하기 전에

[프로필을 만듭니다](shared-user-device-settings.md).

## <a name="shared-multi-user-device-settings"></a>다중 사용자 디바이스 공유 설정

- **공유 PC 모드**: **사용**을 선택하여 공유 PC 모드를 켭니다. 이 모드에서는 한 번에 하나의 사용자만 디바이스에 로그인합니다. 첫 번째 사용자가 로그아웃할 때까지 다른 사용자는 로그인할 수 없습니다. **구성되지 않음**(기본값)은 이 설정을 Intune에서 관리되지 않는 상태로 유지하고, 디바이스에서 이 설정을 제어하는 모든 정책을 푸시하지 않습니다.
- **게스트 계정**: 로그인 화면에서 게스트 옵션을 만들도록 선택합니다. 게스트 계정은 사용자 자격 증명 또는 인증이 필요하지 않습니다. 이 설정은 사용될 때마다 새 로컬 계정을 만듭니다. 옵션은 다음과 같습니다.
  - **게스트**: 디바이스에 게스트 계정을 로컬로 만듭니다.
  - **도메인**: Azure AD(Active Directory)에 게스트 계정을 만듭니다.
  - **게스트 및 도메인**: 디바이스 및 Azure AD(Active Directory)에 게스트 계정을 로컬로 만듭니다.
- **계정 관리**: **사용**으로 설정하여 게스트가 만든 로컬 계정과 AD 및 Azure AD의 계정을 자동으로 삭제합니다. 사용자가 디바이스에서 로그아웃하거나 시스템 유지 관리가 실행될 때 이러한 계정이 삭제됩니다. 활성화되는 경우 다음도 설정합니다.
  - **계정 삭제**: 계정 삭제 시기 선택: **스토리지 공간 임계값 도달 시**, **스토리지 공간 임계값 및 비활성 임계값 도달 시** 또는 **로그아웃 후 즉시**. 또한 다음을 입력합니다.
    - **임계값(%) 삭제 시작**: 디스크 공간의 백분율(0-100)을 입력합니다. 총 디스크/스토리지 공간이 입력한 값 아래로 떨어지는 경우 캐시된 계정이 삭제됩니다. 지속적으로 계정을 삭제하여 디스크 공간을 확보합니다. 활성화되지 않은 가장 긴 계정은 먼저 삭제됩니다.
    - **임계값(%) 삭제 중지**: 디스크 공간의 백분율(0-100)을 입력합니다. 총 디스크/스토리지 공간이 입력한 값을 충족하는 경우 삭제가 중지됩니다.

  **사용하지 않음**으로 설정하여 게스트가 만든 로컬, AD 및 Azure AD 계정을 유지합니다.

- **로컬 스토리지**: **사용**을 선택하여 사용자가 디바이스의 하드 드라이브에 있는 파일을 저장하고 보지 못하도록 합니다. **사용 안 함**을 선택하여 사용자가 파일 탐색기를 사용하여 파일을 로컬로 보고 저장할 수 있도록 합니다. **구성되지 않음**(기본값)은 이 설정을 Intune에서 관리되지 않는 상태로 유지하고, 디바이스에서 이 설정을 제어하는 모든 정책을 푸시하지 않습니다.
- **전원 정책**: **사용**으로 설정하면 사용자는 최대 절전 모드를 해제할 수 없으며, 모든 대기 작업(예: 덮개 닫기)을 재정의할 수 없고, 전원 설정을 변경할 수 없습니다. **사용 안 함**으로 설정하면 사용자는 디바이스를 최대 절전 모드로 전환할 수 있으며, 덮개를 닫아 디바이스를 절전 모드로 전환할 수 있고, 전원 설정을 변경할 수 있습니다. **구성되지 않음**(기본값)은 이 설정을 Intune에서 관리되지 않는 상태로 유지하고, 디바이스에서 이 설정을 제어하는 모든 정책을 푸시하지 않습니다.
- **절전 모드 시간 제한(초)** : 디바이스가 절전 모드로 전환되기 전에 비활성 시간(초)(0-100)의 수를 입력합니다. 시간을 설정하지 않으면 디바이스는 60분 후 절전 모드로 전환합니다.
- **PC 절전 모드 해제시 로그인**: **사용**으로 설정하여 디바이스가 절전 모드에서 해제되면 사용자가 암호를 사용하여 로그인하도록 합니다. **사용 안 함**을 선택하면 사용자는 자신의 사용자 이름과 암호를 입력하지 않아도 됩니다. **구성되지 않음**(기본값)은 이 설정을 Intune에서 관리되지 않는 상태로 유지하고, 디바이스에서 이 설정을 제어하는 모든 정책을 푸시하지 않습니다.
- **유지 관리 시작 시간(자정 기준 분 단위)** : Windows 업데이트와 같은 자동 유지 관리 작업을 실행할 시간(분)(0-1440)을 입력합니다. 기본 시작 시간은 자정 또는 0(`0`)분입니다. 자정을 기준으로 분 단위로 시작 시간을 입력하여 시작 시간을 변경합니다. 예를 들어 오전 2시에 유지 관리를 시작하려는 경우 `120`을 입력합니다. 오후 8시에 유지 관리를 시작하려는 경우 `1200`을 입력합니다.
- **교육 정책**: **사용**을 선택하여 보다 제한적인 학교에서 사용되는 디바이스에 대한 권장 설정을 사용합니다. **사용 안 함**을 선택하면 기본 및 권장되는 교육 정책이 사용되지 않습니다. **구성되지 않음**(기본값)은 이 설정을 Intune에서 관리되지 않는 상태로 유지하고, 디바이스에서 이 설정을 제어하는 모든 정책을 푸시하지 않습니다.

  교육 정책이 수행하는 작업에 대한 자세한 내용은 [교육 고객에 대한 Windows 10 구성 권장 사항](https://docs.microsoft.com/education/windows/configure-windows-for-education)을 참조하세요.

> [!TIP]
> [공유 또는 게스트 PC 설정](https://docs.microsoft.com/windows/configuration/set-up-shared-or-guest-pc)(다른 문서 웹 사이트 열기)은 공유 모드에서 설정할 수 있는 개념 및 그룹 정책을 포함하여 이 Windows 10 기능에서 중요한 리소스입니다.

## <a name="next-steps"></a>다음 단계

- [프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
- [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md)에 대한 설정을 참조하세요.
