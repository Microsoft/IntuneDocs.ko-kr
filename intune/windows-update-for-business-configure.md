---
title: Microsoft Intune에서 비즈니스용 Windows 업데이트 구성 - Azure | Microsoft Docs
description: Windows 10 디바이스에서 Microsoft Intune을 사용하여 비즈니스용 Windows 업데이트 설정에서 업데이트 링을 만들고, 준수를 검토하고, 업데이트를 일시 중지하기 위해 프로필에서 소프트웨어 업데이트 설정을 업데이트합니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/15/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: coryfe
ms.suite: ems
search.appverid: MET150
ms.openlocfilehash: d0fcb021545d96fe8f5bfdf742dd4d181c91fb1a
ms.sourcegitcommit: e08a26558174be3ea8f3d20646e577f1493ea21a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54831567"
---
# <a name="manage-software-updates-in-intune"></a>Intune에서 소프트웨어 업데이트 관리

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Windows as a Service는 Windows 10 디바이스를 업데이트하는 방법입니다. Windows 10에서는 새로운 기능 업데이트 및 품질 업데이트에 모든 이전 업데이트의 내용이 포함됩니다. 최신 업데이트를 설치하면 Windows 10 디바이스가 최신 상태가 됩니다. 이전 버전의 Windows와 달리, 이제는 일부 업데이트가 아니라 전체 업데이트를 설치해야 합니다.

비즈니스용 Windows 업데이트를 사용하여 업데이트 관리 환경을 간소화할 수 있습니다. 디바이스 그룹에 대해 개별 업데이트를 승인할 필요가 없습니다. 업데이트 출시 전략을 구성하여 환경에서 위험을 관리할 수 있습니다. 그리고 Windows 업데이트에서는 적절한 시기에 업데이트가 설치되었는지 확인합니다. Microsoft Intune에서는 디바이스에서 업데이트 설정을 구성하는 기능 및 업데이트 설치를 지연하는 기능을 제공합니다. Intune에서는 업데이트를 저장하지 않고 업데이트 정책 할당만 저장합니다. 디바이스에서 Windows 업데이트에 직접 액세스하여 업데이트합니다. Intune을 사용하여 **Windows 10 업데이트 링**을 구성하고 관리합니다. 업데이트 링에는 Windows 10 업데이트 설치 시기와 방법을 구성하는 설정 그룹이 포함됩니다. 예를 들어 다음 설정을 구성할 수 있습니다.

- **Windows 10 서비스 채널**: 업데이트를 받을 디바이스 그룹에서 서비스 채널을 선택합니다. 다음과 같은 채널이 지원됩니다. 
  - Semi&#8208;연간 채널
  - Semi&#8208;연간 채널(대상 지정)
  - Windows Insider &#8208; 빠름
  - Windows Insider &#8208; 느림
  - Windows Insider 릴리스 
      
  지원되는 서비스 채널에 대한 세부 정보는 [서비스인 Windows에 대한 개요](https://docs.microsoft.com/windows/deployment/update/waas-overview#servicing-channels)를 참조하세요.
- **지연 설정**: 디바이스 그룹의 업데이트 설치를 연기하도록 업데이트 지연 설정을 구성합니다. 이러한 설정을 사용하여 업데이트 출시를 스테이징하므로 과정을 검토할 수 있습니다.
- **일시 중지**: 업데이트 출시 중에 문제가 있는 경우 업데이트 설치를 연기할 수 있습니다. 
- **유지 관리 기간**: 업데이트를 설치할 수 있는 시간을 구성합니다.
- **업데이트 형식**: 설치되는 업데이트의 형식을 선택합니다. 예를 들어 품질 업데이트, 기능 업데이트 또는 드라이버가 있습니다.
- **설치 동작**: 업데이트가 설치되는 방법을 구성합니다. 예를 들어 설치 후 디바이스가 자동으로 다시 시작되도록 할지 설정합니다.
- **피어 다운로드**: 피어 다운로드를 구성하도록 선택합니다. 구성하는 경우, 한 디바이스가 업데이트 다운로드를 마치면 다른 디바이스가 이 디바이스로부터 업데이트를 다운로드할 수 있습니다. 이 설정은 다운로드 프로세스 속도를 향상시킵니다.

업데이트 링을 만든 후에 위의 설정을 디바이스 그룹에 할당합니다. 업데이트 링을 사용하여 비즈니스 요구 사항을 반영하는 업데이트 전략을 만들 수 있습니다. 자세한 내용은 [비즈니스용 Windows 업데이트를 사용하여 업데이트 관리](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb)를 참조하세요.

## <a name="before-you-start"></a>시작하기 전에

- Windows 10 PC를 업데이트하려면 Windows Anniversary 업데이트가 포함된 Windows 10 Pro 이상을 실행 중이어야 합니다.

- Windows 업데이트는 다음 Windows 10 버전을 지원합니다.
  - Windows 10
  - Windows 10 Team(Surface Hub 디바이스용)
  - [Windows Holographic for Business](#windows-holographic-for-business-support)

  Windows 10 Mobile을 실행하는 디바이스는 지원되지 않습니다.

- Windows 디바이스에서 **피드백 및 진단** > **진단 및 사용 현황 데이터**를 **기본** 이상으로 설정해야 합니다.

    ![Windows의 진단 및 사용 현황 데이터 설정](./media/telemetry-basic.png)

    이 설정을 수동으로 구성하거나 Windows 10 이상용 Intune 프로필(**디바이스 제한** > **보고 및 원격 분석** > **사용량 데이터 공유**를 최소한 **기본**으로 설정)을 사용할 수 있습니다. 디바이스 프로필에 대한 자세한 내용은 [디바이스 제한 설정 구성](device-restrictions-configure.md)을 참조하세요.

- Azure 클래식 포털에는 디바이스 구성 프로필에 제한된 개수의 다른 Windows 10 업데이트 설정도 있습니다. Azure Portal로 마이그레이션할 때 이러한 설정 중 하나가 구성되면 다음을 수행할 것을 강력히 권장합니다.

  1. 필요한 설정을 사용하여 Azure Portal에서 Windows 10 업데이트 링을 만듭니다. **시험판 기능 허용** 설정은 더 이상 최신 Windows 10 빌드에 적용할 수 없기 때문에 Azure Portal에서 지원되지 않습니다. 업데이트 링을 만들 때 다른 설정과 기타 Windows 10 업데이트 설정을 구성할 수 있습니다.

   > [!NOTE]
   > 클래식 포털에서 만든 Windows 10 업데이트 설정은 마이그레이션 후 Azure Portal에서 표시되지 않습니다. 하지만 이러한 설정이 적용됩니다. 이러한 설정을 마이그레이션하고 Azure Portal에서 마이그레이션된 정책을 편집하는 경우 정책에서 해당 설정이 제거됩니다.

  2. 클래식 포털에서 업데이트 설정을 삭제합니다. Azure Portal로 마이그레이션하고 동일한 설정을 업데이트 링에 추가한 후에는 잠재적인 정책 충돌을 방지하기 위해 클래식 포털에서 설정을 삭제합니다. 예를 들어 동일한 설정을 서로 다른 값으로 구성한 경우 충돌이 발생합니다. 클래식 포털에 구성된 설정이 Azure Portal에 없기 때문에 쉽게 알 수 없습니다.

## <a name="create-and-assign-update-rings"></a>업데이트 링 만들기 및 할당

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **소프트웨어 업데이트** > **Windows 10 업데이트 링** > **만들기**를 선택합니다.
3. 이름, 설명(선택 사항)을 입력한 다음, **구성**을 선택합니다.
4. **설정**에서 다음 정보를 입력합니다.  

   **업데이트 설정**  
   - **서비스 채널** 디바이스가 Windows 업데이트를 받을 채널을 설정합니다.
   - **Microsoft 제품 업데이트**: Microsoft 업데이트에서 앱 업데이트를 검사하도록 선택합니다.
   - **Windows 드라이버**: 업데이트 도중에 Windows 업데이트 드라이버를 제외하도록 선택합니다.
   - **품질 업데이트 지연 기간(일)**: 품질 업데이트가 지연되는 일의 수를 입력합니다. 릴리스되고나서 최대 30일로 이러한 품질 업데이트 수신을 연기할 수 있습니다.

     품질 업데이트는 일반적으로 기존 Windows 기능에 대한 수정 및 개선 사항이며 매월 두 번째 화요일에 게시됩니다. 비즈니스용 Windows 업데이트를 통한 품질 업데이트는 Microsoft에서 언제든지 다른 업데이트를 릴리스할 수 있지만 해당 업데이트('B' 릴리스)만 수신합니다. Windows 업데이트에서 사용 가능해지면 품질 업데이트 수신을 연기할지 여부와 기간을 정의할 수 있습니다. 자세한 내용은 [비즈니스용 Windows 업데이트를 사용하여 업데이트 배포](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb)를 참조하세요.

   - **기능 업데이트 지연 기간(일)**: 기능 업데이트가 지연되는 일의 수를 입력합니다. 릴리스되고나서 최대 180일로 기능 업데이트 수신을 연기할 수 있습니다.

     기능 업데이트는 일반적으로 Windows의 새로운 기능입니다. **서비스 채널** 설정을 구성한 후에 Windows 업데이트에서 기능 업데이트가 사용 가능해지면 수신을 연기할지 여부와 기간을 정의할 수 있습니다.

     예를 들면 다음과 같습니다. **서비스 채널이 반기 채널(대상 지정)로 설정되고 지연 기간이 30일인 경우**: 기능 업데이트 X가 1월에 최초로 반기 채널(대상 지정)로 Windows 업데이트에서 공개적으로 사용할 수 있다고 가정합니다. 디바이스는 2월, 즉 30일 이후까지 업데이트를 수신하지 않습니다.

     **서비스 채널이 반기 채널로 설정되고 지연 기간이 30일인 경우**: 기능 업데이트 X가 1월에 최초로 반기 채널(대상 지정)로 Windows 업데이트에서 공개적으로 사용할 수 있다고 가정합니다. 4개월 후 4월에 기능 업데이트 X는 반기 채널로 릴리스됩니다. 디바이스는 이 반기 채널 릴리스 30일 후에 기능 업데이트를 수신하며 5월에 업데이트됩니다.  

   **사용자 환경 설정**
   
   - **자동 업데이트 동작** 자동 업데이트를 설치하는 방법, 다시 시작 또는 다시 부팅하는 시기를 선택합니다. 자세한 내용은 [Update/AllowAutoUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-configuration-service-provider#update-allowautoupdate)를 참조하세요.

     *기본값으로 다시 설정*의 설정은 *2018년 10월 업데이트* 이상을 실행하는 Windows 10 머신에서 원래 자동 업데이트 설정을 복원합니다.  

     - **자동 동작 빈도**: 업데이트 동작에 대해 **예약된 시간에 자동 설치 및 다시 시작**를 선택하는 경우 이 설정이 표시됩니다. 이 설정을 사용하여 주, 일, 시간을 비롯하여 업데이트가 설치되는 시기를 예약합니다.

   - **검사 다시 시작**: 기본적으로 사용하도록 설정되어 있습니다. 디바이스를 다시 시작하면 활성 사용자, 배터리 수준, 실행 중인 게임 등에 대한 검사를 비롯하여 일부 검사가 발생합니다. 디바이스를 다시 시작할 때 이러한 검사를 건너뛰려면 **건너뛰기**를 선택합니다.

   - **사용자가 Windows 업데이트를 일시 중지하는 것을 차단**: 기본적으로 허용됩니다. 이 설정을 사용하여 사용자가 머신의 *설정*에서 업데이트 설치를 일시 중지하는 기능을 차단 또는 허용합니다. 
      
   - **배달 최적화 다운로드 모드**: 배달 최적화는 소프트웨어 업데이트에서 더 이상 Windows 10 업데이트 링의 일부로 구성되지 않습니다. 배달 최적화는 이제 디바이스 구성을 통해 설정됩니다. 그러나 이전 구성은 여전히 콘솔에서 사용할 수 있습니다. *구성되지 않음*으로 편집하여 이러한 이전 구성을 제거할 수 있지만 그렇지 않으면 변경할 수 없습니다. 새 정책과 이전 정책 간의 충돌을 방지하려면 [기존 업데이트 링에서 배달 최적화로 이동](delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization)을 참조한 다음, 설정을 배달 최적화 프로필로 이동합니다. 

5. 작업을 완료하면 **확인**을 선택합니다. **업데이트 링 만들기**에서 **만들기**를 선택합니다.

새 업데이트 링이 업데이트 링 목록에 표시됩니다.

1. 링을 할당하려면 업데이트 링 목록에서 링을 선택한 다음 <*링 이름*> 탭에서 **할당**을 선택합니다.
2. 다음 탭에서 **포함할 그룹 선택**을 선택한 후 이 링을 할당할 그룹을 선택합니다.
3. 완료되면 **선택**을 선택하여 할당을 완료합니다.

## <a name="update-compliance-reporting"></a>업데이트 준수 보고
Intune에서 업데이트 준수를 확인하거나 업데이트 준수라는 무료 솔루션을 사용하여 확인할 수 있습니다.

### <a name="review-update-compliance-in-intune"></a>Intune에서 업데이트 준수 확인 
<!-- 1352223 --> 정책 보고서를 검토하여 구성한 Windows 10 업데이트 링의 배포 상태를 확인합니다.

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **소프트웨어 업데이트** > **개요**를 선택합니다. 할당한 모든 업데이트 링의 상태에 대한 일반 정보를 볼 수 있습니다.
3. 다음 보고서 중 하나를 엽니다.

   **모든 배포 링의 경우**:  
   1. **소프트웨어 업데이트** > **Windows 10 업데이트 링**을 엽니다.
   2. **모니터 섹션**에서 **업데이트 링 배포 상태별**을 선택합니다.

   **특정 배포 링의 경우**:  
   1. **소프트웨어 업데이트** > **Windows 10 업데이트 링**에서 검토할 배포 링을 선택합니다.
   2. **모니터** 섹션에서 다음 보고서 중에서 선택하여 업데이트 링에 대한 자세한 정보를 확인합니다.
      - **디바이스 상태**
      - **사용자 상태**

### <a name="review-update-compliance-using-oms"></a>OMS를 사용하여 업데이트 준수 검토
업데이트 준수라는 무료 솔루션을 사용하여 Windows 10 업데이트 롤아웃을 모니터링할 수 있습니다. 자세한 내용은 [Monitor Windows Updates with Update Compliance(Update Compliance를 사용하여 Windows 업데이트 모니터링)](https://technet.microsoft.com/itpro/windows/manage/update-compliance-monitor)를 참조하세요. 이 솔루션을 사용하면 업데이트 준수를 보고할 Intune 관리 Windows 10 디바이스에 상용 ID를 배포할 수 있습니다.

Intune에서 사용자 지정 정책의 OMA-URI 설정을 사용하여 상용 ID를 구성할 수 있습니다. 자세한 내용은 [Microsoft Intune의 Windows 10 디바이스용 Intune 정책 설정](custom-settings-windows-10.md)을 참조하세요.   

상용 ID 구성을 위한 OMA-URI 경로(대/소문자 구분)는 /Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID입니다.

예를 들어 **OMA-URI 설정 추가 또는 편집**에서 다음 값을 사용할 수 있습니다.

- **설정 이름**: Windows 분석 상용 ID
- **설정 설명**: Windows Analytics 솔루션에 대한 상용 ID 구성
- **OMA-URI**(대/소문자 구분): ./Vendor/MSFT/DMClient/Provider/MS DM Server/CommercialID
- **데이터 형식**: 문자열
- **값**: <*OMS 작업 영역에서 Windows 원격 분석 탭에 표시되는 GUID 사용*>

![OMA-URI 설정 - 행 편집](./media/commID-edit.png)

> [!NOTE]
> MS DM Server에 대한 자세한 내용은 [DMClient CSP(구성 서비스 공급자)](https://docs.microsoft.com/windows/client-management/mdm/dmclient-csp)를 참조하세요.

## <a name="pause-updates"></a>업데이트 일시 중지
업데이트를 일시 중지하는 시점부터 최대 35일 동안 디바이스가 기능 업데이트나 품질 업데이트를 수신하지 않게 일시 중지할 수 있습니다. 최대 일수가 경과하고 나면 일시 중지 기능은 자동으로 만료되고 디바이스가 Windows 업데이트에서 적용되는 업데이트를 검색합니다. 이 검색 이후 다시 업데이트를 일시 중지할 수 있습니다.

1. [Azure Portal](https://portal.azure.com)에서 **모든 서비스**를 선택하고 **Intune**에서 필터링한 다음, **Microsoft Intune**을 선택합니다.
2. **소프트웨어 업데이트** > **Windows 10 업데이트 링**을 선택합니다.
3. 업데이트 링 목록에서 일시 중지할 링을 선택한 다음, 일시 중지하려는 업데이트의 유형에 따라 **...** > **품질 업데이트 일시 중지** 또는 **기능 업데이트 일시 중지**를 선택합니다.

> [!IMPORTANT]
> 일시 중지 명령을 실행하면 디바이스는 다음에 서비스에 체크 인할 때 이 명령을 수신합니다. 체크 인 이전에 예약된 업데이트가 설치될 수도 있습니다.
> 또한 일시 중지 명령을 실행할 때 대상 디바이스가 꺼져 있었던 경우 디바이스를 켜면 디바이스가 Intune을 사용해 체크 인하기 전에 예약된 업데이트를 다운로드 및 설치할 수도 있습니다.

### <a name="uninstall-the-latest-from-windows-10-software-updates"></a>Windows 10 소프트웨어 업데이트에서 최신 버전 제거 
Windows 10 머신에서 주요 문제가 있는 경우 최신 기능 업데이트 또는 최신 품질 업데이트를 제거(롤백)하도록 선택할 수 있습니다. 기능 또는 품질 업데이트의 제거는 디바이스가 켜져 있는 서비스 채널에서만 사용할 수 있습니다. 제거하면 Windows 10 컴퓨터에서 이전 업데이트를 복원하는 정책이 트리거됩니다. 특히 기능 업데이트의 경우 최신 버전 제거를 적용할 수 있는 시간을 2-60일로 제한할 수 있습니다. 소프트웨어 업데이트 제거 옵션을 설정하려면:

1. Intune에서 **소프트웨어 업데이트**를 선택합니다.
2. **Windows 10 업데이트 링** > 기존 업데이트 링 선택 > **제거**를 선택합니다.

> [!NOTE]
> Windows 10 컴퓨터에서 품질 업데이트가 성공적으로 롤백된 후 최종 사용자는 **Windows 설정** > **업데이트** > **업데이트 기록**에 나열된 업데이트를 계속 볼 수 있습니다.

## <a name="windows-holographic-for-business-support"></a>Windows Holographic for Business 지원

Windows Holographic for Business는 다음과 같은 설정을 지원합니다.

- **자동 업데이트 동작**
- **Microsoft 제품 업데이트**
- **서비스 채널** **반기 채널** 및 **반기 채널(대상 지정)** 옵션 지원
