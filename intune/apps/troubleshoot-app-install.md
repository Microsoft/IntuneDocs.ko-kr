---
title: 앱 설치 문제 해결
titleSuffix: Microsoft Intune
description: Microsoft Intune 문제 해결 창을 사용하면 앱 설치 문제 해결에 도움이 될 수 있습니다.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/21/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b613f364-0150-401f-b9b8-2b09470b34f4
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 13aea23f58c69d5c7e38f77ae7dfa19bd12edd35
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511654"
---
# <a name="troubleshoot-app-installation-issues"></a>앱 설치 문제 해결

Microsoft Intune MDM 관리 디바이스에서 앱 설치에 실패하는 경우도 있습니다. 이러한 앱 설치에 실패할 경우, 실패 이유를 파악하거나 문제를 해결하기 어려울 수 있습니다. Microsoft Intune은 지원 센터 운영자 및 Intune 관리자가 사용자 도움 요청을 해결하기 위해 앱 정보를 볼 수 있는 앱 설치 실패 세부 정보를 제공합니다. Intune 내의 문제 해결 창에서는 사용자 디바이스의 관리되는 앱에 대한 세부 정보를 비롯하여 실패 세부 정보를 제공합니다. **관리되는 앱** 창에서 개별 디바이스 아래에는 앱의 엔드투엔드 수명 주기에 대한 세부 정보가 제공됩니다. 앱이 만들어지거나 수정되거나 대상이 지정되거나 디바이스에 제공되는 경우 등에 설치 문제를 볼 수 있습니다. 

> [!NOTE]
> 특정 앱 설치 오류 코드에 대한 자세한 내용은 [Intune 앱 설치 오류 참조](~/apps/app-install-error-codes.md)를 참조하세요.

## <a name="app-troubleshooting-details"></a>앱 문제 해결 세부 정보

Intune은 특정 사용자 디바이스에 설치된 앱을 기반으로 앱 문제 해결 세부 정보를 제공합니다.

1. [Microsoft Endpoint Manager 관리 센터](https://go.microsoft.com/fwlink/?linkid=2109431)에 로그인합니다.
3. **문제 해결 + 지원**을 선택합니다.
4. **사용자 선택**을 클릭하여 문제를 해결할 사용자를 선택합니다. **사용자 선택** 창이 표시됩니다.
5. 이름 또는 이메일 주소를 입력하여 사용자를 선택합니다. 창 아래쪽에서 **선택**을 클릭합니다. **문제 해결** 창에 사용자에 대한 문제 해결 정보가 표시됩니다. 
6. **디바이스** 목록에서 문제를 해결할 디바이스를 선택합니다.
    ![Intune 문제 해결 창.](./media/troubleshoot-app-install/troubleshoot-app-install-01.png)
7. 선택한 디바이스 창에서 **관리되는 앱**을 선택합니다. 관리되는 앱 목록이 표시됩니다.
    ![Intune에서 관리되는 특정 디바이스의 세부 정보.](./media/troubleshoot-app-install/troubleshoot-app-install-02.png)
8. 목록에서 **설치 상태**에 실패가 표시된 앱을 선택합니다.
    ![설치 실패 세부 정보를 표시하는 선택된 앱.](./media/troubleshoot-app-install/troubleshoot-app-install-03.png)

    > [!Note]  
    > 같은 앱을 여러 그룹에 할당하되, 앱에 대해 의도한 동작(의도)을 각각 다르게 할 수 있습니다. 예를 들어 앱 할당 중에 사용자에 대해 앱이 제외된 경우 앱에 대해 확인된 의도에 **제외**가 표시됩니다. 자세한 내용은 [앱 의도 간의 충돌을 해결하는 방법](apps-deploy.md#how-conflicts-between-app-intents-are-resolved)을 참조하세요.<br><br>
    > 필수 앱에 대해 설치 오류가 발생하는 경우 사용자 또는 사용자의 지원 센터는 디바이스를 동기화하고 앱 설치를 다시 시도할 수 있습니다.

앱 설치 오류 세부 정보에 문제가 표시됩니다. 이러한 세부 정보를 사용하여 문제를 해결하기 위해 수행할 최상의 조치를 결정할 수 있습니다. 앱 설치 문제를 해결하는 방법에 대한 자세한 내용은 [Android 앱 설치 오류](app-install-error-codes.md#android-app-installation-errors) 및 [iOS 앱 설치 오류](app-install-error-codes.md#ios-and-ipados-app-installation-errors)를 참조하세요.

> [!Note]  
> 브라우저를 [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting)으로 전환하여 **문제 해결** 창에 액세스할 수도 있습니다.

## <a name="user-group-targeted-app-installation-does-not-reach-device"></a>사용자 그룹 대상 앱 설치가 디바이스에 연결되지 않음
앱을 설치하는 데 문제가 있는 경우 다음 작업을 고려해야 합니다.
- 앱이 회사 포털에 표시되지 않으면 앱이 **사용 가능**하도록 배포되었으며 사용자가 앱에서 지원하는 디바이스 유형으로 회사 포털에 액세스하고 있는지 확인합니다.
- Windows BYOD 디바이스의 경우 사용자는 디바이스에 회사 계정을 추가해야 합니다.
- 사용자가 AAD 디바이스 제한을 초과하는지 확인합니다.
  1. [Azure Active Directory 디바이스 설정](https://portal.azure.com/#pane/Microsoft_AAD_IAM/DevicesMenupane/DeviceSettings/menuId)으로 이동합니다.
  2. **Maximum devices per user**(사용자당 최대 디바이스 수)에 설정된 값을 기록합니다.
  3. [Azure Active Directory 사용자](https://portal.azure.com/#pane/Microsoft_AAD_IAM/UsersManagementMenupane/AllUsers)로 이동합니다.
  4. 영향을 받는 사용자를 선택하고 **디바이스**를 클릭합니다.
  5. 사용자가 설정된 제한을 초과하는 경우 더 이상 필요하지 않은 오래된 레코드를 삭제합니다.
- iOS/iPadOS DEP 디바이스의 경우, Intune 디바이스 개요 창에서 **사용자가 등록함**이 표시되는지 확인합니다. NA가 표시되는 경우 Intune 회사 포털에 대한 구성 정책을 배포합니다. 자세한 내용은 [회사 포털 앱 구성을 참조하세요](app-configuration-policies-use-ios.md#configure-the-company-portal-app-to-support-ios-and-ipados-dep-devices).

## <a name="win32-app-installation-troubleshooting"></a>Win32 앱 설치 문제 해결

Intune 관리 확장을 사용하여 배포된 Win32 앱을 선택합니다. Win32 앱 설치에 실패하면 **로그 수집** 옵션을 선택할 수 있습니다. 

> [!IMPORTANT]
> Win32 앱이 디바이스에 성공적으로 설치되면 **로그 수집** 옵션이 활성화되지 않습니다.<p>Win32 앱 로그 정보를 수집하려면 먼저 Windows 클라이언트에 Intune 관리 확장을 설치해야 합니다. Intune 관리 확장은 PowerShell 스크립트 또는 Win32 앱이 사용자 또는 디바이스 보안 그룹에 배포될 때 설치됩니다. 자세한 내용은 [Intune 관리 확장 - 필수 구성 요소](intune-management-extension.md#prerequisites)를 참조하세요.

### <a name="collect-log-file"></a>로그 파일 수집

Win32 앱 설치 로그를 수집하려면 먼저 [앱 문제 해결 세부 정보](troubleshoot-app-install.md#app-troubleshooting-details) 섹션에 나와 있는 단계를 따릅니다. 그런 다음, 다음 절차를 계속 수행합니다.

1. **설치 세부 정보** 창에서 **로그 수집** 옵션을 클릭합니다.

    <image alt="Win32 app installation details - Collect log option" src="./media/troubleshoot-app-install/troubleshoot-app-install-04.png" width="500" />

2. 로그 파일 이름과 함께 파일 경로를 제공하여 로그 파일 수집 프로세스를 시작하고 **확인**을 클릭합니다.

    > [!NOTE]
    > 로그 수집에는 2시간 미만이 소요됩니다. 지원되는 파일 형식: *.log, .txt, .dmp, .cab, .zip, .xml, .evtx 및 .evtl*. 최대 25개의 파일 경로가 허용됩니다.

3. 로그 파일이 수집되면 **로그** 링크를 선택하여 로그 파일을 다운로드할 수 있습니다.

    <image alt="Win32 app log details - Download logs" src="./media/troubleshoot-app-install/troubleshoot-app-install-05.png" width="500" />

    > [!NOTE]
    > 앱 로그 수집의 성공 여부를 나타내는 알림이 표시됩니다.

#### <a name="win32-log-collection-requirements"></a>Win32 로그 수집 요구 사항

로그 파일을 수집하려면 다음과 같이 적용해야 할 특정 요구 사항이 있습니다.

- 전체 로그 파일 경로를 지정해야 합니다. 
- 로그 수집에 대한 환경 변수를 다음과 같이 지정할 수 있습니다.<br>
  *%PROGRAMFILES%, %PROGRAMDATA% %PUBLIC%, %WINDIR%, %TEMP%, %TMP%*
- 다음과 같은 정확한 파일 확장명만 허용됩니다.<br>
  *.log, .txt, .dmp, .cab, .zip, .xml*
- 업로드할 최대 로그 파일은 60MB 또는 25개의 파일 중 먼저 발생하는 파일입니다. 
- Win32 앱 설치 로그 수집은 필수, 사용 가능 및 제거 앱 할당 의도를 충족하는 앱에 대해 활성화됩니다.
- 저장된 로그는 로그에 포함된 모든 개인 식별 정보를 보호하기 위해 암호화됩니다.
- Win32 앱 오류에 대한 지원 티켓을 여는 동안 위에 나와 있는 단계를 사용하여 관련 오류 로그를 첨부합니다.

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Microsoft 스토어의 앱 문제 해결

[Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)(Microsoft 스토어 앱 패키징, 배포 및 쿼리 문제 해결) 항목의 정보는 Intune을 사용하든, 다른 방법을 사용하든 관계없이 Microsoft 스토어에서 앱을 설치할 때 발생할 수 있는 일반적인 문제를 해결하는 데 도움을 줍니다.

## <a name="app-troubleshooting-resources"></a>문제 해결 리소스
- [Deploying Visio and Project as part of your Office Pro Plus Deployment](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Deploying-Visio-and-Project-as-part-of-your-Office/ba-p/701795)(Office Pro Plus 배포의 일부로 Visio 및 Project 배포)
- [Take Action to Ensure MSfB Apps deployed through Intune install on Windows 10 1903](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Take-Action-to-Ensure-MSfB-Apps-deployed-through/ba-p/658864)(Windows 10 1903에서 Intune 설치를 통해 MSfB 앱이 배포되었는지 확인하는 작업)
- [Troubleshooting MSI app deployments in Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-Tip-Troubleshooting-MSI-App-deployments-in-Microsoft/ba-p/359125)(Microsoft Intune에서 MSI 앱 배포 문제 해결)
- [Best practices for software distribution to Intune classic Windows PC agent](https://support.microsoft.com/en-us/help/2583929/best-practices-for-intune-software-distribution-to-windows-pc)(Intune 클래식 Windows PC 에이전트에 소프트웨어 배포 모범 사례)

## <a name="next-steps"></a>다음 단계

- 추가 Intune 문제 해결 정보는 [문제 해결 포털을 사용하여 회사 내 사용자 지원](../fundamentals/help-desk-operators.md)을 참조하세요. 
- 알려진 Microsoft Intune 문제를 알아봅니다. 자세한 내용은 [Intune Customer Success](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)(Intune 고객 성공)를 참조하세요.
- 추가 도움이 필요하십니까? [Microsoft Intune에 대한 지원을 받는 방법](../fundamentals/get-support.md)을 참조하십시오.
