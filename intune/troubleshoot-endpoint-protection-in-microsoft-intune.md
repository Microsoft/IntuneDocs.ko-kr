---
title: Intune에서 Endpoint Protection 문제 해결 - Azure | Microsoft Docs
description: Microsoft Intune Endpoint Protection을 사용하는 동안 문제를 해결합니다.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: f828394c48b5b7d55d9180da875d9cb3062f23c6
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181686"
---
# <a name="troubleshoot-endpoint-protection-in-intune"></a>Intune에서 Endpoint Protection 문제 해결

이 정보를 사용하면 Endpoint Protection을 사용하는 동안 발생하는 문제를 해결할 수 있습니다. [이벤트 로그 및 오류 코드를 검토하여 Windows Defender AV 관련 문제를 해결](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/troubleshoot-windows-defender-antivirus)할 수도 있습니다.

이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.

### <a name="error-messages"></a>오류 메시지
이 섹션에서는 다음 오류 및 경고의 잠재적 원인과 해결 방법을 설명합니다.

|상태 항목|잠재적 원인|잠재적 해결 방법|
|---------------|--------------------|-----------------------|
|**Endpoint Protection 엔진을 사용할 수 없음**|Intune Endpoint Protection 엔진이 손상되었거나 삭제되었습니다.|Intune Endpoint Protection 엔진이 손상되면 소프트웨어 업데이트 또는 다시 설치를 시도해 볼 수 있습니다.<br /><br />즉시 업데이트를 실행하려면 Endpoint Protection 클라이언트 소프트웨어(관리 컴퓨터의 작업 표시줄에 있음)에서 **업데이트**를 선택합니다.<br /><br />엔진을 업데이트할 수 없는 경우 Endpoint Protection 엔진을 다시 설치해야 합니다.<br /><br />관리되는 컴퓨터의 제어판에 있는 설치된 프로그램 목록에서 **Microsoft Intune Endpoint Protection 에이전트**를 찾은 다음 해당 응용 프로그램을 제거합니다.<br /><br />다음 업데이트 동기화 중에 Microsoft Online Management 업데이트 관리자에서 누락된 프로그램을 검색하고 예약된 설치 시간에 다시 설치합니다.|
|**Endpoint Protection 사용 안 함**|관리되는 컴퓨터의 사용자 또는 구성 프로필을 사용하는 관리자가 Intune Endpoint Protection을 사용하지 않도록 설정했습니다.|Endpoint Protection을 사용하도록 설정합니다. Intune에서 [Endpoint Protection 설정 추가](endpoint-protection-configure.md) 또는 [Windows Defender를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요.|
|**실시간 보호 사용 안 함**|관리되는 컴퓨터의 사용자 또는 프로필을 사용하는 관리자가 실시간 보호를 사용하지 않도록 설정했습니다.|Endpoint Protection을 사용하도록 설정합니다. Intune의 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus) 또는 [실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요. |
|**다운로드 검색 사용 안 함**|관리되는 컴퓨터의 사용자 또는 프로필을 사용하는 관리자가 다운로드 검사를 사용하지 않도록 설정했습니다.|검사를 사용하도록 설정합니다. Intune의 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus) 또는 [실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요. |
|**파일 및 프로그램 활동 모니터링 사용 안 함**|관리되는 컴퓨터의 사용자 또는 프로필을 사용하는 관리자가 파일 및 프로그램 활동 모니터링을 사용하지 않도록 설정했습니다.|파일 및 프로그램 활동을 사용하도록 설정합니다. Intune의 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus) 또는 [실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요. |
|**동작 모니터링 사용 안 함**|관리되는 컴퓨터의 사용자 또는 프로필을 사용하는 관리자가 동작 모니터링을 사용하지 않도록 설정했습니다.|동작 모니터링을 사용하도록 설정합니다. Intune의 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus) 또는 [실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요. |
|**스크립트 검색 사용 안 함**|관리되는 컴퓨터의 사용자 또는 프로필을 사용하는 관리자가 스크립트 검사를 사용하지 않도록 설정했습니다.|스크립트 검사를 사용하도록 설정합니다. Intune의 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus) 또는 [실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요. |
|**네트워크 검사 시스템 사용 안 함**|관리되는 컴퓨터의 사용자 또는 프로필을 사용하는 관리자가 네트워크 검사 시스템을 사용하지 않도록 설정했습니다.|NIS(네트워크 검사 시스템)를 사용하도록 설정합니다. Intune의 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus) 또는 [실시간 보호를 켜서 회사 리소스에 액세스](/intune-user-help/turn-on-defender-windows)를 참조하세요. |
|**맬웨어 정의가 만료됨**|컴퓨터가 오랫동안 인터넷에 연결되지 않았거나 맬웨어 정의가 아직 업데이트되지 않았을 수 있습니다. 이 상태는, 컴퓨터의 맬웨어 정의가 14일 이상 만료된 상태인 경우 나타납니다.|맬웨어 정의가 만료된 경우 [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus)을 사용하여 정의를 업데이트할 수 있습니다.|
|**전체 검색 지연**|전체 검색이 14일 동안 완료되지 않았습니다. 이는 전체 검색 중에 컴퓨터를 다시 시작하여 발생할 수 있습니다.|전체 검사가 늦어진 경우 일회성 전체 검사를 실행하거나 되풀이 전체 검사를 예약할 수 있습니다. [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus)을 참조하세요. |
|**빠른 검색 지연**|빠른 검색이 14일 동안 완료되지 않았습니다. 이는 빠른 검색 중에 컴퓨터를 다시 시작하여 발생할 수 있습니다.|빠른 검사가 늦어진 경우 일회성 빠른 검사를 실행하거나 되풀이 빠른 검사를 예약할 수 있습니다. [Windows Defender 바이러스 백신](device-restrictions-windows-10.md#windows-defender-antivirus)을 참조하세요.|
|**다른 엔드포인트 보호 응용 프로그램이 실행되고 있음**|다른 엔드포인트 보호 응용 프로그램이 실행되고 있으며 컴퓨터가 정상 상태입니다.|기본적으로 다른 Endpoint Protection 응용 프로그램이 설치되어 있고 Intune에서 해당 응용 프로그램을 검색한 경우 장치가 불안정해질 수 있습니다.|

### <a name="next-steps"></a>다음 단계
이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.
