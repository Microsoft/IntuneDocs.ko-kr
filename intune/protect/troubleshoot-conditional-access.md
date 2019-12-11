---
title: 조건부 액세스 문제 해결
titleSuffix: Microsoft Intune
description: 사용자가 Intune 조건부 액세스를 통해 리소스에 액세스하지 못할 때 수행할 작업입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c662de98ffa497c5fbc89ac1b78ed8537ff0d80c
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71732700"
---
# <a name="troubleshoot-conditional-access"></a>조건부 액세스 문제 해결
이 문서에서는 사용자가 조건부 액세스로 보호된 리소스에 대한 액세스를 가져오지 못한 경우 또는 사용자가 보호된 리소스에 액세스할 수 있지만 차단되어야 하는 경우 수행할 작업을 설명합니다.

Intune 및 조건부 액세스를 사용 하 여 다음과 같은 서비스에 대 한 액세스를 보호할 수 있습니다.
- Office 365 서비스 (예: Exchange Online, SharePoint Online 및 Skype for Business Online)
- Exchange 온-프레미스
- 기타 다양 한 서비스

이 기능을 사용하면 Intune에서 등록되고 Intune 관리 콘솔 또는 Azure Active Directory에서 설정한 조건부 액세스 규칙을 준수하는 디바이스만 회사 리소스에 대한 액세스를 제한하도록 할 수 있습니다. 

## <a name="requirements-for-conditional-access"></a>조건부 액세스에 대한 요구 사항

조건부 액세스가 작동하려면 다음 요구 사항을 충족해야 합니다.

- 디바이스는 MDM에 등록되고 Intune에서 관리되어야 합니다.

- 사용자 및 디바이스는 모두 할당된 Intune에서 준수 정책을 준수해야 합니다.

- 기본적으로 사용자에게는 디바이스 준수 정책이 할당되어야 합니다. Intune 관리 포털의 **디바이스 준수** > **준수 정책 설정** 아래에서 **다음으로 할당된 준수 정책이 없는 디바이스 표시** 설정 구성에 따라 달라질 수 있습니다.

- 사용자가 Outlook이 아닌 디바이스의 네이티브 메일 클라이언트를 사용하는 경우 Exchange ActiveSync는 디바이스에서 활성화되어야 합니다. 이 작업은 iOS, Windows Phone 및 Android Knox 디바이스에서 자동으로 발생합니다.

- 온-프레미스 Exchange의 경우 Intune Exchange Connector를 적절히 구성 해야 합니다. 자세한 내용은 [Microsoft Intune에서 Exchange Connector 문제 해결](troubleshoot-exchange-connector.md)을 참조하세요.

- 온-프레미스 Skype의 경우 하이브리드 최신 인증을 구성 해야 합니다. [하이브리드 최신 인증 개요](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview)를 참조 하세요.

Azure Portal 및 디바이스 인벤토리 보고서에서 각 디바이스의 이러한 조건을 확인할 수 있습니다.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>디바이스가 규정을 준수한다고 표시되지만 사용자가 여전히 차단됨

- 적절 한 규정 준수 평가를 위해 사용자에 게 Intune 라이선스가 할당 되어 있는지 확인 합니다.

- 사용자가 받은 격리 이메일의 **지금 시작** 링크를 클릭할 때까지 비 Knox Android 디바이스에 액세스할 권한을 부여할 수 없습니다. 사용자가 이미 Intune에 등록된 경우에도 적용됩니다. 사용자가 휴대폰에 있는 링크에서 이메일을 받지 않은 경우 PC를 사용하여 해당 메일에 액세스하고 해당 디바이스의 이메일 계정에 전달할 수 있습니다.

- 디바이스가 먼저 등록되면 디바이스에 규정 준수 정보가 등록되는 데 시간이 걸릴 수 있습니다. 잠시 기다린 후 다시 시도하세요.

- iOS 디바이스의 경우 기존 이메일 프로필이 해당 사용자에게 할당된 Intune 관리자가 만든 이메일 프로필의 배포를 차단하여 디바이스가 규정을 준수하지 않게 만들 수 있습니다. 이 시나리오에서 회사 포털 앱은 수동으로 구성된 이메일 프로필 때문에 규정을 준수하지 않음을 사용자에게 알리고 해당 프로필을 제거하라는 메시지를 표시합니다. 사용자가 기존 이메일 프로필을 제거하면 Intune 이메일 프로필을 성공적으로 배포할 수 있습니다. 이 문제를 방지하려면 사용자가 등록하기 전에 해당 디바이스에서 기존 이메일 프로필을 제거하도록 지시합니다.

- 디바이스가 준수 확인 상태로 중단되어 사용자가 다른 체크 인을 시작하지 못할 수도 있습니다. 이 상태의 장치가 있는 경우:
  - 디바이스에서 최신 버전의 회사 포털 앱을 사용하는지 확인합니다.
  - 디바이스를 다시 시작합니다.
  - 다른 네트워크에 문제가 지속되는지 확인합니다(예: 셀룰러, Wi-Fi 등).

  문제가 지속되면 [Microsoft Intune에 대한 지원 받기](../fundamentals/get-support.md)에서 설명한 대로 Microsoft 지원에 문의하세요.

- 어떤 Android 디바이스는 암호화된 것처럼 보일 수 있지만 회사 포털 앱은 암호화되지 않은 것으로 인식하고 비준수로 표시합니다. 이 시나리오에서 사용자에게는 디바이스의 시작 암호를 설정하라는 회사 포털 앱의 알림이 표시됩니다. 알림을 누르고 기존 PIN 또는 암호를 확인한 후에 **안전한 시작** 화면에서 **기기 시작 시 PIN 요청** 옵션을 선택한 다음, 회사 포털 앱의 디바이스에 대해 **규정 준수 확인**을 누릅니다. 이제 디바이스가 암호화된 것으로 감지됩니다. 

  > [!NOTE]
  > 일부 디바이스 제조업체에서는 사용자가 설정한 PIN이 아닌 기본 PIN을 사용하여 디바이스를 암호화합니다. Intune에서는 안전하지 않은 기본 PIN을 사용하여 암호화를 확인하고 사용자가 기본이 아닌 새로운 PIN을 만들 때까지 해당 디바이스를 비준수로 표시합니다.

- 등록되고 규정을 준수하는 Android 디바이스가 처음 회사 리소스에 액세스하려고 하면 차단되고 격리 알림이 발생할 수 있습니다. 이러한 경우 회사 포털 앱이 실행되지 않았는지 확인한 다음, 격리 이메일에서 **지금 시작** 링크를 선택하여 평가를 트리거합니다. 조건부 액세스를 처음 사용하는 경우 이 작업을 수행해야 합니다.

- 등록 된 Android 장치에서 "인증서를 찾을 수 없습니다." 라는 메시지가 표시 되 고 O365 리소스에 대 한 액세스 권한이 부여 되지 않습니다. 사용자가 등록된 디바이스에서 다음과 같이 *브라우저 액세스 사용* 옵션을 사용하도록 설정해야 합니다.
  1. 회사 포털 앱을 엽니다.
  2. 세 개의 점(...) 또는 하드웨어 메뉴 단추에서 설정 페이지로 이동합니다.
  3. *브라우저 액세스 사용* 단추를 선택합니다.
  4. Chrome 브라우저에서, Office 365에서 로그아웃하고 Chrome을 다시 시작합니다.  


## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>디바이스가 차단되고 격리 이메일이 수신되지 않음

- 디바이스가 Exchange ActiveSync 디바이스로 Intune 관리 콘솔에 표시되는지 확인합니다. 그렇지 않은 경우 Exchange Connector 문제로 인해 디바이스 검색에 실패할 수도 있습니다. 자세한 내용은 [Intune 온-프레미스 Exchange Connector 문제 해결](troubleshoot-exchange-connector.md)을 참조하세요.

- Exchange Connector에서 디바이스를 차단하기 전에 활성화 (격리) 이메일을 전송합니다. 디바이스가 오프라인 상태이면 활성화 메일을 받지 못할 수도 있습니다. 

- 디바이스에서 이메일 클라이언트가 **폴링** 대신 **푸시**를 사용하여 이메일을 검색하도록 구성되었는지 확인합니다. 그렇다면 사용자가 해당 이메일을 누락할 수 있습니다. **폴링**으로 전환하여 디바이스가 이메일을 수신하는지 확인하세요.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>디바이스가 규정을 준수하지 않았지만 사용자가 차단되지 않음

- Windows PC의 경우 조건부 액세스는 네이티브 이메일 앱, 최신 인증을 사용하는 Office 2013 또는 Office 2016만 차단합니다. Windows PC에서 이전 버전의 Outlook 또는 모든 메일 앱을 차단하려면 [Azure Active Directory 조건부 액세스에 대한 SharePoint Online 및 Exchange Online 설정](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication)에 따른 AAD 디바이스 등록 및 AD FS(Active Directory Federation Services) 구성이 필요합니다.

- 디바이스가 선택적으로 초기화되거나 Intune에서 사용 중지되는 경우 사용 중지한 후 몇 시간 동안 액세스 권한이 계속 있을 수 있습니다. Exchange가 6시간 동안 액세스 권한을 캐시하기 때문입니다. 이 시나리오에서는 사용 중지된 디바이스의 데이터를 보호하는 다른 방법을 고려해야 합니다.

- Intune에 대 한 라이선스가 할당 된 사용자가 로그인 하는 경우 Surface Hub, 대량 등록 및 DEM 등록 된 Windows 장치에서 조건부 액세스를 지원할 수 있습니다. 그러나 올바른 평가를 위해 장치 그룹 (사용자 그룹 아님)에 준수 정책을 배포 해야 합니다.

- 준수 정책 및 조건부 액세스 정책에 대한 할당을 확인합니다. 사용자가 정책이 할당 된 그룹에 없거나 제외 된 그룹에 있는 경우 사용자는 차단 되지 않습니다. 할당된 그룹에 있는 사용자의 디바이스만 규정 준수를 검사합니다.

## <a name="noncompliant-device-is-not-blocked"></a>비규격 디바이스가 차단되지 않음

장치가 호환 되지 않지만 계속 액세스할 수 있는 경우 다음 작업을 수행 합니다.

- 대상 및 제외 그룹을 검토합니다. 사용자가 올바른 대상 그룹에 없거나, 제외 그룹에 있는 경우에는 차단되지 않습니다. 대상 그룹에 있는 사용자의 디바이스만 규정 준수에 대해 확인됩니다.

- 디바이스가 검색 중인지 확인합니다. 사용자가 Exchange 2013 서버에 있는 동안 Exchange Connector가 Exchange 2010 CAS를 가리키고 있나요? 이런 경우 기본 Exchange 규칙이 허용이면 사용자가 대상 그룹에 있더라도 Intune에서 Exchange에 대한 디바이스 연결을 인식할 수 없습니다.

- Exchange에서 디바이스 존재/액세스 상태를 확인합니다.
  - 'Get-ActiveSyncDeviceStatistics -mailbox mbx' PowerShell cmdlet을 사용하여 사서함에 대한 모든 모바일 디바이스 목록을 가져옵니다. 디바이스가 나열되지 않으면 Exchange에 액세스하지 않는 것입니다.
  
  - 디바이스가 나열되면 'Get-CASmailbox -identity:’upn’ | fl' cmdlet을 사용하여 액세스 상태에 대한 자세한 정보를 가져와 Microsoft 지원 서비스에 해당 정보를 제공합니다.

## <a name="next-steps"></a>다음 단계
이 정보가 도움이 되지 않으면 [Microsoft Intune에 대한 지원을 받을](../fundamentals/get-support.md) 수도 있습니다.
