---
title: 조건부 액세스 문제 해결
description: 사용자가 Intune 조건부 액세스를 통해 리소스에 액세스하지 못할 때 수행할 작업입니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 10/24/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: eb27605108feb3a2db3072d4a8b7a296f0f74cfc
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31025147"
---
# <a name="troubleshoot-conditional-access"></a>조건부 액세스 문제 해결

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

일반적으로 사용자는 메일 또는 SharePoint에 액세스하려고 하고 등록하라는 메시지가 표시됩니다. 그런 후에는 회사 포털로 연결됩니다.

이 항목에서는 사용자가 Intune 조건부 액세스를 통해 리소스에 액세스하지 못할 때 수행할 작업을 설명합니다.


## <a name="the-basics-for-success-in-conditional-access"></a>조건부 액세스 성공에 대한 기본 사항

조건부 액세스가 작동하려면 다음과 같은 조건이 충족되어야 합니다.

-   장치는 Intune에서 관리되어야 합니다.
-   장치를 AAD(Azure Active Directory)에 등록해야 합니다. 일반적인 환경에서 이 등록은 Intune 등록 중 자동으로 수행됩니다.
-   장치는 장치 및 장치 사용자에 대해 Intune 준수 정책을 준수해야 합니다.  준수 정책이 없는 경우에는 Intune 등록만 해도 괜찮습니다.
-   Exchange ActiveSync는 사용자가 Outlook이 아닌 장치의 네이티브 메일 클라이언트를 통해 메일을 검색하는 경우 장치에서 활성화되어야 합니다.     이 작업은 iOS, Windows Phone 및 Android/KNOX 표준 장치에서 자동으로 발생합니다.
-   Intune Exchange Connector를 제대로 구성해야 합니다. 자세한 내용은 [Microsoft Intune에서 Exchange Connector 문제 해결](troubleshoot-exchange-connector.md)을 참조하세요.

Azure 관리 포털 및 장치 인벤토리 보고서에서 각 장치에 대해 이러한 조건을 확인할 수 있습니다.

## <a name="enrollment-issues"></a>등록 문제

 -  장치가 등록되지 않으므로 등록을 하면 문제가 해결됩니다.
 -  사용자가 장치를 등록했으나 작업 공간에 연결되지 못했습니다. 사용자는 회사 포털에서 등록을 업데이트해야 합니다.

## <a name="compliance-issues"></a>규정 준수 문제

- 장치가 Intune 정책에 맞지 않습니다. 일반적인 문제는 암호화 및 암호 요구 사항입니다. 사용자는 회사 포털로 리디렉션되며 여기서 규정을 준수하도록 장치를 구성할 수 있습니다.
- 장치에 대해 규정 준수 정보가 등록되는 데 시간이 소요될 수 있습니다. 잠시 기다린 후 다시 시도하세요.
- iOS 장치의 경우:
  - 사용자가 만든 기존 메일 프로필에서는 Intune 관리자가 만든 프로필 배포가 차단됩니다. iOS 사용자는 일반적으로 메일 프로필을 만든 후에 등록을 하므로 이것은 일반적인 문제입니다. 회사 포털에서는 수동으로 구성된 메일 프로필 때문에 규정에 맞지 않음을 사용자에게 알리며, 프로필을 제거하라는 메시지를 표시합니다. 사용자는 Intune 프로필을 배포할 수 있도록 메일 프로필을 제거해야 합니다. 이 문제를 방지하려면 메일 프로필을 설치하지 않은 상태에서 등록을 하고 Intune의 프로필 배포를 허용할 것을 지시합니다.
  - iOS 장치가 규정 준수 확인 상태로 국한되어 사용자가 다른 체크 인을 시작하지 못할 수도 있습니다. 회사 포털을 다시 시작하면 이 문제가 해결될 수도 있으며, 준수 상태는 Intune에서 장치 상태를 반영합니다. 장치 동기화를 통해 모든 데이터가 수집되면 규정 준수 확인이 빨라져 평균 0.5초가 걸리지 않게 됩니다.

    일반적으로 장치가 이 상태로 유지되는 이유는 서비스 연결에 문제가 발생하거나 동기화가 오래 걸리기 때문입니다.  장치를 다시 시작해도 다른 네트워크 구성(셀룰러, Wi-Fi, VPN)에서 문제가 지속되면, SSP가 장치에서 최신 상태인지 확인한 후 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)에 설명된 대로 Microsoft 지원 서비스에 문의하세요.

- Android 장치:
   - 어떤 Android 장치는 암호화된 것처럼 보이지만 회사 포털 앱에서 암호화되지 않은 것으로 인식됩니다. 
    
       -   이 상태에 있는 장치는 사용자가 안전한 시작 암호를 설정해야 합니다. 회사 포털 앱에서 사용자에게 장치의 시작 암호를 설정하라는 내용의 장치 알림을 표시합니다. 장치 알림을 탭하고 기존 PIN 또는 암호를 확인한 후에 **안전한 시작** 화면에서 **기기 시작 시 PIN 요청** 옵션을 선택합니다. 그런 다음 회사 포털 앱에서 그 장치의 **준수 확인** 단추를 탭합니다. 이제 장치가 암호화된 것으로 감지됩니다.
    
       -   일부 장치 제조업체에서는 사용자가 설정한 비밀 PIN이 아닌 기본 PIN을 사용하여 장치를 암호화합니다. 악의적인 사용자가 물리적으로 장치에 액세스할 수 있게 되었을 때 장치에 있는 데이터가 위험해질 수 있기 때문에 기본 PIN을 사용하는 암호화 방법은 Intune에서 보안이 약한 것으로 인식됩니다. 이 문제가 우려될 경우는 [앱 보호 정책](/intune-classic/deploy-use/azure-portal-for-microsoft-intune-mam-policies)을 사용합니다.

## <a name="policy-issues"></a>정책 문제

규정 준수 정책을 만들고 메일 정책에 연결할 경우 두 정책이 동일한 사용자에게 배포되어야 하므로 어떤 그룹에 어떤 정책을 배포할지 계획할 때는 주의해야 합니다. 정책이 하나만 적용된 사용자는 해당 장치가 규정을 준수하지 않을 가능성이 높습니다.


## <a name="exchange-activesync-issues"></a>Exchange ActiveSync 문제

### <a name="compliant-android-device-gets-quarantine-notice"></a>규격 Android 장치에서 격리 알림이 발생함
- 회사 리소스에 액세스하려고 할 때, 등록되었으며 규정을 준수하는 Android 장치에서 여전히 격리 알림이 표시될 수 있습니다. **시작** 링크를 선택하기 전에 리소스에 액세스하려고 하면 회사 포털이 열리지 않는다는 사실을 알아야 합니다. 사용자는 회사 포털을 닫고, 리소스 액세스를 다시 시도한 다음 **시작** 링크를 선택해야 합니다.

### <a name="retired-device-continues-to-have-access"></a>사용 중지된 장치는 계속 액세스 권한이 있습니다.
- Exchange Online을 사용하는 경우 사용 중지된 장치는 사용이 중지된 이후에도 몇 시간 정도 계속 액세스할 수도 있습니다. Exchange가 6시간 동안 액세스 권한을 캐시하기 때문입니다. 이 시나리오에서는 사용 중지된 장치의 데이터를 보호하는 다른 방법을 고려해야 합니다.

### <a name="device-is-compliant-and-registered-with-aad-but-still-blocked"></a>장치가 규격이고 AAD에 등록되어 있으나 여전히 차단됨
- 경우에 따라 AAD에 대한 EASID(Exchange ActiveSync ID)의 프로비전이 지연됩니다. 이 문제의 일반적인 원인은 제한 동작이므로 잠시 기다린 후 다시 시도하세요.

### <a name="device-blocked"></a>장치가 차단됨

장치는 활성화 메일을 받지 않고도 조건부 액세스를 통해 차단될 수 있습니다.

- 장치를 격리하거나 차단하는 기본 Exchange 규칙이 있나요? 기본 규칙에서 장치를 차단 또는 격리하는 경우 장치는 Exchange Connector에서 활성화 메일을 받을 수 없게 됩니다. 이것은 설계된 사항입니다.
- 알림 계정이 기본 구성에 설명된 대로 제대로 구성되어 있나요?
- 장치가 Exchange ActiveSync 장치로 Intune 관리 콘솔에 있나요? 그렇지 않은 경우 Exchange Connector 동기화 문제로 인해 해당 장치 검색에 실패할 수도 있습니다. Exchange ActiveSync 장치가 Exchange에서 검색되지 않음을 참조하세요.
- Exchange Connector 로그에서 sendemail 작업과 오류를 확인하세요. 검색할 명령의 예로 알림 계정에서 사용자 메일로 SendEmail이 있습니다.
- Exchange Connector에서 장치를 차단하기 전에 활성화 메일이 전송됩니다. 장치가 오프라인이면 활성화 메일을 받지 못할 수도 있습니다. 장치 메일 클라이언트에 폴링 대신 푸시를 사용하는 메일 검색이 있는지 확인합니다. 폴링을 사용하면 사용자가 메일을 놓칠 수도 있습니다. 폴링으로 전환하여 장치가 메일을 받는지 확인하세요.

## <a name="noncompliant-device-not-blocked"></a>비규격 장치가 차단되지 않음

규격이 아니지만 계속 액세스 권한이 있는 장치가 있는 경우 다음 단계를 수행합니다.

- 대상 및 제외 그룹을 검토합니다. 사용자가 올바른 대상 그룹에 없거나, 제외 그룹에 있는 경우에는 차단되지 않습니다. 대상 그룹에 있는 사용자의 장치만 규정 준수에 대해 확인됩니다.
- 장치가 검색 중인지 확인합니다. 사용자가 Exchange 2013 서버에 있는 동안 Exchange Connector가 Exchange 2010 CAS를 가리키고 있나요? 이런 경우 기본 Exchange 규칙이 허용이면 사용자가 대상 그룹에 있더라도 Intune에서 Exchange에 대한 장치 연결을 인식할 수 없습니다.
- Exchange에서 장치 존재/액세스 상태를 확인합니다.
    - 다음 PowerShell cmdlet을 사용하여 사서함에 대한 모든 모바일 장치 목록을 가져옵니다. "Get-ActiveSyncDeviceStatistics -mailbox mbx" 장치가 나열되지 않으면 Exchange에 액세스하지 않는 것입니다.
    - 장치가 나열되면 Get-CASmailbox -identity:’upn’ | fl cmdlet을 사용하여 액세스 상태에 대한 자세한 정보를 가져와 Microsoft 지원 서비스에 해당 정보를 제공합니다.

## <a name="before-you-open-a-support-ticket"></a>지원 티켓을 열기 전에
이러한 문제 해결 절차로도 문제가 해결되지 않으면 OWA 사서함 로그 또는 Exchange Connector 로그 등 Microsoft 지원 서비스에 정보를 제공하라는 메시지가 나타날 수 있습니다.

### <a name="collecting-owa-mailbox-logs"></a>OWA 사서함 로그 수집

1. OWA를 통해 로그온하고 오른쪽 위 모서리에서 사용자 이름 옆의 설정(톱니 모양) 기호를 선택합니다.
2. **옵션**을 선택합니다.
3. 왼쪽의 열에서 **전화**(**모바일 장치**로 표시될 수도 있음)를 선택합니다.
4. 위쪽 메뉴에서 **모바일 장치**를 선택합니다.
5. 목록에서 장치를 선택하고 **로깅 시작**을 선택합니다.
6. 팝업 대화 상자에서 확인 메시지가 표시되면 **예**를 선택합니다.
7. 문제를 유발한 작업을 수행하여 재현합니다.
8. 1-2분 정도 기다린 후 OWA의 전화 번호 목록으로 돌아갑니다. 목록에서 사용자 전화가 선택되어 있는지 확인하고 그 다음 최상위 메뉴에서 **로그 검색**을 선택합니다.
9. 본인이 보낸 첨부 파일이 포함된 메일을 받아야 합니다. 지원 티켓을 개설할 때 해당 메일 콘텐츠를 Microsoft 지원 서비스에 제공합니다.

### <a name="exchange-connector-logs"></a>Exchange Connector 로그

#### <a name="general-log-information"></a>일반 로그 정보
Exchange Connector 로그를 보려면 [서버 추적 뷰어 도구](<https://msdn.microsoft.com/library/ms732023(v=vs.110).aspx>')를 사용합니다. 이 도구를 사용하려면 Windows Server SDK를 다운로드해야 합니다.

>[!NOTE]
>로그는 C:\ProgramData\Microsoft\Windows Intune Exchange Connector\Logs에 있습니다. 로그는 *Connector0.log*에서 시작하여 *Connector29.log*로 끝나는 일련의 로그 파일 30개에 포함되어 있습니다. 10MB의 데이터가 누적되면 한 로그에서 다른 로그로 롤오버됩니다. 로그가 Connector29로 이동하면 다시 Connector0부터 시작되며 이전 로그 파일을 덮어씁니다.

#### <a name="locating-sync-logs"></a>동기화 로그 찾기

- **full sync**를 검색하여 로그에서 전체 동기화를 찾습니다. 전체 동기화의 시작 부분에 다음 텍스트가 표시됩니다.

  '명령 처리 중: 시간 필터(전체 동기화)를 사용하지 않고 <number>명의 사용자에 대한 모바일 장치 목록을 가져오고 있습니다.

  전체 동기화 로그의 끝부분은 다음과 같습니다.

  시간 필터(전체 동기화)를 사용하지 않고 4명의 사용자에 대한 모바일 장치 목록을 가져왔습니다. 세부 사항: 인벤토리 명령 결과 - 동기화된 장치: 0 명령 ID: commandIDGUID' Exchange 상태: '서버 상태 '이름: 'PowerShellExchangeServer: <Name=mymailservername>' 상태: 연결됨','

- **quick sync**를 검색하여 로그에서 빠른(델타) 동기화를 찾습니다.

##### <a name="exceptions-in-get-next-command"></a>Get next 명령 예외
Exchange Connector 로그에서 **Get next 명령**의 예외를 확인하고 이 예외를 Microsoft 지원 서비스에 제공합니다.

#### <a name="verbose-logging"></a>자세한 정보 로깅

자세한 정보 로깅을 사용하려면

1.  Exchange Connector 추적 구성 파일을 엽니다. 이 파일은: %ProgramData%\Microsoft\Windows Intune Exchange Connector\TracingConfiguration.xml에 있습니다.
2.  OnPremisesExchangeConnectorService 키를 사용하여 TraceSourceLine을 찾습니다.
3.  아래에 표시된 대로 **SourceLevel** 노드 값을 **Warning ActivityTracing**(기본값)에서 **Verbose ActivityTracing**으로 변경합니다.

    <TraceSourceLine> <Key xsi:type="xsd:string">OnPremisesExchangeConnectorService</Key> <Value xsi:type="TraceSource"> <SourceLevel>All</SourceLevel> <Listeners> <Listener> <ListenerType>CircularTraceListener</ListenerType> <SourceLevel>Verbose ActivityTracing</SourceLevel> <FileSizeQuotaInBytes>10000000</FileSizeQuotaInBytes> <FileName>Microsoft\Windows Intune Exchange Connector\Logs\Connector.svclog</FileName> <FileQuota>30</FileQuota> </Listener> </Listeners> </Value>
    </TraceSourceLine>



### <a name="next-steps"></a>다음 단계
문제 해결 정보가 도움이 되지 않는 경우 [Microsoft Intune에 대한 지원을 받는 방법](how-to-get-support-for-microsoft-intune.md)의 설명에 따라 Microsoft 지원에 문의하세요.
