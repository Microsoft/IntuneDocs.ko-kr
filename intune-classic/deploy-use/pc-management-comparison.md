---
title: Windows PC 관리 옵션 비교
description: Apple DEP(장비 등록 프로그램) 또는 Apple Configurator를 사용하여 회사 소유 iOS 장치 등록
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/27/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 068a73bb-e6b3-44a6-8f6e-4cf7d455bbf3
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e2e341e8b8befa43106673607bd5c5264dd18db0
ms.sourcegitcommit: 2162ed46d939b4a9b85fa4e7e9943f2fb5948f1e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
ms.locfileid: "31617273"
---
# <a name="compare-managing-windows-pcs-as-computers-or-mobile-devices"></a>Windows PC를 컴퓨터로 관리하는 방식과 모바일 장치로 관리하는 방식 비교

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

조직은 Microsoft Intune을 사용하여 Windows PC를 모바일 장치로 관리할 수도 있고 컴퓨터로 관리할 수도 있습니다. 모바일 장치로 관리하는 경우에는 MDM(모바일 장치 관리)을 사용하고, 컴퓨터로 관리하는 경우에는 Intune 소프트웨어 클라이언트를 사용합니다.  고객은 가능한 경우 항상 MDM 관리 솔루션을 사용하는 것이 좋습니다. 아래 차트에는 이러한 옵션 간의 차이점을 보다 명확하게 파악할 수 있도록 두 관리 옵션을 비교한 내용이 나와 있습니다.

|**기능/시나리오** |**컴퓨터로 Wndows 관리**<br>Intune 소프트웨어 클라이언트 | **모바일 장치로 Windows 관리**<br>MDM |
|--------------|-------------------------------|-------------------------------|
|**운영 체제** |Windows 10, Windows 8 이상, Windows 7, Windows Vista | Windows 10 이상 |
|**Intune 포털 지원** |[Silverlight 콘솔](https://manage.microsoft.com)|[Azure Portal](https://portal.azure.com) |
|**조건부 액세스**|사용할 수 없음|사용 가능 <br>[조건부 액세스란?](https://docs.microsoft.com/intune-azure/conditional-access/what-is-conditional-access)|
|**대량 등록**|사용할 수 없음|사용 가능 <br>[Windows 장치에 대한 대량 등록](https://docs.microsoft.com/intune-azure/enroll-devices/bulk-enroll-windows)|
|**장치 프로필**|사용할 수 없음|사용 가능 <br>[Microsoft Intune 장치 프로필이란?](https://docs.microsoft.com/intune-azure/configure-devices/what-are-device-profiles)|
|**에이전트 없는 등록**|사용할 수 없음 |사용 가능<br>[Windows 장치 등록](https://docs.microsoft.com/intune-azure/enroll-devices/enroll-windows-devices)|
|**소프트웨어 업데이트 관리**| Windows Update 및 Microsoft 앱 업데이트<br>[소프트웨어 업데이트를 사용하여 Windows PC를 최신 상태로 유지](https://docs.microsoft.com/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)|Windows 10 및 Microsoft 앱 업데이트가 모두 가능한 비즈니스용 Microsoft 스토어<br> [비즈니스용 Windows 업데이트 설정 구성](https://docs.microsoft.com/intune-azure/configure-devices/how-to-configure-windows-update-for-business) |
|**소프트웨어 라이선스 관리**|사용 가능 <br>[Windows PC 소프트웨어의 사용권 계약 관리](https://docs.microsoft.com/intune/deploy-use/manage-license-agreements-for-windows-pc-software-in-microsoft-intune)|비즈니스용 Microsoft 스토어(.appx 앱에만 해당)<br>[비즈니스용 Microsoft 스토어에서 구매한 앱 관리](https://docs.microsoft.com/intune-azure/manage-apps/wsfb-apps)|
|**인벤토리**|사용 가능 <br>[Windows PC에 대한 하드웨어 및 소프트웨어 인벤토리 보기](https://docs.microsoft.com/intune/deploy-use/view-hardware-and-software-inventory-for-windows-pcs-in-microsoft-intune)|사용 가능 <br>[앱 정보를 모니터링하는 방법](https://docs.microsoft.com/intune/apps-monitor)<br>[장치 관리란?](https://docs.microsoft.com/intune/device-management)|
|**Windows 방화벽 정책**|사용 가능 <br>[Windows 방화벽 정책을 사용하여 Windows PC 보호](https://docs.microsoft.com/intune/deploy-use/help-protect-windows-pcs-using-windows-firewall-policies-in-microsoft-intune) |사용 가능 <br>[Windows Defender 방화벽](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10#windows-defender-firewall)|
|**맬웨어 방지 보호**|Endpoint Protection<br>[Endpoint Protection을 사용한 Windows PC의 보안 유지 방법](https://docs.microsoft.com/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)|Windows Defender<br>[Windows Defender 설정](https://docs.microsoft.com/intune-azure/configure-devices/custom-for-windows-10#windows-defender-settings)|
|**원격 지원** |TeamViewer<br>[Windows PC 원격 지원 요청 및 제공](https://docs.microsoft.com/intune/deploy-use/request-and-provide-remote-assistance-for-windows-pcs-in-microsoft-intune)|TeamViewer<br> [TeamViewer를 사용하여 Intune 장치 원격 관리](https://docs.microsoft.com/en-us/intune/device-profile-android-teamviewer) |
|**앱 배포** | 비즈니스용 Microsoft 스토어에는 사용할 수 없음<br>.exe, appx 및 다중 파일 .msi만 해당<br>[Intune 소프트웨어 클라이언트를 실행하는 Windows PC에 앱 추가](https://docs.microsoft.com/intune/deploy-use/add-apps-for-windows-pcs-in-microsoft-intune)|Microsoft 스토어 앱과 기간 업무 앱에 사용 가능<br>[Windows 스토어 앱을 추가하는 방법](https://docs.microsoft.com/intune/store-apps-windows)<br>[Windows LOB(기간 업무) 앱을 추가하는 방법](https://docs.microsoft.com/intune/lob-apps-windows)|
|**앱 보호**|사용할 수 없음|사용 가능 <br>[앱 보호 정책이란?](https://docs.microsoft.com/intune-azure/manage-apps/what-is-app-protection-policy)|
|**상태 증명**|사용할 수 없음|사용 가능|


### <a name="advantages-of-mdm-windows-pc-management"></a>MDM Windows PC 관리의 이점
최신 모바일 장치 관리를 통해 Windows PC를 관리하는 경우 다음과 같은 이점이 있습니다.
- **확장성** - Intune 클라우드 관리와 함께 MDM 관리를 확장할 수 있습니다. Intune 소프트웨어 클라이언트의 경우 PC를 7000대까지만 관리할 수 있습니다.
- **단순성** - 다운로드한 소프트웨어 클라이언트를 사용하지 않고 운영 체제에 포함된 최신 관리 기능을 사용할 수 있습니다.
- **일관성** - 조직의 기타 모든 모바일 장치와 같이 Windows PC를 관리할 수 있습니다.
<!-- - **Cloud optimization** - -->
