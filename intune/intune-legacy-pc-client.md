---
title: 레거시 Intune PC 클라이언트 및 Azure의 Intune
description: Azure에서 Intune을 사용하여 조직의 Windows 디바이스를 관리할 때 고려할 사항입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/15/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3891ce150ea740baa3ba18591139c66d78d9d00
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71166358"
---
# <a name="intune-on-azure-console-and-legacy-intune-pc-client"></a>Azure의 Intune 콘솔 및 레거시 Intune PC 클라이언트

Intune은 Azure 기반 SaaS 애플리케이션 서비스 아키텍처를 사용합니다. Azure는 확장, 용량 및 성능에서 상당한 개선 사항을 제공합니다. 이를 통해 Azure Portal에서 향상된 Intune 관리자 환경과 최적화된 워크플로를 제공합니다. 

Azure용 Intune을 사용하여 조직의 Windows 디바이스를 관리할 경우 다음 사항을 고려하세요.

## <a name="manage-windows-10-devices-by-using-mdm"></a>MDM을 사용하여 Windows 10 디바이스 관리

Linux Intune PC 클라이언트를 사용하는 대신 [MDM(모바일 디바이스 관리)을 사용하여 Windows 10 디바이스를 관리](device-restrictions-windows-10.md)하는 것이 좋습니다. MDM을 통해 Windows 10을 관리하는 기능은 Azure Portal의 Intune에서 사용할 수 있습니다. Windows 10 MDM은 레거시 Intune PC 클라이언트를 통해 사용할 수 없는 많은 새로운 관리 및 보안 기능을 제공합니다.

## <a name="legacy-pc-client-features-are-only-available-in-the-silverlight-console"></a>레거시 PC 클라이언트 기능은 Silverlight 콘솔에서만 사용 가능합니다.

Intune PC 클라이언트 관리 워크플로는 [Silverlight 기반 Intune 관리 콘솔](https://manage.microsoft.com/)을 사용하고 결과는 다음과 같습니다.

- Intune PC 클라이언트를 사용하는 모든 비그룹화 관리 작업의 경우 Silverlight 콘솔을 사용해야 합니다.
- 그룹을 관리할 때는 [Azure Portal의 Intune](https://portal.azure.com/)을 사용해야 합니다. 이 요구 사항이 있는 이유는 이제 Intune에서 레거시 Intune 그룹 대신 Azure AD 그룹을 사용하기 때문입니다. 

Azure AD 그룹으로 전환하기 때문에 Silverlight 콘솔 대시보드 보기에서 “그룹별” 필터링이 약간 변경되었습니다. 업데이트된 Silverlight UI에서 필터링하려면 아래 단계를 따릅니다.

1. 보기를 선택합니다.
2. **필터** 상자에 필터링할 그룹의 이름을 입력하고 Enter 키를 누릅니다. 그러면 해당 특정 그룹의 디바이스에 대한 목록 보기가 필터링됩니다.

   ![선택한 항목이 없는 드롭다운 입력 필터](media/intune-legacy-pc-client/image01.png)


## <a name="continue-to-manage-windows-7-by-using-intune-pc-client"></a>Intune PC 클라이언트를 사용하여 Windows 7을 계속 관리

MDM을 사용하여 관리할 수 없는 Windows 7의 경우 Silverlight 콘솔에서만 기존 Intune PC 클라이언트 기능을 계속 지원합니다. Windows 10으로 업그레이드할 경우 MDM 관리로 마이그레이션하는 것이 좋습니다.

## <a name="mdm-capabilities"></a>MDM 기능

PC 클라이언트와 MDM 기능 간의 자세한 비교는 [Windows PC를 컴퓨터로 관리하는 방식과 모바일 디바이스로 관리하는 방식 비교](pc-management-comparison.md)를 참조하세요. MDM 업데이트는 Win 32 앱에 대한 옵션을 평가하는 기능을 포함하여 새로운 관리 기능을 MDM에 등록된 Windows 10 디바이스로 계속 가져옵니다. 서비스에 추가된 최신 릴리스는 [새로운 기능](whats-new.md)을 확인하세요.

## <a name="switch-from-pc-client-to-mdm"></a>PC 클라이언트에서 MDM으로 전환

Intune PC 클라이언트를 사용하여 Windows 10 디바이스를 관리하는 방식에서 MDM을 사용하여 관리하는 방식으로 전환하려면 아래 단계를 따릅니다.

1. Silverlight 콘솔에서 **선택적 초기화**를 수행하여 PC 클라이언트에서 디바이스를 등록 취소합니다.
  ![' 선택적으로 장치 초기화 ' 라디오 단추가 선택 된 경고 팝업](media/intune-legacy-pc-client/image02.png)
2. [MDM(및/또는 Azure AD 조인)](windows-enroll.md)을 사용하여 디바이스를 다시 등록합니다.

## <a name="next-steps"></a>다음 단계
[Windows 디바이스 등록](windows-enroll.md)
