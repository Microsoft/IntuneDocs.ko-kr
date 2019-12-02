---
title: Intune Exchange connector에 대 한 일반적인 문제 해결
titleSuffix: Microsoft Intune
description: 온-프레미스 Microsoft Intune Exchange connector에 대 한 일반적인 문제를 해결 하 고 해결 합니다.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/26/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: de365312a7d293527c3c83fbbd84ab55de41d530
ms.sourcegitcommit: 23e9c48348a6eba494d072a2665b7481e5b5c84e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2019
ms.locfileid: "74547683"
---
# <a name="resolve-common-problems-with-the-intune-exchange-connector"></a>Intune Exchange connector와 관련 된 일반적인 문제 해결
 
이 문서는 intune 관리자가 Intune Exchange connector 작업과 관련 된 일반적인 문제를 해결 하는 데 도움이 될 수 있습니다.

문제 해결을 시작 하기 전에 커넥터에 대 한 기본 정보는 [Intune 온-프레미스 Exchange Connector 문제 해결](troubleshoot-exchange-connector.md) 을 참조 하세요. 또한 커넥터 구성에 대 한 일반적인 문제를 검토 합니다.

## <a name="an-exchange-activesync-device-isnt-discovered-from-exchange"></a>Exchange ActiveSync 디바이스는 Exchange에서 검색되지 않습니다.

Exchange ActiveSync 장치가 exchange에서 검색 되지 않는 경우 exchange [connector 작업을 모니터링](exchange-connector-install.md#on-premises-intune-exchange-connector-high-availability-support) 하 여 exchange Connector가 exchange server와 동기화 되 고 있는지 확인 하십시오. 장치가 조인 된 이후에 동기화가 수행 되지 않은 경우 동기화 로그를 수집 하 여 지원 요청에 연결 합니다. 장치를 조인한 후 전체 동기화 또는 빠른 동기화가 성공적으로 완료 되 면 다음 문제를 확인 합니다.

- 사용자에 게 Intune 라이선스가 있는지 확인 합니다. 그렇지 않은 경우 Exchange connector는 장치를 검색 하지 않습니다.

- 사용자의 기본 SMTP 주소가 Azure AD(Active Directory)의 해당 UPN(사용자 기본 이름)과 다른 경우 Exchange 커넥터는 해당 사용자의 모든 디바이스를 검색하지 않습니다. 문제를 해결하려면 기본 SMTP 주소를 수정합니다.

- 사용자 환경에 Exchange 2010 및 Exchange 2013 사서함 서버가 모두 있는 경우 Exchange 커넥터가 Exchange 2013 CAS(클라이언트 액세스 서버)를 가리키는 것이 좋습니다. Exchange 커넥터가 Exchange 2010 CAS와 통신하도록 설정되어 있으면 Exchange 커넥터는 Exchange 2013에서 사용자 디바이스를 검색하지 않습니다.

- Exchange Online 전용 환경의 경우 초기 설치 중에 전용 환경에서 exchange connector가 exchange 2013 CAS (Exchange 2010 CA 아님)를 가리켜야 합니다. 커넥터는 PowerShell cmdlet을 실행할 때 Exchange 2013 CA와만 통신 합니다.

## <a name="problems-with-the-notification-email-message"></a>알림 전자 메일 메시지의 문제

Android Knox를 실행 하지 않는 장치에서 온-프레미스 사서함에 대 한 조건부 액세스를 지원 하려면 Intune Exchange connector에서 보내는 "지금 시작" 전자 메일 메시지에서 Intune 등록을 시작 해야 합니다. 메시지에서 등록을 시작 하면 장치가 모든 플랫폼 (Exchange, Azure AD, Intune)에서 고유한 ActiveSyncID를 수신 합니다.

사용자는 다음과 같은 이유로 알림 전자 메일 메시지를 받지 못할 수 있습니다.

- 알림 계정이 잘못 설정 되었습니다.
- 알림 계정에 대 한 자동 검색에 실패 했습니다.
- 전자 메일 메시지 Request to Send EWS (Exchange 웹 서비스)가 실패 했습니다.

전자 메일 알림 문제를 해결 하려면 다음 섹션을 검토 하십시오.

### <a name="check-the-notification-account-that-retrieves-autodiscover-settings"></a>자동 검색 설정을 검색 하는 알림 계정 확인

1. 자동 검색 서비스 및 EWS(Exchange 웹 서비스)가 Exchange 클라이언트 액세스 서비스에 구성되어 있는지 확인합니다. 자세한 내용은 [클라이언트 액세스 서비스](https://docs.microsoft.com/Exchange/architecture/client-access/client-access) 및 [Exchange Server의 자동 검색 서비스](https://docs.microsoft.com/Exchange/architecture/client-access/autodiscover?view=exchserver-2019)를 참조 하세요.

2. 알림 계정이 다음 요구 사항을 충족 하는지 확인 합니다.

   - 계정에는 Exchange 온-프레미스 서버에서 호스팅하는 활성 사서함이 있습니다.

   - 계정 UPN은 SMTP 주소와 일치 합니다.

3. 자동 검색을 사용 하려면 Exchange 클라이언트 액세스 서버를 가리키는 **Autodiscover.SMTPdomain.com** (예: Autodiscover.contoso.com)에 대 한 dns 레코드를 포함 하는 dns 서버가 필요 합니다. 레코드를 확인 하려면 *Autodiscover.SMTPdomain.com* 대신 FQDN을 지정 하 고 다음 단계를 수행 합니다.

   1. 명령 프롬프트에서 *NSLOOKUP*을 입력 합니다.

   2. *Autodiscover.SMTPdomain.com*를 입력 합니다. 출력은 다음 이미지와 비슷해야 합니다. ![Nslookup 결과](./media/troubleshoot-exchange-connector-common-problems/nslookup-results.png
      )

   https://testconnectivity.microsoft.com 인터넷에서 자동 검색 서비스를 테스트할 수도 있습니다. 또는 Microsoft 연결 분석기 도구를 사용 하 여 로컬 도메인에서 테스트 합니다. 자세한 내용은 [Microsoft 연결 분석기 도구](https://docs.microsoft.com/previous-versions/office/exchange-remote-connectivity/jj851141(v=exchg.80))를 참조 하세요.


### <a name="check-autodiscovery"></a>자동 검색 확인

자동 검색에 실패 하면 다음 단계를 수행 합니다.

1. [올바른 자동 검색 DNS 레코드를 구성](https://docs.microsoft.com/previous-versions/exchange-server/exchange-150/mt473798(v=exchg.150))합니다.

2. Intune Exchange connector 구성 파일에서 EWS URL을 하드 코딩 합니다.

   1. EWS URL을 결정 합니다. Exchange의 기본 EWS URL은 `https://<mailServerFQDN>/ews/exchange.asmx`있지만 URL이 다를 수 있습니다. Exchange 관리자에 게 문의 하 여 사용자 환경에 맞는 올바른 URL을 확인 하십시오.

   2. ‘OnPremisesExchangeConnectorServiceConfiguration.xml’ 파일을 편집합니다.  기본적으로이 파일은 Exchange connector를 실행 하는 컴퓨터의 *%ProgramData%\Microsoft\Windows Intune Exchange connector* 에 있습니다. 텍스트 편집기에서 파일을 열고 다음 줄을 변경 하 여 사용자 환경에 대 한 EWS URL을 반영 합니다. `<ExchangeWebServiceURL>https://<YourExchangeHOST>/EWS/Exchange.asmx</ExchangeWebServiceURL>`

3. 파일을 저장한 다음 컴퓨터 또는 Microsoft Intune Exchange Connector 서비스를 다시 시작합니다.

>[!NOTE]
> 이 구성에서 Intune Exchange connector는 자동 검색 사용을 중지 하 고 대신 EWS URL에 직접 연결 합니다.

## <a name="next-steps"></a>다음 단계

특정 오류에 대 한 도움말을 보려면 [Intune Exchange connector에 대 한 일반적인 오류를 해결](troubleshoot-exchange-connector-common-errors.md)해 보세요.

지원을 받으려면 Intune 커뮤니티에서 도움을 받으세요.

- Intune 콘솔을 사용 하 여 문제를 해결 하거나 Microsoft에서 지원 사례를 열려면 [지원 받기](../fundamentals/get-support.md) 를 참조 하세요.
- [Microsoft Intune 포럼](https://social.technet.microsoft.com/Forums/home?forum=microsoftintuneprod)에 문제를 게시 하세요.