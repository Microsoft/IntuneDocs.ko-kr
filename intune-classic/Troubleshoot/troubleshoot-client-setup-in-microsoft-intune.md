---
title: 클라이언트 설정 문제 해결
description: 일반적인 클라이언트 설정 문제를 해결합니다.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 02/22/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 39c0b0997bdbf229064e6b5ef25ab559b9252f83
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31028081"
---
# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Microsoft Intune에서 클라이언트 설정 문제 해결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

다음 정보를 사용하여 일반적인 클라이언트 설정 문제를 해결할 수 있습니다. 이 정보로 문제가 해결되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)을 참조하여 도움을 얻을 수 있는 다른 방법을 찾아보세요.

## <a name="client-installation-fails"></a>클라이언트 설치 실패

-   [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에 컴퓨터에 대한 클라이언트 소프트웨어 배포 경고가 표시되지 않으면, 컴퓨터의 인터넷 연결 및 프록시 구성을 확인하고 컴퓨터가 서비스 URL([https://manage.microsoft.com](https://manage.microsoft.com/))과 통신할 수 있는지 확인합니다. 그런 다음 클라이언트 소프트웨어 설치를 다시 시도해 보세요.

-   **관리** 작업 영역에서 알림 규칙을 구성하면 클라이언트 소프트웨어 배포 실패 경고가 발생할 때 선택한 수신자에게 전자 메일을 보낼 수 있습니다. 자세한 내용은 [Microsoft Intune 경고 알림 받기](/intune-classic/deploy-use/get-notified-by-alerts)항목을 참조하세요.

-   클라이언트 소프트웨어 배포에 실패하면 Intune에 **클라이언트 소프트웨어 배포 실패**라는 중요한 경고가 표시됩니다. 이 경고는 [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)의 **시스템 개요** 페이지 및 **경고** 페이지에 표시됩니다. 경고를 확인하는 방법:

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com/)에서 **경고** &gt; **개요**를 선택합니다.

2.  **경고 개요** 페이지에서 다음 정보를 검토할 수 있습니다.

    -   상위 3개 경고(날짜, 범주 또는 심각도를 기준으로 정렬 가능)

    -   총 활성 경고 수

3.  **모든 경고**를 선택하면 **경고** 페이지에 다음 정보가 표시됩니다. 중요한 알림이 먼저 표시됩니다.

    -   **이름** - 경고를 생성한 경고 유형의 이름입니다.

    -   **원본** – 경고 원본에 대한 링크입니다.  경고 유형의 표시 임계값이 **모두**로 설정된 경우 이 링크는 영향받는 단일 장치를 표시합니다.  경고 유형의 표시 임계값이 특정 값으로 설정된 경우 이 링크는 해당 경고로 영향받는 모든 장치 목록을 표시합니다.

    -   **마지막으로 업데이트한 날짜** - 경고가 마지막으로 수정된 시간을 나타냅니다. 경고가 종결된 경우 경고가 종결된 시간이 표시됩니다.

    -   **심각도** - 경고의 심각도를 나타냅니다.

## <a name="computer-enrollment-package-doesnt-download"></a>컴퓨터 등록 패키지가 다운로드되지 않음
**문제:** 컴퓨터 등록을 시도하는 동안 다음과 같은 문제가 발생합니다.
-  등록 패키지 다운로드 실패
-  다운로드 대화 상자가 표시되지만 시간이 초과됨

**해결 방법:** 다운로드에 사용 중인 브라우저에서, 다운로드가 실행되는 동안, 다운로드가 활성화되어 있는지 확인하고, 암호화된 파일을 로컬 디스크에 저장할 수 있는지 확인합니다.

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>0x80040154 오류 코드와 함께 클라이언트 설치 중단
**문제:**

-  등록 중단 시 클라이언트 설치

-  장치를 등록할 수 없음

-  WindowsUpdate.log에 0x80040154 오류

PC에 중요 소프트웨어 업데이트가 없는 것이 원인일 수 있습니다.

**해결 방법:** [Microsoft Intune에서 소프트웨어 업데이트를 사용하여 Windows PC를 최신 상태로 유지](/intune-classic/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune) 항목의 설명에 따라, 소프트웨어 업데이트 정책에 중요 업데이트 설치가 활성화되어 있는지 확인합니다.


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>policyplatform.log의 Microsoft Intune 정책 관련 오류
비 MDM Windows 장치의 경우 policyplatform.log 파일의 정책 오류는 장치의 Windows UAC(사용자 계정 컨트롤)에서 기본값이 아닌 설정을 사용한 결과일 수 있습니다. 기본값이 아닌 일부 UAC 설정은 Microsoft Intune 클라이언트 설치와 정책 실행에 영향을 줄 수 있습니다.

### <a name="to-resolve-uac-issues"></a>UAC 문제를 해결하려면

1.  [Microsoft Intune 관리에서 데이터 및 장치 사용 중지](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management) 항목의 설명에 따라, 컴퓨터 사용을 중지합니다.

2.  클라이언트 소프트웨어가 제거될 때까지 20분 정도 기다립니다.

    > [!NOTE]
    > 프로그램 및 기능에서 클라이언트를 제거하지 마세요.

3.  시작 메뉴에서 **UAC**를 입력하여 사용자 계정 컨트롤 설정을 엽니다.

4.  알림 슬라이더를 기본 설정으로 이동합니다.

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>Microsoft Intune 관리자 콘솔에서 클라이언트를 제거하지 않을 경우 수행할 작업

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>Microsoft Intune 명령줄 도구를 사용하여 클라이언트 소프트웨어를 제거하려면

1.  관리자 모드에서 명령 프롬프트를 엽니다.

2.  *%programfiles%\Microsoft\OnlineManagement\Common* 폴더로 이동합니다.

3.  다음 명령을 실행합니다. ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>클라이언트 설치 오류 코드
다음 표에는 클라이언트 소프트웨어를 설치하지 못했을 때 **경고** 에 표시될 수 있는 오류 코드가 설명되어 있습니다. 여기에는 각 오류 코드가 나타내는 문제를 해결할 수 있는 권장 방법이 제시되어 있습니다.


|                                                                   오류 코드                                                                    |                                                          가능한 문제                                                          |                                                                                                                                                                                                권장되는 해결 방법                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                           <strong>0x80CF0437</strong>                                                           |                                  클라이언트 컴퓨터의 시계가 올바른 시간으로 설정되어 있지 않습니다.                                  |                                                                                                                                                    클라이언트 컴퓨터의 시계 및 표준 시간대가 올바른 시간 및 표준 시간대로 설정되어 있는지 확인합니다.                                                                                                                                                     |
|                              <strong>0x80240438</strong>, <strong>0x80CF0438</strong>, <strong>0x80CF401B</strong>                              |                               Intune 서비스에 연결할 수 없습니다. 클라이언트 프록시 설정을 확인합니다.                               |                   클라이언트 컴퓨터의 프록시 구성을 Intune에서 지원하는지 그리고 클라이언트 컴퓨터가 인터넷에 연결되어 있는지 확인합니다. 지원되는 프록시 구성에 대한 자세한 내용은 [Microsoft Intune용 Endpoint Protection을 사용한 Windows PC의 보안 유지 방법](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) 항목을 참조하세요.                    |
|                                                           <strong>0x80CF402C</strong>                                                           |                                 Intune 서비스에 연결할 수 없습니다. 네트워크 연결을 확인합니다.                                  |                                                                                                                                                   컴퓨터가 네트워크에 연결되어 있는지 확인합니다. 네트워크 케이블이 연결되어 있거나 무선 네트워크가 작동 중인지 확인합니다.                                                                                                                                                    |
|                                                     <strong>0x80240438, 0x80CF0438</strong>                                                     |                              Internet Explorer 및 로컬 시스템의 프록시 설정이 구성되어 있지 않습니다.                              | 클라이언트 프록시 설정을 확인하고 클라이언트 컴퓨터의 프록시 구성이 Intune에서 지원되는 지와 클라이언트 컴퓨터에서 인터넷에 연결할 수 있는지 확인하세요. 지원되는 프록시 구성에 대한 자세한 내용은 [Microsoft Intune용 Endpoint Protection을 사용한 Windows PC의 보안 유지 방법](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) 항목을 참조하세요. |
|                                                           <strong>0x80043001</strong>                                                           |                                                 등록 패키지가 오래되었습니다.                                                 |                                                                     <strong>관리</strong> 작업 영역에서 최신 클라이언트 소프트웨어 패키지를 다운로드하여 설치합니다. 자세한 내용은 [Microsoft Intune을 사용하여 Windows PC 클라이언트 설치](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune) 항목을 참조하세요.                                                                      |
|                                                           <strong>0x80043004</strong>                                                           |                                            구독이 존재하지 않거나 사용할 수 없습니다.                                            |                                                                                                   Intune에 대한 계정과 구독이 계속 활성 상태인지 확인하십시오. 계정 설정을 보려면 [Office 365 관리 센터](http://go.microsoft.com/fwlink/?LinkId=698854%20)에서 자신의 계정으로 로그인합니다.                                                                                                   |
|                                                           <strong>0x80043002</strong>                                                           |                                                  계정이 유지 관리 모드에 있습니다.                                                   |                                                                                             계정이 유지 관리 모드에 있는 경우 새 클라이언트 컴퓨터를 등록할 수 없습니다. 계정 설정을 보려면 [Office 365 관리 센터](http://go.microsoft.com/fwlink/?LinkId=698854%20)에서 자신의 계정으로 로그인합니다.                                                                                              |
|                                                           <strong>0x80043003</strong>                                                           |                                                        계정이 삭제되었습니다.                                                         |                                                                                                                                            Intune에 대한 계정과 구독이 계속 활성 상태인지 확인하십시오. 계정 설정을 보려면 자신의 계정으로 로그인합니다.                                                                                                                                             |
|                                                           <strong>0x80043005</strong>                                                           |                                                  클라이언트 컴퓨터가 사용 중지되었습니다.                                                   |                                                                  몇 시간 기다렸다가 이전 버전의 클라이언트 소프트웨어를 컴퓨터에서 제거한 다음 클라이언트 소프트웨어를 다시 설치해 봅니다. 자세한 내용은 위의 <strong>Microsoft Intune 관리자 콘솔에서 클라이언트를 제거하지 않을 경우 수행할 작업</strong>을 참조하세요.                                                                  |
|                                                           <strong>0x80043006</strong>                                                           |                                  계정에 허용된 최대 사용자 수에 도달했습니다.                                   |                                                                                                                                                    서비스에 클라이언트 컴퓨터를 더 등록하려면 조직에서 추가 사용자 수를 구매해야 합니다.                                                                                                                                                     |
|                                                           <strong>0x80043007</strong>                                                           |                          설치 관리자 프로그램과 같은 폴더에서 인증서 파일을 찾을 수 없습니다.                          |                                 모든 파일을 추출한 후에 설치를 시작합니다. 추출된 파일의 이름이나 위치를 바꾸지 마십시오. 모든 파일은 같은 폴더에 있어야 합니다. 그렇지 않으면 설치할 수 없습니다. 자세한 내용은 [Microsoft Intune을 사용하여 Windows PC 클라이언트 설치](/intune-classic/deploy-use/install-the-windows-pc-client-with-microsoft-intune) 항목을 참조하세요.                                  |
| <strong>0x8024D015</strong>, <strong>0x00240005</strong>, <strong>0x80070BC2</strong>, <strong>0x80070BC9</strong>, <strong>0x80CFD015</strong> |                       클라이언트 컴퓨터를 다시 시작하는 작업이 보류되어 소프트웨어를 설치할 수 없습니다.                        |                                                                                                                                                                        컴퓨터를 다시 시작한 다음 클라이언트 소프트웨어를 다시 설치해 봅니다.                                                                                                                                                                        |
|                                                           <strong>0x80070032</strong>                                                           |                클라이언트 컴퓨터에 클라이언트 소프트웨어를 설치하기 위한 필수 구성 요소가 하나 이상 없습니다.                 |                            클라이언트 컴퓨터에 필수 업데이트가 모두 설치되었는지 확인한 다음 클라이언트 소프트웨어를 다시 설치해 봅니다. 클라이언트 소프트웨어를 설치하기 위한 필수 조건에 대한 자세한 내용은 [Microsoft Intune의 네트워크 인프라 요구 사항](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune) 항목을 참조하세요.                             |
|                                                           <strong>0x80043008</strong>                                                           |                                  Microsoft Online Management Updates 서비스를 시작할 수 없습니다.                                  |                                                                                                                                               [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md) 항목의 설명에 따라, 지원 센터에 문의하세요.                                                                                                                                                |
|                                                           <strong>0x80043009</strong>                                                           |                                     클라이언트 컴퓨터가 이미 서비스에 등록되어 있습니다.                                      |                                                                                        클라이언트 컴퓨터를 서비스에 다시 등록하기 전에 사용 중지해야 합니다. 지침은 [Microsoft Intune 관리에서 장치 사용 중지](/intune-classic/deploy-use/retire-devices-from-microsoft-intune-management) 항목을 참조하세요.                                                                                         |
|                                                           <strong>0x8004300A</strong>                                                           |  (21단계) 컴퓨터 범위가 아니라 사용자 범위에서 설치하기 위해 GPO에 등록 패키지를 배포할 때 오류가 발생합니다.   |                                                               컴퓨터 범위에서 GPSI를 통해 GPO의 대상이 올바르게 지정되었는지 확인합니다. 이 주제와 관련된 포럼 게시물을 보려면 이 [TechNet 포럼](https://social.technet.microsoft.com/Forums/en-US/bb9fa71c-c132-4954-abb0-70be8acbd925/failed-to-install-windows-intune?forum=microsoftintuneprod)을 참조하세요.                                                                |
|                                                           <strong>0x8004300B</strong>                                                           | 클라이언트를 실행 중인 Windows 버전이 지원되지 않으므로 클라이언트 소프트웨어 설치 패키지를 실행할 수 없습니다. |                                                               Intune에서 클라이언트 컴퓨터에서 실행 중인 Windows 버전을 지원하지 않습니다. 지원되는 운영 체제 목록은 [Microsoft Intune의 네트워크 인프라 요구 사항](/intune-classic/get-started/network-infrastructure-requirements-for-microsoft-intune) 항목을 참조하세요.                                                               |
|                                                             <strong>0xAB2</strong>                                                              |                           Windows Installer에서 사용자 지정 작업에 대한 VBScript 런타임에 액세스할 수 없습니다.                            |                                                      이 오류는 DLL(동적 연결 라이브러리)에 기반한 사용자 지정 작업으로 인해 발생합니다. DLL 문제를 해결하려면 [Microsoft Support KB198038: Useful Tools for Package and Deployment Issues(Microsoft 지원 기술 자료 198038: 패키지 및 배포 문제에 유용한 도구)](http://go.microsoft.com/fwlink/?LinkID=234255)에 설명된 도구를 사용해야 할 수 있습니다.                                                       |
|                                                           <strong>0x8004300f</strong>                                                           |           System Center Configuration Manager 클라이언트가 이미 설치되어 있어서 소프트웨어를 설치할 수 없습니다.            |                                                                                                                                                              Configuration Manager 클라이언트를 제거한 후 클라이언트 소프트웨어 설치를 다시 시도하십시오.                                                                                                                                                               |
|                                                           <strong>0x80043010</strong>                                                           |      OMADM(Open Mobile Alliance Device Management) 클라이언트가 이미 설치되어 있어서 소프트웨어를 설치할 수 없습니다.      |                                                                                                                                                                     OMADM 클라이언트를 등록 해제한 후 클라이언트 소프트웨어 설치를 다시 시도하십시오.                                                                                                                                                                     |

설치 문제가 지속되면 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라, 지원 센터에 문의합니다. 지원 엔지니어가 확인할 수 있도록 클라이언트 컴퓨터 등록 로그(%*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log 및 %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log에 있음) 및 Windows 업데이트 로그(%*windir*%\windowsupdate.log)를 설정합니다.

## <a name="what-to-do-if-endpoint-protection-is-not-uninstalled-when-you-uninstall-the-client"></a>클라이언트를 제거할 때 Endpoint Protection이 제거되지 않는 경우 수행할 작업

경우에 따라 위의 명령을 실행한 후 호스트 보호(Endpoint Protection) 에이전트가 남아 있을 수 있습니다. 이런 경우 관리자 권한 명령 프롬프트에서 다음 명령을 실행합니다.

    ```
    "C:\Program Files\Managed Defender\Setup.exe" /x /q /s
    ```


### <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라 Microsoft 지원에 문의하세요.
