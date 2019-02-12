---
title: Intune의 데이터 보안 및 공유
description: Intune에서 개인 데이터를 보호하고 공유하는 방법을 알아봅니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 68921fd6-5f50-456c-a3af-83d7bc4b134b
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: acbb5c75be4e7733a9b886d0e573d26b6b841f2f
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55836832"
---
# <a name="data-security-and-sharing-in-intune"></a>Intune의 데이터 보안 및 공유


## <a name="data-security"></a>데이터 보안

Microsoft Intune은 Microsoft Enterprise Mobility 및 Security Suite 클라우드 서비스 솔루션의 핵심 구성 요소입니다. [데이터 거버넌스 전략](https://www.microsoft.com/en-us/TrustCenter/Security/default.aspx)을 지원하기 위해 모든 Microsoft 클라우드 서비스는 [Microsoft Privacy](https://www.microsoft.com/en-us/trustcenter/privacy) 및 [Microsoft Security](https://www.microsoft.com/en-us/trustcenter/security/) 방법론으로 개발됩니다.  

Microsoft Intune은 Microsoft Azure 서비스 팀이 데이터 보안 위반 프로세스로부터 보호하기 위해 취하는 것과 동일한 기술 및 조직적 조치를 따릅니다.

자세한 내용은 [Service Trust Portal](https://www.microsoft.com/en-us/TrustCenter/stp)을 참조하세요.

Intune은 다음과 같은 데이터 최소화 기법을 사용합니다.

- aggregation
- 일부 기능에 대한 선택적 데이터 수집
- 덜 정확하거나 중요한 데이터

또한 Intune은 지원 인시던트에 RBAC 및 JiT 보안과 같은 기법을 사용하여 기본적으로 데이터 보호를 보장합니다. 

### <a name="data-breach-reporting"></a>데이터 보안 위반 보고

CRSI(Customer-Reportable Security Incident)가 확인되면 고객에게 알립니다. 이 프로세스에는 Microsoft O365 팀과 협력하여 Intune을 사용하는 모든 Microsoft O365 고객에 대한 위반 알림을 전달하는 작업이 포함됩니다.

## <a name="data-sharing"></a>데이터 공유

테넌트 관리자가 Apple 디바이스 등록 프로그램과 같은 특정 기능을 설정하면 Microsoft Intune은 해당 타사와 데이터를 공유하기 위해 관리자의 동의를 구합니다. 이러한 경우 Intune은 다음 업체와 개인 데이터를 공유할 수 있습니다.

- Microsoft의 에이전트 역할을 하는 타사.
- Microsoft의 에이전트 역할을 하지 않지만 테넌트 관리자가 그러한 역할을 하는 Intune 권한을 명시적으로 부여한 타사.

Microsoft 에이전트 역할을 하는 모든 타사는 [온라인 서비스 협력업체 목록](https://aka.ms/Online_Serv_Subcontractor_List)에 포함되어 있습니다.

이러한 업체와의 데이터 공유는 고객 및 기술 지원, 서비스 유지 관리 및 기타 작업을 지원하기 위해 수행됩니다.

타사와의 테넌트 계약은 타사의 서비스에 보관된 Intune 개인 데이터에 적용됩니다. 또한 타사 서비스로 데이터를 전송할 수 있는 권한을 Intune에 부여합니다.  

특정 타사와 공유하는 데이터에 대한 자세한 내용은 다음 문서를 참조하세요.
- [Intune이 Apple에 보내는 데이터](data-intune-sends-to-apple.md)
- [Intune이 Google에 보내는 데이터](data-intune-sends-to-google.md)
- [Apple이 Intune에 보내는 데이터](data-apple-sends-to-intune.md)
- [Google이 Intune에 보내는 데이터](data-google-sends-to-intune.md)
- [Intune에 보내는 데이터 Jamf Pro](data-jamf-sends-to-intune.md)

### <a name="system-center-configuration-manager-data-sharing"></a>System Center Configuration Manager 데이터 공유

Microsoft Intune은 System Center Configuration Manager와 데이터를 공유하지 않습니다. System Center Configuration Manager는 고객이 직접 배포하고, 관리하고, 운영하는 온-프레미스 제품입니다. Configuration Manager에서 수집하는 진단 및 사용 현황 데이터는 향후 릴리스의 설치 환경, 품질 및 보안을 개선하기 위해서만 사용됩니다.

자세한 내용은 [SCCM의 진단 및 사용 현황 데이터](https://docs.microsoft.com/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data.md)를 참조하세요. 


## <a name="next-steps"></a>다음 단계

Intune에서 개인 데이터 [보기 및 수정](privacy-data-view-correct.md) 방법을 알아봅니다.
