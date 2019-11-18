---
title: 자습서 - Autopilot을 사용하여 Intune에서 디바이스 등록
titleSuffix: Microsoft Intune
description: 이 자습서에서는 Intune에서 디바이스를 등록하도록 Windows Autopilot을 설정합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 10/19/2018
ms.topic: tutorial
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
Customer intent: As an Intune admin, I want to set up Windows Autopilot so that users can enroll in Intune.
ms.reviewer: spshumwa
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8e319c68abd8965b84323bc3b7a5451dee42bc2
ms.sourcegitcommit: 556b7ea2049014c9027f0e44affd3f301fab55fc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2019
ms.locfileid: "73709193"
---
# <a name="tutorial-use-autopilot-to-enroll-windows-devices-in-intune"></a>자습서: Autopilot을 사용하여 Intune에서 Windows 디바이스 등록

Windows Autopilot이 디바이스 등록을 간소화합니다. Microsoft Intune 및 AutoPilot을 사용하면 사용자 지정 운영 체제 이미지를 빌드, 유지 관리 및 적용할 필요 없이 최종 사용자에게 새 디바이스를 제공할 수 있습니다.

이 자습서에서는 다음 작업을 수행하는 방법을 알아봅니다.
> [!div class="checklist"]
> * Intune에 디바이스 추가
> * Autopilot 디바이스 그룹 만들기
> * Autopilot 배포 프로필 만들기
> * 디바이스 그룹에 Autopilot 배포 프로필 할당
> * 사용자에게 Windows 디바이스 배포

Intune 구독이 없으면 [평가판 계정에 등록](../fundamentals/free-trial-sign-up.md)하세요.

Autopilot 이점, 시나리오 및 필수 구성 요소에 대한 개요는 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)를 참조하세요.


## <a name="prerequisites"></a>전제 조건
- [Windows 자동 등록 설정](../quickstart-setup-auto-enrollment.md)
- [Azure Active Directory Premium 구독](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) <!--&#40;[trial subscription](http://go.microsoft.com/fwlink/?LinkID=816845)&#41;-->


## <a name="add-devices"></a>디바이스 추가

Windows Autopilot을 설정하는 첫 번째 단계는 Intune에 Windows 디바이스를 추가하는 것입니다. CSV 파일을 만들고 Intune으로 가져오기만 하면 됩니다.

1. 원하는 텍스트 편집기에서 Windows 디바이스를 식별하는 쉼표로 구분된 값(CSV) 목록을 만듭니다. 다음 형식을 사용합니다.
    
    *serial-number*, *windows-product-id*, *hardware-hash*, *optional-Group-Tag*
    
    처음 세 항목은 필수이지만 그룹 태그(이전에 "주문 ID"라고 함)는 선택 사항입니다.

2. CSV 파일을 저장합니다.

3. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스 등록** > **Windows 등록** > **디바이스** > **가져오기**를 선택합니다.

    ![Windows Autopilot 디바이스 스크린샷](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device.png)

4. **Windows Autopilot 디바이스 추가** 아래에서 저장한 CSV 파일로 이동합니다.

    ![Windows AutoPilot 디바이스 추가 스크린샷](./media/tutorial-use-autopilot-enroll-devices/autopilot-import-device2.png)

5. **가져오기**를 선택하여 디바이스 정보 가져오기를 시작합니다. 가져오기는 몇 분 정도 걸릴 수 있습니다.

4. 가져오기가 완료되면 **디바이스 등록** > **Windows 등록** > **Windows Autopilot** > **디바이스** > **동기화**를 선택합니다. 동기화가 진행 중이라는 메시지가 표시됩니다. 동기화 중인 디바이스의 수에 따라 프로세스가 완료되는 데 몇 분 정도 걸릴 수 있습니다.

5. 보기를 새로 고쳐 새 디바이스를 확인합니다.

## <a name="create-an-autopilot-device-group"></a>Autopilot 디바이스 그룹 만들기

다음으로 디바이스 그룹을 만들고 방금 로드한 Autopilot 디바이스를 디바이스 그룹에 넣습니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **그룹** > **새 그룹**을 선택합니다.
2. **그룹** 블레이드에서:
    1. **그룹 형식**에서 **보안**을 선택합니다.
    2. **그룹 이름**으로 ‘Autopilot 그룹’을 입력합니다.  **그룹 설명**으로 ‘Autopilot 디바이스의 테스트 그룹’을 입력합니다. 
    3. **멤버 자격 유형**으로 **할당됨**을 선택합니다.
3. **그룹** 블레이드에서 **멤버**를 선택하고 Autopilot 디바이스를 그룹에 추가합니다. 아직 등록되지 않은 AutoPilot 디바이스는 디바이스 이름이 디바이스의 일련 번호와 동일한 디바이스입니다.
4. **만들기**를 선택합니다.  

## <a name="create-an-autopilot-deployment-profile"></a>Autopilot 배포 프로필 만들기

디바이스 그룹을 만든 후 Autopilot 디바이스를 구성할 수 있도록 배포 프로필을 만들어야 합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스 등록** > **Windows 등록** > **배포 프로필** > **프로필 만들기**를 차례로 선택합니다.
2. **기본** 페이지에서 **이름**으로 ‘Autopilot 프로필’을 입력합니다.  **설명**으로 ‘Autopilot 디바이스의 테스트 프로필’을 입력합니다. 
3. **모든 대상 디바이스를 Autopilot으로 변환**을 **예**로 설정합니다. 이렇게 설정하면 목록의 모든 디바이스가 Autopilot 배포 서비스를 사용하여 등록됩니다. 등록을 처리하는 데 48시간 정도가 걸립니다.
4. **다음**을 선택합니다.
5. **OOBE(첫 실행 경험)** 페이지에서 **배포 모드**로 **사용자 구동**을 선택합니다. 이 프로필을 사용하는 디바이스는 디바이스를 등록한 사용자와 연결됩니다. 디바이스를 등록하려면 사용자 자격 증명이 필요합니다.
6. **다음으로 Azure AD에 조인** 상자에서 **Azure AD 조인됨**을 선택합니다.
7. 다음 옵션을 구성하고 다른 옵션을 기본값으로 설정해 둡니다.
    - **EULA(최종 사용자 사용권 계약)** : **숨기기**
    - **개인 정보 설정**: **표시**
    - **사용자 계정 유형**: **표준**
8. **다음**을 선택합니다.
9. **할당** 페이지에서 **할당 대상**으로 **선택한 그룹**을 선택합니다.
10. **포함할 그룹 선택**을 선택하고 **Autopilot 그룹**을 선택합니다.
11. **다음**을 선택합니다.
12. **검토 + 만들기** 페이지에서 **만들기**를 선택하여 프로필을 만듭니다.

## <a name="distribute-devices-to-users"></a>사용자에게 디바이스 배포

이제 사용자에게 Windows 디바이스를 배포할 수 있습니다. 처음 로그인하면 Autopilot 시스템이 디바이스를 자동으로 등록하고 구성합니다. 

## <a name="clean-up-resources"></a>리소스 정리

더 이상 사용하지 않으려는 경우 Autopilot 디바이스를 삭제할 수 있습니다.

1. 디바이스가 Intune에 등록된 경우 먼저 [Azure Active Directory 포털에서 삭제](../remote-actions/devices-wipe.md#delete-devices-from-the-azure-active-directory-portal)해야 합니다.

2. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에서 **디바이스 등록** > **Windows 등록** > **디바이스**를 선택합니다.

3. **Windows AutoPilot 디바이스**에서 삭제할 디바이스를 선택한 다음, **삭제**를 선택합니다.

4. **예**를 선택하여 삭제를 확인합니다. 삭제하는 데 몇 분 정도 걸릴 수 있습니다.

## <a name="next-steps"></a>다음 단계

Windows Autopilot의 다른 옵션에 대한 자세한 정보를 찾을 수 있습니다.

> [!div class="nextstepaction"]
> [자세한 Autopilot 등록 문서](enrollment-autopilot.md)


