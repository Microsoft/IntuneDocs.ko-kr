---
title: Microsoft Intune 온-프레미스 Exchange 커넥터 설정
titleSuffix: ''
description: 온-프레미스 Exchange 커넥터를 사용하여 Intune 등록 및 EAS(Exchange Active Sync)에 따라 Exchange 사서함에 장치 액세스를 관리합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a0376ea1-eb13-4f13-84da-7fd92d8cd63c
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c24630dd3cc45b35e6313e9e66db74a548bb0851
ms.sourcegitcommit: cfce9318b5b5a3005929be6eab632038a12379c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51298108"
---
# <a name="set-up-the-intune-on-premises-exchange-connector-in-microsoft-intune-azure"></a>Microsoft Intune Azure에서 Intune 온-프레미스 Exchange Connector 설정

온-프레미스 Exchange Server 환경에서 Intune 조건부 액세스를 사용하여 Exchange 온-프레미스 사서함에 대한 액세스를 허용하거나 차단할 수 있습니다. Exchange Active Sync 온-프레미스 커넥터를 사용하여 Intune을 Exchange 조직에 연결하고 장치 준수 정책과 함께 Intune 조건부 액세스를 설정합니다. 그런 다음, 장치에서 Exchange에 연결하려고 하면 Intune에서 장치가 Intune에 등록되어 있고 호환되는지 확인합니다. Intune에 등록된 장치를 확인하기 위해 온-프레미스 Exchange Connector에서 Exchange Server의 EAS(Exchange Active Sync) 레코드를 Intune 레코드에 매핑합니다. 이 작동 방법에 대한 자세한 내용은 [Intune에서 조건부 액세스를 사용하는 일반적인 방법이란?](conditional-access-intune-common-ways-use.md)을 참조하세요.

> [!IMPORTANT]
> 이제 Intune은 구독당 여러 온-프레미스 Exchange Connector를 지원합니다. 둘 이상의 온-프레미스 Exchange 조직이 있는 경우 각 Exchange 조직에 대해 별도의 커넥터를 설정할 수 있습니다.

Microsoft Intune에서 온-프레미스 Exchange Server와 통신할 수 있도록 하는 연결을 설정하는 일반적인 단계는 다음과 같습니다.

1.  Azure Portal에서 Intune 온-프레미스 Exchange Connector를 다운로드합니다.
2.  Exchange Connector를 온-프레미스 Exchange 조직의 컴퓨터에 설치하고 구성합니다.
3.  Exchange 연결 유효성을 검사합니다.
4. Intune에 연결하려는 각 Exchange 조직에 대해 이러한 단계를 반복합니다.

## <a name="intune-on-premises-exchange-connector-requirements"></a>Intune 온-프레미스 Exchange Connector 요구 사항
다음 표에는 온-프레미스 Exchange Connector를 설치하는 컴퓨터에 대한 요구 사항이 나와 있습니다.


|            요구 사항             |                                                                                                                                                                                                        추가 정보                                                                                                                                                                                                        |
|------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         운영 체제          |                                                               Intune은 Windows Server 2008 SP2 64비트, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 또는 Windows Server 2016의 모든 버전을 실행하는 컴퓨터에서 온-프레미스 Exchange Connector를 지원합니다.<br /><br />이 커넥터는 Server Core 설치에서 지원되지 않습니다.                                                                |
|         Microsoft Exchange         |                                                                           온-프레미스 커넥터를 사용하려면 Microsoft Exchange 2010 SP3 이상 또는 레거시 Exchange Online Dedicated가 필요합니다. Exchange Online Dedicated 환경이 <strong>신규</strong>인지 아니면 <strong>레거시</strong> 구성 상태인지 확인하려면 계정 관리자에게 문의하세요.                                                                           |
| 모바일 장치 관리 기관 |                                                                                                                              [Intune으로 모바일 장치 관리 기관 설정](https://docs.microsoft.com/intune-classic/deploy-use/prerequisites-for-enrollment#step-2-mdm-authority-set).                                                                                                                               |
|              하드웨어              |                                                                                                                                                     커넥터를 설치하는 컴퓨터에는 1.6GHz CPU, 2GB RAM 및 10GB의 사용 가능한 디스크 공간이 필요합니다.                                                                                                                                                      |
|  Active Directory 동기화  |                                                                                      커넥터를 사용하여 Exchange Server에 Intune을 연결하려면, 먼저 로컬 사용자 및 보안 그룹이 Azure Active Directory의 인스턴스와 동기화되도록 [Active Directory 동기화를 설정](users-add.md)해야 합니다.                                                                                      |
|        추가 소프트웨어         |                                                                                                                                           커넥터를 호스트하는 컴퓨터에 Microsoft .NET Framework 4.5 및 Windows PowerShell 2.0 전체 설치를 설치해야 합니다.                                                                                                                                           |
|              Network (네트워크)               | 커넥터를 설치하는 컴퓨터는 Exchange 서버를 호스트하는 도메인과 트러스트 관계에 있는 도메인에 있어야 합니다.<br /><br />이 컴퓨터에서는 포트 80 및 443을 사용하여 방화벽 및 프록시 서버를 통해 Intune 서비스에 액세스할 수 있도록 구성해야 합니다. Intune에서 사용되는 도메인은 manage.microsoft.com, &#42;manage.microsoft.com, &#42;.manage.microsoft.com 등입니다. |

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 요구 사항

온-프레미스 Exchange Connector에서 사용되는 Active Directory 사용자 계정을 만들어야 합니다. 계정에는 다음과 같은 필수 Windows PowerShell Exchange cmdlet을 실행할 수 있는 권한이 있어야 합니다.


 -   Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 -   Get-CasMailbox, Set-CasMailbox
 -   Get-ActiveSyncMailboxPolicy, Set-ActiveSyncMailboxPolicy, New-ActiveSyncMailboxPolicy, Remove-ActiveSyncMailboxPolicy
 -   Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 -   Get-ActiveSyncDeviceStatistics
 -   Get-ActiveSyncDevice
 -   Get-ExchangeServer
 -   Get-ActiveSyncDeviceClass
 -   Get-Recipient
 -   Clear-ActiveSyncDevice, Remove-ActiveSyncDevice
 -   Set-ADServerSettings
 -   Get-Command

## <a name="download-the-on-premises-exchange-connector-software-installation-package"></a>온-프레미스 Exchange Connector 소프트웨어 설치 패키지 다운로드

1. 온-프레미스 Exchange Connector에 지원되는 Windows Server 운영 체제에서 [Azure Portal](http://portal.azure.com)을 열고, 온-프레미스 Exchange Server의 관리자이며 Exchange Server를 사용하기 위한 라이선스가 있는 사용자 계정으로 로그인합니다.

2. 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune**을 선택하고, Intune 대시보드가 열리면 **온-프레미스 액세스**를 선택합니다.

4. **설치** 아래에서 **Exchange ActiveSync 커넥터**를 선택한 다음, **온-프레미스 커넥터 다운로드**를 선택합니다.

5.  온-프레미스 Exchange Connector는 열거나 저장할 수 있는 압축(.zip) 폴더에 포함되어 있습니다. **파일 다운로드** 대화 상자에서 **저장**을 선택하여 이 압축(ZIP) 폴더를 안전한 위치에 저장합니다.

    > [!IMPORTANT]
    > 온-프레미스 Exchange Connector 폴더 내의 파일을 이동하거나 이름을 바꾸지 마세요. 폴더의 콘텐츠를 이동하거나 이름을 바꾸면 Exchange Connector 설치가 실패합니다.

## <a name="install-and-configure-the-intune-on-premises-exchange-connector"></a>Intune 온-프레미스 Exchange Connector 설치 및 구성
Intune 온-프레미스 Exchange Connector를 설치하려면 다음 단계를 수행합니다. 여러 개의 Exchange 조직이 있는 경우 설치하려는 추가 Exchange Connector마다 이러한 단계를 반복합니다.

1. 온-프레미스 Exchange Connector에 지원되는 운영 체제에서 **Exchange_Connector_Setup.zip**의 파일을 안전한 위치로 추출합니다.

2. 파일이 추출되면 압축을 푼 폴더를 열고 **Exchange_Connector_Setup.exe**를 두 번 클릭하여 온-프레미스 Exchange Connector를 설치합니다.

   > [!IMPORTANT]
   > 대상 폴더가 안전한 위치가 아닌 경우 온-프레미스 커넥터 설치가 완료되면 **MicrosoftIntune.accountcert** 인증서 파일을 삭제해야 합니다.

3. **Microsoft Intune Exchange Connector** 대화 상자에서 **온-프레미스 Microsoft Exchange Server** 또는 **호스트된 Microsoft Exchange Server**를 선택합니다.

   ![Exchange Server 유형을 선택하는 경우를 보여주는 이미지](./media/intune-sa-exchange-connector-config.png)

   온-프레미스 Exchange Server의 경우 **클라이언트 액세스 서버** 역할을 호스팅하는 Exchange Server의 서버 이름 또는 정규화된 도메인 이름을 제공합니다.

   Hosted Exchange Server에 대해 Exchange 서버 주소를 지정합니다. Hosted Exchange Server URL을 확인하려면

   1. Office 365용 웹에서 Outlook을 엽니다.

   2. 왼쪽 위에 있는 **?** 아이콘을 선택하고 **정보**를 선택합니다.

   3. **POP 외부 서버** 값을 찾습니다.

   4. **프록시 서버**를 선택하여 Hosted Exchange Server의 프록시 서버 설정을 지정합니다.
       1. **모바일 장치 정보를 동기화는 경우 프록시 서버 사용**을 선택합니다.

       2. 서버에 액세스하는 데 사용할 **프록시 서버 이름** 및 **포트 번호** 를 입력합니다.

       3. 프록시 서버에 액세스하기 위해 사용자 자격 증명을 제공해야 하는 경우 **자격 증명을 사용하여 프록시 서버에 연결**을 선택합니다. 그런 다음 **도메인\사용자** 및 **암호**를 입력합니다.

       4. **확인**을 선택합니다.

   5. **사용자(도메인\사용자)** 및 **암호** 필드에 Exchange Server에 연결하는 데 필요한 자격 증명을 입력합니다.

   6.  사용자의 Exchange Server 사서함에 알림을 보내는 데 필요한 자격 증명을 입력합니다. 이 사용자를 알림에만 전용할 수 있습니다. 알림 사용자는 알림을 이메일로 보낼 수 있도록 Exchange 사서함이 필요합니다. 이러한 알림은 Intune에서 조건부 액세스 정책을 통해 구성할 수 있습니다.  

       자동 검색 서비스 및 Exchange 웹 서비스가 Exchange 클라이언트 액세스 서버에 구성되어 있는지 확인합니다. 자세한 내용은 [Client Access server](https://technet.microsoft.com/library/dd298114.aspx)(클라이언트 액세스 서버)를 참조하세요.

   7.  Intune이 Exchange Server에 액세스할 수 있도록 **암호** 필드에 이 계정의 암호를 입력합니다.

   8. **연결**을 선택합니다.

   > [!NOTE]
   > 연결을 구성하는 데 몇 분 정도 걸릴 수 있습니다.

구성하는 동안 Exchange Connector에서 인터넷에 액세스할 수 있도록 프록시 설정을 저장합니다. 프록시 설정이 변경되면 업데이트된 프록시 설정이 Exchange Connector에 적용되도록 Exchange Connector를 다시 구성해야 합니다.

Exchange Connector에서 연결이 설정되면 Exchange에서 관리되는 사용자와 연결된 모바일 장치가 자동으로 동기화되고 Exchange Connector에 추가됩니다. 이 동기화를 완료하는 데는 다소 시간이 걸릴 수 있습니다.

> [!NOTE]
> 온-프레미스 Exchange Connector를 설치한 경우와 어떤 시점에 Exchange 연결을 삭제한 경우에는 설치된 컴퓨터에서 온-프레미스 Exchange Connector를 제거해야 합니다.

## <a name="install-connectors-for-multiple-exchange-organizations"></a>여러 Exchange 조직에 대한 커넥터 설치
Intune은 구독당 여러 개의 온-프레미스 Exchange Connector를 지원합니다. 여러 Exchange 조직이 있는 테넌트의 경우 각 Exchange 조직마다 하나의 커넥터를 설치할 수 있습니다. .zip 폴더를 한 번 다운로드한 다음, 각 Exchange 조직에 대해 이전 섹션의 단계에 따라 조직의 서버에서 설치 프로그램을 추출하고 실행합니다.

다음 섹션에서 설명하는 고가용성, 모니터링 및 수동 동기화 기능은 Intune에 연결된 각 Exchange 조직에서 지원됩니다.

## <a name="on-premises-exchange-connector-high-availability-support"></a>온-프레미스 Exchange Connector 고가용성 지원 
Exchange Connector는 지정된 CAS를 사용하여 Exchange에 연결한 후 다른 CAS를 검색할 수 있습니다. 기본 CAS를 사용할 수 없게 되면 커넥터는 기본 CAS를 사용할 수 있을 때까지 다른 CAS(사용 가능한 경우)로 장애 조치(failover)됩니다. 이 기능은 기본적으로 켜져 있습니다. 다음 절차를 사용하여 이 기능을 끌 수 있습니다.
1. Exchange Connector가 설치된 서버에서 %*ProgramData*%\Microsoft\Windows Intune Exchange Connector로 이동합니다. 
2. 텍스트 편집기를 사용하여 **OnPremisesExchangeConnectorServiceConfiguration.xml**을 엽니다.
3. &lt;IsCasFailoverEnabled&gt;**true**&lt;/IsCasFailoverEnabled&gt;를 &lt;IsCasFailoverEnabled&gt;**false**&lt;/IsCasFailoverEnabled&gt;로 변경하여 기능을 사용하지 않도록 설정합니다.    


## <a name="monitor-the-exchange-connector-activity"></a>Exchange Connector 작업 모니터링

Exchange Connector가 성공적으로 구성되면 연결 상태 및 마지막으로 성공한 동기화 시도를 볼 수 있습니다. Exchange Connector 연결의 유효성을 검사하려면 다음을 수행합니다.

1. Intune 대시보드에서 **온-프레미스 액세스**를 선택합니다.
2. **설치** 아래에서 **Exchange ActiveSync 커넥터**를 선택하여 각 Exchange Connector에 대한 연결 상태를 확인합니다.

마지막으로 성공한 동기화 시도의 시간과 날짜를 확인할 수도 있습니다.

### <a name="system-center-operations-manager-scom-management-pack"></a>SCOM(System Center Operations Manager) 관리 팩

Intune 1710 릴리스부터 [Exchange Connector 및 Intune 용 SCOM 관리 팩](https://www.microsoft.com/download/details.aspx?id=55990&751be11f-ede8-5a0c-058c-2ee190a24fa6=True&e6b34bbe-475b-1abd-2c51-b5034bcdd6d2=True&fa43d42b-25b5-4a42-fe9b-1634f450f5ee=True)을 사용할 수 있습니다. 이렇게 하면 문제를 해결해야 할 때 Exchange 커넥터를 모니터링하는 여러 가지 방법이 있습니다.

## <a name="manually-force-a-quick-sync-or-full-sync"></a>수동으로 빠른 동기화 또는 전체 동기화 강제 적용
온-프레미스 Exchange Connector는 정기적으로 EAS와 Intune 장치 레코드를 자동으로 동기화합니다. 장치의 준수 상태가 변경되면 자동 동기화 프로세스가 정기적으로 레코드를 업데이트하여 장치 액세스를 차단하거나 허용할 수 있습니다.

   - **빠른 동기화**는 하루에 여러 번 정기적으로 수행됩니다. 빠른 동기화는 마지막 동기화 이후 변경된 Intune 사용 허가 및 온-프레미스 Exchange 조건부 액세스 대상 사용자에 대한 장치 정보를 검색합니다.

   - **전체 동기화**는 기본적으로 하루에 한 번만 수행됩니다. 전체 동기화는 모든 Intune 사용 허가 및 온 프레미스 Exchange 조건부 액세스 대상 사용자에 대한 장치 정보를 검색합니다. 또한 전체 동기화는 Exchange Server 정보를 검색하고, Azure Portal의 Intune에서 지정한 구성이 Exchange Server에서 업데이트되도록 합니다. 

Intune 대시보드에서 다음 단계를 통해 **빠른 동기화** 또는 **전체 동기화** 옵션을 사용하여 커넥터에서 동기화를 실행하도록 할 수 있습니다.

   1. Intune 대시보드에서 **온-프레미스 액세스**를 선택합니다.
   2. **설치** 아래에서 **Exchange Active Sync 커넥터**를 선택합니다.
   3. 동기화하려는 커넥터를 선택한 다음, **빠른 동기화** 또는 **전체 동기화**를 선택합니다.

## <a name="next-steps"></a>다음 단계
[Exchange 온-프레미스에 대해 조건부 액세스 정책 만들기](conditional-access-exchange-create.md)
