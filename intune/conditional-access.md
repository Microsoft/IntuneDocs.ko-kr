---
title: Microsoft Intune을 사용하는 조건부 액세스
titlesuffix: ''
description: 사용자, 장치 및 앱이 Microsoft Intune에서 회사 리소스에 액세스하기 위해 충족해야 하는 조건을 정의하는 방법을 알아봅니다.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 03/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a1973f38-ea55-43eb-a151-505fb34a8afb
ms.suite: ems
ms.custom: intune-azure; get-started
ms.openlocfilehash: b1da098b0d45ed15abc2a260b84e3ab2f60cc007
ms.sourcegitcommit: 18f51ae8291b57562921e40fc364a5a60a59b139
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44254108"
---
# <a name="whats-conditional-access"></a>조건부 액세스란?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

조건부 액세스는 이메일 및 회사 리소스에 연결할 수 있는 앱과 장치를 제어할 수 있는 방법을 말합니다. 이 항목에서는 장치 기반 및 앱 기반 조건부 액세스에 대해 알아보고 Intune을 사용한 조건부 액세스를 사용하는 일반적인 시나리오를 찾아봅니다.

Enterprise Mobility + Security(EMS) 조건부 액세스는 독립 실행형 제품이 아니며 EMS의 일부분인 모든 서비스와 제품에 포함되는 솔루션입니다. EMS 조건부 액세스는 회사 데이터의 보안을 유지할 수 있는 세분화된 액세스 제어 기능을 제공하는 동시에, 사용자에게는 모든 위치와 장치에서 업무를 가장 효율적으로 수행할 수 있도록 하는 환경을 제공합니다.

위치, 장치, 사용자 상태 및 응용 프로그램 민감도 등을 기반으로 회사 데이터에 대한 액세스를 제한하는 조건을 정의할 수 있습니다.

> [!NOTE] 
> 조건부 액세스의 기능은 [Office 365 서비스](https://blogs.technet.microsoft.com/wbaer/2017/02/17/conditional-access-policies-with-sharepoint-online-and-onedrive-for-business/)로도 확장 적용됩니다.

![조건부 액세스 아키텍처 다이어그램](./media/ca-diagram-1.png)

## <a name="conditional-access-with-intune"></a>Intune을 사용하는 조건부 액세스

조건부 액세스는 Azure Active Directory Premium 라이선스에 포함된 Azure Active Directory 기능입니다. Intune은 솔루션에 모바일 장치 호환성과 모바일 앱 관리 기능을 추가하여 이 기능을 향상합니다. 

![EMS 사용 시의 Intune 및 조건부 액세스](./media/intune-with-ca-1.png)

Intune에서 조건부 액세스를 사용하는 방법은 다음과 같습니다.

-   **장치 기반 조건부 액세스**

    -   Exchange 온-프레미스에 대한 조건부 액세스

    -   네트워크 액세스 제어 기준 조건부 액세스

    -   장치 위험 기준 조건부 액세스

    -   Windows PC에 대한 조건부 액세스

        -   회사 소유

        -   BYOD(Bring Your Own Device)

-   **앱 기반 조건부 액세스**

## <a name="next-steps"></a>다음 단계

[Intune에서 조건부 액세스를 사용하는 일반적인 방법](conditional-access-intune-common-ways-use.md)
