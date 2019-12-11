---
title: Exchange Connector 문제 해결
titleSuffix: Microsoft Intune
description: Intune 온-프레미스 Exchange Connector와 관련된 문제를 해결합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: a7e3c742-295b-40bb-9afa-17f243062500
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 962e66a9fdf6d8abcf6855f645775026ee4db850
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72508850"
---
# <a name="troubleshoot-the-intune-exchange-connector"></a>Intune Exchange Connector 문제 해결

이 문서에서는 Intune Exchange Connector와 관련된 문제를 해결하는 방법을 설명합니다.

## <a name="before-you-start"></a>시작하기 전에

Intune에서 Exchange Connector 문제 해결을 시작 하기 전에 견고한 기반 작업을 수행할 수 있도록 몇 가지 기본적인 정보를 수집 하세요. 이 방법은 문제의 특성을 더 잘 이해 하 고 더 빠르게 해결 하는 데 도움이 될 수 있습니다.

- 프로세스가 설치 요구 사항을 충족 하는지 확인 합니다. [온-프레미스 Intune Exchange 커넥터 설정](exchange-connector-install.md)을 참조하세요.
- 계정에 Exchange 및 Intune 관리자 권한이 모두 있는지 확인 합니다.
- 완전 하 고 정확한 오류 메시지 텍스트, 세부 정보 및 메시지가 표시 되는 위치를 확인 합니다.
- 문제가 시작 된 시기를 확인 합니다. 
  - 커넥터를 처음으로 설정 하 고 있습니까? 
  - 커넥터가 제대로 작동 하 고 실패 하나요?
  - 작동 하 고 있는 경우 Intune 환경, Exchange 환경 또는 connector 소프트웨어를 실행 하는 컴퓨터에서 어떤 변경이 발생 하나요?
- MDM 기관 이란? System Center Configuration Manager 되는 경우 사용 하는 Configuration Manager 버전은 무엇 인가요?
- 어떤 버전의 Exchange를 사용 하 고 있습니까?

### <a name="use-powershell-to-get-more-data-on-exchange-connector-issues"></a>Powershell을 사용하여 Exchange 커넥터에 더 많은 데이터를 가져오는 문제

- 사서함에 대 한 모든 모바일 장치 목록을 가져오려면 `Get-ActiveSyncDeviceStatistics -mailbox mbx`를 사용 합니다.
- 사서함에 대 한 SMTP 주소 목록을 가져오려면 `Get-Mailbox -Identity user | select emailaddresses | fl`를 사용 합니다.
- 디바이스의 액세스 상태에 대한 상세 정보를 가져오려면 다음을 사용합니다. `Get-CASMailbox <upn> | fl`

## <a name="review-the-connector-configuration"></a>커넥터 구성 검토

[온-프레미스 Exchange connector 요구 사항을](exchange-connector-install.md#intune-exchange-connector-requirements) 검토 하 여 사용자 환경 및 커넥터가 올바르게 구성 되어 있는지 확인 합니다. 

### <a name="general-considerations-for-the-connector"></a>커넥터에 대 한 일반적인 고려 사항

- 방화벽 및 프록시 서버에서 Intune Exchange Connector 및 Intune 서비스를 호스트 하는 서버 간의 통신을 허용 하는지 확인 합니다.

- Intune Exchange Connector 및 Exchange 클라이언트 액세스 서버 (CAS)를 호스트 하는 컴퓨터는 도메인에 가입 되어 있고 동일한 LAN에 있어야 합니다. Intune Exchange connector에서 사용 되는 계정에 대해 필요한 권한이 추가 되었는지 확인 합니다.

- 알림 계정은 *자동* 검색 설정을 검색 하는 데 사용 됩니다. Exchange의 Autodisover에 대 한 자세한 내용은 [Exchange Server의 자동 검색 서비스](https://docs.microsoft.com/exchange/architecture/client-access/autodiscover?view=exchserver-2016)를 참조 하세요.

- Intune Exchange Connector는 알림 계정 자격 증명을 사용 하 여 *시작* 링크와 함께 알림 전자 메일 메시지를 보내고 intune에 등록 하는 방식으로 EWS URL에 요청을 보냅니다. 등록 하려면 *시작* 링크를 사용 하는 것은 Android 비 Knox 장치에 대 한 요구 사항입니다. 그렇지 않으면 이러한 장치는 조건부 액세스에 의해 차단 됩니다.

### <a name="common-issues-for-connector-configurations"></a>커넥터 구성에 대 한 일반적인 문제

- **계정 사용 권한**: Microsoft Intune Exchange Connector 대화 상자에서 [필수 Windows PowerShell Exchange cmdlet](exchange-connector-install.md#exchange-cmdlet-requirements)을 실행할 수 있는 적절한 사용 권한이 있는 사용자 계정을 지정했는지 확인합니다.
- **알림 전자 메일 메시지**: 알림을 사용 하도록 설정 하 고 알림 계정을 지정 합니다.
- **클라이언트 액세스 서버 동기화**: exchange connector를 구성할 때 exchange connector를 호스트 하는 서버에서 네트워크 대기 시간이 가장 낮은 ca를 지정 합니다. CAS와 Exchange 커넥터 간의 통신 대기 시간은 특히 Exchange Online Dedicated를 사용할 때 디바이스 검색을 지연시킬 수 있습니다.
- **동기화 일정**: 디바이스를 새로 등록한 사용자는 Exchange 커넥터가 Exchange CAS와 동기화될 때까지 액세스가 지연될 수 있습니다. 전체 동기화는 하루에 한 번 수행되며 델타(빠른) 동기화는 하루에 여러 번 수행됩니다. [수동으로 빠른 동기화 또는 전체 동기화를 강제 수행](exchange-connector-install.md#manually-force-a-quick-sync-or-full-sync)하여 지연을 최소화할 수 있습니다.

## <a name="next-steps"></a>다음 단계
다음 문서는 일반적인 문제 및 특정 오류를 해결 하는 데 도움이 될 수 있습니다.

- [Intune Exchange Connector에 대 한 일반적인 문제를 해결](troubleshoot-exchange-connector-common-problems.md)합니다.
- [Intune Exchange Connector에 대 한 일반적인 오류를 해결](troubleshoot-exchange-connector-common-errors.md)합니다.

지원 또는 Intune 커뮤니티에서 지원 받기:

- Intune 콘솔을 사용 하 여 문제를 해결 하거나 Microsoft에서 지원 사례를 열 수 있도록 [지원 받기](../fundamentals/get-support.md) 를 참조 하세요. 
- [Microsoft Intune 포럼](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)에 문제를 게시 하세요.  
