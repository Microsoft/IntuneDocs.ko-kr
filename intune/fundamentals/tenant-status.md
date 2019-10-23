---
title: Microsoft Intune 테넌트 상태 페이지
titleSuffix: Microsoft Intune
description: Intune 테넌트 상태 페이지를 사용하여 Intune 포털을 종료하지 않고 중요한 테넌트 세부 정보 보기
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/05/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.assetid: 7954a686-25dc-4fce-b395-324816f46d3b
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c79f24d44ad0aed78ed0ae6fce0873a080b2904d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504851"
---
# <a name="use-the-intune-tenant-status-page"></a>Intune 테넌트 상태 페이지 사용
Microsoft Intune 테넌트 상태 페이지는 테넌트에 대한 현재 및 중요 세부 정보를 볼 수 있는 중앙 집중식 허브입니다. 이러한 세부 정보에는 라이선스 가용성 및 사용, 커넥터 상태, Intune 서비스에 대한 중요 통신 정보 등이 포함됩니다.  

대시보드를 보려면 [Intune](https://go.microsoft.com/fwlink/?linkid=2090973)에 로그인한 다음 **테넌트 상태**를 선택합니다.  **도움말 및 지원** 아래에 *테넌트 상태*가 표시됩니다.  

이 페이지는 3개 탭으로 구분됩니다.

## <a name="tenant-details"></a>테넌트 세부 정보
테넌트 세부 정보는 테넌트에 대한 요약 정보를 제공합니다. 테넌트 이름 및 위치, MDM 기관 및 테넌트 서비스 릴리스 번호와 같은 세부 정보를 봅니다. 서비스 릴리스 번호는 Microsoft 문서의 *Intune의 새로운 기능* 문서를 여는 링크입니다. *새로운 기능*에서 Intune 서비스의 최신 기능 및 업데이트를 확인할 수 있습니다.  

이 탭에서 사용 가능한 라이선스 및 사용자에게 할당된 수에 대한 기본 정보를 확인할 수 있습니다. 디바이스의 라이선스는 표시되지 않습니다.

## <a name="connector-status"></a>커넥터 상태
커넥터 상태는 Intune에 대해 사용 가능한 모든 커넥터의 상태를 검토하기 위한 원스톱 위치입니다.  

커넥터는 다음과 같습니다.
- **구성하는 외부 서비스에 대한 연결**입니다. 예를 들어 *Apple Volume Purchase Program* 서비스 및 *Windows Autopilot* 서비스입니다.  이 유형의 커넥터에 대한 상태는 마지막으로 성공한 동기화 시간을 기반으로 합니다.
- *Apple Push Notification Service*(APNS) 인증서와 같은 **관리되지 않는 외부 서비스에 연결하는 데 필요한 인증서 또는 자격 증명**입니다. 이 유형의 커넥터에 대한 상태는 인증서 또는 자격 증명의 만료 타임스탬프를 기반으로 합니다.  

*커넥터 상태* 탭을 열면 비정상 커넥터가 목록의 맨 위에 표시됩니다. 다음은 경고가 있는 커넥터와 정상 커넥터의 목록입니다. 아직 구성하지 않은 커넥터가 마지막에 *사용 안 함*으로 나타납니다.

한 가지 유형의 커넥터가 하나 이상인 경우 상태는 동일한 모든 커넥터에 대한 요약입니다. 최소 정상 상태의 단일 커넥터가 그룹에 대한 상태로 사용됩니다.  

**커넥터 상태:**
- **비정상:**
  - 인증서 또는 자격 증명이 만료됨
  - 마지막 동기화는 3일 이상 전임
- **경고:**
  - 인증서 또는 자격 증명이 7일 내에 만료됨
  - 마지막 동기화는 하루 이상 전임
- **정상:**
  - 인증서 또는 자격 증명이 다음 7일 내에 만료되지 않음
  - 최신 동기화는 하루 미만 전임  

목록에서 커넥터를 선택하면 포털은 해당 커넥터와 관련된 포털 페이지를 표시합니다. 이 커넥터 페이지에서 이전에 구성한 커넥터의 상태를 확인할 수도 있고, 옵션을 선택하여 해당 유형의 새 커넥터를 추가하거나 만들 수 있습니다.

예를 들어 **VPP 만료 날짜** 커넥터를 선택하면 해당 커넥터에 대한 자세한 세부 정보를 볼 수 있는 **iOS 대량 구매 프로그램 토큰** 페이지가 열립니다. 또한 새 구성을 만들거나 기존 구성으로 문제를 해결할 수 있습니다.

## <a name="service-health-dashboard"></a>서비스 상태 대시보드  
서비스 상태 대시보드에서 테넌트에 영향을 주는 *서비스 인시던트*에 대한 세부 정보와 업데이트 및 계획된 변경 내용에 대한 정보를 제공하는 *Intune 뉴스*를 볼 수 있습니다.

### <a name="intune-service-health"></a>Intune Service Health
[Microsoft 365 관리 센터](https://admin.microsoft.com)에 있는 Microsoft 365 Service Health 대시보드 또는 메시지 센터로 이동하지 않고도 활성 인시던트 및 권고에 대한 세부 정보를 봅니다. 테넌트에 영향을 주는 인시던트만 표시됩니다.  

인시던트를 선택하면 인시던트 세부 정보가 테넌트 상태 페이지에 직접 표시됩니다. 지난 권고 및 인시던트를 보려면 **지난 인시던트/권고 확인**을 선택합니다. Microsoft 365 관리 센터가 열리고 테넌트에 대한 지난 30일의 권고 및 인시던트를 볼 수 있습니다.  

*Intune Service Health*에 대한 정보를 보려면 해당 계정이 Azure Active Directory 또는 Microsoft 365 관리 센터에서 **글로벌 관리자** 또는 **서비스 관리자** 역할을 갖고 있어야 합니다. 이러한 사용 권한을 할당하려면 글로벌 관리자 권한으로 [Microsoft 365 관리 센터](https://admin.microsoft.com)에 로그인합니다. **사용자 > 활성 사용자**를 선택한 다음, 액세스가 필요한 계정을 선택합니다. 역할에 대해 **편집**을 선택하고, *서비스 관리자* 또는 *글로벌 관리자*를 선택한 다음, 사용 권한을 할당하는 편집 내용을 **저장**합니다.  

Microsoft 365 관리 센터를 통해 Intune Service Health에 대한 통신 기본 설정만 설정할 수 있습니다.

### <a name="intune-news"></a>Intune 뉴스  
Office 메시지 센터를 이동하지 않고 Intune 서비스 팀의 통신 정보를 봅니다. 통신에는 Intune 서비스에 최근에 발생하거나 테넌트에 대해 진행 중인 변경 내용에 대한 메시지가 포함됩니다.  

기본적으로 가장 최근의 메시지 10개와 활성 메시지가 표시됩니다. 이전 메시지를 보려면 **이전 메시지 보기**를 선택하여 Microsoft 365 관리 센터에서 *메시지 센터*를 엽니다.  

Intune 뉴스에 대한 정보를 보려면 해당 계정이 Azure Active Directory에서 **글로벌 관리자** 또는 **서비스 관리자** 역할을 갖고 있거나 Microsoft 365 관리 포털에서 **메시지 센터 읽기 권한자** 역할을 갖고 있어야 합니다.  이 사용 권한을 할당하려면 관리자 권한으로 [Microsoft 365 관리 센터](https://admin.microsoft.com)에 로그인합니다. **사용자 > 활성 사용자**를 선택한 다음, 액세스가 필요한 계정을 선택합니다. *역할*에 대해 **편집**을 선택하고, *팀 통신 관리자*를 선택한 다음, 사용 권한을 할당하는 편집 내용을 **저장**합니다.  

Microsoft 365 관리 센터를 통해 Intune 뉴스에 대한 통신 기본 설정만 설정할 수 있습니다.
