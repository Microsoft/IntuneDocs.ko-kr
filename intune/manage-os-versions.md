---
title: Microsoft Intune을 사용하여 운영 체제 버전 관리
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 여러 플랫폼에서 운영 체제 버전을 관리하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/02/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 361ef17b-1ee0-4879-b7b1-d678b0787f5a
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: b490d5ff083d344a1b39d27a2298503bdfa1f130
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67044910"
---
# <a name="manage-operating-system-versions-with-intune"></a>Intune을 사용하여 운영 체제 버전 관리
최신 모바일 및 데스크톱 플랫폼에서 주요 업데이트, 패치 및 새 버전은 빠른 속도로 출시됩니다. Windows에서는 업데이트와 패치를 완벽하게 관리할 수 있는 컨트롤이 있지만, iOS 및 Android와 같은 다른 플랫폼에서는 최종 사용자가 프로세스에 참여해야 합니다.  Microsoft Intune에는 다양한 플랫폼에서 운영 체제 버전 관리를 구성하는 데 도움이 되는 기능이 있습니다.

Intune은 다음과 같은 일반적인 시나리오를 처리하는 데 도움이 됩니다. 
- 최종 사용자의 디바이스에 있는 운영 체제 버전을 확인합니다.
- 새 운영 체제 릴리스의 유효성을 검사하는 동안 디바이스의 조직 데이터에 대한 액세스를 제어합니다.
- 최종 사용자가 조직에서 승인한 최신 운영 체제 버전으로 업그레이드하도록 권장하거나 요구합니다.
- 조직 전체의 롤아웃을 새 운영 체제 버전으로 관리합니다.
  
## <a name="operating-system-version-control-using-intune-mobile-device-management-mdm-enrollment-restrictions"></a>Intune MDM(모바일 디바이스 관리) 등록 제한을 사용하여 운영 체제 버전 제어
Intune MDM 등록 제한을 사용하면 디바이스 등록을 허용하기 전에 클라이언트 디바이스 요구 사항을 정의할 수 있습니다. 목표는 최종 사용자가 조직 리소스에 액세스하기 전에 준수 디바이스만 등록하도록 요구하는 것입니다. 디바이스 요구 사항에는 지원되는 플랫폼에 허용되는 최소 및 최대 운영 체제 버전이 모두 포함됩니다.
 
![플랫폼 구성 제한 블레이드](./media/os-version-platform-configurations.png) 
 
### <a name="in-practice"></a>실제 사례:
조직에서는 디바이스 유형 제한을 사용하여 다음 설정을 통해 조직 리소스에 대한 액세스를 제어합니다. 
1. 최소 운영 체제 버전을 사용하여 조직의 현재 플랫폼 및 지원되는 플랫폼에서 최종 사용자를 유지합니다. 
2. 최대 운영 체제를 지정하지 않거나(제한 없음) 조직에서 마지막으로 유효성이 검사된 버전으로 설정하여 최신 운영 체제 릴리스에 대한 내부 테스트 시간을 허용합니다.

자세한 내용은 [디바이스 유형 제한 설정](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)을 참조하세요.
 
## <a name="operating-system-version-reporting-and-compliance-with-intune-mdm-device-compliance-policies"></a>운영 체제 버전 보고 및 Intune MDM 디바이스 준수 정책 준수
Intune MDM 디바이스 준수 정책에서 제공하는 도구는 다음과 같습니다. 
- 준수 규칙 지정
- 보고를 통해 준수 상태 보기
- 디바이스 격리 및 조건부 액세스를 통한 비준수에 대한 작업

등록 제한과 마찬가지로 디바이스 준수 정책에는 최소 및 최대 운영 체제 버전이 모두 포함됩니다. 또한 정책에는 사용자가 준수에 대한 유예 기간을 제공하는 준수 타임라인이 있습니다. 디바이스 준수 정책을 통해 등록된 최종 사용자 디바이스에서 조직 정책을 준수하도록 유지합니다.

![디바이스 준수 - 비준수 디바이스에 대한 작업](./media/os-version-actions-noncompliance.png) 

### <a name="in-practice"></a>실제 사례:
조직에서는 등록 제한과 동일한 시나리오에 대한 디바이스 준수 정책을 사용합니다. 이러한 정책을 통해 사용자가 조직에서 유효성이 검사된 현재 운영 체제 버전을 유지합니다. 최종 사용자 디바이스에서 정책을 준수하지 않는 경우 최종 사용자가 조직에서 지원되는 운영 체제 범위 내에 있을 때까지 조건부 액세스를 통해 조직 리소스에 대한 액세스가 차단될 수 있습니다. 최종 사용자에게 정책을 준수하지 않는다고 알리고 액세스 권한을 다시 얻기 위한 단계가 제공됩니다.   

자세한 내용은 [디바이스 준수 시작](https://docs.microsoft.com/intune/device-compliance-get-started)을 참조하세요.
 
## <a name="operating-system-version-controls-using-intune-app-protection-policies"></a>Intune 앱 보호 정책을 사용하여 운영 체제 버전 제어    
Intune 앱 보호 정책 및 MAM(모바일 애플리케이션 관리) 액세스 설정을 사용하면 앱 계층에서 최소 운영 체제 버전을 지정할 수 있습니다. 이를 통해 최종 사용자가 자신의 운영 체제를 지정한 최소 버전으로 업데이트하도록 알리고 권장하거나 요구할 수 있습니다.
 
다음 두 가지 옵션이 있습니다. 
- **경고** - 경고는 지정한 버전 이하의 운영 체제 버전을 사용하는 디바이스에서 애플리케이션 보호 정책 또는 MAM 액세스 설정을 통해 앱을 열면 최종 사용자에게 업그레이드해야 함을 알립니다. 앱 및 조직 데이터에 대한 액세스가 허용됩니다.
  ![Android 업데이트 경고 대화 상자의 이미지](./media/os-version-update-warning.png) 

- **차단** - 차단은 지정한 버전 이하의 운영 체제 버전을 사용하는 디바이스에서 애플리케이션 보호 정책 또는 MAM 액세스 설정을 통해 앱을 열면 최종 사용자에게 업그레이드해야 함을 알립니다. 앱 및 조직 데이터에 대한 액세스가 허용되지 않습니다.
  ![앱 액세스가 차단됨 대화 상자의 이미지](./media/os-version-access-blocked.png)

### <a name="in-practice"></a>실제 사례:
조직에서는 앱을 최신 상태로 유지해야 하는 필요성에 대해 최종 사용자를 교육하는 방법으로 앱을 열거나 다시 시작할 때 앱 보호 정책 설정을 사용합니다. 구성 예에서는 현재 버전 - 1인 경우 최종 사용자에게 경고하고, 현재 버전 - 2인 경우 최종 사용자가 차단됩니다.
 
자세한 내용은 [앱 보호 정책을 만들고 할당하는 방법](https://docs.microsoft.com/intune/app-protection-policies)을 참조하세요.

## <a name="managing-a-new-operating-system-version-rollout"></a>새 운영 체제 버전 롤아웃 관리
이 문서에서 설명하는 Intune 기능을 사용하여 정의한 타임라인 내에서 조직을 새 운영 체제 버전으로 전환할 수 있습니다. 다음 단계에서는 7일 내에 사용자를 운영 체제 v1에서 운영 체제 v2로 전환하는 샘플 배포 모델을 제공합니다.
- **1단계**: 등록 제한을 사용하여 디바이스를 등록하기 위한 최소 버전으로 운영 체제 v2를 요구합니다. 이렇게 하면 새 최종 사용자 디바이스가 등록 시 정책을 준수하는지 확인할 수 있습니다.
- **2a단계**: Intune 앱 보호 정책을 사용하여 앱을 열거나 다시 시작할 때 운영 체제 v2가 필요하다고 사용자에게 경고합니다.
- **2b단계**: 디바이스 준수 정책을 사용하여 디바이스에서 준수하기 위한 최소 버전으로 운영 체제 v2를 요구합니다. 준수하지 않을 경우 **작업**을 사용하여 7일 간의 유예 기간을 허용하고 최종 사용자에게 타임라인과 요구 사항이 포함된 이메일 알림을 보냅니다.
  -  이러한 정책은 앱 보호 정책을 사용하도록 설정된 앱에 대해 앱을 열 때 전자 메일 또는 Intune 회사 포털을 통해 최종 사용자에게 기존 디바이스를 업데이트해야 함을 알립니다.
  - 준수 보고를 실행하여 준수하지 않는 사용자를 확인할 수 있습니다. 
- **3a단계**: Intune 앱 보호 정책을 사용하여 디바이스에서 운영 체제 v2를 실행하지 않는 경우 앱을 열거나 다시 시작할 때 사용자를 차단할 수 있습니다.
- **3b단계**: 디바이스 준수 정책을 사용하여 디바이스에서 준수하기 위한 최소 버전으로 운영 체제 v2를 요구합니다.
  - 이러한 정책을 사용하려면 디바이스에서 조직 데이터에 계속 액세스할 수 있도록 디바이스를 업데이트해야 합니다. 보호된 서비스가 디바이스 조건부 액세스와 함께 사용되면 차단됩니다. 앱 보호 정책을 사용하도록 설정된 앱은 열거나 조직 데이터에 액세스할 때 차단됩니다.

## <a name="next-steps"></a>다음 단계
조직의 운영 체제 버전을 관리하려면 다음 리소스를 사용합니다. 

- [디바이스 유형 제한 설정](https://docs.microsoft.com/intune/enrollment-restrictions-set#set-device-type-restrictions)
- [디바이스 준수 시작](https://docs.microsoft.com/intune/device-compliance-get-started)
- [앱 보호 정책을 만들고 할당하는 방법](https://docs.microsoft.com/intune/app-protection-policies)
