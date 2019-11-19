---
title: Microsoft Intune - Azure에서 일반적인 Endpoint Protection 메시지 | Microsoft Docs
description: Microsoft Intune에서 Endpoint Protection 및 Microsoft Defender를 사용하고 문제를 해결할 때 일반적인 메시지와 가능한 해결 방법을 확인하세요.
keywords: ''
author: Brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 819586a923f5c0f3a81a6d59c4a3895898182f6b
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059167"
---
# <a name="endpoint-protection-issues-and-possible-solutions-in-microsoft-intune"></a>Microsoft Intune에서 Endpoint Protection 문제와 가능한 해결 방법

이 문서에서는 몇 가지 오류 및 경고의 잠재적 원인과 해결 방법을 설명합니다. 이 정보를 사용하면 Endpoint Protection을 사용하는 동안 발생하는 문제를 해결할 수 있습니다.

## <a name="microsoft-defender-error-codes"></a>Microsoft Defender 오류 코드

이벤트 로그 및 오류 코드를 검토하여 [Microsoft Defender AV 관련 문제를 해결](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus)합니다.

## <a name="common-intune-errors-and-possible-resolutions"></a>일반적인 Intune 오류와 가능한 해결 방법

### <a name="endpoint-protection-engine-unavailable"></a>Endpoint Protection 엔진을 사용할 수 없음

**잠재적 원인**: Intune Endpoint Protection 엔진이 손상되었거나 삭제되었습니다.

**가능한 해결 방법**:

- Endpoint Protection이 손상되었거나 업데이트되지 않는 경우 프로그램을 업데이트하거나 다시 설치합니다.
- 즉시 업데이트를 강제 실행합니다. Endpoint Protection 클라이언트 프로그램(작업 표시줄에 있음)에서 **업데이트**를 선택합니다.
- [제어판] > [프로그램]에서 **Microsoft Intune Endpoint Protection 에이전트**를 선택합니다. 애플리케이션을 제거합니다.
- 다음 업데이트 동기화 중에 Microsoft Online Management 업데이트 관리자에서 누락된 프로그램을 검색하고 예약된 설치 시간에 다시 설치합니다.

### <a name="features-are-disabled"></a>기능을 사용할 수 않음

일부 기능을 사용할 수 없다는 메시지가 표시될 수 있습니다. 이러한 메시지는 관리자가 구성 프로필을 사용하여 Intune Endpoint Protection 또는 Microsoft Defender를 사용하지 않도록 설정한 경우에 발생할 수 있습니다. 또는 디바이스에서 최종 사용자가 사용하지 않도록 설정했습니다. 가능한 메시지:

`Endpoint Protection disabled`  
`Real-time protection disabled`  
`Download scanning disabled`  
`File and program activity monitoring disabled`  
`Behavior monitoring disabled`  
`Script scanning disabled`  
`Network Inspection System disabled`  

**가능한 해결 방법**: 이러한 기능을 사용하도록 설정합니다. 지침은 다음을 참조하세요.

- [Endpoint Protection 설정 추가](../protect/endpoint-protection-configure.md)
- [Microsoft Defender 바이러스 백신](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)
- [최종 사용자: 실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)

### <a name="malware-definitions-out-of-date"></a>맬웨어 정의가 만료됨

이 상태는 디바이스의 맬웨어 정의가 14일 이상 만료된 상태임을 보여 줍니다. 예를 들어 디바이스가 인터넷과 연결이 끊겼거나 맬웨어 정의가 만료된 경우 이 메시지가 표시될 수 있습니다.

**가능한 해결 방법**: 맬웨어 정의가 만료된 경우 [Microsoft Defender 바이러스 백신](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)을 사용하여 정의를 업데이트합니다.

### <a name="full-scan-overdue-or-quick-scan-overdue"></a>전체 검색 지연 또는 빠른 검색 지연

전체 검색 또는 빠른 검색이 14일 동안 완료되지 않습니다. 이 시나리오는 전체 검색 중 디바이스를 다시 시작하는 경우에 발생할 수 있습니다.

**가능한 해결 방법**: 검사가 지연되는 경우 일회성 검사를 실행하거나 되풀이 검사를 예약할 수 있습니다. [Microsoft Defender 바이러스 백신](../configuration/device-restrictions-windows-10.md#microsoft-defender-antivirus)을 참조 하세요.

### <a name="another-endpoint-protection-application-running"></a>다른 엔드포인트 보호 애플리케이션이 실행되고 있음

다른 엔드포인트 보호 애플리케이션이 실행되고 있으며 디바이스가 정상 상태입니다.

**가능한 해결 방법**: 다른 엔드포인트 보호 애플리케이션이 설치되어 있고 Intune에서 해당 애플리케이션을 검색한 경우 디바이스가 불안정해질 수 있습니다.

## <a name="next-steps"></a>다음 단계

[Microsoft의 지원 도움말](get-support.md)을 받거나 [커뮤니티 포럼](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune)을 이용하세요.
