---
title: 자습서 - Autopilot을 사용하여 Intune에서 장치 등록
titleSuffix: Microsoft Intune
description: 이 자습서에서는 Intune에서 장치를 등록하도록 Windows Autopilot을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.openlocfilehash: a90f53bfc5841cc0f773751e7df917d8fc8b6cf8
ms.sourcegitcommit: cff65435df070940da390609d6376af6ccdf0140
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2018
ms.locfileid: "49431937"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>자습서: Autopilot을 사용하여 Intune에서 Windows 장치 등록
Windows Autopilot이 장치 등록을 간소화합니다. Microsoft Intune 및 AutoPilot을 사용하면 사용자 지정 운영 체제 이미지를 빌드, 유지 관리 및 적용할 필요 없이 최종 사용자에게 새 장치를 제공할 수 있습니다. 

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * Intune에 장치 추가
> * Autopilot 장치 그룹 만들기
> * Autopilot 배포 프로필 만들기
> * 장치 그룹에 Autopilot 배포 프로필 할당
> * 사용자에게 Windows 장치 배포

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

Autopilot 이점, 시나리오 및 필수 구성 요소에 대한 개요는 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)를 참조하세요.


## <a name="prerequisites"></a>전제 조건
- [Windows 자동 등록 설정](quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium 구독](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>장치 추가

Windows Autopilot을 설정하는 첫 번째 단계는 Intune에 Windows 장치를 추가하는 것입니다. CSV 파일을 만들고 Intune으로 가져오기만 하면 됩니다.

1. 원하는 텍스트 편집기에서 Windows 장치를 식별하는 쉼표로 구분된 값(CSV) 목록을 만듭니다. 다음 형식을 사용하세요.
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-order-id*
    
    처음 3개 항목은 필수이고 주문 ID는 선택 사항입니다.

2. CSV 파일을 저장합니다.

3. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **장치** > **가져오기**를 선택합니다.

    ![Windows Autopilot 장치 스크린샷](media/enrollment-autopilot/autopilot-import-device.png)

4. **Windows Autopilot 장치 추가** 아래에서 저장한 CSV 파일로 이동합니다.

    ![Windows AutoPilot 장치 추가 스크린샷](media/enrollment-autopilot/autopilot-import-device2.png)

5. **가져오기**를 선택하여 장치 정보 가져오기를 시작합니다. 가져오기는 몇 분 정도 걸릴 수 있습니다.

4. 가져오기가 완료되면 **장치 등록** > **Windows 등록** > **Windows Autopilot** > **장치** > **동기화**를 선택합니다. 동기화가 진행 중이라는 메시지가 표시됩니다. 동기화 중인 장치의 수에 따라 프로세스가 완료되는 데 몇 분 정도 걸릴 수 있습니다.

5. 보기를 새로 고쳐 새 장치를 확인합니다.

## <a name="create-an-autopilot-device-group"></a>Autopilot 장치 그룹 만들기

다음으로 장치 그룹을 만들고 방금 로드한 Autopilot 장치를 장치 그룹에 넣습니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **그룹** > **새 그룹**을 선택합니다.
2. **그룹** 블레이드에서:
    1. **그룹 형식**에서 **보안**을 선택합니다.
    2. **그룹 이름**으로 ‘Autopilot 그룹’을 입력합니다. **그룹 설명**으로 ‘Autopilot 장치의 테스트 그룹’을 입력합니다.
    3. **멤버 자격 유형**으로 **할당됨**을 선택합니다.
3. **그룹** 블레이드에서 **멤버**를 선택하고 Autopilot 장치를 그룹에 추가합니다. 아직 등록되지 않은 AutoPilot 장치는 장치 이름이 장치의 일련 번호와 동일한 장치입니다.
4. **만들기**를 선택합니다.  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 만들기

장치 그룹을 만든 후 Autopilot 장치를 구성할 수 있도록 배포 프로필을 만들어야 합니다.

1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기**를 선택합니다.
2. **이름**으로 ‘Autopilot 프로필’을 입력합니다. **설명**으로 ‘Autopilot 장치의 테스트 프로필’을 입력합니다.
3. **모든 대상 장치를 Autopilot으로 변환**을 **예**로 설정합니다. 이렇게 설정하면 목록의 모든 장치가 Autopilot 배포 서비스를 사용하여 등록됩니다. 등록을 처리하는 데 48시가 가량 걸립니다.
4. **배포 모드**에서 **사용자 기반**을 선택합니다. 이 프로필을 사용하는 장치는 장치를 등록한 사용자와 연결됩니다. 장치를 등록하려면 사용자 자격 증명이 필요합니다.
5. **다음으로 Azure AD에 조인** 상자에서 **Azure AD 조인됨**을 선택합니다.
6. **OOBE(첫 실행 경험)** 를 선택하고, 다음 옵션을 구성하고 다른 옵션을 기본값으로 유지한 후, **저장**을 선택합니다.
    - **EULA(최종 사용자 사용권 계약)**: **숨기기**
    - **개인 정보 설정**: **표시**
    - **사용자 계정 유형**: **표준**

6. **만들기**를 선택하여 프로필을 만듭니다. 이제 Autopilot 배포 프로필을 장치에 할당할 수 있습니다.

## <a name="assign-an-autopilot-deployment-profile-to-a-device-group"></a>장치 그룹에 Autopilot 배포 프로필 할당

이제 배포 프로필이 만들어졌으므로 장치 그룹에 할당하겠습니다.
1. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **배포 프로필**을 선택하고 프로필을 선택합니다.
2. 특정 프로필 블레이드에서 **할당**을 선택합니다. 
3. **그룹 선택**을 선택하고, **그룹 선택** 블레이드에서 **Autopilot 그룹**을 선택한 후, **선택**을 선택합니다.

## <a name="distribute-devices-to-users"></a>사용자에게 장치 배포

이제 사용자에게 Windows 장치를 배포할 수 있습니다. 처음 로그인하면 Autopilot 시스템이 장치를 자동으로 등록하고 구성합니다. 

## <a name="clean-up-resources"></a>리소스 정리

더 이상 사용하지 않으려는 Autopilot 장치를 삭제할 수 있습니다.

1. 장치가 Intune에 등록된 경우 먼저 [Azure Active Directory 포털에서 삭제](devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)해야 합니다.

2. [Azure Portal의 Intune](https://aka.ms/intuneportal)에서 **장치 등록** > **Windows 등록** > **장치**를 선택합니다.

3. **Windows AutoPilot 장치**에서 삭제할 장치를 선택한 다음, **삭제**를 선택합니다.

4. **예**를 선택하여 삭제를 확인합니다. 삭제하는 데 몇 분 정도 걸릴 수 있습니다.

## <a name="next-steps"></a>다음 단계

Windows Autopilot의 다른 옵션에 대한 자세한 정보를 찾을 수 있습니다.

> [!div class="nextstepaction"]
> [자세한 Autopilot 등록 문서](enrollment-autopilot.md)


