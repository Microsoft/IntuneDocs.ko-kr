---
title: 인벤토리를 사용하는 장치 이해
description: Intune을 사용하여 관리하는 장치의 하드웨어에 대한 정보를 확인합니다.
keywords: ''
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 09/05/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 312911fe-b963-4949-9911-ae425e0590b2
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e50a7329512e6b57eb5486792669b7cd102eebdb
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31023396"
---
# <a name="understand-your-devices-with-inventory-in-microsoft-intune"></a>Microsoft Intune에서 인벤토리를 사용하는 장치 이해

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Microsoft Intune을 사용하면 Intune 클라이언트 소프트웨어를 실행하는 Windows PC와 등록된 장치의 인벤토리를 볼 수 있습니다.
Intune은 대개 7일마다 관리 장치에서 인벤토리를 수집합니다. 이로 인해 최근에 수행한 장치 변경(예: 장치 이름 변경 또는 저장소 공간 확보)의 결과가 보고서에 표시될 때까지 시간이 약간 지연될 수 있습니다.

## <a name="whats-collected-from-enrolled-devices"></a>등록된 장치에서 무엇이 수집되나요?
모바일 장치에 의해 수집된 인벤토리를 보려면 [모바일 장치 인벤토리 보고서](understand-microsoft-intune-operations-by-using-reports.md)를 실행합니다. Intune은 등록된 장치에서 다음 인벤토리를 수집합니다.

|속성|수집되는 장치|
|------------|-----------------------|
|**Name**|All 장치|
|**운영 체제**|All 장치|
|**제조업체**|All 장치|
|**모델**|All 장치|
|**관리 채널**|All 장치|
|**등록된 AAD**|Mac OS X를 제외한 모든 장치|
|**규격**|All 장치|
|**EAS 활성화됨**|Mac OS X를 제외한 모든 장치|
|**EAS 활성화 ID**|Mac OS X를 제외한 모든 장치|
|**EAS 활성화 시간**|Mac OS X를 제외한 모든 장치|
|**관리 상태**|All 장치|
|**메일 주소**|All 장치|
|**Exchange ActiveSync ID**|All 장치|
|**무단 해제되거나 루팅됨**|iOS 및 Android 장치만|
|**고유한 장치 ID**|Exchange ActiveSync를 제외한 모든 장치|
|**일련 번호**|iOS, Mac OS X, Android, Windows 8.1 및 Windows 10 데스크톱 장치|
|**총 저장소 공간**|iOS, Mac OS X, Windows 8.1, Windows 10 데스크톱 및 모바일 장치|
|**사용 가능한 저장소 공간**|iOS, Mac OS X, Windows 8.1 및 Windows 10 데스크톱 장치|
|**전화 번호**<br>회사로 분류되는 전화는 전체 전화 번호로 식별됩니다(예: 모바일 장치 인벤토리 보고서를 실행하는 경우). BYOD 전화 번호는 &#42;으로 마스킹되고 마지막 4자리만 표시됩니다.|iOS, Android, 및 Windows Phone 장치|
|**IMEI #2**|Exchange ActiveSync, iOS, Android, 및 Windows Phone 장치|
|**MEID**<br>Mobile Equipment Identifier|iOS 장치만|
|**Wi-Fi MAC**|Exchange ActiveSync를 제외한 모든 장치|
|**구독자의 통신사**|iOS 및 Android 장치만|
|**셀룰러 기술**|iOS 및 Android 장치만|
|**감독됨**|iOS 장치만|
|**활성화 잠금 상태**|iOS 장치만|
|**등록된 날짜**|All 장치|
|**마지막 업데이트 날짜**.|All 장치|
|**이더넷 MAC**|Mac OS X 장치만|
|**활성화 잠금 사용**|iOS 장치만|
|**암호화 사용**|All 장치|

>[!NOTE]
>장치에서 사용하는 이동 통신 사업자에 따라 위 항목 중 일부는 수집되지 않을 수 있습니다.

## <a name="whats-collected-from-windows-pcs"></a>Windows PC에서 수집되는 내용
> [!IMPORTANT]
> 이 섹션은 Intune Windows PC 클라이언트 소프트웨어를 실행하는 Windows PC에만 적용됩니다.

Windows PC에 의해 수집된 인벤토리를 보려면 [컴퓨터 인벤토리 보고서](understand-microsoft-intune-operations-by-using-reports.md)를 실행합니다. Intune은 Windows PC에서 다음 인벤토리를 수집합니다.

-   **Name**

-   **섀시 유형**

-   **제조업체**

-   **모델**

-   **운영 체제**

-   **TPM 버전**

-   **총 디스크 공간**

-   **사용된 디스크 공간**

-   **사용 가능한 디스크 공간**

-   **OS 디스크 이름**

-   **OS 디스크 공간**

-   **사용 가능한 OS 디스크 공간**

-   **실제 메모리**

-   **프로세서 이름**

-   **프로세서 아키텍처**

-   **CPU 속도**

-   **IP 주소**

-   **일련 번호**

-   **마지막 로그온 사용자**

-   **할당된 사용자**

-   **마지막 업데이트 날짜**.

<!-- this section below belongs in the planning journey
### See Also
[Monitoring and reports with Microsoft Intune](monitoring-and-reports-with-microsoft-intune.md)
-->
