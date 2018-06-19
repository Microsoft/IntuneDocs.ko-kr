---
title: 앱 배포 문제 해결
description: 이 항목은 Microsoft Intune에서 앱 배포 문제를 해결하는 데 도움을 줍니다.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 09/27/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: df00293335b23d8924887bdd7b70838f9bddfb65
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31014030"
---
# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Microsoft Intune에서 앱 배포 문제 해결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune을 사용하여 앱을 배포하고 관리하는 데 문제가 있는 경우 여기서 시작하세요. 이 항목에는 솔루션에서 함께 발생할 수 있는 몇 가지 일반적인 문제가 포함되어 있습니다.

## <a name="common-app-deployment-error-codes"></a>일반적인 앱 배포 오류 코드

|오류 코드|가능한 문제|권장되는 해결 방법|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C(클라이언트 오류)|이 앱을 설치하려면 테스트용 로드 기능을 사용하는 시스템이 있어야 합니다.|앱 패키지가 신뢰할 수 있는 서명으로 서명되어 있고 AllowAllTrustedApps 정책이 사용하도록 설정된 도메인 조인 장치에 설치되어 있거나, Windows 테스트용 로드 라이선스가 있고 AllowAllTrustedApps 정책이 사용하도록 설정된 장치에 설치되어 있는지 확인하세요.|
|0x80073CF0|패키지를 열 수 없습니다.|가능한 원인:<br /><br />-   패키지가 서명되지 않았습니다.<br />-   게시자 이름이 인증서 서명 주체와 일치하지 않습니다.<br /><br />자세한 내용은 AppxPackagingOM 이벤트 로그를 확인하십시오.|
|0x80073CF3|패키지 업데이트, 종속성 또는 충돌 유효성 검사에 실패했습니다.|가능한 원인:<br /><br />-   들어오는 패키지가 설치된 패키지와 충돌합니다.<br />-   지정된 패키지 종속성을 찾을 수 없습니다.<br />-   패키지가 올바른 프로세서 아키텍처를 지원하지 않습니다.<br /><br />자세한 내용은 AppXDeployment-Server 이벤트 로그를 확인하세요.|
|0x80073CFB|제공된 패키지가 이미 설치되었으며, 패키지를 다시 설치하는 것이 차단되었습니다.|설치하는 패키지가 이미 설치된 패키지와 동일하지 않은 경우 이 오류를 수신할 수 있습니다. 디지털 서명도 패키지의 일부에 포함되었는지 확인하십시오. 다시 작성하거나 다시 서명하는 패키지는 이전에 설치한 패키지와 비트가 더 이상 동일하지 않습니다. 이 오류를 수정할 수 있는 두 가지 가능한 옵션은 다음과 같습니다.<br /><br />-   앱의 버전 번호를 증가한 다음 패키지를 다시 빌드하고 다시 서명합니다.<br />-   새 패키지를 설치하기 전에 시스템의 모든 사용자에 대한 이전 패키지를 제거합니다.|
|0x87D1041C|응용 프로그램을 설치했으나 응용 프로그램이 검색되지 않습니다.|- 앱이 Intune을 통해 정상적으로 배포된 후에 제거되었습니다(최종 사용자가 제거했을 수 있음). 사용자에게 회사 포털에서 앱을 다시 설치하도록 합니다. 다음 번에 장치를 체크 인할 때 필수 앱이 자동으로 다시 설치됩니다.|

## <a name="troubleshooting-apps-from-the-microsoft-store"></a>Microsoft 스토어의 앱 문제 해결

[Troubleshooting packaging, deployment, and query of Microsoft Store apps](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx)(Microsoft 스토어 앱 패키징, 배포 및 쿼리 문제 해결) 항목의 정보는 Intune을 사용하든, 다른 방법을 사용하든 관계없이 Microsoft 스토어에서 앱을 설치할 때 발생할 수 있는 일반적인 문제를 해결하는 데 도움을 줍니다.

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Intune 소프트웨어 클라이언트로 관리되는 PC에 앱 배포 문제 해결
Intune 소프트웨어 클라이언트로 관리되는 PC에 앱을 배포하는 것과 관련된 문제를 해결하려면 다음 두 개의 로그 파일을 살펴볼 수 있습니다.
- %ProgramFiles%\Microsoft\OnlineManagement\Logs 폴더
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

또한 Intune에 대한 지원 케이스를 열어야 할 경우 이러한 로그를 Microsoft에 보내면 유용합니다.


### <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라 Microsoft 지원에 문의하세요.
