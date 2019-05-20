---
title: Microsoft Intune에 대한 네트워크 요구 사항 및 대역폭 세부 정보
titleSuffix: ''
description: Intune에 대한 네트워크 구성 요구 사항 및 대역폭 세부 정보를 검토합니다.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 04/03/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 0f737d48-24bc-44cd-aadd-f0a1d59f6893
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic; get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40f9ada715570de7b5b2f95292b7ed0d238242d2
ms.sourcegitcommit: 04d29d47b61486b3586a0e0e5e8e48762351f2a3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59570795"
---
# <a name="intune-network-configuration-requirements-and-bandwidth"></a>Intune 네트워크 구성 요구 사항 및 대역폭

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Intune 관리자는 이 문서의 지침을 참조하여 Intune 서비스의 네트워크 요구 사항을 파악할 수 있습니다. 이 문서의 정보를 참조하여 프록시 설정에 필요한 IP 주소 및 포트 설정과 대역폭 요구 사항을 파악할 수 있습니다.

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

BITS 및 Windows 컴퓨터에 대한 자세한 내용은 TechNet 라이브러리의 [Background Intelligent Transfer Service](http://technet.microsoft.com/library/bb968799.aspx)를 참조하세요.

### <a name="use-branchcache-on-computers"></a>컴퓨터에서 BranchCache 사용
Intune 클라이언트는 BranchCache를 사용하여 WAN(광역 네트워크) 트래픽을 줄일 수 있습니다. 다음 운영 체제에서 BranchCache를 지원합니다.

- Windows 7
- Windows 8.0
- Windows 8.1
- Windows 10

BranchCache를 사용하려면 클라이언트 컴퓨터에서 BranchCache를 사용하도록 설정한 후 **분산 캐시 모드**에 대해 구성해야 합니다.

컴퓨터에 Intune 클라이언트를 설치할 때 기본적으로 BranchCache 및 분산 캐시 모드는 사용하도록 설정됩니다. 그러나 그룹 정책에서 BranchCache를 사용하지 않도록 설정한 경우 Intune에서 해당 정책을 재정의하지 않으므로 BranchCache는 계속 사용되지 않도록 설정됩니다.

BranchCache를 사용하는 경우 조직의 다른 관리자와 함께 그룹 정책 및 Intune 방화벽 정책을 관리합니다. BranchCache 또는 방화벽 예외를 사용하지 않도록 설정하는 정책을 배포하지 않아야 합니다. BranchCache에 대한 자세한 내용은 [BranchCache 개요](http://technet.microsoft.com/library/hh831696.aspx)를 참조하세요.

## <a name="network-communication-requirements"></a>네트워크 통신 요구 사항

관리하는 디바이스와 클라우드 기반 서비스에 필요한 엔드포인트 간에 네트워크 통신을 사용하도록 설정합니다.

클라우드 전용 서비스인 Intune에는 서버 또는 게이트웨이와 같은 온-프레미스 인프라가 필요하지 않습니다.

방화벽 및 프록시 서버로 보호되는 디바이스를 관리하려면 Intune에 대한 통신을 사용하도록 설정해야 합니다.

- 프록시 서버는 **HTTP(80)** 와 **HTTPS(443)** 를 모두 지원해야 합니다. Intune 클라이언트에서 두 프로토콜을 모두 사용하기 때문입니다.
- 소프트웨어 업데이트 다운로드 등의 일부 작업을 위해 Intune에는 manage.microsoft.com에 대한 인증되지 않은 프록시 서버 액세스가 필요합니다.

개별 클라이언트 컴퓨터에서 프록시 서버 설정을 수정할 수 있습니다. 그룹 정책을 사용하여 지정된 프록시 서버로 보호되는 모든 클라이언트 컴퓨터의 설정을 변경할 수도 있습니다.


<!--
> [!NOTE] If Windows 8.1 devices haven't cached proxy server credentials, enrollment might fail because the request doesn't prompt for credentials. Enrollment fails without warning as the request wait for a connection. If users might experience this issue, instruct them to open their browser settings and save proxy server settings to enable a connection.   -->

관리되는 디바이스를 사용하려면 **모든 사용자**가 방화벽을 통해 서비스에 액세스할 수 있도록 구성해야 합니다.

다음 표에는 Intune 클라이언트에서 액세스하는 포트 및 서비스가 정리되어 있습니다.

|**도메인**|**IP 주소**|
|---------------------|-----------|
|login.microsoftonline.com | 추가 정보: [Office 365 URL 및 IP 주소 범위](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) |
|portal.manage.microsoft.com<br> m.manage.microsoft.com |52.175.12.209<br>20.188.107.228<br>52.138.193.149<br>51.144.161.187<br>52.160.70.20<br>52.168.54.64 |
| sts.manage.microsoft.com | 13.93.223.241 <br>52.170.32.182 <br>52.164.224.159 <br>52.174.178.4 <br>13.75.122.143 <br>52.163.120.84|
|Manage.microsoft.com <br>i.manage.microsoft.com <br>r.manage.microsoft.com <br>a.manage.microsoft.com <br>p.manage.microsoft.com <br>EnterpriseEnrollment.manage.microsoft.com <br>EnterpriseEnrollment-s.manage.microsoft.com | 40.83.123.72<br>13.76.177.110<br>52.169.9.87<br>52.174.26.23<br>104.40.82.191<br>13.82.96.212|
|fei.msua01.manage.microsoft.com<br>portal.fei.msua01.manage.microsoft.com <br>m.fei.msua01.manage.microsoft.com<br>fei.msua02.manage.microsoft.com<br>portal.fei.msua02.manage.microsoft.com<br>m.fei.msua02.manage.microsoft.com<br>fei.msua04.manage.microsoft.com<br>portal.fei.msua04.manage.microsoft.com <br>m.fei.msua04.manage.microsoft.com<br>fei.msua05.manage.microsoft.com <br>portal.fei.msua05.manage.microsoft.com <br>m.fei.msua05.manage.microsoft.com<br>fei.amsua0502.manage.microsoft.com <br>portal.fei.amsua0502.manage.microsoft.com <br>m.fei.amsua0502.manage.microsoft.com<br>fei.msua06.manage.microsoft.com <br>portal.fei.msua06.manage.microsoft.com <br>m.fei.msua06.manage.microsoft.com<br>fei.amsua0602.manage.microsoft.com <br>portal.fei.amsua0602.manage.microsoft.com <br>m.fei.amsua0602.manage.microsoft.com<br>fei.amsua0202.manage.microsoft.com <br>portal.fei.amsua0202.manage.microsoft.com <br>m.fei.amsua0202.manage.microsoft.com<br>fei.amsua0402.manage.microsoft.com <br>portal.fei.amsua0402.manage.microsoft.com <br>m.fei.amsua0402.manage.microsoft.com|52.160.70.20<br>52.168.54.64 |
|fei.msub01.manage.microsoft.com <br>portal.fei.msub01.manage.microsoft.com <br>m.fei.msub01.manage.microsoft.com<br>fei.amsub0102.manage.microsoft.com <br>portal.fei.amsub0102.manage.microsoft.com <br>m.fei.amsub0102.manage.microsoft.com<br>fei.msub02.manage.microsoft.com <br>portal.fei.msub02.manage.microsoft.com <br>m.fei.msub02.manage.microsoft.com<br>fei.msub03.manage.microsoft.com <br>portal.fei.msub03.manage.microsoft.com <br>m.fei.msub03.manage.microsoft.com<br>fei.msub05.manage.microsoft.com <br>portal.fei.msub05.manage.microsoft.com <br>m.fei.msub05.manage.microsoft.com<br>fei.amsub0202.manage.microsoft.com <br>portal.fei.amsub0202.manage.microsoft.com <br>m.fei.amsub0202.manage.microsoft.com<br>fei.amsub0302.manage.microsoft.com <br>portal.fei.amsub0302.manage.microsoft.com <br>m.fei.amsub0302.manage.microsoft.com|52.138.193.149<br>51.144.161.187|
|fei.msuc01.manage.microsoft.com <br>portal.fei.msuc01.manage.microsoft.com <br>m.fei.msuc01.manage.microsoft.com<br>fei.msuc02.manage.microsoft.com <br>portal.fei.msuc02.manage.microsoft.com <br>m.fei.msuc02.manage.microsoft.com<br>fei.msuc03.manage.microsoft.com <br>portal.fei.msuc03.manage.microsoft.com <br>m.fei.msuc03.manage.microsoft.com<br>fei.msuc05.manage.microsoft.com <br>portal.fei.msuc05.manage.microsoft.com <br>m.fei.msuc05.manage.microsoft.com|52.175.12.209<br>20.188.107.228|
|fef.msua01.manage.microsoft.com|138.91.243.97|
|fef.msua02.manage.microsoft.com|52.177.194.236|
|fef.msua04.manage.microsoft.com|23.96.112.28|
|fef.msua05.manage.microsoft.com|138.91.244.151|
|fef.msua06.manage.microsoft.com|13.78.185.97|
|fef.msua07.manage.microsoft.com|52.175.208.218|
|fef.msub01.manage.microsoft.com|137.135.128.214|
|fef.msub02.manage.microsoft.com|137.135.130.29|
|fef.msub03.manage.microsoft.com|52.169.82.238|
|fef.msub05.manage.microsoft.com|23.97.166.52|
|fef.msuc01.manage.microsoft.com|52.230.19.86|
|fef.msuc02.manage.microsoft.com|23.98.66.118|
|fef.msuc03.manage.microsoft.com|23.101.0.100|
|fef.msuc05.manage.microsoft.com|52.230.16.180|
|fef.amsua0202.manage.microsoft.com|52.165.165.17|
|fef.amsua0402.manage.microsoft.com|40.69.157.122|
|fef.amsua0502.manage.microsoft.com|13.85.68.142|
|fef.amsua0602.manage.microsoft.com|52.161.28.64|
|fef.amsub0102.manage.microsoft.com|40.118.98.207|
|fef.amsub0202.manage.microsoft.com|40.69.208.122|
|fef.amsub0302.manage.microsoft.com|13.74.145.65|
|enterpriseregistration.windows.net|52.175.211.189|
|Admin.manage.microsoft.com|52.224.221.227<br>52.161.162.117<br>52.178.44.195<br>52.138.206.56<br>52.230.21.208<br>13.75.125.10|
|wip.mam.manage.microsoft.com|52.187.76.84<br>13.76.5.121<br>52.165.160.237<br>40.86.82.163<br>52.233.168.142<br>168.63.101.57|
|mam.manage.microsoft.com|104.40.69.125<br>13.90.192.78<br>40.85.174.177<br>40.85.77.31<br>137.116.229.43<br>52.163.215.232<br>52.174.102.180|






### <a name="apple-device-network-information"></a>Apple 디바이스 네트워크 정보


|사용 목적|호스트 이름(IP 주소/서브넷)|프로토콜|포트|
|-----|--------|------|-------|
|APNS(Apple Push Notification Service)를 통해 Intune 서비스에서 푸시 알림 받기. [여기](https://support.apple.com/en-us/HT203609)에서 Apple 설명서를 참조하세요.|                                    gateway.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2195     |
|APNS(Apple Push Notification Service)를 통해 Intune 서비스에 피드백 보내기|                                  feedback.push.apple.com(17.0.0.0/8)                                  |    TCP     |     2196     |
|Apple 서버에서 콘텐츠 받기 및 표시|itunes.apple.com<br>\*.itunes.apple.com<br>\*.mzstatic.com<br>\*.phobos.apple.com<br> \*.phobos.itunes-apple.com.akadns.net |    HTTP    |      80      |
|APNS 서버와 통신|#-courier.push.apple.com(17.0.0.0/8)<br>‘#’은 0~50 사이 임의 숫자입니다.|    TCP     |  5223 및 443  |
|World Wide Web, iTunes Store, macOS 앱 스토어, iCloud, 메시징 등 액세스를 포함한 다양한 기능 |phobos.apple.com<br>ocsp.apple.com<br>ax.itunes.apple.com<br>ax.itunes.apple.com.edgesuite.net| HTTP/HTTPS |  80 또는 443   |

자세한 내용은 Apple의 [TCP and UDP ports used by Apple software products](https://support.apple.com/en-us/HT202944)(Apple 소프트웨어 제품에 사용되는 TCP 및 UDP 포트), [About macOS, iOS, and iTunes server host connections and iTunes background processes](https://support.apple.com/en-us/HT201999)(macOS, iOS 및 iTunes 서버 호스트 연결과 iTunes 백그라운드 프로세스 정보) 및 [If your macOS and iOS clients aren't getting Apple push notifications](https://support.apple.com/en-us/HT203609)(macOS 및 iOS 클라이언트가 Apple 푸시 알림을 받지 못하는 경우)를 참조하세요.
