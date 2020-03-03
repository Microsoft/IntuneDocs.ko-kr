---
title: Microsoft Intune에서 Mobile Threat Defense 사용
titleSuffix: Microsoft Intune
description: MTD(Mobile Threat Defense) 파트너와 함께 Intune MTD(Mobile Threat Defense)를 사용하여 디바이스 위험에 따라 회사 리소스에 대한 액세스를 보호합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/29/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: davidra
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f056f665ebee0d1e2315129a4fe739b2c490ca98
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514849"
---
# <a name="mobile-threat-defense-integration-with-intune"></a>Intune에 Mobile Threat Defense 통합

Intune은 디바이스 준수 정책 및 디바이스 조건부 액세스 규칙의 정보 원본인 MTD(Mobile Threat Defense) 공급업체의 데이터를 통합할 수 있습니다. 이 정보를 사용하여 손상된 모바일 디바이스의 액세스를 차단함으로써 Exchange 및 SharePoint 같은 회사 리소스를 보호할 수 있습니다.

Intune은 Intune 앱 보호 정책을 사용하여 등록되지 않은 디바이스의 원본과 동일한 이 데이터를 사용할 수 있습니다. 따라서 관리자는 이 정보를 사용하여 [Microsoft Intune 보호 앱](~/apps/apps-supported-intune-apps.md) 내에서 회사 데이터를 보호하고 블록 또는 선택 초기화를 실행할 수 있습니다.

## <a name="protect-corporate-resources"></a>회사 리소스 보호

MTD 공급업체의 정보를 통합하면 모바일 플랫폼에 영향을 주는 위협으로부터 회사 리소스를 보호할 수 있습니다.  

일반적으로 기업에서는 PC를 취약성 및 공격으로부터 선제적으로 보호하는 반면, 모바일 디바이스를 모니터링하거나 보호하지 않은 채 내버려 둡니다. 모바일 플랫폼에는 앱 격리 및 소비자 앱 스토어 점검과 같은 기본 제공 보호 기능이 있지만, 이러한 플랫폼은 정교한 공격에 여전히 취약합니다. 디바이스를 사용하여 작업을 처리하고 중요한 정보에 액세스하는 직원이 점점 많아지고 있기 때문에 MTD 공급업체의 정보는 점점 정교해지는 공격으로부터 디바이스와 리소스를 보호하는 데 도움이 됩니다.

## <a name="intune-mobile-threat-defense-connectors"></a>Intune 모바일 위협 방어 커넥터

Intune은 Mobile Threat Defense 커넥터를 사용하여 Intune과 고객이 선택한 MTD 공급업체 간의 통신 채널을 만듭니다. Intune MTD 파트너는 직관적이고 쉽게 배포할 수 있는 모바일 디바이스용 애플리케이션을 제공합니다. 이러한 애플리케이션은 위협 정보를 능동적으로 검사 및 분석하여 Intune과 공유합니다. Intune은 데이터를 보고 또는 정책 적용 목적으로 사용할 수 있습니다.

예를 들면 다음과 같습니다. 연결된 MTD 앱이 MTD 공급업체에 보고하기를, 네트워크의 전화기가 현재 메시지 가로채기(Man in the Middle) 공격에 취약한 네트워크에 연결되어 있습니다. 이 정보는 적절한 위험 수준(낮음/중간/높음)으로 분류됩니다. 이 위험 수준은 Intune에서 설정한 허용 위험 수준과 비교됩니다. 이 비교 결과에 따라, 디바이스가 손상된 경우 사용자가 선택한 특정 리소스에 대한 액세스 권한이 취소될 수 있습니다.

## <a name="data-that-intune-collects-for-mobile-threat-defense"></a>Mobile Threat Defense를 위한 Intune의 수집 데이터

사용 설정하면 Intune이 개인 및 회사 소유 디바이스 모두에서 앱 인벤토리 정보를 수집하여 Lookout for Work와 같은 MTD 공급자가 페치할 수 있도록 합니다. iOS 디바이스의 사용자로부터 앱 인벤토리를 수집할 수 있습니다.

이 서비스는 옵트인된 것입니다. 기본적으로 앱 인벤토리 정보는 공유되지 않습니다. Intune 관리자는 앱 인벤토리 정보를 공유하기 전에 Mobile Threat Defense 커넥터 설정에서 **iOS 디바이스에 대한 앱 동기화**를 설정해야 합니다.

**앱 인벤토리**  
iOS/iPadOS 디바이스용 앱 동기화를 사용하면 회사 및 개인 소유 iOS/iPadOS 디바이스 모두의 인벤토리가 MTD 서비스 공급자에게 전송됩니다. 앱 인벤토리의 데이터에는 다음이 포함됩니다.

- 앱 ID
- 앱 버전
- 앱 짧은 버전
- 앱 이름
- 앱 번들 크기
- 앱 동적 크기
- 앱의 유효성 검사 여부
- 앱이 관리되는지 여부

## <a name="sample-scenarios-for-enrolled-devices-using-device-compliance-policies"></a>디바이스 준수 정책을 사용하는 등록된 디바이스의 샘플 시나리오

모바일 위협 방어 솔루션에서 디바이스가 감염된 것으로 간주되는 경우

![Mobile Threat Defense 감염된 디바이스를 보여주는 이미지](./media/mobile-threat-defense/MTD-image-1.png)

디바이스를 재구성하면 액세스가 허용됩니다.

![Mobile Threat Defense 감염된 장치를 보여주는 이미지](./media/mobile-threat-defense/MTD-image-2.png)

## <a name="sample-scenarios-for-unenrolled-devices-using-intune-app-protection-policies"></a>Intune 앱 보호 정책을 사용하는 등록된 디바이스의 샘플 시나리오

모바일 위협 방어 솔루션에서 디바이스가 감염된 것으로 간주되는 경우<br>
![Mobile Threat Defense 감염된 디바이스를 보여주는 이미지](./media/mobile-threat-defense/MTD-image-3.png)

디바이스를 재구성하면 액세스가 허용됩니다.<br>
![Mobile Threat Defense 감염된 디바이스를 보여주는 이미지](./media/mobile-threat-defense/MTD-image-4.png)

> [!NOTE]
> 사용자는 단일 Intune 테넌트로 여러 모바일 방어 공급업체를 이용할 수 있습니다. 그러나 둘 이상의 공급업체가 동일 플랫폼의 사용을 위해 구성되면 해당 플랫폼을 실행하는 모든 디바이스에는 각 MTD 앱을 설치해 위협 요소를 스캔해야 합니다. 구성된 앱에서 스캔 결과를 제출하지 않으면 해당 디바이스는 비준수 디바이스로 표시됩니다. 

## <a name="mobile-threat-defense-partners"></a>Mobile Threat Defense 파트너

다음을 사용하여 디바이스, 네트워크 및 애플리케이션 위험에 따라 회사 리소스에 대한 액세스를 보호하는 방법을 알아봅니다.

- [Lookout for Work](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [더 향상된 모바일](better-mobile-threat-defense-connector.md)
- [Sophos Mobile](sophos-mtd-connector.md)
- [Wandera Mobile Threat Defense](wandera-mtd-connector.md)
