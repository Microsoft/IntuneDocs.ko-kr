---
title: Microsoft Intune을 사용하는 조건부 액세스
titleSuffix: Microsoft Intune
description: 사용자, 디바이스 및 앱이 Microsoft Intune에서 회사 리소스에 액세스하기 위해 충족해야 하는 조건을 정의하는 방법을 알아봅니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 179d135ee8e216495cd7435bf38d8087e5c990e8
ms.sourcegitcommit: 13fa1a4a478cb0e03c7f751958bc17d9dc70010d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188286"
---
# <a name="learn-about-conditional-access-and-intune"></a>조건부 액세스와 Intune에 대해 알아봅니다.

조건부 액세스를 사용하면 메일 및 회사 리소스에 연결할 수 있는 앱과 디바이스를 제어할 수 있습니다. 

EMS(Enterprise Mobility + Security)는 독립 실행형 제품이 아닙니다. EMS를 구성하는 모든 서비스 및 제품에서 역할을 수행하는 솔루션입니다. 조건부 액세스는 회사 데이터의 보안을 유지할 수 있는 세분화된 액세스 제어 기능을 제공하는 동시에, 사용자에게는 모든 위치와 디바이스에서 업무를 가장 효율적으로 수행할 수 있도록 하는 환경을 제공합니다.

위치, 디바이스, 사용자 상태 및 애플리케이션 민감도 등을 기반으로 회사 데이터에 대한 액세스를 제한하는 조건을 정의할 수 있습니다.

> [!NOTE]
> 조건부 액세스의 기능은 [Office 365 서비스](https://docs.microsoft.com/office365/enterprise/office-365-client-support-conditional-access)로도 확장 적용됩니다.

![조건부 액세스 다이어그램](./media/conditional-access/ca-diagram-1.png)

## <a name="use-conditional-access-with-intune"></a>Intune을 사용하는 조건부 액세스 사용

조건부 액세스는 Azure Active Directory Premium 라이선스에 포함된 Azure Active Directory 기능입니다. Intune은 솔루션에 모바일 디바이스 호환성과 모바일 앱 관리 기능을 추가하여 이 기능을 향상합니다. 

![EMS 사용 시의 Intune 및 조건부 액세스](./media/conditional-access/intune-with-ca-1.png)

Intune에서 조건부 액세스를 사용하는 방법은 다음과 같습니다.

- **디바이스 기반 조건부 액세스**

  - Exchange 온-프레미스에 대한 조건부 액세스

  - 네트워크 액세스 제어 기준 조건부 액세스

  - 디바이스 위험 기준 조건부 액세스

  - Windows PC에 대한 조건부 액세스

    - 회사 소유

    - BYOD(Bring Your Own Device)

- **앱 기반 조건부 액세스**

## <a name="next-steps"></a>다음 단계

[Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)
