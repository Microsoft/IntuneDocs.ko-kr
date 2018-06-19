---
title: Exchange ActiveSync 장치 관리
description: Exchange Connector를 사용한 EAS(Exchange ActiveSync) 관리를 통해 모바일 장치 관리
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 07/29/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 14f5cf53-6764-4e22-a18b-fa750b3acd41
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: f5e9bd3dd2026096c323858fc7faa915895ed55d
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31016750"
---
# <a name="exchange-activesync-mobile-device-management-with-microsoft-intune"></a>Microsoft Intune을 사용한 Exchange ActiveSync 모바일 장치 관리

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune에서 모바일 장치를 직접 관리하도록 하려면 장치가 [Intune에 등록](prerequisites-for-enrollment.md)되어 있어야 합니다. 또는 관리자가 EAS(Exchange ActiveSync) 관리를 Exchange Connector와 같이 사용하는 좀 더 제한적인 관리 솔루션을 사용하도록 설정할 수 있습니다. 장치는 Office 365를 사용하는 온-프레미스 Exchange 서버 또는 Exchange Online을 사용하여 관리할 수 있습니다. Intune은 Exchange Connector 연결 형식에 상관없이 구독당 연결을 한 번만 지원합니다.

## <a name="exchange-access-rules-for-mobile-devices"></a>모바일 장치의 Exchange 액세스 규칙 ##

Exchange를 사용하려면 모바일 장치가 EAS에 연결을 시도할 때 일어나는 일을 정의하는 규칙 집합이 필요합니다. 이러한 규칙은 Intune 관리 콘솔에서 관리됩니다.

[모바일 장치의 Exchange 액세스 규칙](exchange-access-rules-for-mobile-devices.md)

## <a name="install-the-exchange-connector"></a>Exchange Connector 설치
Exchange Connector를 사용하면 Intune 콘솔에서 Exchange 배포를 관리할 수 있습니다. 먼저 적절한 Intune과 Exchange 간 커넥터를 설치하고 설정해야 합니다. Exchange 서버가 온-프레미스인지 또는 클라우드에서 서비스로 호스트되는지에 따라 적절한 옵션을 선택합니다.

-   [Exchange Online 또는 새로운 Exchange Online Dedicated 환경에 대한 Intune 구성](intune-service-to-service-exchange-connector.md)
-   [온-프레미스 Exchange Server 및 기존 Exchange Online Dedicated 환경에 대한 Intune 커넥터 설치](intune-on-premises-exchange-connector.md)


## <a name="apply-policy-for-exchange-managed-mobile-devices"></a>Exchange에서 관리하는 모바일 장치에 대한 정책 적용
Intune 콘솔을 사용하여 [EAS 정책 설정](exchange-activesync-policy-settings-in-microsoft-intune.md)을 관리하고, [회사 리소스에 대한 액세스를 제한](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)할 수 있습니다. 특정 모바일 장치가 지원하는 Exchange ActiveSync 정책 설정 및 기능의 목록은 [Exchange ActiveSync Client Comparison Table](http://go.microsoft.com/fwlink/?LinkId=247270)(Exchange ActiveSync 클라이언트 비교 표)을 참조하세요.

> [!NOTE]
> Intune 내에 더 구체적인 정책이 정의되어 있지 않은 경우, Intune을 Microsoft Exchange 환경에 연결하면 Intune을 통해 관리되는 모든 사용자에 대한 Microsoft Exchange Server 정책이 Microsoft Exchange 서버의 현재 기본 정책으로 다시 설정됩니다.

## <a name="wipe-company-data-from-mobile-devices"></a>모바일 장치에서 회사 데이터 초기화
마지막으로 더 이상 사용하지 않거나 장치가 분실 또는 도난당한 경우 [EAS 관리 모바일 장치에서 회사 데이터를 초기화](wipe-for-exchange-managed-mobile-devices.md)할 수 있습니다.
