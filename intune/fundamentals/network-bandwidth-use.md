---
title: Microsoft Intune에 대한 네트워크 요구 사항 및 대역폭 세부 정보
titleSuffix: ''
description: Intune에 대한 네트워크 구성 요구 사항 및 대역폭 세부 정보를 검토합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0507d607bfac6c084f1ce0b1f59d7474810ec8b7
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73415103"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 네트워크 구성 요구 사항 및 대역폭

이 정보를 사용하여 Intune 배포에 대한 대역폭 요구 사항을 이해할 수 있습니다.

## <a name="average-network-traffic"></a>평균 네트워크 트래픽

이 표에는 각 클라이언트의 네트워크를 통해 전송되는 공통 콘텐츠의 대략적인 크기 및 주기가 정리되어 있습니다.

> [!NOTE]
> 디바이스가 Intune에서 업데이트 및 콘텐츠를 받을 수 있도록 하려면 해당 디바이스를 인터넷에 주기적으로 연결해야 합니다. 업데이트나 콘텐츠를 받는 데 필요한 시간은 경우에 따라 다르지만 매일 1시간 이상 인터넷에 계속 연결된 상태를 유지해야 합니다.

|콘텐츠 유형|대략적인 크기|주기 및 세부 정보|
|----------------|--------------------|-------------------------|
|Intune 클라이언트 설치<br /><br />**Intune 클라이언트 설치 외에도 다음 요구 사항을 충족해야 합니다.**|125 MB|**한 번**<br /><br />클라이언트 다운로드 크기는 클라이언트 컴퓨터의 운영 체제에 따라 다릅니다.|
|클라이언트 등록 패키지|15 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|Endpoint Protection 에이전트|65 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|Operations Manager 에이전트|11 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|정책 에이전트|3 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|Microsoft Easy Assist 에이전트를 통한 원격 지원|6 MB|**한 번**<br /><br />이 콘텐츠 유형에 대한 업데이트가 있는 경우 추가로 다운로드할 수 있습니다.|
|클라이언트의 일별 작업|6 MB|**매일**<br /><br />Intune 클라이언트는 Intune 서비스와 정기적으로 통신하여 업데이트 및 정책을 확인하고 클라이언트의 상태를 서비스에 보고합니다.|
|Endpoint Protection 맬웨어 정의 업데이트|상황에 따라 다름<br /><br />일반적으로 40KB -2MB|**매일**<br /><br />하루에 최대 3번|
|Endpoint Protection 엔진 업데이트|5 MB|**매월**|
|소프트웨어 업데이트|상황에 따라 다름<br /><br />크기는 배포하는 업데이트에 따라 달라집니다.|**매월**<br /><br />일반적으로 소프트웨어 업데이트는 매월 두 번째 화요일에 배포됩니다.<br /><br />새로 등록되거나 배포된 컴퓨터는 이전에 배포된 업데이트의 전체 집합을 다운로드하는 동안 네트워크 대역폭을 추가로 사용할 수 있습니다.|
|서비스 팩|상황에 따라 다름<br /><br />크기는 배포하는 각 서비스 팩에 따라 달라집니다.|**상황에 따라 다름**<br /><br />서비스 팩을 배포하는 시기에 따라 달라집니다.|
|소프트웨어 배포|상황에 따라 다름<br /><br />크기는 배포하는 소프트웨어에 따라 달라집니다.|**상황에 따라 다름**<br /><br />소프트웨어를 배포하는 시기에 따라 달라집니다.|

## <a name="ways-to-reduce-network-bandwidth-use"></a>네트워크 대역폭 사용량을 줄이는 방법

다음 방법 중 하나 이상을 사용하여 Intune 클라이언트의 네트워크 대역폭 사용을 줄일 수 있습니다.

### <a name="use-a-proxy-server-to-cache-content-requests"></a>프록시 서버를 사용하여 콘텐츠 요청 캐시

프록시 서버는 콘텐츠를 캐시하여 중복 다운로드를 줄이고 인터넷에서 콘텐츠의 네트워크 대역폭을 줄일 수 있습니다.

클라이언트 컴퓨터에서 콘텐츠를 받는 캐싱 프록시 서버는 해당 콘텐츠를 검색하고 웹 응답 및 다운로드를 모두 캐시할 수 있습니다. 서버는 캐시된 데이터를 사용하여 클라이언트의 후속 요청에 응답합니다.

다음은 Intune 클라이언트의 콘텐츠를 캐시할 프록시 서버에 사용하는 일반적인 설정입니다.


|          Setting           |           권장 값           |                                                                                                  세부 정보                                                                                                  |
|----------------------------|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         캐시 크기         |             5GB - 30GB             | 값은 사용하는 구성 및 네트워크의 클라이언트 컴퓨터의 수에 따라 달라집니다. 파일이 너무 빠르게 삭제되지 않도록 하려면 환경에 맞게 캐시 크기를 조정하세요. |
| 개별 캐시 파일 크기 |                950 MB                 |                                                                     이 설정은 모든 캐싱 프록시 서버에서 사용할 수 없습니다.                                                                     |
|   캐시할 개체 유형    | HTTP<br /><br />HTTPS<br /><br />BITS |                                               Intune 패키지는 HTTP를 통한 BITS(Background Intelligent Transfer Service) 다운로드로 검색되는 CAB 파일입니다.                                               |
> [!NOTE]
> 프록시 서버를 사용하여 콘텐츠 요청을 캐시하는 경우 클라이언트와 프록시 간 통신과 프록시에서 Intune으로 통신만 암호화됩니다. 클라이언트에서 Intune으로 연결은 엔드투엔드로 암호화되지 않습니다.

프록시 서버를 사용하여 콘텐츠를 캐시하는 방법에 대해서는 사용 중인 프록시 서버 솔루션의 설명서를 참조하세요.

### <a name="use-background-intelligent-transfer-service-bits-on-computers"></a>컴퓨터에서 BITS(Background Intelligent Transfer Service) 사용

구성한 시간 동안 Windows 컴퓨터에서 BITS를 사용하여 네트워크 대역폭을 줄일 수 있습니다. Intune 에이전트 정책의 **네트워크 대역폭** 페이지에서 BITS 정책을 구성할 수 있습니다.

> [!NOTE]
> Windows에서 MDM 관리를 위해 MobileMSI 앱 유형의 OS 관리 인터페이스에서만 다운로드에 BITS를 사용합니다. AppX/MsiX는 자체 BITS 이외 다운로드 스택을 사용하고 Intune 에이전트를 통한 Win32 앱은 BITS가 아닌 배달 최적화를 사용합니다.

BITS 및 Windows 컴퓨터에 대한 자세한 내용은 TechNet 라이브러리의 [Background Intelligent Transfer Service](https://technet.microsoft.com/library/bb968799.aspx)를 참조하세요.

### <a name="delivery-optimization"></a>배달 최적화

배달 최적화를 사용하면 Windows 10 디바이스에서 애플리케이션 및 업데이트를 다운로드할 때 Intune을 통해 대역폭 소비를 줄일 수 있습니다. 자체 구성 분산 캐시를 사용하여 기존 서버와 대체 원본(예: 네트워크 피어)에서 다운로드를 끌어올 수 있습니다.

배달 최적화에서 지원되는 Windows 10 버전 및 콘텐츠 형식의 전체 목록을 보려면 [Windows 10 업데이트에 대한 배달 최적화 문서](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#requirements)를 참조하세요.

디바이스 구성 프로필의 일부로서 [배달 최적화를 설정](../configuration/delivery-optimization-settings.md)할 수 있습니다.

### <a name="use-branchcache-on-computers"></a>컴퓨터에서 BranchCache 사용

Intune 클라이언트는 BranchCache를 사용하여 WAN(광역 네트워크) 트래픽을 줄일 수 있습니다. 다음 운영 체제에서 BranchCache를 지원합니다.

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

BranchCache를 사용하려면 클라이언트 컴퓨터에서 BranchCache를 사용하도록 설정한 후 **분산 캐시 모드**에 대해 구성해야 합니다.

컴퓨터에 Intune 클라이언트를 설치할 때 기본적으로 BranchCache 및 분산 캐시 모드는 사용하도록 설정됩니다. 그러나 그룹 정책에서 BranchCache를 사용하지 않도록 설정한 경우 Intune에서 해당 정책을 재정의하지 않으므로 BranchCache는 계속 사용되지 않도록 설정됩니다.

BranchCache를 사용하는 경우 조직의 다른 관리자와 함께 그룹 정책 및 Intune 방화벽 정책을 관리합니다. BranchCache 또는 방화벽 예외를 사용하지 않도록 설정하는 정책을 배포하지 않아야 합니다. BranchCache에 대한 자세한 내용은 [BranchCache 개요](https://technet.microsoft.com/library/hh831696.aspx)를 참조하세요.

> [!NOTE]
> Microsoft Intune을 사용하여 Windows PC를 모바일 디바이스로 관리할 수도 있고 컴퓨터로 관리할 수도 있습니다. [모바일 디바이스로 관리하는 경우에는 MDM(모바일 디바이스 관리)을 사용하고](../enrollment/windows-enroll.md), 컴퓨터로 관리하는 경우에는 Intune 소프트웨어 클라이언트를 사용합니다. 고객은 가능한 경우 항상 [MDM 관리 솔루션](../enrollment/windows-enroll.md)을 사용하는 것이 좋습니다. 이러한 방식으로 관리되는 경우 BranchCache는 지원되지 않습니다. 자세한 내용은 [Windows PC를 컴퓨터로 관리하는 방식과 모바일 디바이스로 관리하는 방식 비교](../pc-management-comparison.md)를 참조하세요.


## <a name="next-steps"></a>다음 단계

[Intune에 대한 엔드포인트 검토](../intune-endpoints.md)

