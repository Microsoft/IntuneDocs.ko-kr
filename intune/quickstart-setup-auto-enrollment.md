---
title: 빠른 시작 - Intune에서 자동 등록 설정
description: 빠른 시작 - Intune에서 Windows 10 디바이스에 대한 자동 등록을 설정합니다.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.localizationpriority: high
ms.topic: quickstart
ms.date: 03/26/2019
ms.author: erikje
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b81525034f69b43abeb60f562e4d6ee6a46b866
ms.sourcegitcommit: d38ca1bf44e17211097aea481e00b6c1e87effae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58514283"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>빠른 시작: Windows 10 디바이스에 대한 자동 등록 설정

이 빠른 시작에서는 특정 사용자가 Windows 10 디바이스에 로그인할 때 자동으로 디바이스를 등록하도록 Microsoft Intune을 설정합니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건

- Microsoft Intune 구독 - [평가판 계정에 등록](free-trial-sign-up.md)하세요.
- 이 빠른 시작을 완료하려면 [사용자를 만들고](quickstart-create-user.md) [그룹을 만들어야 합니다](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다. Intune 평가판 구독을 만든 경우 구독을 만든 계정은 글로벌 관리자입니다.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 설정

이 예제에서는 회사 및 BYOD(bring-your-own-devices)를 모두 자동으로 등록할 수 있도록 MDM 등록을 사용합니다. Azure Active Directory Premium 무료 구독을 신청할 수 있습니다.

1. Azure에서 **Azure Active Directory** > **모바일(MDM 및 MAM)** 을 선택합니다.
2. **Premium 평가판을 받아서 이 기능 사용**을 선택하세요. 이 옵션을 선택하면 Azure Active Directory Premium 평가판을 사용하여 자동 등록할 수 있습니다. 

    ![Azure Active Directory Premium 평가판 선택](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-01.png)

    **Enterprise Mobility + Security E5** 평가판 옵션을 선택합니다. 또한 평가판을 **활성화**하도록 선택해야 합니다.

    ![Enterprise Mobility + Security E5 평가판 선택](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-02.png)

3. **Microsoft Intune**을 선택합니다. 

    ![목록에서 Microsoft Intune 선택](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-03.png)

4. **MDM 사용자 범위**에서 **일부**을 선택하여 MDM 자동 등록을 사용하여 직원의 Windows 디바이스에서 엔터프라이즈 데이터를 관리합니다. MDM 자동 등록은 AAD 조인 디바이스에 대해 구성되며 고유의 디바이스 시나리오를 제공합니다.

    ![구성 목록에서 '일부' 선택](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-04.png)

5. **그룹 선택** > **Contoso 테스터** > **선택**에서 할당된 그룹으로 선택합니다.

    ![등록할 그룹 선택](media/quickstart-setup-auto-enrollment/quickstart-setup-auto-enrollment-05.png)

6. **MAM 사용자 범위**에서 **일부**를 선택하여 직원의 디바이스에서 데이터를 관리합니다.
7. **그룹 선택** > **Contoso 테스터** > **선택**에서 할당된 그룹으로 선택합니다. 
8. 나머지 구성 값에 기본값을 사용합니다.
9. **저장**을 선택합니다.

## <a name="clean-up-resources"></a>리소스 정리

Intune 자동 등록을 다시 구성하려면 [Windows 디바이스에 대한 등록 설정](windows-enroll.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Windows 10 디바이스에 대한 자동 등록을 설정하는 방법을 알아보았습니다. 디바이스 등록에 대한 자세한 내용은 [디바이스 등록이란?](device-enrollment.md)을 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: Windows 10 디바이스 등록](quickstart-enroll-windows-device.md)
