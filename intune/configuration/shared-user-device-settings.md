---
title: Microsoft Intune에서 공유 또는 다중 사용자 디바이스 설정 | Microsoft Docs
description: Microsoft Intune에서 여러 사용자에 의해 공유되거나 사용되는 Windows 10 및 Windows Holographic for Business 디바이스를 추가하고 사용합니다. 모든 설정의 목록 및 Microsoft HoloLens를 비롯한 디바이스에서의 용도를 확인합니다. 게스트 계정 제어, 계정 관리 및 비활성 계정 삭제, 로컬 스토리지에 저장 허용 또는 금지, 전원 설정 및 절전 모드 옵션, 업데이트가 설치되는 시기 선택 및 디바이스 구성 프로필의 교육 환경에서 디바이스 사용
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a04d5c4316a12e16a648784d12c20ce09ac8b6b
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059286"
---
# <a name="control-access-accounts-and-power-features-on-shared-pc-or-multi-user-devices-using-intune"></a>Intune을 사용하여 공유 PC 또는 다중 사용자 디바이스에서 액세스, 계정 및 전원 기능 제어

다중 사용자가 있는 디바이스는 공유 디바이스라고 하며 MDM(모바일 디바이스 관리) 솔루션의 일반적인 부분입니다. Microsoft Intune을 사용하여 다음 플랫폼을 실행하는 공유 디바이스를 사용자 지정할 수 있습니다.

- Windows 10 Professional 이상
- Windows 10 Enterprise 이상
- Windows Holographic for Business(예: HoloLens)

예를 들어 학교는 다수의 학생에 의해 일반적으로 사용되는 디바이스를 보유합니다. 이 설정을 사용하여 학교 Intune 관리자는 한 번에 한 명의 사용자를 허용하도록 공유 PC 기능을 설정할 수 있습니다. 학생은 디바이스에서 다른 로그인 계정 간에 전환할 수 없습니다. 학생이 로그아웃하는 경우 모든 사용자별 설정을 제거하도록 선택합니다.

최종 사용자는 게스트 계정을 사용하여 이러한 공유 디바이스에 로그인할 수 있습니다. 사용자가 로그인한 후 자격 증명이 캐시됩니다. 디바이스를 사용하므로 최종 사용자는 허용하는 기능에 대한 액세스만을 얻습니다. 예를 들어 디바이스가 절전 모드로 전환되는 경우 사용자가 파일을 로컬로 보고 저장할 수 있는지 여부를 선택하고, 전원 관리 설정 등을 활성화 또는 비활성화합니다. 또한 사용자가 로그아웃하는 경우 게스트 계정을 삭제하거나 임계값에 도달하는 경우 비활성 계정을 삭제할지 여부를 제어합니다.

이 문서에서는 구성 프로필을 만드는 방법을 보여주며, 해당 설명이 포함된 사용 가능한 설정에 대한 링크를 포함합니다.

프로필이 Intune에서 생성될 때 조직의 디바이스 그룹에 프로필을 배포하거나 할당합니다. 또한 혼합된 디바이스 유형과 OS(운영 체제) 버전을 사용하여 디바이스 그룹에 이 프로필을 할당할 수도 있습니다.

## <a name="create-the-profile"></a>프로필 만들기

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
2. **디바이스 구성** > **구성 프로필** > **프로필 만들기**를 선택합니다.
3. 다음 속성을 입력합니다.

   - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다.
   - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
   - **플랫폼**: **Windows 10 이상**을 선택합니다.
   - **프로필 유형**: **다중 사용자 디바이스 공유**를 선택합니다.

4. [Windows 10 이상](shared-user-device-settings-windows.md) 또는 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md)에 대한 설정을 구성합니다.

5. **확인** > **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 목록에 표시되지만 아직 아무것도 하지 않습니다. 조직의 디바이스 그룹에 [프로필을 할당](device-profile-assign.md)해야 합니다.

## <a name="next-steps"></a>다음 단계

- [Windows 10 이상](shared-user-device-settings-windows.md) 또는 [Windows Holographic for Business](shared-user-device-settings-windows-holographic.md)에 대한 모든 설정을 확인합니다.
- [프로필을 할당](device-profile-assign.md)하고, 해당 [상태를 모니터링](device-profile-monitor.md)합니다.
