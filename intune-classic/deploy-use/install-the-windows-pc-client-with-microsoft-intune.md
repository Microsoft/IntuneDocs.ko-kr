---
title: PC 클라이언트 소프트웨어 설치
description: 이 가이드를 사용하여 Microsoft Intune 클라이언트 소프트웨어에서 관리되는 Windows PC를 얻을 수 있습니다.
keywords: ''
author: nathbarn
ms.author: nathbarn
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 64c11e53-8d64-41b9-9550-4b4e395e8c52
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 85d77356d7a864f3d7703e087528fe0cefafb312
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31832462"
---
# <a name="install-the-intune-software-client-on-windows-pcs"></a>Windows PC에 Intune 소프트웨어 클라이언트 설치

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune 클라이언트 소프트웨어를 설치하여 Windows PC를 등록할 수 있습니다. Intune 클라이언트 소프트웨어는 다음 방법으로 설치할 수 있습니다.

- IT 관리자가 수동 설치, 그룹 정책, 디스크 이미지에 포함된 설치 등의 방법 중 하나 사용

- 최종 사용자가 클라이언트 소프트웨어 수동 설치

Intune 클라이언트 소프트웨어에는 PC를 Intune 관리에 등록하는 데 필요한 최소 소프트웨어가 포함됩니다. PC가 등록되면 Intune 클라이언트 소프트웨어는 PC 관리에 필요한 전체 클라이언트 소프트웨어를 다운로드합니다.

이 일련의 다운로드는 네트워크 대역폭에 미치는 영향을 줄이고 처음에 PC를 Intune에 등록하는 데 필요한 시간을 최소화합니다. 또한 두 번째 다운로드가 완료된 후 클라이언트에서 최신 소프트웨어를 사용할 수 있도록 해줍니다.

하나의 Intune 라이선스가 있으면 최대 5대의 PC에 Intune 클라이언트 소프트웨어를 설치할 수 있습니다.

## <a name="download-the-intune-client-software"></a>Intune 클라이언트 소프트웨어 다운로드

사용자가 Intune 클라이언트 소프트웨어를 직접 설치하는 방법을 제외한 모든 방법에서는 IT 관리자가 최종 사용자에게 소프트웨어를 배포할 수 있도록 먼저 다운로드해야 합니다.

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **관리** &gt; **클라이언트 소프트웨어 다운로드**를 클릭합니다.

   ![Intune PC 클라이언트 다운로드](../media/pc-sa-client-download.png)

2. **클라이언트 소프트웨어 다운로드** 페이지에서 **클라이언트 소프트웨어 다운로드**를 클릭합니다. 그런 다음 소프트웨어가 포함된 **Microsoft_Intune_Setup.zip** 패키지를 네트워크의 안전한 위치에 저장합니다.

   Intune 클라이언트 소프트웨어 설치 패키지에는 사용자 계정에 대한 고유한 특정 정보가 포함되어 있으며, 이 정보는 포함된 인증서를 통해 사용할 수 있습니다. 권한이 없는 사용자가 설치 패키지에 대한 액세스 권한을 얻는 경우 포함된 인증서에 표시된 계정에 PC를 등록하고 회사 리소스에 대한 액세스 권한을 얻을 수 있습니다.

3. 설치 패키지의 콘텐츠를 네트워크의 안전한 위치로 추출합니다.

    > [!IMPORTANT]
    > 추출된 **ACCOUNTCERT** 파일의 이름을 바꾸거나 제거하지 마세요. 이름을 바꾸거나 제거하면 클라이언트 소프트웨어가 설치되지 않습니다.

## <a name="deploy-the-client-software-manually"></a>클라이언트 소프트웨어 수동 배포

클라이언트 소프트웨어를 설치할 컴퓨터에서 클라이언트 소프트웨어 설치 파일이 있는 폴더로 이동합니다. 그런 다음 **Microsoft_Intune_Setup.exe**를 실행하여 클라이언트 소프트웨어를 설치합니다.

> [!NOTE]
> 클라이언트 PC의 작업 표시줄에 있는 아이콘 위로 마우스를 가져가면 설치 상태가 표시됩니다.

## <a name="deploy-the-client-software-by-using-group-policy"></a>그룹 정책을 사용하여 클라이언트 소프트웨어 배포

1.  **Microsoft_Intune_Setup.exe** 및 **MicrosoftIntune.accountcert** 파일이 포함된 폴더에서 다음 명령을 실행하여 32비트 및 64비트 컴퓨터용 Windows Installer 기반 설치 프로그램을 추출합니다.

    ```
    Microsoft_Intune_Setup.exe/Extract <destination folder>
    ```

2.  클라이언트 소프트웨어를 설치할 모든 컴퓨터에서 액세스할 수 있는 네트워크 위치로 **Microsoft_Intune_x86.msi** 파일, **Microsoft_Intune_x64.msi** 파일 및 **MicrosoftIntune.accountcert** 파일을 복사합니다.

    > [!IMPORTANT]
    > 파일을 서로 다른 위치에 저장하거나 파일 이름을 바꾸지 마십시오. 그렇게 하면 클라이언트 소프트웨어가 설치되지 않습니다.

3.  그룹 정책을 사용하여 네트워크의 컴퓨터에 소프트웨어를 배포합니다.

    그룹 정책을 사용하여 소프트웨어를 자동으로 배포하는 방법에 대한 자세한 내용은 [초보자를 위한 그룹 정책](https://technet.microsoft.com/library/hh147307.aspx)을 참조하세요.

## <a name="deploy-the-client-software-as-part-of-an-image"></a>클라이언트 소프트웨어를 이미지의 일부로 배포
다음 절차를 지침으로 사용하여 운영 체제 이미지의 일부로 Intune 클라이언트 소프트웨어를 컴퓨터에 배포할 수 있습니다.

1.  클라이언트 설치 파일, **Microsoft_Intune_Setup.exe** 및 **MicrosoftIntune.accountcert**를 참조 컴퓨터의 **%Systemdrive%\Temp\Microsoft_Intune_Setup** 폴더로 복사합니다.

2.  **SetupComplete.cmd** 스크립트에 다음 명령을 추가하여 **WindowsIntuneEnrollPending** 레지스트리 항목을 만듭니다.

    ```
    %windir%\system32\reg.exe add HKEY_LOCAL_MACHINE\Software\Microsoft\Onlinemanagement\Deployment /v
    WindowsIntuneEnrollPending /t REG_DWORD /d 1
    ```

3.  **setupcomplete.cmd**에 다음 명령을 추가하여 /PrepareEnroll 명령줄 인수로 등록 패키지를 실행합니다.

    ```
    %systemdrive%\temp\Microsoft_Intune_Setup\Microsoft_Intune_Setup.exe /PrepareEnroll
    ```
    > [!TIP]
    > **SetupComplete.cmd** 스크립트를 사용하여 Windows 설치 프로그램을 통해 사용자가 로그온하기 전에 시스템의 수정 사항을 적용할 수 있습니다. **/PrepareEnroll** 명령줄 인수는 Windows 설치 프로그램이 완료된 후 Intune에서 대상 컴퓨터를 자동으로 등록하도록 준비합니다.

4.  참조 컴퓨터의 **%Windir%\Setup\Scripts** 폴더에 **SetupComplete.cmd**를 저장합니다.

5.  참조 컴퓨터의 이미지를 캡처한 후 대상 컴퓨터에 배포합니다.

    Windows 설치 프로그램 완료 시 대상 컴퓨터가 다시 시작되면 **WindowsIntuneEnrollPending** 레지스트리 키가 만들어집니다. 등록 패키지는 컴퓨터가 등록되어 있는지 여부를 확인합니다. 컴퓨터가 등록된 경우 추가 작업은 없습니다. 컴퓨터가 등록되지 않은 경우 등록 패키지는 Microsoft Intune 자동 등록 작업을 만듭니다.

    다음 번 예약 시간에 자동 등록 작업이 실행될 경우 이 작업은 **WindowsIntuneEnrollPending** 레지스트리 값이 있는지 확인하고 Intune에서 대상 PC를 등록하려고 시도합니다. 어떠한 이유로든 등록에 실패하면 다음에 작업을 실행할 때 등록을 다시 시도합니다. 재시도는 한 달 동안 계속됩니다.

    성공적으로 등록되거나 한 달이 지난 후(둘 중 빠른 시간)에는 Intune 자동 등록 작업인 **WindowsIntuneEnrollPending** 레지스트리 값 및 계정 인증서가 대상 컴퓨터에서 삭제됩니다.

## <a name="instruct-users-to-self-enroll"></a>사용자에게 직접 등록 지시

사용자가 [회사 포털 웹사이트](https://portal.manage.microsoft.com)로 이동하여 Intune 클라이언트 소프트웨어를 설치합니다. 웹 포털에서 사용자에게 표시되는 정확한 정보는 계정의 MDM 기관, 사용자 PC의 OS 플랫폼/버전에 따라 다를 수 있습니다.

사용자가 Intune 라이선스를 할당받지 않은 경우나 조직의 MDM 기관이 Intune으로 설정되지 않은 경우 등록하는 옵션이 표시되지 않습니다.

사용자에게 Intune 라이선스가 할당되고 조직의 MDM 기관이 Intune으로 설정된 경우에는 다음이 표시됩니다.

- Windows 7 또는 Windows 8 PC 사용자에게는 조직에 고유한 PC 클라이언트 소프트웨어를 다운로드하고 설치하여 Intune에 등록하는 옵션만 표시됩니다.

- Windows 10 또는 Windows 8.1 PC 사용자에게는 두 가지 등록 옵션이 표시됩니다.

  -  **PC를 모바일 장치로 등록**: 사용자가 **등록하는 방법 알아보기** 단추를 선택하면 PC를 모바일 장치로 등록하는 방법에 대한 지침이 표시됩니다. MDM 등록이 선호되는 기본 등록 옵션이므로 이 단추는 눈에 잘 띄게 표시됩니다. 그러나 MDM 옵션은 클라이언트 소프트웨어 설치만 설명하는 이 항목과는 관련이 없습니다.
  - **Intune 클라이언트 소프트웨어를 사용하여 PC 등록**: 사용자에게 **Click here to download it**(다운로드하려면 여기 클릭) 링크를 선택하여 클라이언트 소프트웨어 설치로 이동하도록 안내해야 합니다.

다음 표에 옵션이 요약되어 있습니다.

  ![플랫폼별 기본 등록 옵션](../media/default-enrollment-options-table.png)

다음 스크린샷에서는 사용자가 소프트웨어 클라이언트를 사용하여 장치를 등록할 때 무엇이 표시되는지를 보여 줍니다.

먼저 장치를 확인하거나 등록하라는 메시지가 표시됩니다.

  ![확인 식별 또는 등록](../media/identify-device-or-enroll.png)

사용자가 PC 클라이언트 소프트웨어를 설치할 수 있도록 사용자에게 **Click here to download it**(다운로드하려면 여기 클릭) 링크를 선택하여 PC 클라이언트 소프트웨어를 다운로드하고 설치 과정을 진행하도록 안내해야 합니다. **등록하는 방법 알아보기** 단추를 누르는 경우 이러한 소프트웨어 클라이언트 지침과는 관련이 없는 MDM 등록을 사용한 등록 방법에 대한 설명서가 표시됩니다.

  ![다운로드하려면 여기 클릭 링크 선택](../media/enroll-your-windows-device.png)

사용자가 이 링크를 클릭하면 **소프트웨어 다운로드** 단추가 표시되며, 이 단추를 선택하여 PC 클라이언트 소프트웨어 설치를 시작할 수 있습니다.

  ![소프트웨어 다운로드 단추 선택](../media/download-pc-client-software.png)

그런 다음 회사 자격 증명을 사용하여 로그인하라는 메시지가 표시됩니다.

  ![자격 증명으로 로그인](../media/sign-in-to-intune.png)

설치의 [시작] 페이지가 표시됩니다.

  ![PC 클라이언트 설치의 시작 페이지](../media/welcome-to-pc-agent-install-wizard.png)

**다음**을 선택하면 설치가 시작됩니다.

  ![PC 클라이언트 설치의 시작 페이지](../media/welcome-to-pc-agent-install-wizard.png)

설치가 완료되면 **마침**을 선택합니다.

  ![PC 클라이언트 설치 완료](../media/completed-the-setup-wizard.png)

사용자가 Intune PC 클라이언트 소프트웨어를 사용하여 이미 등록한 PC를 모바일 장치로 등록하려고 하면 다음과 같은 오류 화면이 표시됩니다.

  ![PC가 이미 등록된 경우 표시되는 화면](../media/page-shown-if-pc-already-enrolled.png)

## <a name="monitor-and-validate-successful-client-deployment"></a>성공적인 클라이언트 배포 모니터링 및 유효성 검사
다음 절차에 따라 성공적인 클라이언트 배포를 모니터링하고 유효성을 검사할 수 있습니다.

### <a name="to-verify-the-installation-of-the-client-software-from-the-microsoft-intune-administrator-console"></a>Microsoft Intune 관리자 콘솔에서 클라이언트 소프트웨어 설치를 확인하려면

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **그룹** &gt; **모든 장치** &gt; **모든 컴퓨터**를 클릭합니다.

2.  목록에서 Intune과 통신하는 관리 컴퓨터를 찾거나, **장치 검색** 상자에 컴퓨터 이름이나 이름 중 일부를 입력하여 특정 관리 컴퓨터를 검색합니다.

3.  콘솔 맨 아래 창에 있는 컴퓨터의 상태를 확인합니다. 오류가 있으면 해결합니다.

### <a name="to-create-a-computer-inventory-report-to-display-all-enrolled-computers"></a>등록된 모든 컴퓨터를 표시하는 컴퓨터 인벤토리 보고서를 만들려면

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **보고서** &gt; **컴퓨터 인벤토리 보고서**를 클릭합니다.

2.  **새 보고서 만들기** 페이지의 모든 필드에서 기본값을 유지하고(필터를 적용하지 않는 한), **보고서 보기**를 클릭합니다.

3.  **컴퓨터 인벤토리 보고서** 페이지가 새 창에서 열리며, Intune에 등록된 모든 컴퓨터를 표시합니다.

    > [!TIP]
    > 보고서의 모든 열 제목을 클릭하여 해당 열의 콘텐츠별로 목록을 정렬합니다.

## <a name="uninstall-the-windows-client-software"></a>Windows 클라이언트 소프트웨어 제거

Windows 클라이언트 소프트웨어 등록을 취소하는 방법에는 다음 두 가지가 있습니다.

- Intune 관리 콘솔에서(권장 방법)
- 클라이언트의 명령 프롬프트에서

### <a name="unenroll-by-using-the-intune-admin-console"></a>Intune 관리 콘솔을 사용하여 등록 취소

Intune 관리 콘솔을 사용하여 소프트웨어 클라이언트 등록을 취소하려면 **그룹** > **모든 컴퓨터** > **장치**로 이동합니다. 클라이언트를 마우스 오른쪽 단추로 클릭하고 **사용 중지/초기화**를 선택합니다.

### <a name="unenroll-by-using-a-command-prompt-on-the-client"></a>클라이언트에서 명령 프롬프트를 사용하여 등록 취소

관리자 권한 명령 프롬프트를 사용하여 다음 명령 중 하나를 실행합니다.

**방법 1**:

    "C:\Program Files\Microsoft\OnlineManagement\Common\ProvisioningUtil.exe" /UninstallAgents /MicrosoftIntune

**방법 2** 이러한 모든 에이전트는 모든 Windows SKU에 설치되어 있습니다.

    wmic product where name="Microsoft Endpoint Protection Management Components" call uninstall
    wmic product where name="Microsoft Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Microsoft Online Management Policy Agent" call uninstall
    wmic product where name="Microsoft Policy Platform" call uninstall
    wmic product where name="Microsoft Security Client" call uninstall
    wmic product where name="Microsoft Online Management Client" call uninstall
    wmic product where name="Microsoft Online Management Client Service" call uninstall
    wmic product where name="Microsoft Easy Assist v2" call uninstall
    wmic product where name="Microsoft Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Microsoft Intune Center" call uninstall
    wmic product where name="Microsoft Online Management Update Manager" call uninstall
    wmic product where name="Microsoft Online Management Agent Installer" call uninstall
    wmic product where name="Microsoft Intune" call uninstall
    wmic product where name="Windows Endpoint Protection Management Components" call uninstall
    wmic product where name="Windows Intune Notification Service" call uninstall
    wmic product where name="System Center 2012 - Operations Manager Agent" call uninstall
    wmic product where name="Windows Online Management Policy Agent" call uninstall
    wmic product where name="Windows Policy Platform" call uninstall
    wmic product where name="Windows Security Client" call uninstall
    wmic product where name="Windows Online Management Client" call uninstall
    wmic product where name="Windows Online Management Client Service" call uninstall
    wmic product where name="Windows Easy Assist v2" call uninstall
    wmic product where name="Windows Intune Monitoring Agent" call uninstall
    wmic product where name="Windows Intune Endpoint Protection Agent" call uninstall
    wmic product where name="Windows Firewall Configuration Provider" call uninstall
    wmic product where name="Windows Intune Center" call uninstall
    wmic product where name="Windows Online Management Update Manager" call uninstall
    wmic product where name="Windows Online Management Agent Installer" call uninstall
    wmic product where name="Windows Intune" call uninstall

> [!TIP]
> 클라이언트 등록을 취소하면 영향을 받는 클라이언트에 대한 부실 서버 쪽 레코드가 남게 됩니다. 등록 취소 프로세스는 비동기이며, 제거할 에이전트가 9개 있으므로 완료하는 데 최대 30분이 걸릴 수 있습니다.

### <a name="check-the-unenrollment-status"></a>등록 취소 상태 확인

"%ProgramFiles%\Microsoft\OnlineManagement"를 검사하고 다음 디렉터리만 왼쪽에 표시되는지 확인합니다.

- AgentInstaller
- 로그
- 업데이트
- 공용

### <a name="remove-the-onlinemanagement-folder"></a>OnlineManagement 폴더 제거

등록 취소 프로세스는 OnlineManagement 폴더를 제거하지 않습니다. 제거 후 30분 정도 기다린 후 이 명령을 실행합니다. 너무 빨리 실행하면 제거가 알 수 없는 상태로 남을 수 있습니다. 폴더를 제거하려면 관리자 권한 프롬프트를 시작하고 다음을 실행합니다.

    "rd /s /q %ProgramFiles%\Microsoft\OnlineManagement".

### <a name="next-steps"></a>다음 단계
[Microsoft Intune으로 Windows PC 관리](manage-windows-pcs-with-microsoft-intune.md)
[클라이언트 설정 문제 해결](../troubleshoot/troubleshoot-client-setup-in-microsoft-intune.md)
