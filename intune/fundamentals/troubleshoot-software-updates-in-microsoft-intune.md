---
title: Microsoft Intune에서 소프트웨어 업데이트 문제 해결 - Azure | Microsoft Docs
description: Microsoft Intune에서 소프트웨어 업데이트 문제를 해결합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ROBOTS: ''
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8ad8d904f72df169eea136c625a2f44d645cafbc
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509766"
---
# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Microsoft Intune에서 소프트웨어 업데이트 문제 해결

Microsoft Intune에서 소프트웨어 업데이트 문제를 해결하는 데 도움을 줍니다. 오류 코드 및 설명 목록을 보려면 [Microsoft Intune에서 소프트웨어 업데이트 에이전트 오류 코드](../protect/software-update-agent-error-codes.md)로 이동하세요.

## <a name="windows-7-devices-with-many-superseded-updates-stop-reporting-to-intune"></a>대체된 업데이트가 많은 Windows 7 디바이스에서 Intune에 보고를 중지함

Microsoft Intune 클라이언트에서 다음과 같은 증상이 하나 이상 발생할 수 있습니다.

- 디바이스에서 갑자기 Intune에 보고를 중지합니다.  
- 디바이스의 CPU 사용률이 높아집니다.
- Intune을 통해 설치하는 경우 애플리케이션이 느리게 설치됩니다.
- Microsoft Intune Center에서 다음 오류를 표시합니다. `An error occurred while updating your computer. Error found: Code 0x800705b4`.
- [Intune 관리 콘솔] > [그룹] > [모든 디바이스] > [상태]에서 다음을 표시합니다. `One or more agents that are installed on this computer have errors. The information for this computer may not be accurate or up-to-date.`

이 문제는 대체된 업데이트(다른 업데이트에 의해 대체되는 업데이트)가 오랜 기간 동안 거부되지 않은 경우에 발생할 수 있습니다. 특정 프로세스(예: 애플리케이션 설치)가 진행되는 동안, Windows는 업데이트 및 그 후속 작업이 올바르게 매핑되도록, 대체된 모든 업데이트를 순서대로 확인합니다. 대체된 업데이트 목록이 너무 커지면, 이러한 확인 작업에 필요한 시간 및 처리 부하로 인해 CPU 사용률이 높아질 수 있습니다. 이 문제는 Windows 7에 제공되는 대체된 업데이트의 수가 많기 때문에 주로 Windows 7 디바이스에 영향을 미칩니다. 최신 운영 체제에는 대체된 업데이트가 그만큼 많지 않을 수 있으므로 이러한 문제의 영향을 덜 받습니다.

**해결 방법**

1. [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인합니다.
2. **소프트웨어 업데이트**를 선택합니다.
3. Windows 7 또는 영향을 받는 클라이언트에 설치된 애플리케이션(예: Microsoft Office)에 적용될만한 대체되는 업데이트를 모두 거부합니다.
4. 영향을 받는 클라이언트를 다시 시작합니다.

Windows 7을 실행하는 경우, 다음 업데이트가 설치되어 있는지 확인합니다. [3050265 Windows 7용 Windows 업데이트 클라이언트: 2015년 6월](https://support.microsoft.com/kb/3050265)

## <a name="next-steps"></a>다음 단계

[Microsoft의 지원 도움말](get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.