---
title: Microsoft Intune-Azure를 사용한 Windows 10 장치 업그레이드 | Microsoft Docs
description: Windows 10 장치를 최신 버전으로 업그레이드하려면 Microsoft Intune에서 장치 프로필을 만듭니다. Windows 10 Pro, N 버전, 교육, 클라우드, Enterprise, Core, Holographic 및 모바일에 대해 지원되는 업그레이드 경로를 참조하세요.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ae8b6528-7979-47d8-abe0-58cea1905270
ms.reviewer: coryfe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 994ab8e7d955d18b293e4d9e9661e0c44baaaa1f
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025436"
---
# <a name="configure-windows-10-edition-upgrade-profile-in-intune"></a>Intune에서 Windows 10 버전 업그레이드 설정 구성
[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows 10 버전을 실행하는 장치를 다른 버전으로 자동으로 업그레이드하려면 Intune에서 업그레이드 프로필을 구성합니다. 또한 지원되는 업그레이드 경로를 참조합니다.

## <a name="before-you-begin"></a>시작하기 전에
장치를 최신 버전으로 업그레이드하기 전에 다음 중 하나가 있어야 합니다.

- Windows 10 Desktop 버전용 정책에서 대상으로 하는 모든 장치에 업데이트된 버전의 Windows를 설치하는 데 유효한 제품 키입니다. 정책에서 대상으로 하는 모든 장치에 업데이트된 버전의 Windows를 설치하기 위한 라이선스 정보가 포함된 Microsoft의 라이선스 파일 또는 KMS(Key Management Server) 또는 MAK(Multiple Activation Keys)를 사용할 수 있습니다(Windows 10 Mobile 및 Windows 10 Holographic 버전용).
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

## <a name="create-a-device-profile-containing-device-restriction-settings"></a>장치 제한 설정을 포함하는 장치 프로필 만들기
1. 로그인은 [Azure 포털](https://portal.azure.com)합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **장치 구성**을 선택하고 **프로필**을 선택한 다음, **프로필 만들기**를 선택합니다.
4. 버전 업그레이드 프로필에 대한 **이름** 및 **설명**을 입력합니다.
5. **플랫폼** 드롭다운 목록에서 **Windows 10 이상**을 선택합니다.
6. **프로필** 유형 드롭다운 목록에서 선택 **버전 업그레이드**를 선택합니다.
7. **버전 업그레이드** 속성에서 다음 설정을 입력합니다.
   - **업그레이드할 대상 버전** - 드롭다운 목록에서 대상 장치를 업그레이드할 Windows 10 Desktop, Windows 10 Holographic 또는 Windows 10 Mobile 버전을 선택합니다.
   - **제품 키** - 대상으로 지정된 모든 Windows 10 Desktop 장치를 업그레이드하는 데 사용할 수 있는 Microsoft에서 받은 제품 키를 입력합니다. 
    제품 키를 포함하는 정책을 만든 후에 해당 키는 업데이트될 수 없고 보안상의 이유로 숨겨집니다. 제품 키를 변경하려면 전체 키를 다시 입력합니다.
   - **라이선스 파일** - **찾아보기**를 선택하여 Microsoft에서 받은 라이선스 파일을 선택합니다. 이 라이선스 파일은 대상 장치를 업그레이드할 Windows Holographic 또는 Windows 10 Mobile 버전에 대한 라이선스 정보를 포함합니다.
8. 완료되면 **만들기**를 선택하여 변경 내용을 저장합니다.

프로필이 만들어지고 프로필 목록에 표시됩니다.

## <a name="next-steps"></a>다음 단계

이 프로필을 그룹에 할당하려면 [장치 프로필을 할당하는 방법](device-profile-assign.md)을 참조하세요.

>[!NOTE]
>나중에 정책 할당을 제거해도 장치의 Windows 버전을 되돌리지 않고 계속 정상적으로 작동합니다.