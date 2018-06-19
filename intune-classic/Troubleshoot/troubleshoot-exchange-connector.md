---
title: Exchange Connector 문제 해결
description: Intune Exchange 커넥터와 관련된 문제를 해결합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 07/26/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: c5cb5465-fd8e-4524-83b9-ccdf3393b6dc
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0eef4e2ae3792c601bd4a32cd041d7d041091cca
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31015033"
---
# <a name="troubleshoot-the-exchange-connector"></a>Exchange Connector 문제 해결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

이 항목에서는 Intune Exchange Connector와 관련될 수 있는 문제를 해결하는 방법에 대해 설명합니다.

## <a name="steps-for-checking-the-connector-configuration"></a>Connector 구성 확인 단계 

Exchange Connector의 구성을 확인한 다음 문제가 해결되었는지 살펴봅니다.

- Exchange Connector의 초기 설치 시 알림 계정이 지정되어야 합니다.
- Exchange Connector 서비스 계정에는 Exchange Connector에서 사용하는 PowerShell cmdlet 실행에 필요한 적절한 권한이 있어야 합니다.
- Exchange Connector를 구성할 경우 Exchange Connector를 호스팅하는 서버와 최대한 가까이 있는 CAS(클라이언트 액세스 서버)를 지정합니다. CAS와 Exchange Connector 간의 통신 대기 시간은 장치 검색 지연으로 인해 발생할 수 있으며 특히 O365 전용을 사용하는 경우 발생할 수 있습니다.
- Exchange CAS와의 Exchange Connector 동기화 작업 간에는 시간 지연이 발생합니다. 전체 동기화는 하루에 한 번, 델타(빠른) 동기화는 2시간마다 수행됩니다. 새로 등록된 장치를 사용하는 사용자는 액세스 시 지연을 경험할 가능성이 있습니다.
- 
  ## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync 장치가 Exchange에서 검색되지 않음
  Exchange Connector가 Exchange 서버와 동기화하는 중인지 확인합니다. 이렇게 하려면 전체 동기화 또는 델타 동기화에 대한 로그를 찾아 봅니다. Exchange Connector 로그를 참조하세요. 장치가 가입한 이후 전체 동기화 또는 델타 동기화가 완료되면 문제의 출처로 해당 장치를 제거한 것입니다. 동기화가 수행되지 않으면 동기화 로그를 수집하여 지원 요청에 첨부하여 전달하세요.

- 사용자에게 Intune 라이선스가 없는 경우 Exchange Connector에서는 장치가 검색되지 않습니다.
- 사용자의 기본 SMTP 주소가 AAD의 해당 UPN과 다른 경우 Exchange Connector는 해당 Intune/AAD 사용자에 대해 어떤 장치도 검색하지 않습니다. 기본 SMTP 주소를 수정하세요.
- 검색 주기 동안 Exchange Connector에서 통신하는 CAS가 Exchange 2010 CAS이고, Exchange 2010 및 2013 사서함 서버가 모두 있는 경우 Exchange Connector는 Exchange 2013 사용자의 장치를 검색하지 않습니다. 이 문제를 해결하려면 Exchange Connector가 Exchange 2013 CAS를 가리키도록 구성합니다.  이 문제는 주로 O365 전용 토폴로지와 관련이 있지만 모범 사례로 다른 토폴로지에서 Exchange 2013 CAS를 가리키는 것이 좋습니다.
- Exchange 전용(O365 전용) 환경에서는 초기 설치 중 전용 환경에서 Exchange Connector가 Exchange 2013(2010 해당 안 됨)을 가리켜야 합니다. Powershell cmdlet을 실행할 때 이 CAS와만 통신하게 되기 때문입니다.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Powershell을 사용하여 Exchange Connector에 더 많은 데이터를 가져오는 문제
- 사서함에 대한 모든 모바일 장치 목록을 가져오려면 Get-ActiveSyncDeviceStatistics -mailbox mbx를 사용합니다.
- 사서함에 대한 SMTP 주소 목록을 가져오려면 Get-Mailbox -Identity user | select emailaddresses | fl을 사용합니다.
- 장치의 액세스 상태에 대한 상세 정보를 가져오려면 Get-CASMailbox <upn> | fl을 사용합니다.

### <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라 Microsoft 지원에 문의하세요.
