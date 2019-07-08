---
title: 관리되지 않는 디바이스에서 데이터 누수 방지
titleSuffix: Microsoft Intune
description: Microsoft Intune을 사용하여 디바이스에서 회사 데이터에 대한 액세스를 허용하고 데이터 유출로부터 데이터를 보호합니다.
keywords: 데이터 보호 누수 방지 디바이스 O365 Office 365
ms.author: dougeby
author: dougeby
manager: dougeby
ms.date: 01/02/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: b1512c3a-3bbd-4111-a0df-c874a0a335df
ms.reviewer: pchacon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 21aac8bc4f241d2905bd2ba24ecdb8bbda3d1a67
ms.sourcegitcommit: 84c79ceea27f7411528defc5ee8ba35ae2bf473c
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67512290"
---
# <a name="prevent-data-leaks-on-non-managed-devices-using-microsoft-intune"></a>Microsoft Intune을 사용하여 관리되지 않는 디바이스에서 데이터 유출 방지

Office 365에서 호스팅하는 회사 데이터에 대한 액세스를 허용하면 의도적이거나 실수로 데이터가 유출될 위험 없이 사용자가 데이터를 공유하고 저장하는 방법을 제어할 수 있습니다. Microsoft Intune은 사용자 소유 디바이스에서 회사 데이터를 보호하도록 설정한 앱 보호 정책을 제공합니다. 디바이스는 Intune 서비스에 등록할 필요가 없습니다. 

또한 Intune을 사용하여 설정된 앱 보호 정책은 Microsoft 이외의 디바이스 관리 솔루션으로 관리되는 디바이스에서도 작동합니다. 디바이스의 개인 데이터는 수정되지 않으며, 회사 데이터만 IT 부서에서 관리합니다. 

회사 데이터를 보호하기 위해 Windows, iOS 또는 Android를 실행하는 디바이스에서 Office 모바일 앱에 대한 앱 보호 정책을 설정할 수 있습니다. 이러한 정책을 통해 앱 기반 PIN 또는 회사 데이터 암호화와 같은 정책을 설정하거나, 관리되는 앱과 관리되지 않 앱 간에는 고급 설정으로 잘라내기, 복사, 붙여넣기 및 저장을 제한하는 설정이 가능합니다. 또한 사용자가 디바이스를 등록하지 않아도 회사 데이터를 원격으로 초기화할 수도 있습니다. 

Intune 앱 보호 정책은 디바이스 관리와 별개입니다. 앱 보호 정책을 통해 Intune 비관리 및 관리 장치뿐만 아니라 Microsoft MDM이 아닌 솔루션으로 관리되는 장치에서도 Office 모바일 앱을 관리할 수 있습니다. 

## <a name="before-you-begin"></a>시작하기 전에

다음 요구 사항이 충족되면 아래에서 설명하는 작업 계획을 사용할 수 있습니다.
* 회사에서 클라우드로 안전하게 전환할 준비가 되었습니다.
* 회사에서 Office 365 Exchange Online, SharePoint Online, 비즈니스용 OneDrive 또는 Yammer를 사용합니다.
* 회사에서 Microsoft 365, EMS(Enterprise Mobility + Security) 또는 Azure Information Protection에 대한 라이선스를 가지고 있습니다.
* 회사에서 사용자가 회사 소유 또는 개인 소유 Windows, iOS 또는 Android 디바이스의 회사 데이터에 액세스할 수 있도록 허용합니다. 
* 회사에서 개인 소유 디바이스를 디바이스 관리 서비스에 등록하지 않도록 요구하려고 합니다. 

## <a name="action-plan"></a>작업 계획

iOS 및 Android 디바이스의 경우 

1. [앱 보호 정책](app-protection-policy.md)이 작동하는 방법을 알아봅니다.
2. Office 모바일 앱용 [앱 보호 정책을 만들어 배포하는 방법](app-protection-policies.md)을 알아봅니다. 
3. 만들고 배포한 [앱 보호 정책을 모니터링](app-protection-policies-monitor.md)합니다. 

Windows 10 디바이스의 경우 

1. [WIP(Windows Information Protection)가 작동하는 방법](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip)을 알아봅니다. 
2. [Windows 10용 앱 보호 정책](app-protection-policies-configure-windows-10.md)을 구성하도록 준비합니다.
3. [Intune을 사용하여 WIP 앱 보호 정책을 만들고 배포합니다](windows-information-protection-policy-create.md).

## <a name="what-to-tell-employees-and-students"></a>직원 및 학생에게 정보 안내

필요에 따라 추가 정보를 제공하려면 다음 링크를 공유합니다. 
* [iOS 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](app-protection-enabled-apps-ios.md)
* [Android 앱이 앱 보호 정책으로 관리될 때 예상되는 상황](app-protection-enabled-apps-android.md) 

## <a name="next-steps"></a>다음 단계

이와 같은 EMS 또는 다른 EMS나 Office 365 시나리오 등을 사용 및 활성화하기 위한 도움이 필요하시나요? Microsoft 365, Enterprise Mobility + Security 또는 Azure Active Directory Premium에 대한 라이선스를 150개 이상 가지고 있는 경우 [FastTrack 혜택](https://docs.microsoft.com/enterprise-mobility-security/solutions/enterprise-mobility-fasttrack-program)을 사용하세요. 
