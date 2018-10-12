---
title: Microsoft Intune을 사용하여 Windows 10 장치에서 S 모드 업그레이드 또는 사용 - Azure | Microsoft Docs
description: Microsoft Intune에서 장치 프로필을 만들어 Windows 10 장치를 다른 버전으로 업그레이드합니다. 예를 들어 Windows 10 Professional에서 Windows 10 Enterprise로 업그레이드할 수 있습니다. 또한 구성 프로필을 사용하여 장치에서 S 모드를 사용하도록 설정하거나 전환할 수 있습니다. Windows 10 Pro, N 버전, 교육, 클라우드, Enterprise, Core, Holographic 및 모바일에 대해 지원되는 업그레이드 경로를 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 09/11/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: f0e4ba42559a068ebefb453aba18060803dc36e0
ms.sourcegitcommit: f3974c810e172f345853dacd7f2ca0abc11b1a5b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44389628"
---
# <a name="use-a-configuration-profile-to-upgrade-windows-10-or-switch-from-s-mode-in-intune"></a>Intune에서 구성 프로필을 사용하여 Windows 10 업그레이드 또는 S 모드로부터 전환
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10 버전을 실행하는 장치를 다른 버전으로 자동으로 업그레이드하려면 Intune에서 업그레이드 프로필을 구성합니다. 또한 지원되는 업그레이드 경로를 참조합니다.

## <a name="before-you-begin"></a>시작하기 전에
장치를 최신 버전으로 업그레이드하기 전에 요구되는 필수 조건은 다음과 같습니다.

- Windows 10 Desktop 버전용 정책에서 대상으로 하는 모든 장치에 업데이트된 버전의 Windows를 설치하는 데 유효한 제품 키입니다. MAK(다중 정품 인증 키) 또는 KMS(키 관리 서버) 키 둘 중 하나를 사용할 수 있습니다. Windows 10 Mobile 및 Windows 10 Holographic 버전의 경우 라이선스 정보가 포함된 Microsoft 라이선스 파일을 사용하여 정책으로 대상을 지정하는 모든 장치에 업데이트된 Windows 버전을 설치할 수 있습니다.
- 정책을 할당한 Windows 10 장치를 Microsoft Intune에 등록합니다. Intune PC 클라이언트 소프트웨어를 실행하는 PC에는 버전 업그레이드 정책을 사용할 수 없습니다.

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


<!-- Testing a new table on 3/5/18 

The following lists provide the supported upgrade paths for the Windows 10 edition upgrade profile. The Windows 10 edition to upgrade to is in bold followed by the list of supported editions that you can upgrade from:

**Windows 10 Education**
- Windows 10 Pro
- Windows 10 Pro Education
- Windows 10 Cloud
- Windows 10 Enterprise
- Windows 10 Core
    
**Windows 10 Education N edition**    
- Windows 10 Pro N edition
- Windows 10 Pro Education N edition
- Windows 10 Cloud N edition
- Windows 10 Enterprise N edition
- Windows 10 Core N edition
    
**Windows 10 Enterprise**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Enterprise N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition
    
**Windows 10 Pro**
- Windows 10 Cloud
    
**Windows 10 Pro N edition**
- Windows 10 Cloud N edition
    
**Windows 10 Pro Education**
- Windows 10 Pro
- Windows 10 Cloud
- Windows 10 Core
    
**Windows 10 Pro Education N edition**
- Windows 10 Pro N edition
- Windows 10 Cloud N edition
- Windows 10 Core N edition

**Windows 10 Holographic for Business**
- Windows 10 Holographic

**Windows 10 Mobile Enterprise**
- Windows 10 Mobile -->

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

## <a name="upgrade-the-edition"></a>버전 업그레이드

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.
3. 프로필에 대한 **이름**과 **설명**을 입력합니다. 예를 들어 `Windows 10 edition upgrade`와 같이 입력합니다.
4. **플랫폼**에 대해 **Windows 10 이상**을 선택합니다.
5. **프로필 유형**에 대해 **버전 업그레이드**를 선택합니다.
6. **버전 업그레이드** 속성에서 다음 설정을 입력합니다.

   - **업그레이드할 대상 버전**: 업그레이드하려는 Windows 10 버전을 선택합니다. 이 정책의 대상 장치가 선택한 버전으로 업그레이드됩니다.
   - **제품 키**: Microsoft에서 받은 제품 키를 입력합니다. 제품 키를 사용하여 정책이 만들어진 경우 이 키는 업데이트할 수 없으며 보안상의 이유로 숨겨져 있습니다. 제품 키를 변경하려면 전체 키를 다시 입력합니다.
   - **라이선스 파일**: **Windows 10 Holographic for Business** 또는 **Windows 10 Mobile 버전**의 경우 **찾아보기**를 선택하여 Microsoft에서 받은 라이선스 파일을 선택합니다. 이 라이선스 파일에는 대상 장치를 업그레이드하려는 버전의 라이선스 정보가 포함되어 있습니다.

7. **확인**을 선택하여 변경 내용을 저장합니다. **만들기**를 선택하여 프로필을 만듭니다.

## <a name="switch-out-of-s-mode"></a>S 모드로부터 전환

[Windows 10 S 모드](https://support.microsoft.com/help/4456067/windows-10-switch-out-of-s-mode)는 보안 및 성능을 위해 설계되었습니다. 장치에서 Microsoft Store의 앱만 실행하는 경우 S 모드를 사용하여 장치를 안전하게 유지할 수 있습니다. Microsoft Store에서 사용할 수 없는 응용 프로그램이 장치에 필요한 경우 S 모드에서 전환합니다. S 모드로부터 전환하는 것도 한 가지 방법입니다. 그리고 S 모드로부터 전환하면 Windows 10 S 모드로 돌아갈 수 없습니다.

다음 단계에서는 Windows 10(1809 이상) 장치에서 S 모드를 제어하는 프로필을 만드는 방법을 보여 줍니다.

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**을 기준으로 필터링한 다음 **Microsoft Intune**을 선택합니다.
2. **장치 구성** > **프로필** > **프로필 만들기**를 차례로 선택합니다.
3. 프로필에 대한 **이름**과 **설명**을 입력합니다. 예를 들어 `Windows 10 switch off S mode`와 같이 입력합니다.
4. **플랫폼**에 대해 **Windows 10 이상**을 선택합니다.
5. **프로필 유형**에 대해 **버전 업그레이드**를 선택합니다.
6. **모드 전환(Windows 참가자만)** 을 선택하고 **S 모드로부터 전환** 속성을 설정합니다. 옵션은 다음과 같습니다.

    - **구성 없음**: S 모드 장치가 S 모드로 유지됩니다. 최종 사용자는 S 모드로부터 장치를 전환할 수 있습니다.
    - **S 모드로 유지**: 최종 사용자가 S 모드에서 장치를 전환할 수 없도록 설정합니다.
    - **전환**: S 모드로부터 장치를 전환합니다.

7. **확인**을 선택하여 변경 내용을 저장합니다. **만들기**를 선택하여 프로필을 만듭니다.

프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

그룹에 [이 프로필을 할당](device-profile-assign.md)합니다.

>[!NOTE]
>나중에 정책 할당을 제거하더라도 장치의 Windows 버전을 되돌리지 않고 계속 정상적으로 작동합니다.
