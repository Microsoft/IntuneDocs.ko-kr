---
title: Microsoft Intune에서 Mobile Threat Defense 사용
titleSuffix: Microsoft Intune
description: MTD(Mobile Threat Defense) 파트너와 함께 Intune MTD(Mobile Threat Defense)를 사용하여 디바이스 위험에 따라 회사 리소스에 대한 액세스를 보호합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/21/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 97efe5c2445263bba11ee083e89d36fde1986dc1
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71727872"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Intune과 Mobile Threat Defense의 통합이란?
Intune은 규정 준수 정책 및 조건부 액세스 규칙의 정보 소스인 Mobile Threat Defense 공급업체의 데이터를 통합할 수 있습니다. 이 정보를 사용하여 손상된 모바일 디바이스의 액세스를 차단함으로써 Exchange 및 SharePoint 같은 회사 리소스를 보호할 수 있습니다.  

## <a name="what-problem-does-this-solve"></a>이 기능을 통해 어떤 문제가 해결되나요?
Mobile Threat Defense 공급업체의 정보를 통합하면 모바일 플랫폼에 영향을 주는 위협으로부터 회사 리소스를 보호할 수 있습니다.  

일반적으로 기업에서는 PC를 취약성 및 공격으로부터 선제적으로 보호하는 반면, 모바일 디바이스를 모니터링하거나 보호하지 않은 채 내버려 둡니다. 모바일 플랫폼에는 앱 격리 및 소비자 앱 스토어 점검과 같은 기본 제공 보호 기능이 있지만, 이러한 플랫폼은 정교한 공격에 여전히 취약합니다. 디바이스를 사용하여 작업을 처리하고 중요한 정보에 액세스하는 직원이 점점 많아지고 있기 때문에 Mobile Threat Defense 공급업체의 정보는 점점 정교해지는 공격으로부터 디바이스와 리소스를 보호하는 데 도움이 됩니다.  

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 커넥터의 작동 방식

Intune은 Mobile Threat Defense 커넥터를 사용하여 Intune과 고객이 선택한 Mobile Threat Defense 공급업체 간의 통신 채널을 만듭니다. Intune Mobile Threat Defense 파트너는 직관적이고 쉽게 배포할 수 있는 모바일 디바이스용 애플리케이션을 제공합니다. 이러한 애플리케이션은 위협 정보를 능동적으로 검사 및 분석하여 Intune과 공유합니다. Intune은 데이터를 보고 또는 정책 적용 목적으로 사용할 수 있습니다.  

예를 들면 다음과 같습니다. 연결된 Mobile Threat Defense 앱이 Mobile Threat Defense 공급업체에 보고하기를, 네트워크의 전화기가 현재 메시지 가로채기(Man in the Middle) 공격에 취약한 네트워크에 연결되어 있습니다. 이 정보는 적절한 위험 수준(낮음/중간/높음)으로 분류됩니다. 이 위험 수준은 Intune에서 설정한 허용 위험 수준과 비교됩니다. 이 비교 결과에 따라, 디바이스가 손상된 경우 사용자가 선택한 특정 리소스에 대한 액세스 권한이 취소될 수 있습니다.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune은 Mobile Threat Defense를 위해 어떤 데이터를 수집하나요?

사용 설정하면 Intune이 개인 및 회사 소유 디바이스 모두에서 앱 인벤토리 정보를 수집하여 Lookout for Work와 같은 MTD(Mobile Threat Defense) 공급자가 페치할 수 있도록 합니다. iOS 디바이스의 사용자로부터 앱 인벤토리를 수집할 수 있습니다.

이 서비스는 옵트인된 것입니다. 기본적으로 앱 인벤토리 정보는 공유되지 않습니다. Intune 관리자는 앱 인벤토리 정보를 공유하기 전에 서비스 설정에서 iOS 디바이스에 대한 앱 동기화를 설정해야 합니다.

**앱 인벤토리**  
iOS 디바이스용 앱 동기화를 사용하면 회사 및 개인 소유 iOS 디바이스 모두의 인벤토리가 MTD 서비스 공급자에게 전송됩니다. 앱 인벤토리의 데이터에는 다음이 포함됩니다.

- 앱 ID
- 앱 버전
- 앱 짧은 버전
- 앱 이름
- 앱 번들 크기
- 앱 동적 크기
- 앱의 유효성 검사 여부
- 앱이 관리되는지 여부

## <a name="sample-scenarios"></a>샘플 시나리오:

모바일 위협 방어 솔루션에서 디바이스가 감염된 것으로 간주되는 경우

![Mobile Threat Defense 감염된 디바이스를 보여주는 이미지](./media/mobile-threat-defense/MTD-image-1.png)

디바이스를 재구성하면 액세스가 허용됩니다.

![Mobile Threat Defense 감염된 장치를 보여주는 이미지](./media/mobile-threat-defense/MTD-image-2.png)

> [!NOTE] 
> Intune에서 여러 Mobile Threat Defense 공급 업체를 사용하도록 지원되지 않습니다. 여러 MTD 도구를 사용하면 모든 MTD 앱을 설치하도록 강제하고 디바이스에서 위협을 검사합니다.

## <a name="mobile-threat-defense-partners"></a>모바일 위협 방어 파트너

다음을 사용하여 디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스를 보호하는 방법을 알아봅니다.

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [더 향상된 모바일](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
