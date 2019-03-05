---
title: Windows 10 디바이스에서 S 모드 업그레이드 또는 사용 - Microsoft Intune - Azure | Microsoft Docs
description: Microsoft Intune을 사용하여 Windows 10 디바이스를 다른 버전으로 업그레이드하거나 S 모드를 사용하도록 설정합니다. 관리자는 디바이스 구성 프로필을 사용하여 Windows 10 Professional을 Windows 10 Enterprise로 업그레이드하고 S 모드를 활성화 또는 전환할 수 있습니다. Windows 10 Pro, N 버전, 교육, 클라우드, Enterprise, Core, Holographic 및 모바일에 대해 지원되는 업그레이드 경로를 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26a8718247142ef2ed3f509dc185207b1e99e82f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233324"
---
# <a name="upgrade-windows-10-editions-or-enable-s-mode-on-devices-using-microsoft-intune"></a>Windows 10 버전을 업그레이드하거나 Microsoft Intune을 사용하여 디바이스에서 S 모드 사용

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

MDM(모바일 디바이스 관리) 솔루션의 일부로, Windows 10 디바이스를 업그레이드할 수 있습니다. 예를 들어 Windows 10 Professional 디바이스를 Windows 10 Enterprise로 업그레이드하려고 합니다. 또는 S 모바일을 사용하도록 설정하면 디바이스가 Microsoft Store 앱만 실행합니다.

[Windows 10 S 모드](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)는 보안 및 성능을 위해 설계되었습니다. 디바이스에서 Microsoft Store의 앱만 실행하는 경우 S 모드를 사용하여 디바이스를 안전하게 유지할 수 있습니다. 디바이스가 Microsoft Store에서 사용할 수 없는 애플리케이션을 사용하는 경우 S 모드에서 전환합니다. S 모드로부터 전환하는 것도 한 가지 방법입니다. 그리고 S 모드로부터 전환하면 Windows 10 S 모드로 돌아갈 수 없습니다.

이 기능은 다음에 적용됩니다.

- Windows 10 이상
- S 모드용 Windows 10 1809 이상
- Windows Holographic for Business

이러한 기능은 Intune에서 사용할 수 있으며 관리자가 구성할 수 있습니다. Intune은 "구성 프로필"을 사용하여 조직의 요구 사항에 맞게 이러한 설정을 만들고 사용자 지정합니다. 프로필에 이러한 기능을 추가한 후 해당 프로필을 조직의 Windows 10 디바이스에 푸시하거나 배포할 수 있습니다. 프로필을 배포할 때 Intune이 자동으로 디바이스를 업그레이드하거나 S 모드를 사용하도록 설정합니다.

이 문서에서는 지원되는 업그레이드 경로를 나열하고 디바이스 구성 프로필을 만드는 방법을 보여줍니다. [Windows 10](edition-upgrade-windows-settings.md)에 대해 사용 가능한 모든 업그레이드 및 S 모드 설정을 볼 수도 있습니다.

> [!NOTE]
> 나중에 정책 할당을 제거하면 디바이스의 Windows 버전이 되돌려지지 않습니다. 다바이스는 계속 정상적으로 실행됩니다.

## <a name="prerequisites"></a>전제 조건

디바이스를 업그레이드하기 전에 다음 전제 조건이 충족되었는지 확인합니다.

- Windows 10 Desktop 버전용 정책에서 대상으로 하는 모든 디바이스에 업데이트된 버전의 Windows를 설치하는 데 유효한 제품 키입니다. MAK(다중 정품 인증 키) 또는 KMS(키 관리 서버) 키 둘 중 하나를 사용할 수 있습니다.
- Windows 10 Mobile 및 Windows 10 Holographic 버전의 경우 Microsoft 라이선스 파일을 사용할 수 있습니다. 라이선스 파일에는 정책으로 대상을 지정하는 모든 디바이스에 업데이트된 버전을 설치하기 위한 라이선스 정보가 포함되어 있습니다.
- 정책을 할당한 Windows 10 디바이스를 Microsoft Intune에 등록합니다. Intune PC 클라이언트 소프트웨어를 실행하는 PC에는 버전 업그레이드 정책을 사용할 수 없습니다.

## <a name="supported-upgrade-paths"></a>지원되는 업그레이드 경로

다음 테이블은 Windows 10 버전 업그레이드 프로필에 대해 지원되는 업그레이드 경로 목록입니다.

| 다음 버전에서 업그레이드 | 다음 버전으로 업그레이드 |
|---|---|
| Windows 10 Pro | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education |
| Windows 10 Pro N 버전 | Windows 10 Education N 버전 <br/>Windows 10 Enterprise N 버전 <br/>Windows 10 Pro Education N 버전 | 
| Windows 10 Pro Education | Windows 10 Education | 
| Windows 10 Pro Education N 버전 | Windows 10 Education N 버전 |
| Windows 10 Cloud | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro <br/>Windows 10 Pro Education | 
| Windows 10 Cloud N 버전 | Windows 10 Education N 버전 <br/>Windows 10 Enterprise N 버전 <br/>Windows 10 Pro N 버전 <br/>Windows 10 Pro Education N 버전 | 
| Windows 10 Enterprise | Windows 10 Education | 
| Windows 10 Enterprise N 버전 | Windows 10 Education N 버전 | 
| Windows 10 Core | Windows 10 Education <br/>Windows 10 Enterprise <br/>Windows 10 Pro Education | 
| Windows 10 Core N 버전 | Windows 10 Education N 버전 <br/>Windows 10 Enterprise N 버전 <br/>Windows 10 Pro Education N 버전 | 
| Windows 10 Holographic | Windows 10 Holographic for Business |
| Windows 10 Mobile | Windows 10 Mobile Enterprise |

<!--The following table provides information about the supported upgrade paths for Windows 10 editions in this policy:

![supported](./media/check_grn.png)  (X) = not supported    
![unsupported](./media/x_blk.png)    (green checkmark) = supported    

|Upgrade from edition\Upgrade to edition|Education|Education N|Pro Education|Pro Education N|Enterprise|Enterprise N|Professional|Professional N|Mobile Enterprise|Holographic for Business|
|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|--------|
|Pro|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Pro Education N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Cloud N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Enterprise N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)   |![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Core N|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|
|Mobile|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png)|![unsupported](./media/x_blk.png)|
|Holographic|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![unsupported](./media/x_blk.png)|![supported](./media/check_grn.png) -->

## <a name="create-the-profile"></a>프로필 만들기

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 > **Intune**을 기준으로 필터링하고 > **Intune**을 선택합니다.
2. **디바이스 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.
3. 다음 속성을 입력합니다.

    - **이름**: 새 프로필에 대한 설명이 포함된 이름을 입력합니다. 예를 들어 `Windows 10 edition upgrade profile` 또는 `Windows 10 switch off S mode`와 같이 입력합니다.
    - **설명**: 프로필에 대한 설명을 입력합니다. 이 설정은 선택 사항이지만 권장됩니다.
    - **플랫폼**: 플랫폼 선택:  

        - **Windows 10 이상**

    - **프로필 유형**: **버전 업그레이드**를 선택합니다.
    - **설정**: 구성할 설정을 입력합니다. 모든 설정 목록 및 수행할 작업은 다음을 참조하세요.

        - [Windows 10 업그레이드 및 S 모드](edition-upgrade-windows-settings.md)
        - [Windows Holographic for Business](holographic-upgrade.md)

4. **확인** > **만들기**를 선택하여 변경 내용을 저장합니다. 

프로필이 만들어지고 목록에 표시됩니다. [프로필을 할당](device-profile-assign.md)하고 [해당 상태를 모니터링](device-profile-monitor.md)합니다.

## <a name="next-steps"></a>다음 단계

프로필이 생성된 후에는 이를 할당할 수 있습니다. 다음으로, [프로필을 할당](device-profile-assign.md)하고, [해당 상태를 모니터링](device-profile-monitor.md)합니다.

[Windows 10](edition-upgrade-windows-settings.md) 또는 [Windows Holographic for Business](holographic-upgrade.md)에 대한 업그레이드 및 S 모드 설정을 봅니다.
