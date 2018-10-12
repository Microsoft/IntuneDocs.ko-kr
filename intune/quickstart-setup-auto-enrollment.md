---
title: 빠른 시작 - Intune에서 자동 등록 설정
description: 빠른 시작 - Intune에서 Windows 10 장치에 대한 자동 등록을 설정합니다.
services: microsoft-intune
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: quickstart
ms.date: 09/21/2018
ms.author: erikje
ms.openlocfilehash: 3b713f090fb6ada884a269e286f55f6e1b1087c4
ms.sourcegitcommit: 27eed5aba5c8bfafb079171081b68f75a6cbffaf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581645"
---
# <a name="quickstart-set-up-automatic-enrollment-for-windows-10-devices"></a>빠른 시작: Windows 10 장치에 대한 자동 등록 설정

이 빠른 시작에서는 특정 사용자가 Windows 10 장치에 로그인할 때 자동으로 장치를 등록하도록 Microsoft Intune을 설정합니다.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건

- 이 빠른 시작을 완료하려면 [사용자를 만들고](quickstart-create-user.md) [그룹을 만들어야 합니다](quickstart-create-group.md).

## <a name="sign-in-to-intune"></a>Intune에 로그인

[Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.

## <a name="set-up-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 설정

이 예제에서는 회사 장치와 BYOD 장치를 모두 자동으로 등록할 수 있도록 MDM 등록을 사용합니다.

1. Azure에서 **Azure Active Directory** > **이동성(MDM 및 MAM)** > **Microsoft Intune** > **일부**를 선택합니다.
![브라우저](media/quickstart-setup-auto-enrollment/setup-automatic-enrollment-win10.png)
2. **그룹 선택** > **Contoso 테스터** > **선택**을 누릅니다.
3. 다음 URL의 기본값을 사용합니다.
    - MDM 사용 약관 URL
    - MDM 검색 URL
    - MDM 규정 준수 URL
4. **저장**을 선택합니다.
5. Windows 10 장치에서 그룹의 사용자로 로그인하고 지시를 따릅니다.

## <a name="clean-up-resources"></a>리소스 정리

Intune 자동 등록을 다시 구성하려면 [Windows 장치에 대한 등록 설정](windows-enroll.md)을 참조하세요.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Windows 10 장치에 대한 자동 등록을 설정하는 방법을 알아보았습니다. 모든 플랫폼에서 장치를 등록하는 다른 방법을 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [장치 등록이란? 문서](device-enrollment.md)