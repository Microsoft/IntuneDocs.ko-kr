---
title: Endpoint Protection 문제 해결
description: Microsoft Intune Endpoint Protection을 사용하는 동안 문제를 해결합니다.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: dougeby
ms.date: 01/31/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e31df2d2-bb1b-491b-9a71-04e0b18829c1
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 11ee80ee8c13558f109a26a73b50db964ffed4ca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31028291"
---
# <a name="troubleshoot-endpoint-protection-in-microsoft-intune"></a>Troubleshoot Endpoint Protection in Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 섹션의 정보를 사용하면 Microsoft Intune Endpoint Protection 사용 중 발생하는 문제를 해결하는 데 도움이 됩니다. [Windows Defender 문제 해결](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-windows-defender-in-windows-10)에 대한 정보도 검토할 수 있습니다.

이 정보로 문제가 해결되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)을 참조하여 도움을 얻을 수 있는 다른 방법을 찾아보세요.

### <a name="endpoint-protection-error-messages"></a>Endpoint Protection 오류 메시지
이 섹션에서는[Intune 관리 콘솔](https://manage.microsoft.com)의 **Endpoint Protection 상태** 창에 나타나는 다음 오류 및 경고의 잠재적 원인과 해결 방법을 설명합니다.

|상태 항목|잠재적 원인|잠재적 해결 방법|
|---------------|--------------------|-----------------------|
|**Endpoint Protection 엔진을 사용할 수 없음**|Intune Endpoint Protection 엔진이 손상되었거나 삭제되었습니다.|Intune Endpoint Protection 엔진이 손상되면 소프트웨어 업데이트 또는 다시 설치를 시도해 볼 수 있습니다.<br /><br />즉시 업데이트를 실행하려면 Endpoint Protection 클라이언트 소프트웨어(관리 컴퓨터의 작업 표시줄에 있음)에서 **업데이트**를 선택합니다.<br /><br />엔진을 업데이트할 수 없는 경우 Endpoint Protection 엔진을 다시 설치해야 합니다.<br /><br />관리되는 컴퓨터의 제어판에 있는 설치된 프로그램 목록에서 **Microsoft Intune Endpoint Protection 에이전트**를 찾은 다음 해당 응용 프로그램을 제거합니다.<br /><br />다음 업데이트 동기화 중에 Microsoft Online Management 업데이트 관리자에서 누락된 프로그램을 검색하고 예약된 설치 시간에 다시 설치합니다.|
|**Endpoint Protection 사용 안 함**|관리되는 컴퓨터의 사용자 또는 정책을 사용한 관리자가 Intune Endpoint Protection을 사용하지 않도록 설정했습니다.|Endpoint Protection이 사용되지 않도록 설정된 경우 [Intune 관리 콘솔](https://manage.microsoft.com)에서 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리 콘솔](https://manage.microsoft.com)에서 Endpoint Protection을 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **Endpoint Protection 사용** 설정을 변경합니다.<br /><br />또는<br /><br />또는 관리되는 컴퓨터에서 Endpoint Protection을 사용하도록 설정하려면, 알림 영역에서 Intune Endpoint Protection 클라이언트를 시작합니다. 그러면 Endpoint Protection을 사용하도록 설정할지를 묻는 메시지가 표시됩니다.|
|**실시간 보호 사용 안 함**|관리되는 컴퓨터의 관리자(정책 사용) 또는 사용자가 실시간 보호를 사용하지 않도록 설정했습니다.|실시간 보호를 사용하지 않도록 설정된 경우 [Intune 관리 콘솔](https://manage.microsoft.com)에서 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리 콘솔](https://manage.microsoft.com)에서 실시간 보호를 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **실시간 보호 사용** 설정을 **예**로 변경합니다.<br /><br />또는<br /><br />관리되는 컴퓨터에서 실시간 보호를 사용하도록 설정하려면 알림 영역에서 Endpoint Protection 클라이언트 소프트웨어를 시작합니다. 이때 실시간 보호를 사용할지 묻는 메시지가 표시됩니다|
|**다운로드 검색 사용 안 함**|관리 컴퓨터의 사용자 또는 정책을 사용한 관리자가 다운로드 검색을 사용하지 않도록 설정했습니다.|다운로드 검색을 사용하지 않도록 설정된 경우 [Intune 관리 콘솔](https://manage.microsoft.com)에서 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리 콘솔](https://manage.microsoft.com)에서 다운로드 검색을 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **모든 다운로드 검색** 설정을 **예**로 변경합니다.<br /><br />또는<br /><br />관리되는 컴퓨터에서 다운로드 검색을 사용하도록 설정하려면 알림 영역에서 Endpoint Protection 클라이언트 소프트웨어를 시작합니다. **설정** 탭, **실시간 보호**를 차례로 선택하고 **모든 다운로드 검색** 확인란을 선택한 후 **변경 내용 저장**을 선택합니다.|
|**파일 및 프로그램 활동 모니터링 사용 안 함**|관리 컴퓨터의 사용자 또는 정책을 사용한 관리자가 파일 및 프로그램 활동 모니터링을 사용하지 않도록 설정했습니다.|파일 및 프로그램 활동 모니터링을 사용하지 않도록 설정한 경우 [Intune 관리 콘솔](https://manage.microsoft.com) 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리 콘솔](https://manage.microsoft.com)에서 파일 및 프로그램 활동 모니터링을 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **컴퓨터의 파일 및 프로그램 활동 모니터링** 설정을 **예**로 변경합니다.<br /><br />또는<br /><br />관리되는 컴퓨터에서 파일 및 프로그램 활동 모니터링을 사용하도록 설정하려면 알림 영역에서 Endpoint Protection 클라이언트 소프트웨어를 시작합니다. **설정** 탭, **실시간 보호**를 차례로 선택하고 **컴퓨터의 파일 및 프로그램 활동 모니터링** 확인란을 선택한 후 **변경 내용 저장**을 선택합니다.|
|**동작 모니터링 사용 안 함**|관리되는 컴퓨터의 사용자 또는 관리자(정책을 사용하여)가 동작 모니터링을 사용하지 않도록 설정했습니다.|동작 모니터링을 사용하지 않도록 설정된 경우 [Intune 관리 콘솔](https://manage.microsoft.com)에서 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리 콘솔](https://manage.microsoft.com)에서 동작 모니터링을 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **동작 모니터링 사용** 설정을 **예**로 변경한 후 관리되는 컴퓨터를 다시 시작합니다.<br /><br />또는<br /><br />관리되는 컴퓨터에서 동작 모니터링을 사용하도록 설정하려면 알림 영역에서 Endpoint Protection 클라이언트 소프트웨어를 시작합니다. **설정** 탭, **실시간 보호**를 차례로 선택하고 **동작 모니터링 사용** 확인란을 선택한 후 **변경 내용 저장**을 선택합니다. 그런 다음 컴퓨터를 다시 시작합니다.|
|**스크립트 검색 사용 안 함**|관리되는 컴퓨터의 사용자 또는 관리자가(정책을 사용하여) 스크립트 검색을 사용하지 않도록 설정했습니다.|스크립트 검색을 사용하지 않도록 설정된 경우 [Intune 관리 콘솔](https://manage.microsoft.com)에서 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리](https://manage.microsoft.com)에서 스크립트 검색을 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **스크립트 검색 사용** 설정을 **예**로 변경합니다.<br /><br />또는<br /><br />관리되는 컴퓨터에서 스크립트 검색을 사용하도록 설정하려면 알림 영역에서 Endpoint Protection 클라이언트 소프트웨어를 시작합니다. **설정** 탭, **실시간 보호**를 차례로 선택하고 **스크립트 검색 사용** 확인란을 선택한 후 **변경 내용 저장**을 선택합니다.|
|**네트워크 검사 시스템 사용 안 함**|관리 컴퓨터의 정책을 사용한 관리자 또는 사용자가 네트워크 검사 시스템을 사용하지 않도록 설정했습니다.|네트워크 검사 시스템을 사용하지 않도록 설정한 경우 [Intune 관리 콘솔](https://manage.microsoft.com)에서 또는 관리되는 컴퓨터에서 사용하도록 설정할 수 있습니다. 다음 중 하나를 수행합니다.<br /><br />[Intune 관리 콘솔](https://manage.microsoft.com)에서 네트워크 검사 시스템을 사용하도록 설정하려면 **정책** 작업 영역을 연 후 이 컴퓨터에 적용되는 정책에서 **네트워크 검사 시스템 사용** 설정을 **예**로 변경한 후 관리되는 컴퓨터를 다시 시작합니다.<br /><br />또는<br /><br />관리되는 컴퓨터에서 네트워크 검사 시스템을 사용하도록 설정하려면 알림 영역에서 Endpoint Protection 클라이언트 소프트웨어를 시작합니다. **설정** 탭, **실시간 보호**를 차례로 선택하고 **네트워크 검사 시스템 사용** 확인란을 선택한 후 **변경 내용 저장**을 선택합니다. 컴퓨터를 다시 시작하십시오.|
|**맬웨어 정의가 만료됨**|컴퓨터가 오랫동안 인터넷에 연결되지 않았거나 맬웨어 정의가 아직 업데이트되지 않았을 수 있습니다. 이 상태는, 컴퓨터의 맬웨어 정의가 14일 이상 만료된 상태인 경우 나타납니다.|맬웨어 정의가 만료된 경우 [Intune 관리 콘솔](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune) 항목에서 정의를 업데이트할 수 있습니다.|
|**전체 검색 지연**|전체 검색이 14일 동안 완료되지 않았습니다. 이는 전체 검색 중에 컴퓨터를 다시 시작하여 발생할 수 있습니다.|전체 검색이 늦어진 경우 한 번의 전체 검색을 실행하거나 [Intune 관리 콘솔](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)에서 되풀이 전체 검색을 예약할 수 있습니다.|
|**빠른 검색 지연**|빠른 검색이 14일 동안 완료되지 않았습니다. 이는 빠른 검색 중에 컴퓨터를 다시 시작하여 발생할 수 있습니다.|빠른 검색이 늦어진 경우 한 번의 빠른 검색을 실행하거나 [Intune 관리 콘솔](/intune-classic/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client)에서 되풀이 빠른 검색을 예약할 수 있습니다.|
|**다른 끝점 보호 응용 프로그램이 실행되고 있음**|다른 끝점 보호 응용 프로그램이 실행되고 있으며 컴퓨터가 정상 상태입니다.|기본적으로 다른 끝점 보호 응용 프로그램이 설치되어 있는데 Intune에서 해당 응용 프로그램을 감지한 경우 Endpoint Protection이 자동으로 사용되지 않도록 설정됩니다. Intune에서 다른 끝점 응용 프로그램을 감지하지 않으면, Endpoint Protection은 사용하는 상태로 유지됩니다. 자세한 내용은 [Microsoft Intune용 Endpoint Protection을 사용한 Windows PC의 보안 유지 방법](/intune-classic/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)을 참조하세요.|

### <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라 Microsoft 지원에 문의하세요.
