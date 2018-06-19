---
title: 준수 정책 배포 및 모니터링
description: 이 항목의 단계별 지침을 사용하여 장치 준수 정책을 배포 및 모니터링합니다.
keywords: ''
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 11/14/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d8f246d4-0d86-4c8b-a1bf-9977985506d8
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 7e3f67411a4eff357102756e785f4cbbff120d23
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31016070"
---
# <a name="deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune"></a>Microsoft Intune에서 장치 규정 준수 정책 배포 및 모니터링

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

## <a name="deploy-a-compliance-policy"></a>준수 정책 배포
[만든](create-a-device-compliance-policy-in-microsoft-intune.md) 준수 정책을 조직에서 하나 이상의 사용자에게 배포합니다. 준수 정책을 사용자에게 배포하면 사용자 장치의 준수가 확인됩니다.

1.  **정책** 작업 영역에서 배포할 정책을 선택한 다음 **배포 관리**를 선택합니다.
![맨 위에 있는 배포 관리 메뉴 옵션을 표시하는 준수 정책 페이지의 스크린샷](./media/intune-sa-3c-deploy-compliance-policy2.png)

2.  **배포 관리** 대화 상자에서 정책을 배포하려는 그룹을 하나 이상 선택하고 **추가** > **확인**을 선택합니다.
![배포 관리 대화 상자 스크린샷](./media/intune-sa-3d-deploy-compliance-policy3-Manage.png) 이미 만들어 Intune에 동기화한 Active Directory 그룹을 사용하거나, Intune 콘솔에서 이러한 그룹을 수동으로 만듭니다. 정책을 배포하는 방법에 대해 자세히 알아보려면 [구성 정책 배포](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)를 참조하세요.

**정책** 작업 영역의 **개요** 페이지에 있는 상태 요약 및 경고는 주의가 필요한 정책 문제를 식별합니다. 또한 상태 요약은 **대시보드** 작업 영역에 표시됩니다.

> [!IMPORTANT]
> 준수 정책을 배포하지 않은 상태에서 Exchange 조건부 액세스 정책을 사용하도록 설정하면 대상으로 지정된 모든 장치에 액세스할 수 있습니다.

## <a name="monitor-the-compliance-policy"></a>규정 준수 정책 모니터링

#### <a name="to-view-devices-that-do-not-conform-to-a-compliance-policy"></a>준수 정책을 준수하지 않는 장치를 보려면

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **그룹** > **모든 장치**를 선택합니다.

2.  장치 목록에서 장치 이름을 두 번 클릭합니다.

3.  **정책** 탭을 선택하여 해당 장치에 대한 정책 목록을 표시합니다.

4.  **필터** 드롭다운 목록에서 **준수 정책을 준수하지 않음**을 선택합니다.
![필터 목록에서 옵션 목록을 보여 주는 스크린샷](./media/intune-sa-3e-view-device-noncompliance.png)

#### <a name="to-view-the-health-attestation-reports"></a>상태 증명 보고서를 보려면

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **보고서**를 선택합니다.

2.  **상태 증명 보고서 - 새 보고서 만들기** 페이지에서는 Intune에서 수집한 모든 Windows 10 상태 증명 데이터가 포함된 보고서를 볼 수 있습니다. 필터를 사용하여 데이터 하위 집합으로 보고서를 만들 수도 있습니다. 필터는 장치 유형, 운영 체제 또는 데이터 요소 하위 집합만 기반으로 할 수 있습니다.

## <a name="how-intune-resolves-policy-conflicts"></a>Intune에서 정책 충돌을 해결하는 방법
정책 충돌은 장치에 여러 Intune 정책을 적용할 때 발생할 수 있습니다. 정책 설정이 겹치면 Intune에서는 다음 규칙을 사용하여 충돌을 해결합니다.

-   Intune 구성 정책과 준수 정책에 충돌하는 설정이 있는 경우 구성 정책 설정보다 준수 정책 설정이 우선합니다. 이 문제는 구성 정책 설정이 더 안전하더라도 발생합니다.

-   여러 준수 정책을 배포한 경우 Intune은 이러한 정책 중 가장 안전한 정책을 사용합니다.

## <a name="next-steps"></a>다음 단계
조건부 액세스 정책과 함께 준수 정책을 사용하여 사용자의 조직에서 서비스에 대한 액세스를 제어하는 방법을 알아보려면 [Microsoft Intune을 사용한 메일, O365 및 기타 서비스에 대한 액세스 제한](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)을 참조하세요.


### <a name="see-also"></a>참고 항목
[Intune에서 장치 준수 정책 소개](introduction-to-device-compliance-policies-in-microsoft-intune.md)
