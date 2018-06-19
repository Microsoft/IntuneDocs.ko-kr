---
title: 앱 및 데이터 보호
description: 이 항목에서는 회사 앱 및 데이터를 보호하는 데 사용할 수 있는 다양한 Intune의 특징과 기능에 대해 설명합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/19/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5c46e188-87eb-4ce2-b184-24809e8bf783
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 2a05444c757b8e99ca0b897acfcd6238d960aeb2
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31017549"
---
# <a name="protect-apps-and-data-with-microsoft-intune"></a>Microsoft Intune을 사용하여 앱 및 데이터 보호 | Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Intune은 여러 기술 계층을 통해 회사 데이터를 보호합니다. ID 계층에서 조건부 액세스를 통해 관리되는 호환 장치에서만 액세스를 허용하여 서비스에 대한 액세스를 보호합니다. 클라이언트 응용 프로그램 계층에서 MAM(모바일 응용 프로그램 관리)은 보호되지 않는 앱 또는 저장소 위치로 데이터가 이동되는 것을 방지하고 장치를 분실하거나 도난당한 경우 데이터를 삭제하여 데이터 손실을 보호합니다. 모바일 직원의 생산성을 유지하면서 데이터를 보호하려면 이러한 두 가지 보호 계층을 함께 사용하는 것이 좋습니다.

회사 데이터를 보호하기 위한 중요한 첫 번째 단계는 조건부 액세스를 구현하는 것입니다. 이렇게 하려면 해당 데이터에 액세스하는 데 사용되는 장치가 강력한 암호 및 암호화와 같은 보안 보호를 사용하고 무단 해제되지 않도록 하면 됩니다. Intune에서는 장치가 회사 메일 및 데이터에 액세스하기 위해 준수해야 하는 조건을 설정하는 기능을 제공합니다.

[조건부 액세스](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)는 Intune에서 설정 가능한 두 가지 정책 유형을 통해 결정됩니다.
- [준수 정책](introduction-to-device-compliance-policies-in-microsoft-intune.md)은 장치의 준수 여부를 확인하며, 다음과 같은 설정과 조건을 평가합니다.
  - PIN 및 암호: 장치 잠금을 해제하려면 암호를 입력해야 하는 규칙, 암호의 복잡성 요구 사항에 대한 규칙 및 기타 암호 설정에 대한 규칙을 만들 수 있습니다.
  - 암호화: 암호화된 장치에 대한 액세스를 제한할 수 있습니다.
  - 장치가 무단 해제되거나 루팅되지 않는 경우: Intune은 등록된 장치가 무단 해제되었는지 감지할 수 있습니다. 이러한 장치에 대한 액세스를 차단하는 정책을 설정할 수 있습니다.
- Exchange Online 또는 SharePoint Online과 같은 특정 서비스에 대해 [조건부 액세스 정책](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)을 구성합니다. 각 서비스에 대해 이러한 정책을 적용해야 하는 사용자 그룹을 정의할 수 있습니다. 예를 들어 재무 부서의 모든 직원은 규정을 준수하며 등록되어 있는 장치에서만 회사 전자 메일에 액세스할 수 있도록 정의할 수 있습니다.

회사 리소스에 대한 액세스를 보호하는 것은 회사 데이터를 보호하기 위한 첫 번째 단계일 뿐입니다. 장치에 액세스한 후 데이터를 보호하는 기능이 여전히 필요합니다. 이제 해당 내용을 복사, 이동하거나 다른 위치에 저장하거나 공유할 수 있습니다. Intune에서는 다음과 같은 규칙 집합을 만들어 데이터 이동을 제한하는 기능을 제공하여 이 문제를 해결합니다.
- 복사 및 붙여넣기를 차단하거나 회사 컨텍스트 외부로 데이터 전송을 차단합니다.
- 개인 클라우드 저장소로의 백업과 “다른 이름으로 저장” 등을 방지합니다.
- PIN/암호 또는 회사 자격 증명을 요구하여 앱 액세스를 보호합니다.
- Intune Managed Browser 내에서 모든 웹 링크가 열려 있도록 합니다.

이러한 규칙 집합을 [MAM(모바일 응용 프로그램 관리) 정책](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)이라고 합니다. 자신이 관리하거나 관리하지 않는 장치에서 실행되는 앱에 MAM 정책을 적용할 수 있습니다.  

**Intune에 등록**된 장치, **다른 타사 MDM(모바일 장치 관리) 솔루션에 의해 등록 및 관리**되는 장치 또는 직원이 소유한 장치처럼 **MDM 솔루션에 등록되지 않은** 장치에 MAM 정책을 사용하여 회사 데이터를 보호할 수 있습니다.

앱을 MAM 정책과 연결하려면 앱에서 Microsoft Intune 앱 SDK(소프트웨어 개발 키트)를 통합하거나 앱 줄 바꿈 도구를 사용해야 합니다.

Microsoft Office 앱 등의 앱에는 Intune 앱 SDK가 기본 제공됩니다. 지원되는 앱의 전체 목록은 Microsoft Intune 응용 프로그램 파트너 페이지의 [Microsoft Intune 모바일 응용 프로그램 갤러리](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)에서 확인할 수 있습니다. 앱을 선택하여 지원되는 시나리오와 플랫폼, 앱에서 다중 ID를 지원하는지 여부 등을 확인합니다.

[사용자 지정 작성된 LOB(기간 업무) 앱](/intune/apps-prepare-mobile-application-management)을 MAM 정책과 함께 사용하도록 설정할 수도 있습니다.

데이터 이동을 제한하는 것 외에도 장치를 분실하거나 도난당한 경우 또는 사용자가 회사에서 더 이상 근무하지 않는 경우 [회사 데이터를 선택적으로 지울](wipe-managed-company-app-data-with-microsoft-intune.md) 수 있으며 개인 데이터만 내부에 남길 수 있습니다.
