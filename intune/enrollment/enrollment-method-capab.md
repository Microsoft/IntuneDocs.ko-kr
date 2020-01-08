---
title: Windows 디바이스용 Intune 등록 방법 기능
titleSuffix: Microsoft Intune
description: Windows 디바이스의 각 등록 방법에 따른 기능입니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: b68ec61496c3c15acc8facc22a6fdfe3c65f06eb
ms.sourcegitcommit: a82d25d98fdf0ba766f8f074871d4f13725e23f9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75547862"
---
# <a name="intune-enrollment-method-capabilities-for-windows-devices"></a>Windows 디바이스용 Intune 등록 방법 기능
[!INCLUDE[azure_portal](../includes/azure_portal.md)]

Intune에서 작업자의 디바이스를 등록하는 몇 가지 방법이 있습니다. 아래 표에 나와 있는 것처럼 각 방법에는 다른 모범 사례 및 기능이 포함됩니다.

## <a name="best-practices-by-enrollment-method"></a>등록 방법별 모범 사례
| **모범 사례** | **[Azure AD 조인됨](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Autopilot을 사용하여 Azure AD 조인됨(사용자 구동 모드)](enrollment-autopilot.md)** |**[Autopilot을 사용하여 Azure AD 조인됨(셀프 배포 모드)](enrollment-autopilot.md)** |**[대량](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[공동 관리](https://docs.microsoft.com/configmgr/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|EDU에 일반적으로 사용됨|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|디바이스를 공유 디바이스로 사용 가능|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|개인 디바이스는 회사 리소스에 액세스해야 함|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|앱의 셀프 서비스|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|

## <a name="capabilities-by-enrollment-method"></a>등록 방법별 기능

| **기능** | **[Azure AD 조인됨](windows-enroll.md#enable-windows-10-automatic-enrollment)**|**[Autopilot을 사용하여 Azure AD 조인됨(사용자 구동 모드)](enrollment-autopilot.md)** |**[Autopilot을 사용하여 Azure AD 조인됨(셀프 배포 모드)](enrollment-autopilot.md)** |**[대량](windows-bulk-enroll.md)**|**[DEM](device-enrollment-manager-enroll.md)** | **[BYOD](device-enrollment.md#bring-your-own-device)** | **[GPO](https://docs.microsoft.com/windows/client-management/mdm/enroll-a-windows-10-device-automatically-using-group-policy)** | **[공동 관리](https://docs.microsoft.com/configmgr/core/clients/manage/co-management-overview)** |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|조건부 액세스                                      |![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)\*\*|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|디바이스와 연결된 사용자                    |![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|Azure AD Premium 필요                               |![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|디바이스는 CA에서 보호되는 리소스를 평가할 수 있음             |![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|사용자는 해당 디바이스에서 관리자가 아니어야 함               |![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|디바이스 설치 환경을 구성하는 기능        |![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|
|사용자 개입 없이 디바이스를 등록하는 기능      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|PowerShell 스크립트를 실행하는 기능                       |![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/checkmark.png)\*| 
|AD 도메인 조인 후 자동 등록 지원      |![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|하이브리드 Azure AD 조인 후 자동 등록 지원|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|
|Azure AD 조인 후 자동 등록 지원       |![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![확인 표시](./media/enrollment-method-capab/checkmark.png)|![X](./media/enrollment-method-capab/xmark.png)|![X](./media/enrollment-method-capab/xmark.png)|

\* Configuration Manager의 클라이언트 앱 워크로드를 Intune 파일럿 또는 Intune으로 이동해야 합니다.

\** [Windows 10 1803+를 제외하고 디바이스에 대한 조건부 액세스가 차단됩니다.](device-enrollment-manager-enroll.md)

## <a name="next-steps"></a>다음 단계

[Windows 등록 설정](windows-enroll.md)

