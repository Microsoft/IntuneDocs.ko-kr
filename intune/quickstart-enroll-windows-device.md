---
title: 빠른 시작 - Microsoft Intune에서 Windows 10 Desktop 디바이스 등록
description: 빠른 시작 - 회사 포털을 사용하여 Microsoft Intune에서 Windows 10 Desktop 디바이스를 Microsoft Intune에 등록합니다.
services: microsoft-intune
author: ErikRe
ms.author: erikre
manager: dougeby
ms.date: 04/15/2019
ms.topic: quickstart
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 658a7655-a6df-4dbe-b56c-22c7fc60e706
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3c14d55201f88f5090f404ca9a79dd902c8da5e
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66041333"
---
# <a name="quickstart-enroll-your-windows-10-device"></a>빠른 시작: Windows 10 장치 등록

이 빠른 시작에서는 먼저 Intune 사용자의 역할을 수행하고 Microsoft Intune에 Windows 10 디바이스를 등록한 후 그런 다음 Intune으로 돌아가 등록된 디바이스를 확인합니다.

Microsoft Intune에 디바이스를 등록하면 Windows 10 디바이스를 사용하여 메일, 파일 및 기타 리소스를 포함한 조직의 보안 데이터에 액세스할 수 있습니다. Windows 10 데스크톱 및 Windows 10 모바일 디바이스의 경우도 마찬가지입니다. 디바이스를 등록하면 사용자와 조직 모두 이러한 액세스를 보호하고 작업 데이터를 개인 데이터와 별도로 보호할 수 있습니다.

> [!TIP]
> [Intune에서 디바이스를 등록](/intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows)하면 어떻게 되는지 그리고 그것이 [디바이스의 정보](/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune)에 어떤 영향을 주는지 알아보세요.

Intune 구독이 없으면 [평가판 계정에 등록](free-trial-sign-up.md)하세요.

## <a name="prerequisites"></a>전제 조건

- Microsoft Intune 구독 - [평가판 계정에 등록](free-trial-sign-up.md)
- 이 빠른 시작을 완료하려면 [Intune에서 자동 등록 설정](quickstart-setup-auto-enrollment.md)에 대한 단계를 완료해야 합니다.

## <a name="confirm-your-windows-10-desktop-version"></a>Windows 10 Desktop 버전 확인

Windows 10 Desktop을 등록하기 전에 설치한 Windows 버전을 확인해야 합니다.

1. Windows **시작** 아이콘을 마우스 오른쪽 단추로 클릭하고 **설정**을 선택하여 Windows 설정 옵션을 표시합니다.

   ![Windows 설정의 스크린샷 - 시스템](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-01.png)

2. **시스템** > **정보**를 선택합니다. 

   ![시스템 설정의 스크린샷](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-02.png)

    > [!TIP]
    > **검색 표시줄**에 “PC 정보”라는 구문을 입력한 다음, **PC 정보**를 선택할 수도 있습니다.

3. **설정** 창에 PC용 **Windows 사양** 목록이 표시됩니다. 이 목록에서 **버전**을 찾습니다.

4. Windows 10 **버전**이 **1607 이상**인지 확인합니다.

    > [!IMPORTANT]
    > 이 빠른 시작에서 표시된 단계는 Windows 10 버전 **1607 이상**이고, 버전이 **1511**이하인 경우 [이러한 단계](/intune-user-help/enroll-windows-10-device)를 계속합니다.  

## <a name="enroll-windows-10-desktop"></a>Windows 10 Desktop 등록

1. Windows 설정으로 돌아가서 **계정**을 선택합니다.

   ![시스템 설정의 스크린샷 - 계정](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-03.png)

2. **회사 또는 학교 액세스** > **[+]연결**을 선택합니다.

    ![회사 또는 학교 계정 액세스 선택](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-04.png)

3. 회사 또는 학교 계정을 사용하여 Intune에 로그인한 후, **다음**을 선택합니다. [사용자 만들기 및 라이선스 할당](quickstart-create-user.md) 빠른 시작을 수행한 경우 사용자가 만든 사용자 계정으로 로그인할 수 있습니다.

    > [!NOTE]
    > ".onmicrosoft.com"을 설정하는 경우 사용자 계정에는 **.onmicrosoft.com**이 계정 주소의 일부로 포함됩니다. 

   ![회사 또는 학교 계정 입력](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-05.png)

    회사 또는 학교에서 내 디바이스를 등록하고 있다는 메시지가 표시됩니다.

4. **모두 설정되었습니다.** 화면에서 **완료**를 선택하여 작업을 완료합니다.

5. 이제 추가된 계정이 Windows Desktop의 **회사 또는 학교 액세스** 설정의 일부로 표시됩니다.

   ![새로 추가된 계정의 스크린샷](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-06.png)

    위의 단계를 수행해도 여전히 회사 또는 학교 전자 메일 계정 및 파일에 액세스할 수 없는 경우 [회사 또는 학교 액세스가 표시되는 경우 따라야 하는 문제 해결 절차](/intune-user-help/troubleshoot-your-windows-10-device-windows#troubleshooting-steps-to-follow-if-you-see-access-work-or-school)의 단계를 수행합니다.

## <a name="confirm-your-device-enrollment-in-intune"></a>Intune에서 디바이스 등록 확인

1. [Intune](https://aka.ms/intuneportal)에 글로벌 관리자 또는 Intune 서비스 관리자로 로그인합니다.
2. Intune에 등록된 디바이스를 보려면 **장치**를 선택합니다.
3. Intune에 추가 디바이스가 등록되어 있는지 확인합니다.

   ![스크린샷 Intune에 등록된 디바이스](media/quickstart-enroll-windows-device/quickstart-enroll-windows-device-07.png)

## <a name="clean-up-resources"></a>리소스 정리

Windows 디바이스의 등록을 취소하려면 [관리에서 Windows 디바이스 제거](/intune-user-help/unenroll-your-device-from-intune-windows)를 참조하세요.

## <a name="next-steps"></a>다음 단계

이 빠른 시작에서는 Windows 10 디바이스를 Intune에 등록하는 방법을 알아보았습니다. 모든 플랫폼에서 디바이스를 등록하는 다른 방법을 알아볼 수 있습니다. Intune과 함께 디바이스를 사용하는 방법에 대한 자세한 내용은 [관리 디바이스를 사용하여 작업 완료](/intune-user-help/use-managed-devices-to-get-work-done)를 참조하세요.

다음 Intune 빠른 시작을 진행하기 위해서는 아래 빠른 시작 링크를 클릭하세요.

> [!div class="nextstepaction"]
> [빠른 시작: Android 디바이스에 필요한 암호 길이 설정](quickstart-set-password-length-android.md)
