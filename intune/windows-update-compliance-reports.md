---
title: Microsoft Intune의 Windows 업데이트용 업데이트 규정 준수 보고서 사용
titleSuffix: Microsoft Intune
description: OMS 업데이트 규정 준수를 사용하면 Intune으로 배포한 Windows 업데이트의 보고서 데이터를 볼 수 있습니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/12/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 09f3cafc16d8a08885731aa244a089367c6c0933
ms.sourcegitcommit: c715c93bb242f4fe44bbdf2fd585909854ed72b6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68660403"
---
# <a name="intune-compliance-reports-for-updates"></a>업데이트에 대한 Intune 규정 준수 보고서
Intune을 사용하여 Windows 10 디바이스에 Windows 업데이트를 배포할 때 Intune 또는 Microsoft OMS(Operations Management Suite)의 일부인 *업데이트 규정 준수*라는 무료 솔루션을 사용하여 업데이트 규정 준수에 대한 세부 정보를 살펴보세요.

## <a name="use-intune"></a>Intune 사용
구성한 Windows 10 업데이트 링의 배포 상태에 대한 정책 보고서를 검토하려면 다음을 수행합니다. 
1. [Azure 포털](https://portal.azure.com/)에 로그인합니다.
2. **모든 서비스**를 선택하고 **Intune**에서 필터링하고 **Microsoft Intune**을 선택합니다.
3. **소프트웨어 업데이트** > **개요**를 선택합니다. 할당한 모든 업데이트 링의 상태에 대한 일반 정보를 볼 수 있습니다.
4. 다음 보고서 중 하나를 엽니다.  

   **모든 배포 링의 경우**:
   1. **소프트웨어 업데이트** > **Windows 10 업데이트 링**을 엽니다.
   2. **모니터 섹션**에서 **업데이트 링 배포 상태별**을 선택합니다.  

   **특정 배포 링의 경우**:  

   1. **소프트웨어 업데이트** > **Windows 10 업데이트 링**에서 검토할 배포 링을 선택합니다.  
   2. **모니터** 섹션에서 다음 보고서 중에서 선택하여 업데이트 링에 대한 자세한 정보를 확인합니다.  
      - **디바이스 상태**  
      - **사용자 상태**  

## <a name="use-update-compliance"></a>업데이트 규정 준수 사용
Windows Analytics 솔루션인 [업데이트 규정 준수](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)를 사용하여 Windows 10 업데이트 롤아웃을 모니터링할 수 있습니다. 업데이트 규정 준수는 Azure Portal을 통해 제공되며 [필수 구성 요소](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started#update-compliance-prerequisites)를 충족하는 디바이스에서 무료로 사용할 수 있습니다.  

이 솔루션을 사용하는 경우 업데이트 규정 준수를 보고할 Intune 관리형 Windows 10 디바이스에 상용 ID를 배포합니다.  

Intune 콘솔에서 사용자 지정 정책의 OMA-URI 설정을 사용하여 상용 ID를 구성합니다. 자세한 내용은 [Microsoft Intune의 Windows 10 디바이스용 Intune 정책 설정](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune)을 참조하세요.  

상용 ID 구성을 위한 OMA-URI 경로(대/소문자 구분)는 *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*입니다.  

예를 들어 **OMA-URI 설정 추가 또는 편집**에서 다음 값을 사용할 수 있습니다.
- **설정 이름**: Windows 분석 상용 ID
- **설정 설명**: Windows Analytics 솔루션에 대한 상용 ID 구성
- **OMA-URI**(대/소문자 구분): *./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID*
- **데이터 형식**: 문자열
- **값**: \<OMS 작업 영역의 Windows 원격 분석 탭에 표시되는 GUID 사용>
 
> [!NOTE]  
> MS DM Server에 대한 자세한 내용은 [DMClient CSP(구성 서비스 공급자)]( https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)를 참조하세요.

## <a name="next-steps"></a>다음 단계
[Intune에서 소프트웨어 업데이트 관리](windows-update-for-business-configure.md)

