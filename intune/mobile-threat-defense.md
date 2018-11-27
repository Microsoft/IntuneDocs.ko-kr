---
title: Microsoft Intune에서 Mobile Threat Defense 사용
titleSuffix: ''
description: MTD(Mobile Threat Defense) 파트너와 함께 Intune MTD(Mobile Threat Defense)를 사용하여 장치 위험에 따라 회사 리소스에 대한 액세스를 보호합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/28/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ac77b590-a7ec-45a0-9516-ebf5243b6210
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 65bbc207f96ae2b1670fa2ddc45cad56466580df
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52183641"
---
# <a name="what-is-mobile-threat-defense-integration-with-intune"></a>Intune과 Mobile Threat Defense의 통합이란?


Intune 모바일 위협 방어 커넥터를 사용하면 선택한 모바일 위협 방어 공급업체를 준수 정책 및 조건부 액세스 규칙의 정보 소스로 활용할 수 있습니다. 이 경우 IT 관리자가 특히 손상된 모바일 장치에서 Exchange 및 Sharepoint와 같은 회사 리소스에 보호 계층을 추가할 수 있습니다.

## <a name="what-problem-does-this-solve"></a>이 기능을 통해 어떤 문제가 해결되나요?

회사는 OS 취약점뿐만 아니라 물리적 위협, 앱 기반 위협, 네트워크 기반 위협 등 출현하는 위협에서 중요한 데이터를 보호해야 합니다.

지금까지 회사는 공격으로부터 PC를 보호하는 데 사전 예방적인 자세를 취해 왔지만 모바일 장치는 모니터링 및 보호되지 않고 있습니다. 모바일 플랫폼에는 앱 격리 및 소비자 앱 스토어 점검과 같은 기본 제공 보호 기능이 있지만 이러한 플랫폼은 정교한 공격에 여전히 취약합니다. 오늘날 업무에 장치를 사용하며 중요한 정보에 액세스해야 하는 직원이 늘어나고 있습니다. 따라서 점점 더 정교한 공격으로부터 장치를 보호해야 합니다.

## <a name="how-do-the-intune-mobile-threat-defense-connectors-work"></a>Intune Mobile Threat Defense 커넥터의 작동 방식

커넥터는 Intune과 선택한 모바일 위협 방어 공급업체 간에 통신 채널을 만들어 회사 리소스를 보호합니다. Intune Mobile Threat Defense 파트너는 직관적이고 배포하기 쉬운 모바일 장치용 응용 프로그램을 제공합니다. 이 응용 프로그램은 보고 또는 적용을 위해 Intune과 공유할 위협 정보를 적극적으로 검색하고 분석합니다. 

예를 들어 연결된 Mobile Threat Defense 앱이 Mobile Threat Defense 공급업체에 네트워크의 휴대폰이 메시지 가로채기(man-in-the-middle) 공격에 취약한 네트워크에 현재 연결되어 있다고 보고하는 경우 이 정보는 공유되며 적절한 위험 수준(낮음/중간/높음)으로 분류됩니다. 그런 다음, Intune에서 구성된 허용 위험 수준과 비교하여 장치가 손상된 동안 선택한 특정 리소스에 대한 액세스를 해지할지 여부를 확인할 수 있습니다.

## <a name="what-data-does-intune-collect-for-mobile-threat-defense"></a>Intune은 Mobile Threat Defense를 위해 어떤 데이터를 수집하나요?

사용 설정하면 Intune이 개인 및 회사 소유 장치 모두에서 앱 인벤토리 정보를 수집하여 Lookout for Work와 같은 MTD(Mobile Threat Defense) 공급자가 페치할 수 있도록 합니다. iOS 장치의 사용자로부터 앱 인벤토리를 수집할 수 있습니다.

이 서비스는 옵트인된 것입니다. 기본적으로 앱 인벤토리 정보는 공유되지 않습니다. Intune 관리자는 앱 인벤토리 정보를 공유하기 전에 서비스 설정에서 iOS 장치에 대한 앱 동기화를 설정해야 합니다.

**앱 인벤토리**  
iOS 장치용 앱 동기화를 사용하면 회사 및 개인 소유 iOS 장치 모두의 인벤토리가 MTD 서비스 공급자에게 전송됩니다. 앱 인벤토리의 데이터에는 다음이 포함됩니다.

 - 앱 ID
 - 앱 버전
 - 앱 짧은 버전
 - 앱 이름
 - 앱 번들 크기
 - 앱 동적 크기
 - 앱의 유효성 검사 여부
 - 앱이 관리되는지 여부

## <a name="sample-scenarios"></a>샘플 시나리오:

Mobile Threat Defense 솔루션에서 장치가 감염된 것으로 간주되는 경우

![Mobile Threat Defense 감염된 장치를 보여주는 이미지](./media/MTD-image-1.png)

장치를 재구성하면 액세스가 허용됩니다.

![Mobile Threat Defense 감염된 장치를 보여주는 이미지](./media/MTD-image-2.png)

> [!NOTE] 
> Intune에서 여러 Mobile Threat Defense 공급 업체를 사용하도록 지원되지 않습니다. 여러 MTD 도구를 사용하면 모든 MTD 앱을 설치하도록 강제하고 장치에서 위협을 검사합니다.

## <a name="mobile-threat-defense-partners"></a>모바일 위협 방어 파트너

다음을 사용하여 장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스를 보호하는 방법을 알아봅니다.

- [Lookout](lookout-mobile-threat-defense-connector.md)
- [Symantec Endpoint Protection Mobile](skycure-mobile-threat-defense-connector.md)
- [Check Point SandBlast Mobile](checkpoint-sandblast-mobile-mobile-threat-defense-connector.md)
- [Zimperium](zimperium-mobile-threat-defense-connector.md)
- [Pradeo](pradeo-mobile-threat-defense-connector.md)
- [더 향상된 모바일](better-mobile-threat-defense-connector.md)
