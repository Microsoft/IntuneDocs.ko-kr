---
title: 개발 중 - Microsoft Intune
titleSuffix: ''
description: 개발 중인 Microsoft Intune 기능
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/29/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3645d07fe9a703f182e05bc9a7f9fbb93c413ddc
ms.sourcegitcommit: dfcf80a91792715404dc021c8684866c8b0a27e1
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2019
ms.locfileid: "65816238"
---
# <a name="in-development-for-microsoft-intune---may-2019"></a>Microsoft Intune에 대해 개발 중 - 2019년 5월

준비 및 계획을 지원하기 위해 이 페이지에는 개발 중이지만 아직 릴리스되지 않은 Intune UI 업데이트 및 기능이 나열되어 있습니다. 이 밖에도 다음 지침을 따릅니다.

- 변경하기 전에 조치를 취해야 할 것으로 예상되면 보완적인 Office Message Center 게시물을 게시할 것입니다.
- 미리 보기 또는 일반적으로 사용할 수 있는 기능을 프로덕션 환경에서 시작하면 기능 설명이 이 페이지에서 [새로운 기능 페이지](whats-new.md)로 이동합니다.
- 이 페이지와 [새로운 기능 페이지](whats-new.md)는 정기적으로 업데이트됩니다. 추가 업데이트가 있는지 다시 확인하세요.
- 전략적 결과물과 타임라인은 [M365 로드맵](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS)을 참조하세요.

> [!Note]
> 이러한 항목은 향후 릴리스에서 제공될 Intune 기능에 대한 Microsoft의 현재 기대를 반영합니다. 날짜 및 개별 기능이 변경될 수 있습니다. 개발 중인 모든 항목이 이 페이지에 기능 설명이 있는 것은 아닙니다.

**RSS 피드**: 다음(`https://docs.microsoft.com/api/search/rss?search=%22in+development+-+microsoft+intune%22&locale=en-us`) URL을 복사하여 피드 판독기에 붙여넣으면 이 페이지가 업데이트될 때 알림을 받을 수 있습니다.

<!--
## What's coming to Intune in the Azure portal 
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Azure Portal의 Intune


<!-- 1905 start-->


### <a name="baseline-support-for-keyword-search-----3082036-----------"></a>키워드 검색에 대한 기준 지원  <!-- 3082036         -->
보안 기준 프로필을 만들거나 편집하는 동안 곧 *검색*을 사용하여 콘솔에 표시되는 설정을 필터링할 수 있게 됩니다.   

### <a name="reset-and-wipe-devices-in-bulk-by-using-the-graph-api----3295288---"></a>Graph API를 사용하여 디바이스를 대량으로 다시 설정하고 초기화 <!-- 3295288 -->
Graph API를 사용하여 최대 100대의 디바이스를 대량으로 다시 설정하고 초기화할 수 있습니다.

<!-- 1904 start-->

### <a name="device-users-can-view-all-managed-apps-theyve-installed-or-tried-to-install----2352913---"></a>다바이스 사용자는 설치했거나 설치하려고 시도한 모든 관리형 앱을 볼 수 있습니다. <!-- 2352913 -->
Windows용 회사 포털은 사용자의 디바이스에 &ndash;필수 및 사용 가능한&ndash; 모든 관리형 앱을 나열합니다. 사용자는 시도 및 보류 중인 앱 설치와 현재 상태를 볼 수 있습니다. 조직에서 앱을 필수 또는 사용 가능하게 설정하지 않으면 회사 앱이 설치되지 않았다는 메시지가 사용자에게 표시됩니다. 사용자도 설치 상태별로 앱을 정렬하거나 필터링할 수 있습니다.

### <a name="use-applicability-rules-when-creating-windows-10-device-configuration-profiles----2549910---"></a>Windows 10 디바이스 구성 프로필을 만들 때 "적용 가능성 규칙" 사용 <!-- 2549910 -->
Windows 10 다비이스 구성 프로필을 만듭니다(플랫폼용 **디바이스 구성** > **프로필** > **프로필 만들기** > **Windows 10**). 프로필이 특정 에디션 또는 특정 버전에만 적용되도록 **적용 가능성 규칙**을 만들 수 있습니다. 예를 들어 일부 BitLocker 설정을 사용하도록 설정하는 프로필을 만듭니다. 프로필을 추가한 후에는 적용 가능한 규칙을 사용하여 프로필을 Windows 10 Enterprise를 실행하는 디바이스에만 적용되도록 합니다.

적용 대상: 
- Windows 10 이상



## <a name="notices"></a>알림

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>참고 항목
최근 개발 작업에 대한 자세한 내용은 [Microsoft Intune의 새로운 기능](whats-new.md)을 참조하세요.


