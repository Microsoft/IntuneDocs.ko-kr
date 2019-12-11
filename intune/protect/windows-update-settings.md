---
title: Microsoft Intune의 비즈니스요 Windows 업데이트 설정 - Azure | Microsoft Docs
description: Intune을 사용하여 배포할 수 있는 Windows 10 디바이스에 대한 WUfB 설정입니다.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/18/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: aiwang
ms.suite: ems
search.appverid: MET150
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f3359bc5544b3a353271ea17083c8c3acb49742
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72584459"
---
# <a name="windows-update-settings-for-intune"></a>Intune에 대한 Windows 업데이트 설정  

Windows 10 업데이트 설정 보기에서 Microsoft Intune으로 [구성 및 관리](windows-update-for-business-configure.md)할 수 있습니다.  

Intune에서 Windows 10 업데이트 링에 대한 설정을 구성하면, Windows 업데이트 설정을 구성하는 것입니다. Windows 업데이트 설정에 Windows 10 버전 종속성이 있으면, 버전 종속성이 설정 세부 정보에 기록됩니다.  

## <a name="update-settings"></a>업데이트 설정  

업데이트 설정은 디바이스가 다운로드할 비트를 제어합니다. 각 설정의 동작에 대한 자세한 내용은 Windows 참조 설명서를 참조하세요.  

- **서비스 채널**  
  **기본값**: 반기 채널  
  Windows 업데이트 CSP: [업데이트/BranchReadinessLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-branchreadinesslevel)  

  디바이스가 Windows 업데이트를 받을 채널(분기)을 설정합니다. 업데이트가 전달되기 전에 채널에 따라 사용되는 지연 기간이 서로 다를 수 있습니다.  

  예를 들어 반기 채널에는 6개월 지연이 포함됩니다.  이 설정 본문에서 추가 지연 없이 이 채널을 사용하는 경우, 디바이스는 릴리스된 지 6개월 후에 업데이트를 설치합니다.  

  지원되는 업데이트 채널:  

  - 반기 채널  
  - 반기 채널(대상 지정)  
  - Windows Insider – 빠름  
  - Windows Insider – 느림  
  - Windows Insider 릴리스  

  Insider 채널을 선택하면, Intune이 자동으로 Windows 업데이트 설정 [Update/ManagePreviewBuilds](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-managepreviewbuilds)를 구성하므로 Insider 빌드가 작동합니다.  


  > [!IMPORTANT]  
  > Windows 버전 1903부터 반기 채널(대상 지정)(SAC-T)이 사용 중지됩니다.  이 변경으로 SAC-T는 반기 채널과 병합됩니다.  이 변경 및 비즈니스용 Windows 업데이트에 미치는 영향을 자세히 알아보려면, Windows IT Pro 블로그 게시물 [Windows Update for Business and the retirement of SAC-T](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523)(비즈니스용 Windows 업데이트 및 SAC-T 사용 중지)를 참조하세요.  
 
- **Microsoft 제품 업데이트**  
  **기본값**: 허용  
  Windows 업데이트 CSP: [업데이트/AllowMUUpdateService](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowmuupdateservice)

  - **허용** -Microsoft 업데이트에서 앱 업데이트를 검색 하도록 *허용* 을 선택 합니다.  
  - **차단** -앱 업데이트 검색을 방지 하려면 차단을 선택 합니다.  

- **Windows 드라이버**  
  **기본값**: 허용  
  Windows 업데이트 CSP: [업데이트/ExcludeWUDriversInQualityUpdate](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-excludewudriversinqualityupdate)  

  - **허용** -업데이트 중 Windows 업데이트 드라이버 포함 *허용* 을 선택 합니다.  
  - **차단** -드라이버 검색을 방지 하려면 차단을 선택 합니다.  

- **품질 업데이트 지연 기간(일)**  
  **기본값**: 0  
  Windows 업데이트 CSP: [업데이트/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays)  

  품질 업데이트가 지연되는 0~30일의 기간을 지정합니다. 이 기간은 선택한 서비스 채널의 일부인 지연 기간에 추가됩니다. 디바이스에서 정책을 수신하면 지연 기간이 시작됩니다.  

  품질 업데이트는 일반적으로 기존 Windows 기능의 수정 및 향상된 기능입니다.  

- **기능 업데이트 지연 기간(일)**  
  **기본값**: 0  
  Windows 업데이트 CSP: [업데이트/PauseFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays)  

  기능 업데이트가 지연되는 기간(일)을 지정합니다. 이 기간은 선택한 서비스 채널의 일부인 지연 기간에 추가됩니다. 디바이스에서 정책을 수신하면 지연 기간이 시작됩니다.  

  지원되는 지연 기간:  

  - *Windows 버전 1709 이상* -0 ~ 365 일  
  - *Windows 버전 1703* - 0~180일  

  기능 업데이트는 일반적으로 Windows의 새로운 기능입니다.  

- **기능 업데이트 제거 기간 설정(2~60일)**  
  **기본값**: 10  
  Windows 업데이트 CSP: [업데이트/ConfigureFeatureUpdateUninstallPeriod](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configurefeatureupdateuninstallperiod)  

  기능 업데이트를 제거해야 하는 기간을 구성합니다.  

  이 기간이 만료되면, 이전 업데이트 비트가 디바이스에서 제거되고, 더 이상 이전 업데이트 버전을 제거할 수 없습니다.  

  예를 들어 기능 업데이트 제거 기간이 20일인 업데이트 링을 고려합니다. 25일 후에 최신 기능 업데이트를 롤백하고 [제거] 옵션을 사용하기로 결정합니다.  최소 20일 전에 기능 업데이트를 설치한 디바이스는 유지 관리의 일부로 필요한 비트를 제거했으므로 기능 업데이트를 제거할 수 없습니다. 그러나 최대 19일 전에 기능 업데이트만 설치한 디바이스는 제거 기간 20일을 초과하기 전에 제거 명령을 수신하도록 성공적으로 체크 인한 경우, 업데이트를 제거할 수 있습니다.  

## <a name="user-experience-settings"></a>사용자 환경 설정  

사용자 환경 설정은 디바이스 다시 시작 및 미리 알림에 대한 최종 사용자 환경을 제어합니다. 각 설정의 동작에 대한 자세한 내용은 Windows 업데이트 CSP 설명서를 참조하세요.  

- **자동 업데이트 동작**  
  **기본값**: 유지 관리 시간에 자동 설치  
  Windows 업데이트 CSP: [업데이트/Allowautoupdate 업데이트](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

  자동 업데이트를 설치하는 방법 및 필요한 경우, 디바이스를 다시 시작할 시기를 선택합니다.  

  지원 옵션:  

  - **다운로드 알림** - 업데이트를 다운로드하기 전에 사용자에게 알립니다. 사용자는 업데이트를 다운로드 및 설치하도록 선택합니다.  

  - **유지 관리 시간에 자동 설치** – 업데이트가 자동으로 다운로드된 다음, 디바이스가 사용되지 않거나 절전 모드로 실행되는 자동 유지 관리 중에 설치됩니다. 다시 시작이 필요한 경우, 최대 7일 동안 다시 시작할지 묻는 메시지가 사용자에게 표시된 후 다시 시작이 적용됩니다.  

    이 옵션은 업데이트가 설치된 후 자동으로 디바이스를 다시 시작할 수 있습니다. **활성 시간** 설정을 사용하여 자동 다시 시작이 차단되는 기간을 정의합니다.  

    - **활성 시간 시작** - 업데이트 설치로 인한 다시 시작을 차단하기 위한 시작 시간을 지정합니다.  
      **기본**: 오전 8시  
      Windows 업데이트 CSP: [업데이트/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **활성 시간 종료** - 업데이트 설치로 인한 다시 부팅을 차단하기 위한 종료 시간을 지정합니다.  
      **기본값**: 오후 5시  
      Windows 업데이트 CSP: [업데이트/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **유지 관리 시간에 자동 설치 및 다시 시작** – 업데이트가 자동으로 다운로드된 후 디바이스가 사용되지 않거나 절전 모드로 실행되는 자동 유지 관리 중에 설치됩니다. 다시 시작이 필요한 경우, 사용되지 않을 때 디바이스가 다시 시작됩니다. (이 설정은 관리되지 않는 디바이스의 기본값입니다.)  

    이 옵션은 업데이트가 설치된 후 자동으로 디바이스를 다시 시작할 수 있습니다. **활성 시간** 설정 사용은 Windows 업데이트 설정에서 설명되지 않지만, 이 설정은 Intune에서 자동 다시 시작이 차단되는 기간을 정의하는 데 사용됩니다.  

    - **활성 시간 시작** - 업데이트 설치로 인한 다시 시작을 차단하기 위한 시작 시간을 지정합니다.  
      **기본**: 오전 8시  
      Windows 업데이트 CSP: [업데이트/ActiveHoursStart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursstart)  
  
    - **활성 시간 종료** - 업데이트 설치로 인한 다시 부팅을 차단하기 위한 종료 시간을 지정합니다.  
      **기본값**: 오후 5시  
      Windows 업데이트 CSP: [업데이트/ActiveHoursEnd](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-activehoursend)  

  - **예약된 시간에 자동 설치 및 다시 시작** – 설치 날짜 및 시간을 지정합니다. 이 옵션을 지정하지 않으면, 매일 오전 3시에 설치가 실행되고, 이후 다시 시작될 때까지 15분씩 카운트다운됩니다. 로그온한 사용자는 카운트다운 및 다시 시작을 연기할 수 있습니다.   
  Windows 업데이트 CSP: [업데이트/Allowautoupdate 업데이트](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-allowautoupdate)  

    이 옵션은 추가 설정을 지원합니다.  

    - **자동 동작 빈도** - 이 설정을 사용하여 주, 일, 시간을 비롯하여 업데이트가 설치되는 시기를 예약합니다.  
      **기본값**: 매주

    - **예약된 설치 날짜** - 업데이트를 설치할 요일을 지정합니다.  
      **기본값**: 임의의 요일  

    - **예약된 설치 시간** - 업데이트를 설치할 시간을 지정합니다.  
      **기본값**: 오전 3시  

  - **최종 사용자 제어 없이 자동 설치 및 다시 부팅** – 업데이트가 자동으로 다운로드된 후 디바이스가 사용되지 않거나 절전 모드로 실행되는 자동 유지 관리 중에 설치됩니다. 다시 시작이 필요한 경우, 사용되지 않을 때 디바이스가 다시 시작됩니다. 이 옵션은 최종 사용자 제어 창을 읽기 전용으로 설정합니다.  

  - **기본값으로 다시 설정** - 2018년 10월 업데이트 이상을 실행하는 Windows 10 머신에서 원래 자동 업데이트 설정을 복원합니다.  


- **검사 다시 시작**  
  **기본값**: 허용  
  Windows 업데이트 CSP: [Update/SetEDURestart](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setedurestart)  

  디바이스를 다시 시작할 때 이러한 검사를 건너뛰려면 **건너뛰기**를 선택합니다. 
  
  이 설정은 Windows의 디바이스 버전에 따라 다른 결과가 나타납니다.  
 
  - *Windows 버전 1703 이하* - 디바이스를 다시 시작하면 활성 사용자, 배터리 수준, 실행 중인 게임 등에 대한 검사를 비롯하여 몇 가지 검사가 수행됩니다.  
  
  - *Windows 버전 1709 이상* - 활성 시간 중에는 업데이트를 위해 검사, 다운로드, 설치 및 다시 부팅 프로세스가 실행되지 않습니다. 활성 시간 후에는 업데이트 프로세스가 실행되고, 배터리 검사 및 전원 검사에 통과할 경우, 디바이스를 절전 모드에서 해제하고 디바이스를 검사, 다운로드, 설치 및 다시 부팅할 수 있습니다. 

- **사용자가 Windows 업데이트를 일시 중지하는 것을 차단**  
  **기본값**: 허용  
  Windows 업데이트 CSP: [업데이트/SetDisablePauseUXAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisablepauseuxaccess)  

  - **허용** -장치 사용자가 업데이트 설치를 일시 중지할 수 있습니다.  
  - **차단** -장치 사용자가 업데이트 설치를 일시 중지 하지 못하도록 합니다.  

- **사용자의 Windows 업데이트 검색 차단**  
  **기본값**: 허용  
  Windows 업데이트 CSP: [업데이트/SetDisableUXWUAccess](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-setdisableuxwuaccess) 

  - **허용** -장치 사용자가 Windows 업데이트 검색을 사용 하 여 업데이트를 찾고 다운로드 하 고 기능을 설치할 수 있도록 허용 합니다.
  - **차단** -장치 사용자가 Windows 업데이트 검색에 액세스 하거나 업데이트를 다운로드 하 고 기능을 설치 하는 것을 방지 합니다.  

- **업무 시간 이후에 다시 시작하려면 사용자의 승인이 필요합니다.**  
  **기본값**: 구성되지 않음  
  Windows 업데이트 CSP: [업데이트/AutoRestartRequiredNotificationDismissal](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-autorestartrequirednotificationdismissal)
  
  - **구성되지 않음**  
  - **필수** - 업무 시간 이후에 사용자가 디바이스 다시 시작을 승인해야 합니다.  
   
- **해제할 수 있는 미리 알림(시간)이 설정된 필수 자동 다시 시작을 실행하기 전 사용자에게 미리 알립니다.**  
  **기본값**: 4  
  Windows 업데이트 CSP: [업데이트/ScheduleRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-schedulerestartwarning)  

  자동으로 다시 시작하기 전에 디바이스 사용자에게 해당 다시 시작에 대한 해제할 수 있는 알림을 표시할 기간을 지정합니다. **2**, **4**, **8**, **12** 또는 **24**시간 값이 지원됩니다.  
  
  기본값을 지우면이 설정이 *구성 되지 않습니다*.  

- **영구 미리 알림(분)이 설정된 필수 자동 다시 시작을 실행하기 전 사용자에게 미리 알립니다.**  
  **기본값**: 15  
  Windows 업데이트 CSP: [업데이트/ScheduleImminentRestartWarning](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-scheduleimminentrestartwarning)  

  자동으로 다시 시작하기 전에 디바이스 사용자에게 해당 다시 시작에 대한 해제할 수 없는 경고를 표시할 기간을 지정합니다. **15**, **30** 또는 **60**분 값이 지원됩니다.  

  기본값을 지우면이 설정이 *구성 되지 않습니다*.  

- **업데이트 알림 수준 변경**  
  **기본값**: 기본 Windows 업데이트 알림 사용  
  Windows 업데이트 CSP: [업데이트/UpdateNotificationLevel](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-updatenotificationlevel)
  
  사용자에게 표시되는 Windows 업데이트 알림 수준을 지정합니다. 이 설정은 업데이트가 다운로드 및 설치되는 방법 및 시기를 제어하지 않습니다.  

  지원 옵션:
  - **구성되지 않음**
  - **기본 Windows 업데이트 알림 사용**
  - **다시 시작 경고를 제외 하 고 모든 알림을 해제 합니다.**
  - **다시 시작 경고를 포함 하 여 모든 알림 해제**  

- **최종 기한 설정 사용**  
  **기본값**: 구성되지 않음  
 
  사용자가 최종 기한 설정을 사용할 수 있습니다.  

  - **구성되지 않음**
  - **허용**

  *허용*으로 설정 하면 마감일에 대해 다음 설정을 구성할 수 있습니다.

  - **기능 업데이트 최종 기한**  
    **기본값**: *구성되지 않음*  
    Windows 업데이트 CSP: [업데이트/ConfigureDeadlineForFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforfeatureupdates)  

    장치에 기능 업데이트가 자동으로 설치 되기 전까지 남은 일 수를 지정 합니다 (2-30).

  - **품질 업데이트 최종 기한**  
    **기본값**: *구성되지 않음*  
    Windows 업데이트 CSP: [업데이트/ConfigureDeadlineForQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlineforqualityupdates)

    사용자가 장치에 자동으로 설치 하기 전까지 남은 일 수를 지정 합니다 (2-30).

  - **유예 기간**  
    **기본값**: *구성 되지 않음* Windows 업데이트 CSP: [업데이트/ConfigureDeadlineGracePeriod]( https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinegraceperiod)

    다시 시작이 자동으로 발생할 때까지 마감일 이후의 최소 일 수를 지정 합니다 (2-7).

  - **최종 기한 전 자동 다시 부팅**  
    **기본값**: 예 Windows 업데이트 CSP: [Update/ConfigureDeadlineNoAutoReboot](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-configuredeadlinenoautoreboot)

    최종 기한 전에 장치를 자동으로 다시 부팅 해야 하는지 여부를 지정 합니다.
    - **예**
    - **아니요**

### <a name="delivery-optimization-download-mode"></a>배달 최적화 다운로드 모드  

배달 최적화는 소프트웨어 업데이트에서 더 이상 Windows 10 업데이트 링의 일부로 구성되지 않습니다. 배달 최적화는 이제 디바이스 구성을 통해 설정됩니다. 그러나 이전 구성은 여전히 콘솔에서 사용할 수 있습니다. *구성되지 않음*으로 편집하여 이러한 이전 구성을 제거할 수 있지만 그렇지 않으면 변경할 수 없습니다. 

새 정책과 이전 정책 간의 충돌을 방지하려면 [기존 업데이트 링에서 배달 최적화로 이동](../configuration/delivery-optimization-windows.md#move-existing-update-rings-to-delivery-optimization)을 참조한 다음, 설정을 배달 최적화 프로필로 이동합니다.
