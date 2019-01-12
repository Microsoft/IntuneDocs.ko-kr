---
title: Exchange Online용 Intune Exchange 커넥터 | Microsoft Intune
description: Intune을 Office 365 Exchange 서비스에 연결하여 Exchange ActiveSync MDM(모바일 디바이스 관리)을 지원합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 9845ed1b809b611975c07c6c8335acd237d845c0
ms.sourcegitcommit: bee072b61cf8a1b8ad8d736b5f5aa9bc526e07ec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53816704"
---
# <a name="configure-the-exchange-service-connector-for-intune-and-exchange-online"></a>Intune 및 Exchange Online용 Exchange 서비스 커넥터 구성
이 문서에서는 Microsoft Intune 서비스를 Exchange Online 또는 새로운 Exchange Online 전용 서비스에 연결하는 방법을 보여줍니다. Exchange Online Dedicated 환경이 **신규** 또는 **기존** 버전인지 확인하려면 계정 관리자에게 문의하세요.

**Service to Service Connector**를 사용하면 EAS(Exchange ActiveSync) 및 Intune 관리 디바이스를 모두 단일 관리 콘솔에서 관리할 수 있습니다.  커넥터는 Exchange Online의 조건부 액세스를 사용하도록 설정할 필요가 없습니다.

## <a name="service-to-service-connector-requirements"></a>Service to Service Connector 요구 사항
**Service to Service Connector**는 Exchange Online 또는 Exchange Online Dedicated만 지원하며 온-프레미스 인프라에 대한 요구 사항은 없습니다. 


|              요구 사항               |                                                                                                            추가 정보                                                                                                            |
|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Exchange Online 구성 및 실행 |                                                                                 [Exchange Online](https://technet.microsoft.com/library/jj200580.aspx)                                                                                 |
|   모바일 디바이스 관리 기관   |                                                       [Microsoft Intune으로 모바일 디바이스 관리 기관 설정](mdm-authority-set.md)                                                       |
|       Microsoft Exchange 버전       |                                                                                      Exchange Online 또는 신규 Exchange Online Dedicated 서비스                                                                                      |
|    Active Directory 동기화    | Intune Connector를 사용하려면 로컬 사용자 및 보안 그룹이 Azure Active Directory의 인스턴스와 동기화되도록 [Active Directory 동기화를 설정](/intune/users-add)해야 합니다. |

### <a name="exchange-cmdlet-requirements"></a>Exchange cmdlet 요구 사항

또한 Intune Exchange 서비스 커넥터에 사용되는 Exchange Online 사용자 계정을 만들어야 합니다. 계정에는 다음과 같은 필수 Windows PowerShell Exchange cmdlet을 실행할 수 있는 권한이 있어야 합니다.

 - Get-ActiveSyncOrganizationSettings, Set-ActiveSyncOrganizationSettings
 - Get-MobileDeviceMailboxPolicy, Set-MobileDeviceMailboxPolicy, New-MobileDeviceMailboxPolicy, Remove-MobileDeviceMailboxPolicy
 - Get-ActiveSyncDeviceAccessRule, Set-ActiveSyncDeviceAccessRule, New-ActiveSyncDeviceAccessRule, Remove-ActiveSyncDeviceAccessRule
 - Get-MobileDeviceStatistics
 - Get-MobileDevice
 - Get-ActiveSyncDeviceClass

## <a name="set-up-the-service-to-service-connector"></a>서비스 간 커넥터 설정

1. Exchange 관리자 권한, [앞에서 설명한](#exchange-cmdlet-requirements) cmdlet에 대한 권한, 유효한 Intune 라이선스 및 전역 관리자 역할을 가진 사용자 계정으로 [Azure Portal](https://portal.azure.com)에 로그인합니다. Microsoft Intune은 현재 로그인된 사용자의 메일 주소를 사용하여 연결을 설정합니다.

2. 왼쪽 메뉴에서 **모든 서비스**를 선택한 다음, 텍스트 상자 필터에 **Intune**을 입력합니다.

3. **Intune**을 선택하여 Microsoft Intune 대시보드를 엽니다. **조건부 액세스**를 선택한 다음, **설정**에서 **Exchange 서비스 커넥터**를 선택합니다.

4.  **조건부 액세스 - Exchange 서비스 커넥터** 페이지에서 **Service to Service Connector 설정**을 선택합니다. 
   
     ![Service to Service Connector 설정 링크 선택을 보여주는 이미지](media/exchange_service_connector.png)

Service to Service Connector에서 자동으로 Exchange Online 또는 신규 Exchange Online Dedicated 환경을 구성하고 동기화합니다.

## <a name="validate-your-exchange-connection"></a>Exchange 연결 확인

Exchange Service to Service Connector를 성공적으로 구성한 후 **조건부 액세스 - Exchange 서비스 커넥터** 페이지에서 Exchange Connector 서버 정보의 유효성을 검사합니다.

**연결 상태** 및 마지막으로 성공한 동기화 시도의 시간과 날짜를 확인할 수도 있습니다.

 