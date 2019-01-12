---
title: Exchange 커넥터 문제 해결 | Microsoft Intune
description: Intune 온-프레미스 Exchange Connector와 관련된 문제를 해결합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fecdda5467c83ab12ca921e86259884171e07819
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816551"
---
# <a name="troubleshoot-the-intune-on-premises-exchange-connector"></a>Intune 온-프레미스 Exchange Connector 문제 해결

이 문서에서는 Intune 온-프레미스 Exchange Connector와 관련된 문제를 해결하는 방법을 설명합니다.

## <a name="steps-for-checking-the-connector-configuration"></a>커넥터 구성 확인 단계 

[Intune 온-프레미스 Exchange Connector 설정](exchange-connector-install.md)을 확인하여 커넥터가 올바르게 구성되었는지 확인합니다. 다음은 몇 가지 일반적인 문제입니다. 수정한 후 문제가 해결되었는지 확인합니다.

 - Microsoft Intune Exchange Connector 대화 상자에서 [필수 Windows PowerShell Exchange cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements)을 실행할 수 있는 적절한 사용 권한이 있는 사용자 계정을 지정했는지 확인합니다.
- 알림을 사용하도록 설정하고 알림 계정을 지정합니다.
 - Exchange Connector를 구성할 경우 Exchange Connector를 호스팅하는 서버와 최대한 가까이 있는 CAS(클라이언트 액세스 서버)를 지정합니다. CAS와 Exchange Connector 간의 통신 대기 시간은 특히 Exchange Online Dedicated를 사용할 때 디바이스 검색을 지연시킬 수 있습니다.
 - 디바이스를 새로 등록한 사용자는 Exchange Connector가 Exchange CAS와 동기화될 때까지 액세스가 지연될 수 있습니다. 전체 동기화는 하루에 한 번 수행되며 델타(빠른) 동기화는 하루에 여러 번 수행됩니다.  [수동으로 빠른 동기화 또는 전체 동기화를 강제 수행](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)하여 지연을 최소화할 수 있습니다.
 
## <a name="exchange-activesync-device-not-discovered-from-exchange"></a>Exchange ActiveSync 디바이스가 Exchange에서 검색되지 않음
[Exchange Connector 활동을 모니터링](exchange-connector-install.md#on-premises-exchange-connector-high-availability-support)하여 Exchange Connector가 Exchange 서버와 동기화하는 중인지 확인합니다. 디바이스가 연결된 후 전체 동기화 또는 빠른 동기화가 성공적으로 완료되면 아래에 나열된 다른 가능한 문제를 확인할 수 있습니다. 동기화가 수행되지 않으면 동기화 로그를 수집하고 지원 요청에 연결하여 전달하세요.

 - 사용자에게 Intune 라이선스가 있는지 확인합니다. 그렇지 않으면 Exchange Connector가 디바이스를 검색하지 않습니다.
 - 사용자의 기본 SMTP 주소가 Azure AD(Active Directory)의 해당 UPN과 다른 경우 Exchange Connector는 해당 사용자의 모든 디바이스를 검색하지 않습니다. 문제를 해결하려면 기본 SMTP 주소를 수정합니다.
 - 사용자 환경에 Exchange 2010 및 Exchange 2013 사서함 서버가 모두 있는 경우 Exchange Connector가 Exchange 2013 CAS를 가리키는 것이 좋습니다. 그렇지 않은 경우 Exchange Connector가 Exchange 2010 CAS와 통신하도록 설정되어 있으면 Exchange Connector는 Exchange 2013 사용자의 디바이스를 검색하지 않습니다. 
- Exchange Online Dedicated 환경의 경우 Powershell cmdlet을 실행할 때 커넥터가 이 CAS와만 통신하기 때문에, 초기 설치 중 전용 환경에서 Exchange Connector가 Exchange 2013 CAS(Exchange 2010 CAS 해당 안 됨)를 가리켜야 합니다.


## <a name="using-powershell-to-get-more-data-on-exchange-connector-issues"></a>Powershell을 사용하여 Exchange Connector에 더 많은 데이터를 가져오는 문제
- 사서함에 대한 모든 모바일 디바이스 목록을 가져오려면 Get-ActiveSyncDeviceStatistics -mailbox mbx를 사용합니다.
- 사서함에 대한 SMTP 주소 목록을 가져오려면 Get-Mailbox -Identity user | select emailaddresses | fl을 사용합니다.
- 디바이스의 액세스 상태에 대한 상세 정보를 가져오려면 Get-CASMailbox <upn> | fl을 사용합니다.

### <a name="next-steps"></a>다음 단계
이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](get-support.md) 수도 있습니다.
